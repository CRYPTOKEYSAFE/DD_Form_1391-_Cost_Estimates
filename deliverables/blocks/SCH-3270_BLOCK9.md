# SCH-3270 - DD Form 1391 Block 9
## Repair Mechanical / Electrical / Communications / Architectural
## Camp Schwab, Okinawa, Japan | FY27 | MCIPAC G-F PPE

**PAX ID:** 387568 | **Fi Web:** BU26PPE74M | **iNFADS RPUID:** 1174058 | **Primary CCN:** 21451 (Auto Organizational Shop, FAC 2141) | **Total Building GSF:** 25,390 (Floor 1: 20,672 SF, Floor 2: 4,718 SF)

All amounts in $000s to three decimal places. Dollar values exactly as in the CEPBKUP workbook (3270_G_CEPBKUP_BU26PPE74R_POM26_20260319.xlsx). The "R" in the filename is a workbook revision marker; the project Fi Web is BU26PPE74M (operator confirmed 26 Apr 2026).

---

## iNFADS-locked row (PAX-auto, NOT operator entered)

This is the row PAX renders at the top of the Block 9 Data items table. The Description, Classification of Work, Work Type, UM, and Quantity come from the iNFADS property record and are not operator-editable. Unit Cost and Total are PAX-calculated.

```
Description:                AUTO ORGANIZATIONAL SHOP CAB
Classification of Work:     C
Work Type:                  RM
UM:                         SF
Quantity:                   1.00
Unit Cost ($):              3,527,753.00
Total Cost ($000):          3,528
```

Total = Total Project Cost (rounded to nearest $1,000) = $3,528K. PAX back-calculates Unit Cost from Total / Quantity at 1.00 SF.

## Operator-entered Block 9 cost estimate

```
9. COST ESTIMATES                           UNIT COST
ITEM                       U/M | QUANTITY | $000 | $000

PRIMARY FACILITIES                                 1,715.406
 AUTO ORGANIZATIONAL SHOP REPAIR (Conversion/   SF | 25,390 | 67.562 | ( 1,715.406 )
 Alteration; CCN 21451)

SUPPORTING FACILITIES                                 987.690
 SPECIAL CONSTRUCTION FEATURES          LS |     |     | (  987.690 )
  (Life Safety and Health upgrades, 2.5% of
   iNFADS PRV $39,507,617 per NAVFAC 11010.44E
   CH-1 and MCO 11000.12)

SUBTOTAL                                      2,703.096
CONTINGENCY (10.0% of Primary Facilities, per                     171.541
 FSRM program direction; UFS 3-740-05 (2 Feb 2026), Level 3 ROM)
TOTAL CONTRACT COST                                 2,874.637
SUPERVISION, INSPECTION AND OVERHEAD (8.0% of TCC,                  229.971
 OCONUS FSRM customer-directed)
DESIGN COST (6.0% of TCC, NAVFAC agency-directed)                   172.478
CONSTRUCTION MANAGEMENT (4.0% of TCC, agency-directed)                114.985
TOTAL FUNDED COST                                  3,392.070
DESIGN/BUILD - DESIGN COST (4.0% of Total Funded; UFC 3-730-01            135.683
 (2024); applied AFTER Total Funded per Marine Corps FSRM convention)
TOTAL PROJECT COST                                 3,527.753
TOTAL PROJECT COST (ROUNDED)                            3,528.000
EQUIPMENT FROM OTHER APPROPRIATIONS (NON-ADD)                    (  0.000 )
```

## Math verification

- Primary + Supporting = $1,715.406 + $987.690 = $2,703.096 → Subtotal
- Subtotal + Contingency = $2,703.096 + $171.541 = $2,874.637 → matches workbook Construction Base
- 8.0% of $2,874.637 = $229.971 ← matches workbook SIOH
- 6.0% of $2,874.637 = $172.478 ← matches workbook Design
- 4.0% of $2,874.637 = $114.985 ← matches workbook CM
- TCC + SIOH + Design + CM = $3,392.070 ← matches Total Funded
- Total Funded × 4.0% = $135.683 ← matches DB Design
- Total Funded + DB Design = $3,527.753 ← matches Total Project Cost

## Verification footer

| Source | Total Funded ($000s) | Total Project ($000s) |
|--------|----------------------|------------------------|
| CEPBKUP workbook (19 Mar 2026), DD1391_BLOCK9 tab | 3,392.070 | 3,527.753 |
| Current PAX .md state (consolidated file) | 2,374.358 | 2,469.332 |
| This corrected Block 9 | 3,392.070 | 3,527.753 |
| **Reconciliation vs workbook** | **PASS** | **PASS** |
| **Reconciliation vs current PAX .md** | FAIL (PAX .md = older scope; workbook added DOAS 4 EA, exhaust 22 fans + 10 hose reels, NIPR 70 drops, MNS, plumbing, roll-up doors, architectural items) | FAIL |

The current PAX .md predates the 19 Mar 2026 mechanical scope expansion and the unit-confirmed NIPR drop count. Workbook governs.

## What changed cosmetically vs prior PAX entry

- Removed UNIFORMAT codes (prior UNIFORMAT prefixes) from line names.
- Removed discipline-first line names (Mechanical HVAC, Electrical Lighting, Communications Telecom, etc.).
- Consolidated 6 UNIFORMAT-grouped scope lines into a single Primary Facility line.
- Repositioned LSH from a free-standing line between Contingency and Design to a Special Construction Features sub-line under Supporting Facilities.

## PAX Block 9 Data item-list mirror (paste-ready)

This is the same canonical architecture above, expressed as rows that paste directly into the PAX Block 9 Data items table. Order matches the canonical face. All totals reconcile.

```
ROW                                                           UM   Qty       Unit Cost ($)        Total ($000)
--------------------------------------------------------------|----|---------|--------------------|-------------
PRIMARY FACILITIES                                            |    |         |                    |  1,715.406
  AUTO ORGANIZATIONAL SHOP CAB                              |  SF| 1.00    |         1,715,406.00|  1,715.406
  (Conversion/Alteration; per workbook ESTIMATE tab)          |    |         |                    |
                                                               |    |         |                    |
SUPPORTING FACILITIES                                         |    |         |                    |    987.690
  SPECIAL CONSTRUCTION FEATURES                               |  LS| 1.00    |           987,690.00|    987.690
  (Life Safety and Health upgrades, 2.5% of PRV;               |    |         |                    |
  NAVFAC 11010.44E CH-1 / MCO 11000.12)                        |    |         |                    |
```

**Cost rollup adders (Contingency, SIOH, Design, CM, DB Design) — two equivalent options:**

**Option A: Apply via PAX `%` (percent items) below the items list.** This is the cleanest representation of the canonical face. Each row is a separate percent item that PAX auto-calculates against the appropriate base.

| Order | Percent item label | Rate | PAX `%` Base | Resulting $000 |
|-------|--------------------|------|--------------|----------------:|
|   1   | CONTINGENCY                            | 10.0% | Primary only           |     171.541 |
|   2   | SIOH (OCONUS FSRM customer-directed)   | 8.0%  | Subtotal + Contingency |     229.971 |
|   3   | DESIGN (NAVFAC agency-directed)        | 6.0%  | Subtotal + Contingency |     172.478 |
|   4   | CONSTRUCTION MANAGEMENT                | 4.0%  | Subtotal + Contingency |     114.985 |
|   5   | DESIGN/BUILD - DESIGN COST             | 4.0%  | Total Funded Cost      |     135.683 |

Total Project Cost rolls up to $3,527,754 ≈ $3,528K (rounded). Total Funded Cost = $3,392,071.

**Option B: Bake adders into a single dollar item.** If percent items are not in use for FY27 in PAX, add one dollar item to the Supporting Facilities section labeled `PROGRAM ADDERS (CONTINGENCY 10%, SIOH 8%, DESIGN 6%, CM 4%, DB DESIGN 4%)` with Total ($000) = $824.658 so the items list sums to the same Total Request of $3,528K. Block 10 narrative carries the rate breakdown.

Use whichever option the FY27 PAX configuration accepts. Dollar value to the parent locked row is identical either way.

## Block 10 paired statement (PRIMARY FACILITY PS)

PRIMARY FACILITY (PS): "This project repairs and modernizes 25,390 SF of Building 3270, an existing two-story Auto Organizational Shop (FAC 2141) at Camp Schwab. Scope includes ACP HVAC system replacement (7 outdoor condensing units plus 24 indoor fan coils plus refrigerant infrastructure), DOAS fresh air systems (4 units), exhaust system replacement (22 fans plus 10 vehicle exhaust hose reels), welding shop exhaust restoration, battery room ventilation upgrade per OSHA 1910.178, compressed air system inspection and repair, plumbing safety stations and fixtures, roll-up door inspection and repair (22 EA), 94-fixture lighting replacement with motion sensors, Cat6 NIPR infrastructure (70 drops), TR upgrades for both 1F and 2F TRs, MNS junction box installation, and architectural interior repairs and remediation. Functions provided: vehicle organizational maintenance for 4th Marine Regiment and CLB-4. The Special Construction Features line under Supporting Facilities is a 2.5%-of-PRV Life Safety and Health upgrade allowance per NAVFAC 11010.44E CH-1 and MCO 11000.12 (08 Sep 2014). Equipment included in the Primary Facility unit cost; no equipment from other appropriations."
