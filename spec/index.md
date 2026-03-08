Specification: OpenPAKT
Document: Specification Index
Version: v0.1
Status: Draft

# OpenPAKT — Specification

This directory contains the **OpenPAKT specification**, which defines a portable standard for reporting and validating AI agent security findings.

OpenPAKT aims to provide a common interoperability layer for AI agent security testing across tools, frameworks, and CI systems.

---

## Specification Structure

The OpenPAKT specification is organized into the following sections:

| Section | Description |
|-------|-------------|
| [Report Schema](report-schema.md) | Defines the structure of OpenPAKT security reports. |
| [Finding Taxonomy](taxonomy.md) | Defines standardised classifications for agent security risks. |
| [Severity Model](severity.md) | Defines severity levels used for security findings. |
| [Scenario Format](scenario-format.md) | Defines reproducible security testing scenarios for AI agents. |
| [CI Policy Semantics](ci-policy.md) | Defines how CI systems evaluate OpenPAKT findings. |

---

## Specification Goals

OpenPAKT is designed to:

- standardise AI agent security findings
- support reproducible security testing
- enable deterministic CI policy enforcement
- allow interoperability between security tools

---

## Versioning

OpenPAKT follows **semantic versioning** for specification releases.

| Version | Status |
|------|------|
| v0.1 | Initial draft |

Historical versions of the specification are stored in the `archive/` directory.

---

## Reference Implementation

The **Detektor CLI** is the reference implementation of the OpenPAKT specification.

Detektor demonstrates how OpenPAKT findings, scenarios, and CI policy validation can be implemented in practice.