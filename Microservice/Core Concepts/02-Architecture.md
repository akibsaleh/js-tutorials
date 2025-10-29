# 02. Architecture

## Service Boundaries
- Split by business capability (e.g., Payments, Catalog, Users).
- Avoid splitting by technical layers (e.g., "Controllers" service).

## Service Components
- API layer (HTTP/gRPC) and/or messaging consumer (Kafka/NATS/RabbitMQ/Redis Streams).
- Business logic.
- Data layer (database per service).
- Background workers / schedulers.

## Communication Styles
- **Synchronous**: REST/HTTP, gRPC. Easy to reason, tighter coupling.
- **Asynchronous**: Events/messages. Better decoupling and resilience.
- Choose per use case. Often a mix (hybrid).

## Patterns
- API Gateway: single entrypoint for clients.
- Service Discovery: find other services (Kubernetes DNS, Consul, etc.).
- Config Service: central config (12-factor: env vars preferred).
- Circuit Breaker, Retry, Timeout, Bulkhead: resilience patterns.
- Saga: coordinate multi-service transactions.
- Outbox + CDC: reliable event publishing from DB changes.
- CQRS: separate read/write models when needed.

## Data Ownership
- One service = one data store. No shared DB.
- Other services must use APIs/events to read data.

## Idempotency
- Safe to retry the same request/event without creating duplicates.
- Use idempotency keys, unique constraints, and checks.

## Backpressure
- Protect services when downstream is slow. Use queues, rate limits, buffers.

## Evolution
- Backward compatible APIs. Version endpoints or messages.
- Blue/green and canary deployments for safe releases.
