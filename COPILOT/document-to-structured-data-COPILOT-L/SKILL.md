---
name: document-to-structured-data
description: Turns narrative documents into machine-readable fields or structured records. Use when documents contain extractable entities, facts, or relationships.
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
  tags: [extraction, nlp, structured-data, parsing]
---

# Purpose
Turns narrative documents into machine-readable fields or structured records.

# When to use this skill
Use when:
- Extracting structured fields from unstructured document text
- Converting narrative reports into database-ready records
- Parsing forms or questionnaires into structured output

Do NOT use when:
- Documents without extractable structured information
- Tabular data already in structured form (use table-extraction)

# Operating procedure
1. Define target schema with field names and types
2. Extract entities, dates, values using NLP or pattern matching
3. Validate extracted values against constraints
4. Handle missing fields explicitly (null vs absent)
5. Output as JSON or CSV matching target schema

# Output defaults
JSON or CSV with extracted fields matching defined schema, with confidence/null markers

# Failure handling
If extraction confidence is low, flag fields for human verification. Never fabricate values.
