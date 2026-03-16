---
name: godot
description: Applies Godot scene, script, signal, and project organization patterns. Use when the project targets Godot as its engine.
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
  tags: [godot, game-engine, gdscript]
---

# Purpose
Applies Godot scene, script, signal, and project organization patterns.

# When to use this skill
Use when:
- Project uses Godot 3.x or 4.x
- Structuring nodes, signals, or scenes
- GDScript or C# Godot development

Do NOT use when:
- Unity or Unreal projects
- General gamedev theory not tied to Godot's node model

# Operating procedure
1. Confirm Godot version (3.x vs 4.x)
2. Apply node/scene hierarchy best practices
3. Wire signals correctly
4. Organize project file layout
5. Validate exported properties

# Output defaults
GDScript files, scene structures, node wiring diagrams, export configs

# Failure handling
If version unclear, ask. Godot 4 API differs significantly from 3. Fall back to official docs.
