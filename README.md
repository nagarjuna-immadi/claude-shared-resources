# claude-shared-resources

Claude Code skills and rules shared by the SAP BTP repos `sap-tm-projects` and `stingray-s4`. Each repo keeps only what is specific to it.

## Layout

```
.claude-plugin/marketplace.json   marketplace "claude-shared-resources", lists the plugin
plugins/shared/                   plugin "shared"
  .claude-plugin/plugin.json
  skills/<name>/SKILL.md          invoked as shared:<name>
rules/*.md                        shared rules, pulled in by @ imports from each repo's CLAUDE.md
```

## Skills (plugin `shared`)

| Skill | What it does |
|---|---|
| `shared:create-phase` | New phase file in `development-plans/`, linked into the blueprint |
| `shared:implement-phase` | Work through a phase: Claude's tasks, then a handover for the developer |
| `shared:tick-phase` | Tick tasks and exit criteria only with evidence |
| `shared:guide-deploy` | Step-by-step guidance for builds and deploys the developer runs |
| `shared:record-command` | Record commands and procedures in the repo docs |
| `shared:rename-shared-name` | Rename a name across code, config and docs |
| `shared:commit-push` | Commit and push on `main` (only when asked) |

The skills hold the procedure. The facts that differ per repo (paths, commands, commit format, doc locations, names that must not change) are in each repo's **`.claude/shared-skills.md`**, which every skill reads first. A new repo that uses the plugin needs that file, with one section per skill.

## Rules

Plugins can't ship `.claude/rules` or `CLAUDE.md`, so the shared rules are imported:

```markdown
@../claude-shared-resources/rules/cap-typescript.md
@../claude-shared-resources/rules/plans-and-blueprints.md
```

The path is relative to the importing `CLAUDE.md`, so this repo must sit next to the consuming repos (`E:\claude-shared-resources`). Imported rules load in every session; the repo's own path-scoped rules in `.claude/rules/` add the specifics. The first time, Claude Code asks to approve the external imports.

## Using it in a repo

In the repo's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "claude-shared-resources": {
      "source": { "source": "directory", "path": "E:/claude-shared-resources" }
    }
  },
  "enabledPlugins": { "shared@claude-shared-resources": true }
}
```

Claude Code offers to install the plugin when the folder is trusted. By hand: `/plugin marketplace add E:/claude-shared-resources`, then `/plugin install shared@claude-shared-resources`.

Once this repo is pushed to GitHub, replace the source with `{ "source": "github", "repo": "<owner>/claude-shared-resources" }`, so it works on other machines too.

## Changing a skill

- Keep a skill generic. A fact that only holds in one repo goes into that repo's `.claude/shared-skills.md`.
- Bump `version` in `plugins/shared/.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`, then run `/plugin marketplace update claude-shared-resources` in Claude Code (or restart it) to pick up the change.
- `claude plugin validate .` checks the manifests.
