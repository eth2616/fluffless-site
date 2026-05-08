# Stage 2 UI/UX Spec

## Visual direction
- Premium minimalist with subtle Apple-editorial influence through typography, spacing, and restraint
- Warm neutral palette with one calm accent
- No gimmicks, no loud gradients, no clutter, no fake marketing sections

## Layout and hierarchy
- Keep exact order: Hero, About, BabyLull, Support, Privacy, Footer
- Single-column, centered composition
- Prose max width: 680px
- Generous spacing: 64px vertical on mobile, 96px on desktop
- No top navigation for Stage 1

## Typography
- System stack only: `-apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif`
- Large confident headings, restrained body copy width
- Mobile-first scale with clear hierarchy

## Color and surfaces
- Neutral base + subtle surface alternation between sections
- One calm accent used sparingly for labels and subtle emphasis
- Dark mode is included in Stage 1 only if implemented cleanly with CSS `prefers-color-scheme` and no added complexity
- Contrast target: WCAG AA

## Hero composition
- Structure: brand label (`FluffLess`), one strong headline, short supporting paragraph, CTA row
- Keep Hero text compact and brand-first; no oversized imagery, no device mockups, no decorative illustration
- Hero copy positions FluffLess as a broader brand for simple apps for real life, not a baby-only product
- CTA row contains primary `See apps` and secondary `Support`
- No coming-soon helper text in Hero
- On mobile, stack CTA controls with consistent spacing; on larger screens, keep them on one row if space allows

## CTA behavior
- Hero primary CTA text is exactly `See apps` and links to `#babylull`
- Hero primary CTA is a live navigation action (no placeholder/disabled behavior)
- `See apps` target is intentionally future-ready for a later dedicated apps page link
- Secondary CTA: `Support` links to the Support section (UX decision for Stage 1 clarity)
- BabyLull section bottom CTA text is exactly `Get BabyLull`
- BabyLull CTA uses coming-soon placeholder behavior and accessibility pattern: non-navigating button with `aria-disabled=\"true\"`, visible `Coming soon` hint, and `aria-describedby` linkage

## Support behavior
- Show visible text `support@flufflessapp.com`
- Also provide `mailto:support@flufflessapp.com`

## Privacy content requirements
Inline section must include:
- BabyLull stores data on your device
- No ads
- No accounts
- No third-party tracking
- `Full privacy policy coming soon`

## BabyLull content requirements
- Keep BabyLull concise with 1-2 short paragraphs describing a calm coming-soon baby sleep tracker for tired parents, what it is for, and why it is being built
- Include a compact feature list (not a large feature grid) with:
  - Quick sleep tracking
  - Simple day view calendar
  - Easy editing and backfilling
  - Local reminders
  - Live Activities
  - Data stored on your device
- Add `Get BabyLull` CTA at the bottom of BabyLull section after the feature list, with the coming-soon/accessibility pattern

## About content requirements
- About includes 1-2 short paragraphs focused on FluffLess brand philosophy and build intent
- About should support Hero context without repeating Hero headline/tagline message
- About remains brand-level and avoids product-feature detail duplication

## Responsive breakpoints
- Base: under 640px
- Tablet: 640px and up
- Desktop: 960px and up

## Accessibility and semantics
- Semantic landmarks and heading order
- Visible keyboard focus states
- Respect reduced-motion preferences
- Touch targets and controls remain usable on mobile

## Metadata and indexing
- Include title, meta description, social preview metadata, favicon
- Indexable (`index,follow`)
- Use only local assets and no runtime third-party requests (including fonts, scripts, analytics, or remote media)

## Copy tone and footer
- Section copy stays short, calm, warm, clear, and trustworthy; avoid hype or unsupported claims
- Footer content: `FluffLess`, current year, minimal styling, no extra link clutter
