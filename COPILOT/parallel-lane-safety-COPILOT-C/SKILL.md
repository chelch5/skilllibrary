---
name: parallel-lane-safety
description: Determines which tickets or change sets can safely proceed in parallel and which must serialize. Trigger when planning swarm-style or multi-agent parallel work. Do NOT use when all work is already known to be sequential.
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
  tags: [parallel, safety, concurrency]
---

# Purpose
Analyzes work items to identify safe parallelism opportunities and conflict risks, preventing agents from stepping on each other.

# When to use this skill
Use when:
- Multiple agents could work simultaneously on different parts of the codebase
- Planning a swarm-style execution where work order matters

Do NOT use when:
- The work is already confirmed to be strictly sequential
- Only one agent is active at a time

# Operating procedure
1. List all pending work items with their file/module scope
2. Identify shared dependencies, shared files, and shared state
3. Group items that share scope into serialized batches; group independent items for parallel execution
4. Assign lanes and enforce that lane agents do not stray outside their scope

# Output defaults
A parallelism plan with safe-to-parallelize groups, serialized batches, and conflict warnings.

# Failure handling
If a conflict is detected mid-run, pause the conflicting lanes, resolve the dependency, then re-evaluate the plan before continuing.
