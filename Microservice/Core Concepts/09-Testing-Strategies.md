# 09. Testing Strategies

## Pyramid
- Unit tests: fast, many.
- Integration tests: DB, broker, HTTP.
- Contract tests: provider/consumer alignment (e.g., Pact).
- End-to-end: a few critical flows.

## Test Data
- Factories and seed data.
- Ephemeral environments per PR if possible.

## Non-Functional
- Load tests, chaos tests, security tests.

## CI Tips
- Run fast tests early. Parallelize. Cache deps.
