# CodeIgniter 4 Security

Skill for implementing security best practices in CodeIgniter 4 including validation, CSRF protection, rate limiting, encryption, and OWASP compliance.

## Overview

CI4 provides comprehensive security features:
- **Validation**: Input validation with 30+ rules
- **CSRF Protection**: Cross-Site Request Forgery prevention
- **XSS Filtering**: Output escaping
- **Rate Limiting**: Throttle library for API protection
- **Encryption**: Secure data encryption
- **Password Hashing**: Argon2id and bcrypt
- **Security Headers**: CSP, HSTS, X-Frame-Options

## Documentation Reference

- `/ci-userguide/concepts/security.html` - Security Guidelines
- `/ci-userguide/libraries/security.html` - Security Library
- `/ci-userguide/libraries/validation.html` - Validation Library
- `/ci-userguide/libraries/throttler.html` - Rate Limiting
- `/ci-userguide/libraries/encryption.html` - Encryption Service

## OWASP Top 10 Coverage

CI4 addresses OWASP security risks:

| Risk | CI4 Protection |
|------|---------------|
| Broken Access Control | Filters, Shield, user_id() |
| Cryptographic Failures | Encryption service, password_hash() |
| Injection | Query Builder, prepared statements |
| Insecure Design | Validation, form helper |
| Security Misconfiguration | SecureHeaders filter, .env |
| Vulnerable Components | Composer audit |
| Auth Failures | Shield, Session, Throttler |
| Software Integrity | File validation |
| Logging Failures | Logger service |
| SSRF | URI validation |

## Input Validation

### Basic Validation

```php
$validation = \Config\Services::validation();

$rules = [
    'username' => 'required|min_length[3]|max_length[20]',
    'email'    => 'required|valid_email',
    'password' => 'required|min_length[8]',
    'confirm'  => 'required|matches[password]',
    'age'      => 'required|integer|greater_than[17]',
    'website'  => 'permit_empty|valid_url',
];

if (!$this->validate($rules)) {
    $errors = $this->validator->getErrors();
    return $this->failValidationErrors($errors);
}

$data = $this->validator->getValidated();
```

### Validation Rules

```php
// String rules
'alpha'                  // Letters only
'alpha_numeric'          // Letters and numbers
'alpha_numeric_punct'    // Letters, numbers, punctuation
'alpha_numeric_space'    // Letters, numbers, spaces
'alpha_dash'             // Letters, dash, underscore
'numeric'                // Numbers only
'integer'                // Integers only
'decimal'                // Decimal numbers
'valid_url'              // Valid URL
'valid_email'            // Valid email
'valid_emails'           // Comma-separated emails
'valid_ip'               // Valid IP address
'valid_base64'           // Valid base64

// Comparison rules
'exact_length[5]'        // Exactly 5 characters
'min_length[5]'          // Minimum 5 characters
'max_length[50]'         // Maximum 50 characters
'greater_than[0]'        // > 0
'greater_than_equal_to[0]'  // >= 0
'less_than[100]'         // < 100
'less_than_equal_to[100]'   // <= 100
'in_list[red,blue,green]'   // Value in list
'not_in_list[admin,root]'   // Value not in list

// Database rules
'is_unique[users.email]'     // Must be unique
'is_not_unique[users.email]' // Must exist in table

// File rules
'uploaded[field]'            // File was uploaded
'mime_in[field,image/png,image/jpg]'  // MIME type
'ext_in[field,png,jpg,gif]'  // File extension
'max_dims[field,1920,1080]'  // Image dimensions

// Custom rules
'callback_check_username'    // Custom method
```

### Custom Validation Rules

```php
// In Controller
protected $validationRules = [
    'username' => 'required|callback_check_username',
];

public function check_username(string $str, string &$error = null): bool
{
    if ($str === 'admin') {
        $error = 'Username "admin" is reserved';
        return false;
    }
    return true;
}
```

### Model Validation

```php
class UserModel extends Model
{
    protected $validationRules = [
        'username' => 'required|min_length[3]|is_unique[users.username]',
        'email'    => 'required|valid_email|is_unique[users.email]',
    ];

    protected $validationMessages = [
        'username' => [
            'required'  => 'Please enter a username',
            'is_unique' => 'That username is already taken',
        ],
    ];
}
```

## CSRF Protection

CSRF tokens prevent cross-site request forgery:

```php
// In Forms (View)
<form method="post" action="/submit">
    <?= csrf_field() ?>  <!-- Adds CSRF token -->
    <input type="text" name="username">
    <button type="submit">Submit</button>
</form>

// Or manually
<input type="hidden" name="<?= csrf_token() ?>" value="<?= csrf_hash() ?>">
```

```php
// In Config/Security.php
public bool $CSRFProtection = true;
public string $CSRFCookieName = 'csrf_cookie_name';
public int $CSRFExpire = 7200;  // 2 hours
public bool $CSRFRegenerate = true;  // Regenerate token on success
```

```php
// Apply to routes (Filters.php)
public $globals = [
    'before' => [
        'csrf' => ['except' => ['api/*', 'webhook/*']],
    ],
];
```

```php
// For AJAX requests
// Include token in header
headers: {
    'X-CSRF-TOKEN': document.querySelector('meta[name="csrf-token"]').content
}
```

## XSS Prevention

```php
// Escape output (Views)
<p><?= esc($user['username']) ?></p>
<p><?= esc($content, 'html') ?></p>     // HTML entities (default)
<p><?= esc($content, 'js') ?></p>       // JavaScript
<p><?= esc($content, 'css') ?></p>      // CSS
<p><?= esc($content, 'url') ?></p>      // URL
<p><?= esc($content, 'attr') ?></p>     // HTML attribute
<p><?= esc($content, 'raw') ?></p>      // No escaping

// In API responses (automatic when using ResponseTrait)
return $this->respond(['data' => $user]);

// Purify HTML (if allowing HTML input)
$config = HTMLPurifier_Config::createDefault();
$purifier = new HTMLPurifier($config);
$clean_html = $purifier->purify($dirty_html);
```

## Rate Limiting (Throttling)

Protect APIs from abuse:

```php
// Config/Throttler.php
public int $tokenBucketCapacity = 60;  // Max requests
public int $tokenBucketRefillRate = 1; // Per second
public string $tokenBucketRefillPeriod = 'second';
```

```php
// Apply throttling filter
// Config/Filters.php
public $filters = [
    'throttle' => ['before' => ['api/*']],
];

// Or in routes
$routes->group('api', ['filter' => 'throttle:60,minute'], function($routes) {
    $routes->resource('users');
});
```

```php
// Manual throttling in controller
$throttler = \Config\Services::throttler();

// Check rate limit
$allowed = $throttler->check(
    $request->getIPAddress(),  // Key (IP address)
    60,                         // Capacity (requests)
    MINUTE                      // Time period
);

if (!$allowed) {
    return $this->failTooManyRequests('Rate limit exceeded');
}
```

```php
// Different limits for different endpoints
public function login()
{
    $throttler = \Config\Services::throttler();
    
    // Stricter limits for auth endpoints
    if (!$throttler->check('login:' . $this->request->getIPAddress(), 5, MINUTE)) {
        return $this->failTooManyRequests('Too many login attempts');
    }
    
    // ... authentication logic
}
```

## Encryption

```php
$encrypter = \Config\Services::encrypter();

// Encrypt
$plainText = 'sensitive data';
$ciphertext = $encrypter->encrypt($plainText);

// Decrypt
$plainText = $encrypter->decrypt($ciphertext);
```

```php
// Config/Encryption.php
public string $key = '';  // Set in .env: encryption.key = your-key
public string $driver = 'OpenSSL';
public string $digest = 'SHA512';
public int $blockSize = 16;
public string $cipher = 'AES-256-CTR';
```

```php
// Generate key
php spark key:generate

// Add to .env
encryption.key = hex2bin:your-64-char-hex-key
```

## Password Security

CI4 uses Shield's password validators:

```php
// Config/Auth.php (Shield)
public array $passwordValidators = [
    \CodeIgniter\Shield\Authentication\Passwords\CompositionValidator::class,
    \CodeIgniter\Shield\Authentication\Passwords\NothingPersonalValidator::class,
    \CodeIgniter\Shield\Authentication\Passwords\DictionaryValidator::class,
    // \CodeIgniter\Shield\Authentication\Passwords\PwnedValidator::class,
];

public int $minimumPasswordLength = 8;
```

```php
// Password hashing (automatic in Shield)
$password = 'userpassword';
$hash = password_hash($password, PASSWORD_ARGON2ID);

// Verify
if (password_verify($password, $hash)) {
    // Valid password
}
```

## Security Headers

```php
// Config/Filters.php - Enable SecureHeaders filter
public $globals = [
    'after' => [
        'secureheaders',
    ],
];
```

```php
// Config/Security.php
public array $headers = [
    'X-Frame-Options' => 'SAMEORIGIN',
    'X-Content-Type-Options' => 'nosniff',
    'X-XSS-Protection' => '1; mode=block',
    'Referrer-Policy' => 'strict-origin-when-cross-origin',
    'Strict-Transport-Security' => 'max-age=31536000; includeSubDomains',
];
```

## Content Security Policy (CSP)

```php
// Config/ContentSecurityPolicy.php
public bool $reportOnly = false;  // Set true for testing

public array $defaultSrc = ['self'];
public array $scriptSrc = ['self', 'https://cdn.example.com'];
public array $styleSrc = ['self', 'unsafe-inline'];
public array $imgSrc = ['self', 'data:', 'https:'];
public array $connectSrc = ['self', 'https://api.example.com'];
public array $fontSrc = ['self', 'https://fonts.gstatic.com'];
public array $frameSrc = ['none'];
public array $baseUri = ['self'];
public array $formAction = ['self'];
```

```php
// Enable CSP filter
public $globals = [
    'after' => [
        'csp',
    ],
];
```

## CORS Protection

```php
// Config/Cors.php
public array $default = [
    'allowedOrigins' => ['https://example.com', 'https://app.example.com'],
    'allowedOriginsPatterns' => [],
    'supportsCredentials' => true,
    'allowedHeaders' => ['Content-Type', 'Authorization', 'X-Requested-With'],
    'allowedMethods' => ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
    'exposedHeaders' => [],
    'maxAge' => 7200,
];
```

```php
// Enable CORS filter
public $globals = [
    'before' => [
        'cors',
    ],
];
```

## File Upload Security

```php
// Validate file upload
$validation = \Config\Services::validation();

$rules = [
    'avatar' => [
        'rules' => 'uploaded[avatar]'
                 . '|mime_in[avatar,image/png,image/jpg,image/jpeg]'
                 . '|ext_in[avatar,png,jpg,jpeg]'
                 . '|max_size[avatar,2048]'  // 2MB
                 . '|max_dims[avatar,1920,1080]',
    ],
];

if (!$this->validate($rules)) {
    return $this->failValidationErrors($this->validator->getErrors());
}

$file = $this->request->getFile('avatar');

// Generate safe filename
$newName = $file->getRandomName();

// Move to writable/uploads
$file->move(WRITEPATH . 'uploads', $newName);

// Or validate manually
if (!$file->isValid()) {
    throw new RuntimeException($file->getErrorString());
}

if (!$file->hasMoved()) {
    $file->move(WRITEPATH . 'uploads');
}
```

## SQL Injection Prevention

Always use Query Builder or prepared statements:

```php
// SAFE: Query Builder (parameterized)
$user = $db->table('users')
    ->where('email', $email)
    ->get()
    ->getRow();

// SAFE: Prepared statements
$sql = "SELECT * FROM users WHERE email = ?";
$query = $db->query($sql, [$email]);

// UNSAFE: Never do this!
$sql = "SELECT * FROM users WHERE email = '$email'";
$query = $db->query($sql);
```

## Security Checklist

### For API Development:

- [ ] Use HTTPS in production
- [ ] Validate all input with strict rules
- [ ] Apply rate limiting to all endpoints
- [ ] Implement authentication (see ci4-shield-auth)
- [ ] Apply authorization checks
- [ ] Use proper HTTP status codes
- [ ] Sanitize output with `esc()`
- [ ] Enable CORS with restricted origins
- [ ] Set security headers
- [ ] Log security events
- [ ] Use strong password policies
- [ ] Encrypt sensitive data at rest
- [ ] Use secure session handling
- [ ] Validate file uploads
- [ ] Prevent SQL injection with Query Builder

## Related Skills

- **ci4-shield-auth** - Authentication, password validation
- **ci4-api-development** - Secure API responses
- **ci4-routing-controllers** - Filter security
- **ci4-models-database** - Query builder, input validation
- **ci4-configuration** - Security config, environment variables
