# Shared Layer for Grok Bot

Grok Bot connects only to remote MCP servers, by URL. The Shared Layer server is one: no package to install, just connect it and give the bot the skill.

Grok Bot is in beta and xAI documents little of this yet. The steps below follow xAI's [team and enterprise controls](https://docs.x.ai/grok-bot/teams-and-enterprises); the sign-in and the skill install are not verified yet.

## 1. Allow the server (team admins)

On a team plan, members can only add apps an admin allows. In the Grok Bot dashboard, open **Plugins & MCPs** and allow:

```
https://swissai.sharedlayer.ai/mcp?client=grok-bot
```

On an enterprise plan, also add it to the MCP allowlist and allow outbound requests to `swissai.sharedlayer.ai` in the network controls.

## 2. Connect it

In Grok Bot, open **Connect apps**, add a custom MCP server with the URL above, and sign in.

- **OAuth (expected):** the server tells Grok Bot where to sign in. You land on the Shared Layer sign-in page, sign in with your account and allow access. The bot then acts as one of your bots, named after the app, with the access you grant it.
- **API key (fallback):** if Grok Bot asks for a token or lets you set a header instead, create a personal API key on your account page (`https://swissai.sharedlayer.ai/account`) and send it as `Authorization: Bearer <key>`. Never paste the key into a chat.

## 3. Give the bot the skill

The skill tells the bot when to use the knowledge base (recall, remember, save) and to call `begin` first.

- If Grok Bot takes skills, add [`skills/shared-layer/SKILL.md`](skills/shared-layer/SKILL.md). It uses the Agent Skills format: a folder with a `SKILL.md`.
- Otherwise, paste the block from [`codex/AGENTS.md`](../codex/AGENTS.md) into the bot's custom instructions.

The server also sends its own instructions to every client, so the bot gets the basics even without either.

## Check it

Ask the bot: "What areas does the shared knowledge base have?" It should call `begin` and list the areas you can access.

## If sign-in fails

- **Sign-in succeeds, then every call fails with 401:** the access token wasn't issued for `https://swissai.sharedlayer.ai/mcp`. Grok Bot has to send that URL as the OAuth `resource` parameter. Use the API key fallback, and tell us so we can look at the server logs.
- **Registration fails:** the server accepts dynamic client registration and client ID metadata documents. Note the error Grok Bot shows and tell us.

`skills/shared-layer/SKILL.md` is a copy of [`claude-code/skills/shared-layer/SKILL.md`](../claude-code/skills/shared-layer/SKILL.md): change both together.
