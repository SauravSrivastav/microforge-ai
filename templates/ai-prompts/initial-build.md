# Initial Build Prompt Templates

Use these as starting points for your first Claude Code session. Customize the specifics for your tool.

---

## Template 1 — Generic Micro Tool

```
Build a complete [TOOL NAME] for this AstroJS + Tailwind CSS v4 website.

TOOL DESCRIPTION:
[What input does the user provide? What output do they get? What problem does it solve?]

CORE FEATURES:
1. [Primary feature]
2. [Secondary feature — copy to clipboard, unit toggle, etc.]
3. [UX feature — real-time calculation, instant results]
4. Dark mode (CSS prefers-color-scheme, no JS toggle)
5. Mobile responsive (320px to 1440px)

TECHNICAL REQUIREMENTS:
- AstroJS, output: static
- Tailwind CSS v4 syntax (not v3)
- Vanilla JavaScript only (no npm packages unless essential)
- Follow design-guidelines.md

FILE STRUCTURE:
- src/pages/index.astro
- src/layouts/Layout.astro
- src/components/[ToolName].astro

SEO:
- <title>: "[Keyword] — Free Online Tool"
- Meta description: 150-160 chars with keyword
- One H1 with keyword
- 150-word intro paragraph above the tool
```

---

## Template 2 — Calculator Tool

```
Build an online [TOPIC] calculator for this AstroJS website.

WHAT IT CALCULATES:
- Inputs: [list inputs with units]
- Outputs: [list outputs]
- Formula: [describe or write the formula]

UI LAYOUT:
- Input panel: labeled fields with units
- Output panel: results displayed prominently
- "Calculate" button (triggers on Enter key too)
- "Reset" button to clear all fields

INPUT VALIDATION:
- Inline error messages for invalid inputs
- Positive numbers only
- Required field checking before calculation

FORMAT:
- Currency: Intl.NumberFormat with USD locale
- Percentages: 2 decimal places
- Large numbers: comma separators

Follow design-guidelines.md. Tailwind CSS v4. Dark mode. Mobile responsive.
```

---

## Template 3 — Converter Tool

```
Build an online [TOPIC] converter for this AstroJS website.

CONVERSION:
- Bidirectional: editing either field updates the other in real-time
- Units: [list all unit pairs]

UX:
- Two inputs side by side (desktop) / stacked (mobile)
- Unit selector dropdowns for both sides
- Copy result button with visual feedback
- Show the conversion formula (for SEO and education)

PRECISION:
- Up to 6 significant figures
- Scientific notation for very small numbers
- Comma formatting for large numbers

Follow design-guidelines.md. Tailwind CSS v4. Dark mode. Mobile responsive.
```

---

## Template 4 — Text Tool

```
Build an online [text processing tool] for this AstroJS website.

FUNCTION: [What transformation does this tool perform?]

INPUT:
- Large textarea for pasting/typing
- "Paste" button (reads from clipboard)
- Character count display

OUTPUT:
- Non-editable results area
- "Copy" button with "Copied!" feedback
- Real-time output (updates on input event)

STATISTICS:
- Word count, character count (with/without spaces)
- Sentence count, reading time (200 wpm)

Follow design-guidelines.md. Tailwind CSS v4. Dark mode. Mobile responsive.
Textarea minimum 200px tall.
```

---

## Template 5 — Generator Tool

```
Build an online [THING] generator for this AstroJS website.

WHAT IT GENERATES: [describe output]

CONFIGURATION: [list user-configurable options]

OUTPUT:
- Generated result in large, readable font
- "Generate" button (keyboard shortcut: Space or Enter)
- "Copy" button with "Copied!" feedback
- Option to generate multiple results (list view)

RANDOMNESS:
- crypto.getRandomValues() for passwords/tokens
- Math.random() for non-security generation

Follow design-guidelines.md. Tailwind CSS v4. Dark mode. Mobile responsive.
```

---

## Usage Notes

**Always include in every prompt:**
- "Follow design-guidelines.md"
- "Use Tailwind CSS v4" (not v3)
- "Dark mode via CSS prefers-color-scheme"
- "Mobile responsive from 320px"

**After the build:** Review at `localhost:4321`, then use prompts from `bug-fixing.md` for issues.
