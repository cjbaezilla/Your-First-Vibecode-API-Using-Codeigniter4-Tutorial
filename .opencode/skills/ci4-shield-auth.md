# CodeIgniter Shield Authentication

Skill for implementing authentication and authorization in CodeIgniter 4 using Shield.

## Overview

CodeIgniter Shield provides comprehensive authentication:
- **Session Auth**: Stateful authentication with cookies
- **Access Tokens**: Stateless Bearer tokens for APIs
- **HMAC**: Request signing for high-security APIs
- **JWT**: Self-contained tokens with claims
- **Authorization**: Groups and permissions (RBAC)

## Documentation Reference

- `/shield-docs/getting_started/install.md` - Installation
- `/shield-docs/guides/api_tokens.md` - API Token Guide
- `/shield-docs/guides/api_hmac_keys.md` - HMAC Guide
- `/shield-docs/references/authorization.md` - Authorization
- `/shield-docs/references/authentication/authentication.md` - Overview

## Installation

```bash
# Install via Composer
composer require codeigniter4/shield

# Run setup (creates config files, migrations)
php spark shield:setup

# Run migrations
php spark migrate --all
```

## Configuration Files

Shield creates these config files in `app/Config/`:

| File | Purpose |
|------|---------|
| `Auth.php` | Main authentication settings, actions |
| `AuthGroups.php` | Groups, permissions, matrix |
| `AuthToken.php` | Token settings (access tokens, HMAC) |
| `AuthJWT.php` | JWT authentication settings |

## Authentication Methods

### 1. Session Authentication

For traditional web applications:

```php
// Login
$credentials = [
    'email' => $this->request->getPost('email'),
    'password' => $this->request->getPost('password'),
];

$result = auth()->attempt($credentials);

if (!$result->isOK()) {
    return redirect()->back()->with('error', $result->getReason());
}

// Remember me
$result = auth()->remember()->attempt($credentials);

// Check authentication
if (auth()->loggedIn()) {
    $user = auth()->user();
    $userId = auth()->id();
}

// Logout
auth()->logout();
```

### 2. Access Token Authentication

Best for API clients (mobile apps, SPAs):

```php
// Generate token
$user = auth()->user();
$token = $user->generateAccessToken('Device Name', ['users-read', 'users-write']);

// Display raw token immediately (only time it's shown!)
return $this->respond([
    'token' => $token->raw_token,
    'expires' => $token->expires,
]);

// Use token in requests
// Authorization: Bearer <token>

// Check token scope
if ($user->tokenCan('users-write')) {
    // Authorized
}

// Revoke token
$user->revokeAccessToken($token->id);
$user->revokeAllAccessTokens();
```

**Token Settings (AuthToken.php):**
```php
public int $accessTokenLifetime = 365 * DAY;  // Default: 1 year
public int $unusedTokenLifetime = 365 * DAY;  // Expires if unused
```

### 3. HMAC Authentication

For high-security APIs with request signing:

```php
// Generate HMAC key
$user = auth()->user();
$hmac = $user->generateHmacToken('Device Name');

// Client signs requests
// Authorization: HMAC-SHA256 <key_id>:<signature>
// X-Auth-Timestamp: <timestamp>
// X-Auth-Nonce: <random_string>

// Server verifies signature
// Shield validates automatically via hmac filter
```

### 4. JWT Authentication

Requires additional package:

```bash
composer require codeigniter4/shield-jwt
```

```php
// Generate JWT
$token = auth()->user()->generateJWT();

// Use in requests
// Authorization: Bearer <jwt_token>
```

## Route Protection with Filters

Shield automatically registers these filters:

```php
// app/Config/Routes.php

// Session authentication
$routes->get('profile', 'User::profile', ['filter' => 'session']);

// Token authentication
$routes->group('api', ['filter' => 'tokens'], function($routes) {
    $routes->resource('users');
});

// Token with scope check
$routes->get('users', 'User::index', ['filter' => 'tokens:users-read']);

// HMAC authentication
$routes->group('api/secure', ['filter' => 'hmac'], function($routes) {
    $routes->resource('payments');
});

// Chain authentication (session OR token)
$routes->group('api', ['filter' => 'chain:session,tokens'], function($routes) {
    $routes->resource('products');
});
```

**Filter Configuration (Filters.php):**
```php
public $aliases = [
    'session'    => \CodeIgniter\Shield\Filters\SessionAuth::class,
    'tokens'     => \CodeIgniter\Shield\Filters\TokenAuth::class,
    'hmac'       => \CodeIgniter\Shield\Filters\HmacAuth::class,
    'chain'      => \CodeIgniter\Shield\Filters\ChainAuth::class,
    'auth-rates' => \CodeIgniter\Shield\Filters\AuthRates::class,
];

public $globals = [
    'before' => [
        'auth-rates' => ['except' => ['login*', 'register', 'auth/a/*']],
    ],
];
```

## Authorization (RBAC)

### Defining Groups

```php
// app/Config/AuthGroups.php
public array $groups = [
    'superadmin' => [
        'title'       => 'Super Admin',
        'description' => 'Complete system access',
    ],
    'admin' => [
        'title'       => 'Administrator',
        'description' => 'Day-to-day administrators',
    ],
    'user' => [
        'title'       => 'User',
        'description' => 'General users',
    ],
];
```

### Defining Permissions

```php
public array $permissions = [
    'admin.access'    => 'Can access admin area',
    'users.create'    => 'Can create users',
    'users.edit'      => 'Can edit users',
    'users.delete'    => 'Can delete users',
    'products.manage' => 'Can manage products',
];
```

### Permission Matrix

```php
public array $matrix = [
    'superadmin' => ['*'],  // Wildcard - all permissions
    'admin' => [
        'admin.access',
        'users.*',
        'products.manage',
    ],
    'user' => [
        'products.read',
    ],
];
```

### Checking Permissions

```php
$user = auth()->user();

// Check via groups
if ($user->inGroup('admin', 'superadmin')) {
    // User is in admin or superadmin group
}

// Check specific permission
if ($user->can('users.create')) {
    // User can create users (via groups or direct permission)
}

// Check only direct permissions
if ($user->hasPermission('users.create')) {
    // User has direct permission (not via group)
}

// Route-level permission filter
$routes->get('admin/users', 'Admin::users', ['filter' => 'permission:users.manage']);
$routes->group('admin', ['filter' => 'group:admin'], function($routes) {
    // All routes require 'admin' group
});
```

### Managing User Permissions

```php
$user = auth()->user();

// Add to group
$user->addGroup('admin');
$user->removeGroup('user');

// Add permissions
$user->addPermission('users.create', 'users.edit');
$user->removePermission('users.delete');

// Sync permissions (replaces all)
$user->syncPermissions(['users.create', 'users.read']);
```

## Helper Functions

```php
// Get authentication service
$auth = auth();

// Get current user
$user = auth()->user();

// Get user ID
$userId = auth()->id();  // or user_id()

// Get user provider (UserModel)
$users = auth()->getProvider();

// Check if logged in
$isLoggedIn = auth()->loggedIn();

// Check if guest
$isGuest = auth()->guest();
```

## CLI Commands

```bash
# User management
php spark shield:user create                    # Create user
php spark shield:user list                      # List all users
php spark shield:user activate <email>          # Activate user
php spark shield:user deactivate <email>        # Deactivate user
php spark shield:user addgroup <email> <group>  # Add to group
php spark shield:user removegroup <email> <group> # Remove from group
php spark shield:user delete <email>            # Delete user
php spark shield:user password <email>          # Change password

# HMAC management
php spark shield:hmac reencrypt                 # Re-encrypt all HMAC keys
php spark shield:hmac invalidateAll             # Invalidate all HMAC keys
```

## Authentication Actions

Shield supports post-login actions (optional):

```php
// app/Config/Auth.php
public array $actions = [
    'register' => null,
    'login'    => null,
];

// Enable email activation
public array $actions = [
    'register' => \CodeIgniter\Shield\Authentication\Actions\EmailActivator::class,
];

// Enable 2FA
public array $actions = [
    'login' => \CodeIgniter\Shield\Authentication\Actions\Email2FA::class,
];
```

## Magic Link Login

Passwordless login via email:

```php
// Request magic link
return view('Auth/magic_link_form');

// Verify magic link
// Shield handles automatically
// Route: /auth/a/verify-magic-link
```

## User Entity Methods

```php
$user = auth()->user();

// Status checks
$user->isActivated();
$user->isNotActivated();
$user->isBanned();
$user->requiresPasswordReset();

// Status management
$user->activate();
$user->deactivate();
$user->ban('Reason');
$user->unBan();
$user->forcePasswordReset();
$user->undoForcePasswordReset();

// Get ban reason
$reason = $user->getBanMessage();
```

## Password Security

Shield uses multiple validators (see ci4-security):

```php
// app/Config/Auth.php
public array $passwordValidators = [
    'CodeIgniter\Shield\Authentication\Passwords\CompositionValidator',
    'CodeIgniter\Shield\Authentication\Passwords\NothingPersonalValidator',
    'CodeIgniter\Shield\Authentication\Passwords\DictionaryValidator',
    // 'CodeIgniter\Shield\Authentication\Passwords\PwnedValidator',
];
```

## Best Practices

1. **Use tokens for APIs** - Stateless authentication
2. **Set token scopes** - Fine-grained permissions
3. **Apply rate limiting** - On login/register endpoints
4. **Use HTTPS** - Always for authentication
5. **Short token lifetime** - Reduce security risk
6. **Group permissions** - Easier management than individual
7. **Eager load relations** - For better performance
8. **Log auth events** - Track login/logout

## Related Skills

- **ci4-api-development** - Building API endpoints
- **ci4-security** - Validation, rate limiting, password security
- **ci4-routing-controllers** - Route filters, protected routes
- **ci4-models-database** - User model customization
- **ci4-configuration** - Auth config, environment variables
