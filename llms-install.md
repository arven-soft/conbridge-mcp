# Install ConBridge in Cline

ConBridge is a hosted remote MCP server. Nothing is installed locally: no package, binary, API key or token.

- Server URL: `https://mcp.conbridge.app/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 with PKCE. Cline registers itself (dynamic client registration) and opens the browser to sign in.

## Steps for Cline

1. Add this entry to Cline's MCP settings file (`cline_mcp_settings.json`), keeping any existing servers:

   ```json
   {
     "mcpServers": {
       "conbridge": {
         "type": "streamableHttp",
         "url": "https://mcp.conbridge.app/mcp",
         "disabled": false
       }
     }
   }
   ```

   With the Cline CLI, the same is: `cline mcp add conbridge https://mcp.conbridge.app/mcp --transport http --yes`

2. In Cline's MCP Servers view, open `conbridge` and choose the authenticate / authorize OAuth action. With the CLI, run `cline mcp` and choose "Authorize OAuth".
3. The browser opens the ConBridge sign-in and consent screen. The user signs in, picks the organization and the tools Cline may use, and approves. Do not fill in credentials for the user.
4. Confirm `conbridge` shows as connected with its tools, then start with a read-only call such as `security_get_overview`.

Do not add an `Authorization` header or any token to the config. Whether a change runs at once or waits for the owner's approval follows the owner's rules for each target in the ConBridge Console.

## Requirements

- A ConBridge account at https://conbridge.app with at least one computer, server or site connected.

## Documentation

- https://conbridge.app/docs/mcp/oauth
- https://conbridge.app/docs/mcp/tools
- https://conbridge.app/support
