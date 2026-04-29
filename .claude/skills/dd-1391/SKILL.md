---
name: dd-1391
description: Camp Schwab DD Form 1391 architecture, PAX coding rules, and FSRM cost-estimate guardrails for the FY26 five-building portfolio (Bldg 1024, SCH-3213, SCH-3237, SCH-3270, SCH-3314). Covers Block 9 discipline-rollup architecture, the four PAX Associated Costs percentages, the Cost Adjustment Factor reconciliation, locked totals per building, working discipline, and verification gates. Use when working in this repo on Block 9, cost estimate workbooks, PAX submission text, or any handoff prep.
---

# Camp Schwab DD Form 1391 - Project Reference

Internal reference for the five-building Camp Schwab FY26 FSRM Straddler portfolio. Programmed in FY26 with the possibility of a Q1 FY27 award. Fund type O&MMC. Acquisition method Design-Build (DB) for all five.

## The load-bearing rule

When the user pastes the Block 9 discipline rollups into PAX with the four pre-loaded Associated Costs percentages (Cont 10%, SIOH 8%, DB 4%, P&D 6% NON ADD), PAX must print a Total Project Cost equal to the locked TPC for that building, rounded to $000. The workbook's TPC and the PAX-printed TPC must match.

Every workbook is built backward from the locked TPC. The Items Subtotal target = LockedTPC / 1.23552 (1.10 x 1.08 x 1.04). P&D 6% is NON ADD, informational only.

## Block 9 architecture

The Block 9 paste sheet shows discipline rollups by UNIFORMAT II Lv2 group. The user types these into the PAX Block 9 items table; PAX applies the four Associated Costs percentages and prints the form. The number of discipline rollup lines varies by building (4 to 11) depending on which UNIFORMAT II Lv2 categories appear in that building's scope.

```
DD FORM 1391 BLOCK 9 - PAX PASTE
  [discipline rollups, one per UNIFORMAT II Lv2 group]      [$000]
  ...
  ITEMS SUBTOTAL (PAX Block 9 paste total)                   [SUB]

  Contingency (10.0%)  PAX-applied                           [CONT]
  Total Contract Cost                                         [TCC]
  SIOH (8.0%)  PAX-applied                                   [SIOH]
  Total Funded Cost                                           [TFC]
  DB Design (4.0%)  PAX-applied                              [DBD]
  TOTAL PROJECT COST                                          [TPC]
  TOTAL PROJECT COST ($000 rounded)                           [TPC_R]
  Planning and Design (6.0%)  NON ADD                         [PD]
  Reconciliation (must equal 0)                                  0

CLASSIFICATION OF WORK
  Construction                                                100%
  Special Interest: Restoration and Modernization             100%
```

## PAX entry model

**Items table (eight columns):** ID, Description, Classification of Work, Work Type, UM, Quantity, Unit Cost, Total Cost ($000). The first row is iNFADS-supplied and not operator-editable.

**Associated Costs dialog (four percent fields):** Contingency 10.0%, Supervision Inspection and Overhead 8.0% (OCONUS FSRM customer-directed), Design-Build Design 4.0% (required), Planning and Design 6.0% NON ADD.

## Cost Adjustment Factor (reconciliation knob)

The PARAMETERS tab carries one live calibration cell labeled "Cost Adjustment Factor". Formula: `= ItemsSubtotalTarget / PreCalibrationSubtotal`, where `ItemsSubtotalTarget = LockedTPC / 1.23552` and `PreCalibrationSubtotal = BaseDirect x ACF x Escalation x (1 + GeneralRequirements)`. The factor scales the discipline rollups so that their sum equals the items subtotal target. Each discipline rollup formula in DD1391_BLOCK9 multiplies its UNIFORMAT-grouped base direct by ACF, escalation, (1 + GR), and the Cost Adjustment Factor before dividing by 1000 and rounding to $000. The factor implicitly absorbs base-cost adjustments distributed pro-rata across all disciplines. The factor name and labels in the workbook do not reference any specific allowance category.

## Building inventory and PAX entry calibration

| Building | Fi Web | PAX ID | RPUID | iNFADS Description | Primary CCN | GSF | Locked TPC ($) | Items Subtotal Target ($000) | Locked TPC ($000) |
|----------|--------|--------|-------|--------------------|-------------|----:|---------------:|-----------------------------:|------------------:|
| Bldg 1024 | BU26PPE70M | 387356 | 148675 | MULTI PURPOSE BEQ/BOQ/CO HQS | 14345 | 84,861 | 10,413,140 | 8,428 | 10,413 |
| SCH-3213 | BU26PPE72M | 387624 | 48879 | COMPANY HQ | 61010 | 13,484 | 5,397,928 | 4,369 | 5,398 |
| SCH-3237 | BU26PPE73M | 387622 | 51473 | WAREHOUSE/ARMORY | 44112 | 30,973 | 1,455,526 | 1,178 | 1,456 |
| SCH-3270 | BU26PPE74M | 387568 | 1174058 | AUTO ORGANIZATIONAL SHOP CAB | 21451 | 25,390 | 3,527,753 | 2,855 | 3,528 |
| SCH-3314 | BU26PPE71M | 387433 | 50931 | BATTALION SQUADRON HEADQUARTERS | 61072 | 28,699 | 1,949,383 | 1,578 | 1,949 |

Portfolio Locked TPC: $22,743,730. All Fi Web suffixes are M. Items Subtotal Target = LockedTPC / 1.23552, rounded to $000; this is the value the discipline rollups must sum to before PAX percentages are applied.

## PAX rollup math

```
TCC = Items Subtotal x 1.10   (Cont 10% PAX-applied)
TFC = TCC x 1.08              (SIOH 8% PAX-applied)
TPC = TFC x 1.04              (DB 4% PAX-applied)
PD  = Items Subtotal x 0.06   (NON ADD; informational only)
TPC = Items Subtotal x 1.23552
Items Subtotal Target = LockedTPC / 1.23552
```

All five buildings reconcile delta = 0 at $000 at multiplier 1.23552.

## Hard rules

- Parent line locked from iNFADS in PAX. Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
- Block 9 paste sheet uses discipline rollups by UNIFORMAT II Lv2 group. Number of rollup lines varies by building.
- Cost Adjustment Factor in PARAMETERS calibrates the chain to the locked TPC. The factor is a live formula; do not hardcode.
- TPC preservation: every workbook reconciles to its locked TPC at $000.
- Em dashes banned. No version-history scaffolding inside files.
- Use "DB" not "DBD" in user-facing labels for Design-Build.

## Authority references

- **MCO 11000.5** (03 Jun 2016) - Real Property FSRM Program. Active.
- **MCO 11000.12** (08 Sep 2014) - Real Property Facilities Manual. Active.
- **CRB Guidelines May 2024 (REV #15)** - line-item sequencing for Block 9.
- **UFC 3-701-01 with Change 7** (25 Jul 2025) - PUC/ACF tables, PRV formula.
- **UFC 3-730-01** (2024) - design-build contracting.
- **UFS 3-740-05** (02 Feb 2026) - cost estimating ROM levels.
- **JED Cost Estimating Guidance** (Combined, Nov 2025).
- **Japan District Design Guide v9** (April 2025).
- **10 U.S.C. Section 2802** and **DoD 4270.5-M** - Classification of Work.

## Working discipline (eight measures)

1. Single source of truth = this skill file.
2. Commit at logical boundaries with plain-language messages.
3. Push every commit. If `git push` fails 503, use `mcp__github__create_or_update_file` or `mcp__github__push_files` as bypass. Verify with `git log origin/<branch>..HEAD` empty.
4. Deliverables manifest in the file map below.
5. No version-history scaffolding inside files.
6. Pre-handoff checklist: working tree clean, commits pushed, skill current, deliverables list current, no stale files.
7. TodoWrite for in-session work over five steps.
8. Handoff prompt regenerated each time, not edited.

## Repository file map

- `/Consistency Review Board 1391 Development Guidelines 22 May 2024 Edition.pdf` - the manual
- `/M67400_BU26PPE70M_2026.pdf` - signed FY 2026 1391 for Bldg 1024
- `/IMG_0179.jpeg` - PAX Block 9 Data screen
- `/ASSOCIATED_COSTS.png` - PAX Associated Costs dialog
- `/IMG_0185-0188.jpeg` - Camp Courtney Bldg 4207 cosmetic baseline
- `/[1024|3213|3237|3270|3314].pdf` - five recent 1391 PDFs (gitignored)
- `/[1024|3213|3237|3270|3314]_G_CEPBKUP_BU26PPE##M_POM26_*.xlsx` - five CEPBKUP workbooks (rebuild target)
- `/scripts/build_all.py` - generic workbook builder (run with `python3 scripts/build_all.py`)
- `/scripts/data/scope.json` - canonical scope data per building (line items, sections, UNIFORMAT II Lv2 codes)
- `/JED_Cost_Estimating_Guidance_Combined_2025_Nov.pdf` (gitignored)
- `/Japan District Design Guide_v9_APRIL2025 (508 Compliant).pdf` (gitignored)
- `/ufc_3_701_01_2022_c7.pdf` and supporting xlsx (gitignored)
- `/ufs_3_701_01_2026.pdf` (gitignored)
- `/dod-cost-estimating-SKILL.md` (gitignored)
- `/deliverables/04_EMAIL_TO_KAYE_*` - sent email to Rob Kaye
- `/deliverables/04b_EMAIL_TO_KAYE_REPLY_*` - sent reply
- `/deliverables/PAX_1391_Coding_Walkthrough_SCH-1024.docx` - email attachment
- `/deliverables/PAX_BLOCK9_FLOW_AND_BEFORE_AFTER.png` - email attachment
- `/deliverables/06_HANDOFF_PROMPT.md` - workbook rebuild handoff
- `/working/` - OCR output, workbook dumps (gitignored)

## Workbook architecture (all five identical)

Four tabs in this order: ESTIMATE, SCOPE_DETAIL, PARAMETERS, DD1391_BLOCK9.

- **ESTIMATE** - ROM formula chain (Base Direct -> ACF -> Escalation -> GR -> Cost Adjustment Factor -> Items Subtotal), PAX rollup verification (Items Subtotal -> Cont -> TCC -> SIOH -> TFC -> DB -> TPC, Reconciliation row), UNIFORMAT II Lv2 summary, methodology, version history.
- **SCOPE_DETAIL** - line-by-line scope (Item, Group, Description, Qty, Unit, Unit Cost FY24 CONUS, Extended Cost = Qty x Unit Cost, UNIFORMAT II Lv2, Notes). Section group headers retained. Total Base Direct Cost row at the bottom.
- **PARAMETERS** - project identification, cost inputs (yellow user-input cells), PAX Associated Costs (informational), derived values (Compound Escalation Factor, Base Direct, Pre-Calibration Subtotal, Locked TPC, Items Subtotal Target, Cost Adjustment Factor), planning rates (JPY/USD 150.4415), active references.
- **DD1391_BLOCK9** - the PAX paste sheet. Discipline rollups by UNIFORMAT II Lv2 group; Items Subtotal; PAX percentage rows; Total Project Cost; reconciliation row; P&D NON ADD informational; Classification of Work.

## Voice and constraints

- Plain prose preferred over heavy bullet structure.
- Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
- No em dashes. No double hyphens.
- No AI jargon. No "Claude" or "Apex Omega" framing in deliverables.
- Building IDs: Bldg 1024 for the worked example; SCH-#### for the other four.
- JPY/USD: planning rate 150.4415 per FY26 budget; H.10 live rate at submission.
- Acronym: Design-Build is "DB" in user-facing labels.

## Personalities

- **CDR Justus K. O'Connor** - signing officer (PWO).
- **Bil Hawkins** P.E., PMP - Deputy PWO at MCB Camp Butler G-F. Anthony's government client.
- **Robert W. Kaye** RA - Planning Director, NAVFAC FEAD. Reviewer.
- **John Thurber** - NAVFAC HQ CI/MILCON, manual author, john.thurber@navy.mil, 202-685-9401.
- **Anthony L. Potter** - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor.
