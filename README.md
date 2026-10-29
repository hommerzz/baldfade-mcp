# BaldFade MCP Server

**Website:** [baldfade.net](https://baldfade.net)

Remote, read-only [Model Context Protocol](https://modelcontextprotocol.io) server for [BaldFade](https://baldfade.net), the AI bald, buzz cut and fade hairstyle preview.

- **Endpoint:** `https://baldfade.net/api/mcp` (Streamable HTTP)
- **Auth:** none, no API key or account needed
- **Docs:** https://baldfade.net/mcp
- **Official MCP Registry:** `net.baldfade/baldfade`

This repository holds the public listing, configuration examples and `server.json`. The server itself is hosted by BaldFade.

## Tools

| Tool | What it does |
|---|---|
| `list_styles` | Lists the hairstyles BaldFade can preview (bald, buzz cut, fades, tapers), optionally filtered by `gender` (`male` / `female`), each with a link to its style page. |
| `norwood_info` | Explains what the BaldFade Norwood Hairline Self-Check does, how the estimate works and its limits. It is not a diagnosis. |

Both tools are read-only and free. The server does not accept photos, generate images or take payments. Previews are created and paid for on [baldfade.net](https://baldfade.net) (single image 4.99 USD, or credit packs).

## Connect

**Claude Code**

```bash
claude mcp add --transport http baldfade https://baldfade.net/api/mcp
```

**Cursor** (`~/.cursor/mcp.json`) and other clients that support remote HTTP servers

```json
{
  "mcpServers": {
    "baldfade": {
      "url": "https://baldfade.net/api/mcp"
    }
  }
}
```

**Claude Desktop / clients that only support stdio** (via `mcp-remote`)

```json
{
  "mcpServers": {
    "baldfade": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://baldfade.net/api/mcp"]
    }
  }
}
```

**Claude.ai / ChatGPT:** add a custom connector with the URL `https://baldfade.net/api/mcp`.

## Quick test

```bash
curl -s -X POST https://baldfade.net/api/mcp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

## Example prompts

- "What fade haircuts can I preview on BaldFade?"
- "Show me BaldFade's bald styles for women."
- "How does BaldFade's Norwood self-check work?"

## Links

- Website: https://baldfade.net
- Privacy: https://baldfade.net/privacy
- Terms: https://baldfade.net/terms
- Acceptable use: https://baldfade.net/acceptable-use
- Support: support@baldfade.net
