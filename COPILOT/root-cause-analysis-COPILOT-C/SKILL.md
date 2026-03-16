---
name: root-cause-analysis
description: "Investigates why a bug, outage, or process failure happened and what underlying cause actually mattered. Useful once the repo is active. Trigger when the task context clearly involves root cause analysis."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: planning-review-and-critique
  priority: P1
  maturity: draft
  risk: low
  tags: [root-cause, investigation, debugging]
---

# Purpose
Traces a specific failure — a bug, outage, process breakdown, or missed goal — back to its root cause rather than stopping at symptoms or proximate causes.

# When to use this skill
Use when:
- The user says "root cause this", "why did this happen?", "5 Whys", or "post-mortem"
- A bug or outage has occurred and the real cause needs to be identified to prevent recurrence
- A process failure repeated despite apparent fixes — the deeper cause has not been found
- An agent or system produced unexpected output and the source of the deviation needs tracing

Do NOT use when:
- The failure has not occurred yet (use `premortem` or `failure-mode-analysis`)
- The user wants a full FMEA catalogue, not investigation of one specific event
- The failure is fully understood and the user wants remediation, not investigation

# Operating procedure
1. **State the symptom precisely**: Write one sentence describing the observable failure — what happened, when, to what, with what impact. Avoid inferring cause in this statement
2. **Collect available evidence**: List what is known — error messages, logs, git blame, timestamps, inputs that triggered the failure, who reported it
3. **Apply 5 Whys from the symptom**: Ask "Why did X happen?" and answer with the most proximate cause. Then ask "Why did that happen?" Repeat at least 5 times, or until you reach a root cause that is within control to fix
4. **Check for contributing causes (fishbone)**: Apply the Ishikawa categories to ensure no contributing cause is missed:
   - People (wrong understanding, missing skill, communication failure)
   - Process (missing step, unclear procedure, no check)
   - Technology (bug, config error, version mismatch, capacity)
   - Environment (infra, network, third-party service)
   - Data (corrupt, missing, wrong format)
5. **Validate the root cause**: A true root cause passes this test: "If we had fixed this cause before the incident, would the failure have occurred?" If yes, it is not the root cause — keep going
6. **Distinguish root cause from contributing causes**: Name the root cause explicitly. List contributing causes separately
7. **Propose corrective actions**: For the root cause: one action that prevents recurrence. For each major contributing cause: one action that reduces likelihood

# Output defaults
A **Symptom** statement, a **5 Whys chain** (numbered list), a **Fishbone Summary** table, a **Root Cause** statement (one sentence), **Contributing Causes** list, and **Corrective Actions** with owners.

# Failure handling
If insufficient evidence is available, list the specific evidence gaps that prevent completing the 5 Whys chain and state what data needs to be collected before analysis can continue.
