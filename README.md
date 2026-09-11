# webchat-harness

A lightweight, repository-grounded harness for turning **ChatGPT Web + GitHub** into a
persistent autonomous engineering/research agent, optimized for frontier Pro models and
long single-turn execution.

## Idea

ChatGPT Web can reason for a long time in a single turn, but it has no durable working
memory, no reliable shell, and no way to keep state across sessions. GitHub has all three
(version control, issues, Actions, file storage) but no intelligence.

This project is the thin layer that couples them:

> **The repository is the agent's environment. ChatGPT Web is its reasoning engine.
> The harness is the protocol between them.**

Instead of inventing a heavyweight framework, everything the agent needs to persist lives
in plain repository files that a human can read and review:

| Concern | Lives in |
|---|---|
| Current task / acceptance criteria | task + handoff files in-repo |
| Working state between turns | committed files, branch state |
| Execution (tests, builds, scripts) | CI workflows + a local/remote runner |
| Review + audit trail | git history, PRs, review files |

## Design principles

- **Repository-grounded** — no hidden state; if it matters, it is committed.
- **Long single-turn friendly** — the harness assumes the model may work for a long time
  in one shot, so work must be check-pointed into commits, not held in context.
- **Small surface area** — protocols and conventions, not a framework. A new user should
  be able to read the whole harness in one sitting.
- **Human-reviewable** — every artifact the agent produces is a file a human can diff.
- **Pro-model oriented** — assumes strong reasoning + tool use; optimizes for autonomy
  and fewer round-trips rather than for tiny models.

## Status

Early scaffold. Protocol and conventions are being defined; no stable interface yet.

## Related

- Sibling project: **ChatVMD** (natural-language control for VMD) — an example of the kind
  of engineering work this harness is meant to carry.
