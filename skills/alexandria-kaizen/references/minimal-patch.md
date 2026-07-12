# Minimal Patch, Files, and Debugging

Load only when a detailed patch plan, rollback, file map, breakpoint, or logpoint is needed.

## File map

```markdown
### Related files
- `path/to/entrypoint.ext:10`: flow entry; evidence.
- `path/to/shared-rule.ext:42`: candidate shared behavior; evidence.
- `path/to/io.ext:87`: relevant I/O; evidence.
- `path/to/test.ext:15`: existing or regression-test location.
```

Use repository-relative paths. Cite exact lines from local evidence. Mark inferred lines `estimated` and give confirmation method. Include an excluded file only when that reduces ambiguity.

## Debugging points

Suggest only points that validate a named unresolved hypothesis. Favor boundaries: input, validation, transformation, I/O, output. For interactive debugging, give path/line, condition, expression, and expected observation. For races, timing, or production-only behavior use conditional logpoints, metrics, traces, concurrency tests, or controlled reproduction; breakpoints can hide races.

## Patch plan

```markdown
### Minimal patch
Fact: `file:line` [observed behavior].
Hypothesis: [causal mechanism].
Change: `path`: [minimum shared-point change].
Safeguards: [only applicable timeout/retry/idempotency/concurrency/logging].
Test: `exact command` [fails before; passes after].
Rollback: [specific revert, flag, config, or data recovery].
Residual risk: [only if material].
```

For a boundary failure, validate or normalize before domain code. For a shared-rule failure, change that rule and cover reported path. For external I/O, add explicit timeout and only bounded retry backed by idempotency/deduplication. For data repair, default dry-run, process small batches with checkpoint/resume, verify reruns, and validate backup/recovery on sample.
