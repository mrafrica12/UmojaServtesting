# Rumi Café case study — images

All four **website showcase** slots are filled. The **Google Business Profile
evidence** slots are still reserved placeholders, because no GBP screenshots
exist in this repository yet and the page must not show anything that was not
actually captured.

Every slot holds a 16:10 box, so dropping a real file in causes **no layout
shift** and does not push the metrics around.

## Filled — website showcase (`Built around how customers actually browse`)

All exported at 1280×800, WebP q82. Total 224 KB for the four (down from
8.5 MB of PNG).

| File                    | What it shows                                                        |
|-------------------------|----------------------------------------------------------------------|
| `site-homepage.webp`    | Homepage hero — "Handcrafted African Coffee in the Heart of Kilimani", both CTAs, and the 4.9-on-Google / 95-reviews strip |
| `site-mobile.webp`      | The menu on a phone — Ginger Rush and prices above the fixed Home / Story / Menu / Directions / Contact bar |
| `site-ginger-rush.webp` | The Ginger Rush section — signature drink, KSh 350                    |
| `site-location.webp`    | "Find Rumi Café" — Titan Complex entrance, Chaka Road address, Get Directions |

Sources are the PNGs in the parent directory. The conversion: landscape
captures centre-cropped from ~1.75:1 to 16:10 (trims ~4% per side, verified
clear of content); the phone mockup is taller than the box, so it sits on a
blurred extension of itself rather than being cropped — the bottom nav bar is
the whole point of that shot.

## Filled — the baseline

| File                             | What it shows                                                   |
|----------------------------------|-----------------------------------------------------------------|
| `gbp-baseline-2026-05-10.webp`   | The listing on 10 May 2026 — 3 reviews, "Temporarily closed", "Claim this business", plus code PQ5R+H6P, phone +254 703 426695 |

Published in the **Where we started** section at its own aspect ratio rather
than in a 16:10 box, because it is a tall phone screenshot and cropping it
would lose the "Temporarily closed" line that makes it evidence.

## Held back — undated

These are converted and ready, but **not published**, because their capture
dates are not confirmed. A review count with no date cannot sit on a timeline.
Add the dates and they can go into the evidence section.

| File                       | What it shows                       | Needs        |
|----------------------------|-------------------------------------|--------------|
| `gbp-reviews-71.webp`      | 4.9 ★ (71), Hurlingham Estate        | capture date |
| `gbp-reviews-75.webp`      | 4.9 ★ (75), Titan Complex Chaka Rd   | capture date |
| `gbp-owner-dashboard.webp` | Owner view — 70 customer interactions, 43 new reviews | decide whether to publish an owner-only screen at all |

Two numbers on the owner dashboard are easy to misread and should not be
presented as results: **"43 new reviews"** is an unread-notification count,
not a total or a delta; **"70 customer interactions"** is its own metric over
its own window and is not interchangeable with the 102 direction requests.

## Not published — marketing graphic

| File                               | What it is                                                   |
|------------------------------------|--------------------------------------------------------------|
| `umojaserv-performance-card.webp`  | UmojaServ social graphic: Rumi profile card + "Performance Apr 2026 – Sep 2026: 3.5K views, 212 interactions, 32 searches" |

The **numbers** from this graphic are published, rendered as live text in the
`.cs-perf` block. The **graphic** is not, and shouldn't be cropped into the
evidence slots:

- It is a designed UmojaServ asset, not a Google screenshot. The evidence
  section's whole claim is that it shows raw Google data; a cropped marketing
  tile presented there would quietly break that.
- Cropped raster text goes soft on a phone. Live text stays sharp, selectable,
  translatable and readable by a screen reader.

Keep it for social and decks. It is a good asset — just not evidence.

## Filled — performance evidence

Unedited Google Business Profile Performance dashboard captures, with the
`Apr 2026–Sep 2026` time-period selector visible in frame. This is what the
evidence section is for.

| File                                | What it shows                                        |
|-------------------------------------|------------------------------------------------------|
| `gbp-overview-apr-sep-2026.webp`    | Overview tab — **255** Business Profile interactions  |
| `gbp-directions-apr-sep-2026.webp`  | Directions tab — **207** direction requests           |

Both charts are flat through April and May, then climb from June — the profile
was claimed and the "Temporarily closed" status corrected around 10 May 2026,
so the inflection point is the story.

### These superseded two earlier figures

| Was on the page          | Source                          | Now                                  |
|--------------------------|----------------------------------|--------------------------------------|
| 212 interactions         | UmojaServ marketing graphic      | **255** (dashboard)                  |
| 102 direction requests / 29 days | unsourced                | **207** / Apr–Sep 2026 (dashboard)   |

Two figures from the marketing graphic — **3.5K views** and **32 searches** —
were removed and not replaced. That graphic's interaction count was wrong by 43,
so its other numbers are not trusted until a dashboard capture confirms them.

## Still to capture

| Suggested filename          | What it must show                                                    |
|-----------------------------|----------------------------------------------------------------------|
| `gbp-views-apr-sep-2026.webp` | The views figure, from the dashboard rather than the marketing card |
| `gbp-searches-apr-sep-2026.webp` | The searches figure, same                                        |
| `ranking-<term>-<date>.webp`| A dated local ranking check                                          |

## Publishing one

Replace the placeholder `<div class="cs-evidence-pending">…</div>` in
`work/rumi-cafe/index.html` with:

```html
<img src="/assets/images/case-studies/rumi-cafe/gbp-directions-29d.webp"
     alt="Google Business Profile showing 102 direction requests over 29 days"
     width="1280" height="800" loading="lazy" decoding="async">
```

Then update the `figcaption` to state the real capture date, and bump
`article:modified_time` plus `dateModified` in the JSON-LD.

## Rules

- Export WebP (or AVIF), at the width it actually renders — roughly 720px for
  a single-column phone, 1280px for the two-up desktop grid. Don't ship a
  3000px screenshot.
- Always set `width`/`height` and `loading="lazy"` — everything here is below
  the fold.
- Screenshots must be real, unedited captures of Rumi's actual Google Business
  Profile or website. Redacting a private detail is fine; changing a number is
  not.
- A screenshot with no visible date is not evidence. Capture the date range in
  the frame, or state it in the caption.
- The baseline slot stays empty unless a genuine archived screenshot turns up.
  Do not recreate it from memory.

## Review-count readings (keep adding, never overwrite)

| Date | Reviews | Rating | Source |
|---|---|---|---|
| 10 May 2026 | 3 | 5.0 | `gbp-baseline-2026-05-10.webp` — unclaimed, "Temporarily closed" |
| 23 Sep 2026 | 95 | 4.9 | Google Maps, verified in session |
| 23 Sep 2026 (later) | 97 | 4.9 | Google Maps, re-verified — 90 × 5★, 4 × 4★, 3 × 3★ |
| 25 Sep 2026 | 100 | 4.9 | Google Search knowledge panel, verified in session; owner's GBP screenshot `Rumi_Cafe_Review 100(1).png` (not yet in the repo) |
| 13 Oct 2026 | 112 | 4.9 | Google Search, verified. Screenshot `gbp-search-2026-10-13.webp` (600×409, unedited), published after the timeline |

The homepage and cards show the latest reading (3 → 112, +109). The case study
timeline keeps every dated reading. When the count changes again, add a row
here and a `<li>` to the timeline — do not edit the old rows.

## Moved out (2026-09-24)

Not used on any page, so moved to `Deleted/assets/images/case-studies/rumi-cafe/`
during the pre-launch optimisation pass: `gbp-owner-dashboard.webp`,
`gbp-reviews-71.webp`, `gbp-reviews-75.webp` (still need capture dates before
they can be used as evidence) and `umojaserv-performance-card.webp` (a designed
promo graphic, not evidence). Move one back here if a page starts using it.
Full-size originals of the images resized in that pass are in
`Deleted/originals-2026-09-24/`.

## Filled — website performance (25 Sep 2026)

Unedited Google PageSpeed Insights mobile reports for rumicafe.co.ke, both
dated in frame. Copied byte-for-byte from the supplied files (already 510 px
wide and ~20 KB — recompressing would only soften the text). Originals kept at
`assets/images/gallery/before_optimazation_thumbnail.webp` and
`after_optimazation_thumbnail.webp`.

| File                           | What it shows                                                  |
|--------------------------------|----------------------------------------------------------------|
| `rumi-performance-before.webp` | 11:26 AM EDT — Performance 72, A11y 98, BP 96, SEO 100; FCP 3.8 s, LCP 4.6 s, TBT 0 ms, CLS 0, SI 5.2 s |
| `rumi-performance-after.webp`  | 2:59 PM EDT — Performance 90, A11y 100, BP 96, SEO 100; FCP 1.7 s, LCP 3.5 s, TBT 0 ms, CLS 0.005, SI 2.0 s |

Lab data only (Lighthouse 13.5.0, Moto G Power, slow 4G). PageSpeed reported
no real-user field data, so never call these Core Web Vitals results. The
change is **18 points**, not 18 %. The "What changed" list on the page comes
from the Rumi repo (`Rumi Cafe/Rumi Web Page`, commit `ac784d0`,
`PERFORMANCE.md`) — its local-harness figures (98–99) are *not* published;
only the live PageSpeed runs are.

## Still to add — 100-review screenshot

`rumi-google-reviews-100.webp` has ready-made markup, commented out, in the
"From 3 Google reviews to 100" section (an empty placeholder filled a whole
phone screen, so nothing renders until the image exists). The source PNG was not in the repo when the page was
updated. Put the PNG in this folder, then:

```bash
python3 -c "from PIL import Image; im=Image.open('Rumi_Cafe_Review 100(1).png').convert('RGB'); im.thumbnail((720,4000)); im.save('rumi-google-reviews-100.webp','WEBP',quality=85,method=6); print(im.size)"
```

Un-comment that block, put the printed width/height on the `<img>` (alt text
and lazy loading are already set), and move the review timeline `<ol>` inside
the `.cs-before` wrapper beside the figure. Keep the PNG
(move it to `Deleted/` rather than uploading it). The 5,192 views figure in
that screenshot has no known reporting period — don't quote it.
