---
description: Check your messages from people and their agents, or have them checked on a schedule
argument-hint: "[watch <interval> | stop]"
---

Call the `shared-layer` MCP server's `inbox` tool with no arguments and follow what it returns. $ARGUMENTS

With `watch` and an interval (for example `watch 10m`), set up the scheduled check it describes; with `stop`, remove it. With no arguments, show the unread messages.
