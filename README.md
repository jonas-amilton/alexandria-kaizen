# Alexandria Kaizen

Repository for the `alexandria-kaizen` skill: a production-support workflow for incident response, bugfixes, minimal patches, and reusable learning from resolved problems. The name combines Alexandria as a knowledge-library metaphor with Kaizen as the continuous-improvement loop used by the skill.

## What this skill does

Use it when you need to:

- investigate production incidents or regressions;
- find related files and candidate line numbers;
- propose useful breakpoint or logpoint locations when evidence needs them;
- design the smallest safe patch;
- preserve evidence, rollback path, and operational safety;
- record resolved-problem memory so future investigations start with prior knowledge.

## Repository layout

```text
skills/alexandria-kaizen/
├── SKILL.md
├── references/
│   ├── base-methodology.md
│   ├── incident-response.md
│   ├── minimal-patch.md
│   └── resolved-problem-memory.md
└── memory/
    ├── INDEX.md
    └── resolved-problems/
```

## Installation

Clone the repository once:

```bash
git clone https://github.com/jonas-amilton/alexandria-kaizen.git
cd alexandria-kaizen
```

### Claude Code

Claude Code discovers personal skills from `~/.claude/skills/<skill-name>/SKILL.md` and project skills from `.claude/skills/<skill-name>/SKILL.md`.

Personal install:

```bash
mkdir -p ~/.claude/skills
cp -R skills/alexandria-kaizen ~/.claude/skills/
```

Project-local install:

```bash
mkdir -p .claude/skills
cp -R skills/alexandria-kaizen .claude/skills/
```

Invoke directly in Claude Code with:

```text
/alexandria-kaizen
```

### OpenCode

OpenCode discovers skills from `.opencode/skills`, `~/.config/opencode/skills`, `.claude/skills`, `~/.claude/skills`, `.agents/skills`, and `~/.agents/skills`.

Project-local install:

```bash
mkdir -p .opencode/skills
cp -R skills/alexandria-kaizen .opencode/skills/
```

Global install:

```bash
mkdir -p ~/.config/opencode/skills
cp -R skills/alexandria-kaizen ~/.config/opencode/skills/
```

OpenCode loads available skills through its native skill tool. If the skill is not visible, verify that the folder name matches `name: alexandria-kaizen` and that `SKILL.md` is uppercase.

### Codex

Codex reads skills from repository and user `.agents/skills` locations. Use a repository install when the skill should travel with the project, or a user install when it should apply across repositories.

Repository install:

```bash
mkdir -p .agents/skills
cp -R skills/alexandria-kaizen .agents/skills/
```

User install:

```bash
mkdir -p ~/.agents/skills
cp -R skills/alexandria-kaizen ~/.agents/skills/
```

Invoke explicitly in Codex with:

```text
$alexandria-kaizen
```

Restart the tool if the skill does not appear after copying it.

## Invocation

Invoke the skill explicitly by name:

```text
Use $alexandria-kaizen to investigate this production bug with root cause, mitigation, minimal patch, and verification.
```

## Expected output

Troubleshooting output is adaptive and normally includes only `### Conclusion`, `### Evidence`, `### Change or next validation`, `### Tests`, with additional material only when it changes a decision. The full response contract, cost rules, and boilerplate mode live in `skills/alexandria-kaizen/SKILL.md`.

## Usage workflow

Six phases: frame the problem, recall prior knowledge, investigate with evidence, patch minimally, verify freshly, capture learning. Step-level rules live in `SKILL.md` (Workflow, Discovery) and in `references/` loaded on demand.

## Safety rules

- Non-negotiables and cost rules: `SKILL.md`.
- Ops rules (dry-run, batches, checkpoints, I/O timeout/retry, concurrency, no secrets/PII): `references/incident-response.md`.
- Memory and learning rules (no secrets, validated-only, TTL): `references/resolved-problem-memory.md`.

## Maintaining the skill

When changing the skill:

1. Keep `SKILL.md` concise; move detailed workflows into `references/`.
2. Keep references one level below `SKILL.md` and link them from the main file.
3. Search for accidental source-specific references before committing.
4. Use commit messages that describe the skill change without mentioning model families or vendor-specific model names.
