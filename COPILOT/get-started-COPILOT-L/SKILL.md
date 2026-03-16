---
name: get-started
description: Provides a deterministic micro-skill for onboarding or initial validation of a local skill or agent environment. Trigger when a new user or system needs to verify the environment is set up correctly. Do NOT use for complex project initialization.
source: github.com/sst/opencode
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: draft
  risk: low
  tags: [onboarding, validation, environment]
---

# Purpose
Provides a minimal, deterministic onboarding skill that validates the local skill environment and confirms the agent is operational.

# When to use this skill
Use when:
- A new user or machine needs to verify that the skill library and agent environment are correctly configured
- Running a quick sanity check after setup or a configuration change

Do NOT use when:
- Initializing a complex multi-service project (use a project-specific bootstrap skill)
- Debugging specific skill or tool failures

# Operating procedure
1. Check that required CLI tools and runtime dependencies are installed
2. Verify the agent configuration file is present and valid
3. Run a simple end-to-end test (e.g., list available skills)
4. Report a pass/fail result with clear guidance on how to fix any failures

# Output defaults
A brief environment validation report: pass/fail for each check with remediation steps for failures.

# Failure handling
If any check fails, report exactly what is missing and link to the relevant setup documentation. Do not proceed with other tasks until the environment is valid.
