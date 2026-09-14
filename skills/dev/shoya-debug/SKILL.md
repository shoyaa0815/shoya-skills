---
name: shoya-debug
description: Diagnose unexpected software failures with the smallest decisive evidence loop, then fix the proven cause when authorized. Use for failing tests or builds, runtime bugs, regressions, flaky behavior, performance issues, and broken integrations; not for ordinary implementation or speculative cleanup.
---

# Shoya Debug

Find the first wrong transition, explain its mechanism, and—when requested—repair the causal surface. Optimize for decisive evidence, not investigative volume.

## Contract

- Separate observed facts, inferences, and unknowns; prefer `unresolved` to invented certainty.
- Diagnosis-only stays read-only. A fix request authorizes normal local implementation and verification, not production actions, data repair, upgrades, or unrelated refactors.
- Preserve user changes. Inspect repository instructions and worktree state before editing.

## Minimal Evidence Loop

Repeat only while the next observation can change the conclusion:

1. **Frame:** State expected behavior, observed behavior, and the smallest known trigger. Ask only for user-held context that would change the path.
2. **Observe:** Run the narrowest realistic reproduction, or use preserved evidence when reproduction is unsafe. Record the exact command/input and meaningful output, not entire logs.
3. **Trace:** Follow the executed slice around the failure across code, config, data, and boundaries. Locate the last correct state and first incorrect state. Error text and stack frames are leads, not proof.
4. **Discriminate:** Test the leading mechanism with the cheapest safe check that could falsify it. Change one variable; use a passing control when useful.
5. **Conclude:** Label the cause `confirmed`, `probable`, or `unresolved`. If uncertain, name the single highest-value missing observation.

A compiler-localized typo may need one trace and verification. Expand investigation for flaky, concurrent, environment-specific, performance, distributed, security-sensitive, or destructive failures.

## Evidence Rules

A confirmed cause connects trigger → defect → first wrong state → symptom, and an appropriate control or repair removes that path. `Probable` means the mechanism fits available evidence but the decisive observation is unavailable.

Use evidence already present before creating more: inspect the failure and nearby code before broad searches; read only relevant callers, callees, config, schema, and history; compare passing and failing cases at their earliest divergence; distinguish baseline failures from target failures.

Keep a hypothesis ledger only when multiple explanations remain credible or the failure is flaky: `mechanism | discriminating check | result | status`. Drop rejected candidates. Never shotgun-edit, bundle speculative fixes, treat a passing retry as proof, or repeat an unchanged experiment without new reason.

Preserve original evidence before changing code, state, caches, or dependencies. If reproduction would affect production, external data or people, or exceed authorization, stop at that boundary and request the exact permission or artifact needed.

## Repair When Requested

Change the smallest causal surface and verify the original failing path. Add or tighten a regression test when it provides durable coverage; check neighboring behavior and error paths in proportion to risk, not by reflexively running everything.

A small reversible fix may serve as the controlled experiment. If it does not validate the mechanism, revert only that speculative change and resume diagnosis. Remove instrumentation and inspect the final diff.

Do not claim success from a test that bypasses or mocks away the failing boundary. State exactly what remains unverified and why.

## Compact Report

Lead with `fixed and verified`, `root cause confirmed`, `probable cause`, or `unresolved`, then include only:

- **Cause:** one-sentence mechanism or leading unknown.
- **Evidence:** decisive reproduction, trace, and control; cite files/lines when useful.
- **Action:** applied change or smallest recommendation.
- **Verification:** checks, results, and nearest material limit.

Mention alternatives only if genuinely competitive. Do not narrate the debugging diary or repeat raw output.
