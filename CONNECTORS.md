# Notion (required)

**Notion is required** for this plugin. It stores CV versions, LinkedIn profile iterations, post drafts, and profile notes. Without it, the plugin cannot persist your work between sessions.

## Configure MCP during the chat

The assistant will **ask you to set up Notion MCP** when tools are not available or when you first need persistence.

### Claude Code

1. Run **`/mcp`** in the chat.
2. Use the **Notion** entry from this plugin’s `.mcp.json` (`https://mcp.notion.com/mcp`), or add it if it is missing.
3. Complete **OAuth** in the browser and grant access to your Notion workspace.

### CLI alternative

```bash
claude mcp add --transport http notion https://mcp.notion.com/mcp
```

Then return to the chat and confirm the connection so the assistant can verify with a Notion tool (e.g. search).

## After MCP works

Ask the assistant to run **Notion setup** (or say: “set up my Notion workspace”) so it can create `[YourName] - LinkedIn & CV Builder` and the databases under it.

## What gets stored

| Category | Purpose |
| -------- | ------- |
| Notion   | CV versions, posts, profile drafts, strategy / context notes |

## Other environments

If you use a client that supports **Notion connectors** instead of MCP, connect Notion there; the assistant should still verify access before saving.
