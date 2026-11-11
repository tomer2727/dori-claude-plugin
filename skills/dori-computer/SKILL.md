---
name: dori-computer
description: Make Claude check Dori for work on this computer, every few minutes, while the computer is on. Use after dori-setup when the user picks "computer", or when they say "check Dori while I'm working" / "keep watching Dori".
---

# Check Dori on this computer

Say this first, plainly: **this works only while the computer is on and Claude is open.** A request
sent while it is off waits in Dori until the next check. For always-on, use `dori-cloud`.

Run it in the folder the work belongs to (for code: the repo), so Dori's tasks land there.

## Pick one

### A. Claude (the usual one)

Run the `dori-init` skill (the user can also type `/dori-init`): it checks the inbox now, listens every
5 minutes in this session, and in the Claude desktop app adds one hourly `dori-keeper` scheduled task
that tries to start listening again after a restart. It runs only while the app is open and the computer is
awake.

### B. Without the plugin's skills

Tell the user to type `/loop 5m Check my Dori inbox and do any new delegation, following Dori's rules.`
It lasts as long as the session (at most 7 days).

### C. Codex instead of Claude

`codex exec "Check my Dori inbox and do any new delegation, following Dori's rules."` from cron or
launchd every 10–15 minutes, in the work folder (or the Codex app's automations, if the user has them).

## Then

Run `dori-tasks` once now, so a test the user already sent is answered, and confirm with
`loopi_setup_guide` that `connection.verified` is `true`.
