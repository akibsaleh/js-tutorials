# 10. Versioning & Evolution

## Backward Compatibility First
- Add new fields with defaults. Avoid breaking changes.
- Support old and new consumers during migration.

## API Versioning
- URI versioning (e.g., /v1), or header-based, or resource versioning.

## Message Versioning
- Include schema version in message. Consumers handle old/new.

## Database Migrations
- Safe forward-only migrations. Roll forward if possible.
- Zero-downtime steps (add column -> backfill -> switch -> drop later).
