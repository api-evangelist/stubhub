---
name: Search the StubHub event catalog
description: Search public events and drill into event and venue detail.
api: openapi/stubhub-catalog-openapi.yml
operations: [Events_SearchEvents, Events_GetEvents, Events_GetEvent, Venues_GetVenue]
---

# Search the StubHub event catalog

Public catalog data needs only the **application-only (client_credentials)** flow with the
`read:events` scope. Bearer token + valid `User-Agent`.

1. Search with `Events_SearchEvents`, or list with `Events_GetEvents`.
2. Page results with `page` / `page_size` (1-based, default 100) and sort with `sort=event_date,-price`.
3. Fetch a single event with `Events_GetEvent`; use sparse fieldsets (`fields=...&fields[venue]=city`).
4. Resolve the venue with `Venues_GetVenue`.
