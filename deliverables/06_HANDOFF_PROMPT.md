# Handoff - Camp Schwab FY26 cost estimate workbooks

User: Anthony L. Potter, Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor at MCB Camp Butler G-F, Okinawa.

Status: all five FY26 cost estimate workbooks built, reconciled to locked TPC at $000 (delta 0), committed, and pushed. Iterate on what is there. Do not rebuild from scratch.

## Repository

- Repo: `CRYPTOKEYSAFE/DD_Form_1391-_Cost_Estimates`
- Branch: `claude/rebuild-cost-estimate-workbook-NlO5b` is the live branch. It is already checked out at session start. Do not switch branches. Do not work on `main`. Do not work on the older `claude/rebuild-cost-estimate-workbook-ZJR0M` branch.
- Verify before any edit: `git branch --show-current` must print `claude/rebuild-cost-estimate-workbook-NlO5b`. If it does not, stop and surface to Anthony.
- CWD: `/home/user/DD_Form_1391-_Cost_Estimates/`
- Skill: `.claude/skills/dd-1391/SKILL.md` - read first, end to end.
- Builder: `scripts/build_all.py` - run with `python3 scripts/build_all.py`. Rebuilds all five workbooks, runs reconciliation check (delta 0 at $000), runs banned-string sweep, prints summary.
- Scope source of truth: `scripts/data/scope.json`. Canonical per-building line items, sections, UNIFORMAT II Lv2 codes. Edit this, then rerun the builder.

## Reconciliation (verified at last commit)

| Building | File | Locked TPC ($) | Items Subtotal Target ($000) | Workbook TPC ($000) | Δ |
|---|---|---:|---:|---:|---:|
| Bldg 1024 | `1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx` | 10,413,140 | 8,428 | 10,413 | 0 |
| SCH-3213 | `3213_G_CEPBKUP_BU26PPE72M_POM26_20260320.xlsx` | 5,397,928 | 4,369 | 5,398 | 0 |
| SCH-3237 | `3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx` | 1,455,526 | 1,178 | 1,456 | 0 |
| SCH-3270 | `3270_G_CEPBKUP_BU26PPE74M_POM26_20260319.xlsx` | 3,527,753 | 2,855 | 3,528 | 0 |
| SCH-3314 | `3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx` | 1,949,383 | 1,578 | 1,949 | 0 |

Portfolio Locked TPC: $22,743,730. All Fi Web suffixes are M. The R suffix on the previous SCH-3270 file copy was a clerical error and is corrected.

## Load-bearing rule

Anthony pastes each workbook's DD1391_BLOCK9 discipline rollups into the PAX Block 9 items table. PAX applies the four pre-loaded Associated Costs percentages and prints the form. Printed TPC must equal Locked TPC at $000. Math, exactly:

```
Items Subtotal Target = Locked TPC / 1.23552  (1.10 x 1.08 x 1.04)
TCC = Items Subtotal x 1.10   (Cont 10% PAX-applied)
TFC = TCC x 1.08              (SIOH 8% PAX-applied)
TPC = TFC x 1.04              (DB 4% PAX-applied)
PD  = Items Subtotal x 0.06   (NON ADD; informational only; does not roll into TPC)
```

The Cost Adjustment Factor in PARAMETERS is the calibration knob. It is a live formula:

```
CostAdjustmentFactor = ItemsSubtotalTarget / PreCalibrationSubtotal
PreCalibrationSubtotal = BaseDirect x ACF x Escalation x (1 + GeneralRequirements)
```

Each discipline rollup formula in DD1391_BLOCK9 multiplies its UNIFORMAT-grouped base direct by ACF, escalation, (1 + GR), and the Cost Adjustment Factor before dividing by 1000 and rounding to $000. The factor implicitly absorbs base-cost adjustments distributed pro-rata across all disciplines. Do not hardcode it. Do not rename the cell.

## Architecture (all five workbooks identical)

Four tabs in this order: ESTIMATE, SCOPE_DETAIL, PARAMETERS, DD1391_BLOCK9.

- ESTIMATE - ROM formula chain (Section A), PAX rollup verification with reconciliation row (Section B), UNIFORMAT II Lv2 summary by SUMIF (Section C), methodology (Section D), version history (Section E).
- SCOPE_DETAIL - line-by-line scope (Item, Group, Description, Qty, Unit, Unit Cost FY24 CONUS pre-ACF, Extended Cost = Qty x Unit Cost, UNIFORMAT II Lv2 code, Notes). Section group titles retained as banner rows. Total Base Direct Cost row at the bottom.
- PARAMETERS - project ID, cost inputs (yellow user-input cells), PAX Associated Costs (informational), derived values block (Compound Escalation Factor, Base Direct, Pre-Calibration Subtotal, Locked TPC, Items Subtotal Target, Cost Adjustment Factor), planning rates (JPY/USD 150.4415), active references.
- DD1391_BLOCK9 - the PAX paste sheet. Discipline rollups by UNIFORMAT II Lv2 group; Items Subtotal; PAX percentage rows (Cont 10%, SIOH 8%, DB 4%); Total Project Cost; Total Project Cost ($000 rounded); P&D 6% NON ADD informational; Reconciliation row that must equal 0; Classification of Work (Construction 100%, Special Interest: Restoration and Modernization 100%).

## Hard rules

1. Block 9 paste sheet uses discipline rollups by UNIFORMAT II Lv2 group. Line count varies per building (4 to 11 lines).
2. Cost Adjustment Factor is a live formula in PARAMETERS. Do not hardcode. Do not rename.
3. iNFADS-locked top row in PAX: Description, Classification of Work, Work Type, UM, Quantity not operator-editable.
4. PAX Associated Costs at submission: Cont 10%, SIOH 8% (OCONUS FSRM customer-directed), DB 4%, P&D 6% NON ADD. Combined multiplier 1.23552.
5. Acronym in user-facing labels: "DB" for Design-Build. Never "DBD".
6. NAVFAC 11010.44E is inactive per 1987 issuance. Never cite.
7. Banned strings inside any workbook cell, formula, or comment: `LSH`, `Life Safety`, `Life-Safety`, `11010.44E`, `DBD`. The builder verifies on each run; the build fails the sweep if any leak.
8. Banned words in any deliverable, code comment, or commit message: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
9. No em dashes. No double hyphens. No AI jargon. No "Claude" or "Apex Omega" framing in any deliverable.
10. Cosmetic baseline reference: Camp Courtney Bldg 4207 photos `IMG_0185.jpeg` through `IMG_0188.jpeg`.

## Reference materials in the repo

- `Consistency Review Board 1391 Development Guidelines 22 May 2024 Edition.pdf` - the manual.
- `M67400_BU26PPE70M_2026.pdf` - signed FY 2026 1391 for Bldg 1024.
- `IMG_0179.jpeg` - PAX Block 9 Data screen.
- `ASSOCIATED_COSTS.png` - PAX Associated Costs dialog.
- `IMG_0185.jpeg` through `IMG_0188.jpeg` - Camp Courtney Bldg 4207 cosmetic baseline.
- `1024.pdf`, `3213.pdf`, `3237.pdf`, `3270.pdf`, `3314.pdf` - five recent 1391 PDFs (gitignored).
- Original 4-tab blue/white reference workbooks from before the rebuild are preserved in git history at commit `4819bb3` on `main`. Recover any one with `git show 4819bb3:<filename> > /tmp/<filename>` for cosmetic reference only. Those files contain LSH-visible content and an inactive citation; never use them for content guidance, only for palette and column layout.
- JED Cost Estimating Guidance (Combined, Nov 2025), JDDG v9 (April 2025), UFC 3-701-01 with Change 7 (25 Jul 2025), UFS 3-740-05 (02 Feb 2026) - all gitignored references.
- `dod-cost-estimating-SKILL.md` - gitignored secondary reference.

## Working discipline

1. Source of truth: `.claude/skills/dd-1391/SKILL.md`. Read it before editing anything else.
2. Commit at logical boundaries with plain-language messages. No co-author trailers. No "generated with" lines.
3. Push every commit to `claude/rebuild-cost-estimate-workbook-NlO5b`. On 503, retry with backoff (2s, 4s, 8s, 16s) up to four times. If still failing, fall back to `mcp__github__create_or_update_file` or `mcp__github__push_files`.
4. Update the skill when state changes. Skill drifts faster than the workbooks; keep it current.
5. No version-history scaffolding inside files. Git is the version history.
6. Verify; do not assume. Surface ambiguity as an open item rather than guess.
7. TodoWrite for in-session work over five steps.
8. Handoff prompt regenerated each time, not edited.

## Rebuild loop

```
# edit scripts/data/scope.json or scripts/build_all.py
python3 scripts/build_all.py
# inspect printed reconciliation summary; all five must show delta 0 and OK
git add *.xlsx scripts/build_all.py scripts/data/scope.json
git commit -m "..."
git push -u origin claude/rebuild-cost-estimate-workbook-NlO5b
```

## Verification gate (run before declaring any rebuild done)

1. `python3 scripts/build_all.py` - prints reconciliation table and banned-string sweep. All five rows must show `delta 0` and `OK`.
2. Open SCH-3270 (the worked example) in LibreOffice or Excel. Confirm DD1391_BLOCK9 reconciliation row shows 0.
3. `git status` - working tree must be clean after commit.
4. `git log origin/claude/rebuild-cost-estimate-workbook-NlO5b..HEAD` - must be empty after push.

## Likely next tasks

- Cosmetic refinements to DD1391_BLOCK9 face to match Camp Courtney 4207 layout
- Block 11 narrative tab if requested for a specific building
- Scope edits in `scripts/data/scope.json` after site survey updates; rerun the builder
- Style or palette tweaks to `scripts/build_all.py`
- ACF, escalation, or GR adjustments via PARAMETERS inputs (the Cost Adjustment Factor recalibrates automatically through its live formula)

## What NOT to do

- Do not rebuild from scratch. The architecture is locked. Iterate.
- Do not switch branches. Stay on `claude/rebuild-cost-estimate-workbook-NlO5b`.
- Do not introduce LSH or 11010.44E content. The builder will reject the build.
- Do not write "DBD" anywhere user-facing. Use "DB".
- Do not add COVER, BLOCK10, BACKUP, RATES, or REFERENCES tabs. The architecture is four tabs.
- Do not hardcode the Cost Adjustment Factor or any other live formula.
- Do not delegate scope research to subagents without giving them the full skill context. Subagents that operate cold tend to reintroduce removed content.
- Do not push to `main`.

## Personalities

- CDR Justus K. O'Connor - signing officer (PWO).
- Bil Hawkins, P.E., PMP - Deputy PWO at MCB Camp Butler G-F. Anthony's government client.
- Robert W. Kaye, RA - Planning Director, NAVFAC FEAD. Reviewer.
- John Thurber - NAVFAC HQ CI/MILCON, manual author. john.thurber@navy.mil. 202-685-9401.
- Anthony L. Potter - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor.

## First moves next session

1. `git branch --show-current` - confirm `claude/rebuild-cost-estimate-workbook-NlO5b`.
2. `git status` - confirm clean.
3. Read `.claude/skills/dd-1391/SKILL.md` end to end.
4. Run `python3 scripts/build_all.py` - confirm all five rows show delta 0 and OK.
5. Take direction from Anthony.
