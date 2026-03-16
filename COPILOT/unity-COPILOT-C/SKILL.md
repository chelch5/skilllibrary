---
name: unity
description: Applies Unity project structure, component patterns, scenes, assets, and performance-aware coding conventions. Use when the project uses Unity as its primary engine or runtime.
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
  tags: [unity, game-engine, csharp]
---

# Purpose
Applies Unity project structure, component patterns, scenes, assets, and performance-aware coding conventions.

# When to use this skill
Use when:
- Project uses Unity as engine or runtime
- Scaffolding scenes, components, or prefabs
- Optimizing Unity-specific performance issues

Do NOT use when:
- Project uses Godot, Unreal, or another engine
- General C# questions unrelated to Unity

# Operating procedure
1. Identify Unity version and project layout
2. Apply correct component/MonoBehaviour patterns
3. Follow Unity naming conventions and asset organization
4. Validate scene and prefab references
5. Run play-mode tests if available

# Output defaults
C# scripts, prefab configs, scene manifests, Unity asset setup instructions

# Failure handling
If Unity version is ambiguous, target LTS. Fall back to Unity docs for API disputes.
