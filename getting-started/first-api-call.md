---
title: Make your first REST request
description: The API origin is https://api.join.tl.
---

The API origin is `https://api.join.tl`. Jointl does not provide a public sandbox, so
use an authorized workspace and clearly synthetic test records. Obtain a personal
or service-account API key from your Jointl administrator, or use a registered OAuth
client.

First inspect the connected workspace and your current access:

```sh
curl --request POST \
  --url https://api.join.tl/api/v1/operations/workspace.get \
  --header 'Authorization: Bearer $JOINTL_CREDENTIAL' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

A successful response uses the common envelope:

```json
{
  "data": {
    "workspaceId": "workspace_example_01",
    "name": "Example Workspace",
    "member": {
      "id": "member_example_01",
      "name": "Ada Example",
      "roleId": "owner"
    },
    "companyScope": { "mode": "all" },
    "grantedPermissions": ["flows.view"]
  },
  "requestId": "server-request-id-example"
}
```

Jointl generates the `requestId`. Keep it when diagnosing or reporting a failed
request; clients do not supply it.

Logical reads are invoked with `POST` because operation inputs are typed JSON objects.
Discover available operations at `GET /api/v1/operations`; the response is filtered by
the credential's active scopes and the member's Jointl permissions.
