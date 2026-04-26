---
name: dd-1391
description: Camp Schwab DD Form 1391 Block 9 architecture and FSRM cost-estimate rules for the FY27 five-building portfolio (SCH-1024, SCH-3213, SCH-3237, SCH-3270, SCH-3314). Covers locked program adder rates, the canonical Block 9 face per the May 2024 CRB manual, LSH placement, PAX paste discipline, and verification gates. Use when working in this repo on Block 9, cost estimate workbooks, or PAX submission text.
---

# Camp Schwab DD Form 1391 - Cost Estimate Reference

This is the team-internal reference for the five-building Camp Schwab FY27 portfolio. It captures the rules so the next revision cycle starts from the rulebook, not memory.

## Bottom-line architecture for Block 9

The face of Block 9 follows Section 3.1 of the MCON/MCNR Consistency Review Board Guidelines and DD 1391 Development manual (May 2024, REV #15). The cosmetic format mirrors the three Air Force DD 1391 examples Rob Kaye attached (Eielson F-35A 2018, Fairford RC-135 2018, Nellis Red Flag 2018).

```
PRIMARY FACILITIES                                                   [P_TOTAL]
  [Building Name] (Conversion/Alteration)        SF | [GSF] | [PUC] | ([P_LINE])
SUPPORTING FACILITIES                                                [S_TOTAL]
  SPECIAL CONSTRUCTION FEATURES                  LS |       |       | ([LSH])
    (Life Safety and Health upgrades, 2.5% of PRV per
     NAVFAC 11010.44E CH-1 / MCO 11000.12)
SUBTOTAL                                                             [SUBTOTAL]
CONTINGENCY (10.0% of Primary Facilities)                            [CONT]
TOTAL CONTRACT COST                                                  [TCC]
SUPERVISION, INSPECTION AND OVERHEAD (8.0% of TCC)                   [SIOH]
DESIGN COST (6.0% of TCC, NAVFAC agency-directed)                    [DESIGN]
CONSTRUCTION MANAGEMENT (4.0% of TCC)                                [CM]
TOTAL FUNDED COST                                                    [TFC]
DESIGN/BUILD - DESIGN COST (4.0% of Total Funded)                    [DBD]
TOTAL PROJECT COST                                                   [TPC]
TOTAL PROJECT COST (ROUNDED)                                         [TPC_R]
EQUIPMENT FROM OTHER APPROPRIATIONS (NON-ADD)                        ([EOA])
```

## Hard rules (do not change without written direction)

- **Parent line is locked from iNFADS in PAX.** CCN, Class (R), Type (RM), UM (SF), Quantity (whole building GSF), and RPUID are not operator-editable. Unit Cost is back-calculated from Total Project Cost (rounded) divided by total GSF.
- **No UNIFORMAT codes on Block 9 face.** UNIFORMAT II Level 2 codes live in the SCOPE_DETAIL tab of the cost estimate workbook only. They never appear on Block 9.
- **No discipline-first line names.** Lines do not begin with HVAC, Plumbing, Electrical, Mechanical, Fire Protection, Communications, or Site. The Primary Facility line names the facility.
- **One Primary Facility line per building.** Conversion/Alteration scope is described in the Block 10 PS statement, not enumerated as multiple Block 9 lines.
- **LSH is not a free-standing line.** LSH appears as a Special Construction Features sub-line under Supporting Facilities. The 2.5%-of-PRV authority is cited in the line description.
- **Dollar values are not in dispute.** Every line on the corrected Block 9 matches the cost estimate workbook DD1391_BLOCK9 tab to the dollar. If the workbook and the PAX paste-text disagree, the workbook wins.
- **Em dashes are banned.** Use commas, colons, or parentheses.

## Locked program adder rates (all five buildings, identical)

| Adder | Rate | Authority | Applied to |
|-------|------|-----------|------------|
| ACF | 1.85 | UFC 3-701-01 w/Change 7 (25 Jul 2025), Table 4-1 OCONUS, M67400-0004 | FY24 CONUS Base Direct |
| Escalation | 2.1%/yr (compound 3 yrs = 1.0643) | OSD FY25 published rate | ACF-Adjusted Cost |
| General Requirements | 10.0% | FSRM program-directed | Escalated Cost |
| Contingency | 10.0% | FSRM program-directed; UFS 3-740-05 (2 Feb 2026) Level 3 ROM | GR-applied subtotal |
| LSH | 2.5% of PRV | NAVFAC 11010.44E CH-1; MCO 11000.12 (08 Sep 2014) | iNFADS PRV (or formula PRV per UFC 3-701-01 Eq 3-1) |
| Design | 6.0% | NAVFAC agency-directed | Construction Base (TCC) |
| SIOH | 8.0% | OCONUS FSRM customer-directed (NOT standard 7.3% OCONUS, NOT 9.0% Remote OCONUS) | Construction Base (TCC) |
| CM | 4.0% | NAVFAC agency-directed | Construction Base (TCC) |
| DB Design | 4.0% | UFC 3-730-01 (2024) | Total Funded Cost (applied AFTER, per Marine Corps FSRM convention) |

## Building inventory (locked identifiers and totals)

| Building | PAX ID | Fi Web | iNFADS RPUID | iNFADS-locked Description | Primary CCN | GSF | Total Funded ($) | Total Project ($) | LSH ($) | PRV ($) |
|----------|--------|--------|--------------|----------------------------|-------------|-----|----------------:|-------------------:|--------:|--------:|
| SCH-1024 | 387356 | BU26PPE70M | 148675 | MULTI PURPOSE BEQ/BOQ/CO HQS | 14345 (Armory) | 84,861 | 10,012,635 | 10,413,140 | 2,413,084 | 96,523,347 |
| SCH-3213 | 387624 | BU26PPE72M | 48879 | COMPANY HQ | 61010 (BN HQ) | 13,484 | 5,190,315 | 5,397,928 | 272,333 | 10,893,334 |
| SCH-3237 | 387622 | BU26PPE73M | 51473 | WAREHOUSE/ARMORY | 44112 (Storage) | 30,973 | 1,399,544 | 1,455,526 | 665,905 | 26,636,215 |
| SCH-3270 | 387568 | BU26PPE74M | 1174058 | AUTO ORGANIZATIONAL SHOP CAB | 21451 (Auto Org Shop) | 25,390 | 3,392,070 | 3,527,753 | 987,690 | 39,507,617 |
| SCH-3314 | 387433 | BU26PPE71M | 50931 | BATTALION SQUADRON HEADQUARTERS | 61072 (BN/Sqdn HQ) | 28,699 | 1,874,407 | 1,949,383 | 745,670 | 29,826,797 |
| **PORTFOLIO** | | | | | | | **21,868,971** | **22,743,730** | | |

The iNFADS-locked Description is what PAX renders on the green-highlighted top row of Block 9 Data, with Quantity 1.00 and Unit Cost = full Total Project Cost in raw dollars. Operator cannot edit Description, Classification of Work, Work Type, UM, or Quantity on that row.

## LSH placement decision (manual is silent)

The May 2024 CRB manual does not address the Marine Corps 2.5%-of-PRV LSH program adder. Placement is therefore inferred. The deliverable places LSH as a Special Construction Features sub-line under Supporting Facilities.

Rationale anchored to the manual:
- §3.1 Supporting Facilities sequencing item 1: SPECIAL CONSTRUCTION FEATURES
- §4.9 (page 30): "Special Construction Features are those items that are built into or are part of the facility (e.g., radon gas removal system in the foundation). The SPECIAL CONSTRUCTION FEATURES line-item will be listed under the Supporting Facilities."
- LSH represents life-safety / health code compliance work built into the facility (sprinkler, egress, fire alarm, asbestos). It fits the §4.9 definition.

Fallback (if reviewer rejects the §4.9 home): roll LSH inside the Primary Facility line cost; describe the LSH share in the Block 10 PS statement; no separate sub-line.

## Math chain (per building)

```
Base Direct (FY24 CONUS) × 1.85 ACF × 1.0643 Esc × 1.10 GR = Subtotal_GR
Subtotal_GR × 1.10 Cont = Construction Subtotal (workbook label)
Construction Subtotal + LSH = Construction Base (= TCC on canonical face)
Construction Base × 0.06 = Design (NAVFAC)
Construction Base × 0.08 = SIOH
Construction Base × 0.04 = CM
Construction Base + Design + SIOH + CM = Total Funded Cost
Total Funded × 0.04 = DB Design
Total Funded + DB Design = Total Project Cost
```

The contingency rate label on Block 9 reads "10.0%" but the math is 10% × Subtotal-without-LSH. The Block 10 / Section F documents the FSRM cost methodology so a careful reviewer can reconcile.

## Verification gates (run before any PAX submission)

1. **Dollar reconciliation.** For each building, Total Funded and Total Project on the corrected Block 9 must match the workbook DD1391_BLOCK9 tab to the dollar. Sum: portfolio Total Funded $21,868,971; Total Project $22,743,730.
2. **No UNIFORMAT.** `grep -E 'B20|C10|C30|D20|D30|D40|D50|E20|F10|F20|G10|G20|UNIFORMAT'` against every Block 9 face must return zero hits in line descriptions.
3. **No discipline-first naming.** Line descriptions do not begin with HVAC, Plumbing, Electrical, Mechanical, Fire Protection, Communications, or Site.
4. **Architecture order.** Each building follows the canonical face ordering: Primary, Supporting, Subtotal, Contingency, TCC, SIOH, Design, CM, Total Funded, DB Design, Total Project, TPC Rounded, Equipment from Other Appropriations.
5. **LSH placement.** All five buildings place LSH at the same architectural position (Special Construction Features under Supporting Facilities).
6. **No em dashes.** `grep -E '-|--'` against every deliverable returns zero hits.
7. **Authority cites verified against manual OCR.** Every CRB Guidelines page citation must be cross-checkable against the OCR'd manual text in working/crb_master.txt.

## Repository file map

- `/Consistency Review Board 1391 Development Guidelines 22 May 2024 Edition.pdf` - the manual (93 pages, scanned)
- `/DD1391 *.pdf` - three AF MILCON exemplars from Rob's email (Eielson, Fairford, Nellis)
- `/[1024|3213|3237|3270|3314]_G_CEPBKUP_*.xlsx` - five cost estimate workbooks (frozen, read-only reference)
- `/SCH_Block9_PAX_AllFiveBuildings.md` - the legacy PAX paste-text (older than workbooks on three buildings; do not use as source of truth)
- `/deliverables/blocks/SCH-####_BLOCK9.md` - corrected Block 9 per building, PAX-paste-ready
- `/deliverables/01_LSH_PLACEMENT_DECISION.md` - LSH inference rationale with manual cites
- `/deliverables/02_BLOCK9_CANONICAL_TEMPLATE.md` - canonical face template, line-by-line, with manual cites
- `/deliverables/03_DEVIATION_REPORT.md` - building-by-building deviations from current PAX state
- `/deliverables/04_EMAIL_TO_KAYE_DRAFT.md` - outbound to Rob Kaye, NAVFAC FEAD
- `/deliverables/05_FORWARD_LOOK.md` - downstream issues this re-architecture surfaces
- `/deliverables/00_VERIFICATION.md` - automated gate results
- `/working/` - OCR output, workbook dump, intermediate notes (gitignored)

## Voice and constraints

- Plain prose preferred over heavy bullet structure.
- Banned words: delve, leverage, harness, foster, robust, comprehensive, seamless, intricate, nuanced, holistic, transformative, game-changing, pivotal, groundbreaking, cutting-edge.
- Banned phrases: "It's important to note", "When it comes to", "At its core", "Let's break it down".
- No em dashes. No double hyphens. Commas, colons, or parentheses only.
- Numbers in $000s with three decimal places (Camp Schwab convention; SCH-3213 was a one-off whole-thousand entry, now standardized).
- Building IDs as `SCH-####` consistently.
- Manual citations format: `(CRB Guidelines May 2024, p. NN)`.

## Personalities (context for review)

- **CDR Justus K. O'Connor** - signing officer.
- **Bil Hawkins** P.E., PMP - Deputy Public Works Officer at MCB Camp Butler G-F. Anthony's government client.
- **Robert W. Kaye** RA - Planning Director, NAVFAC FEAD. Reviews 1391s on behalf of the signing chain. Stated complaint: "Block 9 is not broken down by discipline or broken out by Uniformat. Straight forward Primary Facility(s), Supporting, Contingency and on down to Other Appropriations."
- **John Thurber** - NAVFAC HQ CI/MILCON, manual author, john.thurber@navy.mil, 202-685-9401. Contact for manual interpretation.

Anthony owns the cost estimate workbooks and the PAX paste-text. Anthony works for Bil and must satisfy Rob's review. The deliverable does not take sides. It satisfies the manual.
