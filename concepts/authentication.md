---
title: Authentication and OAuth
description: REST accepts a Jointl personal API key, service-account API key, or OAuth bearer access token.
---

REST accepts a Jointl personal API key, service-account API key, or OAuth bearer access
token. Treat every credential as a bearer secret. MCP uses its own protected resource
and audience at `https://mcp.join.tl`; an access token issued for the REST resource is
not interchangeable with an MCP access token.

OAuth uses authorization code with PKCE (`S256`). The authorization server is
`https://api.join.tl/oauth`. Discovery, JWKS, UserInfo, token refresh, and revocation
are included in the OpenAPI contract. Request `offline_access` only when the client
needs a refresh token. Refresh tokens rotate; replace the stored token after every
successful refresh.

OAuth clients are registered by Jointl. Request a client identifier through your
Jointl contact and register every redirect URI exactly before starting authorization.

See [permissions](/concepts/permissions) for the authorization boundary applied after a
credential is authenticated.
