# Handoff prompt - Camp Schwab FY26 cost estimate workbooks

You are picking up an in-progress workbook rebuild for Anthony L. Potter (Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor at MCB Camp Butler G-F, Okinawa, Japan). All five DD Form 1391 cost estimate workbooks for the Camp Schwab FY26 portfolio are built, reconciled to locked TPC at $000 (delta 0), and pushed to remote. Do not rebuild from scratch. Iterate on what is there.

## Repository context

- GitHub repo: `CRYPTOKEYSAFE/DD_Form_1391-_Cost_Estimates`
- Active branch: `claude/rebuild-cost-estimate-workbook-NlO5b` (already checked out; do not switch unless directed)
- Working directory: `/home/user/DD_Form_1391-_Cost_Estimates/`
- Skill (read first): `.claude/skills/dd-1391/SKILL.md`
- Generic builder: `scripts/build_all.py` - run with `python3 scripts/build_all.py` to regenerate all five workbooks; the script also runs verification (reconciliation delta and banned-string sweep) and prints a summary.
- Canonical scope data: `scripts/data/scope.json` - per-building line items, sections, UNIFORMAT II Lv2 codes.

## What is built

| Building | Output file | Locked TPC ($) | Items Subtotal Target ($000) | Workbook TPC ($000) |
|----------|-------------|---------------:|-----------------------------:|--------------------:|
| Bldg 1024 | `1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx` | 10,413,140 | 8,428 | 10,413 |
| SCH-3213 | `3213_G_CEPBKUP_BU26PPE72M_POM26_20260320.xlsx` | 5,397,928 | 4,369 | 5,398 |
| SCH-3237 | `3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx` | 1,455,526 | 1,178 | 1,456 |
| SCH-3270 | `3270_G_CEPBKUP_BU26PPE74M_POM26_20260319.xlsx` | 3,527,753 | 2,855 | 3,528 |
| SCH-3314 | `3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx` | 1,949,383 | 1,578 | 1,949 |

All five reconcile to Locked TPC at $000 with delta = 0.

## The load-bearing rule

When Anthony pastes the discipline rollups from each workbook's DD1391_BLOCK9 tab into PAX Block 9 items table, with the four Associated Costs percentages pre-loaded (Cont 10%, SIOH 8%, DB 4%, P&D 6% NON ADD), PAX prints a Total Project Cost equal to the Locked TPC for that building, rounded to $000.

Items Subtotal Target = Locked TPC / 1.23552 (1.10 x 1.08 x 1.04). P&D 6% NON ADD informational only.

## Architecture (all five workbooks identical)

Four tabs in this order: ESTIMATE, SCOPE_DETAIL, PARAMETERS, DD1391_BLOCK9.

- **ESTIMATE** - ROM formula chain, PAX rollup verification with reconciliation row, UNIFORMAT II Lv2 summary, methodology, version history.
- **SCOPE_DETAIL** - line-by-line scope items with UNIFORMAT II Lv2 codes; total at bottom.
- **PARAMETERS** - project ID, cost inputs (yellow user-input cells), PAX Associated Costs (informational), derived values including the live Cost Adjustment Factor, planning rates, active references.
- **DD1391_BLOCK9** - PAX paste sheet. Discipline rollups by UNIFORMAT II Lv2 group; Items Subtotal; PAX percentage rows (Cont, SIOH, DB); Total Project Cost; reconciliation row; P&D NON ADD; Classification of Work.

## Hard rules (do not violate)

1. Block 9 paste sheet uses discipline rollups by UNIFORMAT II Lv2 group. Number of rollup lines varies per building.
2. Cost Adjustment Factor in PARAMETERS is a live formula = ItemsSubtotalTarget / PreCalibrationSubtotal. It calibrates the chain to the locked TPC and absorbs base-cost adjustments distributed pro-rata across discipline rollups. Do not hardcode.
3. iNFADS-locked top row in PAX: Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
4. Four PAX Associated Costs percentages: Contingency 10%, SIOH 8% (OCONUS), DB 4%, P&D 6% NON ADD. Multiplier 1.23552.
5. Acronym: Design-Build is "DB" in user-facing labels.
6. Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
7. No em dashes. No double hyphens. No AI jargon. No "Claude" or "Apex Omega" framing in deliverables.
8. Cosmetic baseline reference: Camp Courtney Bldg 4207 photos `IMG_0185.jpeg` through `IMG_0188.jpeg`.

## Working discipline

1. Single source of truth = `.claude/skills/dd-1391/SKILL.md`. Read it before editing.
2. Commit at logical boundaries with plain-language messages.
3. Push every commit. If `git push` fails 503, retry; fall back to `mcp__github__create_or_update_file` or `mcp__github__push_files`.
4. Update the skill when state changes.
5. No version-history scaffolding inside files (git is the version history).
6. No assumptions. Verify, or surface as open item.

## Likely next tasks

- Cosmetic refinements to DD1391_BLOCK9 face to match Camp Courtney 4207 layout more precisely
- Add Block 11 Requirement narrative tab if needed for a specific building
- Adjust scope items in `scripts/data/scope.json` if site survey turns up new findings; rerun `python3 scripts/build_all.py`
- Extend `scripts/build_all.py` palette/format if the user requests style tweaks

To rebuild any/all workbooks after edits to `scripts/data/scope.json` or `scripts/build_all.py`:
```
python3 scripts/build_all.py
git add *.xlsx scripts/build_all.py scripts/data/scope.json
git commit -m "..."
git push -u origin claude/rebuild-cost-estimate-workbook-NlO5b
```

## Personalities

- **CDR Justus K. O'Connor** - signing officer (PWO)
- **Bil Hawkins** P.E., PMP - Deputy PWO at MCB Camp Butler G-F. Anthony's government client.
- **Robert W. Kaye** RA - Planning Director, NAVFAC FEAD. Reviewer.
- **Anthony L. Potter** - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor.

## Order of operations for next session

1. Read `.claude/skills/dd-1391/SKILL.md` end to end.
2. Open one workbook (suggest SCH-3270) in LibreOffice or Excel and inspect each tab.
3. Verify DD1391_BLOCK9 reconciliation row equals 0.
4. Take next direction from Anthony.
