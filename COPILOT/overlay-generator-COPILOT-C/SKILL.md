---
name: overlay-generator
description: "Produces host-specific overlays for OpenAI, Gemini, OpenCode, Copilot, or other clients from a shared skill source. The architecture docs explicitly favor one source skill with multiple target packages. Trigger when the task context clearly involves overlay generator."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P1
  maturity: draft
  risk: low
  tags: [overlay, client, packaging]
---

# Purpose
Produces host-specific overlays for OpenAI, Gemini, OpenCode, Copilot, or other clients from a shared skill source.

# When to use this skill
Use when:
- when the user or repo work clearly points at overlay generator
- when a task in the "Package Scaffolding Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around overlay generator

Do NOT use when:
- The task is unrelated to overlay generator
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when overlay generator would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
