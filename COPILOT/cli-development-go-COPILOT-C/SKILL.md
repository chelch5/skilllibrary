---
name: cli-development-go
description: Builds command-line tools in Go with clean command structure, config handling, and validation. Use when developing Go CLI applications. Do NOT use for service/API backends.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cli-systems-and-ops
  priority: P0
  maturity: draft
  risk: low
  tags: [go, cli, commands, flags, config]
---

# Purpose
Establishes idiomatic Go CLI structure with command grouping, flag validation, config loading, and helpful error output.

# When to use this skill
Use when:
- Bootstrapping a new Go CLI project
- Adding subcommands, persistent flags, or config file support
- Reviewing CLI UX: help text, exit codes, error messages

Do NOT use when:
- Building a Go API service (use go-api-service)
- Interactive TUI needed (add bubbletea-go)

# Operating procedure
1. Use Cobra for command structure (see cobra-go for details)
2. Load config via Viper with env var override support
3. Validate required flags before executing command logic
4. Write to stderr for errors, stdout for data output
5. Return exit code 1 for errors, 0 for success
6. Provide --version flag with build-time injection

# Output defaults
main.go + root command + example subcommand + config loading snippet.

# Failure handling
Surface friendly error messages to stderr. Wrap underlying errors with context. Never print stack traces to end users.
