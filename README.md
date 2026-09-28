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

**[multi_service_deployment](https://github.com/santosh-kafle/multi_service_deployment)**: React, Express, MongoDB, Redis and Nginx on Docker Compose, tested and shipped by CI.

```
             :8080
  client ───▶ proxy ──┬──▶ web (react)
                      └──▶ api (express) ──┬──▶ mongodb
                                           └──▶ redis
  push ──▶ build ──▶ verify (13 checks) ──▶ ghcr.io :<sha>
```

Only the proxy is exposed, the databases need passwords, and healthchecks gate startup. Every green commit publishes its images to GHCR, so rolling back is just an older SHA.

**[prometheus-grafana-monitoring](https://github.com/santosh-kafle/prometheus-grafana-monitoring)**: one-command monitoring for any Linux machine.

```
  node-exporter ───▶ prometheus ───▶ grafana
  PR ──▶ lint ──▶ install ──▶ uninstall ──▶ nothing left behind
```

Dashboards provisioned as code, with install, update and rollback scripts and versioned releases. Dependabot image bumps are tested in CI before merge.

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
