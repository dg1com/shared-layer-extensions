# Shared Layer extensions

Packages that connect coding agents to the Shared Layer knowledge base, an MCP server at `https://swissai.sharedlayer.ai/mcp`. Every package tells the agent to read `/skills/okf/SKILL.md` from the server first. That skill lives in the knowledge base, so changing it updates every agent without a new release here.

| Agent | Folder | Install |
| --- | --- | --- |
| Claude Code | [`claude-code`](claude-code) | plugin, see below |
| Gemini CLI | [`gemini-cli`](gemini-cli) | extension, see below |
| Codex | [`codex`](codex) | config snippet, see below |
| VS Code (Copilot) | [`vscode`](vscode) | config snippet, see below |

claude.ai and the Claude apps need no package: Settings → Connectors → Add custom connector, name it "Shared Layer" and enter `https://swissai.sharedlayer.ai/mcp`.

## Claude Code

```sh
claude plugin marketplace add dg1com/shared-layer-extensions
claude plugin install shared-layer@shared-layer
```

Then run `/mcp`, pick `shared-layer` and sign in. The plugin bundles the MCP server, the skill and the `/shared-layer:list_knowledge`, `/shared-layer:recall` and `/shared-layer:retain` commands. Update with `claude plugin update shared-layer@shared-layer`, or turn on auto-update for the marketplace in `/plugin`. Bump `version` in `claude-code/.claude-plugin/plugin.json` whenever the plugin's files change, or users will not see the change.

## Gemini CLI

Copy `gemini-cli` somewhere and run `gemini extensions install <path>`, then sign in when the server asks. Gemini reads `gemini-extension.json` from the root of what it installs, so installing straight from this repo's URL will not find it.

## Codex

Create a personal API key on your account page, then:

```sh
export SHARED_KNOWLEDGE_KEY=...   # in your shell profile
codex mcp add shared-layer --url "https://swissai.sharedlayer.ai/mcp?client=codex" \
  --bearer-token-env-var SHARED_KNOWLEDGE_KEY
```

Add the lines from [`codex/AGENTS.md`](codex/AGENTS.md) to `~/.codex/AGENTS.md` or a repository's `AGENTS.md`.

## VS Code (Copilot)

Add [`vscode/mcp.json`](vscode/mcp.json) to your user MCP configuration (Command Palette → "MCP: Open User Configuration"). VS Code asks for a personal API key on first use. Add the lines from [`codex/AGENTS.md`](codex/AGENTS.md) to `.github/copilot-instructions.md` or the repository's `AGENTS.md`.
