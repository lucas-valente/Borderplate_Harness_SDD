---
name: database-mcp-manager
description: "Use when validating database data, reconciling behavior, or diagnosing DB-backed issues. Enforces MCP database query first."
---

# Database MCP Manager

Use MCP database query as first step for data-driven investigation.

## Main Rule

When the task depends on persisted data validation, execute a read-only query with the available database MCP tool before making conclusions.

## When To Use

- check if records exist;
- validate feature impact on persisted data;
- investigate application vs DB mismatch;
- reconcile relations and aggregates;
- verify scoped consistency by business boundary.

## Mandatory Flow

1. read functional/technical context;
2. define objective data hypothesis;
3. run read-only query via MCP;
4. compare expected vs actual;
5. report evidence (query + result + conclusion).

## Safety Rules

- read-only queries only;
- no destructive commands;
- filter by explicit business context when applicable;
- keep scope minimal and explicit.

## Output Format

- hypothesis;
- query;
- evidence;
- divergence (if any);
- next action.
