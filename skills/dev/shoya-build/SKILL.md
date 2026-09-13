---
name: shoya-build
description: Implement an approved specification or a sufficiently explicit coding change with requirement-to-code traceability and verification evidence. Use when the user has authorized implementation; do not use for specification interviews, diagnosis-only requests, or read-only reviews.
---

# Shoya Build

Turn an authorized change into a verified implementation without losing the intent behind it. Maintain a lightweight chain from each acceptance criterion to the code changed and the evidence that demonstrates the resulting behavior.

## Establish the Build Contract

Before editing, inspect the repository instructions, current worktree state, relevant entry points, tests, and the specification or task artifacts supplied by the user. Do not ask the user for facts that the repository can answer.

Treat any of these as a valid build contract:

- a consolidated specification the user approved;
- explicit acceptance criteria or an existing task artifact the user asked to implement;
- a direct implementation request precise enough to determine observable success without choosing product behavior on the user's behalf.

Extract the objective, in-scope and out-of-scope behavior, constraints, acceptance criteria, and required verification. Assign short criterion identifiers internally when the source does not provide them. Do not create a planning or ledger file in the repository unless the user or repository instructions require one.

If a missing decision would materially alter user-visible behavior, a public interface, persisted data, security, cost, or destructive side effects, stop and ask the smallest question needed to resolve it. For ordinary reversible implementation details that do not change the contract, choose the option most consistent with repository evidence and report the assumption in the handoff.

## Build in Verifiable Slices

Organize the work into the smallest cohesive slices that each deliver observable behavior. For every slice:

1. Trace the affected flow through its actual entry point, validation, business logic, state or data access, side effects, output, and failure handling as relevant.
2. Identify which acceptance criteria the slice advances and how they will be verified.
3. Make the smallest complete change that preserves existing conventions and unrelated user work.
4. Add or update tests at the behavior boundary most capable of catching a regression. Do not change tests merely to bless incorrect output.
5. Run focused verification before moving on. Broaden verification when shared code, contracts, schemas, configuration, or cross-cutting behavior changed.
6. Record the code locations and verification evidence for the affected criteria.

Prefer vertical behavior over batches such as “all models, then all handlers, then all tests” when a vertical slice can expose integration errors earlier. Keep the traceability ledger in working memory unless persistence is required for a long-running or multi-session task.

## Control Drift

Implementation discoveries may refine mechanics but must not silently rewrite the contract.

- If repository evidence only changes how the requirement should be implemented, adapt and continue.
- If the requested behavior already exists, verify it and avoid needless code churn.
- If the repository contradicts the specification, determine whether the conflict is a stale factual assumption or an unresolved intent decision. Correct the former when acceptance behavior remains unchanged; ask about the latter.
- If one criterion cannot be completed, continue independent criteria when doing so is safe, then report the exact blocker. Do not represent partial completion as complete.
- If verification exposes an unrelated pre-existing failure, preserve its evidence and distinguish it from regressions introduced by the change. Do not expand scope to fix it without authorization unless it directly prevents the requested implementation.

Never weaken an acceptance criterion, suppress an error, remove a safeguard, or skip a required check merely to obtain a passing result.

## Completion Gate

Call the build complete only when:

- every in-scope acceptance criterion is implemented, no in-scope criterion remains blocked, and anything determined to be out of scope is explicitly identified;
- each implemented criterion maps to concrete changed code and behavioral evidence;
- relevant tests, static checks, builds, or manual checks have run successfully in proportion to the change;
- affected error, boundary, permission, and state-transition paths have been considered;
- required documentation, configuration, migrations, or compatibility handling are included;
- the final diff contains no known unrelated edits introduced by the build.

Passing tests alone is not proof that the requested behavior is complete. Inspect the final diff and re-read the build contract before handing off.

If any in-scope criterion remains blocked, report the build as partial or blocked even when every other criterion passes verification.

## Handoff

Lead with the implemented outcome. Then provide a compact traceability summary containing:

- each acceptance criterion and its status;
- the main code or test evidence for it;
- verification commands or checks performed and their results;
- approved or non-material assumptions and any deviations;
- blockers, unverified areas, or remaining risks.

Use clickable file and line references when supported. Keep internal implementation narration out of the handoff unless it helps the user evaluate a consequential tradeoff. If the user asks for an independent review after the build, hand the completed implementation to the applicable review workflow without biasing the reviewer with suspected findings.
