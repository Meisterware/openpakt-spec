Specification: OpenPAKT
Document: Severity Model
Version: v0.1
Status: Draft

# OpenPAKT — Severity Model

## Purpose

This document defines the canonical severity model for OpenPAKT findings.

The severity model provides a stable, implementation-agnostic way to represent the impact and urgency of a finding across scanners, CI systems, and downstream consumers.

## Scope

This document defines:

- canonical OpenPAKT v0.1 severity levels
- required representation of severity values in findings
- minimal guidance for vendor severity mapping
- stability expectations for cross-version CI usage

This document does **not** define taxonomy categories, report object structure, CI policy semantics, or vendor scoring formulas.

## Design goals

The v0.1 severity model is designed to be:

- minimal for MVP adoption
- deterministic for CI policy evaluation
- stable across specification versions
- implementation-agnostic
- compatible with common external severity systems

## Normative guidance

- A finding `severity` value in interoperable OpenPAKT output **MUST** be one of the canonical severity levels defined in this document.
- Producers **MUST** emit severity values as lowercase strings.
- Producers **MUST NOT** emit numeric-only severity values in place of canonical OpenPAKT severity strings.
- Producers **MAY** retain vendor-native severity values in supplementary metadata, provided the canonical OpenPAKT `severity` remains present and authoritative.
- Consumers and CI evaluators **MUST** interpret canonical severity levels deterministically for policy evaluation.
- Severity values **MUST** represent impact and urgency of the finding, independent of scanner-specific naming conventions.

## Canonical severity levels

OpenPAKT v0.1 defines the following canonical severity levels for finding `severity`:

- `critical`
- `high`
- `medium`
- `low`
- `informational`

These levels are ordered from highest to lowest severity:

`critical` > `high` > `medium` > `low` > `informational`

The canonical level names are stable identifiers for OpenPAKT and are intended to remain consistent across specification versions so CI thresholds remain valid over time.

## Vendor mapping guidance

Security scanners often use vendor-specific labels, numeric scales, or mixed models.

To preserve interoperability:

- Producers **SHOULD** map vendor-native severity models to the canonical OpenPAKT severity levels when generating OpenPAKT findings.
- Producers **MAY** include original vendor severity values in metadata for traceability.
- Consumers **SHOULD** evaluate OpenPAKT findings using the canonical severity only.

OpenPAKT v0.1 intentionally does not define mandatory per-vendor mapping tables.

This model is designed to remain compatible with SARIF and similar ecosystems by using a small, stable normalized severity set without prescribing tool-specific conversion logic.

## Examples

### YAML finding example

```yaml
id: finding-001
type: prompt_injection
severity: high
component: agent.prompt
description: Agent followed malicious instructions embedded in retrieved content.
evidence:
  summary: Tool call was triggered by attacker-controlled context.
```

### CI threshold style example

```txt
fail-on: high
```

Expected deterministic behaviour for `fail-on: high`:

- `critical` -> fail build
- `high` -> fail build
- `medium` -> report without failing build
- `low` -> report without failing build
- `informational` -> report without failing build

## Out of scope

The following are out of scope for this document:

- finding taxonomy definitions
- report schema field definitions
- CI policy language and pass/fail semantics
- numeric scoring models (for example CVSS-like formulas)
- vendor-specific risk formulas or weighting logic
