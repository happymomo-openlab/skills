---
name: publish-skill-to-marketplace
description: Publish a skill to the public marketplace on happymomo-openlab/skills. Every skill needs skill.json + README.md + SKILL.md. README.md follows the standard template so the public skills page renders it correctly.
triggers:
  - "publish skill"
  - "add skill to marketplace"
  - "public skill"
  - "README template"
  - "skill template"
  - "上传公开技能"
  - "发布skill"
---

# Publish Skill to Public Marketplace

Publish a skill to `https://github.com/happymomo-openlab/skills` so it appears on the public skills page at `happymomo.ai/skills`.

## Required Files

Every skill MUST have these three files in its directory:

| File | Purpose |
|------|---------|
| `skill.json` | Metadata for DB sync (slug, name, description, category, tags) |
| `README.md` | Public-facing description — rendered on the skills detail page |
| `SKILL.md` | Agent instruction file — what the agent reads when the skill is loaded |

## README.md Template

```markdown
A clear, one-sentence description of what this skill does.

## What It Does

- **Key point** — what it specifically handles or automates
- **Key point** — another capability
- **Key point** — another capability

## How to Use

A brief paragraph telling the user how to invoke this skill — what prompt to use, what context to provide.

## When Not to Use

When this skill won't help, and what to use instead.

## Why

Why someone would install this — what problem it solves that doing it manually doesn't. 1-2 sentences.
```

### Template Rules
- **NO `# Title`** — the page already shows the skill name at the top
- **`## Why` goes at the END** — the code extracts it and moves it to a dedicated "Why people use this skill" section at the bottom of the page
- Keep `## What It Does` as bullet points
- `## How to Use` and `## When Not to Use` as paragraphs
- Reference template: `https://github.com/happymomo-openlab/skills/blob/main/README_TEMPLATE.md`

## skill.json Format

```json
{
  "slug": "my-skill",
  "name": "My Skill",
  "description": "One-line description matching README intro.",
  "version": "0.1.0",
  "author": "Mergio",
  "category": "devops",
  "tags": ["tag1", "tag2"],
  "status": "published"
}
```

## Step-by-Step Workflow

### 1. Create the skill files

Clone `happymomo-openlab/skills`, create `{category}/{slug}/` with the three files.

### 2. Push to GitHub

```bash
cd /tmp/skills
git add {category}/{slug}/
git commit -m "feat: add {skill-name}"
git push origin main
```

Use the DengZY123 PAT at `/tmp/gh_token3` for write access.

### 3. Sync to DB

Run on the Dokploy container (SSH to 172.17.0.1 with `~/.ssh/id_ed25519`):

```bash
docker exec mergio-mergioweb-gtlxhf.1.1lnfrkmlr32xhwgvwsb1coh4n \
  sh -c 'PUBLIC_SKILLS_SOURCE_REPO=happymomo-openlab/skills npx tsx scripts/sync-public-skills.ts'
```

Or update `source_repo` directly if only modifying an existing skill:

```bash
docker exec {container} node -e "
  const { Pool } = require('pg');
  const pool = new Pool({ host: process.env.POSTGRES_HOST, ... });
  pool.query('UPDATE public_skills SET source_repo=\$1 WHERE slug=\$2', ['happymomo-openlab/skills', 'my-skill']);
"
```

### 4. Verify

Wait for ISR cache (3600s) or check: `https://happymomo.ai/en/skills/{slug}`

## What Happens Behind the Scenes

1. Public page SSR calls `fetchMarketplaceSkillReadme(source_repo, source_path)` → GitHub raw `README.md`
2. Description area renders `readme.split(/\n## Why\b/)[0]` (everything before Why)
3. Bottom area renders `extractWhySection(readme)` (only the Why content)
4. `SKILL.md summary` section renders truncated `fetchMarketplaceSkillInstructionSummary()`

## Allowlist

The `happymomo-openlab/*` org is in the default source allowlist (`source-fetcher.ts`). No extra config needed.
