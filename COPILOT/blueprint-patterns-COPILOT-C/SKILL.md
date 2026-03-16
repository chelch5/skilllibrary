---
name: blueprint-patterns
description: Captures good Unreal Blueprint communication patterns and anti-spaghetti practices. A companion to ue5-blueprint focused on reusable architectural patterns.
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
  tags: [blueprint, unreal, visual-scripting, patterns]
---

# Purpose
Captures good Unreal Blueprint communication patterns and anti-spaghetti practices.

# When to use this skill
Use when:
- Applying established Blueprint patterns to new features
- Refactoring messy Blueprint graphs
- Teaching Blueprint best practices in Unreal projects

Do NOT use when:
- C++-only Unreal projects
- Godot or Unity visual scripting systems

# Operating procedure
1. Identify applicable patterns (interface, dispatcher, component)
2. Apply pattern to current Blueprint context
3. Extract reusable macro or function library
4. Document pattern intent in graph comments
5. Validate no circular dependencies

# Output defaults
Pattern templates, refactored Blueprint structures, pattern documentation

# Failure handling
If pattern causes Blueprint loops, use event-driven decoupling instead of direct calls.
