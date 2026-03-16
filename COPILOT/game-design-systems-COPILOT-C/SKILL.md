---
name: game-design-systems
description: Designs gameplay loops, progression systems, mechanics interplay, and rule coherence. Use when defining or refining game feel, balance, or player progression.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P1
  maturity: draft
  risk: low
  tags: [game-design, gameplay-loops, progression, mechanics]
---

# Purpose
Designs gameplay loops, progression systems, mechanics interplay, and rule coherence.

# When to use this skill
Use when:
- Designing new gameplay loops or mechanics
- Balancing progression and reward systems
- Documenting game rules and win/loss conditions

Do NOT use when:
- Engine-specific implementation details
- Narrative or worldbuilding that doesn't affect mechanics

# Operating procedure
1. Define core loop and player motivations
2. Map out progression tiers and reward cadence
3. Identify mechanics interactions and edge cases
4. Prototype balance values with spreadsheet or simulation
5. Document design decisions as ADRs

# Output defaults
Game design documents, mechanics spreadsheets, loop diagrams, balance tables

# Failure handling
If balance feels wrong, run simulated playtests. Separate feel issues from math issues.
