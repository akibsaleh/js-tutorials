# 07. Example App Guide

We will build a small system:
- Users Service (NestJS + Postgres/Prisma)
- Catalog Service (NestJS + MongoDB/Mongoose)
- Orders Service (NestJS + Postgres/Prisma)
- Notification Service (NestJS + Redis pub/sub)
- API Gateway (NestJS HTTP) to accept client requests

## High-Level Flow
1) Client calls API Gateway to place an order.
2) Gateway calls Users and Catalog (sync) to validate.
3) Orders Service creates order and publishes `order.placed` (async).
4) Notification Service listens and sends email.

## Local Infra (Docker Compose snippet)
```yaml
version: '3.9'
services:
  postgres:
    image: postgres:16
    environment:
      POSTGRES_PASSWORD: password
    ports: ["5432:5432"]
  mongo:
    image: mongo:7
    ports: ["27017:27017"]
  redis:
    image: redis:7
    ports: ["6379:6379"]
```

## Steps
- Create each NestJS service with Nest CLI.
- Implement minimal endpoints and message patterns.
- Wire Prisma for Users/Orders; Mongoose for Catalog; node-redis for Notification.
- Add timeouts and retries on client calls.
- Add health endpoints and basic logging.

## Suggested Endpoints
- Users: GET /users/:id
- Catalog: GET /products/:id
- Orders: POST /orders

## Suggested Events
- `order.placed` with payload `{ orderId, userId, items }`.

## What to Practice
- DTO validation, error handling.
- Idempotency on Orders (idempotency-key header).
- Caching product reads in Redis.
