# Review checklist

Use this for every agent-generated change. The goal is not to nitpick style; it is to catch the failure modes agents produce under pressure.

## Correctness

- [ ] The change matches the spec and acceptance criteria.
- [ ] Edge cases from the spec are handled.
- [ ] Error, empty, and loading states exist.
- [ ] No behavior change outside the task scope.

## Agent-specific risks

- [ ] No invented APIs, flags, or library methods.
- [ ] Imports exist and point to the right modules.
- [ ] No unnecessary dependencies or duplicated helpers.
- [ ] No copy-paste from a different part of the codebase with wrong names.
- [ ] Comments and docs match what the code actually does.
- [ ] No silent fallbacks that hide failures.

## Security and data

- [ ] Input is validated at the boundary.
- [ ] Authorization is checked on the server, not only in the UI.
- [ ] No secrets, tokens, or personal data in code, logs, or tests.
- [ ] Queries are parameterized; no string-built SQL.
- [ ] Migrations have a rollback path.

## Performance

- [ ] No obvious N+1 queries.
- [ ] Lists are paginated or virtualized when needed.
- [ ] Expensive work is not repeated per render or per request.
- [ ] Bundle impact is understood for frontend changes.

## Tests

- [ ] New behavior is covered by a test that would fail without the change.
- [ ] Tests assert behavior, not implementation details.
- [ ] Flaky timing or network dependencies are avoided.

## Operability

- [ ] Logs and metrics allow diagnosing the new path.
- [ ] The change can be rolled back without data loss.
- [ ] Documentation or changelog updated.

## Final question

Would I be comfortable being on call for this change at 3 a.m.? If not, what is missing?
