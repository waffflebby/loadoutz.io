# Security Policy

## Supported Versions

Currently, only the latest version of Loadoutz is supported.

## Reporting Security Vulnerabilities

If you discover a security vulnerability, please report it responsibly.

**Do not** open a public issue.

**Do** send an email to: security@loadoutz.io

Include:
- Description of the vulnerability
- Steps to reproduce (if applicable)
- Impact assessment

## What We Need From You

- Give us reasonable time to investigate and respond
- Avoid public disclosure until a fix is released
- Provide details to help us understand and reproduce the issue

## What You Can Expect From Us

- Confirmation of receipt within 48 hours
- Timeline for investigation and fix
- Notification when a fix is released
- Credit in release notes (if desired)

## Security Features

- OAuth tokens stored server-side with encryption at rest
- Session-scoped access to explicitly selected tools
- Automatic session expiry
- Manual session revocation
- Audited tool calls
- No secrets in URLs or client-side configurations

## Data Handling

- Credentials are never shared with third parties
- OAuth tokens are used only for authorized tool servers
- Session data is retained for audit purposes only
- Users can delete workspaces and associated data at any time