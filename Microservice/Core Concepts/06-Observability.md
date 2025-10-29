# 06. Observability

## Three Pillars
- Logs: structured, with correlation IDs.
- Metrics: RED/USE metrics, SLOs, alerts.
- Traces: distributed tracing across services.

## OpenTelemetry (OTel)
- Standard SDKs for traces/metrics/logs.
- Export to systems like Jaeger, Tempo, Grafana, Datadog.

## What to Trace
- Incoming HTTP/gRPC requests.
- Outgoing calls and message publishing/consuming.
- DB queries (sampled).

## Dashboards
- Error rate, latency percentiles (p95/p99), throughput (RPS), saturation.

## Health and Readiness
- Liveness: is process alive.
- Readiness: can it serve traffic (dependencies OK?).
