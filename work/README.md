# UmojaServ case studies

Each case study is one folder under `/work/`, containing a single `index.html`:

```
work/rumi-cafe/index.html   →  https://umojaserv.com/work/rumi-cafe/
work/_TEMPLATE/index.html   →  starter, not linked or indexed
```

All of them share:

- `assets/css/case-study.css` — the whole visual system (`.cs-*` classes)
- `assets/js/case-study.js` — reveal-on-scroll + declarative analytics

Nothing is per-client except the HTML content. **Do not fork the stylesheet
per case study.** If a client needs something the template can't express, add
the component to `case-study.css` so every future case study gets it.

## Adding a new case study

1. `cp -R work/_TEMPLATE work/<client-slug>`
2. Fill in every `[[PLACEHOLDER]]` in `index.html`. Search for `[[` — if any
   are left, the page is not ready to publish.
3. Put images in `assets/images/case-studies/<client-slug>/`, exported as
   WebP, resized to the width they actually render at, with `width`/`height`
   attributes and `loading="lazy"` on everything below the fold.
4. Add the URL to `sitemap.xml`.
5. Add a results card to `#proof` in `index.html` and a card in
   `pages/ourprojects.html`, both linking to `/work/<client-slug>/`.

## The 14 blocks every case study can carry

Client · Industry · Location · Challenge · Baseline · UmojaServ system ·
Work completed · Results · Performance evidence · Screenshots ·
Customer journey · Related UmojaServ services · CTA · WhatsApp source tag

A case study may omit a block it has no real data for. It must never invent
one. Leave the reserved slot in place (`.cs-evidence-pending`,
`.cs-evidence-empty`) and publish it when the evidence exists.

## WhatsApp source tags

Every case study gets its own tag so leads can be attributed to the page that
produced them. The tag goes in square brackets at the *start* of the prefilled
message, and the whole message is URL-encoded.

| Page                  | Tag             |
|-----------------------|-----------------|
| Homepage              | `[WEB]`         |
| Floating chat button  | `[WEB-CHAT]`    |
| Pricing — closing CTA | `[WEB-PRICE]`   |
| Pricing — $100 Starter | `[WEB-PRICE-STARTER]` |
| Pricing — Level 1 Website Foundation | `[WEB-PRICE-FOUNDATION]` |
| Pricing — Level 2 Connected Business System | `[WEB-PRICE-CONNECTED]` |
| Pricing — Level 3 Business Automation | `[WEB-PRICE-AUTOMATION]` |
| FAQ                   | `[WEB-FAQ]`     |
| Google Business + AI  | `[WEB-GBP-AI]`  |
| Rumi Café case study  | `[CASE-RUMI]`   |
| Lash Lair case study  | `[WEB-CASE-LASHLAIR]` |
| Selectives Home Care case study | `[WEB-CASE-SELECTIVES]` |

New case studies use `[CASE-<CLIENT>]` (Lash Lair uses `[WEB-CASE-LASHLAIR]`, as requested).
Add each new tag to `SERVICES` in `assets/js/wa-track.js` and `TAG_SERVICES` in
`tools/apps-script/Intake.gs`. (The homepage links, including the
pricing tags, put the tag at the end of the message; either position works
as long as the tag is present.) The WhatsApp number never changes:
`255778337298`.

## Analytics

`case-study.js` reads three attributes off `<body>` and one off any link:

```html
<body data-cs-slug="rumi-cafe"
      data-cs-client="Rumi Café"
      data-cs-view-event="rumi_case_study_view">

<a data-cs-event="rumi_case_study_whatsapp_click" ...>
```

The view event fires once on load; every `data-cs-event` element pushes on
click. Each push carries `case_study` and `case_study_client`, so GTM can
report on all case studies together or one at a time. No new JavaScript is
needed for a new case study — only new attribute values.

Events on the Rumi page: `rumi_case_study_view`,
`rumi_case_study_whatsapp_click`, `rumi_case_study_start_click`,
`rumi_case_study_rumi_website_click`, `rumi_case_study_google_maps_click`.

## Claims policy

This is the part that matters most, because a case study is a public claim
about a real client's business.

- Publish a number only with a documented source. Say what the source is.
- **Check the baseline against evidence before publishing it.** The Rumi page
  originally ran a client-supplied "73 reviews → 95, +30%" baseline. Dated
  screenshots later showed the profile had actually started at 3 reviews,
  unclaimed and marked "Temporarily closed" — 73 was a mid-point, not a start.
  The real figure was both more accurate and far stronger. Ask for the earliest
  dated screenshot, not the earliest number someone remembers.
- Say what a metric *is*. Direction requests are direction requests — not
  customers, not visits, not sales.
- Never claim UmojaServ caused every unit of a metric. Use "during the period
  UmojaServ worked on…", "Google Business Profile recorded…", "review count
  increased from…".
- Never publish a Google Maps ranking position without a dated ranking check.
  Rankings move with location, query wording, personalisation, time and
  competition. Until a check exists the search term's status is "Monitored".
- Never mark up a client's rating as an `AggregateRating` for UmojaServ. The
  client's rating belongs to the client. On `/work/rumi-cafe/` the café is
  referenced as `about` on the Article, with no rating markup at all.
- Never fabricate screenshots, historical data or customer quotes.
