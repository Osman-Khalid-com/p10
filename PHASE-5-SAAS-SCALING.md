# Phase 5: SaaS Scaling and External Integrations

## Goal
Turn the comparison engine into a tenant-scoped SaaS platform with programmatic access and billing metadata.

## Delivered So Far
- Tenant billing metadata in PostgreSQL
- Tenant API keys for programmatic access
- API key scopes for read, write, reports, and webhook management planning
- Programmatic comparison endpoint authenticated by API key
- Billing endpoint for tenant plan visibility
- Route-level smoke test for API key integration
- Migration applied locally for SaaS access tables
- API key revocation
- Webhook subscription and delivery layer
- Webhook delivery smoke test
- Webhook delivery retry attempts with dead-letter tracking
- Webhook delivery log endpoint
- Comparison webhooks now support `comparison.failed` in addition to `comparison.created`
- Webhook payload signing and verification headers
- API keys now support read and report scopes for programmatic access
- Dashboard webhook management UI for create/list/revoke/deliveries
- Dead-letter webhook redelivery endpoint and dashboard action

## Scaling Strategy
- Keep tenant identity bound to either a user JWT or an API key.
- Use API keys for server-to-server integrations and automation.
- Keep billing metadata close to the tenant row so plan state is easy to query.
- Add dedicated integration endpoints rather than overloading the human dashboard path.

## Next Phase 5 Tasks
- Phase 5 implementation is complete; next work should move to Phase 6 scaling refinements.
