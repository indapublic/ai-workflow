# ai-workflow

A practical, tool-agnostic template for running software delivery with coding agents
(Claude Code, Codex, Cursor, Cline — whichever you use) without turning the codebase into a slot machine.

The idea is simple: **the agent types, the engineer owns the spec, the tests, and the review.**

## Principles

1. **Spec before code.** If the change cannot be described in a one-page spec, it is not ready for an agent.
2. **Small tasks, small diffs.** One task = one reviewable change. Large prompts produce large mistakes.
3. **Tests are the contract.** Acceptance criteria become tests before implementation.
4. **Context is a file, not a chat.** Project rules live in `AGENTS.md`, not in a prompt someone forgot.
5. **Human review is a gate, not a formality.** Every agent change goes through the checklist in `docs/review-checklist.md`.
6. **Measure, do not brag.** Track lead time, review time, rework rate — not "lines generated".

## What is inside

| File | Purpose |
| --- | --- |
| [`AGENTS.md`](AGENTS.md) | Project rules for coding agents: commands, conventions, boundaries, definition of done |
| [`docs/spec-template.md`](docs/spec-template.md) | One-page feature spec: problem, scope, data, API, edge cases, tests, rollout |
| [`docs/task-decomposition.md`](docs/task-decomposition.md) | How to split a feature into agent-sized tasks with acceptance criteria |
| [`docs/review-checklist.md`](docs/review-checklist.md) | Human review checklist, including agent-specific failure modes |
| [`examples/feature-spec-search.md`](examples/feature-spec-search.md) | A filled example of a spec |
| [`examples/review-notes.md`](examples/review-notes.md) | A filled example of review notes and follow-ups |

## How to use it

1. Copy `AGENTS.md` to the root of your repository and replace the placeholders.
2. Write a spec with `docs/spec-template.md` for the next feature.
3. Split it into tasks with `docs/task-decomposition.md`.
4. Give the agent one task, the spec, and the commands from `AGENTS.md`.
5. Review the result with `docs/review-checklist.md` before merging.
6. Record what slowed you down and update `AGENTS.md` — the file is the memory.

## Non-goals

- This is not a prompt collection for generating an app in one shot.
- It does not replace code review, tests, or architecture decisions.
- It contains no invented metrics: bring your own numbers from your own repositories.

## License

MIT. See [LICENSE](LICENSE).
