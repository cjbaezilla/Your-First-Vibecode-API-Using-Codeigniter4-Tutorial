# LaunchPad API - Agent Guidelines

## Project Purpose & Documentation

**Project Name:** LaunchPad API  
**Project Goal:** Production-ready API foundation with authentication, authorization, and comprehensive documentation for AI-assisted development.

**Primary Documentation:** This project is documented comprehensively in `article.md`—a complete guide explaining our "Vibe Coding" methodology, technical decisions, and entrepreneur-friendly approach to building APIs with AI assistance.

**Documentation Mandate:** Every technical decision in this project must be documented with:
- The decision made and when
- Alternatives considered
- Rationale for the choice
- Trade-offs (pros and cons)
- Whether it's reversible

This file (`AGENTS.md`) serves as the **"how"**—implementation details, commands, and standards.  
The article (`article.md`) serves as the **"why"**—decision rationale, methodology explanation, and entrepreneur guidance.

When modifying this file or adding features, update `article.md` with the reasoning behind your changes.

---

## Project Overview

This is a **CodeIgniter 4** project configured for building **REST API services** with **Shield authentication**.

### Architecture

- **Framework**: CodeIgniter 4 (PHP 8.2+)
- **Authentication**: CodeIgniter Shield (Session, Access Tokens, HMAC, JWT)
- **Documentation**: 
  - CI4 User Guide: `D:\DEV\ci_api_ejemplo\ci-userguide\`
  - Shield Docs: `D:\DEV\ci_api_ejemplo\shield-docs\`

### Directory Structure

```
D:\DEV\ci_api_ejemplo\
├── app/                    # Application code
│   ├── Config/            # Configuration files (42 configs)
│   ├── Controllers/       # API controllers
│   ├── Models/            # Data models
│   ├── Filters/           # Authentication/authorization filters
│   └── Database/          # Migrations and seeds
├── ci-userguide/          # CI4 documentation (HTML)
├── shield-docs/           # Shield authentication docs (Markdown)
├── public/                # Web root (index.php)
├── system/                # Framework core
├── writable/              # Cache, logs, uploads
├── vendor/                # Composer dependencies
└── .opencode/
    └── skills/             # Skills files for this project
```

## Common Commands

### Development

```bash
# Run development server
php spark serve

# Clear cache
php spark cache:clear

# Run migrations
php spark migrate --all

# Run seeds
php spark db:seed SeedName

# Generate controller
php spark make:controller Api/UserController

# Generate model
php spark make:model Models/UserModel

# Generate migration
php spark make:migration create_users_table
```

### Authentication (Shield)

```bash
# Setup Shield (one-time)
php spark shield:setup

# Create user
php spark shield:user create

# List users
php spark shield:user list

# Manage user groups
php spark shield:user addgroup
php spark shield:user removegroup

# HMAC key management
php spark shield:hmac reencrypt
php spark shield:hmac invalidateAll
```

### Testing

```bash
# Run all tests
vendor/bin/phpunit

# Run specific test
vendor/bin/phpunit tests/app/Controllers/UserControllerTest.php

# Run with coverage
vendor/bin/phpunit --coverage-html coverage/
```

## API Development Standards

### Controllers

- Extend `CodeIgniter\RESTful\ResourceController` for API resources
- Use `CodeIgniter\API\ResponseTrait` for consistent responses
- Implement proper HTTP status codes
- Apply authentication filters to protected routes

### Models

- Extend `CodeIgniter\Model` for data access
- Use Entity classes for complex data mapping
- Implement validation rules in models
- Use query builder for secure queries

### Authentication

- **Access Tokens**: For stateless API authentication (Bearer tokens)
- **HMAC**: For high-security API endpoints with signed requests
- **JWT**: For self-contained tokens with claims
- **Session**: For traditional web applications

### Security Checklist

- [ ] Use HTTPS in production
- [ ] Enable CSRF protection for forms
- [ ] Apply rate limiting to auth endpoints
- [ ] Validate all input data
- [ ] Use parameterized queries (Query Builder)
- [ ] Escape output with `esc()` function
- [ ] Set appropriate CORS headers
- [ ] Configure Content Security Policy
- [ ] Enable security headers
- [ ] Hash passwords with strong algorithms (Argon2id/bcrypt)

## Configuration Files

| File | Purpose |
|------|---------|
| `app/Config/App.php` | Base URL, CSRF, sessions |
| `app/Config/Routes.php` | Route definitions |
| `app/Config/Database.php` | Database connections |
| `app/Config/Auth.php` | Shield authentication |
| `app/Config/AuthGroups.php` | Groups and permissions |
| `app/Config/AuthToken.php` | Token settings |
| `app/Config/Filters.php` | Filter configuration |
| `app/Config/Security.php` | Security headers, CSRF |
| `app/Config/Cors.php` | CORS configuration |
| `app/Config/Format.php` | API response formats |

## Available Skills

Refer to skills files in `.opencode/skills/` directory:

1. **ci4-api-development** - REST API patterns, ResponseTrait, content negotiation
2. **ci4-shield-auth** - Authentication methods, tokens, permissions, groups
3. **ci4-routing-controllers** - Routes, controllers, filters, RESTful resources
4. **ci4-models-database** - Models, entities, query builder, migrations
5. **ci4-security** - OWASP compliance, validation, rate limiting, encryption
6. **ci4-configuration** - Config files, environment variables, services
7. **ci4-testing** - PHPUnit, HTTP testing, mocking, database testing

## Key Documentation References

### CodeIgniter 4

- API Guide: `D:\DEV\ci_api_ejemplo\ci-userguide\guides\api\index.html`
- RESTful Resources: `D:\DEV\ci_api_ejemplo\ci-userguide\incoming\restful.html`
- Routing: `D:\DEV\ci_api_ejemplo\ci-userguide\incoming\routing.html`
- Filters: `D:\DEV\ci_api_ejemplo\ci-userguide\incoming\filters.html`
- Models: `D:\DEV\ci_api_ejemplo\ci-userguide\models\model.html`
- Security: `D:\DEV\ci_api_ejemplo\ci-userguide\concepts\security.html`
- Configuration: `D:\DEV\ci_api_ejemplo\ci-userguide\general\configuration.html`

### Shield

- API Tokens: `D:\DEV\ci_api_ejemplo\shield-docs\guides\api_tokens.md`
- HMAC Keys: `D:\DEV\ci_api_ejemplo\shield-docs\guides\api_hmac_keys.md`
- Authorization: `D:\DEV\ci_api_ejemplo\shield-docs\references\authorization.md`
- Authentication: `D:\DEV\ci_api_ejemplo\shield-docs\references\authentication\authentication.md`

## Best Practices

1. **Always validate input** - Use Validation library
2. **Use filters for auth** - Apply at route level
3. **Return consistent responses** - Use ResponseTrait methods
4. **Log important events** - Use CI4's logging
5. **Write tests** - Unit and feature tests
6. **Use migrations** - Never modify database directly
7. **Follow PSR standards** - Code formatting
8. **Document APIs** - Use OpenAPI/Swagger

## Troubleshooting

### Common Issues

**Routes not working:**
- Check `app/Config/Routes.php`
- Verify `.htaccess` in public directory
- Ensure mod_rewrite is enabled

**Authentication failing:**
- Check filter configuration in `Filters.php`
- Verify Shield setup completed
- Check token expiration

**Database errors:**
- Verify `.env` database configuration
- Run migrations: `php spark migrate --all`
- Check database credentials

**CORS errors:**
- Configure `app/Config/Cors.php`
- Add proper headers in `.htaccess`

## Environment Setup

### Required

- PHP 8.2 or higher
- Composer
- MySQL/PostgreSQL/SQLite
- Web server (Apache/Nginx)

### Optional

- Redis (caching, sessions)
- Xdebug (debugging)
- PHPUnit (testing)

### .env Configuration

```bash
# Copy example
# Windows:
copy env .env

# Edit .env
CI_ENVIRONMENT = development
app.baseURL = 'http://localhost:8080'

# Database
database.default.hostname = localhost
database.default.database = ci_api_db
database.default.username = root
database.default.password = secret
database.default.DBDriver = MySQLi
```

## Contact & Support

- CodeIgniter Docs: https://codeigniter.com/user_guide/
- Shield Docs: https://shield.codeigniter.com/
- Community Forum: https://forum.codeigniter.com/

---

## Decision Documentation Format

When adding or modifying this file, document your decisions in `article.md` using this format:

```markdown
### Decision: [Brief description]

**Date**: [When decided]
**Context**: [What led to this change]
**Options Considered**:
- Option A: [description]
- Option B: [description]

**Decision**: We chose [Option] because [reasoning]

**Trade-offs**:
- Pros: [benefits]
- Cons: [drawbacks]

**Reversible?**: [Yes/No] - [Explanation]
```

## Documentation References

- **Methodology & Decisions**: See `article.md` for complete rationale
- **Implementation Details**: This file (`AGENTS.md`)
- **AI Skills**: `.opencode/skills/*.md`
- **Official Docs**: `ci-userguide/` (CI4) and `shield-docs/` (Shield)

---

*Last updated: February 2026*  
*Project: LaunchPad API*  
*Location: D:\DEV\ci_api_ejemplo*  
*Purpose: LinkedIn tutorial on Vibe Coding methodology*
