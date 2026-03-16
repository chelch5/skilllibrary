---
name: pptx
description: An external seed skill focused on PowerPoint PPTX-oriented tasks including reading, writing, and manipulating presentation files. Covers both generation and editing.
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
  tags: [pptx, powerpoint, presentation, office]
---

# Purpose
An external seed skill focused on PowerPoint PPTX-oriented tasks including reading, writing, and manipulating presentation files.

# When to use this skill
Use when:
- Working with .pptx files programmatically
- Reading or modifying existing PowerPoint presentations
- All PPTX-related tasks in a unified skill

Do NOT use when:
- Brand-new presentation creation from scratch (use pptx-generation)
- Google Slides or non-PPTX formats

# Operating procedure
1. Identify PPTX operation (read, write, modify, template)
2. Use python-pptx or equivalent library
3. Preserve existing slide master when modifying
4. Validate output in PowerPoint-compatible viewer
5. Handle slide layouts and placeholders correctly

# Output defaults
PPTX files or extracted content depending on operation type

# Failure handling
If slide layouts are corrupted, rebuild from slide master. Validate placeholder bindings.
