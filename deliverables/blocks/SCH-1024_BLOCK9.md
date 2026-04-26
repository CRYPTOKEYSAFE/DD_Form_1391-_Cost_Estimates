# SCH-1024 - DD Form 1391 Block 9
## Armory Expansion and First Floor Renovation
## Camp Schwab, Okinawa, Japan | FY27 | MCIPAC G-F PPE

**PAX ID:** 387356 | **Fi Web:** BU26PPE70M | **iNFADS RPUID:** 148675 | **Primary CCN:** 14345 (Armory / Small Arms Storage, FAC 4427) | **Total Building GSF:** 84,861 | **Scope-Affected Area:** 26,488 SF (1st floor renovation)

All amounts in $000s to three decimal places. Dollar values exactly as in the CEPBKUP workbook (1024_G_CEPBKUP_BU26PPE70M_POM26_20260319.xlsx).

---

## iNFADS-locked row (PAX-auto, NOT operator entered)

This is the row PAX renders at the top of the Block 9 Data items table. The Description, Classification of Work, Work Type, UM, and Quantity come from the iNFADS property record and are not operator-editable. Unit Cost and Total are PAX-calculated.

```
Description:                MULTI PURPOSE BEQ/BOQ/CO HQS
Classification of Work:     C
Work Type:                  RM
UM:                         SF
Quantity:                   1.00
Unit Cost ($):              10,413,140.00
Total Cost ($000):          10,413
```

Total = Total Project Cost (rounded to nearest $1,000) = $10,413K. PAX back-calculates Unit Cost from Total / Quantity at 1.00 SF.


## Operator-entered Block 9 cost estimate

```
9. COST ESTIMATES                           UNIT COST
ITEM                       U/M | QUANTITY | $000 | $000

PRIMARY FACILITIES                                 5,520.182
 ARMORY AND FIRST FLOOR RENOVATION (Conversion/  SF | 26,488 | 208.405 | ( 5,520.182 )
 Alteration; CCN 14345)

SUPPORTING FACILITIES                                2,413.084
 SPECIAL CONSTRUCTION FEATURES          LS |     |     | ( 2,413.084 )
  (Life Safety and Health upgrades, 2.5% of
   iNFADS PRV $96,523,347 per NAVFAC 11010.44E
   CH-1 and MCO 11000.12)

SUBTOTAL                                      7,933.266
CONTINGENCY (10.0% of Primary Facilities, per                     552.018
 FSRM program direction; UFS 3-740-05 (2 Feb 2026), Level 3 ROM)
TOTAL CONTRACT COST                                 8,485.284
SUPERVISION, INSPECTION AND OVERHEAD (8.0% of TCC,                  678.823
 OCONUS FSRM customer-directed; documented deviation from
 standard 7.3% OCONUS rate per DASD-Con direction)
DESIGN COST (6.0% of TCC, NAVFAC agency-directed)                   509.117
CONSTRUCTION MANAGEMENT (4.0% of TCC, agency-directed)                339.411
TOTAL FUNDED COST                                 10,012.635
DESIGN/BUILD - DESIGN COST (4.0% of Total Funded; UFC 3-730-01            400.505
 (2024); applied AFTER Total Funded per Marine Corps FSRM convention)
TOTAL PROJECT COST                                 10,413.140
TOTAL PROJECT COST (ROUNDED)                            10,413.000
EQUIPMENT FROM OTHER APPROPRIATIONS (NON-ADD)                    (  0.000 )
```

## Math verification

- Primary + Supporting = $5,520.182 + $2,413.084 = $7,933.266 ← matches Subtotal
- Subtotal + Contingency = $7,933.266 + $552.018 = $8,485.284 ← matches workbook Construction Base
- TCC × 8.0% = $8,485.284 × 0.08 = $678.823 ← matches workbook SIOH
- TCC × 6.0% = $8,485.284 × 0.06 = $509.117 ← matches workbook Design
- TCC × 4.0% = $8,485.284 × 0.04 = $339.411 ← matches workbook CM
- TCC + SIOH + Design + CM = $8,485.284 + $678.823 + $509.117 + $339.411 = $10,012.635 ← matches Total Funded
- Total Funded × 4.0% = $400.505 ← matches workbook DB Design
- Total Funded + DB Design = $10,413.140 ← matches Total Project Cost

## Verification footer

| Source | Total Funded ($000s) | Total Project ($000s) |
|--------|----------------------|------------------------|
| CEPBKUP workbook (19 Mar 2026), DD1391_BLOCK9 tab | 10,012.635 | 10,413.140 |
| Current PAX .md state (consolidated file) | 9,468.837 | 9,847.591 |
| This corrected Block 9 | 10,012.635 | 10,413.140 |
| **Reconciliation vs workbook** | **PASS** | **PASS** |
| **Reconciliation vs current PAX .md** | FAIL (older LSH basis; workbook governs) | FAIL (older LSH basis) |

The current PAX .md reflects pre-correction LSH ($1,952.238K) from workbook. Workbook (10 Mar 2026) corrected LSH to $2,413.084K under UFC 3-701-01 Eq 3-1 (post-conversion 4-FAC formula). Workbook governs.

## What changed cosmetically vs prior PAX entry

- Removed UNIFORMAT codes (prior UNIFORMAT prefixes) from line names.
- Removed discipline-first line names (HVAC, Plumbing, Electrical, etc.).
- Consolidated 11 UNIFORMAT-grouped scope lines into a single Primary Facility line (Conversion/Alteration of armory and 1st floor renovation).
- Repositioned LSH from a free-standing line between Contingency and Design to a Special Construction Features sub-line under Supporting Facilities.
- Added Total Project Cost (Rounded) and Equipment from Other Appropriations (NON-ADD) lines per AF MILCON exemplar pattern.

## PAX Block 9 Data item-list mirror (paste-ready)

This is the same canonical architecture above, expressed as rows that paste directly into the PAX Block 9 Data items table. Order matches the canonical face. All totals reconcile.

```
ROW                                                           UM   Qty       Unit Cost ($)        Total ($000)
--------------------------------------------------------------|----|---------|--------------------|-------------
PRIMARY FACILITIES                                            |    |         |                    |  5,520.182
  MULTI PURPOSE BEQ/BOQ/CO HQS                              |  SF| 1.00    |         5,520,182.00|  5,520.182
  (Conversion/Alteration; per workbook ESTIMATE tab)          |    |         |                    |
                                                               |    |         |                    |
SUPPORTING FACILITIES                                         |    |         |                    |  2,413.084
  SPECIAL CONSTRUCTION FEATURES                               |  LS| 1.00    |         2,413,084.00|  2,413.084
  (Life Safety and Health upgrades, 2.5% of PRV;               |    |         |                    |
  NAVFAC 11010.44E CH-1 / MCO 11000.12)                        |    |         |                    |
```

**Cost rollup adders (Contingency, SIOH, Design, CM, DB Design) — two equivalent options:**

**Option A: Apply via PAX `%` (percent items) below the items list.** This is the cleanest representation of the canonical face. Each row is a separate percent item that PAX auto-calculates against the appropriate base.

| Order | Percent item label | Rate | PAX `%` Base | Resulting $000 |
|-------|--------------------|------|--------------|----------------:|
|   1   | CONTINGENCY                            | 10.0% | Primary only           |     552.018 |
|   2   | SIOH (OCONUS FSRM customer-directed)   | 8.0%  | Subtotal + Contingency |     678.823 |
|   3   | DESIGN (NAVFAC agency-directed)        | 6.0%  | Subtotal + Contingency |     509.117 |
|   4   | CONSTRUCTION MANAGEMENT                | 4.0%  | Subtotal + Contingency |     339.411 |
|   5   | DESIGN/BUILD - DESIGN COST             | 4.0%  | Total Funded Cost      |     400.505 |

Total Project Cost rolls up to $10,413,140 ≈ $10,413K (rounded). Total Funded Cost = $10,012,635.

**Option B: Bake adders into a single dollar item.** If percent items are not in use for FY27 in PAX, add one dollar item to the Supporting Facilities section labeled `PROGRAM ADDERS (CONTINGENCY 10%, SIOH 8%, DESIGN 6%, CM 4%, DB DESIGN 4%)` with Total ($000) = $2,479.874 so the items list sums to the same Total Request of $10,413K. Block 10 narrative carries the rate breakdown.

Use whichever option the FY27 PAX configuration accepts. Dollar value to the parent locked row is identical either way.

## Block 10 paired statement (PRIMARY FACILITY PS)

PRIMARY FACILITY (PS): "This project converts and renovates 26,488 SF of the first floor of Building 1024, an existing 84,861 SF four-story facility (FAC 7210 BEQ / FAC 4421 CIF / FAC 6102 Admin / FAC 4427 Armory) at Camp Schwab. Scope includes 28 barracks rooms converted to 14 armory vaults with GSA Class V vault doors, gym-to-workspace conversion, OSS vault with SIPR-capable workspace, communications room and weapons cleaning area, restroom and laundry conversions, building-wide chiller and HVAC replacement, telecom infrastructure modernization per UFC 3-580-01, and exterior site improvements. Functions provided: armory storage, OSS workspace with SIPR, administrative space for 4th Marine Regiment and CLB-4. The Special Construction Features line under Supporting Facilities is a 2.5%-of-PRV Life Safety and Health upgrade allowance per NAVFAC 11010.44E CH-1 and MCO 11000.12 (08 Sep 2014). Equipment included in the Primary Facility unit cost; no equipment from other appropriations."
