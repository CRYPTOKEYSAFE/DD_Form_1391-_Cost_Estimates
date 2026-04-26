# SCH-1024 - DD Form 1391 Block 9
## Repair Building 1024, Armory Expansion & Admin Conversion
## Camp Schwab, Okinawa, Japan | FY 2026 Special Projects Program | MCIPAC G-F PPE

**Project Number:** BU26PPE70M | **PAX ID:** 387356 | **iNFADS RPUID:** 148675 | **Category Code:** 14346 (per PAX 1391 dated 09 Apr 2026; verify against workbook records that show 14345) | **Total Building GSF:** 84,861 | **Scope-Affected Area:** 26,488 SF (1st floor renovation)

All amounts in $000 to the dollar. All facts in this file are verified from three artifacts the operator provided 26 Apr 2026: the PAX Block 9 Data screen (IMG_0179.jpeg), the Associated Costs dialog (ASSOCIATED_COSTS.png), and the printed FY 2026 Special Projects Program form (M67400_BU26PPE70M_2026.pdf, Bil Hawkins Branch Chief approval 09 Apr 2026, Justus OConnor PWO approval 21 Apr 2026).

---

## How PAX is coded today for SCH-1024 (operator-verified state, 26 Apr 2026)

PAX Block 9 Data screen has these columns in the items table: ID, Description, Classification of Work, Work Type, UM, Quantity, Unit Cost, Total Cost ($000). The toolbar above the table provides four buttons: Add (+), Delete (X), Dollar item ($), and Percent item (%). The Associated Costs button opens a dialog with four percent fields:

- Contingency
- Supervision, Inspection, and Overhead
- Design Build (required field; asterisk indicates required)
- Planning and Design

Current state values, verified directly from the screenshots and the printed form:

- Block 9 Data top-right boxes: Subtotal ($000) 10,412 and Total Request ($000) 10,412
- The items table contains 18 rows total: one iNFADS-locked building row plus eleven scope rows plus six cost-rollup adder rows
- The iNFADS-locked building row is the green-highlighted top item: Description "MULTI PURPOSE BEQ/BOQ/CO HQS", Classification of Work C, Work Type RM, UM SF, Quantity 1.00, Unit Cost 10,412,000.00, Total Cost ($000) 10,412
- The eleven scope rows are entered as dollar items with UNIFORMAT II Level 2 prefixes (B20, C10, C30, D20, D30, D40, D50, E20, F20, G10, G20) and discipline-first descriptions
- The six cost-rollup adders are also entered as DOLLAR line items in the items table (not as percent items via Associated Costs):
  - Contingency: $552 ($000)
  - LSH (Life Safety and Health Allowance, 2.5% of iNFADS PRV $96,523,347): $2,413
  - Planning and Design (6% of Construction Base): $509
  - SIOH (Supervision, Inspection and Overhead, 8%): $679
  - CM (Construction Management, 4% of Construction Base): $339
  - DB Design (Design-Build Design, 4% of Total Funded): $401
- All four Associated Costs percent slots are set to 0.00%
- Printed FY 2026 Special Projects Program form rollup section shows: Subtotal 10,412, Contingency (0.0%) 0, SIOH (0.0%) 0, Total Funded Cost 10,412, Total Project Cost 10,412, Planning and Design (0%) (NON ADD) (0)

Because the adders are entered as dollar items and the percent slots are 0.00%, Subtotal equals Total Funded Cost equals Total Project Cost on the printed form ($10,412K).

## Proposed entry method change

Move the six cost-rollup adders OUT of the items table as dollar items and enter them via the Associated Costs dialog as percentages. This addresses the reviewer-stated preference that the rollup adders not appear as line items in the Block 9 items list.

Items table after change (scope only):

1. iNFADS-locked building row (unchanged; not editable): MULTI PURPOSE BEQ/BOQ/CO HQS, C, RM, SF, 1.00, 10,412,000.00, 10,412
2-12. Eleven scope rows with UNIFORMAT prefixes removed and descriptions rewritten in plain English. Dollar values unchanged from current state. Sum: $5,519K (rounded $000s; $5,520.182 from workbook).

Associated Costs dialog after change:

- Contingency: 10.00 %
- Supervision, Inspection, and Overhead: 8.00 %
- Design Build: 4.00 %
- Planning and Design: 10.00 % (covers NAVFAC Design 6% plus Construction Management 4% combined; PAX has no native CM slot)

## Open methodology call: LSH placement

PAX's Associated Costs dialog has four percent slots, none of which is Life Safety and Health. The $2,413K LSH amount cannot be entered as a percent through Associated Costs. Two options preserve the dollar value:

Option 1 - Retain LSH as a single dollar line item in the items table, named "Life Safety and Health Allowance, 2.5% of iNFADS PRV $96,523,347 per NAVFAC 11010.44E CH-1 / MCO 11000.12". Items table then has 13 rows total (iNFADS-locked + 11 scope + LSH).

Option 2 - Bake the $2,413K LSH amount into the scope total (eliminate the discrete LSH line; allocate proportionally across the eleven scope rows or to the building row). Block 10 narrative discloses the LSH share and authority.

Both options preserve the dollar value. Methodology call to be made before PAX entry. The current PAX state (Option 1, LSH as a dollar line item) is the simplest path.

## Verification step required at PAX entry

PAX's internal base for each Associated Costs percentage has not been verified outside the current all-zero state. The exact resulting Total Project Cost on the printed form after the proposed change cannot be predicted without seeing PAX render it.

Workbook target Total Funded Cost: $10,012,635 ($10,012K rounded).
Workbook target Total Project Cost: $10,413,140 ($10,413K rounded).

Steps at PAX entry:

1. Make the change in PAX (delete the six adder dollar items; enter the four Associated Costs percentages).
2. Save and re-render the printed FY 2026 Special Projects Program form.
3. Compare the printed Subtotal, Contingency, SIOH, Total Funded Cost, Total Project Cost against the workbook target values.
4. If a delta exists, the resolution is one of: change LSH option (1)/(2), adjust the percentage rates to match PAX's computation against its base, or adjust the workbook to match PAX's methodology.
5. Document the chosen reconciliation in CEPBKUP ESTIMATE Section F-11.

## Renamed scope line items (UNIFORMAT prefixes removed; descriptions rewritten in plain English; dollar values unchanged)

The renamed descriptions below are based on the printed 1391 (M67400_BU26PPE70M_2026.pdf) which shows truncated descriptions. At PAX entry the operator confirms each current full description and applies the proposed rewrite. Dollar values are taken from the printed form; sum = $5,519K (workbook subtotal $5,520.182K).

| Row | Current description (per printed 1391) | Proposed renamed description | UM | Cost ($000) |
|-----|----------------------------------------|------------------------------|----|------------:|
| 1 | B20 - Exterior Enclosure: CMU infill and weapons port wi... | Exterior Enclosure - CMU infill at 28 weapons port openings | LS | 267 |
| 2 | C10 - Interior Construction: vault doors, structural walls, p... | Interior Construction - vault doors, structural walls, partitions, COMM room, OSS entrance | LS | 401 |
| 3 | C30 - Interior Finishes: paint, VCT, CT tile, bathroom and ... | Interior Finishes - paint, VCT, ceiling tile, bathroom and OSS finishes, armory spaces | LS | 190 |
| 4 | D20 - Plumbing: fixture capping, removal, new water foun... | Plumbing - fixture capping, water fountains, OSS plumbing removal | LS | 195 |
| 5 | D30 - HVAC: ceiling realign, exhaust, split A/C, DX multi-z... | HVAC - chillers, exhaust, split A/C, DX multi-zone, ceiling realign, TAB | LS | 1,674 |
| 6 | D40 - Fire Protection: fire hose cabinet replacement, 4 EA... | Fire Protection - fire hose cabinet replacement, 4 EA per NFPA 10 | LS | 22 |
| 7 | D50 - Electrical and Communications: ... | Electrical and Communications - IDS/ESS, WAOs, SIPR network, telecom room, OSP/ISP, lighting | LS | 1,801 |
| 8 | E20 - Furnishings: stainless steel shelves at 11 weapons... | Furnishings - stainless steel shelves at 11 weapons issue port windows | LS | 14 |
| 9 | F20 - Selective Demolition: window/door, ceiling, OSS gut, ACM... | Selective Demolition - window/door, ceiling, OSS gut, ACM mastic abatement per Bhate 2001 | LS | 432 |
| 10 | G10 - Site Preparation: tree removal at exterior pad locations | Site Preparation - tree removal at six new exterior pad locations | LS | 19 |
| 11 | G20 - Site Improvements: walkways, landings, concrete pads, covered overhangs, pavilion | Site Improvements - walkways, landings, concrete pads, covered overhangs, pavilion | LS | 504 |

Sum of rows 1-11: 267 + 401 + 190 + 195 + 1,674 + 22 + 1,801 + 14 + 432 + 19 + 504 = 5,519. Workbook subtotal $5,520.182 (one $K of rounding difference, consistent with the $000 rounding convention on the printed form).

## CCN discrepancy to verify

The printed 1391 shows Category Code 14346. The workbook records show 14345. This is a one-digit difference. Confirm against iNFADS at PAX entry. If iNFADS shows 14346, update the workbook. If iNFADS shows 14345, correct the PAX entry.

## What does not change

- Dollar values (every line and total to the dollar against the workbook).
- Building line locked from iNFADS (Description, Class of Work, Work Type, UM, Quantity, all not operator-editable).
- Scope content (the eleven scope rows describe the same physical work; only the description text changes).
- The six adder amounts (only their entry method changes from dollar items to Associated Costs percentages, except LSH which depends on the methodology call above).

## Block 10 paired statement (PRIMARY FACILITY PS)

PRIMARY FACILITY (PS): "This project converts and renovates 26,488 SF of the first floor of Building 1024, an existing 84,861 SF four-story facility (FAC 7210 BEQ / FAC 4421 CIF / FAC 6102 Admin / FAC 4427 Armory) at Camp Schwab. Scope includes 28 barracks rooms converted to 14 armory vaults with GSA Class V vault doors, gym-to-workspace conversion, OSS vault with SIPR-capable workspace, communications room and weapons cleaning area, restroom and laundry conversions, building-wide chiller and HVAC replacement, telecom infrastructure modernization per UFC 3-580-01, and exterior site improvements. Functions provided: armory storage, OSS workspace with SIPR, administrative space for 4th Marine Regiment and CLB-4. Life Safety and Health upgrades are funded at 2.5% of iNFADS PRV $96,523,347 per NAVFAC 11010.44E CH-1 and MCO 11000.12 (08 Sep 2014). Equipment included in the unit cost; no equipment from other appropriations."
