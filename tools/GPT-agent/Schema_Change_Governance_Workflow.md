# V13 Schema Change & Governance Workflow

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines the required governance workflow for any schema
changes within the Budget & Ledger System --- Version 13.

Schema elements include:

-   Structural labels
-   Parent categories
-   Child categories
-   Parent → Child relationships
-   Ledger output schema

This workflow ensures:

-   Deterministic rebuild capability
-   Controlled taxonomy evolution
-   No silent schema drift
-   Workbook registry alignment

------------------------------------------------------------------------

## 2. Guiding Principles

1.  Trello is the transaction source of truth.
2.  The Parent → Child Taxonomy is a closed schema.
3.  The Workbook `_Data` sheet is the registry authority.
4.  The Agent must never mutate schema automatically.
5.  All schema changes require documentation update.

------------------------------------------------------------------------

## 3. Adding a New Child Category

When a new child label is created in Trello:

Step 1\
Run conversion.

Step 2\
If child is not in taxonomy: - It must appear in Validation Report under
Unknown Children. - REVIEW must be auto-added.

Step 3\
If approved:

-   Update V13_Parent_Child_Taxonomy.md
-   Update Workbook `_Data` registry
-   Commit change to version control (if applicable)

Step 4\
Re-run JSON conversion.

Step 5\
Confirm Validation Report is clean.

Manual edits to converted CSV are prohibited.

------------------------------------------------------------------------

## 4. Adding a New Parent Category

Requires:

1.  Update to V13_Parent_Category_Registry.md
2.  Update to Parent → Child Taxonomy document
3.  Update to Workbook `_Data` sheet
4.  Version increment (13.x → 13.x+1)
5.  Re-validation of entire ingestion pipeline

------------------------------------------------------------------------

## 5. Modifying Structural Behavior

Any changes to:

-   INCOME logic
-   SPLIT handling
-   Deposit enforcement
-   Structural mutual exclusivity

Require:

-   Update to V13_Structural_Label_Registry.md
-   Version increment
-   Full regression test of prior JSON files

------------------------------------------------------------------------

## 6. Validation Failure Policy

If Validation Report contains:

-   Structural Violations
-   Unknown Parents
-   Unknown Children
-   Invalid Parent-Child combinations

The Ledger CSV must NOT be imported until resolved.

------------------------------------------------------------------------

## 7. Deterministic Rebuild Requirement

The system must always support:

-   Re-running historical JSON files
-   Producing identical output under identical schema
-   Auditable schema version history

Manual corrections to output CSV break this guarantee and are
prohibited.

------------------------------------------------------------------------

## 8. Version Control Policy

All schema changes must:

-   Increment version number
-   Be documented
-   Be uploaded into Agent knowledge
-   Be synchronized with workbook registry

------------------------------------------------------------------------

## 9. Prohibited Behavior

The Agent must NEVER:

-   Auto-create new schema entries
-   Auto-append unknown children to taxonomy
-   Silently reassign parent-child relationships
-   Modify schema without documentation update

------------------------------------------------------------------------

End of Document
