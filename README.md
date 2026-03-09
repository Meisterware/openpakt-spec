# OpenPAKT

## Open Protocol for Agent Knowledge Trust

![Specification](https://img.shields.io/badge/spec-v0.1-blue)
![Status](https://img.shields.io/badge/status-draft-orange)
![License](https://img.shields.io/badge/license-Apache%202.0-green)
![Roadmap](https://img.shields.io/badge/roadmap-public-blue)

OpenPAKT is an open specification for representing **AI agent security findings, security testing scenarios, and CI validation results** in a portable format.

The goal is to provide a **common language for AI agent security testing across tools, programming languages, and CI systems.**

> ⚠️ **Status:** OpenPAKT is currently under active development and evolving toward the **v0.1 Core Specification milestone**.  
> Feedback and contributions are welcome.

---

## Specification Status

OpenPAKT is currently in **Draft status** and evolving toward the **v0.1 Core Specification milestone**.

The v0.1 release will define the minimal interoperable structure for representing AI agent security findings, attack scenarios, and CI policy evaluation results.

Until v1.0, the specification may evolve as the ecosystem matures.

---

## Why OpenPAKT

As AI agents increasingly interact with tools, APIs, and external systems, **security testing has become a critical requirement**. However, current approaches to agent security scanning are fragmented across different frameworks, evaluation methods, and proprietary formats.

This fragmentation makes it difficult to:

- compare results across tools
- enforce security policies in CI pipelines
- share reproducible security scenarios
- integrate agent security testing into standard DevSecOps workflows

OpenPAKT addresses this challenge by defining a **portable, interoperable specification** for representing agent security findings, scenarios, and CI validation rules.

---

## Architecture Overview

OpenPAKT defines the **portable artifacts produced by agent security scanners** and consumed by CI pipelines.

```text
OpenPAKT Scenario
        │
        ▼
AI Agent / Agent System
        │
        ▼
Security Scanner
(Detektor or other tools)
        │
        ├── produces OpenPAKT Report
        │       (findings, taxonomy, severity, evidence)
        │
        ▼
CI Policy Evaluation
(GitHub Actions / GitLab / Azure DevOps)
        │
        ├── pass
        └── fail
```

In this architecture:

- **Security scanners** generate OpenPAKT-compliant reports
- **CI pipelines** evaluate those findings using policy rules
- **Scenarios** enable reproducible security testing of agent behaviour

OpenPAKT acts as the **interoperability layer between scanners and CI systems.**

---

## Scope

OpenPAKT **v0.1** focuses on defining a minimal interoperable structure for:

- security finding reports
- finding taxonomy
- severity model
- attack scenario definitions
- CI policy evaluation semantics

---

## Design Principles

OpenPAKT is designed with the following principles:

- **Language-agnostic** – usable across different programming languages and frameworks
- **CI-first** – optimized for automated security validation in CI pipelines
- **Portable** – findings and scenarios can be shared across tools
- **Deterministic** – results should be reproducible across implementations
- **Minimal v0.1** – start small and evolve through community adoption

---

## Specification

The OpenPAKT specification is defined in the `spec/` directory.

```text
spec/
  report-schema.md
  taxonomy.md
  severity.md
  scenario-format.md
  ci-policy.md
```

Each component defines a part of the OpenPAKT security testing model.

---

## Roadmap

OpenPAKT evolves through milestone-based specification releases.

### v0.1 – Core Specification

Defines the minimal interoperable structure for agent security testing.

Includes:

- report schema
- finding taxonomy
- severity model
- scenario format
- CI policy semantics
- example reports and scenarios

### v0.2 – Ecosystem Integration

Extends OpenPAKT to integrate with existing DevSecOps tooling.

Planned features:

- SARIF mapping for CI security dashboards
- cross-surface finding correlation model
- provenance metadata fields
- tool interoperability guidelines
- implementation guide for tool developers
- reference implementation alignment (Detektor CLI)

### v1.0 – Stable Standard

Finalizes OpenPAKT as a stable open standard.

Planned components:

- governance model
- backwards compatibility rules
- version negotiation semantics
- conformance tests
- registry compatibility

---

## Versioning

OpenPAKT follows **semantic versioning** for the specification.

Current version:

**v0.1 – Initial Draft**

---

## Examples

Example OpenPAKT reports and scenarios are available in the `examples/` directory.

These examples demonstrate how security findings and attack scenarios can be represented using the specification.

---

## Governance

OpenPAKT is an open specification developed under the **Meisterware** organisation.

The specification evolves through:

- public GitHub issues
- community contributions
- milestone-based specification releases

---

## Vision

To become the **common interoperability layer for AI agent security testing.**

---

## Reference Implementation

**Detektor** is the reference CLI implementation of the OpenPAKT specification.

Detektor demonstrates how OpenPAKT findings, scenarios, and CI policy validation can be implemented in practice.

---

## Project Documents

- [Specification](spec/index.md)
- [Contributing Guide](CONTRIBUTING.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
