Systematic methodology for diagnosing API request failures — trace by request ID, user ID, or email. Identify root causes fast and produce actionable reports.

## What It Does

- **Traces the full request chain** — API gateway → backend → database → response
- **Identifies failure patterns** — rate limits, auth errors, timeouts, model config issues
- **Checks common causes** — expired tokens, missing headers, quota exhaustion, upstream errors
- **Produces a summary report** with root cause, impact, and a user-facing talking point

## How to Use

Share a `request_id`, `user_id`, or the user's email with your agent and ask it to "troubleshoot this failure." The agent queries logs, walks the diagnostic checklist, and tells you what went wrong.

## When Not to Use

- For performance optimization or capacity planning — use profiling tools
- If the failure is reproducible in your local environment — debug directly instead
