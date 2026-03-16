---
name: ux-design
description: Applies layout, hierarchy, readability, interaction flow, and usability reasoning to interface work. Trigger when designing or reviewing UI from a user experience perspective. Do NOT use for visual brand or marketing design.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P0
  maturity: draft
  risk: low
  tags: [ux, design, usability]
---

# Purpose
Applies UX principles—layout, visual hierarchy, interaction flow, and usability—to improve interface design quality.

# When to use this skill
Use when:
- Designing new user interfaces or reviewing existing ones for usability
- Making decisions about layout, information hierarchy, or interaction patterns

Do NOT use when:
- Designing brand assets or marketing materials
- Writing backend or API code

# Operating procedure
1. Define the user's primary task and the most common path through the interface
2. Apply visual hierarchy to guide attention to the most important elements first
3. Reduce cognitive load by grouping related items and removing unnecessary choices
4. Design interaction states: idle, hover, active, error, loading, and empty
5. Validate with a usability walkthrough or user testing before finalizing

# Output defaults
A UX design specification or annotated wireframe with hierarchy, interaction states, and rationale for key decisions.

# Failure handling
If users cannot complete the primary task during testing, prioritize fixing that flow over aesthetic improvements.
