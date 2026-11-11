---
name: tick-phase
description: Update a development plan phase file after work is done, ticking tasks and exit criteria and recording dates and results. Use when a task or phase in development-plans/ is finished, when the user says a manual check, hybrid run or deploy worked, or asks to tick, update or close a phase, even if they only name it like "04 Phase 11" or "Phase 2".
---

# Tick a phase

Phase files are how progress is tracked, so a tick has to mean the thing really happened.

First read the repo's `.claude/shared-skills.md`: section *Plans* and section *tick-phase*. They say where phase files live, what can't be checked from here, which status tables to keep in step and how results are recorded.

1. Open the phase file and find the tasks the finished work covers.
2. Tick a task as `- [x]` only with evidence:
   - Code tasks: the code exists; check it instead of assuming.
   - Manual checks, runs against real systems, deploys and anything in BTP (and the other places *Plans* lists as developer-only): only after the user reports the result. These can't be checked from here, so leave them open and name them.
3. Where the file already records results on ticked lines, follow it: add the date and the result, in the format *tick-phase* shows.
4. The phase is done when all of its **Exit criteria** are checked. Open tasks outside the exit criteria don't block it, but list them.
5. Keep the facts consistent:
   - A design change made during the work goes into the blueprint section the phase header cites.
   - API status and plan tables: update what *tick-phase* names, with its rules for when a status may be marked ✅.
   - If the phase's title or focus changed, update the tables *tick-phase* names.
6. Never add test tasks; the project has no automated tests by design. Verification tasks are the kinds *Plans* lists.

Report what you ticked, what stays open and why, and whether the exit criteria are now met.
