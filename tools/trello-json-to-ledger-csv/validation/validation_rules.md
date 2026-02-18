# Validation Rules — Trello JSON → Ledger CSV

This document defines the structural validation rules enforced by the Trello JSON → Ledger CSV converter.

These rules ensure that generated CSV output conforms to the active Ledger schema and governance definitions.

Validation applies before CSV output is produced.

---

## 1. Structural Requirements

Each transaction must include:

- Transaction Date (posted date)
- Transaction Type (Deposit or Expense)
- Economic Classification
- Category
- Subcategory
- Amount (positive value)

Transactions missing required structural fields will fail validation.

---

## 2. Transaction Type Rules

- Must be either `Deposit` or `Expense`.
- Determines structural direction and internal sign handling.
- Amounts must always be entered as positive values.
- Negative values are rejected.

---

## 3. Economic Classification Rules

Allowed values are defined by governance files.

For v13.1+, typical classifications include:

- Income
- Refund
- Pass-Through
- Standard

Classification must:

- Match allowed governance values
- Be valid for the given Transaction Type

Example:
- Refund must be a Deposit
- Standard typically applies to Expense

Invalid classification combinations will fail validation.

---

## 4. Category & Subcategory Rules

- Category and Subcategory must exist in the active governance taxonomy.
- Parent/child relationships must match governance definitions.
- Undefined labels will trigger validation failure (unless TEST MODE is enabled).

The converter does not auto-create new categories.

---

## 5. Split Transaction Rules

If a transaction is split:

- A parent transaction must exist.
- Split rows must:
  - Inherit Transaction Type
  - Inherit Economic Classification
- Split amounts must sum exactly to the parent amount.
- Split amounts must be positive values.

Mismatch between parent and split totals will fail validation.

---

## 6. Amount Validation

- Amounts must be numeric.
- Amounts must be positive.
- Zero-value transactions are not permitted.

Sign is managed internally based on Transaction Type.

---

## 7. Governance Consistency

Validation enforces rules defined in:

- Structural label registry
- Parent/child taxonomy
- Ledger schema definitions

The converter does not define these rules — it enforces them.

---

## 8. Version Awareness

Validation behavior is governed by the active schema and governance files loaded at runtime.

The converter does not hard-code ledger version logic.

Upgrading ledger versions may require updated governance files.

---

## 9. TEST MODE Behavior

When TEST MODE is enabled:

- Undefined categories may be left blank
- Certain structural violations may produce warnings instead of failures
- CSV output may still be generated despite violations

TEST MODE does not:

- Alter ledger invariants
- Modify allocation logic
- Bypass dimensional enforcement entirely

TEST MODE is intended for development and troubleshooting only.

---

## 10. What Validation Does NOT Cover

Validation does not:

- Perform bank reconciliation
- Validate allocation balances
- Confirm Unassigned = 0
- Execute Transfers
- Modify ledger history

Validation ensures structural correctness only.