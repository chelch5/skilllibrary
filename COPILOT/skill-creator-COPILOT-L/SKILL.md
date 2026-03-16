---
name: skill-creator
description: "Creates new skills from user intent, then iterates through testing and improvement loops. This is explicitly present in your source files and should be part of the library. Trigger when the task context clearly involves skill creator."
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P0
  maturity: draft
  risk: low
  tags: [skill-creation, iteration, meta]
---

# Purpose
Creates new skills from user intent, then iterates through testing and improvement loops.

# When to use this skill
Use when:
- when creating, adapting, refining, installing, testing, or packaging a skill
- when a task in the "Meta Skill Engineering" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around skill creator

Do NOT use when:
- The task is unrelated to skill creator
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when skill creator would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
