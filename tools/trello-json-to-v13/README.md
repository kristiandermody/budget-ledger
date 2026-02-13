# Trello JSON → V13 Ledger CSV Converter  
  
This tool converts Trello JSON exports into V13-compatible ledger CSV files. It is an optional tooling layer built on top of the V13 ledger architecture. Operating the ledger manually does not require this tool. The converter enforces ledger invariants without altering ledger meanings, and logs validation violations.  
  
## Structure  
- **src/** – contains conversion and transformation logic (no formulas).  
- **config/** – CSV files defining category master and label mappings.  
- **validation/** – documentation on validation rules and invariants.  
- **tests/** – sample JSON exports, expected CSV outputs, and test case documentation.  
  
## Version Compatibility  
This converter is versioned independently from the ledger. See the compatibility matrix below.  
  
| Converter Version | Compatible Ledger Versions |  
| --- | --- |  
| v1.x | V13.x |  
| v2.x | V14.x |  
  
## Usage  
Run the converter script with your Trello JSON export to produce a CSV file that can be imported into the V13 ledger workbook. See `validation/validation_rules.md` for information on validation and invariants.
