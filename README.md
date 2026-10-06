# Santosh Kafle

I build containerised stacks on Linux and the plumbing around them: Compose, Nginx, CI pipelines that test the whole stack instead of one service, and monitoring defined in code. The repos below are where that work is public.

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

**[homelab-monitoring](https://github.com/santosh-kafle/homelab-monitoring)**: one-command monitoring for any Linux machine.

```
  node-exporter ───▶ prometheus ───▶ grafana
  PR ──▶ lint ──▶ install ──▶ uninstall ──▶ nothing left behind
```

Dashboards provisioned as code, with install, update and rollback scripts and versioned releases. Dependabot image bumps are tested in CI before merge.

## Production work

Shipped at [Quark InfoTech](https://kaflesantosh.com.np/cv), Lalitpur. All four are live in production.

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
```

---

santoshkafle.dev@gmail.com · [LinkedIn](https://www.linkedin.com/in/santosh-kafle-dev) · [kaflesantosh.com.np](https://kaflesantosh.com.np)
