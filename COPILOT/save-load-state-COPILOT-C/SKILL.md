---
name: save-load-state
description: Handles persistence of progress, configuration, checkpoints, and schema evolution in games. Ensures save data survives version upgrades without corruption.
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
  tags: [save-system, persistence, checkpoint, serialization]
---

# Purpose
Handles persistence of progress, configuration, checkpoints, and schema evolution in games.

# When to use this skill
Use when:
- Implementing player save/load functionality
- Designing checkpoint or autosave systems
- Handling save schema migration across versions

Do NOT use when:
- Stateless games with no persistence
- Server-side state in pure multiplayer games

# Operating procedure
1. Define save data schema with versioning field
2. Serialize to JSON or binary with migration hooks
3. Implement atomic writes (temp file + rename)
4. Test load from previous version save files
5. Validate corrupt-save error handling

# Output defaults
Save data schemas, serialization code, migration scripts, checkpoint logic

# Failure handling
If save file is corrupt, offer reset or backup restore. Never silently discard progress.
