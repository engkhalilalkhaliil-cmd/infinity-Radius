> **InfinityNet ISP Ultimate 15.0 — AI Autonomous NOC** | خليل الخليل | Khalil Al Khalil

# InfinityNet ISP Ultimate 5.0

**Developer: خليل الخليل | Khalil Al Khalil**

InfinityNet is an ISP operations platform built around FreeRADIUS, MariaDB and a FastAPI management layer. It covers subscriber CRM, PPPoE/RADIUS authorization and accounting, plans, subscriptions, billing, payments, vouchers, CoA queue, NOC/network health, inventory, technician orders, tickets, branches, RBAC-ready staff, customer portal sessions, IPAM, usage analytics, webhooks/events, reports, audit logs and automatic database backups.

## Start

```bash
cp .env.example .env
# replace every CHANGE_THIS value with long random secrets
docker compose up -d --build
```

Dashboard: `http://SERVER:8080`  
API docs: `http://SERVER:8080/docs`  
Health: `http://SERVER:8080/health`

## Staff

Create a staff account from a trusted administration shell:

```bash
DB_HOST=127.0.0.1 DB_USER=radius DB_PASSWORD=... DB_NAME=radius python3 ops/create_staff.py
```

## Important production notes

* Configure real MikroTik/NAS clients and unique RADIUS shared secrets in `freeradius/clients.conf`.
* Configure the FreeRADIUS SQL module for MariaDB and test with `radiusd -XC` / `radiusd -X` before production.
* External SMS/WhatsApp/Telegram/email delivery is opt-in and requires provider credentials; the platform queues messages without pretending that a provider is connected.
* Test CoA/Disconnect against a staging MikroTik before using it on live subscribers.
* Put the dashboard behind HTTPS and a reverse proxy in production.
* The included FreeRADIUS tree is a development branch; use a supported release for production after compatibility testing.


## Global Platform 7.0
The platform now includes a multi-tenant foundation, event bus, safe automation, versioned workflows, field service, knowledge base, security events, anomaly detection, churn scoring, wallets/referrals, change management, integration registry, IPv6/DNS foundations, public status portal, and a customer portal.

## 8.0 API
The 8.0 API is available under `/api/v8`. Admins can create scoped API keys from `POST /api/v8/api-keys`; keys are returned once and should be stored in a secrets manager. Integration clients use `X-API-Key` and scopes such as `read`, `write`, `billing`, `customers`, `network`, `webhooks`, or `*`.


## Telegram Operations Bot
See `docs/TELEGRAM-BOT.md`. Configure `TELEGRAM_BOT_TOKEN`, `TELEGRAM_ADMIN_IDS`, and `TELEGRAM_CHAT_IDS`.

## GitHub Codespaces test

1. Push this project to a GitHub repository.
2. Open the repository and choose **Code → Codespaces → Create codespace on main**.
3. Wait for the container to finish creating.
4. In the Codespaces terminal run:

```bash
docker compose up -d --build
```

5. Open the forwarded **8080** port to access InfinityNet Manager.
6. Check health with `curl http://localhost:8080/ready`.

For a first test, the included `.env.example` is copied to `.env` automatically. Replace its placeholder secrets before any real deployment.

> The Codespaces setup is for development/testing. Do not expose the database, RADIUS, Grafana, or management API publicly without proper authentication, firewalling and TLS.
