# Trello JSON → V13 Ledger CSV Converter — CHANGELOG

This changelog tracks changes specific to the Trello JSON → V13 converter tool.

It does NOT track changes to:
- Ledger architecture  
- Workbook structure  
- Budget model  
- Allocation model  

Those changes belong in the root CHANGELOG.md.

---

## Versioning Strategy

This tool follows Semantic Versioning:

MAJOR — Breaking changes to conversion behavior  
MINOR — New features or validation rules  
PATCH — Internal refactors or non-breaking fixes  

Compatibility with Ledger versions is documented in the tool README.

---

## [Unreleased]

### Added
- Initial converter scaffolding  
- config/ directory for category and label mappings  
- validation/ directory for rule documentation  
- tests/ directory for test case documentation  

### Changed
- Refactored src directory into proper Python package structure  
- Added __init__.py to establish package boundary  

---

## [0.1.0] - Initial Tool Scaffold
- Created initial converter structure  
- Added documentation and directory layout
