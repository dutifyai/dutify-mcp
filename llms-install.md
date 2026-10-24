# Installing the Dutify MCP server (for AI agents)

This is a **remote** MCP server. Do not clone or build anything.

1. Ask the user for a Dutify API key. A personal key starts with `du_live_`. If they have none, tell them to sign up at https://dutify.cloud and create a personal key in account settings. Never invent a key.
2. Add this server to the MCP settings file:

```json
{
  "mcpServers": {
    "dutify": {
      "type": "streamableHttp",
      "url": "https://mcp.dutify.ai",
      "headers": { "X-API-Key": "<the user's key>" }
    }
  }
}
```

3. Verify by calling the `whoami` tool. It should return the key type and scopes. Then call `list_workspaces` and pass a workspace on later data calls.

A `401` means the key is missing, mistyped or revoked. A `403 FORBIDDEN` names the scope the key lacks.
