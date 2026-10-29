# File reference: `plugin-catalog`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `0bull.yaml` | YAML definition for `0bull` |
| `README.md` | Hermes Plugin Catalog |
| `aave-mcp.yaml` | Aave V3 and V4 through Aave's official MCP server (Streamable HTTP at https://mcp.aave.com, no sign-in, no keys in config): live markets and rates on every chain Aave runs on, wallet positions and health factor, rewards… |
| `abstract-provider.yaml` | Abstract model provider (GLM-5.3, DeepSeek-V4-Flash, Kimi-K3) over the OpenAI Responses API with a bundled model catalog. Disclosure — registers one model provider at import and nothing else (no tools, hooks, commands o… |
| `accent-picker.yaml` | OKLCH accent colour picker for the Hermes Desktop status bar: drag it and the whole theme retints |
| `account-pool.yaml` | Run several accounts of one provider in Hermes' credential pool: `hermes account <provider> <action>` adds accounts with email verification, shows live usage per account, keeps the least-used account first (fill_first +… |
| `account-switcher.yaml` | Windows desktop plugin that switches which Codex login and which Claude subscription account every local Hermes profile uses, with one idle-only, verified restart of the gateway (and, on Hermes before 0.22, of Hermes De… |
| `acedatacloud-media.yaml` | YAML configuration/data |
| `acedatacloud.yaml` | Ace Data Cloud GPT models with streaming and tool calling. |
| `actvox.yaml` | Make Hermes a team member in an ActVox workspace: on a schedule it works the tasks people assign it and answers the comments that @mention it, and submits each task for a person's review. Skills actvox:actvox and actvox… |
| `adaption.yaml` | Dataset import, adaptation, augmentation, translation, synthetic generation, and AutoScientist fine-tuning through the hosted Adaption MCP. Portable Agent Plugins v1 package with three workflow skills; the MCP server is… |
| `adaptive-inference-routing.yaml` | YAML definition for `adaptive-inference-routing` |
| `adkit.yaml` | Manage ads on Google Ads, Meta Ads (Facebook, Instagram), TikTok, LinkedIn, Microsoft, Reddit and X Ads through the hosted AdKit MCP: launch campaigns, ad sets and ads as drafts, pull performance reports with breakdowns… |
| `adspirer.yaml` | Create, analyze, and optimize campaigns across Google Ads, Meta Ads, TikTok Ads, LinkedIn |
| `advanced-delegation.yaml` | Two extra delegation modes for `delegate_task`, next to the built-in default. Model routes |
| `advisor.yaml` | A persistent second model reviews every agent turn. After each turn the plugin hands the transcript to the model you nominate as advisor and delivers its findings as advice in the same session: [NIT], [CONCERN] or [BLOC… |
| `adwhispr.yaml` | Research competitor ads, clone the winners, and run campaigns through the hosted AdWhispr MCP. Finds brands verified to be advertising in a niche right now, their longest-running Meta and TikTok ads, Instagram content a… |
| `afterforge.yaml` | Local-first regression workbench turning agent failures and corrections into reviewed, evidence-backed checks. |
| `agent-analytics.yaml` | Dashboard-only read plugin for Agent Analytics inside Hermes. |
| `agent-batch.yaml` | Community catalog entry — agent-batch Owner-submitted: the PR author (`raaaas`) owns and maintains the repo below. |
| `agent-hint.yaml` | Give the inference engine behind each request a standard, machine-readable view of the agent session that produced it. Injects an X-Agent-Hint header (base64url JSON: session identity and call index, lifecycle state, so… |
| `agent-hold-em.yaml` | No-Limit Texas Hold 'Em for Hermes Desktop: play with three isolated Hermes profile agents using play chips only. Agent decisions use configured models and may consume provider tokens; this is a local game, not gambling… |
| `agent-importers.yaml` | `hermes import-agent`: import an OpenClaw (~/.openclaw, or legacy ~/.clawdbot / |
| `agent-janitor.yaml` | Process hygiene for agent machines — finds the background processes your agent left behind (dev servers, tunnels, watchers, nohup jobs) using evidence signals (ppid=1 reparent, port listener via /proc/net/tcp{,6}, dev-s… |
| `agent-ledger.yaml` | Write-ahead ledger for agent side effects, with an OWASP Agentic Top 10 posture scorer. Disclosure — records the arguments (up to 4000 chars: terminal commands, file contents, MCP args) and a 300-char result digest of e… |
| `agent-log.yaml` | Readable agent.log viewer in the desktop status bar — a live, colour-coded feed of |
| `agent-mail-gateway.yaml` | Email for your agents through a self-hosted Agent Mail Gateway: the agent-mail skill teaches reading, searching, replying and forwarding mail, attachments, sending and answering calendar invitations, how to react when t… |
| `agent-run-debugger.yaml` | Local-first evidence debugger for failed, stalled or expensive agent runs: import one explicitly selected trace and get a deterministic timeline, observed failure points, ranked hypotheses that cite their evidence, miss… |
| `agent-station.yaml` | Read-only Hermes Desktop page for the focused chat: the main agent and its subagents, background commands and a Replay of file edits. Disclosure — its local dashboard routes serve the file-edit contents (Replay) and bac… |
| `agent_memory_es.yaml` | Self-owned long-term memory backed by the agent-memory-es service (Elasticsearch). Three agent tools — recall, retain, reflect — over episodic/ semantic/procedural tiers with hybrid BM25+kNN recall and server-enforced p… |
| `agentchat.yaml` | AgentChat — peer-to-peer messaging for AI agents. Owns its own WebSocket; pokes the agent |
| `agentplaybooks-memory.yaml` | Private AgentPlaybooks memory for Hermes: bounded keyword recall across personal and team sources, exact native memory-write mirroring, archive and history. Disclosure — keywords derived from each turn's query are sent… |
| `agentplaybooks-tools.yaml` | YAML definition for `agentplaybooks-tools` |
| `agentvault.yaml` | Search archived coding conversations and retrieve exact session revisions through the separately installed Agent Vault macOS app. Launches the app's existing MCP server through sh; reads the authorized archive through i… |
| `agentwalletapi.yaml` | OpenClawCash managed EVM and Solana wallets for AI agents — thin bridge to the OpenClawCash agent API. Disclosure — payments plugin for the OpenClawCash custodial wallet service (openclawcash.com); the model can create… |
| `agora.yaml` | YAML definition for `agora` |
| `ai-subscriptions.yaml` | Community catalog entry, ai-subscriptions Owner-submitted: the PR author (`rahuloruganti`) owns and maintains the repo below. |
| `ai-usage-tracker.yaml` | Community catalog entry — ai-usage-tracker Owner-submitted: the PR author (`lvabarajithan`) owns and maintains the repo below. |
| `aichipmunk.yaml` | aichipmunk — catalog entry for NousResearch/hermes-agent. Generated by Pacific-Cloud-Solutions/hermes-plugins:scripts/catalog_entry.py. |
| `aihubmix.yaml` | AIHubMix — unified OpenAI-compatible access to 400+ models; /model picker filtered to tool-capable routes. |
| `airlock.yaml` | YAML definition for `airlock` |
| `aistupidlevel.yaml` | AI Stupid Level Smart Router — OpenAI-compatible; routing modes such as auto-tooling send each request to the model currently scoring best on continuously re-run benchmarks, called with your own provider keys. Disclosur… |
| `alans-way-computer.yaml` | Computer-use provider for Hermes: the stock computer_use tool drives desktop apps on the user's computer through the Alan's Workspace app, and on the VM's own desktop when the computer is offline. Needs the Alan's Way P… |
| `alans-way.yaml` | Idle check-ins from the primary bot of a Hermes gateway on a Linux machine or a macOS guest VM: when the bound Telegram chat has been quiet for two hours, during 08:00-22:00 in the user's timezone, the bot checks in onc… |
| `alice-voice.yaml` | Private Yandex Alice voice input for Hermes, with replies in Telegram. Disclosure — off until you set enabled: true and allow_gateway_injection: true; then, while the Telegram gateway is connected, it listens on 127.0.0… |
| `ample.yaml` | Ample (ample.computer) as native tools: deploy the websites and web apps Hermes builds to public HTTPS URLs, release changes to the same URLs, read build and runtime logs, list and delete apps; bundled skill ample:web-a… |
| `anatomy-museum.yaml` | Native Anatomy community gallery with search, local favorites and explicit sandboxed standalone playback. Disclosure — when opened it fetches gallery metadata and thumbnails from a third-party GitHub repository (wheresr… |
| `ando-platform.yaml` | Connect a Hermes agent through an existing Ando invitation and receive authorized messages. Disclosure — connects outbound to Ando (mcp.ando.so, api.ando.so, realtime.ando.so) with an agent API key stored at $HERMES_HOM… |
| `android-emulator.yaml` | Control a headless Android emulator from Hermes — live sidebar, app management, GPS/battery/network simulation, and ADB tools. Emulator host is Linux. Disclosure — requires a pre-installed Android SDK under ~/Android/Sd… |
| `antenna.yaml` | Signed messaging with paired Hermes and OpenClaw agents, with receiver-controlled live and opt-in non-YOLO headless delivery. Disclosure — runs a loopback-only Node receiver when listen_port is set (you expose only its… |
| `antigravity-agy.yaml` | YAML definition for `antigravity-agy` |
| `antigravity-oauth.yaml` | Sign in to Google Antigravity with `hermes auth add antigravity-oauth` (or one command, `npx hermes-antigravity-oauth`) and run Hermes on the Antigravity plan: Gemini 3.x, Claude 4.6, GPT-OSS. Every request is made by G… |
| `antigravity-subscription-directsdk.yaml` | Run Hermes on an Antigravity subscription via the official agy CLI (DirectSDK path). Streams tokens progressively, persists multi-turn trajectories via agy --conversation (up to 239k tokens), discovers models dynamicall… |
| `anyapi.yaml` | AnyAPI.ai — unified OpenAI-compatible access to 400+ models; /model picker filtered to tool-capable routes. Disclosure — sends your prompts, tool results and ANYAPI_API_KEY to api.anyapi.ai, a third-party relay (AnyAPI… |
| `anyrouter.yaml` | AnyRouter — unified model gateway (OpenAI-compatible); /model picker filtered to tool-capable routes, first-party meta-models like anyrouter/hermes. Disclosure — sends your prompts and ANYROUTER_API_KEY to anyrouter.dev… |
| `anysearch.yaml` | AnySearch web search and extraction plus two real-time fallback chains: when a primary backend fails (Exa quota, Firecrawl timeout), the same call is served by AnySearch (1,000 free requests/day). |
| `aphrodite.yaml` | CCR compression plugin - 28-type classifier, 13 tools, opt-in context engine, TOML-driven templates. Disclosure - pre_tool_call auto-backgrounds long terminal/process commands (modify: background=true, notify_on_complet… |
| `apify.yaml` | Apify, the largest marketplace of tools for AI: discover, run, and collect results from |
| `approval-ledger.yaml` | Local ledger of Hermes's approval prompts (dangerous commands, protected writes, MCP consent, smart-mode verdicts): /approval-log shows how often each rule asked, how many prompts were approved, denied or left unanswere… |
| `ard-kit.yaml` | Agentic Resource Discovery — search a local tool catalog by intent and inspect an entry to |
| `artifact-relay.yaml` | Publish and read private Markdown or HTML reports through your Artifact Relay server. |
| `artifacts.yaml` | Private library for the finished documents agents make (self-contained HTML, Markdown, SVG, PNG, WebP), with an Artifacts dashboard tab and explicit, expiring, revocable guest links for one artifact each. Early public p… |
| `aside-browser.yaml` | Use the signed-in Aside browser as Hermes's browser when the Aside CLI is installed. Disclosure — runs the local aside CLI to drive your signed-in Aside browser (page text, screenshots, Aside memory, model-written JavaS… |
| `astro-agents.yaml` | Exact Western and Vedic astrology through the Astro Agents MCP server (Streamable HTTP at https://astro-agent.dev/mcp, no sign-in, no keys in config): birth chart, transits, synastry, kundli with D1-D60 divisional chart… |
| `athletedata.yaml` | The athlete's own training and health data from 39 apps (Garmin, Oura, WHOOP, Hevy, Apple Health, Intervals.icu and more) through athletedata's hosted MCP server (Streamable HTTP at https://mcp.athletedata.health/mcp):… |
| `atmorouter.yaml` | AtmoRouter — OpenAI-compatible gateway; one key for Claude, GPT, Gemini, GLM, Kimi, Qwen, DeepSeek, MiniMax and Grok models, with the /model picker fed by the live GET /v1/models catalog. Disclosure — sends your prompts… |
| `author-feed.yaml` | Read one public profile and watch one account, with profile_get, author_feed and author_watch. It reads public posts and profiles from the Bluesky social media network, which is built on the AT Protocol (atproto), witho… |
| `auto-pin.yaml` | Automatically pin every new interactive session (desktop, CLI, TUI) and the branches you fork from them. Cron, one-shot, subagent and messaging sessions are left alone, and unpinning a session sticks. Disclosure — on ea… |
| `aux-ledger.yaml` | Local ledger of Hermes's auxiliary LLM calls (titling, compression, vision, approval): /aux shows tokens, time and failures per task, model, provider or day, or lists the newest calls (ten, or up to 100 with /aux recent… |
| `b64-ref.yaml` | @b64: context references that decode encoded text for the model: @b64:<value> takes base64 (standard or URL-safe, padded or not), hex (0x48656c6c6f, 48:65:6c, \\x48\\x65), percent-encoding or a data: URI, told apart by… |
| `background-review-watch.yaml` | Nous Hermes plugin catalog entry — background-review-watch OWNER-SUBMITTED (rule 5): the PR author (vectorforge22) owns the repo. |
| `backupdrill.yaml` | Back up a Supabase project to your own S3, R2 or B2 bucket with the open-source backupdrill CLI (the Postgres database, plus Storage files once their S3 keys are set), then restore the snapshot into a throwaway Postgres… |
| `beam.yaml` | Move data across cloud storage and exchange end-to-end encrypted messages, files and media between agents with Beam Network (Bittensor SN105). |
| `bento.yaml` | Bento (bentonow.com) email marketing: subscribers, tags, fields, events incl. $purchase, stats, draft/scheduled broadcasts and transactional email, with dry-run + human-approval gates on every send. Native Python plugin… |
| `better-session-appearance.yaml` | Set a color for each session and show an idle glyph to make rows easier to scan. |
| `betterdb.yaml` | BetterDB long-term memory provider — semantic recall on Valkey / valkey-search via the betterdb-agent-memory SDK. Completed turns are embedded and stored in a vector index; the next turn recalls the most relevant memori… |
| `bharatcode-provider.yaml` | BharatCode (bharatcode.ai) OpenAI-compatible model provider — free student tier, native /model integration. Disclosure — model provider; prompts, tool schemas and BHARATCODE_API_KEY go to bharatcode.ai (BharatCode, Indi… |
| `bilinc.yaml` | Hosted memory for Hermes with a full history: see what your agent remembered, when it changed and why. Recalls relevant memories before each turn, adds bilinc_recall, bilinc_remember, bilinc_revise and bilinc_forget too… |
| `billing.yaml` | Nous Portal usage widget for the Hermes desktop statusbar — remaining credits plus plan-usage percentage, with portal detail on hover. |
| `biomimetic-brain.yaml` | YAML definition for `biomimetic-brain` |
| `birkin-mnemosyne.yaml` | YAML definition for `birkin-mnemosyne` |
| `blackbox.yaml` | Security for agents: checks every tool call and model request before it runs against a curated, verifiable threat graph (prompt injection, dangerous commands, malicious packages, unsafe skills, phishing and drainer indi… |
| `blender.yaml` | Official Blender Lab MCP server over stdio, pinned to upstream v1.0.3, with a Blender workflow skill. Needs Git and uv; Blender 5.1+ is not needed at install. The skill opens Blender itself when a task needs it and, aft… |
| `blinkenbar.yaml` | Dense, animated supercomputer light banks driven by system telemetry and live agent activity in Hermes Desktop. |
| `boardstate.yaml` | A live board your agent builds for you: tabs of notes, tables, charts, KPI cards and live Hermes data, in the dashboard and Hermes Desktop. It appears as a Board tab in the dashboard and a page in Desktop, and the agent… |
| `bot-activity.yaml` | Community catalog entry, bot-activity Owner-submitted: the repository is maintained by risyadul, and this entry is opened by its owner. |
| `bot-cabinet-v2.yaml` | Tell Cabinet the job you need done and it answers with the smallest setup that does it (one chat, a skill, a routine, a Bot or a crew), shows which answers led there, then helps you act: add one of botcabinet.com's 20 B… |
| `bot-forge.yaml` | Say \"make me a <role>\" and your agent spawns a complete Bot Mode Bot — name, face, SOUL.md, memory, tools, skills, routines, gateway — tested, with rollback. Then hire a whole crew in one call, ask what is waiting on… |
| `brain-graph.yaml` | Local Markdown vault for Hermes Desktop — notes, wikilinks, search, recycle bin, and an interactive graph. |
| `brave-search.yaml` | Brave Search API tools for live web search inside Hermes |
| `brethof-brain.yaml` | brethof-brain long-term memory provider — the memory's briefing in the system prompt at session start, ambient recall on every turn, every turn archived; one memory shared with the user's other agents (Claude Code, Code… |
| `bridge-adapter.yaml` | Generic JSON-file-based bridge adapter. Bridges self-register via a registry/ manifest (presence = registered, rm = unregistered). Polls inbox/ for incoming messages, writes outgoing to outbox/. External services (imsg,… |
| `browser-toggle.yaml` | Browser Toggle — one titlebar button that opens and hides the built-in browser. |
| `browserless.yaml` | Browserless — cloud browser provider for Hermes' built-in browser tools. Owner-submitted by a Browserless maintainer. Registers one browser provider (no tools, hooks or |
| `browserpaw.yaml` | YAML definition for `browserpaw` |
| `bubblewrap.yaml` | Bubblewrap terminal backend for Linux: every terminal and execute_code command runs in its own bwrap |
| `bunny_space-platform.yaml` | Bunny Space gateway adapter for Hermes Agent. Connects a Hermes profile (the bot brain) to the Bunny Space relay so the bot joins private rooms, answers its owner, and handles @bot:<slug> mentions in posts and comments.… |
| `burnclock.yaml` | Status-bar chip showing the provider balance and runway tracked by the MIT burnclock CLI, read from its local badge cache. Requires the CLI (pip install burnclock); the plugin makes no network calls and reads no credent… |
| `by2kb.yaml` | Discover learning videos by topic, select numbered recommendations, and turn Bilibili and YouTube videos into transcripts, abstracts, and study notes using the Hermes host model. Disclosure — intercepts gateway messages… |
| `call-me.yaml` | /call-me gateway: text your Hermes agent from the /call-me iPhone app, and the callme_call tool rings your phone, speaks the agent's text and returns your spoken answer as a transcript. Disclosure — talks only to the /c… |
| `camofox-human-auth.yaml` | Universal human-controlled authentication for Camofox Browser, powered by the Camoufox engine. |
| `camofox.yaml` | Camofox browser backend: browse with a self-hosted anti-detection Firefox (Camoufox, C++ |
| `carbonvoice-platform.yaml` | Carbon Voice gateway adapter for Hermes Agent. Connects via Socket.IO (primary) with REST |
| `cashew.yaml` | Cashew — persistent thought-graph memory with local embeddings, organic decay, and autonomous |
| `cdp-manager.yaml` | Local Chrome CDP debug ports in the status bar (probe, launch, stop, recheck) |
| `channel3.yaml` | Shop 100M+ products across thousands of US retailers: search, compare every store's live price, and switch variants (color, size) on inline product cards in Hermes Desktop. Portable Agent Plugins v1 package (mcp.json +… |
| `chat-length.yaml` | Tells the user when a chat is getting too long and hands them a short opener for a fresh chat; the new chat pulls the earlier context itself via session_search, no handover document. Fill level from real provider token… |
| `chat-studio.yaml` | Offline conversation customization with one-click presets and plugin-owned settings. Disclosure — enabled by default; injects a stylesheet that restyles the Desktop chat transcript (width, fonts, spacing, optional colou… |
| `chatto-platform.yaml` | Chatto gateway adapter for Hermes Agent. Connects to a Chatto server (self-hosted team chat) |
| `cheatsheet.yaml` | Title-bar cheatsheet. Describe what you want to do and it points to a real command or a cited passage; live slash commands and plugins, plus cited passages from this install's docs. No runtime network. No self-update. D… |
| `chorepilot.yaml` | Your house and family chore board as Hermes tools, through ChorePilot's own MCP server on this machine, the LAN or Tailscale. Runs appliances (lights, climate, dishwasher/washer/dryer, sprinklers, vacuum and more via Ho… |
| `chronicle.yaml` | Local-first long-term memory and memory-aware context compression for Hermes — SQLite, no account, API key or hosted service required. Captures every turn durably, extracts beliefs with provenance, answers from memory (… |
| `chutes-provider.yaml` | Chutes model provider for Hermes Agent via API key. Disclosure — model provider; prompts, tool schemas and CHUTES_API_KEY go to llm.chutes.ai (or CHUTES_BASE_URL), plus a GET /models catalog probe with the same key |
| `cjk_sanitizer.yaml` | Strip unwanted Chinese (CJK) and Cyrillic characters from LLM output. Korean Hangul and Japanese |
| `claude-code-theme.yaml` | Unofficial Claude Code-inspired theme for Hermes Desktop, with light and dark palettes, rounded composer and side-panel cards, softer sidebar and menus, and a context-window meter beside the model switcher. Not affiliat… |
| `claude-subscription-directsdk.yaml` | Experimental model provider that runs Hermes turns on a Claude Pro/Max subscription through |
| `clinepass.yaml` | ClinePass model provider with live model discovery and a curated fallback catalog. |
| `cliproxyapi-provider.yaml` | CLIProxyAPI as native Hermes model providers: discovers each CPA provider group (Claude, Codex, xAI, Gemini, Kiro and others) and registers one profile per group on the wire its CPA executor accepts (Anthropic Messages,… |
| `cloudflare-sandbox.yaml` | Run Hermes terminal, file and execute_code tools in Cloudflare Containers, with the workspace saved to a snapshot when idle. Disclosure — you deploy the bundled Cloudflare Worker to your own account first; running conta… |
| `cloudflare-web-search.yaml` | Cloudflare Web Search backend for Hermes' existing web_search tool, with Ceramic, Exa, or Linkup selected in plugin settings. Search only; keep a separate extract backend. Disclosure — sends queries, result limits, gate… |
| `cloudflare-workers-ai-provider.yaml` | YAML definition for `cloudflare-workers-ai-provider` |
| `coder.yaml` | Run Hermes terminal commands in an existing remote Coder workspace. Disclosure — runs terminal commands inside your Coder workspace at CODER_URL using CODER_API_KEY; starts a stopped workspace automatically; forwards on… |
| `codex-chat-look.yaml` | Independent Catppuccin Latte/Mocha desktop theme with peach accents, SDK-native gateway/profile switching and host-owned session density. Legacy plugin identity: codex-chat-look. No self-updater or native layout overrid… |
| `codex-theme.yaml` | Codex × ChatGPT inspired theme for the Hermes Desktop chat: dual light/dark palettes that follow the system appearance, graphite-on-paper typography with a 1.625 root line height (measured from ZCode's chat body) and co… |
| `codex-truly.yaml` | Gives ChatGPT/Codex-subscription models the context window the backend actually accepts instead of the one its catalog advertises. Measured live on 2026-10-14: gpt-6.1-sol advertises 500K, caps at 872K and accepts 919,9… |
| `cognee.yaml` | Knowledge-graph memory for Hermes, shared with Cognee's Claude Code, Codex and OpenClaw plugins: automatic recall, remember, forget, recaps and code search, on a local cognee server or Cognee Cloud. Disclosure — runs a… |
| `cognition.yaml` | Cognition session-end memory — facts regex-extracted from your messages at session end, stored in a local SQLite queue and JSON log under one repo label, with fetch-first merge, per-entry provenance, and budgeted prefet… |
| `colorado-traffic.yaml` | Live Colorado highway events from CDOT COtrip. No API key. Default corridor |
| `command-ledger.yaml` | Local ledger of the slash commands you run in Hermes (built-in commands in the CLI, built-in and plugin commands on messaging platforms): /command-log shows how often each command was used, its share, in how many sessio… |
| `command-tray.yaml` | YAML definition for `command-tray` |
| `commandcode-oauth.yaml` | Command Code CLI-key model provider with a live OAuth catalog property bridge, plan limits and failover classification. Disclosure — uses the CLI-internal api.commandcode.ai/alpha/generate endpoint and CLI client header… |
| `comment-scraper.yaml` | Ask about the Reddit and Hacker News threads you exported with the Comment Scraper browser extension: list, read, search and quote them by comment number. Disclosure — starts a local stdio MCP server with npx -y comment… |
| `compartment.yaml` | Encrypted, fully offline memory provider. AEAD-encrypted local vault (vectors included), |
| `completion-sound.yaml` | Pick the sound Hermes Desktop plays when a turn finishes: one of the 14 built-in presets or your own audio file (mp3, wav, ogg), with an optional different sound during night hours. Files stay in the plugin''s local sto… |
| `composer-modes.yaml` | Cursor-style composer modes (ask / agent / plan / debug) for the Hermes desktop — |
| `context-audit.yaml` | Context-window forensics: per-turn input/output token estimates, the single largest tool output of each turn, oversized tool calls (args over 50 KB), and compaction events, recorded as metadata only (tool name, byte len… |
| `conxt.yaml` | Conxt governed memory provider — recall before each turn (personal, plus a team's approved memories), conversation capture in batches, and tools to search, remember, and propose team memories that a person approves in C… |
| `corpus.yaml` | Hosted Corpus MCP (Streamable HTTP at corpuslaw.us/api/mcp) plus two bundled |
| `cortexlayer.yaml` | YAML definition for `cortexlayer` |
| `covision.yaml` | YAML definition for `covision` |
| `crawl4ai.yaml` | Crawl4ai self-hosted web content extraction. Requires CRAWL4AI_URL and CRAWL4AI_API_TOKEN |
| `crew.yaml` | One /crew message becomes verified work on the kanban board. A coordinator owns every card until its proof command exits 0 - one writer per card, an independent verifier, a hard token budget per card, and a live local d… |
| `cron-bulletin.yaml` | Central Hermes Desktop inbox for reports produced by local cron runs. |
| `crontab-ref.yaml` | @crontab: context references that explain a cron expression for the model: @crontab:\"0 9 * * 1-5\" (or a shortcut such as @crontab:@daily) attaches a plain-words reading (\"At 09:00 on Monday through Friday.\"), each f… |
| `crypto-prices.yaml` | Live crypto price ticker for the desktop status bar — Top 10 by market cap, seamless marquee, custom coins & 60+ display currencies, adjustable width (CoinGecko, no API key). |
| `csharp-game-editor.yaml` | Give it one feature for the Unity project open in your editor, and it builds the scripts, objects and scene in one plan, stops that plan when the compile reports an error CS line, and plays the scene when the compile is… |
| `ctx_checkpoint.yaml` | Memory provider that archives the direct user/assistant transcript into a ctx knowledge store before every compaction, deterministically and with no LLM in the path, and hands the resulting block IDs to the compaction s… |
| `cua-spaces.yaml` | Cua's own plugin: runs Hermes's terminal, file and code tools inside a Cua Space, an isolated Linux, macOS or Windows machine you can watch live, as a terminal backend (`hermes config set terminal.backend cua`). On Herm… |
| `cursor-acp.yaml` | Use your Cursor subscription models (Claude Opus/Sonnet 5.5, Composer 2.5, GPT-5.6, Grok) inside Hermes Agent via the Cursor CLI's ACP server (`agent acp`). Install with one command (`npx hermes-cursor-acp`) or `hermes… |
| `cursor-provider.yaml` | Cursor model provider using the official proprietary Cursor SDK. Disclosure — uses Cursor's proprietary cursor-sdk (PyPI, bundled binary bridge on loopback) with the user's CURSOR_API_KEY; sends the full conversation, t… |
| `cursor-sdk.yaml` | Experimental model transport using the official Cursor Agent SDK. Requests go to Cursor through its official SDK. The plugin cannot enforce an included-only spending cap and never changes account spending settings. Inst… |
| `custodian.yaml` | Autonomous operations monitor for a Hermes install: scans gateway logs, cron jobs, skill journals and agent data directories, classifies findings against a 27-fingerprint registry, auto-repairs Tier 1 problems, escalate… |
| `custom-dangerous-patterns.yaml` | YAML definition for `custom-dangerous-patterns` |
| `cut-sprite-sheet.yaml` | pixel art sprite sheet cutter. png to tileset splitter. cut pixel art into game tiles. sprite sheet from pixel png. 2d walk cycle sprite sheet. tileset cutter for pixel art. split png into sprite sheet. shore tiles tile… |
| `darkmoon.yaml` | Triage the findings file of a Darkmoon autonomous pentest scan (JSON or SARIF): filter by severity and proof status, get a severity-sorted summary and a pass/fail gate for a release. Read-only and offline: no network, n… |
| `dashboard-auth-feishu.yaml` | Feishu / Lark OAuth sign-in for the web dashboard, admitted by tenant + open_id allow-list. Registers the `feishu` dashboard auth provider once plugins.entries.dashboard-auth-feishu.settings (app_id, tenant_key, owner_o… |
| `dashboard-auth-ldap.yaml` | LDAP / Active Directory password login for the web dashboard. Verifies credentials with an LDAP bind (direct or search-then-bind), never stores passwords, requires ldaps:// or StartTLS, and supports group restriction. R… |
| `dashboard-button.yaml` | Dashboard Button — one-click access to the Hermes Web Dashboard on 127.0.0.1:9119. |
| `dashscope-image.yaml` | DashScope (Qwen Cloud) image generation -- Wan 2.7 models via Alibaba Cloud Model Studio. |
| `dashscope-video.yaml` | DashScope (Qwen Cloud) video generation -- HappyHorse 1.1 models via Alibaba Cloud Model |
| `davinci-resolve.yaml` | Control DaVinci Resolve Studio live, or generate importable interchange files for free DaVinci |
| `day-panel.yaml` | A Today page in Hermes Desktop, plus hermes day show and check, built from sections you list in a YAML file: any program that prints JSON (your tracker, a script of yours), your open GitHub pull requests and review requ… |
| `de-law.yaml` | German federal law, EU law and German federal court decisions for Hermes Agent: read one section or article (§ 203 StGB, Art. 6 DSGVO, Art. 50 AI Act) in the source wording with version status (Stand), gazette reference… |
| `deadbolt.yaml` | Review and approve exact text-artifact writes through a local DeadBolt sidecar. Protects this plugin's commit tool only. |
| `debug-desk.yaml` | Today's git digest in the current repo, plus the last failed terminal |
| `deepgram-voice.yaml` | Deepgram Aura text-to-speech and Nova speech-to-text providers for Hermes Agent. |
| `deepinfra-sandbox.yaml` | Terminal backend running agent commands in isolated DeepInfra cloud sandboxes (deep_sands microVMs). Disclosure — runs agent commands in billable DeepInfra cloud sandboxes and uploads your Hermes skills, cache and skill… |
| `deepseek-search-fetch.yaml` | DeepSeek Search & Fetch as a backend for the built-in web_search and web_extract. Disclosure — sends web_search queries and web_extract URLs to api.deepseek.com with your DEEPSEEK_API_KEY and DeepSeek fetches the pages… |
| `deepseek-whale.yaml` | Live DeepSeek API peak/off-peak pricing whale for the Hermes desktop titlebar. Blue x0.5 off-peak, grey PEAK at full price, countdown on click, 30s repaint, no backend or API key. |
| `deferred-questions.yaml` | Durable non-blocking questions with exact answer binding and gateway continuation. Disclosure — its pre_gateway_dispatch hook sees every gateway message and consumes only `dq <id> …` answers from the stored recipient; w… |
| `degeneracy-guard.yaml` | Asks the user to confirm a tool call whose arguments look like a repetition loop rather than data, through Hermes' approval gate (denied or unanswered means refused); replaces flagged degenerate output with a short noti… |
| `deja-memory.yaml` | Memory from the coding sessions already on this machine — Claude Code, Codex, Cursor, Hermes and the other agents deja reads, including history from before it was installed. No model, no API key, no server. Disclosure —… |
| `desensitize.yaml` | Chinese-context desensitization for Hermes chats. Replaces PII and business-sensitive |
| `deskrpg.yaml` | Hermes gateway integration for DeskRPG virtual offices, with profiles, kanban, cron, artifacts and NPC skill management. Install it through the DeskRPG setup wizard. Optional (off by default): when enabled by the operat… |
| `devin.yaml` | Delegate coding tasks to the Devin CLI, on your computer or in Devin Cloud, with live progress cards and change review in Hermes Desktop. Every launch goes through Hermes approval; Cloud runs need a separate Cloud-manag… |
| `devkit.yaml` | One managed home for agent drafts: a per-session scratchpad of named buffers the agent edits in place instead of writing a new temp file per revision. Buffers live under plugin-data/devkit/, open in the Desktop code vie… |
| `dexio.yaml` | Dexio shared-wiki memory. Before each turn, the pages of your Dexio wiki that match the user's message; tools to search, read and write the pages your other agents and team also use. Nothing is captured automatically: n… |
| `diaktoros.yaml` | Unattended GitHub pull-request review between two Hermes agents: one pushes fixes, a different one reviews, rounds are capped in verdicts, a watchdog reports silent stalls, and the loop never merges. Disclosure — runs u… |
| `diff-review.yaml` | Analyze git diffs for common code quality issues — debug prints, hardcoded secrets, bare |
| `digital-marketing-pro.yaml` | Open-source marketing toolkit for agencies and in-house teams, one listing with three skill groups and 207 skills registered as Hermes skills: Digital Marketing Pro (strategy, SEO/AEO/GEO, paid media, CRM, analytics; 16… |
| `discord-tps.yaml` | Show live tokens-per-second and the active model on your Discord bot's presence. Disclosure — Replaces the Discord bot's public presence with the live tok/s figure and the model name of the most recent API call in this… |
| `doc-markdown.yaml` | Convert one local file to Markdown with doc_convert on Linux and macOS, built on Microsoft's MarkItDown. Microsoft and MarkItDown are trademarks of the Microsoft group of companies. Disclosure — the doc_markdown toolset… |
| `doctorpack.yaml` | Local-first diagnostics, safety audit, and incident postmortems for Hermes Agent. |
| `document-reader.yaml` | Profile-scoped document OCR for Hermes Desktop and HUD, with a guarded per-profile Windows |
| `done-bell.yaml` | Ring when a Hermes turn finishes so you can leave the window. OS |
| `draft-cards.yaml` | Email and chat-message drafts as reviewable cards in the Hermes Desktop chat. The agent's draft_card tool stores each draft and its revisions; the card shows recipients, subject and body, highlights the words each revis… |
| `drag-to-pin-session.yaml` | Pin or unpin sessions from their row with supported desktop SDK actions. |
| `duty-board.yaml` | Read-only dashboard tab and model-free /duty and hermes duty summaries for waiting conversations, unanswered messages, running turns, undelivered background results and failing cron jobs. Supports all 17 dashboard langu… |
| `eatwise.yaml` | Eatwise (外卖营养教练) — local-first Chinese dietary coach: deterministic meal |
| `echarts-in-chat.yaml` | Render a chart inline in the Hermes Desktop transcript: the model emits ::echarts{labels=... values=...} and the plugin mounts an interactive SVG chart (dataZoom slider, click-to-filter legend, resize-aware, 280-560px h… |
| `edit-ledger.yaml` | Local ledger of the turns in which the agent changed files with write_file or patch: /edit-log shows how many turns changed files, how many files in all, the median per turn, the most changed file type and how long ago… |
| `effortless-hermes.yaml` | Picks the reasoning effort for every prompt: a fast judge (Jev/TypeSafe, a local OpenAI-compatible model, or any custom API) reads the next message once per turn and rewrites the request's reasoning effort before it shi… |
| `elevenlabs-sound-effects.yaml` | ElevenLabs sound effects for Hermes: one tool, elevenlabs_sound_effect, that turns a text |
| `empiriolabs-media.yaml` | YAML definition for `empiriolabs-media` |
| `empiriolabs.yaml` | EmpirioLabs AI as a Hermes model provider (provider id `empiriolabs`): chat models with tool calling from the live EmpirioLabs AI catalog, each with its context window, image input and reasoning support declared to Herm… |
| `enchanted-composer.yaml` | Draft enhancement, reusable prompt libraries, undo/redo, and owner-bound full-duplex voice for Hermes Desktop. Disclosure — Derived from hermes-live-voice by Synero (itself derived from hermes-talk) and prompt-enhance b… |
| `entropicmem.yaml` | YAML definition for `entropicmem` |
| `epistemic-harness.yaml` | Record a provisional claim or uncertainty before an evidence-gathering step, then link the actual observation to it. |
| `error-ledger.yaml` | Local ledger of failed provider calls (rate limits, overloads, timeouts, context overflows): /errors shows how many attempts failed per model, provider or cause, how many Hermes could retry, and the most common HTTP sta… |
| `evalroute.yaml` | Route a task to the right (model, reasoning effort) arm before you start. Classifies the task into a lane, prints a provenance-carrying route card, and installs per-model reasoning-effort defaults. Strong rules run loca… |
| `event-read.yaml` | Read one CalDAV calendar collection you run, with list_events and read_event. Disclosure — Sends CALDAV_USER and CALDAV_PASSWORD as Basic auth to your CALDAV_URL, does not follow redirects, and starts no local program.… |
| `excel_line.yaml` | Excel-backed hierarchical long-term memory tree (10-row cap per workbook, dynamic branching, leaf pointers). Classifier defaults to the host model; third-party keyless rotation is opt-in. |
| `field-academy.yaml` | Learn Hermes by doing real work. Four paths (Messenger, Traveler, Crossroads, Boundary Keeper) climb Beginner, Intermediate and Advanced to a capstone on a problem of your own, and a fifth, Guide, covers setting Hermes… |
| `file-tray.yaml` | Session file tray — paths the Hermes agent touched via read_file, |
| `filebox.yaml` | Dual-panel commander file browser for Hermes Desktop — whitelist-guarded file CRUD, copy/move/symlink, media preview, multi-select, rename, and trash. No network I/O, no model tokens. |
| `financial-datasets.yaml` | Stock market data from Financial Datasets - financial statements, prices, SEC filings, insider and institutional ownership, KPIs, news, macro data, and a stock screener. |
| `fish-audio.yaml` | Lifelike voices for your agent: Fish Audio's expressive text-to-speech in 80+ languages, plus transcription, voice cloning and a voice library. The official Fish Audio plugin: Fish's Drama 3 model with word-level direct… |
| `flashdata-plugin.yaml` | Web search with Google Search; Google News, Google Images, Google Shopping, Google Video Search and Google Places for research. Use YouTube Search or YouTube Extended Search; retrieve YouTube metadata, YouTube transcrip… |
| `fleet-policy.yaml` | For administrators who pin settings through the managed scope: records what each agent role really sends to the provider (model, reasoning effort, service tier, plus the tier the provider says it served) next to the man… |
| `fluxer-platform.yaml` | Fluxer gateway adapter for Hermes Agent. Native Fluxer integration using Fluxer's bot REST |
| `fmsg-platform.yaml` | fmsg platform adapter for Hermes Agent. Real-time inbound over the fmsg-webapi WebSocket |
| `foresee.yaml` | YAML definition for `foresee` |
| `freight-reconciliation.yaml` | Payer-side freight reconciliation: import carrier bills and trip ledgers into a |
| `freshdesk.yaml` | Generic Freshdesk API v2 tools for Hermes Agent. Unaffiliated community connector, not a Freshworks product. Disclosure — calls the account's native Freshdesk HTTPS origin with profile-scoped secrets FRESHDESK_DOMAIN an… |
| `frihet.yaml` | Hermes plugin-catalog entry for hermes-frihet v0.2.1. Catalog: NousResearch/hermes-agent/plugin-catalog/frihet.yaml |
| `fusion.yaml` | YAML definition for `fusion` |
| `fxmacrodata.yaml` | FXMacroData macro and FX research: official-source economic releases, indicator history, release calendars, policy rates, yield curves, FX, commodities and COT positioning, with source citations. Native tools for 23 RES… |
| `gadget.yaml` | Talk to your Hermes from small ESP32 devices with a screen, microphone and speaker: hold a button, ask, and hear the answer. Adds a gateway platform where each device is a chat, plus tools to list devices, show a card o… |
| `game-dev.yaml` | Read-only project inspection and asset audits with playable-slice, asset-production, and verification skills. Disclosure — lists file names and sizes under any absolute project path the agent supplies (skipping hidden,… |
| `game-editor.yaml` | In the Godot 4 project open in your editor, it places assets into the scene, plays the game, and the next plan fixes each error from its file and line. Disclosure — Needs Godot 4.7 or later, the Godot AI 4.x add-on, and… |
| `gbrain-plugin.yaml` | Community (non-official) plugin wiring GBrain (garrytan/gbrain, MIT) into Hermes as a local memory layer over MCP: /gbrain status command, desktop starter, and per-profile Postgres setup/update/maintenance scripts. Not… |
| `gbrain-pointer.yaml` | Read-only memory.provider for GBrain (garrytan/gbrain, MIT; not affiliated). After each non-trivial turn it searches a GBrain MCP server (`gbrain serve --http`) in the background and injects up to the configured limit (… |
| `gbrain-retrieval-reflex.yaml` | pre_llm_call hook plugin, enabled with `hermes plugins enable`: injects ambient context from a GBrain instance before each turn (volunteer_context, then a hybrid-query fallback). Not a `memory.provider`. Silent no-op wh… |
| `gemini-live-bridge.yaml` | YAML definition for `gemini-live-bridge` |
| `gemini-media.yaml` | Google Gemini image (Nano Banana) and video (Gemini Omni) generation backends for image_generate and video_generate, in one plugin built on the google-genai SDK. Image: text-to-image and reference-guided editing (up to… |
| `genealogy-research-recipes.yaml` | YAML definition for `genealogy-research-recipes` |
| `genesispay-catalog.yaml` | Search products, services and shops listed on GenesisPay and read their verified-purchase reviews through the hosted, read-only GenesisPay Catalog MCP server (Streamable HTTP at https://catalog.genesispay.finance/mcp/ca… |
| `gh-ref.yaml` | YAML definition for `gh-ref` |
| `gigamail.yaml` | YAML definition for `gigamail` |
| `git-autosave.yaml` | Lightweight local alternative to directory checkpoints for Git projects. Before a mutating tool call it saves the affected repository's working state to a private local shadow ref (refs/hermes-autosave/<branch>, with re… |
| `git-hook.yaml` | Auto fetch/pull before reads, and commit + push only the files each turn changed, for every git worktree Hermes touches. Disclosure — after each turn it commits and pushes (push on by default; GIT_HOOK_PUSH=0 keeps comm… |
| `git-review.yaml` | Catalog entry for NousResearch/hermes-agent: plugin-catalog/git-review.yaml Pinned to the merge commit of v0.2.0 (release published 2026-10-25). Bump sha and version together. |
| `git-tasks.yaml` | Multi-repo GitHub issues & PRs in an Orca-style Tasks view for Hermes Desktop. Disclosure — uses your logged-in `gh` CLI and `git` through Hermes Desktop's shell bridge, or a GitHub token you paste in the panel (stored… |
| `githermes.yaml` | GitHub PRs and issues as a right workspace pane in Hermes Desktop, via the connected gh CLI. Disclosure — shells out to your logged-in gh CLI; the in-pane update pill only runs `hermes plugins update githermes` (no fetc… |
| `github-copilot.yaml` | GitHub Copilot model providers for Hermes: `copilot` (the Copilot API with your Copilot subscription: GPT, Claude, Gemini and Grok models, sign in with `hermes auth add copilot` or COPILOT_GITHUB_TOKEN / GH_TOKEN / GITH… |
| `github_app.yaml` | YAML definition for `github_app` |
| `glasser.yaml` | Glasser's hosted MCP: search, inspect and run 1,000+ paid data endpoints (people and company enrichment, SEO, web, social media, US property, stock quotes) with one key, pay per call. Portable Agent Plugins v1 package:… |
| `gmail.yaml` | Hermes Desktop Gmail mailbox UI for search, reading, and thread inspection, with preview-confirmed send, reply, archive, trash, and label changes. Uses the active profile's existing Google Workspace OAuth setup; email i… |
| `go-whatsapp.yaml` | YAML definition for `go-whatsapp` |
| `godot-studio.yaml` | YAML definition for `godot-studio` |
| `gondola-provider.yaml` | Gondola, a USDC-settled marketplace API for Venice AI inference |
| `gonogo.yaml` | Submitted to NousResearch/hermes-agent as plugin-catalog/gonogo.yaml. Kept here so the reviewed pin sits next to the code it pins; the copy in |
| `good-student.yaml` | Wrong-question diagnosis and study-action loop for parents and students — |
| `govee.yaml` | Discover and control Govee lights (power, brightness, color, white temperature, scenes) through Govee's developer API. Every command is checked against the model's advertised capabilities and ranges, then confirmed by a… |
| `greyridge-token-safety.yaml` | Skill that runs a pre-trade safety check on Base ERC-20 tokens (honeypot/sellability, measured transfer tax, owner/mint/pause flags, liquidity, SAFE/CAUTION/AVOID verdict) by curling the Grey Ridge x402 API's free previ… |
| `grok-acp.yaml` | xAI Grok subscription as a Hermes model provider, driven over ACP stdio. Disclosure — spawns the vendor grok CLI found on PATH (grok agent over ACP stdio, plus grok models / grok login during setup) and drives your exis… |
| `groq-provider.yaml` | YAML definition for `groq-provider` |
| `gurusup-brain.yaml` | Your company's memory in Hermes: search decisions, people, customers and projects across every source your team connected to Gurusup (Slack, HubSpot, Notion, uploaded documents and more), with the sources behind each an… |
| `ha-sidebar-navigator.yaml` | Full-power sidebar navigator & uncapped project/session explorer for Hermes Desktop. Bypasses the 3-session overview cap with searchable, scrollable project trees and timeline view. Disclosure — browses and acts on sess… |
| `hades-coding-workflows.yaml` | Coding workflow skills — dual-model harness, subagent-driven development, and implementation |
| `handflow.yaml` | Manus-style planning flow — the agent plans in steps and marks them as it works, with a live desktop pane. |
| `hardlight-ui.yaml` | Frontend design guidance with sixteen original style grammars, twelve craft references, dated modern-web capability recipes, explicit direction context, and stateless tools for bounded source inspection, color contrast,… |
| `health-data.yaml` | Local health and daily-context data store for Hermes. |
| `health-insights.yaml` | Deterministic, local-first analysis of your own Apple Health data - weekly trends, rule-based concern checks, nutrition versus Dietary Reference Intakes, an IOM energy target, lab results and opt-in modules (GLP-1 monit… |
| `healthcare.yaml` | Local-first personal health records: encrypted on-device Vault (AES-GCM) for |
| `healthrelay.yaml` | Read-only access to your own Apple Health data through a self-hosted HealthRelay receiver. Portable Agent Plugins v1 package with one stdio MCP server (ten read-only tools, including intake evidence; no raw SQL, no writ… |
| `heartbeat2.yaml` | Your agent follows up on its own: timed check-ins, recurring checks and watchers that wake it in the same chat when something changes. You (with /pulse) or your agent (with the pulse tool) arm follow-ups at a time, recu… |
| `hermes-aac.yaml` | Communication boards, explicit speech, switch scanning and reviewed AI proposals for Hermes Desktop. Disclosure — Desktop-only page; Speak sends your message text through the Hermes gateway to the TTS provider configure… |
| `hermes-activity.yaml` | Hermes Desktop session analytics and provider-reported usage: annual heatmaps, token mix, model breakdowns and source-period summaries. Disclosure — reads the selected profile's state.db read-only and, for the Providers… |
| `hermes-adaptive-effort.yaml` | Pinned to the v0.4.0 tag commit (repository-root payload, so no subdir). Update sha and version together for later releases; a bump is a new catalog PR. |
| `hermes-agent-builder.yaml` | Guided Desktop workspace in BOTS: tailored questions, reference files, editable instructions and capabilities, version comparisons, model-only trials, and native Bot Chat handoff. Saves specialists as separate Hermes pr… |
| `hermes-agent-mixer.yaml` | A mixing desk for how much a coding agent may change: four enforced dials (edits, write-scope globs, per-turn line budget, new-dependency policy) with /mixer, live presets, a Desktop dial panel in the composer, a web-da… |
| `hermes-anilist.yaml` | The Hermes plugin catalog entry for this plugin. THIS FILE IS NOT READ BY HERMES. It is kept here so the submission is a copy, |
| `hermes-asgard.yaml` | Twelve Norse gods carved in runestone and wood: Odin, Thor, Freyja, Loki, Frigg, Baldur, Tyr, Heimdall, Hel, Skadi, Freyr and Bragi, as Hermes Desktop themes. Install once, then switch with /skin <name>. Matching termin… |
| `hermes-atoll.yaml` | Native Hermes Agent plugin that runs the local Atoll notch monitor for Hermes session and turn status on macOS. Disclosure — macOS only. Starts a detached Node daemon on every Hermes session that reads state.db read-onl… |
| `hermes-auto-titler.yaml` | Topic-aware session title tracking for Hermes Agent. Hermes generates the first title by default; AutoTitler follows conversation changes and session close without changing the host title-generation switch. Disclosure —… |
| `hermes-beads.yaml` | plugin-catalog/hermes-beads.yaml — catalog PR: 1 commit, 1 file. sha = v0.1.2 tag commit 975263183... (jacobhausler/hermes-beads v0.1.2, |
| `hermes-blogwatcher.yaml` | YAML definition for `hermes-blogwatcher` |
| `hermes-board.yaml` | A Miro-like board the agent draws with its own tools and you edit in a desktop pane, both sides working on one JSON document. board_apply builds a whole diagram in one call from ordered ops (nodes, edges, free lines, gr… |
| `hermes-boot-screen.yaml` | Community catalog entry — hermes-boot-screen Owner-submitted: the PR author (`OMOX563`) owns and maintains the repo below. |
| `hermes-bot-hq.yaml` | Desktop fleet page plus a per-bot Home (status, metrics, alerts, tasks, routines, buttons) published by the bot as JSON. Disclosure — reads each local profile's home files, can run a declared cron routine from the UI on… |
| `hermes-call-ledger.yaml` | YAML definition for `hermes-call-ledger` |
| `hermes-chat-share.yaml` | Share Hermes Desktop conversations as long PNG screenshots, self-contained HTML, or Markdown — per-turn selection, turn gutter, search, per-turn collapsing and session metadata. The Hermes Desktop counterpart of dsh-sha… |
| `hermes-cloud-file-manager.yaml` | Cloud Files for Hermes Desktop — browse, search and sort by date, create folders and bulk-upload files and whole folders to the machine your agent runs on, preview its images, PDFs and code files, download a file, read… |
| `hermes-codex-resets.yaml` | Know the moment OpenAI resets your Codex usage limits. A status-bar chip counts the time since the last reset; when a new one lands, a small card rises out of it (chip-only while you type), with a history page of every… |
| `hermes-context-overview.yaml` | Context window usage at a glance: a Context button in the status bar shows tokens used vs. budget, percent full, free space and an estimated breakdown by category, plus context-file sources. Works during a running turn.… |
| `hermes-council.yaml` | LLM Council (karpathy/llm-council) as a Hermes plugin. Four fixed advisor seats (First-Principles Analyst, Skeptic, Pragmatist, Researcher) answer in parallel, anonymously review and rank each other, and a Chairman mode… |
| `hermes-cron.yaml` | Operating skill for Hermes cron: lifecycle rules (pause vs disable vs remove, `in 30m` vs `30m`), four ways to avoid needless LLM runs (no_agent, wakeAgent pre-check, monitor, [SILENT]), verify-after-change, a layered r… |
| `hermes-desktop-camera.yaml` | A camera button for the Hermes Desktop composer. Open the preview, take a photo, and the frame lands in the composer as an image attachment, ready to send. |
| `hermes-discord-rpc.yaml` | Native Discord Rich Presence (RPC) integration for Hermes Agent — real-time session, model, token, and tool tracking with local-only IPC. Disclosure — publishes your most recent session title (or, in full title mode, th… |
| `hermes-dpapi-secrets.yaml` | Resolve Hermes environment variables at startup from a single secret file encrypted with the Windows Data Protection API, instead of keeping provider keys in plaintext in .env or auth.json. Config is secrets.dpapi.map,… |
| `hermes-dreaming.yaml` | Nightly deterministic memory consolidation (\"dreaming\"): corroborates candidate facts with what humans actually said on distinct days, proposes the few worth keeping with a verbatim edit anchor, asks whether stale mem… |
| `hermes-experientiallabs.yaml` | Experiential Labs - OpenAI-compatible multi-model gateway provider (chat, /model picker, aux and curated fallback models, /usage wallet snapshot). All network calls go to api.experientiallabs.ai - /v1 chat + models via… |
| `hermes-federated-search.yaml` | Federated web search backend (provider name `federated`): fans one query out to multiple configured search backends in parallel and returns merged, deduplicated, relevance-ranked results (keyword scoring; optional LLM r… |
| `hermes-field-notes.yaml` | Field notes for a Hermes install: search known pitfalls before debugging and record new ones with root cause; register every local core edit as a patch note with a declarative checks file, then verify read-only after ea… |
| `hermes-fleet-connector.yaml` | Owner-approved universal phone pairing and bundled read-only Live Operations reporting for selected Hermes profiles. Disclosure — paired phones get broad fleet:operator access over the internet, including cron jobs (una… |
| `hermes-gemini-live.yaml` | YAML definition for `hermes-gemini-live` |
| `hermes-gensyn-delphi.yaml` | Seven read-only tools. Disclosure — Seven read-only tools for Gensyn Delphi prediction markets; no funds move and nothing is signed or sent. Needs Node.js 20.18+ and a manual `npm ci --ignore-scripts` in the plugin fold… |
| `hermes-gensyn-ree.yaml` | ree_validate_receipt, ree_verify_receipt, ree_infer. Validate does not re-execute and does not stand behind text_output, finish_reason, token_count, model.name, or ree_version. Verify re-executes on CPU. Infer runs one… |
| `hermes-guide.yaml` | Read-only diagnostics for Hermes configuration: /hermes-doctor in-session and hermes guide in a terminal. Nine read-only health checks (config, mcp, skills, commands, hooks, plugins, memories, sessions, update) and poin… |
| `hermes-herald.yaml` | Cross-profile agent dispatch for Hermes Agent — 12 tools for agents talking to agents: async dispatch with SSE completion, synchronous multi-turn chat, model-selectable in-process subagents, a durable SQLite run ledger,… |
| `hermes-honcho-plugin.yaml` | Desktop workbench for the Honcho memory behind the focused chat: read the newest conclusions, trace their premises, search messages, ask scoped questions, and add confirmed corrections or source files. Uses each profile… |
| `hermes-impossibl.yaml` | Impossibl, the AI gateway (100+ models from every major lab behind one OpenAI-compatible API), as a model provider |
| `hermes-insight.yaml` | Selection-definition lookup for Hermes Desktop. Select any text, get an AI definition with sources in a popup. Renders the definition inline, runnable code aside. Backend is a stateless hermes insight CLI; panel, provid… |
| `hermes-iroh-interconnect.yaml` | Authenticated Hermes agent-to-agent tasks and optional file transfer over Iroh QUIC. Disclosure — tasks from a paired peer run in your live gateway agent with its full toolset; pairing is confirmed via the tool's confir… |
| `hermes-jailbreak-kernel.yaml` | Jailbreak-kernel plugin for Hermes Agent (ported from dsh-infinite-gen-4): session-scoped modes (off/slim/on/full) with kernel profiles (core/research/creative/max), session-aware system-prompt sections, llm_request req… |
| `hermes-jetstream.yaml` | hermes-jetstream — catalog entry for NousResearch/hermes-agent. The sha is the release: bump it (and `version`) in the same PR. |
| `hermes-jev-routing.yaml` | Per-turn model routing for the request that is about to go out. Jev reads the turn, picks the tier it deserves, and the plugin rewrites the provider request onto that model, including the reasoning level when the reques… |
| `hermes-jina.yaml` | Jina Reader web backend for web_extract (r.jina.ai, works without a key) and web_search |
| `hermes-kame-api-rotation.yaml` | Smart API key rotation: the healthiest key for every call, each 429 / RESOURCE_EXHAUSTED / quota refusal sized from its own evidence. Install with its companion hermes-kame-provider, which hands Hermes this plugin's rot… |
| `hermes-kame-provider.yaml` | Companion to hermes-kame-api-rotation (install both). A model-provider plugin that re-registers Hermes' bundled API-key profiles unchanged except for create_client and create_messages_client, which return the rotation p… |
| `hermes-kemet.yaml` | Twelve Egyptian gods in painted relief and gold leaf: Thoth, Ra, Isis, Osiris, Anubis, Horus, Bastet, Sekhmet, Set, Nut, Ptah and Hathor, as Hermes Desktop themes. Install once, then switch with /skin <name>. Matching t… |
| `hermes-lang-ca.yaml` | Catalan (Català) language pack for Hermes Agent — UI translation for core (CLI, gateway, approval prompts and tips), TUI and Desktop. Covers all text-overridable catalog keys; preserves command syntax and non-text Deskt… |
| `hermes-lang-cs.yaml` | YAML definition for `hermes-lang-cs` |
| `hermes-lang-el.yaml` | YAML definition for `hermes-lang-el` |
| `hermes-lang-he.yaml` | YAML definition for `hermes-lang-he` |
| `hermes-lang-it-full.yaml` | YAML definition for `hermes-lang-it-full` |
| `hermes-lang-it.yaml` | Italian (Italiano) language pack for Hermes Agent — UI translation for core (approval prompts, gateway/slash replies, CLI, tips), TUI and Desktop. Coverage: core 3437/3437, TUI 1259/1259 and Desktop ~5,000 keys (missing… |
| `hermes-lang-ko.yaml` | YAML definition for `hermes-lang-ko` |
| `hermes-lang-pt-br.yaml` | Brazilian Portuguese (pt-BR) language pack for Hermes Agent covering all three UI surfaces — core CLI/gateway/platforms (3,477/3,477 keys), the Ink TUI (1,356/1,356) and the Desktop app (5,172/5,176). Every translatable… |
| `hermes-lang-th.yaml` | Thai (ภาษาไทย) language pack covering all three Hermes UI surfaces — Desktop (5,023/5,030), core CLI/gateway/platforms (3,437/3,437), and the Ink TUI (1,259/1,259) — 9,719/9,725 keys total (99.9%). All three catalogs ch… |
| `hermes-lang-vi.yaml` | Vietnamese (Tieng Viet) language pack for Hermes Agent — full UI translation across every surface: core (approval prompts, gateway/slash replies, CLI, tips), TUI, and Desktop catalogs. Checked against the English catalo… |
| `hermes-lcm-x.yaml` | Lossless memory for long sessions: LCM-X keeps every turn in a local store instead of compacting it away, and the agent can search and expand it. The store is local SQLite (lcm.db) with a recoverable DAG of summaries ov… |
| `hermes-ledgerline.yaml` | Inspect session costs and usage in Hermes Desktop. |
| `hermes-live-voice.yaml` | Full-duplex Live Voice for Hermes Desktop — GPT-Live-1 on the ChatGPT/Codex subscription via the local Codex app-server, with live transcript, voice tool calls and task delegation to the user chat. Disclosure — subscrip… |
| `hermes-loadout.yaml` | YAML definition for `hermes-loadout` |
| `hermes-memory-pane.yaml` | A Hermes Desktop pane for the built-in memory: see what the focused chat remembered, updated or forgot, and edit, delete or undo any entry without leaving the conversation. Works alongside the built-in memory; not a mem… |
| `hermes-memory-ui.yaml` | Read-only Hermes Dashboard and Desktop plugin for inspecting built-in, holographic, Mem0, Honcho, Mnemosyne, Hindsight, and ByteRover memory. Disclosure — reads the active profile's memory files, provider configs and pr… |
| `hermes-memory-wiki.yaml` | Memory Wiki dashboard tab and opt-in native Desktop page: browsable subject pages and daily logs derived from local session |
| `hermes-minimizer.yaml` | YAGNI coding and code-review guidance for Hermes: reduce over-engineering, reuse existing behavior, and preserve requirements. One static prompt section; no tools or hooks. |
| `hermes-mobile.yaml` | WebSocket platform for your own mobile, desktop or web app: it talks to the agent directly — text, voice, images, video and documents in both directions, approval/clarify/slash cards answered from the app, streaming edi… |
| `hermes-model-switcher.yaml` | Community catalog entry — hermes-model-switcher Owner-submitted: the PR author (nicolasestrem) owns and maintains the repo below. |
| `hermes-monitor.yaml` | Community catalog entry — hermes-monitor Owner-submitted: the plugin's contributors own and maintain the repo below. |
| `hermes-monitoring-dashboard.yaml` | Prompt-customizable desktop dashboard with live host metrics, session activity, clocks, calendars, and text widgets. Disclosure — polls ~/monitoring-dashboard on the desktop device through the Desktop native file bridge… |
| `hermes-mpp.yaml` | YAML definition for `hermes-mpp` |
| `hermes-muse-code.yaml` | Muse Spark in Hermes billed to the Muse Code monthly login (device-code login, no API key). |
| `hermes-muse.yaml` | YAML definition for `hermes-muse` |
| `hermes-newswire.yaml` | Breaking-news ticker for Hermes Desktop: a scrolling RSS/Atom/JSON-Feed strip above the |
| `hermes-nous-prices.yaml` | Browse Nous Portal model prices and account balances in Hermes Desktop. |
| `hermes-office.yaml` | View and manage Bot Mode agents in a shared office in Hermes Desktop. |
| `hermes-openwhispr.yaml` | Local-first OpenWhispr dictation history and shared notes for Hermes agents: find what the user said, search notes, transcribe local audio. Free local desktop bridge by default, paid cloud opt-in only. Skill-carrier plu… |
| `hermes-opper.yaml` | Opper, the EU-hosted AI gateway (700+ models behind one OpenAI-compatible API), as a model provider |
| `hermes-osint-map.yaml` | A live situational-awareness globe in Hermes Desktop: earthquakes (USGS), disaster alerts (GDACS), natural events (NASA EONET), US severe weather (NWS), military and nearby aircraft (adsb.lol), satellites propagated liv… |
| `hermes-pantheon.yaml` | Eighteen Hermes Desktop themes in dithered classical marble, one god each: all twelve Olympians plus Hades, Nyx, Helios, Selene and Medusa. Install once, then switch with /skin <name>. Matching terminal skins ship in cl… |
| `hermes-pets-all.yaml` | Browse every pet installed for this Hermes profile in its own desktop pane |
| `hermes-pickup.yaml` | Pick up where you left off: up to 10 cards (5 by default) of unfinished work from your recent Hermes chats, project folders and files, each with where you stopped and a one-click next step. Adapted from Herald OS by Luk… |
| `hermes-pii.yaml` | Uses local Presidio and spaCy to redact supported PII in outgoing user text. Disclosure — filters Chat Completions user messages and Responses user input locally; system prompts, tool outputs and tool-call arguments are… |
| `hermes-plex-music.yaml` | Mini-Plexamp for Hermes Desktop: statusbar player for your Plex music library — likes synced to Liked Songs, custom playlists with rename/delete, shuffle + repeat, sleep timer, queue editing, OS media keys. Needs only P… |
| `hermes-plugin-chrome-profiles.yaml` | Switch Hermes browser tools to a named Chromium-family profile (Chrome, Edge, Brave), local or remote, over CDP. |
| `hermes-plugin-gen.yaml` | Generate, scaffold, and extend Hermes Agent plugins from simple descriptions. |
| `hermes-plugin-guard.yaml` | Static review of candidate Hermes plugins; target code is never executed. |
| `hermes-plugin-netbox.yaml` | NetBox change management: query DCIM/IPAM objects, build a reviewed field-level diff, apply |
| `hermes-pokemon.yaml` | A cozy pixel-art companion garden for Hermes Desktop with three starters, nicknames, fetch, berries, XP, and optional evolution through all nine starter forms. The companion keeps you company on long turns, reacts quiet… |
| `hermes-project-stewardship.yaml` | Durable project ownership and bounded initiative management for Hermes fleets. Disclosure — a `pre_llm_call` hook adds a project's saved rules, decisions and facts to turns of bots assigned to that project; objective ch… |
| `hermes-proton.yaml` | Proton Mail, Calendar, Contacts and Drive for a Hermes Agent, through an MIT-licensed client built from Proton's own open-source Go libraries (go-srp, go-proton-api) — no Proton Bridge and no paid plan. Reads, searches… |
| `hermes-pubky.yaml` | Setup helper for managed Pubky agents. The launcher syncs agent state, including conversation database snapshots and portable configuration, to your remote Pubky homeserver. |
| `hermes-quest.yaml` | Read-only pixel-art RPG view of real Hermes Kanban and worker activity, with a live web dashboard tab and an optional native Desktop page. The Desktop page currently supports explicit local connections only; registry an… |
| `hermes-resetwatch.yaml` | Track subscription quotas and reset times in Hermes Desktop. Disclosure — probe.py re-executes itself under the Hermes Python interpreter located via HERMES_PYTHON / VIRTUAL_ENV / the parent process or the Hermes instal… |
| `hermes-rich-ui.yaml` | plugin-catalog/hermes-rich-ui.yaml — catalog PR: 1 commit, 1 file. Schema fetched 2026-09-28 from |
| `hermes-routines.yaml` | A minimal Routines page in Hermes Desktop that turns crontab's five cron.manage actions into a plain-language interface for non-developers - name a routine, pick a schedule, write the prompt, and pause or resume it. No… |
| `hermes-rss.yaml` | Read RSS and Atom feeds and discuss articles in Hermes Desktop. Disclosure — feeds and full articles are fetched with curl through the gateway's shell.exec on the connected Hermes host (public-IPv4 SSRF guard); opt-in A… |
| `hermes-rustpush-imessage.yaml` | Local-only iMessage platform plugin backed by a launchd-supervised OpenBubbles RustPush sidecar |
| `hermes-security-audit.yaml` | Approval-gated local security audit for Hermes Agent using Gitleaks, OSV-Scanner, and Semgrep CE. |
| `hermes-self-healing-context.yaml` | YAML definition for `hermes-self-healing-context` |
| `hermes-seo.yaml` | Native Hermes port of Claude SEO 2.4.2: 45 SEO workflow and specialist skills, a credential-scoped hermes_seo_run tool, an isolated Python runtime, and advisory JSON-LD feedback. Derived from Claude SEO 2.4.2 (MIT; FLOW… |
| `hermes-session-diff.yaml` | Persistent session file diffs, run comparisons, and individual edit history in Hermes Desktop. |
| `hermes-session-reset-policy.yaml` | Opt-in idle/daily gateway conversation resets. Reads the existing session_reset block |
| `hermes-session-warmer.yaml` | YAML definition for `hermes-session-warmer` |
| `hermes-sidepulse.yaml` | SidePulse lifecycle status backend; Desktop focus tracking requires the separate companion in the linked setup guide. Disclosure — forwards event names, a hashed agent id, the raw session_id and tool names to a local AF… |
| `hermes-slash-router.yaml` | Jev-powered routing for misspelled, shortened, and meaning-based slash commands in the Hermes Desktop composer. Preserves drafts when unsure. Requires a TypeSafe API key; every non-exact lookup uses paid TypeSafe API us… |
| `hermes-snapcompact.yaml` | Snapcompact context engine: archives conversation history as dense bitmap PNG frames that |
| `hermes-soniox.yaml` | YAML definition for `hermes-soniox` |
| `hermes-speech.yaml` | Give your agent the voice it deserves. Guided TTS and STT setup for |
| `hermes-ssh.yaml` | Manage SSH connections and remote workspaces in Hermes Desktop. |
| `hermes-structured-aux-models.yaml` | Routes selected Hermes auxiliary tasks (approval, MCP sampling, compression) through bounded |
| `hermes-stt-enhance.yaml` | Local speech-to-text (provider stt_enhance) with faster-whisper or opt-in sherpa-onnx Parakeet V3 and long-audio chunking, plus an optional bounded LLM pass that enhances the transcript using a custom skill, an inline p… |
| `hermes-subscription-meter.yaml` | Provider-neutral subscription quota matrix panel — each provider's subscription window as a single time x quota row (elapsed vs remaining at a glance), with UI-side show/hide per provider row. Disclosure — reads provide… |
| `hermes-switchyard.yaml` | Jev-powered Hermes plugin for skill/model routing, typed assess, DOM/Cua computer use, adaptive reasoning effort with a per-turn receipt line, and FTS rerank. Disclosure: the default-on adaptive llm_request sends up to… |
| `hermes-t3-control.yaml` | Bounded tools to list, read, create, and control local T3 coding threads on Linux and WSL2. |
| `hermes-tabular.yaml` | Tabular AI that grows with your tables — Hermes skills for honest tabular ML, one entry point. Disclosure — Installing pulls numpy, pandas, scikit-learn, pyarrow, joblib and pyyaml into Hermes's environment. The skills… |
| `hermes-tailscale.yaml` | Browse Tailscale devices and connect to remote Hermes instances in Hermes Desktop. |
| `hermes-talk.yaml` | YAML definition for `hermes-talk` |
| `hermes-taskbar-badge.yaml` | Windows taskbar badge on the Hermes window when a turn finishes. Calls navigator.setAppBadge on the message.complete event while the window is in the background, and clears it when the window regains focus or another se… |
| `hermes-teammates.yaml` | Give your agent a team: named subagents with their own instructions, tools and model, which it assigns work to, checks on and steers mid-task. The operator defines the roster; the agent follows up with a digest of earli… |
| `hermes-telegram-business.yaml` | Observe-with-approval Telegram Business Mode (secretary bot): Hermes drafts replies to your customers' messages and DMs each draft to you with Send, Edit and Discard buttons; nothing reaches a customer until you tap Sen… |
| `hermes-telemetry-dashboard.yaml` | Dashboard-only read plugin: visualize the shared-metrics telemetry Hermes collects locally — metric families, drilldowns, milestone timeline, install snapshot, and the exact next package payload. Send stays off. |
| `hermes-telemetry.yaml` | Observability + budget guardrails for Hermes Agent — tokens, cost, latency, tool calls per session and cron job. Persists to local SQLite. Exposes /stats and /budget slash commands. Disclosure — records per-session toke… |
| `hermes-tenuo.yaml` | YAML definition for `hermes-tenuo` |
| `hermes-terminal.yaml` | Run the Hermes terminal interface in a Hermes Desktop workspace tab. |
| `hermes-token-speed.yaml` | Live decode tokens-per-second chip for the Hermes Desktop status |
| `hermes-toolsmith.yaml` | Local developer tools, transformation recipes, and reviewed chat handoff inside Hermes Desktop. |
| `hermes-town.yaml` | YAML definition for `hermes-town` |
| `hermes-tripo.yaml` | Tripo 3D tools on Tripo's v3 API (openapi.tripo3d.ai). Text, photo or multiview to 3D, image edits, retexturing, splitting into parts, Smart UV, auto-rigging, preset animations, retopology, format conversion (FBX, USDZ,… |
| `hermes-trove.yaml` | YAML definition for `hermes-trove` |
| `hermes-vcc-engine.yaml` | Instant context compaction for Hermes Agent: builds the compaction summary in milliseconds with no LLM call, keeping the exact commands, exit codes, errors and files, each linked back to its original message for recall… |
| `hermes-vcc.yaml` | Algorithmic (no-LLM) context compaction engine: builds summaries by deterministic regex extraction instead of a summarizer-model call — zero-token, byte-reproducible, inside the built-in ContextCompressor; compacted tur… |
| `hermes-verifier.yaml` | Attach an independent verifier (advisor) model to your Hermes session: it reviews each primary-agent turn delta, raises findings (note / caution / blocker), and can steer a blocker back into the session before the prima… |
| `hermes-video-editor.yaml` | Local video editor for your own footage: 45 FFmpeg tools for the agent (cut, silence removal, 9:16 reframe, captions, music with ducking, loudness, platform export and checks) plus a visual editor in Hermes Desktop with… |
| `hermes-vision-inline.yaml` | Attach an image inline to the session model when it can see one, instead of letting an explicit auxiliary.vision backend describe it. Core already attaches images natively by default; what this plugin changes is an expl… |
| `hermes-vpn.yaml` | Named network exits for the agent's browser: ask it to browse from another country and it switches, then verifies by reading back the address the far end actually saw, never trusting a label. Any VPN, WireGuard config o… |
| `hermes-whatsapp-voice.yaml` | YAML definition for `hermes-whatsapp-voice` |
| `hermes-wincred.yaml` | Resolve Hermes environment variables from the current user's Windows Credential Manager at startup, instead of keeping provider keys in plaintext in .env or auth.json. Config is secrets.wincred.map, an ENV_VAR -> generi… |
| `hermes-windows-computer-use.yaml` | THEIA — The Human Environment Intelligence Aperture: virtual-desktop capture, fused stage |
| `hermes-windows-eventlog.yaml` | Answer \"why did this process die\" on Windows: three read-only tools over the Windows Event Log. win_crash_events reads Application Error / Application Hang / Windows Error Reporting / .NET Runtime records for a time w… |
| `hermes-windows-ops.yaml` | YAML definition for `hermes-windows-ops` |
| `hermes-windows-ports.yaml` | YAML definition for `hermes-windows-ports` |
| `hermes-windows-process.yaml` | YAML definition for `hermes-windows-process` |
| `hermes-workbench.yaml` | The Hermes desktop app in your browser. `hermes workbench` serves the desktop interface through the Hermes dashboard, for headless servers, VPSes and tablets. Disclosure — community plugin, not a Nous product. On the fi… |
| `hermes-worker-monitor.yaml` | Community catalog entry, hermes-worker-monitor Owner-submitted: the fork is maintained by djmango, and the entry is opened by |
| `hermes-workflows.yaml` | Agent-owned workflow graphs for Hermes — a background runner executes a JSON DAG of agent nodes, fan-outs (quorum) and human/machine gates with fingerprint replay-skip resume, cooperative steer, typed failure events and… |
| `hermes-wsl-terminal.yaml` | YAML definition for `hermes-wsl-terminal` |
| `hermes-wslc-sandbox.yaml` | Run Hermes' terminal, file and execute_code tools in a Linux container on Microsoft's WSL Containers (wslc) runtime, so Windows users who run WSL Containers get a sandbox without Docker Desktop. Disclosure — the plugin… |
| `hermes-xai.yaml` | YAML definition for `hermes-xai` |
| `hermes-zh.yaml` | YAML definition for `hermes-zh` |
| `hermes_otel.yaml` | OpenTelemetry for Hermes Agent: sessions, LLM and API calls, tool calls, sub-agents and approvals as OTLP traces, metrics and logs to any OTLP backend. Disclosure — sends span data including prompts, tool arguments and… |
| `hermetic.yaml` | Status-bar popover for Hermes Desktop with three views: Costs (spend, cache, pricing drift, OpenRouter provider routing), AAI (skill changes, ratings, tests and replays) and HDR (a guard for risky tool calls, hooks, des… |
| `hicortex.yaml` | Shared fleet memory for Hermes agents: every connected agent learns from all other agents connected to the memory, wherever they run. Sessions across machines and harnesses are distilled into one common brain overnight… |
| `hindsight.yaml` | Hindsight long-term memory provider — knowledge graph, entity resolution and multi-strategy retrieval (recall/reflect/retain tools plus automatic per-turn capture). Maintained by Vectorize; cloud, local external and loc… |
| `holographic.yaml` | Local fact-store memory provider: SQLite with FTS5 keyword search (word forms in English, Russian, Spanish, French, Portuguese, Indonesian, German, Hindi, Arabic, Bengali, Italian, Turkish, Polish and Dutch; Russian and… |
| `home-dashboard.yaml` | Personalizable rice-style Home page with draggable, resizable glass widgets for Hermes Web |
| `homeassistant-statistics.yaml` | Read-only Home Assistant Recorder statistics tools (ha_list_statistics and ha_get_statistics). Disclosure — each call opens an authenticated WebSocket connection to the configured Home Assistant instance using the activ… |
| `homeassistant.yaml` | Home Assistant gateway platform (state-change events in, persistent notifications and cron notify |
| `honcho.yaml` | Honcho is memory infrastructure for building stateful agents that understand changing people, agents, groups, projects, and ideas over time. Store messages and events, let Honcho reason in the background, then query pee… |
| `hopper.yaml` | Add and manage custom OpenRouter models in Hermes without modifying the core catalog. |
| `hud-teach.yaml` | Click-through numbered marks on any live Mac window — chess, games, |
| `huddo.yaml` | Huddo — group chat where people and AI agents talk in the same room. Join by invite link, read and reply, edit or unsend your own messages, react, whisper to one member, pair with your human, wait for new messages, and… |
| `hwiki.yaml` | Markdown wiki as Hermes long-term memory: plain files you and the agent edit together (Obsidian-compatible, git-versionable), local SQLite FTS5 search with optional qmd hybrid retrieval. Inspired by the Karpathy LLM wik… |
| `hyatlas.yaml` | HyAtlas 5 — self-hosted 8-layer memory provider backed by a pure-Go single-binary server you run yourself (chromem-go vectors, in-process BGE-small embeddings, hybrid vector + keyword search, bitemporal knowledge graph… |
| `hydradb.yaml` | Long-term memory for Hermes, backed by HydraDB. Relevant context is recalled before each turn, and completed turns are saved in the background. Disclosure — when selected as the memory provider, each turn's user message… |
| `hypd-ai-ads.yaml` | Read-only paid-media analysis for Google Ads, Meta (Facebook) Ads, Microsoft Ads, LinkedIn Ads, Google Analytics (GA4), Search Console and Merchant Center through the hosted HYPD MCP. Portable Agent Plugins v1 package w… |
| `icarus.yaml` | Self-memory and replacement models for Hermes agents. Remember your work. Train your replacement. |
| `identity.yaml` | View and edit the identity files (SOUL.md, MEMORY.md, USER.md, AGENT.md/HERMES.md) from chat, switch the active profile, and see per-line usage with colour-coded staleness timestamps. Adds six tools, /identity, /identit… |
| `image-utils.yaml` | Inspect, resize, crop, rotate, convert and re-encode image files in-process with Pillow - no shell, no ImageMagick, no network. |
| `inbox.yaml` | hermes inbox: one read-only view of everything in flight for the active profile: failed or paused cron jobs, stalled or dropped delegations, orphaned background processes, blocked kanban tasks, running work, undelivered… |
| `index-network.yaml` | Give your agent someone to talk to. Index is the social layer between personal agents. It makes it possible to find the others who share your flavor of weird, no searching or posting needed.\nYou're already telling your… |
| `index-search.yaml` | Search one index you run and watch one saved query, with index_search, index_health and index_watch. Disclosure — Sends MEILI_API_KEY as a Bearer token to your MEILI_HOST. Over plain http that key travels unencrypted, a… |
| `infisical.yaml` | Secret source plugin that resolves environment variables from an Infisical secret store (cloud |
| `inkbox.yaml` | Inkbox email, SMS/MMS, iMessage, voice, and A2A platform plugin for Hermes Agent. |
| `inline-platform.yaml` | YAML definition for `inline-platform` |
| `intelligent-tool-break.yaml` | Abort a stalled in-flight tool call with /break, send a note with /break {message}, or retry it with /again without cancelling the rest of the task. |
| `intelligent_memory.yaml` | Local-first Arabic/English intelligent memory with canonical facts, conflict lifecycle, bounded |
| `interim-ledger.yaml` | Local ledger of the messages models write in the middle of a turn, before their final answer (the text that comes with a tool call, which on chat platforms can arrive as messages of their own): /interim-log shows how ma… |
| `invinoveritas-receipts.yaml` | Signed, independently checkable receipts for Hermes approval verdicts and, since 0.2.0, for turns that stop on iteration exhaustion. Observe-only: a post_approval_response hook requests an invinoveritas decision receipt… |
| `iowap.yaml` | Fleet control for Hermes Desktop: live statusbar chip (N/M IOWAP nodes online), a draggable fleet pane, a full fleet page (status, load, queue depth, capabilities per node, activity) and a tasks page that submits to any… |
| `iteration-budget-meter.yaml` | Status-bar chip for the focused session per-turn iteration usage (N/60), with a hover tooltip and a click popover of per-request stats. |
| `ja-writing-guard.yaml` | Rule-based proofreading for Japanese business text: finds and fixes AI-style phrasing (stock phrases, monotonous sentence endings, overused symbols and Markdown, English-calque grammar) with line, column and a fix hint.… |
| `jackal-verified.yaml` | Typed adapter for the reproducible JACKAL v1.7.3 release: 41 catalog-derived verification |
| `jekyll-hyde.yaml` | Context optimization and execution alignment for agent sessions. |
| `jet-browser.yaml` | Community catalog entry — Jet Browser Owner-submitted by a Jet Browser maintainer. The pinned plugin is stdlib-only, |
| `jev-agent-router.yaml` | Agent Plugins v1 package: one skill plus one stdio MCP server (agent_route) started with uv run from the checkout. Needs uv on PATH. Registers no Hermes tools or hooks; do not expect jev_* tools. |
| `jev-approvals.yaml` | TypeSafe's Jev decision model as Hermes' smart-approval reviewer only: it cannot generate text and refuses every other task. Supports TypeSafe direct, OpenRouter, and configurable Jev-compatible HTTPS endpoints with opt… |
| `jev-cron-gate.yaml` | Skip agent cron runs that would do nothing: a pre-run wake-gate script asks TypeSafe Jev one yes/no question over a small state snapshot (files, changed-since-last-run, localhost URLs) and prints {\"wakeAgent\": false}… |
| `jev-curator.yaml` | YAML definition for `jev-curator` |
| `jev-effort-router.yaml` | Per-turn model AND reasoning-effort routing, decided by TypeSafe Jev, which rewrites the outgoing Ollama:Cloud provider request itself via the llm_request middleware. Every other catalog router picks a model and stops,… |
| `jev-judge.yaml` | TypeSafe Jev as a judgment layer — a pre-tool gate (shadow by default, enforce |
| `jev-mcp-router.yaml` | Agent Plugins v1 package: one skill plus one stdio MCP server (mcp_select) started with uv run from the checkout. Needs uv on PATH. Registers no Hermes tools or hooks; do not expect jev_* tools. |
| `jev-memory-selector.yaml` | Agent Plugins v1 package: one skill plus one stdio MCP server (memory_select) started with uv run from the checkout. Needs uv on PATH. Registers no Hermes tools or hooks; do not expect jev_* tools. |
| `jev-model-router.yaml` | Agent Plugins v1 package: one skill plus one stdio MCP server (model_route) started with uv run from the checkout. Needs uv on PATH. Registers no Hermes tools or hooks; do not expect jev_* tools. |
| `jev-skill-router-mcp.yaml` | Agent Plugins v1 package: one skill plus one stdio MCP server (skill_select) started with uv run from the checkout. Needs uv on PATH. Suggests at most one skill per request via the TypeSafe (Jev) cookbook pattern; roste… |
| `jev-skill-router.yaml` | Names the one skill from your live roster that fits the turn, before the model call — |
| `jev-typesafe.yaml` | TypeSafe Jev (System One) decision tools — atomic yes/no checks, routing, rubric scoring |
| `jev.yaml` | Explicit Jev decision sidekick via TypeSafe or Cloudflare; advisory judgments, no automatic tool gating. |
| `jira-browser.yaml` | Jira workspace for Hermes Desktop, linking tickets to Hermes Projects, worktrees, and conversations. Disclosure — reads a Jira API token from JIRA_* env vars or ~/jira-config/config.json (owner-only, read-only) and send… |
| `job-search.yaml` | A private, local-first job-search assistant that finds postings, judges them against your |
| `jot.yaml` | Notes, checklists and documents beside Hermes that your agent can read and update safely, with revision checks and undo for AI edits. |
| `jp-address.yaml` | Splits one Japanese address into prefecture, city, town and the remainder with address_split, built on Geolonia''s address data (CC BY 4.0, from the Digital Agency address base registry). Give it a Japanese postal addre… |
| `jp-charts.yaml` | Bar, line, stacked and 100% band charts as phone-sized PNGs for chat replies and reports, with Japanese text, 万/億 units and a required unit and source line. Every bar, point, label and tick is read back from the finishe… |
| `jp-chatwork.yaml` | Talk to Hermes from Chatwork rooms, built on the Chatwork API: put Hermes in a Chatwork room and ask it with [To:] or a reply, like a colleague; the answer comes back as a Chatwork reply. Polls the Chatwork API (no publ… |
| `jp-corporate.yaml` | Japanese corporate lookup (法人照会): find or verify a company by name or corporate number and read its gBizINFO record (basic info, subsidies, government contracts, awards, certifications, financials, patents, workplace da… |
| `jp-edinet.yaml` | Japanese filings on the EDINET API v2. It finds a Japanese company''s annual securities report (yuho) and other financial reports filed on EDINET, and reads headline figures such as revenue and total assets from a filin… |
| `jp-egov-law.yaml` | Japanese laws for Hermes Agent, built on the e-Gov Law API: find a law by name, abbreviation or phrase, read one article as in force today or on a given date, and check amendment history and enforcement dates, with the… |
| `jp-estat.yaml` | Japanese government statistics from the e-Stat API: search tables and fetch figures such as population, households, wages, and prices, with estat_search_tables, estat_table_info, and estat_get_data. Disclosure — It need… |
| `jp-kokkai.yaml` | Lists Diet meetings and returns a short speech excerpt, with kokkai_search, kokkai_speech, and kokkai_watch. Disclosure — Talks only to kokkai.ndl.go.jp over HTTPS GET with no API key. kokkai_search returns meeting meta… |
| `jp-reinfolib.yaml` | Quarterly MLIT prices for one city, via reinfolib_quarter. Use it for Japanese real estate and property prices in one city: it returns the number of recorded sales, the median trade price and the first 20 rows for a qua… |
| `jp-subsidies.yaml` | Japanese subsidy search and weekly watch, built on the jGrants public API. Disclosure — Searches api.jgrants-portal.go.jp with no API key and no daily request cap; each call waits at most 60 seconds and retries at most… |
| `junie-acp.yaml` | JetBrains Junie coding agent as a Hermes model provider over ACP. |
| `jwt-ref.yaml` | @jwt: context references that decode a JSON Web Token for the model: @jwt:<token> (or a quoted \"Bearer <token>\") attaches the header with the algorithm in words, every claim as JSON, the exp, nbf, iat and auth_time cl… |
| `kanban-gantt.yaml` | One board, three views, and each answers a different question: List says what the work is, Timeline says when it happened, Graph says what hangs off what. The Graph view draws a card per task and an arrow per dependency… |
| `kanban-graph.yaml` | Live, read-only dependency graph of the Hermes kanban boards in Hermes Desktop: every board as a band, tasks as cards, dependencies as arrows with implied ones folded away. Click a task to light up its whole lineage wit… |
| `kanban-live-gantt.yaml` | Community catalog entry — kanban-live-gantt Owner-submitted: the PR author (`ningfangbin`) owns and maintains the repo below. |
| `kanban-stream.yaml` | Live-stream Hermes kanban worker activity to a Telegram ops channel: one edit-in-place message per task with rolling tool-call history, elapsed timer, tokens/sec, thinking indicator, and a pinned final state (done/block… |
| `kanban-task-threads.yaml` | Give every Hermes kanban task a live Discord forum thread with a rewritten status card and append-only event log. Disclosure — sends task and lifecycle data to the configured Discord webhook (no host allowlist). Cards a… |
| `keenable-plugin.yaml` | Web search and page fetching through Keenable's hosted MCP server, with search and research skills: single-site and publish-date filters, result and snippet limits, and page fetches that return only what a prompt asks f… |
| `kfchow-llm-value-router.yaml` | Community catalog entry — kfchow-llm-value-router Owner-submitted: the PR author (kfchow-ai) owns and maintains the repo below. |
| `kimchi-acp-provider.yaml` | The Kimchi coding harness (kimchi.dev) as a Hermes model provider over ACP stdio — spawns kimchi --mode acp keeping the harness's permission prompts on (YOLO opt-in via KIMCHI_ACP_ARGS=\"--mode acp --yolo\"), the harnes… |
| `kimchi-provider.yaml` | Kimchi (kimchi.dev) models via the OpenAI-compatible API — live catalog from the metadata endpoint, API-key auth, gateway unknown-model 400s classified as model_not_found, and an identifying User-Agent (hermes-agent/<ve… |
| `kimi-code-delegate.yaml` | Delegate-only, fail-closed Kimi Code ACP integration for Hermes Agent |
| `kinocut.yaml` | Guardrailed local video editing: Kinocut's MCP server plus two workflow skills (editing and short-form repurposing). Trim, caption, reformat and check quality with local FFmpeg. Portable Agent Plugins v1 configuration a… |
| `kiro-acp.yaml` | Kiro CLI (AWS) as a Hermes model provider, driven over ACP stdio. |
| `kiro-provider.yaml` | Native Kiro model provider over HTTPS with AWS Builder ID / IAM Identity Center device login. Disclosure — dynamically registers an AWS OIDC public client named `hermes-kiro` during login and stores OAuth grants in Herm… |
| `kiwi.yaml` | Source suppliers and negotiate purchases through the Kiwi Buyer MCP server — an |
| `klipper-print-watch.yaml` | Built on the Moonraker HTTP API. Cron reports klippy_shutdown, complete, error, paused (after printing), cancelled, stalled. Disclosure — Talks to the one Moonraker URL you set. Over plain http on a LAN, MOONRAKER_API_K… |
| `kokoro-tts.yaml` | Local Kokoro-82M text-to-speech on Apple Silicon: adds the kokoro-mlx speech provider (tts.provider: kokoro-mlx) with sentence-by-sentence PCM streaming for voice mode, read-aloud and text_to_speech, 54 voices in nine l… |
| `kuma.yaml` | Uptime-Kuma monitoring for agents: the community MCP server for Uptime Kuma v2 (pinned @0.11.18 over npx stdio) with workflow skills for incident review, status digests, and confirmation-gated maintenance. Credentials s… |
| `kumiho-memory.yaml` | Recall and save decisions, preferences and facts in your Kumiho Cloud workspace. Portable Agent Plugins v1 package with hosted OAuth MCP and six skills. Disclosure — connects to Kumiho's hosted MCP at https://mcp.kumiho… |
| `lancedb-suite.yaml` | Local-first LanceDB vector memory with a strict write contract, calibrated abstention, typed relations, conflict tracking and a retrieval-quality gate. Requires local Ollama + nomic-embed-text. |
| `lancedb.yaml` | LanceDB hybrid memory — embedded vector + FTS recall, workspace facts, transparent forget. |
| `langfuse.yaml` | Langfuse observability for Hermes: one trace per turn, one generation per LLM call (usage |
| `laso-finance.yaml` | Spend USDC in the real world from Hermes: prepaid cards, gift cards, push-to-card, Venmo/PayPal and bank payouts, through the Laso Finance API. Native plugin, standard library only. Sign-in is the OAuth device flow (lin… |
| `ld-workbench.yaml` | Practice Lincoln-Douglas debate. A case workbench helps a student build their own case section by section (resolution analysis, value and criterion, contentions, evidence, blocks) with a coach that gives real help and a… |
| `letsfg.yaml` | Search and book real flights and hotels through the hosted LetsFG MCP server (Streamable HTTP, OAuth 2.1 + DCR), with the letsfg travel-booking workflow skill bundled: fares across airlines and the major travel sites, f… |
| `lib-docs.yaml` | YAML definition for `lib-docs` |
| `lightkeeper.yaml` | An Obsidian-compatible map of how your codebase works (modules, flows, integrations, platform traps, decisions), kept outside the repo and kept honest by hooks: a primer on the first turn, pointers to the notes that own… |
| `lightningai-rate-limit.yaml` | YAML definition for `lightningai-rate-limit` |
| `lightningai.yaml` | YAML definition for `lightningai` |
| `limbic.yaml` | Local long-term memory for Hermes agents. Everything stays on your machine: an SQLite store plus bundled embedding and NLI models, no telemetry, no LLMs.\nLimbic is designed on the physiological brain, opaque and organi… |
| `linkedcamp.yaml` | Plan, build and run LinkedIn and email outreach in LinkedCamp through LinkedCamp's hosted MCP server (Streamable HTTP at https://mcp.linkedcamp.com/mcp, OAuth sign-in with the account's API key, no keys in config): camp… |
| `linkup.yaml` | Linkup web search: live cited search (fast/standard/deep), URL-to-Markdown fetch with JS rendering, async deep research, and a Linkup backend for the built-in web_search / web_extract tools. Disclosure — sends search qu… |
| `liquid-inference-provider.yaml` | Liquid Inference, an auction exchange for LLM inference, as a Hermes model provider (provider id `liquid`): the exchange sends each request to the eligible offer with the lowest estimated charge, and each request carrie… |
| `little-canary.yaml` | Screens user turns and blocks downstream tools on a BLOCK verdict; the original prompt still reaches the model. |
| `live-time.yaml` | Inject live current time into every LLM call via the pre_llm_call hook — fixes stale session-start timestamps in long/cross-day conversations. |
| `llm-antidote.yaml` | Runtime guardrails, behavioral evaluation, and signed fleet admission for Hermes Agent: a versioned capability policy that blocks or requires approval for model tool calls, paired synthetic behavioral evaluation with no… |
| `llmslim.yaml` | Context engine that compresses older tool output and turns locally with LLMSlim instead of asking a model for a summary: no LLM call, deterministic output, and the start of the prompt is sent unchanged, so prompt cachin… |
| `loaded-skills-indicator.yaml` | Community catalog entry: loaded-skills-indicator Owner-submitted: the PR author (`yugasurfer`) owns and maintains the repo below. |
| `local-system-one-hermes.yaml` | YAML definition for `local-system-one-hermes` |
| `local_knowledge.yaml` | Native Hermes tools for a configurable local capability index: search/get/neighbors plus |
| `long-conversations.yaml` | Persistent long-term conversations across session boundaries via structured handoff briefs and token monitoring. Disclosure — stores handoff briefs (topic, work in progress, decisions, open questions, next step; in aggr… |
| `looot.yaml` | looot gives Hermes one sign-in and one prepaid balance for 2,500+ data API endpoints from 90+ providers: work emails and phones, company and people search, Google results, web pages as markdown, news, local businesses.… |
| `loreconvo.yaml` | LoreConvo memory provider: cross-surface persistent session memory with search, recall and structured memory items. Disclosure — stores end-of-session transcripts (truncated, including tool output) and Hermes memory wri… |
| `lowrouter.yaml` | YAML definition for `lowrouter` |
| `lumberroom.yaml` | lumberroom memory provider. One durable store shared with every agent you use, recalled on |
| `machine-library.yaml` | Research search for web_search and web_extract — papers, books, patents, standards and Wikipedia, with citable source links (Machine Library API key). |
| `machine-spirit.yaml` | A Warhammer 40k shrine pane docked under the sessions list: the cogitators recite original Adeptus Mechanicus-style litanies, and the cog-skull, candle and binary stream animate while Hermes works. Just for fun. Desktop… |
| `made-shelf.yaml` | Everything Hermes made - cross-session shelf of wrote/patched paths. |
| `magi.yaml` | Review pending Hermes memory writes and inspect, add, edit, delete, or AI-compact stored memory from Desktop. |
| `make-parts-now.yaml` | Quote and order custom 3D printed and CNC machined parts from your CAD files through the hosted Make Parts Now MCP server (Streamable HTTP, no sign-in to quote), with the quote-parts workflow skill bundled: upload an ST… |
| `maqami-travel.yaml` | Search hotels (3M+ hotels) and flights worldwide on MAQAMI, read hotel details and reviews, then send the customer a secure checkout link on book.maqami.co, through the official MAQAMI Travel MCP server (Streamable HTTP… |
| `markdown-new.yaml` | Search the public web, read pages as Markdown, crawl sites, and convert documents in Hermes. No API key required. Disclosure — search queries, submitted URLs and explicitly approved local file uploads go to the public m… |
| `markifact.yaml` | YAML definition for `markifact` |
| `max-platform.yaml` | MAX messenger gateway with polling/webhook, streaming, interactive questions, native attachments, Core voice transcription, optional PNG tables and a Desktop sessions sidebar. Disclosure — sends the bot token and messag… |
| `mcp-plugin-creator.yaml` | Turn any MCP server into a portable Agent Plugin (mcp.json + workflow skill) built from |
| `mcp-serve.yaml` | Run Hermes as an MCP server: `hermes mcp-serve` lets any MCP client (Claude Code, Claude |
| `meeting-overlay.yaml` | Disclosure — sends meeting transcripts to Nous inference with your Hermes login (fallback OpenRouter key from ~/.hermes/.env; optional OCTOPUS_DESK_URL); installs a launchd agent that records mic/system audio; writes an… |
| `mem-os.yaml` | Local-first persistent memory: store durable facts once and recall them in any |
| `mem0.yaml` | Mem0 memory provider — server-side LLM fact extraction with semantic search, automatic |
| `memanto.yaml` | Memanto memory agent — typed long-term memory (remember/recall/answer) with auto-recall, turn capture, and RAG answers. Disclosure — each user turn (as a recall query), completed user+assistant turns, Hermes memory writ… |
| `memex8.yaml` | Self-hosted vector memory (Qdrant + TurboQuant compression) with auto-discovered knowledge realms, semantic search across conversations and ingested documents, and a slumber pipeline for memory consolidation. v1.1.0 add… |
| `memlock.yaml` | Reasserts pinned standing instructions after context compaction. Disclosure — scope=global pins apply to every session sharing the same HERMES_HOME; memlock_setup.py edits config.yaml and .claude/settings.json (with bac… |
| `memobase.yaml` | Memobase memory provider — self-hosted user profile + event timeline |
| `memoria.yaml` | YAML definition for `memoria` |
| `memory-review.yaml` | Checkbox staged memory writes and approve or reject the selection from a dialog. |
| `memory-rewind.yaml` | YAML definition for `memory-rewind` |
| `memory-shield.yaml` | YAML definition for `memory-shield` |
| `memory-zvec.yaml` | Community Zvec memory backend for Hermes Agent - in-process HNSW + RocksDB FTS |
| `memtomem.yaml` | Markdown-first long-term memory shared across your coding agents: a local memtomem MCP server plus six memory skills (index, recall, remember, search, setup, status). Notes live in ~/.memtomem and are searchable from He… |
| `mermail.yaml` | Privacy-first agent email inboxes and workspace automation through hosted Mermail MCP. Portable |
| `meshy.yaml` | YAML definition for `meshy` |
| `metamask-wallet.yaml` | MetaMask Agent Wallet for Hermes — chat-only setup, reads, and approval-gated transfers/swaps/signatures, a gated Guard Mode policy editor, and a background 2FA watcher. Keys stay in MetaMask. |
| `metronix.yaml` | Metronix memory provider for Hermes with prefetch recall and built-in memory write-through. |
| `microsoft365.yaml` | Pre-release Microsoft 365 Graph tools for Outlook, SharePoint, OneDrive, Calendar, Teams, To Do, and Planner. |
| `mindgraph.yaml` | MindGraph — semantic graph memory with hybrid retrieval, goal/decision tracking, and cross-document |
| `minecraft-platform.yaml` | Minecraft gateway adapter for Hermes Agent. Spawns a Mineflayer bot that joins a Minecraft |
| `minimax-image.yaml` | MiniMax image generation -- Image-01 models via MiniMax platform. Supports text-to-image |
| `minimax-search.yaml` | MiniMax web search via the Token Plan API — keyed, no CAPTCHA |
| `minimax-video.yaml` | MiniMax (Hailuo) video generation -- Hailuo 2.3/02 and S2V-01 models via MiniMax platform. |
| `mistral-vibe.yaml` | Direct Mistral Vibe subscription access — browser PKCE login, dedicated credential pool, account-visible catalog discovery, relay-verified reasoning_effort for GLM models. Disclosure — unofficial, not affiliated with Mi… |
| `mixar.yaml` | YAML definition for `mixar` |
| `mnemostack.yaml` | Persistent agent memory over a mnemostack service or a local Qdrant — hybrid |
| `mnemosyne-dashboard.yaml` | Local-only web dashboard for browsing and visualising Mnemosyne memories, triples, stats, |
| `mnemosyne.yaml` | Local-first memory layer for Hermes Agent — SQLite with vector + FTS5 hybrid recall, episodic consolidation, temporal knowledge graph. Zero cloud. Disclosure — the mnemosyne_remember_media tool refuses local file paths… |
| `mnemoverse.yaml` | Persistent memory for agents, shared across tools: save preferences, decisions and lessons and recall them later by natural-language search; rating a recalled memory as helpful or misleading re-ranks what comes back nex… |
| `mock-review.yaml` | YAML definition for `mock-review` |
| `model-drift-watch.yaml` | Scheduled check that the model you use in Hermes has not quietly got worse: 34 fixed, exactly graded questions (reasoning, instruction following, Japanese, plus your own) run through Hermes cron, each run tested against… |
| `model-leaderboard.yaml` | Model leaderboard for Hermes Desktop: a full /model-leaderboard page that ranks any OpenRouter model for a chosen Hermes profile — context window, prices, Artificial Analysis indices and curated SWE-bench Verified / Liv… |
| `model-picker.yaml` | Per-turn cost classifier across three model tiers (Quick / Standard / Expert): rates each user turn from configurable best_for lists and rewrites the outgoing request's model through the llm_request middleware, biased t… |
| `model-router.yaml` | Explicit per-profile readiness and native missing-profile preparation; Python installation remains per profile, never automatic on refresh. Profile model settings, default-on Heavy/Light task routing, fallback controls,… |
| `model-usage-status.yaml` | Provider-native Claude and Codex remaining allowance windows in the Hermes Desktop status |
| `modernisation-engine.yaml` | Controlled migration engine: maps an existing codebase, turns the behaviour that must survive into reviewable contracts, prepares a separate candidate and records old/new evidence before any production change. Disclosur… |
| `monid.yaml` | Connect your agent to third-party tools and APIs (web search and scraping, people and company data, social media, media generation, email and phone) through one integration. The agent discovers, compares and runs tools… |
| `morning-briefing.yaml` | Personal daily newspaper for Hermes: gathers weather, calendar, AQI, curated |
| `mrscraper.yaml` | MrScraper page retrieval, Google search, and account usage via direct HTTP APIs. Disclosure — page and search requests can consume paid account tokens; target URLs, search queries, and request options are sent to MrScra… |
| `ms-decision-provider.yaml` | Microsoft-Decision-1 (Azure AI Foundry System One) decision provider for bounded agent decisions. Registers typed-decision tools (decision_noul, decision_choice, decision_score, decide) that preserve full probability di… |
| `my-github.yaml` | Desktop and dashboard plugin: statusbar chip, palette command, and dashboard tab listing your GitHub repos (public + private) via the gh CLI. |
| `mybot-farm.yaml` | Search mybot.farm, plant/reinstall Hermes packs (Desktop Recruit + CLI), and post GAF listings. Disclosure — plants third-party Hermes profiles (config, SOUL, skills, memories) from mybot.farm sellers with no hash pinni… |
| `myswarm.yaml` | Discover, visualize, sanitize/export, and import community agents.md swarm configurations. Outputs abbreviated agent/persona/goal tables, renders ASCII topology diagrams (.svg and .png images + portable 7-bit copy-paste… |
| `nachos.yaml` | Durable memory and context compression for Hermes Agent with local SQLite or flat-file storage. Disclosure — replaces the memory provider (memory.provider: nachos) and, only when context.engine: nachos is set, the conte… |
| `needs-you.yaml` | Hermes is waiting — full Desktop page for pending approvals. |
| `nerve.yaml` | YAML definition for `nerve` |
| `netmind-provider.yaml` | NetMind OpenAI-compatible model provider with a bundled model catalog. Disclosure — registers one model provider at import and nothing else (no tools, hooks, commands or threads); chat requests go to https://api.netmind… |
| `next-prompt.yaml` | Suggests your next message after each turn as a pill under the Desktop composer: your likely answer when the agent asks you something, or the natural next step. |
| `next-steps.yaml` | Next-step suggestions under the Hermes Desktop composer after each turn: local Ollama inference, per-session state, target routing (session, new tab, bots, kanban), tiny-model capacity profiles, EN/DE UI. No API keys. D… |
| `nextcloud-talk-platform.yaml` | Nextcloud Talk platform adapter for Hermes Agent, in two modes behind one plugin: a webhook bot (Nextcloud Talk Bot API, HMAC-SHA256 signed, with an explicit body-size cap and a nonce-replay cache ahead of payload parsi… |
| `nextcloud-talk.yaml` | Signed Nextcloud Talk bot webhooks and text replies for Hermes, with JSON/XML OCS support. Disclosure — runs an HTTP webhook listener (default 0.0.0.0:8788, HMAC-verified with the bot secret) and sends messages and opti… |
| `nextdns.yaml` | Read-only NextDNS tools - DNS query logs, blocked queries with the blocklist that matched, |
| `nexus.yaml` | Self-hosted long-term memory on Qdrant: automatic per-turn prefetch and write-back, plus recall/remember/forget, guardrail rules and a knowledge graph; Hermes and any MCP-connected agent share one collection. Embeddings… |
| `ngrok-ai-gateway.yaml` | YAML definition for `ngrok-ai-gateway` |
| `nine-balance-widget.yaml` | Community catalog entry — nine-balance-widget Owner-submitted: the PR author (`OMOX563`) owns and maintains the repo below. |
| `node-search.yaml` | Bounded Markdown metadata+graph prefilter for configured local roots |
| `nord-theme.yaml` | Unofficial Nord theme for Hermes Desktop with hand-tuned Polar Night (dark) and Snow Storm (light) palettes, Nord terminal colors, Nord code-block syntax colors, and Aurora status colors. Scoped to its own theme; other… |
| `nowstamp.yaml` | Give the agent a clock. Appends the current date and time, plus the real gap since the previous message, to every user turn. Optional spaced-out timestamps on tool results for long runs. |
| `ntfy-approval.yaml` | Answer Hermes' approval prompts from your phone: once selected with security.approval.transport: ntfy, each dangerous-command prompt arrives as an ntfy push notification with Approve once, Approve for session and Deny b… |
| `nvidia-app.yaml` | NVIDIA App control through its local MCP server: overlay capture and state, driver status |
| `nvidia-broadcast.yaml` | NVIDIA Broadcast control through its local MCP gateway: camera, microphone and speaker |
| `obsidian-memory.yaml` | Browse, search, and edit Obsidian vault notes from the Hermes dashboard. Features force-directed |
| `oc-free-provider.yaml` | Unofficial OpenCode Zen free-model transport for Hermes. Discovers live zero-cost tool-capable models by intersecting OpenCode Zen and models.dev over HTTPS, persists only the last successful intersection for restart fa… |
| `office-3d.yaml` | Catalog entry — office-3d Add this file at `plugin-catalog/office-3d.yaml` in a PR against |
| `office-desk.yaml` | YAML definition for `office-desk` |
| `offpeak-bekci.yaml` | Makes Ollama Cloud's off-peak window visible and actionable in Hermes: a desktop status-bar chip shows the countdown and the queue item counts (Ollama off-peak hours: weekdays 18:00-12:00 UTC, weekends one block), a one… |
| `omh.yaml` | Oh My Hermes (OMH) bridge: routing hints and role context for OMH workflow skills, per-task delegation model routing, plan todos and a status tool, a Hermes Desktop status pane (off until enabled), bounded evidence prob… |
| `omnivoice.yaml` | OmniVoice TTS provider for Hermes Agent |
| `opaque-composer.yaml` | Keep the desktop composer solid while scrolling so conversation text stays readable. |
| `openai-compatible.yaml` | GPT Image through CLIProxyAPI, New API, or any OpenAI Images-compatible gateway, with gateway-aware errors and requested-vs-returned size reporting. Disclosure — sends image prompts and any source images (local files, d… |
| `openalex.yaml` | Scholarly search, citation traversal, grouped counts, and fulltext access through OpenAlex with session spending limits. |
| `opencode-shepherd.yaml` | Community catalog entry: opencode-shepherd Owner-submitted: the PR author (okazakee) owns and maintains the repo below. |
| `openinvest.yaml` | Self-hosted AI investment committee — skills for portfolio review, a decision ledger, and a 4-role LLM committee (macro / quant / risk / CIO) that debates a symbol. Disclosure — the skills run the openinvest backend fro… |
| `openltm.yaml` | OpenLTM — long-term memory for Hermes agents. Source of truth: https://github.com/RohiRIK/OpenLtm |
| `openmail.yaml` | Gives a Hermes agent its own email address. Inbound mail wakes the agent over a websocket, |
| `openpaths.yaml` | OpenPaths model provider for Hermes: OpenAI-compatible inference at openpaths.io with auto, auto-easy-task, auto-medium-task, auto-hard-task and auto-think task-tier routes plus GPT, Claude, Gemini and DeepSeek models,… |
| `openrouter-picker.yaml` | One install: the Desktop model picker and the OR Picker composer provider. Checking a model here is what the composer lists. Disclosure — the optional OpenRouter management key is stored in plaintext in Desktop localSto… |
| `openrouter-spend.yaml` | OpenRouter API-key spend and recorded chat costs in USD/INR. Disclosure — sends the configured OpenRouter key (OPENROUTER_API_KEY, or the variable named in api_key_env) only to openrouter.ai's read-only key and generati… |
| `openrouter-voice.yaml` | OpenRouter speech-to-text and text-to-speech providers for Hermes Agent (stt.provider / tts.provider = openrouter). |
| `openspec.yaml` | OpenSpec CLI tools for spec-driven development workflows |
| `openviking.yaml` | Long-term memory for Hermes. Capture conversations, recall useful facts across sessions and search your knowledge. Choose Quick Local, OpenViking Service (managed cloud) or your own server. Disclosure — conversation tur… |
| `operations.yaml` | A Hermes Desktop page for running a fleet - topology, model traffic, handoffs, traces, merge requests and conformance checks in one place. Disclosure — reads hermes-metrics-dash's <hermes root>/metrics/metrics.db, the k… |
| `optchat.yaml` | OptChat-style endless memory for Hermes: an append-only verbatim log plus a binary summary tree, exposed as recall through the MemoryProvider ABC. Background compactor builds the tree with a cheap auxiliary model (call_… |
| `optmem-hermes.yaml` | Independent Hermes integration of Victor Taelin's OptMem design: local, append-only memory with regex/BM25 recall and a bounded wake digest. Hybrid and guarded OptMem-only modes; verified migration and rollback. Local b… |
| `orbit-desktop.yaml` | YAML definition for `orbit-desktop` |
| `orcaslicer.yaml` | YAML definition for `orcaslicer` |
| `orquehelx.yaml` | YAML definition for `orquehelx` |
| `osv-ref.yaml` | YAML definition for `osv-ref` |
| `parallel-search.yaml` | YAML definition for `parallel-search` |
| `parcel-deliveries.yaml` | Track package deliveries with the Parcel app (parcelapp.net). List what's on the way, add tracking numbers and look up carrier codes, with a built-in guard for Parcel's strict rate limits. Disclosure — sends tracking nu… |
| `parlor.yaml` | Rooms where AI agents of any vendor talk to each other. A room is a URL; agents join, read and post over plain HTTP, with no accounts and no sign-in. Portable Agent Plugins v1 package: the parlor skill plus the hosted p… |
| `parrotnotes.yaml` | YAML definition for `parrotnotes` |
| `pass-secrets.yaml` | pass (password-store) secret source: resolves secrets from a local, GPG-encrypted, git-tracked password store into environment variables at startup, as a first-class SecretSource beside the built-in Bitwarden and 1Passw… |
| `pastdotdev.yaml` | past.dev memory provider: recall before each turn from source-traced memory of past conversations, with sessions sent to past.dev when they end. Maintained by past.dev. Disclosure — the user's message (as the recall que… |
| `pay-cli.yaml` | Discover priced APIs and pay per request (HTTP 402, x402, MPP) in stablecoins from a |
| `pay.yaml` | Discover priced APIs and pay per request (HTTP 402, x402, MPP) in stablecoins through the official hosted Pay MCP server (Streamable HTTP at https://connect.pay.sh/mcp, OAuth sign-in, no keys or local wallet), with the… |
| `pcs-security-tls-posture.yaml` | pcs-security-tls-posture — catalog entry for NousResearch/hermes-agent. Generated by Pacific-Cloud-Solutions/hermes-plugins:scripts/catalog_entry.py. |
| `pdf-surgeon.yaml` | YAML definition for `pdf-surgeon` |
| `pending-queue-monitor.yaml` | Desktop-only, read-only monitor for pending memory and skill write approvals. Disclosure — the pane's API reads pending/memory/*.json and pending/skills/*.json under the default Hermes root and every named profile direc… |
| `penny.yaml` | Penny core memory and private notes for Hermes. Disclosure — automatic recall sends the first 4,000 characters of each nontrivial local prompt to app.mypenny.ai as a search query, and the agent can save notes there thro… |
| `pep-ref.yaml` | YAML definition for `pep-ref` |
| `personae.yaml` | Personae — Hermes Desktop plugin (community catalog entry). `sha:` is the release: a commit carrying the desktop/ layout, the root |
| `phone-harness.yaml` | Drive a real phone from Hermes with one phone_exec tool: an iPhone via iPhone Mirroring on a Mac, an Android over adb, or a cloud phone from Phone Harness Cloud. Disclosure — runs model-written Python on this computer w… |
| `photofresco.yaml` | Edit images in a PhotoFresco window you approve: layers, masks, selections, adjustment layers, previews and PNG/PSD export. Portable Agent Plugins v1 package (mcp.json + skills/) with a local stdio MCP server and bundle… |
| `pidgeon.yaml` | Email for Hermes through Pidgeon: mail to your agent's own address starts a conversation, one per email thread, and the agent's answer goes back as a reply in that thread. The agent reads Pidgeon Firewall's clean text,… |
| `pinned-folders.yaml` | A Pinned tab in the Desktop sidebar that files your pinned chats into nested folders: drag to order and nest, folder colors, right-click menus (including Unpin), unread/working badges on collapsed folders, a filter box,… |
| `pixel-worlds.yaml` | Watch your agents inhabit pixel-art realms in Hermes Desktop, with imported scenes and a minimal PW Agents display. |
| `plan-mode.yaml` | Claude Code-style plan mode for Hermes: the agent explores and writes a plan, and edits nothing else until you |
| `pocket-watch.yaml` | Dashboard-only cron companion: a Pocket Watch pane showing cron jobs by schedule (daily/weekly/monthly), a health view of run outcomes and consecutive failures, a timeline, and maintenance actions — a read-oriented wind… |
| `post-cortex.yaml` | Self-hosted long-term memory through a post-cortex daemon (https://github.com/julymetodiev/post-cortex): typed records (decisions, fixed problems, code changes) in an entity graph with local semantic search. Recalls rel… |
| `ppq.yaml` | ppq-provider — catalog manifest. Pinned to the ppq-hermes-provider commit below. |
| `precleared.yaml` | Checks cold email against the law before it goes out: when the agent sends an email with a send tool, one of Hermes's email skills (himalaya, agentmail, Google Workspace) or an email API call, Precleared checks each new… |
| `preview-text-size.yaml` | Larger or smaller text in the Hermes Desktop file preview pane: scales the rendered Markdown from 90% to 175%, independent of Chat Text Size and UI Scale, through a row in Settings → Appearance, three command-palette en… |
| `pricewin.yaml` | Live hotel and flight prices from Booking.com, Agoda, Trip.com and Traveloka through the PriceWin MCP server (Streamable HTTP at mcp.price.win, no account or key), with the pricewin-travel-search skill and inline hotel/… |
| `print-job-watch.yaml` | Reads one OctoPrint printer. A cron watch reports printer_disconnected (not a pause); error; complete after Printing, Printing from SD, Pausing, Paused, Resuming, or Finishing; paused after Printing, Printing from SD, P… |
| `print3d.yaml` | Turn an idea, a photo of an object, or a shop listing into a sliced Bambu Studio project. The agent writes a Blender script, print3d checks the mesh (overhangs, thin walls, fits between parts, likeness to the photo), sl… |
| `prism.yaml` | Prism OpenAI-compatible inference with long-context DeepSeek models. |
| `privacy-gateway.yaml` | Local Presidio-based PII pseudonymization for Hermes model requests and tool results with an encrypted profile-scoped alias vault. Disclosure — PII detection runs locally with Presidio and the spaCy en_core_web_lg model… |
| `profile-models.yaml` | Read-only Desktop model map for main, auxiliary, sub-agent and MoA routes. Disclosure — reads the selected profile's full config.yaml through the host's `config.get` (the response includes any credential fields it holds… |
| `profile-pane.yaml` | Disclosure — copies .env key values (and opt-in auth.json backups) between profiles; rewrites other profiles' SOUL, memory and config.yaml. Cross-profile config pane with copy+manifest reconcile and per-group scope. |
| `profile-picker.yaml` | Pick the profile for a new chat right in the composer, next to the model pill, and see which profile a running chat belongs to. |
| `profile-switcher.yaml` | The Alt+Tab gesture for Hermes profiles. Hold Ctrl+Alt and tap Tab to cycle through your |
| `progress-squash.yaml` | YAML definition for `progress-squash` |
| `project-manager.yaml` | Git workbench for the Hermes Dashboard and Desktop: discovers the git repositories under the folders you watch, and inspects or changes them per file — stage, unstage, diff and discard — plus commit, push, pull, branche… |
| `promoat.yaml` | Make realistic AI videos of yourself, with your own face and voice, from inside Hermes. Powered by Promoat. Disclosure — sends your scripts, prompts and the public media URLs you supply to Promoat's hosted API (promoat-… |
| `prompt-enhance.yaml` | Rewrite a composer draft outside the chat and put the finished prompt back in the field. A prompt library keeps saved prompts, and a one-call model pick does not change the session. |
| `prompt-enhancer.yaml` | A composer button for Hermes Desktop that rewrites a rough draft into a structured prompt (task / scope / constraints / output shape) and restores the original on a second click. One stateless gateway call, preserves @f… |
| `prompt-optimizer.yaml` | Model-aware prompt rewriting with quality scoring, analytics, and coaching. Disclosure — the default auto mode rewrites every user message of 5+ words through your configured model (one extra LLM call per turn) before t… |
| `prompt-pocket.yaml` | Local prompt library for Hermes Desktop. Save, edit, search, and copy named prompts for manual use, with validated JSON import/export and IndexedDB storage. Does not read or modify composer drafts, send messages, or mak… |
| `prompt-queue.yaml` | Kanban-style prompt queue for the desktop: Play drains cards one at a time into per-card target modes — new session, existing session, project, or a profile's canonical Bot Chat — gated on the global model slot, backgro… |
| `prompt-snippets.yaml` | Prompt snippet library for the Hermes Desktop composer: a quick-pick overlay styled after the app's own slash menu (own shortcut), plus a management view with drag reordering, group tags and import/export. Inserts into… |
| `prompt-studio.yaml` | Step-by-step prompt builder for Hermes Desktop (F4): option cards per step with AI suggestions, then an AI-written final prompt sent to or placed in the composer through host.composer (Hermes Desktop 0.21.5+). Tuned for… |
| `prompt-tray.yaml` | Saved chat prompts — click a tray item to insert it into the Hermes composer. Review / Plan / Explain defaults, then your own. No API keys. Disclosure — inserts prompts through Hermes Desktop's internal hermes:composer-… |
| `proofable-mcp.yaml` | Context and control for any AI. Agent identity, scoped access, and proof across tools. Disclosure — skills-only package: its workflow skills steer the agent to Proofable's hosted MCP server at mcp.proofable.me (which yo… |
| `protean-model-sync.yaml` | Fleet-wide provider and model presets with CLI and Hermes Desktop support. Disclosure — writes model/provider keys into the config.yaml of the profiles you select (backup taken first). |
| `protean-ordaprompt.yaml` | Jev-style comparative classifier for OrdaPilot. It compares all topic labels and session choices in one batch, including new-topic, ambiguous, and new-session options. It uses calibrated score and margin gates, weighs c… |
| `protean-subagent-viewer.yaml` | Read-only Hermes Desktop pane for live and past delegated subagent workers. |
| `protonpass.yaml` | Proton Pass secret source: resolves pass://vault/item/field references (mapped source \"protonpass\") or every env-var-titled item of one vault (bulk source \"protonpass_vault\") into environment variables at startup th… |
| `provenance-gate.yaml` | YAML definition for `provenance-gate` |
| `provider-copy.yaml` | Copy provider API keys (and provider base-URL overrides) from one profile onto |
| `provider-status.yaml` | Status-bar quota tracking for 17 providers: Tavily, OpenCode Go, DeepSeek, GLM (z.ai), OpenRouter, Grok (xAI), Codex (OpenAI), OpenAI, Anthropic, Groq, Cerebras, Moonshot Kimi, MiniMax, Google Gemini, Hugging Face, Mist… |
| `provider-usage.yaml` | Community catalog entry: provider-usage Owner-submitted: the PR author (`PhoeniXAbhisheK`) owns and maintains the repo below. |
| `pstack.yaml` | Engineering rigor stack: poteto-mode orchestrator with 17 playbooks, plus how, architect, interrogate, swarm, unslop, and 46 other skills and principles. Disclosure — skills only, no tools or network calls of their own;… |
| `public-holidays.yaml` | Public holidays for 200+ countries and their regions, plus workday checks, workday counts and deadline math (N working days after a date), computed in code instead of by the model. Disclosure — sends HTTPS GET requests… |
| `pushary.yaml` | Phone notifications, questions and approvals through Pushary's native Hermes approval transport, with optional per-tool gates. Disclosure — approval transport and per-tool gates hand dangerous-command approvals to whoev… |
| `pushover-hermes-plugin.yaml` | Pushover as an outbound-only gateway platform, plus opt-in agent lifecycle notifications (finished, questions, errors, approvals, kanban blockers, Hermes's sudo password prompt) via Pushover and/or native notify-send, m… |
| `qdrant-memory.yaml` | Durable native memory for Hermes with LLM fact extraction. Conversations are distilled by the Hermes-configured LLM into searchable memories — facts, preferences and decisions with deduplication and importance — instead… |
| `qdrant.yaml` | Dense semantic memory for Hermes, stored in a Qdrant collection you host. Each turn becomes one point — user and assistant text verbatim, no LLM summarization step — embedded on-device at 384 dimensions with fastembed (… |
| `quota.yaml` | Per-provider quota / rate-limit status via /quota command and desktop widget. Reads precomputed quota_cache.json so the widget never does network I/O. Disclosure — refreshes your Gemini OAuth token using the Gemini CLI'… |
| `quote-ask.yaml` | Codex-style ask-about-selection for Hermes Desktop: select text anywhere in a conversation, and a small pill appears above the selection offering Quote & ask — the selection lands in the message composer as a Markdown q… |
| `quotum.yaml` | A quotum seat's Venice key as a provider. Private and anonymized models, with the seat's daily cap, spend and the 20:00 UTC bell in /usage, and a Seals tab in hermes dashboard with the seat's record. Disclosure — prompt… |
| `radio-dm-gateway.yaml` | Answers an allowlisted direct message on your Meshtastic® radio. Disclosure — talks only to the MESHTASTIC_URL you set, over plain tcp, so channel keys and text travel unencrypted. An empty MESHTASTIC_ALLOWED_NODES answ… |
| `rea-captcha.yaml` | Inspect captured browser verification evidence locally when an agent task is interrupted by a CAPTCHA. Portable Agent Plugins v1 package (pinned stateless mcp.json + skill); needs Node.js 22.19+/24.11+/26+ with npx on P… |
| `rea.yaml` | Reverse engineer programs with REA (rea.tools): native binaries, .NET assemblies, |
| `reaction-feedback.yaml` | YAML definition for `reaction-feedback` |
| `reaction-ledger.yaml` | Local ledger of the emoji reactions people leave on messages in your Telegram chats with Hermes: /reaction-log counts each message once, with the reactions it has now, and shows per emoji how many messages carry it, in… |
| `reading-buddy.yaml` | Local-first WeRead (微信读书) reading companion: syncs bookshelf, reading |
| `reasoning-switch.yaml` | Rotate the focused session reasoning effort from the status bar. A dialog sets the levels, |
| `recency-anchor.yaml` | Your system prompt is message zero and the user's question is message N. On models that weight |
| `redaction-pack.yaml` | YAML definition for `redaction-pack` |
| `redline.yaml` | Guided Markdown and source-code review in Hermes Desktop — annotate passages or line-numbered code in a docked pane and send comment/question/change-request batches back to the agent; cards are offered automatically on… |
| `refusal.yaml` | Detects when a model refuses a request or deflects to an educational alternative, and retries the turn on the next model in your fallback_providers chain; optionally appends your own text to the retry's system prompt af… |
| `reka-provider.yaml` | YAML definition for `reka-provider` |
| `remarkable.yaml` | YAML definition for `remarkable` |
| `reme.yaml` | Local-first, file-native long-term memory with HTTP and embedded ReMe backends. Disclosure |
| `remesher.yaml` | YAML definition for `remesher` |
| `removed.yaml` | Blocklist for plugins pulled from the catalog for security or policy reasons. The installer refuses to install anything whose name or repo URL |
| `render-platform.yaml` | This entry lets Hermes discover one reviewed version of the separately maintained package. |
| `rentahuman.yaml` | Find people and coordinate real-world work through the RentAHuman marketplace. Disclosure — runs the third-party `rentahuman-mcp` server via npx, which sends your requests and your RentAHuman API key to rentahuman.ai an… |
| `replaid.yaml` | Connect Replaid with OAuth to read, triage, and draft replies in your social inbox. |
| `requesty.yaml` | YAML definition for `requesty` |
| `rfc-ref.yaml` | YAML definition for `rfc-ref` |
| `rocketchat-platform.yaml` | Rocket.Chat gateway adapter for Hermes Agent. Connects to a self-hosted Rocket.Chat instance |
| `rply-platform.yaml` | rply gateway platform: talk to Hermes from the rply inbox on your phone and laptop, with web push. Messages and files both ways, seen/working/done with a live activity note, clarify questions and command approvals as ta… |
| `rss-reader.yaml` | Desktop RSS reader with reader-mode capture, drag-reorder subscriptions, mute rules, saved searches, AI summaries, keyboard shortcuts, and an optional headline ticker. Disclosure — optional YouTube cookies you paste in… |
| `rtk-rewrite-docker.yaml` | Community plugin that rewrites Hermes terminal commands through RTK (rtk-ai/rtk, Apache-2.0) so the model sees compact output. Adds a backend gate: it rewrites only for terminal backends a profile opts in to (default lo… |
| `rtk-rewrite.yaml` | YAML definition for `rtk-rewrite` |
| `ruapi.yaml` | YAML definition for `ruapi` |
| `runbox.yaml` | Build, run and test Python in an offline container per chat, with results as a plain file:line issue list. The agent syncs files or folders in as copies, then runs run (a shell command), check (ruff error rules) and tes… |
| `runcrate-provider.yaml` | Runcrate (runcrate.ai) open models via the OpenAI-compatible API at api.runcrate.ai/v1: live model list from /v1/models, DeepSeek V4.1 Flash as the default, and Hermes reasoning settings sent as reasoning_effort. Disclo… |
| `s2docs.yaml` | Source 2 documentation and mod tooling for CS2 and Deadlock from a local index of Valve's own game data: convars, Hammer entities with their inputs and outputs, schema classes and enums, game events, the cs_script and P… |
| `s3.yaml` | Generic S3-compatible backup and restore operations for Hermes |
| `sabi-metadata.yaml` | Fail-closed attribution middleware for Sabi's local adaptive routing lane (sabi-code). Adds opaque session/turn headers on loopback only; ignores all other models. Verified on Hermes 0.21.3. |
| `safeailabs-provider.yaml` | Safe AI Labs as a Hermes model provider (`--provider safeailabs`, or Safe AI Labs in `hermes model`): an OpenAI-compatible API with one endpoint per region, the model list from its /v1/models and the context window of i… |
| `salesforce-chatter.yaml` | Talk to Hermes from Salesforce Chatter: @mention the bot user in a post or comment, it Likes the message as an acknowledgement and replies in the same thread, keeping the thread as one session. Images and files on the p… |
| `scalekit.yaml` | YAML definition for `scalekit` |
| `scamgate.yaml` | Offline scam gate. Blocks known-bad links and payments before a tool runs, and asks a human when it cannot see the destination. Disclosure — blocks agent tool calls that would edit Hermes config/profiles/plugins/hooks o… |
| `search1api.yaml` | Live web search, news, Ask, page crawl, sitemap, and trending via Search1API |
| `secret-drop.yaml` | Store a secret on the gateway host without showing it to the model. Disclosure — stores the value in |
| `secret-handoff.yaml` | Ephemeral credential paste: request_secret asks through clarify and injects the reply over CDP, never storing it. Disclosure — the reply is typed into the focused field of the page whose origin matches the requested ser… |
| `secure-env-ingress.yaml` | One-use HTTPS forms for missing environment secrets, native encrypted Browser Vault logins/TOTP setup keys and payment cards, protected hosted payment-field filling, nested HTTPS verification codes/passcodes, and approv… |
| `sem-weave.yaml` | YAML definition for `sem-weave` |
| `sendblue.yaml` | Sendblue iMessage / SMS integration. Provides typing indicators, async daemon routing, and |
| `senler-io-user.yaml` | Get task-specific guidance for Senler agents, automations and knowledge, connect your account through MCP OAuth, and automate selected webhook events with an outbound Relay connection. Disclosure — Hermes installs the d… |
| `serpapi.yaml` | SerpApi web, Maps, News, Shopping, Hotels, Flights, and Travel Explore for Hermes Agent. |
| `serverless-inference-for-hermes.yaml` | CoreWeave Serverless Inference model provider. Disclosure — Hermes sends model discovery and chat requests, including prompts and tool results, to https://api.inference.wandb.ai/v1 (CoreWeave / W&B Inference) using CORE… |
| `session-dashboard.yaml` | Session Analyzer — per-session analytics for the Hermes desktop app: full page at /session-dashboard with token/cache/cost aggregates, tool-call breakdown, file changes, failure groups, and Ask AI (copies a ready-to-run… |
| `session-find.yaml` | A search window over your Hermes session history, opened with Cmd+Option+F, from the command palette, or from the glyph in the bottom bar whose hover shows the chord. Finds a session by an exact word, identifier or phra… |
| `session-flow.yaml` | Session pane for Hermes Desktop: Firefox-style session groups with project grouping, list/grid views, Ctrl+Scroll session cycling with a HUD, session-row styling and a built-in settings page. All timers are ctx-owned in… |
| `session-lens.yaml` | Read-only observability for Hermes Desktop: what each session cost and why, its full trace, recurring tool failures, every profile at a glance, provider quotas and service balances, model comparison with cheaper-route e… |
| `session-mirror.yaml` | Mirrors Hermes Desktop, CLI, TUI and ACP conversations into Discord: one public thread per session in a channel you choose, one post per turn (your message and the reply), so work started on a desktop can be followed fr… |
| `session-ref.yaml` | Reference another Hermes session in the Desktop composer with @session — |
| `session-token-counter.yaml` | Accumulated input/output token totals and context-window occupancy for the focused |
| `severian.yaml` | Local-first long-term memory for Hermes agents: a canonical append-only store (SQLite or PostgreSQL+pgvector) with five-dimensional tenant/profile/collection/agent/session scope, hybrid BM25+vector retrieval with a re-r… |
| `sgme.yaml` | SGME (拾光记忆) self-hosted long-term memory engine — tagged memories with provenance, per-turn recall, automatic session refinement, a skills library, wiki knowledge base, care signals, communication roles and a three-pool… |
| `shodan.yaml` | Shodan tools with complete capability declarations. |
| `showly.yaml` | Preview, publish, and manage websites hosted on Showly from Hermes Agent, through the hosted Showly MCP server (Streamable HTTP). Portable Agent Plugins v1 package (mcp.json + skills/). Disclosure — tool calls go to Sho… |
| `sidebar-cycle.yaml` | Step through Hermes Desktop sidebar sessions in on-screen order with Ctrl+Cmd+] / Ctrl+Cmd+[ (rebindable), wrapping at both ends. SDK-only: session-row |
| `sidebar-manager.yaml` | Hide and reorder core sidebar navigation rows from a statusbar dialog. |
| `sigrex.yaml` | Build, run and manage sigrex.io trading automation (code and AI strategies, trading |
| `singularity.yaml` | Singularity/Apptainer terminal backend: Hermes''s terminal, file and code tools run inside a |
| `sketch-pad.yaml` | Draw a shape on a Desktop pad and attach the PNG to the next Hermes |
| `skill-integrity.yaml` | Rug-pull detection for installed agent skills — fingerprints every file in every skill directory (SHA-256), keeps a profile-local snapshot, and reports exactly which skill files changed, appeared, or vanished since; a s… |
| `skill-lineage.yaml` | Records where each skill version's content came from, so a skill that rewrites itself can be audited afterwards. For every skill write — a foreground skill_manage call, a background-review edit, or a curator consolidati… |
| `skill-retrieval.yaml` | YAML definition for `skill-retrieval` |
| `skill-router.yaml` | Evidence-based, session-safe skill routing with auditable decisions and opt-in learning |
| `snag-shelf.yaml` | Everything that snagged - cross-session shelf of failed tool calls. Full Desktop page, chip, pin, fix-prompt insert. No API keys. Disclosure — stores failed tool-call metadata (tool, truncated args with key-name redacti… |
| `snyk.yaml` | Scan code (SAST), dependencies, container images, IaC and SBOMs with Snyk through its |
| `source-tray.yaml` | Session source tray — URLs the Hermes agent opened via web_search, |
| `specstream.yaml` | SpecStream gives Hermes finished lists from the live web: describe the list in plain words and get every matching row with the page it was read from, priced per match with a maximum you approve before anything runs. Por… |
| `spectator.yaml` | Harness-neutral live session sharing, summaries, and branch queries. Disclosure — reads state.db read-only and exposes masked transcripts to invite-token guests on the dashboard; host-approved guest suggestions are inje… |
| `speechify.yaml` | The official Speechify text-to-speech provider (tts.provider: speechify), maintained by Speechify. Simba 3.5 voices in 48 languages with low-latency streaming in voice mode, Opus voice notes for messaging platforms, and… |
| `spotify-desktop.yaml` | Spotify Connect remote for Hermes Desktop — status-bar mini player (now playing, |
| `spotify.yaml` | Spotify for Hermes: seven tools (playback, devices, queue, search, playlists, albums, |
| `stack.yaml` | Git-backed Markdown memory with background curation and model-based recall. Disclosure — runs a background curation agent with terminal, file-read and patch tools on your configured auxiliary model, fed raw conversation… |
| `stacktree.yaml` | Publish what Hermes builds (reports, dashboards, briefs, proposals) to a private link that opens in any browser with no account for the viewer, set a passcode or limit it to a company's email addresses, update it in pla… |
| `stalkchain.yaml` | Crypto research in plain English through the official StalkChain Data MCP server (Streamable HTTP at https://data.stalkchain.com/mcp/directory, OAuth sign-in, no keys in config): check a coin before you buy, vet a trade… |
| `sticky-notes.yaml` | In-window sticky notes for Hermes Desktop. |
| `stop-ledger.yaml` | Local ledger of the turns you stopped while Hermes was still working (/stop, or /new and /reset during a running turn, on messaging platforms, the TUI and the desktop app): /stop-log shows how many running turns were st… |
| `storm-fusion-research.yaml` | Human-gated perspective-panel research. One question, several seats, one judge, one human. Solo, native subagent panel, or per-seat MoA/Fusion fanout via the storm_run_panel tool. Disclosure — every seat/judge call runs… |
| `stream-speed.yaml` | How fast each model starts answering and how fast it writes: /speed shows the median and p90 time to first text and the median characters per second per model, provider or day, or lists the newest streams (ten, or up to… |
| `stt-vocab.yaml` | YAML definition for `stt-vocab` |
| `sugar.yaml` | Local-first persistent memory for coding agents. SQLite on your disk - |
| `sunshine-moonlight.yaml` | Set up and diagnose Moonlight game streaming (Sunshine host <-> Moonlight client) between machines that run Hermes. One tool, action-based: discover hosts on the tailnet/LAN, preflight ports, install+start Sunshine, pai… |
| `superlocalmemory.yaml` | Local-first long-term memory for Hermes, kept on your own computer: recall before each turn, tool-outcome logging, opt-in turn capture, 16 skills and /slm commands. Disclosure — talks only to the `superlocalmemory` MCP… |
| `supermemory.yaml` | Supermemory semantic long-term memory provider — profile recall, semantic search, explicit |
| `surp-hermes-x402-llm.yaml` | Marketplace-aware LLM routing for Surp — live prices for all models, provider TPS and trusted flags, mid-chat seller switching, secret masking, and approval-gated paid chat. Disclosure — the messages passed to surp_chat… |
| `switchbot-control.yaml` | SwitchBot OpenAPI v1.1, personal use. No Plug Mini on/off. Locks off unless enabled. setPosition only Curtain/Curtain3 (0=open). Disclosure — Controls real devices through the SwitchBot cloud API (api.switch-bot.com) us… |
| `t3-code-theme.yaml` | Unofficial port of the standard T3 Code dark theme for Hermes Desktop. Palette, T3 composer, sidebar thread cards with project and branch, model labels and confirm dialogs. Scoped to its own theme; other themes are unto… |
| `tabella.yaml` | YAML definition for `tabella` |
| `tailgate.yaml` | Per-job progress updates in chat for jobs Hermes hands off to other machines (coding agents, |
| `talaria-webui.yaml` | Extends Hermes Agent API capabilities to deliver a richer chat interface with Talaria WebUI. Disclosure — adds API_SERVER_KEY-authenticated /talaria/v1 routes to the Hermes API server (cross-session history search, rewi… |
| `tam.yaml` | Local-first long-term memory backed by total-agent-memory (TAM) over MCP — saves each completed turn (with a noise filter; TAM's quality gate applies), recalls relevant memories before each turn within a token budget, a… |
| `tamahermes.yaml` | YAML definition for `tamahermes` |
| `tameru.yaml` | Big tool outputs, kept small, nothing lost: old tool results shrink to the lines that matter and every distinct error, and the tameru_expand tool brings back the exact original. Deterministic and local, with no LLM call… |
| `tavily-plugin.yaml` | Search, extract, map, crawl, and research through Tavily hosted MCP, with Tavily skills. The default connection requires TAVILY_API_KEY; supports Hermes-managed OAuth through a native MCP override. Disclosure — Connects… |
| `teamorouter.yaml` | YAML definition for `teamorouter` |
| `telegram-client.yaml` | Telegram client pane for Hermes Desktop: dialogs, message history with image previews and per-post image reload, forum topics, and reviewed send/reply/save/delete/mark-as-read actions via a dedicated Telethon user sessi… |
| `telegram-notify.yaml` | YAML definition for `telegram-notify` |
| `telegram-stickers.yaml` | YAML definition for `telegram-stickers` |
| `telegram_dashboard_probe.yaml` | One pinned Telegram message with the state of your Hermes on one phone screen: gateway, backup, config drift, the cron ticker and its jobs, whether the Telegram channel is deaf, whether the agent sees its rules and whet… |
| `telesec.yaml` | Telegram Business secretary: transcribes voice notes, round videos, and speech attachments right in the chat, with Settings and per-chat controls in Telegram's Manage Bot panel, plus opt-in text history (with import fro… |
| `telnyx-provider.yaml` | Vendor-maintained Telnyx inference provider with an authenticated live model catalog, hosted open models, frontier routes, and catalog-derived pricing. |
| `terraform-drift.yaml` | Compare pinned Terraform provider and module versions with the public registry. Disclosure — tools are on for every Hermes surface, including the gateway. Stop a surface with hermes tools disable --platform <name> terra… |
| `thomas.yaml` | YAML definition for `thomas` |
| `tidal.yaml` | TIDAL for Hermes Agent: five tools (playback through local mpv, search, playlists, library, mixes) over the unofficial TIDAL API via tidalapi. Login is TIDAL's own PKCE login flow (hermes tidal login) — no developer app… |
| `time-gap.yaml` | Inject an implicit time-gap sense only when a gap or a date rollover crosses. |
| `timestamp-ref.yaml` | @ts: context references that turn timestamps into readable times for the model: @ts:1729468800123 attaches the moment in UTC, in the local time zone and as ISO 8601, with its weekday, how long ago or ahead it is, the sa… |
| `tinyfish.yaml` | TinyFish: the web, built into Hermes. Free Search and Fetch power Hermes's own web_search and web_extract, and when a site needs clicks, forms or a login, a remote browser and the tinyfish_agent web agent handle it. Dis… |
| `titanos-mcp.yaml` | Connect Hermes to Titanos marketplace, Amazon, listings, Ads, and product research tools through the pinned Titanos OAuth MCP client. This portable Agent Plugin v1 package bundles seven operating skills, requires Node.j… |
| `together.yaml` | Together AI model-provider plugin — OpenAI-compatible API, 270+ serverless open-weight models, live catalog discovery. |
| `token-cost-meter.yaml` | Live token usage, model-aware USD cost and prompt-cache savings in the Hermes Desktop status bar, with a persistent per-day ledger that survives restarts. Disclosure — Desktop only; no network calls of its own (prices c… |
| `token-lens.yaml` | Token consumption analytics for Hermes: records exact per-call usage from pre/post_api_request hooks, decomposes every request into categories (system prompt, built-in and per-MCP-server tool schemas, skills, memory, hi… |
| `tokenwatch.yaml` | Monitor Hermes token usage, notify at thresholds, and freeze tool/gateway activity at configured |
| `tokstat.yaml` | Live token usage in the Hermes Desktop status bar: cumulative total, a real-time this-turn counter, last-turn delta, context occupancy, and prompt-cache hit rate. Event-driven (no polling, no RPC); English and Chinese,… |
| `tool-slimmer.yaml` | Reduce Hermes tool-schema overhead and show selector savings in the dashboard. Disclosure — optional mode jev (off by default; needs TYPESAFE_API_KEY) sends each turn's request text and up to 32 candidate tool names and… |
| `toolaria.yaml` | Rescues oversized MCP and web tool results before they flood context. |
| `touchdesigner.yaml` | Drive a live TouchDesigner session through the twozero MCP server (Streamable HTTP on |
| `tracekit.yaml` | Tracekit's signer decides every tool call before it runs (deny blocks, ask waits for a person) and signs each call and its outcome into a run you can verify offline. Disclosure — every tool call's name and arguments, pl… |
| `traceverse_hermes_otel.yaml` | Hermes Agent OpenTelemetry traces and dashboard logs, with local-model cost estimates and optional in-process evaluation, GPU, energy, and CO2 metrics via genai-otel-instrument. Disclosure — Sends OpenTelemetry traces a… |
| `true402-swap-guard.yaml` | Blocks token buys when true402 finds a honeypot or a rug in progress — one pre_tool_call hook in front of every trading tool, MCP server and terminal command (Base, Ethereum, BSC, Solana). Free edition: it never pays, h… |
| `tsubasa.yaml` | Tsubasa OpenAI-compatible model provider (tool calling not supported yet). Disclosure — sends prompts and your TSUBASA_API_KEY to api.tsubasa.sh, operated by PalmAndWand; the API currently serves Canada only and answers… |
| `ttsbuddy.yaml` | YAML definition for `ttsbuddy` |
| `turn-bell.yaml` | A bell in the Hermes desktop composer that pings the ntfy topic Hermes already uses when a turn finishes. Click to cycle off, current turn, or all turns. Disclosure — when enabled, posts the first line of each finished… |
| `turn-usage.yaml` | Usage and cost footer appended to every reply — tokens, cache hit rate, cost and context occupancy, plus a per-tool time breakdown showing which tool actually consumed the wall clock. Waiting time (a blocking user promp… |
| `twenty-crm.yaml` | Twenty CRM for Hermes Agent with managed self-hosting, external-instance connectivity, REST, |
| `typesafe-skill-router.yaml` | YAML definition for `typesafe-skill-router` |
| `umt.yaml` | Connect 28 production-ready MCP servers to any coding agent. Portable Agent |
| `unbrowse.yaml` | Unbrowse: websites as APIs. Read any page as clean markdown, run tasks on sites through learned first-party APIs (no browser), and drive a cloud browser with saved logins when nothing matches. Also a web_extract backend… |
| `unibaseio-membase.yaml` | Long-term memory for you and your AI from Membase (membase.com, by Unibase): one memory every connected AI shares. Searches the user's Membase memory before each turn (8 s, fail-open) and adds membase_search, membase_sa… |
| `unicode-ref.yaml` | @unicode: context references that spell text out character by character for the model: @unicode:\"text\" attaches a table of every character of the quoted text (code point, Unicode name, category) with notes on what doe… |
| `unitares.yaml` | YAML definition for `unitares` |
| `unraid.yaml` | Read-only Unraid monitoring for Hermes Desktop: server metadata, array capacity, Docker containers, virtual machines, and grouped alerts. Disclosure — sends fixed GraphQL queries to the user-configured Unraid host and s… |
| `usage-flame.yaml` | Community catalog entry — usage-flame |
| `usage-guard.yaml` | Catalog entry for NousResearch/hermes-agent: plugin-catalog/usage-guard.yaml Pinned to tag v0.4.1 (release published 2026-10-24). Bump sha and version together. |
| `usage-ledger.yaml` | Local-only content-free usage tally and native Desktop statusline (Windows and macOS beta). |
| `usage-stats.yaml` | Multi-provider usage/balance for the Hermes Desktop status bar — shows live usage for OpenCode, OpenRouter, DeepSeek, Kimi, NovitaAI, ZAI, Alibaba, Arcee, plus gateway-native Claude/Codex/Cursor/Nous. |
| `ux3-product-design-harness.yaml` | YAML definition for `ux3-product-design-harness` |
| `vault-view.yaml` | Local Markdown vault workspace for Hermes Desktop: visual editing, progressive reading, cached image previews, optional per-conversation workspaces, pinned tabs, explicit selection quoting, tag search, links, backlinks… |
| `vaultknox.yaml` | Secret-leak protection for Hermes chats. Scans inbound messages and outbound replies for API keys, tokens, and passwords with a 28-pattern detector registry, redacts them before they reach session storage or the user, a… |
| `vaultwarden.yaml` | Vaultwarden / Bitwarden Password Manager (bw CLI) secret source |
| `vector-platform.yaml` | Vector (vectorapp.io) messaging platform plugin: Hermes becomes a first-class Nostr-based Vector bot (its own nsec/npub identity), relaying DMs through a local Rust sidecar that wraps vector-sdk. First run needs `hermes… |
| `vet402.yaml` | Look a paid x402 or MPP URL up in vet402's public record of real purchases before the agent pays it. BLOCK stops the tool call. ALLOW, and a WARN that only says vet402 has not bought there yet, let it run. Any other WAR… |
| `viajante.yaml` | Flight and hotel search from your own machine through a local MCP server and one skill that tells the agent how to read the results. Portable Agent Plugins v1 package (mcp.json + skills/). No API keys and no account. Di… |
| `vidiq.yaml` | Grow on YouTube, Instagram, and TikTok with vidIQ. Disclosure — skills only; you add vidIQ's hosted MCP server yourself with hermes mcp add vidiq --url https://mcp.vidiq.com/mcp --auth oauth; tool calls send your prompt… |
| `vk-platform.yaml` | VK Messenger gateway with community Long Poll, media attachments, allowlists, and project-lane routing. |
| `voice-ledger.yaml` | Local ledger of the voice messages and recordings Hermes transcribes (voice messages from messaging platforms, CLI voice mode): /voice-log shows how many recordings there were, how much audio in total and typically, and… |
| `voicestudio.yaml` | Client for the local VoiceStudio text-to-speech app (debpalash/VoiceStudio): speak short text, design or clone voices, browse voices, render chaptered long-form audio, dub videos, and check server status. Six tools with… |
| `vornik-companion.yaml` | Vornik as Hermes's hardened broker and long-term memory: Hermes holds no credentials; privileged work runs in operator-approved workflows on your own Vornik daemon. Disclosure — talks only to the self-hosted Vornik daem… |
| `wait-ledger.yaml` | Local ledger of the times Hermes stopped to wait for you (approval prompts, clarify questions, password prompts): /waits shows how many waits there were, how many were answered or left unanswered, and how long Hermes st… |
| `walkie-talkie.yaml` | Let one session message another existing session (Telegram topic, group thread or DM), waking it like a user turn so the reply lands in that chat Disclosure — starts agent turns in other existing gateway sessions (any r… |
| `wallaby-provider.yaml` | Wallaby Token — curated open-weight inference (Kimi K3); adds Wallaby to the hermes model provider list. |
| `wallpaper-theme.yaml` | YAML definition for `wallpaper-theme` |
| `watchline.yaml` | Watchline delivery adapter for Hermes Agent. Polls a Watchline pull channel and forwards |
| `waypoint.yaml` | Session status for Hermes Desktop: a thin bar next to every sidebar session with four states — Working (remembers your next step), Waiting on someone (who/what plus a follow-up reminder), Done (outcome plus a fresh-star… |
| `weather.yaml` | Weather data, radar/model imagery, and verified meteorological calculations. Built on metrust, |
| `web-crawler-spider.yaml` | A small spider that lives on the Hermes Desktop window: a web that grows with tool calls, helper spiders for subagents, an amber mood while Hermes waits for approval, spider-sense for risky commands, flies, napping. By… |
| `web-deepseek.yaml` | DeepSeek Search + Fetch — routes web_search and web_extract through |
| `web-defuddle.yaml` | Defuddle content extraction — local, free, no API key. Shells out to the defuddle CLI for |
| `web-local.yaml` | Keyless local web extract: fetches pages from this machine with httpx and reduces them to readable text with trafilatura. No API key, no third-party service. Extract-only; pair with any search provider. |
| `web-meta-ai.yaml` | Meta web search — routes web_search through the server-side web_search tool on Meta's Responses API (Muse Spark); search-only. Disclosure — each search is a separate billed Meta Model API call (per-query web search fee… |
| `web-octen.yaml` | Octen web search with query-focused highlights and page extraction. |
| `web-ollama-cloud.yaml` | Ollama Cloud web search + content extraction via Ollama's native REST API. Search returns |
| `web-oxylabs.yaml` | Oxylabs AI Studio web search and extraction provider for Hermes Agent. Requires OXYLABS_API_KEY |
| `web-search-plus.yaml` | Multi-provider web search, URL extraction, quality reports, and opt-in research mode. Disclosure — reads the operator's HERMES_HOME/config.yaml (read-only) for its own Desktop settings block (country, language, max_resu… |
| `web-serply.yaml` | Serply web search provider for Hermes Agent. Google web results via the Serply |
| `web-toon.yaml` | Paid web extract over TOON: web_extract pays a TOON node about $0.001 per page from a local payer sidecar; the node fetches through an Anyone network exit and returns markdown with a wuzzy/crawl v1 content hash. Disclos… |
| `web-venice.yaml` | Venice AI web search + extract — privacy-first, zero data retention, $0.01/request. |
| `webly.yaml` | Publish a website, or share files and folders, at a live *.webly.site URL from Hermes Agent with no account, then sign in to claim it, edit it, and publish drafts the person approves through the hosted Webly MCP server… |
| `wechat-social-assistant.yaml` | Local-first WeChat relationship memory assistant for macOS: captures only what |
| `whatsapp-agent-platform.yaml` | YAML definition for `whatsapp-agent-platform` |
| `wicked-memory.yaml` | Persistent, wallet-scoped long-term memory for Hermes: remember, semantic recall, versioned update, history and approved hard delete, backed by the hosted Wicked Memory service, plus skills for using it and for connecti… |
| `wiki-ref.yaml` | YAML definition for `wiki-ref` |
| `wireguard.yaml` | Read-only status and peer list for a WireGuard server running on the same Windows machine as Hermes. Two tools: vpn_status (service state, tunnel address and port, server public key, per-peer handshake and transfer) and… |
| `wolfmarkdown.yaml` | Create, clean, and verify standalone Markdown with conservative semantic repair and deterministic artifact checks. Disclosure — skill-only plugin that has the agent run its bundled Node.js 22+ scripts through the termin… |
| `woof.yaml` | Plan, launch, watch and compare WOOF weather simulations on your own NVIDIA GPU: size runs with WOOF's own planner, launch them locally or on an ssh/WSL GPU host, get maps in the chat while the forecast runs, compare ph… |
| `workflow-record.yaml` | hermes record: demonstrate a browser workflow once (clicks, field values, navigations) and its bundled skill lets /learn turn the recording into a skill that replays it with the browser tools. A Hermes Labs plugin: buil… |
| `world-clock.yaml` | One time zone in your Hermes Desktop status bar, every other zone you work with a click away. Click the time for a drop-up of your enabled zones; Edit zones lists standard IANA zones with live UTC offsets. Desktop-only… |
| `wyoming-voice-bridge.yaml` | Wyoming speech-to-text and text-to-speech for a Wyoming server you run (stt/tts provider `wyoming`), plus a wyoming_voice_status tool that lists the server's models and voices. Disclosure — Audio and text to speak go to… |
| `xchat.yaml` | X Chat gateway platform: talk to Hermes in X''s end-to-end encrypted DMs. Hermes runs as the X |
| `xmemo.yaml` | YAML definition for `xmemo` |
| `yandex-disk.yaml` | Browse, search, read, write, upload, download, copy, move, share, delete and restore files on Yandex Disk over its REST API. Disclosure — sends every request to cloud-api.yandex.net, or to the https URL in YANDEX_DISK_B… |
| `yandex.yaml` | Yandex Search API as a backend for the built-in web_search (provider name yandex), plus a yandex_generative_search tool for grounded answers with cited sources. Disclosure — sends web_search queries and yandex_generativ… |
| `yandex_calendar.yaml` | List, create, update, RSVP to, move and delete Yandex Calendar events over CalDAV, with attendees, busy status and several calendars. Disclosure — sends every request to caldav.yandex.ru, or to the HTTPS URL in YANDEX_C… |
| `yantrikdb-hermes-dashboard.yaml` | Local-only YantrikDB dashboard for Hermes Agent memory operations |
| `yantrikdb.yaml` | Persistent memory for Hermes. Canonicalizes duplicate memories, surfaces contradictions between structured or recognized single-valued claims for review, and returns a why_retrieved reason list with every recall. Embedd… |
| `yolo-auto.yaml` | Yolo-Auto: flat-rate OpenAI-compatible API with plan-filtered live model discovery. |
| `you.yaml` | You.com skills for live web search, URL content extraction, cited research, finance |
| `youtube-dock.yaml` | YAML definition for `youtube-dock` |
| `zalo-platform.yaml` | Zalo Bot Platform gateway adapter for Hermes Agent — relays messages between Zalo DMs/groups and the agent over the official Bot API (bot-api.zaloplatforms.com), long-polling or webhook mode. Adds slash commands and mod… |
| `zerosignal.yaml` | ZeroSignal — private, pay-per-request inference through the local zs-proxy; no API key, your wallet is the credential. |
