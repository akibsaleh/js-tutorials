# 10. Deployment

## Containerize
- Multi-stage Dockerfiles for each service.
- Pass config via env vars.

## Orchestrate
- Kubernetes manifests/Helm: Deployments, Services, Ingress, Secrets, ConfigMaps.

## Rollouts
- Blue/green or canary. Health probes required.

## Observability in Prod
- Central logs, metrics, traces with alerts.

## Security
- mTLS for service mesh (Istio/Linkerd) if needed.
- Secret rotation.
