---
name: document-writing
description: Writes internal or external documents with explicit structure, evidence, and audience-aware clarity. Use when producing any formal written artifact for human consumption.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P0
  maturity: draft
  risk: low
  tags: [documentation, writing, technical-writing, clarity]
---

# Purpose
Writes internal or external documents with explicit structure, evidence, and audience-aware clarity.

# When to use this skill
Use when:
- Writing technical guides, proposals, or reports
- Structuring documents with clear sections and evidence
- Producing audience-targeted written communication

Do NOT use when:
- Generating code, not prose
- Short informal messages or chat responses

# Operating procedure
1. Identify document type and audience
2. Define structure (intro, body, conclusion) with section headers
3. Write with evidence citations where applicable
4. Review for clarity and jargon appropriateness
5. Apply consistent formatting and style

# Output defaults
Markdown or structured documents with clear headings, evidence, and conclusion

# Failure handling
If scope is unclear, define document goals before writing. Never pad with filler.
