Specification: OpenPAKT
Document: Finding Taxonomy
Version: v0.1
Status: Draft

# OpenPAKT — Finding Taxonomy

## Purpose

This document defines the canonical classification model for OpenPAKT findings.

The taxonomy provides stable top-level finding types so scanners, CI systems, and downstream consumers can exchange results consistently.

## Scope

This document defines:

- the canonical top-level finding taxonomy for OpenPAKT v0.1
- required usage of taxonomy identifiers in finding `type` fields
- minimal extensibility guidance for implementation-specific mappings

This document does **not** define severity scoring semantics, scenario structure, or CI policy pass/fail behaviour.

## Design goals

The v0.1 taxonomy is designed to be:

- OWASP-aligned
- stable for interoperable report exchange
- implementation-agnostic
- language-agnostic
- CI-friendly

## Normative guidance

- An OpenPAKT finding `type` **MUST** be one of the canonical taxonomy identifiers defined in this document.
- Implementations **MAY** maintain internal rule IDs, aliases, or subcategories.
- Implementations **MUST NOT** replace the canonical top-level `type` with a vendor-specific identifier in interoperable OpenPAKT output.
- Implementations **MAY** enrich findings with additional metadata, provided canonical taxonomy compatibility is preserved.
- OpenPAKT v0.1 defines only top-level categories; future versions **MAY** expand taxonomy guidance.

For finding object structure, see the OpenPAKT report schema specification.

## Canonical taxonomy

OpenPAKT v0.1 defines the following canonical top-level finding identifiers:

- `prompt_injection`
- `tool_abuse_privilege_escalation`
- `data_exfiltration`
- `sensitive_data_exposure`
- `memory_poisoning`
- `goal_hijacking`
- `excessive_autonomy`
- `cascading_failures`
- `denial_of_wallet`

## Type definitions

### `prompt_injection`

Malicious instructions influence agent behaviour through prompt or context manipulation.

### `tool_abuse_privilege_escalation`

The agent misuses connected tools or exceeds intended permissions and authority boundaries.

### `data_exfiltration`

Sensitive information is extracted or transferred to unauthorized destinations.

### `sensitive_data_exposure`

Sensitive data is exposed to unauthorized users, components, logs, or outputs.

### `memory_poisoning`

Malicious or untrusted content contaminates agent memory and affects future behaviour.

### `goal_hijacking`

The agent is redirected away from intended objectives toward attacker-influenced goals.

### `excessive_autonomy`

The agent takes actions beyond intended autonomy constraints or approval boundaries.

### `cascading_failures`

A weakness propagates across agent/tool/workflow boundaries, causing chained failures.

### `denial_of_wallet`

Resource consumption is intentionally amplified to drive unnecessary operational cost.

## Extensibility guidance

Implementations may define additional internal detail levels (for example, subtype labels or detector rule mappings) under canonical types.

When producing interoperable OpenPAKT output:

- the finding `type` must remain the canonical top-level identifier
- implementation-specific detail should be carried in supplementary fields such as metadata or tool-specific reporting layers

v0.1 does not define a standard sub-taxonomy format.

## Out of scope

The following are out of scope for this document:

- severity level definitions and scoring models
- scenario authoring structure and execution format
- CI policy evaluation semantics
- vendor-specific taxonomy registries

## Examples

### YAML finding example

```yaml
type: prompt_injection
severity: high
component: agent.prompt
description: Agent followed malicious instructions embedded in retrieved content.
```

### CI policy style example

```txt
fail if severity >= high and type == prompt_injection
```

## Versioning and compatibility notes

The canonical identifiers in this document are the stable top-level taxonomy for OpenPAKT v0.1.

Future versions may add guidance or extension mechanisms while preserving interoperability for v0.1 reports that use these canonical types.
