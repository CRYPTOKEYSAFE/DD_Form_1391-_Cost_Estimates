# Handoff prompt — Camp Schwab FY26 cost estimate workbook rebuild

You are picking up a five-building DD Form 1391 cost estimate workbook rebuild for Anthony L. Potter (Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton contractor at MCB Camp Butler G-F, Okinawa, Japan). Read this entire prompt, then read `.claude/skills/dd-1391/SKILL.md`. The skill is the source of truth.

## What you are producing

Five Excel workbooks, one per building, cosmetically and architecturally identical, that drive the PAX 1391 Processor entry for the FY26 Camp Schwab portfolio.

| # | Building | Fi Web | PAX ID | Locked TPC ($) | Subtotal Target ($) |
|---|----------|--------|--------|---------------:|--------------------:|
| 1 | Bldg 1024 | BU26PPE70M | 387356 | 10,413,140 | 8,427,941 |
| 2 | SCH-3213 | BU26PPE72M | 387624 | 5,397,928 | 4,369,213 |
| 3 | SCH-3237 | BU26PPE73M | 387622 | 1,455,526 | 1,178,118 |
| 4 | SCH-3270 | BU26PPE74M | 387568 | 3,527,753 | 2,855,925 |
| 5 | SCH-3314 | BU26PPE71M | 387433 | 1,949,383 | 1,577,757 |

Subtotal target = Locked TPC / 1.23552 (planning multiplier; verify at PAX entry).

## The load-bearing rule

PAX-rendered Total Project Cost on the printed FY 2026 Special Projects Program form must equal the locked Total Project Cost above for each building, to the dollar (rounded to $000 on the printed face). The workbook is wrong if it cannot back-solve to this. The locked TPC never changes.

## Files on disk

Existing CEPBKUP workbooks (overwrite these; the 3270 file's `R` suffix is clerical, save the rebuild as `BU26PPE74M`):

```
/home/user/DD_Form_1391/1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx
/home/user/DD_Form_1391/3213_G_CEPBKUP_BU26PPE72M_POM26_20260320.xlsx
/home/user/DD_Form_1391/3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx
/home/user/DD_Form_1391/3270_G_CEPBKUP_BU26PPE74R_POM26_20260319.xlsx
/home/user/DD_Form_1391/3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx
```

Existing 1391 PDFs (gitignored): `1024.pdf`, `3213.pdf`, `3237.pdf`, `3270.pdf`, `3314.pdf`.
Cosmetic baseline: `IMG_0185.jpeg` through `IMG_0188.jpeg` (Camp Courtney Bldg 4207).
PAX ground truth: `M67400_BU26PPE70M_2026.pdf`, `IMG_0179.jpeg`, `ASSOCIATED_COSTS.png`.

## Architectural rules

1. Block 9 face by discipline rollup. No UNIFORMAT prefixes. No discipline-first naming on the Primary Facility line.
2. One Primary Facility line per building, area times unit cost on one line. Conversion / Alteration scope described in Block 10 PS.
3. iNFADS-locked top row (Description, Classification of Work, Work Type, UM, Quantity not operator-editable).
4. Four PAX Associated Costs percentages: Contingency 10.0%, SIOH 8.0%, Design Build 4.0%, Planning and Design 6.0% (NON ADD).
5. LSH and CM absorbed into discipline rollups. No discrete LSH or CM lines. Allocation logic defensible-and-logical: doors to Architectural / Interior Construction, exit lighting and fire alarm to Electrical or Fire Protection, ACM/LBP abatement under Supporting Facilities as a discrete HAZMAT line.
6. Em dashes banned. AI jargon banned. "Apex Omega" framing banned. "Claude" mentions banned.

## PAX rollup math

```
TCC = Subtotal × 1.10   (Cont 10% of Subtotal)
TFC = TCC × 1.08        (SIOH 8% of TCC)
TPC = TFC × 1.04        (DBD 4% of TFC)
PD  = NON ADD           (P&D 6%, does not roll to TPC)
TPC = Subtotal × 1.23552
Subtotal target = Locked TPC / 1.23552
```

The workbook exposes the multiplier as a single switchable cell. Candidate multipliers: 1.22, 1.2272, 1.23552 (planning), 1.28.

## Workbook architecture (cosmetically identical across all five)

Use the existing 3270 workbook as structural baseline (cleanest of the five), but fix overlapping cells, broken merges, layout drift. Tabs in order:

1. **COVER** - building identifiers, locked TPC, Fi Web, PAX ID, RPUID, GSF, signature block placeholders.
2. **BLOCK9** - printed Block 9 face. All cells formula-driven from BACKUP. Matches Camp Courtney Bldg 4207 cosmetic.
3. **BLOCK10** - PRIMARY FACILITY PS narrative paired with Block 9 dollar values. Live-formula references.
4. **BACKUP** - discipline-rollup detail. Every dollar on BLOCK9 traces here. LSH and CM absorbed by line. Multiplier cell lives here.
5. **RATES** - four PAX percentages, JPY/USD planning rate (150.4415 per FY26 budget) plus H.10 live-rate cell, ACF (1.85 OCONUS Okinawa per UFC 3-701-01 w/Ch 7 Table 4-1, M67400-0004), escalation, GR.
6. **REFERENCES** - MCO 11000.5 (03 Jun 2016), MCO 11000.12 (08 Sep 2014), CRB Guidelines May 2024, UFC 3-701-01 w/Ch 7, UFC 3-730-01 (2024), JED Cost Estimating Guide (Nov 2025), JDDG v9 (April 2025). NAVFAC 11010.44E does NOT appear (inactivated by 1987 issuance).

Every formula must be live. No hard-coded dollars on any face tab. No version-history scaffolding. Git is the version history.

## Quality bar

User's words: "It needs to be correct. Nothing is fake. Nothing is static. Nothing is embellished. Nothing is AI garbage. Nothing is inferred. Everything is defensible." Every dollar reconciles. Every formula chains. Every cell is real.

## Working discipline

- Single source of truth: `.claude/skills/dd-1391/SKILL.md`. Read it. Update when state changes.
- Commit at logical boundaries with plain-language messages.
- Push every commit. If `git push` fails 503, use `mcp__github__push_files` or `mcp__github__create_or_update_file` as bypass. Verify with `git log origin/<branch>..HEAD` empty.
- TodoWrite for in-session tracking.
- No assumptions. If you do not know, verify. If you cannot verify, surface as open item.

## Branch

Develop on `claude/fix-dd-form-block-9-KHc33`. Do not create new branches without direction.

## Order of operations

1. Read the dd-1391 skill end to end.
2. Open the 3270 workbook, audit cosmetic issues.
3. Pull scope content from each building's 1391 PDF.
4. Build BACKUP tab math chain: discipline-rollup totals absorb LSH and CM, sum to Subtotal target, drive rest via multiplier cell.
5. Build BLOCK9 face from BACKUP.
6. Build BLOCK10 paired narrative.
7. RATES and REFERENCES.
8. COVER last.
9. Reconcile: BACKUP × multiplier = Locked TPC, to the dollar.
10. Repeat for the other four buildings using the perfected 3270 as template.
11. Commit each workbook separately. Push.
12. Update the skill with anything learned. Commit. Push.

## Reviewer context

Robert W. Kaye, RA, Planning Director NAVFAC FEAD directed: single-line entry by CCN, area times unit cost on one line, no discipline or trade breakdown on the items table, rollup adders as percentages below the items list, LSH allocated to scope categories rather than carried as a discrete percentage line. The architecture above implements his direction. Bil Hawkins is Anthony's government client. CDR Justus K. O'Connor is the signing officer.
