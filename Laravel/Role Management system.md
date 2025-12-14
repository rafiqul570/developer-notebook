
Laravel এ Role System করার জনপ্রিয় উপায়
===================================

🗄️ Step 1: users table এ role add করা

php artisan make:migration add_role_to_users_table

Schema::table('users', function (Blueprint $table) {
    $table->string('role')->default('user'); 
});


Run:

php artisan migrate


📌 এখন users table এ থাকবে:

id | name | email | password | role

👤 Step 2: User roles define করা
Example roles:
admin
user


👉 Register করলে default হবে user


🔑 Step 3: Middleware দিয়ে role check করা
php artisan make:middleware AdminMiddleware
php artisan make:middleware UserMiddleware

### app/Http/Middleware/AdminMiddleware.php

<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;

class AdminMiddleware
{
    public function handle(Request $request, Closure $next)
    {
        if (Auth::check() && Auth::user()->role === 'admin') {
            return $next($request);
        }

        return redirect()->route('dashboard');
    }
}

### app/Http/Middleware/UserMiddleware.php

<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;

class UserMiddleware
{
    public function handle(Request $request, Closure $next)
    {
        if (Auth::check() && Auth::user()->role === 'user') {
            return $next($request);
        }

        return redirect()->route('admin.dashboard');
    }
}



### Kernel.php এ register

protected $middlewareAliases = [
        
        'admin' => \App\Http\Middleware\AdminMiddleware::class,
        'user' => \App\Http\Middleware\UserMiddleware::class,
    ];

আথবা

protected $routeMiddleware = [
	
	'admin' => \App\Http\Middleware\AdminMiddleware::class,
        'user' => \App\Http\Middleware\Authenticate::class,
        
    ];


🛣️ Step 4: Route protection

// Normal user dashboard route
Route::middleware(['auth', 'user'])->group(function () {
    Route::get('/dashboard', function () {
        return view('dashboard');
    })->name('dashboard');
});


// Admin dashboard route
Route::middleware(['auth', 'admin'])->group(function () {
    Route::get('/admin/dashboard', function () {
        return view('admin.dashboard');
    })->name('admin.dashboard');
});


🧭 Step 5: Login করার পর role অনুযায়ী redirect
App/Http/Contrller/Auth/ AuthenticatedSessionController.php
/**
* Handle an incoming authentication request.
*/
    public function store(Request $request): RedirectResponse
    {
        $request->validate([
            'email' => 'required|email',
            'password' => 'required',
        ]);

        if (Auth::attempt($request->only('email', 'password'), $request->boolean('remember'))) {
            $request->session()->regenerate();

            $user = Auth::user();

            if ($user->role === 'admin') {
                return redirect()->intended('/admin/dashboard');
            }

            return redirect()->intended('/dashboard');
        }

        return back()->withErrors([
            'email' => 'The provided credentials do not match our records.',
        ]);
    }


🖥️ Step 6: Blade এ role check
@if(auth()->user()->role === 'admin')
   <a href="/admin/dashboard">Admin Panel</a>
@endif

