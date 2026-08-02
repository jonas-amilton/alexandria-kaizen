# Production Incidents

Load only for real or potential effect on users, data, revenue, security, SLA/SLO, or critical operations. Single source of ops rules (destructive scripts, I/O, concurrency, logging); not restated in SKILL.md or minimal-patch.md.

1. Classify impact: unavailable/incorrect behavior, affected users/tenants/regions/jobs, and data, billing, leakage, or regulatory risk.
2. Contain with smallest reversible, observable action: rollback, flag disable, pause, rate limit, temporary block, failover, or read-only mode. Do not run destructive work without dry-run, backup, batching/checkpoints, and idempotency criteria.
3. Preserve UTC window, request/trace IDs, deploy or commit, relevant config, queue state, sampled redacted payloads, metrics, commands, queries, and evidence limits.
4. Diagnose boundaries: client, gateway, API, service, database/cache/queue, external dependency. At each, check input/output, latency, errors, timeouts, retries, and volume.
5. Make one primary root-cause fix, then add the smallest suitable regression test or operational detector. For external I/O, use timeout, bounded safe retry, fallback, and alert only when evidence requires them.
6. Prevent recurrence with an owned, actionable test, constraint, validation, metric, alert, dashboard, runbook, or process change. Alerts require an owner, threshold, and expected action.

Use this update only when stakeholders need it:

```markdown
Status: investigating | mitigated | fixed | monitoring
Impact: [who/what/since when]
Evidence: [logs, metrics, traces, commits]
Mitigation: [reversible action taken]
Next step: [action + owner + time]
Residual risk: [what can still fail]
```

Operational scripts: rerunnable without duplicate effect; dry-run real-data writes; batches plus checkpoint/resume; I/O timeout and bounded safe retry; counters for read/changed/skipped/failed; no secrets or unnecessary PII in logs.
