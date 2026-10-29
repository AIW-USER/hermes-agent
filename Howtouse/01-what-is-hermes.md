# 1. What is Hermes Agent?

Hermes Agent is an open-source (MIT) **personal AI agent** built by Nous Research. Unlike a plain
chatbot, it can *act*: it runs shell commands, reads and edits files, browses the web, schedules
jobs, sends messages, and spawns helper agents — and it **learns across sessions** by keeping
memories and writing reusable "skills".

You can run it on a laptop, a $5 VPS, a GPU cluster, or a serverless sandbox, and talk to it from
the terminal, a desktop app, or ~20 messaging platforms (Telegram, Discord, Slack, WhatsApp,
Signal, Email, Matrix, Teams, …). It works with almost any model provider (Nous Portal,
OpenRouter, OpenAI, Anthropic, Google, local models via Ollama/LM Studio/vLLM, and many more).

## The core ideas

| Idea | What it means for you |
|---|---|
| **One agent core, many front-ends** | The same agent runs behind the CLI, the TUI, the Electron desktop app and the messaging gateway. Sessions, slash commands and settings are shared. |
| **A closed learning loop** | The agent saves facts to memory (`MEMORY.md`, `USER.md`), creates *skills* after complex tasks, improves them while using them, and can search all its past conversations. |
| **Tools** | Functions the model can call: `terminal`, `read_file`, `write_file`, `patch`, `web_search`, `browser_exec`, `delegate_task`, `memory`, `cronjob_manage`, and many more. Grouped into *toolsets* you can switch on or off. |
| **Skills** | Markdown instruction packs (`SKILL.md`) that teach the agent a procedure — e.g. "review a GitHub PR", "make a slide deck". Loaded only when needed. |
| **Profiles** | Fully isolated Hermes instances (own config, memory, skills, bots) on one machine — e.g. `work` and `personal`. |
| **Terminal backends** | Where commands actually run: your machine (`local`), Docker, SSH, Modal, Daytona, Vercel Sandbox, or plugin backends. |
| **Gateway** | A long-running process that connects Hermes to messaging platforms and runs scheduled (cron) jobs. |
| **Plugins & MCP** | Ways to extend Hermes without changing its core: Python plugins, and any Model Context Protocol (MCP) server. |

## Design principles (why it behaves the way it does)

Two rules from the project's own development guide shape most behaviour:

1. **Prompt caching is sacred.** Hermes avoids changing the system prompt mid-conversation
   because it would make every following request more expensive. That is why memory edits,
   `SOUL.md` edits and newly installed skills usually take effect in the **next** session
   (some commands offer `--now` to apply immediately). Context compression is the one exception.
2. **Narrow core, capability at the edges.** New features arrive as CLI commands + skills,
   plugins, or MCP servers rather than as new built-in tools, because every built-in tool is
   sent to the model on every call.

## The files that shape the agent

| File | Holds | Written by | Location |
|---|---|---|---|
| `SOUL.md` | The agent's personality and tone (slot #1 of the system prompt) | You | `~/.hermes/SOUL.md` |
| `USER.md` | What the agent knows about *you* | The agent (memory tool) | `~/.hermes/memories/` |
| `MEMORY.md` | What the agent has learned (environment facts, conventions) | The agent | `~/.hermes/memories/` |
| `AGENTS.md` / `.hermes.md` | Project-specific rules | You / the project | Your project folder |
| `config.yaml` | All non-secret settings | You (`hermes config set …`) | `~/.hermes/config.yaml` |
| `.env` | Secrets only (API keys, bot tokens) | You | `~/.hermes/.env` |

Only one project context file is loaded per session, first match wins:
`.hermes.md` → `AGENTS.md` → `CLAUDE.md` → `.cursorrules`.

Memory is a **frozen snapshot** taken at session start: if the agent saves something mid-session,
it is stored immediately but appears in the system prompt from the next session.

## Glossary

- **Session** — one conversation, stored in a local SQLite database (`state.db`) with full-text search.
- **Turn** — one user message and everything the agent does in response.
- **Toolset** — a named group of tools (`web`, `file`, `terminal`, `browser`, `memory`, …).
- **Subagent** — a helper agent spawned with `delegate_task`, with its own context; only its summary comes back.
- **Cron job** — a scheduled prompt that runs unattended and delivers results to a platform.
- **Curator** — background maintenance that tidies, merges and archives skills.
- **Compression** — summarising older turns when the context window fills up.
- **YOLO mode** — approvals switched off for a session (dangerous; see the safety guide).
- **`HERMES_HOME`** — the data directory (`~/.hermes` by default; one per profile).
