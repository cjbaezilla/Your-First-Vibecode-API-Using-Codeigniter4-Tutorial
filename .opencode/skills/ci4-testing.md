# CodeIgniter 4 Testing

Skill for testing CodeIgniter 4 applications using PHPUnit, including unit tests, feature tests, database testing, and mocking.

## Overview

CI4 provides comprehensive testing support:
- **PHPUnit**: Industry-standard testing framework
- **Feature Tests**: HTTP request/response testing
- **Database Testing**: Database assertions and seeding
- **Fabricator**: Generate fake data for testing
- **Mocking**: Mock services and libraries

## Documentation Reference

- `/ci-userguide/testing/overview.html` - Testing Overview
- `/ci-userguide/testing/feature.html` - Feature Testing
- `/ci-userguide/testing/database.html` - Database Testing
- `/shield-docs/references/testing.md` - Shield Testing

## Test Setup

```bash
# PHPUnit is installed via Composer
vendor/bin/phpunit

# Run all tests
vendor/bin/phpunit

# Run specific test
vendor/bin/phpunit tests/app/Controllers/HomeTest.php

# Run with coverage
vendor/bin/phpunit --coverage-html coverage/

# Run specific test method
vendor/bin/phpunit --filter testIndex
```

## Test Directory Structure

```
tests/
├── _support/           # Test support files
│   ├── Database/       # Database test seeds
│   ├── Models/         # Model test cases
│   └── TestCase.php    # Base test case
├── app/
│   ├── Controllers/    # Controller tests
│   ├── Filters/        # Filter tests
│   ├── Libraries/      # Library tests
│   └── Models/         # Model tests
├── database/           # Database tests
├── unit/               # Unit tests
└── README.md
```

## Base Test Case

```php
<?php

namespace Tests\Support;

use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\Test\DatabaseTestTrait;

class TestCase extends CIUnitTestCase
{
    use DatabaseTestTrait;

    protected $refresh = true;       // Refresh database between tests
    protected $seed = 'TestSeeder';  // Run seeder before tests
    protected $basePath = ROOTPATH . 'app/Database';
    protected $namespace = 'App';
}
```

## Unit Testing

### Basic Unit Test

```php
<?php

namespace Tests\Unit;

use CodeIgniter\Test\CIUnitTestCase;
use App\Libraries\Calculator;

class CalculatorTest extends CIUnitTestCase
{
    protected Calculator $calculator;

    protected function setUp(): void
    {
        parent::setUp();
        $this->calculator = new Calculator();
    }

    public function testAdd()
    {
        $result = $this->calculator->add(2, 3);
        $this->assertEquals(5, $result);
    }

    public function testAddNegative()
    {
        $result = $this->calculator->add(-2, 3);
        $this->assertEquals(1, $result);
    }

    public function testDivideByZero()
    {
        $this->expectException(\InvalidArgumentException::class);
        $this->calculator->divide(10, 0);
    }
}
```

### Testing with Mocking

```php
<?php

namespace Tests\Unit;

use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\Test\Mock\MockSession;
use Config\Services;

class AuthTest extends CIUnitTestCase
{
    protected function setUp(): void
    {
        parent::setUp();
        
        // Mock session
        $session = new MockSession(new \Config\Session(), '127.0.0.1');
        Services::injectMock('session', $session);
    }

    public function testLoginWithMockSession()
    {
        $session = Services::session();
        $session->set('user_id', 1);
        
        $this->assertEquals(1, $session->get('user_id'));
    }
}
```

## Feature Testing (HTTP)

Feature tests simulate HTTP requests:

```php
<?php

namespace Tests\App\Controllers;

use CodeIgniter\Test\FeatureTestTrait;
use CodeIgniter\Test\CIUnitTestCase;

class HomeTest extends CIUnitTestCase
{
    use FeatureTestTrait;

    protected $basePath = ROOTPATH . 'app/Database';
    protected $namespace = 'App';

    public function testIndexPage()
    {
        $result = $this->get('/');
        
        $result->assertOK();
        $result->assertSee('Welcome to CodeIgniter');
    }

    public function testContactPage()
    {
        $result = $this->get('/contact');
        
        $result->assertOK();
        $result->assertSeeElement('form#contact');
    }
}
```

### API Testing

```php
<?php

namespace Tests\App\Controllers\Api;

use CodeIgniter\Test\FeatureTestTrait;
use CodeIgniter\Test\CIUnitTestCase;

class UserControllerTest extends CIUnitTestCase
{
    use FeatureTestTrait;

    protected $basePath = ROOTPATH . 'app/Database';
    protected $namespace = 'App';
    protected $seed = 'UserSeeder';

    public function testGetUsers()
    {
        $result = $this->get('api/users');
        
        $result->assertOK();
        $result->assertJSON();
        $result->assertJSONFragment(['username' => 'testuser']);
    }

    public function testCreateUser()
    {
        $result = $this->post('api/users', [
            'username' => 'newuser',
            'email'    => 'new@example.com',
            'password' => 'password123',
        ]);
        
        $result->assertStatus(201);
        $result->assertJSONFragment(['message' => 'User created']);
    }

    public function testUpdateUser()
    {
        $result = $this->put('api/users/1', [
            'email' => 'updated@example.com',
        ]);
        
        $result->assertOK();
    }

    public function testDeleteUser()
    {
        $result = $this->delete('api/users/1');
        
        $result->assertOK();
    }

    public function testGetUserNotFound()
    {
        $result = $this->get('api/users/99999');
        
        $result->assertStatus(404);
    }

    public function testCreateUserValidationError()
    {
        $result = $this->post('api/users', [
            'username' => '',  // Empty, should fail validation
        ]);
        
        $result->assertStatus(400);
        $result->assertJSONFragment(['error' => 'Validation Error']);
    }
}
```

### Testing with Authentication

```php
<?php

namespace Tests\App\Controllers;

use CodeIgniter\Test\FeatureTestTrait;
use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\Shield\Test\AuthenticationTesting;
use App\Entities\User;

class ProtectedControllerTest extends CIUnitTestCase
{
    use FeatureTestTrait;
    use AuthenticationTesting;

    protected $namespace = 'App';

    public function testProtectedRouteWithoutAuth()
    {
        $result = $this->get('admin/dashboard');
        
        $result->assertRedirectTo('/login');
    }

    public function testProtectedRouteWithAuth()
    {
        // Create and log in user
        $user = $this->createAuthUser();
        
        $result = $this->withSession([
            'user_id' => $user->id,
        ])->get('admin/dashboard');
        
        $result->assertOK();
    }

    public function testAdminRouteWithPermission()
    {
        $user = $this->createAuthUser([
            'username' => 'admin',
            'email'    => 'admin@example.com',
        ]);
        
        $user->addGroup('admin');
        
        $result = $this->actingAs($user)
            ->get('admin/users');
        
        $result->assertOK();
    }

    protected function createAuthUser(array $data = []): User
    {
        $userData = array_merge([
            'username' => 'testuser',
            'email'    => 'test@example.com',
            'password' => 'password123',
        ], $data);

        $users = auth()->getProvider();
        $user = new User($userData);
        $users->save($user);
        
        return $users->findById($users->getInsertID());
    }
}
```

## Database Testing

### Setting Up Database Tests

```php
<?php

namespace Tests\App\Models;

use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\Test\DatabaseTestTrait;
use App\Models\UserModel;

class UserModelTest extends CIUnitTestCase
{
    use DatabaseTestTrait;

    protected $migrate     = true;
    protected $migrateOnce = false;
    protected $refresh     = true;
    protected $seed        = 'TestSeeder';
    protected $seedOnce    = false;
    protected $basePath    = ROOTPATH . 'app/Database';
    protected $namespace   = 'App';

    protected UserModel $model;

    protected function setUp(): void
    {
        parent::setUp();
        $this->model = new UserModel();
    }

    public function testFindById()
    {
        $user = $this->model->find(1);
        
        $this->assertEquals('testuser', $user['username']);
    }

    public function testInsertUser()
    {
        $data = [
            'username' => 'newuser',
            'email'    => 'new@example.com',
            'password' => 'password123',
        ];
        
        $id = $this->model->insert($data);
        
        $this->seeInDatabase('users', ['username' => 'newuser']);
    }

    public function testUpdateUser()
    {
        $this->model->update(1, ['status' => 'inactive']);
        
        $this->seeInDatabase('users', [
            'id'     => 1,
            'status' => 'inactive',
        ]);
    }

    public function testDeleteUser()
    {
        $this->model->delete(1);
        
        $this->dontSeeInDatabase('users', ['id' => 1]);
    }

    public function testValidationFails()
    {
        $data = [
            'username' => '',  // Empty, should fail
        ];
        
        $result = $this->model->insert($data);
        
        $this->assertFalse($result);
        $this->assertArrayHasKey('username', $this->model->errors());
    }
}
```

### Database Assertions

```php
// Check record exists
$this->seeInDatabase('users', [
    'email' => 'test@example.com',
    'status' => 'active',
]);

// Check record does not exist
$this->dontSeeInDatabase('users', [
    'email' => 'nonexistent@example.com',
]);

// Check number of records
$this->seeNumRecords(5, 'users', ['status' => 'active']);

// Get record from database
$row = $this->grabFromDatabase('users', 'username', ['id' => 1]);
$this->assertEquals('testuser', $row);

// Check if has table
$this->hasTable('users');
```

### Test Seeders

```php
<?php

namespace Tests\Support\Database\Seeds;

use CodeIgniter\Database\Seeder;

class TestSeeder extends Seeder
{
    public function run()
    {
        $data = [
            [
                'id'       => 1,
                'username' => 'testuser',
                'email'    => 'test@example.com',
                'status'   => 'active',
            ],
            [
                'id'       => 2,
                'username' => 'admin',
                'email'    => 'admin@example.com',
                'status'   => 'active',
            ],
        ];

        $this->db->table('users')->insertBatch($data);
    }
}
```

## Fabricator (Fake Data)

Generate test data with Faker:

```php
<?php

namespace Tests\App\Models;

use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\Test\Fabricator;
use App\Models\UserModel;
use App\Entities\User;

class UserModelFabricatorTest extends CIUnitTestCase
{
    protected UserModel $model;

    protected function setUp(): void
    {
        parent::setUp();
        $this->model = new UserModel();
    }

    public function testCreateWithFabricator()
    {
        $fabricator = new Fabricator($this->model);
        
        // Generate single fake user
        $user = $fabricator->make();
        
        // Generate and save
        $user = $fabricator->create();
        
        $this->assertInstanceOf(User::class, $user);
        $this->assertNotEmpty($user->username);
    }

    public function testCreateMultipleWithFabricator()
    {
        $fabricator = new Fabricator($this->model);
        
        // Generate 10 users
        $users = $fabricator->make(10);
        
        $this->assertCount(10, $users);
        $this->assertContainsOnlyInstancesOf(User::class, $users);
    }
}
```

### Custom Fabricator Templates

```php
<?php

namespace App\Models;

use CodeIgniter\Model;
use Faker\Generator;

class UserModel extends Model
{
    // ... model code ...

    public function fake(Generator &$faker)
    {
        return [
            'username' => $faker->userName,
            'email'    => $faker->email,
            'password' => password_hash('password123', PASSWORD_DEFAULT),
            'status'   => 'active',
        ];
    }
}
```

## HTTP Response Assertions

```php
// Status codes
$result->assertOK();                    // 200
$result->assertStatus(201);             // Any status
$result->assertRedirect();              // Any redirect
$result->assertRedirectTo('/login');    // Specific redirect
$result->assertNotRedirect();

// Content
$result->assertSee('Welcome');
$result->assertDontSee('Error');
$result->assertSeeElement('nav.navbar');
$result->assertDontSeeElement('div.error');
$result->assertClickable('Submit');

// JSON
$result->assertJSON();
$result->assertJSONFragment(['status' => 'success']);
$result->assertJSONExact(['id' => 1, 'name' => 'Test']);

// Headers
$result->assertHeader('Content-Type', 'application/json');
$result->assertCookie('session', 'value');
```

## Testing Filters

```php
<?php

namespace Tests\App\Filters;

use CodeIgniter\Test\CIUnitTestCase;
use CodeIgniter\HTTP\Request;
use CodeIgniter\HTTP\Response;
use App\Filters\AuthFilter;

class AuthFilterTest extends CIUnitTestCase
{
    protected AuthFilter $filter;

    protected function setUp(): void
    {
        parent::setUp();
        $this->filter = new AuthFilter();
    }

    public function testFilterRedirectsWhenNotLoggedIn()
    {
        $request = new Request(new \Config\App());
        
        $result = $this->filter->before($request, null);
        
        $this->assertInstanceOf(Response::class, $result);
        $this->assertEquals(302, $result->getStatusCode());
    }
}
```

## Testing with Events

```php
public function testEventIsTriggered()
{
    $triggered = false;
    
    Events::on('userCreated', function() use (&$triggered) {
        $triggered = true;
    });
    
    $this->model->insert(['username' => 'test']);
    
    $this->assertTrue($triggered);
}
```

## Test Configuration

```xml
<!-- phpunit.xml.dist -->
<phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         bootstrap="vendor/autoload.php"
         colors="true"
>
    <testsuites>
        <testsuite name="app">
            <directory>./tests/app</directory>
        </testsuite>
        <testsuite name="unit">
            <directory>./tests/unit</directory>
        </testsuite>
    </testsuites>

    <coverage processUncoveredFiles="true">
        <include>
            <directory suffix=".php">./app</directory>
        </include>
        <exclude>
            <directory>./app/Views</directory>
            <directory>./app/Config</directory>
        </exclude>
    </coverage>
</phpunit>
```

## Testing Best Practices

1. **Test one thing at a time** - Each test should verify one behavior
2. **Use descriptive names** - Test names should explain what they test
3. **Arrange-Act-Assert** - Structure tests clearly
4. **Use factories/fabricators** - For test data generation
5. **Mock external services** - Don't hit real APIs in tests
6. **Clean up after tests** - Use database transactions
7. **Test edge cases** - Empty inputs, nulls, boundaries
8. **Run tests often** - Integrate into development workflow

## Related Skills

- **ci4-models-database** - Model testing, database assertions
- **ci4-api-development** - API endpoint testing
- **ci4-shield-auth** - Authentication testing
- **ci4-security** - Security testing
- **ci4-configuration** - Test environment config
