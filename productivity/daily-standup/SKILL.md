---
name: daily-standup
description: Prepare concise daily standup updates from tasks, commits, notes, or chat context.
version: 0.1.0
author: happymomo
tags:
  - productivity
  - team
  - status
---

# Daily Standup

## When to Use

Use this skill when the user wants to prepare a daily standup update, summarize yesterday/today/blockers, or turn messy notes into a short team status.

## Workflow

1. Gather available context: recent commits, task notes, chat messages, or pasted bullets.
2. Separate the update into three sections: yesterday, today, blockers.
3. Keep each section short and concrete.
4. Remove implementation noise unless it affects team coordination.
5. If important context is missing, list assumptions instead of inventing details.

## Output Format

```markdown
Yesterday
- ...

Today
- ...

Blockers
- None / ...
```
