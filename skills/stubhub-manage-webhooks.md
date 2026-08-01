---
name: Manage StubHub webhooks
description: Register a webhook for sale/listing events and verify delivery.
api: openapi/stubhub-webhooks-openapi.yml
operations: [Webhooks_Post, Webhooks_Get, Webhooks_PingWebhook, Webhooks_Delete]
---

# Manage StubHub webhooks

Authenticate with OAuth2 (`write:webhooks` scope). Bearer token + valid `User-Agent`.

1. Create a subscription with `Webhooks_Post`, choosing a topic: `sales`, `provisional-sale`,
   `cancel-provisional-sale`, `sale-updates`, `sellerlisting-updates`, or `re-transfer-ticket`.
2. List your webhooks with `Webhooks_Get`.
3. Test delivery with `Webhooks_PingWebhook` (POST /webhooks/{webhookId}/ping).
4. Remove one with `Webhooks_Delete`.

StubHub delivers events as HTTP POST callbacks to your registered URL (no AsyncAPI document published).
