# Erganis Companion — Implementation Plan

> **Status:** Not started.  
> **Product plan:** [§9 Companion](../../../docs/erganis-product-plan.md#9-companion) · **Index:** [IMPLEMENTATION-PLANS](../../../docs/IMPLEMENTATION-PLANS.md)

**GitHub:** `erganis-companion` · **Role:** Mobile app for field and on-the-go access.

---

## Overview

| Phase | Name | Delivers | Core deps |
|-------|------|----------|-----------|
| **CP0** | Scaffold | React Native app shell, TypeScript | — |
| **CP1** | Auth + API client | JWT via Core Public API; generated SDK subset | C8 Public API |
| **CP2** | Planner Tasks v1 | Daily todo check-off, project access | Studio S-P1 (backend) |
| **CP3** | Field surfaces | Additional Public API routes as modules expose them | C8 OpenAPI expansion |

---

## CP0 — Scaffold

**Layout:**

```
companion/
└── app/       # React Native application
```

**Stack:**

| Layer | Choice |
|-------|--------|
| Framework | React Native |
| Language | TypeScript |
| Maps | MapLibre RN — defer until Agora web map ships unless needed |
| API | Core Public API (generated TypeScript SDK subset) |

Companion is a **native mobile client** — separate from Studio Next.js. Business logic stays in Core/Studio modules.

---

## CP1 — Auth + API client

**Delivers:**

- `POST /auth/token` → JWT storage
- `Authorization: Bearer` on Public API calls
- `GET /public/v1/me` smoke path
- Generated client from `core/contracts/schemas/public/v1/`

**Core dep:** C8 JWT guard (API keys deferred).

---

## CP2 — Planner Tasks v1

**Primary v1 use case:** Planner **Tasks** — daily todo check-off, field access to projects.

**Studio dep:** S-P1 Planner backend must expose mobile-eligible Public API routes.

---

## CP3 — Expanded surfaces

**Later:** Additional Public API surfaces as Studio modules mark routes `x-audience: public` in OpenAPI.

---

## Principles

- No business logic in Companion — Core is system of record
- Shares contracts with platform; does not duplicate module handlers
- Online-first (offline deferred unless ranked later)
