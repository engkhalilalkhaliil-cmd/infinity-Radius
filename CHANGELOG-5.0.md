# InfinityNet ISP Ultimate 5.0

Developer: خليل الخليل | Khalil Al Khalil

## New in 5.0
- Enterprise+ API router.
- Staff authentication sessions with PBKDF2 password hashes.
- Customer portal token sessions and portal logout.
- IPAM allocation records.
- Daily traffic rollups and top-user analytics.
- Automated monthly invoice generation.
- Network TCP health monitoring and system events.
- Automated lifecycle and expiry synchronization with RADIUS.
- Internal notification processing queue.
- Automatic MariaDB backup service with 14-day retention.
- Customer notes, staff listing, settings and operational KPI reports.
- Invoice CSV export.
- Production-oriented FreeRADIUS SQL/MariaDB entrypoint validation.
- Versioned migration `05_enterprise_plus.sql`.

## Deployment-specific work
Real NAS shared secrets, MikroTik RouterOS API credentials, RADIUS CoA transport, SMS/WhatsApp/Telegram/email provider credentials and OLT/ONU vendor APIs must be configured and tested against the actual network.
