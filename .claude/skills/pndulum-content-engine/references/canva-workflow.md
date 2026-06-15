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

## Gotchas / lessons learned (proven workflow)
- **Cloning is reliable; the 5-Minute master is the workhorse.** Clones of the
  same master reuse identical element IDs, so the role→ID map is stable:
  - Cover: label `…-LBv5CD974dVk07Vc`, headline line1 `…-LBfNndVSXK7Mb6hT`,
    line2 `…-LBDx1lBvzJLbgdhs`, body (2 regions: text + citation) `…-LBXDJhgPpKqTzrBT`.
  - Slide 3 big stat `…-LBzvx5rV5TgvVRSc`, its caption `…-LBwYTXbkP0TM5dl8`.
  - Slide 6 "do it Monday" items: `…-LBbyBqFd1ZnWcJcP` (01), `…-LBfwS1PYWbPNprlS`
    (02), `…-LBcjRHsJsRcBf71g` (03); bottom line `…-LB5vlTGl10l76qVh`.
  - Slide 7 CTA word region is the SECOND region of `…-LBh4H1QBj19qjxY2`
    (find/replace `"WORD"`); DM line is region 1 of `…-LBx46yjctKQXhTt1`.
  Still call `start-editing-transaction` each time to get the live `transaction_id`.
- **Cover headline wrap.** Keep cover line 1 short (~12–15 chars, like "wait 30
  minutes"). Longer lines wrap to a 3rd line and overlap line 2. If it wraps,
  shorten and re-run before committing.
- **API limits.** Can't change background ARTWORK and can't add/remove pages.
  So: pick a master whose length + look already fits, and the owner restyles
  cover backgrounds manually per the cover-variation system.
- **Multi-colour cover** (Meta master, "META OR GOOGLE ADS"): headline is 4
  coloured regions — `find_and_replace_text` each word to keep its colour.
- **Preserve owner edits.** The owner sometimes adds images/lines by hand
  (e.g. a Tesla photo on the EV cover). Text ops don't touch image fills — leave
  their additions alone unless asked.
- Use `find_and_replace_text` for multi-region elements (preserves per-run
  styling like the bold citation); `replace_text` for single-region elements.
- ALWAYS get explicit approval before `commit-editing-transaction`.

## Master design IDs (sources to clone)
- 5-Minute Rule (Industry Insight, sun-glow): `DAHL-QHOyLo`
- Meta vs Google (multi-colour cover, counterpoint+list): `DAHMIUgpWA0`
- Local SEO Levers (9-slide diagnostic): `DAHL9tIC1dY`
