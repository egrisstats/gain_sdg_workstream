# GAIN SDG Workstream — context for Claude

Paste or attach this file (with the CSVs in `data/`) to give Claude the full picture.

## What this is
A living map of comparable **SDG indicators for forcibly displaced people** (refugees, IDPs,
stateless), drawn from **GAIN examples** (EGRISS). Public site:
https://mitrovif.github.io/gain_sdg_workstream/ · Repo: https://github.com/mitrovif/gain_sdg_workstream

## Scope rules (important when reasoning about the data)
- Only **GAIN examples**; **government/NSO-produced preferred**; **data year 2018+** (post-IRRS); **no humanitarian/NGO-only** data.
- Each value is **calc** (computed from microdata) or **rep** (extracted from an official report); none are estimated.
- Populations are kept **distinct** (refugee vs IDP vs stateless vs Palestinian refugees vs migrants — never conflated).
- **SDG 6.1.1**: safely-managed (E. coli-tested, MICS) is the strict value; elsewhere a **basic-water proxy** (microdata, marked with an asterisk) — the two are NOT comparable.

## Current coverage
- **27 countries · 110 SDG values (63 on the 14 EGRISS priority indicators) · 12 of 14 priority indicators · ~67% government-produced.**
- Producer mix: government 67% · UNHCR 22% · World Bank 5% · JIPS 5%.
- The 2 uncovered priority indicators: **4.1.1 foundational learning** and **16.b.1 equal treatment**.

## Data files (in `data/`)
- `gain_sdg_values_calculated.csv` — values computed from microdata (with host comparison + method).
- `gain_sdg_values_promoted.csv` — values extracted from official reports (source + population).
- `GAIN_SDG_methodology_record.md` — how each indicator was derived (see §12 on 6.1.1).
- `nso_census_targets.csv` — 28 NSO census/survey reach-out targets (office + specific ask).
- `mics_acquisition_targets.csv` — 10 MICS reach-out targets.

## Reach-out pipeline (management view)
38 targets to obtain more displaced-group SDG data: **28 NSO census/official surveys** (e.g. Jordan LFS →
informal employment 8.3.1; Armenia/Georgia/Djibouti/Chad/Sri Lanka/Ethiopia/Philippines censuses) and
**10 MICS** (Lebanon & Palestine already on the map; Libya microdata; Bangladesh camp instrument; etc.).
