# Stage 1 Visual Refinement Brief

## Final scope
- Refine the existing single-page FluffLess/BabyLull site to feel less dull and more visually crafted.
- Keep the current hierarchy and structure:
  - broader FluffLess hero
  - hero primary action exactly `See apps`
  - hero secondary action exactly `Support`
  - BabyLull CTA remains in BabyLull section
- Preserve premium minimalist direction and calm tone.
- Improve:
  1) hero composition
  2) section contrast/transitions
  3) typography hierarchy
  4) BabyLull featured emphasis
  5) button treatment
  6) subtle brand character

## Locked decisions for this pass
- Accent direction: shift slightly warmer.
- Copy policy: allow small non-structural copy polish only.
- BabyLull emphasis: allow one subtle new visual element only.
- Hero emphasis: allow one subtle non-illustrative anchor element only.

## Inherited constraints (still mandatory)
- Single-page static site only.
- No new sections.
- No JavaScript, frameworks, build-step changes, or backend work.
- No remote assets or third-party runtime requests.
- Preserve responsive behavior and dark mode parity.
- Keep accessibility expectations (semantic structure, focus visibility, reduced-motion-safe behavior, AA-oriented contrast).
- Keep page lightweight and GitHub Pages realistic.

## Locked strings (must remain exact)
- `See apps`
- `Support`
- `Get BabyLull`
- `Coming soon`
- `support@flufflessapp.com`
- Privacy bullets in current page:
  - `BabyLull stores data on your device`
  - `No ads`
  - `No accounts`
  - `No third-party tracking`
- `Full privacy policy coming soon`

## Measurable acceptance criteria
- Accent reads slightly warmer than the current shipped accent in `styles.css` while staying calm and restrained, validated in both light and dark mode.
- Hero composition feels more anchored through spacing/typography and one subtle non-illustrative element; no flashy visuals or heavy decoration.
- Section boundaries and surface treatment are visibly more intentional in both light and dark mode without harsh block stacking.
- Typographic hierarchy is clearer between labels, headings, body text, and feature text.
- BabyLull section receives one restrained featured treatment while remaining lightweight and text-led.
- CTA styles clearly communicate primary, secondary, and coming-soon states with consistent polish.
- Subtle brand character is present through restrained accent/anchor treatment without adding visual clutter.
- All locked strings and hierarchy remain unchanged.
- No extra sections, no new heavy interactions, no dependency creep.

## Guardrails for new visual elements
- Hero element must be non-illustrative and restrained (for example: subtle typographic mark, thin rule, or soft shape treatment).
- BabyLull featured treatment may use one subtle element only (for example: thin frame, accent rule, or soft surface emphasis).
- Not allowed: mockups, screenshots, device frames, illustration systems, card grids, animated ornaments.

## Non-goals
- No redesign into a busy marketing page.
- No testimonials, signup forms, blog modules, social clutter, pricing blocks, or new feature sections.
- No loud gradients, glassmorphism, or generic SaaS-style visuals.
- No rewritten product positioning or hierarchy changes.
