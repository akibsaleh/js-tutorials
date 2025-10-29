# 12. Migration From Monolith

## Strangler Fig Pattern
- Add new microservices around the monolith.
- Slowly route some features to new services.

## Data Migration
- Sync data with CDC or batch jobs.
- Keep source of truth clear.

## Decomposition Steps
1) Identify bounded contexts.
2) Extract low-risk, high-value services first.
3) Build automation (CI/CD, infra, observability) early.
4) Gradually retire monolith modules.

## Communication Plan
- Inform teams and users about changes and timelines.
