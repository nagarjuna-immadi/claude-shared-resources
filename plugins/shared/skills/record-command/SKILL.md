---
name: record-command
description: Record commands, transactions or a procedure the developer used in the repo docs. Use when the user says to note, record, add or write down a command or flow, such as "note this in commands-used", "note these curl commands in the CAP readme" or "record the entire deployment flow", or when a new command came up during the work.
---

# Record a command

The docs are the developer's recap of how things are done, so entries should work when pasted later.

First read the repo's `.claude/shared-skills.md`, section *record-command*. It says where general commands, app commands and procedures go, the table format and which values are stable enough to keep.

## Where it goes

- The user named a file: use that file.
- Otherwise the place *record-command* gives for a general command, a command for running or testing one app, or a whole procedure with several steps (in the order the steps are run, with the errors seen along the way).

## In the commands list

- Add a table row in the file's format, for example `| Command / tool | What it does | Used in |`, with the phase where it was first used.
- Check for an existing entry first. Extend that row for a variant instead of adding a near-copy.
- Follow what *record-command* says about new files or sections and the `_Last updated:` date (today's date).

## Writing the entry

- Write the command as it was actually run, and include variants the user asked for (with and without `--recent`).
- Commands run in PowerShell unless noted. If cmd or PowerShell need different forms, show both: `set X=Y` does nothing useful in PowerShell, and `curl` is an alias there, so use `curl.exe` and `--%` for JSON.
- Explain in a few words what it does and when to use it.
- Never write passwords, keys, tokens or service-key JSON. Replace them with a placeholder like `<token>`, and check pasted commands for them.
- Replace values specific to one run when they aren't useful later. Keep stable ones, as *record-command* lists.
