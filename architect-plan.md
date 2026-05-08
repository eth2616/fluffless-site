# Stage 3 Architect Plan

## Minimal architecture
- Use `index.html` + `styles.css` only.
- Do not add `script.js` (not needed for required behavior).
- Keep deploy target simple for GitHub Pages root hosting.

## File responsibilities
- `index.html`: metadata, semantic structure, all page copy, CTA/support/privacy markup.
- `styles.css`: design tokens, typography, layout, component styles, dark mode via `prefers-color-scheme`, accessibility focus states.

## Semantic structure
- One `<main>` containing sections in exact order:
  1. Hero
  2. About
  3. BabyLull
  4. Support
  5. Privacy
- One `<footer>` after main.
- Use one `<h1>` in Hero and `<h2>` for remaining sections.
- Keep no top navigation in Stage 1.

## CTA decision
- Hero primary CTA text is exactly `See apps`, implemented as live anchor link to `#babylull`.
- Hero secondary CTA text is exactly `Support`, implemented as live anchor link to `#support`.
- Hero contains no coming-soon helper text.
- BabyLull bottom CTA text is exactly `Get BabyLull`, placed after the feature list.
- BabyLull CTA is a non-navigating `<button type="button">` with `aria-disabled="true"` and `aria-describedby` pointing to adjacent visible helper text `Coming soon`.

## Section content requirements
- About: 1-2 short paragraphs about FluffLess intent (simple, trustworthy, anti-clutter tools for real life) and must not repeat Hero headline/tagline messaging.
- BabyLull: 1-2 short paragraphs describing BabyLull as a coming-soon baby sleep tracker for tired parents.
- BabyLull compact feature list includes:
  - Quick sleep tracking
  - Simple day view calendar
  - Easy editing and backfilling
  - Local reminders
  - Live Activities
  - Data stored on your device
- Support includes visible `support@flufflessapp.com` and `mailto:` link.
- Privacy includes:
  - BabyLull stores data on your device
  - No ads
  - No accounts
  - No third-party tracking
  - `Full privacy policy coming soon`
- Footer includes `FluffLess`, current year, minimal styling, and no extra link clutter.

## CSS and token strategy
- Mobile-first with breakpoints at `640px` and `960px`.
- Content measure around 680px max for body copy.
- Generous vertical rhythm (64px mobile / 96px desktop sections).
- Neutral palette + one calm accent.
- Use subtle surface alternation between sections with neutral tokens.
- Dark mode required in Stage 1 using CSS media query only.
- No remote fonts, scripts, or assets.
- Use system stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif`.

## Metadata and accessibility checklist
- Include title, meta description, social preview metadata, favicon, and indexable setting.
- Keep semantic landmarks and heading order.
- Visible keyboard focus states.
- Respect reduced-motion preferences.
- Meet WCAG AA contrast targets.

## Risks and assumptions
- Canonical URL and final social image may be unknown at first ship.
- Current year in footer can be static text for Stage 1.
- Accent color token may need a final visual pass.

## Handoff checklist for coding
- Create `index.html` and `styles.css`.
- Implement exact section order and required content.
- Keep runtime dependency-free static output.
- Verify mobile, desktop, dark mode, focus visibility, CTA behavior, mailto behavior, and privacy copy accuracy.
- Ensure Hero messaging is brand-level (not baby-only) and metadata aligns with that framing.
