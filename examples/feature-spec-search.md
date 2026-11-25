# Feature spec: search and filters in the sessions dashboard

Status: approved
Owner: example
Date: 2026-01-15

## Problem

Users with hundreds of sessions cannot find a past run. They scroll and guess. Support gets "where is my session" tickets that are solved by search.

## Users and jobs

- Primary user: an engineer who runs agents daily.
- Job: when I need a past session, I want to find it by text, project, or date, so that I stop scrolling.

## Scope

- In scope: full-text search over session titles and messages; filters by project, tag, and date range; URL state.
- Out of scope: semantic search, saved searches, cross-user sharing.

## UX

- Entry: search field at the top of the dashboard.
- Flow: type a query -> results update after 200 ms debounce -> filters narrow the list -> the URL reflects the state.
- Empty: "No sessions match" with a reset action.
- Error: inline message with retry.
- Permissions: users see only their own sessions.

## Data model

- Add a `search_vector` column to `sessions` with a GIN index.
- No destructive migration; backfill in a background job.

## API

- `GET /api/sessions?q=&project=&tag=&from=&to=&cursor=`
- Response: `{ items, nextCursor }`; errors use the existing error envelope.
- Validation: query up to 200 characters; dates in ISO 8601.

## Edge cases

- Empty query returns the unfiltered list.
- Special characters in the query are escaped.
- A deleted project does not break the filter.
- Large result sets are paginated by cursor.

## Observability

- Log query duration; alert if p95 exceeds 300 ms for a week.
- Metric: `sessions_search_latency_ms`.

## Test plan

- Unit: query parser, filter builder.
- Integration: search returns only the user's sessions; pagination is stable.
- E2E: type, filter, reload the URL, see the same results.

## Rollout and rollback

- Feature flag `search_v1`, default off.
- Rollout 10% -> 50% -> 100%.
- Rollback: disable the flag; the column stays.

## Open questions

- [ ] Do we index message bodies or only titles? — owner — before implementation.
