---
name: dori-cloud
description: Make Dori start Claude in the cloud, always on, even with the computer off. Use after dori-setup when the user picks "cloud", or when they ask for Dori to start Claude by itself. Sets up a claude.ai/code routine bound to the user's repo with full network access, and the API token pasted in the Dori app.
---

# Dori starts Claude in the cloud

Always on: a routine at claude.ai/code runs in Claude's cloud, whether the computer is on or not.
It needs a cloud environment, set up once on a computer's browser (the routines page does not take
API triggers on the phone app).

First call `loopi_setup_guide`. Its **Routine prompt** block is the exact text to paste, and its cloud
section says whether this account has instant start (an API trigger) or uses an hourly schedule.

## Steps (the user does them at claude.ai/code/routines; you guide)

1. **New routine.**
2. **Repository:** for code work, the user's repo the work belongs to (for the game developer set-up,
   the game's repo). For lookups and drafts: none.
3. **Cloud environment → Default → settings icon → Network access: Full → Save.** The default (Trusted) reaches only
   package registries, so web lookups fail.
4. **Connectors:** turn on **Dori** (the user connects Dori to Claude at claude.ai first:
   Settings → Connectors → Add custom connector, URL from the Dori app, then approve in the app).
   Then claude.ai → Customize → Connectors → Dori → **Tool permissions → Always allow** (at least for
   claiming and reporting). Without it a routine stops and waits for an approval nobody sees.
5. **Prompt:** paste the routine prompt from `loopi_setup_guide` as is. To add a ready set-up
   (dori-setup's `use-cases.md`), add its lines after it.
6. **Trigger:**
   - Instant start available: **API**. Copy the **Fire URL** and the **token** (shown once). In the
     Dori app: **Settings → Integrations → Tasks sent to agents → Your Connections → Claude → Set up auto-send**, paste both. Dori then starts the routine the
     moment a request arrives, and the token stays sealed on Dori's server.
   - Otherwise: **Schedule**, hourly.
7. **Create.**

If you have a tool that creates routines (the `/schedule` skill), you may create it for the user with
the same repo, prompt and Dori connector; the API trigger and network access are still set on the
routines page.

## Then: prove it

Ask the user to send "Claude, say hello to Dori" from the app (AI Agents → Send) or the band. The
routine runs, reports, and the Dori app shows **Verified**. Check `loopi_setup_guide` →
`connection.verified: true`. Not verified after a few minutes: open the routine's latest run at
claude.ai/code and read why (most often network access, or the Dori connector is off).
