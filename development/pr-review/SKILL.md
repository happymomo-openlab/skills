---
name: pr-review
description: Review a pull request for correctness, regressions, security issues, and missing tests.
version: 0.1.0
author: happymomo
tags:
  - development
  - code-review
  - quality
---

# PR Review

## When to Use

Use this skill when the user asks to review a branch, pull request, or local diff before merge.

## Review Priorities

1. Correctness: logic bugs, broken edge cases, data loss, race conditions.
2. Security: injection, auth bypass, secret exposure, unsafe file/network access.
3. Compatibility: API contract changes, migration risks, runtime assumptions.
4. Tests: missing coverage for changed behavior or regression-prone code.
5. Maintainability: duplicated logic, confusing abstractions, avoidable complexity.

## Rules

- Report only high-confidence, actionable findings.
- Include file paths and line references when available.
- Explain impact and suggest the smallest safe fix.
- Do not block on style-only comments unless they hide a real bug.

## Output Format

```markdown
## Findings

### High / Medium / Low: Title
- Location: path:line
- Impact: ...
- Fix: ...

## Summary
- ...
```
