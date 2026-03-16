---
name: safety-guardrails
description: Defines refusal, escalation, permission, and safe-default controls around model or agent behaviour. Use when adding safety constraints to an AI system. Do NOT use for security hardening of infrastructure.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-runtime-and-integration
  priority: P1
  maturity: draft
  risk: low
  tags: [safety, guardrails, refusal, alignment, moderation]
---

# Purpose
Establishes input/output safety controls: content classifiers, refusal conditions, escalation paths, and safe defaults for deployed AI systems.

# When to use this skill
Use when:
- Adding input/output moderation to a chatbot or agent
- Defining refusal conditions for harmful, illegal, or off-topic requests
- Setting permission tiers for different user classes

Do NOT use when:
- Infrastructure security hardening (use security-reviewer agent)
- Model alignment training (use safety-alignment in cat-12)

# Operating procedure
1. Define categories of unsafe input: harmful, illegal, off-topic, PII
2. Add input classifier before model call (OpenAI Moderation API or custom)
3. Define refusal response templates for each category
4. Add output filter for PII leakage and toxicity
5. Set escalation path: flag for human review above confidence threshold
6. Test with adversarial inputs; document known bypass risks

# Output defaults
Classifier integration + refusal templates + output filter + test cases.

# Failure handling
On classifier failure, default to safe refusal rather than allowing potentially unsafe output. Log all triggered guardrails with input hash for review.
