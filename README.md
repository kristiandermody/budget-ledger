# Budget & Ledger  

This repository contains a structured budget and ledger system. Version 13.1 is the current release, introducing a minor structural refinement to the ledger while keeping the v13 architecture as the foundation.  

## Overview  
- **Architecture:** See [architecture/v13.md](/architecture/v13.md) for the complete design, money flow model, governance rules, and system constraints.  
- **Architecture Addendum (v13.1):** See [architecture/v13.1.md](/architecture/v13.1.md) for details of the ledger dimensional formalization and other refinements introduced in v13.1.  
- **Operating Guide:** See [operating/v13.md](/operating/v13.md) for instructions on using the workbook, recording income, expenses, transfers, refunds, and closing each month.  
- **Operating Addendum (v13.1):** See [operating/v13.1.md](/operating/v13.1.md) for guidance on entering transactions under the new v13.1 structure.  
- **Change Log:** See [CHANGELOG.md](CHANGELOG.md) for a record of all notable changes across versions.  
- **Release Notes:** See [releases/v13/RELEASE_NOTES.md](/releases/v13/RELEASE_NOTES.md) and [releases/v13.1/RELEASE_NOTES.md](/releases/v13.1/RELEASE_NOTES.md) for details of the v13 and v13.1 releases.  

Version 13 remains architecture-locked; v13.1 is a minor structural refinement. Any major architectural changes will be introduced in v14. The roadmap for v14 is available under [roadmap/v14.md](/roadmap/v14.md). 

## Governance & Change Policy
Detailed version increment rules, commit classification standards, branch lifecycle practices, and release discipline are defined in `/governance/versioning_policy.md`.

## Tooling

The repository contains optional tooling that assists with data ingestion, validation, and automation workflows.

Tooling is:

- Not required for operating V13 manually
- Versioned independently from core architecture
- Structured under `/tools/`
- Part of the evolving V14 automation layer

---

### Trello JSON → Ledger CSV Converter (CLI / Python)

[/tools/trello-json-to-ledger-csv/README.md](/tools/trello-json-to-ledger-csv/README.md)

This tool is a command-line Python-based converter that:

- Transforms Trello JSON exports into V13-compatible Ledger CSV format
- Enforces validation rules
- Produces structured error and validation reporting
- Preserves ledger invariants without modifying system meaning

This tool supports automated transaction ingestion while maintaining strict architectural boundaries.

---

### Trello JSON → Ledger CSV Converter GPT Agent

[/tools/GPT-agent/README.md](/tools/GPT-agent/README.md)

This tool defines a GPT-driven automation layer for structured ledger conversion workflows.

It provides:

- Ledger output schema definitions
- Parent/child taxonomy structures
- Structural label registry
- JSON interpretation specifications
- Validation reporting specifications
- Governance workflow definitions

The GPT Agent represents an advanced automation interface layered on top of the core system. It does not alter V13 architecture, ledger meaning, or governance rules.

---

Tooling represents the early foundation of V14 automation but does not modify V13 architecture or system meaning.

## System Requirements

The Budget & Ledger system may be operated manually or with optional tooling that supports convertings Trello JSON Exports to ledger friendly CSV format.

Core requirements:

- Microsoft Excel
- Structured budget workbook (see `/releases/`)

Optional tooling requirements (for automated data ingestion):

- Trello
- Python 3.x
- JSON → CSV converter tool (located under `/tools/trello-json-to-ledger-csv/`)

Manual operation of V13 requires only Excel.
Tooling enables structured transaction import and validation workflows.
