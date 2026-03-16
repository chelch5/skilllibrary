---
name: unity-scriptableobject-events
description: Uses ScriptableObjects and event-driven patterns to build decoupled Unity architectures. Reduces MonoBehaviour interdependencies and improves testability.
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
  tags: [unity, scriptableobject, event-driven, architecture]
---

# Purpose
Uses ScriptableObjects and event-driven patterns to build decoupled Unity architectures.

# When to use this skill
Use when:
- Unity project needs decoupled event systems
- Avoiding tight coupling between game systems
- Replacing direct references with data-driven events

Do NOT use when:
- Non-Unity projects
- Cases where simple UnityEvents or direct references suffice

# Operating procedure
1. Define ScriptableObject event assets
2. Subscribe/unsubscribe listeners via OnEnable/OnDisable
3. Raise events from game logic scripts
4. Test event flow in isolation
5. Document event asset names and payload types

# Output defaults
ScriptableObject event asset definitions, MonoBehaviour listener scripts, event channel patterns

# Failure handling
If events fire unexpectedly, check subscription lifetime. Ensure OnDisable unsubscribes.
