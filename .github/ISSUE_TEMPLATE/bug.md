---
name: Bug Report
about: Report an error, inconsistency, or defect in the OpenPAKT specification, examples, or repository documentation
title: "[Bug] "
labels: bug, spec
---

## Description

Describe the bug clearly and directly.

Examples:

- an example does not validate against the schema
- the specification is internally inconsistent
- a reference file contains an incorrect field name
- documentation contradicts the intended behaviour

---

## Affected Area

Select the affected area if known:

- Report schema
- Finding taxonomy
- Severity model
- Scenario format
- CI policy semantics
- Examples
- Documentation
- Governance / process

---

## Expected Behaviour

Describe what should happen according to the specification or repository content.

---

## Actual Behaviour

Describe what currently happens.

Include validation errors, contradictions, or incorrect examples where relevant.

---

## Steps to Reproduce

Provide the smallest possible reproduction steps.

Example:

1. Open `examples/report-example.json`
2. Validate it against the current schema draft
3. Observe validation failure for an unknown field

---

## Impact

Describe the impact of the issue.

Examples:

- blocks implementation
- creates ambiguity
- breaks validation
- misleads contributors
- causes CI failures

---

## Environment (if relevant)

Include tooling details only if relevant.

Examples:

- validator version
- Detektor CLI version
- OS / shell environment

---

## Additional Context

Add logs, screenshots, links, or related issues if helpful.
