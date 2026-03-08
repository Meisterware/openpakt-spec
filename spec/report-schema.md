Specification: OpenPAKT
Document: Report Schema
Version: v0.1
Status: Draft

# OpenPAKT — Report Schema

## Overview

This document defines the **OpenPAKT report schema**, which represents the canonical structure used to describe AI agent security findings.

The report schema enables security scanners to produce portable scan results that can be evaluated by CI systems and integrated into DevSecOps workflows.

## Design Goals

The report schema is designed to:

- represent security findings in a portable format
- support deterministic CI evaluation
- remain language-agnostic and tool-agnostic
- enable interoperability across security scanners

## Specification

The report schema defines the structure for:

- report metadata
- scanner metadata
- scan target information
- findings
- severity levels
- evidence and contextual information

Detailed schema definitions will be specified in future revisions.

## Examples

Example OpenPAKT reports are available in the `examples/` directory.

## Compatibility Considerations

The OpenPAKT report schema is designed to remain compatible with common security reporting formats used in CI environments.
