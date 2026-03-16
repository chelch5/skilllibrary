---
name: financial-tracker-ops
description: Sets up and operates financial tracking systems for personal or small business use. Covers budget tracking, expense categorization, and reporting workflows.
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
  tags: [finance, tracking, budgeting, spreadsheet]
---

# Purpose
Sets up and operates financial tracking systems for personal or small business use.

# When to use this skill
Use when:
- Setting up a budget or expense tracking system
- Categorizing and analyzing expenses from transactions
- Generating monthly or quarterly financial summaries

Do NOT use when:
- Enterprise accounting or ERP systems (different scope)
- Investment portfolio management

# Operating procedure
1. Define tracking categories and budget targets
2. Import or enter transaction data
3. Categorize transactions consistently
4. Generate summary report by category and period
5. Identify budget variances and overspend areas

# Output defaults
Financial tracking spreadsheet or report with categories, actuals vs budget, and variances

# Failure handling
If data is inconsistent, audit categorization rules before generating reports.
