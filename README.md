# Santosh Kafle

DevOps engineer with a backend development background, based in Kathmandu. I work with Linux servers, containers, CI/CD pipelines and the databases behind production e-commerce platforms and REST APIs.

[kaflesantosh.com.np](https://kaflesantosh.com.np) · [CV](https://kaflesantosh.com.np/cv) · [LinkedIn](https://www.linkedin.com/in/santosh-kafle-dev) · santoshkafle.dev@gmail.com

```
$ whoami
santosh — backend dev turning devops engineer
location: kathmandu, nepal (UTC+5:45)
status:   open to devops roles
```

## Qualifications

- Linux server administration, hardening and incident response
- Containerised development and production environments with Docker and Docker Compose
- CI/CD pipelines with GitHub Actions: full-stack testing, image publishing to GHCR, automated dependency updates
- Nginx reverse proxy and internal network design
- Monitoring and observability with Prometheus and Grafana
- Database administration, migration and query optimisation (PostgreSQL, MySQL, MongoDB)
- Caching and search with Redis and Meilisearch
- DNS and email authentication on Cloudflare (SPF, DKIM, DMARC)
- REST API development with JWT authentication and rate limiting (Laravel, NestJS, Express)

## Projects

### [multi_service_deployment](https://github.com/santosh-kafle/multi_service_deployment)

[![CI](https://github.com/santosh-kafle/multi_service_deployment/actions/workflows/ci.yml/badge.svg)](https://github.com/santosh-kafle/multi_service_deployment/actions/workflows/ci.yml)

React, Express, MongoDB, Redis and an Nginx reverse proxy, run with Docker Compose. The pipeline tests the whole stack on every push and publishes the images that passed.

```
             :8080
  client ───▶ proxy ──┬──▶ web (react)
                      │
                      └──▶ api (express) ──┬──▶ mongodb
                                           └──▶ redis
            └──────────── internal network ─────────────┘

  push ──▶ init-env ──▶ build + up --wait ──▶ verify.sh (13 checks) ──▶ push to ghcr.io :<sha>
```

- Only the proxy publishes a port. Mongo and Redis sit on the internal network and both require a password.
- Healthchecks authenticate against the databases, and startup is gated on them: data stores first, then the API, then the proxy.
- The CI job builds all five containers on a clean VM with throwaway passwords and runs the same black-box tests used locally. Green commits on `master` push `api`, `web` and `proxy` to GHCR, tagged by commit SHA, so rolling back means picking an older SHA.
- Logs are capped per container, with a separate measured budget for Mongo, which writes about 300× more than the API. The whole stack has a 370 MB ceiling.
- Redis cache-aside with invalidation on write, separate liveness and readiness endpoints, non-root API container, pinned image tags.

### [prometheus-grafana-monitoring](https://github.com/santosh-kafle/prometheus-grafana-monitoring)

[![CI](https://github.com/santosh-kafle/prometheus-grafana-monitoring/actions/workflows/ci.yml/badge.svg)](https://github.com/santosh-kafle/prometheus-grafana-monitoring/actions/workflows/ci.yml)

Monitoring for any Linux machine, installed with one command and released with semantic versions (currently v0.3.0).

```
  node-exporter ───▶ prometheus ───▶ grafana
  (host metrics)     (15s scrape,     (dashboard provisioned
                      30d / 5 GB)      from files, read-only)

  PR ──▶ shellcheck + compose + promtool + json lint ──▶ install ──▶ uninstall ──▶ no leftovers
```

<img src="https://raw.githubusercontent.com/santosh-kafle/prometheus-grafana-monitoring/HEAD/docs/images/dashboard.png" alt="Grafana dashboard from prometheus-grafana-monitoring" width="720" />

- `install.sh` checks the machine first and lists anything missing along with how to fix it. It generates the Grafana password, starts the stack and waits until it's healthy. `update.sh` moves between releases and rolls back with `--to <version>`, and `uninstall.sh` can remove everything, including the data.
- CI lints every script and config file, then runs a full install and uninstall and fails if any volume is left behind.
- Dependabot opens a PR for each new Grafana, Prometheus or Node Exporter version, and CI tests it before merge.
- Host networking so Node Exporter reports the real network interfaces instead of the container's. Prometheus and Node Exporter always stay on localhost, and only Grafana can optionally be opened to the LAN.

## Sites I've worked on

At [Quark InfoTech](https://kaflesantosh.com.np/cv), Lalitpur. Intern from Jan to Mar 2025, then Backend Developer until Feb 2026.

| Site | My part | Stack |
|---|---|---|
| [zolpastore.com](https://zolpastore.com/) | E-commerce backend, caching and search | Laravel, PostgreSQL, Redis, Meilisearch, Docker, OAuth |
| [ultima.com.np](https://ultima.com.np/) | E-commerce with GETPAY payments | Laravel, MySQL, Docker |
| [singingbowlvillagenepal.com](https://singingbowlvillagenepal.com/) | PHP 8.4 / Laravel 12 build, PostgreSQL migration | Laravel, PostgreSQL, GETPAY |
| [iteam.com.np](https://iteam.com.np/) | Early backend setup and architecture | Laravel, PostgreSQL, Docker |

## Tools

```yaml
infra:    docker, compose, nginx, linux, bash, aws, cloudflare
ci/cd:    github actions, ghcr, dependabot, shellcheck
observe:  prometheus, grafana, node exporter
backend:  php, laravel, typescript, nestjs, node, express
data:     postgresql, mysql, mongodb, redis, meilisearch
learning: container orchestration, automated deployments
```
