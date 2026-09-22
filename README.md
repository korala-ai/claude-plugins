# Korala for Claude Code

This directory is the root of Korala's Claude Code plugin marketplace. Publish
it as the public repository `korala-ai/claude-plugins` (the contents of this
directory become the repository root).

## Install

In Claude Code:

```
/plugin marketplace add korala-ai/claude-plugins
/plugin install korala@korala
```

Then run `/mcp`, choose **korala** and sign in. Korala's consent page asks what
Claude may do. Sending is off unless you tick it.

The plugin contains:

- `.mcp.json`: the hosted Korala MCP server (`https://api.korala.ai/mcp`,
  OAuth sign-in, no keys).
- `skills/korala-documents`: how to draft, prepare, send and track with those
  tools, and the no-account draft link for people who have not connected.

## Grok CLI

Grok CLI reads Claude Code plugins and marketplaces as they are:

```
grok plugin marketplace add korala-ai/claude-plugins
grok plugin install korala --trust
```

Grok keeps a plugin's MCP server off until you trust the plugin, hence
`--trust`. Then run `/mcps` in Grok, choose `korala` and sign in. If
`~/.grok/config.toml` already has a `korala` server (from
`grok mcp add`), that entry wins over the plugin's.

Checked with Grok CLI 1.0.40 and `HOME` pointed at a throwaway directory:
`grok plugin validate` accepts `plugins/korala`, and after the two commands
above `grok inspect` lists the `korala-documents` skill and the `korala` HTTP
server. The skill names both commands: `/mcp`, and `/mcps` in Grok.

## GitHub Copilot CLI

Copilot CLI also reads `.claude-plugin/marketplace.json`
(https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/plugins-marketplace):

```
copilot plugin marketplace add korala-ai/claude-plugins
copilot plugin install korala@korala
```

Not tried: Copilot CLI is not installed here.

## Try it locally

```
claude plugin validate integrations/claude-marketplace/plugins/korala
/plugin marketplace add ./integrations/claude-marketplace
```

## Keeping the helper in sync

`plugins/korala/skills/korala-documents/scripts/korala.mjs` is a copy of
`integrations/agent-skills/korala-documents/scripts/korala.mjs`.
`node scripts/package-integrations.mjs --check` fails when they differ.
