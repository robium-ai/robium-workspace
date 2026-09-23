# AGENTS.md — Robium workspace

A map only. Each repository's own `AGENTS.md` is authoritative once you are
inside it.

- `robium/` — the skills plugin, the `robium-ai` CLI, and the learning engine.
- `robium-apps/` — upstream reference applications. Read-only unless you are
  contributing one upstream.
- `robium-website/` — maintainer checkout for robium.ai and its live-demo
  orchestrator, when present.
- `my-apps/` — your own applications, created by
  `npx robium-ai app new <id> --from <reference-app>`. Build here, not in
  `robium-apps/`: edits there leave that checkout dirty and
  `npx robium-ai update` will then refuse it.
- `robium-backup/` — ignored local backup/archive for assets and other
  materials that may be useful later. It is not an active source tree; do not
  edit it unless asked by name.

These are independent checkouts, not submodules. Each keeps its own remote,
branches, and history.

## Repository guidance

Claude Code loads both files below into this session automatically. Other
agents scope guidance to the enclosing repository, so read the relevant one
before changing anything under it.

@robium/AGENTS.md
@robium-apps/AGENTS.md
