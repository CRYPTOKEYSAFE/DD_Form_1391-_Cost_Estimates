# SCH-3314 - DD Form 1391 Block 9
## Battalion / Squadron Headquarters Conversion
## Camp Schwab, Okinawa, Japan | FY27 | MCIPAC G-F PPE

**PAX ID:** 387433 | **Fi Web:** BU26PPE71M | **iNFADS RPUID:** 50931 | **Primary CCN:** 61072 (Battalion / Squadron HQ; FAC 6101 best-supported Table 3 proxy pending RPAO crosswalk) | **Total Building GSF:** 28,699 (233 ft x 63 ft, 2 stories)

All amounts in $000s to three decimal places. Dollar values exactly as in the CEPBKUP workbook (3314_G_CEPBKUP_BU26PPE71M_POM26_20260318.xlsx).

**Note:** The current PAX .md file states "DO NOT DRAFT". The 18 Mar 2026 CEPBKUP workbook has fully scoped 23 items across 8 groups with confirmed Total Funded of $1,874.407K. Per operator confirmation 26 Apr 2026, the workbook governs and this Block 9 is produced. Phasing risk (3-6 month MCEN outage during construction; Will Lake DOW for swing-space Bldg 3410) is captured in the forward-look register, not on the Block 9 face.

---

## iNFADS-locked row (PAX-auto, NOT operator entered)

This is the row PAX renders at the top of the Block 9 Data items table. The Description, Classification of Work, Work Type, UM, and Quantity come from the iNFADS property record and are not operator-editable. Unit Cost and Total are PAX-calculated.

```
Description:                BATTALION SQUADRON HEADQUARTERS
Classification of Work:     C
Work Type:                  RM
UM:                         SF
Quantity:                   1.00
Unit Cost ($):              1,949,383.00
Total Cost ($000):          1,949
```

Total = Total Project Cost (rounded to nearest $1,000) = $1,949K. PAX back-calculates Unit Cost from Total / Quantity at 1.00 SF.

## Operator-entered Block 9 cost estimate

```
9. COST ESTIMATES                           UNIT COST
ITEM                       U/M | QUANTITY | $000 | $000

PRIMARY FACILITIES                                  766.192
 BATTALION HEADQUARTERS BUILDING (Conversion/   SF | 28,699 | 26.696 | (  766.192 )
 Alteration; CCN 61072)

SUPPORTING FACILITIES                                 745.670
 SPECIAL CONSTRUCTION FEATURES          LS |     |     | (  745.670 )
  (Life Safety and Health upgrades, 2.5% of
   iNFADS PRV $29,826,797 per NAVFAC 11010.44E
   CH-1 and MCO 11000.12)

SUBTOTAL                                      1,511.862
CONTINGENCY (10.0% of Primary Facilities, per                     76.619
 FSRM program direction; UFS 3-740-05 (2 Feb 2026), Level 3 ROM)
TOTAL CONTRACT COST                                 1,588.481
SUPERVISION, INSPECTION AND OVERHEAD (8.0% of TCC,                  127.078
 OCONUS FSRM customer-directed)
DESIGN COST (6.0% of TCC, NAVFAC agency-directed)                   95.309
CONSTRUCTION MANAGEMENT (4.0% of TCC, agency-directed)                 63.539
TOTAL FUNDED COST                                  1,874.407
DESIGN/BUILD - DESIGN COST (4.0% of Total Funded; UFC 3-730-01             74.976
 (2024); applied AFTER Total Funded per Marine Corps FSRM convention)
TOTAL PROJECT COST                                 1,949.383
TOTAL PROJECT COST (ROUNDED)                            1,949.000
EQUIPMENT FROM OTHER APPROPRIATIONS (NON-ADD)                    (  0.000 )
```

## Math verification

- Primary + Supporting = $766.192 + $745.670 = $1,511.862 → Subtotal
- Subtotal + Contingency = $1,511.862 + $76.619 = $1,588.481 → matches workbook Construction Base
- 8.0% × TCC = $127.078 ← matches SIOH
- 6.0% × TCC = $95.309 ← matches Design
- 4.0% × TCC = $63.539 ← matches CM
- Total Funded = $1,874.407 ✓
- DB Design = $74.976 ✓
- TPC = $1,949.383 ✓

## Verification footer

| Source | Total Funded ($000s) | Total Project ($000s) |
|--------|----------------------|------------------------|
| CEPBKUP workbook (18 Mar 2026), DD1391_BLOCK9 tab | 1,874.407 | 1,949.383 |
| Current PAX .md state | NOT DRAFTED (frozen client snapshot) | NOT DRAFTED |
| This corrected Block 9 | 1,874.407 | 1,949.383 |
| **Reconciliation vs workbook** | **PASS** | **PASS** |
| **Reconciliation vs current PAX .md** | n/a (PAX .md is intentionally blank; workbook governs per operator direction 26 Apr 2026) | n/a |

## Open items (yellow flags carried forward)

- JPY/USD exchange rate: confirm from Federal Reserve H.10 on date of PAX submission. JPY column in workbook is display-only; ROM chain is USD only.
- FAC code crosswalk: CCN 61072 maps to FAC 6189 (Squadron/BN HQ) which has no Table 3 PUC entry; FAC 6101 (Small Unit HQ, $634/SF) used as best-supported proxy pending formal RPAO confirmation.
- Phasing and swing-space: full comm replacement will take the building offline for 3-6 months with no MCEN access during construction; Bldg 3410 identified as swing space; Will Lake DOW assessment due 15 Apr 2026. Phasing language to be added to Block 10 / Section F before submission.

## PAX Block 9 Data item-list mirror (paste-ready)

This is the same canonical architecture above, expressed as rows that paste directly into the PAX Block 9 Data items table. Order matches the canonical face. All totals reconcile.

```
ROW                                                           UM   Qty       Unit Cost ($)        Total ($000)
--------------------------------------------------------------|----|---------|--------------------|-------------
PRIMARY FACILITIES                                            |    |         |                    |    766.192
  BATTALION SQUADRON HEADQUARTERS                           |  SF| 1.00    |           766,192.00|    766.192
  (Conversion/Alteration; per workbook ESTIMATE tab)          |    |         |                    |
                                                               |    |         |                    |
SUPPORTING FACILITIES                                         |    |         |                    |    745.670
  SPECIAL CONSTRUCTION FEATURES                               |  LS| 1.00    |           745,670.00|    745.670
  (Life Safety and Health upgrades, 2.5% of PRV;               |    |         |                    |
  NAVFAC 11010.44E CH-1 / MCO 11000.12)                        |    |         |                    |
```

**Cost rollup adders (Contingency, SIOH, Design, CM, DB Design) — two equivalent options:**

**Option A: Apply via PAX `%` (percent items) below the items list.** This is the cleanest representation of the canonical face. Each row is a separate percent item that PAX auto-calculates against the appropriate base.

| Order | Percent item label | Rate | PAX `%` Base | Resulting $000 |
|-------|--------------------|------|--------------|----------------:|
|   1   | CONTINGENCY                            | 10.0% | Primary only           |      76.619 |
|   2   | SIOH (OCONUS FSRM customer-directed)   | 8.0%  | Subtotal + Contingency |     127.078 |
|   3   | DESIGN (NAVFAC agency-directed)        | 6.0%  | Subtotal + Contingency |      95.309 |
|   4   | CONSTRUCTION MANAGEMENT                | 4.0%  | Subtotal + Contingency |      63.539 |
|   5   | DESIGN/BUILD - DESIGN COST             | 4.0%  | Total Funded Cost      |      74.976 |

Total Project Cost rolls up to $1,949,383 ≈ $1,949K (rounded). Total Funded Cost = $1,874,407.

**Option B: Bake adders into a single dollar item.** If percent items are not in use for FY27 in PAX, add one dollar item to the Supporting Facilities section labeled `PROGRAM ADDERS (CONTINGENCY 10%, SIOH 8%, DESIGN 6%, CM 4%, DB DESIGN 4%)` with Total ($000) = $437.521 so the items list sums to the same Total Request of $1,949K. Block 10 narrative carries the rate breakdown.

Use whichever option the FY27 PAX configuration accepts. Dollar value to the parent locked row is identical either way.

## Block 10 paired statement (PRIMARY FACILITY PS)

PRIMARY FACILITY (PS): "This project converts and modernizes 28,699 SF of Building 3314, an existing two-story 1994-era facility (FAC 6101 / CCN 61072) at Camp Schwab. Scope includes building-wide HVAC diffuser and ceiling restoration (78 diffusers, 78 ceiling patches), office duct modifications for the Rooms 105/106/107 cluster, exhaust fan replacement (31 EA: 25 standard ceiling, 5 sirocco, 1 confirmed FE-7), full building TAB after all work complete, Duty Guard Room HVAC systems for Rooms 102 and 103 (mini-split R&R, abandoned equipment removal, HEU R&R, fresh air system), Mass Notification System junction box installation in Mechanical Room 115, vault demolition (SIPR rack and existing vault door, Rooms 209/210/211/212 cluster), new vault construction (GSA Class V vault door at Corridor 251 plus security bars on windows Rooms 245-250), vault electrical and SIPR network rack installation with IDS sensor raceways, AHU replacement and Mechanical Room 115 overhaul (AC-1 5,100 CFM and AC-2 14,545 CFM plus mech room peripheral work), and water heater plus DHW recirculation pump replacement (WHE 100 gal plus 2 EA inline pumps). Functions provided: Battalion Headquarters for 4th Marine Regiment 3rd Marine Division (M13200) and CLB-4 (M29030). The Special Construction Features line under Supporting Facilities is a 2.5%-of-PRV Life Safety and Health upgrade allowance per NAVFAC 11010.44E CH-1 and MCO 11000.12 (08 Sep 2014); iNFADS PRV $29,826,797 (RPUID 50931) governs per UFC 3-701-01 Section 3-2.1. Construction will require relocation to swing-space Bldg 3410 for 3-6 months due to full communications replacement and MCEN outage; phasing details per Will Lake DOW assessment (15 Apr 2026). Equipment included in the Primary Facility unit cost; no equipment from other appropriations."
