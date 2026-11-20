# Audience Resolver MCP by Nova (CIVAI)

Manage Audience Resolver content calendars, rows, and social scheduling on your AR project.

**Keywords:** mcp-server, model-context-protocol, nova-by-civai, remote-mcp, streamable-http, civai, cursor, claude-desktop, mcp, audience, resolver

Remote **Model Context Protocol (MCP)** server from **Nova by CIVAI**. Connect from **Cursor**, **Claude Desktop**, **Claude Code**, or any MCP client that supports **Streamable HTTP**.

## Links

| Resource | URL |
|----------|-----|
| MCP endpoint | https://nova.civai.co/mcp/agents/mcp-audience-resolver |
| Agent page | https://nova.civai.co/agent/mcp-audience-resolver |
| API keys | https://nova.civai.co/api-keys |
| Official Registry | `co.civai.nova/mcp-audience-resolver` |

## Authentication

Tool discovery (`initialize`, `tools/list`) is open, so you can see every tool before signing up. Calling a tool needs a Nova account, through either of two paths:

1. **OAuth 2.1 (sign in when prompted).** Clients that support MCP OAuth, such as Claude Code, ChatGPT and Codex, open a Nova sign-in on first use. Nothing to configure.
   - Protected resource metadata: https://nova.civai.co/.well-known/oauth-protected-resource/mcp/agents/mcp-audience-resolver
   - Authorization server: https://nova.civai.co (metadata at `/.well-known/oauth-authorization-server`)
2. **API key.** For clients without OAuth (Cursor, Cline, scripts), sign in at [nova.civai.co/api-keys](https://nova.civai.co/api-keys), create a programmatic key, and send it as `Authorization: Bearer <key>` or `X-API-Key: <key>`.

## Cursor Marketplace plugin

This repository ships a **Cursor Plugin** manifest (`.cursor-plugin/plugin.json` + root `mcp.json`) for one-click install after marketplace review. Users configure `NOVA_API_KEY` in Cursor **Plugins → Configure** (never commit secrets).

Local test: copy this folder to `~/.cursor/plugins/local/mcp-audience-resolver-by-nova`, reload the window, set `NOVA_API_KEY`, verify MCP tools load.

## Cursor (manual MCP)

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "mcp-audience-resolver-by-nova": {
      "url": "https://nova.civai.co/mcp/agents/mcp-audience-resolver",
      "headers": {
        "Authorization": "Bearer YOUR_NOVA_API_KEY"
      }
    }
  }
}
```

## Claude Code

Install as a plugin from the Nova marketplace, which prompts for your API key on first enable:

```bash
/plugin marketplace add civai-technologies/nova-catalog-mcp-plugins-by-nova-civai
/plugin install mcp-audience-resolver-by-nova --marketplace civai-technologies/nova-catalog-mcp-plugins-by-nova-civai
```

Or add the MCP server directly:

```bash
claude mcp add --transport http mcp-audience-resolver-by-nova \
  https://nova.civai.co/mcp/agents/mcp-audience-resolver \
  --header "Authorization: Bearer $NOVA_API_KEY"
```

Setting this up on someone's behalf? [`llms-install.md`](./llms-install.md) is written for that.

## Transport

- **Type:** Streamable HTTP (stateless)
- **Auth:** OAuth 2.1, or a Nova API key as `Authorization: Bearer` / `X-API-Key`


## Tools

- `list_content_calendars`
- `create_content_calendar`
- `get_content_calendar`
- `update_content_calendar`
- `delete_content_calendar`
- `create_calendar_row`
- `update_calendar_row`
- `delete_calendar_row`
- `delete_calendar_rows`
- `schedule_calendar_row`
- `schedule_all_calendar_rows`
- `upload_publisher_image`
- `upload_publisher_video`
- `export_content_calendar_json`
- `import_content_calendar_json`
- `list_twitter_accounts`
- `list_social_accounts`
- `nova_generate_calendar`
- `import_webpage_calendar`
- `get_row_generate_asset_context`
- `generate_calendar_row_asset`
- `regenerate_calendar_row_asset`
- `list_publishing_history`
- `get_publishing_history_item`
- `cancel_publishing_history`
- `unschedule_calendar_row`
- `list_project_assets`
- `asset_from_drive`
- `get_project_asset`
- `update_project_asset`
- `delete_project_asset`
- `cancel_project_asset`
- `list_projects`
- `create_project`
- `get_project_initialization_status`
- `generate_research`
- `get_research_status`
- `list_research_reports`
- `list_project_drive`
- `upload_project_drive_file`
- `publish_asset`
- `upload_publisher_audio`
- `set_publisher_video_audio`
- `get_network_identity`
- `set_network_identity`


## Data and usage

- **Where it runs.** The server is hosted by CIVAI on nova.civai.co. Requests and their results are processed on CIVAI's servers under the [Privacy Policy](https://nova.civai.co/privacy) and [Terms](https://nova.civai.co/terms).
- **What an account can run.** Usage depends on the plan of the signed-in Nova account. Current plans and limits are on the [agent page](https://nova.civai.co/agent/mcp-audience-resolver).
- **No local install.** Nothing runs on your machine; it cannot work offline.

## About Nova by CIVAI

**Nova by CIVAI** is a platform for running, building, and deploying AI agents. This MCP server exposes **Audience Resolver MCP** tools to external MCP hosts without sharing upstream credentials.

| | |
|---|---|
| **Company** | CIVAI TECHNOLOGIES |
| **Creator** | [Kayode Femi Amoo](https://x.com/usecodenaija) |
| **Product** | [Nova by CIVAI](https://nova.civai.co) |

## License

The files in this repository (README, manifests, icon, install guides) are MIT licensed. See [LICENSE](LICENSE).

The MCP server itself is a hosted CIVAI service. Its implementation is proprietary and is not in this repository; the MIT license does not cover it.
