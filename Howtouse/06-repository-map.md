# 6. Repository map — what each part of the code does

For a line-by-line description of **every file**, see [file-reference/](file-reference/README.md).
This page explains the folders and how they fit together.

## How a message flows through Hermes

```
 you ──► front-end ──────────────► agent core ──────────────► model provider
        (cli.py / ui-tui +         (run_agent.py AIAgent,      (agent/ transports,
         tui_gateway / apps/        agent/turn_*.py loop,        plugins/model-providers)
         desktop / gateway/)        prompt builder, memory,
                                    compression)
                                         │  tool calls
                                         ▼
                                    model_tools.py ──► tools/registry.py ──► tools/*.py
                                    (dispatch)          (terminal, files, web, browser,
                                                         delegate, memory, cron, …)
                                         │
                                         ▼
                                    hermes_state.py (SessionDB: sessions, messages,
                                    FTS5 search) in ~/.hermes/state.db
```

## Root files

| File | Role |
|---|---|
| `run_agent.py` | `AIAgent` facade — the agent object; the turn loop itself is in `agent/turn_*.py` |
| `cli.py` | Classic interactive CLI (REPL, slash dispatch); behaviour split into `hermes_cli/cli_*_mixin.py` |
| `hermes` | Launcher script equivalent to the installed `hermes` command |
| `model_tools.py` | Tool orchestration: discovers built-in tools and dispatches function calls |
| `toolsets.py` | The `TOOLSETS` map and the core tool list |
| `toolset_distributions.py` | Toolset presets used for batch/data generation |
| `hermes_state.py` + `hermes_state_*.py` | SQLite session store (WAL mode, FTS5 search, compression lineage, repair, usage accounting) |
| `hermes_constants.py` | Profile-aware paths (`get_hermes_home()`, `display_hermes_home()`) and shared constants |
| `hermes_bootstrap.py` | Process bootstrap: UTF-8 console on Windows, import-path hardening, network tweaks |
| `hermes_logging.py`, `hermes_time.py`, `hermes_yaml.py` | Logging setup, timezone-aware clock, shared YAML policy |
| `hermes_startup_watchdog.py` | Respawns a gateway that wedges during start-up |
| `batch_runner.py`, `mini_swe_runner.py`, `trajectory_compressor.py` | Research tooling: batch runs over datasets, SWE-style runner, compress trajectories for training |
| `SOUL.md` | Default persona text |
| `cli-config.yaml.example`, `.env.example` | Annotated configuration and secrets templates |
| `pyproject.toml`, `uv.lock`, `package.json` | Python and Node dependencies (managed by `pm/`) |
| `Dockerfile`, `docker-compose*.yml`, `docker/` | Official container image and Compose setup |
| `flake.nix`, `nix/` | Nix packaging |
| `setup-hermes.sh`, `setup-hermes.ps1`, `activate*` | Install / development-environment activation scripts |
| `AGENTS.md`, `CONTRIBUTING.md`, `SECURITY.md`, `README*.md` | Developer guide, contribution rules, security policy, readmes (EN, ES, UR, ZH) |

## Folders

| Folder | What lives there |
|---|---|
| `agent/` | The agent brain: turn loop phases, provider transports and model resolution, prompt assembly, memory, context compression, curator, auxiliary models |
| `tools/` | Every built-in tool (terminal, file ops, web, browser, delegation, memory, cron, vision, TTS, approvals …) and `tools/environments/` terminal backends |
| `hermes_cli/` | All `hermes …` subcommands: setup wizard, config system, model picker, profiles, plugins loader, updater, skins, slash-command registry, web-server routers |
| `gateway/` | Messaging gateway: `run.py` + `run_*.py` phases, sessions, delivery, streaming, notifications, token locks; `gateway/platforms/` base adapter, API server, webhooks |
| `plugins/` | Built-in plugins: messaging platforms (`platforms/`), memory providers, model providers, image/video generation, web search, browser providers, kanban, computer use, dashboard auth, context engine, … |
| `plugin-catalog/` | Curated third-party plugin catalog entries (admission rules in its README) |
| `skills/` | Built-in skills, by category (each a folder with `SKILL.md`) |
| `optional-skills/` | Shipped but not active skills you can enable |
| `optional-mcps/` | Pre-packaged MCP server definitions |
| `cron/` | Scheduler and job store (`jobs.py`, `scheduler.py`) |
| `tui_gateway/` | Python JSON-RPC backend for the terminal UI (also serves the desktop app) |
| `ui-tui/` | Ink/React terminal UI (TypeScript) |
| `apps/desktop/` | Electron desktop app (`electron/` main process, `src/` React UI) |
| `apps/shared/`, `apps/bootstrap-installer/` | Code shared between apps; Tauri-based installer |
| `web/` | Web dashboard single-page app |
| `acp_adapter/` | Agent Client Protocol server for editor integration (`hermes acp`) |
| `pm/` | Hermes' own dependency and environment manager (pinning, locked environments) |
| `hermes_platform/` | Machine facts and executable lookup (OS-specific behaviour lives here) |
| `providers/` | Provider metadata |
| `native/` | Small native helpers |
| `locales/` | Translations of user-facing strings |
| `scripts/` | Developer tooling: `check` (lint suite), `run_tests.sh`, code-health ratchets, CI and release scripts |
| `tests/`, `tests-js/` | Python pytest suite (mirrors the source tree) and JavaScript tests |
| `evals/` | Behaviour evaluations and live probes for specific features and bug classes |
| `website/` | Docusaurus documentation site (`website/docs/` is the full user and developer manual) |
| `assets/` | Banner and images |
| `contributors/` | Commit-email → GitHub-login mappings used to credit contributors in releases |
| `.github/` | CI workflows, issue/PR templates, automation |

## Conventions worth knowing (from `AGENTS.md`)

- **Facade + siblings:** big modules are split into a facade (`hermes_state.py`, `gateway/run.py`,
  `cli.py`, `run_agent.py`) plus topic files named `<stem>_<topic>.py`. Find code by topic with
  `grep -rn "def name" <dir>/<stem>_*.py`.
- Each area has its own `AGENTS.md` with detailed rules — read it before editing that area.
- Never hard-code `~/.hermes`; use `get_hermes_home()` (paths are per profile).
- `.env` is for secrets only; behaviour belongs in `config.yaml`.
- Lint with `python scripts/check`; test with `scripts/run_tests.sh` (never bare `pytest`).
