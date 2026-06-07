# Building with Claude Code

Claude Code is the core of this workflow. This guide covers how to get consistently good results from it.

## How Claude Code Works

Claude Code reads your entire project directory as context. It understands file relationships, existing code patterns, and your dependencies. This means:

- You don't need to paste code into a chat — it reads files directly
- Fixes are applied in-place — no copy-pasting
- It maintains consistency across files (naming, styling, structure)

## The Initial Build Prompt

Your first prompt sets the foundation. Be as specific as possible.

**Template:**

```
Build a [TOOL NAME] for this AstroJS website.

Tool description:
[Explain what the tool does in 2-3 sentences]

Core features:
- [Feature 1]
- [Feature 2]
- [Feature 3]

Technical requirements:
- AstroJS with Tailwind CSS v4
- Mobile responsive (works on 320px wide screens)
- Dark mode support (using prefers-color-scheme)
- Fast — no heavy libraries, vanilla JS where possible
- All logic in the client-side .astro component or a separate .js file

Design:
- Follow the design guidelines in design-guidelines.md
- Clean, minimal aesthetic
- Clear visual hierarchy
- Accessible (proper ARIA labels, keyboard navigation)

SEO:
- Page title: "[Primary Keyword] — Free Online [Tool Name]"
- Meta description: 150-160 characters, includes keyword
- H1 tag on the page
```

## Iterative Prompting

Expect 3–6 rounds of prompts per site. This is normal.

**Round 1:** Initial build — get the core tool working
**Round 2:** Fix visual bugs, improve responsiveness, add dark mode
**Round 3:** Add secondary features (copy button, keyboard shortcuts, tooltips)
**Round 4:** SEO optimization (see `04-seo-guide.md`)
**Round 5:** Required pages (Privacy Policy, About, robots.txt, sitemap)
**Round 6:** Final polish (error states, edge cases, performance)

## Effective Follow-Up Prompts

**For bugs:**
```
The ruler is not aligned correctly on mobile screens under 375px width.
The measurement labels are overflowing. Fix the responsive layout so
labels wrap or scale appropriately at all screen sizes.
```

**For dark mode:**
```
Add dark mode support. Use the CSS prefers-color-scheme media query.
The background should be #0f172a, text #f1f5f9, and accent color
should remain the current blue but slightly brighter (#3b82f6).
Do not use JavaScript to toggle dark mode — CSS-only is preferred.
```

**For accessibility:**
```
Audit the tool for accessibility issues:
- Add aria-label to all interactive elements that lack visible text labels
- Ensure tab order is logical
- Add keyboard shortcut for the primary action (Enter key)
- Ensure contrast ratio meets WCAG AA (4.5:1 for normal text)
```

**For performance:**
```
Audit for performance issues:
- Remove any unused CSS classes
- Defer any non-critical JavaScript
- Ensure all images/SVGs have explicit width and height attributes
- Check that no heavy npm packages were added unnecessarily
```

## Common Issues and Fixes

**Claude generates broken JavaScript:**
Usually a syntax error or missing import. Paste the browser console error into your next prompt: "I'm seeing this error in the console: [paste error]. Fix it."

**UI looks generic or misaligned:**
Ensure `design-guidelines.md` is in your project root and you've referenced it in your prompt. Also try: "Redesign the tool UI. It currently looks generic. Make it clean, modern, and professional. Reference design-guidelines.md."

**Tailwind classes not applying:**
Claude may generate Tailwind v3 classes in a v4 project. Tell it: "This project uses Tailwind CSS v4. Update any v3-specific syntax (e.g., `bg-opacity-*`, `ring-*` utilities) to the v4 equivalents."

**Large file sizes:**
"The built CSS file is [X]kb. Enable Tailwind's purge/content scanning in the config to remove unused styles and reduce bundle size."

## Working with the AstroJS MCP Server

If you have the [Astro MCP server](https://github.com/withastro/language-tools) configured, Claude Code gets deeper Astro awareness — type checking, component props, and content collection schema validation. This reduces type errors in generated code significantly.

Configure it in your Claude Code settings:

```json
{
  "mcpServers": {
    "astro": {
      "command": "astro-mcp",
      "args": []
    }
  }
}
```

## Tips for Consistent Quality

1. **Keep sessions focused.** One session per major feature. Don't try to build the entire site in one continuous session — context degrades over very long sessions.

2. **Commit between sessions.** `git commit` after each round of fixes. This lets you roll back if Claude Code takes a wrong turn in the next session.

3. **Describe what you see, not what you want fixed.** Instead of "fix the layout bug," say "the tool container is extending beyond the viewport width on mobile. The horizontal scrollbar appears on screens under 400px wide. Fix the container so it never overflows."

4. **Reference file names explicitly.** "In `src/components/Ruler.astro`, the measurement display..." is more effective than "the measurement display..."

5. **Ask for explanations when learning.** If you want to understand what was generated: "Explain what the `useEffect` equivalent pattern in Astro does here, and why it's needed."
