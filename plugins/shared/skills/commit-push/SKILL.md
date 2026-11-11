---
name: commit-push
description: Commit and push changes in this repo using its commit message format, directly on main. Use when the user asks to commit or push.
disable-model-invocation: true
---

# Commit and push

All development happens on `main`. Don't create branches.

First read the repo's `.claude/shared-skills.md`: section *Checks* and section *commit-push*. They give the lint and type check commands and the commit subject format.

1. Look at `git status` and `git diff HEAD`, including untracked files.
2. Decide what goes in. If the user said "all", take everything. Otherwise take the work from this conversation, and ask about unrelated changes you find.
3. Check for secrets in the diff: keys, tokens, passwords, service-key JSON. `.env`, `default-env.json` and `.cdsrc-private.json` must never be staged. Stop and say so if you find any.
4. Run the lint and type check commands from *Checks* for the languages that changed. Report failures before committing and fix them if they come from this work.
5. Stage files by name rather than with `git add -A`, so nothing unexpected goes in.
6. Write the message in the repo's format from *commit-push*. Look at `git log -5` if unsure:
   - Body when it helps: why, plus decisions and findings that the diff doesn't show.
   - End with the attribution lines the session specifies, if any.
7. Commit, then `git push`. Don't use `--no-verify` or force-push. If the push is rejected, pull with rebase only if the user agrees, and report what happened.

Report the commit hash and subject, and anything you left uncommitted.
