---
name: bigquery
description: Applies BigQuery-specific query, cost, and schema guidance for analytics and warehousing workloads. Use when writing or reviewing BigQuery SQL. Do NOT use for OLTP or transactional data access.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P2
  maturity: draft
  risk: low
  tags: [bigquery, gcp, analytics, sql, data-warehouse]
---

# Purpose
Guides BigQuery schema design, query cost optimisation, and partition/cluster strategies for analytical workloads.

# When to use this skill
Use when:
- Writing or optimising BigQuery SQL
- Designing tables with partitioning and clustering
- Controlling query cost via preview and dry-run

Do NOT use when:
- Working with transactional Postgres/SQLite (use those skills)
- Real-time streaming into a hot path

# Operating procedure
1. Define table schema with appropriate NULLABLE vs REQUIRED
2. Choose partition column (DATE or TIMESTAMP preferred)
3. Add clustering columns based on common filter patterns
4. Estimate query cost with dry-run before executing
5. Use parameterised queries to prevent injection
6. Cache repeated reads with materialized views or scheduled queries

# Output defaults
Schema DDL + annotated query with cost estimate + optimisation notes.

# Failure handling
If query exceeds budget, add WHERE partition filter. If schema drift causes errors, run schema diff and apply non-breaking additions only.
