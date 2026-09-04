---
title: Zapier webhook event delivery
description: Jointl sends HTTPS webhook notifications to the allowlisted Zapier REST Hook URL registered for an active trigger.
---

Jointl sends HTTPS webhook notifications to the allowlisted
Zapier REST Hook URL registered for an active trigger. Each notification contains only
a durable event identifier.

## Delivery flow

1. The Jointl Zapier app registers its target through `POST /api/v1/webhook-subscriptions`.
2. Jointl sends the notification below when a matching event occurs. Exact duplicate delivery is possible.
3. Zapier acknowledges the notification promptly and passes its `id` to `events.get`.
4. Jointl returns the authorized event data using the connected member's current permissions.

## Notification payload

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `id` | string | Yes | Durable opaque event identifier used with events.get. |

### Example

```json
{
  "id": "event_example_01"
}
```

## Delivery behavior

- Delivery semantics: at-least-once notification with durable event hydration.
- Subscription lease: 21 days.
- Event hydration window: 30 days.
- Target: Target URL registered through POST /api/v1/webhook-subscriptions.

See the [Zapier integration guide](/integrations/zapier/index) for setup and retry-safe
automation behavior. Use the [AsyncAPI contract](/specs/asyncapi/zapier-events-v1.asyncapi.yaml)
for the machine-readable message definition and the [REST OpenAPI contract](/specs/openapi/jointl-api-v1.openapi.yaml)
for subscription and hydration endpoints.
