---
name: opencode-team-bootstrap
description: "Builds the initial project-specific operating layer of agents, tools, plugins, commands, and skills. Your repos use an agent operating layer, so this deserves a dedicated builder. Trigger when the task context clearly involves opencode team bootstrap."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [opencode, bootstrap, agents]
---

# Purpose
Generate a complete, project-specific OpenCode agent team — agents, tools, plugins, commands, and skills — tailored to the project's stack, domain, and workflow.

# When to use this skill
Use when:
- A repo has been scaffolded and needs its agent team configured
- An existing repo is being migrated to OpenCode and needs its operating layer set up
- The user says "set up the agents for this project" or "configure the team"
- The generic agent templates need to be replaced with project-aware specialists

Do NOT use when:
- The agent team is already configured and only one agent needs updating
- The project has no canonical brief yet (run spec-pack-normalizer first)

# Operating procedure
1. **Load project context**: brief, stack profile, ticket system, existing skills
2. **Define the agent roster** based on the stack and project size:
   - Always include: `planner`, `implementer`, `reviewer`, `process-doctor`
   - Add stack-specific agents: e.g., `rust-parser`, `react-frontend`, `python-backend`
   - Add domain agents based on the brief: e.g., `auth-specialist`, `data-pipeline`
3. **Write each agent file** at `.opencode/agents/AGENT-NAME.md`:
   - `role`: one-sentence description
   - `scope`: which directories/files this agent may touch
   - `tools`: list of allowed tools
   - `forbidden`: explicit list of what this agent must not do
   - `skills`: list of skills this agent should load
4. **Write command files** at `.opencode/commands/COMMAND.md` for common slash commands:
   - `/plan`, `/implement`, `/review`, `/status`, `/ticket`
5. **Write tool manifests** for any project-specific tools
6. **Cross-reference**: ensure every agent references only tools and skills that exist

# Output defaults
Complete `.opencode/` directory with agent, command, and tool files. Each agent file must have a non-empty `forbidden` list.

# Failure handling
If the stack is ambiguous, generate agents for the most likely stack and add a `<!-- ASSUMPTION: -->` comment in each affected file.
