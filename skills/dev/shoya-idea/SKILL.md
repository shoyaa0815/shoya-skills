---
name: shoya-idea
description: Discover and shape the highest-value next feature for an existing codebase using repository evidence, product leverage, and a compact validation plan. Use for feature ideas, roadmap candidates, or "what should we build next"; do not use when the feature is already chosen or implementation is requested.
---

# Shoya Idea

Find a feature worth building, not merely a novel one. Think broadly; report only what advances the decision.

## Ground the Opportunity

Inspect cheap, high-signal evidence first: repository instructions, product docs, manifests, structure, primary user entry points, tests, and recent work when available. Search before opening large files. Stop once the product, principal user, core loop, and capability boundary are clear enough to compare opportunities.

Separate evidence from assumptions; never invent demand, metrics, users, or architecture. Ask at most one question, only if its answer could change the winner. Otherwise state the smallest consequential assumption and continue.

Find friction and leverage in the actual user journey. Favor opportunities that strengthen the core loop, create repeated value, remove a clear blocker, or exploit an underused existing capability. Do not mistake cleanup or fashionable technology for user value.

## Select the Winner

Generate alternatives silently across adjacent improvements, workflow compression, capability expansion, and trust. Reject ideas that:

- conflict with product direction or duplicate existing behavior;
- need unverified demand to justify large scope;
- are internal refactoring without direct user leverage;
- lack an observable outcome.

Judge credible candidates by user value, strategic fit, evidence, effort, and downside risk—without fake-precision scoring. When evidence is weak, prefer a reversible experiment; when strong, favor compounding leverage.

Recommend one winner. Show alternatives only when the tradeoff is close or breadth was requested. Surface material dependencies, migrations, privacy or security boundaries, operating costs, and adoption risks.

## Shape a Buildable Feature

Define the smallest end-to-end version that tests the value hypothesis:

- target user, workflow problem, proposed behavior, and why now;
- MVP boundary and one explicit non-goal;
- likely integration points grounded in repository evidence;
- one observable success signal and the cheapest useful validation;
- largest uncertainty or failure mode.

Do not produce a full specification, architecture, backlog, or implementation plan unless asked. Do not edit code; hand an accepted idea to a specification or build workflow.

## Token Discipline

Default to a 150–250 word decision brief:

**Feature — one-line verdict**

- **Why now:** strongest repository or user-flow evidence.
- **MVP:** smallest complete behavior and its non-goal.
- **Proof:** success signal and validation method.
- **Risk:** largest uncertainty and how to contain it.
- **Next:** the single next decision or experiment.

Use terse file references instead of an exploration log. Omit known background, generic advice, exhaustive lists, scoring tables, and repeated conclusions. Expand only on request or when a consequential tradeoff requires it.
