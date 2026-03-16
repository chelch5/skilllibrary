---
name: cross-platform-shell
description: Covers shell and path differences across Linux, macOS, and Windows for tools that must travel. Use when a script or CLI must run on multiple OSes. Do NOT use for Linux-only server scripts.
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
  tags: [cross-platform, shell, windows, macos, linux, portability]
---

# Purpose
Identifies and resolves platform-specific shell, path, and binary differences for portable developer tools.

# When to use this skill
Use when:
- A Makefile, CI script, or CLI must run on Linux, macOS, and Windows
- Reviewing a script that uses Linux-specific utilities
- Packaging a tool with platform-specific install paths

Do NOT use when:
- Linux-only server automation (use bash or linux-ubuntu-ops)
- Language-level portability issues (use the relevant language skill)

# Operating procedure
1. Use forward slashes in paths; use filepath.Join() in Go, os.path.join() in Python
2. Avoid GNU-specific flags; prefer POSIX equivalents
3. Detect OS via GOOS, sys.platform, or $OSTYPE
4. Provide PowerShell equivalents for Windows users in README
5. Use shebang #!/usr/bin/env bash for portability on macOS/Linux
6. Test in CI matrix: ubuntu-latest, macos-latest, windows-latest

# Output defaults
Platform detection snippet + path handling examples + CI matrix template.

# Failure handling
If a platform-specific utility is unavailable, fail with an explicit error naming the missing dependency and how to install it.
