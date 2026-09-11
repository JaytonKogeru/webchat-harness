# webchat-harness

A **thin, native harness for ChatGPT Web + GitHub** that turns a strong Web Chat model into a repository-grounded autonomous engineering/research agent **without adding a local MCP server, browser automation layer, shell daemon, or second coordinator agent**.

The core idea is deliberately small:

> **The project is the unit of work. The live repository is the source of truth. The model owns the outcome. The harness defines only the operating invariants that help a frontier model keep auditing, acting, verifying, and re-auditing until the project is genuinely deliverable.**

## Why this exists

ChatGPT Web can already read and modify GitHub repositories, create branches and pull requests, inspect diffs and repository state, and reason for a long time in one turn. The missing piece is not another coding runtime. It is a compact, reusable **semantic control layer** that helps the model:

- take project-level ownership rather than behave like a ticket worker;
- audit the real repository before trusting existing plans or architecture;
- bias toward action instead of stopping at analysis or a proposal;
- re-evaluate priorities after material changes instead of mechanically draining a stale plan;
- reuse, simplify, consolidate, replace, or delete before inventing new infrastructure;
- distinguish implementation from verified completion;
- avoid claiming tests, provenance, evidence, or review that did not actually occur;
- stop only at a real terminal condition rather than at a plan, commit, PR, or partial success.

This is designed for strong Web Chat models such as GPT-6 Pro/Astra, but the protocol is intentionally model-agnostic.

## What this project is *not*

`webchat-harness` is intentionally **not**:

- a local coding agent runtime;
- an MCP filesystem/shell server;
- a browser-automation wrapper around chatgpt.com;
- a replacement for Codex, Claude Code, OpenHands, SWE-agent, or similar execution environments;
- a large library of role-play skills;
- a mandatory PRD/TDD/issue workflow;
- an attempt to teach a frontier model generic software-engineering knowledge it already has.

If the native ChatGPT Web + GitHub surface can already do something well, this project should not reimplement it.

## The native loop

```text
load canonical harness
        ↓
inspect the target repository and external evidence
        ↓
first-principles project audit
        ↓
identify the highest-value resolvable gap
        ↓
decide whether to act, simplify, reuse, replace, or delete
        ↓
implement / research / repair
        ↓
verify with evidence available through the live environment
        ↓
adversarially review the result
        ↓
re-audit the project from its new state
        ↓
material gap remains? ── yes ──↺
        │
        no
        ↓
diminishing returns or genuine external blocker
        ↓
stop
```

The loop is **audit-driven**, not plan-driven. Plans, issues, PRDs, work packets, milestones, commits, and PRs are optional intermediate artifacts. They never become the definition of completion by themselves.

## Repository layout

- [`HARNESS.md`](HARNESS.md) — canonical operating contract; intentionally short.
- [`LAUNCH.md`](LAUNCH.md) — copy/paste launchers for starting a native Web Chat ownership run.
- [`research/LANDSCAPE.md`](research/LANDSCAPE.md) — prior-art audit and project boundary.
- [`evals/README.md`](evals/README.md) — behavioral evaluation plan for premature stopping, scope drift, false verification, stale-plan lock-in, and related failure modes.
- [`AGENTS.md`](AGENTS.md) — map for agents working *on this harness repository itself*.

## Design rule: thin harness, strong model

The harness should constrain only failure modes that remain important at frontier-model capability levels. It should not prescribe a long sequence of generic coding rituals.

Project-specific scientific, product, architectural, safety, or operational truths belong in the **target repository**, not in the universal harness. The canonical harness stays the same across projects.

## Using it with a target repository

The preferred mode is **central canonical contract + explicit launch**. A target repository does not need to vendor a copy of `HARNESS.md`.

Start a new standard Web Chat with the GitHub connection available and use the launcher in [`LAUNCH.md`](LAUNCH.md), replacing `<owner/repo>` with the target repository. The launcher tells the model to load the latest canonical `HARNESS.md`, then read the target repository's own instructions and live state.

A target repo may optionally add a small pointer in `AGENTS.md`, but project-specific instructions must not fork or duplicate the universal contract unless there is a deliberate, documented override.

## Prior-art verdict

This project is **not being built from a blank landscape**. Several strong projects already make ChatGPT Web more agentic, including local MCP runtimes, browser-driven orchestration, durable workflow skills, and file-backed harnesses.

The closest systems found so far are documented in [`research/LANDSCAPE.md`](research/LANDSCAPE.md). None found in the current audit targets exactly this combination:

1. ordinary/native ChatGPT Web as the reasoning surface;
2. the native GitHub connector as the repository action layer;
3. no required local runtime, MCP server, browser driver, API adapter, or second agent;
4. project-level ownership and first-principles re-audit rather than a fixed ticket/PR workflow;
5. a deliberately small semantic kernel plus behavioral evals for frontier models.

That narrow boundary is the reason this repository is worth building. If a mature project is later found that fully covers it, this project should integrate, narrow, or stop rather than duplicate it.

## Status

**v0.1 design scaffold.** The first goal is to validate the semantic contract and evaluation method before building any installer, CLI, package, router, or skill ecosystem.
