# DATA_ARCHITECTURE.md

Template for documenting how a project stores, interprets, and reuses data.

## Principle

Define the data model before scaling features. The system should make it clear what is source data, what is derived data, what is cached, and what is generated analysis.

## Recommended Sections

Project-specific versions of this file should define:

- primary data store
- entity model
- event log
- cache policy
- generated artifacts
- retention policy
- privacy boundaries
- analytics model
- external provider strategy
- future semantic or vector retrieval layer, if needed

## Source Data Vs Analysis

Keep source facts separate from generated interpretation.

Example:

```text
Fact:
  price = 0.132
  source = provider
  observed_at = timestamp
  confidence = high

Analysis:
  short thesis, risk summary, recommendation, or report text
  generated from known input IDs
```

This makes stale data, missing data, provider errors, and report quality easier to inspect.

## Cache Policy

Cache by stable entity and data type, not only by user query.

Examples:

```text
entity:chain:contract + market_snapshot
entity:chain:contract + holder_summary
entity:project + docs_summary
report_type + report_version + entity
```

Each data type should have its own TTL based on how fast it changes.

## Vector Search

Use vector search as a retrieval layer when semantic lookup is useful. Do not make it the primary database for facts, IDs, counts, audit logs, or permissions.

Rule of thumb:

```text
SQL or structured store = facts, IDs, joins, audit trail
Vector store = similarity, fuzzy memory, semantic search
LLM = interpretation
```
