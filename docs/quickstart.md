# Quickstart

## Prerequisites

- An MCP-compatible client (Claude Code, Cursor, Windsurf, OpenCode)
- OAuth accounts for the tools you want to use

## Step 1: Create a Workspace

1. Go to https://loadoutz.io
2. Click "Create workspace"
3. Name your workspace
4. Connect the tool servers you want to use

## Step 2: Pick or Configure a Loadout

You can:
- Use a pre-configured loadout (Design, Research, Build, Ops)
- Create a custom loadout by selecting individual tools

## Step 3: Create a Session

1. In your workspace, click "Create session"
2. Select your loadout
3. Copy the generated MCP config

## Step 4: Connect Your Client

Add the MCP config to your client's configuration file:

```json
{
  "mcpServers": {
    "loadoutz": {
      "url": "https://loadoutz.io/mcp/session/<session-id>"
    }
  }
}
```

Replace `<session-id>` with your actual session ID.

Restart your MCP client. The tools configured in your loadout will now be available.

## Next Steps

- Read the [Security](security.md) documentation
- Review [FAQ](faq.md) for common questions
- Configure project-specific overrides if needed

## Troubleshooting

**Session expired:** Create a new session from your workspace.

**Tools not appearing:** Verify your loadout includes the desired tools.

**OAuth errors:** Reconnect the tool server in your workspace settings.