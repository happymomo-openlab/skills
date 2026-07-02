Publish a skill to the public marketplace so it appears on happymomo.ai/skills with a standardized, clean detail page.

## What It Does

- **Enforces the three-file structure** — every skill needs skill.json (metadata) + README.md (public page) + SKILL.md (agent instructions)
- **Standardizes README format** — What It Does / How to Use / When Not to Use / Why, with Why auto-extracted to a dedicated section on the page
- **Handles GitHub push + DB sync** — clone, commit, push to happymomo-openlab/skills, then sync the public_skills table

## How to Use

Clone `happymomo-openlab/skills`, create `{category}/{slug}/` with skill.json, README.md (follow the template at `README_TEMPLATE.md`), and SKILL.md. Push to main. Then run the sync script on the Dokploy container to update the database.

## When Not to Use

If the skill only lives in Mergio-AI/skills for agent use and doesn't need a public detail page, skip this. This workflow is for skills that appear on the public marketplace.

## Why

Without a template, every skill's README has different structure — some show raw SKILL.md, some have duplicate headings, some look broken. This skill makes every public skill page consistent and readable.
