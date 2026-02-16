# V13 Parent → Child Taxonomy

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines the authoritative Parent → Child mapping for
Budget & Ledger System --- Version 13.

This mapping is a closed taxonomy.

No child may be auto-created. No parent-child relationship may be
inferred. Unknown combinations must be flagged.

------------------------------------------------------------------------

## 2. Authoritative Parent → Child Mapping

### Cars

-   Car Maintenance
-   Fuel

### Debt

-   Car Payment
-   CC Payment
-   Credit Monitoring
-   Student Loan

### Education

(Currently no children assigned)

### Groceries & Food

-   Groceries
-   Prepared Food
-   School Lunch

### Housing

-   Data
-   Dry Cleaners (Tide)
-   House Maintenance
-   House Move
-   House Stuff
-   Housekeeping
-   Lease
-   Media
-   Prime
-   Water, Electric & Gas

### Insurance

-   Amy Life (Penn)
-   Kristian - Life (Penn)
-   Kristian - Life (USAA)
-   Car & Home Rental Insurance

### Legal

-   Attorney
-   Taxes

### Medical

-   Direct Care (PCP)
-   Medicine
-   Dog

### Miscellaneous

-   Appliance
-   ATM
-   Babysitter
-   Crafts
-   Date Night
-   Easter
-   Family
-   Gifts
-   Parking
-   Pictures
-   Pool
-   Postage
-   Shipping
-   Supplies
-   Tolls
-   Uber
-   Xmas Presents

### Nanny

(Currently no children assigned)

### Travel

-   Flights
-   Hotel
-   Car Rental
-   Spending Money

### Amy

-   Allowance 1
-   Allowance 2
-   Misc 1
-   Misc 2
-   Nails
-   Poker
-   Work Travel
-   Gift Income
-   Side Income
-   Payroll
-   Bonus
-   Sale
-   AppliedNet
-   Dog
-   Xmas Presents

### Emma

-   Apps
-   Birthday Presents
-   Clothing
-   General
-   School
-   Summer Camp
-   Summer Camp Stuff
-   Swim Lessons
-   Toys
-   Gift Income
-   Xmas Presents

### Grayson

-   Apps
-   Birthday Presents
-   Clothing
-   General
-   School
-   Summer Camp
-   Summer Camp Stuff
-   Swim Lessons
-   Toys
-   Gift Income
-   Xmas Presents

### Kristian

-   Allowance 1
-   Allowance 2
-   Misc 1
-   Misc 2
-   Poker
-   Work Travel
-   Gift Income
-   Side Income
-   Payroll
-   Bonus
-   Sale
-   Xmas Presents

### Other

-   Xmas Stuff
-   Tax Return

### Kids Activities

-   Birthday Party
-   Sports
-   After School Program

------------------------------------------------------------------------

## 3. Rules

1.  Parent detection is case-insensitive.
2.  Child detection is case-insensitive.
3.  Canonical casing must match this document in output.
4.  If Parent is valid but Child not listed → flag Unknown Child.
5.  If Child listed but used under wrong Parent → flag Invalid
    Parent-Child Pair.
6.  Agent must NEVER auto-create new children.
7.  Agent must NEVER auto-add new parent-child relationships.

------------------------------------------------------------------------

## 4. Version Control

This taxonomy applies to:

Budget & Ledger System --- V13

Any addition of a new child requires:

-   Update to this document
-   Update to workbook registry (\_Data sheet)
-   Re-run of JSON conversion

------------------------------------------------------------------------

End of Document
