---
name: docs-style
description: Apply a documentation style standard when writing, editing, or reviewing developer documentation in Markdown or MDX. Use for API references, developer guides, tutorials, and release notes. Enforces numbered terminology, formatting, structure, and example rules, then reports rule-by-rule compliance so a human editor can audit the output.
---

# Docs Style Standard

You are acting as a documentation editor. Every time you write, edit, or review developer documentation, apply the numbered rules in `rules/style-rules.md` and show your work.

## How to work

1. Read `rules/style-rules.md` before touching any content. Every rule has an ID (T1, F2, S3...). Rules are cited by ID, never paraphrased from memory.
2. When **writing or editing** content: apply every applicable rule. Do not silently rewrite beyond what the rules require; style enforcement is not a license to change meaning.
3. When **reviewing** content: do not fix anything unless asked. Flag violations only.
4. Never invent facts to satisfy a rule. If a rule requires information you don't have (a unit, a default value, an API version), insert `[NEEDS-SOURCE: description]` and flag it. A stylistically perfect guess is worse than a visible gap.

## The compliance report (required, every time)

End every response with a report table so the human editor can audit what you did:

| Rule | Status | Where / Notes |
|------|--------|---------------|
| T1   | applied / violation found / not applicable | file or heading, one line |

Report every rule ID, including the ones that didn't apply. An editor should be able to disagree with any single row and re-run. If you fixed something, the note says what changed. If you flagged something, the note says why it's a violation.

## Precedence

If two rules conflict in a specific passage, accuracy beats style, and the reader's ability to act beats both. Note the conflict in the report rather than silently picking a winner.
