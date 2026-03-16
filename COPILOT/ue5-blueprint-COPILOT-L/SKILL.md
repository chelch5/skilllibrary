---
name: ue5-blueprint
description: A specialized Unreal Engine 5 Blueprint skill covering visual scripting patterns, communication, and anti-spaghetti practices. Use when working specifically with UE5 Blueprint graphs.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P2
  maturity: draft
  risk: low
  tags: [ue5, blueprint, visual-scripting, unreal]
---

# Purpose
A specialized Unreal Engine 5 Blueprint skill covering visual scripting patterns, communication, and anti-spaghetti practices.

# When to use this skill
Use when:
- Working with UE5 Blueprint visual scripts
- Designing Blueprint communication architecture
- Refactoring spaghetti Blueprint graphs

Do NOT use when:
- UE4 projects unless patterns translate cleanly
- Pure C++ Unreal work with no Blueprint involvement

# Operating procedure
1. Assess Blueprint graph complexity and identify anti-patterns
2. Apply event-driven communication (interfaces, dispatchers)
3. Encapsulate logic into functions and macros
4. Validate Blueprint compilation errors
5. Document graph flow with comments

# Output defaults
Blueprint graph architecture, communication patterns, refactoring recommendations

# Failure handling
If Blueprint crashes on compilation, isolate the offending node. Consult UE5 Blueprint docs.
