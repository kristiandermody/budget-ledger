# V13 Parent Category Registry

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines the authoritative and closed set of valid Parent
Categories for the Budget & Ledger System --- Version 13.

No parent category outside this list is considered valid.

Parent categories determine:

-   Budget ownership
-   Domain grouping
-   Roll-up reporting
-   Ledger classification

------------------------------------------------------------------------

## 2. Authoritative Parent Category List

The following Parent Categories are valid:

1.  Cars
2.  Debt
3.  Education
4.  Groceries & Food
5.  Housing
6.  Insurance
7.  Legal
8.  Medical
9.  Miscellaneous
10. Nanny
11. Travel
12. Amy
13. Emma
14. Grayson
15. Kristian
16. Other
17. Kids Activities

------------------------------------------------------------------------

## 3. Parent Category Rules

-   Exactly one valid Parent must be assigned per non-SPLIT ledger row.
-   Parent detection is case-insensitive.
-   Canonical casing must match exactly as listed above.
-   Parents may not be auto-created.
-   Parents may not be inferred.
-   Unknown parents must be flagged in the Validation Report.

------------------------------------------------------------------------

## 4. Parent Semantics

Parent categories represent:

A. Functional Domains\
(Cars, Debt, Housing, etc.)

B. Person-Based Budgets\
(Amy, Emma, Grayson, Kristian)

C. Household-Level Domains\
(Miscellaneous, Other, Kids Activities)

Funding source (e.g., transfers from savings) does NOT affect Parent
classification.

------------------------------------------------------------------------

## 5. Prohibited Behavior

The Agent must NEVER:

-   Create new Parent categories
-   Guess intended Parent
-   Default unknown Parent to Miscellaneous
-   Silently reassign Parent values

Unknown Parent values must:

-   Trigger REVIEW
-   Be logged in Validation Report

------------------------------------------------------------------------

## 6. Version Control

This registry applies to:

Budget & Ledger System --- V13

Changes require:

-   Version increment
-   Update to this document
-   Update to Parent → Child mapping table
-   Re-validation of ingestion pipeline

------------------------------------------------------------------------

End of Document
