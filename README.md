# Ingest Narrative & Spin Up Branded Microsite

An Agent Skill that transforms a raw customer Salesforce narrative into a beautifully branded, Heroku-ready HTML/Tailwind microsite — complete with deployment scaffolding.

This repo ships **two optimized versions** of the same skill:

| Version | File | Optimized for |
| --- | --- | --- |
| Cursor | [`SKILL-cursor.md`](./SKILL-cursor.md) | [Cursor](https://docs.cursor.com/) |
| Claude Code | [`SKILL-claude.md`](./SKILL-claude.md) | [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) |

Both versions run the same pipeline and produce the same output. They differ only in the agent-specific tooling used for the web-scraping step (Cursor's browser tool vs. Claude Code's `WebFetch` tool) and their install locations.

## What is this?

This skill activates a specialized pipeline that takes a plain markdown narrative and turns it into a polished, on-brand web experience. It scrapes brand signals from the customer's site and Salesforce brand guidelines, maps the narrative content into structured visual sections (hero, metrics, story), generates the site code, and prepares everything needed for an immediate Heroku deployment.

## When to use it

**Use this skill to build consumption-focused narrative sites for customer-facing presentations.** It's designed for turning a story or account narrative into a shareable, branded microsite that puts the customer's brand — alongside Salesforce's — front and center.

Reach for it when you want to:

- Ingest a narrative markdown file and spin up a microsite from it.
- Apply customer and Salesforce brand signals (colors, typography, UI vibe) automatically.
- Generate a deployable HTML/Tailwind site for a customer presentation.
- Prepare immediate Heroku deployment artifacts (Express `server.js`, `Procfile`).

## How it works

The skill runs through four steps:

1. **Scrape & extract design tokens** — Pulls dominant brand colors, typography, and UI vibe from the customer URL and Salesforce brand guidelines, plus any local override assets in `./branding/`.
2. **Architecture & layout mapping** — Reads the narrative `.md` and maps it into structured sections: a customized hero, current-state metrics rendered as Tailwind components, and the core story.
3. **Code generation & deployment prep** — Generates `index.html` (Tailwind via CDN or Vite), optional `app.js`/`style.css`, and a Node.js `server.js` + `Procfile` for Heroku.
4. **Verification** — Confirms WCAG AA color contrast and that every section of the narrative is represented in the output.

## Prerequisites

Before running, the workspace should contain:

1. A target narrative file (e.g., `input/customer-narrative.md`).
2. A configuration file (`input/config.json`) containing:
   - `customer_url`: `"https://..."`
   - `salesforce_brand_url`: `"https://www.salesforce.com/company/brand/"`

## Installation

### Cursor

```bash
mkdir -p ~/.cursor/skills/ingest-narrative-spin-up-branded-microsite-cursor-optimized
cp SKILL-cursor.md ~/.cursor/skills/ingest-narrative-spin-up-branded-microsite-cursor-optimized/SKILL.md
```

Then invoke the skill from Cursor by asking the agent to ingest a narrative and spin up a branded microsite.

### Claude Code

```bash
mkdir -p ~/.claude/skills/ingest-narrative-spin-up-branded-microsite-claude-code-optimized
cp SKILL-claude.md ~/.claude/skills/ingest-narrative-spin-up-branded-microsite-claude-code-optimized/SKILL.md
```

Then invoke the skill from Claude Code by asking the agent to ingest a narrative and spin up a branded microsite.

## Files

- [`SKILL-cursor.md`](./SKILL-cursor.md) — The Cursor-optimized skill definition.
- [`SKILL-claude.md`](./SKILL-claude.md) — The Claude Code-optimized skill definition.
