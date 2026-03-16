---
name: tui-development
description: Applies terminal UI patterns, event loops, layout, and keyboard-centric UX to text interfaces. Use when building interactive terminal applications. Do NOT use for web UI development.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P1
  maturity: draft
  risk: low
  tags: [tui, terminal, interactive, keyboard, layout]
---

# Purpose
Guides terminal UI design with keyboard-first UX, responsive layout, colour/style conventions, and graceful degradation.

# When to use this skill
Use when:
- Designing the UX flow of an interactive terminal application
- Choosing between Bubble Tea (Go), Textual (Python), or similar frameworks
- Handling terminal resize, colour depth, and accessibility

Do NOT use when:
- Web browser-based UI (use frontend skills)
- Simple output-only CLIs with no interaction

# Operating procedure
1. Define key bindings upfront; provide ? help screen
2. Use a model-update-view loop to separate state from rendering
3. Design for 80-column minimum; test at 40-column for narrow terminals
4. Degrade gracefully when NO_COLOR env var is set
5. Handle Ctrl+C and Ctrl+Z correctly for clean exit/suspend
6. Test with screen readers via terminal accessibility guidelines

# Output defaults
Key binding map + layout design sketch + framework selection recommendation.

# Failure handling
On terminal capability error (e.g., no colour support), fall back to plain text output. Never crash on SIGWINCH (resize signal).
