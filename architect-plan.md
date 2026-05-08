# Stage 2 Architect Plan

Replaces the prior Stage 1 plan. Carries forward what still applies; everything below is the locked technical shape for the Coder.

## 1. File responsibilities
- `index.html` — single page: metadata, semantic structure, all copy, CTA markup. No inline styles, no `<script>`.
- `styles.css` — single stylesheet: tokens, reset, base, focus, layout, typography, components, dark mode, reduced-motion.
- No new files. No JS file. No build step. No remote assets, fonts, scripts. Local `favicon.svg` only.

## 2. Semantic structure
One `<main>` containing six `<section>` elements in this exact order, then a `<footer>` outside main:
1. `<section class="section hero">` — `<h1>`, eyebrow, accent rule, sub-copy, CTA row, phone frame
2. `<section class="section philosophy" id="philosophy">` — `<h2>`, intro `<p>`, 3 `<article class="card">` (each with `<h3>` + `<p>`)
3. `<section class="section featured" id="babylull">` — eyebrow, `<h2>`, body, primary list (`<ul class="value-list">`), separator, secondary list (`<ul class="feature-list">`), CTA, phone frame
4. `<section class="section why-less">` — `<h2>`, single `<p>`
5. `<section class="section privacy">` — `<h2>`, `<ul class="privacy-list">`, italic note
6. `<section class="section about">` — `<h2>`, single `<p>`
7. `<footer class="footer">` — brand `<p>`, `<a class="footer-email" href="mailto:…">`, copyright `<p>`

Anchor IDs: `#philosophy` (Learn More target), `#babylull` (See Apps target). Other IDs not required.

Heading order: one `<h1>` (Hero only), `<h2>` per section, `<h3>` only inside Philosophy cards.

ARIA & landmarks: implicit roles via `<main>`, `<section>`, `<footer>` are sufficient. Lists use `aria-label` only where context is ambiguous (e.g. `aria-label="BabyLull value props"` and `aria-label="BabyLull features"`). Phone frame is decorative: `aria-hidden="true"` on its wrapper.

BabyLull CTA pattern (locked, do not modify):
```
<div class="product-cta">
  <button type="button" class="btn btn-primary" aria-disabled="true" aria-describedby="babylull-coming-soon">Get BabyLull</button>
  <p class="coming-soon-hint" id="babylull-coming-soon">Coming soon</p>
</div>
```

## 3. CSS architecture and design tokens

Section order in `styles.css`: DESIGN TOKENS → RESET → BASE → FOCUS → LAYOUT → TYPOGRAPHY → HERO → BUTTONS → CARDS → LISTS (value/feature/privacy) → PHONE FRAME → FOOTER → DARK MODE OVERRIDES (single `@media (prefers-color-scheme: dark)` block at end).

### Locked tokens (light mode `:root`)
```
--color-bg:           #F7F6F3;   /* Hero + Privacy + page body */
--color-surface:      #FFFFFF;   /* Philosophy, Why Less, About, card bg */
--color-surface-tint: #F1ECE3;   /* Featured App — verified 6.57:1 vs plum */
--color-surface-dark: #1A1A1A;   /* Footer */
--color-text:         #1C1C1E;
--color-text-muted:   #56565A;
--color-text-on-dark: #F2F2F7;            /* footer primary */
--color-text-on-dark-muted: #AEAEB2;      /* footer brand/copyright */
--color-border:       #E2E2DF;
--color-accent:       #5E4B73;            /* plum fill */
--color-accent-fg:    #FFFFFF;            /* on plum fill */
--color-accent-text:  #5E4B73;            /* plum used as text/markers/rules on light */
--color-accent-on-dark:#C4B5D9;           /* lavender for footer email link, both modes */
--color-frame-shell:  #1C1C1E;
--color-frame-screen: #FAFAF9;
--font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif;
/* type scale, spacing, --section-gap, radius — carry Stage 1 verbatim */
--max-prose:  680px;
--max-wide:   1040px;
--max-narrow: 580px;
--page-padding: 1.5rem;
```

### Dark-mode swaps (single block)
```
--color-bg:           #0F0F10;
--color-surface:      #1C1C1E;
--color-surface-tint: #222224;
--color-surface-dark: #0A0A0B;
--color-text:         #F2F2F7;
--color-text-muted:   #AEAEB2;
--color-border:       #2C2C2E;
--color-accent-text:  #C4B5D9;   /* lavender swap for text/eyebrow/markers/rule */
--color-frame-shell:  #2C2C2E;
--color-frame-screen: #1C1C1E;
```
`--color-accent` (plum fill) and `--color-accent-fg` (white) are unchanged in dark mode — white-on-plum button passes AA in both modes.

### Container pattern (locked: ONE approach)
Use the existing `.container` modifier pattern:
- `.container` → `max-width: var(--max-prose)` (default, used by Hero, Why Less, Privacy, About)
- `.container--wide` → `max-width: var(--max-wide)` (Featured App only)
- `.container--narrow` → `max-width: var(--max-narrow)` (Why Less and About; UX spec tightened these)

Do not introduce per-section `max-width` overrides on `.section`. Modifier-on-container is the single pattern.

## 4. Component patterns

### Phone frame placeholder (locked structure)
Markup (used twice — Hero + Featured):
```
<div class="phone-frame" aria-hidden="true">
  <div class="phone-frame__screen"></div>
</div>
```
Sizing approach: `aspect-ratio: 9 / 19.5` with `max-height` as the primary constraint, `width: auto`, `margin-inline: auto`. Mobile cap `max-height: 280px`; desktop hero `480px`; desktop featured `420px`.

Frame: `background: var(--color-frame-shell)`, `padding: 8px` (creates bezel), `border-radius: 36px`, soft `box-shadow: 0 10px 30px rgba(0,0,0,0.12)`.

Screen (`.phone-frame__screen`): `width: 100%; height: 100%; background: var(--color-frame-screen); border-radius: 28px; position: relative;`. Intentionally empty — no text, no icon.

Notch: `.phone-frame__screen::before` — absolute, `top: 8px; left: 50%; transform: translateX(-50%); width: 32%; height: 18px; background: var(--color-frame-shell); border-radius: 12px;`. ONE pseudo-element — no `::after`.

### Card (Philosophy 3-up)
```
<article class="card">
  <h3 class="card__title">…</h3>
  <p class="card__body">…</p>
</article>
```
`background: var(--color-surface-tint)`, `border: 1px solid var(--color-border)`, `border-radius: var(--radius)`, `padding: var(--space-3)`. No hover transform.

### Two-column layouts (Hero + Featured)
Locked pattern: **CSS Grid**. Mobile-first single column, switch to two-column at `≥960px`.
- Hero: `grid-template-columns: 1fr` base; at `≥960px` `grid-template-columns: minmax(0, 1.2fr) minmax(0, 1fr)` (text ~55% / frame ~45%).
- Featured: `grid-template-columns: 1fr` base; at `≥960px` `minmax(0, 1.1fr) minmax(0, 1fr)` (text ~52% / frame ~48%).
- Philosophy 3-up: `grid-template-columns: 1fr` base; at `≥960px` `repeat(3, 1fr)`. Skip 2-col tablet step.

Do not mix flexbox and grid for the column shells. Flexbox is fine for in-row CTAs and footer stack only.

### Buttons
Carry existing `.btn`, `.btn-primary`, `.btn-secondary`, `.btn-primary[aria-disabled="true"]` styles. `min-height: 44px` already enforced. Outline secondary → fills on hover (carry Stage 1).

### Eyebrow
Single `.eyebrow` class used in Hero and Featured: `text-transform: uppercase; letter-spacing: 0.1em; font-weight: 600; font-size: ~0.8em; color: var(--color-accent-text);`. Existing `.brand-label` class is renamed to `.eyebrow` (one site-wide eyebrow component).

## 5. Responsive strategy
Mobile-first. Breakpoints: base (`<640px`), tablet (`≥640px`), desktop (`≥960px`).
- Hero columns transition at `≥960px`. CTA row stacks → side-by-side at `≥640px` (carry).
- Featured columns transition at `≥960px`. Below that, frame stacks below CTA.
- Philosophy 3-up transitions at `≥960px` only.
- Why Less, Privacy, About, Footer: single column at all breakpoints.
- Hero `<h1>` steps to `--text-4xl` at `≥640px` (carry).

## 6. Dark mode strategy
- Single `@media (prefers-color-scheme: dark)` block at the end of `styles.css` swapping tokens only.
- No JS, no toggle UI, no `data-theme` attribute.
- `--color-accent-text` swaps to lavender so every plum text/marker/rule/eyebrow auto-lightens.
- `--color-accent` (button fill) and `--color-accent-fg` are unchanged.
- Footer email uses `--color-accent-on-dark` (lavender) in BOTH modes — footer surface is dark in both modes, so plum text would fail in light mode too.

## 7. Accessibility implementation contract
- `:focus-visible` ring: `outline: 2.5px solid var(--color-accent-text); outline-offset: 3px; border-radius: 4px;` — applied globally (carry Stage 1). In dark mode the token swap auto-lightens the ring.
- All buttons and the footer email link: `min-height: 44px` (existing on `.btn`; add to `.footer-email`).
- `prefers-reduced-motion: reduce` block: `transition-duration: 0.01ms !important; animation-duration: 0.01ms !important;` and `scroll-behavior: auto`. Carry Stage 1.
- Landmarks: `<main>`, `<section>`, `<footer>`. One `<h1>`. Sequential `<h2>`. Card `<h3>` is nested under Philosophy `<h2>`.
- BabyLull CTA: `aria-disabled` + `aria-describedby` + visible "Coming soon" hint — preserved verbatim. Disabled CTA stays keyboard-focusable; focus ring not suppressed.

## 8. Implementation guardrails for the Coder
- Do NOT add any `<script>`, JS file, or inline event handler.
- Do NOT add inline styles (`style="…"`).
- Do NOT introduce CSS custom properties not defined in §3. If a new token is needed, surface it as an open question; do not invent it.
- Do NOT change any copy from the PO brief. Title Case is locked for "See Apps", "Learn More", "Get BabyLull".
- Do NOT modify the BabyLull CTA accessibility pattern (`aria-disabled` + `aria-describedby` + visible hint).
- Do NOT widen `.container--wide` past `--max-wide` (1040px) or narrow past `--max-narrow` (580px).
- Do NOT add icons, SVGs, or images that require remote assets. Keep `favicon.svg` only.
- Do NOT introduce a serif font, font import, or `@font-face`.
- Do NOT add a top border to any section whose surface change already signals the boundary. Exception: Featured App's 2px plum top border is intentional.
- Do NOT add hover transforms (translate/scale) — only opacity, color, background, border, box-shadow transitions.
- Use `.container--wide` ONLY on Featured. Use `.container--narrow` ONLY on Why Less and About.
- Use CSS Grid for column shells; do not mix in flexbox for the same shell.
- Keep eyebrow exclusively in Hero and Featured. Other sections are heading-led.
- Section order in HTML must match §2 exactly.

## 9. Risks and assumptions
- **Warm-tint contrast (resolved)**: Plum `#5E4B73` on `#F1ECE3` ≈ 6.57:1 — passes AA with comfortable headroom. Plum eyebrow on Featured surface is safe. (UX spec's stated 5.0:1 was conservative.)
- **Dark-mode footer boundary (monitor)**: `#0A0A0B` vs page `#0F0F10` is a ~1.03:1 luminance difference — perceptually subtle on some displays. Mitigation: generous footer padding + no top border per UX spec. Coder should eyeball on real OLED + non-OLED panels; if the boundary disappears, fall back to `--color-surface-dark: #050506` in dark mode (still no border).
- **Lavender footer email both modes (assumption)**: Footer is dark in both modes, so plum text fails in light mode too. Locking lavender in both modes preserves brand consistency without contrast failure (8.73:1 light, 10.36:1 dark).
- **Phone frame proportions (monitor)**: Strict 9:19.5 ratio with `max-height: 280px` mobile yields ~129px width — narrow but recognizable. Acceptable; verify it doesn't read as "broken" in-browser. If it does, relax mobile cap to `max-height: 360px`.
- **Type scale carry**: No new size tokens introduced. Eyebrow uses `~0.8em` relative sizing inside the component, not a new token.

## 10. Handoff checklist for the Coder (build order)
1. Update `:root` tokens and dark-mode block per §3 (no markup yet).
2. Add `.container--wide` and `.container--narrow` modifiers.
3. Rewrite `<main>` section order and markup per §2 (copy from PO brief verbatim).
4. Wire CTAs: `See Apps` → `#babylull`, `Learn More` → `#philosophy`.
5. Migrate `.brand-label` → `.eyebrow`; add eyebrow to Featured.
6. Build `.card` styles for Philosophy 3-up; add grid at `≥960px`.
7. Build phone-frame markup + CSS (locked structure in §4); place in Hero and Featured.
8. Featured-App two-column grid at `≥960px`; verify primary list (weight A) reads heavier than feature list (weight B); add subtle separator between the two lists.
9. Footer: dark surface, lavender email link with `min-height: 44px`, brand line + email + copyright.
10. Verify in-browser: dark mode, mobile <640px, tablet ≥640px, desktop ≥960px, keyboard focus on every interactive element (including disabled CTA), reduced-motion, and the two monitor risks above.
