---
name: local-git-specialist
description: "Applies safe local git hygiene for status inspection, diff review, and non-destructive history usage. You frequently work CLI-first and want careful, practical git guidance. Trigger when the task context clearly involves local git specialist."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [git, version-control, hygiene]
---

# Purpose
Perform safe, precise local git operations — inspecting history, staging selective changes, amending commits, managing worktrees — without destroying work or corrupting history.

# When to use this skill
Use when:
- Staging only specific hunks of a large diff
- Amending or squashing commits before push
- Inspecting blame, log, or history to understand when a change was introduced
- Setting up a git worktree for isolated parallel work
- Recovering from a bad merge or rebase

Do NOT use when:
- The operation involves a remote (push, pull, fetch) — verify remote state separately
- Force-pushing to a shared branch — this skill prohibits that

# Operating procedure
**Safe inspection (always allowed)**:
```bash
git log --oneline --graph --decorate -20   # recent history
git diff HEAD                              # unstaged changes
git diff --staged                          # staged changes
git show <sha> --stat                      # what a commit changed
git blame -L 10,20 src/file.ts            # who changed a range
```

**Selective staging**:
```bash
git add -p                                 # interactive hunk staging
git add src/specific-file.ts              # file-level staging
git restore --staged src/file.ts          # unstage without losing changes
```

**Safe commit operations**:
```bash
git commit --amend --no-edit              # add staged to last commit
git commit --fixup <sha>                  # create fixup commit
git rebase -i HEAD~3                      # interactive rebase last 3
```

**Worktrees for isolation**:
```bash
git worktree add ../feature-branch feature/my-branch
git worktree list
git worktree remove ../feature-branch
```

**Hard rules**:
- Never `git push --force` to `main` or `master`
- Never `git reset --hard` without first confirming the target SHA
- Always `git stash` before switching branches with uncommitted work
- Never delete a branch without confirming it is merged

# Output defaults
Git commands with brief explanation of what each does. Show `git status` after any mutation operation.

# Failure handling
If a rebase or merge produces conflicts, stop and show the conflict files. Do not auto-resolve conflicts — surface them for human decision.
