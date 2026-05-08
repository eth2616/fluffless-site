# Stage 3 Architect Plan — Visual Refinement

## Scope framing
- This is a refinement pass on the current shipped site.
- Do not change page structure, section order, CTA text, or CTA placement.
- Do not add sections, JavaScript, dependencies, or remote assets.

## Files to edit
- `index.html` (one additive decorative hero element only)
- `styles.css` (token and style refinements only)

## Locked content/hierarchy constraints
- Keep exact strings:
  - `See apps`
  - `Support`
  - `Get BabyLull`
  - `Coming soon`
  - `support@flufflessapp.com`
  - privacy bullets + `Full privacy policy coming soon`
- Keep hero CTA hierarchy and destinations unchanged.
- Keep BabyLull CTA `aria-disabled` + `aria-describedby` pattern.

## Implementation shape

### 1) Hero anchor element
- Add one decorative non-illustrative element in hero:
  - `<span class="hero-rule" aria-hidden="true"></span>` after `.brand-label`.
- Keep hero text and CTA block unchanged.
- Spacing guardrail: avoid margin stacking between `.brand-label` and `.hero-rule`.
- Increase hero breathing room with a hero-only section-gap multiplier (or equivalent top/bottom padding bump) without changing hero content structure.

### 2) Accent warming (token-level)
- Update accent tokens to a slightly warmer periwinkle/warm-slate direction than current shipped values while keeping restrained tone.
- Keep contrast AA-oriented for:
  - primary button background vs button text
  - accent text on light and dark surfaces
  - focus visibility in both themes
- Apply in both light and dark mode token sets.
- Re-verify all accent-text consumers after token shift: brand label, section markers, list markers, support link, secondary button outline/text, and focus ring.

### 3) Section contrast and transitions
- Add subtle top boundary treatment to non-hero sections.
- BabyLull gets the single featured variant (accent top boundary) as the only added decorative element in that section.
- Ensure BabyLull accent boundary replaces, not stacks with, neutral boundary.

### 4) Typography hierarchy
- Increase H1/H2 separation on larger screens.
- Keep utility section headings restrained.
- Give BabyLull heading a slight prominence over utility sections without creating a new visual system.
- Preserve clear differentiation between label, heading, body, and feature text.
- If H2 desktop scaling is flattened to strengthen H1 contrast, explicitly verify utility headings still read intentional (not undersized).

### 5) Button treatment
- Primary active CTA should read active and intentional.
- Secondary CTA remains distinct and restrained.
- BabyLull coming-soon CTA should read intentionally inactive (not broken/faded) while preserving accessibility attributes.

## Risks and safeguards
- Risk: warmer accent can reduce contrast.
  - Safeguard: verify AA-oriented contrast in both themes before finalizing.
- Risk: section boundaries can look heavy.
  - Safeguard: keep boundary treatment subtle and consistent.
- Risk: hero rule can create awkward spacing.
  - Safeguard: explicitly resolve label/rule spacing and test mobile + desktop.

## Verification checklist for coder
- Hero still contains exact CTA texts and links; no hero copy hierarchy regressions.
- Exactly one new decorative hero element added, non-illustrative, aria-hidden.
- BabyLull remains the only section with featured boundary variant.
- Buttons communicate active/secondary/coming-soon states clearly.
- Locked strings remain exact.
- Section order and semantics unchanged.
- No JS, no new dependencies, no remote assets.
- Light and dark mode both visually coherent with improved contrast and hierarchy.
