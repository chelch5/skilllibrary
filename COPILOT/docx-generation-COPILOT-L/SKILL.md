---
name: docx-generation
description: Creates formatted Word-compatible DOCX documents when richer office output is needed. Use when stakeholders require editable Word format.
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
  tags: [docx, word, document, generation]
---

# Purpose
Creates formatted Word-compatible DOCX documents when richer office output is needed.

# When to use this skill
Use when:
- Generating DOCX files from structured content
- Producing editable Word documents for collaboration
- Creating formatted reports in Word format

Do NOT use when:
- PDF-only outputs (use pdf-generation)
- Plain text or markdown deliverables

# Operating procedure
1. Define document structure with styles (Heading1, Body)
2. Populate content with correct style application
3. Add table of contents if document exceeds 5 pages
4. Insert tables and images with captions
5. Validate in Word or LibreOffice Writer

# Output defaults
DOCX file with applied heading styles, table of contents, and consistent formatting

# Failure handling
If styles are missing, apply Normal style as fallback. Validate heading hierarchy.
