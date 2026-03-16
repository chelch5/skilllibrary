---
name: skill-benchmarking
description: "Measures pass rate, time, tokens, and qualitative win-rate for a skill versus alternatives. Useful when the library gets large and competing variants appear. Trigger when the task context clearly involves skill benchmarking."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P2
  maturity: draft
  risk: low
  tags: [benchmarking, metrics, comparison]
---

# Purpose
Compares a skill's performance against a baseline or competing variant on defined metrics — output quality, trigger accuracy, token cost, and task completion rate — to determine which version to keep.

# When to use this skill
Use when:
- Two versions of a skill exist and one must be chosen as the canonical version
- A skill has been refined and the new version's improvement over the old needs to be quantified
- A library audit is needed to determine which skills are worth keeping versus retiring
- The user says "benchmark this skill", "compare these skill versions", or "is this skill worth using?"

Do NOT use when:
- Only one version of a skill exists and there is nothing to compare it against (use `skill-evaluation`)
- The comparison is qualitative only and no metrics are needed
- The skills being compared have completely different scopes — comparison is meaningless

# Operating procedure
1. **Define the benchmark scope**: Which skill(s) are being compared? What is the baseline? (Unaided model, previous version, competing skill)
2. **Select the test suite**: Use or create 5–10 representative test prompts covering the skill's trigger range. If a `tests/` folder exists (from `skill-testing-harness`), use those fixtures
3. **Define the metrics to measure**:
   - **Trigger accuracy**: Precision and recall across the test prompts
   - **Output quality score**: Rate each output on: completeness (0–3), specificity (0–3), actionability (0–3). Total: /9
   - **Token cost**: Approximate token count of the skill instructions + typical output
   - **Task completion rate**: For behaviour tests, did the output satisfy all `expected_output_contains` criteria? (Pass/Fail per test)
4. **Run each skill/baseline against all test prompts**: Record scores for each metric
5. **Build the comparison table**: Rows = skills being compared, Columns = metrics. Fill in scores
6. **Compute the win rate**: For quality comparisons, count the number of test cases where each skill outperforms the others
7. **State the winner and confidence**: Name the winning skill version with its win rate and the margin over the runner-up. State if the margin is too small to be confident (< 20% win rate advantage = insufficient evidence)

# Output defaults
A **Benchmark Configuration** section (skills compared, test suite, metrics), a **Results Table** (skills × metrics), a **Win Rate Summary**, and a **Recommendation** stating which version to promote and any conditions.

# Failure handling
If test prompts are unavailable, build a minimal 5-prompt test suite using the skill's trigger section before running the benchmark.
