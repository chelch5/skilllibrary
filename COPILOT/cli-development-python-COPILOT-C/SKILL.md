---
name: cli-development-python
description: Builds command-line tools in Python with sensible packaging, argument parsing, and UX conventions. Use when creating Python CLI applications. Do NOT use for web services.
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
  tags: [python, cli, click, typer, argparse, packaging]
---

# Purpose
Establishes Python CLI conventions using Click or Typer with proper packaging, entry points, and error handling.

# When to use this skill
Use when:
- Building a new Python CLI tool
- Adding subcommands, options, or config file support
- Packaging for pip install or pipx

Do NOT use when:
- Building a web API (use fastapi or flask)
- Shell scripting is sufficient (use bash)

# Operating procedure
1. Use Click or Typer; avoid raw argparse for complex CLIs
2. Define entry point in pyproject.toml [project.scripts]
3. Use @command decorators with type-annotated parameters
4. Read config from env vars with python-dotenv as fallback
5. Handle errors with sys.exit(1) and a clear message to stderr
6. Provide --version option using importlib.metadata

# Output defaults
pyproject.toml entry point + Click/Typer command skeleton + error handling pattern.

# Failure handling
Catch expected exceptions at command boundary; print user-friendly message to stderr and exit 1. Never let a traceback reach the end user.
