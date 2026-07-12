# Resolved-Problem Memory

Load only when existing memory/runbooks may help, recurrence is plausible, or a validated resolution is ready to record. Search and record from this one reading; current code and tests still decide.

## Consult

Search exact error, stack frame, endpoint, job, table, flag, component, and failing command in existing memory, tickets, runbooks, commits, and related tests. Start in known documentation locations; use specific, bounded text search rather than a broad repository scan.

Classify candidates:

- **Reused**: symptom, component, and cause match; revalidate against current code.
- **Similar**: supports a hypothesis, not proof.
- **Discarded**: evidence diverged; state why if material.

Use existing knowledge/runbook storage. If none exists, propose `.sustaining/memory/resolved-problems/<slug>.md`; otherwise provide markdown for the existing team system. Never store secrets, tokens, sensitive payloads, unnecessary PII, or customer data.

## Record

Record only validated, reusable resolutions. An inconclusive investigation is a note, not resolved memory. Keep entries searchable and concise:

```markdown
# <short problem slug>

- Date/component/status/severity: [values]
- Symptoms and impact: [exact redacted evidence]
- Validated cause: Fact: [evidence]. Mechanism: [cause]. Validation: [test/log/metric/reproduction].
- Minimal patch: [files, shared-point strategy, why safe].
- Verification: `exact command` - expected/observed result.
- Rollback and residual risk: [revert/recovery, recurrence signal].
- Learning: [reusable rule, minimum evidence, destination: memory | skill | runbook | test | alert | discard].
- Tags: `#component` `#error` `#cause` `#patch-type`
```

Promote only learning that is reusable, safe, verified, and operationally actionable. Periodically merge duplicates, mark obsolete entries when contracts change, and promote recurring lessons to a runbook, test, alert, or skill rule.
