---
name: skill-evaluation
description: "Evaluates whether a skill routed correctly and produced higher-quality results than a baseline. Useful when you want evidence that a skill is actually helping. Trigger when the task context clearly involves skill evaluation."
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
  tags: [evaluation, quality, routing]
---

# Purpose
Evaluates a skill's quality on two dimensions: routing accuracy (does it trigger on the right inputs?) and output quality (is the output better than what the agent would produce without the skill?).

# When to use this skill
Use when:
- The user says "evaluate this skill", "is this skill working?", or "how good is this skill?"
- A skill has been deployed and its value needs to be measured before promoting from draft to stable
- Two competing skill versions need comparison to determine which to keep
- A skill is suspected of undertriggering or overtriggering

Do NOT use when:
- The user wants to run automated eval tests (use `skill-eval-runner`)
- The skill has never been used — evaluate after at least 3–5 real uses
- The skill is being evaluated for safety or scope issues (use `skill-safety-review`)

# Operating procedure
1. **Collect evaluation inputs**: Gather 3–10 representative prompts that should trigger this skill and 3–5 prompts that should NOT trigger it
2. **Evaluate routing accuracy**:
   - For each trigger prompt: does the skill fire? (Yes/No/Uncertain)
   - For each non-trigger prompt: does the skill NOT fire? (Correct/False positive)
   - Calculate trigger precision: correct triggers / (correct triggers + false positives)
   - Calculate trigger recall: correct triggers / (correct triggers + missed triggers)
3. **Evaluate output quality against a baseline**:
   - Run a representative trigger prompt through the skill
   - Run the same prompt without the skill (baseline: the model's unaided response)
   - Compare on: completeness (did it cover all expected elements?), specificity (concrete vs. vague), actionability (are outputs usable without further interpretation?), accuracy (are claims correct?)
4. **Rate each quality dimension**: Worse than baseline / Same / Better — with one sentence of evidence
5. **Identify the skill's strongest and weakest points**: What does it reliably improve? Where does it add no value or degrade output?
6. **Issue an overall verdict**:
   - **Promote**: Routing accurate, output consistently better than baseline
   - **Refine**: Core value present but specific issues identified (list them)
   - **Demote or retire**: Routing unreliable or output consistently no better than baseline

# Output defaults
A **Routing Accuracy** table (precision and recall), an **Output Quality** comparison for the representative case, and a **Verdict** with specific evidence. If "Refine" verdict, list the exact issues to fix.

# Failure handling
If no real usage data exists, run the evaluation using synthetic test prompts and label all findings as **Synthetic (not validated)**.
