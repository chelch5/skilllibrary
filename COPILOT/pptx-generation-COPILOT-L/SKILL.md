---
name: pptx-generation
description: Creates PowerPoint-compatible slide decks with structured sections and presentation-friendly summaries. Use when a slide format is required for delivery.
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
  tags: [pptx, powerpoint, presentation, slides]
---

# Purpose
Creates PowerPoint-compatible slide decks with structured sections and presentation-friendly summaries.

# When to use this skill
Use when:
- Generating PPTX presentation files from content
- Creating structured slide decks for stakeholders
- Converting a written report into presentation format

Do NOT use when:
- Interactive presentations requiring live coding (use different tool)
- Simple visual content without structured slide needs

# Operating procedure
1. Define slide structure and narrative arc
2. Create title, content, and conclusion slides
3. Apply consistent theme and slide master
4. Add speaker notes for key slides
5. Validate slide count and readability at 16:9

# Output defaults
PPTX file with structured slides, speaker notes, and consistent theme

# Failure handling
If slide count is too high, consolidate detail into appendix slides.
