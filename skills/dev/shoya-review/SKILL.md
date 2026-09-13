---
name: shoya-review
description: Perform an evidence-isolated, flow-to-flow review of an existing implementation, using a fresh subagent when available and a repository-first blind review fallback otherwise. Use when the user asks for a Shoya Review or wants an unbiased review that reconstructs the project from source evidence; do not use for ordinary code explanation or implementation work.
---

# Shoya Review

Review the implementation from the perspective of a competent engineer encountering the project for the first time.

## Independent Reviewer

- Prefer delegating the review to a newly spawned subagent with no inherited conversation turns.
- Give a delegated reviewer only the user's review request, the repository or target path, and any explicit scope or acceptance criteria supplied by the user. Do not include prior conclusions, suspected bugs, implementation rationale, or hints that could bias the review.
- If fresh-agent delegation is unavailable, continue immediately in repository-first blind review mode. Do not refuse the review or ask the user to open another session.
- In blind review mode, treat only the user's review request, explicit scope or acceptance criteria, and evidence independently rediscovered from the repository as admissible. Set aside prior conclusions, suspected bugs, implementation rationale, remembered file summaries, and earlier claims about how the code works.
- Whether delegated or direct, start discovery from the repository itself. Read the relevant documentation and code again, identify entry points, and build a new evidence trail before judging the implementation. Do not use conversation memory as a substitute for repository evidence.
- Keep the review read-only. Do not edit or fix code unless the user separately asks for implementation after receiving the findings.
- Do not claim that a direct blind review erased the model's context. Its independence comes from restricting conclusions to a newly reconstructed repository evidence trail.

## Review Flow to Flow

Trace each relevant behavior end to end rather than reviewing isolated files. Follow the actual path through entry points, validation, business logic, state or data access, integrations, side effects, output, and failure handling.

For every flow in scope:

1. Establish the intended behavior from repository evidence and the user's explicit requirements.
2. Trace the happy path across component and file boundaries.
3. Trace important alternate, boundary, permission, and failure paths.
4. Check whether data, state transitions, side effects, errors, and user-visible results remain consistent throughout the flow.
5. Run focused, safe verification when it can confirm or disprove a suspected problem.

Prioritize correctness bugs, security issues, data loss or corruption, broken contracts, race conditions, missing failure handling, and meaningful requirement gaps. Mention maintainability or test gaps only when they create a concrete risk. Ignore purely stylistic preferences unless the user requests them.

## Evidence Standard

- Report only findings supported by a reproducible path through the code or strong repository evidence.
- Verify assumptions against callers, callees, configuration, schemas, and tests before presenting them as facts.
- Do not invent findings, inflate severity, or force a minimum number of issues. An honest result may contain no findings.
- Distinguish confirmed defects from unresolved questions. Do not present speculation as a defect.
- Account for existing safeguards and tests; do not report an issue that the implementation already prevents.

## Deliverable

Return the review findings ordered by impact. Each finding must include:

- severity;
- affected flow;
- exact file and line evidence;
- what triggers the problem;
- observable impact;
- concise remediation direction;
- verification performed or still needed.

After the findings, summarize the flows reviewed, validation performed, and any important coverage limits. If no actionable defect is found, say so directly and still state what was reviewed and what could not be verified.
