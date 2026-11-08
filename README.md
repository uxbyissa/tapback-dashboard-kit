# TapBack Dashboard — Media Kit

Everything the front-end team needs to build the TapBack sales dashboard on the **Trezo** (Bootstrap 5) theme: logos, icons, fonts, design tokens, previews and handoff notes, plus the **TapBack Design System** (`design-system/`).

**Version:** 1.0.0 · **Design source:** Figma "Tapback Dashboard — Trezo" → page "TapBack identity — 02"
**Open `docs/index.html`** in a browser for a visual overview of the whole kit.

## Structure

```
tapback-dashboard-kit/
├── assets/
│   ├── logo/            TapBack logo + mark (SVG: lime, navy, white, black) and PNG exports, app icons
│   ├── icons/           30 SVG icons (Material Symbols, currentColor) + ICONS.md
│   └── fonts/inter/     Inter 400 / 500 / 600 / 700 (woff2) + OFL licence
├── tokens/
│   ├── tokens.css               CSS custom properties (colours, type, radius, spacing, motion)
│   ├── tokens.json              Same tokens as JSON
│   ├── _trezo-overrides.scss    Bootstrap / Trezo variable overrides
│   └── fonts.css                @font-face for Inter
├── previews/
│   ├── dashboard-main.png             Approved design
│   ├── dashboard-variant-b-lime.png   Variant with lime accents
│   ├── concept-detail.png             Concept detail page
│   ├── components/                    10 hover cards + 6 floating elements (2x)
│   └── flow/ceo-flow-hover.mp4        Interaction flow video
├── design-system/        TapBack Design System (POS): UX rules, tokens, 49 icons, Poppins + IBM Plex Sans Arabic, boards
│                         → see design-system/README.md
├── docs/
│   ├── index.html        Visual kit viewer
│   └── handoff-notes.md  Colour rule, Trezo build map, interactions, estimated values
├── CHANGELOG.md
└── README.md
```

## Quick start

**1. Fonts and tokens (plain CSS)**

```html
<link rel="stylesheet" href="tapback-dashboard-kit/tokens/fonts.css">
<link rel="stylesheet" href="tapback-dashboard-kit/tokens/tokens.css">
```

```css
.kpi-card { background: var(--card-bg); border: 1px solid var(--card-border); border-radius: var(--radius-xl); }
.kpi-value { font: var(--fw-bold) var(--fs-kpi)/1.2 var(--font-sans); letter-spacing: var(--ls-kpi); color: var(--text-primary); }
.badge-net-sales { background: var(--metric-net-sales-subtle); color: var(--metric-net-sales); }
```

**2. Trezo / Bootstrap (SCSS)**: import the overrides **before** Trezo:

```scss
@import "tapback-dashboard-kit/tokens/trezo-overrides";
@import "trezo/scss/style";
```

This adds theme colours you can use as normal Bootstrap utilities: `bg-net-sales`, `text-orders`, `btn-primary` (TapBack navy), and so on.

**3. Icons**

```html
<span class="icon" style="color: var(--tb-navy)">
  <!-- paste or inline assets/icons/storefront.svg -->
</span>
```

Icons use `currentColor`, so they follow the text colour.

## Rules that matter

1. **TapBack identity lives only in the top bar and the side menu.** The content area uses the metric colours.
2. **One colour per metric, everywhere**: Net sales blue `#2E64C6` · Orders sky `#2DB6F5` · Avg. ticket violet `#8B5CF6` · Profit green `#25B003` · Stores pink `#EC4899`.
3. Red, amber and green are used **only** for alerts and limits.
4. Values marked **≈ / est.** are estimates. See `docs/handoff-notes.md` §6 for the formulas, and replace them when the API provides the real fields.

## Updates

Design changes are released as new versions (see `CHANGELOG.md`). To request a change, open an **Issue** in this repository.

## Download

On the repository page: **Code → Download ZIP**, or open **Releases** and download the latest version.

## Licences

- Inter: SIL Open Font License 1.1 (`assets/fonts/inter/OFL.txt`)
- Poppins, IBM Plex Sans Arabic: SIL Open Font License 1.1
- Material Symbols: Apache License 2.0
- TapBack logo and brand assets: property of TapBack. For use in TapBack products only.
