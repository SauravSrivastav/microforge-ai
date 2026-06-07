# SEO Optimization Prompt Templates

Use these after your tool is built and working locally.

---

## Full SEO Pass

```
Perform a complete on-page SEO optimization of this website.
Primary keyword: "[YOUR KEYWORD]"
Target audience: US English speakers

1. PAGE TITLE
   "[Primary Keyword] — Free Online [Tool Type]"
   Max 60 characters. Must include exact keyword.

2. META DESCRIPTION
   150–160 characters. Includes keyword naturally.
   Ends with soft CTA: "Try it free." or "No signup required."

3. H1 TAG
   Exactly one H1. Naturally includes keyword. Compelling, not just the keyword.

4. INTRODUCTION SECTION (180–220 words above the tool)
   - First sentence includes keyword
   - What the tool does and who it's for
   - How to use it briefly
   - 2–3 secondary keyword variants
   - No filler — every sentence adds value

5. HOW TO USE SECTION
   H2 "How to Use [Tool Name]" with 3–5 numbered steps.
   Include keyword once.

6. FAQ SECTION (5 Q&A pairs)
   Q1: "How do I use [tool name]?"
   Q2: "Is [tool name] free?"
   Q3: "Does [tool name] work on mobile?"
   Q4: "How accurate is [tool name]?"
   Q5: [Long-tail question specific to this niche]

7. OPEN GRAPH TAGS
   og:title, og:description, og:url, og:type, og:image

8. CANONICAL TAG
   <link rel="canonical" href="https://[yourdomain.com]/">

9. SCHEMA MARKUP
   FAQ schema JSON-LD + WebApplication schema
```

---

## Privacy Policy Generator

```
Generate a Privacy Policy page at src/pages/privacy.astro.

Site: [name] at https://[domain]
Data collected: Google Analytics (anonymized), Google AdSense cookies
No user accounts or form submissions
Contact: [your@email.com]

Cover:
1. What we collect (cookies, analytics, ad data)
2. How we use it
3. Third-party services (Google Analytics, AdSense)
4. Cookie explanation (AdSense uses cookies for ad personalization)
5. User rights (opt-out via Google)
6. Contact info
7. Last updated date

Plain English. H2 headings per section. 300–500 words.
```

---

## About Page Generator

```
Generate an About page at src/pages/about.astro.

Tool: [name] — [what it does] — [problem it solves]

Include:
- What the tool is and why it exists (2 paragraphs)
- Free to use, no account required
- Built with AstroJS, hosted on Cloudflare
- Contact: [your@email.com]

Tone: genuine, human — not corporate boilerplate.
200–300 words total.
```

---

## Sitemap and robots.txt

```
Set up sitemap and robots.txt:

1. Install: npm install @astrojs/sitemap
   Add sitemap() to astro.config.mjs integrations

2. public/robots.txt:
   User-agent: *
   Allow: /
   Sitemap: https://[domain]/sitemap-index.xml

3. astro.config.mjs: site: 'https://[domain]'

4. Verify sitemap includes: /, /about, /privacy, /contact
```

---

## WebApplication Schema

```
Add WebApplication JSON-LD to homepage <head>:

- name: "[Tool Name]"
- url: "https://[domain]"
- description: "[1-sentence description]"
- applicationCategory: "UtilityApplication"
- operatingSystem: "Web Browser"
- offers: { price: "0", priceCurrency: "USD" }
- browserRequirements: "Requires JavaScript"
```
