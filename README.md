# robium-workspace

The parent folder for a Robium setup. It holds the cross-agent map that tells
Codex, Claude Code, and Gemini CLI which directory owns what, and nothing else.

```bash
git clone https://github.com/robium-ai/robium-workspace
cd robium-workspace
npx robium-ai setup
```

`setup` clones `robium/` (skills plugin and CLI) and `robium-apps/` (reference
applications) here as **independent checkouts, not submodules**: each keeps its
own remote, branches, and history, so `npx robium-ai update` can review them
without touching your work, and you can point either at your own fork.

Your own applications go in `my-apps/`, created on demand by
`npx robium-ai app new <id> --from <reference-app>`. See [AGENTS.md](./AGENTS.md).
