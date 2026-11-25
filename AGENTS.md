# AGENTS.md

> Project rules for coding agents. Keep this file short, concrete, and current.
> Replace every `<placeholder>` before use.

## Project context

- Product: `<what it does, for whom>`
- Stack: `<languages, frameworks, databases, infra>`
- Repo layout: `<apps/, packages/, services/ ...>`
- Environments: `<local, staging, production>`

## Commands

```bash
# install
<command>

# run locally
<command>

# tests
<command>

# lint / typecheck
<command>

# build
<command>
```

## Code conventions

- Language and style: `<e.g. TypeScript strict, no any, functional components>`
- Naming: `<files, components, database tables>`
- Error handling: `<pattern>`
- Logging and telemetry: `<pattern>`
- Do not add dependencies without explicit approval.

## Workflow contract

1. **Plan first.** For any task larger than a one-line fix, produce a short plan and wait for approval.
2. **Work from the spec.** The spec is the source of truth; if it is wrong, stop and ask.
3. **One task per change.** Do not mix refactoring, features, and formatting in one diff.
4. **Tests first.** Add or update tests that encode the acceptance criteria.
5. **No secrets.** Never print, commit, or log credentials, tokens, or personal data.
6. **No destructive operations.** No force-push, history rewrite, or data deletion without explicit approval.
7. **Ask when ambiguous.** A wrong assumption costs more than a question.

## Definition of done

- The change matches the spec and the acceptance criteria.
- Tests pass locally and in CI.
- Lint and typecheck pass.
- Error states, empty states, and loading states are handled.
- Documentation or changelog updated when behavior changes.
- The diff is small enough to review in one sitting.

## Review gates

- Human review is required for every change.
- Use `docs/review-checklist.md`.
- Agent-generated code is treated as a draft from a fast but overconfident colleague.
