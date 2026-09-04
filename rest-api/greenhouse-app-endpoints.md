---
title: Greenhouse endpoint overview
description: The 5 endpoints in this reference are available only to a provisioned Jointl Greenhouse installation.
---

The 5 endpoints in this reference are available only to a
provisioned Jointl Greenhouse installation. They are not general-purpose Jointl API
endpoints.

## Endpoint groups

| Group | Purpose | Authentication |
| --- | --- | --- |
| Webhook delivery | Receive supported Greenhouse Recruiting events. | Installation webhook signature and durable event ID |
| Assessment API | List tests, create or reconcile an assessment, read its status, and acknowledge response errors. | Installation API key with HTTP Basic authentication |

The endpoint pages contain the exact parameters, schemas, examples, status
codes, and retry behavior. Download the [Greenhouse OpenAPI contract](/specs/openapi/greenhouse-v1.openapi.yaml)
for code generation and validation, or use the [Greenhouse integration guide](/integrations/greenhouse/index)
for installation, event mapping, and assessment lifecycle guidance.
