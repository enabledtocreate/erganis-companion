# Erganis Companion

**Mobile app** — Companion for Erganis Platform (designer or client on the go).

## Structure

- **`app/`** — Main mobile application
- **`shared/`** — Shared logic, API client, types

Consumes **Core Public API** only (URL or generated SDK subset).

## Dependencies

- **Erganis Core Public API** — no direct Core repo reference in production

## Environment variables

Copy `.env.example` to `.env`.

| Variable | Required | Description |
|----------|----------|-------------|
| `API_BASE_URL` | Yes | Core Public API endpoint |
| `API_TIMEOUT` | No | Request timeout ms (default 30000) |
| `AUTH_ENABLED` | No | Enable auth (default true) |
| `NODE_ENV` | No | development \| production |
| `LOG_LEVEL` | No | debug \| info \| warn \| error |

## GitHub

**Owner:** [enabledtocreate](https://github.com/enabledtocreate)  
**Repo:** `erganis-companion`
