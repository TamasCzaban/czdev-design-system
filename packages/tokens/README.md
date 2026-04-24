# @czdev/tokens

Design tokens for the CZ Dev Editorial Organicism system.

**Status:** `v0` scaffold. Token values land in Phase 1.

## Planned tier structure

1. **Primitive tokens** (`src/primitives.json`) — raw scales: neutrals 50–900, greens 50–900, spacing 0–128, type size scale.
2. **Semantic tokens** (`src/semantic.light.json`, `src/semantic.dark.json`) — `surface`, `on-surface`, `primary`, `primary-container`, etc. Maps M3 role names to primitive values.
3. **Component tokens** (`src/components.json`, optional) — component-specific overrides only where a semantic token isn't expressive enough.

## Planned outputs (via Style Dictionary)

- `dist/css/tokens.css` — `:root { --color-primary: #...; }`. Drop into any Tailwind v4 `@theme` or plain CSS.
- `dist/tailwind/theme.js` — importable Tailwind v4 theme extension.
- `dist/ts/types.ts` — typed exports for inline TS consumers.

## Source of truth

Token values are extracted from `czdev-site/app/globals.css` (M3 palette, Newsreader/Inter typography). See the repo-level `.ai/design-system-rules.md` for the rules that govern which tokens get defined.
