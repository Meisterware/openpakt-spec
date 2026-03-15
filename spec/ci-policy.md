Specification: OpenPAKT
Document: CI Policy Evaluation Semantics
Version: v0.1
Status: Draft

# OpenPAKT — CI Policy Evaluation Semantics

## Purpose

This document defines a minimal, deterministic model for evaluating OpenPAKT findings in CI.

The v0.1 model provides a tool-independent way to determine pass/fail outcomes from normalized findings.

CI policy evaluation operates on findings that conform to the OpenPAKT report schema.

## Scope

This document defines:

- a minimal CI policy input shape
- deterministic pass/fail evaluation rules
- deterministic handling for ignored severities and ignored finding types
- severity threshold behavior aligned to the OpenPAKT severity model
- compatibility guidance for CI systems and external reporting formats

This document does **not** define:

- a policy DSL or query language
- scanner normalization logic
- taxonomy or severity definitions (see dedicated specification documents)
- SARIF mapping
- provenance or registry semantics
- implementation-specific workflow logic

## Design goals

The v0.1 CI policy evaluation semantics are designed to be:

- minimal
- deterministic
- implementation-agnostic
- CI-friendly
- compatible with simple pipeline gate behavior

## Normative guidance

- CI policy evaluation **MUST** operate on normalized OpenPAKT findings.
- Evaluators **MUST** apply the severity ordering defined in the OpenPAKT severity model and referenced in this document.
- Policies **MUST** define `fail_on`, and the value **MUST** be one of the severity levels defined in the OpenPAKT severity model.
- Policies **MAY** define `ignore_severities`.
- Policies **MAY** define `ignore_types`.
- If present, `ignore_severities` values **MUST** be severity levels defined in the OpenPAKT severity model.
- If present, `ignore_types` values **MUST** be canonical taxonomy identifiers defined in the OpenPAKT taxonomy specification.
- Evaluators **MUST** treat policies containing unsupported `ignore_severities` or `ignore_types` values as invalid input and **MUST NOT** continue evaluation with those values.
- Evaluators **MUST** exclude ignored findings from fail/pass evaluation.
- A build **MUST** fail if at least one non-ignored finding has severity at or above `fail_on`.
- A build **MUST** pass if no non-ignored finding has severity at or above `fail_on`.
- Evaluators **MUST NOT** use tool-specific extensions to alter the normative pass/fail outcome.
- Evaluators **SHOULD** return a machine-readable evaluation result that includes at least: decision (`pass`/`fail`), `fail_on`, and matched finding identifiers.

## Policy input model (v0.1)

A v0.1 policy input uses three concepts:

- `fail_on` (required): severity threshold for failing the build
- `ignore_severities` (optional): list of severities to exclude
- `ignore_types` (optional): list of finding `type` values to exclude

Policy keys are case-sensitive and **MUST** appear exactly as defined.

If present, `ignore_severities` and `ignore_types` values **MUST** use canonical identifiers defined by the severity and taxonomy specifications.

### Example policy input (YAML)

```yaml
fail_on: high
ignore_severities:
  - informational
ignore_types:
  - prompt_injection
```

## Evaluation model

Given:

- a policy `P`
- a normalized findings list `F`

evaluation proceeds as follows:

1. Start with all findings in `F`.
2. Remove findings where `severity` is listed in `P.ignore_severities`.
3. Remove findings where `type` is listed in `P.ignore_types`.
4. From the remaining findings, select findings with `severity >= P.fail_on` according to the severity ordering defined in this document.
5. If one or more findings match step 4, decision is `fail`; otherwise decision is `pass`.

If `ignore_severities` or `ignore_types` are omitted, evaluators **MUST** treat them as empty sets.

## Deterministic severity threshold behavior

Severity comparison **MUST** use this strict ranking:

1. `critical`
2. `high`
3. `medium`
4. `low`
5. `informational`

For threshold checks, a finding meets `fail_on` when its severity is the same as the threshold or appears to the left of the threshold in the ordered list above.

Examples:

- with `fail_on: medium`, severities `medium`, `high`, and `critical` meet the threshold
- with `fail_on: high`, only `high` and `critical` meet the threshold

## Deterministic ignore handling

Ignore logic applies before threshold comparison.

A finding is ignored when at least one of the following is true:

- its `severity` is in `ignore_severities`
- its `type` is in `ignore_types`

If both ignore lists are present, evaluators **MUST** treat ignore matching as logical OR.

Ignored findings:

- **MUST NOT** contribute to threshold matching
- **MAY** be reported as excluded in implementation-specific output
- **MUST NOT** change the normative pass/fail rule

## Compatibility guidance

### CI system compatibility

Implementations in CI systems (for example GitHub Actions, GitLab CI, and Azure Pipelines) **SHOULD** preserve the normative evaluation order and pass/fail rules in this document.

The CI platform exit status **SHOULD** be derived directly from the policy decision:

- `pass` -> successful job/stage
- `fail` -> failed job/stage

### External reporting compatibility

When exporting results to external reporting formats, producers **SHOULD** preserve:

- the original policy inputs used for evaluation
- the final decision (`pass`/`fail`)
- the set of matching non-ignored finding identifiers

Export behavior **MUST NOT** redefine OpenPAKT evaluation semantics.

## Deterministic examples

### Example findings (normalized)

```yaml
findings:
  - id: f-001
    type: tool_abuse_privilege_escalation
    severity: high
  - id: f-002
    type: prompt_injection
    severity: medium
  - id: f-003
    type: sensitive_data_exposure
    severity: informational
```

### Evaluation examples

| Policy input | Non-ignored findings | Threshold matches | Decision |
|---|---|---|---|
| `fail_on: high` | `f-001`, `f-002`, `f-003` | `f-001` | `fail` |
| `fail_on: high`, `ignore_types: [prompt_injection]` | `f-001`, `f-003` | `f-001` | `fail` |
| `fail_on: critical`, `ignore_severities: [informational]` | `f-001`, `f-002` | none | `pass` |
| `fail_on: medium`, `ignore_severities: [high, medium]` | `f-003` | none | `pass` |

## Versioning and compatibility notes

This document defines the minimal CI policy evaluation semantics for OpenPAKT v0.1.

Future versions may extend policy expressiveness, but v0.1 implementations should treat this evaluation model as the normative baseline for deterministic pass/fail behavior.
