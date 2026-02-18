# Budget & Ledger

This repository contains a structured budget and ledger system designed for rigorous financial tracking, deterministic transaction ingestion, and governed category taxonomy control.

---

## Project Stage

The system is currently in MVP stabilization phase.

Major versions indicate structural evolution of the ledger architecture.  
Backward compatibility is not guaranteed until v1.0.

---

## Overview

- **Architecture:** See `/architecture/` for complete system design documentation.
- **Operating Guide:** See `/operating/` for workbook operating guidance.
- **Change Log:** See [CHANGELOG.md](CHANGELOG.md)
- **Releases:** See `/releases/` for versioned release notes and snapshots.
- **Roadmap:** See `/roadmap/` for future development direction.

---

## Governance & Change Policy

This system follows structured governance discipline.  
Schema changes, structural refinements, and versioning policies are documented under:

- `/governance/versioning_policy.md`
- `/governance/`

Major structural changes increment the major version number.  
Minor refinements increment minor versions.  
Documentation and internal improvements may increment patch versions.

---

## Tooling

The repository includes optional automation tooling.

### Trello JSON → Ledger CSV Converter

- Transforms Trello JSON exports into structured Ledger CSV format.
- Enforces governance rules.
- Produces validation reports.
- Operates against the current governance schema.

### GPT Agent

Defines a GPT-driven automation layer that:

- Converts Trello JSON exports to Ledger CSV.
- Enforces governance rules deterministically.
- Produces structured validation reports.
- Does not modify governance files.

Tooling is optional and does not alter system meaning.

---

## System Requirements

### Core Requirements

- Spreadsheet software (e.g., Excel)
- Trello (for transaction capture and JSON export)

### Automation (Optional)

If using GPT-based ingestion:

- ChatGPT with configured governance files
- Trello JSON export

### Local Tooling (Optional)

If using CLI-based conversion:

- Python 3.x
- Command-line interface (CLI)
- JSON processing capability
- Properly configured governance files
---

## Directory Structure

- `/architecture/` – System design documentation  
- `/operating/` – Workbook operating guidance  
- `/governance/` – Versioning and schema change discipline  
- `/tools/` – Automation tools  
- `/releases/` – Versioned release notes with associated .xlsx files  
- `/roadmap/` – Future direction documentation  

---

For full change history, see `CHANGELOG.md`.  
For version snapshots, see `/releases/`.