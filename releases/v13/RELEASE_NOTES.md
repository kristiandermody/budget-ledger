# Budget & Ledger — Version 13.0 Release Notes


**Release Date:** February 2026

## Purpose
Version 13 is the first fully governed architecture of the Budget & Ledger system.

## Highlights
- Defined structured money flow model: Deposits (Income, Refunds, etc.) → Unassigned → Transfers → Budget / Savings & Flex.
- Centralized Transfers control for all reallocations.
- Introduced Savings & Flex to track long‑term balances and reconciliation.
- Added Refund handling as negative expenses.
- Formalized governance rules: dates and amounts immutable; labels can change; ledger dates never drive budget logic; all income must enter through Deposits; all reallocations via Transfers; month closes at zero Unassigned; no circular references or hidden logic.
- Introduced Trello JSON → CSV validation pipeline with error reporting.
- Added TEST MODE to override validation for development purposes.

## Removed
- Implicit reallocation and date-driven budget logic.
- Auto-balancing shortcuts and circular formulas.
- Over-automation attempts from version 12.2.

## Known Edge Cases
- Checking vs Savings & Flex mismatch.
- Surplus after allocation.
- Multi-parent split transactions.
- New categories introduced mid‑month.

## Stability Declaration
Version 13 is considered architecturally stable and production ready. All future development must branch from this version.