---
name: dori-setup
description: Set up Dori with this Claude, in one session. Use when the user says "set me up with Dori", "connect Dori", "Dori setup", or pastes the setup message from the Dori app. Connects the Dori MCP server, proves it with a first request, and picks where Claude checks Dori for work (computer or cloud).
---

# Set up Dori

Dori is the user's personal assistant: a voice wristband, an app and WhatsApp. When the user says
"Claude, …" to Dori, Dori hands that request to you as a **delegation** and shows your answer back
to them. Dori is only the pipe: you do the work with your own tools.

Speak the user's language. One step at a time; wait for the user after each step.

## 1. Connect Dori to Claude

- Check whether the Dori MCP tools are available (tools whose names end in `loopi_setup_guide`,
  `loopi_list_delegations` and so on; this plugin's server is called `dori`).
- Not available or not signed in: tell the user to type `/mcp`, choose **dori**, then **Authenticate**.
  A browser page opens. They tap "Open in Dori" (on a computer: scan the QR code with the phone),
  approve in the Dori app and check that the code matches. No need to type it.
- Then call `loopi_setup_guide`. It returns this connection's state (`connection.verified`) and the
  current guide. If its text differs from this skill, the guide wins: it comes from the live server.

No Dori account yet: the user installs the Dori app and signs up first. Nobody can connect without
a Dori account and their own approval in the app.

## 2. Pick where Claude checks Dori for work

Ask: **on this computer, or in the cloud?** Say the trade-off plainly:

| | Computer | Cloud |
|---|---|---|
| Runs | here, with the user's files, repos and tools | in Claude's cloud |
| When | **only while the computer is on** and Claude is open | always, even with the computer off |
| Needs | nothing more | a cloud environment (a routine at claude.ai/code), for code a repo bound to it |

Then follow `dori-computer` or `dori-cloud`.

## 3. Prove it with a first request

Ask the user to send a test from Dori: in the app, **AI Agents → Send**, or to the band:
"Claude, say hello to Dori." Then run `dori-tasks` once. When the report lands, Dori shows this agent
as **Verified** in the app, and `loopi_setup_guide` says `verified: true`. Tell the user.

## 4. Offer a ready set-up

Read [use-cases.md](use-cases.md) and offer the one that fits what the user does. Adjust the words to
their repo and work; never widen what it allows (no merging, no paying, no messaging other people
without asking).

## Done when

- `loopi_setup_guide` returns `verified: true` for this connection.
- The user knows where it runs and, for computer, that the computer must be on.
