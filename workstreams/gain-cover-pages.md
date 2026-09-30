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
| Cover images actually available | 3 (SharePoint `GAIN SDG Map & Outreach Resources/covers/`), none in this repo |
| Usable covers | 2 (`ex082` Mali INSTAT EMOP 2024; `ex322` Uganda UBOS National Governance, Peace and Security Survey 2024/25) |
| Rejected | `ex069`: not a cover (Jordan DoS publication price list) |
| `data/gain_example_links.csv` | **added on this branch**, rebuilt from `covers.html` and joined to the GAIN group roster |

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

- [ ] **Regenerate covers for the 37 examples with URLs.** PDF → render page 1 at about 400 px wide
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
