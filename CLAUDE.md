# czdev-design-system — Claude Instructions

## Design authority

**`.ai/design-system-rules.md` is the single source of truth for every design decision in this repo and in any project that imports from it.**

Read it first, before any styling, token, component, or layout change. Do not introduce patterns, colors, components, or conventions that contradict it. If a new pattern seems necessary, the rules file itself must be updated — with justification — before the code lands.

## Monorepo conventions

- pnpm workspaces + Turbo. Root scripts: `pnpm build`, `pnpm dev`, `pnpm lint`, `pnpm typecheck`.
- Packages use the `@czdev/*` namespace. Workspace deps are `"workspace:*"`.
- Tokens consumed as CSS vars (from `@czdev/tokens/dist/css/tokens.css`) or Tailwind v4 theme — never hardcode hex values.
- Every React component has a sibling `ComponentName.md` declaring its prop API (once Phase 3 lands).

## Current scaffold state

- `.ai/design-system-rules.md` — stub with the four load-bearing rules. Full per-topic rule files in `packages/rules/` come in Phase 2.
- `packages/{tokens,react,rules}` — `package.json` + `README.md` only. No `src/` implementation yet.
- `apps/docs` + `templates/client-theme` — README placeholders.

See top-level `README.md` for the phased roadmap.

## Reference authority

The existing implementation at `C:/Users/Toma/projects/portfolio_sites/czdev-site` — specifically `DESIGN.md`, `app/globals.css`, and `components/*.tsx` — is the **authoritative source** for Phase 1–3 migrations. Do not re-derive values; extract them.
