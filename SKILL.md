---
name: webchat-harness
description: Use for autonomous repository ownership in ChatGPT Web with GitHub. Bootstrap a target repository into a concise WEBCHAT.md adapter, audit its live state before execution, or take ownership and keep working toward the real project objective.
metadata:
  version: "0.4.0-draft"
  type: process
---

# WebChat Harness

Use this skill when the user asks to bootstrap, audit, or autonomously own and advance a repository.

## Core contract

- The project outcome is the unit of work.
- Use `WEBCHAT.md` to understand the target objective and context map; use the live repository and its declared authoritative sources for current reality.
- Work autonomously on the highest-value unresolved gap. Prefer reuse, simplification, replacement, or deletion over unnecessary construction.
- Verify material work with evidence actually available, then reassess the project from its new state.
- Stop project ownership only when another serious pass is unlikely to yield material improvement, a genuine external blocker remains, or an unauthorized destructive/irreversible action is required.
- Treat turn completion and project completion separately: a turn budget may require checkpoint/handoff without making the project complete.
- Never claim execution, verification, evidence, access, or authority that was not actually available.

## Long-run preflight

For any audit or ownership run likely to involve sustained reasoning or tool use:

1. Establish a user-provided operational budget for the current WebChat turn.
2. If the user did not provide a budget, ask once for the duration before starting substantive long-run work. Do not infer one from model/product names or rumored platform limits.
3. Treat the budget as a runtime parameter for this turn, not a project deadline or a fixed property of the model.
4. Checkpoint independently verified closures when appropriate. As closeout approaches, stop opening new large scope, finish the current coherent batch, verify it, persist durable progress, and reserve enough time for handoff.
5. Keep the handoff minimal: current state, verification observed, branch/commit, uncommitted work, and the next highest-value gap.
6. Do not wait for the platform to terminate the turn.

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

## Mode: audit

When asked to audit `<owner/repo>` before execution:

1. Apply the long-run preflight when the audit is expected to be long.
2. Read `<owner/repo>/WEBCHAT.md`. If it does not exist, bootstrap first.
3. Reconstruct current reality from the live repository, its authoritative sources, and only the relevant context mapped in `WEBCHAT.md`.
4. Identify the highest-value execution batch, the evidence needed to verify it, and any genuine decision or blocker that cannot be resolved autonomously.
5. Do not advance the implementation backlog during audit unless the user explicitly asks. End with a compact execution brief suitable for handoff to a stronger model.
6. A later execution run must refresh critical live state before acting rather than blindly trusting the earlier audit.

## Mode: own

When asked to own `<owner/repo>`:

1. Apply the long-run preflight when the ownership run is expected to be long.
2. Read `<owner/repo>/WEBCHAT.md`. If it does not exist, bootstrap first.
3. Reconstruct current reality from the live repository and authoritative sources. Use any prior audit as context, not as a substitute for checking current state.
4. Repeatedly choose the highest-value resolvable gap, act, verify, challenge the result, and reassess from the new state.
5. Treat plans, issues, PRDs, commits, pull requests, passing checks, and milestones as intermediate artifacts rather than automatic completion.
6. Continue until the core contract's project-level stopping condition is genuinely met. If the current turn budget requires closeout first, leave durable state for the next ownership turn and state that the project remains incomplete.

## Invocation

The user should not need to restate this workflow. Short requests such as these are sufficient when the skill is installed or attached:

- `用 webchat-harness bootstrap <owner/repo>。`
- `用 webchat-harness 审计 <owner/repo>。本轮 55 分钟。`
- `用 webchat-harness 接管 <owner/repo>，直接执行。本轮 90 分钟。`

If a long audit or ownership request omits the operational budget, ask for it before starting.
