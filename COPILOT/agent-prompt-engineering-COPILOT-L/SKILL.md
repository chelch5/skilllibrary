---
name: agent-prompt-engineering
description: "Designs and hardens prompts for planners, implementers, reviewers, utilities, and workflow commands. Your reports repeatedly identified prompt hardening as necessary for weak-model reliability. Trigger when the task context clearly involves agent prompt engineering."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [prompts, agents, engineering]
---

# Purpose
Designs and hardens prompts for planners, implementers, reviewers, utilities, and workflow commands.

# When to use this skill
Use when:
- when the user or repo work clearly points at agent prompt engineering
- when a task in the "Package Scaffolding Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around agent prompt engineering

Do NOT use when:
- The task is unrelated to agent prompt engineering
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when agent prompt engineering would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
