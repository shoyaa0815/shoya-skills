---
name: shoya-debug
description: Evidence-first diagnosis of software failures through reproduction, end-to-end tracing, falsifiable hypotheses, and root-cause proof. Use when tests, builds, runtime behavior, performance, or integrations fail unexpectedly; implement a fix only when the user also asks for one.
---

# Shoya Debug

Reproduce the failure, locate the first incorrect transition, and prove the causal mechanism before proposing or applying a fix.

## Operating Stance

- **Evidence before explanation.** Logs, traces, tests, state, and code paths outrank intuition and error-message wording.
- **One hypothesis, one discriminating experiment.** Every experiment states why it is being run and what result would support or weaken the hypothesis.
- **Root cause, not symptom relief.** Distinguish the trigger, causal defect, contributing conditions, and visible symptom.
- **Diagnosis does not imply mutation.** Keep investigation read-only unless the user explicitly asks to fix the problem. Temporary local instrumentation is an implementation change and requires the same authorization.

## Workflow

Run these stages in order. Return to an earlier stage when new evidence invalidates its conclusions.

### 1. Frame — what exactly is failing?

- State expected behavior and observed behavior separately.
- Capture the triggering input or action, exact failure output, affected environment, frequency, impact, and last-known-good state when available.
- Inspect repository instructions, current worktree state, relevant configuration, tests, and recent changes before asking the user for facts the workspace can answer.
- Separate confirmed facts from reports and assumptions. If essential user-only context is missing, ask the smallest question that can change the investigation path.

Do not silently redefine the bug around whatever is easiest to reproduce.

### 2. Reproduce — make the failure observable

- Reproduce with the smallest realistic path that still exhibits the reported behavior.
- Record the exact command, input, environment, and output. Establish whether the failure is deterministic, intermittent, environment-specific, or not reproduced.
- Compare against a control when useful: a passing input, prior revision, alternate environment, or direct call below a suspected layer.
- Preserve the original evidence before changing code, configuration, dependencies, caches, or state.

If reproduction would be destructive, affect production, contact external parties, or mutate data outside the authorized scope, do not run it. Use safe evidence or request authorization for the exact action.

### 3. Trace — find the first wrong transition

- Follow the real path from trigger to symptom: entry point → validation → branches → state or data access → integrations → side effects → output or failure.
- Include unchanged callers, callees, configuration, schemas, and boundaries around the suspicious code. A stack trace is a lead, not the whole execution path.
- Identify the last state known to be correct and the first state known to be incorrect.
- Mark surprising branches, implicit conversions, stale state, retries, ordering, concurrency, and swallowed or transformed errors. Surprises are candidate evidence, not conclusions.

### 4. Falsify — test competing explanations

Maintain a compact hypothesis ledger. For each candidate state:

- the proposed causal mechanism;
- evidence that would support it;
- evidence that would falsify it;
- the cheapest safe experiment that distinguishes it from alternatives;
- its status: `untested`, `supported`, `weakened`, or `rejected`.

Rank hypotheses by fit with the evidence, not familiarity. Change one meaningful variable at a time. Do not repeat a failed experiment without new evidence, and do not bundle speculative fixes as a diagnostic test.

### 5. Prove — establish the root cause

Call a root cause confirmed only when the evidence explains:

- the trigger and required conditions;
- the exact mechanism from correct state to incorrect state;
- why the observed symptom follows;
- why important passing or non-affected cases remain unaffected;
- which plausible alternatives were ruled out.

When a controlled test is feasible, show that introducing the causal condition produces the failure and removing it removes the failure. If the evidence cannot meet this gate, report the cause as probable or unresolved instead of upgrading confidence through repetition.

### 6. Repair — fix only when authorized

If the user requested diagnosis only, stop after the evidence-backed diagnosis and remediation direction.

Enter repair only when the root cause passes the confirmation gate above. A request to fix the problem does not lower that evidence threshold. If the cause remains probable or unresolved, do not mutate the implementation; report `needs more evidence` and name the next discriminating evidence required.

If the user also requested a fix and the root cause is confirmed:

- change the smallest causal surface rather than suppressing the symptom;
- add a regression test that exercises the reproduced path and fails without the fix when feasible;
- verify the original reproduction, relevant neighboring behavior, and error paths;
- remove temporary instrumentation and speculative changes that are not part of the repair;
- inspect the final diff to ensure the repair did not absorb unrelated cleanup.

A passing test is insufficient when it bypasses the failing path, mocks away the causal boundary, or asserts only an intermediate state.

### 7. Report

Lead with one of: `root cause confirmed`, `probable cause`, `unresolved`, or `fixed and verified`.

For each confirmed or probable cause, provide one tight section:

- **Cause** — the defect and causal mechanism in one sentence.
- **Evidence** — reproduction and traced code or state, with file and line references when applicable.
- **Ruled out** — the closest competing explanations and the evidence against them.
- **Remediation** — the smallest appropriate correction; state whether it was applied.
- **Verification** — the commands or checks performed, why each mattered, and its result.

Close with a one-line verdict: `fix verified`, `ready to fix`, `needs more evidence`, or `blocked`, followed by the single most important reason. Name coverage limits and preserve uncertainty; do not pad the report with a debugging diary.

## Operating Rules

- **No shotgun debugging.** Do not make several unrelated changes and infer causality from a later pass.
- **No error-message literalism.** Verify where an error originates and how it reaches the user before treating its wording as the cause.
- **No retry-as-proof.** A transient pass does not disprove a race, timing, cache, or environment failure.
- **No hidden baseline failures.** Distinguish failures introduced by the target change from pre-existing or unrelated failures.
- **No scope laundering.** A bug investigation does not authorize refactors, dependency upgrades, data repair, production actions, or external mutations.
- **No forced certainty.** If available evidence supports multiple causes, say what would distinguish them and stop when the remaining evidence is inaccessible or unsafe to obtain.
