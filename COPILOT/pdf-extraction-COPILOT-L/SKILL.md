---
name: pdf-extraction
description: Extracts structured content, provenance, and layout-aware details from PDF documents. Use when processing PDF files to retrieve text, tables, or metadata with source fidelity.
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
  tags: [pdf, extraction, parsing, documents]
---

# Purpose
Extracts structured content, provenance, and layout-aware details from PDF documents.

# When to use this skill
Use when:
- Extracting text or tables from PDF documents
- Processing PDF files for downstream structured data use
- Parsing PDFs with complex layouts (columns, headers)

Do NOT use when:
- Editing or modifying PDF content (use pdf-editor)
- PDFs that are primarily images (use image-heavy-pdfs)

# Operating procedure
1. Identify PDF structure (text-based vs image-based)
2. Extract content with layout context preserved
3. Handle multi-column and table structures correctly
4. Validate extraction against source pages
5. Output with provenance (page number, section)

# Output defaults
Structured text or JSON with page provenance, table arrays, and section markers

# Failure handling
If text extraction fails, fall back to OCR. Flag low-confidence regions.
