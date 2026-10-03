# skogai-fleet

Entry point for the Nelson remake: a Royal Navy–style workflow for orchestrating
multi-agent work (parallel captains, quality gates, a captain's log).

## What's here

| Path | What it is |
|---|---|
| `skills/nelson/SKILL.md` | The skill. An 8-phase workflow plus standing orders, damage control and doctrine sections. |
| `skills/nelson/references/` | Templates and detailed rules the skill points at (sailing orders, battle plan, squadron composition, crew roles, action stations, damage control, standing orders). |
| `skogai/experiments/` | Incubating material from an older Nelson snapshot. **Not loaded at runtime.** To be merged when getting started. |
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

## Placeholder convention

The helper scripts the skill calls do not exist yet. Every place that would call one is
marked with a placeholder instead of a command:

- `TODO(script:<name>) <subcommand>`: a call to a helper that is not built yet.
  `<name>` is the intended script (`nelson-data`, `nelson-phase`, `nelson_conflict_scan`,
  `nelson_data_patterns`, `nelson_circuit_breakers`).
- Block form: `# TODO(script:<name>) <subcommand> — not built yet`.

`references/structured-data.md` still documents the intended arguments for each
subcommand, so it works as the spec for building them.

## Decisions and open items

- **Script references:** replaced with `TODO(script:…)` placeholders (done).
- **Project root env var:** undecided. The skill currently has no project-root reference;
  the plugin-root variable (`CLAUDE_PLUGIN_ROOT`) was removed with the script calls. Pick
  the general project-root env var when it's needed.
- **Mission state dir:** renamed from `.nelson/` to `.state/` throughout the skill
  (`paths:`, mission directory, session marker). The user-level `~/.nelson/prefs.json`
  is unchanged. It's a separate file in the user's home, not project state.
- **Plugin manifest:** still missing (`plugin.json` / `.claude-plugin/`). Not needed
  until the plugin layout is decided.
- **Experiments:** `skogai/experiments/` (`fleet-memory`, `personas`, design memo) will be
  merged when getting started. Reconcile against the in-flight branches noted in its README first.
- **Dangling reference:** `nelson-example.md` mentions `references/sailing-orders-wizard.md`,
  which does not exist in the current skill.

## Suggested order for the remake

1. Build the helper scripts behind the `TODO(script:…)` placeholders, starting from `structured-data.md`.
2. Decide the project-root env var and the plugin layout (manifest or plain skill).
3. Merge the experiments.
4. Trim `SKILL.md` toward the Quick Start in `nelson-example.md` and move detail into `references/`.
