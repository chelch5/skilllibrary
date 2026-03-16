---
name: unreal-engine
description: Applies Unreal project structure, Blueprint/C++ boundaries, asset handling, and engine-specific workflow guidance. Use when Unreal Engine is the project runtime.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P0
  maturity: draft
  risk: low
  tags: [unreal, ue5, cpp, game-engine]
---

# Purpose
Applies Unreal project structure, Blueprint/C++ boundaries, asset handling, and engine-specific workflow guidance.

# When to use this skill
Use when:
- Project uses Unreal Engine (4 or 5)
- Tasks crossing Blueprint and C++ boundaries
- Asset handling and project module layout

Do NOT use when:
- Unity or Godot projects
- General C++ unrelated to Unreal's subsystems

# Operating procedure
1. Identify UE version and module layout
2. Apply Blueprint/C++ split guidelines
3. Follow Unreal naming conventions (U, A, F prefixes)
4. Handle asset references with soft/hard pointer discipline
5. Run editor validation

# Output defaults
C++ classes, Blueprint graphs, .uproject configs, asset import settings

# Failure handling
If UE version is ambiguous, target UE5 LTS. Reference Unreal docs for disputed API.
