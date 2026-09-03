---
title: Jointl MCP
description: Jointl MCP uses Streamable HTTP at the root endpoint https://mcp.join.tl/.
---

Jointl MCP uses Streamable HTTP at the root endpoint `https://mcp.join.tl/`. It is an
MCP JSON-RPC service, not a collection of REST endpoints. Connect with OAuth and request
an access token whose resource/audience is exactly `https://mcp.join.tl`.

The server exposes read tools directly, prepare tools for protected writes, and
`jointl_confirm_action` for approved confirmations. Tool discovery is filtered by the
connected member's current permissions. Responses provide structured content plus a
text fallback for clients that do not consume structured output.

Start with [client setup](/integrations/ai-clients/index), then use the
[tool and skill reference](/jointl-mcp/reference) for schemas, annotations, and complete JSON-RPC
examples.

## Product access and documentation search

Jointl provides two MCP services with separate purposes:

| URL | Purpose | Access |
| --- | --- | --- |
| `https://mcp.join.tl` | Work with authorized Jointl workspace data and actions | Jointl OAuth; role, scope, company, and record permissions apply |
| `https://docs.join.tl/mcp` | Search this public developer documentation | Public, read-only documentation search; no workspace data or actions |

Connecting the documentation-search service does not grant access to Jointl. Use the
product endpoint whenever a client must list or change workspace data.
