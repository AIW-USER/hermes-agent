# 2. Installing and setting up Hermes

## Step 1 — Install

| Platform | Command / method |
|---|---|
| **Linux, macOS, WSL2** | `curl -fsSL https://hermes-agent.nousresearch.com/install.sh \| bash` |
| **Windows (native, PowerShell)** | `iex (irm https://hermes-agent.nousresearch.com/install.ps1)` |
| **macOS / Windows with the desktop app** | Download the Hermes Desktop installer from <https://hermes-agent.nousresearch.com/> — it installs both the CLI and the app |
| **Android (Termux, aarch64)** | Use the signed APT repository (`stable` or `canary` channel) — see the Termux guide in `website/docs/getting-started/termux.md` |
| **Docker** | `docker run -it --rm -v ~/.hermes:/opt/data nousresearch/hermes-agent setup` (then run the gateway container; see `website/docs/user-guide/docker.md`) |
| **Nix** | `flake.nix` in this repo; guide in `website/docs/getting-started/nix-setup.md` |
| **From source (developers)** | Clone this repo, `source ./activate` — see `CONTRIBUTING.md` |

The installer sets up Python 3.14, Node.js, npm, ripgrep, FFmpeg and Hermes' Python
dependencies through Hermes' own package manager (PM). Afterwards reload your shell:

```bash
source ~/.bashrc     # or: source ~/.zshrc
```

Where things are installed:

- Linux / macOS / WSL2: `~/.hermes` (data, config, skills, sessions)
- Native Windows: `%LOCALAPPDATA%\hermes`

> **Windows antivirus note:** some antivirus tools flag the bundled `uv.exe` (Astral's Python
> package manager) as malware. It is a false positive; the main `README.md` shows how to verify
> the binary with `gh attestation verify` and how to whitelist the *folder*.

## Step 2 — Choose a model provider

This is the most important setup step.

```bash
hermes setup            # full guided wizard (provider, tools, options)
hermes model            # just pick provider + model
hermes setup --portal   # fastest: sign in to Nous Portal (300+ models + Tool Gateway, one subscription)
```

On a fresh install `hermes setup` offers three modes:

- **Quick Setup (Nous Portal)** — OAuth login, no API keys; also enables the Tool Gateway
  (web search, image generation, text-to-speech, cloud browser) billed to your subscription.
- **Full Setup** — walk through every provider, tool and option with your own keys.
- **Blank Slate** — only provider/model, file tools and terminal; everything else off until you
  turn it on with `hermes tools`.

Supported providers include Nous Portal, OpenRouter, OpenAI / ChatGPT-Codex subscription,
Anthropic (API key or OAuth), Google AI Studio / Vertex, AWS Bedrock, Azure Foundry, xAI,
DeepSeek, Hugging Face, Kimi/Moonshot, Z.AI/GLM, MiniMax, Qwen, Alibaba DashScope, NVIDIA NIM,
Fireworks, Nebius, Ollama (local and cloud), LM Studio, Vercel AI Gateway, and any
OpenAI-compatible endpoint (vLLM, SGLang, …).

> **Minimum context window: 64,000 tokens.** Smaller models are rejected at startup because they
> cannot hold a multi-step tool-calling workflow.

You can switch provider any time with `hermes model` or `/model provider:model` inside a chat.

### Where settings go

- **Secrets** (API keys, bot tokens) → `~/.hermes/.env`
- **Everything else** → `~/.hermes/config.yaml`

`hermes config set` puts each value in the right file automatically:

```bash
hermes config set model anthropic/claude-opus-4.6
hermes config set terminal.backend docker
hermes config set OPENROUTER_API_KEY sk-or-...
hermes config get terminal.backend
```

## Step 3 — First chat

```bash
hermes          # classic terminal REPL
hermes --tui    # modern terminal UI (modal overlays, mouse selection, non-blocking input)
hermes desktop  # native desktop app
```

Start with something easy to verify, e.g. *"Summarize this repo in 5 bullets and tell me what
the main entrypoint is."* **Rule of thumb:** get one clean conversation working before adding
the gateway, cron, voice or fallback routing.

## Step 4 (optional) — Messaging bots

```bash
hermes gateway setup     # interactive: Telegram, Discord, Slack, WhatsApp, Signal, Email, …
hermes gateway           # run in the foreground, or:
hermes gateway install   # install as a user service (systemd on Linux, launchd on macOS)
hermes gateway start | stop | status
```

On WSL use `hermes gateway run` (optionally inside `tmux`) because WSL's systemd support is
unreliable. Always configure who may talk to the bot — see the safety guide.

## Step 5 (optional) — Import from another agent

Coming from OpenClaw, Claude Code, Codex CLI or Cursor? `hermes setup` offers to import, or:

```bash
hermes plugins install agent-importers
hermes import-agent openclaw --dry-run     # preview
hermes import-agent openclaw               # import persona, memories, skills, allowlists, settings
hermes import-agent claude-code            # or: codex / cursor
```

API keys are only imported when you add `--migrate-secrets`.

## Keeping Hermes healthy

| Task | Command |
|---|---|
| Update to the latest release | `hermes update` (`--check` to preview, `--backup` to back up first) |
| Diagnose problems | `hermes doctor` |
| Show status of agent, auth and platforms | `hermes status` |
| View / follow logs | `hermes logs`, `hermes logs -f` |
| Summary to paste into a support request | `hermes dump` |
| Back up / restore everything | `hermes backup` / `hermes import <zip>` |
| Troubleshoot with all customizations off | `hermes chat --safe-mode` |
| Remove Hermes | `hermes uninstall` |
