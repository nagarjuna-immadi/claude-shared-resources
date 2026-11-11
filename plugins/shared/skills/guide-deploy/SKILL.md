---
name: guide-deploy
description: Guide the developer step by step through a deploy or BTP setup they run by hand, and read the output they paste back. Use for mbt build, cf deploy, joule deploy, destinations, role collections, Event Mesh, CDS_CONFIG and Work Zone steps, and whenever the user pastes output or errors from cf, mbt or joule, cf logs, or a failing call to a deployed app (401, 403, 500), even without asking a question.
---

# Guide a deploy

The developer runs builds and deploys, and Claude guides them. A wrong step costs a long retry, so go one step at a time and read each result before moving on.

First read the repo's `.claude/shared-skills.md`: section *Checks* and section *guide-deploy*. They list the sources (deploy steps, known errors, account facts), the pre-deploy checks, what often blocks a deploy and the commands Claude must not run.

## Before the first step

Go through the pre-deploy checks *guide-deploy* lists. Run what you can yourself (the lint and type check commands from *Checks*, look for secrets in the diff) and ask the developer about the rest. Don't skip an eval gate it names (the developer runs it, never you).

Also ask about what *guide-deploy* lists as often stopping a deploy or a check.

## Each step

1. Give one step: the exact command for PowerShell, the folder to run it in, why it is needed and what success looks like. In PowerShell, use `curl.exe` (`curl` is an alias) and `--%` when the arguments contain JSON.
2. Wait for the result.
3. Read what comes back. If it worked, say so briefly and give the next step.

Don't run `mbt build`, `cf login`, `cf deploy` or other commands that change BTP yourself, nor the others *guide-deploy* names.

## When something fails

Check the known errors in the sources first. Otherwise find the cause in the code and config before suggesting a change, and say what the evidence shows: for a 403, which user and which scope or role; for a crash, the first error in the log rather than the last. If you need more, ask for one specific thing, such as `cf logs <app> --recent`.

Pasted output may hold tokens or keys. If it does, tell the developer to rotate what was exposed if it matters, and never copy those values into a file. Ask for `VCAP_APPLICATION` or a specific value rather than all of `VCAP_SERVICES`, and treat `cf env` output with the same care when the app keeps secrets in env vars.

## Afterwards

- Add new errors and their fixes to the source they belong to, and new commands with the `shared:record-command` skill.
- Tick the verified steps with the `shared:tick-phase` skill.
