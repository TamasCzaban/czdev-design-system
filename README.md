# czdev-design-system

> **Editorial Organicism.** The CZ Dev agency's headless design system — tokens, rules, and React primitives that codify our "Clinical Atelier" aesthetic so it survives across every client build.

**Status:** `v0` scaffold. Architecture is shaped; token values, rule files, and components land in subsequent phases.

## Why this exists

CZ Dev (Tamas + Zsombor) ships custom tools for founders who've outgrown no-code. Our visual voice — high-end editorial meets clinical precision, tonal surfaces over borders, serif–sans contrast — lived in a single project (`czdev-site/DESIGN.md`) and got re-derived every time a new client spun up. This repo pulls that voice out of a single project into a **portable, headless, AI-legible** system:

- **Tokens are data**, not CSS — compiled to CSS vars, a Tailwind theme, and TS types from one JSON source.
- **Rules are markdown**, read by Claude before it writes any UI.
- **Components are props-driven**, consuming tokens — never hardcoded colors or spacings.

New client work inherits the architecture by default; only the token values swap.

## Monorepo map

| Path | Purpose | Phase |
|---|---|---|
| [`.ai/design-system-rules.md`](./.ai/design-system-rules.md) | Single file Claude reads before any design decision. | 0 (scaffold) |
| [`packages/tokens`](./packages/tokens) | Primitive / semantic / component tokens as JSON, compiled via Style Dictionary. | 1 |
| [`packages/rules`](./packages/rules) | Markdown rulebook installable into client repos. | 2 |
| [`packages/react`](./packages/react) | React primitives (Button, Card, Input, Chip, Nav) consuming `@czdev/tokens`. | 3 |
| [`apps/docs`](./apps/docs) | Next.js site — live token/component/rule catalog. | 4 |
| [`templates/client-theme`](./templates/client-theme) | `create-czdev-theme <client>` — scaffolds a token override layer. | 5 |

## Architecture

```
  primitives.json ──┐
  semantic.*.json  ─┼──► Style Dictionary ──► css / tailwind / ts
  components.json  ─┘                              │
                                                   ▼
                                         @czdev/react
                                              │
                                              ▼
                                      client Next.js app
                                     (swaps brand.overrides.json)
```

## Reference systems

Architecture takes cues from three proven design systems:

- [Shopify Polaris](https://github.com/shopify/polaris) — monorepo pattern, standalone tokens package.
- [IBM Carbon](https://github.com/carbon-design-system/carbon) — themes as token diffs, not component forks.
- [GitHub Primer](https://github.com/primer/primitives) — JSON primitives compiled via Style Dictionary.

## Getting started

Requires pnpm 9+ and Node 20+.

```bash
pnpm install
pnpm build
```

Until Phase 1 lands, `build` is a no-op — the scaffold is working if the command exits 0.

## Phased roadmap

Each phase ships independently. Every phase ends with a working increment and a commit.

1. **Tokens** — extract M3 palette from `czdev-site/app/globals.css` into JSON; wire Style Dictionary.
2. **Rules** — split `DESIGN.md` into per-topic files under `packages/rules`.
3. **React primitives** — port Button, Card, Input, Chip, Nav.
4. **Docs site** — Next.js catalog at `apps/docs`.
5. **Client theme template** — `create-czdev-theme <client>` scaffolder.
6. **Publish** — register `@czdev` npm scope, GH Actions release pipeline.

## Team

- **Tamas Czaban** — backend/data/Python, Budapest. Owns tokens + build pipeline.
- **Zsombor Czaban** — frontend/UX/TS, Finland→Greece. Owns React primitives + docs site.

---

MIT licensed. See [LICENSE](./LICENSE).
