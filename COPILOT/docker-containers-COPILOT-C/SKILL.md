---
name: docker-containers
description: Handles container build, layering, runtime config, and local-to-prod consistency for containerized applications. Ensures Dockerfiles are efficient and images are minimal.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P1
  maturity: draft
  risk: low
  tags: [docker, containers, dockerfile, devops]
---

# Purpose
Handles container build, layering, runtime config, and local-to-prod consistency for containerized applications.

# When to use this skill
Use when:
- Containerizing an application with Docker
- Optimizing Dockerfile layer caching
- Running multi-service stacks with Docker Compose

Do NOT use when:
- Native VM deployments without containerization
- Kubernetes orchestration specifics (use terraform-iac instead)

# Operating procedure
1. Write multi-stage Dockerfile with minimal final image
2. Order layers for cache efficiency (deps before code)
3. Configure healthchecks and resource limits
4. Validate with docker build and docker run locally
5. Document environment variables and volume mounts

# Output defaults
Dockerfiles, docker-compose.yml, .dockerignore, container run instructions

# Failure handling
If build fails, isolate failing layer. Never use :latest tags in production.
