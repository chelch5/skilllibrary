---
name: retrieval-quality
description: Measures and improves retrieval relevance, coverage, and grounding quality over time. Use when diagnosing or improving a RAG or search system's retrieval accuracy. Do NOT use for initial RAG setup.
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
  tags: [retrieval, quality, recall, precision, evaluation]
---

# Purpose
Provides evaluation and improvement procedures for retrieval systems: measuring recall@k, precision@k, and grounding faithfulness.

# When to use this skill
Use when:
- Diagnosing why a RAG system gives poor answers
- Setting up automated retrieval quality metrics
- Iterating on chunking strategy, embedding model, or reranking

Do NOT use when:
- Initial RAG pipeline setup (use rag-retrieval)
- Generation quality issues unrelated to retrieval

# Operating procedure
1. Build a retrieval eval set: questions with known relevant chunks (ground truth)
2. Measure recall@k: what fraction of relevant chunks appear in top-k
3. Measure precision@k: what fraction of top-k chunks are relevant
4. Measure grounding: does generated answer match retrieved context?
5. Identify failure modes: missing coverage, semantic mismatch, stale index
6. Iterate: adjust chunk size, embedding model, or add BM25 hybrid search

# Output defaults
Eval set schema + recall/precision measurement script + iteration log.

# Failure handling
On low recall, check for missing documents, stale index, or poor chunking. On low precision, add a reranker or tighten similarity threshold.
