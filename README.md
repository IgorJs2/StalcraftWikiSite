# Stalcraft Wiki

The most visited fan site for the game STALZONE (formerly STALCRAFT): item database, interactive map, auction price history, calculators and player accounts.

[stalzone.wiki](https://stalzone.wiki) (formerly stalcraft.wiki; the game was renamed from STALCRAFT to STALZONE) · [Discord](https://discord.gg/YGnhb2UD9E)

> Source code is private (Stalcraft-Dev-Team). This repository describes the project and my role.

## At a glance
| | |
|---|---|
| My role | Co-founder and full-stack developer, Stalcraft LAB, Apr 2023 – Oct 2026 |
| Traffic | 5–7k concurrent users · 40–50k per day · ~1M unique visitors last year |
| Team | Two co-founders, no managers: we plan, code, release and run the infrastructure ourselves |
| My code | ~2,000 commits across 35 repositories (wiki, marketplace, parsers, bots) |

![screenshot](https://github.com/user-attachments/assets/faaa18ba-4cea-4e94-9a3b-fb9166ec0517)

## What I built
- Frontend: Next.js with React, TanStack Query, Zustand, Tailwind and Radix UI.
- Backend: Django REST Framework with PostgreSQL and pgbouncer.
- Item database, interactive Leaflet map (markers, areas, shapes), auction and price history, orders, comments, and a barter calculator that uses live auction prices.
- Accounts: profiles, public pages, Discord, EXBO and Telegram linking, deal notifications.
- Collaborative editing with TipTap and Yjs, Sentry tracing, Umami analytics, horizontal-scaling tests for Next.js.

![screenshot](https://github.com/user-attachments/assets/cb6c9d4a-429f-435b-915e-d9ced496d57f)

## Data pipeline
- Game-data parser: items, barter recipes, icons uploaded to a CDN, our own item catalog with stable IDs.
- EXBO API parser (NestJS): auction lots, operations and player activity, with a proxy pool, token rotation, sharded instances and Prometheus metrics.
- 3-broker Kafka cluster → replicated ClickHouse with Keeper; a ClickHouse sink that isolates bad rows; a BullMQ metrics aggregator.
- Discord trade-post collection with item recognition in text and images (Python, spaCy, OCR, Redis worker pool), streamed into Kafka and shown on the site.

## Infrastructure and operations
- Docker Compose on local, dev, staging and production; deploys through GitHub Actions; moved to a dedicated server in July 2024.
- nginx, Angie, Caddy and Cloudflare in front of the services; SSL.
- Prometheus, Grafana, Loki, Alertmanager, cAdvisor and Sentry across all services.
- Internal tools (Jira, Confluence, Portainer, Grafana, pgAdmin) reachable only over VPN; CrowdSec; a secrets vault.
- S3 backups and incident response, including recovery from a failed ClickHouse disk in October 2026 with a written postmortem.

## Tech stack
| Area | Stack |
|---|---|
| Frontend | Next.js, React, TypeScript, TanStack Query, Zustand, Tailwind, Radix UI, Leaflet, TipTap, Yjs |
| Backend | Django, Django REST Framework, gunicorn; NestJS for parsers |
| Data | PostgreSQL, pgbouncer, ClickHouse, Redis, Kafka, BullMQ |
| ML | spaCy, OCR |
| Infrastructure | Docker, GitHub Actions, nginx, Angie, Caddy, Cloudflare, Portainer, CrowdSec, VPN |
| Observability | Sentry, Prometheus, Grafana, Loki, Alertmanager, Umami |

![](https://github.com/user-attachments/assets/d1f48f54-0bc8-474c-aab3-48f32d454062)
![](https://github.com/user-attachments/assets/f1fa349c-1949-4dff-876c-80361729f49c)
