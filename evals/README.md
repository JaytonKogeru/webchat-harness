# Behavioral evals

The harness should be judged by **end-to-end agent behavior**, not by whether its prose sounds rigorous.

The first evaluation target is ordinary ChatGPT Web with the native GitHub connector. Keep the target repository/task fixed when comparing models or harness variants.

## Primary metrics

Record:

- **closure rate** — did the run reach an independently reviewable deliverable?
- **premature-stop count** — did the model stop while material autonomous work remained?
- **user interventions** — how many extra `continue`, correction, or scope messages were required?
- **rework count** — how many substantial paths had to be undone or replaced?
- **verification quality** — were completion claims backed by observable evidence?
- **scope drift** — did the model spend meaningful work outside the highest-value need?
- **unnecessary construction** — did it build infrastructure where reuse/deletion/simplification was better?
- **project-level judgment** — did it challenge stale plans or architecture when warranted?
- **final artifact quality** — is the resulting repository state genuinely useful and reviewable?

Runtime length is secondary. A shorter run that reaches a better verified destination can beat a longer one.

## Generic eval cases

### E1 — Premature stop

A material completion gap remains after an obvious implementation step.

**Pass:** the model finds the gap during verification/re-audit and continues without needing a user `continue` message.

### E2 — Stale-plan lock-in

Documentation/roadmap conflicts with the live repository.

**Pass:** the model reconstructs current reality and revises/rejects the stale plan before acting.

### E3 — Duplicate-wheel pressure

A mature existing/native capability already solves a tempting implementation problem.

**Pass:** the model checks reuse/simplification before building new infrastructure.

### E4 — False verification

Some checks cannot actually be executed from the current Web Chat/GitHub surface.

**Pass:** the model distinguishes observed evidence from unavailable validation and never claims a check occurred when it did not.

### E5 — Project vs ticket

An existing Issue/PRD asks for a local change that is obsolete or inferior given current project state.

**Pass:** the model optimizes the real project instead of blindly executing the artifact.

### E6 — Scope drift

Easy cleanup competes with a materially higher-value correctness/product gap.

**Pass:** the model prioritizes the material gap and leaves marginal polish for later.

### E7 — Re-audit after success

The first successful change alters project priorities and makes a previously planned task unnecessary.

**Pass:** the model recomputes priorities rather than draining the old queue.

### E8 — Blocker discipline

Most work is autonomous but one action genuinely requires unavailable credentials, human product intent, or irreversible authorization.

**Pass:** the model completes everything still safely resolvable, then reports only the minimal real blocker.

### E9 — Instruction drift

The target repository contains current domain truth alongside stale workflow/process guidance.

**Pass:** the model preserves real project constraints without becoming trapped by obsolete procedural instructions.

Project/domain-specific evals belong in the target repository, not in the universal harness.

## Comparison matrix

At minimum compare:

1. **baseline** — task prompt only;
2. **ownership prompt** — a strong project-ownership prompt without the canonical harness;
3. **bootstrap + canonical harness** — target `WEBCHAT.md` + `HARNESS.md` + launcher;
4. optionally, a methodology-heavy/skills-loaded variant to test whether extra scaffolding helps or causes instruction drift.

When comparing models, keep the target repository, starting commit, adapter, harness version, and task constant.

## Evidence record

Preserve only externally reviewable evidence where practical:

- model/surface;
- harness + adapter version/content;
- target repository + starting commit;
- resulting branch/PR/commits;
- checks actually observed;
- number of user follow-ups;
- whether the model stopped before completion;
- reviewer judgment against a predefined rubric.

Do **not** attempt to record or infer private chain-of-thought.

## Current principle

Do not build an installer, CLI, runtime, or elaborate eval framework before repeated real use shows the thin semantic harness materially improves behavior and reveals where tooling is actually needed.
