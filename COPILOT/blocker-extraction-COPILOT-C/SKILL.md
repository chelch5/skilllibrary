---
name: blocker-extraction
description: "Identifies what decisions, assets, or evidence truly block progress and separates them from minor unknowns. Useful for ticket flow and planning hygiene. Trigger when the task context clearly involves blocker extraction."
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
  tags: [blockers, extraction, planning]
---

# Purpose
Scans a plan, ticket, or status document to identify what genuinely cannot proceed until something external resolves, separating true blockers from noise, unknowns, and deferrable risks.

# When to use this skill
Use when:
- The user says "what's blocking us?", "extract the blockers", or "what do we need before we can proceed?"
- A sprint, project, or ticket is stalled and the blockers need to be made explicit
- A status update contains a mix of blockers, risks, and open questions that need untangling
- An agent workflow is stuck and the blocker needs to be identified before escalating

Do NOT use when:
- The user wants general risk analysis (use `premortem`)
- The goal is to prioritise work, not identify what is blocking it
- Everything is moving and there are no blockers — this skill has no output in that case

# Operating procedure
1. **Collect all stated problems**: Read the plan, tickets, or status. List every item flagged as blocked, unclear, waiting, or dependent
2. **Apply the blocker test**: For each item, ask: "Can work proceed on this without this being resolved?" If yes, it is not a blocker. If no, it is a blocker. Be strict — most "unknowns" are not true blockers
3. **Classify each blocker**:
   - **Decision blocker**: A choice must be made by a person before work can continue. Name who owns the decision
   - **Dependency blocker**: An external system, team, or artifact must be delivered first. Name the dependency and its owner
   - **Information blocker**: A specific piece of data or evidence is required and does not yet exist. Name what is needed
   - **Resource blocker**: People, budget, or access are unavailable. Name the specific resource
4. **Assess how long each blocker has been active**: If a blocker is more than one sprint old, flag it as **Stale Blocker** — it may be accepted risk masquerading as a blocker
5. **For each blocker, write an unblock action**: One specific action, one owner, and a deadline. If no action exists, the blocker is either a risk to accept or a reason to cancel/descope
6. **Separate non-blockers**: List items that appeared to be blockers but are actually: deferred decisions, accepted unknowns, or items that can be worked around

# Output defaults
A **True Blockers** list with type, owner, and unblock action per item. A **Non-Blockers** list with brief explanation. A **Stale Blockers** callout for anything unresolved for more than one cycle.

# Failure handling
If the input does not contain enough status information to determine what is genuinely blocking versus what is merely uncertain, list the three questions that would resolve the ambiguity.
