# skogai-fleet

Entry point for the Nelson remake: a Royal Navy–style workflow for orchestrating
multi-agent work (parallel captains, quality gates, a captain's log).

## What's here

| Path | What it is |
|---|---|
| `skills/nelson/SKILL.md` | The live skill. An 8-phase workflow plus standing orders, damage control and doctrine sections. |
| `skills/nelson/references/` | Templates and detailed rules the skill points at (sailing orders, battle plan, squadron composition, crew roles, action stations, damage control, standing orders). |
| `skogai/experiments/` | Incubating material salvaged from an older Nelson snapshot. **Not loaded at runtime.** |
| `nelson-example.md` | A sample version of the skill with a shorter Quick Start. Useful as a reference for tone and structure. |
| `chat.md` | Design conversation behind the metaphor and the "KRONSCH" culture-alignment idea. Background, not spec. |

## The workflow (as currently written)

1. **Sailing Orders**: outcome, metric, deadline, constraints, out-of-scope, stop criteria.
2. **The Estimate**: weigh options before committing.
3. **Battle Plan**: split work into tasks with owners, dependencies, file ownership, ship manifests.
4. **Form the Squadron**: pick mode (`single-session` / `subagents` / `agent-team`), size it (default 1 admiral + 3–6 captains, cap of 10 squadron-level agents), name ships by task weight.
5. **Get Permission to Sail**: approval gate before execution.
6. **Quarterdeck Rhythm**: checkpoints, blockers, budget.
7. **Action Stations**: risk-tiered verification before anything is marked complete.
8. **Stand Down**: captain's log with decisions, artifacts, evidence, follow-ups.

Cross-cutting sections: Standing Orders (17 named situations, e.g. `becalmed-fleet`,
`split-keel`, `press-ganged-navigator`), Damage Control (circuit breakers, rollback,
session resumption, scuttle-and-reform), and Admiralty Doctrine.

## Known gaps to fix in the remake

These are real mismatches I found while writing this, not style notes:

- **Missing scripts.** `SKILL.md` runs `${CLAUDE_PLUGIN_ROOT}/skills/nelson/scripts/nelson-data.py status` as a
  dynamic `!` injection and references `nelson-data.py`, `nelson-phase.py`,
  `nelson_conflict_scan.py`, `nelson_data_patterns.py`. None exist in this repo.
  The skill will not run its status step as written.
- **No plugin manifest.** There is no `plugin.json` / `.claude-plugin/`, so `CLAUDE_PLUGIN_ROOT`
  has nothing to resolve to. The repo is currently a bare skill folder.
- **Dangling reference.** `nelson-example.md` mentions `references/sailing-orders-wizard.md`,
  which is not in the current skill.
- **Mission state dir.** The skill's `paths: [".nelson/**"]` and "mission directory" imply a
  `.nelson/` working folder that the skill does not yet create or document.
- **Incubating, unwired.** `skogai/experiments/` contains `fleet-memory` (shared-state
  governance), `personas` (character-voice index) and a design memo. Promote deliberately;
  the README there notes an in-flight branch conflict to reconcile first.

## Suggested order for the remake

1. Decide whether the remake is a plugin (add manifest + `skills/` layout) or a plain skill.
2. Either implement the state scripts (`nelson-data.py` etc.) or drop the `!` injection and
   the script references from `SKILL.md`.
3. Define the `.nelson/` mission-state layout once and point everything at it.
4. Trim `SKILL.md` toward the Quick Start in `nelson-example.md` and move detail into `references/`.
5. Only then decide on promoting `fleet-memory` and personas.
