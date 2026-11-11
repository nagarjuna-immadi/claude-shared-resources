---
name: implement-phase
description: Work through a development plan phase. Use when the user asks what's next in a phase, asks to implement or finish a phase or a section of one ("implement all possible code changes from Phase 11", "finish §6"), or asks for the status of a blueprint's plan.
---

# Implement a phase

Most phases mix code Claude can write with steps only the developer can do on real systems or BTP. The useful result is all the code done and a clear handover for the rest.

First read the repo's `.claude/shared-skills.md`: section *Checks*, section *Plans* and section *implement-phase*. They say which commands check the work, how to run the app locally, what only the developer does and which docs to update.

## If the user only asks what's next

Read the phase file and answer with the next open tasks in order. Say for each who does it (Claude or the developer) and what it needs (a real system running, a deploy, money for an LLM run). Don't start the work.

## Implementing

1. Read the phase file, the blueprint sections its header cites, and the phases it depends on. Check that the dependencies are met, and name any that aren't.
2. Sort the open tasks:
   - **Claude:** code, config, docs and checks that work locally (as *Checks* describes).
   - **Developer:** everything *Plans* lists as developer-only, plus builds, deploys and every agent eval run. Give the exact command; the developer decides whether to run it.
3. Do the Claude tasks in the file's order. Follow its `Design` and `Decided` sections instead of redesigning. If the code shows the plan is wrong, stop and raise it, then record the decision in the phase and the blueprint.
4. Check the result:
   - The lint and type check commands from *Checks* for the languages that changed.
   - The phase's local checks, by running the app the way *Checks* says.
   - Don't add automated tests; the project has none by design.
5. Update what the phase names under its doc tasks and deliverables, plus what *implement-phase* lists.
6. Tick what is really done with the `shared:tick-phase` skill.

## Reporting

Say what you built and checked. Then list what is left for the developer, in order, with the exact commands or the `shared:guide-deploy` skill as the next step. Don't commit unless asked.
