# Professional Laravel Portfolio Project Structure

This is a **real‑world, scalable, and professional Laravel portfolio project structure**, suitable for **freelancers, job portfolios, and agency‑level projects**.

---

## 📁 Root Directory Structure

```text
portfolio/
│
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Frontend/
│   │   │   │   ├── HomeController.php
│   │   │   │   ├── ProjectController.php
│   │   │   │   ├── BlogController.php
│   │   │   │   └── ContactController.php
│   │   │   │
│   │   │   └── Admin/
│   │   │       ├── DashboardController.php
│   │   │       ├── ProjectController.php
│   │   │       ├── ProjectImageController.php
│   │   │       ├── SkillController.php
│   │   │       ├── ExperienceController.php
│   │   │       └── BlogController.php
│   │   │
│   │   ├── Middleware/
│   │   │   └── AdminMiddleware.php
│   │   │
│   │   └── Requests/
│   │       └── ProjectRequest.php
│   │
│   ├── Models/
│   │   ├── Project.php
│   │   ├── ProjectImage.php
│   │   ├── Skill.php
│   │   ├── Experience.php
│   │   ├── Blog.php
│   │   └── User.php
│   │
│   └── Services/
│       └── ImageUploadService.php
│
├── database/
│   ├── migrations/
│   │   ├── create_projects_table.php
│   │   ├── create_project_images_table.php
│   │   ├── create_skills_table.php
│   │   ├── create_experiences_table.php
│   │   └── create_blogs_table.php
│   │
│   └── seeders/
│       ├── DatabaseSeeder.php
│       └── AdminUserSeeder.php
│
├── public/
│   ├── uploads/
│   │   ├── projects/
│   │   ├── blogs/
│   │   └── profile/
│   │
│   └── assets/
│       ├── css/
│       ├── js/
│       └── images/
│
├── resources/
│   ├── views/
│   │   ├── layouts/
│   │   │   ├── frontend.blade.php
│   │   │   └── admin.blade.php
│   │   │
│   │   ├── frontend/
│   │   │   ├── home.blade.php
│   │   │   ├── about.blade.php
│   │   │   ├── projects/
│   │   │   │   ├── index.blade.php
│   │   │   │   └── show.blade.php
│   │   │   ├── blog/
│   │   │   │   ├── index.blade.php
│   │   │   │   └── show.blade.php
│   │   │   └── contact.blade.php
│   │   │
│   │   └── admin/
│   │       ├── dashboard.blade.php
│   │       ├── projects/
│   │       │   ├── index.blade.php
│   │       │   ├── create.blade.php
│   │       │   └── edit.blade.php
│   │       ├── skills/
│   │       ├── experiences/
│   │       └── blogs/
│   │
│   └── lang/
│
├── routes/
│   ├── web.php
│   ├── admin.php
│   └── api.php
│
├── storage/
├── tests/
├── .env
└── artisan
```

---

## 🧠 Architecture Highlights

### ✅ Frontend & Admin Separation

* `Frontend` → Public portfolio (Home, Projects, Blog)
* `Admin` → Secure dashboard (CRUD operations)

### ✅ Project with Multiple Images (Industry Standard)

* `projects` table → main project info
* `project_images` table → unlimited images per project

### ✅ Blade Layout System

* `layouts/frontend.blade.php`
* `layouts/admin.blade.php`

### ✅ Clean Upload Management

* Separate folders for projects, blogs, and profile images

### ✅ Ready for Growth

This structure easily supports:

* REST API
* React / Vue frontend
* Role management
* SEO optimization
* Caching & performance improvements

---

## 🎯 Perfect For

* Freelancer portfolio
* Job application showcase
* Agency website
* Laravel learning & reuse

---

**This is a production‑ready Laravel portfolio structure used in real projects.**

---

# 🚀 Laravel Portfolio Website (A to Z) – Copy & Paste Ready (Bangla)

এই গাইডে আপনি **Laravel দিয়ে একটি Complete Professional Portfolio Website** বানাতে পারবেন **শুধু Copy–Paste করে**।

👉 Admin Panel থাকবে (Project CRUD + Multiple Images)
👉 Frontend Portfolio থাকবে (Home, Projects, Project Details)

---

## 🧩 Step 0: Laravel Install

```bash
composer create-project laravel/laravel portfolio
cd portfolio
php artisan serve
```

---

## 🧩 Step 1: Database Setup (.env)

```env
DB_DATABASE=portfolio
DB_USERNAME=root
DB_PASSWORD=
```

```bash
php artisan migrate
```

---

## 🧩 Step 2: Models & Migrations

### ▶ Project Model

```bash
php artisan make:model Project -m
```

```php
Schema::create('projects', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('description');
    $table->timestamps();
});
```

---

### ▶ ProjectImage Model

```bash
php artisan make:model ProjectImage -m
```

```php
Schema::create('project_images', function (Blueprint $table) {
    $table->id();
    $table->foreignId('project_id')->constrained()->onDelete('cascade');
    $table->string('image');
    $table->timestamps();
});
```

```bash
php artisan migrate
```

---

## 🧩 Step 3: Model Relationship

```php
class Project extends Model
{
    protected $fillable = ['title','description'];

    public function images()
    {
        return $this->hasMany(ProjectImage::class);
    }
}
```

```php
class ProjectImage extends Model
{
    protected $fillable = ['project_id','image'];
}
```

---

## 🧩 Step 4: Controllers

```bash
php artisan make:controller Admin/ProjectController
php artisan make:controller Frontend/ProjectController
```

---

### ▶ Admin ProjectController (Store Multiple Images)

```php
public function store(Request $request)
{
    $project = Project::create($request->only('title','description'));

    if ($request->hasFile('images')) {
        foreach ($request->images as $img) {
            $name = time().'_'.$img->getClientOriginalName();
            $img->move(public_path('uploads/projects'), $name);

            $project->images()->create(['image'=>$name]);
        }
    }

    return redirect()->back();
}
```

---

### ▶ Frontend ProjectController

```php
public function index()
{
    $projects = Project::latest()->get();
    return view('frontend.projects.index', compact('projects'));
}

public function show($id)
{
    $project = Project::with('images')->findOrFail($id);
    return view('frontend.projects.show', compact('project'));
}
```

---

## 🧩 Step 5: Routes

```php
use App\Http\Controllers\Frontend\ProjectController as FrontProject;
use App\Http\Controllers\Admin\ProjectController as AdminProject;

Route::get('/', [FrontProject::class,'index']);
Route::get('/project/{id}', [FrontProject::class,'show']);

Route::post('/admin/project/store', [AdminProject::class,'store']);
```

---

## 🧩 Step 6: Blade Layout

```blade
<html>
<head><title>Portfolio</title></head>
<body>
@yield('content')
</body>
</html>
```

---

## 🧩 Step 7: Frontend Pages

### ▶ Project List

```blade
@foreach($projects as $project)
<a href="/project/{{ $project->id }}">
<h3>{{ $project->title }}</h3>
</a>
@endforeach
```

---

### ▶ Project Details (Multiple Image)

```blade
<img id="mainImage" src="{{ asset('uploads/projects/'.$project->images[0]->image) }}" width="400">

@foreach($project->images as $img)
<img src="{{ asset('uploads/projects/'.$img->image) }}" width="80" onclick="changeImage(this.src)">
@endforeach

<script>
function changeImage(src){ document.getElementById('mainImage').src = src }
</script>
```

---

## 🧩 Step 8: Admin Upload Form

```blade
<form method="POST" action="/admin/project/store" enctype="multipart/form-data">
@csrf
<input name="title"><br>
<textarea name="description"></textarea><br>
<input type="file" name="images[]" multiple><br>
<button>Save</button>
</form>
```

---

## 🎉 Final Result

✔ Professional Portfolio Website
✔ Admin can add projects with multiple images
✔ Frontend project listing & details page
✔ Clean Laravel structure

---

# 🧑‍💻 GitHub‑Ready Final Version (Laravel Portfolio)

এখন আমরা এই Portfolio Project‑টাকে **GitHub‑এ Upload করার জন্য 100% Professional Ready** করবো।
এই অংশটা follow করলে আপনার প্রজেক্ট **Job / Client / Team** সবাই বুঝতে পারবে 👍

---

## ✅ 1️⃣ Production‑Ready Folder Clean‑up

### ❌ GitHub‑এ যাবে না (Automatically Ignore)

Laravel already standard যেগুলো GitHub‑এ দেয়া হয় না:

* `/vendor`
* `/node_modules`
* `.env`
* `/storage/*.log`

এগুলোর জন্য `.gitignore` আগে থেকেই আছে ✔

---

## ✅ 2️⃣ .env.example ঠিক করা (VERY IMPORTANT)

👉 GitHub‑এ **আসল .env দিবেন না**
👉 শুধু example দিবেন

```env
APP_NAME=LaravelPortfolio
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

DB_DATABASE=portfolio
DB_USERNAME=root
DB_PASSWORD=
```

📌 Client / Recruiter এটা দেখে বুঝবে কীভাবে run করতে হবে

---

## ✅ 3️⃣ Database Seed (Optional but Pro)

### Admin User Seeder

```bash
php artisan make:seeder AdminUserSeeder
```

```php
User::create([
    'name' => 'Admin',
    'email' => 'admin@mail.com',
    'password' => bcrypt('password'),
]);
```

```bash
php artisan db:seed --class=AdminUserSeeder
```

👉 Recruiter project run করেই login করতে পারবে

---

## ✅ 4️⃣ README.md (MOST IMPORTANT)

👉 **Good README = Professional Developer**

````md
# Laravel Portfolio Website

A professional portfolio website built with Laravel.

## Features
- Admin Panel
- Project CRUD
- Multiple Images per Project
- Frontend Portfolio Pages

## Installation
```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
````

## Admin Login

* Email: [admin@mail.com](mailto:admin@mail.com)
* Password: password

````

---

## ✅ 5️⃣ Screenshot Folder (Highly Recommended)

```text
/screenshots
 ├── home.png
 ├── projects.png
 ├── project-details.png
 └── admin-dashboard.png
````

👉 README‑তে image দিলে recruiter impressed হয়

```md
![Home](screenshots/home.png)
```

---

## ✅ 6️⃣ Git Init & First Commit

```bash
git init
git add .
git commit -m "Initial commit: Laravel portfolio website"
```

---

## ✅ 7️⃣ Push to GitHub

```bash
git branch -M main
git remote add origin https://github.com/yourusername/laravel-portfolio.git
git push -u origin main
```

---

## 🏆 Final GitHub Folder Look

```text
laravel-portfolio/
├── app/
├── database/
├── public/
├── resources/
├── routes/
├── screenshots/
├── README.md
├── .env.example
└── composer.json
```

---

## 🎯 Why This Is GitHub‑Ready

✔ Clean commit history
✔ No sensitive data
✔ Easy installation
✔ Screenshots included
✔ Professional README

👉 This is **job‑interview standard** Laravel project

---

## 🚀 Next Level (Optional)

If you want to stand out even more:

* Live demo (Render / Railway)
* Tag releases (v1.0.0)
* Issues & Projects tab
* Add LICENSE file

---

### 💡 এখন আপনি confidently বলতে পারেন:

> “This is a production‑ready Laravel portfolio project.”

আপনি চাইলে পরের ধাপে আমি দিতে পারি:

* ✅ **Live Deployment Guide**
* ✅ **Interview‑ready explanation (how to explain this project)**
* ✅ **React Frontend version**

শুধু বলুন 👍
