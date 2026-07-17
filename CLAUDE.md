# Central Medical Associates — Website

Live site: the `main` branch auto-deploys via GitHub Pages (~1 minute after every push).
Custom domain: cmahardin.com (once DNS is connected; otherwise the *.github.io/cma-website URL).

## What this is

A single-page static website for Central Medical Associates, a physician-led primary care
group in Elizabethtown & Radcliff, Kentucky. The entire site is **one file: `index.html`**
(inline CSS + JS, no build step, no frameworks, no dependencies). Photos live in `assets/img/`.

## How to make edits

1. Edit `index.html` directly (content is plain HTML; CSS is in the single `<style>` block).
2. Commit and push to `main`. GitHub Pages redeploys automatically — verify at the live URL
   about a minute later. There is no build command; what you push is what serves.
3. Preview locally with `python3 -m http.server 8000` and open http://localhost:8000.

## Page map (section ids)

`#about` story + timeline · `#services` 3 service cards + full tag list · `#locations`
5 offices w/ Google Maps embeds · `#providers` 12 clinician cards with expandable bios ·
`#patients` visit prep · `#health-library` patient-education articles · `#news` announcements ·
`#billing` payment policies · `#heat-exhaustion` + `#focus-on` seasonal "Focus On" deep-dives
(current + previous topic) · footer = contact + affiliations. The gold announcement bar sits
under the nav. The nav's "Focus On…" item is a dropdown listing the Focus On topics — when
adding a new topic, add a new section AND a link in the dropdown menu (`#focus-dropdown`).

## Common tasks

- **Update a bio**: find the clinician's `<div class="provider-card">` in `#providers`;
  the bio is inside `<details><div class="bio">`. (Spelling note: it's Carrie **Westbrook**.)
- **Add a news post**: copy an existing `<div class="post-card">` in `#news`.
- **Add a health article**: copy an `<div class="article-card">` in `#health-library`.
- **Change the announcement bar**: edit `.announce-text` near the top of `<body>`.
- **Add a "Focus On" topic**: copy an existing focus section (e.g. `#heat-exhaustion`), give it
  a new id, add it before the previous topics, and add its link to the nav dropdown
  (`#focus-dropdown`) — move the old "Current feature" kicker to the new one.
- **Photos**: optimized JPEGs in `assets/img/providers/` (~700px) and `assets/img/locations/`
  (~1200px). Compress before adding (`sips -s format jpeg -s formatOptions 80 -Z 700 in.png --out out.jpg`).
  Never inline images as base64.

## Design system (do not drift from it)

- Palette via CSS variables in `:root`: `--pine #24463F` (primary), `--gold #A97A2B` (accent),
  `--deepblue #1B3A5C` (info/billing thread), `--paper #F1F3EC` (ground).
- Type: Fraunces (display), Source Sans 3 (body), IBM Plex Mono (labels/eyebrows) via Google Fonts.
- Keep the flat/editorial look: 2px radii, 1px `--line` borders, mono uppercase eyebrows.
- Interactions (scroll reveal, scrollspy, back-to-top) are in the `<script>` at the bottom
  and respect `prefers-reduced-motion`.

## Facts to keep consistent (single source of truth)

- **Five locations** — four in Elizabethtown, one in Radcliff (stated in hero, fact strip,
  and `#locations`; keep all three in sync if it ever changes).
- FHH = **Family Healing and Health**, 5900 N Dixie Hwy.
- Phones: Quadri 270-769-0892 · Nasir 270-900-4555 · Ahmed 270-986-7392 · Psychiatry
  270-982-2002 · Labs 270-982-2027 · FHH 270-737-1215 · Movania (Radcliff) 270-351-3192 ·
  Billing office 270-982-2015.
- Patient portal (HEALOW): https://mycw104.ecwcloud.com/portal14112/jsp/login.jsp
- Founded 2016 (merger of the practices of Drs. Movania, Ahmed, Quadri, Nasir).
- Hours: Mon–Fri 8:00 AM – 5:00 PM. All insurances accepted; new patients welcome.

## Content cautions

- This is a medical practice site: keep health content educational, sourced (CDC etc.),
  and keep the Health Library disclaimer intact. No specific medical advice.
- Time-sensitive content to watch: the flu-vaccine announcement (dated Aug 1, 2026) in the
  announcement bar, `#news`, and `#patients`; and the seasonal `#focus-on` topic.
- `_previous-draft/` is an archived earlier multi-page version — ignore it; not deployed.
