---
name: rename-shared-name
description: Rename a name used across the repo, such as a destination, virtual host, technical user, role or role collection, event name, admin action, CDS entity or service, app or folder. Use whenever the user wants to rename or change one of these, even a seemingly small one, because the name is repeated across code, config, blueprints, plans and READMEs.
---

# Rename a shared name

Facts are repeated across code, config and docs, so a rename that stops at the code leaves wrong instructions behind.

First read the repo's `.claude/shared-skills.md`: section *Checks* and section *rename-shared-name*. It lists what must not change without asking, the docs to update and what lives outside the repo.

1. Search the whole repo for the old name in all its forms: PascalCase, camelCase, snake_case, kebab-case, UPPER_CASE, and with spaces in prose. Skip `node_modules/`, `gen/` and `@cds-models/`. Show the user the matches grouped by area, with the count, before changing a large set.
2. Don't change these without asking:
   - What *rename-shared-name* lists as protected.
   - Dated history that describes the past, such as "renamed 2026-10-21".
3. Rename in code and config, then in the docs *rename-shared-name* lists (blueprints, phase files, READMEs, `docs/`, `CLAUDE.md`).
4. Search again for the old name, and explain every match that is left.
5. Run the lint and type check commands from *Checks*.
6. List what lives outside the repo and has to change by hand, with the commands, using the list in *rename-shared-name*. Builds and deploys are run by the developer, not by Claude.
