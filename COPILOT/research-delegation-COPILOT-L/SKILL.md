---
name: research-delegation
description: "Delegates read-only evidence gathering to narrow lanes and persists durable findings as artifacts. Useful for keeping research separate from mutation. Trigger when the task context clearly involves research delegation."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [research, delegation, read-only]
---

# Purpose
Delegate read-only research tasks to sub-agents with narrow, explicit scopes, then consolidate findings into durable artifacts without letting research bleed into mutation work.

# When to use this skill
Use when:
- A task requires gathering information before making changes (e.g., "research how library X handles Y")
- Multiple independent research questions can be parallelized across sub-agents
- An agent is about to mix research and editing in the same pass (a drift risk)
- The user says "find out how X works", "look up Y", or "investigate Z before we change anything"

Do NOT use when:
- The research is a single targeted grep or file read (do it directly)
- The task is pure execution with no open questions

# Operating procedure
1. **Define the research scope**: write a one-sentence research question with explicit success criteria (e.g., "Find all places where AuthService is instantiated; success = complete list of call sites")
2. **Scope the blast radius**: specify which directories or files are in scope; explicitly name what is out of scope
3. **Assign to a read-only sub-agent**: the sub-agent may only read, grep, and summarize — no writes, no edits
4. **For parallel questions**: launch separate sub-agents per question simultaneously; do not serialize unnecessarily
5. **Receive findings**: each sub-agent returns a structured findings artifact:
   ```
   QUESTION: <question>
   ANSWER: <direct answer>
   EVIDENCE: <file:line references>
   CONFIDENCE: high / medium / low
   GAPS: <what could not be determined>
   ```
6. **Consolidate into a research artifact** (`docs/research/TOPIC-DATE.md`) before starting mutation work
7. **Hand off to execution**: attach the research artifact to the relevant ticket before any code changes begin

# Output defaults
Research artifact file + consolidated summary. Sub-agents must not modify files.

# Failure handling
If a sub-agent cannot answer a question with high confidence, escalate as a gap rather than guessing. Record gaps explicitly — a known unknown is better than a wrong answer.
