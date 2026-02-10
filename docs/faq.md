# FAQ

## General

### What is Loadoutz?

Loadoutz is an MCP session manager that provides secure, scoped access to OAuth-protected tools across MCP-compatible clients.

### What is MCP?

MCP (Model Context Protocol) is a protocol for connecting AI assistants to external tools and services.

### What clients work with Loadoutz?

Any MCP-compatible client. Tested clients include Claude Code, Cursor, Windsurf, and OpenCode.

## Security

### What data does Loadoutz access?

Loadoutz only accesses data when you explicitly invoke a tool through a session. It does not scrape, monitor, or automatically access any data.

### When does Loadoutz access data?

Loadoutz accesses data only when:
- You invoke a tool through an active session
- The tool makes an API call to the tool server using your OAuth token

### Where are my credentials stored?

OAuth tokens are stored on Loadoutz servers with encryption at rest. Credentials are never stored in URLs or on your client.

### Can I revoke access?

Yes. You can:
- Revoke individual sessions
- Disconnect tool servers (removes OAuth tokens)
- Delete entire workspaces

### Is my data shared with third parties?

No. OAuth tokens are used only to communicate with the tool servers you authorized. No data is shared with other third parties.

### Is Loadoutz running autonomously?

No. All tool calls are user-initiated. Loadoutz does not run background processes or make automatic API calls.

## Usage

### How do I create a session?

1. Create a workspace at loadoutz.io
2. Connect tool servers via OAuth
3. Pick or configure a loadout
4. Create a session and copy the MCP config
5. Add the config to your MCP client

### How long do sessions last?

Sessions have a configurable expiry time. Default is 24 hours. You can create new sessions at any time.

### Can I use multiple workspaces?

Yes. You can create separate workspaces for different projects or teams.

### Can I override tools for a specific project?

Yes. You can create project-level tool overrides that apply on top of your global workspace configuration.

### What happens when a session expires?

Expired sessions cannot make new tool calls. You can create a new session from your workspace.

## Troubleshooting

### My session isn't working

Check that:
- The session hasn't expired
- The session hasn't been revoked
- Your loadout includes the tools you're trying to use
- Your MCP client is configured correctly

### OAuth isn't working

Make sure:
- You're using a supported OAuth provider
- Pop-up blockers are disabled for loadoutz.io
- You're logged in to the provider's account

### Tools aren't appearing in my client

Verify:
- Your loadout includes the tools
- The session is active (not expired or revoked)
- Your MCP client is restarted after adding the config

## Data & Privacy

### What data is stored?

Loadoutz stores:
- Workspace configurations
- OAuth tokens
- Session metadata
- Audit logs for tool calls

### Can I delete my data?

Yes. You can delete individual workspaces, which removes all associated data including tokens and audit logs.

### How long are audit logs kept?

Audit logs are retained for security and debugging purposes. Contact support for specific retention policies.

### Does Loadoutz work with enterprise SSO?

Enterprise OAuth flows are supported if the provider supports standard OAuth 2.0.

## Billing

### Is Loadoutz free?

Pricing information is available at https://loadoutz.io/pricing

### What happens if I hit usage limits?

You'll receive notifications as you approach limits. Additional capacity can be added through your account settings.

## Support

### Where can I get help?

- Documentation: https://github.com/waffflebby/loadoutz.io
- Issues: https://github.com/waffflebby/loadoutz.io/issues
- Security: See SECURITY.md

### How do I report a bug?

Open an issue on GitHub with:
- Steps to reproduce
- Expected behavior
- Actual behavior
- Environment details