# Plan — test — 2026-08-16

## Objective
Smoke-test the full Orca pipeline end-to-end with one small, isolated task: a minimal Node + TypeScript + vitest skeleton with one passing test and a minimal GitHub Actions CI workflow, merged to `main` on a green PR. "Done" = a green `t1` PR merged, `main` carrying the skeleton, and every link of setup → plan → tasks → orchestrate → gate → merge proven on a tiny surface.

## Context
- First run on an empty repo (only `docs/agents/setup.md` is tracked). Tracker: linear (workspace `testing-orca`, team `TES`). Remote: `github.com/adamelhirch/test` (created public during setup).
- Hybrid merge setup chosen in the interview: GitHub PR + CI-green gate. No CI existed; this run adds it.
- Conventions (from `docs/agents/setup.md`): CI-green merge gate, one-task-one-branch, TDD by default.

## Decisions
- Objective: pipeline smoke test, not real feature work.
- Stack: Node + TypeScript + vitest; seam = `npm test` exits 0 with ≥1 real assertion; TDD on.
- Merge gate: GitHub PR + CI-green (GitHub Actions), squash-merge; the run includes the workflow file.
- Decomposition: single task `t1` — skeleton + test + workflow in one isolated worker run.
- Isolation: `t1` runs isolated in its own worktree/branch; nothing runs in the primary worktree.
- Agent: `worker` (opencode), default model, no override.
- Tracker: linear issue mirror per setup; worktree linked via `--linear-issue`.

## Out of scope
- Any real feature, library, or domain code.
- CONTEXT.md glossary, ADRs, extra CI (lint/typecheck/coverage steps).
- `t1` must not modify anything under `docs/` (`setup.md`, `plan.md` stay untouched).

## Tasks

### t1: minimal TS skeleton + passing test + CI workflow
- spec: In this repo create a minimal Node + TypeScript project: `package.json` (npm name `test`, `"private": true`, `"type": "module"`, scripts `{ "test": "vitest run" }`, devDependencies `typescript` + `vitest`), `tsconfig.json` (strict TS, ESM), `src/greet.ts` exposing `greet(name: string): string` returning `` `Hello, ${name}!` ``, and `src/greet.test.ts` with at least one real assertion against `greet`. Add `.github/workflows/ci.yml` triggered on push + pull_request: checkout, setup-node (Node 20, npm cache), `npm ci`, `npm test`. TDD: write the test first, watch it fail, then implement and watch it go green. Verification: from a clean checkout, `npm ci && npm test` exits 0. Do not modify anything under `docs/`.
- blocked-by: none
- agent: worker
- isolated: yes

## Status
approved — 2026-08-16
