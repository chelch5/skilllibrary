---
name: table-extraction
description: Extracts tables from documents while preserving row/column meaning, merged cells, and data provenance. Use when tables are the primary artifact to extract.
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
  tags: [tables, extraction, parsing, structured-data]
---

# Purpose
Extracts tables from documents while preserving row/column meaning, merged cells, and data provenance.

# When to use this skill
Use when:
- Extracting tables from PDFs, Word docs, or HTML pages
- Parsing structured tabular data from documents
- Converting document tables to CSV or JSON format

Do NOT use when:
- Extracting free-form text (use pdf-extraction or document-to-structured-data)
- Creating new tables (use xlsx-generation or csv-ready)

# Operating procedure
1. Detect table boundaries and headers
2. Parse rows and columns preserving merged cell semantics
3. Handle multi-line cells and header hierarchies
4. Output as structured array with column names
5. Validate against visible source table

# Output defaults
Structured table data (JSON arrays or CSV) with column headers and row data

# Failure handling
If table structure is ambiguous, output multiple interpretations and flag for review.
