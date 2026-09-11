# webchat-harness

A **thin native harness for ChatGPT Web + GitHub** that helps a strong Web Chat model act as a repository-grounded autonomous engineering/research owner **without adding a local MCP server, browser automation layer, shell daemon, or second coordinator agent**.

The design is deliberately small:

> **Universal behavior lives in one canonical harness. Project identity lives in the target repository. A Pro model owns the outcome.**

## Core idea

ChatGPT Web already has strong reasoning and native GitHub actions. The harness should not teach a frontier model a giant coding methodology. It should only reduce the failure modes that matter for autonomous project work:

- optimizing the wrong thing;
- trusting stale plans over the live repository;
- stopping at analysis, planning, a PR, or partial success;
- mechanically draining an old task queue after priorities changed;
- building unnecessary infrastructure instead of reusing/simplifying;
- claiming verification that did not actually occur;
- failing to re-audit after material changes;
- stopping before a real terminal condition.

## Two-stage use

### 1. Bootstrap the target repository

Use [`BOOTSTRAP.md`](BOOTSTRAP.md) once with a capable reasoning model such as **GPT-5.6 Sol Extra High**.

The bootstrap step does **not** own or advance the whole project. It inspects the target repository and creates a short root-level `WEBCHAT.md` adapter containing only project-local information:

- actual objective;
- meaningful progress signals;
- hard project/domain truths;
- source-of-truth map;
- verification surfaces;
- authority boundaries.

This prevents every expensive Pro run from having to infer project identity from a noisy repository from scratch.

### 2. Run the autonomous owner

Use a Pro-tier model such as **GPT-6 Pro/Astra or GPT-5.6 Sol Pro** with the launcher in [`LAUNCH.md`](LAUNCH.md).

The Pro run loads:

```text
canonical HARNESS.md
        +
target WEBCHAT.md
        +
live target repository/evidence
```

Then it owns the project outcome through:

```text
objective → inspect → audit → choose → act → verify → adversarial review → re-audit
   ↑                                                                        │
   └────────────────────────────────────────────────────────────────────────┘
```

The model chooses the appropriate engineering/research method. Plans, Issues, PRDs, work packets, commits, and PRs are optional intermediate artifacts, not definitions of completion.

## Repository layout

- [`HARNESS.md`](HARNESS.md) — canonical universal operating contract.
- [`BOOTSTRAP.md`](BOOTSTRAP.md) — one-time target-repository integration prompt and `WEBCHAT.md` shape.
- [`LAUNCH.md`](LAUNCH.md) — copy/paste launch/resume/review prompts for Pro ownership runs.
- [`research/LANDSCAPE.md`](research/LANDSCAPE.md) — prior-art audit and non-duplication boundary.
- [`evals/README.md`](evals/README.md) — generic behavioral evaluation criteria.
- [`AGENTS.md`](AGENTS.md) — instructions for agents modifying this harness repository itself.

## What this project is not

`webchat-harness` is intentionally **not**:

- a local coding/runtime environment;
- an MCP filesystem/shell server;
- a browser driver around chatgpt.com;
- a second-agent coordinator;
- a replacement for Codex, Claude Code, OpenHands, SWE-agent, Rel.AI, or WebGPT Orchestrator;
- a large role/skill router;
- a mandatory PRD/TDD workflow;
- an attempt to encode generic senior-engineer knowledge the frontier model already has.

If an existing mature project already solves a capability better, use it rather than rebuilding it here.

## Design rule: thin harness, strong model

The universal contract should stay small enough to audit as a whole. Project-specific truths belong in the target repository's `WEBCHAT.md` and existing authoritative files. Generic procedural instruction should be added only when field evidence shows a recurring failure that the model does not reliably correct itself.

## Prior-art boundary

ChatGPT Web harnessing is not a new category. The closest systems found so far are documented in [`research/LANDSCAPE.md`](research/LANDSCAPE.md), including WebGPT Orchestrator, durable ChatGPT Web workflow skills, and local MCP/runtime harnesses.

The narrower product hypothesis here is:

> **native standard ChatGPT Web + native GitHub connector + no required local runtime/browser driver/second agent + a thin project-ownership semantic contract + a small target-repository adapter for frontier models.**

That boundary should remain sharp. If this repository starts growing a local runtime, browser automation stack, workflow engine, or generic skill marketplace, it is probably duplicating a stronger existing wheel.

## Status

**v0.2 design scaffold.** Current priority is validating the two-stage bootstrap/ownership pattern on real repositories before building any installer, CLI, package, or plugin ecosystem.
