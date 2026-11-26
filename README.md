<p align="center"><img src="logo-400.png" width="120" alt="AI Video GT logo"></p>

# AI Video GT MCP server

The official remote MCP server for [AI Video GT](https://aivideogt.com/?utm_source=github&utm_medium=mcp&utm_campaign=listing-repo), an AI video and image studio. Connect it to Claude, Claude Code, Cursor, VS Code, ChatGPT or any Streamable HTTP MCP client.

- **URL:** `https://aivideogt.com/mcp`
- **Transport:** Streamable HTTP (hosted, nothing to install)
- **Auth:** optional `Authorization: Bearer <API key>` header
- **Docs:** https://aivideogt.com/mcp-server

## Tools

| Tool | Needs a key | What it does |
|---|---|---|
| `list_models` | No | Every video and image model with the exact credits for each resolution and clip length |
| `estimate_cost` | No | The credit cost of a generation before you make it |
| `find_video_tool` | No | Finds a free browser video tool: trim, crop, compress, convert, merge, add music, GIF, screen recorder and more (files stay on your device) |
| `generate_video` | Yes | Makes a video with sound from text with Genesis Flash, Vanta Ultra, Vanta Fast or Vanta Lite |
| `generate_image` | Yes | Makes an image with Nimbus Pro, Spectra 5, Fusion 2 or Graphite 2 |
| `get_generation` | Yes | Status and result of a generation |
| `list_generations` | Yes | Your recent generations |
| `get_account` | Yes | Your plan and credit balance |

Generations use the same credits as the website, and failed generations are refunded automatically. Credits come with a monthly plan (from $9 a month): https://aivideogt.com/pricing

To generate, create a Developer API key at aivideogt.com → Account → Developer API.

## Connect

### Claude Code

```bash
claude mcp add --transport http ai-video-gt https://aivideogt.com/mcp \
  --header "Authorization: Bearer YOUR_AIVIDEOGT_API_KEY"
```

### Claude (web and desktop)

Customize → Connectors → + Add → Add custom connector. Paste `https://aivideogt.com/mcp`, choose no sign-in, and to generate add the request header `Authorization: Bearer YOUR_AIVIDEOGT_API_KEY`.

### Cursor (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "ai-video-gt": {
      "url": "https://aivideogt.com/mcp",
      "headers": { "Authorization": "Bearer ${env:AIVIDEOGT_API_KEY}" }
    }
  }
}
```

### VS Code (`.mcp.json`)

```json
{
  "mcpServers": {
    "ai-video-gt": {
      "type": "http",
      "url": "https://aivideogt.com/mcp",
      "headers": { "Authorization": "Bearer ${AIVIDEOGT_API_KEY}" }
    }
  }
}
```

### ChatGPT

On chatgpt.com, open the plugins page, choose + and Add custom MCP server, paste `https://aivideogt.com/mcp` and pick no authentication. ChatGPT does not send API key headers, so it gets the model, price and video tool lookups; use one of the clients above to generate.

### Gemini CLI

```bash
gemini extensions install https://github.com/ismailgalaxys25-del/aivideogt-mcp
```

Set `AIVIDEOGT_API_KEY` in your environment to generate.

### Try it with curl

```bash
curl https://aivideogt.com/mcp \
  -H "Content-Type: application/json" -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

## Registry

Published in the official MCP Registry as `com.aivideogt/ai-video-gt`.

## Support

support@aivideogt.com · https://aivideogt.com/help

This repository only describes the hosted server; there is no source code to run.
