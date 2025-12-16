# Laravel Portfolio Homepage (Professional)

This is a **complete homepage structure** including **Google Fonts, Header, Hero, Portfolio, About, Skills, and Footer**. You can directly use this in Laravel.

---

## 1️⃣ Layout File (`resources/views/layouts/app.blade.php`)

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@yield('title', 'My Portfolio')</title>

    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        body{
            font-family: 'Poppins', sans-serif;
        }
        .hero{
            background: linear-gradient(to right, #4f46e5, #9333ea);
            color: white;
            padding: 100px 0;
        }
        .portfolio-card img{
            height: 200px;
            object-fit: cover;
        }
        footer{
            background:#111827;
            color:#9ca3af;
        }
    </style>
</head>
<body>

@include('partials.header')

@yield('content')

@include('partials.footer')

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

---

## 2️⃣ Header (`resources/views/partials/header.blade.php`)

```blade
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
        <a class="navbar-brand fw-bold" href="#">Rafiqul</a>
        <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#menu">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="menu">
            <ul class="navbar-nav ms-auto">
                <li class="nav-item"><a class="nav-link" href="#home">Home</a></li>
                <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                <li class="nav-item"><a class="nav-link" href="#portfolio">Portfolio</a></li>
                <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
            </ul>
        </div>
    </div>
</nav>
```

---

## 3️⃣ Homepage (`resources/views/home.blade.php`)

```blade
@extends('layouts.app')

@section('title', 'Home')

@section('content')

<section class="hero text-center" id="home">
    <div class="container">
        <h1 class="display-4 fw-bold">Hi, I’m Rafiqul Islam</h1>
        <p class="lead">Laravel Developer | PHP | React | WordPress</p>
        <a href="#portfolio" class="btn btn-light btn-lg mt-3">View My Work</a>
    </div>
</section>

<section class="py-5" id="about">
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <h2 class="fw-bold">About Me</h2>
                <p>I am a professional Laravel developer with experience in real-world projects including eCommerce, Blog, and Portfolio systems.</p>
            </div>
            <div class="col-md-6">
                <h2 class="fw-bold">Skills</h2>
                <ul class="list-group">
                    <li class="list-group-item">Laravel & PHP</li>
                    <li class="list-group-item">React & JavaScript</li>
                    <li class="list-group-item">MySQL & REST API</li>
                    <li class="list-group-item">WordPress & Elementor</li>
                </ul>
            </div>
        </div>
    </div>
</section>

<section class="py-5 bg-light" id="portfolio">
    <div class="container">
        <h2 class="text-center fw-bold mb-4">Portfolio</h2>
        <div class="row g-4">
            @for($i=1;$i<=6;$i++)
            <div class="col-md-4">
                <div class="card portfolio-card shadow-sm">
                    <img src="https://via.placeholder.com/600x400" class="card-img-top">
                    <div class="card-body">
                        <h5 class="card-title">Project {{ $i }}</h5>
                        <p class="card-text">Laravel based web application.</p>
                    </div>
                </div>
            </div>
            @endfor
        </div>
    </div>
</section>

<section class="py-5" id="contact">
    <div class="container text-center">
        <h2 class="fw-bold">Let’s Work Together</h2>
        <p>Email: your@email.com</p>
    </div>
</section>

@endsection
```

---

## 4️⃣ Footer (`resources/views/partials/footer.blade.php`)

```blade
<footer class="py-4">
    <div class="container text-center">
        <p class="mb-0">© {{ date('Y') }} Rafiqul Islam. All rights reserved.</p>
    </div>
</footer>
```

---

## ✅ Result

✔ Professional homepage
✔ Google Fonts included
✔ Header, Hero, Portfolio, Footer
✔ Laravel Blade ready
✔ GitHub & Client-ready

---

If you want next:

* 🔥 Dynamic portfolio from database
* 🔐 Admin panel to manage content
* 🎨 Dark / Light mode
* 🌐 SEO optimized version

Just tell me 👍
