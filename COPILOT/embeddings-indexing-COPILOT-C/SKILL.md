---
name: embeddings-indexing
description: Handles embedding model choice, indexing strategy, deduplication, and provenance-aware storage. Use when building a semantic search or RAG index. Do NOT use for keyword-only search.
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
  tags: [embeddings, indexing, vector-db, semantic-search, rag]
---

# Purpose
Establishes embedding pipeline conventions: model selection, chunking, deduplication, metadata storage, and index maintenance.

# When to use this skill
Use when:
- Building or updating a vector index for semantic search or RAG
- Choosing an embedding model (OpenAI, sentence-transformers, BGE, etc.)
- Handling document updates and deduplication in the index

Do NOT use when:
- Keyword/BM25 search only (no embedding model needed)
- Real-time streaming indexing without batching

# Operating procedure
1. Choose embedding model appropriate to domain and latency budget
2. Chunk documents at semantic boundaries (paragraphs, sections)
3. Store chunk + embedding + source metadata (doc_id, position, timestamp)
4. Deduplicate on content hash before embedding
5. Update index incrementally; do not re-embed unchanged chunks
6. Monitor embedding drift when swapping models

# Output defaults
Chunking function + embedding pipeline + metadata schema + upsert logic.

# Failure handling
On embedding API failure, retry with backoff. On model change, re-embed all documents and validate recall before switching production traffic.
