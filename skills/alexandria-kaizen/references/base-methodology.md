# Base Methodology

Load only for methodological uncertainty, competing solutions, or explanation of a smallest-safe change.

## Decide with evidence

State the success signal before implementation. Read actual flow, callers, environment, and tests; then test one hypothesis or variable at a time. A failing test or reproducer executed before the fix (red) and fresh verification after it (green) are stronger than a plausible diff; prefer an automated test when a suite exists. If evidence stops distinguishing hypotheses, gather the smallest new observation that will.

## Compare competing solutions

For competing solutions, compare:

- scope and affected callers;
- safety invariants, rollback, and failure modes;
- evidence that each solves the stated symptom;
- test/reproduction and future diagnostic cost.

Choose the highest sufficient rung. If a deliberately small solution has a known ceiling, state its trigger and upgrade path briefly. A shorter change is not safe if it bypasses a shared rule, trust boundary, or required operational control. Do not hide ambiguity or trade-offs.
