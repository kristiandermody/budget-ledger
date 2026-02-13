# Changelog
All notable changes to this project will be documented here.

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
