# ConBridge MCP server

ConBridge connects your AI app to the computers, servers and CMS sites you own. In the AI app you can:

- read the known vulnerabilities ConBridge found on each system;
- check with a read-only check that a finding applies;
- fix it on the one target you select.

Whether an action runs at once or waits for your approval follows the rule you set for that target in the ConBridge Console. ConBridge never changes a system by itself.

ConBridge is a hosted service. **This repository holds no server code**: it is the public home of the MCP server listing, with the endpoint, install links and the [MCP Registry](https://registry.modelcontextprotocol.io) entry ([`server.json`](server.json), `app.conbridge/conbridge`).

| | |
|---|---|
| Endpoint | `https://mcp.conbridge.app/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE and dynamic client registration. No API key, header or local process |
| Protected resource metadata | `https://mcp.conbridge.app/.well-known/oauth-protected-resource` |
| Tools | Security overview, findings, read-only checks and fix actions; file, command and site tools on the target you select. Full list: [conbridge.app/docs/mcp/tools](https://conbridge.app/docs/mcp/tools) |

## Quick install

- **Cursor:** [![Add ConBridge MCP server to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=conbridge&config=eyJ1cmwiOiJodHRwczovL21jcC5jb25icmlkZ2UuYXBwL21jcCJ9) or the [Cursor plugin](https://github.com/arven-soft/conbridge-cursor)
- **Visual Studio Code (GitHub Copilot):** [Add to Visual Studio Code](https://vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522conbridge%2522%252C%2522type%2522%253A%2522http%2522%252C%2522url%2522%253A%2522https%253A%252F%252Fmcp.conbridge.app%252Fmcp%2522%257D), or from a terminal:

  ```sh
  code --add-mcp '{"name":"conbridge","type":"http","url":"https://mcp.conbridge.app/mcp"}'
  ```

- **LM Studio** (0.3.17 or later): [Add to LM Studio](https://lmstudio.ai/install-mcp?name=conbridge&config=eyJ1cmwiOiJodHRwczovL21jcC5jb25icmlkZ2UuYXBwL21jcCJ9)
- **Claude:** [Add to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=ConBridge&connectorUrl=https%3A%2F%2Fmcp.conbridge.app%2Fmcp) (opens the Add custom connector dialog with the address filled in)
- **Claude Code:**

  ```sh
  claude mcp add --transport http conbridge https://mcp.conbridge.app/mcp
  ```

  Then open `/mcp` in a Claude Code session, choose ConBridge and finish the Authenticate step.

- **Codex:**

  ```sh
  codex mcp add conbridge --url https://mcp.conbridge.app/mcp
  codex mcp login conbridge
  ```

- **Cline:** see [llms-install.md](llms-install.md).
- **Google Antigravity:** `agy plugin install https://github.com/arven-soft/conbridge-antigravity`
- **Gemini CLI:** `gemini extensions install https://github.com/arven-soft/conbridge-gemini`, then `/mcp auth conbridge`
- **Any other MCP client:** add a remote (Streamable HTTP) server with the URL `https://mcp.conbridge.app/mcp` and no headers:

  ```json
  {"mcpServers": {"conbridge": {"url": "https://mcp.conbridge.app/mcp"}}}
  ```

The app opens the ConBridge sign-in in your browser. Sign in, choose the organization and the tools the app may use, and approve. Then ask, for example: "Show my ConBridge security overview."

Setup guides for every supported app: https://conbridge.app/integrations

## Requirements

A ConBridge account ([conbridge.app](https://conbridge.app), free to start) with at least one computer, server or site connected.

## Revoke access

Revoke an app in the ConBridge Console under **AI Apps**, or turn single tools off for it there.

## Security

- Every request is checked against your account, organization, the app's consent, the selected target and the tool's capability.
- A request never falls back to another computer, server or site.
- Content returned from files, logs, websites and commands is treated as data, not instructions.

Report a security issue to [security@conbridge.app](mailto:security@conbridge.app).

## Documentation and support

- [MCP server overview](https://conbridge.app/product/mcp-server)
- [Tools an AI app can use](https://conbridge.app/docs/mcp/tools)
- [Scopes and revoking access](https://conbridge.app/docs/mcp/oauth)
- [Support](https://conbridge.app/support) · [support@conbridge.app](mailto:support@conbridge.app)
- [Privacy policy](https://conbridge.app/legal/privacy) · [Terms](https://conbridge.app/legal/terms)

## License

The files in this repository are MIT licensed. ConBridge is an Arven Soft product, operated by Mehmet Aksoy.
