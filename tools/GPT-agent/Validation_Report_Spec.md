# V13 Validation & Labor Report Specification

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines the required structure and contents of the
post-conversion Validation & Labor Report for Budget & Ledger System ---
V13.

The report exists to:

-   Detect schema drift
-   Detect structural violations
-   Surface unknown labels
-   Prevent silent corruption
-   Provide a pre-import review checklist

If the report is empty of issues, the Ledger CSV is considered safe to
import.

------------------------------------------------------------------------

## 2. Report Structure (Required Sections)

The report must contain the following sections in this exact order:

1.  Summary
2.  Structural Violations
3.  Unknown Parents
4.  Unknown Children
5.  Invalid Parent--Child Combinations
6.  Auto-Added REVIEW Flags

If a section contains no entries, it must explicitly state:

"None detected."

------------------------------------------------------------------------

## 3. Section Definitions

### 3.1 Summary

Must include:

-   Total Trello cards processed
-   Total ledger rows produced
-   Total split transactions detected
-   Total validation issues found

------------------------------------------------------------------------

### 3.2 Structural Violations

Include transactions where:

-   Multiple economic structural labels detected
-   Missing required economic label on deposit
-   Invalid structural combinations

Each entry must include:

-   Transaction ID
-   Description
-   Violation type

------------------------------------------------------------------------

### 3.3 Unknown Parents

Include transactions where:

-   Parent label does not match Parent Registry

Each entry must include:

-   Transaction ID
-   Detected Parent value
-   Description

------------------------------------------------------------------------

### 3.4 Unknown Children

Include transactions where:

-   Child label does not exist in Parent → Child taxonomy

Each entry must include:

-   Transaction ID
-   Parent
-   Detected Child value
-   Description

------------------------------------------------------------------------

### 3.5 Invalid Parent--Child Combinations

Include transactions where:

-   Child exists in taxonomy but not under detected Parent

Each entry must include:

-   Transaction ID
-   Parent
-   Child
-   Description

------------------------------------------------------------------------

### 3.6 Auto-Added REVIEW Flags

Include transactions where:

-   REVIEW label was automatically added by converter

Each entry must include:

-   Transaction ID
-   Reason for REVIEW

------------------------------------------------------------------------

## 4. Validation Logic Policy

The Agent must:

-   Never suppress validation errors
-   Never silently correct schema mismatches
-   Always report unknown labels
-   Always report structural violations

Graceful degradation rules apply:

-   Valid Parent + Unknown Child → Process Parent, flag Child
-   Valid Child + Unknown Parent → Blank Parent, flag Parent
-   Both Unknown → Flag both

All such cases must appear in this report.

------------------------------------------------------------------------

## 5. Output Format

The report may be:

-   Plain text (.txt)
-   Markdown (.md)

Formatting must be clean and human-readable.

------------------------------------------------------------------------

## 6. Version Control

This validation spec applies to:

Budget & Ledger System --- V13

Changes require:

-   Version increment
-   Update to this document
-   Agent update

------------------------------------------------------------------------

End of Document
