# OpenPAKT
### Open Protocol for Agent Knowledge Trust

A language-agnostic specification for AI agent security findings, testing scenarios, and CI policy enforcement.

OpenPAKT defines an open, portable specification for reporting security findings, describing attack scenarios, and validating agent behavior in CI pipelines. The goal is to provide a common language for AI agent security testing across tools, languages, and CI systems.

## Why OpenPAKT
As AI agents increasingly interact with tools, APIs, and external systems, security testing has become a critical requirement. However, current approaches to agent security scanning are fragmented across different frameworks, evaluation methods, and proprietary formats.

This fragmentation makes it difficult to:

- compare results across tools
- enforce security policies in CI pipelines
- share reproducible security scenarios
- integrate agent security testing into standard DevSecOps workflows

OpenPAKT addresses this challenge by defining a portable, interoperable specification for representing agent security findings, scenarios, and CI validation rules.

## Scope
OpenPAKT v0.1 focuses on defining a minimal interoperable structure for:

- security finding reports
- finding taxonomy
- severity model
- attack scenario definitions
- CI policy evaluation semantics

## Design Principles
OpenPAKT is designed with the following principles:

- **Language-agnostic** – usable across different programming languages and frameworks
- **CI-first** – optimized for automated security validation in CI pipelines
- **Portable** – findings and scenarios can be shared across tools
- **Deterministic** – results should be reproducible across implementations
- **Minimal v0.1** – start small and evolve through community adoption

## Specification
The OpenPAKT specification is defined in the `spec/` directory.

```
spec/
  report/
  taxonomy/
  scenarios/
  ci/
```

## Versioning
OpenPAKT follows semantic versioning for the specification.

The current version is **v0.1 (initial draft)**.

## Examples

## Governance

## Vision
To become the common interoperability layer for AI agent security testing.

## Reference Implementation
Detektor is the reference CLI implementation of the OpenPAKT specification.

Detektor demonstrates how OpenPAKT findings, scenarios, and CI policy validation can be implemented in practice.
