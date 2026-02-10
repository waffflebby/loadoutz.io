# Authentication & Security

## OAuth Flow

Loadoutz uses standard OAuth 2.0 flows for authentication:

1. You initiate OAuth for a tool server in your workspace
2. You are redirected to the provider's authorization page
3. You grant permission to Loadoutz
4. The provider returns an OAuth token to Loadoutz
5. Loadoutz stores the token server-side

## Token Storage

- Tokens are stored on Loadoutz servers
- Encryption at rest is applied
- Tokens are never exposed to clients or included in session URLs
- Tokens are only used for authenticated requests to authorized tool servers

## Session Security

### Session Scoping
Each session only has access to tools explicitly selected in the loadout. Tools not selected cannot be accessed through that session.

### Session Expiry
- Sessions have a configurable expiry time
- Expired sessions cannot be used for new tool calls
- You can create new sessions at any time

### Session Revocation
- Sessions can be revoked immediately from your workspace
- Revoked sessions cannot be used for new tool calls
- Active tool calls may complete before revocation takes effect

## Tool Call Auditing

All tool calls through Loadoutz are logged with:
- Timestamp
- Session ID
- Tool server
- Tool name
- Request/response metadata

Audit logs are retained for security and debugging purposes.

## What Loadoutz Does Not Do

- Does not store your OAuth credentials (uses standard tokens)
- Does not share tokens with third parties
- Does not make unauthorized API calls
- Does not run background processes
- Does not access data without user initiation

## What You Should Know

- OAuth tokens grant Loadoutz access to the tools you authorized
- You can revoke access by disconnecting tool servers in your workspace
- Deleting a workspace removes all associated data
- Sessions are scoped — they cannot access tools not in the loadout

## Best Practices

- Use separate workspaces for different projects or teams
- Review your loadout selections before creating sessions
- Revoke unused sessions
- Disconnect tool servers you no longer use
- Create new sessions periodically for critical work

## Data Retention

- Workspace configurations: retained until deleted
- OAuth tokens: retained until tool server is disconnected
- Session data: retained according to audit policy
- Audit logs: retained for security and compliance purposes