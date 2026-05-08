# Stage 3 Product Owner Brief — Surgical Correction

Stage 3 is a refinement pass on the shipped Stage 2 page, not a redesign. The Stage 2 site felt too narrow, too text-only, and too visually timid; this stage tightens composition, hierarchy, and product presence without adding sections or visual noise.

## Section reduction (from 7 to 5)
1. Hero
2. Philosophy
3. Featured App: BabyLull (now also contains a compact privacy reassurance row)
4. About FluffLess
5. Footer

**Removed as standalone sections**: `Why less can be better` (its argument is absorbed into the existing Philosophy intro and hero copy) and the standalone `Privacy` section (compact reassurance row moves into BabyLull).

## Stage 3 locked decisions (from owner)
1. **Hero visual anchor**: replace the Stage 2 CSS phone-frame with a subtle brand wordmark / monogram lockup. The CSS phone-frame moves exclusively to BabyLull, where it earns its presence.
2. **Footer**: subtle warm-tint surface with a hairline 1px top divider. Plum-accented email link. The Stage 2 dark charcoal block is dropped — too heavy for the minimalist direction.
3. **Philosophy**: no bordered cards. Present `Focused / Clear / Useful` as inline horizontal rhythm — a single styled paragraph with subtle separators, integrated into the section.

## Hero copy (carry from Stage 2)
- Eyebrow: `Simple apps. Less fluff.`
- Headline: `Apps that do the core job — clearly, simply, and without the bloat.`
- Body: `FluffLess builds focused iPhone apps for people who want useful software without clutter, unnecessary features, or gimmicks.`
- Primary CTA: `See Apps` → `#babylull`
- Secondary CTA: `Learn More` → `#philosophy`

## Philosophy copy
- Heading: `Built for people who want simple`
- Intro: `Too many apps add more to manage instead of making life easier. FluffLess takes a different approach: build useful software around the essentials, and leave the rest out.`
- Three principles, inline rhythm: `Focused — Core features first.` · `Clear — Easy to understand quickly.` · `Useful — No fluff for the sake of looking busy.`

## BabyLull section
- Eyebrow: `Featured App`
- Title: `BabyLull`
- Body: `A simple baby sleep timer for parents who want a calm, dependable tool during an exhausting season of life. Built with the FluffLess philosophy, BabyLull focuses on fast logging, clear visibility, and a product experience that stays out of the way.`
- Feature list (6 items): `Quick sleep tracking`, `Simple day view calendar`, `Easy editing and backfilling`, `Local reminders`, `Live Activities`, `Data stored on your device`
- Privacy reassurance row (4 compact items): `Data stored on your device`, `No ads`, `No accounts`, `No third-party tracking`
- CTA: `Get BabyLull` (Stage 2 coming-soon a11y pattern preserved exactly)
- Subtext: `Coming soon`
- Desktop layout: two-column — text/lists left, refined phone-frame visual right
- The Stage 2 3-item value-prop list and `<hr>` separator are removed in favor of the single feature list + privacy reassurance row

## About copy (carry from Stage 2)
- Heading: `About FluffLess`
- Body: `I started FluffLess to build simple apps without bloat, unnecessary features, or subscription models that get in the way of the core product. The goal is straightforward: create software that feels clear, useful, and easy to trust.`

## Footer
- Brand line: `FluffLess Applications — Simple iPhone apps focused on the core experience.`
- Email: `support@flufflessapp.com`
- Copyright: `© 2026 FluffLess Applications`
- Subtle warm-tint surface (light mode) with hairline 1px top divider

## Constraints (carry from Stage 2 unless overridden above)
- Static page only, GitHub Pages compatible
- `index.html` + `styles.css` only — no JS, no build step
- No remote assets, system font stack only
- WCAG AA contrast
- Mobile responsive
- BabyLull CTA accessibility pattern preserved exactly (`aria-disabled` + `aria-describedby` + visible "Coming soon")
- Dark mode via `prefers-color-scheme` only

## Acceptance criteria (Stage 3)
- Exactly 5 sections in the locked order
- Wider, more confident composition than Stage 2 — less narrow centered text rail
- BabyLull reads as the product centerpiece (after hero)
- Privacy reassurance is integrated into BabyLull; standalone Privacy section removed
- `Why less can be better` standalone section removed
- Hero anchored with a wordmark/monogram, not a phone-frame
- Footer is subtle warm-tint with hairline divider, not dark charcoal
- Philosophy uses no bordered cards
- Page feels more polished but is **not longer** than Stage 2
- All Stage 2 a11y guarantees still hold

## Non-goals (Stage 3)
- No redesign from scratch
- No new sections beyond the 5 listed
- No real screenshots
- No animations or hover transforms
- No JS, no remote requests
- No analytics, tracking, or accounts messaging beyond the existing privacy reassurance row
- The page must not feel longer or busier after these changes
