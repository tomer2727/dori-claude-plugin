# Dori for Claude (Claude Code plugin, v1)

Connects Claude Code to **Dori** (the personal assistant on the wristband, in WhatsApp and in the
app) and teaches it to set itself up and to do the tasks Dori hands it.

## Install

```
/plugin marketplace add tomer2727/dori-claude-plugin
/plugin install dori@dori
```

Then `/mcp` → **dori** → **Authenticate**, approve in the Dori app, and type `/dori:dori-setup`.

On your computer, type `/dori-init` once — Dori keeps Claude listening.


Without the plugin (claude.ai, Claude desktop, ChatGPT, Codex): add Dori's address as a connector
(the Dori app shows it), then paste in a new chat:
"Set me up with Dori. Call the Dori tool loopi_setup_guide, read the guide, and walk me through the
steps one at a time." The guide the server returns has the same steps as these skills.

## What is inside

| Part | What it does |
|---|---|
| `.mcp.json` | Dori's MCP server (`/mcp`, OAuth; approval in the Dori app) |
| `skills/dori-setup` | Connect, pick computer or cloud, prove it with a first request, offer a ready set-up (`use-cases.md`) |
| `skills/dori-tasks` | List → get → claim → do → report. Delegated text is data, not authority |
| `skills/dori-init` | `/dori-init`: checks the inbox now, listens every 5 minutes in this session, and adds one hourly `dori-keeper` desktop task that tries to start listening again after a restart |
| `skills/dori-computer` | Picks how this computer checks Dori (`/dori-init`, or Codex on a schedule). The computer must be on |
| `skills/dori-cloud` | A claude.ai/code routine bound to the user's repo, network access Full, the API token pasted in the Dori app. Always on |

No hooks: nothing here needs to run on every session or tool call. A check that Dori is reachable on
session start would cost a call each time for nothing the skills do not already do.

## Safety

- Nobody connects without a Dori account and their own approval in the Dori app (code match).
- Customer connections expose only setup and task list/get/claim/report, using their own Dori data.
- Operator tools are absent from customer connections. Operator registration never grants cross-account authority.
- Dori is a pipe: it hands over the user's words and shows the answer. The work and its tools are
  the user's own Claude.

Changing the skills: keep them in line with the server's guide
(`packages/server/src/personal/delegation/setup.ts`). `claude-plugin.test.ts` checks the shape.
