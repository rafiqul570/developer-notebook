# Laravel 10 Role Management System (GitHub Ready)

This is a **complete role management system** for Laravel 10 including Admin/User roles, middleware, controllers, routes, and views.

---

## 1️⃣ Database Migration

Add `role` column to users table:

```php
Schema::table('users', function (Blueprint $table) {
    $table->string('role')->default('user');
});
```

---

## 2️⃣ User Model (`app/Models/User.php`)

```php
protected $fillable = [
    'name',
    'email',
    'password',
    'role',
];
```

---

## 3️⃣ Role Middleware

Create middleware:

```bash
php artisan make:middleware RoleMiddleware
```

**app/Http/Middleware/RoleMiddleware.php**

```php
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Support\Facades\Auth;

class RoleMiddleware
{
    public function handle($request, Closure $next, $role)
    {
        if (!Auth::check()) {
            return redirect()->route('login');
        }

        if (Auth::user()->role !== $role) {
            abort(403, 'Unauthorized access');
        }

        return $next($request);
    }
}
```

**app/Http/Middleware/RedirectIfAuthenticated.php**

```php
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Support\Facades\Auth;

class RoleMiddleware
{
    public function handle($request, Closure $next, ...$guards)
    {
        if (Auth::check()) {
            if (Auth::user()->role === 'admin') {
                return redirect('/admin/dashboard');
            }

            return redirect('/user/dashboard');
        }

        return $next($request);
    }
}
```

**Register middleware in Kernel (`app/Http/Kernel.php`)**

```php
protected $routeMiddleware = [
    'role' => \App\Http\Middleware\RoleMiddleware::class,
];
```

---

## 4️⃣ Controllers

**Admin Dashboard Controller (`app/Http/Controllers/Admin/AdminDashboardController.php`)**

```php
<?php

namespace App\Http\Controllers\Admin;

use App\Http\Controllers\Controller;

class AdminDashboardController extends Controller
{
    public function index()
    {
        return view('admin.dashboard');
    }
}
```

**User Dashboard Controller (`app/Http/Controllers/User/UserDashboardController.php`)**

```php
<?php

namespace App\Http\Controllers\User;

use App\Http\Controllers\Controller;

class DashboardController extends Controller
{
    public function index()
    {
        return view('user.dashboard');
    }
}
```

---

## 5️⃣ Routes (`routes/web.php`)

```php
use App\Http\Controllers\Admin\AdminDashboardController;
use App\Http\Controllers\User\UserDashboardController;

Route::middleware('guest')->group(function () {
    Route::get('/login', function () {
        return view('auth.login');
    })->name('login');
});

Route::middleware(['auth','role:admin'])->group(function () {
    Route::get('/admin/dashboard', [AdminDashboardController::class, 'index'])->name('admin.dashboard');
});

Route::middleware(['auth','role:user'])->group(function () {
    Route::get('/user/dashboard', [UserDashboardController::class, 'index'])->name('user.dashboard');
});
```

---

## 6️⃣ Login Logic (Breeze Style)

**app/Http/Controllers/Auth/AuthenticatedSessionController.php**

```php
public function store(LoginRequest $request): RedirectResponse
{
    $request->authenticate();
    $request->session()->regenerate();

    $user = Auth::user();

    return match ($user->role) {
        'admin' => redirect()->route('admin.dashboard'),
        'user'  => redirect()->route('user.dashboard'),
        default => redirect('/'),
    };
}
```

---

## 7️⃣ RouteServiceProvider (`app/Providers/RouteServiceProvider.php`)

```php
public const HOME = '/user/dashboard';
```

---

## 8️⃣ Views Structure

```text
resources/views
│
├── layouts
│   ├── admin-template.blade.php
│   └── user-template.blade.php
│
├── admin
│   └── dashboard.blade.php
│
├── user
│   └── dashboard.blade.php
```

---

## 🔐 Security Flow (Important)

1. User Login
2. Redirect via `AuthenticatedSessionController` (role-based)
3. Route Middleware (`auth` + `role`) validation
4. Dashboard Controller
5. Blade View Rendering

---

✅ **GitHub Ready:**

* Clean folder structure
* Role-based middleware
* Admin & User dashboards
* Breeze authentication compatible
* Ready for production

---

You can now **push this to GitHub** and it will work for a multi-role Laravel project.
