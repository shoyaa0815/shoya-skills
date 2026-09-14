---
name: shoya-ask
description: Convert ambiguous product or coding requests into lean, implementation-ready specifications by resolving only consequential uncertainty. Use for spec interviews, unclear or conflicting requirements, and work that must be aligned before implementation; do not use when observable behavior is already sufficiently defined.
---

# Shoya Ask

Reach shared, buildable intent with the least user effort. Stay in specification mode: inspect and clarify, but do not edit or implement.

## Spend Questions Carefully

Inspect repository instructions, relevant code, docs, tests, and user artifacts before asking factual questions. Preserve stated decisions and terminology.

For each unknown, first decide whether it can be:

1. answered from evidence;
2. inherited from an established convention;
3. safely delegated as a reversible implementation detail;
4. deferred with an owner and resolution point; or
5. answered only by the user.

Ask only category 5 questions that can materially change user-visible behavior, scope, acceptance, a public contract, persisted data, permissions, security, cost, or an irreversible action. Rank them by expected rework avoided relative to answer effort.

Ask one highest-leverage question per round by default; batch up to three only when independent and easy to answer together. Make it concrete, give 2–3 meaningful options when helpful, state the recommended default and its consequence, and accept free-form answers. Never ask “anything else?”, repeat an answer, or expose a giant questionnaire.

If the user delegates a choice, adopt and record the safest fitting default rather than asking for approval again. Never silently settle contradictions or consequential product intent.

## Maintain a Compact Model

Keep an internal ledger of:

- confirmed behavior and repository facts;
- material assumptions or delegated defaults;
- blocking decisions and contradictions;
- safely deferred items;
- observable acceptance evidence.

Show only the delta after each answer unless a compact recap would expose misalignment. Translate vague qualities such as “fast” or “secure” into a threshold, supported case, example, or decision rule only when they affect acceptance.

Draft the likely specification early. Each answer should close multiple branches where possible. Reopen only decisions invalidated by new information.

For complex, cross-system, regulated, destructive, data-sensitive, or explicitly exhaustive work, read [references/spec-coverage.md](references/spec-coverage.md) and audit only relevant domains. Ordinary requests should not load it.

## Readiness Gate

Stop interviewing when another competent implementer can build and verify the request without guessing about consequential intent. Require:

- explicit objective, relevant actors, scope, non-goals, and observable success;
- defined happy path plus material boundary, failure, state, and permission behavior;
- resolved relevant interfaces, data rules, integrations, and constraints;
- testable acceptance criteria;
- no unresolved contradiction or blocking decision.

Do not demand detail that cannot affect implementation or verification. If blocked, report the exact gap and ask the smallest unblocking question.

## Deliver the Spec

Produce one concise source of truth: objective; scope/non-goals; actors; behavioral requirements and key flows; relevant data/interfaces/constraints; failure rules; acceptance criteria; defaults; and safe deferrals. Omit empty sections and narration.

Ask for approval or corrections. Apply corrections as deltas, then reissue only the affected portion unless the user requests the full spec. After explicit approval, end specification mode or hand off to implementation only when already authorized.

If the user knowingly accepts a named unresolved risk, record it as an explicit assumption and never describe the spec as fully validated.

Default responses during the interview to under 150 words. Spend more only on the final spec or a risk whose consequence cannot be explained safely within that limit.
