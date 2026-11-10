---
name: dori-computer
description: Make Claude check Dori for work on this computer, every few minutes, while the computer is on. Use after dori-setup when the user picks "computer", or when they say "check Dori while I'm working" / "keep watching Dori".
---

# Check Dori on this computer

Say this first, plainly: **this works only while the computer is on and Claude is open.** A request
sent while it is off waits in Dori until the next check. For always-on, use `dori-cloud`.

Run it in the folder the work belongs to (for code: the repo), so Dori's tasks land there.

## Pick one

### A. While this Claude Code session is open (quickest)

Tell the user to type:

```
/loop 10m /dori:dori-tasks
```

It checks every 10 minutes until the session ends. Closing the terminal stops it.

### B. A scheduled task in the Claude desktop app (survives restarts)

- If you have a scheduled-task tool (the Claude desktop app's `create_scheduled_task`), create one:
  - prompt: `Run the dori-tasks skill: check my Dori inbox and do any new delegation.`
  - folder: the current one;
  - schedule: the shortest interval it offers (every 15 minutes or hourly).
- Otherwise give the user the steps: Claude desktop app → Code → Scheduled → New task, the same prompt,
  this folder, the shortest interval.

It runs only while the desktop app is open and the computer is awake.

### C. Codex instead of Claude

`codex exec "Check my Dori inbox and do any new delegation, following Dori's rules."` from cron or
launchd every 10–15 minutes, in the work folder (or the Codex app's automations, if the user has them).

## Then

Run `dori-tasks` once now, so a test the user already sent is answered, and confirm with
`loopi_setup_guide` that `connection.verified` is `true`.
