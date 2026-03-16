---
name: spreadsheet-analysis
description: Analyzes spreadsheet data to extract insights, trends, and summaries. Use when working with tabular data in Excel, Google Sheets, or CSV format.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: business-research-and-optional-domains
  priority: P2
  maturity: draft
  risk: low
  tags: [spreadsheet, data-analysis, excel, csv]
---

# Purpose
Analyzes spreadsheet data to extract insights, trends, and summaries.

# When to use this skill
Use when:
- Analyzing data in an existing spreadsheet
- Identifying trends, outliers, or patterns in tabular data
- Building pivot tables or summary statistics from raw data

Do NOT use when:
- Generating new spreadsheets (use xlsx-generation)
- Complex database queries (use bigquery-skill instead)

# Operating procedure
1. Load and inspect spreadsheet structure
2. Clean data (handle nulls, duplicates, type issues)
3. Build summary statistics and pivot views
4. Identify trends and outliers
5. Document findings with chart or table recommendations

# Output defaults
Analysis summary with statistics, trend findings, and visualization recommendations

# Failure handling
If data quality is poor, clean before analyzing. Document cleaning steps applied.
