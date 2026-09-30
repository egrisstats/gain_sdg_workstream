# Workstream: GAIN example cover pages and source links

**Status:** open · **Owner:** EGRISS Secretariat (GAIN) · **Started:** 2026-09-30

## Why

GAIN examples are easier to trust and reuse when a reader can see the report behind them.
Cover thumbnails and working source links feed three products:

1. **This SDG map**: the ✻ GAIN-example cards can show the report cover and link to the source.
2. **"Counted, and counting"**, the GAIN 2021–2025 scrollytelling page: every point of light opens
   a standard pop-up card, which now shows a cover thumbnail and an *Open the source ↗* link where
   one exists.
3. **Outreach**: covers make the "your work is in the global record" message concrete when
   contacting NSOs for the next GAIN round.

## Where things stand

| Item | State |
|---|---|
| Examples with a cover card in `covers.html` | 94 |
| … of which with a source URL | 37 |
| Usable covers in `covers/` (checked by eye) | **9** |
| Rejected after checking | 10 (logos, icons, stock photos, an inner yearbook page, a price list) |
| Still missing | 75 (57 without a URL; 18 links that failed or had no preview image) |

**Covers in use:** `ex007` Kazakhstan population report · `ex082` Mali INSTAT EMOP 2024 ·
`ex105` Jordan LFS 2024 questionnaire (first page) · `ex111` Statistics Norway asylum-migration note ·
`ex114` UNHCR, *From Stateless to Citizens* (Kenya) · `ex204` Colombia Victims Unit data portal ·
`ex307` Belize 2022 Census migration report · `ex322` Uganda UBOS Governance, Peace and Security Survey 2024/25 ·
`ex327` Kosovo 2024 census report.

**First pass (30 Sep 2026):** `tools/fetch_covers.py` ran over the 37 links; results are in
`data/cover_fetch_log.csv`. Why 18 links gave nothing: 403 blocks (unece.org, iadb.org, unrwa.org),
404s (gouv.ci, stat.gov.pl), timeouts (knbs.or.ke, pcbs.gov.ps), a private Google Drive file, and
landing pages without a preview image (ons.gov.uk, dosweb.dos.gov.jo, inegi.org.mx, instad.dj, insee.fr).
Web-page previews need extra care: Statistics Norway's are stock photos, not report covers.

**ID convention:** `exNNN` is the 1-based row in `analysis_ready_group_roster.csv`
(e.g. `ex113` = row 113 = Burkina Faso INSD, socio-economic survey of IDP and host households).

## `data/gain_example_links.csv`

| Column | Meaning |
|---|---|
| `ex_id`, `roster_row` | Example ID and its row in the GAIN group roster |
| `gain_year`, `country`, `organisation`, `title` | From the roster / cover card |
| `lead` | `country` or `institution` (Table 1.1 definition) |
| `uses_recommendations` | `yes` / `no/dk` (roster `PRO09`) |
| `source_url` | Public link to the report or page, when known |
| `cover_file` | `covers/exNNN.png` once a checked cover exists |
| `cover_status` | `ok` · `missing: …` · `rejected: …` |

Suggested extra columns as the work progresses: `url_found_by` (respondent / web search / NSO site),
`checked_by`, `checked_on`.

## Tasks

- [x] **First pass over the 37 examples with URLs** (9 usable covers; see above).
- [ ] **Retry the 18 failed links** by hand in a browser (403/timeout sites), or replace landing pages with the specific publication.
- [ ] ~~Regenerate covers for the 37 examples with URLs.~~ PDF → render page 1 at about 400 px wide
      (e.g. PyMuPDF) → `covers/exNNN.png`. For HTML pages use the page's `og:image` or a screenshot
      of the report landing page.
- [ ] **Find sources for the 57 examples without URLs.** Search by title + organisation + country
      on the NSO website, the UNHCR Microdata Library, the World Bank Microdata Library and a general
      web search. Record the URL and how it was found.
- [ ] **Extend beyond the 94.** The GAIN 2021–2025 roster holds 413 examples. Prioritise
      (1) examples on the SDG map (government-produced, data year 2018+), and
      (2) examples featured in the scrollytelling story (Burkina Faso INSD, Nigeria NBS,
      Philippines PSA, Belgium, Kazakhstan census, Uganda 2024 census, Thailand LFS migration module,
      African Union school).
- [ ] **QA every cover by eye** before it is published. Reject anything that is not the report's
      cover (see `ex069`), and set `cover_status`.
- [ ] **Rights check with Secretariat comms.** Covers are shown as small thumbnails of public reports,
      always linked to the source and credited to the producer; confirm this is acceptable, and keep
      photo credits (e.g. © UNHCR) verbatim.
- [ ] **Wire up**: add covers to the SDG map cards; add each new cover to the scrollytelling pop-ups.
- [ ] **Ask at source:** add an optional "link to report / upload cover" field to the next GAIN
      questionnaire, so respondents supply it directly.

## Notes

- Do not store microdata or restricted reports here, only public links and cover thumbnails.
- Link checks: several URLs point to landing pages rather than the report itself
  (e.g. `ons.gov.uk/peoplepopulationandcommunity/`); replace them with the specific publication where possible.
