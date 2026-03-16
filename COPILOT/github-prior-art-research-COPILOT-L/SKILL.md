---
name: github-prior-art-research
description: Searches GitHub for similar repos, patterns, and existing implementations and returns grounded findings. Use when evaluating whether to build vs adopt, or when needing real examples before designing an approach. Do NOT use for general web research — scope is GitHub repositories.
source: github.com/gpttalker/agent-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P2
  maturity: draft
  risk: low
  tags: [github, research, prior-art, discovery]
---

# Purpose
Finds prior art, reference implementations, and comparable projects on GitHub to inform design and build-vs-adopt decisions.

# When to use this skill
Use when:
- Evaluating whether an existing library or pattern already solves the problem
- Needing real implementation examples before designing an approach
- Checking how common projects solve a specific technical problem

Do NOT use when:
- General research is needed beyond GitHub (use `research-delegation`)
- The answer is already known from project context

# Operating procedure
1. Identify the core concept or problem to search
2. Formulate 2-3 targeted GitHub search queries (language, topic, filename filters)
3. Evaluate top 5-10 results: stars, activity, licence, implementation approach
4. Summarise findings: what exists, what's worth adopting, what gaps remain
5. Return grounded findings with repo links and brief assessments

# Output defaults
Bulleted summary of findings with GitHub URLs, star counts, licence, and a one-line assessment per repo.

# Failure handling
If search returns too many irrelevant results, narrow with language or topic filters. If nothing relevant is found, state that explicitly.
