---
name: csv-ready
description: Shapes extracted or synthesized data into clean CSV-compatible form with stable headers and consistent values. Use when CSV format is the required deliverable.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [csv, data, tabular, export]
---

# Purpose
Shapes extracted or synthesized data into clean CSV-compatible form with stable headers and consistent values.

# When to use this skill
Use when:
- Producing clean CSV output from extracted or processed data
- Normalizing data to consistent CSV format for downstream use
- Validating CSV headers and value types before export

Do NOT use when:
- Complex multi-sheet spreadsheets (use xlsx-generation)
- Data requiring rich formatting or formulas

# Operating procedure
1. Define column headers with stable names (no spaces, lowercase)
2. Ensure consistent value types per column
3. Handle null/missing values explicitly (empty string or NULL)
4. Validate row count against source
5. Output UTF-8 encoded CSV with header row

# Output defaults
UTF-8 CSV file with stable headers, consistent types, and no formatting

# Failure handling
If encoding issues arise, force UTF-8 output. Validate with csv.reader.
