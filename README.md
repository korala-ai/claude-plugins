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

## Try it locally

```
claude plugin validate integrations/claude-marketplace/plugins/korala
/plugin marketplace add ./integrations/claude-marketplace
```

## Keeping the helper in sync

`plugins/korala/skills/korala-documents/scripts/korala.mjs` is a copy of
`integrations/agent-skills/korala-documents/scripts/korala.mjs`.
`node scripts/package-integrations.mjs --check` fails when they differ.
