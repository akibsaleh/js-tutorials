# 01. Introduction

- **Goal**: Understand what microservices are and when to use them.
- **Audience**: Beginners, non-native English readers.

## What is a Microservice?
- A small, independent service that does one main business job ("single responsibility").
- Runs as its own process. Communicates with other services over the network.
- Each service can be built, deployed, and scaled independently.

## Why Microservices?
- **Team speed**: Small teams own small services.
- **Scalability**: Scale hot services only.
- **Resilience**: Failure in one service should not stop others.
- **Technology freedom**: Each service can choose its own tech (but keep company standards).

## When to avoid?
- Very small apps or early prototypes. A monolith is simpler.
- Teams without strong DevOps and automation.

## Key Ideas
- Bounded Context (from Domain-Driven Design): each service owns a clear domain.
- API-first: clear, stable contracts between services.
- Data isolation: each service owns its data store.
- Asynchronous messaging: reduce coupling, improve resilience.

## Typical Service Examples
- User Service
- Order Service
- Inventory Service
- Payment Service
- Notification Service

## Comparison: Monolith vs Microservices
- Monolith: one codebase, easy to start, hard to scale organization.
- Microservices: many services, harder to start, can scale teams and features faster.

## Learning Path
1) Core concepts (this section)
2) Hands-on NestJS guide
3) Build example app + assignments
