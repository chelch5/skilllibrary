---
name: multiplayer-netcode
description: Handles authority, synchronization, prediction, and state consistency in multiplayer game development. Use when building or debugging networked game systems.
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
  tags: [multiplayer, netcode, synchronization, prediction]
---

# Purpose
Handles authority, synchronization, prediction, and state consistency in multiplayer game development.

# When to use this skill
Use when:
- Implementing authoritative server/client networking
- Designing state synchronization and rollback
- Debugging desync or latency compensation issues

Do NOT use when:
- Single-player games with no networking
- General networking unrelated to game state sync

# Operating procedure
1. Identify authority model (server-auth vs peer)
2. Implement state serialization with delta compression
3. Add client-side prediction and server reconciliation
4. Test under simulated latency and packet loss
5. Document network messages and state machine

# Output defaults
Network message schemas, sync component configs, latency simulation test results

# Failure handling
If desyncs occur, add deterministic logging on both sides. Compare state snapshots.
