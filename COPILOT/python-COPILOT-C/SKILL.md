---
name: python
description: Holds Python project conventions, typing expectations, structure, and standard validation habits. Use as a base layer for any Python project. Do NOT use for non-Python work.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P0
  maturity: draft
  risk: low
  tags: [python, typing, conventions, packaging, structure]
---

# Purpose
Establishes consistent Python project structure, type annotation standards, and import hygiene across all Python repos.

# When to use this skill
Use when:
- Starting a new Python project
- Reviewing Python code for convention compliance
- Adding type annotations or setting up pyproject.toml

Do NOT use when:
- Working in Go, Rust, or TypeScript projects

# Operating procedure
1. Use pyproject.toml (not setup.py) with hatch or poetry
2. Annotate all function signatures with types; run mypy or pyright
3. Use pathlib over os.path throughout
4. Place source under src/packagename/ layout
5. Use __all__ in modules that export public API
6. Format with black; lint with ruff

# Output defaults
pyproject.toml template + src layout + type annotation examples.

# Failure handling
If mypy reports errors on third-party stubs, add py.typed markers or use # type: ignore with inline comment. Never suppress all type checking globally.
