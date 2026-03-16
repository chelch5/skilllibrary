---
name: preference-optimization
description: Applies preference-based optimisation (RLHF, DPO, IPO) to align models with human preferences. Use when moving beyond SFT to preference alignment. Do NOT use for supervised fine-tuning without preference data.
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
  tags: [rlhf, dpo, ipo, alignment, preferences, reward]
---

# Purpose
Guides preference optimisation training: data collection format, method selection (RLHF vs DPO vs IPO), and alignment quality evaluation.

# When to use this skill
Use when:
- Collecting chosen/rejected preference pairs for alignment training
- Choosing between RLHF (reward model + PPO) and DPO/IPO (direct optimisation)
- Evaluating alignment quality post-training

Do NOT use when:
- Instruction tuning without preference data (use instruction-tuning)
- Reward model design in isolation (use reward-modeling)

# Operating procedure
1. Collect preference pairs: (prompt, chosen_response, rejected_response)
2. Verify preference labeling quality with inter-annotator agreement
3. Choose method: DPO for simplicity; RLHF for fine-grained control; IPO for stability
4. For DPO: use beta=0.1–0.3; train for 1–3 epochs on preference data
5. Evaluate with win rate vs reference model on held-out prompts
6. Check for alignment tax: verify general capability is not degraded

# Output defaults
Preference data format spec + DPO/RLHF training config + win rate evaluation script.

# Failure handling
On reward hacking (mode collapse), reduce beta or add KL constraint. On alignment tax exceeding acceptable threshold, reduce training epochs or mix in SFT data.
