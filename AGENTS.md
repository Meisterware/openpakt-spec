# OpenPAKT Agent Guidelines

## Project Overview

OpenPAKT (Open Protocol for Agent Knowledge Trust) is an open specification for representing:

- AI agent security findings
- security testing scenarios
- CI validation results

The goal of OpenPAKT is to provide a **portable, interoperable format** that security tools, CI systems, and agent scanners can use to exchange security results.

This repository contains the **specification only**, not product implementations.

---

## Specification Scope

OpenPAKT v0.1 intentionally keeps the specification extremely small.

The core areas of the specification are:

- report schema
- finding taxonomy
- severity model
- scenario format
- CI policy semantics
- example report
- example scenario

Changes should remain aligned with these areas unless a new milestone explicitly expands scope.

Changes should remain aligned with the active milestone (e.g. v0.1 Core Specification).

Agents should prioritise implementing or clarifying the issues assigned to the active milestone.

---

## Scope Guardrails

This repository is **specification-first**.

Agents must NOT introduce:

- application code
- web services
- APIs
- SDKs
- servers
- databases
- UI components
- infrastructure tooling
- package managers
- dependency frameworks

Do not scaffold new software projects inside this repository.

The OpenPAKT repository defines **standards**, not implementations.

---

## Allowed Contributions

Valid contributions include:

- improving specification clarity
- refining schema definitions
- updating taxonomy definitions
- clarifying severity semantics
- improving CI validation semantics
- adding minimal examples
- improving documentation structure
- correcting terminology or formatting

Example files may be added to demonstrate specification usage.

Examples should remain **minimal and implementation-agnostic**.

Examples must not introduce language-specific code or runtime dependencies.

---

## Disallowed Drift

Agents must avoid:

- expanding the specification beyond current milestones
- introducing speculative features
- adding large frameworks or runtime environments
- converting the repository into a software project
- generating unrelated code or tooling

The specification must remain **implementation-agnostic**.

---

## Architecture Principles

When proposing changes:

Prefer:

- minimal schema design
- simple structures
- explicit semantics
- deterministic CI behaviour

Avoid:

- unnecessary abstraction
- tool-specific behaviour
- vendor-specific assumptions

OpenPAKT should remain usable by **any language, platform, or security tool**.

---

## File Structure

Specification documents live under:

```text
spec/
```

Formatting and terminology conventions are defined in `spec/STYLE.md`

Examples live under:

```text
examples/
```

Top-level documents may include:

- README.md
- CONTRIBUTING.md
- GOVERNANCE.md
- ROADMAP.md

Governance files should only be modified when changes are explicitly requested by a GitHub issue or milestone update.

Agents should prefer **editing existing files** instead of creating new files unless required by an issue or specification change.

---

## Change Discipline

Pull requests should:

- remain small and focused
- reference the relevant GitHub issue
- avoid introducing changes not described by an issue or milestone
- maintain terminology consistency
- avoid breaking existing specification examples

Pull requests must use the repository PR template.

Agents creating pull requests should:

- populate the Summary section
- select the correct Type of change
- select the correct Specification classification
- link the Related issue
- complete the What changed section
- describe the expected Impact

Only tick checkboxes that apply.
Do not leave placeholder text in the PR body.

Pull requests that do not follow this structure may be rejected during review.

Agents should create changes in a dedicated branch rather than committing directly to `main`.

When applicable, pull requests should include the GitHub issue number at the start of the PR title.

Preferred branch naming patterns:

- `issue/<number>-<short-slug>`
- `spec/<short-slug>`
- `docs/<short-slug>`
- `chore/<short-slug>`
- `fix/<short-slug>`

Use the most specific branch type when possible.

Examples:

```text
issue/1-report-schema
issue/4-scenario-format
spec/severity-model
docs/spec-governance
chore/repository-cleanup
fix/schema-validation-error
```

Branch names should be lowercase, use kebab-case and follow the repository branch naming rules.

Agents should review changes for:

- scope drift
- terminology consistency
- specification clarity
- unnecessary complexity

Agents must not rename existing taxonomy identifiers or schema fields unless explicitly required by a specification update.

---

## Relationship to Detektor

OpenPAKT is designed to support **AI agent security scanners** such as the Detektor CLI reference implementation.

However, Detektor is developed **in a separate repository**.

Implementation work should not be added here.

---

## Summary

OpenPAKT defines a **minimal, implementation-agnostic security specification** for AI agent security scanning.

Agents should prioritise:

- clarity
- minimalism
- interoperability
- stability
