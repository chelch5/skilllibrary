---
name: failure-mode-analysis
description: "Enumerates how a system could fail in production, operation, or workflow and what controls reduce each risk. Good for MCP, orchestration, and LLM systems. Trigger when the task context clearly involves failure mode analysis."
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
  tags: [failure-modes, risk, controls]
---

# Purpose
Systematically enumerates how a system, workflow, or component can fail, rates each failure mode by severity and likelihood, and identifies controls that reduce each risk.

# When to use this skill
Use when:
- The user says "what are the failure modes?", "FMEA this", or "how could this break in production?"
- A new system is about to be deployed and failure modes need to be catalogued before go-live
- An orchestration system, agent, or MCP tool is being designed and its failure surface needs mapping
- Post-incident: a system failed and all related failure modes need to be enumerated to prevent recurrence

Do NOT use when:
- The user wants to trace a specific past failure to its root cause (use `root-cause-analysis`)
- The user wants project-level risk analysis (use `premortem`)
- The system has not yet been designed — there is nothing concrete to analyse

# Operating procedure
1. **Decompose the system into components**: List every functional unit — each service, agent, tool, integration, store, and human actor
2. **For each component, enumerate failure modes**: Ask: "In what ways can this component fail to do its job?" Consider:
   - Silent failure (appears to work, produces wrong output)
   - Crash failure (component stops responding)
   - Slow failure (latency degrades until unusable)
   - Corrupt failure (data or state becomes inconsistent)
   - Cascade failure (this component's failure causes downstream failures)
   - Security failure (component is exploited or produces unauthorised output)
3. **For each failure mode, assess**:
   - **Likelihood**: How often does this failure mode typically occur? (Frequent / Occasional / Rare)
   - **Severity**: What is the impact if it occurs? (Critical / High / Medium / Low)
   - **Detectability**: How quickly would this failure be detected? (Immediate / Minutes / Hours / Silent)
4. **Prioritise by Risk Priority Number (RPN)**: Score = Likelihood × Severity × (1/Detectability). Focus controls on high-RPN items
5. **Assign controls to high-priority failure modes**:
   - **Preventive control**: Stops the failure from occurring (validation, circuit breaker, rate limiting)
   - **Detective control**: Catches the failure quickly (alerting, health check, audit log)
   - **Corrective control**: Recovers from the failure (retry logic, fallback, rollback)
6. **Identify single points of failure (SPOF)**: Any component whose failure has no fallback

# Output defaults
A failure mode table (component | failure mode | likelihood | severity | detectability | RPN | controls), a **SPOF List**, and a **Top 5 Risk Items** section.

# Failure handling
If component boundaries are unclear, list the components that could be identified and note which areas of the system need clarification before their failure modes can be enumerated.
