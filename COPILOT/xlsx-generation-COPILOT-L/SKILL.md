---
name: xlsx-generation
description: Creates Excel-compatible spreadsheet deliverables with structured sheets, formulas, and validation. Use when a spreadsheet format is required for the output.
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
  tags: [xlsx, spreadsheet, excel, generation]
---

# Purpose
Creates Excel-compatible spreadsheet deliverables with structured sheets, formulas, and validation.

# When to use this skill
Use when:
- Generating Excel or XLSX files from data
- Creating spreadsheets with formulas, charts, or formatting
- Producing structured tabular outputs for stakeholders

Do NOT use when:
- Simple CSV outputs (use csv-ready instead)
- Web-based data tables not intended for download

# Operating procedure
1. Define sheet structure and column headers
2. Populate data with appropriate cell types
3. Add formulas or calculated columns as needed
4. Apply formatting (header styles, number formats)
5. Validate with Excel or LibreOffice Calc

# Output defaults
XLSX file with named sheets, formatted headers, and validated data

# Failure handling
If formula references break, verify sheet names. Avoid circular references.
