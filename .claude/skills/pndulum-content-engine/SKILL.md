---
name: pndulum-content-engine
description: >-
  Generate Pendulum Digital (Pndulum) social carousels for auto detailers —
  diagnostic, data-backed, Alex Hormozi free-value copy with a familiar
  big-name case-study, then push to Canva by cloning a live brand template.
  Reads from and writes to the shared "PNDULUM META CONTENT ENGINE" Notion
  database every time, learning the house voice from past + partner entries.
  Use when the user asks for a Meta/Instagram carousel, "another post", content
  for auto detailers, or anything in the Pndulum voice.
---

# Pndulum Content Engine

A copy-first content engine for **Pendulum Digital** (handle `@pndulumdigital`),
a marketing agency for **Australian auto detailers** (PPF, ceramic, tint).
It writes scroll-stopping, data-backed carousel copy in a fixed brand voice,
then renders it in Canva by cloning a live carousel as the brand master.

**System of record: the shared Notion database.** Every post is read from and
written to the **PNDULUM META CONTENT ENGINE** Notion database, which is shared
with the partner (who runs a parallel engine, `Hermes`). Read the database
*before* writing — it is the evolving voice model — and fill the template row
*after* writing. Full spec, schema, and the learning loop: `references/notion-database.md`.

## Core philosophy (do not violate)

> **Pendulum diagnoses business problems first. Marketing, AI systems, CRM
> automation and lead-gen are introduced only *after* the diagnosis lands.**

- **Persona:** diagnostic, direct, problem-aware. We are obviously a
  high-level agency — the copy and design must look the part.
- **Hormozi free value:** give the *entire* fix away for free. The full
  "do-it-Monday" checklist goes in the post. The offer is done-for-you, not
  withheld information.
- **Trust through honesty:** every post earns belief with a real, cited
  number and at least one **honest counterpoint** (the place our own argument
  is weakest). This is the single most important credibility move.

## The five non-negotiables for every post

1. **Verify every statistic with a live web search before writing.** Pndulum's
   whole brand rests on "backed by studies." Never invent or approximate a
   number, and **never claim primary research Pndulum didn't do** (no "we
   surveyed 100 detailers" unless it's real — anchor in citable sources like
   IBISWorld instead). Cite the source on-slide (e.g. `Whitespark, 2026`).
2. **One familiar big-name corporation as the case study,** with backed data
   (Amazon, Tesla, McDonald's, Starbucks, Domino's, Salesforce…). This is the
   "what the giants know" lever. See `references/case-study-bank.md`.
3. **An honest-counterpoint slide** — name where the easy answer is wrong or
   where our own claim has a limit. (e.g. "Google still closes 2.5× higher.")
4. **Give the full fix away** — a numbered "DO IT MONDAY / STEAL THIS" slide.
5. **One clear CTA** — `Comment "WORD"` for a DM asset, or a free audit. Plus
   `SAVE THIS` and `Follow @pndulumdigital`.

## Workflow

0. **Sync from the database first** (`references/notion-database.md`). Query the
   Notion DB across **both engines** (`Claude Code` *and* `Hermes`) to: (a) avoid
   cannibalising a recent topic or `Content Lesson`, (b) learn the current house
   voice from `Approved`/`Posted` rows, and (c) read the `Manual Edits` column —
   the human corrections are the strongest voice signal. Note the current max
   `Number`. This DB is now the canonical log (supersedes `posts/POST-LOG.md`).
1. **Pick the topic.** Pull from `references/topic-bank.md`. Cross-check against
   the DB sync above — do **not** cannibalise a recent post (e.g. speed-to-lead
   has been done heavily; avoid re-treading it).
2. **Choose a template** (`references/carousel-templates.md`): Diagnostic,
   Revenue Leak, or Industry Insight. Rotate for variety.
3. **Research & verify.** Run parallel web searches for: the core stat, the
   big-name case-study data, and one supporting number. Keep only sources you
   can name.
4. **Write the slides** in the brand grammar (`references/brand-voice.md`):
   lowercase pain hook → ALL-CAPS payoff headline → one cited line per slide.
   Default to the **sharp & data-led** voice (owner's preference; numbers do the
   talking) — not the heavier emotional tone. 7 slides matches the live Canva
   masters; 8 is the doc-only ideal.
5. **Vary the cover.** Keep logo/handle/palette/`SWIPE →` fixed; vary ONE
   cover device per post so the feed looks designed by an agency
   (`references/brand-voice.md` → Cover variation system).
6. **Ship the package:** per-slide copy + caption + hashtags + a `Sources:`
   list of real links.
7. **Render in Canva** (`references/canva-workflow.md`): clone a live carousel
   as the brand master and inject the copy text-for-text. Do **not** use Canva
   AI to generate fresh designs — it breaks brand consistency.
8. **Write the template row to Notion** (`references/notion-database.md`). Create
   one new page in the data source, fill **every** field (Carousel Name, Number,
   Angle, Content Lesson, Slide 1 Hook, Slide Breakdown, CTA, Slide Count,
   Post Caption, Post Date if known), set `Engine = Claude Code`, set
   `Status = Needs Edit` (lands in the partner's Approval Queue), and leave
   `Manual Edits` empty for the human. Add the `Canva Link` once rendered.
9. **Also save locally:** mirror the copy to `posts/` and append a line to
   `posts/POST-LOG.md` (the DB is canonical; the files are a backup/worked log).

## Output format

Deliver copy as one block per slide: `Label` → `Headline` → `Body` (+ big stat
where used), then page number `n/8`. Follow with the caption, hashtags, and
sources. Worked examples: `posts/post-01-no-more-leads.md`,
`posts/post-02-ev-growth.md`.

## References

- `references/brand-voice.md` — voice, slide grammar, cover-variation system
- `references/carousel-templates.md` — the 3 slide skeletons
- `references/canva-workflow.md` — clone-and-inject Canva process + MCP tools
- `references/case-study-bank.md` — verified big-name case studies + data
- `references/topic-bank.md` — the 10-topic content bank
- `references/notion-database.md` — the shared Notion DB: schema, template
  fields, status flow, and the read-before-write **learning loop**
- `posts/POST-LOG.md` — local backup log (the Notion DB is now canonical)
