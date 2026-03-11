Specification: OpenPAKT
Document: Report Schema
Version: v0.1
Status: Draft

# OpenPAKT — Report Schema

## Purpose

This document defines the canonical JSON-serialisable report structure for OpenPAKT scan results.

The v0.1 report schema provides a minimal contract that scanners, CI systems, and security dashboards can use to exchange findings consistently.

## Scope

This document defines:

- report-level metadata
- scan metadata
- target metadata
- summary counts by severity
- findings array structure
- optional extensibility and provenance fields

This document does **not** define the full finding taxonomy, severity model semantics, scenario format, or CI policy behaviour. Those are specified in separate OpenPAKT documents.

## Design goals

The v0.1 report schema is designed to be:

- minimal for early adoption
- deterministic for CI evaluation
- implementation-agnostic
- straightforward to validate with JSON Schema in future revisions
- extensible without breaking the core contract

## Normative guidance

- An OpenPAKT report **MUST** be valid JSON.
- An OpenPAKT report **MUST** include all required fields defined in this document.
- Field names **MUST** use `snake_case`.
- Producers **SHOULD** preserve deterministic key ordering in generated reports.
- Producers **SHOULD** use RFC 3339 UTC timestamps for `scan.timestamp`.

## Top-level structure

An OpenPAKT v0.1 report has the following top-level fields:

- `schema_version` (required)
- `scan` (required)
- `target` (required)
- `summary` (required)
- `findings` (required)
- `metadata` (optional)
- `provenance` (optional)

## Required and optional fields

### Top-level fields

| Field | Type | Required | Description |
|---|---|---|---|
| `schema_version` | string | Yes | OpenPAKT schema version implemented by the report (for v0.1, use `"0.1"`). |
| `scan` | object | Yes | Metadata about the scan run and scanning tool. |
| `target` | object | Yes | Information about what was scanned. |
| `summary` | object | Yes | Count of findings by severity level. |
| `findings` | array | Yes | Zero or more finding objects. |
| `metadata` | object | No | Additional implementation-agnostic key/value metadata. |
| `provenance` | object | No | Optional provenance details about report generation and transport context. |

### `scan` object

| Field | Type | Required | Description |
|---|---|---|---|
| `tool` | object | Yes | Scanner identity and version. |
| `timestamp` | string | Yes | Scan completion timestamp (RFC 3339 UTC recommended). |

### `scan.tool` object

| Field | Type | Required | Description |
|---|---|---|---|
| `name` | string | Yes | Scanner/tool name. |
| `version` | string | Yes | Scanner/tool version. |

### `target` object

| Field | Type | Required | Description |
|---|---|---|---|
| `type` | string | Yes | Target category (for example `repository`, `agent-config`, `workflow`). |
| `path` | string | Yes | Target identifier or path as provided by the scanner. |

### `summary` object

All fields below are required integer counters.

| Field |
|---|
| `critical` |
| `high` |
| `medium` |
| `low` |
| `informational` |

`summary` values **SHOULD** match the severity distribution of entries in `findings`.

### `findings` array

Each item in `findings` is a finding object.

A finding object includes the following fields:

| Field | Type | Required | Description |
|---|---|---|---|
| `id` | string | Yes | Stable identifier for the finding instance. |
| `type` | string | Yes | Finding category identifier. |
| `severity` | string | Yes | Severity value (`critical`, `high`, `medium`, `low`, or `informational`). |
| `component` | string | Yes | Component, file, or logical unit where the finding applies. |
| `description` | string | Yes | Human-readable summary of the issue. |
| `evidence` | object | Yes | Supporting evidence for the finding. |
| `context` | object | No | Additional structured context useful for triage. |
| `references` | array | No | Related links or identifiers relevant to the finding. |
| `metadata` | object | No | Additional implementation-agnostic key/value metadata. |

### `evidence` object

The evidence object is intentionally minimal in v0.1.

| Field | Type | Required | Description |
|---|---|---|---|
| `summary` | string | Yes | Short evidence statement supporting the finding. |
| `location` | string | No | Optional location hint (file path, line span, or logical location). |
| `snippet` | string | No | Optional raw excerpt or snippet. |

## Compact example

```json
{
  "schema_version": "0.1",
  "scan": {
    "tool": {
      "name": "detektor",
      "version": "0.1.0"
    },
    "timestamp": "2026-03-08T10:00:00Z"
  },
  "target": {
    "type": "agent-config",
    "path": "agent-config.yaml"
  },
  "summary": {
    "critical": 0,
    "high": 1,
    "medium": 0,
    "low": 0,
    "informational": 0
  },
  "findings": [
    {
      "id": "finding-001",
      "type": "unsafe-tool-execution",
      "severity": "high",
      "component": "agent-config.yaml",
      "description": "Tool execution lacks command allow-list constraints.",
      "evidence": {
        "summary": "No explicit allow-list found for shell tool invocation.",
        "location": "agent-config.yaml:12-18"
      }
    }
  ],
  "provenance": {
    "generator": "detektor-cli",
    "run_id": "ci-run-1842"
  }
}
```

## Future compatibility notes

Future OpenPAKT versions may expand finding taxonomy definitions, severity semantics, and CI policy integration rules while preserving the core v0.1 report envelope.
