---
name: skill-testing-harness
description: "Sets up repeatable prompts, fixtures, and comparison runs for skill development. This formalizes the test loop described in the creator docs. Trigger when the task context clearly involves skill testing harness."
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
  tags: [testing, harness, fixtures]
---

# Purpose
Creates a reusable set of test fixtures, trigger prompts, and expected output checks for a skill so it can be evaluated consistently during development and after changes.

# When to use this skill
Use when:
- The user says "build a test harness for this skill", "create test cases for this skill", or "set up skill tests"
- A skill is being developed and needs repeatable test cases to verify it works correctly
- A skill is being modified and regression tests are needed to confirm existing behaviour is preserved
- A skill evaluation is needed but no test fixtures yet exist (prerequisite for `skill-eval-runner`)

Do NOT use when:
- The harness already exists — run it instead (use `skill-eval-runner`)
- The skill is too early-draft to define expected outputs
- The skill is being retired

# Operating procedure
1. **Create a `tests/` directory** inside the skill folder: `SKILLNAME/tests/`
2. **Write trigger tests** in `tests/triggers.md`:
   - 5 prompts that SHOULD trigger the skill (positive cases) — use the exact language from the skill's "Use when" section
   - 3 prompts that should NOT trigger the skill (negative cases) — use the "Do NOT use when" section
   - For each test: a `prompt:` field and an `expected_trigger:` field (yes/no)
3. **Write behaviour tests** in `tests/behaviour.md`:
   - 3 representative prompts with realistic input content
   - For each: `prompt:`, `input:` (the content the user would provide), and `expected_output_contains:` (a list of specific elements that must appear in the output — section names, key terms, minimum structure)
4. **Write a baseline comparison** in `tests/baseline.md`:
   - One representative test prompt
   - `with_skill_expected:` section describing the quality improvements the skill should produce over the baseline
   - `baseline_expected:` section describing what the unaided model would typically produce
5. **Create `tests/README.md`**: List what each test file contains and how to run them with `skill-eval-runner`
6. **Populate `expected_output_contains` conservatively**: Only require elements that the skill's operating procedure definitively produces, not aspirational outputs

# Output defaults
A `tests/` folder containing: `triggers.md`, `behaviour.md`, `baseline.md`, and `README.md`. Each file in the format described above with all test cases filled in.

# Failure handling
If the skill's operating procedure is too vague to write specific expected outputs, note which steps need to be made more concrete before expected outputs can be defined.
