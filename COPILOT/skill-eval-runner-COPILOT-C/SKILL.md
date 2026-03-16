---
name: skill-eval-runner
description: "Runs trigger tests, behavior tests, baseline comparisons, and report aggregation for skills. The architecture docs and Claude creator loop both imply this as mandatory infrastructure. Trigger when the task context clearly involves skill eval runner."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P1
  maturity: draft
  risk: low
  tags: [eval, testing, benchmark]
---

# Purpose
Executes a skill's test suite (from the `tests/` folder created by `skill-testing-harness`) and produces a structured report covering trigger accuracy, behaviour correctness, and comparison against baseline.

# When to use this skill
Use when:
- The user says "run the skill eval", "test this skill", or "run the tests for this skill"
- A skill has been modified and regression testing is needed before promoting it
- A CI check or pre-release validation requires a documented eval run
- A skill's quality needs to be measured before inclusion in a catalog or library release

Do NOT use when:
- No `tests/` folder exists for the skill — build one first (use `skill-testing-harness`)
- The goal is to evaluate skill quality without running tests (use `skill-evaluation` for manual evaluation)
- The goal is to benchmark two skill versions (use `skill-benchmarking`)

# Operating procedure
1. **Locate the test suite**: Check for `SKILLNAME/tests/triggers.md`, `behaviour.md`, and `baseline.md`. Confirm all three exist before running; note which are missing
2. **Run trigger tests** (from `tests/triggers.md`):
   - For each positive test case: present the prompt to the skill context and check if the skill would fire (Yes/No)
   - For each negative test case: confirm the skill does NOT fire
   - Record: prompt, expected trigger, actual trigger, Pass/Fail
3. **Run behaviour tests** (from `tests/behaviour.md`):
   - For each test case: run the skill with the provided input
   - Check the output against `expected_output_contains`: does the output include each required element?
   - Record: test ID, each expected element, Present/Absent, overall Pass/Fail
4. **Run baseline comparison** (from `tests/baseline.md`):
   - Run the representative prompt with the skill active
   - Note which `with_skill_expected` elements are present in the output
   - Note which `baseline_expected` elements would be present in unaided output
   - Compute: skill adds value? (Yes if at least 2 expected elements are present that baseline would lack)
5. **Aggregate results**:
   - Trigger precision: correct triggers / (correct triggers + false positives)
   - Trigger recall: correct triggers / (correct triggers + missed triggers)
   - Behaviour pass rate: passed behaviour tests / total behaviour tests
   - Baseline win: Yes/No with evidence
6. **Issue the eval verdict**: Pass (all rates ≥ 80%, baseline win = Yes) / Pass with issues (any rate 60–79%) / Fail (any rate < 60% or baseline win = No)

# Output defaults
An **Eval Report** with: trigger test results table, behaviour test results table, baseline comparison summary, aggregate metrics, and a **Verdict** (Pass / Pass with issues / Fail). Include the date and skill version evaluated.

# Failure handling
If the skill produces no output when run (silent failure), record as a Fail with reason "No output produced" and halt remaining tests for that test case. Do not skip — a silent skill is a failed skill.
