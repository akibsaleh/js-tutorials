# 03. Communication

## Request/Response (Sync)
- HTTP/REST: human-friendly, universal.
- gRPC: fast, binary, strong types. Good for service-to-service.

## Messaging (Async)
- Message broker: Kafka, NATS, RabbitMQ, Redis Streams.
- Publish/Subscribe: one-to-many broadcast.
- Queues: work distribution and backpressure.

## Choosing
- If user is waiting (e.g., checkout): usually sync + small timeouts.
- For workflows and integration: async events + retries.

## Contracts
- REST: OpenAPI/Swagger.
- gRPC: .proto files.
- Messaging: JSON/Avro/Protobuf schemas.

## Reliability
- Retries with exponential backoff.
- DLQ (dead-letter queue) for poison messages.
- Idempotency and deduplication.

## Example Message Flow (Order Placed)
- Order Service saves order and publishes `order.placed` event.
- Inventory Service listens, reserves stock.
- Payment Service listens, charges card.
- Notification Service listens, sends email.

## Timeouts and Circuit Breakers
- Always set timeouts on sync calls.
- Circuit breaker opens after failures to protect upstream services.
