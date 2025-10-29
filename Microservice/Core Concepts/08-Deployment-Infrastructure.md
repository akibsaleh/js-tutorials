# 08. Deployment & Infrastructure

## Containers
- Pack each service as a container (Dockerfile).
- Keep images small. Use multi-stage builds.

## Orchestration
- Kubernetes or ECS to run many services.
- Service discovery via DNS. Ingress/Gateway for external traffic.

## Config and Secrets
- Use environment variables for config.
- Use secret managers (KMS, Vault, SSM, Kubernetes Secrets).

## CI/CD
- Automated tests and deployments.
- Blue/green or canary for safer releases.

## Infrastructure as Code
- Terraform, Pulumi, Helm, CDK.

## Local Dev
- Docker Compose for local databases and brokers.
