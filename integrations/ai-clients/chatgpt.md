---
title: Connect ChatGPT
description: If your ChatGPT workspace permits custom MCP connections, enable Developer mode under Settings → Security and login.
---

If your ChatGPT workspace permits custom MCP connections, enable Developer mode under
**Settings → Security and login**. Open the ChatGPT Plugins page, add a connection named
Jointl, and enter the complete Streamable HTTP endpoint `https://mcp.join.tl/`. Review
the requested scopes and discovered tools, then complete Jointl authorization in the
browser. Follow the
[official OpenAI connection instructions](https://developers.openai.com/plugins/deploy/connect-chatgpt)
if the ChatGPT navigation changes.

The access request must target the MCP resource, not the REST audience. Available tools
reflect the authorizing member's active Jointl permissions.

Before a write, ChatGPT should present the preparation preview and ask for explicit
approval. Approval of one preview does not authorize a changed input or later action.
