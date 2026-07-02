# Static Site Publishing

Publish HTML reports, dashboards, and interactive decision forms to a public URL — complete with sanitization checks, theme consistency, and one-click sharing.

## What It Does

Every time your agent produces an HTML artifact, this skill ensures:

- **Correct file placement** — writes to the right nginx-served directory, avoiding 404 traps
- **Theme consistency** — applies the standard light theme CSS instead of ad-hoc dark styles
- **Sanitization check** — verifies the page is safe before making it publicly visible
- **Auto-publishing** — the page is live at a public URL immediately after generation

## Output Types

- **Product pages** — hero section, problem/solution, how it works, FAQ
- **Interactive decision forms** — drag-to-rank, multi-select cards, conditional sections, export-to-markdown
- **Report pages** — structured analysis results with charts and tables

## How to Use

Just ask your agent to create a report or HTML page. It automatically handles publishing. Share the generated URL on any platform.

## Why

Without this skill, agents write HTML to random directories, break theme consistency, or serve pages with exposed internal data. This workflow makes publishing reliable and safe.
