# Bug Fixing Prompt Templates

Use these after reviewing your AI-generated site in the browser.

---

## Mobile Responsiveness

```
The tool is not displaying correctly on mobile.

Issue: [e.g., horizontal scrollbar, inputs too small to tap, text overflow]
Screen size: [e.g., 375px iPhone, 320px Android]

Fix so:
- No horizontal scrollbar at 320px–1440px
- All tap targets at least 44×44px
- Minimum 14px font size
- Tool container padding 12–16px on small screens
```

---

## Dark Mode Issues

```
Dark mode not working correctly.

Issue: [e.g., light backgrounds remain, text invisible, inputs unchanged]
Affected elements: [e.g., result box, dropdowns, tooltips]

Fix using CSS prefers-color-scheme only (no JS toggle).
Dark bg: slate-900 (#0f172a) | text: slate-100 (#f1f5f9)
```

---

## Calculation Logic Error

```
The calculation produces incorrect results.

Input: [exact values used]
Expected: [correct answer]
Actual: [what the tool shows]
Formula should be: [describe correct formula]

Fix and verify with these test cases:
- Input: [case 1] → Expected: [result 1]
- Input: [case 2] → Expected: [result 2]
```

---

## JavaScript Console Error

```
Browser console shows an error:

[Paste exact error message]
File/line: [e.g., index.astro:47]

Relevant code:
[Paste the code block]

Fix so no console errors or warnings appear.
```

---

## Tailwind v4 Syntax

```
This project uses Tailwind CSS v4 but has v3 syntax.

Update these patterns:
- bg-opacity-* → bg-[color]/[opacity]
- text-opacity-* → text-[color]/[opacity]
- border-opacity-* → border-[color]/[opacity]

Audit all Tailwind classes and fix v3 syntax.
Run npm run build to verify no compilation errors.
```

---

## Copy to Clipboard

```
The "Copy" button is not working.

Expected:
1. Click Copy
2. Text copied to clipboard
3. Button shows "Copied!" for 2 seconds
4. Returns to "Copy"

Current behavior: [describe]

Use navigator.clipboard.writeText() with execCommand fallback.
Handle async with try/catch.
```

---

## Performance (Lighthouse < 90)

```
Lighthouse score is [X]. Target: 90+.

Fix:
1. Remove unused CSS (verify Tailwind content scanning)
2. Add defer/async to non-critical scripts
3. Add explicit width/height to all images and SVGs
4. Replace heavy npm packages with vanilla JS equivalents
5. Fix layout shifts (add min-height or aspect-ratio to dynamic containers)

Show updated build output size after fixes.
```

---

## Accessibility Audit

```
Audit and fix all accessibility issues:

1. Missing alt text on images/SVGs
2. Inputs without <label> elements
3. Elements not reachable via keyboard
4. Icon-only buttons without aria-label
5. Contrast ratio below 4.5:1 (WCAG AA)
6. Missing focus styles
7. Dynamic content without aria-live regions

Priority: labels > keyboard nav > contrast > aria.
```

---

## Error Pages

```
Create error pages:

1. src/pages/404.astro
   - "Page Not Found" heading
   - "The page you're looking for doesn't exist."
   - Link: "← Back to [Tool Name]" → homepage
   - Use Layout.astro, match site design

2. src/pages/500.astro
   - "Something Went Wrong"
   - "An unexpected error occurred. Please try again."
   - Link back to homepage
```
