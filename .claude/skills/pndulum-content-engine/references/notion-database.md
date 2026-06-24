# Notion Database — the system of record

The shared **PNDULUM META CONTENT ENGINE (DATABASE)** is the single source of
truth for everything this engine produces. It is shared with the partner, who
runs a parallel engine (**Hermes**). Every post **must** be written into this
database, and the database must be **read first** so the engine keeps learning
the house voice.

- **Database URL:** https://app.notion.com/p/84ebfdb27d10451c8fb1484de07d83ec
- **Data source ID:** `collection://d1044c64-a9fe-41c2-a7ce-d90e4b4565b1`
- **Tools:** the Notion MCP — `notion-fetch`, `notion-query-data-sources`,
  `notion-create-pages`, `notion-update-page`. Load them via ToolSearch
  (`select:notion-create-pages,notion-query-data-sources` …) before use.

## Who owns what (the `Engine` field)

| Engine        | Who         | View                |
|---------------|-------------|---------------------|
| `Claude Code` | Dion (this) | "Dion / Claude Code"|
| `Hermes`      | Partner     | "Partner / Hermes"  |
| `Manual`      | hand-made   | —                   |
| `Hybrid`      | mixed       | —                   |

**Anything this skill produces is `Engine = Claude Code`.** Never overwrite a
`Hermes` or `Manual` row — those belong to the partner.

## The template — fill EVERY field, every time

When a post is generated, create one new page in the data source and populate:

| Field            | Type   | What goes in it |
|------------------|--------|-----------------|
| `Carousel Name`  | title  | Short, human title (e.g. "Cut Your CPL in 2026") |
| `Number`         | number | Next sequential number (max existing `Number` + 1) |
| `Angle`          | select | One of: Problem-aware, Education, Case Study, Proof, Offer, Authority, Behind the Scenes |
| `Content Lesson` | text   | **A meta-reflection FOR THE ENGINE** — what pattern/spine/giant/objection this post used and when to reuse it. NOT the post's takeaway. This is the field the learning loop reads back. |
| `Slide 1 Hook`   | text   | The exact cover/slide-1 hook line (lowercase, problem-aware) |
| `Slide Breakdown`| text   | Per-slide copy. House format: `NN ROLE \| HEADLINE \| body`, one slide per line, separated by `<br>` (e.g. `01 COVER (...) \| ... \| ...<br>02 INSTINCT \| ...`). Use `<br>` for every line break inside any text field. |
| `CTA`            | text   | The CTA word + offer (e.g. `Comment "CPL"` / free audit) |
| `Slide Count`    | number | Number of slides (7 = live Canva masters, 8 = doc-only ideal) |
| `Status`         | select | See status flow below — a finished generated post = **Needs Edit** |
| `Post Caption`   | text   | The full Instagram caption + hashtags |
| `Post Date`      | date   | Planned post date if known; otherwise leave empty |
| `Canva Link`     | url    | Fill once rendered in Canva (else leave empty) |
| `Manual Edits`   | text   | **Leave empty** — this is the human's column (a learning signal) |
| `Engine`         | select | Always `Claude Code` for this engine |

Read-only / system fields — **do not set**: `Created`, `Last Edited`.

### Status flow

`Idea` → `Draft` → `Needs Edit` → `Approved` → `Scheduled` → `Posted` → `Archived`

- A bare concept (no copy yet) = **Idea**.
- A fully-written post from this engine = **Needs Edit** — this lands it in the
  partner's **Approval Queue** view for human review/sign-off.
- The humans drive it from there (Approved → Scheduled → Posted).

## The learning loop (read before you write)

Before writing any new post, query the database and learn from it. The database
— not a static file — is now the evolving voice model.

1. **Avoid cannibalisation.** Pull recent rows across **both engines** and skip
   topics/lessons already covered (check `Content Lesson`, `Slide 1 Hook`,
   `Carousel Name`). This supersedes `posts/POST-LOG.md` as the canonical log.
2. **Learn the house voice from what shipped.** Read `Approved` + `Posted` rows
   (both `Claude Code` and `Hermes`). The partner's `Hermes` rows are voice
   exemplars — match their cadence, not just past Claude output.
3. **Mine `Manual Edits` — the most valuable signal.** Where a human edited a
   Claude draft, the diff between the draft and the approved/posted version is a
   direct voice correction. Internalise those edits before drafting.
4. **Distil and improve the skill itself.** When a manual-edit pattern recurs
   (same fix made 2–3+ times — e.g. "they always shorten the hook", "they cut
   the emoji", "they prefer AU spelling"), propose updating
   `references/brand-voice.md` so the correction becomes permanent. Surface this
   to the user; don't silently rewrite voice rules.

## Query patterns

> **Plan gate (important):** `notion-query-data-sources` (SQL **and** view mode)
> requires a Notion **Business plan + Notion AI**. On the current plan it returns
> a `validation_error`. Use the search+fetch fallback below instead.
> A plain `notion-fetch` on the database URL returns only the **schema**, never
> the rows — do not conclude the DB is empty from that.

- **Pre-write sync (read rows):** `notion-search` with
  `data_source_url: collection://d1044c64-a9fe-41c2-a7ce-d90e4b4565b1` and a
  topic query → returns page IDs (incl. the `🧩 TEMPLATE — Carousel Copy Map`
  exemplar). Then `notion-fetch` each relevant page ID to read its full
  properties (`Slide Breakdown`, `Content Lesson`, `Manual Edits`, `Status`,
  `Engine`). Prioritise `Posted`/`Approved` rows and the partner's `Hermes` rows
  as voice exemplars.
- **Write a post:** `notion-create-pages` with
  `parent: {type: data_source_id, data_source_id: d1044c64-...}` and the template
  fields above (set `date:Post Date:start` for the date column).
- **Add the Canva link later:** `notion-update-page` (command
  `update_properties`) on the row's `page_id`, set `Canva Link` once the carousel
  is rendered. (`Canva Link` is its own property — fill it only after design.)
- **`Number`:** the team leaves it blank often; do not fabricate a value or
  reuse `1`. Leave empty unless the user gives the next number.
