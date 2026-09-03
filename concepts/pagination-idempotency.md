---
title: Pagination and idempotency
description: List operations return items, hasMore, and nextCursor.
---

List operations return `items`, `hasMore`, and `nextCursor`. Treat the cursor as opaque,
send it back unchanged, and stop when `hasMore` is false. Do not construct or edit a
cursor. Pagination reflects permissions at request time; records can move between pages
when the underlying workspace changes.

Confirmed actions use a server-issued confirmation token and enforce their declared
retry behavior. Tokens expire after five minutes. Completed confirmation receipts are
retained for 24 hours; Zapier action receipts are retained for 70 days.

Zapier actions derive idempotency from Source Event ID. Reuse the exact same Source
Event ID only when retrying the same logical upstream event. A different payload with
the same identity is a conflict. Do not use timestamps or random values when the source
system already supplies a durable event identifier.
