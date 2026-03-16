---
name: instruction-tuning
description: Applies instruction-following fine-tuning to make base models respond to user directives. Use when training a model to follow instructions. Do NOT use for RLHF-style preference optimisation.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P1
  maturity: draft
  risk: low
  tags: [instruction-tuning, sft, alignment, chat, flan]
---

# Purpose
Establishes instruction-tuning procedures: data format design, task diversity, format consistency, and evaluation of instruction-following capability.

# When to use this skill
Use when:
- Converting a base language model into an instruction-following chat model
- Designing the instruction-response dataset format
- Evaluating instruction-following quality with MT-Bench or AlpacaEval

Do NOT use when:
- Preference optimisation beyond SFT (use preference-optimization)
- Domain-specific task fine-tuning without instruction format (use fine-tuning)

# Operating procedure
1. Curate diverse instruction dataset: task coverage across reasoning, coding, writing, QA
2. Format as system/user/assistant turns in ChatML or provider-specific format
3. Include negative examples: refusals, partial completions, format edge cases
4. Train with next-token prediction loss on assistant turns only
5. Evaluate with MT-Bench (multi-turn) and AlpacaEval (single-turn) post-training
6. Iterate on data mix based on failure categories in evaluation

# Output defaults
Dataset format spec + training mask config + evaluation results template.

# Failure handling
On poor instruction-following scores, analyse failure categories and add targeted examples. On repetition or format collapse, reduce learning rate and add regularisation.
