# Task decomposition

Large prompts produce large mistakes. Split work until each task is reviewable in one sitting.

## Rules

- One task = one behavior change.
- Every task has acceptance criteria and a verification command.
- Refactoring that is not required by the task goes into a separate task.
- If a task touches more than ~5 files, split it again.

## Task template

```md
### Task <n>: <title>

Goal: <one sentence>

Context:
- Spec section: <link or heading>
- Files: <paths>

Acceptance criteria:
- [ ] <observable result>
- [ ] <test proves it>

Verification:
- `<command>`

Out of scope:
- <what not to touch>
```

## Order of work

1. Tests or fixtures that describe the expected behavior.
2. The smallest implementation that makes them pass.
3. Cleanup, documentation, and observability.
4. Independent review.

## Handoff prompt

```
Read AGENTS.md and the spec at <path>. Implement task <n> only.
Do not change files outside the task scope.
Run <tests> and <lint> before you finish.
Return: a summary, the diff, and anything you are unsure about.
```
