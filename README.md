# QRStuff OpenAI Codex Plugins

A [Codex plugin marketplace](https://developers.openai.com/codex/mcp) that lets you install and configure the **QRStuff MCP server** in the OpenAI Codex CLI with a single command — no manual TOML editing required.

## What's in here

This repository is a Codex marketplace (`qrstuff-codex-plugins`) that distributes a single plugin:

| Plugin               | Description                                                                                                                                                       |
| :------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `qrstuff-mcp-server` | Adds the QRStuff [MCP server](https://mcp.qrstuff.ai/mcp) to OpenAI Codex, giving Codex access to the QRStuff platform for QR code generation and scan analytics. |

When you install the plugin, Codex CLI registers the remote MCP server at `https://mcp.qrstuff.ai/mcp` for you.

## Requirements

- [OpenAI Codex CLI](https://developers.openai.com/codex) installed and signed in.

## Installation

You can add the marketplace and install the plugin either from within an interactive Codex CLI session (using `/marketplace` slash commands) or from your terminal (using `codex` subcommands).

### From within Codex CLI

1. Add this marketplace:

```text
/marketplace add qrstuff/codex-plugins
```

2. Install the plugin:

```text
/plugin install qrstuff-mcp-server@qrstuff-codex-plugins
```

### From the terminal

```bash
codex marketplace add qrstuff/codex-plugins
codex plugin install qrstuff-mcp-server@qrstuff-codex-plugins
```

> The `qrstuff/codex-plugins` shorthand resolves to this GitHub repository (`https://github.com/qrstuff/codex-plugins`). You can also pass the full URL:
>
> ```bash
> codex marketplace add https://github.com/qrstuff/codex-plugins.git
> ```

## Usage

Once the plugin is installed, the QRStuff MCP server is available to Codex automatically. Start (or restart) a Codex CLI session and the `qrstuff` MCP server will be connected.

You can then ask Codex to use QRStuff in natural language, for example:

> "Generate a QR code for https://qrstuff.com using QRStuff."

To confirm the server is connected, list the active MCP servers:

```text
codex mcp list
```

You should see `qrstuff` in the list of connected servers.

## Updating

When a new version of the plugin or marketplace is published, refresh your local copy:

```text
codex marketplace update qrstuff-codex-plugins
```

## Uninstalling

Remove the plugin:

```text
codex plugin uninstall qrstuff-mcp-server@qrstuff-codex-plugins
```

Remove the marketplace entirely:

```text
codex marketplace remove qrstuff-codex-plugins
```

## Repository structure

```
.
├── .codex-plugin/
│   └── marketplace.json          # Marketplace catalog (lists the plugins)
└── plugins/
    └── qrstuff-mcp-server/
        ├── .codex-plugin/
        │   └── plugin.json       # Plugin manifest
        ├── assets/
        │   └── logo.png          # Plugin logo
        ├── skills/
        │   └── CODEX.md          # Custom agent instructions
        ├── mcp.json              # MCP server configuration
        └── README.md             # Plugin-specific documentation
```

## Troubleshooting

- **Marketplace not found**: make sure you ran `codex marketplace add qrstuff/codex-plugins` and that you have network access to GitHub.
- **`qrstuff` server not listed in `codex mcp list`**: restart your Codex CLI session after installing.
- **Plugin not updating**: versions are pinned via `.codex-plugin/plugin.json`. Run `codex marketplace update qrstuff-codex-plugins` to fetch the latest catalog.

For more on how marketplaces and plugins work, see the official [OpenAI Codex developer documentation](https://developers.openai.com/codex).

With ❤️ From [QRStuff](https://www.qrstuff.com/)
