# Validation Rules  

This document outlines the validation rules for the Trello JSON → V13 Ledger CSV converter. These rules define what constitutes a violation, when errors block conversion, and what is allowed in test mode. They ensure that the converter enforces ledger invariants without changing ledger meaning.  

## Violation Types  

- **Blocking error**: Conditions that prevent conversion and must be resolved before processing.  
- **Warning**: Conditions that can be ignored in test mode but should be addressed.  

## Required Invariants  

- All transactions must map to valid categories and subcategories.  
- Split transactions must inherit their parent attributes.  
- Amounts must be absolute values with direction controlled by transaction type. 
