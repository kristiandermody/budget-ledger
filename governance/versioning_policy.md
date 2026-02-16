# Budget & Ledger — Governance & Change Policy

## Purpose

This document defines how changes are introduced into the Budget & Ledger system.

System meaning, structure, and operational behavior are defined in:

- `/docs/architecture/`
- `/docs/operating/`
- `/releases/`

This document governs **how the system evolves**, not what the system is.

---

# 1. Versioning Model

The project follows:

MAJOR.MINOR.PATCH

Example:
13.1.0

Version numbers communicate structural and architectural intent.

---

## 1.1 Major Version

Increment the MAJOR version when:

- Core architectural meaning changes
- Allocation model semantics change
- Ledger model semantics change
- Budget capacity philosophy changes
- Structural relationships between system components change

A major version reflects architectural evolution.

Major versions may require documentation updates and release notes describing conceptual shifts.

---

## 1.2 Minor Version

Increment the MINOR version when:

- Structural workbook elements are added
- Non-breaking system capabilities expand
- Validation rules expand
- Tooling behavior expands without architectural change
- Documentation clarifies behavior without changing meaning

Minor versions expand capability while preserving system philosophy.

---

## 1.3 Patch Version

Increment the PATCH version when:

- Incorrect behavior is corrected
- Non-structural defects are resolved
- Documentation errors are fixed

Patch versions must not alter architectural meaning.

---

# 2. Commit Classification Standard

All commits must begin with one of the following prefixes:

Refactor:
Feature:
Fix:
Docs:
Governance:
Release:

These prefixes apply to commit messages, branch naming, and pull request titles.

---

## Refactor
Structural or organizational changes without altering system behavior.

## Feature
New capability or structural expansion.

## Fix
Correction of unintended behavior.

## Docs
Documentation-only changes.

## Governance
Policy or workflow changes.

## Release
Used only when tagging official system releases.

---

# 3. Branch Lifecycle

All non-trivial changes must occur on a branch.

## 3.1 Short-Lived Branches

Used for:
- Refactors
- Minor fixes
- Documentation changes

Lifecycle:
1. Create branch
2. Implement change
3. Open Pull Request
4. Merge into `main`
5. Delete branch (remote and local)

---

## 3.2 Long-Running Feature Branches

Used for:
- Major version development (e.g., `feature/v14`)
- Multi-phase structural evolution

The branch remains active until the feature is fully stable and merged into `main`.

---

# 4. Main Branch Policy

The `main` branch represents:

Stable, authoritative system state.

Anything merged into `main` is considered production-ready and architecturally intentional.

Direct commits to `main` are discouraged except for trivial changes.

---

# 5. Release Discipline

Each official release must:

- Include updated release notes
- Reflect correct version increment
- Align with architecture documentation
- Preserve history integrity

Release tags must match version numbers exactly.

---

# 6. Tool Version Coupling

Tooling must not be permanently bound to a single system version via folder naming.

Version-specific behavior should be configuration-driven rather than directory-driven.

This protects future major version transitions.

---

# Philosophy

This repository is a structured financial operating system.

Governance exists to:

- Prevent architectural drift
- Protect structural clarity
- Maintain disciplined evolution
- Support long-term scalability
