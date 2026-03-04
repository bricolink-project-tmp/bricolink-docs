# Local Artisan & Repair Service Booking

## Project Overview
This platform serves as the source of truth for the local artisan and repair service booking system. It is composed of a single REST API base serving web, and eventually a Phase 2 Flutter application.

### Architecture
- **Backend & Web**: Laravel (PHP) acting as the main REST API and rendering basic base views using Blade.
- **Database**: Oracle SQL+ to manage robust relational data across `Users`, `Artisans`, and `Bookings` components. Connection to Laravel handled using `yajra/laravel-oci8` or similar configuration.
- **Mobile (Phase 2)**: To be implemented in Flutter/Dart, designed to directly consume the Laravel API endpoints.

## Git Workflow
For our team of 5, the established Git workflow must be strictly adhered to:
1. **Never commit directly to `main`**. The `main` branch is locked for direct pushes.
2. **Use Feature Branches**: Check out a new branch for each individual task or feature (e.g., `feature/user-auth`, `fix/routing-error`).
3. **Mandatory Pull Requests (PRs)**: All changes must be integrated into `main` solely through Pull Requests requiring peer review.

## Setup Instructions (Fedora Linux)

### Prerequisites
1. Ensure the required PHP CLI extensions and web server dependencies are installed via `dnf` on Fedora:
   ```bash
   sudo dnf install php php-cli php-fpm php-mbstring php-xml php-json php-zip php-curl
   ```
2. **Oracle Instant Client**: Install Oracle Instant Client and compile the `oci8` PHP extension. Ensure the extension is enabled inside your `php.ini` file (`extension=oci8.so`).

### Local Environment Getting Started
1. Clone the necessary repositories into your workspace.
2. Inside the `artisan-backend-laravel` directory, run:
   ```bash
   composer install
   ```
3. Copy the example environment variable file:
   ```bash
   cp .env.example .env
   ```
4. Configure your local Oracle database credentials in the `.env` file (`DB_CONNECTION=oracle`, update host, port, username, password).
5. Generate the local application key:
   ```bash
   php artisan key:generate
   ```
6. Run the local database instantiation script found at `artisan-db-oracle/schema.sql` against your localized Oracle DB instance to set up standard tables.
7. Serve the backend locally:
   ```bash
   php artisan serve
   ```
