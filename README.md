# webchat-harness

A **thin Agent Skill for autonomous repository ownership in ChatGPT Web + GitHub**.

The repository is the canonical development source. The installed/attached [`SKILL.md`](SKILL.md) is the runtime interface. Users should not need to ask a model to open several files in this repository on every run.

## Use

Once the skill is installed or attached to the ChatGPT Project, the normal commands are intentionally tiny:

```text
用 webchat-harness bootstrap <owner/repo>。
```

```text
用 webchat-harness 接管 <owner/repo>，直接开始。
```

Bootstrap creates or refreshes the target repository's short `WEBCHAT.md` adapter. Ownership mode then uses that adapter plus the live repository/evidence to work autonomously toward the real project outcome.

## Install / attach

`webchat-harness` follows the open Agent Skills format: `SKILL.md` is the single runtime entrypoint.

Where ChatGPT Skills are available, install/upload this as a Skill once and invoke it by name. Where Skills are not available on the current account/surface, add `SKILL.md` once to the relevant ChatGPT Project sources (or copy its contents into the Project instructions) rather than repeatedly fetching this GitHub repository during every task.

Model choice is outside the protocol.

## Runtime design

The skill keeps only a small control kernel:

- own the real project outcome;
- use `WEBCHAT.md` for project identity/context and live authoritative evidence for current reality;
- choose the highest-value unresolved gap and act autonomously;
- prefer reuse/simplification over unnecessary construction;
- verify material work and reassess from the new state;
- stop only at diminishing returns, a genuine external blocker, or an unauthorized irreversible action;
- never invent access, evidence, verification, execution, or authority.

Project-specific truth belongs in each target repository's `WEBCHAT.md` and authoritative project files, not in this universal skill.

## Repository layout

- [`SKILL.md`](SKILL.md) — canonical runtime skill: bootstrap + ownership modes.
- [`research/LANDSCAPE.md`](research/LANDSCAPE.md) — prior-art audit and non-duplication boundary.
- [`evals/README.md`](evals/README.md) — generic behavioral evaluation criteria.
- [`AGENTS.md`](AGENTS.md) — instructions for agents modifying this repository itself.

## Boundary

This project is intentionally not a local coding runtime, MCP filesystem/shell server, browser driver, second-agent coordinator, large role/skill router, or mandatory PRD/TDD framework. Existing mature tools should be reused rather than rebuilt.

**Status: v0.3 draft — skill-first packaging for real project trials.**
