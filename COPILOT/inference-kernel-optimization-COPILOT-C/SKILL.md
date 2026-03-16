---
name: inference-kernel-optimization
description: Optimises low-level inference kernels for throughput and latency, including flash attention and custom CUDA ops. Use when profiling and optimising model inference at the kernel level. Do NOT use for high-level serving architecture.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: ai-llm-training-architecture-and-research
  priority: P2
  maturity: draft
  risk: low
  tags: [kernels, cuda, flash-attention, triton, inference-speed]
---

# Purpose
Provides guidance on profiling and optimising inference kernels: flash attention, fused ops, Triton kernels, and memory layout tuning.

# When to use this skill
Use when:
- Profiling a model's inference to identify kernel bottlenecks
- Integrating flash attention or other optimised kernels
- Writing custom Triton kernels for specific ops

Do NOT use when:
- High-level serving config (use inference-serving or vllm-serving)
- Architecture design (use model-architecture)

# Operating procedure
1. Profile with torch.profiler or nsys to identify time-consuming ops
2. Replace standard attention with FlashAttention-2 where applicable
3. Enable torch.compile with inductor backend for automatic kernel fusion
4. Use memory-efficient attention (xformers) if FlashAttention is unavailable
5. Profile memory bandwidth: compute-bound vs memory-bound
6. Benchmark before and after each optimisation with warmup runs

# Output defaults
Profiling report + kernel swap checklist + torch.compile config + benchmark script.

# Failure handling
On kernel compatibility error, fall back to standard PyTorch ops and document the limitation. Never deploy an optimised kernel without numerical correctness verification.
