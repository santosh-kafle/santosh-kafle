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
- CI/CD pipelines with GitHub Actions
- Nginx reverse proxy and internal network design
- Monitoring and observability with Prometheus and Grafana
- Database administration, migration and query optimisation (PostgreSQL, MySQL, MongoDB)
- Caching and search with Redis and Meilisearch
- DNS and email authentication on Cloudflare (SPF, DKIM, DMARC)
- REST API development with JWT authentication and rate limiting (Laravel, NestJS, Express)

## Projects

**[multi_service_deployment](https://github.com/santosh-kafle/multi_service_deployment)**: five-service stack behind a single Nginx entry point.

```
              :80
  client ───▶ nginx ──┬──▶ react
                      │
                      └──▶ express ──┬──▶ mongodb
                                     └──▶ redis
            └──────── internal bridge network ────────┘
```

Only Nginx publishes a port; the API, database and cache can't be reached from outside. Reads go through Redis (cache-aside, 30s TTL) and writes invalidate the key. `/health` and `/ready` are separate, and readiness actually checks that Mongo and Redis answer.

**[prometheus-grafana-monitoring](https://github.com/santosh-kafle/prometheus-grafana-monitoring)**: host metrics, set up entirely as code.

```
  node-exporter ───▶ prometheus ───▶ grafana
  (host metrics)     (scrape+store)   (provisioned dashboards)
```

`git clone && docker compose up` and you have a working dashboard. It tracks CPU, memory, disk, network, temperature, battery and pressure stalls. Everything binds to `127.0.0.1` and secrets stay in a gitignored `.env`.

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
infra:    docker, compose, nginx, linux, bash, github actions, aws, cloudflare
observe:  prometheus, grafana, node exporter
backend:  php, laravel, typescript, nestjs, node, express
data:     postgresql, mysql, mongodb, redis, meilisearch
learning: container orchestration, automated deployments
```
