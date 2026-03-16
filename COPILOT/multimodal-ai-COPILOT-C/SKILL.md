---
name: multimodal-ai
description: Handles systems that mix text, image, audio, or document inputs and outputs. Use when building features that process multiple modalities. Do NOT use for text-only LLM integrations.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P2
  maturity: draft
  risk: low
  tags: [multimodal, vision, audio, image, document]
---

# Purpose
Guides integration of multimodal models and pipelines that handle mixed input types (text, image, audio, PDF).

# When to use this skill
Use when:
- Adding image understanding to a chatbot or agent
- Processing PDFs or audio alongside text
- Choosing between native multimodal models vs separate modality pipelines

Do NOT use when:
- Text-only LLM work (use llm-integration)
- Training multimodal models (use model-architecture in cat-12)

# Operating procedure
1. Identify input modalities and desired output modalities
2. Choose model: native multimodal (GPT-4V, Claude 3, Gemini) vs pipeline (OCR + LLM)
3. Pre-process inputs: resize images, extract audio transcripts, parse PDFs
4. Pass modality-specific tokens or content blocks per provider API spec
5. Validate model handles modality combination in testing
6. Set size limits per modality type to control cost and latency

# Output defaults
Modality pre-processing functions + API payload template + size/cost guard.

# Failure handling
On unsupported modality, fall back to text extraction. On image too large, resize before sending. Never pass raw binary data without encoding per API requirements.
