---
name: alexandria-kaizen
description: Use for maintenance, bugs, regressions, incidents, troubleshooting, support, and risky existing-system changes. Guides smallest-safe, verified fixes; not greenfield work, routine features, or generic refactors.
---

## Activate and prioritize

Use for existing-system maintenance, failures, regressions, support, risky reviews, and incidents. Not for greenfield work, routine features, or generic refactors.

Priority: contain production impact; establish cause; change the correct shared point; verify now; communicate only decision-relevant evidence.

## Non-negotiables

- Mark material statements as fact, hypothesis, or recommendation. Current source and tests decide; do not invent causes, APIs, or behavior.
- Inspect instructions, working-tree changes, errors, code, and tests. No lateral cleanup or dependencies when existing capabilities suffice.
- Preserve validation, security, accessibility, data protection, idempotency, and concurrency. Fix shared points; validate trust boundaries.
- Mitigate reversibly and observably. Destructive scripts need dry-run, batches, checkpoints/resume, idempotency, and validated backup/recovery.
- Use I/O timeouts when needed; retry only bounded, safe, idempotent, or deduplicated work. Protect concurrency with applicable transaction, constraint, lock, CAS, or deduplication.
- Use structured logs without secrets or unnecessary PII. Test/reproduce before and after non-trivial patches; read fresh output/status before claims. State applicable rollback and residual risk.
- Preserve exact evidence. Mark inferred `file:line` as estimated and give confirmation.
- After three failed fix attempts, stop and reassess the hypothesis or architecture.

## Discovery strategy

**Graphify-first for semantic relationships. Text-search-first for exact textual evidence. Current source and tests are the final authority.**

When Graphify or equivalent graph is available, verify capability, language/directory coverage, freshness versus current/uncommitted code, and verifiable symbols, paths, or locations when offered. Prefer it for definitions, references, callers/callees, dependencies, implementations, entrypoint-to-I/O paths, shared points, related tests, traversal, and impact.

Treat a graph result as a candidate until current code confirms it. Fall back to text search and direct reading when Graphify is unavailable, stale, incomplete, lacks relevant coverage, conflicts with the working tree, or returns generic or unverifiable results.

Use `rg`/`grep` first for literal errors, stack frames, logs, strings, environment variables, flags, config/payload fields, text-declared routes, SQL, migrations, seeds, templates, docs, runbooks, memory, generated files, uncovered areas, and confirmation. Start from one symbol, file, endpoint, or entrypoint and relation. Keep graph traversal shallow (normally one or two hops where supported); request metadata/paths/symbols before code, limit entities where supported, and read relevant ranges.

Use specific terms in likely directories; exclude `.git`, dependencies, builds, caches, and generated output; bound results and expand only if needed. Do not repeat a repository search or use Graphify, `rg`, and `grep` for one purpose without distinct justification. Retain only needed evidence.

## Workflow

1. Frame symptom, scope, impact, success signal, and unknowns. Ask only if ambiguity blocks safety.
2. Gather evidence, reproduce/observe, inspect changes/configuration, and trace input through validation, domain, I/O, and output. Test one hypothesis at a time.
3. Choose first sufficient rung: operation/config/documentation, existing pattern, stdlib, platform, installed dependency, small adjustment, then minimum new code. Compare callers and siblings before patching a shared rule.
4. Apply proportional safeguards from the non-negotiables. Use interactive breakpoints only when they resolve an ambiguity that tests, logs, metrics, or traces cannot. For concurrency, timing, or production-only behavior prefer conditional logpoints, metrics, tracing, concurrency tests, or controlled reproduction.
5. Run relevant reproduction/tests/checks. Record exact manual validation if needed. Propose learning only after validated, reusable resolution.

## References: load only when needed

Never load a reference merely because this skill activated. Do not reload a reference already read during the current task.

- `references/base-methodology.md`: methodological uncertainty, competing solutions, or need to explain the smallest-safe change.
- `references/incident-response.md`: real or potential effect on users, data, revenue, security, SLA/SLO, or critical operations.
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
