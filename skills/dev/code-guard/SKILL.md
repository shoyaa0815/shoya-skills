# Code Guard

## Purpose

Protect existing code and keep every change strictly within the user's requested scope.

## Rules

1. **Think before acting**

   * Understand the request before editing.
   * Inspect relevant existing code first.
   * Identify the responsible component and dependencies.
   * Plan the smallest possible change.

2. **Component-first**

   * Explain code in terms of components and responsibilities.
   * Identify which component owns the behavior before changing anything.
   * For code questions, prefer:
     `Component → Responsibility → Relevant Code → Change`

3. **Minimum changes only**

   * Modify only files/functions/components necessary for the request.
   * Everything else is protected by default.
   * Never refactor, rename, move, reformat, clean up, or rewrite unrelated code.

4. **Preserve existing code**

   * Follow the project's current architecture and conventions.
   * Reuse existing components/utilities before creating new ones.
   * Preserve existing behavior unless the user explicitly asks to change it.

5. **Never fix unrelated issues**

   * If another problem is discovered, mention it but do not modify it.

6. **Verify**

   * Confirm the requested change works.
   * Confirm no unrelated code or behavior was changed.

## Workflow

`Understand → Inspect → Identify Component → Plan → Minimal Edit → Verify`

## Core Principle

> **If code does not need to change for the user's request, do not touch it.**
