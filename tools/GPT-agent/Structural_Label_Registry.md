# V13 Structural Label Registry

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines:

-   All valid structural labels
-   Behavioral rules
-   Mutual exclusivity rules
-   Deposit enforcement logic
-   SPLIT handling behavior
-   REVIEW behavior
-   Validation requirements

Structural labels control **transaction behavior**, not classification.

------------------------------------------------------------------------

## 2. Structural Label List (Authoritative)

Detection is case-insensitive.\
Canonical output casing must match exactly as written below.

### Economic (Mutually Exclusive Group)

-   INCOME
-   REFUND
-   PASS-THROUGH

Only ONE may appear on a transaction.

If more than one appears → Structural Violation.

------------------------------------------------------------------------

### Behavioral

-   SPLIT

Indicates transaction must be divided into multiple ledger rows.

May combine with any structural label.

------------------------------------------------------------------------

### Control

-   REVIEW

Indicates transaction requires attention.

May combine with any structural label.

May be: - User-added in Trello - Auto-added by converter

Does not affect financial math.

------------------------------------------------------------------------

## 3. Structural Group Rules

### 3.1 Mutual Exclusivity

Only one of the following may exist per transaction:

-   INCOME
-   REFUND
-   PASS-THROUGH

If multiple detected: - Flag Structural Violation - Add to Validation
Report

------------------------------------------------------------------------

### 3.2 SPLIT Rules

If SPLIT present:

-   Parent transaction row retains original Trello ID
-   Child rows receive suffix:
    -   TrelloID-1
    -   TrelloID-2
    -   etc.
-   Parent Transaction ID field references original ID
-   Parent amount becomes 0 after split
-   Child rows contain distributed amounts

SPLIT may combine with: - INCOME - REFUND - PASS-THROUGH - REVIEW

------------------------------------------------------------------------

### 3.3 REVIEW Rules

REVIEW:

-   Does not change classification
-   Does not change math
-   Triggers workbook formatting
-   Is added automatically if:
    -   Unknown parent detected
    -   Unknown child detected
    -   Structural violation detected

------------------------------------------------------------------------

## 4. Deposit Logic Enforcement

If Amount \> 0:

Transaction must include exactly one of:

-   INCOME
-   REFUND
-   PASS-THROUGH

If none present: - Add REVIEW - Flag in Validation Report

If more than one present: - Structural Violation

------------------------------------------------------------------------

## 5. Expense Logic

If Amount \< 0:

-   No economic structural label required.
-   Parent and child required unless SPLIT.

------------------------------------------------------------------------

## 6. Case Sensitivity Policy

Structural label detection is:

-   Case-insensitive
-   Trimmed for whitespace

Canonical output casing:

-   INCOME
-   REFUND
-   PASS-THROUGH
-   SPLIT
-   REVIEW

------------------------------------------------------------------------

## 7. Prohibited Behaviors

The Agent must NEVER:

-   Auto-create new structural labels
-   Guess missing structural labels
-   Reclassify structural labels
-   Ignore structural conflicts
-   Downgrade structural violations silently

------------------------------------------------------------------------

## 8. Validation Requirements

The Agent must report:

-   Multiple economic labels
-   Missing required economic label on deposit
-   Invalid structural combinations

All structural violations must appear in the Validation Report.

------------------------------------------------------------------------

## 9. Version Control

This registry applies to:

Budget & Ledger System --- V13

Changes to structural behavior require:

-   Version increment
-   Updated registry document
-   Mapping re-validation

------------------------------------------------------------------------

End of Document
