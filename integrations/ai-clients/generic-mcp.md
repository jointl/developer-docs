---
title: Connect a generic MCP client
description: The client must support MCP Streamable HTTP, OAuth protected-resource discovery, PKCE S256, and the JSON-RPC initialize, tools/list, and tools/call methods.
---

The client must support MCP Streamable HTTP, OAuth protected-resource discovery, PKCE
`S256`, and the JSON-RPC `initialize`, `tools/list`, and `tools/call` methods. Start at
`https://mcp.join.tl/`; OAuth metadata is discovered from
`https://mcp.join.tl/.well-known/oauth-protected-resource`.

Request only the scopes needed for the intended tools. Respect MCP error objects and
the structured result schema. The `io.modelcontextprotocol/skills` capability is a
Jointl-advertised extension; clients may ignore it when unsupported.
