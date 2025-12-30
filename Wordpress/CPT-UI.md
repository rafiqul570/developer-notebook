নিশ্চিত 👍
আমি **CPT UI (Custom Post Type UI) – A to Z** খুব সহজ **বাংলা ভাষায়**, step-by-step ব্যাখ্যা করছি।
তুমি যেহেতু **WordPress + Elementor + Portfolio/Project** নিয়ে কাজ করো, তাই উদাহরণও সেইভাবেই দেবো।

---

## 🔹 CPT UI কী?

**CPT UI** হলো একটি WordPress plugin, যেটা দিয়ে **Custom Post Type** ও **Custom Taxonomy** তৈরি করা যায়—কোনো কোড ছাড়াই।

👉 যেমন:

* Portfolio
* Projects
* Services
* Testimonials
* Team Members
* Case Study

---

## 🔹 কেন CPT UI ব্যবহার করবো?

WordPress-এর ডিফল্ট:

* Post → Blog
* Page → Static Page

কিন্তু বাস্তবে দরকার হয়:

* আলাদা **Portfolio**
* আলাদা **Service**
* আলাদা **Project**

👉 CPT UI এগুলো আলাদা করে ম্যানেজ করতে সাহায্য করে।

---

## 🔹 CPT UI ইনস্টল করার নিয়ম

1. **Dashboard → Plugins → Add New**
2. Search: `Custom Post Type UI`
3. Install → Activate

ইনস্টল হলে Dashboard-এ দেখবে:

```
CPT UI
 ├ Add/Edit Post Types
 ├ Add/Edit Taxonomies
 └ Tools
```

---

# 🅰️ Custom Post Type (A–Z)

## 🅰️ Add/Edit Post Types

👉 নতুন Custom Post Type বানানোর জায়গা

---

## 🅱️ Basic Settings (সবচেয়ে গুরুত্বপূর্ণ)

### 🔹 Post Type Slug

```
portfolio
```

✔ ছোট হাতের
✔ space নেই
✔ URL-এ ব্যবহার হবে

---

### 🔹 Plural Label

```
Portfolios
```

Dashboard menu নাম

---

### 🔹 Singular Label

```
Portfolio
```

Single item নাম

---

## 🅲 Menu Settings

### 🔹 Show in Menu

✔ True রাখলে Dashboard-এ দেখাবে

### 🔹 Menu Position

```
20
```

Portfolio সাধারণত Pages এর নিচে ভালো

---

## 🅳 Supports (খুব গুরুত্বপূর্ণ)

✔ Title
✔ Editor (Description)
✔ Featured Image
✔ Excerpt

👉 Portfolio হলে এগুলো অবশ্যই টিক দিবে

---

## 🅴 Visibility Settings

### 🔹 Public

✔ True

### 🔹 Publicly Queryable

✔ True (Front-end এ দেখানোর জন্য)

---

## 🅵 URL & Rewrite

### 🔹 Rewrite

✔ True

### 🔹 Rewrite Slug

```
portfolio
```

👉 তাহলে URL হবে:

```
your-site.com/portfolio/project-name
```

---

## 🅶 Archive Page

### 🔹 Has Archive

✔ True

👉 তখন এই পেজ কাজ করবে:

```
your-site.com/portfolio
```

---

## 🅷 REST API

### 🔹 Show in REST

✔ True

👉 Elementor / Gutenberg / API ব্যবহার করতে চাইলে দরকার

---

## 🅸 Save Post Type

সব সেটিং শেষ হলে
👉 **Add Post Type** ক্লিক করো

---

# 🅰️ Custom Taxonomy (Category / Tag)

## 🅰️ Add/Edit Taxonomies

👉 Portfolio Category বানানোর জন্য

---

### 🔹 Taxonomy Slug

```
portfolio_category
```

### 🔹 Plural Label

```
Portfolio Categories
```

### 🔹 Singular Label

```
Portfolio Category
```

---

### 🔹 Attach to Post Type

✔ portfolio

---

### 🔹 Hierarchical

✔ True
👉 Category মতো কাজ করবে

---

### 🔹 Rewrite Slug

```
portfolio-category
```

---

### 🔹 Save Taxonomy

👉 **Add Taxonomy**

---

# 🅾️ Dashboard-এ কী দেখবে?

```
Portfolio
 ├ Add New
 ├ Portfolio Categories
```

---

# 🅿️ Single Portfolio Page কীভাবে দেখাবো?

## Elementor Pro থাকলে:

1. **Templates → Theme Builder**
2. **Single → Add**
3. Post Type → Portfolio
4. Design করো
5. Display Condition → All Portfolio

---

## Elementor Free হলে:

* Single template theme (Astra / Hello Elementor)
* অথবা `single-portfolio.php` ব্যবহার

---

# 🆀 Archive Portfolio Page

Elementor Pro:

* **Archive Template**
* Post Type → Portfolio

Free:

* `archive-portfolio.php`

---

# 🆁 SEO টিপস

✔ Slug ছোট রাখো
✔ Featured Image বাধ্যতামূলক
✔ Excerpt ব্যবহার করো
✔ Rank Math / Yoast compatible

---

# 🆂 CPT UI vs Code

| CPT UI            | Code         |
| ----------------- | ------------ |
| Beginner friendly | Advanced     |
| No coding         | Full control |
| Fast setup        | Manual       |

---

# 🆃 Common Problem & Solution

### ❌ 404 error

✔ Settings → Permalinks → Save

---

### ❌ Elementor এ Portfolio দেখা যাচ্ছে না

✔ Show in REST = True

---

# 🆄 Best Use Case (তোমার জন্য)

✔ Portfolio Website
✔ Client Projects
✔ Services
✔ Real Estate Listing
✔ Restaurant Menu

---

# 🆅 Want Next?

চাও তো আমি দিতে পারি:
1️⃣ **Portfolio full design (Elementor)**
2️⃣ **CPT UI + ACF complete guide**
3️⃣ **Single & Archive PHP file structure**
4️⃣ **SEO-friendly portfolio system**

👉 কোনটা চাই বলো 👍
