# Handoff prompt - Camp Schwab FY26 cost estimate workbooks

You are picking up an in-progress workbook rebuild for Anthony L. Potter (Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor at MCB Camp Butler G-F, Okinawa, Japan). All five DD Form 1391 cost estimate workbooks for the Camp Schwab FY26 portfolio have been built and pushed to remote. Do not rebuild from scratch. Iterate on what is there.

## Repository context

- GitHub repo: `CRYPTOKEYSAFE/DD_Form_1391-_Cost_Estimates`
- Active branch: `claude/rebuild-cost-estimate-workbook-NlO5b` (already checked out; do not switch unless directed)
- Working directory: `/home/user/DD_Form_1391-_Cost_Estimates/`
- Skill (read first): `.claude/skills/dd-1391/SKILL.md` - already in this branch, no fetch needed
- Generic builder: `scripts/build_all.py` - run with `python3 scripts/build_all.py` to regenerate any/all workbooks
- Last commit: `194cbda` - "Rebuild all five Schwab workbooks with single Primary Facility line; reconcile to locked TPC at $000 (delta 0)"

## What is built

| Building | Output file | Locked TPC ($) | Unit Cost ($/SF) | Workbook TPC ($000) | Match |
|----------|-------------|---------------:|-----------------:|--------------------:|:-----:|
| Bldg 1024 | `1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx` | 10,413,140 | 99.32 | 10,413 | ✓ |
| SCH-3213 | `3213_G_CEPBKUP_BU26PPE72M_POM26_20260320.xlsx` | 5,397,928 | 324.00 | 5,398 | ✓ |
| SCH-3237 | `3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx` | 1,455,526 | 38.04 | 1,456 | ✓ |
| SCH-3270 | `3270_G_CEPBKUP_BU26PPE74M_POM26_20260319.xlsx` | 3,527,753 | 112.46 | 3,528 | ✓ |
| SCH-3314 | `3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx` | 1,949,383 | 54.98 | 1,949 | ✓ |

All five reconcile to Locked TPC at $000 with delta = 0.

## The load-bearing rule

When Anthony enters the Unit Cost from each workbook into PAX (Block 9 Primary Facility line) with the four Associated Costs percentages already pre-loaded (Contingency 10%, SIOH 8%, Design Build 4%, Planning and Design 6% NON ADD), PAX must print a Total Project Cost equal to the Locked TPC for that building, rounded to $000. The workbook's TPC cell and the PAX-printed TPC must match.

This is verified mathematically in each workbook's BACKUP tab reconciliation panel.

## Architecture (all five workbooks identical)

Six tabs in this order: COVER, BLOCK9, BLOCK10, BACKUP, RATES, REFERENCES.

- **COVER** - identifiers, locked TPC, signature block
- **BLOCK9** - one Primary Facility line; no discipline sub-lines on the printed face; adders below
- **BLOCK10** - narrative pulled directly from each building's source 1391 PDF
- **BACKUP** - Locked TPC back-solver, multiplier cell, reconciliation panel
- **RATES** - four PAX percentages, ACF 1.85, JPY/USD planning rate 150.4415, escalation
- **REFERENCES** - MCO 11000.5, MCO 11000.12, CRB Guidelines May 2024, UFC 3-701-01 w/Ch 7, UFC 3-730-01, JED Cost Estimating Guide Nov 2025, JDDG v9

## Hard rules (do not violate)

1. ONE Primary Facility line per building. No discipline sub-lines on the printed Block 9 face.
2. LSH and CM dollars absorbed into the Unit Cost. No discrete LSH or CM lines on the face.
3. Supporting Facilities only if ACM/LBP applies. None of the five currently use it.
4. iNFADS-locked top row: Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
5. Four PAX Associated Costs percentages: Contingency 10%, SIOH 8% (OCONUS), Design Build 4%, Planning and Design 6% (NON ADD).
6. Multiplier 1.10 x 1.08 x 1.04 = 1.23552 is the default. Switchable in BACKUP cell B8 if directed.
7. NAVFAC 11010.44E DO NOT CITE - inactivated by 1987 issuance.
8. Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
9. No em dashes. No double hyphens. No AI jargon. No "Claude" or "Apex Omega" framing in deliverables.
10. Cosmetic baseline reference: Camp Courtney Bldg 4207 photos `IMG_0185.jpeg` through `IMG_0188.jpeg` for column layout, headers, percent-renders below items list. The DISCIPLINE BREAKDOWN visible on 4207 is OLD architecture and is NOT replicated.

## Working discipline

1. Single source of truth = `.claude/skills/dd-1391/SKILL.md`. Read it before editing.
2. Commit at logical boundaries with plain-language messages.
3. Push every commit. If `git push` fails 503, retry; fall back to `mcp__github__create_or_update_file` or `mcp__github__push_files`.
4. Update the skill when state changes.
5. No version-history scaffolding inside files (git is the version history).
6. No assumptions. Verify, or surface as open item.

## Likely next tasks

- Cosmetic refinements to BLOCK9 face to match 4207 layout more precisely
- Tighten BLOCK10 narrative formatting (page breaks, paragraph wrapping)
- Add Block 11 Requirement section if needed for PAX submission
- Add ACM/LBP Supporting Facilities line to specific buildings if confirmed
- Switch the multiplier cell to 1.22 / 1.2272 / 1.28 if PAX behavior changes

To rebuild any/all workbooks after edits to `scripts/build_all.py`:
```
python3 scripts/build_all.py
git add *.xlsx scripts/build_all.py
git commit -m "..."
git push -u origin claude/rebuild-cost-estimate-workbook-NlO5b
```

## Personalities

- **CDR Justus K. O'Connor** - signing officer (PWO)
- **Bil Hawkins** P.E., PMP - Deputy PWO at MCB Camp Butler G-F. Anthony's government client.
- **Robert W. Kaye** RA - Planning Director, NAVFAC FEAD. Reviewer who directed the single-line architecture.
- **Anthony L. Potter** - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor.

## Order of operations for next session

1. Read `.claude/skills/dd-1391/SKILL.md` end to end.
2. Open one workbook (suggest SCH-3270) in LibreOffice or Excel and inspect each tab.
3. Verify BACKUP tab reconciliation: Workbook TPC ($000) - Locked TPC ($000) = 0.
4. Take next direction from Anthony.
