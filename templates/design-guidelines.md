# Design Guidelines for Micro-Tool Websites

Place this file in your project root. Reference it in your Claude Code prompts to get consistently high-quality UI output.

---

## Core Design Principles

**Clarity over cleverness.** The tool is the product. The UI should disappear into the background and let the function shine.

**Mobile-first.** Design for a 375px screen first, then expand. Most tool users discover sites via Google on mobile.

**Performance as design.** A fast, lightweight page is a design choice. Avoid heavy animations, large images, or JavaScript-dependent layouts.

---

## Typography

```css
/* System font stack — zero load time */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

/* Scale */
--text-xs:   0.75rem;   /* 12px — labels */
--text-sm:   0.875rem;  /* 14px — secondary */
--text-base: 1rem;      /* 16px — body */
--text-lg:   1.125rem;  /* 18px — emphasized */
--text-xl:   1.25rem;   /* 20px — subheadings */
--text-2xl:  1.5rem;    /* 24px — section headings */
--text-3xl:  1.875rem;  /* 30px — page heading */
```

---

## Color System

### Light Mode

```css
--bg-primary:     #ffffff;
--bg-secondary:   #f8fafc;  /* Slate 50 */
--bg-tertiary:    #f1f5f9;  /* Slate 100 */
--text-primary:   #0f172a;  /* Slate 900 */
--text-secondary: #475569;  /* Slate 600 */
--text-muted:     #94a3b8;  /* Slate 400 */
--border:         #e2e8f0;  /* Slate 200 */
--accent:         #2563eb;  /* Blue 600 */
--accent-hover:   #1d4ed8;  /* Blue 700 */
```

### Dark Mode

```css
--bg-primary:     #0f172a;  /* Slate 900 */
--bg-secondary:   #1e293b;  /* Slate 800 */
--bg-tertiary:    #334155;  /* Slate 700 */
--text-primary:   #f1f5f9;  /* Slate 100 */
--text-secondary: #94a3b8;  /* Slate 400 */
--border:         #334155;  /* Slate 700 */
--accent:         #3b82f6;  /* Blue 500 */
--accent-hover:   #60a5fa;  /* Blue 400 */
```

---

## Spacing

8px base grid. All values multiples of 4px or 8px.

```
4px  — xs  | 8px  — sm  | 16px — md
24px — lg  | 32px — xl  | 48px — 2xl
```

---

## Component Patterns

### Tool Container
```
- bg-white (light) / bg-slate-800 (dark)
- border-radius: 12px
- border: 1px solid var(--border)
- padding: 24px desktop / 16px mobile
- max-width: 800px, centered
```

### Primary Button
```
- bg: var(--accent) | text: white
- padding: 10px 20px | border-radius: 8px
- font-weight: 500
- hover: var(--accent-hover), transition 150ms
- active: scale(0.98)
- focus: 2px outline (accessibility)
```

### Input Fields
```
- border: 1px solid var(--border)
- focus-border: 1px solid var(--accent)
- border-radius: 8px | padding: 10px 12px
- font-size: 16px minimum (prevents iOS zoom)
```

---

## Layout

```
Header → Logo / nav (minimal)
Main   → H1 | Tool container | How to use | FAQ
Footer → Privacy Policy | About | Contact | Copyright
```

Breakpoints: Mobile 320–767px | Tablet 768–1023px | Desktop 1024px+

Max-widths: Tool 800px | Text content 680px | Full-width 1200px

---

## Micro-Interactions

- Button press: `transform: scale(0.98)` on active
- Copy button: show "Copied!" for 2 seconds
- Input focus: border color transition, 150ms
- No splash screens — tools should be instantly usable

---

## Accessibility

- Contrast ratio: 4.5:1 minimum (WCAG AA)
- Tap targets: 44×44px minimum
- All inputs: associated `<label>` elements
- Keyboard accessible: tab + enter/space
- Icon-only buttons: `aria-label` required
- Dynamic output: `role="status"` for screen readers

---

## What to Avoid

- External font CDNs (system fonts are fine and zero-latency)
- Shadows heavier than `shadow-md`
- Gradient text
- Full-width hero images
- Carousels or sliders
- Cookie consent banners unless legally required
