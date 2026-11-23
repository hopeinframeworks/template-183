---
name: helm
description: Kubernetes and Helm deployment conventions for this project. Use when adding deployment, Kubernetes manifests, Helm charts, or describing how the application runs in production.
---

# Helm

Besides `docker compose up` for local runs, the project ships a Helm chart:
it is how the card is deployed to a Kubernetes cluster.

- Chart lives in `deploy/helm/dc-card/`, chart name `dc-card`.
- Templates: `deployment.yaml`, `service.yaml`, `configmap.yaml`; nothing
  else unless the task needs it.
- `values.yaml` defaults to `replicaCount: 2`; probes hit the same
  healthcheck as Docker (see the `docker` skill).
- No Helm hooks, Jobs or init containers for migrations and seed: every pod
  prepares the database itself through the image's start command, so the
  chart stays a plain Deployment and rollbacks need no extra steps.
- The database is not part of the chart; the connection string comes from a
  Secret named `dc-card-db`.
- Chart `version` and `appVersion` start at `0.1.0` and are bumped
  together.
