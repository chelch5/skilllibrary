---
name: pdf-generation
description: Generates or exports PDF-ready artifacts cleanly when final distribution format matters. Use when producing deliverables that must be shared as portable, print-ready documents.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [pdf, generation, documents, export]
---

# Purpose
Generates or exports PDF-ready artifacts cleanly when final distribution format matters.

# When to use this skill
Use when:
- Generating a PDF report or document for distribution
- Exporting structured content to PDF format
- Producing print-ready documents with consistent styling

Do NOT use when:
- Extracting content from PDFs (use pdf-extraction)
- Documents intended for web-only consumption

# Operating procedure
1. Choose PDF generation tool appropriate to content (pandoc, weasyprint, reportlab)
2. Apply consistent CSS/styles for print layout
3. Include page numbers, headers, and footers
4. Validate pagination and overflow handling
5. Test output across PDF readers

# Output defaults
PDF file with proper layout, page numbers, headers, and print-ready formatting

# Failure handling
If layout breaks, isolate to specific content type. Test with minimal example.
