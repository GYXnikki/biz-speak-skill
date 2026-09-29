---
name: biz-speak
description: Rewrite AI task-completion output from technical/code language into business language. Use when the user wants to translate a technical summary into business-oriented expression, or invokes /biz-speak.
---

# biz-speak

Rewrite a task-completion summary from technical language into business language. The output should be understandable by non-technical stakeholders while preserving all actionable information.

## When to use

After an AI agent has completed a task (bug fix, new feature, refactor, etc.) and produced a technical summary. The user invokes `/biz-speak` to get a business-friendly version.

## Output structure

Every rewritten output must contain three elements:

1. **Business** — what this means in business terms (the rule, the requirement, the capability)
2. **Behavior** — how the system now behaves, from the user's perspective (no code references, no file names, no function names)
3. **Impact** — who is affected, what they need to do (if anything)

The exact headings can vary by task type, but these three elements must always be present.

## Task-type variations

### Bug fix

Structure: Rule → Behavior change → Impact scope

- **Rule**: what the business rule/logic is (or should be)
- **Behavior change**: what was wrong, what is correct now (user-perceptible)
- **Impact scope**: which users/data are affected, how to fix existing cases

### New feature

Structure: Capability → User actions → Entry point

- **Capability**: what the system can now do (business value)
- **User actions**: what users can do that they couldn't before
- **Entry point**: where in the product users access this

### Refactor

Structure: What changed → Behavior unchanged → Why

- **What changed**: what was restructured (in business terms, not code terms)
- **Behavior unchanged**: explicitly state that user-facing behavior is the same
- **Why**: the business reason for the change (maintainability, performance, etc.)

## Transformation rules

1. **Code references → business rules.** Replace function names, file paths, variable names with what they represent in business logic.
   - BAD: "Added `validate_email()` call in `services/auth.py` line 42"
   - GOOD: "User registration now validates email format"

2. **Implementation details → user-perceptible behavior.** Describe what the user sees or experiences, not how it's implemented.
   - BAD: "Added `refreshTailFlags()` at the end of `toggleMulti`"
   - GOOD: "After selecting an option, the button immediately updates to show the next question"

3. **Technical impact → business consequences.** Explain what the bug/feature means for the business, not just the code.
   - BAD: "Missing field causes null value in risk stratification calculation"
   - GOOD: "Affected users had incomplete risk assessment results; re-entering the form will recalculate correctly"

4. **Test results → verification path.** Instead of "all tests pass", tell the user how to verify the fix works.
   - BAD: "423 tests passed"
   - GOOD: "To verify: open user 97's profile, the form should now show question 34/34, and they can fill in the missing answers"

## Anti-patterns

- **Over-sanitization**: removing all technical detail so developers can't act on the output. The goal is to add business context, not replace technical information entirely. If the audience needs both, provide both.
- **Vague business language**: "improved the user experience" says nothing. Be specific about what changed and how.
- **Losing the action**: the output must always tell the reader what to do next (if anything). "The bug is fixed" is incomplete — "The bug is fixed; affected users need to re-enter the form" is complete.

## Examples

See the `examples/` directory for complete before/after examples:

- [Bug fix](examples/bug-fix.md)
- [New feature](examples/new-feature.md)
- [Refactor](examples/refactor.md)

## Language

Output in the same language the user is using. If the conversation is in Chinese, output in Chinese. If in English, output in English.
