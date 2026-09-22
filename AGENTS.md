# AGENTS.md — Robium workspace map

Canonical guidance for Codex, Claude Code, Gemini CLI, and other coding agents
working anywhere under this folder.

This file is a map only: it names which directory owns what, so work lands in
the right place. Each repository's own `AGENTS.md` is the canonical authority
once you are inside it — read it before doing work there.

## Layout

`npx robium-ai setup` clones these as siblings here. They are independent
checkouts, not submodules: each has its own remote, branches, and history, and
`npx robium-ai update` reviews each one without touching your branches or
local changes.

| Directory | Owns | Guidance |
| --- | --- | --- |
| `robium/` | Skills plugin, `agents/`, hooks, the `robium-ai` CLI under `cli/`, learning engine | `robium/AGENTS.md`, plus `skills/AGENTS.md` and `learnings/AGENTS.md` |
| `robium-apps/` | Upstream reference applications and `REGISTRY.md`. **Read-only for you** — see below | `robium-apps/AGENTS.md` |
| `my-apps/` | Your own applications, one per top-level directory. Created on demand | `my-apps/AGENTS.md` |

## Where your own applications go

**Build your applications in `my-apps/`, never in `robium-apps/`.**

`robium-apps/` is a checkout of the upstream showcase. Adding your own app
there leaves the checkout permanently dirty, and `npx robium-ai update` will
refuse to update it ("uncommitted changes; commit or stash them yourself"), so
you stop receiving new reference apps.

`my-apps/` is your own git repository with no upstream. Start an app there
with `npx robium-ai app new <id> --from <reference-app>`, which copies a
reference app out of `robium-apps/` as the starting point and leaves the
upstream checkout untouched. Point its remote at your own host whenever you
want; Robium never writes to it.

If `my-apps/` does not exist yet, create it with `npx robium-ai app new`.

## Cross-directory edges

- Application code, app docs, and demo backends → `my-apps/` (yours) or a PR
  to `robium-apps/` (contributions upstream).
- Skills, hooks, CLI, and captured learnings → `robium/`, with learnings as
  `learnings/YYYY-MM-DD-<app>.md`.
- Never edit `robium-apps/` to change how an app of yours behaves. Copy it
  into `my-apps/` first.

## Where to start a session

- **Work inside one repository** — the normal case: start your agent in that
  directory. Its `AGENTS.md` / `CLAUDE.md` / `GEMINI.md` and its hooks only
  load when it is the working directory.
- **Cross-directory work** (a skill change plus the app that proves it):
  start here, then read the relevant directory's `AGENTS.md` before editing.

The Robium plugin is installed from `robium/`, so Robium skills are available
in any session regardless of the starting directory.
