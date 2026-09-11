# AGENTS.md

This repository develops a **thin semantic/evaluation harness for native ChatGPT Web + native GitHub repository actions**.

## Start here

Read, in order:

1. `README.md` — product boundary and rationale.
2. `HARNESS.md` — canonical universal operating contract.
3. `research/LANDSCAPE.md` — prior art and explicit non-duplication boundary.
4. `evals/README.md` — how claims about harness quality must be tested.
5. `LAUNCH.md` — user-facing bootstrap prompts.

## Core constraints for this repository

- Do not turn this project into a local MCP server, shell/filesystem runtime, browser driver, unofficial ChatGPT API adapter, or second-agent coordinator unless new evidence shows that the product boundary itself should change.
- Do not add a large generic skill/router framework merely because other agent products have one.
- Frontier-model judgment is a feature. Add instruction only when it addresses an observed, testable failure mode.
- Keep the canonical harness short enough to audit as a whole. Prefer deleting or compressing guidance over accumulating overlapping rules.
- Existing nearby projects are prior art, not competitors to reimplement. Reuse/integrate/defer where they already solve a problem better.
- A new feature should be justified by an eval, field failure, or clearly missing native capability.
- This repository's own docs may be wrong. Re-audit the boundary against the live ecosystem before major architectural expansion.

## Current product hypothesis

The useful unoccupied layer is a **native, project-ownership semantic kernel plus eval suite** for strong ChatGPT Web models working directly through the GitHub connector.

The current hypothesis is falsifiable. If a mature existing project is found that already provides the same layer cleanly, narrow this project, integrate with it, or stop rather than defending novelty.

## Near-term work

Highest-value next work is evidence, not packaging:

1. strengthen the landscape audit;
2. create deterministic eval fixtures for the behavioral failure modes in `evals/README.md`;
3. compare baseline vs ownership prompt vs canonical harness on the same tasks;
4. simplify `HARNESS.md` if rules do not measurably help;
5. only then consider installation/sync tooling.

Do not build a Python/Node installer, plugin ecosystem, or CLI before the evals justify it.
