# Stage 1 Product Owner Brief

- Brand: FluffLess
- Product: BabyLull (first app)
- Launch state: Coming soon
- Page type: Single static public webpage
- Hosting target: GitHub Pages compatible

## Required section order
1. Hero
2. About
3. BabyLull
4. Support
5. Privacy
6. Footer

## Constraints
- Static page only
- No backend, no auth, no accounts
- No data collection, no analytics, no tracking
- No runtime third-party requests (local assets only)
- English only for Stage 1
- Search indexable
- Dark mode is in scope for Stage 1 and required if implemented cleanly with CSS `prefers-color-scheme`, without added JavaScript, settings UI, dependencies, or complexity

## CTA requirements
- Hero primary action text is exactly: `See apps`
- Hero secondary action text is exactly: `Support`
- Hero `Support` action navigates to the Support section on this page
- `See apps` currently navigates to the BabyLull section on this page and is intentionally future-ready for a later apps page link
- BabyLull primary CTA text at the bottom of BabyLull section is exactly: `Get BabyLull`
- BabyLull CTA keeps the existing coming-soon placeholder and accessibility pattern

## Support requirements
- Email-only support
- Publish and link: `support@flufflessapp.com`

## Privacy requirements
- Inline privacy summary on this page
- Must include:
  - BabyLull stores data on your device
  - No ads
  - No accounts
  - No third-party tracking
- Include exact text: `Full privacy policy coming soon`
- Stage 1 can ship publicly with this placeholder

## Done criteria
- Correct section order and required content present
- Hero positions FluffLess as a broader brand for simple apps for real life (not baby-only framing)
- About section includes 1-2 short paragraphs that support brand philosophy and do not repeat Hero headline/tagline message
- BabyLull section includes 1-2 short paragraphs focused on product intent: a calm coming-soon baby sleep tracker for tired parents, what it is for, and why it is being built
- BabyLull includes a compact feature list with:
  - Quick sleep tracking
  - Simple day view calendar
  - Easy editing and backfilling
  - Local reminders
  - Live Activities
  - Data stored on your device
- Responsive mobile and desktop rendering
- Metadata updated and present (title, description, social preview, favicon) to align with broader brand-level hero
- Tone stays calm, warm, clear, and trustworthy

## Non-goals
- No full redesign or expansion into a larger marketing site
- No new pages in this revision
- No new products or product sections beyond BabyLull
- No backend, routing, dependency, or analytics changes
