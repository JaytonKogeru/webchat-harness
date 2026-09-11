# Bootstrap a target repository

A full autonomous run should not have to reconstruct the target project's identity and background from scratch every time.

The recommended setup is a **one-time lightweight bootstrap** using any model capable of accurately reconstructing project-local truth, followed by autonomous ownership runs using whichever model the user chooses.

The bootstrap model is **not** the project controller. Its job is only to compile project-local truth and the relevant context map into a short adapter file that later ownership runs can load immediately.

Model choice is deliberately outside this protocol. The bootstrap role is defined by the task it performs, not by a specific model name, reasoning tier, subscription tier, or product label.

## Result

Create or refresh a root-level file in the target repository:

```text
WEBCHAT.md
```

Keep it short. It should contain only project-specific information that a fresh autonomous model needs in order to optimize the correct thing and find the right background quickly.

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

## Context sources
List only sources that materially help reconstruct intent, history, dependencies, or adjacent work.

- Working repository: <owner/repo> — current project implementation/state.
- Related GitHub repositories: <repo + why it matters>.
- ChatGPT Project context: <relevant project conversations/files actually available to this chat + what they contribute>.
- External sources: <only when they are part of the project's normal context>.

## Source-of-truth map
Where should an agent look for authoritative current state, data, architecture, evidence, tests, decisions, or other project truth?

## Verification surfaces
What evidence can actually demonstrate correctness or progress in this repository?

## Authority boundaries
Only project-specific destructive/irreversible actions or human decisions that remain outside normal autonomous authority.
```

### Source roles

Use related repositories and available ChatGPT Project context to recover **intent, history, dependencies, prior decisions, and adjacent work**. They are context, not automatic proof of the target repository's current state.

The live working repository and the authoritative sources named in its `Source-of-truth map` control current-state claims. If a conversation, old repository, or stale document conflicts with current repository evidence, preserve the useful history but do not let it override live reality without explicit evidence.

Do not claim access to ChatGPT Project conversations/files that are not actually available in the current chat. If important background appears to exist but cannot be accessed, record that limitation rather than reconstructing it from guesswork.

Do not search every accessible repository indiscriminately. Inspect related repositories only when the target repository, available project context, repository metadata, or explicit user intent gives a reasonable basis for the relationship.

Do **not** copy `HARNESS.md` into `WEBCHAT.md`. The universal behavior remains canonical in this repository; `WEBCHAT.md` is only the target-specific adapter.

Do not turn `WEBCHAT.md` into a roadmap, issue list, coding style guide, methodology manual, conversation transcript, or duplicate of existing documentation. Prefer concise repo names/paths and links to authoritative project files over restating them.

## Bootstrap prompt

Replace `<owner/repo>` and use this in standard Web Chat with GitHub connected.

```text
Prepare <owner/repo> for autonomous use with JaytonKogeru/webchat-harness.

Read the current canonical HARNESS.md from JaytonKogeru/webchat-harness. Reconstruct the project's background from the target repository, materially related GitHub repositories, and any relevant ChatGPT Project conversations/files actually available to this chat; then inspect the working repository deeply enough to identify its real objective, meaningful progress signals, hard project/domain truths, authoritative state, and verification surfaces.

Do not execute the project's backlog or redesign the project in this run. Your task is only to create or refresh a concise root-level WEBCHAT.md project adapter for future autonomous ownership runs.

WEBCHAT.md must contain: Objective, Meaningful progress, Project truths, Context sources, Source-of-truth map, Verification surfaces, and Authority boundaries. Keep it concise and project-specific. Record related repositories and available ChatGPT Project context by role, not as copied content. Treat project conversations as context/history and the live working repository as the current-state authority unless the repository explicitly defines another source of truth.

If the repository's actual objective is genuinely ambiguous or internally contradictory, do not invent one. Record the ambiguity clearly in WEBCHAT.md and report that this bootstrap cannot safely resolve project intent without human input.

Do not make unrelated project changes. Commit the adapter change and return the branch/PR or commit for review.
```

## Refreshing the adapter

Refresh `WEBCHAT.md` only when the project's objective, relevant context-source map, source-of-truth structure, verification surface, or hard local constraints materially change. Routine implementation work should not churn this file.
