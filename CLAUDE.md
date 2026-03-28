# Portfolio — Claude Context

## Project overview

Personal portfolio / resume site based on the **Civio Framer Resume Template**, originally exported from Framer as a single-file HTML (SingleFile browser extension) and refactored into a structured GitHub Pages project.

- **Live URL**: GitHub Pages (main branch, root)
- **Source origin**: https://just-tournaments-678897.framer.app/
- **Template**: Civio – minimal one-page resume/CV with two layout variants

## Repository structure

```
portfolio/
├── index.html                  # Main entry point (~200 KB, Framer-generated HTML)
├── assets/
│   └── css/
│       ├── sf-images.css       # Base64-encoded images (SingleFile export artefact, ~114 KB)
│       ├── fonts.css           # @font-face declarations with base64 fonts (~1 MB — do not edit)
│       ├── framer-core.css     # Core Framer layout, resets, and utility styles (~58 KB)
│       ├── framer-editor.css   # Framer editor bar overlay styles (safe to ignore)
│       ├── framer-components.css # Framer component-level styles (~13 KB)
│       ├── framer-utils.css    # SingleFile utility class (.sf-hidden)
│       ├── theme.css           # Design tokens, Inter font config, base theme (~727 KB — large due to base64)
│       └── custom.css          # User-owned overrides — edit this file for customizations
├── .gitignore
├── README.md
└── CLAUDE.md                   # This file
```

## Key facts for future iterations

### What was done
- The original 2.2 MB single-file HTML was split: all `<style>` blocks extracted into `assets/css/`
- `index.html` now loads CSS via `<link>` tags — reducing it from 2.2 MB to ~200 KB
- One tiny inline style remains in the body: `<style data-framer-html-style class=sf-hidden>` — this is a Framer runtime style and must stay inline
- CSS load order in `<head>` mirrors the original style block order to preserve specificity

### CSS file ownership
| File | Owner | Edit? |
|------|-------|-------|
| `sf-images.css` | Framer/SingleFile | No |
| `fonts.css` | Framer | No |
| `framer-core.css` | Framer | No |
| `framer-editor.css` | Framer | No |
| `framer-components.css` | Framer | No |
| `framer-utils.css` | Framer | No |
| `theme.css` | Framer | No |
| `custom.css` | User | YES — put all overrides here |

### Content editing
- All visible content (name, job title, bio, experience, links) is in `index.html`
- Framer uses complex class names (e.g. `framer-6jWyo`, `framer-bmpgw8`) — search for text content directly
- The page has responsive breakpoints: desktop (≥1200px), tablet (810–1199px), mobile (≤809px)

### Design tokens
- Background: `rgb(249, 247, 235)` (warm off-white), token: `--token-e925c78c-514a-42ff-8dbd-2de4cfbbd362`
- Font stack: Inter, then system-ui fallback
- Serif accent: Baskervville (italic)

### What NOT to do
- Do not regenerate `fonts.css` or `sf-images.css` — they contain multi-MB base64 data
- Do not run a bundler/minifier on the Framer CSS files — they're already optimized
- Do not add a build step unless the project grows significantly beyond static HTML+CSS

### Next steps (suggested)
1. Replace placeholder content in `index.html` with real personal info
2. Use `custom.css` to tweak colors, spacing, or typography
3. Replace base64 favicon (`<link href="data:image/png;base64,...">`) with a real `/favicon.ico` or `/favicon.png`
4. Consider self-hosting fonts by extracting the base64 font data from `fonts.css` into actual `.woff2` files under `assets/fonts/` (reduces initial CSS parse time)
5. Add GitHub Actions workflow for automated deployment if needed
