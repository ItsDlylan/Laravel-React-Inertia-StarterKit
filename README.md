# Laravel Inertia React Starter Template

A professional, type-safe Laravel application template built with Inertia.js and React. This template provides a solid foundation for building modern web applications with strict code quality standards, comprehensive testing, and enterprise-ready architecture.

## Project Overview

This template combines the power of Laravel 12, Inertia.js v2, and React to deliver a full-stack application framework that prioritizes type safety, code quality, and developer experience. The architecture is designed to scale from small projects to large enterprise applications.

### Key Features

- **Actions-Oriented Architecture**: Business logic is encapsulated in single-purpose Action classes located in `app/Actions/`
- **Type-Safe Development**: 100% type coverage enforced with PHPStan level 9 and TypeScript strict mode
- **Modern Frontend Stack**: React 19 with TypeScript, Tailwind CSS, and Radix UI components
- **Comprehensive Testing**: Pest PHP testing framework with browser testing capabilities and 100% code coverage requirements
- **Code Quality Tools**: Pre-configured Rector, Laravel Pint, ESLint, and Prettier for automated code formatting and refactoring
- **Laravel 12**: Built on the latest Laravel framework with streamlined structure and modern PHP 8.4 features
- **Authentication Ready**: Laravel Fortify integration for authentication flows
- **API Documentation**: Automatic Postman collection generation from Laravel API routes
- **AI-Assisted Development**: Integrated AI guidelines and Laravel Boost MCP tools for enhanced development workflow

### Tech Stack

**Backend:**
- PHP 8.4+
- Laravel 12
- Inertia.js Laravel v2
- Laravel Fortify
- Pest PHP (Testing)

**Frontend:**
- React 19
- TypeScript
- Tailwind CSS 4
- Radix UI
- Vite

**Development Tools:**
- PHPStan (Static Analysis)
- Rector (Code Refactoring)
- Laravel Pint (Code Formatting)
- ESLint & Prettier (JavaScript/TypeScript)
- Pest Browser Testing (Playwright)
- Laravel Postman (API Documentation)

## Prerequisites

Before you begin, ensure you have the following installed on your development machine:

- **PHP 8.4+** - [Download PHP](https://www.php.net/downloads.php)
- **Composer** - PHP dependency manager - [Install Composer](https://getcomposer.org/download/)
- **Node.js 18+** and **npm** - JavaScript runtime and package manager - [Download Node.js](https://nodejs.org/)
- **Code Coverage Driver** - Required for testing (xdebug or PCOV) - [xdebug Installation Guide](https://xdebug.org/docs/install)
- **Database** - SQLite (default), MySQL, or PostgreSQL
- **Git** - Version control system

### Optional Prerequisites

- **Playwright** - For browser testing capabilities (can be installed after initial setup)

## Quick Start

This template is designed to be cloned and customized for your specific project needs.

### 1. Clone or Fork the Template

```bash
# Clone the repository
git clone <repository-url> your-project-name
cd your-project-name

# Or fork the repository and clone your fork
```

### 2. Initial Setup

Run the setup command to install dependencies, configure the environment, and prepare the database:

```bash
composer setup
```

This command will:
- Install PHP dependencies via Composer
- Copy `.env.example` to `.env` if it doesn't exist
- Generate application encryption key
- Run database migrations
- Install Node.js dependencies
- Build frontend assets

### 3. Start Development Server

Launch the development environment with a single command:

```bash
composer dev
```

This starts:
- Laravel development server (typically `http://localhost:8000`)
- Queue worker for background jobs
- Log monitoring with Laravel Pail
- Vite development server for hot module replacement

### 4. Verify Installation

Run the test suite to ensure everything is configured correctly:

```bash
composer test
```

You should see all tests passing with 100% code coverage.

## Installation / Setup

### Manual Setup Steps

If you prefer to set up the project manually:

1. **Install PHP Dependencies**
   ```bash
   composer install
   ```

2. **Configure Environment**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

3. **Configure Database**
   
   Edit `.env` file and set your database configuration. By default, the project uses SQLite (`database/database.sqlite`).

   **Using PostgreSQL with Docker Compose (Recommended for quick setup):**
   
   Start the PostgreSQL container:
   ```bash
   docker-compose up -d
   ```
   
   Update your `.env` file with PostgreSQL configuration:
   ```env
   DB_CONNECTION=pgsql
   DB_HOST=127.0.0.1
   DB_PORT=5432
   DB_DATABASE=laravel_starterkit
   DB_USERNAME=user
   DB_PASSWORD=password
   ```
   
   To stop the PostgreSQL container:
   ```bash
   docker-compose down
   ```
   
   To switch back to SQLite, change `DB_CONNECTION` in `.env`:
   ```env
   DB_CONNECTION=sqlite
   ```
   
   **Using MySQL or PostgreSQL (without Docker):**
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=your_database
   DB_USERNAME=your_username
   DB_PASSWORD=your_password
   ```

4. **Run Migrations**
   ```bash
   php artisan migrate
   ```

5. **Install Frontend Dependencies**
   ```bash
   npm install
   ```

6. **Build Frontend Assets**
   ```bash
   npm run build
   ```

### Browser Testing Setup (Optional)

If you plan to use Pest's browser testing capabilities:

```bash
npm install playwright
npx playwright install
```

This installs Playwright and the necessary browser binaries for end-to-end testing.

## Development Workflow

### Development Commands

- **`composer dev`** - Starts all development services concurrently (Laravel server, queue worker, logs, Vite)

### Code Quality Commands

- **`composer lint`** - Runs all code quality tools:
  - Rector (automated code refactoring)
  - Laravel Pint (PHP code formatting)
  - Prettier (JavaScript/TypeScript formatting)
  - ESLint (JavaScript/TypeScript linting)

- **`composer test:lint`** - Dry-run mode for CI/CD pipelines (checks formatting without modifying files)

### Testing Commands

- **`composer test:type-coverage`** - Ensures 100% type coverage with Pest
- **`composer test:types`** - Runs static analysis:
  - PHPStan at level 9 (maximum strictness)
  - TypeScript type checking
- **`composer test:unit`** - Runs Pest tests with 100% code coverage requirement
- **`composer test`** - Runs the complete test suite:
  - Type coverage validation
  - Unit and feature tests
  - Linting checks
  - Static analysis

### Maintenance Commands

- **`composer update:requirements`** - Updates all PHP and NPM dependencies to their latest compatible versions

### Frontend Commands

- **`npm run dev`** - Start Vite development server with hot module replacement
- **`npm run build`** - Build production assets
- **`npm run build:ssr`** - Build both client and server-side rendering assets
- **`npm run lint`** - Run ESLint and Prettier on frontend code

### API Documentation

This starter kit includes [Laravel Postman](https://github.com/yasin-tgh/laravel-postman) for automatically generating Postman collections from your Laravel API routes.

**Pre-generated Collection:**

A starter Postman collection is included in the repository at `storage/postman/api_collection.json`. You can import this directly into Postman to get started quickly. The collection includes:

- Pre-configured authentication variables (Bearer token)
- Base URL variable set to `http://localhost:8000`
- Ready-to-use structure for when you add API routes

**Generate/Update Postman Collection:**

After adding API routes, regenerate the collection to include them:

```bash
php artisan postman:generate
```

The collection will be saved to `storage/postman/api_collection.json` and can be imported directly into Postman.

**Configuration:**

The Postman configuration is located in `config/postman.php`. Key features:

- **Automatic Route Discovery**: Automatically discovers all API routes with the `api` prefix
- **FormRequest Integration**: Generates request bodies from FormRequest validation rules
- **Authentication Support**: Configures Bearer token authentication for protected routes
- **Flexible Organization**: Routes are organized using nested path strategy by default
- **Environment Variables**: Use `.env` variables for sensitive authentication data

**Default Configuration:**

- Routes are filtered to include only those with the `api` prefix
- Authentication is enabled with Bearer token support
- Protected routes are detected via `auth:api` and `auth:sanctum` middleware
- Routes are organized using nested path structure

**Customization:**

You can customize the Postman collection generation by editing `config/postman.php`:

- **Route Filtering**: Include/exclude specific routes, middleware, or controllers
- **Organization Strategy**: Choose between prefix, nested_path, or controller-based grouping
- **Authentication**: Configure Bearer, Basic Auth, or API Key authentication
- **Request Formatting**: Customize request naming and body types

**Environment Variables:**

Add these to your `.env` file for Postman authentication (optional):

```env
POSTMAN_AUTH_TOKEN=your-bearer-token-here
POSTMAN_AUTH_USER=user@example.com
POSTMAN_AUTH_PASSWORD=password
POSTMAN_API_KEY=your-api-key
POSTMAN_API_KEY_NAME=X-API-KEY
```

For more details, see the [Laravel Postman documentation](https://github.com/yasin-tgh/laravel-postman).

## Testing

This template enforces strict testing standards to ensure code quality and reliability.

### Running Tests

**Run all tests:**
```bash
composer test
```

**Run specific test file:**
```bash
php artisan test tests/Feature/ExampleTest.php
```

**Run tests matching a filter:**
```bash
php artisan test --filter=testName
```

**Run only unit tests:**
```bash
composer test:unit
```

### Test Coverage

The project requires 100% code coverage. All tests must pass and maintain full coverage before code can be merged.

### Browser Testing

Browser tests are located in `tests/Browser/` and use Playwright for end-to-end testing. These tests can interact with the application in a real browser environment.

**Run browser tests:**
```bash
php artisan test tests/Browser/
```

### Writing Tests

- Feature tests should be placed in `tests/Feature/`
- Unit tests should be placed in `tests/Unit/`
- Browser tests should be placed in `tests/Browser/`
- Use factories for creating test data
- Follow existing test patterns and conventions

## Deployment

### Pre-Deployment Checklist

1. **Environment Configuration**
   - Ensure `.env` is properly configured for production
   - Set `APP_ENV=production`
   - Set `APP_DEBUG=false`
   - Configure production database credentials
   - Set secure `APP_KEY`

2. **Dependencies**
   ```bash
   composer install --optimize-autoloader --no-dev
   npm ci
   npm run build
   ```

3. **Database**
   ```bash
   php artisan migrate --force
   ```

4. **Cache Optimization**
   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

5. **Storage Link**
   ```bash
   php artisan storage:link
   ```

### Production Build

Build optimized frontend assets for production:

```bash
npm run build
```

For SSR-enabled applications:

```bash
npm run build:ssr
```

### Server Requirements

- PHP 8.4+
- Composer
- Node.js 18+ (for building assets)
- Web server (Apache/Nginx)
- Database (MySQL/PostgreSQL recommended for production)

### Environment Variables

Ensure all required environment variables are set in your production `.env` file. Refer to `.env.example` for available configuration options.

## Contributing

This template follows strict code quality standards. When contributing or customizing:

### Code Style

- **PHP**: Code must pass Laravel Pint formatting and Rector refactoring checks
- **JavaScript/TypeScript**: Code must pass ESLint and Prettier checks
- Run `composer lint` before committing to ensure code style compliance

### Type Safety

- All PHP methods, properties, and parameters must have explicit type declarations
- TypeScript strict mode is enabled - all types must be properly defined
- Code must pass PHPStan level 9 and TypeScript type checking

### Testing Requirements

- All new features must include corresponding tests
- Tests must pass with 100% code coverage
- Use Pest PHP testing framework
- Follow existing test patterns and conventions

### Pull Request Process

1. Create a feature branch from `main`
2. Make your changes following code style guidelines
3. Write or update tests for your changes
4. Ensure all tests pass: `composer test`
5. Ensure code style is correct: `composer lint`
6. Submit pull request with clear description of changes

### Architecture Guidelines

- **Actions**: Business logic should be placed in `app/Actions/` classes
- **Controllers**: Keep controllers thin - delegate to Actions
- **Models**: Use Eloquent relationships and follow Laravel conventions
- **Frontend**: Reuse existing components from `resources/js/components/`
- **Forms**: Use Inertia's `useForm` helper for form handling

### Code Quality Tools

The following tools are configured and should be used:

- **Rector**: Automated code refactoring (`vendor/bin/rector`)
- **Laravel Pint**: PHP code formatting (`vendor/bin/pint`)
- **PHPStan**: Static analysis (`vendor/bin/phpstan`)
- **ESLint**: JavaScript/TypeScript linting (`npm run lint`)
- **Prettier**: Code formatting (`npm run lint`)

## License

This project template is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
