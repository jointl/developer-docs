---
title: Choose an access method
description: Use a personal API key for a script acting as one Jointl member.
---

Use a personal API key for a script acting as one Jointl member. Use a service account
for an approved unattended integration with explicitly assigned companies and
permissions. Both are bearer credentials and must stay in a server-side secret store.

Use OAuth for registered client applications and MCP clients. Jointl supports the
authorization code flow with PKCE (`S256`) and rotating refresh tokens. Before starting
authorization, request a client ID from Jointl and register every redirect URI exactly.

Use MCP when a compatible AI client should discover and call Jointl tools. Use Zapier
for event-driven no-code workflows and actions approved for the Jointl Zapier app. Use
Greenhouse only for the supported recruiting webhook and assessment integration.

| Need | Recommended surface | Credential |
| --- | --- | --- |
| Personal server script | REST | Personal API key |
| Registered backend automation | REST | Service account key |
| User-authorized application | REST | OAuth with PKCE |
| AI assistant or agent | MCP | OAuth with PKCE |
| No-code workflow | Zapier | Zapier-managed OAuth installation |
| Greenhouse Recruiting | Greenhouse | Installation webhook secret and assessment API key |

Do not paste a Jointl API key into ChatGPT, Claude, Codex, or another hosted AI client.
Use the client's OAuth-based MCP connection instead.
