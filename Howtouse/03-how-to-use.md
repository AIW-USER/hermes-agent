# 3. How to use Hermes day to day

## Ways to talk to Hermes

| Interface | Start it | Good for |
|---|---|---|
| **Classic CLI** | `hermes` (or `hermes --cli`) | Quick terminal work, scripts |
| **TUI** | `hermes --tui` | Rich terminal UI: overlays, mouse selection, live session switcher |
| **Desktop app** | `hermes desktop` (alias `gui`) | Native window with file tree, terminal pane, preview pane, settings |
| **Web workspace / dashboard** | `hermes webapp`, `hermes dashboard` | Browser access to sessions, config and keys |
| **Messaging** | `hermes gateway setup` + `hermes gateway start`, then message the bot | Telegram, Discord, Slack, WhatsApp, Signal, Email, Matrix, Teams, SMS, … |
| **Editor (ACP)** | `hermes acp` | Use Hermes from editors that speak the Agent Client Protocol |
| **Scripts / one-shot** | `hermes chat -q "…" --oneshot`, `hermes -z "…"` | Automation; `--format stream-json` gives machine-readable JSONL |
| **Python library / API server** | see `website/docs/guides/python-library.md`, `user-guide/features/api-server.md` | Embedding Hermes in your own software |

All front-ends share the same sessions, slash commands, memory and skills.

## Talking to the agent effectively

- Be specific and give a way to verify: *"Fix the failing test in `tests/test_x.py` and run it."*
- Interrupt and redirect at any time: **Ctrl+C** in the CLI, or just send a new message
  (`/stop` on messaging). `/steer <note>` adds guidance mid-run without interrupting.
- Long task? Use `/plan` to get a written plan first, `/goal` to keep it working toward a
  standing objective, or `/bg <prompt>` to run it in a background session.
- Want something remembered? Say *"remember that I prefer concise answers"* — the agent stores it.

## Most useful slash commands

These work in the CLI/TUI and (mostly) on messaging platforms. `/help` lists everything,
`/palette` (Ctrl+P) is a fuzzy finder.

| Category | Commands |
|---|---|
| Session | `/new` (`/reset`), `/clear`, `/retry`, `/undo`, `/title`, `/resume`, `/sessions`, `/branch`, `/history`, `/save`, `/export` |
| Steering | `/stop`, `/queue`, `/steer`, `/btw` (side question), `/bg`, `/goal`, `/subgoal`, `/loop`, `/heartbeat`, `/plan`, `/review` |
| Model | `/model [provider:model]`, `/reasoning`, `/fast`, `/personality`, `/moa` (mixture of agents) |
| Context & cost | `/compress`, `/context`, `/usage`, `/insights`, `/status` |
| Files & git | `/diff`, `/rollback` (restore checkpoints), `/snapshot`, `/worktree`, `/init` (generate AGENTS.md) |
| Tools & skills | `/tools`, `/toolsets`, `/skills`, `/<skill-name>`, `/learn`, `/bundles`, `/curator`, `/reload-skills`, `/reload-mcp`, `/plugins` |
| Memory | `/memory` (review pending writes), `/journey` (timeline of what it learned), `/refine` |
| Automation | `/cron`, `/blueprint`, `/suggestions`, `/kanban` |
| Safety | `/approvals [manual\|smart\|off]`, `/yolo` (toggle — careful!), `/whoami` |
| Display | `/verbose`, `/focus`, `/skin`, `/statusbar`, `/timestamps`, `/voice`, `/redraw` |
| Messaging | `/sethome`, `/status`, `/platforms`, `/footer`, `/busy` |

## Important command-line commands

```bash
hermes chat [-m model] [--provider p] [-t toolsets] [-s skill] [--resume ID | -c]
hermes model | tools | config (show/edit/set/get) | setup
hermes sessions            # browse, export, prune, rename, delete sessions
hermes skills              # browse, install, publish, audit skills
hermes plugins             # install / enable / disable / remove plugins
hermes mcp                 # manage MCP servers
hermes cron                # inspect and tick the scheduler
hermes memory              # configure an external memory provider
hermes profile             # create / switch / delete isolated profiles
hermes kanban | project    # multi-agent task board, multi-folder workspaces
hermes pairing             # approve / revoke people who DM your bots
hermes insights            # token / cost / activity analytics
hermes pause | resume      # global emergency stop for cron, kanban and gateway work
hermes security audit      # supply-chain audit of installed packages, plugins, MCP servers
```

Useful global flags: `-p <profile>`, `--resume latest`, `-c` (continue last), `--in <dir>`,
`--worktree` (isolated git worktree), `--checkpoints`, `--ignore-rules`, `--safe-mode`,
`--yolo` (skips approvals — avoid unless sandboxed).

## Sessions

- Every conversation is saved in `state.db` (SQLite, full-text searchable).
- Resume: `hermes -c`, `hermes --resume <id|title|latest>`, or `/resume` / `/sessions`.
- Branch a conversation to try another path: `/branch`.
- The agent can search old conversations itself with the `session_search` tool.
- Long conversations are automatically **compressed** (older turns summarised) when they near
  the context limit; `/compress` does it on demand.

## Profiles — several independent Hermes instances

```bash
hermes profile create work           # blank profile (or --clone / --clone-all)
hermes -p work                       # use it once
hermes profile use work              # make it the sticky default
hermes profile list
```

Each profile has its own config, `.env`, memory, skills, sessions and bots. Profiles are
isolated on purpose; messaging channels are never cloned unless you pass `--clone-channels`.

## Configuration essentials (`~/.hermes/config.yaml`)

```yaml
model:
  default: anthropic/claude-opus-4.6   # default model
  provider: auto                       # auto-detect from credentials
terminal:
  backend: docker                      # local | docker | ssh | modal | daytona | vercel_sandbox
approvals:
  mode: smart                          # smart | manual | off
  timeout: 300
  deny:                                # commands that are ALWAYS blocked
    - 'git push --force*'
compression:
  threshold: 0.5                       # compress when context is this full (ratio)
```

- `hermes config` shows everything, `hermes config edit` opens the file.
- `cli-config.yaml.example` in this repo is an annotated example of most settings.
- Secrets never go in `config.yaml` — use `.env` or a secret manager (`hermes secrets`:
  Bitwarden, 1Password, command-based).

## Personality

- Edit `~/.hermes/SOUL.md` to change how the agent talks (permanent).
- `/personality <name>` applies a temporary overlay for the session; `/personality none` clears it.
- `/skin` changes the CLI look.

## Getting help

- `/help`, `hermes --help`, `hermes <command> --help`
- `hermes doctor` for diagnostics, `hermes logs` for logs, `hermes dump` for a support summary
- Docs: <https://hermes-agent.nousresearch.com/docs/> · Discord: <https://discord.gg/NousResearch>
