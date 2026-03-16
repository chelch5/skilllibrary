---
name: postgresql
description: Defines schema, migration, indexing, transaction, and query expectations for PostgreSQL-backed services. Use when building or maintaining Postgres databases. Do NOT use for BigQuery analytics workloads.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P1
  maturity: draft
  risk: low
  tags: [postgresql, sql, migrations, indexing, transactions]
---

# Purpose
Establishes Postgres schema design, migration, indexing, and query conventions for production-safe databases.

# When to use this skill
Use when:
- Designing or reviewing Postgres schemas
- Writing migration files (Flyway, Alembic, goose)
- Choosing index types or query plans

Do NOT use when:
- Analytics at warehouse scale (use bigquery)
- SQLite for lightweight local persistence (use sqlite)

# Operating procedure
1. Use UUIDs or BIGSERIAL for primary keys; document choice
2. Add NOT NULL constraints by default; justify every NULL
3. Create indexes for all foreign keys and common filter columns
4. Use transactions for multi-table writes
5. Test EXPLAIN ANALYZE on queries touching large tables
6. Migrations: additive first, column drops in a separate release

# Output defaults
Schema DDL + migration file + index recommendations.

# Failure handling
On lock timeout, retry or defer the migration to a maintenance window. On constraint violation, surface the specific constraint name in the error response.
