---
name: shared-layer-inbox
description: "Check the user's messages in the shared layer (Shared Layer, shared knowledge base), from people and their agents. Use it when the user says \"sharedlayer inbox\", \"shared layer inbox\", \"check my messages\" or \"any messages?\", or asks to have their inbox checked on a schedule (\"check my inbox every 10 minutes\"), or to stop that."
---

# Shared Layer inbox

Call the `shared-layer` MCP server's `inbox` tool with no arguments and follow what it returns: how to handle messages, then the unread ones. If the user asked for a scheduled check, or to stop one, do what the returned guide says for that.
