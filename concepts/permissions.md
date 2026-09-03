---
title: Permissions and company scope
description: Authentication never grants broader access than the connected Jointl member or service account has in Jointl.
---

Authentication never grants broader access than the connected Jointl member or service
account has in Jointl. An operation must pass all three checks:

1. The credential must contain the operation's OAuth/API scope.
2. The member must be allowed to use third-party apps.
3. The member's current role, company scope, sharing, creator rules, and record-level
   visibility must allow the requested data or mutation.

Discovery is permission-dependent. `GET /api/v1/operations`, MCP `tools/list`, and MCP
skill discovery show only currently available capabilities. Losing a permission can
remove an operation immediately and can invalidate an already prepared action before
confirmation.

Applications must not infer that an omitted record exists. When access is denied,
a not-found response does not reveal whether the record exists.
