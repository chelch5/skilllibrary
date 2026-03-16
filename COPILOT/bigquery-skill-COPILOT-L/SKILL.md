---
name: bigquery-skill
description: A BigQuery-focused skill for SQL queries, schema design, and data warehouse operations on Google BigQuery. Use when working with BigQuery datasets or pipelines.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [bigquery, sql, data-warehouse, gcp]
---

# Purpose
A BigQuery-focused skill for SQL queries, schema design, and data warehouse operations on Google BigQuery.

# When to use this skill
Use when:
- Writing or optimizing BigQuery SQL queries
- Designing BigQuery schemas and partitioning strategies
- Building data pipelines with BigQuery as the warehouse

Do NOT use when:
- General SQL not targeting BigQuery (syntax differences apply)
- Other GCP services not involving BigQuery

# Operating procedure
1. Understand BigQuery dataset and table structure
2. Write SQL using BigQuery dialect (ARRAY, STRUCT, partitioning)
3. Optimize with partition pruning and clustering
4. Estimate query cost before running
5. Validate results against expected output

# Output defaults
BigQuery SQL queries, schema DDL, partitioning configs, cost estimates

# Failure handling
If query costs are high, add partition filters. Use dry-run to estimate before executing.
