# Handoff - Camp Schwab FY26 cost estimate workbooks

User: Anthony L. Potter, Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor at MCB Camp Butler G-F, Okinawa.

Status: all five FY26 cost estimate workbooks built, reconciled to locked TPC at $000 (delta 0), committed, and pushed. Iterate on what is there. Do not rebuild from scratch.

## Repository

- Repo: `CRYPTOKEYSAFE/DD_Form_1391-_Cost_Estimates`
- Branch: `claude/rebuild-cost-estimate-workbook-NlO5b` (already checked out; do not switch)
- CWD: `/home/user/DD_Form_1391-_Cost_Estimates/`
- Skill: `.claude/skills/dd-1391/SKILL.md` - read first
- Builder: `scripts/build_all.py` - run with `python3 scripts/build_all.py`; rebuilds all five and prints reconciliation + banned-string sweep
- Scope source: `scripts/data/scope.json` - canonical per-building line items, sections, UNIFORMAT II Lv2 codes

## Reconciliation

| Building | File | Locked TPC ($) | Items Subtotal Target ($000) | Workbook TPC ($000) | Δ |
|---|---|---:|---:|---:|---:|
| Bldg 1024 | `1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx` | 10,413,140 | 8,428 | 10,413 | 0 |
| SCH-3213 | `3213_G_CEPBKUP_BU26PPE72M_POM26_20260320.xlsx` | 5,397,928 | 4,369 | 5,398 | 0 |
| SCH-3237 | `3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx` | 1,455,526 | 1,178 | 1,456 | 0 |
| SCH-3270 | `3270_G_CEPBKUP_BU26PPE74M_POM26_20260319.xlsx` | 3,527,753 | 2,855 | 3,528 | 0 |
| SCH-3314 | `3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx` | 1,949,383 | 1,578 | 1,949 | 0 |

Portfolio Locked TPC: $22,743,730.

## Load-bearing rule

Anthony pastes each workbook's DD1391_BLOCK9 discipline rollups into the PAX Block 9 items table. PAX applies the four pre-loaded Associated Costs percentages and prints the form. Printed TPC must equal Locked TPC at $000.

```
Items Subtotal Target = Locked TPC / 1.23552  (1.10 x 1.08 x 1.04)
TCC = Items Subtotal x 1.10   (Cont 10% PAX-applied)
TFC = TCC x 1.08              (SIOH 8% PAX-applied)
TPC = TFC x 1.04              (DB 4% PAX-applied)
PD  = Items Subtotal x 0.06   (NON ADD; informational only)
```

## Architecture (all five identical)

Four tabs in order: ESTIMATE, SCOPE_DETAIL, PARAMETERS, DD1391_BLOCK9.

- ESTIMATE - ROM chain, PAX rollup verification with reconciliation row, UNIFORMAT II Lv2 summary, methodology, version history.
- SCOPE_DETAIL - line-by-line scope (Qty x Unit Cost extended), UNIFORMAT II Lv2 codes, total at bottom.
- PARAMETERS - project ID, cost inputs (yellow user-input), PAX Associated Costs (informational), derived values, Cost Adjustment Factor (live formula), planning rates, active references.
- DD1391_BLOCK9 - PAX paste sheet. Discipline rollups by UNIFORMAT II Lv2 group; Items Subtotal; PAX percentage rows (Cont 10%, SIOH 8%, DB 4%); Total Project Cost; reconciliation row; P&D 6% NON ADD; Classification of Work.

## Hard rules

1. Block 9 paste sheet uses discipline rollups by UNIFORMAT II Lv2 group. Number of lines varies per building (4 to 11).
2. Cost Adjustment Factor is a live formula in PARAMETERS: `= ItemsSubtotalTarget / PreCalibrationSubtotal`. Do not hardcode.
3. iNFADS-locked top row in PAX: Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
4. PAX Associated Costs: Cont 10%, SIOH 8% (OCONUS), DB 4%, P&D 6% NON ADD. Multiplier 1.23552.
5. Acronym: "DB" in user-facing labels (not "DBD").
6. Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
7. No em dashes. No double hyphens. No AI jargon. No "Claude" or "Apex Omega" framing in deliverables.
8. NAVFAC 11010.44E inactive per 1987 issuance; do not cite.
9. Cosmetic baseline: Camp Courtney Bldg 4207 photos `IMG_0185-0188.jpeg`.

## Working discipline

1. Source of truth: `.claude/skills/dd-1391/SKILL.md`. Read it before editing.
2. Commit at logical boundaries; plain-language messages.
3. Push every commit. On 503, retry with backoff; fall back to `mcp__github__create_or_update_file` or `mcp__github__push_files`.
4. Update the skill when state changes.
5. No version-history scaffolding inside files.
6. Verify or surface as open item. No assumptions.

## Rebuild loop

```
python3 scripts/build_all.py
git add *.xlsx scripts/build_all.py scripts/data/scope.json
git commit -m "..."
git push -u origin claude/rebuild-cost-estimate-workbook-NlO5b
```

## Likely next tasks

- Cosmetic refinements to DD1391_BLOCK9 face to match Camp Courtney 4207 layout
- Block 11 narrative tab if requested for a specific building
- Scope edits in `scripts/data/scope.json` after site survey updates; rerun builder
- Style or palette adjustments to `scripts/build_all.py`

## Personalities

- CDR Justus K. O'Connor - signing officer (PWO)
- Bil Hawkins, P.E., PMP - Deputy PWO at MCB Camp Butler G-F; Anthony's government client
- Robert W. Kaye, RA - Planning Director, NAVFAC FEAD; reviewer
- Anthony L. Potter - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor

## First moves next session

1. Read `.claude/skills/dd-1391/SKILL.md` end to end.
2. Open SCH-3270 in LibreOffice or Excel; inspect each tab.
3. Confirm DD1391_BLOCK9 reconciliation row equals 0.
4. Take direction from Anthony.
