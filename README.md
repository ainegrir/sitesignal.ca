# SiteSignal Landing Page

**URL:** sitesignal.ca  
**Service:** Ontario construction permit intelligence for contractors  
**Built by:** L Consulting

---

## Files

```
sitesignal-landing/
├── index.html    ← Single-file landing page (self-contained)
└── README.md     ← This file
```

The entire site is one `index.html` file. No build step, no dependencies, no Node.js — just drag and deploy.

---

## Before Going Live

### 1. Replace Stripe link
Search for `#stripe-link` in `index.html` and replace with your actual Stripe Payment Link:

```
Find:    href="#stripe-link"
Replace: href="https://buy.stripe.com/YOUR_LINK_HERE"
```

There are **4 occurrences** (nav CTA, hero CTA, Starter plan, Growth plan).

### 2. Update contact email
Replace `hello@sitesignal.ca` and `unsubscribe@sitesignal.ca` with your real addresses.

### 3. Add favicon (optional)
Place a `favicon.ico` or `favicon.png` in the same folder and add to `<head>`:
```html
<link rel="icon" href="favicon.png" type="image/png" />
```

---

## Deployment: GitHub Pages (Free)

**Best for:** Quick launch, free hosting on `username.github.io/sitesignal`

### Steps

1. Create a new **public** GitHub repo (e.g. `sitesignal-landing`)
2. Push the files:
   ```bash
   cd sitesignal-landing
   git init
   git add .
   git commit -m "Initial SiteSignal landing page"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/sitesignal-landing.git
   git push -u origin main
   ```
3. In the repo → **Settings → Pages**
4. Source: **Deploy from a branch** → Branch: `main` → Folder: `/ (root)`
5. Click **Save** → site goes live at `https://YOUR_USERNAME.github.io/sitesignal-landing/`

### Custom domain (sitesignal.ca)

1. In repo root, create a file named `CNAME` containing:
   ```
   sitesignal.ca
   ```
2. At your DNS registrar (Namecheap, etc.), add:
   ```
   Type   Host   Value
   A      @      185.199.108.153
   A      @      185.199.109.153
   A      @      185.199.110.153
   A      @      185.199.111.153
   CNAME  www    YOUR_USERNAME.github.io
   ```
3. Back in GitHub Pages settings → add custom domain `sitesignal.ca`, enable **Enforce HTTPS**
4. DNS propagation takes 10–60 minutes

---

## Deployment: Namecheap Shared Hosting

**Best for:** Already have a Namecheap hosting plan

### Steps

1. Log into **Namecheap → cPanel → File Manager**
2. Navigate to `public_html` (or create a subdirectory like `public_html/sitesignal`)
3. Upload `index.html` directly
4. If hosting at root of domain: file goes in `public_html/index.html`
5. Site is live immediately at your domain

### Point domain to hosting

In Namecheap Dashboard → **Domain List → Manage → Nameservers**:
- Set to **Namecheap Web Hosting DNS** (if on Namecheap hosting)
- Or add A record pointing to your hosting server IP

---

## Deployment: Any Static Host

The file is 100% static — works anywhere:

| Host | Cost | Notes |
|------|------|-------|
| **GitHub Pages** | Free | Best option, HTTPS included |
| **Netlify** | Free tier | Drag-and-drop upload at netlify.com |
| **Cloudflare Pages** | Free | Fast global CDN |
| **Namecheap Hosting** | ~$3/mo | Already familiar if domain is there |
| **AWS S3 + CloudFront** | ~$1/mo | Most scalable |

---

## Netlify (Fastest Deploy)

1. Go to [netlify.com](https://netlify.com) → sign up free
2. Drag the `sitesignal-landing/` folder onto the deploy area
3. Site is live in ~30 seconds at a `*.netlify.app` URL
4. Add custom domain in Site Settings → Domain Management

---

## Performance Notes

- **No build step** — deploy as-is
- **Single HTTP request** for the HTML (fonts load from Google CDN)
- **Mobile responsive** — tested at 320px–1440px
- **No JS libraries** — the only script is the 8-line FAQ accordion
- Google Fonts (`Inter`) requires internet connection; for fully offline/air-gapped use, download the font and inline it

---

## Customization Quick Reference

| What | Where in index.html |
|------|-------------------|
| CTA button link | `href="#stripe-link"` (4 places) |
| Hero headline | `.hero__title` |
| Pricing amounts | `.pricing__price` in each card |
| FAQ questions/answers | `.faq__item` blocks |
| Company name in footer | `L Consulting` text |
| Primary color | `:root { --primary: #1a237e }` |
| Accent color | `:root { --accent: #0d47a1 }` |

---

*Built March 2025 · L Consulting*
