# Phase 7: Beta Testing and Feedback Loop

## Goal
Collect tester feedback on real comparison runs and keep the dashboard and API aligned with what users actually flag.

## Delivered So Far
- Comparison feedback table in PostgreSQL
- Feedback submit and list endpoints for comparison runs
- Dashboard feedback form and feedback list on the run detail view
- Smoke test that creates a comparison run, submits feedback, and reads it back
- Tenant tuning endpoint that derives a default comparison tolerance from feedback
- Dashboard tuning summary showing the derived tolerance and rationale
- Issue status table in PostgreSQL
- Issue status submit and list endpoints for comparison runs
- Dashboard issue resolution controls on the run detail view
- Smoke test that creates a failing comparison, resolves an issue, and reads it back

## Beta Loop Strategy
- Keep feedback attached to a specific comparison run.
- Capture rating, sentiment, notes, and tags.
- Use the dashboard to review what testers say before expanding automation.

## Next Phase 7 Tasks
- Run against a few real pages and Figma exports to validate the full flow end to end.
