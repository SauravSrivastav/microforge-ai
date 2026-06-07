# Monetization Guide

## Google AdSense — The Core Strategy

Google AdSense is the primary monetization method for micro-tool sites. It's a display advertising network: Google places relevant ads on your site and pays you every time a visitor views or clicks them.

### Why AdSense for Micro Tools

- **Passive:** Once set up, it earns without any action from you
- **Automatic:** Google selects ads relevant to your audience
- **Scalable:** More traffic = more revenue, no extra work
- **Threshold:** Payout when balance reaches $100

---

## Understanding RPM vs CPC vs CTR

| Metric | What it means |
|---|---|
| **RPM** (Revenue per Mille) | Revenue per 1,000 page views |
| **CPC** (Cost per Click) | What advertisers pay per click (you receive ~68%) |
| **CTR** (Click-through Rate) | % of ad impressions that result in clicks |

**Realistic RPM ranges (US traffic):**
- Low competition niches: $1–$5 RPM
- Mid-range niches (finance, productivity): $5–$15 RPM
- High-value niches (legal, finance, insurance): $15–$50+ RPM

---

## AdSense Eligibility Requirements

- [ ] Site is live on a **custom domain** (not `.pages.dev`)
- [ ] Site has been live for **at least 4 weeks**
- [ ] Minimum of **10–15 pages** of substantial, original content
- [ ] **Privacy Policy** page mentioning cookies and data collection
- [ ] **About** page
- [ ] Some real traffic (even 50–100 visitors helps)
- [ ] Content complies with [AdSense policies](https://support.google.com/adsense/answer/48182)
- [ ] Site owner is 18+

---

## How to Apply

1. Go to [adsense.google.com](https://adsense.google.com)
2. Enter your site URL and select your country
3. Add the AdSense auto-ads script to your site's `<head>`
4. Submit for review (1–2 weeks typically)

---

## Adding AdSense to AstroJS

```html
<head>
  <script
    async
    src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXXX"
    crossorigin="anonymous"
  ></script>
</head>
```

Start with **auto ads** — Google places ads automatically. Once you have traffic data, experiment with manual placements.

---

## Ad Placement Best Practices

- **Above the fold:** Leaderboard (728×90) or responsive banner — don't push the tool below the fold
- **Below the tool:** Rectangle (300×250) — users who interacted are more likely to engage with ads
- **Sidebar:** 300×600 on desktop, hidden on mobile
- **Avoid:** More than 3 ad units per page, ads that look like tool buttons, interstitials

---

## Realistic Earnings Projections

| Monthly US Visitors | RPM | Monthly Earnings |
|---|---|---|
| 1,000 | $3 | $3 |
| 5,000 | $3 | $15 |
| 10,000 | $5 | $50 |
| 50,000 | $5 | $250 |
| 100,000 | $8 | $800 |
| 500,000 | $8 | $4,000 |

The model works because traffic is **free** (SEO), hosting is **free** (Cloudflare), and you build **multiple** sites. Twelve sites averaging $50/month = $600/month passive income.

---

## Alternative Monetization

- **Affiliate marketing:** Link to relevant products (e.g., mortgage calculator → mortgage comparison sites)
- **Sponsored placement:** Direct deals with advertisers once you have significant traffic
- **Freemium features:** Free tier with ads + paid tier without ads
- **Direct ad sales:** Higher CPM than AdSense once you reach 10,000+ monthly visitors
