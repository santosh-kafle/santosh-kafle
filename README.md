# Santosh Kafle

I started out writing Laravel and Node APIs for e-commerce shops in Kathmandu. Over time I became the person who got pulled in when a server misbehaved, a deploy broke, or the database got slow, and I realised I liked that part of the job more than the features. So now I'm moving into DevOps full-time.

[kaflesantosh.com.np](https://kaflesantosh.com.np) · [CV](https://kaflesantosh.com.np/cv) · [LinkedIn](https://www.linkedin.com/in/santosh-kafle-dev) · santoshkafle.dev@gmail.com

```
$ whoami
santosh — backend dev turning devops engineer
location: kathmandu, nepal (UTC+5:45)
status:   open to devops roles
```

## Some things I've dealt with in production

A server I looked after got compromised and was quietly mining crypto. I tracked down the miner, removed it, rotated every credential in the environment and hardened the box so the same door couldn't be used twice.

We were outgrowing MySQL, so I moved the production databases to PostgreSQL. Queries got about 70% faster.

One e-commerce backend had to stay quick under real traffic. Redis caching and Meilisearch kept responses under 300ms.

I put dev and prod into Docker so "works on my machine" stopped being an argument, and handled the Linux hosts and Cloudflare DNS, including the SPF, DKIM and DMARC records nobody else wanted to touch.

The APIs I built in Laravel and Node.js use JWT auth and rate limiting, and serve 250+ consumers a day.

## Projects

**[multi_service_deployment](https://github.com/santosh-kafle/multi_service_deployment)**: five containers behind one door.

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

`git clone && docker compose up` and you have a working dashboard with no clicking around in the UI. It tracks CPU, memory, disk, network, temperature, battery and pressure stalls. Everything binds to `127.0.0.1` and secrets stay in a gitignored `.env`.

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
