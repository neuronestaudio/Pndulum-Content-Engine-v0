# Pndulum Content Engine v0

A copy-first **content engine** for **Pendulum Digital** (`@pndulumdigital`) —
diagnostic, data-backed, Alex Hormozi free-value carousels for **Australian
auto detailers**, rendered in Canva from a cloned brand template.

> **Philosophy:** diagnose the business problem first. Every post earns trust
> with a verified statistic, a familiar big-name case study, and an honest
> counterpoint — then gives the full fix away for free.

## How to use this repo

This repo ships a Claude Code skill. When you open this repo in Claude Code,
the skill is auto-discovered from `.claude/skills/`. Just ask:

> "Write the next Pndulum carousel" — or — "do another post for the detailers"

Claude will: **sync from the shared Notion database** (learning the house voice
from past + partner entries) → pick a topic from the bank (avoiding
cannibalisation) → choose a template → **verify every stat with a live web
search** → write the slide copy in the brand voice → offer to push it to Canva →
and **write the filled template row back to Notion**.

## The Notion database (system of record)

This engine reads from and writes to the shared **PNDULUM META CONTENT ENGINE**
Notion database every run. It's shared with the partner's engine (`Hermes`), and
the database — not a static file — is the evolving voice model: every post fills
a template row, and every run learns from past entries and the human `Manual
Edits`. Full spec: `.claude/skills/pndulum-content-engine/references/notion-database.md`.

To use it from any project, copy `.claude/skills/pndulum-content-engine/` into
your `~/.claude/skills/` folder.

## What's inside

```
.claude/skills/pndulum-content-engine/
├── SKILL.md                      # the operating procedure
└── references/
    ├── brand-voice.md            # voice, slide grammar, cover variations
    ├── carousel-templates.md     # 3 slide skeletons
    ├── canva-workflow.md         # clone-and-inject Canva process
    ├── case-study-bank.md        # verified big-name case studies
    ├── topic-bank.md             # the 10-topic content bank
    └── notion-database.md        # shared Notion DB: schema, template, learning loop
posts/
├── POST-LOG.md                   # shipped log (avoid cannibalisation)
├── post-01-no-more-leads.md      # worked example — Diagnostic / Amazon
└── post-02-ev-growth.md          # worked example — Industry Insight / Tesla
```

## The five non-negotiables

1. Verify every statistic with a live web search before writing.
2. One familiar big-name corporation as the case study, with backed data.
3. An honest-counterpoint slide.
4. Give the full fix away (DO IT MONDAY).
5. One clear CTA + `SAVE THIS` + `Follow @pndulumdigital`.
