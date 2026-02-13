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

## Tooling  
Trello JSON → Ledger CSV, Converter Tool Readme
[/tools/trello-json-to-v13/README.md](/tools/trello-json-to-v13/README.md)

The repository contains optional tooling that assists with data ingestion and validation. Tooling is:  
- Not required for operating V13 manually  
- Versioned independently  
- Structured under `/tools/`  

Current tools:  
- Trello JSON → V13 Ledger CSV converter  

Tooling represents the beginning of V14 automation but does not modify V13 architecture. 
