# V13 Ledger Output Schema Specification

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines the exact structure of the Ledger-ready CSV output
for Budget & Ledger System --- Version 13.

The Agent must strictly follow:

-   Column names
-   Column order
-   Required fields
-   ID formatting rules
-   Split handling rules

No column may be added, removed, or reordered unless version is
incremented.

------------------------------------------------------------------------

## 2. Ledger Output Columns (Authoritative Order)

The Ledger CSV must contain columns in the following exact order:

1.  Transaction ID
2.  Parent Transaction ID
3.  Posted Date
4.  Authorized Date
5.  Description
6.  Parent
7.  Child
8.  Amount
9.  Notes

------------------------------------------------------------------------

## 3. Column Definitions

### 1. Transaction ID

-   Source: Trello Card ID
-   For split rows: append suffix
    -   Example: abc123-1, abc123-2
-   Must be unique per row

### 2. Parent Transaction ID

-   For non-split rows: same as Transaction ID
-   For split rows: original Trello ID (without suffix)

### 3. Posted Date

-   Parsed from Trello card title
-   If only one date present → Posted Date
-   Format: YYYY-MM-DD

### 4. Authorized Date

-   If two dates exist in title → second date is Authorized Date
-   If not present → blank

### 5. Description

-   Parsed from Trello card title (excluding dates and amount)
-   Must preserve original transaction description

### 6. Parent

-   Must match canonical parent name from Parent Registry
-   Case-sensitive output, case-insensitive detection

### 7. Child

-   Must match canonical child name from Parent → Child Taxonomy
-   Case-sensitive output, case-insensitive detection

### 8. Amount

-   Parsed from Trello card title
-   Negative for expenses
-   Positive for deposits
-   Numeric format only (no currency symbols)

### 9. Notes

-   Contains Trello card URL only
-   No prefix text
-   No additional formatting

------------------------------------------------------------------------

## 4. Split Handling Rules

If SPLIT label present:

1.  Parent row amount becomes 0.
2.  Child rows are created for each split component.
3.  Child rows receive Transaction ID suffix:
    -   TrelloID-1
    -   TrelloID-2
4.  Parent Transaction ID references original Trello ID.
5.  Sum of split child rows must equal original amount.

------------------------------------------------------------------------

## 5. Validation Requirements

The Agent must ensure:

-   All required columns are present.
-   Column order is exact.
-   No additional columns are added.
-   IDs are unique.
-   Amount field is numeric.
-   Parent and Child fields comply with taxonomy.

------------------------------------------------------------------------

## 6. Prohibited Behavior

The Agent must NEVER:

-   Guess missing dates
-   Guess parent category
-   Guess child category
-   Modify amount formatting beyond numeric normalization
-   Insert additional metadata columns

------------------------------------------------------------------------

## 7. Version Control

This schema applies to:

Budget & Ledger System --- V13

Changes require:

-   Version increment
-   Updated schema document
-   Workbook alignment
-   Agent update

------------------------------------------------------------------------

End of Document
