# Phase 4: Flagging and Reporting

## Goal
Turn comparison runs into actionable reports with severity grouping, threshold summaries, and downloadable output.

## Delivered So Far
- Comparison issues already carry severity
- Comparison runs already persist tolerance values
- Shared report generation with severity totals and grouped issue counts
- API report endpoint for persisted comparison runs
- Dashboard report download action for persisted runs
- API report route smoke-tested against local PostgreSQL and JWT auth
- Dashboard CSV export for report issues
- Dashboard report issue-group drill-down
- Dashboard PDF export for report summaries
- Report pattern drill-down summaries

## Reporting Strategy
- Reuse the persisted comparison run as the source of truth.
- Group issues by code and severity.
- Summarize the run by status, severity count, and tolerance.
- Export the report as JSON first, then add richer formats later.

## Next Phase 4 Tasks
- Phase 4 is complete; move to the SaaS scaling phase.
