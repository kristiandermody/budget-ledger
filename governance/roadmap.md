# Budget & Ledger Project Roadmap

This document defines implementation phases for the project.

IMPORTANT:
Roadmap phases are NOT version numbers.
Version numbers follow semantic versioning rules defined in `versioning_policy.md`.

Phases describe development sequencing.
Versions describe meaning stability.

---

# Phase 1 — Schema Stabilization

Objective:
Finalize structural integrity of the workbook before activating logic.

Scope includes:

- All worksheets created
- All required columns defined
- Column order finalized
- Field meanings documented
- Structural relationships defined
- Split transaction rules defined
- Budget Month architecture finalized
- Source-of-truth rules defined
- Required vs optional fields defined
- Allowed values defined (Transaction Type, Classification, etc.)
- Data validation rules implemented
- No cross-sheet calculation logic required yet

Exit Criteria:
The workbook structure can be frozen without ambiguity.
No semantic interpretation of data is unclear.

---

# Phase 2 — Logic Activation

Objective:
Wire structural components together with formulas and behavioral logic.

Scope may include:

- Month Summary formulas
- Budget rollups
- Allocation connections
- Transfer integration
- Reconciliation logic
- Pending transaction handling (if introduced)
- Signed Amount derivation enforcement
- Cross-sheet integrity checks

Phase 2 must NOT alter structural meaning defined in Phase 1.
If structural meaning changes, a MAJOR version is required.

Exit Criteria:
All sheets operate cohesively.
Reporting reflects ledger data accurately.

---

# Phase 3 — UX & Presentation

Objective:
Improve usability and visual clarity without altering structure or logic.

Scope may include:

- Conditional formatting
- Sheet styling
- Layout improvements
- Dashboard refinements
- Freeze panes and grouping
- Visual error indicators

No structural or behavioral meaning changes permitted.

---

# Phase 4 — Tooling & Automation

Objective:
Develop and integrate external tools that interface with the workbook.

Scope may include:

- Trello JSON → CSV converter
- Data import automation
- Validation scripts
- Snapshot tooling
- External analysis integration

Tools must conform to stabilized schema.
Tools must not redefine workbook meaning.

---

# Phase Governance

- Roadmap phases guide development order.
- Version numbers follow semantic impact.
- Phases and versions are intentionally decoupled.
