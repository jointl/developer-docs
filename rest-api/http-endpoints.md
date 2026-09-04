---
title: HTTP endpoint map
description: The bundled OpenAPI contract contains exact parameters, schemas, authentication, and responses.
---

The bundled OpenAPI contract contains exact parameters, schemas, authentication, and
responses. This page provides the stable route map without duplicating those schemas.

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `GET` | `/oauth/authorize` | Start registered-client authorization with PKCE S256. |
| `POST` | `/oauth/token` | Exchange an authorization code or rotate a refresh token. |
| `POST` | `/oauth/revoke` | Revoke an access or refresh token. |
| `GET` | `/oauth/jwks` | Read OAuth signing keys. |
| `GET` | `/oauth/userinfo` | Read authorized OpenID claims. |
| `GET` | `/.well-known/oauth-authorization-server/oauth` | OAuth server discovery. |
| `GET` | `/.well-known/openid-configuration/oauth` | OpenID Provider discovery. |
| `GET` | `/.well-known/oauth-protected-resource/api/v1` | REST resource discovery. |
| `GET` | `/api/v1/operations` | List permission-available operations. |
| `POST` | `/api/v1/operations/{operationId}` | Call a read operation by ID. |
| `POST` | `/api/v1/actions/prepare` | Prepare a protected write. |
| `POST` | `/api/v1/actions/confirm` | Confirm an explicitly approved write. |
| `POST` | `/api/v1/actions/execute` | Execute a permitted action; official Jointl Zapier app only. |
| `POST` | `/api/v1/webhook-subscriptions` | Create or renew a hook subscription; official Jointl Zapier app only. |
| `DELETE` | `/api/v1/webhook-subscriptions/{id}` | Disable a hook subscription; official Jointl Zapier app only. |

The 31 concrete read URLs are listed individually in the [operation reference](/rest-api/operations)
and in OpenAPI. MCP uses its root Streamable HTTP endpoint and is documented separately.
