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

**[prometheus-grafana-monitoring](https://github.com/santosh-kafle/prometheus-grafana-monitoring)**: one-command monitoring for any Linux machine.

```
  node-exporter ───▶ prometheus ───▶ grafana
  PR ──▶ lint ──▶ install ──▶ uninstall ──▶ nothing left behind
```

Dashboards provisioned as code, with install, update and rollback scripts and versioned releases. Dependabot image bumps are tested in CI before merge.

## Tools

```yaml
infra:    docker, compose, nginx, linux, bash, aws, cloudflare
ci/cd:    github actions, ghcr, dependabot, shellcheck
observe:  prometheus, grafana, node exporter
backend:  php, laravel, typescript, nestjs, node, express
data:     postgresql, mysql, mongodb, redis, meilisearch
```

---

More at [kaflesantosh.com.np](https://kaflesantosh.com.np).
