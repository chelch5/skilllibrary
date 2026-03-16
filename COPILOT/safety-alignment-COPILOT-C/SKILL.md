---
name: safety-alignment
description: Applies safety alignment procedures to LLMs including RLHF, constitutional AI, and red-teaming. Use when training or evaluating model safety. Do NOT use for runtime safety guardrails.
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
  tags: [safety, alignment, constitutional-ai, red-teaming, rlhf]
---

# Purpose
Guides training-time safety alignment: safety fine-tuning data, Constitutional AI principles, red-teaming methodology, and alignment evaluation.

# When to use this skill
Use when:
- Adding safety training to a base or instruction-tuned model
- Designing red-team evaluation for harmful output categories
- Applying Constitutional AI self-critique and revision loop

Do NOT use when:
- Runtime safety guardrails for deployed models (use safety-guardrails in cat-11)
- General RLHF without safety focus (use preference-optimization)

# Operating procedure
1. Define harm categories: violence, self-harm, CSAM, privacy, misinformation
2. Collect safety training data: refusals + explanations for each category
3. Apply Constitutional AI: generate critique + revision pairs
4. Fine-tune on safety data; verify helpfulness is preserved (alignment tax check)
5. Red-team with adversarial prompts; document failure modes
6. Establish safety eval suite; run before each release

# Output defaults
Harm category taxonomy + safety SFT data format + Constitutional AI prompt templates + red-team report template.

# Failure handling
On over-refusal (helpfulness degradation), add more helpful examples to the safety mix. On safety failure in red-teaming, expand training data for that category before release.
