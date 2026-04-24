# templates/client-theme

Starter template for a new client project — drops in on top of the base token set.

**Status:** `v0` placeholder. Lands in Phase 5.

## Intent

Run `pnpm dlx create-czdev-theme <client-name>` to generate a directory with:

- `brand.overrides.json` — token diff against `@czdev/tokens` primitives (client colors, fonts, radii).
- `README.md` — pre-populated with client-specific Claude context.
- `.ai/client-brand.md` — short Claude brief naming the client, constraints, and voice deltas from the base rules.

The generated directory is committed into the client project, not the agency monorepo.
