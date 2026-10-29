# Project Development Log: kimbaillie.com

**Domain:** `kimbaillie.com` / `www.kimbaillie.com`  
**Repository:** [github.com/FloralArtOnline/kimbaillie-site](https://github.com/FloralArtOnline/kimbaillie-site)  
**Production Host:** Cloudflare Pages (`kimbaillie-site.pages.dev`)  
**Architecture:** Astro 5 (Static Site Generation)  

---

## 1. Project Background & Migration Objectives
* **Goal:** Migrate `kimbaillie.com` away from legacy WordPress on GreenGeeks into an ultra-fast, zero-maintenance static personal portal hosted on Cloudflare Pages ($0/mo hosting).
* **Core Purpose:** Serve as the executive hub connecting visitors to Kim Baillie's primary ventures around the world:
  1. **Public Speaking & Presentation Coaching** (`talkinginpublic.com`)
  2. **Executive & Business Mentoring (Inside Exec Podcast)** (`inside-exec.com`)
  3. **Floral Art & Flower Arranging** (`floralartonline.com` / `floralartreview.com`)
  4. **Book Repair & Conservation** (`book-repair.com`)
  5. **Thinking Out Loud** (Reflections and management perspectives)
* **URL Preservation:** Ensure all existing WordPress permalinks (`/public-speaking-tips/`, `/executive-and-business-mentoring/`, `/flower-arranging/`, `/book-repairs/`, `/thinking-out-loud/`, and `/privacy-policy/`) resolve with zero broken links.

---

## 2. Technical Milestones & Architecture

### Phase 1: High-Resolution Media Preservation
* Extracted and preserved the original photography and branding assets into `public/images/`:
  * `speaking.jpg` (Public speaking coaching)
  * `inside-exec-logo.jpg` (Inside Exec podcast identity)
  * `floral-art.jpg` (International floral competition design)
  * `book-repair.jpg` (Book conservation workshop)

### Phase 2: Static Astro Architecture & Design
* **Layout & Theme:** Designed a modern, elegant executive theme in `src/styles/global.css` with responsive activity cards, hover transitions, and clean typography.
* **Component Engine:** Created `BaseLayout.astro` with Schema.org **`Person`** and **`WebSite`** structured data linking all primary web properties together for Google Knowledge Graph.
* **Permanent Route Preservation:**
  * `index.astro` (Hub portal featuring primary activity cards)
  * `public-speaking-tips.astro`
  * `executive-and-business-mentoring.astro`
  * `flower-arranging.astro`
  * `book-repairs.astro`
  * `thinking-out-loud.astro`
  * `privacy-policy.astro`

### Phase 3: Enterprise Security & Headers
* **Deployed `public/_headers`:**
  * `X-Frame-Options: DENY` & `frame-ancestors 'none'` (Anti-clickjacking protection)
  * `X-Content-Type-Options: nosniff` (Anti-MIME sniffing)
  * `Referrer-Policy: strict-origin-when-cross-origin`
  * `Permissions-Policy: camera=(), microphone=(), geolocation=()`
  * `Strict-Transport-Security: max-age=31536000; includeSubDomains; preload` (1-year HSTS)
  * Strict `Content-Security-Policy` (CSP)
* **Deployed `public/robots.txt`** and automated `sitemap-index.xml`.
* **Deployed `public/_redirects`** for legacy WordPress RSS feeds and system paths.

---

## 3. Maintenance Guide & Local Commands
* `npm run dev` — Launch local development server (`http://localhost:4321`).
* `npm run build` — Compile static production build (`dist/`).
* `git push origin main` — Push updates to GitHub; Cloudflare Pages automatically rebuilds and deploys in ~25 seconds.
