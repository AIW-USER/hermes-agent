# 7. Notes from the agentwikis.com Hermes knowledge base

[Agent Wikis](https://agentwikis.com/) maintains a third-party knowledge base about Hermes at
<https://agentwikis.com/wiki/hermes/>. It is **not** official Nous Research documentation.

> **How this page was made.** When this folder was written, agentwikis.com could not be opened
> directly from the environment used (its network policy blocked the site), so the points below
> come from web-search summaries of the wiki's pages. Each point was then checked against this
> repository — the "Checked in repo" column says what was found. Read the linked wiki pages
> yourself for the full text, and prefer the official docs when they disagree.

## About the wiki

- Covers setup, configuration, CLI commands, features, skills, providers, deployment,
  integrations and troubleshooting. It leaves out live community discussion and third-party pricing.
- Split into `raw/` (unchanged source documents) and `wiki/` (synthesized pages: entities,
  concepts, syntheses). At the time of writing it listed ~126 pages and tracked Hermes v0.21.x.
- Entry point: [README](https://agentwikis.com/wiki/hermes/README.md).

## Useful tips from the wiki

| Topic | Tip from the wiki | Checked in repo |
|---|---|---|
| Desktop app ([page](https://agentwikis.com/wiki/hermes/wiki/entities/hermes-desktop-app.md)) | Installing the desktop app on top of an existing install reuses your config, keys, sessions and skills; `hermes desktop` launches it — no re-setup | `hermes desktop` documented in `website/docs/reference/cli-commands.md` |
| Desktop app | Tail desktop logs with `hermes logs gui -f` | `logs gui` referenced in the docs |
| Remote backend | Bind the backend to a specific reachable IP instead of `0.0.0.0`, e.g. `hermes serve --host <tailscale-ip> --port 9119`. OAuth over a bare Tailscale IP only works when the backend binds to that exact IP | `hermes serve --host` documented; matches SECURITY.md advice not to expose surfaces publicly |
| Remote backend | Sessions that drop after a restart → set a stable `HERMES_DASHBOARD_BASIC_AUTH_SECRET` | Variable exists in the docs/code |
| Docker backend ([page](https://agentwikis.com/wiki/hermes/wiki/entities/backend-docker.md)) | One long-lived container is reused across sessions and subagents; skills and credentials are mounted automatically; profiles, memories and credentials stay separate | Matches `website/docs/user-guide/configuration.md` (also: `container_persistent: false` gives one container per session) |
| Approvals | The desktop app has a per-session YOLO toggle — understand the trade-off before using it | See [05-safety-and-security.md](05-safety-and-security.md#54-yolo-mode--use-with-care) |
| Matrix ([page](https://agentwikis.com/wiki/hermes/wiki/entities/platform-matrix.md)) | Reaction-based approvals are bound to the requesting user by default; an admin can change that | — |
| MCP ([page](https://agentwikis.com/wiki/hermes/wiki/concepts/mcp-integration.md)) | Set approval rules per server, since remote write actions don't always prompt | Matches the `trust: untrusted` per-server setting in the MCP docs |
| Signal ([page](https://agentwikis.com/wiki/hermes/wiki/entities/platform-signal.md)) | Uses `signal-cli` in daemon mode; configure with `SIGNAL_HTTP_URL` and `SIGNAL_ACCOUNT` | Both variables exist in the repo |
| WhatsApp ([page](https://agentwikis.com/wiki/hermes/wiki/entities/platform-whatsapp.md)) | Pair with the QR wizard `hermes whatsapp`; lock down session files with `chmod 700` | `hermes whatsapp` documented |
| iMessage / Photon ([page](https://agentwikis.com/wiki/hermes/wiki/entities/platform-imessage-photon.md)) | Missing sidecar deps → `hermes photon install-sidecar`; missing device token → re-run `hermes photon setup` | Both commands referenced in the repo |
| Memory providers ([Holographic](https://agentwikis.com/wiki/hermes/wiki/entities/memory-holographic.md), [Hindsight](https://agentwikis.com/wiki/hermes/wiki/entities/memory-hindsight.md), [OpenViking](https://agentwikis.com/wiki/hermes/wiki/entities/memory-openviking.md)) | Set up with `hermes memory setup`, or `hermes config set memory.provider <name>` + key/endpoint in `.env`. Holographic is local with no extra service; OpenViking needs a running `openviking-server`; Hindsight adds retain/recall/reflect tools, cloud or local | Matches `website/docs/user-guide/features/memory-providers.md`. **Note:** these providers now install from the plugin catalog (`hermes plugins install holographic`, etc.) |
| Memory | Lowering the compression threshold (e.g. `0.5`) reduces forgetting | `0.50` is already the shipped default for `compression.threshold` |
| Cron troubleshooting ([checklist](https://agentwikis.com/wiki/hermes/wiki/syntheses/cron-troubleshooting-checklist.md)) | Jobs only fire while the **gateway** runs (a CLI session is not enough); check that the delivery platform's token is configured; a `[SILENT]` marker suppresses output; duplicate gateway instances can cause skipped jobs | Consistent with `website/docs/guides/cron-troubleshooting.md` |
| Web search ([page](https://agentwikis.com/wiki/hermes/wiki/concepts/web-search-extract.md)) | Overview of `web_search` / `web_extract` and their backends | Backends live in `plugins/web/` (Brave, DDGS, Exa, Firecrawl, Parallel, Perplexity, SearXNG, Tavily, xAI, …) |
| Community ([hermes-webui](https://agentwikis.com/wiki/hermes/wiki/entities/community-webui.md)) | A community-built web UI for Hermes exists | Third-party — review before installing (see safety guide) |

## Other wiki pages worth reading

The wiki's index also lists a Skills deep-dive and a Security Hardening page. For security, the
repository's own `SECURITY.md` and [05-safety-and-security.md](05-safety-and-security.md) are
the authoritative references.

## Sources

- [Hermes Agent Knowledge Base (README)](https://agentwikis.com/wiki/hermes/README.md)
- [Agent Wikis home](https://agentwikis.com/)
- [Hermes Desktop App](https://agentwikis.com/wiki/hermes/wiki/entities/hermes-desktop-app.md)
- [Docker Container Backend](https://agentwikis.com/wiki/hermes/wiki/entities/backend-docker.md)
- [MCP Integration](https://agentwikis.com/wiki/hermes/wiki/concepts/mcp-integration.md)
- [Web Search & Extract](https://agentwikis.com/wiki/hermes/wiki/concepts/web-search-extract.md)
- [Signal Platform](https://agentwikis.com/wiki/hermes/wiki/entities/platform-signal.md)
- [WhatsApp Platform](https://agentwikis.com/wiki/hermes/wiki/entities/platform-whatsapp.md)
- [Matrix Platform](https://agentwikis.com/wiki/hermes/wiki/entities/platform-matrix.md)
- [iMessage (Photon) Platform](https://agentwikis.com/wiki/hermes/wiki/entities/platform-imessage-photon.md)
- [Holographic Memory Provider](https://agentwikis.com/wiki/hermes/wiki/entities/memory-holographic.md)
- [Hindsight Memory Provider](https://agentwikis.com/wiki/hermes/wiki/entities/memory-hindsight.md)
- [OpenViking Memory Provider](https://agentwikis.com/wiki/hermes/wiki/entities/memory-openviking.md)
- [Cron Troubleshooting — the Four-Category Checklist](https://agentwikis.com/wiki/hermes/wiki/syntheses/cron-troubleshooting-checklist.md)
- [hermes-webui (community)](https://agentwikis.com/wiki/hermes/wiki/entities/community-webui.md)
