# webchat-harness — retired

> **Retired on 2026-09-13.** This repository is preserved as historical prior art. New development has moved to [`JaytonKogeru/PAIS`](https://github.com/JaytonKogeru/PAIS).

`webchat-harness` explored a thin semantic layer for making ordinary ChatGPT Web + GitHub behave more like an autonomous repository owner.

The experiment produced several useful principles:

- reconstruct current reality from the live repository and authoritative evidence;
- optimize the real project outcome rather than blindly execute stale plans;
- continue while material autonomous work remains;
- verify material actions with evidence actually available;
- persist state that must survive a session boundary;
- reassess priorities after meaningful changes;
- prefer reuse, simplification, replacement, or deletion over unnecessary construction.

Those ideas have been absorbed into PAIS as general operating principles. The standalone harness is no longer differentiated enough to justify separate maintenance: repository harness engineering, durable checkpoints, cross-session continuation, acceptance evidence, and repo-as-truth patterns now have substantial native and open-source prior art.

## What happens to the old artifacts?

They remain in this repository for historical reference:

- `SKILL.md` — the final skill-first runtime experiment;
- `research/LANDSCAPE.md` — the prior-art audit that helped establish the non-duplication boundary;
- `evals/README.md` — behavioral evaluation ideas;
- `AGENTS.md` — repository-maintenance guidance from the experiment.

Do not bootstrap new repositories with Web Chat Harness and do not add new features here.

## Successor

PAIS addresses the broader and more durable problem:

```text
replaceable frontier web model
        ↓
replaceable control / gateway plane
        ↓
multi-device capability fabric
        ↓
durable project + task + machine state
```

The model session is treated as replaceable. Work and authoritative state are not.

See: [`JaytonKogeru/PAIS`](https://github.com/JaytonKogeru/PAIS)
