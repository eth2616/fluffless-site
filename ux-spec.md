# Stage 3 UX Spec — FluffLess

## 1. Composition Strategy

**Container approach: introduce `.container--layout` (~960px).** Do not widen the default `.container` — About prose must stay letter-like.
- `.container--layout` (~960px): Hero, Philosophy
- `.container--wide` (1040px): BabyLull — unchanged
- `.container--narrow` (580px): About — unchanged
- `.container` (680px): Footer inner — unchanged

Section composition mix: Hero (two-column layout), Philosophy (single-column intro + inline principles row spanning full layout width), BabyLull (two-column), About (narrow single-column prose), Footer (centered single-column).

Section backgrounds — no two adjacent sections share a surface:
1. Hero → `--color-bg` (off-white)
2. Philosophy → `--color-surface` (white)
3. BabyLull → `--color-surface-tint` (warm tint) + 2px plum top border
4. About → `--color-surface` (white)
5. Footer → `--color-surface-tint` + 1px `--color-border` hairline top divider

## 2. Hero (Stage 3)

**Wordmark direction: oversized typographic lockup.** Right grid column filled with "FluffLess" set at `--text-4xl`, weight 700, color `--color-border` (very muted warm gray). Pure CSS text — no SVG, no image. `aria-hidden="true"`. Reads as a typographic counterweight to the headline, not as a logo or interactive element. No hover state.

Desktop: right column, vertically centered, right-aligned within the column. Hidden below 640px — wordmark does not appear on mobile or tablet. This prevents any vertical length increase.

Text-column hierarchy unchanged: eyebrow → accent rule → h1 → sub-copy → CTA row. Hero uses `.container--layout`.

Hero grid: `~55% text / ~45% wordmark`. Existing `hero-grid` column ratio (`1.2fr / 1fr`) carries forward.

## 3. Philosophy (Stage 3)

**Principles composition: flex row of three labeled items with thin vertical hairline dividers between them.** Each item: `<strong>` label (semibold, `--color-text`) followed by em-dash and descriptor (muted, regular weight). Items sit side-by-side at ≥640px. Thin 1px `--color-border` vertical dividers separate items. At base mobile: stack vertically, dividers become horizontal hairlines.

Container: `.container--layout`. Section intro `<p>` constrained to ~620px, left-aligned (not full-width) — intentional asymmetry within the wider container creates layout variety. Principles row sits flush below intro, spanning the full `.container--layout` width.

No card chrome. No eyebrow. Heading leads, intro follows, principles row closes the section.

## 4. BabyLull (Stage 3)

**Two-column desktop via existing `.featured-grid`** — no structural change. Column proportions (`1.1fr / 1fr`) carry forward.

**Phone-frame refinement:** Increase desktop height to 460px (from 420px). Strengthen shadow to ~`0 16px 48px rgba(0,0,0,0.18)`. Screen interior: **empty** — no content hint. Larger frame + stronger shadow delivers the product-centerpiece presence without decoration risk.

**Lists:** Replace Stage 2 dual-list pattern with:
1. Single feature list (6 items) — existing dash marker style (`--text-sm`, muted).
2. Privacy reassurance row (4 items) — rendered as a horizontally-arranged `<ul>` (semantic list preserved) with middle-dot (`·`) separators added via CSS `::after` pseudo-elements between items (not real text). Items sit inline at ≥640px, wrap if needed; stack vertically at base. `--text-xs` muted text, no list markers. Reads as a trust stamp visually distinct from the feature list above. Separated from the feature list by ~12–16px (less than the gap to the CTA).

Text-column order: eyebrow → h2 → body → feature list → privacy row → CTA.

`.product-cta` pattern (`aria-disabled` + `aria-describedby` + visible "Coming soon") preserved verbatim.

## 5. About (Stage 3)

No changes. Single column, `.container--narrow` (580px), heading-led, single body paragraph. Letter-like intimacy preserved.

## 6. Footer (Stage 3)

**Surface:** `--color-surface-tint` — reuses existing token, no new token required. Top boundary: 1px `--color-border` hairline divider. Reduce vertical padding to ~2.5rem (down from 4rem) — tighter and less imposing.

**Layout:** Centered flex-column, three stacked items: brand line → email link → copyright. `.footer-inner` carry.

**Email link:** `--color-accent-text` (plum) in light mode (6.57:1 on `--color-surface-tint` — verified AA). `--color-accent-on-dark` (lavender) in dark mode. Underlined, 44px min touch height. Opacity-only hover (`0.8`).

**Dark mode:** Footer uses `--color-surface-tint` dark swap (`#222224`). Hairline divider uses `--color-border` dark swap (`#2C2C2E`). `--color-surface-dark` is no longer applied to footer — token remains defined but unused; architect may keep for future use or remove.

## 7. Hierarchy Upgrades

- **h1 mobile base:** `--text-2xl` (32px) → `--text-3xl` (40px). Desktop stays `--text-4xl`. More confident at all sizes.
- **h2:** Set to `--text-2xl` (32px) at all breakpoints — remove the `≥640px` step-up. Wider containers make the desktop size appropriate at base too.
- **h2 margin-bottom:** `--space-3` → `--space-4` (2rem). More air below section headings without adding section length.
- Body weight contrast (700 heading / 400 body) is already doing the hierarchy work — no changes to body or muted text.

## 8. Color and Surface Plan

All light-mode tokens carry from Stage 2. Changes only:
- Footer no longer applies `--color-surface-dark` — uses `--color-surface-tint` instead.
- Footer email: plum in light mode (safe on `--color-surface-tint`), lavender in dark mode.
- Plum usage set: eyebrows, accent rule, button fills, focus rings, BabyLull 2px top border, feature-list dash markers, footer email (light mode). Count unchanged at ≤5 meaningful touch points. No new plum applications introduced.

## 9. Removed Elements (Stage 3)

- `.why-less` section — HTML, CSS class, narrow-container assignment
- `.privacy` section — HTML, CSS class, `.privacy-list`, `.privacy-note`
- Hero `.phone-frame` markup and `height: 480px` desktop rule → replaced by `.hero-wordmark`
- BabyLull `.value-list` (3-item), `<hr class="list-separator">`
- `.card`, `.card__title`, `.card__body`, `.cards-grid`
- Footer `--color-surface-dark` surface application (dark charcoal footer dropped)

## 10. Acceptance Criteria

- [ ] Exactly 5 sections in order: Hero, Philosophy, BabyLull, About, Footer
- [ ] Hero right column is a typographic wordmark, `aria-hidden`, hidden below 640px
- [ ] Hero and Philosophy on `.container--layout` (~960px); BabyLull on `--wide` (1040px); About on `--narrow` (580px)
- [ ] No two adjacent sections share the same background surface token
- [ ] Philosophy renders three labeled principles in a horizontal flex row with hairline dividers; zero card borders
- [ ] BabyLull has one feature list (6 items, dashes, muted) + one inline privacy row (4 items, dots, `--text-xs`, no markers, but still a `<ul>` semantically)
- [ ] Privacy row is visually distinct from the feature list: smaller text, inline/horizontal, no vertical list markers, dots via CSS pseudo-elements (not real text)
- [ ] BabyLull phone-frame desktop height ~460px, stronger shadow; screen interior empty
- [ ] Footer: `--color-surface-tint` surface, 1px hairline top divider, no dark charcoal
- [ ] Footer email: plum in light mode, lavender in dark mode, underlined, 44px min touch height
- [ ] `Get BabyLull`: `aria-disabled="true"` + `aria-describedby` + visible "Coming soon" — preserved verbatim
- [ ] Dark mode via CSS only; plum text swaps to lavender on all dark surfaces
- [ ] Wordmark element is `aria-hidden="true"` and has no interactive behavior
- [ ] Page vertical length is not longer than Stage 2 (two sections removed + hero frame removed offsets wider layout)
