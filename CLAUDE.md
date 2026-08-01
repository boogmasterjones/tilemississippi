# Tile Mississippi — Hattiesburg, MS (rank-and-rent lead-gen site)

Built from `- - RANK AND RENT SITE TEMPLATE- -/CLAUDE.md`. This is a **speculative
local-SEO lead-gen site**, not a real operating business — see "Content honesty rules"
below before writing/editing copy. No real business history, no fabricated trust
signals (no review counts, no "X years in business," no license numbers).

- **Niche:** Residential tile installation
- **Target city (hub):** Hattiesburg, MS
- **Phone (fixed across all rank-and-rent template sites):** `(941) 564-5088` /
  `tel:+19415645088` (Google Voice)
- **Email:** unknown at kickoff — lead form is the secondary contact method (see
  Lead form notes below).

## Brand identity

- **Name:** Tile Mississippi — went through two prior working names before this:
  "Longleaf Tile Co." (navy/copper, Pine Belt-themed) was rejected by the user, then
  "Adroit Tile Co." was confirmed and built out, then the user asked for "Tile
  Missouri" — flagged as a likely mix-up since this entire site is Hattiesburg,
  **Mississippi** (not Missouri), confirmed via AskUserQuestion, and landed on **Tile
  Mississippi** as the final name. No operating Hattiesburg-area tile business found
  under this name via a quick web search.
- **Voice:** Written in first person as the installer speaking directly ("we install,"
  "we handle," "we'll get back to you") — **not** rank-and-rent "we connect you with a
  local installer" language. This was an explicit user correction; the site should
  read like a real, singular tile crew, not a lead-gen middleman. This does **not**
  relax the content-honesty rules below — no fabricated years/jobs/reviews, just a
  direct-installer voice instead of a hedged connector voice.
- **Domain:** `tilemississippi.com` (not yet purchased/confirmed available — see
  `NOTES.md`).
- **Palette** (CSS custom properties, `css/style.css`) — deliberately moved *away*
  from the navy-blue family used by both the prior tile client site (rsitile.com,
  navy `#142338` / gold `#C9A84C`) and this project's own earlier Longleaf draft, per
  explicit user feedback that the site looked too similar to rsitile.com. Now a
  charcoal + terracotta-clay palette (literally tile-colored) instead of navy:

  | Variable | Value | Use |
  |---|---|---|
  | `--charcoal` | `#24211E` | Primary / hero / footer background |
  | `--charcoal-mid` | `#332E29` | Secondary dark section background |
  | `--clay` | `#C4552E` | CTAs, primary accent, phone number |
  | `--clay-dark` | `#A2431F` | Hover state for clay elements |
  | `--slate` | `#5C6D66` | Secondary accent (icon chips, links) |
  | `--stone` | `#F5F0E8` | Light section backgrounds (warm, not cool white) |
  | `--ink` | `#24211E` | Body headings on light backgrounds |
  | `--body-text` | `#5B534B` | Body copy on light backgrounds |

- **Typography:** `Oswald` (600/700) for headlines instead of the template's default
  Barlow Condensed — chosen specifically so the type doesn't read the same as
  rsitile.com (which uses Barlow Condensed). `Inter` for body copy (kept — body font
  similarity is far less noticeable than headline font).
- **Buttons/icons/art — tactile, offset-shadow system inspired by the
  `INTERIOR MOTIVES` project's button treatment** (see that project's
  `css/style.css` `.btn` rules for the reference pattern), adapted with this site's
  own charcoal/clay colors rather than copied outright:
  - `.btn` has a solid 2px border + a hard 4px offset shadow (`box-shadow: 4px 4px 0
    var(--charcoal)`) that compresses to 2px on hover and disappears on `:active`
    (translate + shadow shrink), giving buttons a pressable, tactile feel instead of
    a flat rounded rectangle.
  - Icons are wrapped in a rotated-45°-square "diamond tile" chip (`.icon`, `.chip`
    classes) instead of a plain circle — a literal tile motif, reused across
    `why-item`, `trust-badge`, `area-card`, `contact-list`, and the card
    corner-notch accent (`.card::before`, a small clay triangle in the top-left
    corner of every service card).
  - The hero background uses an offset two-layer grid (`.hero::before`/`::after`)
    meant to read as brick/subway-tile coursing, not the plain single-layer thin-grid
    dot pattern rsitile.com and the earlier Longleaf draft both used.
  - The logo mark is a small pinwheel-diamond SVG (four triangles in clay/slate/taupe/
    stone around a center point) — reused as the favicon and in every header/footer
    logo lockup.

## Location research (Step 1)

Hattiesburg is the hub page (homepage). Verified driving distances (not straight-line)
via web search; all candidates are real incorporated towns/county seats, not CDPs.
Picked 7 for geographic spread around Hattiesburg:

| City | Direction | Driving distance | Population (2020 census) | Why picked |
|---|---|---|---|---|
| Petal | E | ~4 mi | ~10,200 | Hattiesburg's twin city across the Leaf River, own identity, high search volume |
| Purvis | SSW | ~11 mi | ~1,910 | Lamar County seat; kept despite being the smallest pick — very close (prime "near me" search territory) and a fast-growing bedroom community |
| Sumrall | WNW | ~12 mi | ~2,170 | Prominent Lamar County town; no larger town found in this direction within range |
| Laurel | NNE | ~30 mi | ~18,000 | Jones County seat, most prominent pick besides Hattiesburg itself |
| Ellisville | NNE | ~22 mi | ~4,652 | Jones County city ~7 mi south of Laurel — clusters direction-wise with Laurel, but user explicitly chose it over the more-spread-out Collins (~2,240 pop) after a population-vs-spread tradeoff review; replaced Collins in this lineup |
| Columbia | WSW | ~33 mi | ~6,500 | Marion County seat |
| Wiggins | S | ~39 mi | ~4,280 | Stone County seat |

**Population re-review (post-launch):** the user asked whether population had been
maximized. Verified every real alternative within ~50 mi via web search — Picayune
(~11,885 pop) is the only larger town nearby but at 63 mi it's well outside the
radius cap, so it was excluded. Magee (~3,988 pop, ~47 mi, N/NNW) was considered to
fill the north slot but the user chose to skip it (marginal population gain, near
the edge of the radius, no existing north-direction pick to replace). Collins
(~2,240 pop, NNW) was swapped for Ellisville (~4,652 pop, NNE) — nearly double the
population and closer to Hattiesburg, at the cost of clustering near Laurel instead
of spreading into a fourth compass direction. Poplarville (~2,833 pop, SSW/S, ~40 mi)
was considered as a Purvis replacement but rejected — modest population gain for
4x the distance, and redundant with Wiggins' southern coverage.

## Service breakdown (Step 2)

Mirrors the proven tile-project split (bathroom/shower/kitchen/floor/patio) —
research confirmed this is the standard way tile-installation customers search:

1. Bathroom tile installation
2. Shower tile installation
3. Kitchen tile installation (incl. backsplash)
4. Floor tile installation
5. Patio & outdoor tile installation

## Site structure

Same as the template's Step 4 — `services/`, `locations/` sibling dirs, `css/`,
`js/`, `index.html`, `contact.html`, `404.html`, `sitemap.xml`, `robots.txt`.
No build step, static HTML/CSS/vanilla JS, deployable via Netlify drag-and-drop.

## Lead form

Homepage and `contact.html` both use a Netlify Forms lead-capture form
(`data-netlify="true"`, no backend code needed). **The Netlify dashboard's Form
notifications email needs to be set to boogmasterjones@gmail.com after deploy**
(Site settings → Forms → Form notifications) — this can't be set from the HTML/form
markup itself, only from the Netlify dashboard once the site is live. See
`NOTES.md` for the full pre-launch checklist.

## Local dev / preview

No Node/Python assumed on this machine — PowerShell static file server
(`System.Net.HttpListener`) via `.claude/launch.json`, same pattern as prior projects.

## Content honesty rules

No fabricated years-in-business, job counts, license numbers, review counts, or
ratings anywhere (copy or schema) until this is attached to a real business. Photos
are dashed-border `.placeholder` blocks with descriptive `aria-label`s until real/
licensed photography is supplied — do not bulk-download stock photos autonomously.
The first-person "we install" voice (see Brand identity above) is compatible with
these rules — it's a tone choice, not a factual claim like a review count or years in
business would be.
