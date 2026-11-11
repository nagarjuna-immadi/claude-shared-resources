# Blueprints and plans (shared)

Applies to `blueprints/` and `development-plans/` in every repo. The repo's own `.claude/rules/plans-and-blueprints.md` adds its specifics.

- **Phase files:** tick tasks as `- [x]`. A phase is done when all of its **Exit criteria** are checked. Each file opens with a header block: `Blueprint` link with § refs, `Goal`, `Depends on`. Keep the § refs right when blueprint sections move. See the `shared:create-phase` and `shared:tick-phase` skills.
- **Keep in step:** a design change goes into both the blueprint and its phase files.
- **No test tasks.** Verification means exit criteria: manual checks, runs against a real or simulated system, demo scenarios (and LLM eval sets where the repo has agents).
- **Dates:** record decisions with absolute dates (`Decided: 2026-10-29`).
