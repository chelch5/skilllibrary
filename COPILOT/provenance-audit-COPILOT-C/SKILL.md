---
name: provenance-audit
description: "Tracks where each generated skill came from: user request, repo evidence, imported example, or invented extension. You want evidence and traceability, so provenance deserves its own utility. Trigger when the task context clearly involves provenance audit."
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
  tags: [provenance, audit, traceability]
---

# Purpose
Tracks where each generated skill came from: user request, repo evidence, imported example, or invented extension.

# When to use this skill
Use when:
- when the user or repo work clearly points at provenance audit
- when a task in the "Package Scaffolding Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around provenance audit

Do NOT use when:
- The task is unrelated to provenance audit
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when provenance audit would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
