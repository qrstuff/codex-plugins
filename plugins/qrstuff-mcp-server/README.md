# QRStuff MCP Server Plugin for OpenAI Codex

Adds the hosted QRStuff MCP server to OpenAI Codex CLI so agents can use QRStuff tools for QR code generation and scan analytics.

The plugin registers the `qrstuff` MCP server at:

```text
https://mcp.qrstuff.ai/mcp
```

After installing the plugin, restart the Codex CLI session and ask the agent to use QRStuff, for example:

> "Generate a QR code for https://qrstuff.com using QRStuff."
