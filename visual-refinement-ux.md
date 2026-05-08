# Stage 2 UX Spec — Visual Refinement

## 1) Why the page feels dull
- Accent tone reads cold and generic, reducing brand character.
- Hero composition is text-only with no anchor gesture, so the top feels flat.
- Section boundaries are subtle to the point of blending.
- BabyLull reads too similar to utility sections.
- Type scale compression (H1 vs H2) weakens hierarchy.

## 2) Revised visual approach
- Keep minimalist structure, but increase craft through composition and contrast.
- Add one restrained hero anchor element (non-illustrative).
- Give BabyLull one restrained featured treatment.
- Warm the accent slightly while preserving calm tone and AA contrast.

## 3) Concrete UX changes (minimal scope)

### Hero composition
- Add one non-illustrative anchor element below `FluffLess` label.
- Increase hero breathing room using section-gap multipliers.
- Keep hero copy and CTA hierarchy unchanged.

### Hero rule spacing fix
- Avoid stacked spacing between `.brand-label` and `.hero-rule`.
- Keep spacing token rhythm consistent so the rule sits close to the label without creating a double gap.

### Section contrast/transitions
- Add subtle top boundaries to non-hero sections.
- Ensure BabyLull accent boundary visually replaces its neutral boundary.

### Typography hierarchy
- Strengthen H1/H2 separation.
- Keep BabyLull heading slightly more prominent than utility sections.
- Acknowledge intentional tradeoff if H2 desktop scaling is flattened.

### BabyLull featured emphasis
- One subtle visual element only: top accent boundary on BabyLull section.
- No cards, screenshots, mockups, or decorative systems.

### Buttons
- Active primary button looks active.
- Secondary `Support` CTA remains visually distinct and consistent with overall button system.
- Disabled BabyLull CTA uses intentional inactive treatment (not broken/faded).
- Keep `aria-disabled` + `aria-describedby` pattern for `Get BabyLull`.

### Accent direction assumption (explicit)
- Interpret “slightly warmer” as a subtle shift from the current cool blue toward a warmer periwinkle/warm-slate family.
- Baseline: current shipped accent token in `styles.css`.
- If product intent differs, adjust within a warmer direction and re-verify.
- Validate final accent and boundary/rule visibility in both light and dark mode.

## 4) Locked hierarchy/string constraints
- Keep exact strings:
  - `See apps`
  - `Support`
  - `Get BabyLull`
  - `Coming soon`
  - `support@flufflessapp.com`
  - Privacy bullets + `Full privacy policy coming soon`
- Keep single-page structure and existing section order.

## 5) Guardrails
- No new sections.
- No heavy animation or JS.
- No remote assets/dependencies.
- No busy marketing visual style.
