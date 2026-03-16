---
name: stack-standards
description: "Holds the actual language, framework, validation, and safety rules for the chosen stack. This is currently the most important weak point and needs to become deep and specific. Trigger when the task context clearly involves stack standards."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [stack, standards, conventions]
---

# Purpose
Encode and enforce the project's actual stack conventions — language rules, framework idioms, validation requirements, and safety constraints — so every agent follows them consistently.

# When to use this skill
Use when:
- An agent is about to write code and the stack conventions are not yet loaded
- A code review finds convention violations that should be captured as standards
- A new stack is being introduced and its rules need to be recorded
- An agent asks "how should I do X in this project?"
- Scaffolding generates a new service or module that must conform to existing patterns

Do NOT use when:
- The question is about architecture decisions (use architecture-review skill)
- The question is about a single one-off implementation detail

# Operating procedure
1. **Identify the stack**: language version, framework, runtime, cloud target, test runner, linter config
2. **Load existing standards** from: `AGENTS.md`, `.opencode/`, stack-specific config files (`.eslintrc`, `pyproject.toml`, `Cargo.toml`, etc.)
3. **Apply the following rule categories**:
   - **Naming**: file names, function names, variable names (e.g., snake_case for Python, camelCase for JS)
   - **Error handling**: which error types to use, how to propagate, what must be logged
   - **Imports**: absolute vs. relative, grouping order, forbidden imports
   - **Testing**: test file location, naming convention, minimum coverage threshold, mock policy
   - **Validation**: where input validation happens, which library to use, what must be validated
   - **Secrets**: never hardcode, always use env vars or secrets manager, never log
4. **Flag any code** that violates a standard as a blocker before proceeding
5. If a convention is missing for the current situation, propose the simplest rule consistent with existing patterns and record it in `AGENTS.md`

# Output defaults
Inline annotation of violations + proposed or confirmed rules. If updating `AGENTS.md`, show the diff.

# Failure handling
If no stack config files exist, infer conventions from the existing code corpus. If the corpus is inconsistent, surface the inconsistency and propose a canonical choice.
