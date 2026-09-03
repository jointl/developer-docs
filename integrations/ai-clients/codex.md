---
title: Connect Codex
description: Connect Codex directly to Jointl MCP.
---

Connect Codex directly to Jointl MCP. Install the
[Jointl AI plugin](https://github.com/jointl/jointl-ai-plugin) to add five workflow
skills; MCP discovery still provides the tools and schemas available to your account.

Request a registered OAuth client ID from Jointl, then run:

```sh
codex mcp add jointl --url https://mcp.join.tl/ --oauth-client-id APPROVED_CLIENT_ID
codex mcp login jointl
codex mcp list
```

Register the exact loopback callback URL printed by `codex mcp add` for that client ID.
An unregistered client ID or callback cannot complete authorization. See the
[official Codex MCP configuration](https://learn.chatgpt.com/docs/extend/mcp) for CLI
and callback behavior.

Do not place credentials in plugin files, project instructions, or shell history.
