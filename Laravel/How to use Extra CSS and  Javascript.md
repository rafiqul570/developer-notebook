ঠিক আছে 👍
আমি **একটাও code পরিবর্তন না করে**, শুধু **clean formatting + সুন্দরভাবে arrange** করে দিচ্ছি যেন পড়তে, বুঝতে এবং ভবিষ্যতে reference হিসেবে রাখতে সুবিধা হয়।

---

# 🔷 `@stack`, `@push`, `@yield` আসলে কী?

Laravel Blade-এ এগুলো ব্যবহার হয়
👉 **Layout → Child page communication** এর জন্য।

---

## 1️⃣ `@yield('content')` — Main body area

### 📌 Layout ফাইলে (Placeholder)

```blade
<body>
    @yield('content')
</body>
```

### 📌 Child page থেকে content পাঠানো

```blade
@section('content')
    <h1>Dashboard</h1>
@endsection
```

### 🧠 মানে

**Layout বলছে → “এই জায়গায় child page এর content বসবে”**

---

## 2️⃣ `@stack('styles')` — Extra CSS ঢোকানোর জায়গা

### 📌 Layout ফাইলে (`<head>` এর ভিতরে)

```blade
<head>
    <link rel="stylesheet" href="{{ asset('css/app.css') }}">

    @stack('styles')
</head>
```

### 📌 Child page এ (যদি extra CSS লাগে)

```blade
@push('styles')
    <link rel="stylesheet" href="{{ asset('css/dashboard.css') }}">
@endpush
```

### 🧠 মানে

**Child page থেকে layout এর `<head>` এ CSS ঢোকানো**

---

## 3️⃣ `@stack('scripts')` — Extra JS ঢোকানোর জায়গা

### 📌 Layout ফাইলে (`</body>` এর আগে)

```blade
<body>

    @yield('content')

    @stack('scripts')
</body>
```

### 📌 Child page এ JS পাঠানো

```blade
@push('scripts')
    <script src="{{ asset('js/dashboard.js') }}"></script>
@endpush
```

### 🧠 মানে

**Page-specific JavaScript এখানে যাবে**

---

## 🔄 Full Flow Diagram (মাথায় রাখার জন্য)

```
Layout (app.blade.php)
│
├── <head>
│     ├── common CSS
│     └── @stack('styles')   ← child CSS
│
├── <body>
│     ├── @yield('content')  ← child HTML
│     └── @stack('scripts')  ← child JS
```

---

## ✅ Minimal Working Example

### 🔹 Layout (`app.blade.php`)

```blade
<html>
<head>
    <title>@yield('title')</title>
    @stack('styles')
</head>
<body>

    @yield('content')

    @stack('scripts')
</body>
</html>
```

---

### 🔹 Child Page

```blade
@extends('layouts.app')

@section('title','Profile')

@push('styles')
<style>
    h1 { color: red; }
</style>
@endpush

@section('content')
    <h1>My Profile</h1>
@endsection

@push('scripts')
<script>
    console.log('Profile page loaded');
</script>
@endpush
```

---

## 🧠 One-line মনে রাখার ট্রিক

* **HTML content → `@yield`**
* **Extra CSS / JS → `@stack` + `@push`**
* **Layout = Skeleton**
* **Child page = Flesh**

---

এখন এই structure তুমি
✅ Admin layout
✅ User layout
✅ Dashboard
✅ DataTable / JS heavy page

সব জায়গায় confidently ব্যবহার করতে পারবে।

চাও তো পরের ধাপে আমি এটাকে **real admin dashboard file structure** দিয়ে দেখাতে পারি 👌
