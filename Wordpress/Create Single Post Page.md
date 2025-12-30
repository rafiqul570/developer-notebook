চমৎকার প্রশ্ন Rafiqul 👍
তুমি যেটা HTML দিয়ে **Project Details / Single Project Page** বানিয়েছো, সেটাকেই আমরা এখন **WordPress + Elementor Pro + CPT + ACF** দিয়ে **ডাইনামিক Single Post Page** বানাবো।

নিচে **A–Z Bangla Step-by-Step Guide** দিলাম—একদম HTML layout → WordPress Dynamic পর্যন্ত।

---

# 🎯 Final Goal

HTML Project Details Page ➜
**WordPress Custom Post Type (Project)** ➜
**ACF দিয়ে Dynamic Data** ➜
**Elementor Pro Single Template**

---

## 🧱 Step-1: Custom Post Type (CPT) তৈরি করা – Project

### Option A (Beginner Friendly) ✅

Plugin ব্যবহার করো:

🔹 **CPT UI** plugin install করো

**CPT UI → Add/Edit Post Types**

| Field          | Value                    |
| -------------- | ------------------------ |
| Post Type Slug | `project`                |
| Plural Label   | Projects                 |
| Singular Label | Project                  |
| Public         | true                     |
| Has Archive    | true                     |
| Supports       | Title, Editor, Thumbnail |

👉 **Save Post Type**

📌 এখন Dashboard এ **Projects** নামে menu আসবে

---

## 🧱 Step-2: Advanced Custom Fields (ACF) Setup

🔹 **ACF Pro** (recommended) অথবা Free install করো

### ACF → Add New → Field Group

**Name:** Project Details

### 🔸 Fields বানাও (HTML অনুযায়ী)

| Label            | Field Name       | Type     |
| ---------------- | ---------------- | -------- |
| Project Subtitle | project_subtitle | Text     |
| Project Overview | project_overview | Textarea |
| Features         | project_features | Repeater |
| Feature Text     | feature_text     | Text     |
| Backend Tech     | backend_tech     | Text     |
| Frontend Tech    | frontend_tech    | Text     |
| Tools            | project_tools    | Text     |
| Client Name      | client_name      | Text     |
| Category         | project_category | Text     |
| Duration         | project_duration | Text     |
| Version          | project_version  | Text     |
| Live URL         | live_url         | URL      |
| GitHub URL       | github_url       | URL      |
| Gallery          | project_gallery  | Gallery  |

**Location Rule:**
`Post Type is equal to Project`

👉 Save

---

## 🧱 Step-3: Project Post Data Insert

**Dashboard → Projects → Add New**

* Title → *Laravel eCommerce Website*
* Featured Image → Main Banner Image
* ACF fields পূরণ করো
* Gallery তে screenshots যোগ করো
* Publish

---

## 🎨 Step-4: Elementor Pro Single Template তৈরি করা

📌 Elementor Pro লাগবে (Dynamic Content এর জন্য)

### Elementor → Theme Builder → Add

**Choose:** Single Post
**Post Type:** Project

---

## 🧱 Step-5: Navbar & Footer

### Header

* Theme: **Hello Elementor**
* Elementor Header Template ব্যবহার করো
* Nav Menu widget → Home | Projects | Hire Me

### Footer

* Simple Text widget

```
© 2025 Rafiqul Islam — Laravel Developer
```

---

## 🧱 Step-6: Banner Section (HTML Banner Equivalent)

Elementor Section:

* Background Color → `#0d6efd`
* Padding → Top/Bottom 80px

### Widgets:

1️⃣ **Post Title** (Dynamic)
2️⃣ **Text Editor**

* Dynamic → ACF → `project_subtitle`

---

## 🧱 Step-7: Main Content Layout (2 Column)

**Section → 2 Columns (8 / 4)**

---

## 🔹 Left Column (Content)

### 1️⃣ Project Overview

* Heading → “Project Overview”
* Text Editor → Dynamic → `project_overview`

---

### 2️⃣ Features List

* Heading → “Features”
* Repeater Field দেখানোর জন্য:

**Dynamic Field widget**

* Source → ACF Repeater
* Field → `project_features`
* Sub Field → `feature_text`

OR

* Icon List (Manual)

---

### 3️⃣ Technologies Used

Text Editor:

```
Backend: {{backend_tech}}
Frontend: {{frontend_tech}}
Tools: {{project_tools}}
```

Dynamic → ACF Fields bind করো

---

### 4️⃣ Project Screenshots

* **Gallery Widget**
* Dynamic → ACF Gallery → `project_gallery`

---

## 🔹 Right Column (Sidebar)

### Inner Section

* Background: White
* Padding: 20
* Border Radius: 8
* Box Shadow: Light

### Widgets:

* Heading → Project Info
* Text Editor (Dynamic):

```
Client: {{client_name}}
Category: {{project_category}}
Duration: {{project_duration}}
Version: {{project_version}}
```

---

### Buttons

1️⃣ Button → Live Preview
Dynamic Link → `live_url`

2️⃣ Button → GitHub Code
Dynamic Link → `github_url`

3️⃣ Button → Back
Link → `/projects/`

---

## 🔗 Step-8: Archive Page (projects.html alternative)

**Elementor → Theme Builder → Archive**

* Post Type → Project
* Use:

  * Loop Grid / Posts Widget
  * Click → Goes to Single Project Page

URL হবে:

```
yourdomain.com/project/laravel-ecommerce-website
```

---

## ✅ Final Result

✔ HTML Design = Elementor Layout
✔ Static Text = ACF Dynamic
✔ single-project.html = `single-project.php` (Elementor)
✔ Fully SEO Friendly
✔ Reusable for unlimited projects

---

## 🧠 Pro Tips (তোমার Level অনুযায়ী)

* Schema (Project) SEO plugin দিয়ে add করো
* Lazy Load gallery images
* Use Breadcrumb (RankMath / Yoast)
* Custom Slug: `/projects/project-name`

---

## 🔥 তুমি চাইলে পরের ধাপে:

* Live Demo দেখানো
* GitHub auto embed
* Project Filter (AJAX)
* Dark Mode
* Elementor Loop Grid Card Design

বললেই আমি next step বানিয়ে দেবো 👌
