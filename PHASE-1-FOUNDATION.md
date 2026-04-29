# Phase 1: Conceptualization & Initial Setup

## Goal
Define the core product shape, establish the technical boundaries, and prepare the repository for implementation.

## Product Scope
The application compares Figma designs against live web pages and flags design-to-production mismatches.

Core capabilities in scope:
- Figma design extraction
- Live page element extraction
- Comparison engine
- Mismatch detection and severity scoring
- Reporting and dashboard views

Out of scope for Phase 1:
- Full plugin implementation
- Full comparison algorithms
- AI-based visual matching
- Billing and production scaling

## User Stories
1. As a designer, I want to extract design metadata from Figma so that it can be checked against the built page.
2. As a QA reviewer, I want mismatches grouped by severity so I can focus on the highest-risk issues first.
3. As a product owner, I want reports that summarize layout, spacing, and missing element issues.
4. As a team admin, I want project and team isolation so multiple clients can use the platform safely.
5. As a developer, I want a predictable API contract so the plugin and backend can evolve independently.

## Functional Requirements
- Authenticate users and associate them with a tenant or team.
- Accept structured design payloads from the Figma plugin.
- Store design snapshots and project metadata.
- Define a comparison contract between design data and live page data.
- Expose a basic dashboard/reporting model for later phases.

## Non-Functional Requirements
- Data isolation between tenants.
- Clear API boundaries between plugin, backend, and dashboard.
- Testable payload formats and comparison inputs.
- Incremental delivery with minimal coupling between modules.

## Architecture
### Components
- Figma plugin: extracts design structure and sends JSON payloads.
- Backend API: authenticates requests, stores data, and orchestrates comparisons.
- Database: persists tenants, projects, designs, comparison runs, and issues.
- Dashboard: renders comparison results and reports.
- Comparison worker: later phase component for live page extraction and diffing.

### Data Flow
1. User authenticates into the platform.
2. Plugin extracts design data from Figma.
3. Plugin sends structured JSON to the backend.
4. Backend validates and stores the payload.
5. Comparison worker later retrieves design and page data.
6. Dashboard reads the stored comparison results and issues.

## Technology Stack Decision
Recommended baseline stack:
- Frontend: React
- Backend: Node.js with Fastify
- Database: PostgreSQL
- Auth: Auth0 or JWT-based auth service
- Plugin: Figma Plugin API
- Comparison automation: Playwright or Puppeteer
- Reporting: JSON first, PDF/Excel later

Reasoning:
- React and Node.js keep the stack consistent and common for SaaS dashboards.
- Fastify gives schema-first request validation and a clean route model for payload-heavy APIs.
- PostgreSQL fits structured tenancy, project, and comparison data.
- Playwright or Puppeteer handles DOM extraction reliably.
- JSON-first payloads keep the plugin/backend contract simple.

## Authentication and Tenancy Model
- Tenant is the top-level boundary for teams or clients.
- Users belong to one or more tenants.
- Roles should cover at least admin, editor, and reviewer.
- Every project, design snapshot, and comparison run must be tenant-scoped.

## Figma Integration Plan
Phase 1 plugin goals:
- Authenticate plugin sessions.
- Extract basic node metadata: frame, text, image, component, and auto-layout properties.
- Serialize the extracted content into structured JSON.
- Define a versioned payload schema for backend ingestion.

## Repository Setup
Initial repository structure:
- `docs/` for product and architecture notes
- `apps/` for frontend and backend applications
- `packages/` for shared types and utilities
- `plugins/` for the Figma plugin source
- `tests/` for cross-cutting verification

## Phase 1 Exit Criteria
- Product scope is written and stable enough to start implementation.
- A basic architecture is documented.
- Stack choices are recorded.
- Auth and tenancy rules are defined.
- The Figma plugin extraction contract is specified.
