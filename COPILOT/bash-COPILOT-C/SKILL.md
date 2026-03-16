---
name: bash
description: Applies shell scripting safety, quoting, error handling, and portable command composition. Use when writing Bash scripts or reviewing shell code. Do NOT use for Python or Go CLI development.
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
  tags: [bash, shell, scripting, safety, portability]
---

# Purpose
Enforces safe Bash scripting with strict mode, proper quoting, error trapping, and portable POSIX idioms.

# When to use this skill
Use when:
- Writing automation scripts, install scripts, or CI hooks in Bash
- Reviewing shell scripts for correctness and safety
- Deciding between Bash and a higher-level language for a task

Do NOT use when:
- The task warrants a full Python or Go CLI (use cli-development-python or cli-development-go)
- Cross-platform Windows support is required (use cross-platform-shell)

# Operating procedure
1. Start every script with set -euo pipefail
2. Quote all variable expansions: "$var" not $var
3. Use [[ ]] for conditionals; avoid [ ] for bash-specific scripts
4. Trap ERR and EXIT for cleanup
5. Use local variables inside functions
6. Validate required environment variables at script top

# Output defaults
Script skeleton with strict mode + input validation + cleanup trap.

# Failure handling
On unexpected exit, ERR trap logs the failing line number and exits non-zero. Never silently continue after a failed command.
