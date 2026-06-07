# Cloudflare Pages Deployment Guide

## Prerequisites

- Cloudflare account (free): [cloudflare.com](https://cloudflare.com)
- Wrangler CLI installed: `npm install -g wrangler`
- AstroJS project with Cloudflare adapter configured

## Cloudflare Adapter Setup

Ensure your `astro.config.mjs` uses the Cloudflare adapter:

```js
import { defineConfig } from 'astro/config';
import tailwind from '@astrojs/tailwind';
import cloudflare from '@astrojs/cloudflare';

export default defineConfig({
  output: 'static',
  adapter: cloudflare(),
  integrations: [tailwind()],
  site: 'https://yourdomain.com',
});
```

---

## Deploy via CLI (Recommended for First Deploy)

```bash
# Authenticate with Cloudflare
wrangler login

# Build the site
npm run build

# Deploy to Cloudflare Pages
wrangler pages deploy dist --project-name your-project-name
```

Your site will be live at `https://your-project-name.pages.dev` immediately.

---

## Deploy via Git Integration

1. Push your project to GitHub
2. Go to Cloudflare Dashboard → Pages → Create a project
3. Connect to GitHub → Select your repository
4. Configure build settings:
   - Framework preset: **Astro**
   - Build command: `npm run build`
   - Build output directory: `dist`
5. Click Deploy

Every `git push` to your main branch now triggers an automatic deployment.

---

## Cloudflare Pages vs Workers

| | Pages | Workers |
|---|---|---|
| Best for | Static sites, SSG | Edge functions, dynamic APIs |
| Pricing | Free (unlimited requests) | Free tier: 100k req/day |
| Setup | Simple | More complex |
| Use case | Micro-tool sites | Sites needing server-side logic |

For micro-tool websites, **Pages is always sufficient**.

---

## Fixing the pages.dev Duplicate Content Issue

When you add a custom domain to Cloudflare Pages, your site is accessible at both `https://yourdomain.com` and `https://your-project.pages.dev`. Fix it:

**Option A — Disable the pages.dev subdomain (Recommended):**
1. Cloudflare Dashboard → Pages → Your project → Settings → General
2. Under "Enable access to your deployment via your pages.dev subdomain" → Disable

**Option B — Add a redirect rule** returning a 301 from `*.pages.dev` to your custom domain.

---

## Connecting Your Custom Domain

1. Buy your domain (after your site is working locally)
2. Cloudflare Dashboard → Pages → Your project → Custom Domains → Set up a custom domain
3. Update your domain registrar's nameservers to Cloudflare's nameservers
4. Wait for propagation — usually 15 minutes to 1 hour

Cloudflare automatically provisions a free SSL certificate.

---

## The npm run deploy Shortcut

```json
{
  "scripts": {
    "deploy": "npm run build && wrangler pages deploy dist --project-name your-project-name"
  }
}
```

Workflow:
```bash
git add .
git commit -m "feat: add dark mode"
npm run deploy
```

---

## Google Analytics Setup

Add to your `Layout.astro`:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```
