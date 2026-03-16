---
name: fine-tuning
description: Applies supervised fine-tuning procedures to adapt a pretrained model to specific tasks or styles. Use when adapting an existing base model. Do NOT use for pretraining from scratch.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P0
  maturity: draft
  risk: low
  tags: [fine-tuning, sft, lora, peft, adaptation]
---

# Purpose
Guides supervised fine-tuning of pretrained LLMs with parameter-efficient methods (LoRA/QLoRA) or full fine-tuning where resources allow.

# When to use this skill
Use when:
- Adapting a base model to a domain, task, or style
- Choosing between LoRA, QLoRA, or full fine-tuning based on hardware
- Setting up training data format (instruction-response pairs)

Do NOT use when:
- Training a model from scratch (use pretraining-pipeline)
- Preference-based alignment (use preference-optimization)

# Operating procedure
1. Format training data as instruction-response pairs (ChatML or Alpaca format)
2. Choose method: LoRA (rank 8–64) for GPU-limited, full SFT for high-resource
3. Set learning rate: 1e-4 to 2e-4 for LoRA; 1e-5 to 5e-5 for full SFT
4. Use gradient checkpointing and mixed precision (bf16)
5. Evaluate on held-out task dataset every N steps
6. Merge LoRA adapters and test merged model before deploying

# Output defaults
Training config (YAML) + dataset format spec + evaluation hook + merge script.

# Failure handling
On loss spike, reduce learning rate or add gradient clipping. On catastrophic forgetting, add general instruction data to the training mix. On OOM, switch to QLoRA or reduce batch size.
