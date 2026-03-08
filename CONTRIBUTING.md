# Contributing to OpenPAKT

Thank you for your interest in contributing to OpenPAKT.

OpenPAKT is an open specification for representing AI agent security findings, testing scenarios, and CI policy semantics.

## Ways to Contribute

Contributions may include:

- improving specification clarity
- proposing new taxonomy entries
- suggesting improvements to the report schema
- contributing example scenarios
- reporting issues or ambiguities

---

## Proposing Specification Changes

Specification changes should follow this process:

1. Open a GitHub Issue describing the proposed change.
2. Discuss the proposal with maintainers and the community.
3. Submit a Pull Request referencing the issue.
4. Maintainers review the change before merging.

Major changes may be scheduled for future specification versions.

---

## Pull Requests

Pull requests should be small and focused.

Please ensure that:

- the change clearly relates to an existing GitHub issue
- specification terminology remains consistent
- examples remain minimal and implementation-agnostic
- unrelated changes are not included in the same pull request

---

## Branch Naming

Contributions should be developed in a dedicated branch and submitted via a pull request to the `main` branch.

Branches should use clear and descriptive names.

Recommended formats:

- `issue/<number>-<short-slug>` for issue-driven work
- `spec/<short-slug>` for specification drafting or updates
- `docs/<short-slug>` for documentation or governance changes
- `chore/<short-slug>` for repository maintenance

Examples:

```text
issue/1-report-schema
issue/4-scenario-format
spec/finding-taxonomy-refinement
docs/spec-governance
chore/add-pr-template
```

Guidelines:

- use **lowercase**
- use **kebab-case** (`-`) to separate words
- keep branch names **short and descriptive**
- prefer linking branches to an **existing GitHub issue**

All changes should be submitted via a **pull request** and reviewed before merging into `main`.

---

## Language and Style

Specification prose uses **UK English spelling** (e.g. "standardised", "organisation", "behaviour").

Schema fields and identifiers follow **US English spelling** (e.g. `behavior`, `authorization`) to align with common software conventions.

Please keep contributions consistent with these conventions.

---

## Code of Conduct

All contributors must follow the project's [Code of Conduct](CODE_OF_CONDUCT.md).

We welcome constructive discussion and contributions that help improve the clarity and usefulness of the OpenPAKT specification.

