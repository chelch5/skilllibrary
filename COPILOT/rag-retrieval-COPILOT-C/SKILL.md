---
name: rag-retrieval
description: Covers retrieval design, chunking, grounding, citation, and failure modes in retrieval-augmented generation systems. Use when building a RAG pipeline. Do NOT use for pure semantic search without generation.
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
  tags: [rag, retrieval, grounding, citation, chunking]
---

# Purpose
Establishes RAG pipeline architecture from document ingestion through retrieval, context injection, and grounded response generation with citations.

# When to use this skill
Use when:
- Building a question-answering system over a document corpus
- Adding source citation to LLM responses
- Diagnosing hallucination in a generation pipeline

Do NOT use when:
- Pure embedding/index work without generation (use embeddings-indexing)
- Fine-tuning a model on domain knowledge (use fine-tuning in cat-12)

# Operating procedure
1. Ingest documents: chunk at semantic boundaries, embed, store with metadata
2. At query time: embed query, retrieve top-k chunks by similarity
3. Re-rank retrieved chunks with a cross-encoder for precision
4. Inject retrieved context into prompt with clear source citations
5. Instruct model to answer only from provided context; refuse if insufficient
6. Measure retrieval recall and answer faithfulness separately

# Output defaults
Ingestion pipeline + retrieval + reranking + prompt template with citation format.

# Failure handling
On retrieval returning empty results, inform user and do not hallucinate. On context window overflow, truncate lower-ranked chunks, not citations.
