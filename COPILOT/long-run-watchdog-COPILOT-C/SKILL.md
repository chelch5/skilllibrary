---
name: long-run-watchdog
description: Monitors autonomous workflows for loops, inactivity, repeated errors, or missing outputs and intervenes with a bounded recovery policy. Trigger at the start of any long autonomous run. Do NOT use for short interactive sessions.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P2
  maturity: draft
  risk: low
  tags: [watchdog, monitoring, recovery]
---

# Purpose
Watches long-running autonomous workflows for pathological patterns (loops, stalls, repeated failures) and applies a bounded recovery policy.

# When to use this skill
Use when:
- Launching an autonomous run expected to take many steps or a long time
- Implementing safeguards against infinite loops or stuck states

Do NOT use when:
- The session is short and human-supervised throughout
- Failure is expected to be caught by other gates

# Operating procedure
1. Define watchdog thresholds: max retries per stage, max elapsed time, max repeated identical outputs
2. At each stage transition, check progress against thresholds
3. On threshold breach, attempt a single bounded recovery (retry, replan, or skip with flag)
4. If recovery fails, halt the run and surface a diagnostic report

# Output defaults
A watchdog log with timestamp, threshold checks, interventions taken, and final run disposition.

# Failure handling
If the watchdog itself encounters an error, default to halting the run and emitting a failure notice.
