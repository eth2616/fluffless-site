# Stage 2 UX Spec — FluffLess

## 1. Visual Hierarchy

**Type scale (relative to body, not exact rem values):**
- Hero headline (h1): ~3× body — bold (700), tight line-height (~1.1), slight negative tracking (~-0.02em)
- Section headings (h2): ~1.6× body — bold, tight line-height (~1.2), slight negative tracking
- Philosophy principle titles: ~1.15× body — semibold, normal tracking
- Hero sub-copy: ~1.15× body — regular weight, muted secondary text
- Eyebrow labels: ~0.8× body — uppercase, wide letter-spacing (~0.1em), semibold, accent plum color
- Secondary feature list: ~0.9× body — muted secondary text color, regular weight
- Footer: ~0.85× body — muted

**Weight and rhythm:** Headings are the heavy layer; body copy is purely regular (400). The contrast between bold headings and light body does the hierarchy work — do not add weight to body or muted text.

**Eyebrow treatment:** Uppercase, ~0.1em letter-spacing, semibold, plum accent color. Small gap (~0.5rem) between eyebrow and headline. Used in: Hero, Featured App. Not used in Philosophy, Why Less, Privacy, or About — the heading carries those sections without eyebrow preamble.

---

## 2. Spacing and Rhythm

- **Section vertical padding:** ~64px mobile, ~96px desktop — carry from Stage 1
- **Hero:** 1.5× the standard section gap; it is the typographic anchor and needs extra air
- **Container (prose sections):** max 680px centered — carry from Stage 1
- **Featured App container:** wider wrapper, max ~1040px centered. Text column constrained to ~520px; phone frame column fills the remainder up to ~400px. All other sections stay at the 680px prose max.
- **About:** Tighten prose max to ~580px — feels personal and letter-like, not editorial-wide
- **Why Less:** Tighten prose max to ~560px — short editorial block, intimacy over spaciousness
- **Inter-element gaps inside sections:** eyebrow → headline ~0.5rem; headline → body ~1rem; body → list ~1.5rem; list → CTA ~1.5–2rem; philosophy card interior padding ~1.5rem

---

## 3. Color and Surface Plan

**Per-section backgrounds (locked):**
1. Hero: off-white `#F7F6F3`
2. Philosophy / Why FluffLess: white `#FFFFFF`
3. Featured App: warm tint — a surface one step warmer/darker than off-white (call it "section-tint"; architect defines exact value, targets a subtle warm gray with good contrast headroom for plum eyebrow text)
4. Why This Approach Matters: white `#FFFFFF`
5. Privacy: off-white `#F7F6F3`
6. Founder / About: white `#FFFFFF`
7. Footer: dark charcoal near-black (~`#1A1A1A`)

No two adjacent sections share the same background. Section background change is the primary boundary signal — do not stack a top border on top of a background change; pick one mechanism per boundary. Exception: Featured App retains its 2px plum accent top border as a deliberate featured-section marker.

**Accent plum `#5E4B73` usage (restrained):**
- Primary button fills (white text on plum fill)
- Eyebrow labels (text)
- List markers in Privacy and value-prop list
- Focus rings
- Accent rule below Hero eyebrow
- Featured App 2px top border
- Footer email link (in dark mode, use lightened variant — see below)

Do not use plum as body text, section headings, or decorative fill beyond the above. Maximum ~5 application points.

**Dark mode (CSS `prefers-color-scheme` only, no JS):**
- Background: near-black (~`#0F0F10`) — carry
- Surface: dark gray (~`#1C1C1E`) — carry
- Section-tint: one step above dark surface (~`#222224`)
- Text primary: near-white (~`#F2F2F7`) — carry
- Text secondary/muted: medium gray (~`#AEAEB2`) — carry
- Borders: subtle dark (~`#2C2C2E`) — carry
- Footer dark background: deepen further from the body dark — a very dark near-black or very dark plum-tinted charcoal so it contrasts from page bg (~`#0A0A0B`)
- **Plum text on dark surfaces will fail WCAG AA.** Lighten all text/eyebrow/link plum uses to a lavender variant (~`#C4B5D9`) in dark mode. Button fills keep `#5E4B73` — white text on plum fill passes at all breakpoints. Focus rings use the lightened variant in dark mode.

**Borders/dividers:** Subtle, 1px, border-color token. Used only where a background change alone is insufficient. Do not add borders between every section.

---

## 4. Section-by-Section UX

### 4.1 Hero
- **Desktop:** Two-column — text left (~55%), phone-frame placeholder right (~45%)
- **Mobile:** Single-column — text stack → CTA row → phone frame below, centered
- **Hierarchy:** Eyebrow → accent rule (2px wide, short, plum) → h1 → sub-copy → CTA row → [frame]
- **Phone-frame placeholder treatment:** CSS-only tall rounded rectangle (aspect ratio ~9:19.5, representing a modern iPhone). Outer frame: 2–3px stroke or slightly contrasting fill suggesting a device shell, soft border-radius matching device corners. Inner "screen" area: slightly different fill from the frame — neutral warm light (light mode) or slightly lighter dark (dark mode). A small pill notch at the top center, pure CSS (small rounded rectangle cutout). No text, no icons inside the screen area — intentionally empty so it reads as placeholder, not broken. Subtle drop shadow lifts it from the background. Desktop max height: ~480px. Mobile: ~280px tall, centered below CTA.
- **CTAs:** "See Apps" (primary, plum fill) + "Learn More" (secondary, outline). Side-by-side at ≥640px, stacked at base.
- **Edge cases:** Phone frame is never hidden — it provides visual interest even on mobile. If layout is very narrow, reduce frame width proportionally rather than hiding.

### 4.2 Philosophy / Why FluffLess
- **Desktop:** Single-column intro text (prose max), then 3-column equal-width principle cards
- **Mobile:** Intro text → 3 cards stacked single-column
- **No eyebrow.** Section heading leads directly.
- **Principle card treatment:** 1px border (border-color token), use the section-tint as card background (slightly differentiated from the white section bg), ~1.5rem interior padding, soft corner radius. Principle title: semibold, ~1.15× body. Descriptor: muted secondary text, regular weight, below the title. No icons.
- **Column transition:** Single-column through 640px, jump to 3-column at 960px. Skip 2-column awkward intermediate.

### 4.3 Featured App: BabyLull
- **Desktop:** Two-column — text left (~52%), phone frame right (~48%)
- **Mobile:** Single column — eyebrow, heading, body, primary list, secondary list, CTA stacked top; phone frame below CTA
- **Eyebrow:** "Featured App" in plum uppercase eyebrow style
- **Primary value-prop list (weight A, 3 items):** Body size or slightly larger, normal weight is fine; marker is a filled accent checkmark or solid bullet — more prominent than a dash. Items stand as short, confident value statements. This list visually leads.
- **Secondary feature list (weight B, 6 items):** ~0.9× body, muted secondary color, dash (–) marker in plum, carry Stage 1 pattern. Add a small visual separator (subtle horizontal rule or ~12px additional gap) between the two lists to signal the layer change. Reads as supporting detail, not a competing list.
- **CTA:** After both lists, in the text column. Button + "Coming soon" hint below.
- **Phone frame:** Same CSS-only treatment as Hero. Vertically centered in right column on desktop. Max ~420px tall on desktop. Below CTA on mobile.
- **Section background:** Warm tint surface — clearly distinguished from adjacent white sections.

### 4.4 Why This Approach Matters
- **Composition:** Single-column, prose max ~560px — tighter than standard for editorial intimacy
- **Hierarchy:** h2 → single body paragraph — nothing else. No eyebrow, no list, no CTA.
- **Background:** White. No top border — the white-on-white from the adjacent Featured App tint provides enough contrast signal via background shift.
- **h2 size:** Same scale as other section headings — do not step it down. The narrow prose width and lack of surrounding elements makes it feel appropriately calm without size reduction.

### 4.5 Privacy
- **Composition:** Single-column, standard prose max (680px)
- **Hierarchy:** h2 → checkmark list → italic privacy note (muted, small)
- **Background:** Off-white `#F7F6F3`. Creates a surface distinction from the surrounding white sections.
- **List markers:** Keep existing checkmark (✓) in plum accent — do not change.
- **Privacy note:** italic, muted secondary text color, slightly below body size. Carry Stage 1 pattern exactly.
- **No CTA.**

### 4.6 Founder / About
- **Composition:** Single-column, prose max ~580px (tightened for personal, letter-like feel)
- **Hierarchy:** h2 → body paragraph — no eyebrow, no list, no CTA
- **Background:** White. Contrasts with preceding off-white Privacy section.
- **Restraint is the design:** One block of body text, no embellishments.

### 4.7 Footer / Contact
- **Composition:** Single-column, centered at all breakpoints. Three content pieces stacked: brand line → email link → copyright.
- **Background:** Dark charcoal near-black. Light text. Email link uses lightened plum variant in dark mode for brand consistency (verify AA against dark charcoal — if it fails, fall back to near-white text with underline; brand consistency is not worth a contrast failure).
- **No top border** — background change is sufficient boundary signal.
- **Footer padding:** Generous (~2× standard footer pad) so the dark section has visual weight without crowding.
- **Email link:** Underlined, lightened plum on dark bg, 44px min touch height.
- **No extra links, no social, no legal pages** — footer contract from PO brief is locked.

---

## 5. Buttons / CTAs

- **Primary (filled plum):** Plum fill, white text, ~10px corner radius. Hover: opacity ~0.88 or very slight darkening — no transform or movement. Active: shadow reduces slightly. Simple, functional.
- **Secondary (outline) — locked direction:** Transparent background, plum border (2px), plum text. Hover: fills to plum + white text (carry Stage 1 pattern). Text-only direction is rejected — outline is clearer and more accessible at a glance.
- **Disabled "Get BabyLull":** Neutral surface fill, muted text, 1px border-color border, cursor default. Intentionally inactive — NOT a dimmed/faded version of the primary fill. Pattern is carry from Stage 1.
- **Accessibility on disabled:** `aria-disabled="true"` + `aria-describedby` linked to visible "Coming soon" hint text. Keep keyboard focusable. Visible focus ring on disabled button.
- **Focus:** 2.5px solid accent ring, 3px offset, via `:focus-visible`. Lightened plum on dark surfaces.
- **Hover transitions:** ≤150ms ease. All transitions collapse to near-zero under `prefers-reduced-motion`.

---

## 6. Typography

**System font stack confirmed:** `-apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif`. No remote fonts.

**Serif accent decision: AGAINST.** System serif stacks diverge significantly across platforms — New York (Apple) vs. Georgia (Windows) — producing an inconsistent heading feel that undercuts the premium editorial look the owner wants. The Apple-editorial restraint is better served by confident sans-serif headings with deliberate weight and spacing than by a serif that risks feeling generic on non-Apple devices. Mixing type families adds complexity for minimal gain.

---

## 7. Responsive Plan

**Breakpoints (carry from Stage 1):** base <640px | tablet ≥640px | desktop ≥960px

| Section | Base | Tablet | Desktop |
|---|---|---|---|
| Hero | 1-col: text → CTA → frame below | 1-col, frame larger (capped ~320px wide centered) | 2-col: text left, frame right |
| Philosophy | 1-col stacked cards | 1-col (no awkward 2-col) | 3-col equal cards |
| Featured App | 1-col: text → frame below | 1-col: text → frame below | 2-col: text left, frame right |
| Why Less | 1-col narrow prose | 1-col narrow prose | 1-col narrow prose |
| Privacy | 1-col | 1-col | 1-col |
| About | 1-col narrow prose | 1-col narrow prose | 1-col narrow prose |
| Footer | Stacked centered | Stacked centered | Stacked centered |

---

## 8. Accessibility

**Plum contrast audit:**
- `#5E4B73` text on white `#FFFFFF`: ~5.2:1 — passes AA (≥4.5:1 for normal text). Safe.
- `#5E4B73` text on off-white `#F7F6F3`: ~5.0:1 — passes AA. Safe.
- `#5E4B73` text on warm tint surface: **risk — architect must verify the exact tint keeps plum eyebrow text at ≥4.5:1. If it fails, limit plum use on that surface to button fills only (white on plum is always safe).**
- White text on plum fill `#5E4B73`: ~5.2:1 — passes AA for button labels. Safe.
- Plum text on dark bg (dark mode): FAILS — use lightened lavender variant (~`#C4B5D9`) for all text/eyebrow/link/marker uses in dark mode. Button fills unaffected (fill is the element; white text on plum fill still passes).

**Keyboard focus:** All interactive elements receive a visible `:focus-visible` ring. Disabled button remains keyboard-reachable and also receives a focus ring. No element may suppress focus visibility.

**Reduced motion:** `prefers-reduced-motion: reduce` collapses all `transition-duration` to near-zero. `scroll-behavior: auto` on reduced-motion. Carry Stage 1 pattern.

**Touch targets:** All buttons and links minimum 44px height. Footer email link must also meet 44px minimum.

**Semantic structure:** One `h1` (Hero only). Sequential `h2` per section. Landmark regions (`<main>`, `<footer>`, `<section>`). Privacy list and feature lists use proper `<ul>`/`<li>` with accessible `aria-label` where context is ambiguous.

---

## 9. Acceptance Criteria for UX

- [ ] Page renders exactly 7 sections in the locked order with correct IDs for anchor navigation
- [ ] Hero shows eyebrow, accent rule, h1, sub-copy, two-CTA row, and CSS-only phone frame placeholder
- [ ] Phone frame contains no image assets, no placeholder text inside the screen area, and reads as intentional
- [ ] "See Apps" → BabyLull section; "Learn More" → Philosophy section (live same-page anchors)
- [ ] Philosophy renders 3 cards: 3-column on desktop (≥960px), single-column on mobile
- [ ] Featured App renders two-column text/frame on desktop (≥960px), single-column stacked on mobile
- [ ] BabyLull value-prop list (3 items, weight A) is visually heavier than the feature list (6 items, weight B)
- [ ] Both BabyLull lists are present; a visual separator clearly distinguishes them
- [ ] "Get BabyLull" uses `aria-disabled="true"` + `aria-describedby` + visible "Coming soon" hint; appears intentionally inactive
- [ ] Section backgrounds alternate per the locked surface plan; no two adjacent sections share the same background
- [ ] Footer uses dark charcoal background with light text and brand line + email + copyright
- [ ] Plum is restricted to eyebrows, markers, button fills, focus rings, accent rule, Featured App top border
- [ ] Dark mode is applied via CSS `prefers-color-scheme` only; no JavaScript
- [ ] Plum text elements on all surfaces pass WCAG AA (architect verifies tinted surface)
- [ ] Dark mode uses lightened plum variant for all text/link/eyebrow/marker uses
- [ ] All interactive elements have visible `:focus-visible` rings including the disabled CTA
- [ ] All buttons and links meet 44px minimum touch target height
- [ ] `prefers-reduced-motion` collapses all transition durations to near-zero and disables smooth scroll
- [ ] System font stack only — no remote font requests at any network level
- [ ] No JavaScript required for any visual or layout behavior
