---
name: cobra-go
description: Structures Go CLIs around Cobra commands, flags, and subcommand organisation. Use when adding Cobra to a Go project or reviewing command structure. Do NOT use for non-Go CLIs.
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
  tags: [cobra, go, cli, subcommands, flags]
---

# Purpose
Provides Cobra command organisation patterns: root command, subcommands, persistent flags, and RunE error handling.

# When to use this skill
Use when:
- Adding Cobra to a Go CLI project
- Structuring subcommands and flag inheritance
- Integrating Viper for config binding with Cobra

Do NOT use when:
- Simple single-command tools where the standard flag package may suffice
- Non-Go languages

# Operating procedure
1. Create root command in cmd/root.go with PersistentPreRunE for shared setup
2. Add subcommands as separate files in cmd/
3. Use RunE (not Run) so errors propagate correctly
4. Bind Viper keys to Cobra flags with viper.BindPFlag
5. Set SilenceUsage = true to prevent usage dump on error
6. Add shell completion via cobra.GenBashCompletion

# Output defaults
root.go + example subcommand + Viper binding + completion command.

# Failure handling
Return errors from RunE; Cobra prints them automatically. Use fmt.Errorf with %w for wrapped errors. Never call os.Exit inside a command handler.
