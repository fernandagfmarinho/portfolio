# Portfolio

Personal portfolio site based on the Civio Framer Resume Template, hosted on GitHub Pages.

## Structure

```
portfolio/
├── index.html              # Main entry point
├── assets/
│   └── css/
│       ├── sf-images.css       # Inline base64 images (SingleFile export)
│       ├── fonts.css           # Web font declarations
│       ├── framer-core.css     # Core Framer layout & reset styles
│       ├── framer-editor.css   # Framer editor toolbar (safe to ignore)
│       ├── framer-components.css # Framer component styles
│       ├── framer-utils.css    # Framer utility classes
│       ├── theme.css           # Design tokens & theme styles
│       └── custom.css          # Your custom overrides (edit this)
└── CLAUDE.md               # AI assistant context
```

## Customization

Edit `assets/css/custom.css` to override any styles without touching the Framer-generated files.

## GitHub Pages

Enable GitHub Pages in repo Settings → Pages → Deploy from branch `main` → `/ (root)`.
