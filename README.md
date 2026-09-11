# Hi, I'm Santosh 👋

<a href="https://kaflesantosh.com.np">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=22&pause=1200&color=2F81F7&vCenter=true&width=520&lines=DevOps+Engineer+%26+Backend+Developer;Docker+%C2%B7+CI%2FCD+%C2%B7+Linux+%C2%B7+Nginx;Laravel+%C2%B7+NestJS+%C2%B7+PostgreSQL+%C2%B7+Redis;Open+to+DevOps+roles" alt="DevOps Engineer & Backend Developer" />
</a>

**DevOps Engineer & Backend Developer** in Kathmandu, Nepal. I run containerized environments, CI/CD pipelines and Linux servers behind high-traffic e-commerce platforms and REST APIs.

🟢 **Open to DevOps roles** · [Portfolio](https://kaflesantosh.com.np) · [CV](https://kaflesantosh.com.np/cv) · [LinkedIn](https://www.linkedin.com/in/santosh-kafle-dev)

<p>
  <img src="https://skillicons.dev/icons?i=docker,linux,nginx,githubactions,aws,cloudflare,prometheus,grafana,bash,git" alt="DevOps stack" /><br />
  <img src="https://skillicons.dev/icons?i=php,laravel,ts,nestjs,nodejs,express,postgres,mysql,mongodb,redis" alt="Backend stack" />
</p>

## ⚡ Highlights
- **Incident response:** cleaned up a compromised production host. Removed a cryptocurrency miner, rotated all environment credentials and hardened the server.
- **Database migration:** moved production databases from MySQL to PostgreSQL and improved query performance by **70%**
- **Performance:** built e-commerce backends with Redis caching and Meilisearch, keeping responses **under 300ms**
- **Infrastructure:** containerized dev and prod environments with Docker for parity, and managed Linux hosts and Cloudflare DNS (SPF, DKIM, DMARC)
- **APIs:** Laravel and Node.js services with JWT auth and rate limiting, serving 250+ daily API consumers

## 🚀 Projects

### [multi_service_deployment](https://github.com/santosh-kafle/multi_service_deployment)
Five containers behind one entry point: React, Express, MongoDB, Redis and an Nginx reverse proxy, orchestrated with Docker Compose.
- Only the proxy publishes a port. The API, database and cache sit on an internal bridge network.
- Redis cache-aside on reads with a 30s TTL, and key invalidation on writes
- Separate liveness (`/health`) and readiness (`/ready`) endpoints; readiness checks Mongo and Redis

### [prometheus-grafana-monitoring](https://github.com/santosh-kafle/prometheus-grafana-monitoring)
Node Exporter → Prometheus → Grafana, running in Docker.
- Datasources and dashboards provisioned entirely as code, so `git clone && docker compose up` gives a working dashboard
- Everything bound to `127.0.0.1`; secrets kept in a gitignored `.env`
- Tracks CPU, memory, disk, network, temperature, battery and resource pressure

## 🌐 Production Work
Built at [Quark InfoTech](https://kaflesantosh.com.np/cv):

| Site | What I did | Stack |
|---|---|---|
| [zolpastore.com](https://zolpastore.com/) | E-commerce backend with Redis caching and Meilisearch | Laravel · PostgreSQL · Redis · Meilisearch · Docker · OAuth |
| [ultima.com.np](https://ultima.com.np/) | E-commerce with GETPAY payment integration | Laravel · MySQL · Docker |
| [singingbowlvillagenepal.com](https://singingbowlvillagenepal.com/) | PHP 8.4 / Laravel 12 build with PostgreSQL migration | Laravel · PostgreSQL · GETPAY |
| [iteam.com.np](https://iteam.com.np/) | Early backend setup and architecture | Laravel · PostgreSQL · Docker |

## 💼 Experience
- **Backend Developer**, Quark InfoTech, Lalitpur · Apr 2025 – Feb 2026
- **Backend Developer Intern**, Quark InfoTech, Lalitpur · Jan – Mar 2025

## 🌱 Currently learning
Container orchestration and automated deployments.

## 📫 Reach me
santoshkafle.dev@gmail.com · [LinkedIn](https://www.linkedin.com/in/santosh-kafle-dev) · [kaflesantosh.com.np](https://kaflesantosh.com.np)
