# PR Review

Automated pull request review that catches correctness bugs, security issues, regression risks, and missing tests before you merge.

## What It Does

Reviews your branch, PR, or local diff against a structured checklist:

- **Correctness** — logic bugs, broken edge cases, data loss, race conditions
- **Security** — injection, auth bypass, secret exposure, unsafe file/network access
- **Compatibility** — API contract changes, migration risks, runtime assumptions
- **Tests** — missing coverage for changed behavior or regression-prone code
- **Maintainability** — duplicated logic, confusing abstractions, avoidable complexity

## How to Use

Point it at a branch or PR and ask it to review. It reports only high-confidence, actionable findings with file paths, line references, impact explanation, and the smallest safe fix.

## Output Example

```
## Findings
### High: Unvalidated user input passed to shell command
- Location: src/utils/runner.ts:42
- Impact: Command injection via crafted filename
- Fix: Use execFile instead of exec, or validate input with allowlist

### Medium: Missing error handling on API timeout
- Location: src/api/client.ts:87
- Impact: Unhandled promise rejection crashes the worker
- Fix: Add try/catch with exponential backoff retry

## Summary
- 1 high, 2 medium, 0 low
- Recommend fixing the high-severity issue before merge
```

## When Not to Use

It won't flag style-only issues unless they hide a real bug. Prefer linting tools for formatting concerns.
