# AGENTS.md

This repository develops a **thin semantic harness for native ChatGPT Web + native GitHub repository actions**.

## Start here

Read, in order:

1. `README.md` — product boundary and two-stage usage model.
2. `HARNESS.md` — canonical universal operating contract.
3. `BOOTSTRAP.md` — how a target repository gets a concise local `WEBCHAT.md` adapter.
4. `LAUNCH.md` — user-facing launch/resume/review prompts.
5. `research/LANDSCAPE.md` — prior art and explicit non-duplication boundary.
6. `evals/README.md` — generic behavioral evaluation criteria.

## Core constraints

- Keep the universal harness small, auditable, and model-agnostic.
- Do not turn this project into a local MCP server, shell/filesystem runtime, browser driver, unofficial ChatGPT API adapter, or second-agent coordinator.
- Do not add a large generic skill/router framework merely because other agent products have one.
- Frontier-model judgment is a feature. Add instruction only when it addresses a recurring, observable failure mode.
- Target-project identity belongs in that target repository's `WEBCHAT.md` and authoritative files, not in the universal harness.
- Existing nearby projects are prior art to reuse or integrate with, not competitors to reimplement.
- This repository's own assumptions may be wrong. Re-audit the ecosystem before major architectural expansion.

## Product hypothesis

The useful layer is:

```text
canonical semantic harness
        +
small target-repository adapter
        +
frontier Pro model
        +
native GitHub actions
```

The bootstrap model prepares the target adapter; it does not become the long-term controller. The later Pro model owns project-level audit, prioritization, execution, verification, and re-audit.

This hypothesis is falsifiable. If a mature existing project already provides the same layer more cleanly, narrow, integrate, or stop rather than defending novelty.

## Near-term work

Prioritize evidence over packaging:

1. keep `HARNESS.md` and `WEBCHAT.md` semantics minimal and non-overlapping;
2. test bootstrap quality on different repository types;
3. test autonomous ownership runs with the same target adapter across Pro models;
4. measure closure, intervention, drift, unnecessary construction, and verification quality;
5. simplify rules that do not measurably help;
6. only then consider sync/install tooling.

Do not build a Python/Node installer, plugin ecosystem, CLI, or runtime before repeated use shows that manual bootstrap/update is the real friction.
