---
name: skill-safety-review
description: "Checks a skill for hidden destructive behavior, misleading instructions, or excessive permissions. Useful for any library that might be shared. Trigger when the task context clearly involves skill safety review."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P1
  maturity: draft
  risk: low
  tags: [safety, review, permissions]
---

# Purpose
Audits a skill for instructions that could cause destructive, deceptive, or out-of-scope behaviour when executed by an agent, particularly before the skill is shared, published, or installed in a production environment.

# When to use this skill
Use when:
- A skill is about to be published to a registry or shared outside the original team
- The user says "safety review this skill", "is this skill safe?", or "check for harmful instructions"
- A skill was received from an external source and needs to be vetted before installation
- A skill has been through several edits and may have accumulated unintended instructions

Do NOT use when:
- The review is for code quality or logical correctness (not safety)
- The skill is internal-only and the risk of external misuse is zero
- The goal is to evaluate output quality (use `skill-evaluation`)

# Operating procedure
1. **Check for destructive instructions**: Does any step instruct an agent to: delete files, overwrite data, modify production systems, send external requests, or execute code without explicit user confirmation? Flag each one
2. **Check for scope creep instructions**: Does the skill instruct the agent to do things beyond its stated purpose? An `assumptions-audit` skill that also writes code, or a `planning` skill that directly modifies files, has dangerous scope creep
3. **Check for permission escalation**: Does the skill instruct the agent to request elevated permissions, bypass access controls, or act with more authority than it was given?
4. **Check for deceptive instructions**: Does the skill instruct the agent to: pretend to be a different agent, hide its actions from the user, produce output that misrepresents its source, or suppress error messages?
5. **Check for injection vulnerability**: Does the skill instruct the agent to process user-provided text and then execute or relay that text without sanitisation? (e.g. "pass the user's input directly to the command" is a risk)
6. **Check for data exfiltration patterns**: Does the skill instruct the agent to collect, summarise, or output information beyond what the task requires?
7. **Rate each finding**:
   - **Blocker**: Must be fixed before any use
   - **High**: Should be fixed before sharing outside the team
   - **Low**: Worth noting but not blocking
8. **Issue a clearance verdict**: Safe to publish / Safe with conditions (list conditions) / Not safe (list blockers)

# Output defaults
A findings list with severity ratings, a **Verdict** (Safe / Safe with conditions / Not safe), and a **Required Changes** list for any Blocker findings.

# Failure handling
If the skill is so vague that intent cannot be determined, mark it as **Unverifiable** — a skill whose instructions cannot be understood cannot be cleared as safe.
