# SCH-3237 - DD Form 1391 Block 9
## Storage and Telecommunications Room Repair
## Camp Schwab, Okinawa, Japan | FY27 | MCIPAC G-F PPE

**PAX ID:** 387622 | **Fi Web:** BU26PPE73M | **iNFADS RPUID:** 51473 | **Primary CCN:** 44112 (General Purpose Storage) | **Total Building GSF:** 30,973

All amounts in $000s to three decimal places. Dollar values exactly as in the CEPBKUP workbook (3237_G_CEPBKUP_BU26PPE73M_POM26_20260309.xlsx).

---

## iNFADS-locked row (PAX-auto, NOT operator entered)

This is the row PAX renders at the top of the Block 9 Data items table. The Description, Classification of Work, Work Type, UM, and Quantity come from the iNFADS property record and are not operator-editable. Unit Cost and Total are PAX-calculated.

```
Description:                WAREHOUSE/ARMORY
Classification of Work:     C
Work Type:                  RM
UM:                         SF
Quantity:                   1.00
Unit Cost ($):              1,455,526.00
Total Cost ($000):          1,456
```

Total = Total Project Cost (rounded to nearest $1,000) = $1,456K. PAX back-calculates Unit Cost from Total / Quantity at 1.00 SF.

## Operator-entered Block 9 cost estimate

```
9. COST ESTIMATES                           UNIT COST
ITEM                       U/M | QUANTITY | $000 | $000

PRIMARY FACILITIES                                  472.863
 STORAGE AND TR REPAIR (Conversion/Alteration;   SF | 30,973 | 15.267 | (  472.863 )
 CCN 44112)

SUPPORTING FACILITIES                                 665.905
 SPECIAL CONSTRUCTION FEATURES          LS |     |     | (  665.905 )
  (Life Safety and Health upgrades, 2.5% of
   iNFADS PRV $26,636,215 per NAVFAC 11010.44E
   CH-1 and MCO 11000.12)

SUBTOTAL                                      1,138.768
CONTINGENCY (10.0% of Primary Facilities, per                     47.286
 FSRM program direction; UFS 3-740-05 (2 Feb 2026), Level 3 ROM)
TOTAL CONTRACT COST                                 1,186.054
SUPERVISION, INSPECTION AND OVERHEAD (8.0% of TCC,                   94.884
 OCONUS FSRM customer-directed)
DESIGN COST (6.0% of TCC, NAVFAC agency-directed)                   71.163
CONSTRUCTION MANAGEMENT (4.0% of TCC, agency-directed)                 47.442
TOTAL FUNDED COST                                  1,399.544
DESIGN/BUILD - DESIGN COST (4.0% of Total Funded; UFC 3-730-01             55.982
 (2024); applied AFTER Total Funded per Marine Corps FSRM convention)
TOTAL PROJECT COST                                 1,455.526
TOTAL PROJECT COST (ROUNDED)                            1,456.000
EQUIPMENT FROM OTHER APPROPRIATIONS (NON-ADD)                    (  0.000 )
```

## Math verification

- Primary + Supporting = $472.863 + $665.905 = $1,138.768 → Subtotal
- Subtotal + Contingency = $1,138.768 + $47.286 = $1,186.054 → matches workbook Construction Base
- 8.0% × TCC = $94.884 ← matches SIOH
- 6.0% × TCC = $71.163 ← matches Design
- 4.0% × TCC = $47.442 ← matches CM
- Total Funded = $1,399.544 ✓
- DB Design = $55.982 ✓
- TPC = $1,455.526 ✓

## Verification footer

| Source | Total Funded ($000s) | Total Project ($000s) |
|--------|----------------------|------------------------|
| CEPBKUP workbook (09 Mar 2026), DD1391_BLOCK9 tab | 1,399.544 | 1,455.526 |
| Current PAX .md state (consolidated file) | 1,396.620 | 1,452.485 |
| This corrected Block 9 | 1,399.544 | 1,455.526 |
| **Reconciliation vs workbook** | **PASS** | **PASS** |
| **Reconciliation vs current PAX .md** | minor delta (about $2.9K, rounding artifact) | minor delta (about $3.0K, rounding artifact) |

## What changed cosmetically vs prior PAX entry

- Removed UNIFORMAT codes (prior UNIFORMAT prefixes) from line names.
- Removed discipline-first naming (TR HVAC, TR Electrical, etc.).
- Consolidated 7 UNIFORMAT-grouped scope lines (with duplicate scope groups in the prior layout) into a single Primary Facility line.
- Repositioned LSH from a free-standing line to a Special Construction Features sub-line under Supporting Facilities.

## Open items (yellow flags carried forward)

- Fire suppression line in the prior PAX entry was a $15K LS placeholder (system type TBD) included in the HAZMAT subtotal; design will resolve type per NFPA 75 / UFC 3-600-01.
- HAZMAT $127.183K pending PWD ENV confirmation on Room 101 flooring; included in the Primary Facility line cost.

## PAX Block 9 Data item-list mirror (paste-ready)

This is the same canonical architecture above, expressed as rows that paste directly into the PAX Block 9 Data items table. Order matches the canonical face. All totals reconcile.

```
ROW                                                           UM   Qty       Unit Cost ($)        Total ($000)
--------------------------------------------------------------|----|---------|--------------------|-------------
PRIMARY FACILITIES                                            |    |         |                    |    472.863
  WAREHOUSE/ARMORY                                          |  SF| 1.00    |           472,863.00|    472.863
  (Conversion/Alteration; per workbook ESTIMATE tab)          |    |         |                    |
                                                               |    |         |                    |
SUPPORTING FACILITIES                                         |    |         |                    |    665.905
  SPECIAL CONSTRUCTION FEATURES                               |  LS| 1.00    |           665,905.00|    665.905
  (Life Safety and Health upgrades, 2.5% of PRV;               |    |         |                    |
  NAVFAC 11010.44E CH-1 / MCO 11000.12)                        |    |         |                    |
```

**Cost rollup adders (Contingency, SIOH, Design, CM, DB Design) — two equivalent options:**

**Option A: Apply via PAX `%` (percent items) below the items list.** This is the cleanest representation of the canonical face. Each row is a separate percent item that PAX auto-calculates against the appropriate base.

| Order | Percent item label | Rate | PAX `%` Base | Resulting $000 |
|-------|--------------------|------|--------------|----------------:|
|   1   | CONTINGENCY                            | 10.0% | Primary only           |      47.286 |
|   2   | SIOH (OCONUS FSRM customer-directed)   | 8.0%  | Subtotal + Contingency |      94.884 |
|   3   | DESIGN (NAVFAC agency-directed)        | 6.0%  | Subtotal + Contingency |      71.163 |
|   4   | CONSTRUCTION MANAGEMENT                | 4.0%  | Subtotal + Contingency |      47.442 |
|   5   | DESIGN/BUILD - DESIGN COST             | 4.0%  | Total Funded Cost      |      55.982 |

Total Project Cost rolls up to $1,455,525 ≈ $1,456K (rounded). Total Funded Cost = $1,399,543.

**Option B: Bake adders into a single dollar item.** If percent items are not in use for FY27 in PAX, add one dollar item to the Supporting Facilities section labeled `PROGRAM ADDERS (CONTINGENCY 10%, SIOH 8%, DESIGN 6%, CM 4%, DB DESIGN 4%)` with Total ($000) = $316.757 so the items list sums to the same Total Request of $1,456K. Block 10 narrative carries the rate breakdown.

Use whichever option the FY27 PAX configuration accepts. Dollar value to the parent locked row is identical either way.

## Block 10 paired statement (PRIMARY FACILITY PS)

PRIMARY FACILITY (PS): "This project repairs and reconfigures portions of Building 3237, a 30,973 SF general purpose storage facility (FAC 4421) at Camp Schwab. Scope includes Room 101 storage cage demolition and new partitions, Telecommunications Room interior construction (partition walls, backboards, fire-rated door), TR dedicated HVAC (independent 24/7 mini-split per UFC 3-580-01), TR electrical infrastructure (dedicated panel, receptacles, cable tray), TR fire suppression system (NFPA 75 / UFC 3-600-01, type TBD at design), communications infrastructure modernization (EMT, Cat6 NIPR/SIPR, work area outlets, TR cabinet, testing), and asbestos mastic abatement (Bhate Environmental 2001 H2 Chrysotile finding, Room 101 plus hallway). Functions provided: storage and telecommunications support for 4th Marine Regiment and CLB-4. The Special Construction Features line under Supporting Facilities is a 2.5%-of-PRV Life Safety and Health upgrade allowance per NAVFAC 11010.44E CH-1 and MCO 11000.12 (08 Sep 2014). Equipment included in the Primary Facility unit cost; no equipment from other appropriations."
