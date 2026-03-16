---
name: verification-before-advance
description: Requires proof that a stage is actually complete before the workflow advances to the next stage. Trigger at every stage boundary in a multi-step workflow. Do NOT use as a replacement for final QA or testing.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P1
  maturity: draft
  risk: low
  tags: [verification, stage-gates, progress]
---

# Purpose
Enforces evidence-based stage completion so workflows cannot drift forward on assumptions; each stage must produce verifiable proof before advancing.

# When to use this skill
Use when:
- A multi-step workflow has discrete stages with defined completion criteria
- There is risk of agents claiming completion without actually finishing

Do NOT use when:
- Only one stage exists (no advancement needed)
- Final testing and QA already cover verification adequately

# Operating procedure
1. Define completion criteria for each stage (test pass, artifact present, count matches)
2. After each stage, run the defined verification check
3. Only update the workflow state to the next stage if verification passes
4. Log each verification result (pass/fail) with evidence reference

# Output defaults
A verification log with stage name, criteria checked, evidence found, and pass/fail result.

# Failure handling
If verification fails, keep the stage in-progress, log the failure, and return control to the responsible agent to complete the work.
