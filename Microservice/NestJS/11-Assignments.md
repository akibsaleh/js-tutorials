# 11. Assignments

## Build
- Implement Users, Catalog, Orders, Notifications, API Gateway.
- Add Postgres (Users, Orders), Mongo (Catalog), Redis (Notifications, cache).

## Validate
- Add DTO validation and error handling.
- Add idempotency-key for Orders creation.

## Operate
- Add health endpoints and basic metrics.
- Add request timeouts and retries.

## Stretch Goals
- Add gRPC between services.
- Add outbox pattern for Orders → `order.placed`.
