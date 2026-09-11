# AGENTS.md

This repository develops a **thin, model-agnostic Agent Skill for autonomous repository ownership in ChatGPT Web + GitHub**.

## Start here

1. `SKILL.md` — canonical runtime contract and the only user-facing execution interface.
2. `README.md` — product boundary and installation/use guidance.
3. `research/LANDSCAPE.md` — prior art and non-duplication boundary.
4. `evals/README.md` — generic behavioral evaluation criteria.

## Core constraints

- Keep `SKILL.md` small enough to audit as a whole.
- Do not duplicate runtime instructions across multiple canonical files.
- Add instruction only for recurring, observable failures that materially affect outcomes.
- Target-project identity/context belongs in the target repository's `WEBCHAT.md` and authoritative files.
- Do not turn this project into a local MCP server, browser driver, shell/filesystem runtime, second-agent coordinator, workflow engine, or generic skill marketplace.
- Reuse mature adjacent projects instead of rebuilding their capabilities.
- Model/product/version names are not part of the protocol.
- Runtime budgets are user-supplied turn parameters, not hard-coded assumptions about model limits.
- This repository's assumptions are falsifiable; if a mature existing project covers the same layer better, narrow, integrate, or stop.

## Product hypothesis

```text
installed/attached webchat-harness skill
        +
target WEBCHAT.md
        +
live target repository/evidence
        +
audit / autonomous owner model
        +
native GitHub actions
```

Bootstrap prepares `WEBCHAT.md`; audit reconstructs the execution-ready current state; ownership handles project-level prioritization, execution, verification, re-audit, and stopping.

## Near-term work

Prioritize real field trials over packaging machinery. Compare baseline vs skill-enabled runs, measure closure/intervention/drift/verification quality, and simplify `SKILL.md` whenever a rule is not clearly helping.
