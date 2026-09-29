# biz-speak-skill

An AI agent skill that rewrites task-completion output from technical/code language into business language.

## What it does

When an AI agent finishes a task, it often reports in technical terms: file names, function names, implementation details. This skill rewrites that output into business language that non-technical stakeholders can understand.

**Before** (technical):
> Added `validate_email()` in `services/auth.py` line 42. Updated 3 test cases in `test_auth.py`.

**After** (business):
> User registration now validates email format. Related tests have been updated.

## Installation

### Cursor

Copy `SKILL.md` to `.cursor/skills/biz-speak/SKILL.md` in your project.

### Qoder

Copy `SKILL.md` to your project's skills directory, or install via the Qoder skill marketplace (coming soon).

### Claude

Copy `SKILL.md` to `.claude/skills/biz-speak/SKILL.md` in your project.

### Other platforms

The skill is a plain Markdown file. Adapt it to your platform's skill/instruction format.

## Usage

After an AI agent completes a task and produces technical output, invoke:

```
/biz-speak
```

The agent will rewrite the output in business language.

## Output structure

Every rewritten output contains three elements:

1. **Business** — what this means in business terms
2. **Behavior** — how the system now behaves (user perspective)
3. **Impact** — who is affected, what to do next

The structure adapts to task type:

| Task type | Structure |
|---|---|
| Bug fix | Rule → Behavior change → Impact scope |
| New feature | Capability → User actions → Entry point |
| Refactor | What changed → Behavior unchanged → Why |

## Examples

See the [`examples/`](examples/) directory:

- [Bug fix](examples/bug-fix.md) — conditional logic bug in a questionnaire
- [New feature](examples/new-feature.md) — Excel export for reports
- [Refactor](examples/refactor.md) — extracting risk stratification module

## License

MIT
