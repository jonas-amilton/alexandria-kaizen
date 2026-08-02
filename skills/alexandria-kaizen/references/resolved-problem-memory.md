# Resolved-Problem Memory

Load only when existing memory/runbooks may help, recurrence is plausible, or a validated resolution is ready to record. Search and record from this one reading; current code and tests still decide.

## Storage convention

Memory lives inside this skill directory, next to SKILL.md:

- `<skill-dir>/memory/INDEX.md` — table of all entries.
- `<skill-dir>/memory/resolved-problems/<slug>.md` — one file per resolution.

Relative to SKILL.md, so the convention holds in any install (global `~/.config/opencode/skills`, project `.opencode/skills`, `.claude/skills`, `.agents/skills`). If the skill directory is a repo checkout, commit entries there so they travel across machines.

## Consult

1. Read `memory/INDEX.md` first (one small read; no full-directory scan).
2. Search exact error, stack frame, endpoint, job, table, flag, component, and failing command in the INDEX and matching entries, plus tickets, runbooks, commits, and related tests. Start in known documentation locations; use specific, bounded text search rather than a broad repository scan.

Classify candidates:

- **Reused**: symptom, component, and cause match; revalidate against current code.
- **Similar**: supports a hypothesis, not proof.
- **Discarded**: evidence diverged; state why if material.

Never store secrets, tokens, sensitive payloads, unnecessary PII, or customer data.

## Record

Record only validated, reusable resolutions. An inconclusive investigation is a note, not resolved memory; a stopped investigation (e.g., three failed fix attempts with a reassessed hypothesis) is a note, not resolved memory. Keep entries searchable and concise. Add one line to `INDEX.md` (`slug | symptom | component | tags`) per entry.

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

Promote only learning that is reusable, safe, verified, and operationally actionable. After ~20 entries or 30 days, run a maintenance pass: merge duplicates and mark obsolete entries when contracts change; promote recurring lessons to a runbook, test, alert, or skill rule.
