# Phase 6: SaaS Architecture and Scaling

## Goal
Add practical scaling guardrails around the SaaS surface: tenant usage visibility, plan-based quotas, and enforcement at write boundaries.

## Delivered So Far
- Tenant usage endpoint for counts and limits
- Plan-based quota checks for API keys, webhooks, design snapshots, and comparison runs
- Tenant usage smoke test covering API key and webhook caps
- Dashboard usage summary tied to the tenant usage endpoint
- Tenant billing metadata plus checkout and portal action endpoints
- Billing provider smoke test against the manual fallback path

## Scaling Strategy
- Keep billing metadata on the tenant row.
- Derive quotas from the plan name in application code.
- Enforce quotas before writes so the API fails fast.
- Keep usage reads tenant-scoped and dashboard-facing.

## Next Phase 6 Tasks
- Add paid-plan billing provider credentials when you want Stripe-backed checkout and portal URLs.
