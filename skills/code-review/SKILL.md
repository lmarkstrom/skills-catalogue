---
name: code-review
description: >-
  Governs how the agent reviews code. Use this skill when asked to review a
  diff, pull request, file, or function — covering what to flag, what to ignore,
  how to prioritise findings, and how to phrase feedback.
---

# Code Review

## Mindset

Review as a collaborative peer, not a gatekeeper. The goal is to improve the
code, not to demonstrate thoroughness. Flag what matters; skip what doesn't.

---

## Priority Tiers

Order findings by impact. Address higher tiers before lower ones.

| Tier | Label | What it covers |
|---|---|---|
| 1 | Must fix | Bugs, security issues, data loss risk, broken logic |
| 2 | Should fix | Performance problems, missing error handling, unclear naming |
| 3 | Suggestion | Style, readability, minor improvements — take or leave |

Always state the tier at the start of each comment.

---

## What to Focus On

- **Correctness** — does it do what it's supposed to do in all cases (including
  edge cases and error paths)?
- **Error handling** — are failures caught and surfaced clearly?
- **Naming** — are functions, variables, and modules named clearly enough that
  a reader doesn't need to trace the logic to understand intent?
- **Complexity** — is there a simpler way to express this? Flag functions that
  are doing too much.
- **Tests** — are the tests actually testing the right things? Are edge cases
  covered?

---

## What to Ignore

- Formatting and whitespace that a linter/formatter would catch automatically.
- Style choices that are valid alternatives (e.g. `x if cond else y` vs a
  short `if` block) unless they hurt readability.
- Rewrites that change the approach but don't improve correctness, clarity,
  or performance.

---

## How to Phrase Feedback

- Be **specific** — quote the exact line or block, then explain the problem and
  suggest a fix.
- Use questions for suggestions, statements for must-fixes:
  - Suggestion: "Could this be simplified with `itertools.chain`?"
  - Must fix: "This will raise `KeyError` if `user` is not in the dict."
- Never say "just" or "simply" — it's condescending when the fix isn't obvious.
- Keep each comment self-contained — don't assume the reader remembers a
  previous comment.

---

## Output Format

Present findings as a structured list grouped by tier, then file:

```
## Must Fix

**`auth/token.py:42`** — `secret` is logged at INFO level and will appear in
plaintext in production logs. Remove the log line or redact the value.

## Should Fix

**`utils/parser.py:18`** — No handling for an empty input string; `split()`
will return `['']` rather than `[]`, which breaks the caller.

## Suggestions

**`models/user.py:67`** — `get_full_name` could be a `@property` to match the
style of the other computed attributes on this class.
```

If there is nothing to flag in a tier, omit that section entirely.

---

## Summary Line

End every review with a one-sentence overall verdict, e.g.:

> Looks solid overall — one security fix needed before merging, the rest are minor.
