# skogai-fleet

a remake of a older "nelson" claude code-plugin with focus on making each crew member into an agent with a specialized prompt, tooling, state and personality. 

## routes

- @SKILL.md the old skill for the nelson plugin 
- @PERSONAS.md a example of how personas could work in the new setup
- @personas-index.md a example of how a index could be presented when setting up the squadron

## the old workflow to be replaced and/or updated

1. **sailing orders**: outcome, metric, deadline, constraints, out-of-scope, stop criteria.
2. **the estimate**: weigh options before committing.
3. **battle plan**: split work into tasks with owners, dependencies, file ownership, ship manifests.
4. **form the squadron**: pick mode (`single-session` / `subagents` / `agent-team`), size it (default 1 admiral + 3–6 captains, cap of 10 squadron-level agents), name ships by task weight.
5. **get permission to sail**: approval gate before execution.
6. **quarterdeck rhythm**: checkpoints, blockers, budget.
7. **action stations**: risk-tiered verification before anything is marked complete.
8. **stand down**: captain's log with decisions, artifacts, evidence, follow-ups.

cross-cutting sections: standing orders (17 named situations, e.g. `becalmed-fleet`, `split-keel`, `press-ganged-navigator`), damage control (circuit breakers, rollback, session resumption, scuttle-and-reform), and admiralty doctrine.

