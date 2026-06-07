# MicroForge AI

> **Build profitable micro-tool websites with AI — zero coding knowledge required.**
> Deploy free. Rank on Google. Earn passively with AdSense.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Stack: AstroJS](https://img.shields.io/badge/Stack-AstroJS-FF5D01?logo=astro)](https://astro.build)
[![AI: Claude Code](https://img.shields.io/badge/AI-Claude%20Code-7C3AED)](https://claude.ai/code)
[![Hosting: Cloudflare](https://img.shields.io/badge/Hosting-Cloudflare-F38020?logo=cloudflare)](https://pages.cloudflare.com)

---

## What Is This?

**MicroForge AI** is an open-source playbook for building, deploying, and monetizing **micro-tool websites** using AI as your developer.

A micro-tool website solves one small, specific problem — an online ruler, a word counter, a percentage calculator, a color picker. These sites:

- Rank on Google for long-tail keywords (organic, free traffic)
- Require no backend, no database, no user accounts
- Run entirely on **free static hosting** (Cloudflare Pages)
- Earn passive income through **Google AdSense** on every page view

This repository documents the complete workflow: from finding a profitable niche to deploying a live, SEO-optimized, AdSense-ready website — built almost entirely by AI.

---

## The Win-Win Strategy

Build **1 micro-tool website per month** for 12 months straight.

| Outcome | Result |
|---|---|
| Even 1 site gets traffic | Passive AdSense income — potentially for years |
| No sites get significant traffic | 12 live, real-world projects on your resume |
| Both outcomes | Better job offers AND passive income |

**Total investment:** ~$12/year (12 domain names) | **Hosting:** Free on Cloudflare

This is the key reframe: you win either way.

---

## Tech Stack

| Layer | Tool | Cost |
|---|---|---|
| AI Developer | [Claude Code](https://claude.ai/code) | Free tier available |
| Framework | [AstroJS](https://astro.build) | Free / Open Source |
| Styling | [Tailwind CSS v4](https://tailwindcss.com) | Free / Open Source |
| Hosting | [Cloudflare Pages](https://pages.cloudflare.com) | Free |
| Domain | Namecheap / GoDaddy / Porkbun | ~$10–12/year |
| Keyword Research | [Ahrefs](https://ahrefs.com) / [Ubersuggest](https://neilpatel.com/ubersuggest/) | Paid / Free tier |
| Analytics | Google Analytics + Search Console | Free |
| Monetization | Google AdSense | Free to apply |
| Version Control | Git + GitHub | Free |

**Why AstroJS?** It generates fully static HTML with zero JavaScript hydration overhead. Google crawls it perfectly — a structural SEO advantage over React or Next.js SPAs.

**Why Cloudflare?** Global CDN, free SSL, free hosting, excellent performance. Also handles the `pages.dev` duplicate-content issue natively.

---

## Prerequisites

- A computer with [Node.js](https://nodejs.org/) (v18+), [Git](https://git-scm.com/), and [VS Code](https://code.visualstudio.com/) installed
- A [Claude Code](https://claude.ai/code) account (for AI-assisted development)
- A [Cloudflare](https://cloudflare.com) account (free)
- A domain registrar account (Namecheap, GoDaddy, Porkbun, etc.)
- A [Google Search Console](https://search.google.com/search-console/) account (free)
- Basic familiarity with running terminal commands

No prior coding experience is required.

---

## Complete Workflow

### Step 1 — Find a Profitable Niche

The goal is to find a **small problem that many people Google for a tool to solve**.

1. Open [Ahrefs](https://ahrefs.com) (or a free alternative like [Ubersuggest](https://neilpatel.com/ubersuggest/))
2. Search for keywords like: `online [thing] tool`, `[thing] calculator`, `[thing] converter`, `free [thing] checker`
3. Filter for:
   - **Search volume:** 1,000+ monthly searches (US)
   - **Keyword difficulty:** Low (under 20 ideally)
   - **Intent:** Clearly wants a free online tool, not information
4. Validate: Does a clean, dedicated micro-tool site exist for this keyword, or just clunky multi-tool aggregators?

**Target the US market.** English-language tools targeting US keywords earn 5–10x higher AdSense RPM than non-English or regional markets.

**Good niche examples:**
- Online ruler / screen ruler
- Character counter / word counter
- Aspect ratio calculator
- Random number generator
- JSON formatter / validator
- Password strength checker
- Epoch timestamp converter

See [`docs/01-niche-research.md`](docs/01-niche-research.md) for a deeper guide.

---

### Step 2 — Choose a Domain Name

**Rules for a good micro-tool domain:**
- Descriptive and exact-match (e.g., `realonlineruler.com`, `wordcountertool.com`)
- `.com` preferred; `.io` or `.tools` as alternatives
- Short — under 20 characters
- No hyphens if avoidable
- No numbers

> **Critical:** Write your code FIRST, then buy the domain. Never spend money on a domain before you have confirmed the tool is buildable and the site looks good.

Where to buy: [Namecheap](https://namecheap.com), [Porkbun](https://porkbun.com) (often cheapest), [GoDaddy](https://godaddy.com)

---

### Step 3 — Set Up Your Environment

```bash
# Install Node.js (if not already installed)
# https://nodejs.org/

# Verify installations
node --version   # Should be v18+
git --version
```

Install VS Code extensions:
- **Claude Code** extension (or use the CLI)

Install Claude Code CLI:
```bash
npm install -g @anthropic-ai/claude-code
```

---

### Step 4 — Create Your AstroJS Project

```bash
# Create a new Astro project
npm create astro@latest my-tool-website
cd my-tool-website

# Install Tailwind CSS v4
npx astro add tailwind

# Install the Cloudflare adapter
npx astro add cloudflare

# Start the dev server
npm run dev
```

Add design context for better AI output by placing the [`templates/design-guidelines.md`](templates/design-guidelines.md) file in your project root. Claude Code reads this as context, which dramatically improves generated UI quality.

Also add [`templates/ai-prompts/initial-build.md`](templates/ai-prompts/initial-build.md) as a reference for structuring your first prompt.

---

### Step 5 — Build the Tool with Claude Code

Open Claude Code in your project directory:

```bash
claude
```

Write your initial prompt. Be specific:

```
Build a fully functional online ruler tool for this AstroJS website.

Requirements:
- The ruler should display in both inches and centimeters
- It must be calibrated to the user's actual screen DPI
- Include a toggle to switch between imperial and metric
- Mobile responsive
- Dark mode support
- Clean, minimal design following the design-guidelines.md in this project
- Use Tailwind CSS v4 for all styling
- SEO-optimized with proper title, meta description, and heading structure
```

Claude Code will generate the complete implementation. Review it in your browser at `localhost:4321`.

**Iterative fixes:** Stay in Claude Code to fix bugs, add dark mode, improve mobile responsiveness. Each fix is a follow-up prompt in the same session.

See [`templates/ai-prompts/`](templates/ai-prompts/) for a library of proven prompts.

---

### Step 6 — On-Page SEO

Ask Claude Code to optimize your site for search:

```
Optimize this website for the keyword "online ruler".
Add:
1. A proper <title> tag and meta description
2. An H1 that naturally includes the keyword
3. A 200-word introduction paragraph explaining what the tool does
4. An FAQ section (5 questions) targeting related long-tail keywords
5. Proper heading hierarchy (H1 → H2 → H3)
6. Alt text on any images/SVGs
7. Internal links if multiple pages exist
```

**Required pages for AdSense approval** (all can be AI-generated):
- Privacy Policy
- About Us
- Contact (or a contact email link)
- 404 error page
- robots.txt
- sitemap.xml

See [`docs/04-seo-guide.md`](docs/04-seo-guide.md) for the complete SEO checklist.

---

### Step 7 — Version Control

```bash
git init
git add .
git commit -m "Initial commit: online ruler micro-tool"
```

Continue committing after each significant change.

---

### Step 8 — Deploy to Cloudflare Pages

```bash
# Build the project
npm run build

# Install Wrangler (Cloudflare CLI)
npm install -g wrangler

# Login to Cloudflare
wrangler login

# Deploy
npm run deploy
```

Or connect your GitHub repository directly via the [Cloudflare Pages dashboard](https://dash.cloudflare.com) for automatic deployments on every push.

**Fix the `pages.dev` duplicate content issue:**
In your Cloudflare Pages settings → Custom Domains, disable the default `.pages.dev` subdomain after adding your custom domain, or set a canonical redirect.

See [`docs/05-deployment.md`](docs/05-deployment.md) for the full deployment walkthrough.

---

### Step 9 — Connect Your Domain

1. Buy your domain (after Step 5)
2. In your domain registrar, update nameservers to Cloudflare's (provided in your Cloudflare dashboard)
3. In Cloudflare → Pages → Custom Domains, add your domain
4. Wait for DNS propagation (usually under 1 hour with Cloudflare)
5. Verify your site is live at `https://yourdomain.com`

---

### Step 10 — Submit to Search Engines

**Google Search Console:**
1. Go to [search.google.com/search-console](https://search.google.com/search-console/)
2. Add property → Domain (enter your domain)
3. Verify via DNS TXT record (add in Cloudflare DNS)
4. Go to Sitemaps → Submit `sitemap.xml`

**Bing Webmaster Tools:**
1. Go to [bing.com/webmasters](https://bing.com/webmasters)
2. Add your site
3. Submit your sitemap

Both are free and essential. Don't skip Bing — it's low-effort, free additional traffic.

---

### Step 11 — Promote for Initial Traffic

Google's crawler needs to see real traffic before ranking a new site. Give it a push:

- **Reddit:** Find subreddits relevant to your tool's topic. Share it as a genuinely useful resource (no spam — contribute first)
- **Quora:** Answer questions where your tool is the answer
- **Twitter / X:** Tweet it with relevant hashtags
- **Product Hunt:** If the tool is genuinely useful, launch it

Even 50–100 initial visitors signals to Google that the site is real.

---

### Step 12 — Apply for Google AdSense

**When to apply:**
- Site is live on a custom domain (not `.pages.dev`)
- Has at least 10–15 pages of content (the tool + required pages + a few blog posts or FAQs)
- Has been live for at least 2–4 weeks
- Has received some real traffic

**Apply:** [adsense.google.com](https://adsense.google.com)

AdSense review typically takes 1–2 weeks. Once approved, add the auto-ads script to your site's `<head>` and Google places ads automatically.

See [`docs/06-monetization.md`](docs/06-monetization.md) for placement strategies and RPM optimization.

---

## Project Structure

```
microforge-ai/
├── README.md                     # This file — the complete playbook
├── CONTRIBUTING.md               # How to contribute to this repo
├── LICENSE                       # MIT License
├── docs/
│   ├── 01-niche-research.md      # Finding profitable micro-tool niches
│   ├── 02-tech-stack.md          # Tech stack setup in detail
│   ├── 03-ai-development.md      # Building effectively with Claude Code
│   ├── 04-seo-guide.md           # On-page SEO checklist and strategies
│   ├── 05-deployment.md          # Cloudflare Pages deployment guide
│   └── 06-monetization.md        # AdSense setup and optimization
└── templates/
    ├── design-guidelines.md       # UI design context for Claude Code
    └── ai-prompts/
        ├── initial-build.md       # First-build prompt templates
        ├── seo-optimization.md    # SEO prompt templates
        └── bug-fixing.md          # Debugging prompt templates
```

---

## Pro Tips

**The domain-last rule.** Write your code, see the site working, then buy the domain. Reverse this and you'll accumulate unused domains.

**US market = highest AdSense RPM.** Build English-language tools that solve problems US users search for. RPM from US traffic can be 5–10x higher than traffic from other regions.

**Use design-guidelines.md for better AI output.** Drop a well-written design system document into your project root. Claude Code uses it as context and generates significantly better UI. The [`templates/design-guidelines.md`](templates/design-guidelines.md) in this repo is a solid starting point.

**AstroJS content collections for SEO depth.** Add a small blog or FAQ section using Astro content collections. More indexed pages = more entry points from Google.

**Cloudflare Pages vs Workers.** Use Pages for standard static sites. Use Workers if your tool needs edge-side logic (e.g., fetching external APIs, server-side processing). For most micro tools, Pages is sufficient.

**One tool per site, not many tools per site.** A dedicated domain for one tool ranks faster and builds topical authority more cleanly than a multi-tool aggregator.

---

## Frequently Asked Questions

**Do I need to know how to code?**
No. Claude Code handles the implementation. You need to be able to run terminal commands and understand what you're asking the AI to build.

**How long does it take to build one site?**
With this workflow, a basic micro-tool site (tool + SEO + deployment) takes 4–8 hours on your first attempt. By your third site, expect 2–4 hours.

**How much can one site earn?**
It varies enormously. A site with 10,000 US monthly visitors might earn $50–$300/month from AdSense. A viral tool with 500,000 monthly visitors could earn significantly more. Treat each site as a lottery ticket — most earn modestly, some earn nothing, occasionally one earns a lot.

**Can I do this outside India?**
Yes. This workflow is geography-agnostic. The AdSense advantage of targeting US traffic applies globally.

**What if Claude Code produces broken code?**
Stay in the same Claude Code session and describe the problem. It will fix it. Iterative prompting is normal — expect 2–5 rounds of fixes per site.

**Is this sustainable long-term?**
Google algorithm changes can affect rankings. The hedge is building many sites and diversifying traffic sources. The resume/portfolio value of the 12 projects is entirely independent of Google.

---

## Contributing

Contributions are welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md) for guidelines.

Ideas for contributions:
- Additional prompt templates for different tool types
- A starter AstroJS template with SEO and AdSense pre-configured
- Guides for alternative monetization (affiliate links, freemium tools)
- Translations of the core guide into other languages
- Case studies / real numbers from sites built with this workflow

---

## Related Resources

- [AstroJS Documentation](https://docs.astro.build)
- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages)
- [Google AdSense Help](https://support.google.com/adsense)
- [Google Search Console Help](https://support.google.com/webmasters)
- [Ahrefs Free SEO Tools](https://ahrefs.com/free-seo-tools)
- [IndieHackers Community](https://indiehackers.com) — solopreneur stories and advice

---

## License

[MIT](LICENSE) — free to use, modify, and distribute.

---

*Built on the principles of micro-SaaS, AI-assisted development, and the compounding value of shipping consistently.*
