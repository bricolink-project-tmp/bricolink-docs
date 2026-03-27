# BricoLink Service Booking

## Project Overview
This platform serves as the source of truth for the local artisan and repair service booking system. It is composed of a single REST API base serving web, and eventually a Phase 2 Flutter application.

### Architecture
- **Backend & Web**: Laravel (PHP) acting as the main REST API and rendering fully custom, authentic Tailwind CSS interfaces via Blade and Vite for our Artisan Platform.
- **Database**: MySQL to manage robust relational data across `Users`, `Artisans` (including `cover_image_path`), and `Bookings` (including `description` and `image_path` for repair issues). Eloquent Models and Migrations map directly to this schema.
- **Mobile (Phase 2)**: To be implemented in Flutter/Dart, designed to directly consume the Laravel API endpoints.

## Git Workflow
For our team of 5, the established Git workflow must be strictly adhered to:
1. **Never commit directly to `main`**. The `main` branch is locked for direct pushes.
2. **Use Feature Branches**: Check out a new branch for each individual task or feature (e.g., `feature/user-auth`, `fix/routing-error`).
3. **Mandatory Pull Requests (PRs)**: All changes must be integrated into `main` solely through Pull Requests requiring peer review.

## Setup Instructions (Fedora Linux / Global)

### Prerequisites
1. Ensure the required PHP CLI extensions and web server dependencies are installed:
   ```bash
   sudo dnf install php php-cli php-fpm php-mbstring php-xml php-json php-zip php-curl php-mysqlnd mysql-server
   ```
2. **Node.js**: Ensure Node.js and NPM are installed to compile the Tailwind CSS frontend.

### Local Environment Getting Started
1. Clone the necessary repositories into your workspace.
2. Inside the `artisan-backend-laravel` directory, install PHP dependencies:
   ```bash
   composer install
   ```
3. Install Node dependencies:
   ```bash
   npm install
   ```
4. Copy the example environment variable file:
   ```bash
   cp .env.example .env
   ```
5. Configure your `.env` file with the BricoLink environment settings:
   - Change the app name: `APP_NAME=BricoLink`
   - Configure your local MySQL database credentials:
     ```env
     DB_CONNECTION=mysql
     DB_HOST=127.0.0.1
     DB_PORT=3306
     DB_DATABASE=artisan_project
     DB_USERNAME=root
     DB_PASSWORD=
     ```
6. Generate the local application key:
   ```bash
   php artisan key:generate
   ```
7. Instantiate the database tables using the Laravel migrations:
   ```bash
   php artisan migrate
   ```
8. Build the frontend assets (Tailwind CSS and JavaScript) via Vite:
   ```bash
   npm run build
   ```
   *(Alternatively, run `npm run dev` in a separate terminal during development).*
9. Serve the backend locally:
   ```bash
   php artisan serve
   ```
