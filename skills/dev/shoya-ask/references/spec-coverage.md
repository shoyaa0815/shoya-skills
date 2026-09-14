# Risk-Weighted Coverage Audit

Use only for complex, high-risk, or explicitly exhaustive specifications. Cover relevant domains; do not turn this map into a questionnaire. Resolve facts from artifacts, inherit established conventions, and ask the user only about consequential intent.

## Product

- Problem, target actor, desired outcome, success/failure signal, urgency.
- Scope, non-goals, priorities, compatibility, supported platforms or regions.
- Main journey: entry, preconditions, actions, result, feedback, cancellation and recovery.

## Behavior

- Roles and permissions, including anonymous, suspended, expired, and administrative states where plausible.
- Empty, minimum, maximum, malformed, duplicate, stale, conflicting, timeout, retry, and partial-failure cases.
- State transitions, side effects, idempotency, concurrency, and destructive-action safeguards.
- UI states: loading, empty, error, offline, success, denied; accessibility and localization when relevant.

## Contracts and Data

- Entities, required/unique/derived/sensitive fields, ownership, source of truth, units and time zones.
- Retention, deletion, audit, migration, import/export, backfill, and backward compatibility.
- API or event schemas, authentication, errors, pagination, ordering, retries, rate limits, and versioning.
- Third-party credentials, limits, availability, sandbox behavior, and degraded operation.

## Quality and Delivery

- Measurable performance, capacity, availability, recovery, privacy, security, and compliance targets.
- Observability, rollout, flags, rollback, operations, documentation, and support ownership.
- Required automated/manual/security/performance evidence, accepting party, and launch blockers.

## Audit Result

Classify each relevant domain as **resolved**, **evidence-backed convention**, **delegated default**, **safely deferred**, **not applicable**, or **blocking**. Record reasoning only for surprising classifications. A blocking item prevents approval; an irrelevant detail must not prolong the interview.
