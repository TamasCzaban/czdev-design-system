# Design System Rules — Editorial Organicism

> **Single source of truth for the CZ Dev visual voice.** Every styling, layout, token, and component decision — in this repo, and in every client project that imports from it — must conform to the rules below. If a rule must be broken, update this file first.

**Scope:** Load-bearing summary (Phase 0). Full per-topic rule files land in `packages/rules/*.md` during Phase 2.

---

## The creative north star

**"The Clinical Atelier."** In the healthcare and professional-services space, trust is usually coded as sterile blue rectangles and Helvetica. We reject that. Instead: the prestige of a botanical journal meets the precision of modern medical technology. Intentional asymmetry. Expansive negative space. Sharp Swiss grotesques beside soft humanist serifs. Depth felt through tonal layering — never drop shadows.

## The four load-bearing rules

### 1. The No-Line Rule

**Do not use 1px solid borders for sectioning or containment.** Define boundaries through background color shifts or subtle tonal transitions instead. A `surface-container-low` section sits directly against a `surface` background — the color change *is* the edge.

- Wrong: `border: 1px solid #e5e5e5;`
- Right: adjacent surfaces at different semantic tiers (`surface` + `surface-container-low`).
- Ghost-border fallback (rare accessibility case only): `outline-variant` at 15% opacity. Never 100% opaque.

### 2. Tonal Layering (elevation)

**Depth comes from stacking tokens, not casting shadows.** A card that "floats" does so by being `surface-container-lowest` on top of a `surface-container-low` section — the tonal step *is* the lift.

- When a true ambient shadow is unavoidable (modals): `box-shadow: 0 20px 40px rgba(20, 30, 22, 0.06)`. Note the tint — `on-surface` hue, not pure black.
- Never use 2014-era drop shadows. If "shadow" feels right in code, reconsider.

### 3. Glass & Gradient (high-value interaction surfaces)

**Escape flat color on the two highest-value surfaces: floating nav and primary CTAs.**

- Floating nav / overlays: `background: rgba(surface, 0.7); backdrop-filter: blur(20px);` — glassmorphism.
- Primary CTA: 45° linear gradient from `primary` (`#002708`) to `primary-container` (`#0f3e17`). Gives the interaction point soul.
- Secondary and tertiary buttons stay flat.

### 4. Editorial Contrast (typography)

**Two voices, in dialogue.**

- **Newsreader (serif)** — Display + Headline. The emotional, editorial voice. Generous leading (1.2–1.4). Place with intentional asymmetry.
- **Inter (sans)** — Body + UI labels. The functional, clinical voice. Modern, highly legible.
- **Micro-copy (`label-sm`, 0.6875rem):** UPPERCASE with `letter-spacing: 0.05em`. Signals professionalism.

Do not mix roles — no Inter for display, no Newsreader for form labels.

---

## The non-negotiables (short form)

**Do:**
- Embrace asymmetry. Let images bleed off one grid edge while text insets.
- Change the entire section background to transition content zones (hero `surface` → testimonial `secondary-container`).
- When in doubt, add 16px more padding than feels necessary.

**Don't:**
- 1px dividers anywhere.
- Pure black text (`#000`). Always `on-surface` (`#141e16`).
- Standard drop shadows.
- Perfect center-alignment as a default — left-aligned or staggered layouts carry the editorial weight.

---

## Token authority

Tokens follow Material 3 role names but are re-tuned for our organic palette. Extracted from `czdev-site/app/globals.css` — full migration in Phase 1.

Always reference semantic tokens by name, never raw hex:

- **Surfaces:** `surface`, `surface-container-lowest`, `surface-container-low`, `surface-container-high`, `surface-container-highest`, `surface-variant`.
- **Primary family:** `primary`, `primary-container`, `on-primary`, `on-primary-container`.
- **Secondary / Tertiary:** same shape.
- **Semantic text / structure:** `on-surface`, `on-surface-variant`, `outline-variant`, `error`, `error-container`.

**If a token is missing, extend `packages/tokens` — don't hardcode.** Missing tokens are a signal, not a license.

---

## TBD (lands in Phase 2)

The following rule areas exist in DESIGN.md but haven't been fully extracted. Flag to the user if they come up:

- **Dark mode** — token pairing strategy (first-class vs deferred).
- **Motion tokens** — durations, easings. The hero animations in `czdev-site/app/globals.css` need a home.
- **Spacing scale** — currently implicit (4px grid, 16-padding default). Needs named scale (`space-1` through `space-32`).
- **Radius scale** — `--radius`, `--radius-lg`, `--radius-xl`, `--radius-full` exist; intermediate steps likely needed.
- **Icon conventions** — Material Symbols Outlined weight/grade/optical-size defaults.

---

## When this file is wrong

If the aesthetic has genuinely evolved (validated across 2+ client projects), update this file in the same PR as the code change. The rules file is the contract; code that contradicts it is the bug.
