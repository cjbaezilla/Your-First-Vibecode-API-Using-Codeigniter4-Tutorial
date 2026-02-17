# CodeIgniter 4 API Development

Skill for building RESTful APIs in CodeIgniter 4 using ResponseTrait, ResourceController, and content negotiation.

## Overview

CodeIgniter 4 provides powerful tools for building REST APIs:
- **ResponseTrait**: Consistent API responses with proper HTTP status codes
- **ResourceController**: Pre-built CRUD controller for RESTful resources
- **Content Negotiation**: Automatic format detection (JSON, XML)
- **API Transformers**: Transform data before output

## Documentation Reference

- `/ci-userguide/guides/api/index.html` - REST API Guide
- `/ci-userguide/incoming/restful.html` - RESTful Resource Handling
- `/ci-userguide/outgoing/api_responses.html` - API ResponseTrait
- `/ci-userguide/outgoing/api_transformers.html` - API Resources

## ResponseTrait Methods

Always use `CodeIgniter\API\ResponseTrait` in API controllers:

```php
namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;
use CodeIgniter\API\ResponseTrait;

class UserController extends ResourceController
{
    use ResponseTrait;

    // Available response methods
    public function index()
    {
        return $this->respond($data);               // 200 OK
        return $this->respondCreated($data);        // 201 Created
        return $this->respondUpdated($data);        // 200 OK (update)
        return $this->respondDeleted();             // 200 OK (delete)
        return $this->respondNoContent();           // 204 No Content
        
        // Error responses
        return $this->failUnauthorized('Invalid credentials');
        return $this->failForbidden('Access denied');
        return $this->failNotFound('Resource not found');
        return $this->failValidationErrors($errors);
        return $this->failServerError('Server error');
    }
}
```

## ResourceController

The `ResourceController` provides standard RESTful CRUD operations:

```php
namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class ProductController extends ResourceController
{
    protected $modelName = 'App\Models\ProductModel';
    protected $format = 'json';

    // GET /products - List all
    public function index()
    {
        return $this->respond($this->model->findAll());
    }

    // GET /products/{id} - Show one
    public function show($id = null)
    {
        $product = $this->model->find($id);
        if (!$product) {
            return $this->failNotFound('Product not found');
        }
        return $this->respond($product);
    }

    // POST /products - Create
    public function create()
    {
        $data = $this->request->getJSON(true);
        
        if (!$this->model->insert($data)) {
            return $this->failValidationErrors($this->model->errors());
        }
        
        return $this->respondCreated([
            'id' => $this->model->insertID(),
            'message' => 'Product created'
        ]);
    }

    // PUT/PATCH /products/{id} - Update
    public function update($id = null)
    {
        $data = $this->request->getJSON(true);
        
        if (!$this->model->update($id, $data)) {
            return $this->failValidationErrors($this->model->errors());
        }
        
        return $this->respondUpdated(['message' => 'Product updated']);
    }

    // DELETE /products/{id} - Delete
    public function delete($id = null)
    {
        if (!$this->model->find($id)) {
            return $this->failNotFound('Product not found');
        }
        
        $this->model->delete($id);
        return $this->respondDeleted(['message' => 'Product deleted']);
    }
}
```

## Content Negotiation

CI4 automatically detects desired response format:

```php
// Client sends: Accept: application/json
// CI4 responds with JSON

// Client sends: Accept: application/xml
// CI4 responds with XML

// Default format (set in controller)
protected $format = 'json';  // or 'xml'

// Force format via URL extension
// GET /products.json
// GET /products.xml
```

## API Response Format

Standard response structure:

```php
// Success response (200 OK)
{
    "status": 200,
    "error": null,
    "messages": {
        "success": "Products retrieved"
    },
    "data": [
        {"id": 1, "name": "Product 1"},
        {"id": 2, "name": "Product 2"}
    ]
}

// Error response (400 Bad Request)
{
    "status": 400,
    "error": "Validation Error",
    "messages": {
        "name": "The name field is required.",
        "price": "The price must be a number."
    },
    "data": null
}
```

## API Transformers

Transform data before sending to client:

```php
namespace App\Transformers;

use CodeIgniter\Entity\Entity;
use CodeIgniter\RESTful\Transformer;

class ProductTransformer extends Transformer
{
    public function transform(Entity $product): array
    {
        return [
            'id' => $product->id,
            'name' => $product->name,
            'price' => number_format($product->price, 2),
            'image_url' => base_url('uploads/' . $product->image),
            'created_at' => $product->created_at->format('c'),
        ];
    }
}

// Use in controller
$transformer = new ProductTransformer();
return $this->respond($transformer->transform($product));
```

## API Versioning

Version your APIs via URL:

```php
// Routes.php
$routes->group('api/v1', function($routes) {
    $routes->resource('users');
});

$routes->group('api/v2', function($routes) {
    $routes->resource('users');
});

// Controllers
// app/Controllers/Api/V1/UserController.php
// app/Controllers/Api/V2/UserController.php
```

## Pagination

Paginate API responses:

```php
public function index()
{
    $perPage = $this->request->getGet('per_page') ?? 20;
    $page = $this->request->getGet('page') ?? 1;
    
    $products = $this->model->paginate($perPage, 'default', $page);
    
    return $this->respond([
        'data' => $products,
        'pagination' => [
            'current_page' => $page,
            'per_page' => $perPage,
            'total' => $this->model->countAll(),
        ]
    ]);
}
```

## Rate Limiting (Throttling)

Apply rate limiting to API endpoints (see ci4-security for details):

```php
// In Filters.php
public $filters = [
    'throttle' => ['before' => ['api/*']],
];
```

## API Authentication

Integrate Shield authentication (see ci4-shield-auth):

```php
// In Routes.php
$routes->group('api', ['filter' => 'tokens'], function($routes) {
    $routes->resource('users');
});
```

## Error Handling

Handle exceptions consistently:

```php
use CodeIgniter\Exceptions\PageNotFoundException;

public function show($id = null)
{
    try {
        $product = $this->model->find($id);
        if (!$product) {
            throw new PageNotFoundException('Product not found');
        }
        return $this->respond($product);
    } catch (PageNotFoundException $e) {
        return $this->failNotFound($e->getMessage());
    } catch (\Exception $e) {
        log_message('error', $e->getMessage());
        return $this->failServerError('Internal server error');
    }
}
```

## Best Practices

1. **Always validate input** - Use model validation or Validation library
2. **Return proper HTTP codes** - Use ResponseTrait methods
3. **Consistent response format** - Same structure for success/error
4. **Use transformers** - Don't expose raw database data
5. **Implement pagination** - For large datasets
6. **Add rate limiting** - Prevent abuse
7. **Version your API** - Support multiple versions
8. **Document your API** - Use OpenAPI/Swagger

## Related Skills

- **ci4-shield-auth** - Authentication and authorization
- **ci4-routing-controllers** - Routing and controller setup
- **ci4-models-database** - Models and data handling
- **ci4-security** - Validation, rate limiting, security headers
- **ci4-configuration** - API config, CORS settings
