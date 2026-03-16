---
name: skill-anti-patterns
description: "Collects common ways skills fail: vague scope, weak triggers, broad but shallow bodies, or missing evals. Handy as a QA lens when editing skills. Trigger when the task context clearly involves skill anti patterns."
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
  tags: [anti-patterns, quality, review]
---

# Purpose
Identifies specific anti-patterns in a SKILL.md file that reduce its reliability, trigger accuracy, or output quality, and provides the corresponding fix for each.

# When to use this skill
Use when:
- The user says "check this skill for anti-patterns", "what's wrong with this skill?", or "review this skill against quality standards"
- A skill is being reviewed before promotion from draft to stable
- A skill is producing unexpected outputs and a quality audit is needed
- A skill was written quickly and needs a pass for structural issues

Do NOT use when:
- The goal is a full skill rewrite (use `skill-authoring`)
- The goal is routing/trigger improvement specifically (use `skill-trigger-optimization`)
- The skill is confirmed good — no need to scan a healthy skill for problems

# Operating procedure

Check the skill for each of the following anti-patterns. For each one found, mark it as PRESENT and provide the specific fix.

**AP-1: Circular trigger language**
Pattern: "Use when the task clearly involves X" or "when the user or repo work points at X"
Fix: Replace with specific phrases the user would actually say, or specific observable conditions

**AP-2: Boilerplate procedure steps**
Pattern: Steps that say "Keep the scope explicit", "Prefer references, scripts, or examples", or "Decide whether this belongs in the core"
Fix: Delete these steps. They are meta-commentary that survived from a template, not real instructions

**AP-3: Generic output defaults**
Pattern: "Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps"
Fix: Name the specific output format — table, numbered list, named sections, file type — and describe its contents

**AP-4: Generic failure handling**
Pattern: "If inputs are missing, surface the gap as a decision item rather than guessing"
Fix: Name the specific most-common failure for this skill and state the exact response to it

**AP-5: Overloaded purpose**
Pattern: The Purpose section contains "and" more than once, or covers two different task families
Fix: Split the skill (use `skill-variant-splitting`) or narrow the scope

**AP-6: Unmeasurable acceptance**
Pattern: The skill's output cannot be evaluated by an agent without human judgment ("good summary", "appropriate level of detail")
Fix: Define the output with observable criteria — section names, field counts, presence of specific labels

**AP-7: Missing Do NOT use when**
Pattern: No "Do NOT use when" section, or it is empty
Fix: Add 1–3 cases that a user might mistakenly invoke this skill for, naming the correct alternative

**AP-8: Missing failure handling**
Pattern: No failure handling section
Fix: Add one, covering the most common input failure mode for this skill type

# Output defaults
A checklist of all 8 anti-patterns with PRESENT/ABSENT status for each, plus the specific fix for every PRESENT finding. A **Clean Bill of Health** statement if all 8 are ABSENT.

# Failure handling
If the skill file cannot be read or is empty, report that the file is unavailable and no audit can be completed.
