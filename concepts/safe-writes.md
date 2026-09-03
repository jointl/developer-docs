---
title: Safe writes and human approval
description: "Every general REST and MCP write follows prepare, approve, and confirm:"
---

Every general REST and MCP write follows prepare, approve, and confirm:

1. Prepare the exact operation and input.
2. Show the returned preview to the human who requested it.
3. Obtain explicit approval for that exact preview.
4. Confirm once with the issued token before its five-minute expiry.

Changing the target or input requires a new preparation. Re-check the response because
current permissions and record state are evaluated again at confirmation. Destructive
actions and at-most-once actions must never be retried speculatively.

Zapier's `/actions/execute` path is available only to the installed Zapier app and its
approved actions. It does not turn arbitrary writes into unattended actions; the
installation, operation, permissions, idempotency identity, and safety classification
must all qualify.

The Arazzo workflows mark the approval checkpoint with
`x-jointl-human-approval-required: true`.
