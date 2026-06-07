# On-Page SEO Guide

SEO is what makes these sites earn passively without ongoing marketing. Every micro-tool site should be fully optimized before deployment.

## SEO Checklist

Use this as a checklist for every site you build.

### Page Structure
- [ ] `<title>` tag: primary keyword + brand (under 60 characters)
- [ ] `<meta name="description">`: compelling, includes keyword (150–160 characters)
- [ ] `<meta name="robots" content="index, follow">`
- [ ] Canonical URL: `<link rel="canonical" href="https://yourdomain.com/">`
- [ ] Open Graph tags (for social sharing): `og:title`, `og:description`, `og:image`, `og:url`

### Content
- [ ] H1 tag: exactly one, includes primary keyword naturally
- [ ] H2/H3 tags: used for supporting sections (How to use, FAQ, About)
- [ ] Introduction paragraph: 150–200 words, introduces the tool and its use case, includes keyword in first sentence
- [ ] FAQ section: 4–6 questions targeting long-tail variants of your keyword
- [ ] No keyword stuffing — write for humans, keyword appears naturally

### Technical
- [ ] `robots.txt` in `/public/robots.txt`
- [ ] `sitemap.xml` generated and linked in `robots.txt`
- [ ] All images/SVGs have `alt`, `width`, and `height` attributes
- [ ] No broken internal links
- [ ] Canonical domain configured (no `www` vs non-`www` split)
- [ ] `pages.dev` subdomain disabled (Cloudflare dashboard)
- [ ] HTTPS only (Cloudflare enforces this automatically)

### Performance (Core Web Vitals)
- [ ] Lighthouse Performance score >= 90
- [ ] LCP (Largest Contentful Paint) < 2.5s
- [ ] CLS (Cumulative Layout Shift) < 0.1
- [ ] No render-blocking resources
- [ ] Images lazy-loaded where appropriate

### Required Pages for AdSense
- [ ] Privacy Policy (must mention data collection and cookies)
- [ ] About page (who runs this site)
- [ ] Contact (email address or contact form)
- [ ] 404 error page
- [ ] 500 error page

---

## AI Prompt for SEO Optimization

Use this prompt in Claude Code after building your tool:

```
Optimize this website for search engines. The primary target keyword is
"[YOUR KEYWORD]" targeting US searchers.

Please:

1. Update the <title> tag to: "[Primary Keyword] — Free Online Tool | [Brand Name]"
   (Keep it under 60 characters)

2. Write a meta description: 150-160 characters, includes "[keyword]",
   communicates the value, ends with a mild CTA like "Try it free."

3. Ensure there is exactly one H1 on the page that naturally includes
   the keyword.

4. Add a 200-word introduction section above the tool explaining:
   - What this tool does
   - Who it's useful for
   - How to use it (briefly)
   Include the keyword in the first sentence.

5. Add an FAQ section with these 5 questions:
   - How do I use [tool name]?
   - Is [tool name] free?
   - Does [tool name] work on mobile?
   - How accurate is [tool name]?
   - [A long-tail question specific to this tool's use case]

6. Add a "How to Use" section with 3-5 numbered steps.

7. Add proper Open Graph meta tags for social sharing.

8. Add a canonical URL tag pointing to https://[yourdomain.com]/
```

---

## robots.txt Template

Place in `public/robots.txt`:

```
User-agent: *
Allow: /

Sitemap: https://yourdomain.com/sitemap.xml
```

---

## Generating a Sitemap in AstroJS

Install the official Astro sitemap integration:

```bash
npx astro add sitemap
```

This auto-generates `/sitemap-index.xml` and `/sitemap-0.xml` at build time based on your pages. Reference it in `robots.txt` and submit the URL to Google Search Console.

Configure in `astro.config.mjs`:

```js
import sitemap from '@astrojs/sitemap';

export default defineConfig({
  site: 'https://yourdomain.com',
  integrations: [tailwind(), sitemap()],
});
```

---

## Title Tag Formulas

These patterns work well for micro tools:

```
[Keyword] — Free Online [Tool Category]
[Keyword] | Free [Tool Name] Tool
[Keyword]: Fast, Free & Accurate [Tool Name]
```

Examples:
- `Online Ruler — Free Screen Ruler Tool`
- `Aspect Ratio Calculator | Free Online Tool`
- `Word Counter: Fast, Free & Accurate`

---

## FAQ Writing Tips

FAQs are powerful for two reasons:
1. They target long-tail variants of your keyword (each question is a separate ranking opportunity)
2. They can trigger FAQ rich snippets in Google search results (higher CTR)

Write FAQs in plain language. Answer each question in 2–4 sentences. Don't pad with filler — concise answers rank better in featured snippets.

Add FAQ schema markup:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How do I use the online ruler?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Hold your screen up to a physical ruler and use the calibration slider until they match. Then use the on-screen ruler to measure any object."
      }
    }
  ]
}
</script>
```

---

## After Deployment: Search Console Setup

1. Go to [search.google.com/search-console](https://search.google.com/search-console/)
2. Add property → Domain type (not URL prefix)
3. Verify ownership via DNS TXT record (add the TXT record in Cloudflare DNS)
4. After verification, go to Sitemaps → Add your sitemap URL: `https://yourdomain.com/sitemap-index.xml`
5. Monitor: Coverage report → check for crawl errors after 48–72 hours
