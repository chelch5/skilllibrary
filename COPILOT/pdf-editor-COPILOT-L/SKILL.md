---
name: pdf-editor
description: Performs PDF manipulations such as page operations, form filling, annotation, or targeted edits under explicit constraints. Use when modifying existing PDF documents.
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
  tags: [pdf, editing, manipulation, documents]
---

# Purpose
Performs PDF manipulations such as page operations, form filling, annotation, or targeted edits under explicit constraints.

# When to use this skill
Use when:
- Merging, splitting, or reordering PDF pages
- Filling PDF form fields programmatically
- Adding annotations or watermarks to PDFs

Do NOT use when:
- Creating PDFs from scratch (use pdf-generation)
- Extracting text content (use pdf-extraction)

# Operating procedure
1. Identify specific manipulation required
2. Use appropriate tool (pypdf, pdftk, pikepdf)
3. Apply changes without modifying unrelated content
4. Validate output preserves original content integrity
5. Check metadata and permissions after edit

# Output defaults
Modified PDF file with only the specified changes applied

# Failure handling
If PDF is encrypted, request password or original source. Never attempt to bypass protection.
