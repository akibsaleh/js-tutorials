# 05. Resilience & Reliability

## Common Techniques
- Timeouts: never wait forever.
- Retries: exponential backoff + jitter.
- Circuit Breaker: stop calling when downstream is unhealthy.
- Bulkhead: isolate resources per service or pool.
- Rate Limiting and Throttling.

## Delivery Semantics
- At-least-once is common for messaging. Design for idempotency.
- Exactly-once is expensive and rare in distributed systems.

## Data Integrity
- Unique constraints and idempotency keys.
- Compensating transactions for Sagas.

## Graceful Shutdown
- Handle SIGTERM. Stop accepting new work. Finish in-flight tasks.

## Testing for Failure
- Chaos testing and fault injection.
- Load testing with realistic traffic.
