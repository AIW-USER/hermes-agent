# 5. Safety and security

Hermes runs real commands, reads the web and your messages, and can act on your behalf. This
page explains how it protects you, what those protections do **not** cover, and how to set it
up safely. The authoritative source is `SECURITY.md` at the repository root; the detailed user
guide is `website/docs/user-guide/security.md`.

## 5.1 The trust model in plain words

- Hermes is a **single-user personal agent**. By running it you let it do anything *your user
  account* can do (the "trust envelope").
- **The only real security boundary against a misbehaving model is the operating system** —
  a container, VM, remote host or sandbox. Everything inside the agent process (approval
  prompts, redaction, scanners, allowlists of tools) is a helpful *heuristic*, not containment.
- Two isolation postures:
  - **Terminal-backend isolation** (`terminal.backend: docker | ssh | modal | daytona | …`):
    shell and file tools run in the sandbox. It does *not* confine `execute_code`, MCP
    subprocesses, plugins, hooks or skill loading, which run in the agent's own process.
  - **Whole-process wrapping**: run all of Hermes inside a container (the official Docker image
    / Compose setup) or NVIDIA OpenShell. Use this when the agent reads content you don't
    control — the open web, inbound email, group chats, untrusted MCP servers — and for any
    shared or production deployment.

## 5.2 Layers of protection

1. **Who can talk to it** — allowlists and DM pairing on every messaging platform.
2. **Dangerous-command approval** — a human-in-the-loop prompt for risky shell commands.
3. **Hardline blocklist** — catastrophic commands are always refused.
4. **File-write safety** — denylist and optional write sandbox for `write_file` / `patch`.
5. **Container isolation** — Docker/Modal/Daytona/etc. with hardened settings.
6. **Credential filtering** — API keys and tokens are stripped from the environment given to
   shell commands, MCP servers, cron scripts and `execute_code`.
7. **Context-file and skill scanning** — prompt-injection detection in project files; Skills Guard for installable skills.
8. **Cross-session isolation and input sanitization** — sessions cannot read each other; paths and working directories are validated.

## 5.3 Approvals

Configure in `~/.hermes/config.yaml`:

```yaml
approvals:
  mode: smart            # smart (default) | manual | off
  timeout: 300           # seconds; no answer = denied (fail-closed)
  cron_mode: deny        # what unattended cron jobs do on a dangerous command
  single_query_mode: deny
  unattended_mode: deny  # webhook / API sessions
  deny:                  # your own always-blocked commands (glob patterns, quote them!)
    - 'git push --force*'
    - 'dd if=* of=/dev/*'
```

- **smart** — an auxiliary model auto-approves clearly harmless commands, auto-denies clearly
  dangerous ones and asks you about the rest.
- **manual** — always ask.
- **off** — never ask (same as YOLO). Only for disposable, sandboxed environments.

Commands that trigger a prompt include recursive `rm`, `chmod 777`, `mkfs`, `dd`, writes to
`/etc` or `~/.ssh`, SQL `DROP`/`TRUNCATE`/`DELETE` without `WHERE`, `curl … | sh`, `bash -c`,
killing Hermes itself, stopping services or containers, and redirecting Docker to another daemon.
In container backends these prompts are skipped because the container is the boundary.

**Hardline blocklist (cannot be overridden, not even by YOLO):** `rm -rf /` and variants, fork
bombs, `mkfs` on the live root, `dd` onto a disk device, piping untrusted URLs to `sh` at the
filesystem root, and commands whose quoting cannot be parsed.

**`execute_code` scripts** on messaging/API sessions ask once for the whole script before it runs.

## 5.4 YOLO mode — use with care

`hermes --yolo`, `/yolo` (toggle) or `HERMES_YOLO_MODE=1` skip all approval prompts. A red
banner and a `⚠ YOLO` status-bar marker remind you it's on. It is saved with the session.
YOLO still respects the hardline blocklist, your `approvals.deny` rules, MCP spend limits and
payment-card prompts. On messaging platforms, `/new` turns approvals back on.

## 5.5 Messaging bots — lock them down

```bash
# ~/.hermes/.env
TELEGRAM_ALLOWED_USERS=123456789
DISCORD_ALLOWED_USERS=...
GATEWAY_ALLOWED_USERS=123456789,987654321    # applies to all platforms
# GATEWAY_ALLOW_ALL_USERS=true               # NOT recommended for a bot with terminal access
```

Or use **DM pairing**: unknown users get a one-time code; approve them with
`hermes pairing approve telegram <CODE>` (`hermes pairing list`, `hermes pairing revoke …`).
Codes expire after an hour. Allowed users are split into **admins** (all commands) and
**regular users** (chat plus only the slash commands you allow). Every network-exposed adapter
must have an allowlist — an adapter that works without one is a security bug.

Everyone inside an allowlist is equally trusted. If people need different powers, run separate
profiles/instances with separate allowlists.

## 5.6 Secrets

- API keys and tokens go **only** in `~/.hermes/.env` (tight file permissions), never in
  `config.yaml` or version control. Or pull them at start-up from a secret manager:
  `hermes secrets` (Bitwarden, 1Password, command-based).
- `browser_vault` fills saved logins and cards on web pages without the secret entering the conversation.
- Output redaction hides secret-looking strings in displays (a heuristic, not a guarantee).
- `hermes egress` (iron-proxy) can inject credentials at the network edge for remote sandboxes
  so the sandbox never sees them.

## 5.7 Skills, plugins and MCP servers

- **Plugins and skills run inside the agent with full privileges.** Read a third-party skill's
  Python and scripts — not just its `SKILL.md` — and review plugins before installing.
- Skills Guard and the install audit log help review, but they are aids, not boundaries.
- Mark untrusted MCP servers `trust: untrusted` so their write tools ask first; set
  `spend_limit` for paid tools.
- `hermes security audit` checks your environment, plugin requirements and pinned MCP servers
  against known vulnerabilities (OSV.dev).

## 5.8 Undo and recovery

- `--checkpoints` / `/rollback` — restore files from snapshots taken before destructive edits.
- `/undo`, `/retry`, `/branch` — conversation-level undo and alternatives.
- `/snapshot` — snapshot and restore Hermes' own config/state.
- `hermes backup` / `hermes import` — full backups.
- `hermes pause` — stop all cron, kanban and gateway dispatch at once.

## 5.9 Hardening checklist

- [ ] Run Hermes as a **non-root** user (the Docker image does this by default).
- [ ] Match isolation to what it reads: untrusted input → container backend or whole-process Docker/OpenShell.
- [ ] Keep `approvals.mode` at `smart` or `manual`; add `approvals.deny` rules for things that must never happen.
- [ ] Set an allowlist or use pairing for **every** messaging platform.
- [ ] Never expose the gateway, API server or dashboard to the internet without VPN/Tailscale/firewall
      and authentication; dashboards bind to loopback by default — keep it that way unless you know why.
- [ ] Secrets only in `.env` or a secret manager; `chmod 600 ~/.hermes/.env`.
- [ ] Review third-party skills, plugins and MCP servers before installing.
- [ ] Keep Hermes updated (`hermes update`) and run `hermes security audit` periodically.
- [ ] Use `--safe-mode` to troubleshoot with every customization disabled.

## 5.10 Reporting a vulnerability

Report privately through GitHub Security Advisories or **security@nousresearch.com** — never in a
public issue. Include the file and line range, `hermes --version`, OS, a reproduction, and which
trust boundary is crossed. Prompt injection alone, or a bypass of an in-process heuristic (e.g.
the approval regexes), is not a vulnerability under the policy — but improvements are welcome
as normal issues or pull requests. There is no bug bounty; disclosure window is 90 days.
