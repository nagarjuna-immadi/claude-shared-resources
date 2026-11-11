---
name: create-phase
description: Create a new development plan phase file in development-plans/ and link it into the plan index and blueprint. Use when the user wants to add, plan, draft or write a new phase for a blueprint, or turns a new piece of scope into phased tasks, even if they only say something like "plan this as 04 Phase 12" or "plan Phase 2".
---

# Create a phase

A phase file is the checklist the work is built and verified from, and `shared:tick-phase` later closes it against its exit criteria. So tasks and criteria must be specific enough to check.

First read the repo's `.claude/shared-skills.md`: section *Plans* and section *create-phase*. They give the file path and numbering, the header lines, the scope and name checks, the verification section names and where to link the phase in.

## Before writing

1. Read the blueprint, the sections the phase touches, and the phases it depends on. Read one or two neighbouring phase files to match their level of detail.
2. Take the number the way *create-phase* says. Don't renumber existing phases, because other files cite them.
3. Check the scope and the names against the sources *create-phase* lists. If something conflicts or a design choice is really open, ask the user rather than writing a guess into the plan.

## The file

Name and header as *create-phase* gives them, with a two-digit number in the file name. Body:

```markdown
**Decided:** <Only if a design choice was made: absolute date, the choice and why.>

## 1. <Work area (`path/to/file`)>

- [ ] <One checkable task>

## <n>. <Local verification section, named as in create-phase>

- [ ] <What to do and what to expect>

## <n>. Deploy and check

- [ ] <Only if the phase needs it>

## Deliverables

- <What exists afterwards>

## Exit criteria

- [ ] <Observable result>
```

- Add a `## Design (decided before §1)` section after the header when the phase makes several connected decisions.
- Keep sections in build order, each named after its work area, with the file path when there is one.
- Write tasks as small, concrete steps with the real names: actions, fields, roles, edge cases to decide.
- Exit criteria describe results someone can observe, not work done. A phase with a prompt or LLM change needs its eval gate.
- Don't add unit, contract or e2e test tasks; verification is the kinds *Plans* lists.
- Plan builds and deploys as steps the developer runs by hand.
- Start every box unticked, unless the user says the work is already done.

## Link it in

Update what *create-phase* lists under *Link it in*: plan tables, the blueprint's build steps and any section whose scope or design changes. Link the phase file where a decision is recorded.

Report the file you created, what you changed elsewhere, and any decisions you left open for the user.
