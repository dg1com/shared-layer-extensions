---
description: Load a skill from the shared knowledge base and follow it for the rest of this session
argument-hint: <skill name or path>
---

Use the `shared-layer` MCP server to load the skill: $ARGUMENTS

Call the `begin` tool first if you have not this session. Its `# Skills` section lists the skills you can use, by area, with each one's path. Pick the one named above: by its name, or by its path if one is given. If two areas have a skill with that name, ask the user which one. If none matches or the name is empty, show the list of skills and ask which to load.

`read` the skill's `SKILL.md` and follow it for the rest of this session. Read the helper files it links to only when you need them. Tell the user in one line which skill you loaded, with its path.
