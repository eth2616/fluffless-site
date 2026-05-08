# Stage 2 Product Owner Brief

FluffLess has already shipped Stage 1 as a simple static one-page website. Stage 2 is a refined redesign of that page: more premium, engaging, and professional while preserving the brand promise of simple iPhone apps with no bloat, no manipulative subscription tactics, no tracking, and no trend-chasing gimmicks.

## Provenance

This brief consolidates two owner inputs:
1. The owner's Stage 2 change report, which explicitly required the 7-section order below (including the new `Philosophy / Why FluffLess` and `Why This Approach Matters` brand sections, and the rename of About to `Founder / About`).
2. Four follow-up owner decisions resolving conflicts with Stage 1: Privacy stays as a short brand-reinforcing section; Support collapses into the footer; hero gets a CSS-only phone-frame placeholder (no real screenshot this revision); BabyLull leads with 3 value-prop points and also keeps the Stage 1 6-feature list as a smaller secondary list; deep plum `#5E4B73` replaces periwinkle as the accent direction.

This brief supersedes the earlier `po-brief.md` for Stage 2.

## Final Approved Section Order

1. Hero
2. Philosophy / Why FluffLess
3. Featured App: BabyLull
4. Why This Approach Matters
5. Privacy
6. Founder / About
7. Footer / Contact

## Brand Direction

The site should feel calm, modern, premium, product-focused, and simple without feeling dull.

Approved tone:
- Apple/editorial restraint
- Soft premium modernism
- Clear and trustworthy
- Product-focused
- Not flashy
- Not generic SaaS
- Not dark "tech bro"

The accent direction is deep plum, using `#5E4B73` as the owner-approved direction. Final contrast pairing and exact implementation treatment belong to UX/coding.

## Hero Copy

Eyebrow:

`Simple apps. Less fluff.`

Headline:

`Apps that do the core job — clearly, simply, and without the bloat.`

Supporting copy:

`FluffLess builds focused iPhone apps for people who want useful software without clutter, unnecessary features, or gimmicks.`

Primary CTA:

`See Apps`

Secondary CTA:

`Learn More`

## Philosophy / Why FluffLess Copy

Heading:

`Built for people who want simple`

Intro:

`Too many apps add more to manage instead of making life easier. FluffLess takes a different approach: build useful software around the essentials, and leave the rest out.`

Principle blocks:

`Focused`

`Core features first.`

`Clear`

`Easy to understand quickly.`

`Useful`

`No fluff for the sake of looking busy.`

## Featured App: BabyLull Copy

Eyebrow:

`Featured App`

Title:

`BabyLull`

Body:

`A simple baby sleep timer for parents who want a calm, dependable tool during an exhausting season of life. Built with the FluffLess philosophy, BabyLull focuses on fast logging, clear visibility, and a product experience that stays out of the way.`

Primary value-prop points (lead, larger emphasis):

- `Quick sleep tracking`
- `Clear daily visibility`
- `Calm, distraction-free design`

Secondary feature list (smaller, concrete details, placed after the value-prop points):

- `Quick sleep tracking`
- `Simple day view calendar`
- `Easy editing and backfilling`
- `Local reminders`
- `Live Activities`
- `Data stored on your device`

The repetition of `Quick sleep tracking` across both lists is intentional: it serves as both a top-line value prop and a concrete feature. UX/coder may treat the two lists with clearly different visual weight so the repetition reads as reinforcement rather than duplication.

BabyLull CTA:

`Get BabyLull`

Coming-soon hint:

`Coming soon`

## Why This Approach Matters Copy

Heading:

`Why less can be better`

Body:

`Many apps have become crowded with features, aggressive monetization, and unnecessary friction. FluffLess is built on a simpler idea: software should feel clear, useful, and easy to trust.`

## Privacy Copy

Heading:

`Privacy`

Privacy bullets:

- `BabyLull stores data on your device`
- `No ads`
- `No accounts`
- `No third-party tracking`

Privacy note:

`Full privacy policy coming soon`

## Founder / About Copy

Heading:

`About FluffLess`

Body:

`I started FluffLess to build simple apps without bloat, unnecessary features, or subscription models that get in the way of the core product. The goal is straightforward: create software that feels clear, useful, and easy to trust.`

## Footer / Contact Copy

Footer statement:

`FluffLess Applications — Simple iPhone apps focused on the core experience.`

Contact:

`support@flufflessapp.com`

Required copyright line: `© 2026 FluffLess Applications` (see Footer Contract for full requirements).

## CTA Contract

Hero primary CTA:
- Text: `See Apps`
- Target: BabyLull section
- Behavior: Live same-page navigation link

Hero secondary CTA:
- Text: `Learn More`
- Target: Philosophy / Why FluffLess section
- Behavior: Live same-page navigation link

BabyLull CTA:
- Text: `Get BabyLull`
- Behavior: Coming-soon placeholder, not a live app-store link
- Must preserve the existing accessibility pattern:
  - Button uses `aria-disabled="true"`
  - Visible hint text says `Coming soon`
  - Button uses `aria-describedby` linked to the hint text

Footer contact:
- Visible email text: `support@flufflessapp.com`
- Email should be usable as a contact action

## Footer Contract

Footer must include:
- `FluffLess Applications — Simple iPhone apps focused on the core experience.`
- `support@flufflessapp.com`

Footer must also include a copyright line in the form: `© 2026 FluffLess Applications`

Footer must not introduce:
- Extra navigation clutter
- Social links
- Additional product links
- Legal pages that do not exist yet

## Constraints

Carried constraints:
- Static page only
- GitHub Pages compatible
- No backend
- No auth
- No accounts
- No data collection
- No analytics
- No tracking
- No runtime third-party requests
- Local assets only
- System font stack only
- English only
- Search indexable
- Dark mode required using CSS `prefers-color-scheme` only
- No JavaScript required for theme behavior
- Mobile responsive
- WCAG AA contrast

New Stage 2 constraints:
- Preserve the FluffLess brand identity around simple, useful iPhone apps
- Use deep plum accent direction, with `#5E4B73` as the approved starting point
- Include a subtle CSS-only phone-frame placeholder in the hero so a real screenshot can be added later
- No real screenshot is required in this revision
- Support is collapsed into the footer only
- Privacy remains a short brand-reinforcing section before Founder / About
- BabyLull remains the only featured app
- BabyLull must include both the three short value-prop points and the six concrete feature bullets

## Done Criteria / Acceptance Criteria

The Stage 2 redesign is done when:
- The page uses the approved section order exactly.
- The prior dedicated Support section is removed.
- Support contact appears in the footer.
- The Privacy section remains present with all four required bullets and `Full privacy policy coming soon`.
- Hero copy matches the approved Stage 2 copy.
- Hero CTAs are `See Apps` and `Learn More`.
- `See Apps` navigates to BabyLull.
- `Learn More` navigates to Philosophy / Why FluffLess.
- BabyLull appears as the featured app.
- BabyLull includes the approved body copy.
- BabyLull leads with the three short value-prop points.
- BabyLull also includes the six concrete feature bullets from Stage 1.
- BabyLull keeps the `Get BabyLull` coming-soon CTA pattern and accessibility behavior.
- Founder / About uses the approved founder copy.
- Footer includes the approved footer statement and support email.
- The visual direction feels more premium and professional while remaining calm, simple, and restrained.
- The site remains static, search indexable, responsive, dark-mode capable, and dependency-free.
- No analytics, tracking, backend, accounts, or third-party runtime requests are introduced.
- Copy avoids hype, unsupported claims, and generic SaaS language.

## Non-Goals

- No top navigation
- No extra pages
- No dedicated Support section
- No analytics
- No tracking
- No backend
- No auth
- No accounts
- No real screenshot in this revision
- No expansion beyond BabyLull
- No additional app sections
- No flashy or animated UI
- No AI positioning
- No pricing/subscription messaging
- No app-store availability claim until BabyLull is actually available

## Assumptions

- `See Apps`, `Learn More`, and `Get BabyLull` capitalization is locked in Title Case.
- Privacy is placed between `Why less can be better` and `Founder / About`.
- Copyright line is locked as `© 2026 FluffLess Applications`.
