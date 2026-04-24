# @czdev/rules

The CZ Dev design rulebook — markdown only, installable as a package so client projects can `pnpm add -D @czdev/rules` and point Claude at it.

**Status:** `v0` scaffold. Individual rule files land in Phase 2.

## Planned files (extracted from `czdev-site/DESIGN.md`)

| File | Rule |
|---|---|
| `no-line.md` | No 1px borders. Boundaries come from color shifts. |
| `tonal-layering.md` | Elevation is tonal, not shadow-based. |
| `glass-gradient.md` | Glassmorphism for floating UI; gradient for primary CTAs. |
| `typography.md` | Newsreader serif + Inter sans pairing. Asymmetry rules. |
| `asymmetry.md` | Intentional left-alignment and grid-breaking. |
| `dos-and-donts.md` | The opinionated list of what to avoid and always do. |

The repo-level `.ai/design-system-rules.md` is the index that points into this package.
