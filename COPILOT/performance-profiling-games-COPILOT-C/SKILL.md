---
name: performance-profiling-games
description: Measures frame time, memory, loading, and engine-specific performance regressions in games. Use when diagnosing hitches, memory bloat, or loading bottlenecks.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P1
  maturity: draft
  risk: low
  tags: [profiling, frame-time, memory, optimization]
---

# Purpose
Measures frame time, memory, loading, and engine-specific performance regressions in games.

# When to use this skill
Use when:
- Investigating FPS drops or hitches in gameplay
- Profiling memory usage and object allocation
- Optimizing asset loading and streaming

Do NOT use when:
- Server-side profiling unrelated to game engines
- Abstract algorithmic optimization without a game context

# Operating procedure
1. Run engine profiler (Unity Profiler, Unreal Insights)
2. Identify top CPU/GPU hotspots per frame
3. Profile memory allocations and GC pressure
4. Optimize draw calls, batching, and culling
5. Document baseline and post-fix benchmarks

# Output defaults
Profiling reports, frame time graphs, memory allocation logs, optimization recommendations

# Failure handling
If profiler is unavailable, use frame counters and manual timing. Log results consistently.
