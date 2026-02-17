# CodeIgniter 4 Routing and Controllers

Skill for defining routes, creating controllers, and using filters in CodeIgniter 4.

## Overview

CI4 provides a powerful routing system:
- **Defined Routes**: Manual route configuration
- **Auto Routing**: Automatic controller/method mapping
- **Resource Routes**: RESTful resource routing
- **Filters**: Middleware for request/response processing

## Documentation Reference

- `/ci-userguide/incoming/routing.html` - URI Routing
- `/ci-userguide/incoming/controllers.html` - Controllers
- `/ci-userguide/incoming/filters.html` - Controller Filters
- `/ci-userguide/incoming/restful.html` - RESTful Resources

## Route Configuration

Routes are defined in `app/Config/Routes.php`:

```php
<?php

namespace Config;

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */

// Default route
$routes->get('/', 'Home::index');

// Basic routes
$routes->get('products', 'Product::index');
$routes->get('products/(:num)', 'Product::show/$1');
$routes->post('products', 'Product::create');
$routes->put('products/(:num)', 'Product::update/$1');
$routes->delete('products/(:num)', 'Product::delete/$1');

// Multiple HTTP verbs
$routes->match(['GET', 'POST'], 'products', 'Product::list');
$routes->add('products', 'Product::list');  // Any HTTP verb
```

## Route Placeholders

```php
// (:num) - Numbers only
$routes->get('user/(:num)', 'User::profile/$1');

// (:alpha) - Letters only
$routes->get('category/(:alpha)', 'Category::show/$1');

// (:alphanum) - Letters and numbers
$routes->get('tag/(:alphanum)', 'Tag::show/$1');

// (:segment) - Single URI segment (no slashes)
$routes->get('product/(:segment)', 'Product::show/$1');

// (:any) - Any characters
$routes->get('page/(:any)', 'Page::show/$1');

// Custom regex
$routes->get('products/([a-z]+)', 'Product::category/$1');
```

## Route Groups

```php
// Basic group
$routes->group('admin', function($routes) {
    $routes->get('dashboard', 'Admin::dashboard');
    $routes->get('users', 'Admin::users');
    $routes->get('settings', 'Admin::settings');
});
// Results in: /admin/dashboard, /admin/users, /admin/settings

// Group with namespace
$routes->group('api', ['namespace' => 'App\Controllers\Api'], function($routes) {
    $routes->get('users', 'UserController::index');
    $routes->get('users/(:num)', 'UserController::show/$1');
});

// Group with filters
$routes->group('admin', ['filter' => 'auth'], function($routes) {
    $routes->get('dashboard', 'Admin::dashboard');
});

// Nested groups
$routes->group('api', function($routes) {
    $routes->group('v1', function($routes) {
        $routes->resource('users');
    });
});
// Results in: /api/v1/users
```

## Resource Routes (RESTful)

Create full CRUD routes with one line:

```php
// Full resource routes
$routes->resource('photos');

// Equivalent to:
// GET    /photos           -> Photos::index
// GET    /photos/new       -> Photos::new
// GET    /photos/(:num)    -> Photos::show/$1
// GET    /photos/(:num)/edit -> Photos::edit/$1
// POST   /photos           -> Photos::create
// PUT    /photos/(:num)    -> Photos::update/$1
// PATCH  /photos/(:num)    -> Photos::update/$1
// DELETE /photos/(:num)    -> Photos::delete/$1

// Custom resource routes
$routes->resource('photos', [
    'controller' => 'Gallery',           // Custom controller name
    'namespace'  => 'App\Controllers\Api', // Custom namespace
    'except'     => ['new', 'edit'],     // Exclude some routes
    'only'       => ['index', 'show'],   // Only these routes
    'websafe'    => true,                // Allow GET for PUT/DELETE
]);

// API resource (no new/edit)
$routes->resource('photos', ['websafe' => false]);

// Additional resource routes
$routes->resource('photos', function($routes) {
    $routes->get('photos/(:num)/download', 'Photos::download/$1');
    $routes->post('photos/(:num)/share', 'Photos::share/$1');
});
```

## Presenter Routes

For view-based resources:

```php
$routes->presenter('photos');

// Creates routes for:
// index, show, new, create, edit, update, remove, delete
```

## Route Options

```php
// Custom HTTP verbs
$routes->get('products', 'Product::index');
$routes->post('products', 'Product::create');
$routes->put('products/(:num)', 'Product::update/$1');
$routes->patch('products/(:num)', 'Product::patch/$1');
$routes->delete('products/(:num)', 'Product::delete/$1');
$routes->options('products', 'Product::options');
$routes->head('products', 'Product::head');

// Route with filter
$routes->get('admin', 'Admin::index', ['filter' => 'auth']);

// Route with multiple filters
$routes->get('admin', 'Admin::index', ['filter' => ['auth', 'admin']]);

// Route with filter parameters
$routes->get('users', 'User::index', ['filter' => 'tokens:users-read']);

// Named routes
$routes->get('products', 'Product::index', ['as' => 'products']);
$routes->get('product/(:num)', 'Product::show/$1', ['as' => 'product-detail']);

// Generate URLs
$url = url_to('products');  // /products
$url = url_to('product-detail', 123);  // /product/123
```

## Auto Routing (Improved)

Automatically map URLs to controllers:

```php
// app/Config/Routes.php
$routes->setAutoRoute(true);

// URL: /products/show/123
// Maps to: App\Controllers\Products::show(123)

// URL: /api/v1/users
// Maps to: App\Controllers\Api\V1\Users::index()

// Requires controller:
// app/Controllers/Products.php
// app/Controllers/Api/V1/Users.php
```

## Redirect Routes

```php
// Simple redirect
$routes->addRedirect('old-page', 'new-page', 301);

// Redirect with placeholders
$routes->addRedirect('product/(:num)', 'products/detail/$1');

// Closure-based redirect
$routes->get('legacy', function() {
    return redirect()->to('/new-path')->with('message', 'Redirected');
});
```

## Environment-Specific Routes

```php
// Development only
if (ENVIRONMENT === 'development') {
    $routes->get('test', 'Test::index');
}

// CLI only
if (is_cli()) {
    $routes->cli('migrate', 'Migrate::index');
}
```

## Base Controllers

Extend `BaseController` for shared functionality:

```php
<?php

namespace App\Controllers;

use CodeIgniter\Controller;
use CodeIgniter\HTTP\RequestInterface;
use CodeIgniter\HTTP\ResponseInterface;
use Psr\Log\LoggerInterface;

class BaseController extends Controller
{
    protected $helpers = ['url', 'form'];
    
    public function initController(
        RequestInterface $request,
        ResponseInterface $response,
        LoggerInterface $logger
    ) {
        parent::initController($request, $response, $logger);
        
        // Preload models, libraries here
    }
}
```

## Controllers

```php
<?php

namespace App\Controllers;

class Product extends BaseController
{
    public function index()
    {
        // GET /products
    }
    
    public function show($id = null)
    {
        // GET /products/123
    }
    
    public function create()
    {
        // POST /products
        $data = $this->request->getPost();
        $data = $this->request->getJSON(true);
    }
    
    public function update($id = null)
    {
        // PUT /products/123
        $data = $this->request->getRawInput();
    }
    
    public function delete($id = null)
    {
        // DELETE /products/123
    }
}
```

## Request Handling

```php
// Get request data
$data = $this->request->getPost();      // POST data
$data = $this->request->getGet();       // GET data
$data = $this->request->getRawInput();  // PUT/PATCH raw input
$data = $this->request->getJSON(true);  // JSON input

// Get specific value
$name = $this->request->getPost('name');
$name = $this->request->getVar('name');  // Any method

// Check request method
if ($this->request->isAJAX()) { }
if ($this->request->is('get')) { }

// Get headers
$token = $this->request->getHeaderLine('Authorization');

// Get uploaded files
$file = $this->request->getFile('avatar');
```

## Filters

Filters process requests before/after controllers:

### Creating a Filter

```php
<?php

namespace App\Filters;

use CodeIgniter\Filters\FilterInterface;
use CodeIgniter\HTTP\RequestInterface;
use CodeIgniter\HTTP\ResponseInterface;
use CodeIgniter\HTTP\Response;

class AuthFilter implements FilterInterface
{
    public function before(RequestInterface $request, $arguments = null)
    {
        // Check authentication
        if (!auth()->loggedIn()) {
            return redirect()->to('/login');
        }
        
        // Check specific permission
        if (!auth()->user()->can($arguments[0] ?? '')) {
            return redirect()->to('/unauthorized');
        }
        
        // For API responses
        // return service('response')->setStatusCode(401)->setJSON(['error' => 'Unauthorized']);
    }
    
    public function after(RequestInterface $request, ResponseInterface $response, $arguments = null)
    {
        // Modify response after controller
        // Add headers, logging, etc.
    }
}
```

### Registering Filters

```php
// app/Config/Filters.php

public $aliases = [
    'auth'       => \App\Filters\AuthFilter::class,
    'csrf'       => \CodeIgniter\Filters\CSRF::class,
    'honeypot'   => \CodeIgniter\Filters\Honeypot::class,
    'invalidchars' => \CodeIgniter\Filters\InvalidChars::class,
    'secureheaders' => \CodeIgniter\Filters\SecureHeaders::class,
    'throttle'   => \CodeIgniter\Filters\PageCache::class, // Use Throttler
];

// Global filters (all routes)
public $globals = [
    'before' => [
        'csrf' => ['except' => ['api/*']],  // Exclude API routes
    ],
    'after' => [
        'secureheaders',
    ],
];

// Route-specific filters
public $filters = [
    'auth' => ['before' => ['admin/*', 'profile/*']],
    'throttle' => ['before' => ['api/*']],
];
```

### Filter Arguments

```php
// Route definition
$routes->get('admin', 'Admin::index', ['filter' => 'auth:admin']);

// In filter
public function before(RequestInterface $request, $arguments = null)
{
    // $arguments = ['admin']
    $requiredRole = $arguments[0] ?? 'user';
}
```

## Controller Attributes (PHP 8+)

```php
use CodeIgniter\Filters\Filter;

class Product extends BaseController
{
    #[Filter(['auth'], except: ['index', 'show'])]
    public function create() { }
    
    #[Filter(['admin'])]
    public function delete() { }
}
```

## Route Caching

```bash
# Enable route caching for production
php spark route:cache

# Clear route cache
php spark route:clear
```

## Best Practices

1. **Use defined routes** - More control than auto routing
2. **Group related routes** - Better organization
3. **Use resource routes** - For RESTful APIs
4. **Apply filters** - At group level when possible
5. **Name your routes** - For URL generation
6. **Use namespaces** - Organize controllers
7. **Version your API** - Via URL groups
8. **Document routes** - Use annotations or OpenAPI

## Related Skills

- **ci4-api-development** - RESTful controllers, ResponseTrait
- **ci4-shield-auth** - Authentication filters
- **ci4-security** - CSRF, security headers, rate limiting
- **ci4-configuration** - Routes config, environment setup
