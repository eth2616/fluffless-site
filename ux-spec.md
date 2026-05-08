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
- Dark mode is a Stage 1 requirement, implemented cleanly with CSS `prefers-color-scheme` only
- Contrast target: WCAG AA

## Hero composition
- Structure: brand label (`FluffLess`), one strong headline, short supporting paragraph, CTA row, small coming-soon helper line
- Keep Hero text compact and product-first; no oversized imagery, no device mockups, no decorative illustration
- CTA row contains primary `Get BabyLull` and secondary `Support`
- On mobile, stack CTA controls with consistent spacing; on larger screens, keep them on one row if space allows

## CTA behavior
- Primary CTA in Hero: `Get BabyLull`
- Primary CTA is intentionally coming-soon and must not navigate or jump-scroll when activated
- Keep visible helper text near CTA: `Coming soon`
- Accessible label communicates coming-soon state
- Secondary CTA: `Support` links to the Support section (UX decision for Stage 1 clarity)

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
- Keep BabyLull concise with 1-2 short paragraphs describing a calm coming-soon baby sleep tracker for tired parents
- Include a compact feature list (not a large feature grid) with:
  - Quick sleep tracking
  - Simple day view calendar
  - Easy editing and backfilling
  - Local reminders
  - Live Activities
  - Data stored on your device

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
