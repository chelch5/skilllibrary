---
name: structured-output-pipelines
description: Builds pipelines that produce structured, typed output at each stage instead of free-form text. Trigger when a workflow needs machine-readable outputs at every step. Do NOT use for UI or user-facing output formatting.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: mcp
  priority: P1
  maturity: draft
  risk: low
  tags: [structured-output, pipelines, typed]
---

# Purpose
Designs multi-stage pipelines where each stage produces schema-validated, structured output, enabling reliable downstream processing.

# When to use this skill
Use when:
- Building an LLM or agent pipeline where outputs feed into other systems
- Replacing free-form text outputs with JSON or typed structured outputs

Do NOT use when:
- Producing user-facing text responses intended for human reading
- Simple single-step tasks that do not chain outputs

# Operating procedure
1. Define the output schema for each pipeline stage
2. Enforce schema validation at each stage boundary
3. Use structured output modes (JSON mode, tool calls, Pydantic) to extract typed data
4. Pass validated structured output as typed input to the next stage
5. Log schema validation failures and reject invalid outputs before forwarding

# Output defaults
A pipeline definition with stage schemas, validation logic, and end-to-end type flow documentation.

# Failure handling
If a stage produces schema-invalid output, retry the stage with explicit schema reminders. After N failures, halt and surface the invalid output for human review.
