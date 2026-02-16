# Changelog

All notable changes to this project will be documented here.

## v13.1.1 — Governance & Tooling Stabilization - 2026-02-15

### Governance
- Introduced formal versioning policy under `/governance/versioning_policy.md`
- Standardized commit classification (Feature, Docs, Refactor, etc.)
- Formalized branch lifecycle discipline and merge expectations
- Established semantic version alignment rules

### Repository Structure
- Introduced `/docs/` directory and reorganized documentation hierarchy
- Moved architecture documentation to `/docs/architecture`
- Moved operating guides to `/docs/operating`
- Cleaned and standardized folder structure
- Preserved file history during renames

### Tooling
- Renamed `trello-json-to-v13` to `trello-json-to-ledger-csv`
- Updated all references to reflect new tool naming
- Introduced `/tools/GPT-agent` automation scaffold
- Clarified separation between:
  - CLI-based Python converter
  - GPT-driven automation layer
- Updated root README to reflect tooling boundaries and system requirements

### Documentation
- Refined Tooling section for clarity
- Added System Requirements section
- Removed minor formatting artifacts

---

No architectural, ledger schema, or workbook changes were introduced in this release.
This patch release stabilizes governance, tooling structure, and repository organization.

## [13.1] - 2026-02-13

### Added
- Transaction Type column (Deposit / Expense)
- Transaction Classification column
- Trello Link column
- Hidden Signed Amount system column

### Removed
- Authorized Date column

### Structural
- Formalized Ledger dimensional modeling
- Added validation constraints
- Splits inherit parent direction

No architectural philosophy changes.

## [13.0] — February 2026

### Added
- Finalized money flow model and transfer control.
- Introduced Savings & Flex and governance rules.
- Added Trello JSON → CSV validation pipeline with reports.
- Added TEST MODE for validation overrides.
- Added release documentation and operating guide.

### Changed
- Transfers tab designated as authoritative movement layer.
- Ledger dates used only for historical reference.
- Refunds treated as negative expenses.
- Surplus handling requires explicit transfers.
- Governance rules enforced across workbook.

### Removed
- Implicit reallocation and date-driven budget logic.
- Circular reference formulas and auto-balancing shortcuts.
- Over-automation attempts from previous version 12.2.

### Stability
- Architecture locked, governance enforced, production ready.

## [12.3.1] — February 2026

- Added dedicated Monthly Ledger page and clarified separation between budget template and ledger.
- Defined JSON → CSV manual paste workflow.

## [12.3] — February 2026

- Added Deposits and Refunds tabs with standardized headers and baseline fields.
- Styled tabs to match workbook.

## [12.2] — Reverted

- Reverted attempted automation due to complexity.

## [12.1]

- Added parent/child category labeling and split transaction logic.
- Clarified that dates and amounts are immutable.

## [12.0]

- Established governance reset: transaction dates and amounts are never modified; labels may change for reclassification.

## [11.4] — Stable Release

- Major styling improvements: header rows, fonts, line item formatting.
- Debugged and removed circular references.

## [11.0 – 11.3]

- Introduced Transfers worksheet and budget month column; separated expenses, deposits, transfers.

## [10.x] — Simplification Reset

- Removed complex automation and re-centered on manual clarity.

## [9.x] — Refactor Attempt (Abandoned)

- Attempted automation between sheets but found unstable.

## [6.x – 8.x]

- Experimental structures for transfer concepts; abandoned due to circular logic.

## [2.x – 5.x]

- Iterative builds exploring categories and manual tracking.

## [1.0]

- Initial concept: basic budget and ledger workbook with manual workflows.
