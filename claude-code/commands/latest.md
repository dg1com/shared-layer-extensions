---
description: List the latest changes in the shared knowledge base, by default from the last day
argument-hint: "[how far back, e.g. 7d, 2 weeks, 12h]"
---

Use the `shared-layer` MCP server to list the latest changes. Arguments: $ARGUMENTS

The optional argument is how far back to look, e.g. `7d`, `7 days`, `2 weeks` or `12h`. Without it, look back 1 day. Turn it into a number of days (`2 weeks` is 14, `12h` is 0.5).

Call the `begin` tool first if you have not this session. Then call `changes_since` with `days` and no cursor. If it returns any changes, call it again with the same `days` and the returned `cursor`, and repeat until the cursor stops changing.

Show the changes newest first, grouped by area, as a short list: each file or folder's path, what happened (its `op`, e.g. created, updated, moved, deleted, restored), who made it (person, and bot if any), when, and the change message. Changes of one batch belong together. Do not open the files unless asked. If nothing changed in that time, say so.
