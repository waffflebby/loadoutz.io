# Loadoutz.io

Open workspace. Pick loadout. Attach once. One MCP config. All your tools. Any editor.

## What This Is

Loadoutz is an MCP (Model Context Protocol) session manager that provides scoped, audited access to external tools requiring OAuth. It lets you configure tool servers once and use them across MCP-compatible clients.

## What This Is Not

- An automated agent or autonomous system
- A background service that accesses data without user initiation
- A tool discovery or scraping platform
- A credential vault or secrets manager

## How It Works

1. **Open workspace** — Connect providers and tool servers
2. **Pick a loadout** — Select tools based on your task (Design, Research, Build, Ops)
3. **Create session** — Paste the MCP config once. You are live across clients

### Architecture

- **Workspaces** — Container for your tool configurations and preferences
- **Loadouts** — Pre-configured tool sets for specific workflows
- **Sessions** — Scoped MCP connections with explicit permissions and expiry

## MCP Config

```json
{
  "mcpServers": {
    "loadoutz": {
      "url": "https://loadoutz.io/mcp/session/<id>"
    }
  }
}
```

## Supported Clients

- Claude Code
- Cursor
- Windsurf
- OpenCode

## Security

- OAuth tokens are stored server-side with encryption at rest
- No secrets are exposed in URLs or client-side configs
- Sessions are scoped to explicit tool selections
- Sessions expire automatically and can be revoked at any time
- All tool calls are audited

## Documentation

- [Overview & Concepts](docs/overview.md)
- [Quickstart](docs/quickstart.md)
- [Authentication & Security](docs/security.md)
- [API Reference](docs/api.md)
- [FAQ](docs/faq.md)

## License

See [LICENSE](LICENSE) for details.

## Support

- Issues: https://github.com/waffflebby/loadoutz.io/issues
- Security: See [SECURITY.md](SECURITY.md)