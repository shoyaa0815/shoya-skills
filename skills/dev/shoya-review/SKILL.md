---
name: shoya-review
description: Audit an existing implementation through independent, risk-ranked, end-to-end code-flow analysis with reproducible evidence. Use for Shoya Review or an unbiased implementation review; not for explanation, design-only feedback, or fixing code.
---

# Shoya Review

Find consequential defects with high confidence and low noise.

## Setup

- Prefer a fresh subagent with no inherited turns. Give it only the request, target, and explicit requirements. Otherwise review directly from newly gathered repository evidence; never claim context was erased.
- Remain read-only unless the user separately authorizes fixes.
- For a change, establish the baseline and diff; follow unchanged code only when an affected flow reaches it. For a repository, derive entry points from docs, manifests, routing, and tests.
- Resolve ambiguity from repository evidence. Ask only if competing answers materially change the review.

## Review

1. Map affected flows and trust boundaries; rank them by harm and uncertainty.
2. Prioritize security, data integrity, contracts, permissions, concurrency, external side effects, and recovery.
3. Trace each important flow: input -> validation -> logic/state -> persistence/integration -> output/error. Where relevant, cover boundaries, denial, retries, partial failure, and concurrency.
4. Try to disprove every suspected defect against callers, callees, guards, types, schemas, configuration, migrations, and tests.
5. Use the smallest safe check that changes confidence: a targeted existing test or minimal reproduction. Avoid external writes and broad mutations.

Batch discovery and searches; read narrow regions and expand only across relevant boundaries. Spend depth by risk and stop after scoped high-risk flows are traced and more inspection is unlikely to change the result. Do not narrate exploration.

## Finding Gate

Report a defect only with:

- exact path and file/line evidence;
- realistic trigger and observable impact;
- proof that safeguards do not prevent it;
- verification performed or precisely still needed.

Exclude style, harmless cleanup, speculation, duplicate root causes, and test gaps without behavioral risk. Put material uncertainty under **Open questions**. Zero findings is valid.

Grade impact, not confidence:

- **Critical:** practical catastrophic compromise or widespread irreversible loss.
- **High:** security bypass, serious corruption/loss, or core-flow failure.
- **Medium:** meaningful wrong behavior with limited scope or workaround.
- **Low:** minor concrete defect; omit trivial polish unless requested.

## Output

List findings by severity, then likelihood. Use one compact block each:

`[Severity] Title — file:line`

State flow, trigger, impact, failed safeguard, and verification/remediation direction. Group locations sharing one root cause.

Then provide only:

- **Open questions** — material unresolved issues, if any.
- **Coverage** — flows, checks, and important limits.

If nothing survives the gate, say so directly. Passing tests never proves absence of defects.
