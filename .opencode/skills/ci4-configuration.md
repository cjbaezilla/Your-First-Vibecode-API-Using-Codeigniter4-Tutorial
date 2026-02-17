# CodeIgniter 4 Configuration

Skill for working with CodeIgniter 4 configuration files, environment variables, services, and environment management.

## Overview

CI4 uses a flexible configuration system:
- **Config Classes**: PHP classes in `app/Config/`
- **Environment Variables**: `.env` file for sensitive data
- **Services**: Dependency injection container
- **Environment Modes**: Development, testing, production

## Documentation Reference

- `/ci-userguide/general/configuration.html` - Configuration System
- `/ci-userguide/general/environments.html` - Environment Handling
- `/ci-userguide/concepts/services.html` - Services

## Configuration Files

Located in `app/Config/` (42+ config files):

### Core Config Files

| File | Purpose |
|------|---------|
| `App.php` | Base URL, index page, encryption key |
| `Routes.php` | Route definitions |
| `Database.php` | Database connections |
| `Autoload.php` | Autoload helpers, libraries |
| `Services.php` | Service definitions |
| `Filters.php` | Filter configuration |
| `Security.php` | CSRF, security headers |
| `Cors.php` | CORS configuration |
| `Format.php` | API response formats |
| `Validation.php` | Custom validation rules |
| `Encryption.php` | Encryption settings |
| `Session.php` | Session configuration |
| `Cache.php` | Cache settings |
| `Logger.php` | Logging configuration |
| `Email.php` | Email settings |

### Shield Config Files

| File | Purpose |
|------|---------|
| `Auth.php` | Authentication settings |
| `AuthGroups.php` | Groups and permissions |
| `AuthToken.php` | Token settings |
| `AuthJWT.php` | JWT settings |

## Using Config Classes

```php
// Load config
$config = config('App');
$config = new \Config\App();

// Access properties
$baseURL = config('App')->baseURL;
$environment = ENVIRONMENT;

// Modify at runtime
$config = config('App');
$config->baseURL = 'https://example.com';
```

## Environment Variables (.env)

### Setup

```bash
# Copy template
copy env .env

# Or on Unix
cp env .env
```

### .env Structure

```ini
# Environment
CI_ENVIRONMENT = development

# App settings
app.baseURL = 'http://localhost:8080'
app.indexPage = ''
app.appTimezone = 'America/New_York'
app.CSPEnabled = true

# Database
database.default.hostname = localhost
database.default.database = ci_api_db
database.default.username = root
database.default.password = secret
database.default.DBDriver = MySQLi
database.default.DBPrefix =

# Email
email.SMTPHost = smtp.example.com
email.SMTPUser = user@example.com
email.SMTPPass = password
email.SMTPPort = 587

# Encryption
encryption.key = hex2bin:your64characterhexkeyhere

# Session
session.driver = 'CodeIgniter\Session\Handlers\FileHandler'
session.cookieName = ci_session
session.expiration = 7200

# Logger
logger.threshold = 4
```

### Accessing Environment Variables

```php
// In PHP
$dbHost = getenv('database.default.hostname');
$dbHost = $_ENV['database.default.hostname'] ?? 'localhost';
$dbHost = $_SERVER['database.default.hostname'] ?? 'localhost';

// Using env() helper
$dbHost = env('database.default.hostname', 'localhost');

// Config classes automatically read .env
// Config/Database.php reads database.default.* values
```

## Creating Custom Config

```php
<?php

namespace Config;

use CodeIgniter\Config\BaseConfig;

class Payment extends BaseConfig
{
    public string $gateway = 'stripe';
    public string $apiKey = '';
    public string $apiSecret = '';
    public string $currency = 'USD';
    public bool $sandbox = true;
    
    public function __construct()
    {
        parent::__construct();
        
        // Load from environment
        $this->apiKey = env('payment.stripe_key', '');
        $this->apiSecret = env('payment.stripe_secret', '');
        $this->sandbox = env('payment.sandbox', true);
    }
}
```

Usage:

```php
$paymentConfig = config('Payment');
$apiKey = $paymentConfig->apiKey;
```

## Registrars

Registrars allow modules to auto-register configs:

```php
// Shield provides Registrar for filters
// Config/Filters.php doesn't need manual aliases
// Shield automatically registers: session, tokens, hmac, jwt, chain, etc.
```

## Services

Services provide dependency injection:

```php
// Get service
$renderer = \Config\Services::renderer();
$email = \Config\Services::email();
$session = \Config\Services::session();
$validation = \Config\Services::validation();

// With options
$email = \Config\Services::email([
    'protocol' => 'smtp',
    'SMTPHost' => 'smtp.example.com',
]);

// Check if service exists
if (\Config\Services::has('mycustom')) {
    $service = \Config\Services::mycustom();
}
```

### Creating Custom Services

```php
<?php

namespace Config;

use CodeIgniter\Config\BaseService;
use App\Libraries\PaymentGateway;

class Services extends BaseService
{
    public static function payment($getShared = true)
    {
        if ($getShared) {
            return static::getSharedInstance('payment');
        }

        $config = new \Config\Payment();
        return new PaymentGateway($config);
    }
    
    public static function customService($param = null, $getShared = true)
    {
        if ($getShared) {
            return static::getSharedInstance('customService', $param);
        }

        return new \App\Libraries\CustomLibrary($param);
    }
}
```

Usage:

```php
$payment = \Config\Services::payment();
$custom = \Config\Services::customService('param');
```

## Environment Modes

```php
// Check environment
if (ENVIRONMENT === 'development') {
    // Development-only code
}

if (ENVIRONMENT === 'production') {
    // Production-only code
}

if (ENVIRONMENT === 'testing') {
    // Testing-only code
}
```

### Switching Environments

```bash
# Set in .env
CI_ENVIRONMENT = development

# Or via spark command
php spark env development
php spark env production
php spark env testing
```

### Environment-Specific Configs

```php
// Config/App.php - checks environment automatically
// Set CI_ENVIRONMENT and configs load appropriately

// Custom environment configs
// app/Config/development/
// app/Config/production/
// app/Config/testing/
```

## Helper Functions

```php
// Base URL
base_url('path/to/resource');           // http://example.com/path/to/resource
base_url(['path', 'to', 'resource']);   // Same as above

// Site URL (with index_page if set)
site_url('controller/method');

// Current URL
current_url();
current_url(true);  // Returns URI object

// Previous URL
previous_url();

// Config
config('App');
config('App')->baseURL;

// Environment
env('VAR_NAME', 'default_value');

// CI Environment
ENVIRONMENT;  // 'development', 'production', 'testing'
```

## Common Configuration Scenarios

### API Configuration

```php
// Config/Format.php
public string $supportedResponseFormats = [
    'application/json',
    'application/xml',
];

public array $formatters = [
    'application/json' => \CodeIgniter\Format\JSONFormatter::class,
    'application/xml'  => \CodeIgniter\Format\XMLFormatter::class,
];
```

### Database Configuration

```php
// Config/Database.php or .env
database.default.hostname = localhost
database.default.database = mydb
database.default.username = root
database.default.password = secret
database.default.DBDriver = MySQLi
database.default.DBDebug = false  // Set false in production

// Multiple connections
database.tests.hostname = localhost
database.tests.database = test_db
database.tests.username = test_user
database.tests.password = test_pass
database.tests.DBDriver = MySQLi
```

### CORS Configuration

```php
// Config/Cors.php
public array $default = [
    'allowedOrigins' => ['https://app.example.com'],
    'allowedOriginsPatterns' => [],
    'supportsCredentials' => true,
    'allowedHeaders' => ['Content-Type', 'Authorization'],
    'allowedMethods' => ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
    'exposedHeaders' => [],
    'maxAge' => 7200,
];
```

### Session Configuration

```php
// Config/Session.php
public string $driver = 'CodeIgniter\Session\Handlers\FileHandler';
public string $cookieName = 'ci_session';
public int $expiration = 7200;
public string $savePath = WRITEPATH . 'session';
public bool $matchIP = false;
public int $timeToUpdate = 300;
public bool $regenerateDestroy = false;

// Database session handler
public string $driver = 'CodeIgniter\Session\Handlers\DatabaseHandler';
```

### Cache Configuration

```php
// Config/Cache.php
public string $handler = 'file';  // file, memcached, redis, predis
public string $backupHandler = 'dummy';
public int $ttl = 60;

// File settings
public string $file = [
    'storePath' => WRITEPATH . 'cache/',
    'mode'      => 0640,
];

// Redis settings
public array $redis = [
    'host'     => '127.0.0.1',
    'password' => null,
    'port'     => 6379,
    'timeout'  => 0,
    'database' => 0,
];
```

### Logging Configuration

```php
// Config/Logger.php
public int $threshold = 4;  // 0-9, higher = more verbose

public array $handlers = [
    'CodeIgniter\Log\Handlers\FileHandler' => [
        'handles' => ['critical', 'alert', 'emergency', 'debug', 'error', 'info', 'notice', 'warning'],
        'path' => WRITEPATH . 'logs/',
    ],
];
```

### Email Configuration

```php
// Config/Email.php
public string $protocol = 'smtp';
public string $SMTPHost = 'smtp.gmail.com';
public string $SMTPUser = 'user@gmail.com';
public string $SMTPPass = 'app-password';
public int $SMTPPort = 587;
public string $SMTPCrypto = 'tls';
public string $mailType = 'html';
public string $charset = 'UTF-8';
```

## Configuration Best Practices

1. **Use .env for secrets** - Never commit sensitive data
2. **Set defaults** - Always provide fallback values
3. **Group related configs** - Keep configs organized
4. **Document configs** - Add comments explaining options
5. **Environment-specific** - Use .env for environment differences
6. **Cache configs** - In production, configs can be cached
7. **Validate configs** - Check required settings on load
8. **Use type hints** - PHP 7.4+ type declarations

## Troubleshooting

### Config not loading from .env:
- Check `.env` file exists in root
- Ensure no syntax errors in .env
- Variable names must match exactly
- Use `env()` helper for debugging

### Services not found:
- Check `Config/Services.php` exists
- Ensure correct namespace
- Clear cache: `php spark cache:clear`

### Environment not detected:
- Check `CI_ENVIRONMENT` in .env
- Verify file permissions
- Try setting directly in index.php

## Related Skills

- **ci4-routing-controllers** - Routes config, controller setup
- **ci4-security** - Security config, CSRF, CSP
- **ci4-models-database** - Database config
- **ci4-shield-auth** - Auth config
- **ci4-api-development** - API format config
- **ci4-testing** - Testing environment config
