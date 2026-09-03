---
title: Errors, rate limits, and retries
description: REST failures use a consistent envelope with a stable machine code, a non-sensitive message, and the request ID.
---

REST failures use a consistent envelope with a stable machine code, a non-sensitive
message, and the request ID. Do not parse human-readable messages.

```json
{
  "error": {
    "code": "invalid-external-operation-input",
    "message": "The operation input is invalid."
  },
  "requestId": "example-request-002"
}
```

Requests are limited to one MiB. Current limits are 300 requests per minute per network,
120 read requests per minute per principal, 20 write requests per minute per principal,
and 120 OAuth requests per minute per network. Greenhouse has integration-specific
limits documented in its reference. On `429`, honor `Retry-After` and use exponential
backoff with jitter.

Retry reads after transient `429` or `5xx` failures. For writes, follow the operation's
`retrySafety`: idempotent operations may be replayed with the same identity; at-most-once
operations require outcome reconciliation and must not be blindly resubmitted. A
confirmation result with an unknown outcome must be reconciled before any new action.

Shared error examples are in `examples/shared/errors.json`; operation-specific replay,
conflict, permission, and asynchronous outcomes are linked from the operation examples.
