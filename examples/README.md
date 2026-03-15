# OpenPAKT Example Artifacts

This directory contains **non-normative example artifacts** demonstrating how OpenPAKT specifications can be implemented in practice.

These examples are provided to help implementers understand how OpenPAKT documents may appear when used by scanners, CI systems, and security tooling.

Examples are intended for **learning and reference purposes only**.

---

## Non-normative note

The example artifacts in this directory are **not part of the normative OpenPAKT specification**.

Implementations should rely on the documents in the `spec/` directory as the authoritative definition of OpenPAKT structure and behaviour.

Examples should not introduce new required fields, semantics, or behaviours that are not defined by the specification.

---

## Example artifacts

### `report-example.json`

Example OpenPAKT report output illustrating how scan results and findings may be represented using the v0.1 report schema.

This example demonstrates:

- report metadata
- scan metadata
- target metadata
- severity summary counts
- findings structure

---

### `scenario-prompt-injection-example.yaml`

Example scenario demonstrating a **prompt injection attempt**.

This scenario illustrates how adversarial user input may attempt to override system instructions or request sensitive information.

---

### `scenario-tool-abuse-example.yaml`

Example scenario demonstrating **attempted tool misuse or privilege escalation**.

This scenario illustrates how an agent should avoid invoking privileged tools when prompted by untrusted input.

---

### `scenario-data-exfiltration-example.yaml`

Example scenario demonstrating a **data exfiltration attempt**.

This scenario illustrates how a security test can verify that an agent does not expose sensitive data such as credentials, system prompts, or secrets.

---

## Adding new examples

Contributors may add additional example artifacts to demonstrate OpenPAKT usage patterns.

When adding examples, please follow these guidelines:

- Examples **must align with the current OpenPAKT specification**.
- Examples **must remain non-normative**.
- Examples **must not introduce new required fields or semantics**.
- Scenario examples should contain **a single scenario object per file**.
- File names should clearly describe the example they represent.

Recommended naming conventions:

```text
scenario-<attack-type>-example.yaml
report-<description>-example.json
```

Examples should remain **small, readable, and implementation-agnostic**.

---

## Purpose of examples

Example artifacts help:

- implementers understand how OpenPAKT documents are structured
- tool developers build compatible scanners and CI integrations
- contributors create reproducible security testing scenarios
