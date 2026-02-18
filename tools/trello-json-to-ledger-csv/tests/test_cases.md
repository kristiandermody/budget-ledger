# Test Cases — Trello JSON → Ledger CSV

This document defines expected validation behavior for the Trello JSON → Ledger CSV converter.

Each test case specifies:

- Input scenario
- Expected validation result
- Expected CSV behavior

These tests validate structural and dimensional integrity only.

---

## 1. Valid Transaction — Deposit (Income)

**Scenario**
- Transaction Type: Deposit
- Economic Classification: Income
- Valid Category/Subcategory
- Positive Amount

**Expected Result**
- Pass validation
- CSV row generated
- Sign handled internally

---

## 2. Valid Transaction — Expense (Standard)

**Scenario**
- Transaction Type: Expense
- Economic Classification: Standard
- Valid Category/Subcategory
- Positive Amount

**Expected Result**
- Pass validation
- CSV row generated
- Internal sign set correctly

---

## 3. Refund (Expense Reversal)

**Scenario**
- Transaction Type: Deposit
- Economic Classification: Refund
- Valid Category/Subcategory
- Positive Amount

**Expected Result**
- Pass validation
- CSV row generated
- Classified correctly as Refund
- Does not increase Income totals in ledger

---

## 4. Invalid Transaction Type

**Scenario**
- Transaction Type: "Credit"
- Valid other fields

**Expected Result**
- Fail validation
- No CSV output generated

---

## 5. Negative Amount Entered

**Scenario**
- Amount: -100
- Valid other fields

**Expected Result**
- Fail validation
- Negative amounts rejected

---

## 6. Missing Category

**Scenario**
- Category blank or undefined
- Other fields valid

**Expected Result**
- Fail validation
- Error identifies missing taxonomy match

---

## 7. Invalid Parent/Child Category Pair

**Scenario**
- Category exists
- Subcategory does not belong to Category

**Expected Result**
- Fail validation
- Error identifies taxonomy mismatch

---

## 8. Split Transaction — Valid

**Scenario**
- Parent transaction defined
- Two split rows
- Splits inherit Transaction Type and Economic Classification
- Split amounts sum exactly to parent amount

**Expected Result**
- Pass validation
- CSV rows generated correctly

---

## 9. Split Transaction — Amount Mismatch

**Scenario**
- Parent amount: 100
- Split amounts sum to 90

**Expected Result**
- Fail validation
- Error indicates mismatch between parent and split totals

---

## 10. Split Transaction — Classification Override Attempt

**Scenario**
- Parent Classification: Standard
- Split row attempts Classification: Pass-Through

**Expected Result**
- Fail validation
- Classification must inherit from parent

---

## 11. Undefined Economic Classification

**Scenario**
- Classification not present in governance file

**Expected Result**
- Fail validation
- Error identifies invalid classification

---

## 12. TEST MODE — Undefined Category

**Scenario**
- Undefined category
- TEST MODE enabled

**Expected Result**
- Validation warning generated
- CSV output still produced
- Field may be left blank

---

## 13. TEST MODE — Split Mismatch

**Scenario**
- Split totals do not match parent
- TEST MODE enabled

**Expected Result**
- Validation warning generated
- CSV output may still be produced
- Structural mismatch clearly flagged

---

## 14. Zero Amount Transaction

**Scenario**
- Amount: 0

**Expected Result**
- Fail validation
- Zero-value transactions not permitted

---

## 15. Missing Required Field

**Scenario**
- Transaction missing Transaction Type or Classification

**Expected Result**
- Fail validation
- CSV output not generated

---

# Test Philosophy

Validation enforces structural and dimensional integrity.

It does not:

- Perform reconciliation
- Validate allocation balances
- Confirm Unassigned = 0
- Execute Transfers
- Modify ledger logic

Structural correctness is required before ledger import.