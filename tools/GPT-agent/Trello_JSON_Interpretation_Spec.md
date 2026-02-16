# V13 Trello JSON Interpretation Specification

Version: 13.0\
Status: Locked\
Scope: Trello → Ledger Conversion Agent

------------------------------------------------------------------------

## 1. Purpose

This document defines how raw Trello JSON exports must be interpreted by
the V13 conversion agent.

It establishes:

-   Which JSON fields are used
-   How card titles are parsed
-   How dates are extracted
-   How amounts are extracted
-   How descriptions are derived
-   How labels are interpreted
-   How Trello URLs are handled

No assumptions outside this document are permitted.

------------------------------------------------------------------------

## 2. Trello JSON Fields Used

The Agent must use the following fields:

-   Card ID → Transaction ID source
-   Card Name → Title parsing (dates, description, amount)
-   Card Description → Notes context (but not split parsing)
-   Labels → Structural / Parent / Child detection
-   Card URL → Ledger Notes field

No other Trello JSON fields may affect ledger logic.

------------------------------------------------------------------------

## 3. Card Title Parsing Rules

Each card title is a direct copy of the bank transaction line.

The title will always contain:

-   One or two dates
-   A description
-   An amount

------------------------------------------------------------------------

### 3.1 Date Rules

If one date exists: → It is the Posted Date.

If two dates exist: → First date = Posted Date\
→ Second date = Authorized Date

Dates must be normalized to:

YYYY-MM-DD format.

The Agent must not guess missing dates.

------------------------------------------------------------------------

### 3.2 Amount Rules

-   The amount will always be present in the title.
-   Currency symbols must be removed.
-   Output must be numeric only.
-   Deposits must be positive.
-   Expenses must be negative.
-   Commas must be removed.

The Agent must not infer sign --- it must respect source formatting
logic.

------------------------------------------------------------------------

### 3.3 Description Rules

Description is:

-   All remaining title text after removing:
    -   Dates
    -   Amount

Description must preserve original wording. No normalization beyond
whitespace trimming.

------------------------------------------------------------------------

## 4. Card Description Field

The Trello card description may contain:

-   Split notes
-   Transaction context
-   Personal notes

The Agent must:

-   Preserve description content as-is.
-   Not attempt to parse split logic from description.
-   Not alter formatting.

------------------------------------------------------------------------

## 5. Label Interpretation Order

After removing administrative labels, labels must be evaluated in this
order:

1.  Structural labels
2.  Parent category
3.  Child category

Detection must be case-insensitive. Canonical casing must match taxonomy
output.

------------------------------------------------------------------------

## 6. Trello URL Handling

The Card URL must be placed in:

Ledger column → Notes

Rules:

-   No prefix text.
-   No label.
-   URL only.
-   Must always be present.

------------------------------------------------------------------------

## 7. Prohibited Behavior

The Agent must NEVER:

-   Guess missing amounts
-   Guess missing dates
-   Guess missing parent or child
-   Parse split logic from free-text description
-   Modify title semantics beyond defined rules

------------------------------------------------------------------------

## 8. Determinism Requirement

Given identical JSON input and identical schema configuration:

The Agent must produce identical output.

No probabilistic interpretation is allowed.

------------------------------------------------------------------------

## 9. Version Control

This interpretation spec applies to:

Budget & Ledger System --- V13

Changes require:

-   Version increment
-   Updated document
-   Validation of conversion logic

------------------------------------------------------------------------

End of Document
