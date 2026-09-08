# TradeFlow Design Languages

Internal decision board for choosing a visual language for the **TradeFlow** admin portal, using official **Koa** brand colours and type.

Live site: https://syllabusromeo.github.io/design-previews/

(Temporary here.now preview may still exist; GitHub Pages is the permanent free host — see [HOSTING.md](./HOSTING.md).)

Brand source: [Koa Frontify Style Guide](https://company-164955.frontify.com/d/vAejAP8xgb73/style-guide)

---

## Purpose

Before changing production TradeFlow UI, compare **23 design languages** side by side. Every mock shares the same information architecture (sidebar, KPIs, invoice table, icons) so you judge **look and feel only** — not layout differences.

Use this repo to:

1. Review each language with Koa brand applied
2. Shortlist 2–3 directions with stakeholders
3. Implement the winner in TradeFlow (Jinja / CSS), not as a static site

---

## Quick start

Open locally (no build step):

```bash
# from repo root
start index.html          # Windows
open index.html           # macOS
xdg-open index.html       # Linux
```

Or serve statically:

```bash
npx --yes serve .
```

Then open the URL shown in the terminal.

---

## What’s included

| Path | Description |
|------|-------------|
| `index.html` | Hub / design board — links to every portal |
| `brand.css` | Koa tokens, Maison Neue + Koa Display `@font-face` |
| `hub.css` | Hub layout and swatches |
| `fonts/` | Self-hosted Maison Neue (Book/Bold) and Koa Display |
| `portals/` | One full admin mockup per design language |
| `portals/shared.css` | Shared portal chrome + icon sizing |
| `portals/*.css` | Language-specific visual treatment |

---

## Design languages

### Original set
1. Skeuomorphism  
2. Neomorphism  
3. Glassmorphism  
4. Claymorphism  
5. Minimalism  
6. Maximalism  
7. Brutalism  
8. Liquid glass  
9. Spatial UI  

### Extended set
10. Flat Design  
11. Material Design  
12. Fluent Design  
13. Neubrutalism  
14. Swiss Style  
15. Aurora / Mesh  
16. Bento UI  
17. Cyberpunk / Neon  
18. Terminal / CLI  
19. Editorial / Paper  
20. Y2K / Retro Web  
21. Holographic  
22. Organic / Biophilic  
23. Industrial / Utilitarian  

Each portal: `portals/<name>.html`

---

## Koa brand tokens

Applied across every mock so comparisons stay on-brand.

### Colour

| Token | Hex | Role |
|-------|-----|------|
| Koa Blue | `#00109F` | Primary text / chrome |
| Koa Teal | `#00AE8D` | Brand accent (Frontify brand colour) |
| Koa Green | `#00CC99` | Secondary / success |
| Koa Orange | `#FF4500` | CTA / danger / attention |
| Koa Gold | `#FFD700` | Highlight / warning |
| Cream | `#FFF2DE` | Warm page wash |
| Mint | `#E0F5EE` | Soft surface |
| Lemon | `#FFFACD` | Soft highlight |
| Soft yellow | `#FFF19A` | Soft highlight |
| Lavender | `#E6E6FA` | Soft accent wash |
| Gray | `#ABABAB` | Muted / secondary |
| Cloud | `#F4F6F7` | Neutral surface |

CSS variables live in `brand.css` / `portals/brand.css` as `--koa-*`.

### Typography

| Face | File | Use |
|------|------|-----|
| Maison Neue Book | `fonts/mn-book.woff2` | Body / UI |
| Maison Neue Bold | `fonts/mn-bold.woff2` | Emphasis / labels |
| Koa Display (FRL) | `fonts/frl-regular.woff2` | Headings / logo wordmark feel |

Fonts are self-hosted for offline / preview use. Confirm licensing with brand before shipping to public production if required by your font agreement.

---

## How to decide

1. Open the hub and walk every portal (or your shortlist).  
2. Score on: clarity at desk density, brand fit, accessibility contrast, implementation effort in Bootstrap/Jinja.  
3. Pick a primary language + optional “dark / dense” variant if needed.  
4. Document the winner in your TradeFlow UI notes, then implement in `salesinventory` theme CSS — do not treat these static mocks as production.

Suggested scorecard (1–5):

- Readable metrics at a glance  
- Sidebar scannability  
- Tables / forms would still work  
- Feels like Koa (not generic SaaS)  
- Feasible with current TradeFlow stack  

---

## Editing guides

### Change brand colours or type

Edit `brand.css` and mirror token values in `portals/brand.css` (font paths differ: `fonts/` vs `../fonts/`).

### Tweak one language only

Edit `portals/<language>.css`. Keep HTML structure in sync across portals when possible.

### Shared chrome (layout, icons)

Edit `portals/shared.css` and the HTML pattern used by all portals. Icons are inline SVG with hard size locks (`16px` / `18px`) so they do not dominate cards.

### Add a new language

1. Copy an existing `portals/*.html` + `*.css`  
2. Add a tile on `index.html` + swatch in `hub.css`  
3. Restyle with `--koa-*` tokens only  

---

## Permanent hosting (free)

Do not rely on here.now for the lasting board (TTL / 24h limits). Full guide:

→ **[HOSTING.md](./HOSTING.md)**

Quick pick:

| Option | Free URL | Custom domain needed? |
|--------|----------|------------------------|
| **GitHub Pages** (recommended) | `SyllabusRomeo.github.io/design-previews` | No |
| Cloudflare Pages | `*.pages.dev` | No |
| Netlify | `*.netlify.app` | No |
| Vercel | `*.vercel.app` | No |

Enable GitHub Pages: repo **Settings → Pages → Deploy from a branch → `main` / root**.

---

## Notes

- These are **static mockups** for visual decision-making. TradeFlow itself is a Flask app and needs a real staging/local run for interaction testing.  
- Do not commit API keys or `.herenow/` credentials into this repository.

---

## License

Internal Koa / TradeFlow design tooling. Brand assets remain subject to Koa brand guidelines.
