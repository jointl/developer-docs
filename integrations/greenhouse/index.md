---
title: Greenhouse integration
description: The Jointl Greenhouse integration receives selected recruiting webhooks and implements the Greenhouse assessment-partner API.
---

The Jointl Greenhouse integration receives selected recruiting webhooks and implements
the Greenhouse assessment-partner API. Its five Jointl endpoints are defined in the
[Greenhouse app endpoint reference](/rest-api/greenhouse-app-endpoints). Greenhouse Harvest is an
upstream dependency; use [Greenhouse's official Harvest API documentation](https://developers.greenhouse.io/harvest.html)
for those APIs.

## Install and configure

An authorized Jointl administrator installs Greenhouse, selects the allowed Jointl
companies, supplies the Greenhouse Harvest credential required by the integration, and
configures webhook and assessment credentials. Jointl provides an installation-specific
webhook URL, a webhook signing secret, the assessment API base URL, and an assessment
API key. Store all values as secrets.

Configure Greenhouse webhooks to send the supported actions and include both the
`Signature` header and a stable, unique `Greenhouse-Event-ID`. Configure the assessment
partner with HTTP Basic authentication using the installation API key.

## Event mapping

Job-created and job-deleted events synchronize the configured hiring Flow. Candidate
application creation or update and stage changes synchronize the Check. Hire, unhire,
reject, and unreject map to supported Check lifecycle statuses. Candidate deletion
archives the matching Check. Events outside the installation's allowed company scope
do not grant access.

## Assessment lifecycle

1. Greenhouse calls `list_tests` to list active, in-scope Jointl hiring Flows.
2. Greenhouse calls `send_test` with the selected Flow and candidate/application data.
3. Jointl returns a `partner_interview_id` for the created or reconciled request.
4. Greenhouse polls `test_status` with that opaque identifier.
5. Jointl reports `in_progress` or `complete`, a profile URL available to the installation,
   score, and metadata.
6. Greenhouse may notify `response_error`; Jointl records and acknowledges the notification.

Do not construct Jointl or Greenhouse identifiers. When the same installation submits
a matching candidate again, Jointl reuses the existing Check.

## Replay and troubleshooting

The signed webhook body and `Greenhouse-Event-ID` form the replay identity. An exact
duplicate is acknowledged. Reusing the ID with a different body returns `409`; an event
already processing returns `503`. Retry `429` and transient `5xx` responses with
backoff, preserving the exact body and event ID.

Webhook limits are 600 requests per minute per network and 300 per installation.
Assessment reads allow 120 requests per minute per installation; `send_test` allows 20.
Requests are limited to one MiB. `429` responses include `Retry-After`.
Send every POST body as a JSON object. Invalid or missing JSON returns `400`, and a
body above the size limit returns `413`; these responses do not echo request content.

For authentication failures, verify the installation is active and the correct secret
is configured. For a missing test, verify the Flow is active, is a hiring Flow, and is in
the installation company scope. For a missing status, verify that the returned opaque
`partner_interview_id` is unchanged.
