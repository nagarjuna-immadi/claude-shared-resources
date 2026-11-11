# CAP and TypeScript (shared)

Applies to every CAP project in these repos. The repo's own `.claude/rules/cap-typescript.md` adds its specifics and loads for its CAP paths.

- **Stack:** TypeScript, not JavaScript, with `cds-typer` types, `tsx` for `cds watch`, `cds build` compiles, `tsc --noEmit` as type check. `@cds-models/` and `gen/` are generated; don't edit them.
- **DB:** SQLite locally, HANA Cloud on BTP.
- **Writes:** deterministic code only, never decided by an LLM.
- **No automated tests:** don't add unit, contract or e2e tests; verification is manual checks and the repo's demo scenarios.
