Here’s the correct & easiest way to install Laravel 10 on Windows (XAMPP) step-by-step. I’ll keep it simple and practical 👇

✅ 1. System Requirements

Make sure you have:

PHP 8.1 or 8.2 ✅

Composer (latest) ✅

XAMPP / Apache ✅

OpenSSL enabled

Check versions
php -v
composer -V

✅ 2. Install Composer (If Not Installed)

Download & install:
👉 https://getcomposer.org/download/

✔ During install, select:

C:\xampp\php\php.exe


Restart CMD after installation.

✅ 3. Go to Your Project Directory
cd C:\xampp\htdocs

✅ 4. Install Laravel 10 (Recommended Way)

Run this command:

composer create-project laravel/laravel myproject "^10.0"


Example:

composer create-project laravel/laravel blog-site "^10.0"


⏳ Wait 2–5 minutes (depends on internet speed)

✅ 5. Configure .env File

Go to:

C:\xampp\htdocs\blog-site\.env


Update database settings:

DB_DATABASE=blog_site
DB_USERNAME=root
DB_PASSWORD=


Create database blog_site in phpMyAdmin.

✅ 6. Generate App Key
cd blog-site
php artisan key:generate

✅ 7. Run Laravel Server
php artisan serve


Open browser:
👉 http://127.0.0.1:8000

🎉 Laravel 10 is running successfully!

✅ 8. (Optional) Install Node & Vite

If you want frontend assets:

npm install
npm run dev

####Then

Step 1: Navigate to your Laravel project
cd C:\xampp\htdocs\blog-site

Step 2: Install Laravel Breeze

Run:

composer require laravel/breeze --dev


This installs the Breeze package in your project.

Step 3: Choose Breeze Stack
Option 1: Blade (Default)
php artisan breeze:install


This will install Blade-based authentication (login, register, dashboard).

Then run:

npm install
npm run dev
php artisan migrate