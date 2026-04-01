# AGENTS.md

This file provides guidance to Codex (Codex.ai/code) when working with code in this repository.

## Project Overview

**Steelab Landing Page** — A static marketing site for Steelab, a Vietnamese enterprise AI Gateway security product. The site promotes PII redaction, Prompt Injection protection, and Nghị định 13 (Vietnamese data protection decree) compliance for businesses using ChatGPT, Codex, and Gemini.

Live: https://steelab.vn/

## Tech Stack

- **Single HTML file**: `index.html` (~76KB) — the entire page, including inline Tailwind config, structured data, and all content
- **Styling**: Tailwind CSS via CDN (`cdn.tailwindcss.com`) with `forms` and `container-queries` plugins
- **Custom CSS**: `assets/css/style.css` — theme variables (light/dark), terminal styles, animations, marquee
- **Fonts**: Lora (headings), Be Vietnam Pro (body), JetBrains Mono (code)
- **Icons**: Material Symbols Outlined (Google Fonts)
- **No build system, no bundler, no package.json**

## Design System

### Color Palette (CSS custom properties in `assets/css/style.css`)

| Token | Dark | Light |
|-------|------|-------|
| `--bg-deep` | `#050a14` | `#f8fafc` |
| `--bg-surface` | `#0c1322` | `#ffffff` |
| `--bg-surface-up` | `#111b2e` | `#f1f5f9` |
| `--bg-edge` | `#1e2d44` | `#cbd5e1` |
| `--text-body` | `#cbd5e1` | `#334155` |
| `--text-muted` | `#64748b` | `#64748b` |

**Accent colors** (defined in Tailwind config, not CSS vars):
- Primary: `#2563eb` (blue)
- Accent: `#c9a84c` (gold)

### Typography
- Headings: `font-heading` → Lora serif
- Body: `font-body` → Be Vietnam Pro
- Code/mono: `font-mono` → JetBrains Mono

### Themes
Theme is toggled via `data-theme` attribute and `localStorage`. The JS in `index.html` head sets `dark` or `light` class on `<html>`.

## File Structure

```
index.html           # Complete landing page (markup + inline Tailwind config + JS)
assets/css/style.css # Theme variables, animations, terminal, marquee styles
assets/css/          # (Currently only style.css exists)
assets/*.png         # Images: avatars, logos, mockups, og-image
schema.json          # Standalone copy of structured data (reference)
schema-embed.html    # Copy of <head> structured data block for re-embedding
llms.txt             # GEO: helps AI crawlers understand site structure
robots.txt           # GEO: allows AI bots (GPTBot, ClaudeBot, PerplexityBot)
GEO-GUIDE.md         # GEO implementation guide (next steps)
geo-audit-report.json # GEO audit results (old — some issues already fixed)
geo-seo-tool/        # Separate Node.js tool (own git history) for GEO auditing
```

## Development Commands

There is no build system. To preview locally:

```bash
# Serve with any static server
npx serve .
# or
python -m http.server 8080
```

Then open `http://localhost:8080` (or the port shown).

**No lint, no tests, no type-checking** — this is a pure static site.

## Making Changes

### Adding/Editing Structured Data

Structured data (JSON-LD) is **inline in the `<head>`** of `index.html` (lines ~30–127). Edit it directly in `index.html`. The standalone `schema.json` is a reference copy and is not used by the page.

If editing structured data:
1. Edit the `<script type="application/ld+json">` block in `index.html`
2. Optionally sync to `schema.json` and `schema-embed.html` for documentation purposes

### Theme/Color Changes

Theme colors are defined in **two places**:
1. `tailwind.config` block in `index.html` `<head>` — defines CSS custom property equivalents as Tailwind tokens
2. `assets/css/style.css` — defines actual CSS custom properties (`--bg-deep`, etc.)

Both must be kept in sync. The CSS file uses a `html.dark { }` / `html.light { }` pattern.

### Animations

Defined in `assets/css/style.css`:
- `hero-reveal` / `hero-delay-1` through `hero-delay-5` — scroll reveal animations
- `animate-float` — floating badge effect
- `animate-marquee` — logo carousel
- `card-lift` — hover lift effect

### Adding New Sections

Follow the existing section pattern in `index.html`:
- Use Tailwind utility classes
- Wrap in a `<section>` with appropriate padding (`py-28 lg:py-40`)
- Use `reveal` class for scroll-triggered animations
- Use `section-divider` divs between major sections

## GEO / AI Crawler Optimization

This site has explicit GEO (Generative Engine Optimization) support:
- `llms.txt` — standard for AI crawler discoverability
- `robots.txt` — allows GPTBot, ClaudeBot, PerplexityBot, Google-Extended, CCBot
- JSON-LD structured data: `SoftwareApplication`, `Organization`, `FAQPage` schemas

The `geo-seo-tool/` subdirectory is a separate Node.js project (independent git history) used internally for GEO auditing.

## Deployment

Pushes go to: `https://github.com/BlackDevTeam2025/steelab-landing-page`

No CI/CD pipeline exists in this repo. Changes are pushed manually.
