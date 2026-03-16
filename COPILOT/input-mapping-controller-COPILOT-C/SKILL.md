---
name: input-mapping-controller
description: Structures keyboard, mouse, controller, rebinding, and accessibility-friendly input design for games. Ensures consistent cross-device input handling.
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
  tags: [input, controller, keybinding, accessibility]
---

# Purpose
Structures keyboard, mouse, controller, rebinding, and accessibility-friendly input design for games.

# When to use this skill
Use when:
- Adding controller or keyboard remapping support
- Designing accessibility-friendly input systems
- Implementing input action maps in Unity or Unreal

Do NOT use when:
- Backend services with no player input
- Web apps not targeting game controllers

# Operating procedure
1. Define input actions abstractly (not raw keys)
2. Map actions to default bindings per platform
3. Implement rebinding persistence
4. Test with keyboard, mouse, and gamepad
5. Document accessibility considerations

# Output defaults
Input action maps, binding config files, rebinding UI specs

# Failure handling
If controller not detected, verify driver/SDK. Fall back to keyboard defaults gracefully.
