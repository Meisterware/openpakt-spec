# OpenPAKT

## Open Protocol for Agent Knowledge Trust

![Specification](https://img.shields.io/badge/spec-v0.1.0-blue)
![Spec Version](https://img.shields.io/badge/version-v0.1.0-blue)
![Status](https://img.shields.io/badge/status-draft-orange)
![License](https://img.shields.io/badge/license-Apache%202.0-green)
![Roadmap](https://img.shields.io/badge/roadmap-public-blue)

OpenPAKT is an open specification for representing **AI agent security findings, security testing scenarios, and CI validation results** in a portable format.

The goal is to provide a **common language for AI agent security testing across tools, programming languages, and CI systems.**

---

## OpenPAKT v0.1.0 — Core Specification

The **v0.1.0 Core Specification** defines the minimal interoperable structure for representing AI agent security testing artifacts.

This version establishes the foundational components required for scanners and CI systems to exchange and evaluate agent security findings in a consistent way.

⚠️ **Status:** The specification is currently in **Draft status** while the ecosystem and reference implementations mature.

Until **v1.0**, the specification may evolve as adoption and implementation experience grows.

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

OpenPAKT **v0.1.0** defines a minimal interoperable structure for:

- security finding reports
- finding taxonomy
- severity model
- attack scenario definitions
- CI policy evaluation semantics

This version focuses on establishing a **stable core model** for representing AI agent security testing results.

---

## Design Principles

OpenPAKT is designed with the following principles:

- **Language-agnostic** – usable across different programming languages and frameworks
- **CI-first** – optimized for automated security validation in CI pipelines
- **Portable** – findings and scenarios can be shared across tools
- **Deterministic CI evaluation** – CI systems evaluate normalized findings consistently
- **Minimal v0.1** – start small and evolve through ecosystem adoption

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

Each document defines a component of the OpenPAKT security testing model.

---

## Roadmap

OpenPAKT evolves through milestone-based specification releases.

### v0.1 – Core Specification (Current)

Defines the minimal interoperable structure for agent security testing.

Includes:

- report schema
- finding taxonomy
- severity model
- scenario format
- CI policy semantics
- example reports and scenarios

---

### v0.2 – Ecosystem Integration

Extend the OpenPAKT specification to support interoperability with existing DevSecOps tooling, CI pipelines, and agent security scanners.

This milestone introduces mappings to widely used security reporting formats, defines metadata required for cross-surface correlation, and establishes guidance for tool compatibility and implementation.

Planned features:

- SARIF mapping for CI security dashboards
- cross-surface finding correlation model
- provenance metadata fields
- implementation guidance for tool developers
- reference implementation alignment (Detektor CLI)

The goal of this milestone is to make OpenPAKT practical for real-world integrations while maintaining the minimal core defined in v0.1.

---

### v0.3 – Multi-Agent Security

Expands OpenPAKT to support security testing and validation of multi-agent systems and agent ecosystems.

As AI systems increasingly involve multiple cooperating agents and tool integrations, security testing must account for interactions across agent boundaries.

Planned areas of exploration include:

- multi-agent interaction testing scenarios
- agent-to-agent security boundaries
- tool invocation trust validation
- cross-agent data flow analysis
- distributed agent security findings

The goal of this milestone is to enable OpenPAKT to represent security findings that emerge from complex agent workflows rather than single agent prompts.

---

### v1.0 – Stable Standard

Finalize the OpenPAKT specification as a stable, production-ready standard for representing AI agent security findings, scenarios, and CI validation results.

This milestone formalizes governance rules, versioning semantics, compatibility guarantees, and conformance requirements needed for long-term ecosystem adoption.

Planned components:

- governance model
- backwards compatibility rules
- version negotiation semantics
- conformance tests
- registry compatibility

The objective of v1.0 is to provide a reliable and stable contract that tool vendors, platforms, and CI systems can implement with confidence.

---

## Versioning

OpenPAKT follows **Semantic Versioning** for specification releases.

Current version:

```text
v0.1.0 — Core Specification
```

Until **v1.0**, the specification may evolve as the ecosystem matures.

---

## Examples

Example OpenPAKT reports and scenarios are available in the `examples/` directory.

These demonstrate how security findings and attack scenarios can be represented using the specification.

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

## Specification vs Implementations

OpenPAKT defines an **open specification**, not a single security scanner.

The specification defines the **interoperable format for scenarios, findings, and CI evaluation**, while different tools may implement scanners that produce OpenPAKT-compliant reports.

This separation allows multiple tools and vendors to adopt the specification.

OpenPAKT-compatible scanners may include:

- Detektor (reference CLI implementation)
- future ecosystem tools
- CI security scanners
- agent security testing frameworks

---

## Reference Implementation

**[Detektor](https://github.com/Meisterware/detektor)** is the reference CLI implementation of the OpenPAKT specification.

Detektor demonstrates how OpenPAKT findings, scenarios, and CI policy validation can be implemented in practice.

The reference implementation helps validate the specification and provides a starting point for building compatible scanners.

---

## Project Documents

- [Specification](spec/index.md)
- [Contributing Guide](CONTRIBUTING.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
