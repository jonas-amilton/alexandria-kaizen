---
name: alexandria-kaizen
description: Use for maintenance, bugs, regressions, incidents, troubleshooting, support, and risky existing-system changes. Guides smallest-safe, verified fixes; not greenfield work, routine features, or generic refactors.
---

## Non-negotiables

- Mark material statements as fact, hypothesis, or recommendation. Current source and tests decide; never invent causes, APIs, or behavior.
- Inspect instructions, working-tree changes, errors, code, and tests. No lateral cleanup or new dependencies when existing capabilities suffice.
- Preserve validation, security, accessibility, data protection, idempotency, and concurrency. Fix shared points; validate trust boundaries.
- Mitigate reversibly and observably. Ops rules (dry-run, batches, checkpoints, idempotency, I/O timeout/retry, concurrency, no-secrets): incident-response.md.
- Test/reproduce before and after non-trivial patches; read fresh output/status before claims. Preserve exact evidence; mark inferred `file:line` as estimated with confirmation method. State rollback and residual risk.
- After three failed fix attempts, stop and reassess the hypothesis or architecture.

## Discovery

Graph-first for semantic relationships; text-first for literal evidence. Current source and tests are the final authority.

- Verify graph freshness, coverage, and verifiable symbols vs current/uncommitted code before trusting it. Prefer it for definitions, references, callers/callees, dependencies, entrypoint-to-I/O paths, shared points, tests, and impact.
- Treat a graph result as a candidate until current code confirms it. Fall back to text search and direct reading when stale, incomplete, conflicting, generic, or unverifiable.
- `rg`/`grep` first for literal errors, stack frames, logs, strings, env vars, flags, config/payload fields, text-declared routes, SQL, migrations, docs, runbooks, memory, generated files.
- Regressions: start with `git log -S`/`git diff`/`git blame` of the affected area before broad searching.
- Start from one symbol, file, endpoint, or entrypoint. Keep traversal shallow (normally ≤2 hops); request paths/metadata/symbols before code; read relevant ranges only.
- Exclude `.git`, deps, builds, caches, generated output. Bound results. Never repeat a search or use two tools for one purpose without distinct justification.
- Large repo or deep exploration: delegate to an explore subagent; keep only its findings in context.

## Workflow

1. Frame symptom, scope, impact, success signal, and unknowns. Ask only if ambiguity blocks safety.
2. Gather evidence, reproduce/observe, inspect changes/configuration, and trace input through validation, domain, I/O, and output. Test one hypothesis at a time.
3. Choose first sufficient rung: operation/config/documentation, existing pattern, stdlib, platform, installed dependency, small adjustment, then minimum new code. Compare callers and siblings before patching a shared rule. Trace every changed line to the request; preserve existing style.
4. Apply proportional safeguards. Prefer conditional logpoints, metrics, tracing, concurrency tests, or controlled reproduction over interactive breakpoints.
5. Run relevant reproduction/tests/checks. Record exact manual validation if needed. Propose learning only after validated, reusable resolution.

## References: load only when needed

Never load a reference merely because this skill activated. Do not reload a reference already read during the current task.

- `references/base-methodology.md`: methodological uncertainty, competing solutions, or need to explain the smallest-safe change.
- `references/incident-response.md`: real or potential effect on users, data, revenue, security, SLA/SLO, or critical operations. Also the single source of ops rules.
- `references/minimal-patch.md`: detailed patch plan, rollback, file map, breakpoint, or logpoint is needed.
- `references/resolved-problem-memory.md`: existing memory/runbook, suspected recurrence, or validated resolution ready to record. Consult it once; do not load it again for recording in the same investigation.

## Response

Use only sections needed for the decision, normally:

```markdown
### Conclusion
### Evidence
### Change or next validation
### Tests
```

Add context, impact, facts, hypotheses, related files, debugging points, mitigation, rollback, residual risk, memory, or observability only when material. Never emit empty/repeated sections or make a simple bug an incident report. Evidence precedes cause or fix claims.

Cost rules:
- Never echo the question, tool output, or code already in context; quote only decision-relevant lines.
- Keep responses normally ≤15 lines; more only when material.
- Keep at most the 3 strongest evidence items.
- Stop investigating when evidence is conclusive; no repeat searches or re-reads.
