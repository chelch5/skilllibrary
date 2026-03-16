---
name: training-infrastructure
description: Provisions and configures GPU cluster infrastructure for LLM training runs including storage, networking, and job scheduling. Use when setting up training infrastructure. Do NOT use for inference serving infrastructure.
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
  tags: [infrastructure, gpu, slurm, nccl, storage, training]
---

# Purpose
Establishes GPU cluster setup for LLM training: node configuration, high-speed interconnect, distributed storage, and job scheduler integration.

# When to use this skill
Use when:
- Provisioning a GPU cluster for a new training run
- Configuring NCCL for inter-node communication
- Setting up shared storage (NFS, Lustre, or S3-compatible) for training data and checkpoints

Do NOT use when:
- Serving infrastructure (use serving-architecture or vllm-serving)
- Single-node local training setup (use fine-tuning or pretraining-pipeline)

# Operating procedure
1. Provision nodes with homogeneous GPU type and driver version
2. Configure InfiniBand or high-bandwidth Ethernet for NCCL
3. Set NCCL_IB_DISABLE=0, NCCL_DEBUG=INFO for initial run verification
4. Mount shared storage at consistent path across all nodes
5. Configure SLURM or Kubernetes for job submission with GPU resource requests
6. Run NCCL bandwidth test (nccl-tests) before starting training

# Output defaults
Cluster setup checklist + NCCL env config + SLURM job template + storage mount verification.

# Failure handling
On NCCL timeout, check network interface binding and IB switch status. On storage latency spike, switch to node-local SSD for hot checkpoint data and async upload to shared storage.
