---
name: biz-speak
description: Rewrite AI-produced technical output — completed work or an implementation plan — into business language. Use when the user invokes /biz-speak, or asks to restate a technical summary, plan, or code-change notes in terms that business stakeholders, product, or customers can follow.
---

# biz-speak

## When to use

After an AI agent has produced technical output that a business audience needs to understand — either a completed task (bug fix, new feature, refactor, etc.) or an implementation plan that has not been executed yet. The user invokes `/biz-speak` to get a business-friendly version.

## Output structure

Every rewritten output must answer three questions:

1. What is this in business terms?
2. What can users perceive as different?
3. Who is affected, and what do they need to do?

Headings vary by task type (see below). All three questions must be answered — including when the answer is "nothing changes for users".

Code-level references never appear in the output; business identifiers such as user IDs, order numbers, or question numbers do, because they are how a business reader locates the case.

## Task-type variations

The three types below apply to both finished work and plans that have not shipped yet. For a plan, describe what will change once it ships rather than what already happens.

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
- **Why**: the business reason for the change (maintainability, performance, etc.). State plainly whether users have to do anything — for most refactors the answer is no.

## Transformation rules

1. **Code references → business rules.** Replace function names, file paths, variable names with what they represent in business logic. Keep business identifiers (user IDs, order numbers, question numbers) — they are how a reader locates the case.
   - BAD: "Added `validate_email()` call in `services/auth.py` line 42"
   - GOOD: "User registration now validates email format"

2. **Implementation details → user-perceptible behavior.** Describe what the user sees or experiences, not how it's implemented. If nothing changes for users, say so — do not invent a visible effect.
   - BAD: "Added `refreshTailFlags()` at the end of `toggleMulti`"
   - GOOD: "After selecting an option, the button immediately updates to show the next question"

3. **Technical impact → business consequences.** Explain what the bug/feature means for the business, not just the code. Do not add numbers, affected-user counts, or timing that the source does not state; mark anything you infer as inference.
   - BAD: "Missing field causes null value in risk stratification calculation"
   - GOOD: "Affected users had incomplete risk assessment results; re-entering the form will recalculate correctly"

4. **Test results → verification path.** Instead of "all tests pass", tell the user how to verify the fix works. The verification path must come from the source — if it only reports test counts, say what area was covered rather than inventing a concrete case.
   - BAD: "423 tests passed"
   - GOOD: "To verify: open user 97's profile, the form should now show question 34/34, and they can fill in the missing answers"

Concrete values are content, not noise. Thresholds, limits, ranges, timeouts, counts, and what happens at the boundary must appear as stated — "over 30 days" must not become "after a while", and "files above 5 MB are rejected" must not become "large files are rejected".

## Anti-patterns

- **Over-sanitization**: removing all technical detail so developers can't act on the output. The goal is to add business context, not replace technical information entirely. If the audience needs both, provide both.
- **Vague business language**: "improved the user experience" says nothing. Be specific about what changed and how.
- **Losing the action**: the output must always tell the reader what to do next (if anything). "The bug is fixed" is incomplete — "The bug is fixed; affected users need to re-enter the form" is complete.

## Examples

Before rewriting, read the example that matches the task type:

- bug fix → `examples/bug-fix.md`
- new feature → `examples/new-feature.md`
- refactor → `examples/refactor.md`

If the source is a plan that has not shipped yet, also read `examples/plan.md`.

## Language

Output in the same language the user is using. If the conversation is in Chinese, output in Chinese. If in English, output in English.
