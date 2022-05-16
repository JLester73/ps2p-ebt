# ps2p-ebt
PowerSchool to P-EBT Report


This report extracts the data needed to do the P-EBT student upload for school nutrition.  You'll need the paid sqlReports add-on for PowerSchool.

You'll need to modify "Washington County Public Schools" to your division.  You'll also likely need to modify the last part of the query where we are excluding our special schools, our Region 7 Virtual Academy students, and students in homebound/homebase.

You  still have to manipulate it in Excel, but that only takes about 5-10 minutes per file:
- Add a sheet called Alphacodes for vlookup of the L, M, H values.  First column has numbers from 1-30, the second column matches up L, M, H with those numbers.
- Add a column Q to export sheet called Count with the formula "=countif(student number column range, stustudentnumber)".  Real example: "=COUNTIF(M:M,M2)"
- Add a column R to export sheet called Alphacode with the formula "=vlookup(count column, vlookup sheet table, column 2)".  Real example: "=VLOOKUP(Q1,Alphacodes!$A$2:$B$31,2)"
- Add a sheet for the actual data we'll export with the column headings they want.  Copy and paste columns in as values to the new sheet.  Leave off the attendance code, attendance date, and count columns.
- Remove duplicates from the entire sheet, this collapses each student down to one line.
- Do a search and replace for address column and replace any commas with spaces.
- Do a search and replace for name columns and replace any parentheses with spaces
- Export out the sheet as a CSV file
