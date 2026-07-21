# OTTO Design System

Recreation of the **OTTO Design System** (designsystem.otto.de) — the design system of OTTO (otto.de), one of Germany's largest e-commerce platforms. Surfaces: **Mobile Web, Android App, iOS App, Desktop Web** (mobile-first). Components carry the `oc-` prefix ("otto components") in Figma/Storybook.

**Sources:** 69 full-page screenshots of designsystem.otto.de (July 2026) in `uploads/`. No codebase, Figma access, font binaries, or SVG assets were provided — all values are transcribed or pixel-sampled from screenshots and marked approximate. Raw extraction notes: `notes/extraction.md`.

## Content fundamentals
- **Language:** product UI is German, informal **du-form** ("Wonach suchst du?", "Willkommen zurück, Chris!", "Dir fehlen noch 40€ zum Mindestbestellwert von 80€"). Documentation is English.
- **Tone:** friendly, direct, service-oriented. Short imperative labels ("Anmelden", "Zur Aktivierung", "In den Warenkorb"). Sentence case everywhere; no ALL-CAPS except the OTTO wordmark.
- **Microcopy patterns:** progress with context ("Vervollständige den letzten Schritt…"), loading in passive present ("Daten werden übermittelt"), states as plain words ("Ausverkauft", "Sehr beliebt", "10% Extra").
- **No emoji.** Icons come from the proprietary icon set only.
- Buttons = actions; links = navigation. Error copy explains how to fix, never blames.

## Visual foundations
- **Color:** three clusters — *Neutral* (black/white/grays), *Exclusive* (functional: success-green, error-red, warning-orange, hint-purple, interactive-blue, sustainable-green, service-blue — each reserved strictly for its meaning), *Corporate* (otto-red + mint/blue/green/purple/pink/warm-red/orange/yellow/beige palettes for campaign styling). Higher numeric suffix = darker. Semantic tokens preferred over base tokens. WCAG 2.1 AA minimum.
- **Type:** single family **OTTO Sans** (regular/bold/black only). Styles: display300–100 (black weight, section leads), headline300–25 (bold), copy125–50 (regular; copy100 default body, copy125 long-form). Links in copy are underlined; bold = highlight; strikethrough = old price. Left-aligned, rem-based (100% = 16px).
- **Spacing:** 4px increments (`spacing-25` = 4px … `spacing-100` = 16px …). 8px grid standard, 4px grid inside components. Proximity principle: 8px related, 40px unrelated.
- **Radii:** interactive ≥4px, default **8px** (buttons, fields), large containers **16px** (cards, promo cards, popovers, sheets); **static elements max 2px** (tags, blocks, banners' inner decor). Nesting: spacing = outer − inner radius.
- **Elevation:** levels 0 Frame (gray-25 bg) → 1 Canvas (white) → 1.5 Stacked (card) → 2 Above (shadow-200: tooltip, icon button) → 3 Sticky (shadow-300: snackbar) → 4 Overlay (scrim: sheet, dialog) → 5 Native (tab bar). Alternating gray/white for depth by color; never custom shadows.
- **Motion:** transitions over animations. Semantic clusters (enter/exit/appear/disappear/expand/collapse/navigate/loop); durations short 80–160ms, medium 240–360ms, long 420–600ms; default easings in-out/in/out, expressive only for special moments; full reduced-motion support (0ms).
- **States:** default/hover (slightly darker)/active (darker still)/focused (2px outline, 2px offset, radius follows component)/checked/disabled (grays, low emphasis). Checked exists only in chip, radio, checkbox, switch, tabs, selection tile, table row, pagination dots.
- **Backgrounds/imagery:** flat color surfaces, no gradients or textures (only "protection" needs on promo images); product photography on white; warm, bright imagery.
- **Layout:** 12-column content grid (spacing-100 margins/gaps) + page grid (no margins, spacing-25 gaps, desktop-only); breakpoints S 360 / M 448 / L 768 (major) / XL 992 / XXL 1232px max; container-based breakpoint classes; skyscraper ad column at XXL; content max 1152px then.

## Iconography
- OTTO uses a **proprietary line icon set** (hundreds of kebab-case icons: `arrow-left`, `basket`, `wishlist`, `otto-up-points`, `sustainable-recycling`, …) — thin ~1.5px strokes, rounded caps, 2 sizes (100/50). Delivered as SVG paths via their Storybook; **not extractable from screenshots**.
- **Substitution here: [Lucide](https://lucide.dev) via CDN** — closest free match in weight and style. `components/icons/Icon.jsx` fetches and inlines `lucide-static` SVGs; `ICON_MAP` translates common OTTO icon names to Lucide equivalents. **Flagged: replace with real OTTO icon SVGs when available.**
- No emoji, no unicode-as-icon.

## App patterns (from real app screenshots, uploads/IMG_9749–51.jpg)
- Vouchers = PaperCard with red rounded-square amount block, red overline for audience ("Nur für Neukund*innen"), "Gültig bis:" + primary button in the dashed footer.
- Price display: "UVP" + black strikethrough old price; current price bold otto-red; discount as sale Tag ("-33%"); "ab 23,00 €" bold black when no discount.
- hint-purple is used for the KI-Assistent FAB and post-purchase rewards ("Dankeschön einlösen") — the only decorative purple use.
- Order confirmation: success-green-25 hero surface, success-green-100 headline ("Lara, Danke für deine Bestellung!").
- App tab bar: 5 line-icon tabs, active = otto-red icon + 3px top indicator bar; count Badges on bell and heart.
- Empty states: centered line icon + short dry copy ("Ganz schön leer hier.") + secondary button.

## Logos
No vector logo files were provided and the OTTO wordmark is **not redrawn** — components render the wordmark as styled text (`Wordmark` component: black-weight italic caps in otto-red). Payment/social/app logos are omitted. Supply official SVGs to `assets/` to replace.

## Fonts — ACTION NEEDED
`OTTO Sans` (regular/bold/black) binaries are not public. The token stack is `'OTTO Sans', 'Helvetica Neue', Arial, sans-serif` — system grotesques render until the real font arrives. **Please upload OTTO Sans woff2 files** and we'll add proper `@font-face` rules.

## Index
- `styles.css` → `tokens/{colors,typography,layout}.css` — all design tokens
- `guidelines/` — foundation specimen cards (Design System tab)
- `components/` — 40 component families in 8 groups: `actions/` (Button, IconButton, Link, ActionSignifier, InteractiveOverlay), `forms/` (TextField, Dropdown, Checkbox, RadioButton, Switch, Chip, SelectionTile, SearchField, FormGroup), `containers/` (Card, Block, Row, Accordion, Expander, Divider, MediaObjectCard, PaperCard, PromoCard), `feedback/` (Badge, Banner, Tag, Snackbar, Spinner, Skeleton, ProgressBar), `overlays/` (Tooltip, Toggletip, Popover, Sheet, FocusedDialog), `navigation/` (TabBar, SkipLink, Carousel, Cinema), `communication/` (ChatBubble), `icons/` (Icon, Wordmark)
- `ui_kits/otto_web/` — otto.de storefront + login recreation
- `ui_kits/otto_app/` — iOS app recreation from real screenshots (storefront, basket, order confirmation)
- `notes/extraction.md` — per-component spec notes from the screenshots
- `SKILL.md` — agent skill entry point

### Intentional additions
- `Icon` (Lucide-backed wrapper) and `Wordmark` (text-only logo stand-in) — both exist only because the real assets weren't provided.
