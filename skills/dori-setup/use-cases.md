# Ready set-ups

Offer the one that fits. Each has a place (computer or cloud) and a line the user adds to the
scheduled task's or routine's prompt, after the standard Dori line. Fill in the brackets with the user.

## Game or app developer: bugs by voice get fixed in the repo

- **Place:** cloud routine bound to the game's repository (always on), or computer, in that repo.
- **The user says to the band:** "Claude, the jump button sticks after you pause the game."
- **Add to the prompt:**
  > When a Dori delegation describes a bug in [game], reproduce it, fix it on a new branch named
  > `dori/<short-name>`, run the tests, open a pull request, and report done with the PR link.
  > Never merge, never push to the main branch, never touch release signing. If you cannot reproduce
  > it, report needs_user with one question.

## Look things up

- **Place:** cloud, no repo, network access **Full**.
- **The user says:** "Claude, what time does the science museum open tomorrow?"
- **Add to the prompt:**
  > Answer with web search. Put the answer first, then up to 3 source links.

## Write a draft

- **Place:** either.
- **The user says:** "Claude, draft a thank-you note to the team for the launch."
- **Add to the prompt:**
  > Report the draft itself as the summary, ready to copy. Do not send it anywhere.

## Repo chores while you are away from the desk

- **Place:** computer, in the repo.
- **The user says:** "Claude, why did last night's build fail?"
- **Add to the prompt:**
  > Read the logs and the recent commits. Report the cause and the smallest fix. Change code only on a
  > new branch, and never push without asking.
