# Landscape audit: are we reinventing an existing ChatGPT Web harness?

Audit date: **2026-09-11**

## Verdict

We are **not entering an empty field**. Several public projects already make ChatGPT Web more agentic, and at least two are close enough that ignoring them would be wheel-reinvention.

However, the current audit did **not** find a mature project whose primary product is exactly this repository's intended layer:

> **a thin semantic/evaluation harness for ordinary native ChatGPT Web + the native GitHub connector, with no required local runtime, MCP server, browser automation, API adapter, second coordinator agent, or fixed coding methodology, and with project-level ownership + first-principles re-audit as the control loop.**

Therefore the project is worth pursuing **only while that boundary remains sharp**. If we start building local shell tools, a browser driver, a workflow state machine, a generic skill marketplace, or a second-agent coordinator, we would be moving directly into territory already occupied by stronger existing projects.

## Closest prior art

### 1. `capitalparser/webgpt-orchestrator` — closest on native GitHub + Web Chat 6 Pro

Repository: https://github.com/capitalparser/webgpt-orchestrator

This is the closest project found to the execution surface we care about. It explicitly uses **standard ChatGPT Web with `6 Pro` and the native GitHub connector** to implement a PR. A separate local coordinator (Claude Code, Codex CLI, or another agent) drives the browser, tests the PR in an isolated checkout, sends failures back into the same chat, and repeats until ready to merge.

Key overlap:

- standard Web Chat, not Work/Codex;
- exact `6 Pro` model requirement;
- native GitHub connector does the repository writes;
- long Web Chat turn is treated as the implementation engine;
- completion is not trusted without external verification.

Key difference:

- requires a **second coordinator agent**;
- requires browser driving (`ego-browser`);
- requires local Python/`gh`/git/test execution;
- optimizes a bounded **PR test/fix loop**, not project-level autonomous ownership;
- the user/coordinator supplies a confirmed question, intent brief, scope, and validation before WebGPT starts;
- a hard iteration state machine lives outside ChatGPT.

What to borrow:

- independent verification is more reliable than trusting model prose;
- standard Chat + GitHub can be a real implementation surface;
- keep the Web Chat question/outcome explicit;
- never confuse a PR existing with the PR being correct.

What **not** to rebuild here:

- local coordinator;
- browser automation;
- checkout/test runner;
- deterministic PR retry state machine.

If users need those capabilities, `webgpt-orchestrator` is a better starting point than reimplementing them.

---

### 2. `JesseSenior/chatgpt-web-harness` — closest on durable ChatGPT Web workflow semantics

Repository: https://github.com/JesseSenior/chatgpt-web-harness

This project is a durable workflow skill for long-running ChatGPT Web tasks. It keeps workflow state, one-use execution tokens, acceptance evidence, action permissions, recovery state, and a release gate. Users attach a skill ZIP to a ChatGPT Project and set project instructions that require the runtime to start before task reasoning.

Key overlap:

- explicitly targets ChatGPT Web;
- addresses premature stopping and interrupted work;
- treats evidence and completion state as durable objects;
- tries to enforce workflow behavior beyond a simple prompt.

Key difference:

- intentionally uses a **fixed deterministic workflow runtime**;
- requires a skill ZIP + project instructions + Node scripts;
- routes actions through `allowed_next_calls`;
- requires an explicit `skill-continue-or-finalize` recovery message when ChatGPT stops;
- not specifically about native remote GitHub ownership;
- much stronger procedural enforcement than the thin frontier-model-first approach proposed here.

What to borrow:

- termination/completion behavior deserves explicit evaluation;
- resumability should not depend only on chat narrative;
- acceptance evidence should be observable.

What not to duplicate:

- tokenized workflow runtime;
- deterministic action router;
- release-state machine.

This project is evidence that "ChatGPT Web harness" is already a real category. Our value must therefore come from being intentionally **thinner and native-GitHub/project-ownership focused**, not from claiming the category itself is new.

---

### 3. `Kyne0328/rel-ai-chatgpt-web-harness` — strong local MCP agency runtime

Repository: https://github.com/Kyne0328/rel-ai-chatgpt-web-harness

Rel.AI keeps the normal ChatGPT Web reasoning surface but adds a local MCP/desktop agency layer: repository access, shell commands, tests, processes, Git, validation, memory, observability, and optional computer control.

Key overlap:

- ChatGPT Web remains the reasoning/conversation host;
- repository work is first-class;
- validation and task continuity are explicit;
- aims at end-to-end coding from normal ChatGPT.

Key difference:

- local repository, local runtime, MCP tunnel, desktop application;
- provides tools ChatGPT Web otherwise lacks;
- much larger execution surface and security boundary.

Boundary decision:

`webchat-harness` should **not** build local filesystem/shell/MCP capabilities. Rel.AI already addresses that problem directly.

---

### 4. `jamesmendax/chatgpt-web-harness` — self-hosted MCP tool surface

Repository: https://github.com/jamesmendax/chatgpt-web-harness

A self-hosted MCP server with local files, shell, Git, checkpoints, binary transfer, skills, and ChatGPT Web tool profiles.

Key difference from our intended project:

- tool/runtime infrastructure rather than a semantic operating contract;
- local computer execution rather than native remote GitHub actions.

Boundary decision:

Do not build a competing MCP tool server.

---

### 5. `escapeWu/chatgpt-web-oauth-mcp` / `AxelHu/chatgpt-web-agent`

Repositories:

- https://github.com/escapeWu/chatgpt-web-oauth-mcp
- https://github.com/AxelHu/chatgpt-web-agent

Both bridge ChatGPT Web to local filesystem/shell/git-style tools through MCP-style infrastructure. They are relevant proof that many users want normal Web Chat as the reasoning surface, but they solve **local tool access**, not the native GitHub semantic-control problem.

---

### 6. `Ancienttwo/repo-harness`

Repository: https://github.com/Ancienttwo/repo-harness

A file-backed workflow harness primarily for reliable Claude Code/Codex sessions, with a ChatGPT browser consult engine through Oracle.

Overlap:

- repository-backed durable state;
- explicit policy and audit records;
- ChatGPT Web can contribute planning/review.

Difference:

- external agent runtime remains primary;
- ChatGPT Web is driven as a browser consult engine rather than acting natively through its GitHub connector.

---

### 7. `chatgpt-web-adapter`

Repository surfaced in search: https://github.com/kymuco/chatgpt-web-adapter

A Python SDK around an existing chatgpt.com web session, including experimental auto-approval of GitHub connector actions and independent verification hooks.

Important lesson:

- connector side effects should be verified independently where possible;
- there is already tooling for automating the web transport layer.

Boundary decision:

Do not build an unofficial ChatGPT Web transport/API adapter here.

---

## Adjacent workflow systems

These are important intellectual prior art but not direct product duplicates.

### OpenAI harness engineering

https://openai.com/index/harness-engineering/

Important lessons:

- repository knowledge should be the system of record;
- large monolithic `AGENTS.md` manuals fail;
- give agents a map and use progressive disclosure;
- plans, architecture, quality, and decision state can be durable repo artifacts;
- feedback loops matter more than simply producing code.

### OpenAI GPT-6 Astra model guidance

https://developers.openai.com/api/docs/guides/latest-model?model=gpt-6-astra

Important lessons:

- Astra is more instruction-sensitive than earlier models;
- conflicting skills/AGENTS instructions can alter behavior or cause pauses;
- autonomy should be prompted explicitly when reasonable assumptions are desired;
- long-task coherence is improved, so a thin harness can rely more on model judgment;
- testing should be calibrated rather than ritualized.

These points strongly argue against building a huge router/skill stack by default.

### Superpowers

https://github.com/obra/superpowers

A complete skill-driven development methodology with brainstorming, design approval, implementation planning, TDD, debugging, and subagent workflows.

Useful ideas: testing discipline, systematic debugging, YAGNI.

Not adopted as the universal harness because its mandatory human approval and workflow gates conflict with project-level autonomous ownership, and because a frontier model should be allowed to choose the appropriate engineering method for the specific project.

### Ponytail

https://github.com/jorgeasaurus/agent-skills/tree/main/ponytail

Useful principle: eliminate the need, reuse existing code, use standard/native solutions, prefer deletion and minimalism.

The principle is valuable; loading the full skill globally is unnecessary. The canonical harness compresses this into a short value/simplicity invariant.

## Exact differentiation we should defend

A change belongs in this project only if it improves at least one of these without requiring a new runtime:

1. **Project ownership** — model optimizes the real product, not a stale ticket queue.
2. **Reality reconstruction** — live repo/evidence outranks inherited narrative.
3. **Autonomous follow-through** — model acts instead of stopping at plan/proposal.
4. **Value-based re-audit** — after material work, priorities are recomputed.
5. **Simplicity/reuse pressure** — avoid unnecessary infrastructure and duplicate wheels.
6. **Truthful verification** — no fake tests/review/provenance.
7. **Termination calibration** — stop on diminishing returns or genuine blockers, not intermediate artifacts.
8. **Behavioral evaluation** — measure premature stop, drift, false verification, stale-plan lock-in, and unnecessary intervention.

If a proposed feature is primarily about local execution, browser control, tool transport, deterministic state-machine orchestration, or teaching generic coding technique, the default answer should be **reuse an existing project instead of adding it here**.

## Non-duplication conclusion

The initial claim "nobody has built anything similar" is **false**.

The narrower claim below is currently supported by the landscape audit:

> No mature project found so far is specifically a **thin, frontier-model-first, native ChatGPT Web + native GitHub connector semantic harness** whose control loop is **project ownership → first-principles audit → autonomous action → evidence-based verification → adversarial review → project re-audit**, with no required local runtime or second agent.

That is a meaningful niche, but it is narrow. The repository should remain small enough that this distinction stays obvious.

## Search terms used in the initial audit

Examples:

- `ChatGPT Web GitHub autonomous repository harness`
- `GPT-6 Pro GitHub Web Chat PR autonomous repository`
- `ChatGPT Web GitHub connector autonomous engineering harness`
- `native ChatGPT Web GitHub agent harness`
- `chatgpt web harness`
- `ChatGPT Web GitHub connector`

This file should be updated whenever a new adjacent project is discovered. Finding a superior mature implementation is a success condition: integrate or defer to it rather than protecting this repository's scope for its own sake.
