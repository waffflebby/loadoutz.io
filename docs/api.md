# API Reference

## Session Endpoint

### Create Session

```
POST /api/session
```

Creates a new MCP session with the specified tool permissions.

**Request Body:**
```json
{
  "workspaceId": "string",
  "loadoutId": "string",
  "toolIds": ["string"],
  "expiry": "ISO8601 datetime"
}
```

**Response:**
```json
{
  "sessionId": "string",
  "mcpUrl": "https://loadoutz.io/mcp/session/{sessionId}",
  "expiresAt": "ISO8601 datetime",
  "tools": ["string"]
}
```

### Get Session

```
GET /api/session/{sessionId}
```

Retrieves session information and status.

**Response:**
```json
{
  "sessionId": "string",
  "workspaceId": "string",
  "status": "active|expired|revoked",
  "expiresAt": "ISO8601 datetime",
  "tools": ["string"],
  "createdAt": "ISO8601 datetime"
}
```

### Revoke Session

```
POST /api/session/{sessionId}/revoke
```

Immediately revokes a session. New tool calls will be rejected.

**Response:**
```json
{
  "success": true
}
```

## MCP Protocol

Loadoutz implements the MCP protocol for tool invocation.

### Tool Invocation

Clients invoke tools through the session URL:

```
POST https://loadoutz.io/mcp/session/{sessionId}
```

**Request Body:**
```json
{
  "tool": "string",
  "method": "string",
  "params": {}
}
```

**Response:**
```json
{
  "result": {},
  "error": null,
  "callId": "string"
}
```

## Workspace API

### Create Workspace

```
POST /api/workspace
```

**Request Body:**
```json
{
  "name": "string"
}
```

**Response:**
```json
{
  "workspaceId": "string",
  "name": "string",
  "createdAt": "ISO8601 datetime"
}
```

### List Workspaces

```
GET /api/workspace
```

**Response:**
```json
{
  "workspaces": [
    {
      "workspaceId": "string",
      "name": "string",
      "createdAt": "ISO8601 datetime"
    }
  ]
}
```

## Tool Server API

### Connect Tool Server

```
POST /api/workspace/{workspaceId}/tool-server
```

Initiates OAuth flow for a tool server.

**Request Body:**
```json
{
  "provider": "string",
  "redirectUrl": "string"
}
```

**Response:**
```json
{
  "authUrl": "string",
  "state": "string"
}
```

### List Tool Servers

```
GET /api/workspace/{workspaceId}/tool-server
```

**Response:**
```json
{
  "toolServers": [
    {
      "toolServerId": "string",
      "provider": "string",
      "status": "connected|disconnected",
      "connectedAt": "ISO8601 datetime"
    }
  ]
}
```

### Disconnect Tool Server

```
DELETE /api/workspace/{workspaceId}/tool-server/{toolServerId}
```

Removes OAuth tokens and disconnects the tool server.

**Response:**
```json
{
  "success": true
}
```

## Loadout API

### Create Loadout

```
POST /api/workspace/{workspaceId}/loadout
```

**Request Body:**
```json
{
  "name": "string",
  "toolIds": ["string"]
}
```

**Response:**
```json
{
  "loadoutId": "string",
  "name": "string",
  "tools": ["string"],
  "createdAt": "ISO8601 datetime"
}
```

### List Loadouts

```
GET /api/workspace/{workspaceId}/loadout
```

**Response:**
```json
{
  "loadouts": [
    {
      "loadoutId": "string",
      "name": "string",
      "isCustom": boolean,
      "tools": ["string"]
    }
  ]
}
```

## Error Responses

All endpoints may return standard error responses:

```json
{
  "error": {
    "code": "string",
    "message": "string"
  }
}
```

### Common Error Codes

- `UNAUTHORIZED` — Invalid or missing authentication
- `FORBIDDEN` — Insufficient permissions
- `NOT_FOUND` — Resource does not exist
- `SESSION_EXPIRED` — Session has expired
- `SESSION_REVOKED` — Session has been revoked
- `INVALID_REQUEST` — Malformed request
- `INTERNAL_ERROR` — Server error

## Rate Limiting

API endpoints are rate-limited. Exceeding limits returns `429 Too Many Requests`.

Response includes:
```json
{
  "error": {
    "code": "RATE_LIMITED",
    "message": "string",
    "retryAfter": "number"
  }
}
```