# Questionnaire & variable guide — identifying displaced people and computing SDGs

For each reach‑out target: how the source **identifies** refugees / IDPs / stateless / returnees, and
which **SDG variables** it carries. Compiled from the held DDIs/codebooks (106 DDI + 104 variable CSVs),
the Bangladesh MICS7 microdata, the Jordan LFS questionnaire, and NSO/IHSN/IPUMS/World‑Bank metadata.
Nothing here is invented — variable names are transcribed from the actual instruments/codebooks.

## How displacement is identified (the variable families to look for)
1. **Direct status flag** — a categorical variable: IDP / host / returnee / refugee / non‑displaced (best).
2. **Country of origin / country of birth** + **year of arrival** (refugees, returnees).
3. **Reason for the last move** with a conflict/violence/HR‑violation/disaster/eviction option (forced displacement).
4. **Place of previous / usual residence N years ago** (IDPs, returnees).
5. **Citizenship** incl. an explicit **stateless** category; **protection status** (refugee, asylum‑seeker, temporary protection); **refugee/asylum documents**.
6. **Camp / site** locator, or a **sampling domain/stratum** for a displaced population (refugee inferred from domain).

---

## A. Held microdata with a CLEAN displacement flag — computable NOW (no reach‑out)
These carry a single variable classifying each case by displacement status, so SDGs can be cross‑tabulated
by status directly. ★ = one of the 38 reach‑out targets.

| Country | Dataset (id) | Displacement‑ID variable | Key SDG variables |
|---|---|---|---|
| ★ Burkina Faso | IDP & Host Communities Survey 2024 (`nada_1466`) | `typmen` = PDI/Hôte; +`s01q07e` refugee card, `s01q07f` stateless card, `s01q07g` asylum attestation; `s12q02` return intention | 8.5 `s06q04` occupation status; 2.1.2 `s05aq07` hunger‑no‑money; 1.4.2 `s06q07` pays rent |
| ★ Burkina Faso / ★ Cameroon | Livelihoods Beneficiary Survey 2023 (`microlib_1400`/`1402`) | `POC_or_Host` = Person‑of‑Concern / Host; `Camp` = camp/site | 4.1 `Education`; 8.5 `O1/O2_Unemployment` |
| ★ Cameroon | UNHCR CMR 2020 SEI (`microlib_379`) | `int_status_legal` legal status; `site_horssite` in/out‑site | 6.2.1 `impact_service2` lack of latrines |
| ★ Chad | Refugee‑camp Food/Cash PDM 2020 (`microlib_482`) | `typerefugies` refugee type | 7.1.1 `q616_elect` electricity spend; 8.5 `q718_ppocup` occupation; 2.1.2 `rcsi` coping index |
| Sudan | PBF Baseline (`nada_509`) | `dmh16_a/b/c` = non‑displaced / IDP / returned‑IDP (3‑way); `dmh3` returned refugees; `dmh15` forced to leave | 6.1.1 `ascsm5` water source; 6.2.1 `ascsm4` toilet; 7.1.1 `ascsm13` lighting; 2.1.2 `lvhd22` reduce meals; 1.4.2 `hlp26` tenure |
| Afghanistan | MSNA 2025 (`microlib_1398`) — richest single file | `current_displacement_status`; `refugee_returnee_country`; `last_displacement_reason` (armed conflict/violence/HR/disaster/eviction) | 6.2.1 `sanitation_facilities`; 7.1.1 `lighting_source`; 11.1.1 `num_rooms_house`,`housing_tenure_status`; 4.1 `school_attendance_all`,`literacy_15plus`; 16.9.1 `id_doc_birth_cert`; 8.3.1 `informal_sector_participation`; 2.1.2 `food_insufficiency_30days` |
| Afghanistan | CBPM 2024 (`microlib_8050`) | `Is_KI_IDP_Host_Community_Returnee_Refugee` (4‑way) | 6.1.1 water access; 6.2.1 toilet access; 7.1.1 electricity availability; 16.9.1 birth cert; 8.5 occupation; 1.4.2 title deed/customary |
| Ukraine | Returnees survey Feb 2024 (`nada_1277`) | `ret_type` returnee type; `time_displacement`; `time_arrival` | 7.1.1 `q69_6` electricity access; 4.1 `q4`/`q6_3` education; 8.5 `q65` main activity; 1.4.2 `q64` owned dwelling pre‑war |
| Zambia | Forced Displacement Survey 2025 (`nada_13952`) — full EGRISS instrument | `COO`/`origincntry` country of origin; `ID_17b` refugee cert; `Legal_asylum_cert`; `DH_12` reason left; `HH_21/25` parent refugee | 6.1.1 `BD01` water; 6.2.1 `SAN01` toilet; 7.1.1 `HE01` electricity, `HL03` lighting; 11.1.1 `HH14` rooms; education/employment/land modules |
| ★ Malawi | DHS 2024 (`nada_13930`) | `shcamps` refugee camps + `shv005` refugee weight (subsample); `v105` prev residence, `v173` country of birth, `v175` reason moved | 6.1.1 `hv201`/`hv204`; 6.2.1 `hv205`/`hv225`; 7.1.1 `hv206`; 11.1.1 `hv213‑216`; 16.9.1 `hv140`; 2.2.1 `ha2`/`ha3` (anthro); 1.4.2 `hv244`,`v745a/c` |
| ★ Uganda | Malaria Indicator Survey 2024‑25 (`nada_13931`) | `shrefugee` refugee settlements + `sv005` weight (subsample) | 6.1.1 `hv201`/`hv204`; 6.2.1 `hv205`; 7.1.1 `hv206`; 11.1.1 `hv213‑216` |

*(Weaker/partial held flags: Moldova SEIS refugee‑cert docs `nada_1227`; Afghanistan modules `microlib_1221/1419/1461`; Belgium `microlib_783`; Malaysia `microlib_812`. Libya MSNA 2021 `microlib_995` = DDI only, no variable list.)*

---

## B. MICS surveys — variables & displacement separability
**Standard MICS6/7 has NO displacement identifier** (confirmed: zero `born|migrat|displac|refug|nationalit|citizen`
hits in the Bangladesh MICS7 `hh.sav`/`hl.sav`). Displaced people are separable only via a **custom module**
or a **displacement sampling domain**. The only near‑standard hook is the Women's questionnaire birthplace
items **WB5A/WB6** (foreign‑born women 15–49 — a proxy).

**Standard SDG variables (confirmed against Bangladesh MICS7):**
- 6.1.1 water: `WS1`–`WS4` (source, location, time), `WS7` availability
- 6.2.1 sanitation: `WS11` toilet type, `WS15`–`WS17` shared
- 7.1.1 electricity: `HC8`/`HC8B`; 7.1.2 clean fuel: `EU1`/`EU4`/`EU9`
- 11.1.1 housing: `HC3` sleeping rooms, `HC4`/`HC5`/`HC6` floor/roof/wall, `HH48` members
- 4.1.2 education: `ED4`/`ED5`, `ED9`/`ED10`; **4.1.1 foundational learning: FL module**
- 16.9.1 birth registration: `BR1`/`BR2`
- 2.2.1 stunting: anthropometry (`hc70` height‑for‑age z‑score)

| MICS country | Displacement separability | Needs |
|---|---|---|
| Libya MICS7 2024‑25 | Custom **Internal Displacement module** (forced‑to‑flee / IDP vs returnee) — in microdata | request microdata |
| Lebanon Subnational 2023 | Separable via **sampling domains** (displaced‑Syrian settlements, Palestinian camps) — on the map | request full report/microdata for 4.1.1 |
| State of Palestine | Refugee‑affected frame; UNRWA/camp variable needed to separate registered refugees | custom variable/domain |
| Bangladesh MICS7 2025 | National frame **excludes Rohingya camps**; no displacement variable | separate Cox's Bazar / Bhasan Char camp survey |
| Mauritania, CAR, Cameroon, Burkina Faso, South Sudan, Zimbabwe | Standard MICS — displaced **not identifiable** without a custom module/stratum | request custom module or stratum |

---

## C. Jordan Labour Force Survey 2024 (held questionnaire, ex105)
Sample represents Jordanians **and non‑Jordanians**. Identification + informality questions (verbatim codes):
- **Nationality**: 1 Jordanian · 2 Egyptian · **3 Syrian** · **4 Iraqi** · 6 Non‑Arab.
- **Non‑Jordanian sub‑module** ("reason NAME came to live in Jordan"): **a. As refugee · b. As asylum seeker · c. For work · f. Other**; + country of birth, **country of previous residence**, **year of arrival**, age at arrival.
- Health‑insurance fund incl. **UNRWA** (refugee proxy).
- **8.3.1 informal employment**: social‑security contribution (yes‑now/yes‑before/no); **written vs oral vs no contract** + duration; employment status (employee/employer/own‑account/family worker); **establishment registered with Tax Authority/commercial registry**; keeps **written accounts**.
- **8.5.2 unemployment**: worked for pay last 7 days; actively looking (job‑search methods incl. public employment service); available to start; duration.

→ Requesting the **non‑Jordanian microdata** yields refugee 8.3.1 (informal) + 8.5.2 (unemployment) directly.

---

## D. Census questionnaires (NSO) — displacement‑ID + SDG variables
| Country (NSO) | Questionnaire | Displacement identification | SDG variables |
|---|---|---|---|
| **Moldova — NBS 2024** ✅ best | public (`Chestionare`) | **Explicit "forced displacement" migration‑reason** + **protection status (refugee/asylum/temp protection)** + year of arrival + previous residence (returnees) + **stateless** citizenship; refugee reception centres as collective quarters | standard PHC water/sanitation/dwelling/tenure/education/employment |
| **Kazakhstan — BNS 2021** ◑ partial | 4 forms public (stat.gov.kz) | Form **4‑В** flags **stateless + asylum‑seekers/foreigners**; main Form 3‑I = place of birth + citizenship only (no IDP/refugee item) | Form 2‑Ж housing (water/sanitation); 3‑I education/employment |
| **South Africa — Stats SA 2022** ◔ | request from Stats SA | Country of birth + citizenship + previous province + **reason for moving** → foreign‑born only, **no refugee/IDP question** | water, energy, dwelling, **tenure**, education (employment/services withheld from public 10%) |
| **Cambodia — NIS 2019/CIPS** ◔ | IPUMS (licensed) | Place of birth, **residence 1 yr ago (`MIGRATE1`)**, previous residence — migrants only, **no refugee/IDP** | utilities (water, electricity), dwelling, education, employment |
| **Mali — INSTAT RGPH5** ◔ | xlsx (DEMOSTAF/INED) | Emigration module + standard place of birth/nationality — **no refugee/IDP/returnee item** | housing characteristics + assets (item‑level not in online metadata) |
| **Armenia, Georgia, Djibouti, Chad, Côte d'Ivoire, Sri Lanka, Philippines, Indonesia, Kyrgyzstan, Azerbaijan, Belarus, Liberia, Kosovo, Iraq‑KRI, Mexico (ENADID/ENVIPE)** | request from NSO / IHSN‑IPUMS | Standard census/survey migration items (place of birth, previous residence, citizenship, reason for move); a few carry an explicit displaced/returnee item (Armenia = NK‑displaced in census; Djibouti/Chad/CIV/Liberia flag refugees/IDPs per GAIN). **Request the questionnaire + a custom tabulation by displacement status.** | Standard census SDG set: water source+time, toilet type, electricity/lighting, rooms/materials/**tenure**, school attendance/attainment, **birth registration**, employment/occupation |

*Ask each NSO for: (1) the questionnaire/codebook, and (2) a custom tabulation of the SDG variables above by the displacement‑status/protection variable.*

---

## E. EU register‑based NSOs (Germany, Netherlands, Norway, Poland, Slovenia, Liechtenstein)
Statistics come from **population + administrative registers**, not household questionnaires — so **no WASH/housing
micro‑data**. They identify refugees via **residence‑permit / protection‑status registers** (asylum, recognised
refugee, temporary/collective protection for Ukrainians; Norway's `innvandringsgrunn`=flukt; Poland's PESEL‑UKR),
linked to the population register.
→ Yields **employment/unemployment (8.5), education attainment (4.1.x), income & at‑risk‑of‑poverty (1.2/10)** by
protection status — **not** SDG 6/7/11. Ask for register‑linked tables by protection status.
