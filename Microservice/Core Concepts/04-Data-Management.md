# 04. Data Management

## Database per Service
- Each service owns its schema and storage engine.
- Tech choice by need: PostgreSQL, MongoDB, Redis, etc.

## Transactions Across Services
- Avoid 2PC (distributed transactions) if possible.
- Use Sagas: split into small steps with compensations.

## Outbox Pattern
- Write data and event in the same local transaction.
- A worker reads the outbox table and publishes events.

## Change Data Capture (CDC)
- Tools like Debezium read DB logs to publish change events.

## Read Models and Caching
- Pre-compute denormalized views for fast reads (CQRS).
- Use Redis for caching and rate limiting.

## Schema Evolution
- Backward compatible changes first (add fields with defaults).
- Deploy producers/consumers safely with versioning.

## Multi-Tenancy (brief)
- Separate DBs or schemas per tenant, or row-level filtering.
- Prefer isolation for noisy neighbors and compliance.
