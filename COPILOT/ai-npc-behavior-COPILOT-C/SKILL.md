---
name: ai-npc-behavior
description: Designs and implements NPC logic, state machines, goals, and player-facing behavior patterns. Use when creating believable or interactive non-player characters.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P2
  maturity: draft
  risk: low
  tags: [ai, npc, behavior-tree, state-machine]
---

# Purpose
Designs and implements NPC logic, state machines, goals, and player-facing behavior patterns.

# When to use this skill
Use when:
- Implementing NPC state machines or behavior trees
- Designing reactive or goal-driven NPC AI
- Debugging NPC logic issues or erratic behavior

Do NOT use when:
- Player character logic (which is input-driven)
- ML/RL approaches requiring training pipelines

# Operating procedure
1. Define NPC states and valid transitions
2. Implement behavior trees or utility AI if needed
3. Connect perception (sight, sound) to decision logic
4. Test NPC responses to player actions
5. Document behavior contracts and debug visualizations

# Output defaults
State machine diagrams, behavior tree assets, NPC data configs, debug overlay specs

# Failure handling
If NPC gets stuck, add pathfinding debug visualization. Check NavMesh coverage.
