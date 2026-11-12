---
description: List the files in a folder of the shared knowledge base, optionally only those of one OKF type (e.g. Skill)
argument-hint: <folder path> [type]
---

Use the `shared-layer` MCP server to list files. Arguments: $ARGUMENTS

The first argument is the folder path, e.g. `/progmbh/clients`. It is required: if it is missing, ask for it and stop. The optional second argument is an OKF type, e.g. `Skill`, `Person`, `Meeting`, `Decision`; types are case-sensitive, so capitalize the first letter as in those examples.

Call the `begin` tool first if you have not this session. Then:

- **No type**: call `list` with the path. Show its folders and files as a short list with each one's title and description. Do not open files or descend into folders unless asked; end by saying which folder to list deeper.
- **With a type**: call `find` with `type` and the path as `prefix`. It searches every folder below the path. Show the matching files as a short list with each one's path, title and description. For example, `/shared-layer:list_files / Skill` lists every skill you can use.
