# Tech Stack Setup

This guide walks through the complete environment setup from a fresh machine.

## Why This Stack?

### AstroJS
Astro generates pure static HTML at build time. Every page is fully rendered before a visitor arrives — no JavaScript required in the browser to display content. This means:
- Google can crawl and index every page perfectly (no SSR/hydration issues)
- Pages load fast, which is a Core Web Vitals ranking factor
- Zero server-side complexity — just HTML, CSS, and optional client-side JS where needed

### Cloudflare Pages
- Free tier covers unlimited sites and requests
- Global CDN with 300+ edge locations
- Automatic SSL/HTTPS on custom domains
- Integrated with Git — push to deploy
- Handles the `pages.dev` → custom domain redirect cleanly

### Claude Code
Claude Code is Anthropic's AI coding assistant. It reads your entire project context, writes code, fixes bugs, and iterates based on your plain-English prompts. For micro tools, it can generate a complete working site in one session.

### Tailwind CSS v4
Utility-first CSS that pairs well with AI-generated code. Claude Code is trained on Tailwind patterns and produces clean, maintainable styles. v4 has improved performance and a simplified configuration.

---

## Installation

### Node.js

Download from [nodejs.org](https://nodejs.org/). Use the LTS version (v20+ recommended).

```bash
node --version   # Should output v18.x or higher
npm --version    # Should output 9.x or higher
```

### Git

macOS: `xcode-select --install` (includes Git)
Windows: [git-scm.com/download/win](https://git-scm.com/download/win)
Linux: `sudo apt install git` or `sudo dnf install git`

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### VS Code

Download from [code.visualstudio.com](https://code.visualstudio.com/).

Recommended extensions:
- **Astro** (official Astro language support)
- **Tailwind CSS IntelliSense**
- **ESLint**
- **Prettier**

### Claude Code

```bash
npm install -g @anthropic-ai/claude-code
claude --version
```

You will need an Anthropic account. Claude Code has a free tier; paid tiers offer more context and faster responses.

Alternatively, use Claude Code via the VS Code extension or the Claude web interface.

---

## Creating a New AstroJS Project

```bash
# Create the project (follow the interactive prompts)
npm create astro@latest my-tool-name

# Options to select:
# Template: Empty (or "Just the basics")
# TypeScript: Yes, strict
# Install dependencies: Yes
# Initialize git repo: Yes

cd my-tool-name

# Add Tailwind CSS
npx astro add tailwind

# Add Cloudflare adapter
npx astro add cloudflare

# Start the dev server
npm run dev
# Visit http://localhost:4321
```

---

## Project Configuration

### astro.config.mjs

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

### package.json deploy script

Add a deploy script so `npm run deploy` pushes to Cloudflare:

```json
{
  "scripts": {
    "dev": "astro dev",
    "build": "astro build",
    "preview": "astro preview",
    "deploy": "npm run build && wrangler pages deploy dist"
  }
}
```

---

## Project File Structure (Astro)

```
my-tool-name/
├── public/
│   ├── favicon.svg
│   └── robots.txt
├── src/
│   ├── components/       # Reusable UI components (.astro files)
│   ├── layouts/
│   │   └── Layout.astro  # Base HTML layout (head, nav, footer)
│   └── pages/
│       ├── index.astro   # Homepage / main tool
│       ├── about.astro
│       ├── privacy.astro
│       └── contact.astro
├── astro.config.mjs
├── package.json
├── tailwind.config.mjs
└── tsconfig.json
```

---

## Wrangler (Cloudflare CLI)

```bash
npm install -g wrangler
wrangler login   # Opens browser to authenticate with Cloudflare
```

After login, `npm run deploy` will build and push your site to Cloudflare Pages automatically.

---

## Setting Up Claude Code for Your Project

In your project directory:

```bash
claude
```

Claude Code opens a REPL. It reads your project files as context. Before your first prompt, add the design guidelines file:

```bash
cp /path/to/microforge-ai/templates/design-guidelines.md ./design-guidelines.md
```

Now reference it in your first prompt: "Follow the design guidelines in `design-guidelines.md`."
