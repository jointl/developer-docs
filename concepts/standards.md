---
title: Machine-readable contracts
description: Use the downloadable contracts to generate clients, validate payloads, configure API tools, or index the documentation for an AI system.
---

Use the downloadable contracts to generate clients, validate payloads, configure API
tools, or index the documentation for an AI system. Each specification is a standalone
bundle with no unresolved external references.

| Contract | Format | Purpose |
| --- | --- | --- |
| [Jointl REST API and OAuth](/specs/openapi/jointl-api-v1.openapi.yaml) | OpenAPI 3.1.2 | HTTP endpoints, security schemes, operation schemas, and examples |
| [Greenhouse integration API](/specs/openapi/greenhouse-v1.openapi.yaml) | OpenAPI 3.1.2 | Webhook and assessment-partner endpoints |
| [Zapier event delivery](/specs/asyncapi/zapier-events-v1.asyncapi.yaml) | AsyncAPI 3.0 | Subscription delivery and event hydration |
| [Jointl workflows](/specs/arazzo/jointl-workflows-v1.arazzo.yaml) | Arazzo 1.1 | OAuth, reads, protected writes, and Zapier event workflows |
| [Operation schemas](/specs/json-schema/jointl-operations-v1.schema.json) | JSON Schema 2020-12 | Reusable input and result data models |
| [MCP tool catalog](/artifacts/mcp/tools-list.json) | MCP JSON-RPC | Tool discovery, annotations, and schemas |

The HTTP contracts use [OpenAPI 3.1.2](https://spec.openapis.org/oas/v3.1.2.html),
shared data models use [JSON Schema 2020-12](https://json-schema.org/draft/2020-12),
and multi-step flows use [Arazzo 1.1](https://spec.openapis.org/arazzo/v1.1.0.html).
MCP examples follow the [MCP base protocol](https://modelcontextprotocol.io/specification/2025-11-25/basic)
and [tool model](https://modelcontextprotocol.io/specification/2025-11-25/schema).

The distribution also provides an [RFC 9727](https://www.rfc-editor.org/rfc/rfc9727.html)
API catalog plus `llms.txt` and `llms-full.txt` indexes. Treat those indexes as
navigation aids; use OpenAPI, JSON Schema, and MCP discovery for exact field definitions.
