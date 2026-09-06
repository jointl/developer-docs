---
title: Zapier integration
description: Jointl's Zapier app is an approved OAuth client with event triggers, selectable searches, and Zapier-specific actions.
---

Jointl's Zapier app is an approved OAuth client with event triggers, selectable searches,
and Zapier-specific actions. The [Zapier component reference](/integrations/zapier/reference) lists every public
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

## Verification and public-profile results

**Verification Check Finished** runs when one verification check completes or fails.
**Public Profile Discovery Finished** runs when a new public-profile discovery run
completes or fails. Both triggers require **Run Result**: Completed (the default),
Failed, or Completed or Failed. Jointl applies this setting before sending a webhook
and when returning test records in the Zap editor.

The returned `run_status` distinguishes `completed` from `failed`. Completion describes
the run lifecycle; it does not mean that a person passed a verification. Use `run_id`
and, when present, `run_group_id` to identify the run. Use **Find Verification Results**
or **Find Public Profile Results** when a later step needs the current authorized
findings. Route findings to an authorized reviewer; do not use them to automate
employment decisions.

When using the subscription API, choose `verification.finished` or
`public_profiles.finished` and set `filters.runStatus` to `completed` or `failed`.
Omit that filter to receive both results. It is supported only for these two event types.
The former separate Completed and Failed trigger keys are replaced by the Finished
triggers; existing Zaps using those keys must select the replacement trigger and
their intended Run Result before being turned on again.

## Unique Source Key

Every write action requires a **Unique Source Key**. Map an immutable identifier for
the event or submission that caused the Zap run, rather than a reusable person's ID.
Reuse it only to retry the same logical action with the same payload. Jointl derives
a protected idempotency identity from it; a different payload under the same identity
is rejected as a conflict.

## Actions

### People searches and employee actions

**Find People** searches the same authorized, merged people as Jointl global search,
including permitted Checks, Employees, Talent Pool profiles, References, and Team
Members. It returns up to 30 ranked matches, not an exhaustive workspace export.
To keep all returned people, set **If multiple search results are found?** to
**Return all results as line items** in Zapier. Zapier supplies the grouped results
and count; use a line-item-aware action or Looping for the next step.

When an action needs one exact record, use **Add search step** in its Check,
Employee, or Talent field. These searches reject ambiguous matches rather than
choosing a person to modify. Select **Find Employee** and optionally enable
create-if-missing to create one only if no employee matches. Leave creation unchecked
when looking up an employee for a status change or another update.

Find Employee returns the current work record chosen by Jointl from the member's
visible positions, not simply the last work-history entry. Its Work Record ID
matches `profile.positionId` from `employees.get`; use the Work Record dropdown
in **Update Employee** when you intend to change a different position.

Single-record actions accept ordinary fields and return one resource. Bulk actions
accept up to 250 aligned line items and return batch outcomes and row-level errors.
Both follow Jointl's existing matching and permission rules. Single and bulk employee Tags fields accept
multiple values; commas inside one value are preserved as part of the tag name.

### Authorization

Zapier actions use `/api/v1/actions/execute`, which is available only to the official
Jointl Zapier app. Only operations that are non-destructive, idempotent, enabled for Zapier,
and available to the connected member can run this way. General clients must use
prepare, human approval, and confirm.

Use the [component reference](/integrations/zapier/reference) for every available trigger, search, action,
field, and sample result. The [webhook event delivery reference](/rest-api/zapier-webhook-event-delivery)
describes the notification envelope, hydration, and delivery behavior.
