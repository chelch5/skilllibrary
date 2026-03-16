---
name: performance-baseline
description: "Defines what to measure, what tools to use, and what thresholds or regressions matter for the stack. Without a baseline, optimization work becomes vibe-based. Trigger when the task context clearly involves performance baseline."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P2
  maturity: draft
  risk: low
  tags: [performance, benchmarking, metrics]
---

# Purpose
Establish measurable performance baselines BEFORE making changes. Without a baseline recording p50/p95/p99 latency, throughput, and memory usage, you cannot prove an optimization actually improved anything—you're just vibes-coding.

# When to use this skill
Use when:
- Starting performance optimization work ("make it faster")
- Before/after comparison is needed to prove improvement
- Setting up CI performance regression detection
- Defining SLOs or performance budgets for a service

Do NOT use when:
- Task is pure functional correctness (use testing skill)
- Performance is not a concern for the workload
- You need profiling to find bottlenecks (use performance-profiling skill first)

# Operating procedure
1. **Define metrics to capture**: Choose from latency percentiles (p50/p95/p99), throughput (req/s, ops/s), memory (peak, average), CPU utilization, and cold start time where applicable.

2. **Select measurement tooling by stack**:
   - Python: `pytest-benchmark` with `benchmark.pedantic()` for microbenchmarks; `locust` or `k6` for load testing
   - Node.js: `autocannon` for HTTP benchmarks; `benchmark.js` for micro
   - Go: built-in `testing.B` benchmarks with `-benchmem`
   - Rust: `criterion` crate for statistical rigor
   - HTTP APIs: `wrk`, `hey`, or `k6` with defined request patterns

3. **Run baseline measurement**:
   ```bash
   # pytest-benchmark example
   pytest tests/bench/ --benchmark-only --benchmark-autosave --benchmark-json=baseline.json
   
   # Go example
   go test -bench=. -benchmem -count=5 | tee baseline.txt
   ```

4. **Record baseline artifact**: Store JSON or text output in `benchmarks/baseline/` with timestamp and git SHA. Include machine specs (CPU, memory, OS) in metadata.

5. **Define regression threshold**: Typically 5-10% degradation triggers investigation; 20%+ is a blocker. Document in `PERFORMANCE.md`.

6. **Set up CI comparison**: Configure pytest-benchmark `--benchmark-compare` or equivalent to fail on regression exceeding threshold.

# Output defaults
```markdown
## Performance Baseline - [date] - [git SHA]

### Environment
- CPU: [model], [cores]
- Memory: [amount]
- OS: [version]

### Metrics
| Operation | p50 | p95 | p99 | Throughput |
|-----------|-----|-----|-----|------------|
| [name]    | Xms | Yms | Zms | N ops/s    |

### Regression Threshold
- Warning: >5% degradation
- Blocker: >20% degradation
```

# References
- https://pytest-benchmark.readthedocs.io/en/latest/
- https://pkg.go.dev/testing#hdr-Benchmarks

# Failure handling
- **Missing baseline data**: Run `--benchmark-autosave` to create one; do not compare against nothing
- **High variance between runs**: Increase iteration count (`--benchmark-min-rounds=100`), disable CPU scaling, close background processes
- **CI flakiness**: Use statistical comparison (pytest-benchmark does this automatically) rather than single-run comparison
- **No clear metric to track**: Default to p95 latency for user-facing; throughput for batch processing
