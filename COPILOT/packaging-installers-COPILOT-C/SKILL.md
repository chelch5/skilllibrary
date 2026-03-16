---
name: packaging-installers
description: Handles distribution methods, install scripts, PATH setup, and uninstallation for developer tools. Use when distributing a CLI or tool to end users. Do NOT use for library packaging.
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
  tags: [packaging, installer, distribution, path, install-script]
---

# Purpose
Designs install scripts and packaging artifacts that put a tool on PATH cleanly and provide a working uninstall path.

# When to use this skill
Use when:
- Writing a curl | bash install script for a CLI tool
- Creating a .deb, .pkg, or Homebrew formula
- Deciding on distribution channel (GitHub Releases, npm, pip, homebrew)

Do NOT use when:
- Library packaging for developers (use language-specific skills)
- Container-based distribution (use Docker/OCI)

# Operating procedure
1. Download to a temp dir; verify checksum before install
2. Place binary in ~/.local/bin or /usr/local/bin based on --user vs system flag
3. Detect shell (bash/zsh/fish) and append PATH export to the correct profile
4. Provide an uninstall command that reverses all changes
5. Write idempotent install: re-running does not break existing install
6. Pin version in install URL; support VERSION= env override

# Output defaults
Install script skeleton + checksum verification + PATH injection + uninstall routine.

# Failure handling
On download failure, clean up temp dir and exit non-zero. On PATH conflict, warn but do not overwrite existing binary without --force.
