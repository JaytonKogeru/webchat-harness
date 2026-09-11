# Launchers

These launchers are intentionally short. The universal behavior lives in [`HARNESS.md`](HARNESS.md); the target repository's local objective/context map lives in its root `WEBCHAT.md` created with [`BOOTSTRAP.md`](BOOTSTRAP.md).

## Full-project ownership run

Replace `<owner/repo>` with the target repository.

```text
Take full ownership of <owner/repo> under the current JaytonKogeru/webchat-harness. Load HARNESS.md and <owner/repo>/WEBCHAT.md, reconstruct the project from the live working repository plus the related GitHub repositories and ChatGPT Project context actually available through the sources it identifies, then work autonomously until the harness terminal condition is genuinely met.

Treat the live target repository and its declared authoritative sources as current-state truth, do not invent unavailable context, and do not give me a running diary. Start now.
```

If `WEBCHAT.md` does not exist, bootstrap the target repository first using [`BOOTSTRAP.md`](BOOTSTRAP.md).

## Resume an existing ownership run

```text
Resume autonomous ownership of <owner/repo> under the current JaytonKogeru/webchat-harness. Reload <owner/repo>/WEBCHAT.md, refresh only the relevant context sources that remain available, reconstruct current reality from the live target repository, and continue until the harness terminal condition is met or a real non-delegable blocker remains.

Do not trust old chat narrative or stale task state over live repository evidence, and do not give me a running diary.
```

## Independent adversarial review

Prefer a fresh chat so the reviewer is not anchored to the builder's narrative.

```text
Review <owner/repo> independently under the current JaytonKogeru/webchat-harness. Read <owner/repo>/WEBCHAT.md, use the relevant context sources it identifies only as background, reconstruct current truth from the live repository/evidence, try to falsify the completion claim, fix every material resolvable problem, and stop only under the harness terminal conditions.
```

## What not to put in the launcher

Do not turn the launch message into a second workflow manual. Avoid mandatory brainstorming gates, human approval of every design, universal TDD, fixed PR counts, fixed agent roles, or a mandatory PRD pipeline unless the target project itself genuinely requires them.
