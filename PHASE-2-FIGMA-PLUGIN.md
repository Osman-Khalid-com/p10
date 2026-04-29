# Phase 2: Figma Plugin Development

## Goal
Build the plugin that extracts design data from Figma and makes it available as structured JSON for backend comparison.

## Delivered So Far
- Plugin manifest scaffold
- Plugin UI with export controls
- Recursive node extraction helpers
- Shared snapshot contract expanded for layout, paint, text, and component metadata
- Main-thread export flow for selection or page snapshots
- Plugin-side payload validation
- Plugin package and TypeScript config scaffolding
- Sample snapshot fixture
- Build script that generates `plugins/figma/code.js`
- Fixture verification script for the extractor
- Verified extractor output against `plugins/figma/fixtures/sample-node-tree.json`
- Backend upload flow using API base URL and JWT settings
- Persisted plugin settings in Figma client storage
- Session-context loading from the API
- Session-driven project and file selection
- Verified session-context load against local PostgreSQL data
- Versioned snapshot metadata

## Current Export Flow
1. User opens the plugin.
2. User enters API URL and JWT, then loads the session context.
3. Plugin resolves the tenant and available projects/files from the API.
4. User chooses export selection or export page.
5. Plugin extracts the current nodes into a structured design snapshot.
6. Plugin displays the JSON in the UI, allows copying it, or uploads it to the API.

## Next Phase 2 Tasks
- None. Phase 2 is complete.

## Manual Verification
- Open the plugin in Figma.
- Export selection or page.
- Confirm the JSON matches the snapshot shape in `plugins/figma/fixtures/sample-snapshot.json`.
- Confirm invalid payloads are blocked by validation before export.

## Automated Verification
- Run `npm run verify:figma`.
- The script extracts a snapshot from `plugins/figma/fixtures/sample-node-tree.json`.
- The script compares the extracted result against `plugins/figma/fixtures/sample-snapshot.json`.

## Upload Behavior
- Uploads go to `POST /v1/design-snapshots`.
- The request uses the JWT in the `Authorization` header.
- The API rejects snapshots if the tenant in the token does not match the snapshot payload or if the user lacks tenant membership.

## Saved Settings
- Plugin settings are loaded from Figma client storage on open.
- Settings are written back to client storage whenever an export or upload action runs.

## Session Context
- The plugin requests `GET /v1/session-context` using the JWT.
- The API returns the tenant and accessible projects/files for the current user.
- The plugin uses that response to populate project and file selectors.
- Verified with a local tenant, project, and Figma file record set.
