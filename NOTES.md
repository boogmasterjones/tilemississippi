# Notes & Pre-Launch TODOs — Tile Mississippi

Speculative rank-and-rent lead-gen site for tile installation in Hattiesburg, MS,
built from `- - RANK AND RENT SITE TEMPLATE- -/CLAUDE.md`. Not tied to a real
operating business yet — see assumptions below.

## Deployment (Netlify)

- Repo is on GitHub at `https://github.com/boogmasterjones/tilemississippi.git`
  (pushed to `main`, renamed from the original "tilemissouri" slug).
- Added `.gitignore` excluding `pictures/` (9.2 MB of original, unoptimized
  source photos — not served by the site, only `assets/photos/` is) and OS junk
  files. `.claude/settings.local.json` also excluded since local permission
  settings shouldn't be version-controlled.
- Added `netlify.toml`: `publish = "."` (root, no build step) plus long cache
  headers for `/assets/*`, `/css/*`, `/js/*`.
- **Still needed from you in the Netlify dashboard** (can't be done from code):
  1. Connect the GitHub repo in Netlify (New site from Git → pick this repo →
     branch `main` → no build command → publish directory `.`).
  2. **Site settings → Forms → Form notifications → add notification → Email
     notification → boogmasterjones@gmail.com** — required for the lead-capture
     form on the homepage and `contact.html` to actually notify anyone.
  3. Set a custom domain once `tilemississippi.com` (or whichever domain you
     land on) is purchased, and update `robots.txt`, `sitemap.xml`, every
     canonical tag, and every JSON-LD `url`/`@id` field if the domain differs
     from what's hardcoded now.
  4. Swap the placeholder GA4 ID (`G-XXXXXXXXXX`) for a real measurement ID once
     you've created the GA4 property.

## Pre-launch TODOs

- **Lead form backend.** The homepage and `contact.html` forms use
  `data-netlify="true"`, which works automatically once deployed to Netlify (no
  backend code needed) — but Netlify Forms only emails a notification once the
  **Site settings → Forms → Form notifications → Email notification** is configured
  in the Netlify dashboard after deploy. **Set that notification email to
  boogmasterjones@gmail.com** — this can't be set from the HTML/form markup itself.
  If not deployed to Netlify, swap the form action to a Formspree endpoint instead
  (requires creating a Formspree account first).
- **GA4 measurement ID is a placeholder** (`G-XXXXXXXXXX`) in every page's `<head>`.
  Replace with a real GA4 property ID before launch (same position in every page —
  immediately after the opening `<head>` tag, per Google's placement requirement).
- **Google Search Console** not yet set up — verify via the **URL prefix** property
  type (not "Domain") once the site has a real domain, then submit `sitemap.xml`.
- **Canonical URLs and JSON-LD `url`/`@id` fields assume the domain
  `tilemississippi.com`** — this domain has not been purchased or confirmed
  available. Update every canonical tag, OG `url`, and JSON-LD URL if a different
  domain is used.
- **Real photos — mostly done.** The user supplied real photos for the 4 non-patio
  service pages, 4 patio material photos, and one photo per city for all 8
  locations (`pictures/services/` and `pictures/locations/` at the project root —
  originals, not deployed). Service photos were resized/cropped with a
  PowerShell + System.Drawing script (heroes to a 1600×900 cover crop, headers
  capped at 1600px on the long edge, patio materials capped at 700px). Location
  photos needed a different pipeline — two arrived as `.avif` and one as `.webp`
  (System.Drawing/GDI+ can't decode either), so those used WPF imaging
  (`System.Windows.Media.Imaging` — `BitmapDecoder` reads avif/webp/jpeg alike,
  `CroppedBitmap` + `TransformedBitmap` + `JpegBitmapEncoder` do the crop/resize/
  re-encode) to a uniform 1600×900 cover crop, quality 85. All resized photos live
  in `assets/photos/<category>/`. Service card photos on the homepage reuse each
  service's hero image; location card photos on the homepage and each location
  page's own hero reuse that city's single photo. Purvis's source photo was only
  516×387, so it's upscaled to fill 1600×900 — noticeably softer than the others,
  though the hero scrim hides most of it, same tradeoff the prior tile client
  project made for a similarly small source. The patio hero/header photos arrived
  later (the header as `.webp`, decoded via the same WPF pipeline) and are now in
  place too — every service and location page has real photography, no
  placeholders remain anywhere on the site.
- **No fabricated trust signals anywhere** (by design, per the content honesty
  rules) — no years-in-business, job count, license number, review count, or
  rating anywhere in copy or JSON-LD. Once this site is attached to a real,
  operating tile contractor, add real business details, license info, and (once
  real reviews exist) `aggregateRating`/`review` schema.
- **Brand name trademark check.** "Tile Mississippi" was checked against a quick
  web search and no operating Hattiesburg-area tile business by that name was
  found, but this was not a formal trademark search. The name went through two
  earlier revisions ("Longleaf Tile Co.," then "Adroit Tile Co.") before landing
  here at the user's request — see `CLAUDE.md` Brand identity section.
- **Phone number** is the template's fixed number, `(941) 564-5088`
  (Google Voice) — used as the live "Call now" CTA everywhere per the template's
  instructions. Replace with a real business line if/when this site is attached to
  an actual contractor.

## Assumptions made during the build

- **Service breakdown** (bathroom / shower / kitchen / floor / patio) mirrors the
  prior tile client project's proven split — confirmed via a quick web search that
  this matches how tile-installation customers typically search.
- **7 location pages** picked for geographic spread and population, after a
  population re-review: Petal, Purvis, Sumrall, Laurel, Ellisville, Columbia,
  Wiggins — see `CLAUDE.md` for the full distance/direction/population table and
  reasoning, including why Collins was swapped for Ellisville and why Picayune,
  Magee, and Poplarville were considered and not used.
- **JSON-LD schema type:** `HomeAndConstructionBusiness` on the homepage (matches
  the prior tile client project's pattern), `Service` + `BreadcrumbList` on service
  pages, `BreadcrumbList` on location pages. No address/geo coordinates included
  since there's no real business address yet.
- **No Calendly/scheduling page** — unlike the prior tile client site, this project
  uses a single `contact.html` page with a lead-capture form as the only
  secondary contact method (no live scheduling embed, since there's no real
  business calendar to book against yet).

## SEO audit fixes (2026-08-01)

A full site-wide SEO audit found and fixed:
- **Duplicate location meta descriptions.** All 7 location pages previously shared
  one template description with only the city name swapped. Rewrote each to pull
  its unique local angle (Purvis's ranch homes, Columbia's Pearl River humidity,
  Wiggins's De Soto National Forest proximity, etc.) into the description Google
  actually shows in search results.
- **Added FAQPage JSON-LD schema** to all 5 service pages and all 7 location pages
  (12 pages total), mirroring the existing visible `<details>/<summary>` FAQ
  content exactly — this is free rich-snippet eligibility (expandable Q&A in
  Google search results) that wasn't being claimed before.
- **Shortened two titles that risked SERP truncation:** Kitchen went from
  "Kitchen Tile & Backsplash Installation | Hattiesburg, MS | Tile Mississippi"
  (~76 rendered chars) to "Kitchen Tile & Backsplash | Hattiesburg, MS | Tile
  Mississippi" (~63 chars); Patio similarly dropped "Installation" from its title.
  The on-page H1s and breadcrumb schema still say the full "Installation" name —
  only the `<title>`/OG/Twitter tags were shortened.
- **Added `og:image`/`og:image:width`/`og:image:height` and matching
  `twitter:image`** to every indexable page (14 of 15 — 404.html intentionally
  skipped since it's noindex and not meant to be shared). Each service/location
  page uses its own hero photo; homepage and contact.html use the kitchen hero.
- **Fixed generic alt text** on 6 of 8 location photos (Petal, Sumrall, Laurel,
  Ellisville, Columbia, Wiggins previously just had `alt="[City], MS"`) to
  actually describe what's in each photo, in both `index.html` and each location
  page's own hero — fixed in both places for each city.
- **Expanded the floor page** from 387 back to ~470 words (added a "Choosing the
  Right Floor Tile" paragraph covering porcelain/ceramic/stone/wood-look plank in
  prose) after the materials gallery section was removed per an earlier request —
  it had dropped below the other service pages' depth.
- **Homepage H1 now contains the target keyword** ("Tile Installation in
  Hattiesburg, MS — Done Like It's Our Own House") instead of relying on the
  `<title>` tag alone for that phrase, while keeping the brand voice intact.
- **`sitemap.xml` `lastmod` dates** bumped to the date of this edit pass (all 14
  entries had been stuck on the initial build date regardless of later changes).
- **Not changed:** GA4 tracking is intentionally absent from `404.html` (noindex,
  not a real crawlable page) — flagged in the audit as optional, not fixed, since
  it's a minor diagnostic nicety rather than an SEO issue.

## Verified

- [x] All 5 service pages + 7 location pages built with differentiated content
      (local landmarks, housing-stock notes, climate notes specific to each city)
- [x] Homepage, `sitemap.xml`, `robots.txt`, `404.html` present and cross-referenced
- [x] GA4 snippet present on every page (placeholder ID, see TODO above)
- [x] No fabricated trust signals anywhere (schema or visible copy)
- [x] All 5 service pages use real project photos (hero + header + homepage
      service card, plus 4 real material photos on the patio page). All 8
      location pages (hub + 7) use real photos for their hero section and
      homepage location card. No placeholder images remain anywhere on the site.
- [x] Lead-capture form present on homepage and `contact.html`, marked as needing
      the Netlify notification-email step above
- [x] Phone number `(941) 564-5088` used consistently (header, footer, CTAs,
      `tel:` links) — no placeholder/made-up number anywhere
- [x] Verified in browser preview (desktop); see TODO to also check mobile widths
      before calling the build fully done
