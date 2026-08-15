# Orca setup — test — 2026-08-16

## Primary worktree
- Selector: `main`
- id: `15f37d4f-5bd2-441e-ab19-6d1e044524a7::/Users/adamelhirch/orca/projects/test`
- Path: `/Users/adamelhirch/orca/projects/test` (isMainWorktree: true)
- The cockpit: stays on `main`, receives merged PRs, orchestrator coordinates from here. Tasks never run in it.

## Repo
- Remote: `https://github.com/adamelhirch/test.git` (origin, created public during setup, `main` pushed and tracking `origin/main`)
- Already registered in Orca (repo id `15f37d4f-5bd2-441e-ab19-6d1e044524a7`)

## Conventions
- CI-green merge gate: merge only PRs whose CI is green and tests pass; never merge red.
- One-task-one-branch: each task runs in its own branch/worktree, one branch = one PR = one responsibility; delete branch + worktree after merge.
- TDD by default.

## Issue tracker
- linear
- Workspace: `testing-orca` (id `870db740-2d63-4667-849d-363197bffef7`)
- Team: `Testing-orca` (key `TES`)
- `/orca-tasks` mirrors tasks as Linear issues and links worktrees via `orca worktree set --worktree <sel> --linear-issue <key>`.

## Agents installed
- opencode: `worker` + `orchestrator` → `~/.config/opencode/agents/{worker,orchestrator}.md`
- Claude Code: `worker` + `orchestrator` → `~/.claude/agents/{worker,orchestrator}.md`
- Verified up to date against `orca-setup` skill on 2026-08-16.

## Guides
- `orca orchestration` + `orca-cli` guides present in the Orca binary (verified `orca skills get` on 2026-08-16).

## Status
- setup complete
