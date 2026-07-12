# Base Methodology

Load only for methodology uncertainty, competing solutions, or explanation of a smallest-safe change.

## Decide with evidence

State the success signal before implementation. Read actual flow, callers, environment, and tests; then test one hypothesis or variable at a time. A failing reproduction before a bug fix and fresh verification after it are stronger than a plausible diff. If evidence stops distinguishing hypotheses, gather the smallest new observation that will.

## Choose the smallest safe solution

Prefer, in order: operation/configuration/documentation; existing code or runbook; stdlib; platform/database capability; installed dependency; small adjustment; minimum new code. A shorter change is not safe if it bypasses a shared rule, trust boundary, or required operational control.

For competing solutions, compare:

- scope and affected callers;
- safety invariants, rollback, and failure modes;
- evidence that each solves the stated symptom;
- test/reproduction and future diagnostic cost.

Choose the highest sufficient rung. If a deliberately small solution has a known ceiling, state its trigger and upgrade path briefly.

## Keep scope and communication surgical

Trace every changed line to the request. Preserve existing style; remove only debris introduced by the change. Do not hide ambiguity or trade-offs. Keep commands, errors, paths, numbers, payload fields, test outcome, and applicable risk exact; remove explanation that does not alter a decision.
