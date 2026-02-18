---
name: tools.git
description: Git internals mastery - bare repos, worktrees, submodules, refs, plumbing.
user-invocable: false
belf:
  text:
    - skill_abstract.xml
    - skill_concrete.xml
---

# Git Expertise Skill

Deep mastery of git internals for infrastructure and platform work.

## Philosophy

**Git is not just version control - it's a content-addressable filesystem with VCS semantics.** This skill goes beyond porcelain commands to understand the plumbing that powers advanced workflows.

## Core Capabilities

| Capability | Description |
|------------|-------------|
| **Bare Repos** | Repositories without working directory - local origins |
| **Worktrees** | Multiple working directories from single repo |
| **Submodules** | Nested repositories with pointer semantics |
| **Refs** | Branches, tags, HEAD - the naming layer |
| **Plumbing** | Low-level commands for scripting |

## Key Patterns

```bash
# Bare clone (local origin pattern)
git clone --bare <url> <path>

# Worktree from bare
git -C <bare-path> worktree add <worktree-path> <ref>

# Submodule init (ONE level, not recursive)
git submodule update --init

# Push through bare to remote
git -C <worktree> push origin <branch>
```

## Principles

1. **Understand the object model** - blobs, trees, commits, refs
2. **Bare repos are first-class** - not just for servers
3. **Worktrees enable parallelism** - multiple checkouts, one history

---

*Forged for M09 R4.0 - MetaverseManager recon*
