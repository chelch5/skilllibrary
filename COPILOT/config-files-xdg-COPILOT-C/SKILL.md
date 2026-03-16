---
name: config-files-xdg
description: Standardises config paths using XDG Base Directory spec, with environment overrides and user-editable defaults. Use when a CLI needs persistent config. Do NOT use for runtime server config.
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
  tags: [xdg, config, dotfiles, paths, cli]
---

# Purpose
Locates config, data, and cache files according to XDG spec so tools behave predictably across Linux and macOS.

# When to use this skill
Use when:
- A CLI needs to persist user preferences or state
- Implementing config file discovery with env var override
- Deciding between TOML, YAML, or JSON for user config

Do NOT use when:
- Server-side config loaded from environment only
- Config embedded in the binary

# Operating procedure
1. Resolve XDG_CONFIG_HOME (default ~/.config) for config files
2. Resolve XDG_DATA_HOME (default ~/.local/share) for persistent data
3. Resolve XDG_CACHE_HOME (default ~/.cache) for ephemeral cache
4. Support APP_CONFIG env var override pointing to a custom path
5. Document config file format in --help output
6. Provide a config init or config edit subcommand

# Output defaults
Config path resolution function + TOML/YAML config struct + env override logic.

# Failure handling
If config file is missing, create with defaults silently. If config file is malformed, report the path and error; do not silently ignore.
