# Specification Coverage Map

Use this reference to find omissions, not as a questionnaire to dump on the user. Select the questions that can materially change the result, group related ones, and derive follow-ups from the answers.

## 1. Problem and Outcome

- What problem exists now, for whom, and in what situation?
- What outcome should change after delivery?
- What evidence or metric proves success? What would count as failure?
- Why is this needed now, and is there a fixed deadline or event?
- Is the requested solution mandatory, or may a better solution to the same problem be proposed?

## 2. Actors and Permissions

- Who uses, administers, supports, audits, or receives output from the system?
- What can each role view, create, change, approve, export, or delete?
- Are anonymous, suspended, expired, invited, or partially configured users possible?
- Which actor owns each action and each recovery path?

## 3. Scope

- What exact capability is included in this delivery?
- What adjacent capability is deliberately excluded?
- What existing behavior must remain unchanged?
- Which platforms, devices, browsers, locales, regions, tenants, or versions are supported?
- Is backward compatibility required, and for how long?

## 4. User and System Flows

For each flow, determine:

- entry point and prerequisites;
- ordered actions or system events;
- validation rules and business rules;
- state transitions and side effects;
- successful result and user-visible feedback;
- cancellation, retry, timeout, duplicate action, and partial failure behavior;
- empty, minimum, maximum, malformed, stale, and conflicting input behavior.

Ask for an example of the most common case and the most dangerous failure case.

## 5. UI and Content

- What screens, components, states, and navigation changes are needed?
- What must be visible, editable, disabled, hidden, or confirmed?
- What are the loading, empty, error, offline, success, and permission-denied states?
- Are responsive breakpoints, accessibility level, keyboard behavior, or localization required?
- Is there an existing design system or reference experience to follow?
- Who supplies final copy, labels, assets, and translations?

## 6. Data and Business Rules

- What entities, fields, types, units, ranges, defaults, and relationships exist?
- Which fields are required, unique, derived, immutable, sensitive, or auditable?
- What is the source of truth? Who may change it?
- How are dates, time zones, currency, rounding, ordering, and identifiers handled?
- What are the retention, deletion, import, export, migration, and backup rules?
- How are concurrent edits, idempotency, duplication, and stale data handled?

## 7. APIs, Events, and Integrations

- Who calls whom, through what protocol, and with what authentication?
- What are the request, response, error, pagination, filtering, and versioning contracts?
- What delivery guarantees, ordering, retry, timeout, rate-limit, and idempotency rules apply?
- Which third-party limits, sandboxes, credentials, webhooks, or availability assumptions matter?
- What happens when a dependency is slow, unavailable, inconsistent, or returns partial data?

## 8. Quality Attributes

Turn each relevant quality into a measurable target:

- performance: latency percentile, throughput, payload, or dataset size;
- availability and resilience: uptime, recovery time, recovery point, degradation behavior;
- scalability: expected and peak load, growth horizon, concurrency;
- security: authentication, authorization, encryption, abuse prevention, secrets;
- privacy and compliance: personal data, consent, residency, retention, audit requirements;
- accessibility and usability: target standard and supported interaction modes;
- observability: logs, metrics, traces, alerts, dashboards, and audit trail;
- maintainability: ownership, supported runtime, dependency or architecture constraints.

## 9. Delivery and Operations

- What codebase, environment, architecture, conventions, and dependencies constrain the work?
- Are schema changes, backfills, flags, staged rollout, or rollback required?
- How will existing users or data transition?
- Who deploys, approves, operates, and supports it?
- What documentation, training, analytics, monitoring, or runbooks are deliverables?

## 10. Verification and Acceptance

- Express each acceptance criterion as a specific setup/action/result or other observable rule.
- Cover success, validation failure, dependency failure, boundary values, and permission differences.
- Identify required automated tests, manual checks, security checks, performance tests, and supported environments.
- State who accepts the result and what evidence they need.
- Distinguish launch-blocking criteria from desirable follow-ups.

## 11. Priority and Tradeoffs

- Which requirement wins when speed, cost, scope, quality, and compatibility conflict?
- What is must-have, should-have, could-have, and explicitly not planned?
- Which defaults has the user accepted, and which choices require a named decision maker?
- What may be simplified without defeating the objective?

## Readiness Audit

Before consolidating, classify every relevant section as:

- **Resolved** — explicit and testable;
- **Accepted default** — recommendation explicitly approved by the user;
- **Deferred safely** — non-blocking, with owner and resolution point;
- **Not applicable** — excluded for a stated reason; or
- **Blocking** — continue interviewing.

Any relevant section left unclassified is a gap. Any blocking item prevents final approval.
