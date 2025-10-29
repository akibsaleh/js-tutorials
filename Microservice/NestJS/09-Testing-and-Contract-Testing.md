# 09. Testing & Contract Testing

## Unit Tests
- Test services and helpers with mocks.

## Integration Tests
- Spin up Postgres/Mongo/Redis in Docker for tests.
- Test repositories and controllers.

## Contract Tests
- Use Pact or similar: define consumer expectations; verify provider.

## Microservice Messaging Tests
- Test message handlers with in-memory transport or test brokers.

## CI Tips
- Run unit first, then integration/contract.
