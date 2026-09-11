# Bootstrap a target repository

A full autonomous run should not have to reconstruct the target project's identity from scratch every time.

The recommended setup is a **one-time lightweight bootstrap** using any model capable of accurately reconstructing project-local truth, followed by autonomous ownership runs using whichever model the user chooses.

The bootstrap model is **not** the project controller. Its job is only to compile project-local truth into a short adapter file that later ownership runs can load immediately.

Model choice is deliberately outside this protocol. The bootstrap role is defined by the task it performs, not by a specific model name, reasoning tier, subscription tier, or product label.

## Result

Create or refresh a root-level file in the target repository:

```text
WEBCHAT.md
```

Keep it short. It should contain only project-specific information that a fresh autonomous model needs in order to optimize the correct thing.

Recommended shape:

```markdown
# WebChat Project Adapter

Harness: JaytonKogeru/webchat-harness

## Objective
What is the actual product/outcome this repository exists to produce?

## Meaningful progress
What observable changes materially advance that objective?

## Project truths
Only hard domain/product constraints that must not be guessed or violated.

## Source-of-truth map
Where should an agent look for the live state, data, architecture, evidence, tests, or other authoritative project information?

## Verification surfaces
What evidence can actually demonstrate correctness or progress in this repository?

## Authority boundaries
Only project-specific destructive/irreversible actions or human decisions that remain outside normal autonomous authority.
```

Do **not** copy `HARNESS.md` into `WEBCHAT.md`. The universal behavior remains canonical in this repository; `WEBCHAT.md` is only the target-specific adapter.

Do not turn `WEBCHAT.md` into a roadmap, issue list, coding style guide, methodology manual, or duplicate of existing documentation. Prefer links/paths to authoritative project files over restating them.

## Bootstrap prompt

Replace `<owner/repo>` and use this in standard Web Chat with GitHub connected.

```text
Prepare <owner/repo> for autonomous use with JaytonKogeru/webchat-harness.

Read the current canonical HARNESS.md from JaytonKogeru/webchat-harness, then inspect the target repository deeply enough to understand its actual purpose, meaningful progress signals, hard project/domain truths, authoritative state, and real verification surfaces.

Do not execute the project's backlog or redesign the project in this run. Your task is only to create or refresh a concise root-level WEBCHAT.md project adapter for future autonomous ownership runs.

WEBCHAT.md must contain: Objective, Meaningful progress, Project truths, Source-of-truth map, Verification surfaces, and Authority boundaries. Keep it concise and project-specific. Do not copy the universal harness, generic coding advice, stale task queues, or large existing documents into it. Link to authoritative repository files instead.

If the repository's actual objective is genuinely ambiguous or internally contradictory, do not invent one. Record the ambiguity clearly in WEBCHAT.md and report that this bootstrap cannot safely resolve project intent without human input.

Do not make unrelated project changes. Commit the adapter change and return the branch/PR or commit for review.
```

## Refreshing the adapter

Refresh `WEBCHAT.md` only when the project's objective, source-of-truth structure, verification surface, or hard local constraints materially change. Routine implementation work should not churn this file.
