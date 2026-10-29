# 4. Features and functions

This page covers everything Hermes can do and how to switch each capability on, off, or tune it.

## 4.1 Tools and toolsets

A **tool** is a function the model can call. Tools are grouped into **toolsets**; enable or
disable them per platform with `hermes tools`, per run with `hermes chat -t web,file,terminal`,
or per session with `/tools enable|disable <name>`. Some tools appear only when their
service is configured (e.g. Discord tools need `DISCORD_BOT_TOKEN`).

| Toolset | Tools (main ones) | What it lets the agent do |
|---|---|---|
| `terminal` | `terminal`, `process_manage` | Run shell commands (foreground or background), manage long-running processes |
| `file` | `read_file`, `write_file`, `patch`, `search_files` | Read, create and edit files (fuzzy find-and-replace), ripgrep-backed search |
| `web` | `web_search`, `web_extract` | Search the web; extract clean text from pages and PDFs |
| `browser` | `browser_exec`, `browser_cdp`, `browser_dialog`, `browser_vault` | Drive a real Chromium browser; fill saved logins without exposing secrets |
| `code_execution` | `execute_code` | Run a Python script that calls Hermes tools programmatically (many steps, one turn) |
| `delegation` | `delegate_task` | Spawn subagents with their own context, alone or in parallel batches |
| `memory` | `memory` | Save facts about you and the environment across sessions |
| `session_search` | `session_search` | Full-text search over past conversations |
| `skills` | `skills_list`, `skill_view`, `skill_manage` | Find, load, create and update skills |
| `todo` | `todo_list` | Keep a task list for multi-step work |
| `clarify` | `clarify` | Ask you 1–5 questions (multiple choice supported) before proceeding |
| `cronjob` | `cronjob_manage` | Create, list, pause, run and remove scheduled jobs |
| `kanban` | `kanban_*` | Work on a multi-agent task board (show, complete, block, comment, attach, …) |
| `vision` | `vision_analyze` | Look at images |
| `video` / `video_gen` | `video_analyze`, `video_generate` | Analyze and generate videos |
| `image_gen` | `image_generate` | Generate or edit images (FAL, OpenAI, xAI, Krea, OpenRouter, …) |
| `tts` | `text_to_speech` | Speak replies (voice bubbles on Telegram, audio on Discord/WhatsApp) |
| `x_search` | `x_search` | Read-only search of public X/Twitter posts (via xAI) |
| `computer_use` | `computer_use` | Background desktop control: screenshots, click, type (cua-driver) |
| `desktop_ui` | `desktop_preview`, `drive_preview`, `gui_tour`, `set_theme`, … | Control the Hermes desktop app's panes, preview browser and tours |
| `connections` / `catalog` / `project` | `manage_connections`, `manage_catalog`, `desktop_project` | Desktop: hosted connectors, catalog search, named workspaces |
| `discord`, `discord_admin`, `feishu_*`, `hermes-yuanbao` | platform tools | Act inside a specific messaging platform |

Full list with every parameter: `website/docs/reference/tools-reference.md` and
`toolsets-reference.md`. The code is in `tools/` (one module per tool, registered in
`tools/registry.py`) and the toolset map is `toolsets.py`.

## 4.2 Where commands run — terminal backends

Set with `terminal.backend` in `config.yaml`:

| Backend | Runs commands… | Notes |
|---|---|---|
| `local` (default) | Directly on your machine as your user | Fastest; **no isolation** |
| `docker` | In a long-lived container (or one per session with `container_persistent: false`) | Recommended when the agent reads untrusted content |
| `ssh` | On a remote host | Keep the agent off your laptop |
| `modal`, `daytona` | In a serverless cloud sandbox | Hibernates when idle, near-zero cost between sessions |
| `vercel_sandbox` | In a Vercel Sandbox | |
| plugin backends | e.g. Singularity/Apptainer | |

File tools go through the same backend, so they can only reach what the backend exposes.

## 4.3 Skills — procedural memory

A skill is a folder with a `SKILL.md` (YAML frontmatter + instructions) and optional scripts,
templates and references. Only the name and description sit in the prompt; the full content
loads when needed ("progressive disclosure").

- **Use one:** type `/<skill-name>`, or just ask — the agent finds relevant skills itself.
  `hermes chat -s name` preloads one.
- **Install:** `/skills` or `hermes skills` browse online registries (agentskills.io standard,
  Skills Hub). Built-in skills live in `skills/`; extra shipped-but-inactive ones in
  `optional-skills/`.
- **Create:** the agent writes skills after complex tasks (`skill_manage`); `/learn <source>`
  distills a skill from a URL, directory or the workflow you just did.
- **Bundle:** `hermes bundles` groups several skills under one `/name`.
- **Maintain:** the **Curator** (`hermes curator`, `/curator`) tidies, merges, pins and
  archives agent-created skills in the background, with backups and rollback.
- New/removed skills: `/reload-skills`. Your skills live in `~/.hermes/skills/`.

Built-in skill categories include apple, autonomous-ai-agents (Claude Code, Codex, OpenCode),
creative (diagrams, Manim, p5.js, music), email, media, note-taking (Obsidian), productivity
(Google Workspace, Notion, Airtable, docx/pdf/pptx/xlsx), research (arXiv, citations),
social media and software development. See `website/docs/reference/skills-catalog.md`.

## 4.4 Memory and learning

- **Built-in memory:** two small files, `MEMORY.md` (agent notes, ~2,200 chars) and `USER.md`
  (your profile, ~1,375 chars), injected at session start. The agent writes them with the
  `memory` tool. Gate writes with `memory.write_approval` and review with `/memory pending`.
- **Session search:** every conversation is indexed (SQLite FTS5); the agent can recall it.
- **Learning journey:** `hermes journey` / `/journey` shows a timeline of skills and memories
  learned; you can edit or delete entries.
- **Background review:** after turns, an auxiliary model reviews what's worth saving
  (`/refine` runs it now).
- **External memory providers** (`hermes memory setup`, `memory.provider`): Honcho, OpenViking,
  Mem0, Hindsight, Holographic, Supermemory (installed from the plugin catalog), RetainDB,
  ByteRover, Memori. Each profile keeps its own provider data.

## 4.5 Scheduled automation — cron

- Create jobs in natural language ("every weekday at 8am send me a news brief on Telegram"),
  with `/cron`, or `hermes cron`. Jobs can use skills, run inside a project directory, have a
  time zone, and deliver to any platform.
- **Jobs only fire while the gateway is running.**
- `/blueprint` sets up automations from templates; `/suggestions` reviews automations Hermes proposes.
- `hermes pause` / `hermes resume` is a global emergency stop.
- Related: `/loop` (repeat a prompt on an interval), `/heartbeat` (recurring prompt in this
  session), `/goal` (keep working toward an objective, judged after every turn).
- Code: `cron/` (`jobs.py`, `scheduler.py`).

## 4.6 Subagents, parallel work and kanban

- `delegate_task` spawns isolated subagents — one task or a parallel batch — each with its own
  context, terminal session and tools; only the summary returns. You can give subagents a
  cheaper model (`delegation` settings / Desktop → Settings → Model → Subagents).
- `/review` spawns an independent reviewer subagent. `/moa` runs a prompt through a
  Mixture-of-Agents preset.
- **Kanban** (`hermes kanban`, `/kanban`): a durable multi-profile task board with a dispatcher,
  dependencies, reviews and attachments, for long-running multi-agent projects.
- `--worktree` / `/worktree` gives each agent its own git worktree for parallel coding.

## 4.7 Messaging gateway

One gateway process serves many platforms: Telegram, Discord, Slack, WhatsApp (bridge or Cloud
API), Signal, Email, SMS, Matrix, Mattermost, Microsoft Teams (+ meeting pipeline), Google Chat,
Feishu/Lark, DingTalk, WeCom, Weixin, QQ, LINE, IRC, ntfy, BlueBubbles/iMessage (Photon),
SimpleX, Home Assistant, Open WebUI, webhooks, A2A and more. Features: voice-memo
transcription, cross-platform continuity (`/handoff`), per-channel model and prompt overrides,
DM pairing, admin vs regular-user tiers, approval buttons. Adapters: `plugins/platforms/` and
`gateway/platforms/`.

`hermes send` posts a one-off message from scripts; `hermes webhook` sets up event-driven
activation; `hermes peer` connects gateways on different machines.

## 4.8 MCP — Model Context Protocol

Connect any MCP server to add tools:

```yaml
mcp_servers:
  filesystem:
    command: "npx"
    args: ["-y", "@modelcontextprotocol/server-filesystem", "/home/user/projects"]
  asana:
    url: https://mcp.asana.com/v2/mcp
    auth: oauth
```

Manage with `hermes mcp` (catalog one-click installs, OAuth login, tool selection) and reload
with `/reload-mcp`. Servers can be marked `trust: untrusted` (writes ask first) and given a
`spend_limit`. Hermes can also *be* an MCP server (mcp-serve plugin). Pre-packaged servers:
`optional-mcps/`.

## 4.9 Plugins

Plugins add model providers, memory providers, messaging platforms, terminal backends, web
search / image / video / browser providers, context engines, dashboards, hooks and more —
without touching the core. Manage with `hermes plugins` (install, enable, disable, remove);
the curated catalog is `plugin-catalog/`. Built-in plugins live in `plugins/`.

## 4.10 Models and providers

- `hermes model` / `/model provider:model` — switch any time.
- **Fallback providers** — tried automatically when the primary errors (`hermes fallback`).
- **Credential pools** — rotate several keys for one provider.
- **Mixture of Agents** — `hermes moa` presets; `/moa` per prompt.
- **Reasoning effort / fast mode** — `/reasoning`, `/fast`.
- **Local models** — Ollama, LM Studio, vLLM, SGLang via a custom endpoint.
- **Subscription proxy** — `hermes proxy` exposes OAuth subscriptions as a local OpenAI-compatible API.
- Provider code: `agent/` (transports), `plugins/model-providers/`, `providers/`.

## 4.11 Other features

| Feature | How |
|---|---|
| Checkpoints & rollback | `--checkpoints`; `/rollback` lists and restores file snapshots taken before destructive edits |
| Voice | `/voice` in the CLI (record with Ctrl+B), wake word `/wake`, TTS replies |
| Vision & documents | Paste images (`/paste`), `--image`, document extraction |
| Context references | Mention files/URLs in prompts to attach them |
| LSP | `hermes lsp` — semantic diagnostics after `write_file`/`patch` |
| Hooks | `hermes hooks` — shell scripts run on events (approved before use) |
| Context compression | Automatic near the limit; `/compress`, `compression.*` settings |
| Insights & usage | `/usage`, `/insights`, `hermes insights` |
| Skins, personalities, pets | `/skin`, `/personality`, `/pet` |
| Batch / research | `batch_runner.py` (run prompts in parallel over a JSONL dataset), `trajectory_compressor.py` (training data) |
| Web dashboard | `hermes dashboard` |
| Backups & portability | `hermes backup`, `hermes import`, `/export` (profile to `.tar.gz`) |
