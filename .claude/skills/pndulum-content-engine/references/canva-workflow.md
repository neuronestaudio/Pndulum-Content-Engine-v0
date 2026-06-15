# Canva Delivery Workflow

**Principle:** never generate a fresh design with Canva AI — it breaks brand
consistency. Instead **clone a live Pndulum carousel as the brand master and
inject the new copy text-for-text**, then apply the cover variation.

## Live brand-master carousels (reference designs)
These are the existing, on-brand posts. Clone one of these (match the template):
- Local SEO Levers (9 slides, Diagnostic): `DAHL9tIC1dY`
- Meta vs Google Ads (7 slides, case study): `DAHMIUgpWA0`
- The 5-Minute Rule (7 slides, Industry Insight): `DAHL-QHOyLo`

(IDs are extracted from `https://www.canva.com/design/{design_id}/...`.)

## Steps (Canva MCP tools)
1. **Read the master's content** — `get-design-content` (richtexts) to map the
   text layers and structure you'll overwrite.
2. **Clone it** — `copy-design` on the chosen master → new design retains the
   exact visual template.
3. **Edit text** — `start-editing-transaction`, then
   `perform-editing-operations` to replace each text layer with the new slide
   copy (label, headline, body, big stat, page number). `commit-editing-transaction`.
4. **Adjust the cover** — apply the post's cover variation device.
5. **Hand back** the edit URL for final visual polish.

## Adding/removing slides
If the new post has a different slide count than the master, duplicate or
remove pages in the cloned design before injecting text. Prefer choosing a
master whose length already matches (default 8 → clone the 9-slide SEO master
and trim one, or the 7-slide masters and add one).

## Notes
- Resolve shortlinks first with `resolve-shortlink` if given a `canva.link/...`.
- Keep handle, logo, palette, and `SWIPE →` untouched — only swap copy + cover.
- Export with `export-design` if a flat PNG/PDF set is needed for scheduling.
