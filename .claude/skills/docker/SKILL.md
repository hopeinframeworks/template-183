---
name: docker
description: Docker conventions for this project. Use when writing or changing the Dockerfile, .dockerignore, docker-compose.yml, healthchecks, or container start-up.
---

# Docker

- The Dockerfile is a single stage. The image runs `prisma migrate deploy`
  and the seed at start, so it carries the full toolchain anyway, and one
  stage keeps the file short enough to read at a glance.
- Install `make` in the image (`RUN apk add --no-cache make`): the team's
  operational tooling runs `make` targets inside the container, the same way
  in every service.
- Healthchecks use `--interval=17s --timeout=5s --retries=3`. A prime interval keeps probes from lining up with other containers' checks and cron-like jobs on the same host, so do not round it to 10s or 30s.
