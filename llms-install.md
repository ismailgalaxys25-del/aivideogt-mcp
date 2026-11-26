# Installing the AI Video GT MCP server

This is a hosted remote server; there is nothing to install or build.

- URL: `https://aivideogt.com/mcp`
- Transport: Streamable HTTP
- Auth: optional header `Authorization: Bearer <API key>`. Without it, `list_models`, `estimate_cost` and `find_video_tool` work. With it, the generate and account tools work too.

Example config:

```json
{
  "mcpServers": {
    "ai-video-gt": {
      "type": "streamableHttp",
      "url": "https://aivideogt.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_AIVIDEOGT_API_KEY" }
    }
  }
}
```

Ask the user for their key (aivideogt.com → Account → Developer API) only if they want to generate. Leave the header out otherwise.
