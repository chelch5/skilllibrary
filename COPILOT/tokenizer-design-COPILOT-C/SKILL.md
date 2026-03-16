---
name: tokenizer-design
description: Designs or evaluates tokenizers including vocabulary size, training data, and fertility analysis. Use when creating or adapting a tokenizer. Do NOT use for inference-time tokenization issues.
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
  tags: [tokenizer, vocabulary, bpe, sentencepiece, fertility]
---

# Purpose
Guides tokenizer design decisions: algorithm choice (BPE, Unigram, WordPiece), vocabulary size, training data composition, and fertility analysis.

# When to use this skill
Use when:
- Training a new tokenizer from scratch for a new model
- Adapting an existing tokenizer to a new language or domain
- Analysing tokenizer fertility and coverage for a target corpus

Do NOT use when:
- Using an existing tokenizer without modification
- Inference-time tokenization debugging

# Operating procedure
1. Choose algorithm: BPE (GPT-style), Unigram (T5-style), or SentencePiece with BPE
2. Select vocabulary size: 32K–100K for general use; larger for multilingual
3. Train on a representative sample of the target corpus (1–10GB)
4. Measure fertility: tokens/word for key languages and domains
5. Verify special tokens are correctly defined (BOS, EOS, PAD, UNK)
6. Validate encoding/decoding round-trip on test samples

# Output defaults
Tokenizer training config + fertility analysis table + special token definitions + validation script.

# Failure handling
On high fertility for a target language (>3 tokens/word), increase vocab size or add language-specific data to tokenizer training. On encoding error, check for unseen characters and add to pre-tokenisation handling.
