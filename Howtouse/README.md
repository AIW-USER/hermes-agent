# Howtouse — a plain-language guide to Hermes Agent

This folder explains what Hermes Agent is, how to install and use it, what it can do, how to
keep it safe, and what every file in this repository is for.

| Read | What you get |
|---|---|
| [01-what-is-hermes.md](01-what-is-hermes.md) | What Hermes is, its main ideas, and the words used throughout |
| [02-install-and-setup.md](02-install-and-setup.md) | Installing on Linux, macOS, Windows, Android; choosing a model provider; first chat |
| [03-how-to-use.md](03-how-to-use.md) | Day-to-day use: CLI, TUI, desktop app, messaging bots, slash commands, sessions, profiles, config |
| [04-features-and-functions.md](04-features-and-functions.md) | Every capability: tools and toolsets, skills, memory, cron, subagents, MCP, plugins, providers, terminal backends |
| [05-safety-and-security.md](05-safety-and-security.md) | The trust model, approvals, YOLO mode, sandboxing, allowlists, secrets, hardening checklist |
| [06-repository-map.md](06-repository-map.md) | Folder-by-folder tour of the source code and how the pieces fit together |
| [07-agentwikis-notes.md](07-agentwikis-notes.md) | Extra tips gathered from the community wiki at agentwikis.com, cross-checked against this repo |
| [file-reference/](file-reference/README.md) | **Every file in the repository** (21,858 of them), one line each: what it does |

## Where the information comes from

- The repository itself: `README.md`, `SECURITY.md`, `AGENTS.md` files, the documentation site
  sources under `website/docs/`, and each source file's own docstring or header comment.
- The third-party knowledge base at <https://agentwikis.com/wiki/hermes/> (see
  [07-agentwikis-notes.md](07-agentwikis-notes.md) for what was taken from it and its caveats).

The official, always-current documentation is at <https://hermes-agent.nousresearch.com/docs/>.
When this folder and the official docs disagree, trust the official docs and the code.

## The 60-second version

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash   # install (Linux/macOS/WSL2)
source ~/.bashrc
hermes setup        # guided setup: pick a model provider, tools, options
hermes              # start chatting in the terminal
hermes --tui        # or the richer terminal UI
hermes gateway setup && hermes gateway start   # talk to it from Telegram, Discord, Slack, ...
hermes doctor       # something wrong? diagnose it
```

Safety in one line: Hermes runs real shell commands with your user's permissions. Keep approvals
on, run it in a container (`terminal.backend: docker`) when it reads untrusted content, set an
allowlist for every messaging bot, and review third-party skills and plugins before installing
them. Details in [05-safety-and-security.md](05-safety-and-security.md).
