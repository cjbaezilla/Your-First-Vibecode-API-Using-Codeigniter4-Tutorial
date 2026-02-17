# CodeIgniter 4 Models and Database

Skill for working with CodeIgniter 4 models, entities, query builder, migrations, and database operations.

## Overview

CI4 provides robust database tools:
- **Model Class**: Active Record pattern with validation
- **Entities**: Map database rows to objects
- **Query Builder**: Secure, chainable query construction
- **Migrations**: Version-controlled database schema
- **Seeds**: Populate database with test data

## Documentation Reference

- `/ci-userguide/models/model.html` - Using CodeIgniter's Model
- `/ci-userguide/models/entities.html` - Entity Classes
- `/ci-userguide/database/query_builder.html` - Query Builder
- `/ci-userguide/dbmgmt/migration.html` - Database Migrations
- `/ci-userguide/database/configuration.html` - Database Config

## Database Configuration

Configure in `app/Config/Database.php` or `.env`:

```php
// .env
database.default.hostname = localhost
database.default.database = ci_api_db
database.default.username = root
database.default.password = secret
database.default.DBDriver = MySQLi
```

```php
// app/Config/Database.php
public array $default = [
    'DSN'      => '',
    'hostname' => 'localhost',
    'username' => 'root',
    'password' => '',
    'database' => 'ci_api_db',
    'DBDriver' => 'MySQLi',
    'DBPrefix' => '',
    'pConnect' => false,
    'DBDebug'  => true,  // Set false in production
    'charset'  => 'utf8mb4',
    'DBCollat' => 'utf8mb4_general_ci',
];
```

## Creating Models

```bash
# Generate model
php spark make:model Models/UserModel
```

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class UserModel extends Model
{
    protected $table            = 'users';
    protected $primaryKey       = 'id';
    protected $useAutoIncrement = true;
    protected $returnType       = 'array';  // 'array' or 'object' or Entity class
    protected $useSoftDeletes   = true;
    protected $protectFields    = true;
    protected $allowedFields    = ['username', 'email', 'status'];

    // Dates
    protected $useTimestamps = true;
    protected $dateFormat    = 'datetime';
    protected $createdField  = 'created_at';
    protected $updatedField  = 'updated_at';
    protected $deletedField  = 'deleted_at';

    // Validation
    protected $validationRules    = [
        'username' => 'required|min_length[3]|max_length[20]|is_unique[users.username]',
        'email'    => 'required|valid_email|is_unique[users.email]',
    ];
    protected $validationMessages = [
        'username' => [
            'required'   => 'Username is required',
            'is_unique'  => 'Username already exists',
        ],
    ];
    protected $skipValidation     = false;

    // Callbacks
    protected $allowCallbacks = true;
    protected $beforeInsert   = ['hashPassword'];
    protected $afterInsert    = [];
    protected $beforeUpdate   = [];
    protected $afterUpdate    = [];
    protected $beforeFind     = [];
    protected $afterFind      = [];
    protected $beforeDelete   = [];
    protected $afterDelete    = [];

    protected function hashPassword(array $data)
    {
        if (isset($data['data']['password'])) {
            $data['data']['password'] = password_hash(
                $data['data']['password'], 
                PASSWORD_DEFAULT
            );
        }
        return $data;
    }
}
```

## Using Models

```php
$userModel = new UserModel();

// Find by ID
$user = $userModel->find($id);

// Find all
$users = $userModel->findAll();
$users = $userModel->findAll(10, 20);  // Limit 10, offset 20

// Find with where
$user = $userModel->where('email', 'john@example.com')->first();

// Insert
$data = [
    'username' => 'john_doe',
    'email'    => 'john@example.com',
];
$userModel->insert($data);
$id = $userModel->getInsertID();

// Update
$userModel->update($id, ['status' => 'active']);

// Delete (soft delete if enabled)
$userModel->delete($id);

// Hard delete (even with soft deletes)
$userModel->delete($id, true);

// Count
$count = $userModel->countAll();
$count = $userModel->where('status', 'active')->countAllResults();
```

## Entity Classes

Entities map database rows to objects:

```bash
# Generate entity
php spark make:entity Entities/User
```

```php
<?php

namespace App\Entities;

use CodeIgniter\Entity\Entity;

class User extends Entity
{
    protected $datamap = [];
    protected $dates   = ['created_at', 'updated_at', 'deleted_at'];
    protected $casts   = [
        'id'       => 'integer',
        'status'   => 'string',
        'settings' => 'json',
        'is_admin' => 'boolean',
    ];

    // Custom getter
    public function getFullName()
    {
        return $this->attributes['first_name'] . ' ' . $this->attributes['last_name'];
    }

    // Custom setter
    public function setPassword(string $password)
    {
        $this->attributes['password'] = password_hash($password, PASSWORD_DEFAULT);
        return $this;
    }

    // Custom method
    public function isActive(): bool
    {
        return $this->attributes['status'] === 'active';
    }
}
```

Using entities in models:

```php
class UserModel extends Model
{
    protected $returnType = User::class;  // Entity class
}

// Usage
$user = $userModel->find($id);
echo $user->fullName;  // Uses custom getter
$user->password = 'newpassword';  // Uses custom setter
```

## Query Builder

### Basic Queries

```php
$db = \Config\Database::connect();
$builder = $db->table('users');

// Select
$builder->select('id, username, email');
$results = $builder->get()->getResultArray();

// Where
$builder->where('status', 'active');
$builder->where('age >', 18);
$builder->where(['status' => 'active', 'verified' => 1]);

// OR Where
$builder->where('status', 'active')
        ->orWhere('role', 'admin');

// Where In
$builder->whereIn('role', ['admin', 'moderator']);

// Like
$builder->like('username', 'john', 'both');  // %john%
$builder->like('email', '@gmail.com', 'before');

// Joins
$builder->join('roles', 'users.role_id = roles.id');
$builder->join('profiles', 'profiles.user_id = users.id', 'left');

// Order By
$builder->orderBy('created_at', 'DESC');

// Group By
$builder->groupBy('status');

// Limit
$builder->limit(10, 20);  // Limit 10, offset 20

// Get results
$query = $builder->get();
$results = $query->getResult();        // Array of objects
$results = $query->getResultArray();   // Array of arrays
$row = $query->getRow();               // Single object
$row = $query->getRowArray();          // Single array
```

### Method Chaining

```php
$results = $db->table('users')
    ->select('users.*, roles.name as role_name')
    ->join('roles', 'users.role_id = roles.id')
    ->where('users.status', 'active')
    ->where('users.created_at >', date('Y-m-d', strtotime('-30 days')))
    ->orderBy('users.created_at', 'DESC')
    ->limit(10)
    ->get()
    ->getResult();
```

### Aggregate Functions

```php
$builder = $db->table('users');

$count = $builder->countAllResults();
$count = $builder->where('status', 'active')->countAllResults();

$sum = $builder->selectSum('amount')->get()->getRow()->amount;
$avg = $builder->selectAvg('rating')->get()->getRow()->rating;
$max = $builder->selectMax('created_at')->get()->getRow()->created_at;
$min = $builder->selectMin('created_at')->get()->getRow()->created_at;
```

### Insert

```php
$data = [
    'username' => 'john_doe',
    'email'    => 'john@example.com',
];

$db->table('users')->insert($data);
$insertId = $db->insertID();

// Batch insert
$data = [
    ['username' => 'user1', 'email' => 'user1@test.com'],
    ['username' => 'user2', 'email' => 'user2@test.com'],
];
$db->table('users')->insertBatch($data);
```

### Update

```php
$db->table('users')
    ->where('id', $id)
    ->update(['status' => 'active']);

// Update batch
$data = [
    ['id' => 1, 'status' => 'active'],
    ['id' => 2, 'status' => 'inactive'],
];
$db->table('users')->updateBatch($data, 'id');
```

### Delete

```php
$db->table('users')->where('id', $id)->delete();

// Delete all (be careful!)
$db->table('users')->emptyTable();

// Truncate
$db->table('users')->truncate();
```

## Database Migrations

Migrations version-control your database schema:

```bash
# Create migration
php spark make:migration CreateUsersTable

# Run all pending migrations
php spark migrate

# Run specific namespace
php spark migrate --all

# Rollback last migration
php spark migrate:rollback

# Rollback all
php spark migrate:rollback --all

# Status
php spark migrate:status

# Refresh (rollback all + migrate)
php spark migrate:refresh
```

### Migration Example

```php
<?php

namespace App\Database\Migrations;

use CodeIgniter\Database\Migration;

class CreateUsersTable extends Migration
{
    public function up()
    {
        $this->forge->addField([
            'id' => [
                'type'           => 'INT',
                'constraint'     => 11,
                'unsigned'       => true,
                'auto_increment' => true,
            ],
            'username' => [
                'type'       => 'VARCHAR',
                'constraint' => '100',
                'unique'     => true,
            ],
            'email' => [
                'type'       => 'VARCHAR',
                'constraint' => '255',
                'unique'     => true,
            ],
            'password' => [
                'type'       => 'VARCHAR',
                'constraint' => '255',
            ],
            'status' => [
                'type'       => 'ENUM',
                'constraint' => ['active', 'inactive', 'banned'],
                'default'    => 'inactive',
            ],
            'created_at' => [
                'type' => 'DATETIME',
                'null' => true,
            ],
            'updated_at' => [
                'type' => 'DATETIME',
                'null' => true,
            ],
            'deleted_at' => [
                'type' => 'DATETIME',
                'null' => true,
            ],
        ]);
        
        $this->forge->addKey('id', true);
        $this->forge->addKey('created_at');
        $this->forge->createTable('users');
    }

    public function down()
    {
        $this->forge->dropTable('users');
    }
}
```

### Forge Methods

```php
// Create table
$this->forge->addField([...]);
$this->forge->addKey('id', true);  // Primary key
$this->forge->addKey('email');      // Index
$this->forge->addUniqueKey('username');  // Unique index
$this->forge->addForeignKey('user_id', 'users', 'id');
$this->forge->createTable('products');

// Modify table
$this->forge->addColumn('users', [
    'phone' => [
        'type'       => 'VARCHAR',
        'constraint' => '20',
        'null'       => true,
    ],
]);
$this->forge->modifyColumn('users', [...]);
$this->forge->dropColumn('users', 'phone');

// Drop table
$this->forge->dropTable('users');
$this->forge->dropTable('users', true);  // If exists
```

## Database Seeding

Seeders populate the database with test data:

```bash
# Create seeder
php spark make:seeder UserSeeder

# Run seeder
php spark db:seed UserSeeder
```

```php
<?php

namespace App\Database\Seeds;

use CodeIgniter\Database\Seeder;
use Faker\Factory;

class UserSeeder extends Seeder
{
    public function run()
    {
        $faker = Factory::create();
        
        $data = [];
        for ($i = 0; $i < 100; $i++) {
            $data[] = [
                'username' => $faker->userName,
                'email'    => $faker->email,
                'password' => password_hash('password123', PASSWORD_DEFAULT),
                'status'   => 'active',
            ];
        }
        
        $this->db->table('users')->insertBatch($data);
    }
}
```

## Transactions

```php
$db = \Config\Database::connect();

// Manual transaction
$db->transBegin();

try {
    $db->table('users')->insert($userData);
    $userId = $db->insertID();
    
    $db->table('profiles')->insert([
        'user_id' => $userId,
        'bio'     => 'New user',
    ]);
    
    $db->transCommit();
} catch (\Exception $e) {
    $db->transRollback();
    throw $e;
}

// Automatic transaction (simpler)
$db->transStart();
$db->table('users')->insert($data1);
$db->table('profiles')->insert($data2);
$db->transComplete();

if ($db->transStatus() === false) {
    // Transaction failed
}
```

## Best Practices

1. **Use Query Builder** - Prevents SQL injection
2. **Validate input** - Use model validation rules
3. **Use transactions** - For multi-table operations
4. **Index foreign keys** - For better performance
5. **Soft deletes** - Don't hard delete data
6. **Use migrations** - Version control your schema
7. **Seed test data** - For development/testing
8. **Eager loading** - Use `with()` to avoid N+1

## Related Skills

- **ci4-security** - SQL injection prevention, data validation
- **ci4-api-development** - API responses with models
- **ci4-shield-auth** - User model, authentication data
- **ci4-testing** - Database testing, factories
- **ci4-configuration** - Database config, environments
