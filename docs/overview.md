# Overview

## What is Loadoutz?

Loadoutz is an MCP (Model Context Protocol) session manager that provides scoped, audited access to external tools requiring OAuth authentication.

## Problem It Solves

MCP clients need secure, manageable access to OAuth-protected tools. Loadoutz provides:
- Centralized OAuth token management
- Session-scoped tool access
- Cross-client compatibility
- Audit trails for all tool interactions

## Core Concepts

### Workspaces
A workspace is a container for your tool configurations and preferences. You can have a global workspace with optional project-level overrides.

### Loadouts
Loadouts are pre-configured tool sets designed for specific workflows:
- **Design** — Figma + Playwright + screenshots + UI checks
- **Research** — Cloudflare docs + web search + citations
- **Build** — GitHub + terminal + filesystem + CI checks
- **Ops** — Logs + metrics + deploy workflows

### Sessions
A session represents a scoped MCP connection with:
- Explicit tool permissions (only tools you select)
- Automatic expiry
- Manual revocation capability
- Full audit logging

### What Gets Saved

**Saved in Loadoutz:**
- Workspace configurations
- Loadout selections
- Tool selections

**Exported to Client:**
- Session MCP config (contains session URL, no credentials)

**Runtime:**
- Audited tool calls with timestamps
- Session metadata (expiry, revocation status)

## Data Flow

1. You configure tool servers in your workspace
2. You select a loadout (or custom tool set)
3. Loadoutz generates a session URL
4. Your MCP client connects via the session URL
5. Tool calls are routed through Loadoutz with your OAuth tokens
6. All calls are logged for audit purposes

## Client Compatibility

Any MCP-compatible client can use Loadoutz. Tested clients include:
- Claude Code
- Cursor
- Windsurf
- OpenCode

## Limitations

- Does not run autonomously — all actions are user-initiated
- Does not access data without explicit user action
- Session scope only — no background or persistent access beyond session expiry