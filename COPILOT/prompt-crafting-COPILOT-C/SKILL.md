---
name: prompt-crafting
description: "Improves repo-local prompts, command wording, tool instructions, and output templates for ongoing use. Useful beyond initial scaffold because prompts continue changing. Trigger when the task context clearly involves prompt crafting."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [prompts, templates, refinement]
---

# Purpose
Writes, rewrites, or improves agent prompts, system instructions, command descriptions, and output templates to produce more reliable, accurate, and consistent agent behaviour.

# When to use this skill
Use when:
- The user says "write a prompt for X", "improve this prompt", "why is this agent producing bad output?"
- An agent instruction is vague, producing inconsistent results, or drifting from intended behaviour
- A new command, tool, or workflow needs its prompt written from scratch
- An existing AGENTS.md, COMMANDS.md, or skill description needs sharpening

Do NOT use when:
- The user wants to write a SKILL.md (use `skill-authoring`)
- The problem is the tool itself, not the prompt
- The agent is working correctly — no change needed

# Operating procedure
1. **Identify the prompt type**: System instruction, user-facing command description, tool description, output template, or routing description — each has different optimisation targets
2. **State the intended behaviour**: What should the agent do when this prompt fires? Write it in one sentence
3. **Diagnose the current prompt** (if rewriting): What specific failure mode is occurring? (Scope drift? Wrong output format? Hallucination? Under-triggering?)
4. **Apply prompt structure principles**:
   - **Role first**: State who the agent is and what it is responsible for before giving instructions
   - **Constraint before freedom**: State what the agent must NOT do before stating what it can do
   - **Specify output format**: If the output needs a specific shape, describe it with an example or schema
   - **Use positive imperatives**: "Always do X" rather than "Try to do X" or "You might want to do X"
   - **Anchor to evidence**: If the agent should cite, quote, or check sources, state this explicitly
5. **For routing/trigger text** (skill descriptions, tool descriptions): Start with the most discriminating signal word or phrase. State "Use when: [specific trigger]" and "Do NOT use when: [common confusion case]"
6. **Test the prompt against failure cases**: Does the rewritten prompt prevent the failure mode identified in step 3? Walk through the scenario mentally
7. **Remove filler**: Eliminate "please", "try to", "it would be ideal if", and any sentence that does not constrain or instruct behaviour

# Output defaults
The rewritten prompt, preceded by a **Change Summary** explaining what was changed and why. If the prompt was rewritten for a specific failure mode, include a **Before / After** comparison.

# Failure handling
If the intended behaviour cannot be determined, list the three questions that must be answered before the prompt can be written (who uses it, what output is expected, what failure to prevent).
