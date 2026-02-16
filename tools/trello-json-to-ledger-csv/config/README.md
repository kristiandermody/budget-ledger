# Configuration Layer

This directory contains the configuration files used by the Trello JSON → Ledger CSV converter tool.

These files define the structural controls that allow Trello transaction data to be translated into a governed V13 Ledger format.

This directory is part of the tool layer and does not modify or redefine V13 ledger architecture.

---

## Purpose

The configuration layer exists to provide:

- Controlled category definitions
- Trello label translation rules
- Structural validation inputs for the converter
- Protection against classification drift

Trello is flexible by design.  
The V13 Ledger is structured and governed.  

This configuration layer bridges that gap.

---

## Files

### `category_master.csv`

Authoritative registry of valid ledger classifications.

This file defines:

- What categories are allowed
- How categories relate to one another
- Which classifications are considered valid for conversion

It functions as the structural validation source for the converter.

No category should exist in the ledger output unless it is represented here.

---

### `label_mapping.csv`

Translation layer between Trello labels and ledger classifications.

This file defines:

- How Trello labels are interpreted
- Which ledger classification a label maps to
- How user input becomes structured ledger data

All Trello labels used for transaction classification must be mapped here.

If a label is not mapped, the converter should treat it as a validation issue.

---

## Governance Rules

1. These files are tool-level configuration artifacts.
2. Changes to these files affect conversion behavior.
3. Changes do not alter V13 ledger architecture.
4. Any structural changes should be accompanied by:
   - Tool version review
   - Tool CHANGELOG update
5. Categories should not be created ad hoc in Trello without updating this configuration layer.
6. This directory is considered controlled infrastructure, not casual data.

---

## Design Philosophy

The converter tool is intentionally separated from ledger architecture.

The ledger defines structure.
This configuration layer enforces translation into that structure.

The goal is:

- Predictable classification
- Repeatable conversion
- Prevention of category drift
- Auditability of transformation logic

---

## Scope

This directory governs only the Trello JSON → Ledger CSV tool.

It does not:

- Define budget logic
- Define workbook calculations
- Redefine V13 architecture
- Modify ledger rules

Those concerns are documented in the root project documentation.

---

## Future Evolution

Schema refinements may occur as the tool matures.

Any evolution should maintain:

- Clear separation from ledger architecture
- Backward compatibility where possible
- Explicit documentation of structural changes
