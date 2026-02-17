# LaunchPad API

**A Production-Ready API Foundation Built with Vibe Coding**

Built in days, not months. Documented for entrepreneurs, developers, and AI assistants.

---

## What is This?

**LaunchPad API** is a complete, production-ready REST API foundation featuring authentication, authorization, and best practices—built using our "Vibe Coding" methodology alongside AI assistance.

This isn't just another boilerplate. It's a documented journey showing how entrepreneurs can build professional backends without hiring expensive developers or drowning in complexity.

### Key Features

✅ **Complete Authentication System** - Registration, login, password reset, API tokens, HMAC  
✅ **Role-Based Authorization** - Groups and permissions (admin, user, etc.)  
✅ **RESTful API Structure** - Proper HTTP methods, status codes, JSON responses  
✅ **Security Hardened** - CSRF protection, XSS filtering, rate limiting, secure headers  
✅ **Database Ready** - Migrations, seeders, query builder, model relationships  
✅ **Development Tools** - Local server, code generators, testing framework  
✅ **Comprehensive Documentation** - Every decision explained with rationale  

---

## Documentation Structure

This project follows a dual-documentation approach:

### 📖 article.md - The "Why"
**Start here if you're new!**

Our comprehensive guide explaining:
- The Vibe Coding methodology
- Technical decisions and rationale
- PHP vs Node.js for entrepreneurs
- Cost comparisons and hosting options
- Complete walkthrough of how we built this
- Code examples for beginners

**Read it like:** A tutorial from a friend who's been there

### 🛠️ AGENTS.md - The "How"
**Reference this during development**

Technical reference containing:
- Common commands and CLI tools
- Code standards and patterns
- Configuration file references
- Security checklists
- Troubleshooting guides

**Read it like:** A technical manual for your team

### 🧠 .opencode/skills/*.md - AI Knowledge
**Context for AI assistants**

Seven skill files that teach AI about our stack:
1. `ci4-api-development` - REST API patterns
2. `ci4-shield-auth` - Authentication & authorization
3. `ci4-routing-controllers` - Routing and controllers
4. `ci4-models-database` - Database operations
5. `ci4-security` - Security best practices
6. `ci4-configuration` - Configuration management
7. `ci4-testing` - Testing methodologies

---

## Quick Start

### Prerequisites

- PHP 8.2 or higher
- Composer (PHP package manager)
- MySQL or SQLite (MySQL recommended for production)
- A code editor (VS Code recommended)

### Installation

```bash
# Clone or download the project
git clone [your-repo-url] launchpad-api
cd launchpad-api

# Install dependencies
composer install

# Copy environment file
cp env .env

# Edit .env with your database credentials
# For SQLite (development): database.default.database = ../writable/database.sqlite
# For MySQL: configure hostname, database, username, password

# Run database migrations
php spark migrate --all

# Start development server
php spark serve
```

Visit `http://localhost:8080` - You should see the CodeIgniter welcome page!

---

## The Vibe Coding Methodology

This project was built using our 3-step approach:

### 1️⃣ Download Documentation Locally
We downloaded the complete CodeIgniter 4 user guide and Shield authentication docs into the project. This ensures our AI assistant gives accurate, version-specific advice.

**Location:** `ci-userguide/` and `shield-docs/`

### 2️⃣ AI Analyzes and Creates Skills
We trained OpenCode AI on our local documentation. It created 7 skill files that teach the AI about our specific tech stack, ensuring consistent, expert-level assistance.

**Location:** `.opencode/skills/`

### 3️⃣ Install Libraries with Composer
Instead of writing authentication from scratch (weeks of work), we ran:
```bash
composer require codeigniter4/shield
```

Five minutes later, we had a complete authentication system.

**Read `article.md` for the full story!**

---

## Tech Stack

| Component | Purpose | Why We Chose It |
|-----------|---------|-----------------|
| **PHP 8.2+** | Programming language | Fast, stable, runs on cheap hosting |
| **CodeIgniter 4** | Web framework | Lightweight, excellent docs, API-focused |
| **Shield** | Authentication | Official CI4 solution, multiple auth methods |
| **Composer** | Package manager | One-command installs, automatic updates |
| **MySQL/SQLite** | Database | Universal support, easy deployment |
| **OpenCode AI** | Coding assistant | Context-aware, trained on our docs |

### Why PHP + Shared Hosting?

| Hosting Type | Monthly Cost | Yearly Cost | Complexity |
|-------------|-------------|-------------|------------|
| PHP Shared Hosting | $3-10 | $36-120 | Upload files, done |
| VPS for Node/Python | $20-50 | $240-600 | Server setup, monitoring |
| Managed VPS | $50-150 | $600-1800 | Simpler but expensive |

**Savings:** $564 - $1,680 per year

PHP runs on shared hosting (just upload files). Node.js/Python generally need VPS (server management required).

See `article.md` for the full cost breakdown.

---

## Project Structure

```
launchpad-api/
├── 📖 article.md              # Comprehensive guide (START HERE!)
├── 🛠️ AGENTS.md               # Technical reference
├── 📋 README.md               # This file
├──
├── 📁 app/                    # Application code
│   ├── Config/               # Configuration files
│   ├── Controllers/          # API controllers
│   ├── Models/               # Data models
│   ├── Filters/              # Authentication filters
│   └── Database/             # Migrations and seeds
│
├── 📁 ci-userguide/          # CodeIgniter 4 docs (local copy)
├── 📁 shield-docs/           # Shield auth docs (local copy)
├── 📁 .opencode/             # AI configuration
│   └── skills/               # AI knowledge files
│
├── 📁 public/                # Web root (index.php)
├── 📁 system/                # Framework core
├── 📁 vendor/                # Composer dependencies
└── 📁 writable/              # Logs, cache, uploads
```

---

## Common Commands

### Development

```bash
# Start development server
php spark serve

# Clear cache
php spark cache:clear

# Generate code
php spark make:controller Api/UserController
php spark make:model Models/UserModel
php spark make:migration create_users_table
```

### Database

```bash
# Run all migrations
php spark migrate --all

# Rollback last migration
php spark migrate:rollback

# Seed database with test data
php spark db:seed DatabaseSeeder
```

### Authentication (Shield)

```bash
# Create new user
php spark shield:user create

# List all users
php spark shield:user list

# Add user to group
php spark shield:user addgroup

# Manage HMAC keys
php spark shield:hmac reencrypt
```

### Testing

```bash
# Run all tests
vendor/bin/phpunit

# Run with coverage
vendor/bin/phpunit --coverage-html coverage/
```

See `AGENTS.md` for complete command reference.

---

## Code Example

Here's what a protected API endpoint looks like:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class UserController extends ResourceController
{
    protected $modelName = 'App\Models\UserModel';
    protected $format = 'json';

    // GET /api/users
    public function index()
    {
        $users = $this->model->findAll();
        return $this->respond(['status' => 200, 'data' => $users]);
    }

    // GET /api/users/{id}
    public function show($id = null)
    {
        $user = $this->model->find($id);
        
        if (!$user) {
            return $this->failNotFound('User not found');
        }
        
        return $this->respond(['status' => 200, 'data' => $user]);
    }
}
```

**Protect the route:**
```php
// routes.php
$routes->group('api', ['filter' => 'tokens'], function($routes) {
    $routes->resource('users');
});
```

That's it! One line protects all user endpoints with token authentication.

See `article.md` for more examples and detailed explanations.

---

## Documentation Philosophy

Every technical decision in this project is documented using this format:

```markdown
## Decision: [What we decided]

**Date**: [When decided]
**Context**: [What led to this]
**Options Considered**:
- Option A: [description]
- Option B: [description]

**Decision**: We chose [Option] because [reasoning]

**Trade-offs**:
- Pros: [benefits]
- Cons: [drawbacks]

**Reversible?**: [Yes/No]
```

This ensures:
- We remember why we made choices
- New team members understand the codebase
- AI assistants give consistent advice
- We can evaluate decisions later

See `article.md` for examples of documented decisions.

---

## Learning Resources

### For Entrepreneurs (Non-Technical)

1. **Read `article.md`** - Complete guide with explanations
2. **Understand the costs** - Hosting comparison tables
3. **Follow the methodology** - 3-step Vibe Coding process
4. **Start small** - Build a simple feature first

### For Developers

1. **Read `AGENTS.md`** - Technical reference
2. **Study the skills** - `.opencode/skills/*.md`
3. **Review the code** - `app/Controllers/Api/`
4. **Check decisions** - Documented in `article.md`

### Official Documentation

- **CodeIgniter 4**: `ci-userguide/` (local) or https://codeigniter.com/user_guide/
- **Shield Auth**: `shield-docs/` (local) or https://shield.codeigniter.com/
- **PHP**: https://www.php.net/docs.php

---

## Contributing

This is a learning project built with Vibe Coding. We welcome:

- Questions and clarifications
- Suggestions for better documentation
- Bug reports (with context)
- Improvements to the methodology

**Before contributing:**
1. Read `article.md` to understand our approach
2. Check `AGENTS.md` for technical standards
3. Document your reasoning using our decision format

---

## Support

### Getting Help

1. **Check the docs first**
   - `article.md` for methodology questions
   - `AGENTS.md` for technical issues
   - `ci-userguide/` for CodeIgniter specifics

2. **Ask the AI**
   - OpenCode is trained on our documentation
   - Reference specific skill files for context

3. **Community**
   - CodeIgniter Forum: https://forum.codeigniter.com
   - PHP Help: https://www.reddit.com/r/PHPhelp

### Common Issues

**"Page Not Found" errors:**
- Check `app/Config/Routes.php`
- Ensure you're accessing via `http://localhost:8080` (not `public/`)

**Database connection errors:**
- Verify `.env` configuration
- Run `php spark migrate --all`
- Check MySQL is running

**Authentication not working:**
- Verify Shield setup: `php spark shield:setup`
- Check filters in `app/Config/Filters.php`
- Ensure tokens haven't expired

See `AGENTS.md` troubleshooting section for more.

---

## What's Next?

### Immediate Next Steps

1. ✅ Read `article.md` completely
2. ✅ Set up local environment
3. ✅ Install dependencies with Composer
4. ✅ Run migrations
5. ✅ Test the API with Postman or curl
6. ✅ Build your first feature

### Future Enhancements

- [ ] API documentation with Swagger/OpenAPI
- [ ] Frontend integration examples
- [ ] Deployment guides (shared hosting, VPS)
- [ ] Video tutorial series
- [ ] Advanced features (webhooks, notifications)

## About Vibe Coding

Vibe Coding is the art of building software alongside AI, not against it. It's about:

- **Leveraging documentation** - Give AI context for better help
- **Documenting decisions** - Understand the "why" not just the "what"
- **Iterative learning** - Build while you learn, learn while you build
- **Collaborative development** - AI as pair programmer, not replacement

This project is proof that entrepreneurs can build production-ready software without:
- Months of learning before starting
- Expensive developer hires
- Compromising on quality or security

---

## License

This project extends CodeIgniter 4, which is licensed under the MIT License.

Shield authentication is also MIT licensed.

Our documentation and methodology are shared freely to help other entrepreneurs build their dreams.
