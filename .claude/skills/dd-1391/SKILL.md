---
name: dd-1391
description: Camp Schwab DD Form 1391 architecture, PAX coding rules, and FSRM cost-estimate guardrails for the FY26 five-building portfolio (Bldg 1024, SCH-3213, SCH-3237, SCH-3270, SCH-3314). Covers Block 9 discipline-rollup architecture, the four PAX Associated Costs percentages, LSH/CM absorption rule, locked totals per building, working discipline, and verification gates. Use when working in this repo on Block 9, cost estimate workbooks, PAX submission text, or any handoff prep.
---

# Camp Schwab DD Form 1391 - Project Reference

Internal reference for the five-building Camp Schwab FY26 FSRM Straddler portfolio. Programmed in FY26 with the possibility of a Q1 FY27 award. Fund type O&MMC. Acquisition method Design-Build (DB) for all five.

## The load-bearing rule

**Total Project Cost as PAX renders the printed form must equal the locked Total Project Cost for that building.** The locked TPC is the largest dollar number on the cost estimate workbook for each building. Whatever the operator enters in the PAX items table plus the four Associated Costs percentages, when PAX rolls it up and prints the form, that printed TPC must equal the locked workbook TPC to the dollar (rounded to $000 on the printed face).

Every workbook is built backward from the locked TPC.

## Block 9 architecture (current)

Block 9 face follows the May 2024 CRB Guidelines line-item sequencing and mirrors the Camp Courtney Bldg 4207 cosmetic example (discipline-rollup style). The face shows one Primary Facility line keyed to the building CCN, area times unit cost on one line, no UNIFORMAT prefixes anywhere visible, no discipline-first line names that compete with the facility name, and rollup adders rendered as percentages below the items list rather than as discrete dollar lines.

```
PRIMARY FACILITY                                                     [P_TOTAL]
  [Building Name] (Conversion / Alteration)        SF | [GSF] | [PUC] | [P_LINE]
SUPPORTING FACILITIES                                                [S_TOTAL]
  [discipline rollup lines as needed: Site, ACM/LBP Abatement, etc.]
SUBTOTAL                                                             [SUBTOTAL]
CONTINGENCY (10.0%)                                                  [CONT]
TOTAL CONTRACT COST                                                  [TCC]
SUPERVISION, INSPECTION AND OVERHEAD (8.0%)                          [SIOH]
TOTAL FUNDED COST                                                    [TFC]
DESIGN-BUILD - DESIGN COST (4.0%)                                    [DBD]
TOTAL PROJECT COST                                                   [TPC]
TOTAL PROJECT COST (ROUNDED)                                         [TPC_R]
PLANNING AND DESIGN (6.0%) (NON ADD)                                 [PD]
EQUIPMENT FROM OTHER APPROPRIATIONS (NON ADD)                        [EOA]
```

## PAX entry model

**Items table (eight columns):** ID, Description, Classification of Work, Work Type, UM, Quantity, Unit Cost, Total Cost ($000). The first row is iNFADS-supplied and not operator-editable.

**Associated Costs dialog (four percent fields):** Contingency 10.0%, Supervision Inspection and Overhead 8.0%, Design Build 4.0% (required), Planning and Design 6.0%.

CM (4.0%) has no native PAX percent slot. CM dollars are absorbed into the discipline rollups in the items table.

## Absorption rule (LSH and CM)

LSH and CM dollars are absorbed into discipline rollups in the items table, not entered as discrete adder lines. Allocation logic is defensible-and-logical: doors to Architectural / Interior Construction, exit lighting and fire alarm to Electrical or Fire Protection, ACM/LBP abatement under Supporting Facilities as a discrete HAZMAT line.

**LSH provenance.** The 2.5%-of-PRV LSH allowance carries the weight of local direction at startup. The percentage is not published in any section of MCO 11000.5 (03 Jun 2016) or MCO 11000.12 (08 Sep 2014) that we can stand up. NAVFAC 11010.44E was inactivated by the 1987 issuance and is not citable. We preserve the dollar value by allocation, not by citation.

## Building inventory

| Building | Fi Web | PAX ID | RPUID | iNFADS Description | Primary CCN | GSF | Locked TPC ($) | LSH ($) | PRV ($) |
|----------|--------|--------|-------|--------------------|-------------|-----|---------------:|--------:|--------:|
| Bldg 1024 | BU26PPE70M | 387356 | 148675 | MULTI PURPOSE BEQ/BOQ/CO HQS | 14345 (verify vs printed 14346) | 84,861 | 10,413,140 | 2,413,084 | 96,523,347 |
| SCH-3213 | BU26PPE72M | 387624 | 48879 | COMPANY HQ | 61010 | 13,484 | 5,397,928 | 272,333 | 10,893,334 |
| SCH-3237 | BU26PPE73M | 387622 | 51473 | WAREHOUSE/ARMORY | 44112 | 30,973 | 1,455,526 | 665,905 | 26,636,215 |
| SCH-3270 | BU26PPE74M | 387568 | 1174058 | AUTO ORGANIZATIONAL SHOP CAB | 21451 | 25,390 | 3,527,753 | 987,690 | 39,507,617 |
| SCH-3314 | BU26PPE71M | 387433 | 50931 | BATTALION SQUADRON HEADQUARTERS | 61072 | 28,699 | 1,949,383 | 745,670 | 29,826,797 |

Portfolio Locked TPC: $22,743,730. All Fi Web suffixes are M (the R on a 3270 file copy is a clerical error).

## PAX rollup math (verify divisor at PAX entry)

```
TCC = Subtotal × 1.10   (Cont 10% of Subtotal)
TFC = TCC × 1.08        (SIOH 8% of TCC)
TPC = TFC × 1.04        (DBD 4% of TFC)
PD  = NON ADD           (P&D 6%, does not roll to TPC)
TPC = Subtotal × 1.23552
Subtotal target = Locked TPC / 1.23552
```

The workbook exposes the multiplier as a single switchable cell. Candidate multipliers if planning baseline does not render: 1.22 (flat-additive, P&D non-add), 1.2272, 1.28 (flat-additive, P&D added).

## Hard rules

- Parent line locked from iNFADS in PAX. Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
- No UNIFORMAT codes on Block 9 face.
- No discipline-first line names competing with the facility name.
- One Primary Facility line per building, area times unit cost on one line.
- LSH and CM absorbed into discipline rollups. No discrete LSH or CM lines.
- TPC preservation: every workbook reconciles to its locked TPC to the dollar.
- Em dashes banned. No version-history scaffolding inside files.

## Authority references

- **MCO 11000.5** (03 Jun 2016) - Real Property FSRM Program. Active.
- **MCO 11000.12** (08 Sep 2014) - Real Property Facilities Manual. Active.
- **CRB Guidelines May 2024 (REV #15)** - line-item sequencing for Block 9.
- **UFC 3-701-01 with Change 7** (25 Jul 2025) - PUC/ACF tables, Eq 3-1 PRV formula.
- **UFC 3-730-01** (2024) - design-build contracting.
- **JED Cost Estimating Guide** (Nov 2025).
- **Japan District Design Guide v9** (April 2025).
- **NAVFAC 11010.44E** - DO NOT CITE. Inactivated by 1987 issuance.

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

## Voice and constraints

- Plain prose preferred over heavy bullet structure.
- Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
- No em dashes. No double hyphens.
- No AI jargon. No "Claude" or "Apex Omega" framing in deliverables.
- Building IDs: Bldg 1024 for the worked example; SCH-#### for the other four.
- JPY/USD: planning rate 150.4415 per FY26 budget; H.10 live rate at submission.

## Personalities

- **CDR Justus K. O'Connor** - signing officer (PWO).
- **Bil Hawkins** P.E., PMP - Deputy PWO at MCB Camp Butler G-F. Anthony's government client.
- **Robert W. Kaye** RA - Planning Director, NAVFAC FEAD. Reviewer.
- **John Thurber** - NAVFAC HQ CI/MILCON, manual author, john.thurber@navy.mil, 202-685-9401.
- **Anthony L. Potter** - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor.
