# Installing the Skael MCP server

Skael is a hosted, remote MCP server. Do not clone or build anything. Add the remote endpoint to the client configuration.

## Cline

1. The user needs a Skael account (https://api.skael.de, free sign-up).
2. Ask the user to create a personal MCP token in the Skael dashboard under Settings → MCP (`/settings/mcp`). It starts with `eak_`.
3. Add this entry to `cline_mcp_settings.json`, with the token in place of `<YOUR_MCP_TOKEN>`:

```json
{
  "mcpServers": {
    "skael": {
      "type": "streamableHttp",
      "url": "https://api.skael.de/mcp",
      "headers": {
        "Authorization": "Bearer <YOUR_MCP_TOKEN>"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Keep the word `Bearer` and the space before the token.

4. Verify the connection by calling the `whoami` tool. It returns the user, the organizations and the credit balance.

## Notes

- Tools that cost credits always state the price first. Anything above 500 credits needs explicit confirmation from the user.
- Clients with OAuth support can omit the `headers` block; they open the Skael sign-in on the first call.
- Full documentation: https://api.skael.de/docs/mcp
