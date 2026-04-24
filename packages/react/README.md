# @czdev/react

React primitives implementing the Editorial Organicism design system.

**Status:** `v0` scaffold. Components land in Phase 3.

## Planned primitives (ported from `czdev-site/components`)

| Component | Purpose |
|---|---|
| `Button` | Primary (gradient), Secondary (container), Tertiary (ghost). Size + variant props. |
| `Card` | Tonal-layered surface. No borders. Hover = layer shift. |
| `Input` | Surface-variant background, primary bottom-border on focus. |
| `Chip` | Filter chips — pill shape, `tertiary-fixed` unselected / `primary` selected. |
| `Nav` | Glassmorphism top nav — `surface` at 70% opacity + 20px backdrop-blur. |

Each component ships with a sibling `ComponentName.md` API contract next to the `.tsx` file — Claude reads these when generating new views that use the component.

## Design authority

Every component must conform to the rules in the repo-level `.ai/design-system-rules.md`. **No new patterns.** Add tokens first, then reference them — never hardcode.
