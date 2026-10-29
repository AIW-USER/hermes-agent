# File reference: `website`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `website/`

| File | What it does |
|---|---|
| `.gitignore` | Dependencies |
| `.npmrc` | needed to prevent bad npm that has min-release-age but not exclude |
| `README.md` | Website |
| `docusaurus.config.ts` | TypeScript source: `docusaurus.config` |
| `package-lock.json` | npm dependency lock file |
| `package.json` | JSON manifest for `website` |
| `sidebars.ts` | TypeScript source: `sidebars` |
| `tsconfig.json` | JSON object with keys `extends`, `compilerOptions`, `exclude` |

## `website/docs/`

| File | What it does |
|---|---|
| `developer-guide/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `developer-guide/acp-internals.md` | How the ACP adapter works: lifecycle, sessions, event bridge, approvals, and tool rendering |
| `developer-guide/adding-platform-adapters.md` | Adding a Platform Adapter |
| `developer-guide/adding-providers.md` | How to add a new inference provider to Hermes Agent — auth, runtime resolution, CLI flows, adapters, tests, and docs |
| `developer-guide/adding-tools.md` | How to add a new tool to Hermes Agent — schemas, handlers, registration, and toolsets |
| `developer-guide/agent-loop.md` | Detailed walkthrough of AIAgent execution, API modes, tools, callbacks, and fallback behavior |
| `developer-guide/architecture.md` | Hermes Agent internals — major subsystems, execution paths, data flow, and where to read next |
| `developer-guide/billing-lifecycle.md` | Map from every billing/subscription state and typed refusal to the exact TUI copy and recovery action |
| `developer-guide/browser-provider-plugin.md` | How to build a cloud browser backend plugin for Hermes Agent |
| `developer-guide/browser-supervisor.md` | How Hermes detects and responds to native JS dialogs and interacts with cross-origin iframes via a persistent CDP connection. |
| `developer-guide/browser-vault-plugin.md` | Add a password manager to browser_vault with ctx.register_login_backend, and the isolation rules it runs under |
| `developer-guide/chronos-managed-cron-contract.md` | Agent ↔ NAS wire contract for the Chronos cron provider |
| `developer-guide/cli-internals.md` | How hermes_cli is shaped: slash dispatch, config loaders, the skin engine, the transactional update pipeline, and process-identity rules |
| `developer-guide/codebase-ownership.md` | Which directories belong to which subsystem, and where the right docs entry point lives for each |
| `developer-guide/completion-backlog-delivery.md` | Background completion backlogs |
| `developer-guide/config-backend.md` | Where a profile's user config.yaml is read and written: the ConfigBackend seam, the file and remote backends, and the CI lints that keep every caller on it |
| `developer-guide/context-compression-and-caching.md` | Context Compression and Caching |
| `developer-guide/context-engine-plugin.md` | How to build a context engine plugin that replaces the built-in ContextCompressor |
| `developer-guide/contributing.md` | How to contribute to Hermes Agent — dev setup, code style, PR process |
| `developer-guide/creating-skills.md` | How to create skills for Hermes Agent — SKILL.md format, guidelines, and publishing |
| `developer-guide/cron-internals.md` | How Hermes stores, schedules, edits, pauses, skill-loads, and delivers cron jobs |
| `developer-guide/delegation-provider-plugin.md` | Delegation Provider Plugins |
| `developer-guide/desktop-plugin-sdk.md` | Extend the native Hermes Desktop app — panes, pages, sidebar nav, status bar, palette commands, keybinds, themes, and a scoped backend namespace, with one import and no build step. |
| `developer-guide/egress-internals.md` | How the iron-proxy egress firewall integrates with Hermes — module layout, lifecycle, security invariants, and extension points |
| `developer-guide/extending-the-cli.md` | Build wrapper CLIs that extend the Hermes TUI with custom widgets, keybindings, and layout changes |
| `developer-guide/gateway-classic-cli.md` | How hermes chat / --cli attach to the gateway authority |
| `developer-guide/gateway-command-parity.md` | What each local client does with every slash command on the shared gateway |
| `developer-guide/gateway-internals.md` | How the messaging gateway boots, authorizes users, routes sessions, and delivers messages |
| `developer-guide/gateway-local-sessions.md` | Local CLI/TUI sessions as canonical gateway admissions |
| `developer-guide/gateway-monitoring.md` | Health export, structured diagnostics, fleet queries and how to extend the monitoring plane |
| `developer-guide/gateway-session-lifecycle.md` | SessionSource, SessionEntry, SessionStore, session-key rules and multi-user isolation in the gateway |
| `developer-guide/hosted-profile-owners.md` | Hosted rooms across local profile owners |
| `developer-guide/image-gen-provider-plugin.md` | How to build an image-generation backend plugin for Hermes Agent |
| `developer-guide/macos-bundle-updates.md` | macOS bundle updates |
| `developer-guide/memory-provider-plugin.md` | How to build a memory provider plugin for Hermes Agent |
| `developer-guide/micro-compaction.md` | How micro-compaction amortizes context compression cost: triggers, tail sizing, the cached-prefix trade-off |
| `developer-guide/middleware.md` | Behavior-changing plugin middleware for LLM and tool calls: contract, execution order, examples |
| `developer-guide/model-provider-plugin.md` | How to build a model provider (inference backend) plugin for Hermes Agent |
| `developer-guide/multiplexing-gateway.md` | Design of the one-gateway-for-all-profiles mode: scope composition, secret scope, inbound routing, persistence |
| `developer-guide/observer-hooks.md` | Read-only telemetry contract for plugins: event families, correlation IDs, payload safety |
| `developer-guide/plugin-llm-access.md` | Run any LLM call from inside a plugin via ctx.llm — chat or structured, sync or async. Host-owned auth, fail-closed trust gate, optional JSON Schema validation. |
| `developer-guide/plugins/application-declarations.md` | Application declarations |
| `developer-guide/plugins/catalog-submission.md` | The full admission guidelines for the Hermes plugin catalog: what to check before you submit, the rules every entry follows, and what reviewers look at |
| `developer-guide/plugins/index.md` | Step-by-step guide to building a complete Hermes plugin with tools, hooks, data files, and skills |
| `developer-guide/pm-audit-status.md` | PM audit remediation status |
| `developer-guide/programmatic-integration.md` | Three protocols for driving hermes-agent from external programs: ACP, the TUI gateway JSON-RPC, and the OpenAI-compatible HTTP API |
| `developer-guide/prompt-assembly.md` | How Hermes builds the system prompt, preserves cache stability, and injects ephemeral layers |
| `developer-guide/provider-runtime.md` | How Hermes resolves providers, credentials, API modes, and auxiliary models at runtime |
| `developer-guide/relay-connector-contract.md` | Wire contract between the Hermes gateway relay adapter and external connectors (experimental) |
| `developer-guide/relay-shared-metrics.md` | NeMo Relay shared metrics: what is exported, consent and retention, staging validation |
| `developer-guide/secret-source-plugin.md` | How to build a secret-manager backend plugin for Hermes Agent |
| `developer-guide/session-storage.md` | Session Storage |
| `developer-guide/shared-bundle-builds.md` | Shared bundle builds |
| `developer-guide/source-update-completion.md` | Source update completion ownership |
| `developer-guide/stable-releases.md` | Stable release admission and promotion |
| `developer-guide/state-db-recovery.md` | How Hermes recovers state.db when the FTS index or the file itself is corrupt |
| `developer-guide/streaming-tts.md` | Sentence chunker, streaming provider ABC, capability matrix and how to add a streaming TTS provider |
| `developer-guide/subagent-lifecycle-api.md` | Public Subagent Lifecycle API |
| `developer-guide/terminal-environment-plugin.md` | Terminal Environment Provider Plugins |
| `developer-guide/tools-runtime.md` | Runtime behavior of the tool registry, toolsets, dispatch, and terminal environments |
| `developer-guide/trajectory-format.md` | Trajectory Format |
| `developer-guide/video-gen-provider-plugin.md` | How to build a video-generation backend plugin for Hermes Agent |
| `developer-guide/web-search-provider-plugin.md` | How to build a web-search/extract/crawl backend plugin for Hermes Agent |
| `developer-guide/worktree-ui-dev.md` | Run the Ink TUI and Electron desktop app from a git worktree without a full npm install per checkout |
| `getting-started/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `getting-started/installation.md` | Install Hermes Agent with desktop bundles, source installers, Docker, Nix, or the Termux APT package |
| `getting-started/learning-path.md` | Choose your learning path through the Hermes Agent documentation based on your experience level and goals. |
| `getting-started/nix-setup.md` | Install and deploy Hermes Agent with Nix — from quick `nix run` to fully declarative NixOS module with container mode |
| `getting-started/platform-support.md` | Which operating systems, distribution methods, and features Hermes Agent supports. |
| `getting-started/quickstart.md` | Your first conversation with Hermes Agent — from install to chatting in under 5 minutes |
| `getting-started/termux.md` | Install Hermes Agent on Android from its signed Termux APT repository |
| `getting-started/updating.md` | How to update Hermes Agent to the latest version or uninstall it |
| `guides/_category_.json` | JSON object with keys `label`, `position`, `collapsible`, `collapsed` |
| `guides/agent-email-address.md` | Set up a dedicated mailbox your agent can read and send from using the bundled Himalaya skill, with a cron polling pattern and safety notes |
| `guides/automate-with-cron.md` | Real-world automation patterns using Hermes cron — monitoring, reports, pipelines, and multi-skill workflows |
| `guides/automation-blueprints.md` | Ready-to-use automation blueprints — scheduled tasks, GitHub event triggers, API webhooks, and multi-skill workflows |
| `guides/aws-bedrock.md` | Use Hermes Agent with Amazon Bedrock — native Converse API, Anthropic SDK routing, OpenAI models via Bedrock Mantle, IAM authentication, Guardrails, and cross-region inference |
| `guides/azure-foundry.md` | Use Hermes Agent with Microsoft Foundry — OpenAI-style and Anthropic-style endpoints, auto-detection of transport and deployed models |
| `guides/cron-script-only.md` | Classic watchdog cron jobs that skip the LLM entirely — a script runs on schedule and its stdout gets delivered to your messaging platform. Memory alerts, disk alerts, CI pings, periodic health checks. |
| `guides/cron-troubleshooting.md` | Diagnose and fix common Hermes cron issues — jobs not firing, delivery failures, skill loading errors, and performance problems |
| `guides/daily-briefing-bot.md` | Build an automated daily briefing bot that researches topics, summarizes findings, and delivers them to Telegram or Discord every morning |
| `guides/delegation-patterns.md` | When and how to use subagent delegation — patterns for parallel research, code review, and multi-file work |
| `guides/desktop-native-signin.md` | How the Hermes Desktop app signs in to a gated gateway using your system browser and PKCE — no embedded webview, no session cookies |
| `guides/github-pr-review-agent.md` | Build an automated AI code reviewer that monitors your repos, reviews pull requests, and delivers feedback — hands-free |
| `guides/google-gemini.md` | Use Hermes Agent with Google Gemini — native AI Studio API, API-key setup, tool calling, streaming, and quota guidance |
| `guides/google-vertex.md` | Use Hermes Agent with Gemini on Google Cloud Vertex AI — OAuth2 service account or ADC, GCP billing and quotas, no static API key |
| `guides/local-llm-on-mac.md` | Set up a local OpenAI-compatible LLM server on macOS with llama.cpp or MLX, including model selection, memory optimization, and real benchmarks on Apple Silicon |
| `guides/local-ollama-setup.md` | Step-by-step guide to running Hermes Agent entirely on your own machine with Ollama and open-weight models like Gemma 4, no cloud API keys or paid subscriptions needed |
| `guides/manage-hermes-cloud-with-mcp.md` | Connect Hermes Agent to the Nous Portal MCP server so your local agent can list, start, stop, and manage your Hermes Cloud instances conversationally |
| `guides/microsoft-graph-app-registration.md` | Azure portal walkthrough for creating the app registration that powers the Teams meeting pipeline |
| `guides/migrate-from-openclaw.md` | Complete guide to migrating your OpenClaw / Clawdbot setup to Hermes Agent — what gets migrated, how config maps, and what to check after. |
| `guides/minimax-oauth.md` | Log into MiniMax via browser OAuth and use MiniMax-M2.7 models in Hermes Agent — no API key required |
| `guides/oauth-over-ssh.md` | How to complete browser-based OAuth (Spotify, MCP servers) when Hermes runs on a remote machine, container, or behind a jump box |
| `guides/operate-teams-meeting-pipeline.md` | Runbook, go-live checklist, and operator worksheet for the Microsoft Teams meeting pipeline |
| `guides/pipe-script-output.md` | Send text from any shell script, cron job, CI hook, or monitoring daemon to Telegram, Discord, Slack, Signal, and other platforms using `hermes send`. |
| `guides/python-library.md` | Embed AIAgent in your own Python scripts, web apps, or automation pipelines — no CLI required |
| `guides/run-hermes-with-nous-portal.md` | Start-to-finish walkthrough: subscribe, set up, switch models, enable gateway tools, and verify routing |
| `guides/run-nemotron-3-ultra-free.md` | Try NVIDIA Nemotron 3 Ultra on Nous Portal — free June 4–18 — with day 0 support in Hermes Agent |
| `guides/secure-hermes-on-a-work-machine.md` | A security-posture walkthrough for running Hermes Agent on the machine you live on — what the defaults protect, how to tighten further, and how to undo mistakes |
| `guides/team-telegram-assistant.md` | Step-by-step guide to setting up a Telegram bot that your whole team can use for code help, research, system admin, and more |
| `guides/tips.md` | Practical advice to get the most out of Hermes Agent — prompt tips, CLI shortcuts, context files, memory, cost optimization, and security |
| `guides/troubleshooting-agent-quality.md` | A diagnostic checklist for when Hermes seems less capable than before or forgets things mid-session — model switches, context pressure, wrong context detection, and the frozen memory snapshot |
| `guides/use-mcp-with-hermes.md` | A practical guide to connecting MCP servers to Hermes Agent, filtering their tools, and using them safely in real workflows |
| `guides/use-soul-with-hermes.md` | How to use SOUL.md to shape Hermes Agent's default voice, what belongs there, and how it differs from AGENTS.md and /personality |
| `guides/use-voice-mode-with-hermes.md` | A practical guide to setting up and using Hermes voice mode across CLI, Telegram, Discord, and Discord voice channels |
| `guides/webhook-github-pr-review.md` | Connect Hermes to GitHub so it automatically fetches PR diffs, reviews code changes, and posts comments — triggered by webhooks with no manual prompting |
| `guides/work-with-skills.md` | Find, install, use, and create skills — on-demand knowledge that teaches Hermes new workflows |
| `guides/xai-grok-oauth.md` | Sign in with your SuperGrok or X Premium+ subscription to use Grok models in Hermes Agent — no API key required |
| `index.mdx` | The self-improving AI agent built by Nous Research. A built-in learning loop that creates skills from experience, improves them during use, and remembers across sessions. |
| `integrations/buzz.md` | All three ways to connect Hermes Agent to Buzz — Block's Nostr-based human+agent workspace |
| `integrations/index.md` | Integrations |
| `integrations/nous-portal.md` | One subscription, 300+ frontier models, and the Tool Gateway — the recommended way to run Hermes Agent |
| `integrations/providers.md` | LLM and Model Providers |
| `reference/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `reference/automation-blueprints-catalog.mdx` | Ready-to-run automation blueprints — set one up from the dashboard, CLI, TUI, any messenger, or the desktop app. |
| `reference/cli-commands.md` | Authoritative reference for Hermes terminal commands and command families |
| `reference/cli-symbols.md` | What every symbol in the Hermes terminal UI means — transcript markers, status-bar badges, overlay glyphs, and approval prompts. |
| `reference/environment-variables.md` | Complete reference of all environment variables used by Hermes Agent |
| `reference/faq.md` | Frequently asked questions and solutions to common issues with Hermes Agent |
| `reference/mcp-config-reference.md` | Reference for Hermes Agent MCP configuration keys, filtering semantics, and utility-tool policy |
| `reference/model-catalog.md` | Remotely-hosted manifest driving curated model picker lists for OpenRouter and Nous Portal. |
| `reference/optional-skills-catalog.md` | Official optional skills shipped with hermes-agent — install via hermes skills install official/<category>/<skill> |
| `reference/package-management.md` | PM tool pins, Python environments, optional dependencies, and installation ownership |
| `reference/profile-commands.md` | Profile Commands Reference |
| `reference/skills-catalog.md` | Catalog of bundled skills that ship with Hermes Agent |
| `reference/slash-commands.md` | Complete reference for interactive CLI and messaging slash commands |
| `reference/tools-reference.md` | Authoritative reference for Hermes built-in tools, grouped by toolset |
| `reference/toolsets-reference.md` | Reference for Hermes core, composite, platform, and dynamic toolsets |
| `user-guide/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `user-guide/bot-mode.md` | Turn your Hermes profiles into a roster of named Bots — each with its own chat, role, model, memory, skills, and avatar. Bots run routines, share group chats, and message each other. |
| `user-guide/checkpoints-and-rollback.md` | Filesystem safety nets for destructive operations using shadow git repos and automatic snapshots |
| `user-guide/cli.md` | Master the Hermes Agent terminal interface — commands, keybindings, personalities, and more |
| `user-guide/configuration.md` | Configure Hermes Agent — config.yaml, providers, models, API keys, and more |
| `user-guide/configuring-models.md` | Configuring Models |
| `user-guide/desktop.md` | The native Hermes desktop app — a polished experience for chatting with Hermes, with streaming tool output, side-by-side previews, a file browser, voice, cron, profiles, skills, and settings. macOS, Windows, and Linux. |
| `user-guide/docker.md` | Running Hermes Agent in Docker and using Docker as a terminal backend |
| `user-guide/egress/index.md` | Egress proxy |
| `user-guide/egress/iron-proxy.md` | Egress credential-injection proxy (iron-proxy) |
| `user-guide/egress/network-isolation.md` | Segment Docker networks so the agent sandbox can only reach allowlisted hosts |
| `user-guide/features/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `user-guide/features/acp.md` | Use Hermes Agent inside ACP-compatible editors and collaboration platforms |
| `user-guide/features/api-server.md` | Expose hermes-agent as an OpenAI-compatible API for any frontend |
| `user-guide/features/batch-processing.md` | Generate agent trajectories at scale — parallel processing, checkpointing, and toolset distributions |
| `user-guide/features/bot-screen.md` | Bot Screen |
| `user-guide/features/browser.md` | Drive a real browser with browser_exec — Hermes-launched Chromium, cloud browsers, Lightpanda, or your own Chrome via CDP — for web interaction, form filling, scraping, and more. |
| `user-guide/features/built-in-plugins.md` | Plugins shipped with Hermes Agent that run automatically via lifecycle hooks — disk-cleanup and friends |
| `user-guide/features/code-execution.md` | Programmatic Python execution with RPC tool access — collapse multi-step workflows into a single turn |
| `user-guide/features/codex-app-server-runtime.md` | Codex App-Server Runtime (optional) |
| `user-guide/features/computer-use.md` | Computer Use |
| `user-guide/features/context-files.md` | Project context files — .hermes.md, AGENTS.md, CLAUDE.md, global SOUL.md, and .cursorrules — automatically injected into every conversation |
| `user-guide/features/context-references.md` | Inline @-syntax for attaching files, folders, git diffs, and URLs directly into your messages |
| `user-guide/features/credential-pools.md` | Pool multiple API keys or OAuth tokens per provider for automatic rotation and rate limit recovery. |
| `user-guide/features/credential-vault.md` | The agent signs into sites, pays and fills addresses for you without ever seeing a password. |
| `user-guide/features/cron.md` | Schedule automated tasks with natural language, manage them with one cron tool, and attach one or more skills |
| `user-guide/features/curator.md` | Background maintenance for agent-created skills — usage tracking, staleness, archival, and LLM-driven review |
| `user-guide/features/delegation.md` | Spawn isolated child agents for parallel workstreams with delegate_task |
| `user-guide/features/deliverable-mode.md` | How the agent ships generated charts, PDFs, spreadsheets, and other files as native attachments in messaging platforms. |
| `user-guide/features/document-extraction.md` | How read_file converts PDFs, Office documents, and notebooks to text — and what to do when a PDF is scanned images |
| `user-guide/features/extending-the-dashboard.md` | Build themes and plugins for the Hermes web dashboard — palettes, typography, layouts, custom tabs, shell slots, page-scoped slots, and backend API routes |
| `user-guide/features/fallback-providers.md` | Configure automatic failover to backup LLM providers when your primary model is unavailable. |
| `user-guide/features/goals.md` | Set a standing goal and let Hermes keep working across turns until it's done. Our take on the Ralph loop. |
| `user-guide/features/heartbeat.md` | A recurring prompt that re-enters your current session whenever it's idle — /heartbeat every 10m Check the deployment. |
| `user-guide/features/honcho.md` | AI-native persistent memory via Honcho — dialectic reasoning, multi-agent user modeling, and deep personalization |
| `user-guide/features/hooks.md` | Run custom code at key lifecycle points — log activity, send alerts, post to webhooks |
| `user-guide/features/image-generation.md` | Generate images via FAL.ai — 11 models including FLUX 2, GPT Image (1.5 & 2), Nano Banana Pro, Ideogram, Recraft V4 Pro, Krea 2, and more, selectable via `hermes tools`. |
| `user-guide/features/kanban-multi-gateway.md` | Running one kanban board across several per-profile gateways: single dispatcher, profile-owned delivery |
| `user-guide/features/kanban-tutorial.md` | Kanban tutorial |
| `user-guide/features/kanban-worker-lanes.md` | Kanban worker lanes |
| `user-guide/features/kanban.md` | Durable SQLite-backed task board for coordinating multiple Hermes profiles |
| `user-guide/features/language-packs.md` | Add or override UI languages for the CLI, gateway, TUI and Desktop with a plugin or a personal overlay |
| `user-guide/features/loops.md` | Re-run a prompt on a recurring interval inside your session — Hermes' take on Claude Code's /loop. |
| `user-guide/features/lsp.md` | Real language servers (pyright, gopls, rust-analyzer, …) wired into the post-write lint check used by write_file and patch. |
| `user-guide/features/mcp.md` | Connect Hermes Agent to external tool servers via MCP — and control exactly which MCP tools Hermes loads |
| `user-guide/features/memory-providers.md` | External memory provider plugins — Honcho, OpenViking, Mem0, Hindsight, Holographic, RetainDB, ByteRover, Supermemory |
| `user-guide/features/memory.md` | How Hermes Agent remembers across sessions — MEMORY.md, USER.md, and session search |
| `user-guide/features/mixture-of-agents.md` | Create named MoA presets that appear as selectable models under the Mixture of Agents provider |
| `user-guide/features/overview.md` | Features Overview |
| `user-guide/features/personality.md` | Customize Hermes Agent's personality with a global SOUL.md, built-in personalities, and custom persona definitions |
| `user-guide/features/pets.md` | Adopt an animated mascot that reacts to agent activity across the CLI, TUI, and desktop app |
| `user-guide/features/plugin-catalog.md` | Give Hermes new powers with reviewed plugins you can install in one click |
| `user-guide/features/plugins.md` | Extend Hermes with custom tools, hooks, and integrations via the plugin system |
| `user-guide/features/provider-routing.md` | Configure OpenRouter provider preferences to optimize for cost, speed, or quality. |
| `user-guide/features/skills.md` | On-demand knowledge documents — progressive disclosure, agent-managed skills, and the Skills Hub |
| `user-guide/features/skins.md` | Customize the Hermes CLI with built-in and user-defined skins |
| `user-guide/features/spotify.md` | Spotify |
| `user-guide/features/subscription-proxy.md` | Use your Nous Portal subscription (or other OAuth provider) as an OpenAI-compatible endpoint for external apps |
| `user-guide/features/tool-gateway.md` | One subscription, every tool. Web search, image generation, TTS, and cloud browsers — all routed through Nous Portal with no extra API keys. |
| `user-guide/features/tool-search.md` | Tool Search |
| `user-guide/features/tools.md` | Overview of Hermes Agent's tools — what's available, how toolsets work, and terminal backends |
| `user-guide/features/tts.md` | Text-to-speech and voice message transcription across all platforms |
| `user-guide/features/vision.md` | Paste images from your clipboard into the Hermes CLI for multimodal vision analysis. |
| `user-guide/features/voice-mode.md` | Real-time voice conversations with Hermes Agent — CLI, Telegram, Discord (DMs, text channels, and voice channels) |
| `user-guide/features/wake-word.md` | Hands-free 'Hey Hermes' wake word — start a voice session by speaking, the 'Hey Siri' way |
| `user-guide/features/web-dashboard.md` | Browser-based administration panel for managing configuration, API keys, MCP servers, messaging pairing, webhooks, the gateway, memory, credentials, sessions, logs, analytics, cron jobs, and skills |
| `user-guide/features/web-search.md` | Search the web and extract page content with multiple backend providers — including free self-hosted SearXNG. |
| `user-guide/features/x-search.md` | Search X (Twitter) posts and threads from within the agent using xAI's built-in x_search Responses tool — works with either a SuperGrok OAuth login or an XAI_API_KEY. |
| `user-guide/git-worktrees.md` | Run multiple Hermes agents safely on the same repository using git worktrees and isolated checkouts |
| `user-guide/import-from-other-agents.md` | One-command import of an OpenClaw (~/.openclaw), Claude Code (~/.claude), OpenAI Codex CLI (~/.codex) or Cursor (~/.cursor) setup into Hermes — instructions, rules, allowlists, MCP servers, skills, and memories. |
| `user-guide/local-models.md` | Run models entirely on your own machine — no account, no API key, nothing leaves your computer. |
| `user-guide/managed-scope.md` | Administrator-pinned, user-immutable config and secrets via a system-level managed directory |
| `user-guide/messaging/_category_.json` | JSON object with keys `label`, `position`, `link` |
| `user-guide/messaging/a2a.md` | A2A (Agent-to-Agent) |
| `user-guide/messaging/bluebubbles.md` | BlueBubbles (iMessage) |
| `user-guide/messaging/buzz.md` | Buzz |
| `user-guide/messaging/dingtalk.md` | Set up Hermes Agent as a DingTalk chatbot |
| `user-guide/messaging/discord.md` | Set up Hermes Agent as a Discord bot |
| `user-guide/messaging/email.md` | Set up Hermes Agent as an email assistant via IMAP/SMTP |
| `user-guide/messaging/feishu.md` | Set up Hermes Agent as a Feishu or Lark bot |
| `user-guide/messaging/google_chat.md` | Set up Hermes Agent as a Google Chat bot using Cloud Pub/Sub |
| `user-guide/messaging/homeassistant.md` | Control your smart home with Hermes Agent via the Home Assistant plugin from the plugin catalog. |
| `user-guide/messaging/index.md` | Chat with Hermes from Telegram, Discord, Slack, WhatsApp, Signal, SMS, Email, Home Assistant, Mattermost, Matrix, DingTalk, Yuanbao, Microsoft Teams, LINE, Raft, Webhooks, or any OpenAI-compatible frontend via the API s… |
| `user-guide/messaging/irc.md` | Markdown document |
| `user-guide/messaging/line.md` | Set up Hermes Agent as a LINE Messaging API bot |
| `user-guide/messaging/matrix.md` | Set up Hermes Agent as a Matrix bot |
| `user-guide/messaging/mattermost.md` | Set up Hermes Agent as a Mattermost bot |
| `user-guide/messaging/msgraph-webhook.md` | Receive Microsoft Graph change notifications (meetings, calendar, chat, etc.) in Hermes |
| `user-guide/messaging/ntfy.md` | ntfy |
| `user-guide/messaging/open-webui.md` | Connect Open WebUI to Hermes Agent via the OpenAI-compatible API server |
| `user-guide/messaging/photon.md` | Photon iMessage |
| `user-guide/messaging/qqbot.md` | QQ Bot |
| `user-guide/messaging/raft.md` | Connect Hermes Agent to Raft as an external agent via wake-channel bridge |
| `user-guide/messaging/relay.md` | Connect Hermes to messaging platforms through a relay connector that owns the platform credentials — enrollment, capabilities, config, and troubleshooting |
| `user-guide/messaging/signal.md` | Set up Hermes Agent as a Signal messenger bot via signal-cli daemon |
| `user-guide/messaging/simplex.md` | SimpleX Chat |
| `user-guide/messaging/slack.md` | Set up Hermes Agent as a Slack bot using Socket Mode |
| `user-guide/messaging/sms.md` | Set up Hermes Agent as an SMS chatbot via Twilio |
| `user-guide/messaging/teams-meetings.md` | Set up the Microsoft Teams meeting summary pipeline with Microsoft Graph webhooks |
| `user-guide/messaging/teams.md` | Set up Hermes Agent as a Microsoft Teams bot |
| `user-guide/messaging/telegram.md` | Set up Hermes Agent as a Telegram bot |
| `user-guide/messaging/webhooks.md` | Receive events from GitHub, GitLab, and other services to trigger Hermes agent runs |
| `user-guide/messaging/wecom-callback.md` | WeCom Callback (Self-Built App) |
| `user-guide/messaging/wecom.md` | Connect Hermes Agent to WeCom via the AI Bot WebSocket gateway |
| `user-guide/messaging/weixin.md` | Connect Hermes Agent to personal WeChat accounts via the iLink Bot API |
| `user-guide/messaging/whatsapp-cloud.md` | Set up Hermes Agent as a WhatsApp bot via Meta's official Business Cloud API |
| `user-guide/messaging/whatsapp.md` | Set up Hermes Agent as a WhatsApp bot via the built-in Baileys bridge |
| `user-guide/messaging/yuanbao.md` | Connect Hermes Agent to the Yuanbao enterprise messaging platform via WebSocket gateway |
| `user-guide/multi-connection-desktop.md` | Connecting Desktop to Many Hermes Instances |
| `user-guide/multi-profile-gateways.md` | Running Many Gateways at Once |
| `user-guide/profile-distributions.md` | Profile Distributions: Share a Whole Agent |
| `user-guide/profiles.md` | Profiles: Running Multiple Agents |
| `user-guide/remote-config.md` | Serve each profile's config from the config plane instead of config.yaml |
| `user-guide/secrets/bitwarden.md` | Bitwarden Secrets Manager |
| `user-guide/secrets/command.md` | Command Helper Secret Source |
| `user-guide/secrets/index.md` | Secrets |
| `user-guide/secrets/onepassword.md` | 1Password |
| `user-guide/security.md` | Security model, dangerous command approval, user authorization, container isolation, and production deployment best practices |
| `user-guide/session-storage-recovery.md` | What to do when Hermes says another process holds an old copy of the session database's write-ahead log, and what the files beside state.db are |
| `user-guide/sessions.md` | Session persistence, resume, search, management, and per-platform session tracking |
| `user-guide/skills/bundled/apple/apple-apple-notes.md` | Manage Apple Notes via memo CLI: create, search, edit |
| `user-guide/skills/bundled/apple/apple-apple-reminders.md` | Apple Reminders via remindctl: add, list, complete |
| `user-guide/skills/bundled/apple/apple-findmy.md` | Track Apple devices/AirTags via FindMy.app on macOS |
| `user-guide/skills/bundled/apple/apple-imessage.md` | Send and receive iMessages/SMS via the imsg CLI on macOS |
| `user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-claude-code.md` | Delegate coding to Claude Code CLI (features, PRs) |
| `user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-codex.md` | Delegate coding to OpenAI Codex CLI (features, PRs) |
| `user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-computer-use.md` | Drive the desktop background-first; escalate on signal |
| `user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-hermes-agent.md` | Use, configure, theme, extend, and orchestrate Hermes Agent |
| `user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-opencode.md` | Delegate coding to OpenCode CLI (features, PR review) |
| `user-guide/skills/bundled/creative/creative-architecture-diagram.md` | Dark-themed SVG architecture/cloud/infra diagrams as HTML |
| `user-guide/skills/bundled/creative/creative-ascii-video.md` | ASCII video: convert video/audio to colored ASCII MP4/GIF |
| `user-guide/skills/bundled/creative/creative-baoyu-infographic.md` | Infographics: 21 layouts x 21 styles (信息图, 可视化) |
| `user-guide/skills/bundled/creative/creative-claude-design.md` | Design one-off HTML artifacts (landing, deck, prototype) |
| `user-guide/skills/bundled/creative/creative-design-md.md` | Author/validate/export Google's DESIGN.md token spec files |
| `user-guide/skills/bundled/creative/creative-humanizer.md` | Humanize text: strip AI-isms and add real voice |
| `user-guide/skills/bundled/creative/creative-manim-video.md` | Manim CE animations: 3Blue1Brown math/algo videos |
| `user-guide/skills/bundled/creative/creative-p5js.md` | p5.js sketches: gen art, shaders, interactive, 3D |
| `user-guide/skills/bundled/creative/creative-popular-web-designs.md` | 54 real design systems (Stripe, Linear, Vercel) as HTML/CSS |
| `user-guide/skills/bundled/creative/creative-songwriting-and-ai-music.md` | Songwriting craft and Suno AI music prompts |
| `user-guide/skills/bundled/devops/devops-sdlc-review.md` | Review Kanban handoffs and route verified outcomes |
| `user-guide/skills/bundled/email/email-email-inbox-triage.md` | Triage an inbox: prioritize threads, draft replies safely |
| `user-guide/skills/bundled/email/email-himalaya.md` | Himalaya CLI: IMAP/SMTP email from terminal |
| `user-guide/skills/bundled/media/media-gif-search.md` | Search/download GIFs from Tenor via curl + jq |
| `user-guide/skills/bundled/media/media-songsee.md` | Audio spectrograms/features (mel, chroma, MFCC) via CLI |
| `user-guide/skills/bundled/media/media-youtube-content.md` | YouTube transcripts to summaries, threads, blogs |
| `user-guide/skills/bundled/note-taking/note-taking-obsidian.md` | Read, search, create, and edit notes in the Obsidian vault |
| `user-guide/skills/bundled/productivity/productivity-airtable.md` | Airtable REST API via curl |
| `user-guide/skills/bundled/productivity/productivity-box.md` | Box manages cloud files, sharing, search, and metadata |
| `user-guide/skills/bundled/productivity/productivity-document-to-action-items.md` | Extract cited obligations, deadlines, tasks from documents |
| `user-guide/skills/bundled/productivity/productivity-docx.md` | Create, read, edit, template, and review Word .docx files |
| `user-guide/skills/bundled/productivity/productivity-google-workspace.md` | Gmail, Calendar, Drive, Docs, Sheets via gws CLI or Python |
| `user-guide/skills/bundled/productivity/productivity-maps.md` | Geocode, POIs, routes, timezones via OpenStreetMap/OSRM |
| `user-guide/skills/bundled/productivity/productivity-meeting-action-items.md` | Turn meeting notes into cited decisions, owners, tickets |
| `user-guide/skills/bundled/productivity/productivity-notion.md` | Notion API + ntn CLI: pages, databases, markdown, Workers |
| `user-guide/skills/bundled/productivity/productivity-pdf.md` | PDF files: create, read, merge, fill, OCR, edit text |
| `user-guide/skills/bundled/productivity/productivity-powerpoint.md` | Create, read, edit .pptx decks with python-pptx |
| `user-guide/skills/bundled/productivity/productivity-product-price-monitor.md` | Watch product, flight, or listing prices; alert on target |
| `user-guide/skills/bundled/productivity/productivity-teams-meeting-pipeline.md` | Teams meeting summaries, job replay, Graph subscriptions |
| `user-guide/skills/bundled/productivity/productivity-weekly-review-planning.md` | Weekly reset: commitments, stalled work, next-week plan |
| `user-guide/skills/bundled/productivity/productivity-xlsx.md` | Create, read, edit Excel .xlsx workbooks and CSVs |
| `user-guide/skills/bundled/research/research-arxiv.md` | Search arXiv papers by keyword, author, category, or ID |
| `user-guide/skills/bundled/research/research-competitor-news-monitor.md` | Watch named companies for material news; cited digests |
| `user-guide/skills/bundled/research/research-grounded-citations.md` | Ground answers and documents in cited, verifiable sources |
| `user-guide/skills/bundled/research/research-llm-wiki.md` | Karpathy's LLM Wiki: build/query interlinked markdown KB |
| `user-guide/skills/bundled/social-media/social-media-xurl.md` | X/Twitter via xurl CLI: raw post search, posting, DM, media |
| `user-guide/skills/bundled/software-development/software-development-codebase-inspection.md` | Inspect codebases w/ pygount: LOC, languages, ratios |
| `user-guide/skills/bundled/software-development/software-development-dogfood.md` | Exploratory QA of web apps: find bugs, evidence, reports |
| `user-guide/skills/bundled/software-development/software-development-github.md` | GitHub via gh CLI: PRs, issues, reviews, repos, auth |
| `user-guide/skills/bundled/software-development/software-development-hermes-agent-skill-authoring.md` | Author in-repo SKILL.md files: frontmatter and structure |
| `user-guide/skills/bundled/software-development/software-development-inspecting-hermes-desktop-dom.md` | Read the live Hermes desktop DOM/CSS over CDP |
| `user-guide/skills/bundled/software-development/software-development-node-inspect-debugger.md` | Debug Node.js via --inspect + Chrome DevTools Protocol CLI |
| `user-guide/skills/bundled/software-development/software-development-python-debugpy.md` | Debug Python: pdb REPL + debugpy remote (DAP) |
| `user-guide/skills/bundled/software-development/software-development-requesting-code-review.md` | Pre-commit review: security scan, quality gates, auto-fix |
| `user-guide/skills/bundled/software-development/software-development-simplify-code.md` | Parallel 4-agent cleanup of recent code changes |
| `user-guide/skills/bundled/software-development/software-development-spike.md` | Throwaway experiments to validate an idea before build |
| `user-guide/skills/bundled/software-development/software-development-systematic-debugging.md` | 4-phase root cause debugging: understand bugs before fixing |
| `user-guide/skills/bundled/software-development/software-development-test-driven-development.md` | TDD: enforce RED-GREEN-REFACTOR, tests before code |
| `user-guide/skills/bundled/web/web-blocked-page-recovery.md` | Use when a fetch fails: 403/429, paywall, WAF, bot wall |
| `user-guide/skills/google-workspace.md` | Send email, manage calendar events, search Drive, read/write Sheets, and access Docs — all through OAuth2-authenticated Google APIs |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-agent-merge-conflict-arbiter.md` | Neutral arbiter for merge conflicts between two agents |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-antigravity-cli.md` | Operate the Antigravity CLI (agy): plugins, auth, sandbox |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-blackbox.md` | Delegate coding tasks to the Blackbox AI multi-model CLI |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-dynamic-workflow.md` | Plan-in-code fan-outs, adversarial verification, waves |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-grok.md` | Delegate coding to xAI Grok Build CLI (features, PRs) |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-honcho.md` | Configure and troubleshoot Honcho memory for Hermes |
| `user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-openhands.md` | Delegate coding to OpenHands CLI (model-agnostic, LiteLLM) |
| `user-guide/skills/optional/blockchain/blockchain-evm.md` | Read-only EVM client: wallets, tokens, gas across 8 chains |
| `user-guide/skills/optional/blockchain/blockchain-hyperliquid.md` | Hyperliquid market data, account history, trade review |
| `user-guide/skills/optional/blockchain/blockchain-solana.md` | Query Solana wallets, tokens, txs, and NFTs in USD |
| `user-guide/skills/optional/communication/communication-one-three-one-rule.md` | 1-3-1 decision briefs: problem, three options, one pick |
| `user-guide/skills/optional/creative/creative-ai-presenter-video.md` | Make a verified AI presenter video from script + image |
| `user-guide/skills/optional/creative/creative-anatomy.md` | Explain an idea as an interactive isometric machine figure |
| `user-guide/skills/optional/creative/creative-archify.md` | Validated interactive HTML diagrams, upstream-maintained |
| `user-guide/skills/optional/creative/creative-ascii-art.md` | ASCII art: pyfiglet, cowsay, boxes, image-to-ascii |
| `user-guide/skills/optional/creative/creative-audiocraft-audio-generation.md` | AudioCraft: MusicGen text-to-music, AudioGen text-to-sound |
| `user-guide/skills/optional/creative/creative-auteur.md` | Design and build cinematic, award-level web pages |
| `user-guide/skills/optional/creative/creative-baoyu-article-illustrator.md` | Article illustrations: type × style × palette consistency |
| `user-guide/skills/optional/creative/creative-baoyu-comic.md` | Knowledge comics (知识漫画): educational, biography, tutorial |
| `user-guide/skills/optional/creative/creative-brag-slim.md` | Launch video from a project or URL, upstream-maintained |
| `user-guide/skills/optional/creative/creative-brag.md` | Project launch video via Hyperframes, upstream-maintained |
| `user-guide/skills/optional/creative/creative-comfyui.md` | Generate images, video, and audio via diffusion workflows |
| `user-guide/skills/optional/creative/creative-concept-diagrams.md` | Generate flat, minimal educational SVG visuals as HTML |
| `user-guide/skills/optional/creative/creative-creative-ideation.md` | Generate ideas via named methods from creative practice |
| `user-guide/skills/optional/creative/creative-draw-your-font.md` | Turn a handwriting photo into an installable TTF font |
| `user-guide/skills/optional/creative/creative-dream-loop.md` | Build stunning 3D scenes via a concept-art fidelity loop |
| `user-guide/skills/optional/creative/creative-excalidraw.md` | Hand-drawn Excalidraw JSON diagrams (arch, flow, seq) |
| `user-guide/skills/optional/creative/creative-heartmula.md` | HeartMuLa: Suno-like song generation from lyrics + tags |
| `user-guide/skills/optional/creative/creative-hyperframes.md` | Render MP4/WebM videos from HTML compositions |
| `user-guide/skills/optional/creative/creative-impeccable.md` | Frontend design guidance, upstream-maintained (impeccable) |
| `user-guide/skills/optional/creative/creative-ip-as-logo.md` | Design minimal cute IP mascot marks readable at 32px |
| `user-guide/skills/optional/creative/creative-kanban-video-orchestrator.md` | Plan and run multi-agent video production pipelines |
| `user-guide/skills/optional/creative/creative-meme-generation.md` | Create meme PNGs from templates with Pillow text overlay |
| `user-guide/skills/optional/creative/creative-mono-color.md` | Generate one- or two-ink editorial print poster images |
| `user-guide/skills/optional/creative/creative-pixel-art.md` | Pixel art w/ era palettes (NES, Game Boy, PICO-8) |
| `user-guide/skills/optional/creative/creative-pretext.md` | Build creative browser demos with DOM-free text layout |
| `user-guide/skills/optional/creative/creative-simple-english.md` | Rewrite text to ASD-STE100 Simplified Technical English |
| `user-guide/skills/optional/creative/creative-sketch.md` | Throwaway HTML mockups: 2-3 design variants to compare |
| `user-guide/skills/optional/creative/creative-social-media-content-calendar.md` | Plan multi-platform social campaigns: briefs to posting |
| `user-guide/skills/optional/creative/creative-system-atlas.md` | Build explorable isometric architecture atlases as HTML |
| `user-guide/skills/optional/creative/creative-tldraw-offline.md` | Drive and script tldraw offline canvases with an agent |
| `user-guide/skills/optional/creative/creative-unreal-mcp.md` | Automate Unreal Engine editor scenes, actors, and renders |
| `user-guide/skills/optional/data-science/data-science-jupyter-notebook.md` | Iterative Python via live Jupyter kernel (hamelnb) |
| `user-guide/skills/optional/devops/devops-actual-setup.md` | Set up Actual Computer (actual.inc) inference in Hermes |
| `user-guide/skills/optional/devops/devops-docker-management.md` | Manage Docker containers, images, volumes, and Compose |
| `user-guide/skills/optional/devops/devops-hermes-s6-container-supervision.md` | Modify or debug s6 services in the Hermes Docker image |
| `user-guide/skills/optional/devops/devops-inference-sh-cli.md` | Run 150+ AI apps (image, video, LLM) via inference.sh CLI |
| `user-guide/skills/optional/devops/devops-pinggy-tunnel.md` | Zero-install localhost tunnels over SSH via Pinggy |
| `user-guide/skills/optional/devops/devops-setup-wizard-generator.md` | Generate a bash wizard guiding a human through manual setup |
| `user-guide/skills/optional/devops/devops-watchers.md` | Poll RSS, JSON APIs, and GitHub with watermark dedup |
| `user-guide/skills/optional/dogfood/dogfood-adversarial-ux-test.md` | Roleplay a hostile user to find and triage UX pain points |
| `user-guide/skills/optional/email/email-agentmail.md` | Use when an agent needs AgentMail CLI email inboxes |
| `user-guide/skills/optional/finance/finance-3-statement-model.md` | Build integrated IS/BS/CF financial workbooks in Excel |
| `user-guide/skills/optional/finance/finance-comps-analysis.md` | Build comparable-company valuation workbooks in Excel |
| `user-guide/skills/optional/finance/finance-dcf-model.md` | Build discounted cash flow valuation workbooks in Excel |
| `user-guide/skills/optional/finance/finance-excel-author.md` | Build auditable financial workbooks headless via openpyxl |
| `user-guide/skills/optional/finance/finance-lbo-model.md` | Build leveraged buyout workbooks with IRR/MOIC in Excel |
| `user-guide/skills/optional/finance/finance-merger-model.md` | Build M&A accretion/dilution workbooks in Excel |
| `user-guide/skills/optional/finance/finance-polymarket.md` | Query Polymarket: markets, prices, orderbooks, history |
| `user-guide/skills/optional/finance/finance-pptx-author.md` | Build PowerPoint decks headless with python-pptx |
| `user-guide/skills/optional/finance/finance-stocks.md` | Stock quotes, history, search, compare, crypto via Yahoo |
| `user-guide/skills/optional/gaming/gaming-minecraft-modpack-server.md` | Host modded Minecraft servers (CurseForge, Modrinth) |
| `user-guide/skills/optional/gaming/gaming-pokemon-player.md` | Play Pokemon via headless emulator + RAM reads |
| `user-guide/skills/optional/health/health-fitness-nutrition.md` | Workout planning, macros, and body metrics via wger/USDA |
| `user-guide/skills/optional/health/health-neuroskill-bci.md` | Use live BCI cognitive and mood state from NeuroSkill |
| `user-guide/skills/optional/mcp/mcp-fastmcp.md` | Build, test, and deploy Python MCP servers |
| `user-guide/skills/optional/mcp/mcp-mcp-oauth-remote-gateway.md` | Manual OAuth for remote MCP servers on headless gateways |
| `user-guide/skills/optional/mcp/mcp-mcporter.md` | List, auth, and call MCP servers/tools from the terminal |
| `user-guide/skills/optional/mlops/mlops-accelerate.md` | Run PyTorch training across GPUs with minimal changes |
| `user-guide/skills/optional/mlops/mlops-chroma.md` | Embedding database for RAG and semantic search |
| `user-guide/skills/optional/mlops/mlops-clip.md` | Zero-shot image classification and image-text search |
| `user-guide/skills/optional/mlops/mlops-evaluation-evaluating-llms-harness.md` | lm-eval-harness: benchmark LLMs (MMLU, GSM8K, etc.) |
| `user-guide/skills/optional/mlops/mlops-evaluation-weights-and-biases.md` | W&B: log ML experiments, sweeps, model registry, dashboards |
| `user-guide/skills/optional/mlops/mlops-faiss.md` | Fast vector similarity search at billion scale |
| `user-guide/skills/optional/mlops/mlops-flash-attention.md` | Speed up long-sequence transformer training and inference |
| `user-guide/skills/optional/mlops/mlops-guidance.md` | Constrain LLM output with grammars; guarantee valid JSON |
| `user-guide/skills/optional/mlops/mlops-huggingface-tokenizers.md` | Fast BPE/WordPiece tokenization and custom vocab training |
| `user-guide/skills/optional/mlops/mlops-inference-llama-cpp.md` | llama.cpp local GGUF inference + HF Hub model discovery |
| `user-guide/skills/optional/mlops/mlops-inference-outlines.md` | Outlines: structured JSON/regex/Pydantic LLM generation |
| `user-guide/skills/optional/mlops/mlops-inference-serving-llms-vllm.md` | vLLM: high-throughput LLM serving, OpenAI API, quantization |
| `user-guide/skills/optional/mlops/mlops-instructor.md` | Structured LLM outputs validated with Pydantic |
| `user-guide/skills/optional/mlops/mlops-lambda-labs.md` | On-demand GPU cloud instances for ML training |
| `user-guide/skills/optional/mlops/mlops-llava.md` | Vision-language chat: VQA, captioning, image dialogue |
| `user-guide/skills/optional/mlops/mlops-modal.md` | Serverless GPU cloud for ML jobs and model APIs |
| `user-guide/skills/optional/mlops/mlops-models-huggingface-hub.md` | HuggingFace hf CLI: search/download/upload models, datasets |
| `user-guide/skills/optional/mlops/mlops-models-segment-anything-model.md` | SAM: zero-shot image segmentation via points, boxes, masks |
| `user-guide/skills/optional/mlops/mlops-nemo-curator.md` | Curate LLM training data: dedupe, filter, PII redaction |
| `user-guide/skills/optional/mlops/mlops-obliteratus.md` | OBLITERATUS: abliterate LLM refusals (diff-in-means) |
| `user-guide/skills/optional/mlops/mlops-peft.md` | Fine-tune large LLMs with LoRA on limited GPU memory |
| `user-guide/skills/optional/mlops/mlops-pinecone.md` | Managed vector DB for production RAG and search |
| `user-guide/skills/optional/mlops/mlops-pytorch-fsdp.md` | Fully sharded data-parallel training for large models |
| `user-guide/skills/optional/mlops/mlops-pytorch-lightning.md` | Clean training loops with built-in distributed support |
| `user-guide/skills/optional/mlops/mlops-qdrant.md` | Vector search engine for production RAG systems |
| `user-guide/skills/optional/mlops/mlops-research-dspy.md` | DSPy: declarative LM programs, auto-optimize prompts, RAG |
| `user-guide/skills/optional/mlops/mlops-saelens.md` | Train sparse autoencoders to interpret model features |
| `user-guide/skills/optional/mlops/mlops-simpo.md` | Reference-free preference alignment, simpler than DPO |
| `user-guide/skills/optional/mlops/mlops-slime.md` | RL post-training for LLMs with Megatron and SGLang |
| `user-guide/skills/optional/mlops/mlops-stable-diffusion.md` | Text-to-image generation, inpainting, and img2img |
| `user-guide/skills/optional/mlops/mlops-tensorrt-llm.md` | High-throughput LLM inference on NVIDIA GPUs |
| `user-guide/skills/optional/mlops/mlops-torchtitan.md` | Pretrain LLMs at scale with PyTorch 4D parallelism |
| `user-guide/skills/optional/mlops/mlops-training-axolotl.md` | Axolotl: YAML LLM fine-tuning (LoRA, DPO, GRPO) |
| `user-guide/skills/optional/mlops/mlops-training-trl-fine-tuning.md` | TRL: SFT, DPO, GRPO, RLOO reward modeling for LLM RLHF |
| `user-guide/skills/optional/mlops/mlops-training-unsloth.md` | Unsloth: 2-5x faster LoRA/QLoRA fine-tuning, less VRAM |
| `user-guide/skills/optional/mlops/mlops-whisper.md` | Transcribe and translate speech in 99 languages |
| `user-guide/skills/optional/payments/payments-mpp-agent.md` | Pay HTTP 402 APIs via Machine Payments Protocol (MPP) |
| `user-guide/skills/optional/payments/payments-stripe-link-cli.md` | Agent payments via Stripe Link — cards, SPT, approvals |
| `user-guide/skills/optional/payments/payments-stripe-projects.md` | Provision SaaS services + sync creds via Stripe Projects |
| `user-guide/skills/optional/productivity/productivity-canvas.md` | Fetch Canvas LMS courses and assignments via API token |
| `user-guide/skills/optional/productivity/productivity-decision-questionnaire.md` | Turn an unanswerable decision into a questionnaire doc |
| `user-guide/skills/optional/productivity/productivity-here-now.md` | Publish sites to {slug}.here.now and store files in Drives |
| `user-guide/skills/optional/productivity/productivity-live-dashboard.md` | Build self-updating dashboards from live sources |
| `user-guide/skills/optional/productivity/productivity-memento-flashcards.md` | Spaced-repetition flashcards: create, review, quiz, export |
| `user-guide/skills/optional/productivity/productivity-property-listings.md` | Present property and rental listings as desktop cards |
| `user-guide/skills/optional/productivity/productivity-shop.md` | Shop catalog search, checkout, order tracking, returns |
| `user-guide/skills/optional/productivity/productivity-shopify.md` | Query Shopify Admin/Storefront GraphQL APIs via curl |
| `user-guide/skills/optional/productivity/productivity-siyuan.md` | Query and edit a SiYuan knowledge base via its API |
| `user-guide/skills/optional/productivity/productivity-telephony.md` | Provision Twilio numbers, SMS/MMS, and AI outbound calls |
| `user-guide/skills/optional/research/research-bioinformatics.md` | Gateway to 400+ genomics and computational biology skills |
| `user-guide/skills/optional/research/research-blogwatcher.md` | Monitor blogs and RSS/Atom feeds via blogwatcher-cli tool |
| `user-guide/skills/optional/research/research-darwinian-evolver.md` | Evolve prompts/regex/SQL/code with Imbue's evolution loop |
| `user-guide/skills/optional/research/research-domain-intel.md` | Passive recon of subdomains, SSL certs, WHOIS, and DNS |
| `user-guide/skills/optional/research/research-drug-discovery.md` | Drug discovery: ChEMBL search, drug-likeness, interactions |
| `user-guide/skills/optional/research/research-duckduckgo-search.md` | Free keyless web, news, and image search via ddgs |
| `user-guide/skills/optional/research/research-gitnexus-explorer.md` | Serve an interactive codebase knowledge graph web UI |
| `user-guide/skills/optional/research/research-osint-investigation.md` | Follow the money via public records and sanctions data |
| `user-guide/skills/optional/research/research-parallel-cli.md` | Agent-native web search, deep research, and enrichment |
| `user-guide/skills/optional/research/research-pinecone-research.md` | Agent RAG and long-term memory with Pinecone |
| `user-guide/skills/optional/research/research-qmd.md` | Hybrid local search over notes, docs, and transcripts |
| `user-guide/skills/optional/research/research-research-paper-writing.md` | Write ML papers for NeurIPS/ICML/ICLR: design→submit |
| `user-guide/skills/optional/research/research-rss-feeds.md` | Read RSS, Atom, JSON feeds; discover feeds behind a page |
| `user-guide/skills/optional/research/research-scrapling.md` | Scrape sites with stealth browsing and Cloudflare bypass |
| `user-guide/skills/optional/research/research-searxng-search.md` | Free keyless meta-search aggregating 70+ engines |
| `user-guide/skills/optional/security/security-1password.md` | Set up op CLI, sign in, and read or inject secrets |
| `user-guide/skills/optional/security/security-godmode.md` | Jailbreak LLMs: Parseltongue, GODMODE, ULTRAPLINIAN |
| `user-guide/skills/optional/security/security-oss-forensics.md` | GitHub supply-chain forensics: recovery, IOCs, reporting |
| `user-guide/skills/optional/security/security-sherlock.md` | Find accounts for a username across 400+ platforms |
| `user-guide/skills/optional/security/security-unbroker.md` | Remove your info from data-broker sites, by name or phone |
| `user-guide/skills/optional/security/security-web-pentest.md` | Authorized web pentest: recon, proof-based exploits, report |
| `user-guide/skills/optional/smart-home/smart-home-openhue.md` | Control Philips Hue lights, scenes, rooms via OpenHue CLI |
| `user-guide/skills/optional/social-media/social-media-reddit-reading.md` | Read Reddit: subreddits, search, threads, users |
| `user-guide/skills/optional/software-development/software-development-ast-grep.md` | AST-aware structural code search and rewrite via ast-grep |
| `user-guide/skills/optional/software-development/software-development-code-wiki.md` | Generate wiki docs + Mermaid diagrams for any codebase |
| `user-guide/skills/optional/software-development/software-development-grill-me.md` | Adversarial plan interview before implementation |
| `user-guide/skills/optional/software-development/software-development-pr-lens.md` | Draw code changes as animated architecture/data-flow SVGs |
| `user-guide/skills/optional/software-development/software-development-rest-graphql-debug.md` | Debug REST/GraphQL APIs: status codes, auth, schemas, repro |
| `user-guide/skills/optional/software-development/software-development-subagent-driven-development.md` | Execute plans via delegate_task subagents (2-stage review) |
| `user-guide/skills/optional/web-development/web-development-cloudflare-temporary-deploy.md` | Deploy a Worker live, no account, via wrangler --temporary |
| `user-guide/skills/optional/web-development/web-development-har-derived-api-client.md` | Record a site's XHR into a HAR, derive an HTTP client |
| `user-guide/skills/optional/web-development/web-development-page-agent.md` | Embed an in-page natural-language GUI copilot in web apps |
| `user-guide/skills/optional/web-development/web-development-publish-site.md` | Versioned site deploys to GitHub/Cloudflare/Netlify Pages |
| `user-guide/skills/optional/web-development/web-development-scrollcraft.md` | Premium scroll-driven landing pages; scroll = timeline |
| `user-guide/skills/optional/yuanbao/yuanbao-yuanbao.md` | Yuanbao (元宝) groups: @mention users, query info/members |
| `user-guide/switching-to-source.md` | Run a separate source checkout without overwriting packaged files or losing track of user data |
| `user-guide/tui.md` | Launch the modern terminal UI for Hermes — mouse-friendly, rich overlays, and non-blocking input. |
| `user-guide/which-file-does-what.md` | SOUL.md vs USER.md vs MEMORY.md vs AGENTS.md — a one-page map of the agent's files, who writes each one, and when the agent actually sees them |
| `user-guide/windows-native.md` | Run Hermes Agent natively on Windows 10 / 11 — install, feature matrix, UTF-8 console, Git Bash, gateway as a Scheduled Task, editor handling, PATH, uninstall, and common pitfalls |
| `user-guide/windows-wsl-quickstart.md` | Run Hermes Agent on Windows via WSL2 — setup, filesystem access between Windows and Linux, networking, and common pitfalls |
| `user-stories.mdx` | Real stories from the Hermes Agent community — what people are actually building, scraped from X, GitHub, Reddit, Hacker News, YouTube, blogs, and podcasts. |

## `website/i18n/`

| File | What it does |
|---|---|
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/acp-internals.md` | ACP 适配器的工作原理：生命周期、会话、事件桥接、审批流程与工具渲染 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/adding-platform-adapters.md` | 添加平台适配器 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/adding-providers.md` | 如何向 Hermes Agent 添加新的推理 provider——认证、运行时解析、CLI 流程、适配器、测试与文档 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/adding-tools.md` | 如何向 Hermes Agent 添加新工具——schema、handler、注册与 toolset |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/agent-loop.md` | AIAgent 执行流程、API 模式、工具、回调及回退行为的详细说明 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/architecture.md` | Hermes Agent 内部结构——主要子系统、执行路径、数据流及延伸阅读指引 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/browser-supervisor.md` | Browser CDP Supervisor — 设计文档 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/context-compression-and-caching.md` | Hermes Agent 如何通过双重压缩系统和 Anthropic prompt 缓存高效管理上下文窗口。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/context-engine-plugin.md` | 如何构建替换内置 ContextCompressor 的 context engine 插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/contributing.md` | 如何为 Hermes Agent 做贡献 — 开发环境配置、代码风格、PR 流程 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/creating-skills.md` | 如何为 Hermes Agent 创建 skill——SKILL.md 格式、规范与发布 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/cron-internals.md` | Hermes 如何存储、调度、编辑、暂停、加载技能以及投递 cron 任务 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/extending-the-cli.md` | 构建包装 CLI，通过自定义 widget、快捷键和布局变更来扩展 Hermes TUI |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/gateway-internals.md` | 消息 gateway 如何启动、授权用户、路由会话以及投递消息 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/image-gen-provider-plugin.md` | 如何为 Hermes Agent 构建图像生成后端插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/memory-provider-plugin.md` | 如何为 Hermes Agent 构建 memory provider 插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/model-provider-plugin.md` | 如何为 Hermes Agent 构建模型提供商（推理后端）插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/plugin-llm-access.md` | 通过 ctx.llm 在 plugin 内部运行任意 LLM 调用——支持对话或结构化输出、同步或异步。宿主持有认证凭据，失败关闭信任门控，可选 JSON Schema 验证。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/plugins/index.md` | 逐步指南：构建包含工具、钩子、数据文件和技能的完整 Hermes 插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/programmatic-integration.md` | 从外部程序驱动 hermes-agent 的三种协议：ACP、TUI gateway JSON-RPC 以及兼容 OpenAI 的 HTTP API |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/prompt-assembly.md` | Hermes 如何构建系统 prompt、保持缓存稳定性并注入临时层 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/provider-runtime.md` | Hermes 如何在运行时解析 provider、凭据、API 模式及辅助模型 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/session-storage.md` | 会话存储 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/tools-runtime.md` | 工具注册表、toolset、调度及终端环境的运行时行为 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/trajectory-format.md` | 轨迹格式 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/video-gen-provider-plugin.md` | 如何为 Hermes Agent 构建视频生成后端插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/developer-guide/web-search-provider-plugin.md` | 如何为 Hermes Agent 构建网页搜索/提取/爬取后端插件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/installation.md` | 在 Linux、macOS、WSL2 或原生 Windows 上安装 Hermes Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/learning-path.md` | 根据您的经验水平和目标，选择适合您的 Hermes Agent 文档学习路径。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/nix-setup.md` | 使用 Nix 安装和部署 Hermes Agent——从快速 `nix run` 到完全声明式的 NixOS 模块（含容器模式） |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/quickstart.md` | 与 Hermes Agent 的第一次对话——从安装到开始聊天，5 分钟内完成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/termux.md` | 通过签名 APT 仓库安装适用于 aarch64 Android 的 Hermes 预发布软件包 |
| `zh-Hans/docusaurus-plugin-content-docs/current/getting-started/updating.md` | 如何将 Hermes Agent 更新至最新版本或将其卸载 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/automate-with-cron.md` | 使用 Hermes cron 的真实自动化模式——监控、报告、数据管道与多技能工作流 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/automation-blueprints.md` | 开箱即用的自动化蓝图——定时任务、GitHub 事件触发、API webhook 及多技能工作流 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/aws-bedrock.md` | 将 Hermes Agent 与 Amazon Bedrock 配合使用——原生 Converse API、IAM 身份验证、Guardrails 及跨区域推理 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/azure-foundry.md` | 将 Hermes Agent 与 Microsoft Foundry 配合使用——OpenAI 风格与 Anthropic 风格端点、传输协议与已部署模型的自动检测 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/cron-script-only.md` | 完全跳过 LLM 的经典看门狗 cron 任务——脚本按计划运行，其 stdout 输出直接投递到你的消息平台。内存告警、磁盘告警、CI 通知、定期健康检查。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/cron-troubleshooting.md` | 诊断并修复常见的 Hermes cron 问题——任务未触发、投递失败、skill 加载错误及性能问题 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/daily-briefing-bot.md` | 构建一个自动化每日简报机器人，研究主题、汇总发现，并每天早晨推送至 Telegram 或 Discord |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/delegation-patterns.md` | 何时以及如何使用子代理委托——并行研究、代码审查和多文件工作的模式 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/github-pr-review-agent.md` | 构建一个自动化 AI 代码审查器，监控你的仓库、审查 Pull Request 并自动发送反馈——全程无需人工干预 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/google-gemini.md` | 将 Hermes Agent 与 Google Gemini 配合使用——原生 AI Studio API、API 密钥配置、工具调用、流式传输及配额说明 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/local-llm-on-mac.md` | 使用 llama.cpp 或 MLX 在 macOS 上搭建兼容 OpenAI 的本地 LLM 服务器，涵盖模型选择、内存优化以及 Apple Silicon 上的实测基准数据 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/local-ollama-setup.md` | 使用 Ollama 和 Gemma 4 等开放权重模型在本机完整运行 Hermes Agent 的分步指南，无需云端 API 密钥或付费订阅 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/microsoft-graph-app-registration.md` | Azure 门户操作指南：创建为 Teams 会议流水线提供支持的应用注册 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/migrate-from-openclaw.md` | 将 OpenClaw / Clawdbot 配置迁移到 Hermes Agent 的完整指南——包括迁移内容、配置键映射及迁移后的检查事项。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/minimax-oauth.md` | 通过浏览器 OAuth 登录 MiniMax，在 Hermes Agent 中使用 MiniMax-M2.7 模型——无需 API 密钥 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/oauth-over-ssh.md` | 当 Hermes 运行在远程机器、容器或跳板机后面时，如何完成基于浏览器的 OAuth（Spotify、MCP 服务器） |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/operate-teams-meeting-pipeline.md` | Microsoft Teams 会议流水线的运行手册、上线检查清单及操作员工作表 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/pipe-script-output.md` | 使用 `hermes send` 将任意 shell 脚本、cron 任务、CI hook 或监控守护进程的文本发送到 Telegram、Discord、Slack、Signal 等平台。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/python-library.md` | 将 AIAgent 嵌入你自己的 Python 脚本、Web 应用或自动化流水线——无需 CLI |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/run-hermes-with-nous-portal.md` | 完整操作指南：订阅、配置、切换模型、启用 gateway 工具并验证路由 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/team-telegram-assistant.md` | 逐步指南：为整个团队搭建一个 Telegram 机器人，用于代码帮助、研究、系统管理等 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/tips.md` | 充分发挥 Hermes Agent 潜力的实用建议——prompt 技巧、CLI 快捷键、上下文文件、记忆、成本优化与安全 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/use-mcp-with-hermes.md` | 将 MCP 服务器连接到 Hermes Agent、过滤其工具并在实际工作流中安全使用的实践指南 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/use-soul-with-hermes.md` | 如何使用 SOUL.md 塑造 Hermes Agent 的默认风格，哪些内容应放在其中，以及它与 AGENTS.md 和 /personality 的区别 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/use-voice-mode-with-hermes.md` | 在 CLI、Telegram、Discord 及 Discord 语音频道中设置和使用 Hermes 语音模式的实用指南 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/webhook-github-pr-review.md` | 将 Hermes 连接到 GitHub，使其自动获取 PR diff、审查代码变更并发布评论——由 webhook 触发，无需手动提示 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/work-with-skills.md` | 查找、安装、使用和创建 skills——按需加载的知识文档，用于教会 Hermes 新的工作流程 |
| `zh-Hans/docusaurus-plugin-content-docs/current/guides/xai-grok-oauth.md` | 使用 SuperGrok 或 X Premium+ 订阅登录，在 Hermes Agent 中使用 Grok 模型——无需 API 密钥 |
| `zh-Hans/docusaurus-plugin-content-docs/current/index.mdx` | 由 Nous Research 构建的自我改进 AI 智能体。内置学习循环，从经验中创建技能，在使用过程中持续改进，并跨会话保持记忆。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/integrations/buzz.md` | 将 Hermes Agent 连接到 Buzz（Block 基于 Nostr 的人机协作工作区）的全部三种方式 |
| `zh-Hans/docusaurus-plugin-content-docs/current/integrations/index.md` | Markdown document |
| `zh-Hans/docusaurus-plugin-content-docs/current/integrations/nous-portal.md` | 一个订阅，300+ 前沿模型，以及 Tool Gateway —— 运行 Hermes Agent 的推荐方式 |
| `zh-Hans/docusaurus-plugin-content-docs/current/integrations/providers.md` | AI 提供商 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/cli-commands.md` | Hermes 终端命令及命令族的权威参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/environment-variables.md` | Hermes Agent 使用的所有环境变量完整参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/faq.md` | Hermes Agent 常见问题解答及常见问题解决方案 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/mcp-config-reference.md` | Hermes Agent MCP 配置键、过滤语义及工具策略参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/model-catalog.md` | 远程托管的清单文件，驱动 OpenRouter 和 Nous Portal 的精选模型选择器列表。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/optional-skills-catalog.md` | hermes-agent 附带的官方可选技能 — 通过 hermes skills install official/<category>/<skill> 安装 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/profile-commands.md` | Profile 命令参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/skills-catalog.md` | 随 Hermes Agent 附带的内置技能目录 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/slash-commands.md` | 交互式 CLI 和消息平台斜杠命令完整参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/tools-reference.md` | Hermes 内置工具权威参考，按工具集分组 |
| `zh-Hans/docusaurus-plugin-content-docs/current/reference/toolsets-reference.md` | Hermes 核心、复合、平台及动态工具集参考 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/bot-mode.md` | 把你的 Hermes profile 变成一支具名的 Bot 团队——每个 Bot 都有自己的对话、角色、模型、记忆、技能和头像。Bot 可以运行例行任务、共享群聊，并互相发消息。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/checkpoints-and-rollback.md` | 使用影子 git 仓库和自动快照为破坏性操作提供文件系统安全保障 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/cli.md` | 掌握 Hermes Agent 终端界面——命令、快捷键、人格设定等 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/configuration.md` | 配置 Hermes Agent — config.yaml、providers、模型、API 密钥等 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/configuring-models.md` | 配置模型 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/docker.md` | 在 Docker 中运行 Hermes Agent 以及将 Docker 用作终端后端 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/acp.md` | 在兼容 ACP 的编辑器和协作平台中使用 Hermes Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/api-server.md` | 将 hermes-agent 作为 OpenAI 兼容的 API 暴露给任意前端 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/batch-processing.md` | 大规模生成 agent 轨迹——并行处理、断点续跑与工具集分布 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/browser.md` | 使用 browser_exec 驱动真实浏览器——Hermes 启动的 Chromium、云端浏览器、Lightpanda，或通过 CDP 连接您自己的 Chrome——用于网页交互、表单填写、数据抓取等场景。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/built-in-plugins.md` | 随 Hermes Agent 附带并通过生命周期 hook 自动运行的插件——disk-cleanup 等 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/code-execution.md` | 通过 RPC 工具访问实现程序化 Python 执行——将多步骤工作流压缩至单次对话轮次 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/codex-app-server-runtime.md` | Codex App-Server 运行时（可选） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/computer-use.md` | 电脑操控 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/context-files.md` | 项目上下文文件 — .hermes.md、AGENTS.md、CLAUDE.md、全局 SOUL.md 以及 .cursorrules — 自动注入每次对话 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/context-references.md` | 用于将文件、文件夹、git diff 及 URL 直接附加到消息中的内联 @-语法 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/credential-pools.md` | 为每个提供商池化多个 API 密钥或 OAuth 令牌，实现自动轮换和速率限制恢复。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/cron.md` | 用自然语言调度自动化任务，通过单一 cron 工具管理，并附加一个或多个 skill |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/curator.md` | Agent 创建的技能的后台维护——使用跟踪、过期检测、归档及 LLM 驱动的审查 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/delegation.md` | 使用 delegate_task 为并行工作流生成隔离的子智能体 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/deliverable-mode.md` | Agent 如何将生成的图表、PDF、电子表格及其他文件作为原生附件发送到消息平台。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/extending-the-dashboard.md` | 为 Hermes Web Dashboard 构建主题和插件——调色板、字体排版、布局、自定义标签页、shell 插槽、页面级插槽以及后端 API 路由 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/fallback-providers.md` | 配置自动故障转移，在主模型不可用时切换到备用 LLM 提供商。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/goals.md` | 设置一个持续目标，让 Hermes 跨轮次持续工作直到完成。我们对 Ralph loop 的实现。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/honcho.md` | 通过 Honcho 实现 AI 原生持久记忆——辩证推理、多智能体用户建模与深度个性化 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/hooks.md` | 在关键生命周期节点运行自定义代码——记录活动、发送告警、推送到 webhook |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/image-generation.md` | 通过 FAL.ai 文生图；支持 8 个模型，含 FLUX 2、GPT-Image、Nano Banana Pro、Ideogram、Recraft V4 Pro 等，可用 hermes tools 切换。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/kanban-tutorial.md` | Kanban 教程 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/kanban-worker-lanes.md` | Kanban worker lanes（工作者通道） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/kanban.md` | 基于 SQLite 的持久化任务看板，用于协调多个 Hermes 配置文件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/lsp.md` | 真实语言服务器（pyright、gopls、rust-analyzer 等）接入 write_file 和 patch 所使用的写后 lint 检查。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/mcp.md` | 通过 MCP 将 Hermes Agent 连接到外部工具服务器，并精确控制 Hermes 加载哪些 MCP 工具 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/memory-providers.md` | 外部记忆提供者插件 — Honcho、OpenViking、Mem0、Hindsight、Holographic、RetainDB、ByteRover、Supermemory |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/memory.md` | Hermes Agent 如何跨会话记忆——MEMORY.md、USER.md 与会话搜索 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/overview.md` | 功能概览 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/personality.md` | 通过全局 SOUL.md、内置个性预设和自定义角色定义来自定义 Hermes Agent 的个性 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/plugins.md` | 通过插件系统为 Hermes 添加自定义工具、hook 和集成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/provider-routing.md` | 配置 OpenRouter provider 偏好，以优化成本、速度或质量。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/skills.md` | 按需加载的知识文档——渐进式披露、agent 管理的 skills 以及 Skills Hub |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/skins.md` | 使用内置和用户自定义皮肤定制 Hermes CLI 的外观 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/spotify.md` | Spotify |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/subscription-proxy.md` | 将你的 Nous Portal 订阅（或其他 OAuth 提供商）用作外部应用的 OpenAI 兼容端点 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/tool-gateway.md` | 通过 Nous 订阅统一使用网页搜索、文生图、语音合成与浏览器自动化，无需单独申请网页搜索、FAL、OpenAI、Browser Use 等 API Key |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/tools.md` | Hermes Agent 工具概览——可用工具、工具集工作方式及终端后端 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/tts.md` | 跨所有平台的文字转语音与语音消息转录 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/vision.md` | 将剪贴板中的图像粘贴到 Hermes CLI，进行多模态视觉分析。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/voice-mode.md` | 与 Hermes Agent 进行实时语音对话 — CLI、Telegram、Discord（私信、文字频道和语音频道） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/web-dashboard.md` | 基于浏览器的仪表板，用于管理配置、API 密钥、会话、日志、分析、定时任务和技能 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/web-search.md` | 通过多个后端提供商搜索网页并提取页面内容——包括免费的自托管 SearXNG。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/features/x-search.md` | 使用 xAI 内置的 x_search Responses 工具在 agent 内搜索 X (Twitter) 帖子和话题串——支持 SuperGrok OAuth 登录或 XAI_API_KEY。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/git-worktrees.md` | 使用 git worktrees 和隔离检出在同一仓库中安全运行多个 Hermes agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/bluebubbles.md` | BlueBubbles（iMessage） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/dingtalk.md` | 将 Hermes Agent 设置为钉钉聊天机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/discord.md` | 将 Hermes Agent 设置为 Discord 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/email.md` | 通过 IMAP/SMTP 将 Hermes Agent 设置为电子邮件助手 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/feishu.md` | 将 Hermes Agent 配置为飞书或 Lark 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/google_chat.md` | 使用 Cloud Pub/Sub 将 Hermes Agent 设置为 Google Chat 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/homeassistant.md` | 通过插件目录中的 Home Assistant 插件，使用 Hermes Agent 控制您的智能家居。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/index.md` | 通过 Telegram、Discord、Slack、WhatsApp、Signal、SMS、Email、Home Assistant、Mattermost、Matrix、DingTalk、Yuanbao、Microsoft Teams、LINE、Webhooks 或任何兼容 OpenAI 的前端与 Hermes 对话 — 架构与配置概览 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/line.md` | 将 Hermes Agent 设置为 LINE Messaging API 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/matrix.md` | 将 Hermes Agent 设置为 Matrix 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/mattermost.md` | 将 Hermes Agent 配置为 Mattermost 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/msgraph-webhook.md` | 在 Hermes 中接收 Microsoft Graph 变更通知（会议、日历、聊天等） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/ntfy.md` | ntfy |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/open-webui.md` | 通过 OpenAI 兼容 API 服务器将 Open WebUI 连接到 Hermes Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/qqbot.md` | QQ Bot |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/signal.md` | 通过 signal-cli 守护进程将 Hermes Agent 设置为 Signal 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/simplex.md` | SimpleX Chat |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/slack.md` | 使用 Socket Mode 将 Hermes Agent 设置为 Slack 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/sms.md` | 通过 Twilio 将 Hermes Agent 设置为 SMS 聊天机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/teams-meetings.md` | 使用 Microsoft Graph webhook 配置 Microsoft Teams 会议摘要流水线 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/teams.md` | 将 Hermes Agent 设置为 Microsoft Teams 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/telegram.md` | 将 Hermes Agent 设置为 Telegram 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/webhooks.md` | 接收来自 GitHub、GitLab 等服务的事件以触发 Hermes agent 运行 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/wecom-callback.md` | WeCom 回调（自建应用） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/wecom.md` | 通过 AI Bot WebSocket 网关将 Hermes Agent 连接到 WeCom |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/weixin.md` | 通过 iLink Bot API 将 Hermes Agent 连接到个人微信账号 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/whatsapp.md` | 通过内置 Baileys 桥接将 Hermes Agent 设置为 WhatsApp 机器人 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/messaging/yuanbao.md` | 通过 WebSocket gateway 将 Hermes Agent 连接到元宝企业消息平台 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/profile-distributions.md` | Profile 分发：共享完整 Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/profiles.md` | Profiles：运行多个 Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/secrets/bitwarden.md` | Bitwarden Secrets Manager |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/secrets/index.md` | Secrets |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/security.md` | 安全模型、危险命令审批、用户授权、容器隔离及生产部署最佳实践 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/sessions.md` | 会话持久化、恢复、搜索、管理及各平台会话跟踪 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/apple/apple-apple-notes.md` | 通过 memo CLI 管理 Apple Notes：创建、搜索、编辑 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/apple/apple-apple-reminders.md` | 通过 remindctl 管理 Apple Reminders：添加、列出、完成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/apple/apple-findmy.md` | 通过 FindMy 追踪 Apple 设备/AirTag |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/apple/apple-imessage.md` | 通过 macOS 上的 imsg CLI 发送和接收 iMessages/SMS |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-claude-code.md` | 将编码任务委托给 Claude Code CLI（功能、PR） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-codex.md` | 将编码任务委托给 OpenAI Codex CLI（功能开发、PR） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-hermes-agent.md` | Use, configure, theme, extend, and orchestrate Hermes Agent |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/autonomous-ai-agents/autonomous-ai-agents-opencode.md` | 将编码任务委托给 OpenCode CLI（功能开发、PR 审查） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-architecture-diagram.md` | 深色主题 SVG 架构/云/基础设施图表（HTML 格式） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-ascii-video.md` | ASCII 视频：将视频/音频转换为彩色 ASCII MP4/GIF |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-baoyu-infographic.md` | 信息图：21种布局 × 21种风格（信息图, 可视化） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-claude-design.md` | 设计一次性 HTML 制品（落地页、幻灯片、原型） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-design-md.md` | 编写/验证/导出 Google 的 DESIGN |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-humanizer.md` | 人性化文本：去除 AI 腔调，注入真实声音 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-manim-video.md` | Manim CE 动画：3Blue1Brown 数学/算法视频 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-p5js.md` | Markdown document |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-popular-web-designs.md` | 54 个真实设计系统（Stripe、Linear、Vercel）的 HTML/CSS |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/creative/creative-songwriting-and-ai-music.md` | 歌词创作与 Suno AI 音乐提示词 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/email/email-himalaya.md` | Himalaya CLI：从终端收发 IMAP/SMTP 邮件 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/media/media-gif-search.md` | 通过 curl + jq 搜索/下载 Tenor GIF |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/media/media-songsee.md` | 通过 CLI 生成音频频谱图/特征（mel、chroma、MFCC） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/media/media-youtube-content.md` | YouTube 视频转文字摘要、推文、博客 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/note-taking/note-taking-obsidian.md` | 在 Obsidian 知识库中读取、搜索、创建和编辑笔记 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-airtable.md` | 通过 curl 调用 Airtable REST API |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-google-workspace.md` | 通过 gws CLI 或 Python 使用 Gmail、Calendar、Drive、Docs、Sheets |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-maps.md` | 通过 OpenStreetMap/OSRM 进行地理编码、POI、路线、时区查询 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-notion.md` | Notion API + ntn CLI：页面、数据库、Markdown、Workers |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-powerpoint.md` | 创建、读取、编辑 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/productivity/productivity-teams-meeting-pipeline.md` | 通过 Hermes CLI 操作 Teams 会议摘要流水线 — 总结会议、检查流水线状态、重放任务、管理 Microsoft Graph 订阅 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/research/research-arxiv.md` | 通过关键词、作者、分类或 ID 搜索 arXiv 论文 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/research/research-llm-wiki.md` | Karpathy 的 LLM Wiki：构建/查询互联 Markdown 知识库 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/social-media/social-media-xurl.md` | 通过 xurl CLI 使用 X/Twitter：发帖、搜索、私信、媒体、v2 API |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-dogfood.md` | 网页应用探索性 QA：发现缺陷、收集证据、生成报告 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-hermes-agent-skill-authoring.md` | 在仓库中编写 SKILL.md |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-node-inspect-debugger.md` | 调试 Node |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-python-debugpy.md` | 调试 Python：pdb REPL + debugpy 远程（DAP） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-requesting-code-review.md` | 提交前审查：安全扫描、质量门控、自动修复 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-spike.md` | 在构建前验证想法的一次性实验 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-systematic-debugging.md` | 4阶段根因调试：先理解缺陷再修复 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/bundled/software-development/software-development-test-driven-development.md` | TDD：强制执行 RED-GREEN-REFACTOR，测试先于代码 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/google-workspace.md` | 通过 OAuth2 认证的 Google API，发送邮件、管理日历事件、搜索 Drive、读写 Sheets 并访问 Docs |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-blackbox.md` | 将编码任务委托给 Blackbox AI CLI 代理 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/autonomous-ai-agents/autonomous-ai-agents-honcho.md` | 配置并使用 Honcho 记忆功能与 Hermes -- 跨会话用户建模、多配置文件 peer 隔离、观察配置、辩证推理、会话摘要及上下文预算控制。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/blockchain/blockchain-evm.md` | 只读 EVM 客户端：跨 8 条链的钱包、代币、Gas |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/blockchain/blockchain-hyperliquid.md` | Hyperliquid 市场数据、账户历史、交易复盘 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/blockchain/blockchain-solana.md` | 使用 USD 定价查询 Solana 区块链数据——钱包余额、带价值的代币投资组合、交易详情、NFT、巨鲸检测及实时网络状态... |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/communication/communication-one-three-one-rule.md` | 技术提案与权衡分析的结构化决策框架 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-audiocraft-audio-generation.md` | AudioCraft：MusicGen 文本转音乐，AudioGen 文本转声音 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-concept-diagrams.md` | 以统一的教育视觉语言生成扁平、简约、支持明暗模式的 SVG 图表，输出为独立 HTML 文件，包含 9 种语义色阶、句首大写排版及自动暗色模式。... |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-heartmula.md` | HeartMuLa：基于歌词与标签的类 Suno 歌曲生成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-hyperframes.md` | 使用 HyperFrames 创建基于 HTML 的视频合成、动画标题卡、社交叠加层、带字幕的对话视频、音频响应视觉效果和着色器转场... |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-kanban-video-orchestrator.md` | 规划、搭建并监控由 Hermes Kanban 支撑的多智能体视频制作流水线 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/creative/creative-meme-generation.md` | 使用 Pillow 选取模板并叠加文字，生成真实的表情包图片 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/data-science/data-science-jupyter-notebook.md` | 通过实时 Jupyter 内核进行迭代式 Python 开发（hamelnb） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/devops/devops-docker-management.md` | 管理 Docker 容器、镜像、卷、网络和 Compose 栈——生命周期操作、调试、清理及 Dockerfile 优化 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/devops/devops-inference-sh-cli.md` | 通过 inference 运行 150+ AI 应用 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/devops/devops-pinggy-tunnel.md` | 通过 Pinggy 实现零安装 SSH localhost 隧道 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/devops/devops-watchers.md` | 使用水印去重轮询 RSS、JSON API 和 GitHub |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/dogfood/dogfood-adversarial-ux-test.md` | 扮演产品最难搞的技术抵触用户 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/email/email-agentmail.md` | 通过 AgentMail 为 Agent 提供专属电子邮件收件箱 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-3-statement-model.md` | 在 Excel 中构建完整集成的三表模型（利润表、资产负债表、现金流量表），包含营运资本明细表、折旧摊销滚动表、债务计划表，以及使现金和留存收益勾稽的插销项。与 excel-author 配合使用。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-comps-analysis.md` | 在 Excel 中构建可比公司分析——运营指标、估值倍数、与同行集合的统计基准对比 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-dcf-model.md` | 在 Excel 中构建机构级 DCF 估值模型——收入预测、FCF 构建、WACC、终值、熊/基/牛情景、5x5 敏感性表格。与 excel-author 配合使用。适用于内在价值股权分析。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-excel-author.md` | 使用 openpyxl 无头构建可审计的 Excel 工作簿——蓝/黑/绿单元格约定、公式优先于硬编码、命名范围、余额检查、敏感性表格。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-lbo-model.md` | 在 Excel 中构建杠杆收购模型——资金来源与用途、债务计划、现金清扫、退出倍数、IRR/MOIC 敏感性分析 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-merger-model.md` | 在 Excel 中构建增厚/摊薄（并购）模型 — 备考损益表、协同效应、融资结构、每股收益影响 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-polymarket.md` | 查询 Polymarket：市场、价格、订单簿、历史记录 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-pptx-author.md` | 使用 python-pptx 无头构建 PowerPoint 演示文稿 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/finance/finance-stocks.md` | 通过 Yahoo 获取股票报价、历史、搜索、比较及加密货币数据 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/health/health-fitness-nutrition.md` | 健身房训练计划与营养追踪 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/health/health-neuroskill-bci.md` | 连接到运行中的 NeuroSkill 实例，将用户的实时认知与情绪状态（专注度、放松度、情绪、认知负荷、困倦度、心率、HRV、睡眠分期及 40+ 项衍生 EXG 评分）融入响应中... |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mcp/mcp-fastmcp.md` | 使用 FastMCP 在 Python 中构建、测试、检查、安装和部署 MCP 服务器 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mcp/mcp-mcporter.md` | 使用 mcporter CLI 列出、配置、认证并直接调用 MCP 服务器/工具（HTTP 或 stdio），包括临时服务器、配置编辑及 CLI/类型生成等功能。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-accelerate.md` | 最简分布式训练 API |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-chroma.md` | 面向 AI 应用的开源 embedding 数据库 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-clip.md` | OpenAI 连接视觉与语言的模型 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-faiss.md` | Facebook 用于高效相似性搜索和密集向量聚类的库 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-flash-attention.md` | 通过 Flash Attention 优化 Transformer 注意力机制，实现 2-4 倍加速和 10-20 倍内存减少 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-guidance.md` | 使用正则表达式和语法控制 LLM 输出，保证生成有效的 JSON/XML/代码，强制结构化格式，并使用 Guidance（微软研究院的约束生成框架）构建多步骤工作流... |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-huggingface-tokenizers.md` | 为研究和生产优化的快速 tokenizer |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-inference-outlines.md` | Outlines：结构化 JSON/regex/Pydantic LLM 生成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-instructor.md` | 使用 Pydantic 验证从 LLM 响应中提取结构化数据，自动重试失败的提取，以类型安全方式解析复杂 JSON，并使用 Instructor 流式传输部分结果——经过实战检验的结构化输出库 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-lambda-labs.md` | 用于 ML 训练和推理的预留及按需 GPU 云实例 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-llava.md` | 大型语言与视觉助手 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-modal.md` | 用于运行 ML 工作负载的无服务器 GPU 云平台 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-models-segment-anything-model.md` | SAM：通过点、框、掩码实现零样本图像分割 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-nemo-curator.md` | 用于 LLM 训练的 GPU 加速数据整理工具 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-peft.md` | 使用 LoRA、QLoRA 及 25+ 种方法对 LLM 进行参数高效微调 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-pinecone.md` | 面向生产级 AI 应用的托管向量数据库 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-pytorch-fsdp.md` | PyTorch FSDP 全分片数据并行训练专家指导 - 参数分片、混合精度、CPU 卸载、FSDP2 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-pytorch-lightning.md` | 基于 PyTorch 的高层框架，提供 Trainer 类、自动分布式训练（DDP/FSDP/DeepSpeed）、回调系统及极简样板代码 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-qdrant.md` | 用于 RAG 和语义搜索的高性能向量相似度搜索引擎 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-saelens.md` | 提供使用 SAELens 训练和分析稀疏自编码器（SAE）的指导，将神经网络激活分解为可解释特征 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-simpo.md` | 用于 LLM 对齐的简单偏好优化 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-slime.md` | 使用 slime（Megatron+SGLang 框架）进行 LLM RL 后训练的指导 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-stable-diffusion.md` | 通过 HuggingFace Diffusers 使用 Stable Diffusion 模型实现最先进的文本到图像生成 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-tensorrt-llm.md` | 使用 NVIDIA TensorRT 优化 LLM 推理以实现最大吞吐量和最低延迟 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-torchtitan.md` | 使用 torchtitan 提供 PyTorch 原生分布式 LLM 预训练，支持 4D 并行（FSDP2、TP、PP、CP） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-training-axolotl.md` | Axolotl：基于 YAML 的 LLM 微调（LoRA、DPO、GRPO） |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-training-trl-fine-tuning.md` | TRL：面向 LLM RLHF 的 SFT、DPO、PPO、GRPO 及奖励建模 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-training-unsloth.md` | Unsloth：2-5倍更快的 LoRA/QLoRA 微调，更少显存 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/mlops/mlops-whisper.md` | OpenAI 的通用语音识别模型 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-canvas.md` | Canvas LMS 集成 — 使用 API token 认证获取已注册课程和作业 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-here-now.md` | 将静态站点发布到 {slug} |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-memento-flashcards.md` | 间隔重复闪卡系统 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-shop.md` | Shop.app：商品搜索、订单追踪、退货、重新下单 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-shopify.md` | 通过 curl 使用 Shopify Admin 与 Storefront GraphQL API |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-siyuan.md` | 通过 curl 调用 SiYuan Note API，在自托管知识库中搜索、读取、创建和管理块与文档 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/productivity/productivity-telephony.md` | 无需修改核心工具即可赋予 Hermes 电话能力 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-bioinformatics.md` | 来自 bioSkills 和 ClawBio 的 400+ 生物信息学技能网关 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-darwinian-evolver.md` | 使用 Imbue 的进化循环来优化 prompt/正则/SQL/代码 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-domain-intel.md` | 使用 Python 标准库进行被动域名侦察 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-drug-discovery.md` | 药物发现工作流的制药研究助手 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-duckduckgo-search.md` | 通过 DuckDuckGo 免费搜索网络 — 文本、新闻、图片、视频 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-gitnexus-explorer.md` | 使用 GitNexus 为代码库建立索引，并通过 Web UI + Cloudflare 隧道提供交互式知识图谱服务 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-osint-investigation.md` | 公开记录 OSINT 调查框架 — SEC EDGAR 文件、USAspending 合同、参议院游说、OFAC 制裁、ICIJ 离岸泄露、纽约市房产记录（ACRIS）、OpenCorporates 注册信息、CourtListener 法院记录、Wayback Machine 存档、Wikipedia + Wikidata、GDELT 新闻监控。跨来源实体解析、交叉链接分析、时序关联、证据链。仅使用 Python 标准库。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-parallel-cli.md` | 可选的供应商技能，用于 Parallel CLI — 面向 agent 的网络搜索、提取、深度研究、数据丰富、FindAll 和监控 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-qmd.md` | 使用 qmd 在本地搜索个人知识库、笔记、文档和会议记录 — 一个集成 BM25、向量搜索和 LLM 重排序的混合检索引擎 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-scrapling.md` | 使用 Scrapling 进行网页抓取——HTTP 获取、隐身浏览器自动化、Cloudflare 绕过及通过 CLI 和 Python 进行爬虫抓取 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/research/research-searxng-search.md` | 通过 SearXNG 免费元搜索 — 聚合 70+ 搜索引擎的结果 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/security/security-1password.md` | 设置并使用 1Password CLI (op) |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/security/security-oss-forensics.md` | GitHub 仓库的供应链调查、证据恢复与取证分析 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/security/security-sherlock.md` | 跨 400+ 社交网络的 OSINT 用户名搜索 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/software-development/software-development-rest-graphql-debug.md` | 调试 REST/GraphQL API：状态码、认证、Schema、复现 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/web-development/web-development-page-agent.md` | 将 alibaba/page-agent 嵌入你自己的 Web 应用——一个纯 JavaScript 页内 GUI agent，以单个 <script> 标签或 npm 包形式发布，让你网站的终端用户能用自然语言驱动 UI（如'点击登录，将用户名填为 John'）。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/skills/optional/yuanbao/yuanbao-yuanbao.md` | Yuanbao（元宝）群组：@提及用户、查询信息/成员 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/tui.md` | 启动 Hermes 的现代终端 UI——支持鼠标操作、丰富的浮层面板和非阻塞输入。 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/windows-native.md` | 在 Windows 10 / 11 上原生运行 Hermes Agent — 安装、功能矩阵、UTF-8 控制台、Git Bash、将 gateway 作为计划任务、编辑器处理、PATH、卸载及常见问题 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-guide/windows-wsl-quickstart.md` | 通过 WSL2 在 Windows 上运行 Hermes Agent —— 安装配置、Windows 与 Linux 之间的文件系统访问、网络设置及常见问题 |
| `zh-Hans/docusaurus-plugin-content-docs/current/user-stories.mdx` | 来自 Hermes Agent 社区的真实故事——人们实际在构建的内容，来源涵盖 X、GitHub、Reddit、Hacker News、YouTube、博客和播客。 |

## `website/plugins/`

| File | What it does |
|---|---|
| `plugin-catalog-pages/index.js` | Docusaurus plugin: static pages for every plugin catalog entry and every author. /docs/plugins/<name> one page per entry in website/static/api/plugins.json /docs/plugins/by/<slug> one page per maintainer (slug from extr… |
| `plugin-catalog-pages/readme.js` | README rendering for the per-plugin pages (/docs/plugins/<name>). Every entry gets its README rendered on its page (opt out with `readme: false`). The build fetches it from the PINNED commit (extract-plugins.py emits `r… |

## `website/scripts/`

| File | What it does |
|---|---|
| `check-live-search.mjs` | JavaScript (ES module): `check-live-search` |
| `check_doc_links.py` | Keep cross-page links in website/docs resolvable on GitHub AND on the site. |
| `extract-automation-blueprints.py` | Generate the Automation Blueprints catalog JSON for the docs site. |
| `extract-plugins.py` | Extract plugin-catalog entries into website/static/api/plugins.json. |
| `extract-skills.py` | Extract skill metadata into website/static/api/skills.json for the Skills Hub page. |
| `fetch-plugin-stars.py` | Refresh GitHub star counts for plugin-catalog repos, at most once a day. |
| `generate-llms-txt.py` | Generate llms.txt and llms-full.txt for the Hermes docs site. |
| `generate-skill-docs.py` | Generate per-skill Docusaurus pages from skills/ and optional-skills/ SKILL.md files. |
| `prebuild.mjs` | JavaScript (ES module): `prebuild` |

## `website/src/`

| File | What it does |
|---|---|
| `components/AutomationBlueprintsCatalog/index.tsx` | Exports `AutomationBlueprintsCatalog` |
| `components/AutomationBlueprintsCatalog/styles.module.css` | Stylesheet |
| `components/CatalogFeatured/index.tsx` | The catalog hero both /skills and /plugins show, laid out like the desktop app's featured card (author, title, one-line description, tags; action bottom-right; no artwork). The pick comes from apps/shared `pickFeatured`… |
| `components/CatalogFeatured/styles.module.css` | Mirrors the desktop app's featured card: one plain card, copy stacked on the left, the action bottom-right, no artwork. Border and radius match the catalog grid cards; a soft accent wash marks it as the featured pick. |
| `components/PluginCatalog/AuthorPage.tsx` | Exports `AuthorPage` |
| `components/PluginCatalog/CopyButton.tsx` | Copies an install command; shared by the catalog cards and the plugin pages. |
| `components/PluginCatalog/MiniCard.tsx` | Exports `MiniCard` |
| `components/PluginCatalog/PluginPage.tsx` | Exports `PluginPage` |
| `components/PluginCatalog/catalog.ts` | Shared catalog vocabulary for the Plugins grid (src/pages/plugins), the per-plugin pages and the author pages (plugins/plugin-catalog-pages generates their routes). One definition of the entry shape, the tier/category t… |
| `components/PluginCatalog/pages.module.css` | Per-plugin pages (/plugins/<name>) and author pages (/plugins/by/<slug>). Shares the visual language of the catalog grid (src/pages/plugins/styles.module.css): DM Sans, gold accents, mono pills. Light mode is a first-cl… |
| `components/UserStoriesCollage/index.tsx` | Exports `UserStoriesCollage` |
| `components/UserStoriesCollage/styles.module.css` | User Stories collage — masonry grid with category-driven accents. |
| `css/custom.css` | Hermes Agent — Custom Docusaurus Theme Matches the landing page branding: amber-on-dark, terminal aesthetic Colors from landingpage/style.css |
| `data/userStories.json` | JSON data/configuration |
| `pages/plugins/index.tsx` | Exports `PluginCatalogPage` |
| `pages/plugins/styles.module.css` | Stylesheet |
| `pages/skills/index.tsx` | Exports `SkillsDashboard` |
| `pages/skills/styles.module.css` | Stylesheet |
| `remark/relativeDocLinks.js` | Remark plugin: make relative Markdown file links resolve across the zh-Hans fallback boundary. Docs are authored with relative file links (`../user-guide/profiles.md`) so |

## `website/static/`

| File | What it does |
|---|---|
| `.nojekyll` | Data/support file |
| `api/model-catalog.json` | JSON object with keys `version`, `updated_at`, `metadata`, `providers` |
| `img/apple-touch-icon.png` | PNG image asset |
| `img/catalog/official-art-card-one.jpg` | JPEG image asset |
| `img/catalog/official-art-card-two.jpg` | JPEG image asset |
| `img/catalog/official-art-feature.jpg` | JPEG image asset |
| `img/catalog/official-art.jpg` | JPEG image asset |
| `img/dashboard/admin-channels.png` | PNG image asset |
| `img/dashboard/admin-config.png` | PNG image asset |
| `img/dashboard/admin-hook-create.png` | PNG image asset |
| `img/dashboard/admin-mcp.png` | PNG image asset |
| `img/dashboard/admin-pairing.png` | PNG image asset |
| `img/dashboard/admin-sessions.png` | PNG image asset |
| `img/dashboard/admin-skills-hub.png` | PNG image asset |
| `img/dashboard/admin-system-curator.png` | PNG image asset |
| `img/dashboard/admin-system-ops.png` | PNG image asset |
| `img/dashboard/admin-system-top.png` | PNG image asset |
| `img/dashboard/admin-webhooks.png` | PNG image asset |
| `img/docs/cli-layout.svg` | SVG vector image |
| `img/docs/dashboard-models/auxiliary-expanded.png` | PNG image asset |
| `img/docs/dashboard-models/overview.png` | PNG image asset |
| `img/docs/dashboard-models/picker-dialog.png` | PNG image asset |
| `img/docs/dashboard-models/use-as-dropdown.png` | PNG image asset |
| `img/docs/session-recap.svg` | SVG vector image |
| `img/docs/tui-session-orchestrator/session-orchestrator-demo.mp4` | Video asset |
| `img/docs/tui-session-orchestrator/session-orchestrator.png` | PNG image asset |
| `img/favicon-16x16.png` | PNG image asset |
| `img/favicon-32x32.png` | PNG image asset |
| `img/favicon.ico` | Icon file |
| `img/favicon.svg` | SVG vector image |
| `img/hermes-agent-banner.png` | PNG image asset |
| `img/kanban-tutorial/01-board-overview.png` | PNG image asset |
| `img/kanban-tutorial/02-board-flat.png` | PNG image asset |
| `img/kanban-tutorial/03-drawer-schema-task.png` | PNG image asset |
| `img/kanban-tutorial/04b-drawer-retry-history-scrolled.png` | PNG image asset |
| `img/kanban-tutorial/06-drawer-crash-recovery.png` | PNG image asset |
| `img/kanban-tutorial/07-fleet-transcribes.png` | PNG image asset |
| `img/kanban-tutorial/08-pipeline-auth.png` | PNG image asset |
| `img/kanban-tutorial/09-drawer-pipeline-review.png` | PNG image asset |
| `img/kanban-tutorial/10-drawer-in-flight.png` | PNG image asset |
| `img/kanban-tutorial/11-drawer-gave-up.png` | PNG image asset |
| `img/logo-dark.png` | PNG image asset |
| `img/logo.png` | PNG image asset |
| `img/nous-logo-dark.png` | PNG image asset |
| `img/nous-logo.png` | PNG image asset |
| `oauth/client-metadata.json` | JSON object with keys `client_id`, `client_name`, `client_uri`, `logo_uri`, `application_type`, `grant_types` |
