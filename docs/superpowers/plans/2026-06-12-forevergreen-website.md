# Forevergreen Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a 4-page static informational website for Forevergreen Landscape Management.

**Architecture:** Pure static HTML files with Tailwind CSS loaded via CDN. Each page is self-contained with its own navbar and footer. No build step, no framework, no backend.

**Tech Stack:** HTML5, Tailwind CSS (CDN), vanilla JS (mobile menu only), Netlify (deploy)

---

## File Map

| File | Purpose |
|---|---|
| `index.html` | Home page — hero, services highlights, CTA |
| `services.html` | Services detail page — one card per service |
| `about.html` | About page — company story, owner |
| `contact.html` | Contact page — phone, email, location, hours |
| `css/custom.css` | Custom CSS overrides (minimal) |
| `img/ForeverGreenLandscapeLogo.png` | Logo (copy from repo root) |
| `.gitignore` | Standard web .gitignore |

**Colors used throughout:**
- Dark green: `#2d6a2d` (Tailwind config: `fg-green`)
- Gold/orange: `#f5a623` (Tailwind config: `fg-gold`)
- Body text: `#333333`
- Background: white

---

## Task 1: Project Setup

**Files:**
- Create: `css/custom.css`
- Create: `.gitignore`
- Create: `img/` directory (copy logo in)

- [ ] **Step 1: Create the css directory and custom.css**

Create `css/custom.css` with this content:
```css
/* Custom overrides for Forevergreen site */
html {
  scroll-behavior: smooth;
}
```

- [ ] **Step 2: Create .gitignore**

Create `.gitignore` with this content:
```
.DS_Store
Thumbs.db
*.log
```

- [ ] **Step 3: Copy the logo into the img directory**

Run (PowerShell):
```powershell
New-Item -ItemType Directory -Force -Path img
Copy-Item -Path "C:\git\ForeverGreenLandscapeLogo.png" -Destination "img\ForeverGreenLandscapeLogo.png"
```

- [ ] **Step 4: Commit**

```bash
git add css/custom.css .gitignore img/ForeverGreenLandscapeLogo.png
git commit -m "chore: project setup — assets, css, gitignore"
```

---

## Task 2: Home Page (index.html)

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create index.html**

Create `index.html` with this complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Forevergreen Landscape Management — Harrodsburg, KY</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            'fg-green': '#2d6a2d',
            'fg-gold': '#f5a623',
          }
        }
      }
    }
  </script>
  <link rel="stylesheet" href="css/custom.css">
</head>
<body class="text-gray-700">

  <!-- Navbar -->
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
      <a href="index.html">
        <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen Landscape Management" class="h-16">
      </a>
      <div class="hidden md:flex gap-8 font-medium">
        <a href="index.html" class="text-fg-gold font-bold transition-colors">Home</a>
        <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <button id="menu-btn" class="md:hidden text-fg-green focus:outline-none">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>
    <div id="mobile-menu" class="hidden md:hidden bg-white px-4 pb-4 flex flex-col gap-3 font-medium border-t border-gray-100">
      <a href="index.html" class="text-fg-gold font-bold">Home</a>
      <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
      <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
      <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
    </div>
  </nav>

  <!-- Hero -->
  <section class="bg-white py-24 px-4 text-center">
    <h1 class="text-4xl md:text-5xl font-bold text-fg-green mb-4">Professional Lawn Care &amp; Landscaping</h1>
    <p class="text-lg text-gray-500 mb-8">Serving Harrodsburg, Kentucky and surrounding areas</p>
    <a href="contact.html" class="bg-fg-gold text-white font-bold px-8 py-3 rounded-full hover:bg-yellow-500 transition-colors">Contact Us</a>
  </section>

  <!-- Services Highlights -->
  <section class="bg-gray-50 py-16 px-4">
    <div class="max-w-6xl mx-auto">
      <h2 class="text-3xl font-bold text-fg-green text-center mb-10">What We Do</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div class="bg-white rounded-xl shadow-sm p-6 text-center border border-gray-100">
          <div class="text-4xl mb-3">🌿</div>
          <h3 class="font-bold text-fg-green text-lg mb-2">Lawn Mowing</h3>
          <p class="text-gray-500 text-sm">Reliable, consistent mowing to keep your lawn looking its best.</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-6 text-center border border-gray-100">
          <div class="text-4xl mb-3">🪵</div>
          <h3 class="font-bold text-fg-green text-lg mb-2">Mulching</h3>
          <p class="text-gray-500 text-sm">Fresh mulch to protect your landscaping and boost curb appeal.</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-6 text-center border border-gray-100">
          <div class="text-4xl mb-3">🌳</div>
          <h3 class="font-bold text-fg-green text-lg mb-2">Landscaping Design</h3>
          <p class="text-gray-500 text-sm">Custom designs to transform your outdoor space.</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-6 text-center border border-gray-100">
          <div class="text-4xl mb-3">✂️</div>
          <h3 class="font-bold text-fg-green text-lg mb-2">Trimming</h3>
          <p class="text-gray-500 text-sm">Precise trimming of hedges, shrubs, and edges for a clean finish.</p>
        </div>
        <div class="bg-white rounded-xl shadow-sm p-6 text-center border border-gray-100">
          <div class="text-4xl mb-3">🌱</div>
          <h3 class="font-bold text-fg-green text-lg mb-2">Crabgrass Control</h3>
          <p class="text-gray-500 text-sm">Effective treatment to keep your lawn healthy and weed-free.</p>
        </div>
      </div>
      <div class="text-center mt-10">
        <a href="services.html" class="bg-fg-green text-white font-bold px-8 py-3 rounded-full hover:bg-green-800 transition-colors">View All Services</a>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-fg-green text-white py-10 px-4">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
      <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen" class="h-14 brightness-0 invert">
      <div class="flex flex-col md:flex-row gap-6 font-medium text-sm">
        <a href="index.html" class="text-fg-gold font-bold">Home</a>
        <a href="services.html" class="hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <div class="text-sm text-center md:text-right text-green-200">
        <p>(859) 734-0202</p>
        <p>forevergreen36@yahoo.com</p>
        <p>Harrodsburg, KY</p>
      </div>
    </div>
    <p class="text-center text-xs text-green-400 mt-6">&copy; 2026 Forevergreen Landscape Management. All rights reserved.</p>
  </footer>

  <script>
    document.getElementById('menu-btn').addEventListener('click', function () {
      document.getElementById('mobile-menu').classList.toggle('hidden');
    });
  </script>
</body>
</html>
```

- [ ] **Step 2: Open in browser and verify**

Open `index.html` in a browser. Check:
- Logo appears in navbar top-left
- Desktop nav links appear top-right
- Hero section has green heading and gold "Contact Us" button
- 5 service cards appear in a grid
- Footer is dark green with logo, links, and contact info
- On mobile width: hamburger icon appears and opens the mobile menu when clicked

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add home page"
```

---

## Task 3: Services Page (services.html)

**Files:**
- Create: `services.html`

- [ ] **Step 1: Create services.html**

Create `services.html` with this complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Services — Forevergreen Landscape Management</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            'fg-green': '#2d6a2d',
            'fg-gold': '#f5a623',
          }
        }
      }
    }
  </script>
  <link rel="stylesheet" href="css/custom.css">
</head>
<body class="text-gray-700">

  <!-- Navbar -->
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
      <a href="index.html">
        <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen Landscape Management" class="h-16">
      </a>
      <div class="hidden md:flex gap-8 font-medium">
        <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="text-fg-gold font-bold transition-colors">Services</a>
        <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <button id="menu-btn" class="md:hidden text-fg-green focus:outline-none">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>
    <div id="mobile-menu" class="hidden md:hidden bg-white px-4 pb-4 flex flex-col gap-3 font-medium border-t border-gray-100">
      <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
      <a href="services.html" class="text-fg-gold font-bold">Services</a>
      <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
      <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
    </div>
  </nav>

  <!-- Page Header -->
  <section class="bg-fg-green text-white py-16 px-4 text-center">
    <h1 class="text-4xl font-bold mb-2">Our Services</h1>
    <p class="text-green-200">Professional lawn care and landscaping for Harrodsburg and surrounding areas</p>
  </section>

  <!-- Services List -->
  <section class="py-16 px-4">
    <div class="max-w-4xl mx-auto space-y-6">

      <div class="flex gap-5 items-start bg-white rounded-xl shadow-sm border border-gray-100 p-6">
        <div class="text-4xl flex-shrink-0">🌿</div>
        <div>
          <h2 class="text-xl font-bold text-fg-green mb-2">Lawn Mowing</h2>
          <p class="text-gray-500">Reliable, consistent mowing services to keep your lawn looking its best all season long. We handle lawns of all sizes with professional-grade equipment and attention to detail.</p>
        </div>
      </div>

      <div class="flex gap-5 items-start bg-white rounded-xl shadow-sm border border-gray-100 p-6">
        <div class="text-4xl flex-shrink-0">🪵</div>
        <div>
          <h2 class="text-xl font-bold text-fg-green mb-2">Mulching</h2>
          <p class="text-gray-500">Fresh mulch installation to protect your plants and landscaping, retain soil moisture, suppress weeds, and dramatically improve your home's curb appeal.</p>
        </div>
      </div>

      <div class="flex gap-5 items-start bg-white rounded-xl shadow-sm border border-gray-100 p-6">
        <div class="text-4xl flex-shrink-0">🌳</div>
        <div>
          <h2 class="text-xl font-bold text-fg-green mb-2">Landscaping Design</h2>
          <p class="text-gray-500">Custom landscape design services to transform your outdoor space into something beautiful and functional. From planning to installation, we bring your vision to life.</p>
        </div>
      </div>

      <div class="flex gap-5 items-start bg-white rounded-xl shadow-sm border border-gray-100 p-6">
        <div class="text-4xl flex-shrink-0">✂️</div>
        <div>
          <h2 class="text-xl font-bold text-fg-green mb-2">Trimming</h2>
          <p class="text-gray-500">Precise trimming of hedges, shrubs, and lawn edges to give your property a clean, polished finish that sets it apart from the rest of the neighborhood.</p>
        </div>
      </div>

      <div class="flex gap-5 items-start bg-white rounded-xl shadow-sm border border-gray-100 p-6">
        <div class="text-4xl flex-shrink-0">🌱</div>
        <div>
          <h2 class="text-xl font-bold text-fg-green mb-2">Crabgrass Control</h2>
          <p class="text-gray-500">Targeted crabgrass treatment and prevention to protect your lawn from invasive weeds, keeping your grass healthy, green, and weed-free throughout the season.</p>
        </div>
      </div>

    </div>

    <div class="text-center mt-12">
      <a href="contact.html" class="bg-fg-gold text-white font-bold px-8 py-3 rounded-full hover:bg-yellow-500 transition-colors">Get in Touch</a>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-fg-green text-white py-10 px-4">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
      <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen" class="h-14 brightness-0 invert">
      <div class="flex flex-col md:flex-row gap-6 font-medium text-sm">
        <a href="index.html" class="hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="text-fg-gold font-bold">Services</a>
        <a href="about.html" class="hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <div class="text-sm text-center md:text-right text-green-200">
        <p>(859) 734-0202</p>
        <p>forevergreen36@yahoo.com</p>
        <p>Harrodsburg, KY</p>
      </div>
    </div>
    <p class="text-center text-xs text-green-400 mt-6">&copy; 2026 Forevergreen Landscape Management. All rights reserved.</p>
  </footer>

  <script>
    document.getElementById('menu-btn').addEventListener('click', function () {
      document.getElementById('mobile-menu').classList.toggle('hidden');
    });
  </script>
</body>
</html>
```

- [ ] **Step 2: Open in browser and verify**

Open `services.html` in a browser. Check:
- "Services" link in navbar is highlighted gold (active state)
- Green page header banner at top
- 5 service cards appear as rows with emoji icon and description
- "Get in Touch" gold button at the bottom
- Footer matches home page

- [ ] **Step 3: Commit**

```bash
git add services.html
git commit -m "feat: add services page"
```

---

## Task 4: About Page (about.html)

**Files:**
- Create: `about.html`

- [ ] **Step 1: Create about.html**

Create `about.html` with this complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>About — Forevergreen Landscape Management</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            'fg-green': '#2d6a2d',
            'fg-gold': '#f5a623',
          }
        }
      }
    }
  </script>
  <link rel="stylesheet" href="css/custom.css">
</head>
<body class="text-gray-700">

  <!-- Navbar -->
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
      <a href="index.html">
        <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen Landscape Management" class="h-16">
      </a>
      <div class="hidden md:flex gap-8 font-medium">
        <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="text-fg-gold font-bold transition-colors">About</a>
        <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <button id="menu-btn" class="md:hidden text-fg-green focus:outline-none">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>
    <div id="mobile-menu" class="hidden md:hidden bg-white px-4 pb-4 flex flex-col gap-3 font-medium border-t border-gray-100">
      <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
      <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
      <a href="about.html" class="text-fg-gold font-bold">About</a>
      <a href="contact.html" class="text-fg-green hover:text-fg-gold transition-colors">Contact</a>
    </div>
  </nav>

  <!-- Page Header -->
  <section class="bg-fg-green text-white py-16 px-4 text-center">
    <h1 class="text-4xl font-bold mb-2">About Us</h1>
    <p class="text-green-200">Dedicated to keeping Harrodsburg beautiful, one lawn at a time</p>
  </section>

  <!-- About Content -->
  <section class="py-16 px-4">
    <div class="max-w-3xl mx-auto space-y-10">

      <div>
        <h2 class="text-2xl font-bold text-fg-green mb-3">Who We Are</h2>
        <p class="text-gray-500 leading-relaxed">Forevergreen Landscape Management is a locally owned and operated lawn care and landscaping company based in Harrodsburg, Kentucky. We take pride in delivering reliable, high-quality service to homeowners and businesses throughout the area.</p>
      </div>

      <div>
        <h2 class="text-2xl font-bold text-fg-green mb-3">Our Mission</h2>
        <p class="text-gray-500 leading-relaxed">Our goal is simple — to keep your property looking its best, every season. Whether it's a weekly mow, a full landscape redesign, or targeted weed control, we bring professionalism and care to every job.</p>
      </div>

      <div>
        <h2 class="text-2xl font-bold text-fg-green mb-3">Meet the Owner</h2>
        <p class="text-gray-500 leading-relaxed">Willie Cheek founded Forevergreen Landscape Management with a commitment to quality work and honest service. With years of hands-on experience in lawn care and landscaping, Willie and his team are dedicated to making your outdoor space something you're proud of.</p>
      </div>

      <div class="bg-fg-green text-white rounded-xl p-10 text-center">
        <p class="text-lg font-medium mb-5">Ready to get started?</p>
        <a href="contact.html" class="bg-fg-gold text-white font-bold px-8 py-3 rounded-full hover:bg-yellow-500 transition-colors inline-block">Contact Us Today</a>
      </div>

    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-fg-green text-white py-10 px-4">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
      <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen" class="h-14 brightness-0 invert">
      <div class="flex flex-col md:flex-row gap-6 font-medium text-sm">
        <a href="index.html" class="hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="text-fg-gold font-bold">About</a>
        <a href="contact.html" class="hover:text-fg-gold transition-colors">Contact</a>
      </div>
      <div class="text-sm text-center md:text-right text-green-200">
        <p>(859) 734-0202</p>
        <p>forevergreen36@yahoo.com</p>
        <p>Harrodsburg, KY</p>
      </div>
    </div>
    <p class="text-center text-xs text-green-400 mt-6">&copy; 2026 Forevergreen Landscape Management. All rights reserved.</p>
  </footer>

  <script>
    document.getElementById('menu-btn').addEventListener('click', function () {
      document.getElementById('mobile-menu').classList.toggle('hidden');
    });
  </script>
</body>
</html>
```

- [ ] **Step 2: Open in browser and verify**

Open `about.html` in a browser. Check:
- "About" link in navbar is highlighted gold (active state)
- Green page header banner
- Three content sections: Who We Are, Our Mission, Meet the Owner
- Dark green CTA box at the bottom with gold button
- Footer matches other pages

- [ ] **Step 3: Commit**

```bash
git add about.html
git commit -m "feat: add about page"
```

---

## Task 5: Contact Page (contact.html)

**Files:**
- Create: `contact.html`

> **Note:** Hours below are placeholder — confirm actual hours with Willie Cheek before launch.

- [ ] **Step 1: Create contact.html**

Create `contact.html` with this complete content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contact — Forevergreen Landscape Management</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            'fg-green': '#2d6a2d',
            'fg-gold': '#f5a623',
          }
        }
      }
    }
  </script>
  <link rel="stylesheet" href="css/custom.css">
</head>
<body class="text-gray-700">

  <!-- Navbar -->
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
      <a href="index.html">
        <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen Landscape Management" class="h-16">
      </a>
      <div class="hidden md:flex gap-8 font-medium">
        <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="text-fg-gold font-bold transition-colors">Contact</a>
      </div>
      <button id="menu-btn" class="md:hidden text-fg-green focus:outline-none">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>
    <div id="mobile-menu" class="hidden md:hidden bg-white px-4 pb-4 flex flex-col gap-3 font-medium border-t border-gray-100">
      <a href="index.html" class="text-fg-green hover:text-fg-gold transition-colors">Home</a>
      <a href="services.html" class="text-fg-green hover:text-fg-gold transition-colors">Services</a>
      <a href="about.html" class="text-fg-green hover:text-fg-gold transition-colors">About</a>
      <a href="contact.html" class="text-fg-gold font-bold">Contact</a>
    </div>
  </nav>

  <!-- Page Header -->
  <section class="bg-fg-green text-white py-16 px-4 text-center">
    <h1 class="text-4xl font-bold mb-2">Contact Us</h1>
    <p class="text-green-200">We'd love to hear from you</p>
  </section>

  <!-- Contact Info -->
  <section class="py-16 px-4">
    <div class="max-w-3xl mx-auto">

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-center mb-10">

        <div class="bg-white rounded-xl shadow-sm border border-gray-100 p-6">
          <div class="text-3xl mb-3">📞</div>
          <h3 class="font-bold text-fg-green mb-2">Phone</h3>
          <a href="tel:8597340202" class="text-gray-500 hover:text-fg-gold transition-colors">(859) 734-0202</a>
        </div>

        <div class="bg-white rounded-xl shadow-sm border border-gray-100 p-6">
          <div class="text-3xl mb-3">✉️</div>
          <h3 class="font-bold text-fg-green mb-2">Email</h3>
          <a href="mailto:forevergreen36@yahoo.com" class="text-gray-500 hover:text-fg-gold transition-colors break-all text-sm">forevergreen36@yahoo.com</a>
        </div>

        <div class="bg-white rounded-xl shadow-sm border border-gray-100 p-6">
          <div class="text-3xl mb-3">📍</div>
          <h3 class="font-bold text-fg-green mb-2">Location</h3>
          <p class="text-gray-500">Harrodsburg, Kentucky</p>
        </div>

      </div>

      <div class="bg-gray-50 rounded-xl p-8 text-center">
        <h2 class="text-2xl font-bold text-fg-green mb-4">Hours</h2>
        <div class="text-gray-500 space-y-1">
          <p>Monday – Friday: 8:00 AM – 6:00 PM</p>
          <p>Saturday: 8:00 AM – 4:00 PM</p>
          <p>Sunday: Closed</p>
        </div>
        <p class="text-xs text-gray-400 mt-3">Hours may vary by season</p>
      </div>

    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-fg-green text-white py-10 px-4">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
      <img src="img/ForeverGreenLandscapeLogo.png" alt="Forevergreen" class="h-14 brightness-0 invert">
      <div class="flex flex-col md:flex-row gap-6 font-medium text-sm">
        <a href="index.html" class="hover:text-fg-gold transition-colors">Home</a>
        <a href="services.html" class="hover:text-fg-gold transition-colors">Services</a>
        <a href="about.html" class="hover:text-fg-gold transition-colors">About</a>
        <a href="contact.html" class="text-fg-gold font-bold">Contact</a>
      </div>
      <div class="text-sm text-center md:text-right text-green-200">
        <p>(859) 734-0202</p>
        <p>forevergreen36@yahoo.com</p>
        <p>Harrodsburg, KY</p>
      </div>
    </div>
    <p class="text-center text-xs text-green-400 mt-6">&copy; 2026 Forevergreen Landscape Management. All rights reserved.</p>
  </footer>

  <script>
    document.getElementById('menu-btn').addEventListener('click', function () {
      document.getElementById('mobile-menu').classList.toggle('hidden');
    });
  </script>
</body>
</html>
```

- [ ] **Step 2: Open in browser and verify**

Open `contact.html` in a browser. Check:
- "Contact" link in navbar is highlighted gold (active state)
- Green page header banner
- Three info cards: phone (clickable), email (clickable), location
- Hours section below cards
- Footer matches other pages
- Click the phone number — it should trigger a phone call prompt on mobile

- [ ] **Step 3: Commit**

```bash
git add contact.html
git commit -m "feat: add contact page"
```

---

## Task 6: Final Review & Deploy Setup

**Files:**
- No new files

- [ ] **Step 1: Cross-page navigation check**

Open `index.html` in a browser and click every nav link on every page. Verify:
- All 4 pages load correctly
- The active page link is always gold
- Logo on every page links back to home
- Footer links work on all pages
- Mobile hamburger works on all pages

- [ ] **Step 2: Create GitHub repo and push**

Run (PowerShell):
```powershell
gh repo create forevergreen-website --public --source . --remote origin --push
```

If `gh` is not authenticated, run `gh auth login` first.

- [ ] **Step 3: Connect to Netlify**

1. Go to [netlify.com](https://netlify.com) and log in
2. Click **Add new site → Import an existing project**
3. Choose **GitHub** and select the `forevergreen-website` repo
4. Build command: *(leave blank)*
5. Publish directory: `.` (root)
6. Click **Deploy site**

- [ ] **Step 4: Verify live site**

Once Netlify finishes deploying, open the generated `.netlify.app` URL and verify all 4 pages load correctly with styles and logo.
