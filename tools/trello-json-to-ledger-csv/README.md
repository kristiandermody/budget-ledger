# Trello JSON → Ledger CSV Converter (CLI)

Deterministic local conversion tool for the Budget & Ledger system.

This tool converts a Trello JSON export into:

- Ledger-ready CSV  
- Validation & Labor Report  

It operates under the same governance model as the GPT ingestion engine.

---

## Purpose

This tool provides a local, CLI-based implementation of the deterministic ingestion contract defined by the governance documents.

It does not define business rules.  
It enforces the rules defined in governance files.

---

## System Requirements

### Core Requirements

- Spreadsheet software (e.g., Excel)  
- Trello (for transaction capture and JSON export)  

---

### Optional: GPT-Based Automation

If using ChatGPT for ingestion instead of the CLI tool:

- ChatGPT (Custom GPT configured with governance files)  
- Trello JSON export  
- Properly aligned governance files  

---

### Optional: Local CLI Conversion

If using this CLI tool:

- Python 3.x  
- Command-line interface (CLI)  
- JSON processing capability  
- Properly configured governance files  

All governance files must originate from the same repository snapshot (tag, release, or commit).  
Do not mix governance files from different versions or branches.

---

## Installation (CLI Only)

From the repository root:

```bash
cd tools/trello-json-to-ledger-csv