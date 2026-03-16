---
name: game-ui-hud
description: Handles menus, HUDs, readability, control prompts, and interaction design for games. Covers both diegetic and non-diegetic UI approaches.
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
  tags: [ui, hud, menu, game-interface]
---

# Purpose
Handles menus, HUDs, readability, control prompts, and interaction design for games.

# When to use this skill
Use when:
- Designing or implementing game menus and HUDs
- Adding controller prompt icons and input legends
- Improving UI readability and accessibility

Do NOT use when:
- Backend systems with no player-facing UI
- Marketing assets or non-interactive graphics

# Operating procedure
1. Define UI hierarchy and screen flow
2. Design HUD elements with performance budgets
3. Add platform-appropriate control prompts
4. Test readability at target resolution and FOV
5. Validate accessibility (color-blind modes, font size)

# Output defaults
UI mockups, HUD layout specs, screen flow diagrams, accessibility checklists

# Failure handling
If UI performance is poor, check overdraw and canvas rebuild frequency.
