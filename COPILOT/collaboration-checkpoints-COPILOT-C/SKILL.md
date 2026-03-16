---
name: collaboration-checkpoints
description: Introduces synchronization moments where agents reconcile assumptions, artifacts, and blockers before merging parallel work. Trigger before merging output from parallel agent lanes. Do NOT use within a single sequential agent lane.
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
  tags: [checkpoints, collaboration, synchronization]
---

# Purpose
Provides synchronization rituals where parallel agent lanes align on assumptions, surface conflicts, and reconcile artifacts before work is merged.

# When to use this skill
Use when:
- Two or more parallel agent lanes are about to merge their outputs
- Divergent assumptions between agents need to be surfaced before integration

Do NOT use when:
- Only one lane is active (no parallel work to reconcile)
- Work is already serialized and no merge is needed

# Operating procedure
1. Collect artifacts from each lane at the checkpoint
2. Identify any conflicting assumptions, naming, or design decisions
3. Resolve conflicts through a defined priority rule or escalation
4. Produce a reconciled artifact set before allowing the merge to proceed

# Output defaults
A checkpoint reconciliation report listing each lane's outputs, conflicts found, resolutions applied, and merged output reference.

# Failure handling
If conflicts cannot be automatically resolved, halt the merge and escalate to the orchestrator with a detailed conflict report.
