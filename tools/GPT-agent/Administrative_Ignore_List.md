# V13 Administrative Ignore List

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines all Trello labels that are considered:

-   Workflow management labels
-   Administrative markers
-   Non-financial indicators

These labels must be completely ignored during:

-   Parent detection
-   Child detection
-   Structural detection
-   Ledger classification
-   Validation mapping

They do NOT participate in any financial logic.

------------------------------------------------------------------------

## 2. Administrative Labels (Authoritative List)

The following labels are administrative and must be ignored by the
converter:

-   !
-   ?
-   ADDED
-   Deposit
-   Not adding to budget
-   Return
-   Returned
-   Returning

------------------------------------------------------------------------

## 3. Behavior Rules

For any transaction:

1.  Remove administrative labels before structural validation.
2.  Remove administrative labels before parent-child matching.
3.  Administrative labels must NOT:
    -   Trigger REVIEW
    -   Affect validation reports
    -   Affect classification logic

They are invisible to the ingestion engine.

------------------------------------------------------------------------

## 4. Case Sensitivity Policy

Administrative label matching is:

-   Case-insensitive
-   Trimmed for whitespace

Canonical casing is preserved in Trello but ignored in processing.

------------------------------------------------------------------------

## 5. Prohibited Behavior

The Agent must NEVER:

-   Treat administrative labels as structural
-   Treat administrative labels as parents
-   Treat administrative labels as children
-   Report administrative labels as unknown

------------------------------------------------------------------------

## 6. Version Control

This ignore list applies to:

Budget & Ledger System --- V13

Changes require:

-   Version increment
-   Update to this document
-   Re-validation of ingestion pipeline

------------------------------------------------------------------------

End of Document
