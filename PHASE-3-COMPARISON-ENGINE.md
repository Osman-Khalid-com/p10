# Phase 3: Comparison Engine Development

## Goal
Compare the Figma design snapshot against a live page snapshot and produce actionable mismatch issues.

## Delivered So Far
- Shared page snapshot types
- Shared comparison engine
- Style-aware comparison for text and background color
- Greedy child matching by tag, text, and box proximity
- Layout-aware spacing comparisons
- Page snapshot validation
- API preview route for running comparisons
- Fixture-based comparison verification
- Live page snapshot extraction from a URL
- Fixture-based page extraction verification
- Browser-backed page extraction verification
- Browser-aware viewport, scale, and user-agent capture settings
- Component-aware matching for buttons, links, and form controls
- Persisted comparison runs in PostgreSQL
- Comparison history read path for dashboard use
- Dashboard UI for history browsing and run drill-down
- Dashboard filters, summary cards, and JSON export
- Dashboard project and Figma file drill-down filters

## Comparison Strategy
- Compare root counts and child counts first.
- Compare bounding boxes with a pixel tolerance.
- Compare text content where it exists.
- Match child nodes greedily by tag, text, and box proximity.
- Compare layout spacing when the design snapshot exposes padding or item spacing.

## Preview Route
- `POST /v1/comparisons/preview`
- Accepts a design snapshot and a page snapshot
- Returns a comparison result with severity and issue details

## Next Phase 3 Tasks
- Phase 3 is complete; reporting continues in Phase 4.
