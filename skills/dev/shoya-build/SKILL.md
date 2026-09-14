---
name: shoya-build
description: Implement an authorized, sufficiently defined coding change end to end with requirement-to-code traceability and risk-proportional verification. Use for approved specifications or explicit implementation requests; do not use for ideation, clarification-only, diagnosis-only, or read-only review.
---

# Shoya Build

Deliver the requested behavior with the smallest complete, proven change. Preserve user intent, unrelated work, and authorization boundaries.

## Lock the Contract

Before editing, inspect repository instructions, worktree state, relevant entry points, tests, and supplied task artifacts. Search before opening broad files. Establish a baseline that distinguishes pre-existing changes and failures from yours.

Extract internally:

- objective, scope, non-goals, constraints, and observable acceptance criteria;
- likely affected flow and verification needed for each criterion;
- consequential assumptions and risks.

Do not create a plan file or narrate this ledger unless requested. A direct request is sufficient when success is observable without choosing product intent. Resolve facts from the repository and choose conventional, reversible implementation details yourself. Ask one smallest question only when a missing choice could materially change behavior, public contracts, persisted data, permissions, security, cost, or destructive effects.

If the requested behavior already exists, verify and report it; avoid churn.

## Build the Shortest Complete Path

Work in cohesive vertical slices. For each slice:

1. Trace the real path from entry and validation through state or side effects to output and failure handling.
2. Make the smallest change that fully advances named criteria and follows local conventions.
3. Add or update a behavior-boundary test when it adds material regression evidence; never weaken assertions to bless a defect.
4. Run the narrowest meaningful test or check, then broaden only according to blast radius.

Keep criterion → code → evidence traceability in memory. Prefer observable behavior over speculative abstraction, premature generalization, or unrelated cleanup. Preserve compatible interfaces unless the contract requires change.

Verification depth follows risk: shared contracts, schemas, security, concurrency, migrations, configuration, and cross-cutting code require broader checks than isolated local behavior. Exercise relevant success, boundary, failure, permission, and state-transition paths—not a ritual checklist.

When a check fails, first determine whether the failure is caused by the change, pre-existing, or environmental. Preserve evidence. Do not stack speculative fixes, suppress errors, remove safeguards, or expand scope merely to make checks pass.

## Control Drift

Repository discoveries may change mechanics, not intent. Adapt silently when acceptance behavior is preserved. Stop for user direction when evidence conflicts with consequential intent. Continue independent criteria safely if one is blocked, but label the result partial.

Do not alter unrelated user changes. Inspect the final diff specifically for accidental edits, generated noise, secrets, debugging residue, missing migrations or documentation, and contract changes not covered by acceptance criteria.

## Completion Gate

Finish only when every in-scope criterion is implemented and linked to concrete evidence; relevant checks pass; material edge and failure paths were considered; required compatibility, configuration, docs, and migrations are present; and no known regression or unrelated edit was introduced. Passing tests alone is insufficient. A blocked or unverified criterion means partial completion.

## Compact Handoff

Lead with the outcome. Then report only:

- criterion status with primary code/test references;
- verification commands and results;
- consequential assumptions, deviations, blockers, or residual risks.

Group criteria sharing the same evidence. Use clickable file references. Omit exploration logs, routine mechanics, repeated summaries, and generic advice. Default to under 200 words unless complexity or risk requires more.
