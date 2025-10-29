# 08. Observability in NestJS

## Logging
- Use Nest built-in logger or a structured logger.
- Add correlation IDs per request.

## Health Checks
- Add `/health` and `/ready` in each service.
- For gRPC: integrate grpc-health-check.

## Tracing (OpenTelemetry)
- Add OTel SDK, instrument HTTP/gRPC, Prisma, Mongoose.
- Export to Jaeger/Tempo. Trace IDs in logs.

## Metrics
- Expose Prometheus metrics (HTTP endpoint) or use OTel metrics.

Sources: NestJS gRPC health, microservice basics.
