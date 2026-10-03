# skogai-fleet

A Royal Navy–style workflow for orchestrating multi-agent work.

## The old workflow

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

