# CLI Tool Configuration

This directory contains static configuration files required by the Trello JSON → Ledger CSV CLI converter.

These files provide mapping and reference data used during conversion.

They are not governance documents.

---

## Purpose

The configuration files in this directory:

- Support deterministic conversion
- Provide label-to-category mapping
- Define known category structures for the CLI tool
- Assist with validation alignment

They must remain consistent with active governance documentation.

---

## Files

### category_master.csv

Defines the valid parent and child category relationships recognized by the CLI tool.

This file must align with:

- Parent_Category_Registry.md
- Parent_Child_Taxonomy.md

The CLI tool does not auto-create new categories.

---

### label_mapping.csv

Maps Trello labels to ledger categories and structural classifications.

This file defines how Trello metadata is interpreted during conversion.

Label mappings must be consistent with:

- Structural_Label_Registry.md
- Trello_JSON_Interpretation_Spec.md

---

## Governance Alignment

Governance documents define structural rules.

Configuration files implement static mappings that must conform to those rules.

If governance changes:

1. Update governance documentation.
2. Update configuration files in this directory.
3. Re-run conversion and validation.
4. Commit changes together.

Do not update configuration files independently of governance changes.

---

## Version Awareness

Configuration files must match the active ledger schema and governance snapshot.

Do not mix configuration files from different branches or versions.

---

## Prohibited Actions

- Do not auto-create categories.
- Do not add structural labels not defined in governance.
- Do not modify schema columns.
- Do not bypass validation errors via configuration.

All structural behavior is defined in governance documentation.
