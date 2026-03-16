---
name: docx
description: An external-style skill focused on DOCX-oriented document tasks including reading, writing, and manipulating Word documents. Covers both generation and editing use cases.
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
  tags: [docx, word, document, office]
---

# Purpose
An external-style skill focused on DOCX-oriented document tasks including reading, writing, and manipulating Word documents.

# When to use this skill
Use when:
- Working with .docx files programmatically
- Reading or modifying existing Word documents
- All DOCX-related tasks in a unified skill

Do NOT use when:
- PDF-specific tasks (use pdf-extraction or pdf-editor)
- Markdown or plain-text document generation

# Operating procedure
1. Identify DOCX operation (read, write, modify, template)
2. Use python-docx or equivalent library
3. Preserve existing styles when modifying
4. Validate output in Word-compatible reader
5. Handle tracked changes and comments if present

# Output defaults
DOCX files or extracted content depending on operation type

# Failure handling
If styles are corrupted, rebuild from template. Never merge incompatible document formats.
