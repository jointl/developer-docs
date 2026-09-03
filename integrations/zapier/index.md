---
title: Zapier integration
description: Jointl's Zapier app is an approved OAuth client with event triggers, selectable searches, and Zapier-specific actions.
---

Jointl's Zapier app is an approved OAuth client with event triggers, selectable searches,
and Zapier-specific actions. The [Zapier reference](/integrations/zapier/reference) lists every public
component and its fields.

## Event delivery

Each trigger creates a webhook subscription with a 21-day lease. The Zapier app renews
the subscription while the Zap remains active and deletes it when unsubscribed. Jointl
delivers only an opaque JSON object containing the durable event ID:

```json
{ "id": "event_example_01" }
```

The app hydrates that ID through `events.get` using its installation credential. Events
are retained for 30 days. Consumers must not treat the hook body as the business event,
guess entity data from the ID, or cache it beyond the workflow's needs.

## Source Event ID

Every action requires a Source Event ID. Use the immutable identifier from the system
that caused the Zap run—for example, an order ID plus event type. Reuse it only to retry
the same logical action with the same payload. Jointl derives a protected idempotency
identity from it; a different payload under the same identity is rejected as a conflict.

## Actions

Zapier actions use `/api/v1/actions/execute`, which is available only to the installed
Zapier app. Only operations that are non-destructive, idempotent, approved for Zapier,
and available to the connected member can run this way. General clients must use
prepare, human approval, and confirm.

Use the [component reference](/integrations/zapier/reference) for every available trigger, search, action,
field, and sample result. The [event contract](/specs/asyncapi/zapier-events-v1.asyncapi.yaml)
describes subscription delivery and hydration.
