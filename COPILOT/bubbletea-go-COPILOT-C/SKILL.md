---
name: bubbletea-go
description: Builds stateful terminal UIs in Go with Bubble Tea models, updates, and views. Use when adding interactive TUI components to a Go CLI. Do NOT use for simple output-only CLIs.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P2
  maturity: draft
  risk: low
  tags: [bubbletea, go, tui, interactive, terminal]
---

# Purpose
Structures Bubble Tea programs with clean Model/Update/View separation and composable sub-models.

# When to use this skill
Use when:
- Adding interactive selection, progress, or form UIs to a Go CLI
- Composing multiple Bubble Tea components into one screen
- Handling keyboard events and terminal resize

Do NOT use when:
- Output-only CLIs with no interaction needed
- Non-Go projects (use tui-development for generic patterns)

# Operating procedure
1. Define Model struct with all UI state
2. Implement Init(), Update(msg), View() on the model
3. Use tea.Cmd for async work (network, filesystem)
4. Compose sub-models via embedding or delegation
5. Handle WindowSizeMsg for responsive layout
6. Use lipgloss for styling; define a shared style set

# Output defaults
Model skeleton + Update switch + View render function + lipgloss style definitions.

# Failure handling
On tea.Cmd error, wrap in a custom Err message type and handle in Update. Never panic in View; return error state string instead.
