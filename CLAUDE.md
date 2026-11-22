# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Arcade Vault — a platform for playing games online and competing for the highest score (see README.md, in Spanish). Currently just the unmodified `create-next-app` scaffold (`app/page.tsx` is still the default template) — no game logic, routes, or data layer exist yet.

## Commands

```bash
npm run dev     # start dev server (Turbopack)
npm run build   # production build (Turbopack)
npm run start   # run production build
npm run lint    # eslint
```

There is no test runner configured yet. No `tsc` script exists; type errors surface via `next build` or the editor (`tsc --noEmit` works too since `noEmit` is already set in tsconfig).

## Architecture

- Next.js 16 App Router (`app/` directory), React 19, TypeScript, Tailwind CSS v4 via the `@tailwindcss/turbopack` loader (configured in `next.config.ts`, not a `tailwind.config` file).
- `next.config.ts` enables `cacheComponents` and `partialPrefetching` (experimental caching/prefetch behavior) and `experimental.agentFeedback`.
- **This repo's Next.js version has breaking changes from what training data assumes.** Before writing any App Router code (routing, data fetching, caching, server/client components), check `node_modules/next/dist/docs/01-app/` for current conventions rather than relying on prior Next.js knowledge.

## Workflow: Spec Driven Design

Per README.md, this project follows spec-driven design using `/spec` and `/spec-impl`, based on practices from https://github.com/Klerith/fernando-skills. Those skills are not yet installed in this repo; install with:

```bash
npx skills@latest add Klerith/fernando-skills
```

If asked to implement a feature and these skills are present, use `/spec` to produce a spec before `/spec-impl` to implement it, rather than jumping straight to code.
