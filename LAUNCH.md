# Launchers

These launchers are intentionally short. The canonical behavior lives in [`HARNESS.md`](HARNESS.md); the launcher only switches the current Web Chat into autonomous repository-ownership mode.

## Full-project ownership run

Replace `<owner/repo>` with the target repository.

```text
Take full ownership of <owner/repo> for this run.

Before acting, load and follow the latest canonical HARNESS.md from JaytonKogeru/webchat-harness, then inspect the target repository's own instructions and live state. Treat the project—not its existing issues, plans, architecture, or current task list—as the unit of work.

Use the native GitHub tools directly. Audit the project from first principles, decide what materially improves the intended product, act on what you find, verify the result with evidence actually available to you, adversarially review your own work, then re-audit from the new repository state and continue under the harness terminal conditions.

Do not stop at planning, an audit, a work packet, a commit, a pull request, passing one check, or partial success. Do not ask me questions that you can resolve from the repository, tools, evidence, or external research. Do not switch this task to Work or Codex unless I explicitly ask you to.

Do not give me a running diary. Start now.
```

## Resume an existing ownership run

Use this when a prior Web Chat stopped, lost context, or needs a fresh conversation.

```text
Resume autonomous ownership of <owner/repo> under the latest canonical HARNESS.md from JaytonKogeru/webchat-harness.

Do not trust the previous chat's narrative as current state. Reconstruct reality from the live repository, recent relevant commits/branches/PRs, project-specific instructions, and available external evidence. Determine what was actually completed, what remains material, and what earlier plans are now stale.

Continue the audit → act → verify → adversarial review → re-audit loop until the harness terminal condition is genuinely met or a real non-delegable blocker remains. Stay in standard Web Chat and use the native GitHub tools directly. Do not give me a running diary.
```

## Independent adversarial review

Prefer a fresh chat for this mode so the reviewer is not anchored to the builder's narrative.

```text
Audit <owner/repo> as an independent adversarial reviewer under the latest canonical HARNESS.md from JaytonKogeru/webchat-harness.

Assume another agent claims the project or current delivery is complete. Do not trust that claim, its plans, or its self-review. Reconstruct the live state from the repository and relevant evidence, try to falsify the completion claim, and directly fix every material problem that can be resolved within the available authority. Re-audit after fixes. Stop only under the harness terminal conditions.
```

## Target-repository pointer (optional)

A target repository may add this small pointer to its own `AGENTS.md` or equivalent map. Do **not** copy the full universal contract into every repository unless offline/self-contained operation is specifically required.

```text
When the user explicitly launches autonomous Web Chat ownership mode, load the current canonical contract from JaytonKogeru/webchat-harness/HARNESS.md. Project-specific instructions in this repository define domain truth and explicit local constraints; they do not silently fork the universal harness.
```

## What not to put in the launcher

Avoid turning the launch message into a large workflow manual. In particular, do not automatically require brainstorming gates, human approval of every design, TDD for every change, fixed numbers of PRs, fixed agent roles, or a mandatory PRD pipeline. Add project-specific constraints only when they represent real project truth or explicit user intent.
