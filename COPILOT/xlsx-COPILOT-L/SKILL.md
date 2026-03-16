---
name: xlsx
description: An external seed skill focused on Excel XLSX-oriented tasks including reading, writing, and manipulating spreadsheet files. Covers both generation and data extraction.
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
  tags: [xlsx, excel, spreadsheet, office]
---

# Purpose
An external seed skill focused on Excel XLSX-oriented tasks including reading, writing, and manipulating spreadsheet files.

# When to use this skill
Use when:
- Working with .xlsx files programmatically
- Reading or modifying existing Excel spreadsheets
- All XLSX-related tasks in a unified skill

Do NOT use when:
- Simple CSV outputs (use csv-ready instead)
- New spreadsheet creation with complex formatting (use xlsx-generation)

# Operating procedure
1. Identify XLSX operation (read, write, modify, formula)
2. Use openpyxl, xlrd/xlwt, or equivalent library
3. Preserve existing formatting when modifying
4. Validate formulas and named ranges after edit
5. Test output in Excel or LibreOffice Calc

# Output defaults
XLSX files or extracted data depending on operation type

# Failure handling
If formulas break after edit, check named range references. Avoid breaking existing sheet structure.
