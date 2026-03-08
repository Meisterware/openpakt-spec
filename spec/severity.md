Specification: OpenPAKT
Document: Severity Model
Version: v0.1
Status: Draft

# OpenPAKT — Severity Model

## Overview

This document defines the **severity model** used to represent the impact and urgency of security findings in OpenPAKT reports.

The severity model enables CI systems to consistently interpret and evaluate security findings produced by different tools.

## Design Goals

The severity model is designed to:

- support deterministic CI policy enforcement
- provide consistent interpretation of security findings
- remain simple and implementation-agnostic
- allow mapping from vendor-specific severity systems

## Specification

The severity model defines a set of standardised severity levels used in OpenPAKT findings.

Detailed definitions and evaluation semantics will be defined in future revisions.

## Examples

Examples demonstrating severity usage are included in the OpenPAKT report examples located in the `examples/` directory.

## Compatibility Considerations

The severity model is designed to support mapping to other security reporting formats commonly used in DevSecOps workflows.
