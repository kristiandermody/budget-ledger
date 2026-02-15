# Test Cases  

This document contains sample test cases for the Trello JSON → V13 Ledger CSV converter. Each test case describes a JSON input, the expected CSV output, and any validation logs.  

## Example Test Case  

- **Description**: Single transaction with simple mapping.  
- **Input**: `example_simple.json`  
- **Expected Output**: `example_simple.csv`  
- **Notes**: No violations expected.  

## Edge Case Test  

- **Description**: Transaction with multiple splits and refund classification.  
- **Input**: `example_edge.json`  
- **Expected Output**: `example_edge.csv`  
- **Notes**: Splits should inherit parent transaction type and classification. 
