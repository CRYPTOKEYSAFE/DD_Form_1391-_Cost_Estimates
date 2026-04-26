**To:** Robert W. Kaye, RA - Planning Director, NAVFAC FEAD
**Cc:** Bil Hawkins, P.E., PMP - Deputy PWO, MCB Camp Butler G-F
**From:** Anthony L. Potter - Facilities Planner, MCIPAC G-F PPE, Booz Allen Hamilton
**Subject:** Camp Schwab FY26 Block 9: PAX Coding Review for the Five-Building Portfolio

Rob,

I went into the PAX 1391 Processor for the Camp Schwab FY26 portfolio (SCH-1024, SCH-3213, SCH-3237, SCH-3270, SCH-3314), pulled the printed 1391 for SCH-1024, and walked the current Block 9 entry against the May 2024 CRB Guidelines. SCH-1024 is the worked example. These five are out-of-cycle FSRMs (FSRM Straddlers), programmed in FY26 with the possibility of a Q1 FY27 award. Fund type is O&MMC. The local rates we apply (Contingency, SIOH, NAVFAC Design, Construction Management, LSH, DB Design) are settled under MCIPAC G-F, NAVFAC 11010.44E CH-1, and MCO 11000.12. The depiction on the face of the printed form is what this email is about. Four PDFs are attached: the signed FY 2026 1391 for Building 1024 (the current state in PAX, what this email walks through), the CRB Guidelines (the published reference for Block 9 line-item structure), the PAX 1391 Coding Walkthrough (a narrative that steps through the SCH-1024 entry, lists the renamed scope lines, and explains the proposed change), and the PAX Block 9 Data Flow with BEFORE and AFTER (a one-page visual whose top half maps each piece of data from its source through PAX entry to where it lands on the printed form, and whose bottom half shows the SCH-1024 items table side by side, before and after the proposed change).

How PAX codes Block 9. Two operator inputs feed one rendered output. The Block 9 Data screen holds an items table with eight columns: ID, Description, Classification of Work, Work Type, UM, Quantity, Unit Cost, and Total Cost ($000). The first row is the iNFADS-supplied building line and is not operator-editable. Below it the operator adds rows as either dollar items (a fixed amount) or percent items (a rate computed against a PAX-internal base). The Associated Costs dialog opens from the same screen and holds four named percent fields: Contingency, Supervision Inspection and Overhead, Design Build (required), and Planning and Design. The printed FY 2026 Special Projects Program form is rendered from the items table plus the Associated Costs entries. Subtotal equals the items list sum, with rollup rows printed below for Contingency, SIOH, Total Funded Cost, Total Project Cost, and Planning and Design (NON ADD). The exact print position of each percent item once non-zero will be verified at entry.

Current SCH-1024 entry. The items table holds 18 rows: the iNFADS-locked building line, 11 scope rows with UNIFORMAT II Level 2 prefixes (B20 through G20) entered as dollar items, and 6 cost rollup adders also entered as dollar items (Contingency, LSH, Planning and Design, SIOH, CM, DB Design). All four Associated Costs percent slots are at 0.00 percent. Because the adders are already absorbed as dollar items and the percent slots are zero, the printed Subtotal, Total Funded Cost, and Total Project Cost are all $10,412K. Math is internally consistent; the question is just where each piece lives in the data model.

What the references say. CRB Guidelines §3.1 sequences Block 9 line items by facility and function name. The word UNIFORMAT does not appear in the 93-page document. §§3.3, 3.4, and 3.5 address Contingency, SIOH, and DB Design as percent-based adders; the AF exemplars in the prior reference set show those adders as percent rollup lines below the items list. The Guidelines do not address LSH, the 6 percent NAVFAC Design, or the 4 percent Construction Management, since those are FSRM Marine Corps program adders outside the MCON / MCNR scope of the document. The local rates are documented in the cost estimate workbook at Section F-11.

Proposed coding change for SCH-1024, mirrored across the other four when ready. Strip the UNIFORMAT prefixes from the 11 scope rows and rewrite the descriptions in plain English. Move Contingency 10.00 percent, SIOH 8.00 percent, Design Build 4.00 percent, and Planning and Design 10.00 percent into the Associated Costs dialog. Planning and Design 10.00 percent covers the NAVFAC 6 percent Design plus 4 percent CM combined, since PAX has no native CM percent slot; the breakout is disclosed in the Block 10 narrative. Dollar values do not change. The attached diagram shows the data flow on the top half and the BEFORE / AFTER side by side on the bottom half.

LSH note. The 2.5 percent of PRV LSH allowance ($2,413K for SCH-1024) is required in the project. The Guidelines are silent on Block 9 placement and PAX has no LSH percent slot. Two options preserve the dollar value: keep LSH as one dollar line item in the items table (the current PAX method), or fold the LSH amount into the scope total with the breakout disclosed in Block 10. I would like to walk through this with the team before we settle on the depiction.

Cost estimates and scope are still being refined for several of the five buildings before submission, so the printed form numbers will continue to move through the cycle. This email is about the depiction approach, not the dollar values. Open to a walk-through on SCH-1024 whenever works for you.

V/R,

Anthony Potter
Facilities Planner | MCIPAC G-F PPE
Booz Allen Hamilton

Attachments (all PDFs):
- Signed FY 2026 1391 for Building 1024 (current PAX state, for reference)
- Consistency Review Board 1391 Development Guidelines, 22 May 2024 Edition
- PAX 1391 Coding Walkthrough, SCH-1024
- PAX Block 9 SCH-1024 Data Flow with BEFORE and AFTER (one-page diagram)
