---
name: webchat-harness
description: Use for autonomous repository ownership in ChatGPT Web with GitHub. Bootstrap a target repository into a concise WEBCHAT.md adapter, or take ownership of an already-bootstrapped repository and keep working until the real project objective is materially complete or genuinely blocked.
metadata:
  version: "0.3.0-draft"
  type: process
---

# WebChat Harness

Use this skill when the user asks to bootstrap a repository for WebChat Harness or to autonomously own and advance a repository.

## Core contract

- The project outcome is the unit of work.
- Use `WEBCHAT.md` to understand the target objective and context map; use the live repository and its declared authoritative sources for current reality.
- Work autonomously on the highest-value unresolved gap. Prefer reuse, simplification, replacement, or deletion over unnecessary construction.
- Verify material work with evidence actually available, then reassess the project from its new state.
- Stop only when another serious pass is unlikely to yield material improvement, a genuine external blocker remains, or an unauthorized destructive/irreversible action is required.
- Never claim execution, verification, evidence, access, or authority that was not actually available.

## Mode: bootstrap

When asked to bootstrap `<owner/repo>`:

1. Inspect the target repository, materially related GitHub repositories, and relevant ChatGPT Project conversations/files that are actually available.
2. Create or refresh `<owner/repo>/WEBCHAT.md` as a short project adapter containing:
   - Objective
   - Meaningful progress
   - Project truths
   - Context sources
   - Source-of-truth map
   - Verification surfaces
   - Authority boundaries
3. Keep `WEBCHAT.md` concise. Record sources by role; do not copy conversations, roadmaps, or this skill into it.
4. Do not advance the project backlog during bootstrap. Commit only the adapter change needed for future ownership runs.

Related repositories and project conversations recover intent, history, dependencies, and adjacent work. They do not override live target-repository evidence for current-state claims unless the target repository explicitly declares another authoritative source.

## Mode: own

When asked to own `<owner/repo>`:

1. Read `<owner/repo>/WEBCHAT.md`. If it does not exist, bootstrap first.
2. Reconstruct current reality from the live repository, its authoritative sources, and only the relevant context mapped in `WEBCHAT.md`.
3. Repeatedly choose the highest-value resolvable gap, act, verify, challenge the result, and reassess from the new state.
4. Treat plans, issues, PRDs, commits, pull requests, passing checks, and milestones as intermediate artifacts rather than automatic completion.
5. Continue until the core contract's stopping condition is genuinely met.

## Invocation

The user should not need to restate this workflow. Short requests such as these are sufficient when the skill is installed or attached:

- `用 webchat-harness bootstrap <owner/repo>。`
- `用 webchat-harness 接管 <owner/repo>，直接开始。`
