# Stage 3 Architect Plan

Replaces the Stage 2 plan. Carries forward what still applies; everything below is the locked technical shape for the Stage 3 surgical correction.

## 1. File responsibilities
Carry from Stage 2: `index.html` + `styles.css` only. No JS, no build step, no remote assets, local `favicon.svg` only.

## 2. Semantic structure (Stage 3)
`<main>` contains FIVE `<section>` elements in this exact order, then `<footer>` outside main:
1. `<section class="section hero">` — `.hero-grid` containing `.hero-text` (eyebrow → `.hero-rule` → `<h1>` → `.hero-sub` → `.cta-row`) and `<div class="hero-wordmark" aria-hidden="true">FluffLess</div>`
2. `<section class="section philosophy" id="philosophy">` — `<h2>` → `<p class="philosophy-intro">` → `<ul class="principles">` with three `<li>` (each: `<strong>Label</strong> — descriptor.`)
3. `<section class="section featured" id="babylull">` — `.featured-grid` containing `.featured-text` (eyebrow → `<h2>` → body → `<ul class="feature-list">` 6 items → `<ul class="privacy-row">` 4 items → `.product-cta`) and `.phone-frame`
4. `<section class="section about">` — `<h2>` + body
5. `<footer class="footer">` — `.footer-inner` with brand `<p>` → `<a class="footer-email">` → copyright `<p>`

Anchors: `#philosophy`, `#babylull` (carry). One `<h1>` (Hero); `<h2>` per section; NO `<h3>` (cards removed).

Principles list is `<ul>` (decisive): three is an enumerable set. List semantics > div soup. Privacy row is `<ul>` per UX.

BabyLull CTA pattern (locked verbatim): `<button … aria-disabled="true" aria-describedby="babylull-coming-soon">Get BabyLull</button>` + `<p id="babylull-coming-soon">Coming soon</p>` inside `.product-cta`.

## 3. Token plan (Stage 3 deltas)
- ADD `--max-layout: 960px` (approved). Used by Hero and Philosophy. Sits between `--max-prose` (680) and `--max-wide` (1040).
- KEEP `--color-surface-dark` defined but unused. Cost is one CSS line. Removal requires touching both light and dark blocks for zero token-hygiene gain. Reassess at Stage 4.
- All other Stage 2 tokens carry verbatim (type scale, spacing, accent set, frame colors, `--max-prose`, `--max-wide`, `--max-narrow`).
- Footer dark-mode uses the existing `--color-surface-tint` swap (`#222224`) — no rule change needed beyond removing the `--color-surface-dark` reference in §4.

## 4. Component patterns (Stage 3)

### `.hero-wordmark` (NEW)
- Single `<div>` containing the literal text `FluffLess`. No SVG, no nested spans.
- `font-size: clamp(3.25rem, 6vw, 5rem);` — fluid from `--text-4xl` floor to ~80px ceiling. At 1280px viewport ≈ 77px.
- `font-weight: 700` (system bold). `letter-spacing: -0.02em`. `line-height: 1`.
- `color: var(--color-border)` (very muted warm gray; auto-swaps in dark via token).
- `text-align: right` within its grid cell. Hero grid `align-items: center` carries vertical centering.
- Mobile/tablet rule: `display: none` at base, `display: block` at `≥960px` only (matches Hero column split — the wordmark only appears when there's a real two-column layout for it to occupy).
- `aria-hidden="true"`. No focus, no hover, no link.

### `.principles` (NEW)
- `<ul class="principles">` — three `<li>`, `list-style: none`.
- Base (<640px): `display: flex; flex-direction: column;` with `border-top: 1px solid var(--color-border)` on `li:not(:first-child)`. `padding-block: var(--space-2)` per `<li>`.
- ≥640px: `flex-direction: row; align-items: stretch;`. Each `<li>` `flex: 1; padding-inline: var(--space-3); padding-block: 0; border-top: 0;` and `li:not(:first-child) { border-left: 1px solid var(--color-border); }`.
- Item content: `<strong>Focused</strong> — Core features first.` `<strong>` is `--color-text` weight 600. Parent `<li>` is `color: var(--color-text-muted)`. Em-dash is real text.
- No card chrome. No background. `margin-top: var(--space-4)` below the philosophy intro.

### `.phone-frame` (carry Stage 2 fix + Stage 3 tweaks)
- Used ONCE in Stage 3 (BabyLull only). Hero `.phone-frame` markup deleted.
- Base CSS unchanged: `aspect-ratio: 9 / 19.5; height: 280px; width: auto; justify-self: center; margin-inline: auto;` (Stage 2 fix: `height` not `max-height`).
- Update at `≥960px`: `.featured .phone-frame { height: 460px; box-shadow: 0 16px 48px rgba(0,0,0,0.18); }`.
- Drop `.hero .phone-frame { height: 480px; }`.

### `.privacy-row` (NEW)
- `<ul class="privacy-row">` with four `<li>`.
- Base (<640px): `display: flex; flex-direction: column; gap: 0.375rem; list-style: none;`. Pseudo dots HIDDEN via `li::after { display: none; }`.
- ≥640px: `flex-direction: row; flex-wrap: wrap; align-items: baseline; gap: 0;`. Re-enable `li::after` (override).
- `.privacy-row li { white-space: nowrap; font-size: var(--text-xs); color: var(--color-text-muted); }` — `nowrap` keeps each label intact; the entire `<li>` (label + its trailing dot) is one flex item, so wrap occurs only between items.
- `.privacy-row li:not(:last-child)::after { content: "·"; margin-inline: 0.5rem; color: var(--color-text-muted); }` — dot is bound to its `<li>`, so a stranded dot at line START is structurally impossible.
- `margin-top: var(--space-2)` from feature list above (less than gap to CTA below).

### `.footer` (Stage 3 update)
- `background-color: var(--color-surface-tint);` (light AND dark via token swap).
- `border-top: 1px solid var(--color-border);` — hairline divider.
- `padding-block: 2.5rem;` (down from 4rem).
- `.footer p { color: var(--color-text-muted); }` (drop `--color-text-on-dark-muted`).
- `.footer-email { color: var(--color-accent-text); }` — plum on tint = 6.57:1 AA in light; auto-swaps to lavender in dark via the token. Underline + 44px min-height carry.
- DO NOT reference `--color-surface-dark`, `--color-text-on-dark`, or `--color-text-on-dark-muted` anywhere in `.footer` rules.

### `.container--layout` (NEW modifier)
`.container--layout { max-width: var(--max-layout); }` — applies to Hero and Philosophy only. Mobile padding (`--page-padding` 1.5rem) unchanged.

## 5. Section background and container assignment
- Hero → `.container--layout` → `--color-bg`
- Philosophy → `.container--layout` → `--color-surface`
- BabyLull → `.container--wide` → `--color-surface-tint` (+ existing 2px plum top border)
- About → `.container--narrow` → `--color-surface`
- Footer → `.container` (default 680) → `--color-surface-tint` (+ 1px hairline top border)

Adjacency check: bg / surface / tint / surface / tint. No two adjacent share a token. ✓

## 6. Removal contract (Coder must delete)
HTML: (1) `<section class="why-less">` block; (2) `<section class="privacy">` block; (3) Hero `.phone-frame` markup; (4) BabyLull `<ul class="value-list">` and `<hr class="list-separator">`.

CSS: (5) `.cards-grid`, `.card`, `.card__title`, `.card__body`; (6) `.value-list` + `.value-list li::before`; (7) `.list-separator`; (8) `.privacy-list`, `.privacy-list li`, `.privacy-list li::before`, `.privacy-note`; (9) `.why-less` and `.privacy` background rules; (10) `.hero .phone-frame { height: 480px; }`; (11) `.footer` rules referencing `--color-surface-dark` / `--color-text-on-dark*` (replaced per §4, not just deleted).

## 7. Responsive strategy (Stage 3)
- `.hero-wordmark`: hidden <960px, shown ≥960px (matches hero column split — no awkward stacked tablet state).
- `.principles`: column-stack <640px, horizontal flex row ≥640px. (No 960px-only behavior — three short labeled items fit at 640px.)
- BabyLull two-column at ≥960px (carry). `.privacy-row`: column stack <640px, inline `flex-wrap: wrap` ≥640px.
- About + Footer: single column always (carry).
- `<h1>`: `--text-3xl` base (Stage 3 bump from 2xl), `--text-4xl` at ≥640px.
- `<h2>`: `--text-2xl` at all breakpoints (drop the ≥640px step-up). `margin-bottom: var(--space-4)`.

## 8. Accessibility implementation contract
- `.hero-wordmark`: `aria-hidden="true"`, not interactive.
- `.privacy-row`: `<ul>` semantics preserved; middle dots are CSS pseudo-content (not announced).
- BabyLull CTA: `aria-disabled` + `aria-describedby` + visible "Coming soon" — verbatim.
- `:focus-visible` ring carries (token-driven, auto-lightens in dark). Reduced-motion block carries. One `<h1>`, sequential `<h2>`, no `<h3>`.

## 9. Implementation guardrails for the Coder
Stage 2 guardrails carry: no `<script>`, no inline `style="…"`, no inline event handlers; no copy changes; no new tokens beyond §3 (Stage 3 adds exactly one: `--max-layout`); no widening past `--max-wide` or narrowing past `--max-narrow`; no SVG/image other than `favicon.svg`; no `@font-face`; no remote anything; no hover transforms — only opacity/color/background/border/box-shadow transitions; CSS Grid for column shells only; eyebrow class limited to Hero and BabyLull.

Stage 3 additions:
- Do NOT add `<svg>` or `<img>` for the wordmark — single `<div>` of pure text.
- Do NOT use flex `gap` as the privacy-row dot spacing mechanism. Spacing comes from the dot's `margin-inline`; flex `gap` is `0` at ≥640px.
- Do NOT use `display: contents`. Do NOT set `width: 100%` on `.privacy-row li`.
- Do NOT add a divider element (`<hr>`, `<span>`) inside `.principles` — dividers are `border-left` / `border-top` on `<li>`.
- Use `.container--layout` ONLY on Hero and Philosophy; `.container--wide` ONLY on BabyLull; `.container--narrow` ONLY on About.

### Mental render correctness check (mandatory before declaring done)
For each new primitive, the Coder must mentally execute the CSS at 375 / 640 / 1280 widths and confirm:
1. `.hero-wordmark` at 1280px: clamp resolves to ~77px → ~395px text width vs ~414px right grid cell — fits. Right-aligned, vertically centered. Hidden at 375px and 640px (now hidden until ≥960px).
2. `.principles` at 640px: three `<li>` at `flex: 1` ≈ 197px each; descriptors may wrap to 2 lines per `<li>` (acceptable). Vertical hairlines render between items only. At 375px: column stack with horizontal hairlines on items 2 and 3.
3. `.privacy-row` at 640px: four items inline. On wrap, the dot bound to a wrapped `<li>` ends the previous wrap line (acceptable); a stranded dot at line START is impossible by construction. At 375px: column stack, dots hidden.

## 10. Risks and assumptions
- **Wordmark presence (monitor)**: `clamp(3.25rem, 6vw, 5rem)` chosen so the word feels filled at ≥1100px without overflow. If QA reads as floating, raise the clamp ceiling to `5.5rem` — do NOT switch to a heavier weight or aggressive letter-spacing first.
- **Privacy row trailing dot (accepted)**: `::after` binds the dot to its preceding `<li>`. At wrap, dot ends a line. Preferred over the `::before` alternative (stranded dot at line start) and matches UX preference.
- **h1 mobile bump 32→40 (monitor)**: 12-word headline at 40px / 1.15 line-height on a 327px content width sets in ~4 lines (was ~3 at 32px). Acceptable. Last-resort fallback: keep `--text-2xl` at widths <360px via media query.
- **`--color-surface-dark` retained**: zero cost; revisit at Stage 4.
- **Wordmark color in dark mode**: `--color-border` swaps to `#2C2C2E` on `#0F0F10` ≈ 1.6:1. Decorative + `aria-hidden`, so AA does not apply. Verify it's faintly visible (intentional) on OLED in QA; if invisible, raise the wordmark color in the dark block to `#3A3A3C` (one-off, not a token change).

## 11. Handoff checklist for the Coder (build order)
1. Add `--max-layout: 960px` to `:root`. No other token changes.
2. Add `.container--layout` modifier in LAYOUT block.
3. Rewrite `<main>` to the 5-section structure in §2; perform all HTML deletions from §6.
4. Add `.hero-wordmark` markup + CSS (§4) with mobile/tablet-hide rule (`display: none` until ≥960px).
5. Rewrite Philosophy markup (intro + `.principles`); delete `.cards-grid`/`.card*`; add `.principles` CSS (column-stack base, row at ≥640px).
6. Update BabyLull markup (single feature-list + new `<ul class="privacy-row">`). Update `.featured .phone-frame` desktop height + shadow.
7. Update typography: `<h1>` base size, `<h2>` flat size + larger margin-bottom.
8. Rewrite `.footer` rules per §4. Delete remaining CSS blocks per §6.
9. Verify in-browser at 375 / 640 / 960 / 1280, light + dark, keyboard focus on every interactive element including disabled CTA, reduced-motion. Run the §9 mental-render check on all three new primitives.
