# File reference: `hermes_cli`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `hermes_cli/`

| File | What it does |
|---|---|
| `AGENTS.md` | hermes_cli/ + cli.py — CLI, slash commands, config, skins, updater, profiles |
| `__init__.py` | Hermes CLI - Unified command-line interface for Hermes Agent. |
| `_early_recovery.py` | Startup requests for PM recovery and rescue of orphaned launchers. |
| `_early_recovery_zip.py` | Settles a ZIP ``hermes update`` swap whose owner died: its journal, owner lock and recovery. |
| `_install_repair.py` | Repair Windows launchers and their registered PATH entries. |
| `_launchers.py` | Source-install launchers shared by setup, installers, and Windows repair. |
| `_old_updater.py` | The newly imported escape hatch from an already-running historical updater. |
| `_parser.py` | Top-level argparse construction for the hermes CLI. |
| `_scan_venv_blockers.py` | Compatibility entry point for historical Desktop venv preflights. |
| `_secrets_common.py` | Helpers shared by the Bitwarden and 1Password ``hermes secrets`` CLIs. |
| `_startup_fast.py` | Pre-import startup fast paths — THE canonical lightweight helpers. |
| `_subprocess_compat.py` | Windows subprocess compatibility helpers. |
| `_update_takeover.py` | Absolute-path bootstrap for historical updater takeover; no app imports yet. |
| `active_sessions.py` | Cross-process active chat session leases. |
| `agent_plugins.py` | Compatibility helpers for Agent Plugins v1 portable directory packages. |
| `anon_auth.py` | Nous free-tier identity: the ``anonymous`` auth method of the ``nous`` provider. |
| `anon_challenge.py` | Nous free tier: the browser challenge the account service may put in front of a token exchange. |
| `anon_sign_in.py` | The one Nous sign-in: the plain device-code login every surface renders, plus its states and copy. |
| `anon_sign_in_cli.py` | Terminal and chat rendering for the shared sign-in flow. |
| `approval_mode.py` | Shared persistent approval-mode command logic. |
| `approval_transport.py` | Host-owned contract for plugin-provided human approval transports. |
| `approvals_suggest.py` | ``hermes approvals suggest`` — mine approval history into allowlist proposals. |
| `approvals_test.py` | ``hermes approvals test`` — dry-run approval verdict for a command. |
| `archive_safe.py` | Safe ``tar.gz`` primitives shared by the profile and kanban transfer paths. |
| `auth.py` | Multi-provider authentication system for Hermes Agent. |
| `auth_codex.py` | OpenAI Codex OAuth: token store, refresh, quota probe, device-code login. |
| `auth_codex_browser.py` | OpenAI Codex browser login: authorization-code + PKCE on a loopback listener (opt-in). |
| `auth_commands.py` | Credential-pool auth subcommands. |
| `auth_constants.py` | Shared constants, the lazy ``httpx`` proxy and :class:`AuthError` for the auth package. |
| `auth_device_flow.py` | Shared device-code / loopback-PKCE / browser / TLS helpers for interactive OAuth logins. |
| `auth_error_copy.py` | Plain-language copy for sign-in and provider-setup failures (CLI). |
| `auth_external_process.py` | Executable lookup and launch-env policy for ``external_process`` (ACP) providers. |
| `auth_minimax.py` | MiniMax OAuth (user-code grant) login, refresh and runtime credentials. |
| `auth_model_picker.py` | Interactive model picker used after OAuth login. |
| `auth_nous.py` | Nous Portal OAuth: device-code login, refresh, shared-store mirroring, JWT selection, status. |
| `auth_oauth_grants.py` | Single-use OAuth grant hygiene: strip cloned grants from profiles, heal forked grants. |
| `auth_oauth_pkce_plugin.py` | Declarative OAuth 2.0 Authorization-Code + PKCE login for out-of-tree model-provider plugins. |
| `auth_openrouter.py` | OpenRouter OAuth PKCE login (``hermes auth add openrouter --type oauth``). |
| `auth_plugin_providers.py` | Model-provider plugins as first-class citizens of ``hermes auth`` and the credential pool. |
| `auth_qwen.py` | Qwen OAuth (qwen-cli token file) runtime credentials and status. |
| `auth_xai.py` | xAI Grok OAuth: token store, discovery, refresh, device-code login. |
| `auth_zai_kimi.py` | Kimi Code and Z.AI endpoint auto-detection, LM Studio base-URL normalization. |
| `azure_detect.py` | Azure Foundry endpoint auto-detection. |
| `backend_retirement.py` | Process-owned admission fence for cooperative Desktop backend retirement. |
| `backup.py` | Backup and import commands for hermes CLI. |
| `backup_cron_prompts.py` | Post-update cron safety net for field-level loss: restore agent-job prompts an update collapsed to the job name while the job count stayed the same (issue #82990). |
| `backup_restore.py` | SQLite-safe restore and archive-member publish plumbing for backups. |
| `backup_sqlite.py` | WAL-safe SQLite snapshots. Direct execution needs only the standard library. |
| `bang_shell.py` | ``!<command>`` shell mode for the interactive CLI. |
| `banner.py` | Welcome banner, ASCII art, skills summary, and update check for the CLI. |
| `blueprint_cmd.py` | Shared ``/blueprint`` command logic for CLI, TUI, and gateway. |
| `boot_bootstrap.py` | Bounded home maintenance after an installed revision changes. |
| `browser_connect.py` | Shared helpers for attaching Hermes to a local Chromium-family CDP port. |
| `browser_credential.py` | The browser credential, and how every grant made under it ends when it is replaced. |
| `browser_runtime.py` | Read-only full-Chromium selection shared by browser launchers. |
| `build_info.py` | Shims to suppress old updater work until relaunch. Live identity uses version_info. |
| `bundled_app.py` | Where the running BUNDLED desktop app lives, and how to start it. |
| `bundles.py` | Implementation of the ``hermes bundles`` CLI subcommand. |
| `callbacks.py` | Secret-capture prompt for the interactive CLI (``_secret_capture_callback`` backend). |
| `chat_catalog.py` | Admit only chat models into shared chat catalogs. |
| `checkpoints.py` | `hermes checkpoints` CLI subcommand. |
| `cli_agent_setup_mixin.py` | Agent construction + session-resume display for ``HermesCLI``: credential resolution, per-turn agent config, first-use build, resume preload + recap. ``cli.py`` helpers are imported lazily inside each method (import cyc… |
| `cli_auto_maintenance.py` | Startup auto-maintenance for the classic CLI: state-db pack/vacuum and checkpoint pruning run off the prompt thread. |
| `cli_billing_mixin.py` | Billing and subscription handlers for the interactive CLI (mixed into ``HermesCLI``). cli.py symbols are imported LAZILY inside methods — never at module load (import cycle). |
| `cli_browser_gateway.py` | Classic CLI ``/browser`` on the shared gateway (#134889 CLI-9): ``browser.manage``, as Ink and Desktop send it. Split from ``cli_commands_mixin`` (the file is over its size target). |
| `cli_chat_error_copy.py` | Plain-language copy for chat-turn failures shown in the CLI response panel. |
| `cli_chat_turn_mixin.py` | chat() and its per-turn phases: image routing, staging, agent thread, interrupt monitor, rendering. |
| `cli_commands_mixin.py` | Slash-command handlers for the interactive CLI (``HermesCLI`` inherits ``CLICommandsMixin``). |
| `cli_commands_session_tools.py` | Shared print/translate helpers + session-info slash handlers (``cli_commands_mixin`` split). |
| `cli_commands_worktree.py` | ``/worktree new``'s step into the tree it just created, split out of ``cli_commands_mixin``. |
| `cli_config_load.py` | Classic-CLI config loading: prefill messages, reasoning/service-tier parsing, terminal env mirroring, CLI defaults + user YAML merge and the logging/display bootstrap. |
| `cli_cron_lines.py` | The classic CLI's `/cron` as plain lines: the overview, the list and every store write. |
| `cli_enter_burst.py` | Enter arriving inside a fast input burst: pasted newline or scripted submit. |
| `cli_footer_split.py` | Root container of the classic CLI footer: clips a late row instead of giving up. |
| `cli_info_lines.py` | The classic CLI's `/toolsets` and `/platforms` reports as plain lines. |
| `cli_info_mixin.py` | Informational views and reload flows for the interactive CLI: banner, help, tools, usage, insights, MCP/skills reload, bang shell. |
| `cli_init_mixin.py` | HermesCLI constructor phases: display options, model/provider routing, turn limits, toolsets, checkpoints, prompt/reasoning, runtime state, session store and UI state. |
| `cli_loops_mixin.py` | Simple slash-command wrappers plus goal/heartbeat/loop manager hooks for the interactive CLI. Mixin on ``HermesCLI``; cli.py symbols are imported lazily inside methods (import cycle). |
| `cli_modal_mixin.py` | Modal overlays for the interactive CLI: clarify, approval, sudo/secret capture, command palette, slash-confirm, external editor. |
| `cli_model_switch_mixin.py` | Model picker, /model switch application, runtime snapshot/restore, and codex runtime handling for the interactive CLI |
| `cli_modern_layout.py` | Glyph-grammar transcript and bottom-anchored chrome for the classic CLI (``display.cli_layout``). |
| `cli_output.py` | Shared CLI output helpers (``print_*`` + ``prompt()``) for the setup/config wizards. |
| `cli_panel.py` | Bordered overlay panels (approval, clarify, sudo, pickers) for the classic CLI's live region. |
| `cli_process_dock.py` | Background-process rows for the classic CLI live-work dock. |
| `cli_process_notifications.py` | CLI notification ownership, structured queueing and last-moment consumption. |
| `cli_render.py` | Classic-CLI rendering helpers: reasoning-tag stripping, ANSI/skin colours, light-mode detection, markdown/final-content rendering, output-history replay, ``_cprint`` and the panel box/wrap helpers. |
| `cli_session_dock.py` | Goal, loop + queued-prompt rows for the classic CLI live-work dock. |
| `cli_session_mixin.py` | Session lifecycle for the interactive CLI: new/resume/save, undo/retry rewinds, yolo persistence, manual compression, and exit summary. |
| `cli_session_switch.py` | Session-switch plumbing shared by /resume, /sessions and /branch. |
| `cli_shutdown.py` | Classic-CLI shutdown and one-shot finalize helpers: process session-id sync, deferred agent startup, exit watchdog, cleanup steps, session-finalize notifications and the terminal input-mode reset. |
| `cli_single_query.py` | Single-query (``-q`` / one-shot) helpers: kanban goal loops, exit-code mapping, quiet single-query runner, image routing, signal handlers and the single-query mode orchestrator. |
| `cli_snapshot.py` | Classic CLI snapshot restore: hand off the profile offline, then rejoin its authority. |
| `cli_status_bar_mixin.py` | Status bar, spinner, turn-summary, pet pane, and prompt-stash rendering for the interactive CLI. |
| `cli_stream_mixin.py` | Streaming output, reasoning preview, tool progress callbacks, and busy-command spinner for the interactive CLI |
| `cli_subagent_monitor.py` | Classic CLI live-work dock (subagents, background processes, active goal, standing loop, queued prompts) and scoped controls; no agent-loop state is changed. Process rows come from ``cli_process_dock``, goal/loop/queue… |
| `cli_terminal_input.py` | Classic-CLI terminal input helpers: file-drop/attachment path resolution, bracketed-paste patching, extended Enter-key sequences, CPR leak guards and TUI input-height estimation. |
| `cli_terminal_mixin.py` | Terminal repaint/resize recovery, input-mode healing, and clipboard helpers for the interactive CLI. Mixin on ``HermesCLI``; cli.py symbols are imported lazily inside methods (import cycle). |
| `cli_tui_mixin.py` | prompt_toolkit TUI construction, key-binding handlers, and overlay display fragments for the interactive CLI. Mixin bound onto ``HermesCLI`` via the MRO; cli.py-internal symbols are imported LAZILY inside each method (`… |
| `cli_tui_runtime_mixin.py` | Classic-TUI run loop phases: input processing, after-turn bookkeeping, startup banner/prewarm/maintenance, prompt_toolkit application build, signal handlers and shutdown. |
| `cli_tui_wrap.py` | Row-wrapping helpers for the classic CLI's prompt_toolkit panels (moved from ``cli_tui_mixin``). |
| `cli_unknown_command.py` | Copy for an unknown slash command: says nothing was sent and suggests a near-miss. |
| `cli_voice_mixin.py` | Voice mode (recording, STT, TTS, full-duplex barge-in) and wake-word listener handlers for the interactive CLI |
| `clipboard.py` | Clipboard image extraction and text write for macOS, Windows, Linux, and WSL2. |
| `codex_models.py` | Codex model discovery from API, local cache, and config. |
| `codex_runtime_plugin_migration.py` | Migrate Hermes MCP server config and Codex's installed curated plugins into ~/.codex/config.toml. |
| `codex_runtime_switch.py` | Shared logic for the /codex-runtime slash command (CLI and gateway call into this module). |
| `colors.py` | Shared ANSI color utilities for Hermes CLI modules. |
| `commands.py` | Slash command registry for the Hermes CLI and gateway. |
| `commands_completion.py` | prompt_toolkit completer + inline auto-suggest for slash commands. Kept out of :mod:`hermes_cli.commands` (which re-exports both classes) so the registry module stays prompt_toolkit-free for the gateway. |
| `commands_platforms.py` | Gateway platform command derivations (Telegram / Discord / Slack) from ``COMMAND_REGISTRY``. |
| `completion.py` | Shell completion script generation for hermes CLI. Walks the live argparse parser tree, so completion scripts never go stale; no extra dependencies. |
| `config.py` | Configuration management for Hermes Agent: config.yaml / .env loading, saving, validation, migration, and the ``hermes config`` command. |
| `config_backend.py` | Where the user config layer lives: the ``ConfigBackend`` seam (config-config design §4.1, D10/D11). |
| `config_backups.py` | Point-in-time copies of ``config.yaml``: one directory, one naming scheme, bounded count. |
| `config_check_diagnostics.py` | Read-only diagnostics for saved toolsets and bundled platform selections. |
| `config_defaults.py` | Default configuration data for Hermes Agent: DEFAULT_CONFIG and OPTIONAL_ENV_VARS. |
| `config_defaults_auxiliary.py` | Pure-data factory for auxiliary model configuration defaults. |
| `config_defaults_env.py` | Entry factories for ``config_defaults.OPTIONAL_ENV_VARS`` (pure-data leaf, no imports). |
| `config_effective.py` | The effective USER config: config.yaml + managed overlay + ``${VAR}`` expansion, no defaults. |
| `config_env_routing.py` | Which ``hermes config`` keys live in ``.env`` instead of ``config.yaml``, and their lifecycle. |
| `config_home.py` | Directory initialization and storage diagnostics for the active Hermes home. |
| `config_issues.py` | The issue record config validation emits (``hermes config check``, doctor, startup warnings). |
| `config_key_notices.py` | Notices ``hermes config set`` prints for a key path the schema does not know. |
| `config_language.py` | ``display.language`` validation for ``hermes config set`` — pluggable languages. |
| `config_migrations.py` | Table-driven config migration registry. |
| `config_migrations_browser.py` | Config step 51 -> 52 (registered in ``hermes_cli.config_migrations.MIGRATIONS``): agent-browser and the built-in browser_* tools left Hermes, so ``browser.backend`` / ``browser.extension_control`` go and the AGENT_BROWS… |
| `config_providers.py` | Custom-provider entry normalization and per-route lookups (TLS, headers, context length, capabilities). |
| `config_read_errors.py` | What Hermes does when an existing ``config.yaml`` cannot be read or parsed. |
| `config_runtime_keys.py` | Config keys the runtime reads that the DEFAULT_CONFIG walk in ``_validate_config_key`` cannot see. |
| `config_section_guard.py` | Guard ``hermes config set`` against a single-segment key overwriting a whole config section. |
| `config_show.py` | ``hermes config`` / ``hermes config show``: the read-only configuration summary. |
| `config_value_checks.py` | Value checks for single config sections (voice, timezone, web backends), run by ``hermes_cli.config.validate_config_structure`` for doctor and the startup warnings. |
| `config_version_stamp.py` | The config schema-version stamp: raw reads of ``_config_version`` from config.yaml. |
| `config_worker_save.py` | What ``save_config`` persists when the process serves a frozen session config. |
| `connectors_cmd.py` | ``hermes connectors``: list, connect, rename and remove hosted connector accounts. |
| `console_engine.py` | Safe Hermes Console command engine. |
| `container_boot.py` | Container-boot reconciliation of per-profile gateway s6 services. |
| `context_switch_guard.py` | Warn when an in-session model switch will trigger preflight compression on the next turn. |
| `credential_lifecycle.py` | Unified provider-credential lifecycle across every store Hermes reads. |
| `cron.py` | Cron subcommand for hermes CLI. |
| `curator.py` | CLI subcommand: `hermes curator <subcommand>`. |
| `curses_ui.py` | Curses checklist / radiolist / single-select menus with keyboard navigation and fuzzy ``/`` search, plus a numbered text fallback for terminals without curses. |
| `dashboard_procs.py` | Dashboard process-hygiene helpers — extracted from ``hermes_cli/main.py``. |
| `dashboard_register.py` | ``hermes dashboard register`` — register a self-hosted dashboard OAuth client. |
| `data_cleanup.py` | Data-only deletion separates user state from the runtime that must survive. |
| `data_cleanup_holders.py` | Home-scoped runtime coordination for an explicitly confirmed data wipe. |
| `debug.py` | ``hermes debug`` debug tools for Hermes Agent. |
| `debug_redaction.py` | Fail-closed redaction for text and structures leaving debug/support flows. |
| `default_soul.py` | Default SOUL.md template seeded into HERMES_HOME on first run. |
| `desktop_build_lock.py` | Cross-process serialization for the mutable Desktop build preflight. |
| `desktop_build_reuse.py` | Reuse a packaged desktop app across commits that changed none of its build inputs. |
| `desktop_console.py` | Keep Windows console backpressure off the packaged desktop startup path. |
| `desktop_plugin_halves.py` | Copy each unified agent+desktop package's ``desktop/`` half into the app-level desktop-plugins folder. |
| `desktop_plugin_install.py` | Install a desktop plugin from Git onto the host that serves the Webapp. |
| `desktop_release_holders.py` | Name the programs holding ``apps/desktop/release`` open by working directory (#101789). |
| `desktop_update_verify.py` | Read-only verification at the Windows Desktop handoff receipt boundary. |
| `diagnostics_upload.py` | Client for uploading ``hermes debug share`` bundles to Nous-internal S3. 1. POST {NAS_BASE}/api/diagnostics/upload-url → {uploadUrl, viewUrl, id, ...}; the body carries ``sizeBytes``, which NAS signs into the presigned… |
| `dingtalk_auth.py` | DingTalk Device Flow authorization. |
| `doctor.py` | ``hermes doctor`` — diagnose (and with --fix, repair) a Hermes install. |
| `doctor_config.py` | Configuration-file checks for hermes doctor: .env, config.yaml validation, drift, deprecations. Split out of ``hermes_cli/doctor.py``. |
| `doctor_connectivity.py` | API connectivity probes for ``hermes doctor`` (split out of ``doctor.py``). |
| `doctor_live.py` | ``hermes doctor --live`` — opt-in bounded real-call tool-backend probes. |
| `doctor_platform.py` | Host-platform checks for hermes doctor: interpreter, SQLite, certificates, macOS TCC, gateway supervision, command install. Split out of ``hermes_cli/doctor.py``, which re-exports every name so ``hermes_cli.doctor.<name… |
| `doctor_report.py` | Doctor output primitives shared by every ``hermes_cli.doctor_*`` module. |
| `doctor_state.py` | HERMES_HOME state checks for hermes doctor: directories, memory files, state.db health, skills hub, memory provider, profiles. Split out of ``hermes_cli/doctor.py``, which re-exports every name so ``hermes_cli.doctor.<n… |
| `doctor_tools.py` | External-tool checks for hermes doctor: terminal backends, git/rg, Node + Chromium, npm audit, tool availability. Split out of ``hermes_cli/doctor.py``, which re-exports every name so ``hermes_cli.doctor.<name>`` keeps… |
| `dump.py` | Dump command for hermes CLI. |
| `env_loader.py` | Helpers for loading Hermes .env files consistently across entrypoints. |
| `fallback_cmd.py` | hermes fallback — manage the fallback provider chain (tried in order when the primary fails). |
| `fallback_config.py` | Helpers for reading the effective fallback provider chain from config. |
| `focus_view.py` | Focus view — display-only reduced output: "just my prompt and the answer, and tell me what you hid". ON snaps ``tool_progress_mode`` to ``"off"`` and remembers the configured mode so the *existing* suppression path does… |
| `foreign_sessions.py` | Import sessions from foreign coding agents (Claude Code, Codex CLI). Foreign files are only ever read; imported history must satisfy the provider role-alternation invariant (see ``_merge_turns``). |
| `foreign_sessions_browser.py` | Backend-local discovery and previews for the desktop session importer. |
| `free_tier_bootstrap.py` | Record of who carries inference, for ``setup.status`` and ``setup.ready``. |
| `free_tier_offer.py` | When a free-tier "sign in" offer is due: after finished tasks, backing off. |
| `fs_utils.py` | Filesystem helpers shared across Hermes CLI subsystems. |
| `gateway.py` | Gateway subcommand for hermes CLI. |
| `gateway_agent.py` | The AIAgent surface main's HermesCLI uses, backed by the shared gateway session (CALLMAP §3.2-3.3). |
| `gateway_automation.py` | The classic CLI's /goal, /subgoal, /loop and /heartbeat managers, backed by the gateway session. |
| `gateway_chat.py` | Normal classic/one-shot launch through the canonical gateway, never AIAgent. |
| `gateway_chat_commands.py` | Classic CLI slash commands on the shared gateway, beyond the view's own controls. |
| `gateway_chat_listing.py` | ``--list-tools`` / ``--list-toolsets`` on the gateway path: a catalog listing needs no session. |
| `gateway_chat_startup.py` | Frontend startup checks shared by classic chat and top-level one-shot. |
| `gateway_chat_view.py` | Classic terminal presentation of authority events and fenced controls. |
| `gateway_cli_commands.py` | Classic CLI commands whose state lives in the gateway session, answered there. |
| `gateway_client.py` | Transport-only RPC client. Closing a viewer never stops its authority. |
| `gateway_command_errors.py` | User-facing copy for ``hermes gateway start/stop/restart`` failures on systemd hosts. |
| `gateway_connection.py` | One gateway connection per classic-CLI process (CALLMAP §3.1, §4). |
| `gateway_enroll.py` | ``hermes gateway enroll`` — enroll a self-hosted gateway with a relay connector. |
| `gateway_host_record.py` | Host-gateway cleanup after a confirmed stop: the rendezvous record and the memoized probe. |
| `gateway_launchd.py` | Gateway launchd (macOS LaunchAgent) backend: plist generation/refresh, bootstrap, start/stop/restart/status. |
| `gateway_launchd_runtime.py` | macOS: start an unmanaged gateway as a one-off launchd job so it keeps Local Network access. |
| `gateway_lifecycle_guards.py` | Refusals that keep ``hermes gateway`` lifecycle verbs off gateways they must not take down. |
| `gateway_migrate.py` | ``hermes gateway migrate --multiplex``: converge a per-profile-gateway install onto the ONE host gateway, with a table-driven preflight. |
| `gateway_migrate_guards.py` | Boundaries the AUTOMATIC multiplex migration (``hermes update``) must not cross, and the opt-out. |
| `gateway_multiplex_mode.py` | Boot-time verdict for ``gateway.multiplex_profiles`` (the default is on, and there is no opt-out). |
| `gateway_multiplex_s6.py` | s6 leg of the one-gateway-per-host convergence, shared by container boot and in-process migration. |
| `gateway_multiplex_served.py` | Which profiles does the LIVE default multiplexer serve? One answer for every CLI/dashboard surface. |
| `gateway_mutations.py` | Prepared native controls retain their identity across ambiguous RPC replies. |
| `gateway_plugin_commands.py` | Plugin slash commands of the classic CLI on the shared gateway (``slash.exec``). |
| `gateway_profile_lifecycle.py` | Named-profile lifecycle inside the host gateway, never a service-manager action. |
| `gateway_queue.py` | The classic CLI's ``/queue`` over the gateway's durable FIFO (refs #134889, N5). |
| `gateway_replay_gap.py` | After ``session.replay_gap``: re-attach, settle once, never splice the reply across the hole. |
| `gateway_rollback.py` | ``/rollback`` on the shared gateway session (``rollback.list`` / ``rollback.diff`` / ``rollback.restore``). |
| `gateway_runtime.py` | Validated, credential-free gateway endpoint discovery for local clients. |
| `gateway_runtime_cli.py` | Machine-readable ensure boundary. No bootstrap credentials leave this command. |
| `gateway_runtime_discovery.py` | Bounded local-control discovery without diagnostic fallback or mutation (the one exception: an upgraded same-owner ``gateway.lock`` is narrowed to 0600, see :func:`_private_lock`). |
| `gateway_runtime_multiplex.py` | Which daemon a named-profile client must start when nothing serves its home. |
| `gateway_runtime_replace.py` | Replace a gateway left running by an older Hermes on this install's own home. |
| `gateway_runtime_service.py` | Non-installing service-manager operations for an explicit canonical profile. |
| `gateway_runtime_service_identity.py` | Read-only binding checks; unknown supervisor syntax is not profile absence. |
| `gateway_runtime_start.py` | One detached-process primitive; callers must first prove owner/service absence. |
| `gateway_service_owner.py` | Who may write a gateway service definition (systemd unit, launchd plist). |
| `gateway_session_store.py` | ``HermesCLI._session_db`` backed by the shared gateway session (CALLMAP §3.5). |
| `gateway_setting_commands.py` | Per-session setting commands of the classic CLI on the shared gateway (``slash.exec``). |
| `gateway_setup_service.py` | Gateway service setup orchestration; runtime startup is separate. |
| `gateway_setup_wizard.py` | Gateway platform setup wizard (hermes gateway setup): platform registry/status table, per-platform setup prompts, service offer. |
| `gateway_side.py` | ``/bg`` and ``/btw`` on the shared gateway session (``prompt.background`` / ``prompt.btw``). |
| `gateway_status_notes.py` | Notes `hermes gateway status` prints beside the running/not-running verdict. |
| `gateway_supervised_restart.py` | ``hermes gateway restart`` for a gateway whose supervisor Hermes did not install. |
| `gateway_tools.py` | The background-process registry main's classic CLI reads, served by the gateway session. |
| `gateway_tools_notify.py` | Background-process notification turns the gateway admits for this CLI's session (W11). |
| `gateway_windows.py` | Windows gateway service backend (Scheduled Task + Startup-folder fallback). |
| `gateway_windows_legacy.py` | Pre-suffix Windows gateway launchers: the objects the current per-profile names cannot reach. |
| `git_commit_graph.py` | Keep a checkout's commit-graph fresh: the ``hermes -w`` pass and every ``hermes update``. |
| `git_credentials.py` | Non-interactive HTTPS credentials for Hermes's internal git clones (private plugin/MCP/profile repos). |
| `git_pack_tidy.py` | Progressive, time-boxed cleanup of a partial clone's promisor packfiles (#129712). |
| `github_api.py` | Credentials and failure copy for the update check's api.github.com calls. |
| `gitlock.py` | Stale git lock-file and aborted-fetch pack-debris recovery for update/check paths. |
| `goal_command.py` | The CLI's /goal semantics, shared by every goal command surface. |
| `goals.py` | Persistent session goals — the Ralph loop for Hermes. |
| `guest_handoff.py` | Guest handoff: after a Nous account replaces the free tier, move the free tier's apps into it. |
| `gui_uninstall.py` | Hermes Desktop (Chat GUI) uninstaller: removes only GUI state — built Electron artifacts, the packaged app, and the desktop's own ``userData`` — never agent source, venv, config, sessions or .env. |
| `heartbeat.py` | Session heartbeats — recurring re-entry prompts for the current session. |
| `home_data_layout.py` | Machine-specific state excluded from portable home transfers. |
| `hooks.py` | hermes hooks — inspect and manage shell-script hooks. |
| `image_provenance.py` | Image-authored deployment provenance for immutable Hermes runtimes. |
| `init_command.py` | ``/init`` — build the prompt that asks the agent to generate or update a project AGENTS.md. |
| `input_sanitize.py` | Sanitize user prompt text leaked from terminal / paste control sequences. |
| `install_identity.py` | Stable opaque identity shared by every profile in one Hermes install. |
| `install_state.py` | Has this OS user already used Hermes on this computer? |
| `inventory.py` | Provider/model inventory — shared substrate for the dashboard ``/api/model/options``, the TUI ``model.options``/``model.save_key`` RPC handlers, and the interactive picker. |
| `journey.py` | ``hermes journey`` — what Hermes has learned, on a timeline. |
| `kanban.py` | ``hermes kanban …`` — dispatch (``kanban_command``), task-verb handlers, ``run_slash`` for ``/kanban``. DB work lives in ``kanban_db``; siblings: ``kanban_parser`` (argparse, re-exported ``build_parser``), ``kanban_outp… |
| `kanban_boards.py` | ``hermes kanban boards …`` — board directories, the ``current`` pointer and ``board.json``. Filesystem-only, so every action works before ``kanban init`` and must ignore the shared ``--board`` task-routing override. |
| `kanban_db.py` | SQLite-backed Kanban board shared across profiles (the cross-profile coordination primitive). |
| `kanban_db_boards.py` | Board metadata (``board.json``) and board lifecycle management for the Kanban DB: read/write of per-board display metadata, board creation/discovery/archival, and the ``board.json``-as-identity-marker rule. |
| `kanban_db_connect.py` | SQLite connection lifecycle for the Kanban DB: open/configure, cross-process init and dispatch-tick locks, WAL checkpoints, corruption detection + quarantine + repair, additive migrations and the busy-retrying ``write_t… |
| `kanban_db_context.py` | Worker-context rendering for ``build_worker_context``: the capped markdown sections a spawned worker reads about its task (header, attachments, prior attempts, parent handoffs, role history, comments). |
| `kanban_db_dispatch.py` | Dispatcher: crash/stale/orphan detection, failure accounting and the respawn circuit breaker, memory-aware concurrency caps, the one-shot ``dispatch_once`` pass, worker spawning (``_default_spawn``), worker-log rotation… |
| `kanban_db_graph.py` | Task graph initialization and atomic decomposition persistence. |
| `kanban_db_notify.py` | Notification subscriptions consumed by the gateway kanban-notifier: per-(task, platform, chat, thread) rows with delivery metadata, unseen-event cursors and purge of stale done-task subs. |
| `kanban_db_workspace.py` | Task workspace lifecycle: scratch/dir/worktree resolution (incl. git worktree creation), post-completion cleanup with containment guards, worker tmux teardown and the first-use scratch-workspace tip. |
| `kanban_decompose.py` | Kanban decomposer — fan a triage task out into a graph of child tasks. |
| `kanban_diagnostics.py` | Kanban diagnostics — structured, actionable distress signals for tasks. |
| `kanban_ops.py` | Dispatcher and maintenance verbs for ``hermes kanban``: ``dispatch``, ``daemon`` (deprecated standalone loop), ``tail``/``watch`` event streaming, ``gc`` and ``repair``. |
| `kanban_output.py` | Text / ``--json`` output helpers shared by the ``hermes kanban`` CLI modules. |
| `kanban_owner_recovery.py` | Read-only canonical admission fences for dispatcher reclaim paths. |
| `kanban_parser.py` | Argparse tree for ``hermes kanban …`` (``build_parser``). |
| `kanban_pr_acceptance.py` | Exact-head GitHub acceptance for explicitly declared PR tasks. |
| `kanban_pr_acceptance_store.py` | Persist acceptance with the same ownership snapshot as the terminal write. |
| `kanban_resume_guard.py` | Centralized resume-time guard for Kanban-owned sessions (#68779) — the ONE place that decides whether a Kanban worker transcript may resume as an ordinary session. |
| `kanban_specify.py` | Kanban triage specifier — flesh out a one-liner into a real spec. |
| `kanban_swarm.py` | Kanban Swarm v1: thin swarm topology helpers on top of Kanban. |
| `kanban_transfer.py` | Kanban board export / import — move a whole board between machines. |
| `kanban_worker_client.py` | Dispatcher subprocess: submit one claim to its profile owner; never run an agent. |
| `kanban_worker_log.py` | Per-task worker log rotation, split out of ``hermes_cli.kanban_db_dispatch``. |
| `kanban_workflow.py` | Kanban board workflow: the one definition of board columns and manual moves. |
| `left_core_migration.py` | Move a home onto the catalog plugin of a feature that left core. |
| `lifecycle.py` | Hermes lifecycle dispatch for first-party observers and plugins. |
| `linux_desktop_entry.py` | Install and remove the Linux desktop entry (``<app_id>.desktop``). |
| `logs.py` | ``hermes logs`` — view and filter Hermes log files. |
| `loops.py` | Recurring in-session wakeups — the /loop command (Claude Code parity). |
| `macos_signing.py` | Managed interpreter identity, available before PM or application imports. |
| `macos_tcc_anchor.py` | Stable macOS TCC anchor for the uv-managed Python interpreter. |
| `main.py` | Hermes CLI - Main entry point. |
| `main_agent_cmds.py` | Agent-facing subcommand handlers: memory, acp, tools, insights, monitoring, skills (+trust). |
| `main_container.py` | NixOS container mode: route a ``hermes`` invocation into the managed container (``main()``). |
| `main_dashboard.py` | Dashboard/serve support: managed-service restart (systemd/respawn), status/listening probes, SSH session token file, named-profile routing, web-dist resolution, update stdio hangup protection. |
| `main_dep_hints.py` | Repair guidance for an unavailable declared dependency group. |
| `main_desktop.py` | Desktop (Electron) app: build/stamp, stage-and-swap pack, exe integrity gate, macOS signing, Linux sandbox, launch (hermes gui/desktop). |
| `main_desktop_apparmor.py` | Chromium's Linux sandbox under AppArmor's unprivileged-userns restriction (#130177). |
| `main_desktop_tcc.py` | ``hermes gui --setup-tcc-identity``: a persistent self-signed macOS code-signing identity. |
| `main_install_repair.py` | Update dependency diagnostics, historical markers and Windows launcher recovery. |
| `main_platform_setup.py` | Interactive messaging-platform setup wizards: WhatsApp (bridge + Cloud API), Slack manifest. |
| `main_profile_recovery.py` | Which commands may run in the default home when the sticky ``active_profile`` is gone. |
| `main_provider_setup.py` | Provider setup wizard helpers: provider picker, custom-provider save/remove, auxiliary-model routing menu, API-key/reasoning prompts, Anthropic OAuth. |
| `main_query_file.py` | ``--query-file``: the single-query transport that never passes through a shell. |
| `main_resume_args.py` | ``hermes chat`` resume-argument steps split out of ``hermes_cli.main``: ``--resume @claude/@codex`` imports, and recreating a removed ``--tui -w`` worktree a resumed session needs (N8). |
| `main_tui_launch.py` | TUI (ui-tui) launcher: prepared source builds and argv/env assembly. |
| `main_web_build.py` | Dashboard build freshness/serialization and checkout bytecode sweep. |
| `managed_scope.py` | Managed scope — IT-pushed, user-immutable config & env layer. |
| `managed_uv.py` | Shims to stop the old updater doing work until relaunch. |
| `mcp_catalog.py` | MCP catalog — curated, Nous-approved MCP servers shipped with the repo. |
| `mcp_config.py` | MCP Server Management CLI — ``hermes mcp`` subcommand. |
| `mcp_picker.py` | MCP picker — interactive `hermes mcp picker` (also the default `hermes mcp`). |
| `mcp_security.py` | Security checks for user-configured MCP server entries. |
| `mcp_startup.py` | Shared CLI/TUI-safe helpers for background MCP discovery. |
| `mem_trim.py` | Rate-limited heap release for long-lived Hermes gateway processes. |
| `memory_oauth.py` | HTTP routes for memory-provider OAuth connect, mounted by ``web_server``. |
| `memory_provider_migration.py` | Move a user from a memory provider that left core onto its catalog plugin. |
| `memory_setup.py` | hermes memory setup\|status — configure memory provider plugins. |
| `middleware.py` | Hermes middleware contract helpers. |
| `migrate.py` | CLI handlers for ``hermes migrate ...``. |
| `moa_cmd.py` | CLI helpers for configuring Mixture of Agents. |
| `moa_config.py` | Mixture-of-Agents configuration and slash-command helpers. |
| `model_catalog.py` | Remote model catalog fetcher. |
| `model_cost_guard.py` | Expensive-model confirmation helpers for model selection surfaces. |
| `model_data_policy_guard.py` | Data-policy confirmation helpers for model selection surfaces. |
| `model_normalize.py` | Per-provider model name normalization. |
| `model_picker_usage.py` | Plan-usage chrome for the model pickers (CLI radiolist and the gateway ``model.options`` inventory). |
| `model_search.py` | Picker-only search aliases for model ids. |
| `model_selection_guards.py` | Unified selection-time guard registry for model switching surfaces. |
| `model_setup.py` | Public helpers for a provider plugin's own ``hermes model`` step (``ProviderProfile.model_setup_flow``). |
| `model_setup_flows.py` | Per-provider model-selection wizard flows for ``hermes setup`` / ``hermes model``. |
| `model_setup_flows_azure.py` | Azure Foundry wizard (OpenAI-style or Anthropic-style transport, API-key or Entra ID auth). |
| `model_setup_flows_bedrock.py` | AWS Bedrock wizards: native Converse API (IAM chain, region-scoped model discovery) and the Bedrock API Key mode on the OpenAI-compatible bedrock-mantle endpoint. |
| `model_setup_flows_common.py` | Shared skeleton for the ``_model_flow_*`` wizards: banner, credentials, model list, picker, persist, confirmation — one copy of each step. Prompt strings and the config keys written (and their insertion order = config.y… |
| `model_setup_flows_custom.py` | Custom OpenAI-compatible endpoint wizards: the ad-hoc ``custom`` flow and the ``custom_providers`` / ``providers.<key>`` named-endpoint flow. |
| `model_setup_flows_local.py` | ``hermes model`` → Local models: the desktop's Local Models setup, in the terminal. |
| `model_switch.py` | Shared model-switching logic for the CLI and gateway /model commands. |
| `model_switch_providers.py` | Picker provider listing: credential discovery, curated/live model lists, row builders for list_authenticated_providers / list_picker_providers, and the parallel cache prefetch. |
| `models.py` | Provider/model catalogs: discovery, caching, and identity helpers. |
| `models_cache_lock.py` | Cross-process lock for ``provider_models_cache.json`` read-modify-write. |
| `models_catalog_static.py` | Static provider/model catalog tables (data only — no network). |
| `models_detect.py` | Live-catalog and credential guards for ``detect_provider_for_model``. |
| `models_local.py` | Local / self-hosted model servers. |
| `models_pricing.py` | Live model pricing. |
| `models_profile_cache.py` | Per-profile view of ``hermes_cli.models``' module-level catalog slots. |
| `models_reasoning_caps.py` | Per-model reasoning capabilities from OpenRouter-schema ``/v1/models`` catalogs. |
| `models_validate.py` | Validate a requested ``/model`` value against the active provider's catalog. |
| `nous_account.py` | Normalized Nous Portal account entitlement helpers. |
| `nous_auth_keepalive.py` | Background keepalive for long-lived Nous Portal sessions. |
| `nous_billing.py` | Nous Portal Remote Spending HTTP client. |
| `nous_subscription.py` | Helpers for Nous subscription managed-tool capabilities. |
| `npm_engine.py` | Stop an already-running old updater before its retired npm retry path. |
| `old_updater_deps.py` | Retired dependency hooks requested by already-running historical updaters. |
| `old_updater_main.py` | Frozen main.py imports for updater code still running after a checkout swap. |
| `onboarding_due.py` | The desktop's boot question, answered once: is onboarding due, and can something carry it. |
| `onboarding_run.py` | ``onboarding.run``: whether the desktop first-run onboarding opens on the next launch. |
| `onepassword_secrets_cli.py` | CLI handlers for ``hermes secrets onepassword ...``. |
| `oneshot.py` | Oneshot (-z) mode: send a prompt, get the final content block, exit. |
| `pairing.py` | CLI commands for the DM pairing system. |
| `partial_compress.py` | Boundary-aware partial compression — "summarize up to here". |
| `personality.py` | Single owner for personality overlays. |
| `pets.py` | CLI subcommand: ``hermes pets <subcommand>``. |
| `platform_actions.py` | Capability-gated platform action facade for plugins (#64176, action half). |
| `platforms.py` | Shared platform registry for Hermes Agent. |
| `plugin_capabilities.py` | Plugin capability declarations + consent state. |
| `plugin_catalog.py` | Plugin catalog — curated, Nous-approved Hermes plugins shipped with the repo. |
| `plugin_catalog_presence.py` | Whether the desktop app a catalog plugin drives is on this machine, before the plugin is installed. |
| `plugin_choices.py` | ``PluginContext.ask_choice``: a plugin slash command asks its user to pick one option. |
| `plugin_command_dispatch.py` | Compatibility-aware call boundary for plugin slash-command handlers. |
| `plugin_compat.py` | Frozen exports for ``hermes update`` processes that predate the plugin compat layer's removal. |
| `plugin_dev.py` | Runtime-backed validation behind ``hermes plugins doctor``: every manifest/import/registration check routes through the real runtime contracts instead of a parallel scanner. |
| `plugin_events.py` | Public event bridge for plugin backends (``plugin_api.py``, slash commands). |
| `plugin_host.py` | Parent side of the plugin host: one process per profile that runs its third-party plugins. |
| `plugin_host_child.py` | The plugin host process: imports third-party plugins and serves their callbacks to Hermes. |
| `plugin_host_http_auth.py` | Carry route-local admission over the private plugin-host channel, without credentials. |
| `plugin_host_profiles.py` | Model-provider plugins under ``plugins.isolation: host``. |
| `plugin_host_wire.py` | Wire format for the plugin host: framed JSON-RPC in both directions plus a value codec. |
| `plugin_install_phase.py` | The slow steps of a plugin install, as ids. A leaf module (stdlib only) so the gateway wire contract (``tui_gateway/contracts/connectors_operation.py``) can type them without importing the installer. |
| `plugin_isolation.py` | Where third-party Python plugin code is allowed to run (``plugins.isolation``). |
| `plugin_isolation_audit.py` | Static answer to "will this plugin run in the plugin host?" (``plugins.isolation: host``). |
| `plugin_messages.py` | ``PluginContext.post_message``: one message in the current conversation, editable in place. |
| `plugin_oauth.py` | OAuth clients a plugin declares in ``plugin.yaml``: Hermes signs in, stores and refreshes the grant. |
| `plugin_packs.py` | Plugin packs — declarative, shareable plugin sets. |
| `plugin_provider_requests.py` | Signed-in provider requests that core makes FOR plugins; the token never reaches plugin code. |
| `plugin_session.py` | The session a plugin hook or tool is running for, read from the turn's task-local context. |
| `plugin_validate.py` | ``hermes plugins validate`` — admission checks for a plugin directory. |
| `plugin_validate_core_override.py` | Admission lint: a catalog plugin must not rebind Hermes core at runtime. |
| `plugin_validate_desktop.py` | Static admission lint for a plugin's Desktop surface (``plugin.js`` / ``desktop/plugin.js``). |
| `plugin_validate_locales.py` | ``hermes plugins validate`` — language-pack checks (``provides_locales``). |
| `plugin_validate_private_imports.py` | Admission lint: name a plugin's imports of private Hermes core modules (a warning, never a refusal). |
| `plugins.py` | Hermes Plugin System — discovers, loads, and manages plugins. |
| `plugins_activation.py` | Mid-run plugin activation: what a just-loaded plugin does NOW vs next session (#87770). |
| `plugins_activation_live.py` | Make an installed plugin's MCP servers and skills usable in THIS process now (#87770 follow-up). |
| `plugins_admission.py` | Submit proposed plugin selections to the independent PM publisher. |
| `plugins_aux_tasks.py` | Validation and entry shape for ``PluginContext.register_auxiliary_task``. |
| `plugins_cadence.py` | The plugin update-check cadence: read-only, receipt-surfaced. |
| `plugins_capability_ctx.py` | Capability-gated ``PluginContext`` surface: ``has_capability`` probing and ``side_question`` (ask the session's own agent after a turn, ``llm.side_question``). |
| `plugins_cmd.py` | ``hermes plugins`` CLI subcommand — install, update, remove, and list plugins. |
| `plugins_cmd_capabilities.py` | Capability consent (#64228): declared-vs-granted reads, the consent screen, ``hermes plugins capabilities`` and the legacy ``allow_tool_override`` grant. |
| `plugins_cmd_catalog.py` | ``hermes plugins`` catalog surface: resolution, provenance sidecar, search/browse/info/validate, catalog-aware update, plus the dashboard/TUI-facing catalog payload helpers. |
| `plugins_cmd_git.py` | Plugin install metadata (``.install-metadata.json`` source/revision/pin records) and the git plumbing behind clone, exact-revision checkout, credential scrubbing and the autostashing ``git pull``. |
| `plugins_cmd_inspect.py` | Read-only inspection of a plugin source before install: which halves (agent, desktop) it ships. |
| `plugins_cmd_install.py` | ``hermes plugins install``: dependency/env consent, the atomic clone-scan-publish installer core, and the dashboard/TUI non-interactive install. |
| `plugins_cmd_listing.py` | Read-only presentation: ``hermes plugins list``, ``show`` and ``compat``. |
| `plugins_cmd_remove.py` | ``hermes plugins remove``: tree + install-metadata removal kept consistent, config bookkeeping, and the dashboard/TUI remove path. |
| `plugins_cmd_toggle.py` | The interactive ``hermes plugins`` composite UI: general-plugin checkboxes (saved through the one admission authority) and the memory-provider / context-engine category pickers. |
| `plugins_cmd_update.py` | ``hermes plugins update`` plus the provenance verbs around it: ``adopt``, ``trust-update-url`` and the read-only ``check-updates``; the dashboard update path shares the same pull/re-clone core. |
| `plugins_cmd_update_all.py` | ``hermes plugins update`` with no name: update every installed plugin that has an update. |
| `plugins_content.py` | Content registrars on ``PluginContext``: plugin skills and Automation Blueprints. |
| `plugins_discovery.py` | Plugin discovery: directory scanning, entry-point manifests, and the enable/disable gate. |
| `plugins_dispatch.py` | Plugin hook / middleware / event-bus / system-prompt-section dispatch. |
| `plugins_injection.py` | Host routing for ``PluginContext.inject_message``: classic CLI REPL, Ink TUI / desktop, messaging gateway (existing ``session_key`` or a new session at ``origin``). |
| `plugins_ledger.py` | Registration ownership ledger and unload: every plugin registration is recorded with its inverse so force reload / targeted unload unwind registries in reverse order. Mixed into :class:`hermes_cli.plugins.PluginManager`. |
| `plugins_loader.py` | Plugin loading: directory/entry-point module import, deferred bundled platforms, portable packages, dependency/config-schema warnings. Mixed into :class:`hermes_cli.plugins.PluginManager`. |
| `plugins_manifest.py` | Plugin manifest model and parsing (``plugin.yaml`` v1/v2, portable ``plugin.json``). |
| `plugins_provenance.py` | Plugin provenance: the 2x2 reconciliation of install metadata. |
| `plugins_registrars.py` | The ``register_<category>_provider`` table behind :class:`hermes_cli.plugins.PluginContext`. |
| `plugins_settings.py` | Plugin-declared settings fields for the Desktop/TUI Plugins hub (#46600, #87934). |
| `plugins_state.py` | Plugin-owned durable state and namespaced settings helpers (split out of hermes_cli.plugins). |
| `plugins_transaction.py` | Publish plugin code and its dependency selection through one recoverable handoff. |
| `plugins_updates.py` | Plugin update checks — the standard, read-only 'is it outdated?' verb. |
| `portal_cli.py` | ``hermes portal`` — the human-readable entry point for Nous Portal. |
| `post_update.py` | Home maintenance shared by explicit updates and bounded boot maintenance. |
| `process_identity.py` | Process identity: spawn tags, the machine-wide spawn ledger, and the Windows job-object self-attach. |
| `profile_channels.py` | Messaging-channel settings a profile clone must NOT inherit. |
| `profile_cmd.py` | ``hermes profile`` command — one handler per action, dispatched by ``PROFILE_ACTIONS``. |
| `profile_describer.py` | Profile describer — auto-generate ``description`` for a profile. |
| `profile_distribution.py` | Profile distributions — shareable, packaged Hermes profiles via git. |
| `profile_identity.py` | Rekey a renamed profile's durable identity (#111926), and purge a deleted profile's (#112727). |
| `profile_memory_config.py` | Carry the ACTIVE memory provider's own config into a ``--clone`` (#120115). |
| `profile_model_seed.py` | Copy the model and its selected custom endpoint into a new profile, and merge that endpoint over same-identity entries the new profile already has. |
| `profiles.py` | Profile management for multiple isolated Hermes instances. |
| `profiles_cache.py` | The per-profile derived-value cache behind ``list_profiles`` (``hermes_cli.profiles``). |
| `profiles_config.py` | Migrate a new profile's copied config document (``hermes_cli.profiles`` creation helper). |
| `profiles_honcho.py` | Honcho host-block migration for ``hermes profile rename``. |
| `profiles_initialization.py` | Initial profile files, written on the staging tree before publication. |
| `profiles_remove.py` | Profile directory removal: wait out the live owner, then rmtree with a short retry. |
| `profiles_service_cleanup.py` | Profile delete/rename: remove the OLD name's supervisor registrations that live outside the user systemd / launchd arms in ``profiles._cleanup_gateway_service``. |
| `projects_cmd.py` | ``hermes project`` CLI — manage first-class, multi-folder Projects. |
| `projects_db.py` | Per-profile first-class Project store. |
| `prompt_size.py` | Prompt-size diagnostic: ``hermes prompt-size``. |
| `prompt_stash.py` | Ctrl+S prompt stash — pure state machine for the classic CLI composer. |
| `provider_catalog.py` | Unified provider catalog — one source of truth for the provider universe. |
| `providers.py` | Single source of truth for provider identity in Hermes Agent. |
| `proxy_cli.py` | CLI handlers for ``hermes egress ...``. |
| `prune_advisor.py` | Low-disk prompt for ``sessions.auto_prune`` (off by default). |
| `psutil_android.py` | Shims to stop the old updater doing work until relaunch, not Android support. |
| `pt_input_extras.py` | Augmentations to prompt_toolkit's input-parsing tables. |
| `pty_bridge.py` | PTY bridge for `hermes dashboard` chat tab. |
| `pty_session.py` | Keep-alive PTY sessions for dashboard terminals. |
| `quiet_single_query.py` | Quiet ``hermes chat -Q`` helpers: bind this session's key and resume nested notifies. |
| `relaunch.py` | Unified self-relaunch for Hermes CLI: preserves inherited flags (--tui, --dev, --profile, --model…) across process replacement so ``hermes sessions browse`` / post-setup relaunch keep the user's mode. |
| `relay_plugin_cutover.py` | Shared migration guards for Hermes' native NeMo Relay ownership. |
| `relay_plugin_migrate.py` | Migrate legacy ``HERMES_NEMO_RELAY_ATIF_*`` / ``ATOF_*`` exporter vars into a Relay ``plugins.toml``. |
| `release_channels.py` | R2 channel wire protocol. Names are data; no local channel registry exists. |
| `resource_limits.py` | Best-effort process resource-limit adjustments for long-running services. |
| `route_identity.py` | Fail-closed URL identity normalization for model/provider routes. |
| `runtime_paths.py` | Frozen updater surface: pre-PM updaters import these names from here. |
| `runtime_provider.py` | Shared runtime provider resolution for CLI, gateway, cron, and helpers: the resolution ORDER (:func:`resolve_runtime_provider`), api_mode / base_url helpers and the pool / OAuth / explicit paths. Custom-provider lookup… |
| `runtime_provider_backends.py` | Provider-specific runtime builders for :mod:`hermes_cli.runtime_provider`: Azure Foundry, the OpenRouter / bare-custom fallback resolver, Bedrock, and external-process providers. Origin-internal collaborators are resolv… |
| `runtime_provider_custom.py` | Custom-provider resolution: ``providers:`` / ``custom_providers:`` lookup, identity recovery, custom credential pools, and the named-custom runtime builder. Extracted from :mod:`hermes_cli.runtime_provider`; origin-inte… |
| `runtime_readiness.py` | Provider readiness probe for the session authority's ``setup.runtime_check``. |
| `runtime_state.py` | Stdlib-only recovery and lifetime protection for dependency generations. |
| `sandbox_image_switch.py` | Approval gate for the default sandbox image change (nikolaik base → hermes-sandbox:desktop). |
| `secret_prompt.py` | Secret input prompts with masked typing feedback. |
| `secrets_cli.py` | CLI handlers for ``hermes secrets bitwarden ...``. |
| `security_advisories.py` | Security advisory checker for Hermes Agent. |
| `security_audit.py` | On-demand supply-chain audit for Hermes Agent installs. |
| `security_audit_startup.py` | Startup security posture audit (warn-on-load, never blocks). |
| `send_cmd.py` | CLI subcommand: ``hermes send`` — pipe text from shell scripts to any configured messaging platform (Telegram, Discord, Slack, Signal, SMS, etc.). |
| `service_manager.py` | Abstract service manager interface + systemd/launchd/Windows/s6 backends. |
| `session_export.py` | Shared renderers for session export commands. |
| `session_export_html.py` | Standalone single-file HTML export (single or multi-session with sidebar); no remote deps. |
| `session_export_md.py` | Markdown/QMD export helpers for Hermes sessions. |
| `session_filters.py` | Shared time/filter parsing for `hermes sessions prune` / `archive`. |
| `session_listing.py` | Shared session-listing helpers for CLI and gateway slash surfaces. |
| `session_lost_and_found.py` | Last-resort page-level salvage for an unreadable session database schema, via the sqlite3 shell's ``.recover`` (rows it cannot attribute to a schema land in ``lost_and_found`` tables: ``rootpgno, pgno, nfield, id, c0..c… |
| `session_recap.py` | Session recap — summarize the current session from in-memory history. Pure local computation: no LLM call, no auxiliary model, no prompt-cache invalidation. A recap should be instant and free. |
| `session_recovery.py` | Offline, non-destructive recovery for a damaged Hermes session database. |
| `session_reset_retirement.py` | Point configs that still declare an idle/daily ``session_reset`` at the plugin that restores it. |
| `session_schema_history.py` | Physical column history of the state.db tables the page-level salvage lane maps. |
| `sessions_adopt.py` | ``hermes sessions adopt``: bring this profile's pre-gateway history under its gateway, as the host. |
| `sessions_cmd.py` | ``hermes sessions`` command. |
| `sessions_cmd_browse.py` | Interactive picker for ``hermes sessions browse``: curses UI with live search filtering and ``d`` delete-with-confirmation; numbered-list fallback when curses is unavailable (Windows, etc.). |
| `sessions_cmd_journal_mode.py` | `hermes sessions set-journal-mode delete\|wal` — the offline self-service path for #100896. |
| `sessions_cmd_repair_profiles.py` | ``hermes sessions repair-profiles`` — the CLI face of :mod:`hermes_cli.sessions_repair_profiles`. |
| `sessions_discard.py` | ``hermes sessions discard``: acknowledge a turn lost across a gateway crash, without a REPL. |
| `sessions_owner.py` | Bulk prune while the gateway is up: the owner applies it, this process never writes. |
| `sessions_repair_profiles.py` | ``hermes sessions repair-profiles`` — settle crossed-profile durable state across every store. |
| `setup.py` | Interactive setup wizard for Hermes Agent (config lives in ~/.hermes/). |
| `setup_agent_import.py` | First-time ``hermes setup``'s "Coming from another agent?" step (it replaces core's old OpenClaw migration offer). |
| `setup_hidden_env.py` | Which platform env vars the setup surfaces hide. |
| `setup_migration.py` | Post-import section-skip logic: after ``hermes setup`` imported another agent's settings, each section that is already configured shows its summary and offers to skip (setup.py re-exports the names it uses; setup helper… |
| `setup_platforms.py` | Messaging-platform setup wizards (Telegram, webhooks) and the ``hermes setup gateway`` flow. setup.py re-exports the public names, and tests monkeypatch prompt/print/env helpers on hermes_cli.setup, so those are importe… |
| `setup_quick.py` | Streamlined setup flows: the Nous Portal one-shot (`hermes portal`), first-time quick setup, Blank Slate setup and the `--quick` missing-items pass. Names from setup.py are imported lazily per function so test patches o… |
| `setup_summary.py` | Setup-completion summary (tool availability + "Setup Complete!" banner). setup.py names are resolved through the module object so test patches on ``hermes_cli.setup.<name>`` take effect. |
| `setup_terminal.py` | Terminal-backend setup wizard (local/docker/modal/daytona/vercel/ssh/plugin). setup.py names are resolved through the module object so test patches on ``hermes_cli.setup.<name>`` take effect; setup.py re-exports the pub… |
| `setup_tts.py` | Text-to-speech provider setup (provider picker, API-key prompts, local engine installs, xAI OAuth). setup.py names are resolved through the module object so test patches on ``hermes_cli.setup.<name>`` take effect; setup… |
| `shared_profile_warning.py` | Advisory only: simultaneous installs share profile data, not ownership. |
| `shared_session_attach.py` | Discover a cooperative local runtime without taking its session lease. |
| `sizefmt.py` | Small shared size-formatting helpers for CLI/agent output (sibling of ``hermes_cli.timefmt``: a tiny purpose-named module lightweight consumers can import without the CLI surface). |
| `skills_config.py` | Skills configuration for Hermes Agent. `hermes skills` enters this module. |
| `skills_hub.py` | Skills Hub CLI — Unified interface for the Hermes Skills Hub. |
| `skin_cmd.py` | ``hermes skin`` — list, switch, and tweak skins from the CLI. |
| `skin_engine.py` | Hermes skin/theme engine — the theme SDK for every surface. |
| `slack_cli.py` | ``hermes slack manifest`` — generate the Slack app manifest JSON that registers every gateway command as a native Slack slash (``/btw``, ``/stop``, ``/model``, …). |
| `slash_exec.py` | Registry-owned slash command execution (thin slice). |
| `source_build.py` | Source launch/update composition over the shared JavaScript builders. |
| `source_check.py` | Passive source update decisions for one exact installation and profile. |
| `source_completion.py` | The tail every source install and update shares. |
| `source_releases.py` | Resolve promoted source releases, never infer publication from a Git tag. |
| `source_stamp.py` | Atomically publish identity for a mutable source checkout. |
| `sqlite_runtime.py` | Import-safe helpers for inspecting a Python interpreter's linked SQLite. |
| `sqlite_safe_read.py` | Lock-safe inspection of SQLite database files. |
| `sqlite_util.py` | Shared SQLite primitives for the small per-profile / board stores. |
| `ssh_workspace_fs.py` | Filesystem adapter for Desktop workspaces executed over SSH. |
| `staged_uploads.py` | Browser uploads staged in a profile home, and the receipt ``file.attach`` redeems. |
| `stale_modules.py` | Heal mixed ``sys.modules`` after an in-place checkout update. |
| `status.py` | Status command for hermes CLI. |
| `status_auth.py` | Credential sections of `hermes status`, run through ``status._SECTIONS`` with its shared context. Origin helpers (``_row``, ``_first_env_value``, ...) are resolved through the ``hermes_cli.status`` module object so test… |
| `status_bar_git.py` | Current git branch for the CLI status bar. |
| `status_report.py` | The one field set behind ``/status`` on every surface. |
| `stderr_timestamp.py` | Run a child process while prefixing each stdout and stderr line with a timestamp. |
| `stdio.py` | Windows-safe stdio configuration. |
| `steward.py` | Steward classification and refusal text for sealed install trees. |
| `stream_json.py` | ``hermes chat -q … --format stream-json``: one JSON object per stdout line. |
| `suggestions_cmd.py` | Shared ``/suggestions`` command logic for CLI and gateway. |
| `telegram_managed_bot.py` | Telegram Managed Bot onboarding client: creates a user-owned child bot via the Nous onboarding service (no BotFather copy-paste); the raw Telegram token is saved locally after one retrieval. |
| `terminal_breadcrumbs.py` | Per-terminal session breadcrumbs for ``hermes -c`` / ``--continue``. Strictly best-effort: no function raises; without a stable terminal identity (no tty, no known multiplexer env var) ``-c`` falls back to latest-sessio… |
| `terminal_notify.py` | Terminal-native desktop notifications: OSC 9 and Warp's OSC 777 CLI-agent protocol. |
| `timefmt.py` | Small shared time-formatting helpers for CLI output. |
| `timeouts.py` | Defines `_coerce_timeout`, `_configured_timeout`, `get_provider_request_timeout`, `get_provider_stale_timeout`, `_get_model_config` |
| `tips.py` | Random tips shown at CLI session start to help users discover features. |
| `tool_availability_notices.py` | Startup notice lines for toolsets that are switched off because their requirements are not met. |
| `tools_config.py` | Unified tool configuration for Hermes Agent. |
| `tools_config_cua.py` | PM-backed CUA setup and the host integration not supplied by its binary archive. |
| `tools_config_mcp.py` | MCP tool checklists and the non-interactive ``hermes tools enable\|disable\|list`` command. |
| `tools_config_post_setup.py` | Post-setup install hooks and installed-state predicates for `hermes tools` provider rows. |
| `tools_config_providers.py` | Provider rows, active-provider detection, model pickers and provider-selection persistence for `hermes tools`. |
| `toolset_scope.py` | Platform scope rules for configured toolsets. |
| `toolset_validation.py` | Validation for the ``platform_toolsets`` config section. |
| `tui_worktree_resume.py` | Bring back a ``hermes --tui -w`` worktree a resume needs (N8). |
| `turn_exit.py` | Turn-result exit policy shared by CLI views and authority-owned workers. |
| `ui_preferences.py` | Machine-level Desktop/Webapp UI preferences (#145213). |
| `uninstall.py` | Hermes Agent Uninstaller. |
| `update_abort_recovery.py` | Fresh-process recovery after the update's in-process restart phase aborts. Separate owner from ``update_cmd``: its own vocabulary (``verified`` / ``relaunch_attempted`` / ``failed``, serve units, survivors) and its own… |
| `update_channel.py` | Per-install update-channel records. |
| `update_cmd.py` | Hermes update pipeline: dispatchers (``_cmd_update_impl``/``_cmd_update_check``) + git plumbing. |
| `update_cmd_check.py` | Steps of ``hermes update --check``: debris cleanup, channel target, scoped fetch, verdict. |
| `update_cmd_commit.py` | The single commit point of a source ``hermes update``: everything the tree move needs armed first. |
| `update_cmd_common.py` | Shared leaf helpers for the ``hermes update`` modules (no Hermes imports; no cycle). |
| `update_cmd_config.py` | Post-``hermes update`` config-schema migration for the active profile and every sibling. Names are re-imported by ``update_cmd`` (``hermes_cli.update_cmd.<name>`` resolves/monkeypatches); origin helpers are imported laz… |
| `update_cmd_drain_report.py` | Name what a draining gateway is waiting on while ``hermes update`` blocks on it. |
| `update_cmd_fleet.py` | Gateway fleet restart + post-update verification for ``hermes update``. |
| `update_cmd_fleet_checkout.py` | Checkout ancestry for the update-restart obligation (``update_cmd_fleet`` sibling). |
| `update_cmd_fleet_gatewayless.py` | Gateway-less host evidence for the update-restart obligation (``update_cmd_fleet`` sibling). |
| `update_cmd_fleet_unit_budget.py` | systemd unit timing budgets for the update's gateway restarts (``update_cmd_fleet`` sibling). |
| `update_cmd_fleet_verify.py` | Post-restart fleet verification for ``hermes update`` (``update_cmd_fleet`` sibling). |
| `update_cmd_git.py` | Git plumbing for ``hermes update``: fork/upstream sync, trampoline-git detection, lockfile/EOL churn cleanup, orphan rescue refs, parked-branch assessment, fetch-failure classification. |
| `update_cmd_maint.py` | Post-update maintenance for ``hermes update``: pre-update backup snapshot, state-db verify/restore, curator/FTS notices, FHS path guard, completion summary. |
| `update_cmd_pause_gate.py` | The paused gateways' tree gate for the update's checkout-writing steps (Windows pause, #132338). |
| `update_cmd_posix_pause.py` | Pre-swap gateway pause for ``hermes update`` on Linux and macOS. |
| `update_cmd_stale_survivors.py` | Post-update escalation for gateways the fleet matrix proved stale. |
| `update_cmd_stash.py` | Autostash handling for ``hermes update``: stash before the pull, restore/park/discard afterwards, warn about orphans. |
| `update_cmd_validation.py` | Source import-integrity checks for update and stash restoration. |
| `update_cmd_windows.py` | Windows gateway lifecycle for ``hermes update``: pause/resume/cold-start the service, sweep venv holders, reap orphaned backends. |
| `update_cmd_zip.py` | ZIP-download fallback for ``hermes update`` (Windows with broken git): two-phase stage/commit swap, dirty-tree guard. |
| `update_completion.py` | Fresh-checkout source update completion and its stdlib-only parent transport. |
| `update_contract.py` | Image-managed install refusal contract. |
| `update_custody.py` | Checkout custody for the updater's children (R2): the ONE spawn policy for every git (and the Node build) an update starts. |
| `update_downgrade_guard.py` | Refuse an update whose target predates the gateway runtime while a state.db already depends on it. |
| `update_finish.py` | Post-checkout completion shared by current and historical update callers. |
| `update_fleet_scope.py` | Home scoping for ``hermes update``'s fleet restart (#93349). |
| `update_handoff.py` | Frozen compat surface for releases that finish `hermes update` via the post-swap hand-off. |
| `update_host_obligation.py` | Host-scoped update→restart obligation for ``hermes update``. |
| `update_inventory.py` | Runtime inventory + update plan for the fleet-update pipeline. |
| `update_lock.py` | Cross-process mutual exclusion for in-flight Hermes updates. |
| `update_owning_install.py` | Send ``hermes update`` back to the install whose interpreter it is running on. |
| `update_pause_record.py` | Durable record of the gateways and services ``hermes update`` paused on Windows. |
| `update_proxy_env.py` | Undo the system proxy the Desktop handed to an update's children. |
| `update_receipt.py` | Structured update receipts + post-update fleet version verification. |
| `update_restart_recovery.py` | Restart supervised gateway profiles from a clean Python generation. |
| `update_serve_obligations.py` | Durable serve/dashboard restart reminders (manual serves, and unit-owned ones the update could not restart), independent of gateway restart receipts. |
| `update_serve_resume.py` | Fresh-process adapter for manual backends paused by historical updaters. |
| `update_stage.py` | Stage updates to a desktop hand-off UI, if one is watching. |
| `update_windows_acl.py` | ``hermes update``'s owed ``windows_home_acl`` step: after an elevated update, give the same user back access to the home tree that run may have left Administrators-only (#139870, #134889 W8). Split from ``update_cmd_mai… |
| `url_utils.py` | Small helpers for composing URLs from configured network hosts. |
| `urllib_security.py` | Security policy for credential-bearing stdlib urllib requests. |
| `vault.py` | ``hermes vault`` — manage the local encrypted autofill vault. |
| `venv_sync.py` | Pre-venv entry point for PM's dependency transaction. |
| `vercel_auth.py` | Helpers for reporting Vercel Sandbox authentication state. |
| `verify_cmd.py` | ``hermes verify`` — detect a project's run recipe and smoke-test it. |
| `version_info.py` | Canonical runtime identity for Hermes. |
| `voice.py` | Process-wide voice recording + TTS API for the TUI gateway. |
| `web_asset_mime_types.py` | MIME types for served web assets, normalised in the serving layer. |
| `web_build_limits.py` | Web UI build resource caps (issue #63338). |
| `web_deps.py` | Late-binding dependency seam for extracted dashboard routers. |
| `web_git.py` | Backend git operations for the desktop coding rail + review pane. |
| `web_host_terminal.py` | Host-terminal policy and process setup for the browser-hosted Desktop UI. |
| `web_host_terminal_sessions.py` | Process-lifetime host shells, owned by Webapp identity and profile home. |
| `web_models.py` | Pydantic request/response models for the Hermes dashboard web server. |
| `web_read_coalescing.py` | Coalesce concurrent synchronous HTTP reads before threadpool admission. |
| `web_server.py` | Hermes Agent — Web UI server: FastAPI app assembly, auth/host middleware, ``start_server``. |
| `web_server_app.py` | HTTP lifespan composition; standalone backend services remain opt-in owners. |
| `web_server_boundary.py` | Listener boundary primitives shared by the dashboard app and the gateway's session listener: Host validation, the auth-gate decision and the native WebSocket ticket subprotocol. |
| `web_server_chat.py` | Chat/terminal WebSocket plumbing: PTY bridge selection and registry, WS client/origin/auth gates, chat argv resolution, gateway/sidecar URL building. |
| `web_server_config.py` | Dashboard config schema and model-assignment logic: CONFIG_SCHEMA construction, dynamic provider options, web<->config normalisation, main/aux model assignment. |
| `web_server_cron.py` | Dashboard cron helpers: per-profile scheduler I/O, job validation/normalisation, cron fire and gateway forwarding. |
| `web_server_dashboard.py` | Dashboard UI assets: SPA mount, theme normalisation/bootstrap CSS, dashboard-plugin discovery and the plugins-hub merge. |
| `web_server_file_response.py` | Range responses over a descriptor opened under the file ticket's profile lease. |
| `web_server_file_tickets.py` | Path-bound tickets for browser file URLs (``/api/fs/download``, ``/api/files/stream``). |
| `web_server_files.py` | Managed-files policy for the dashboard file browser: root resolution, path containment, entry metadata. |
| `web_server_gateway.py` | Gateway/process helpers for the dashboard: per-profile gateway topology (+cache), action subprocess spawning, gateway restart plumbing, system platform display. |
| `web_server_idle_exit.py` | Idle-exit for Desktop-owned ``hermes serve --isolated`` backends reached over SSH (#101626). |
| `web_server_idle_proof.py` | Diagnostic work snapshot for a Desktop-pooled ``hermes serve`` child. |
| `web_server_lifecycle.py` | Serve-process lifecycle: parent death watchdog, port-conflict preflight, READY announcement, browser open, trusted proxies. |
| `web_server_mcp.py` | MCP dashboard helpers: create-payload normalisation, env redaction/summary, dashboard-driven MCP OAuth worker. |
| `web_server_memory.py` | Memory-provider dashboard helpers: manifest/schema loading, setup-env and dependency probes, configured-status discovery. |
| `web_server_messaging.py` | Messaging-platform catalog and onboarding helpers: platform overrides/env discovery, WhatsApp and Telegram onboarding state. |
| `web_server_oauth.py` | Dashboard OAuth/login-status helpers: provider catalog, per-provider device pollers, Anthropic/Claude-Code status probes, and the poller for provider-profile device logins. |
| `web_server_owner_exit.py` | Supersession retirement for Desktop-owned ``hermes serve --isolated`` backends reached over SSH. |
| `web_server_plugin_profiles.py` | Dashboard plugins of a secondary served profile (PLG-3, #134889). |
| `web_server_profiles.py` | Profile-scoped helpers: profile discovery fallback, profile dir/MCP-server writes, the profile/config scope context managers, skills-hub and tools/analytics catalog helpers. |
| `web_server_remote_media.py` | Inline audio/video from a profile's SSH workspace for ``/api/files/stream``. |
| `web_server_session_token.py` | The dashboard session token: where its value comes from. |
| `web_server_sessions.py` | Read-only session browsing, latest-descendant lookup and owner maintenance. |
| `web_server_skew_exit.py` | Code-skew retirement for Desktop-owned ``hermes serve --isolated`` backends reached over SSH. |
| `web_server_static_assets.py` | Static asset lookups the SPA catch-all must not answer with ``index.html``. |
| `web_server_surface.py` | What each launch surface of the one web-server stack may do. |
| `web_session_sockets.py` | Browser sockets the dashboard session token opens, and how they end when it is replaced. |
| `web_upload_limit.py` | Bound chat upload request bodies before FastAPI parses, spools or buffers them. |
| `web_whatsapp_session.py` | Preserve WhatsApp authentication state before dashboard re-pairing. |
| `webapp.py` | Build and launch plumbing for the browser-hosted Desktop workspace. |
| `webapp_access.py` | Remote access to the gateway-served Webapp, for Desktop's Web Access pane. |
| `webapp_launcher.py` | ``hermes webapp``: open the browser-hosted Desktop that the gateway serves. |
| `webapp_page_policy.py` | CSP for the browser-hosted Desktop, independently of its preview documents. |
| `webapp_previews.py` | Credential-free preview assets: private HTML crosses only a parent/frame message. |
| `webapp_sign_in.py` | Behind the sign-in gate, a Webapp login lasts only while the browser credential it is bound to does. |
| `webhook.py` | hermes webhook — manage dynamic webhook subscriptions from the CLI. |
| `welcome_trial.py` | The desktop's welcome trial: free inference on ``nous/welcome`` for a first install, once per OS user. |
| `win_pty_bridge.py` | Windows ConPTY bridge for the `hermes dashboard` chat tab. |
| `windows_appinstaller_update.py` | Check for an App Installer update for the running MSIX package. |
| `windows_ssh_runtime.py` | Native Windows trust boundary for Desktop SSH backend lifecycle. |
| `windows_store_update.py` | Run a Store check, download, or install with the packaged interpreter. |
| `worktree_archive.py` | Restorable snapshots of git worktrees: ``refs/hermes/archive/<tree>``. |
| `worktree_cmd.py` | ``hermes worktree`` — audit (``list [--json] [--older-than DAYS]``), reclaim (``prune [--dry-run] [--json] [--older-than DAYS] [--trees-only \| --branches-only]``) and ``restore <name> [--path DIR]`` accumulated git wor… |
| `worktree_exit.py` | The keep / archive / discard question when an interactive ``hermes -w`` session exits with a dirty or unpushed worktree. |
| `worktree_gc.py` | On-demand worktree + branch reclaim (``hermes worktree`` / ``/worktree prune``). |
| `worktree_ops.py` | Git worktree isolation for ``hermes -w`` sessions: create, classify, prune. |
| `worktree_registry.py` | Per-profile registry of every repository Hermes has created a worktree in. |
| `worktree_retention.py` | What a worktree holds that neither git nor an archive can bring back. |
| `worktree_sweep.py` | Snapshot-then-delete sweep for stale worktrees (``worktrees.archive_dirty``, default on). |
| `write_approval_commands.py` | Shared handlers for the /memory and /skills write-approval subcommands. |
| `xai_retirement.py` | Detect xAI models retired on May 15, 2026 and migrate config.yaml references. |

## `hermes_cli/dashboard_auth/`

| File | What it does |
|---|---|
| `__init__.py` | Dashboard authentication provider framework. The auth gate engages only when the dashboard binds to a non-loopback host without ``--insecure``; every request must then carry a verified session from a registered ``Dashbo… |
| `audit.py` | Audit log for dashboard-auth events: ``$HERMES_HOME/logs/dashboard-auth.log``, one JSON object per line. Token-like fields are stripped before serialisation so refresh tokens / JWTs never reach disk. Minimal import surf… |
| `base.py` | Abstract base + dataclasses + exceptions for dashboard auth providers. |
| `body_limit.py` | Bound public auth bodies before FastAPI assembles JSON for validation. |
| `cookies.py` | Cookie helpers for dashboard auth. |
| `listener_client.py` | The Nous Portal client the listener this process serves signs in with instead of the configured one. |
| `login_page.py` | Server-rendered /login page (no React, no SPA bundle, no injected token). |
| `middleware.py` | Auth-gate middleware for the dashboard. |
| `native_flow.py` | Gateway-brokered RFC 8252 (OAuth 2.0 for Native Apps) authorization store. |
| `native_http.py` | Same-user private bootstrap at the existing HTTP authentication boundary. |
| `prefix.py` | X-Forwarded-Prefix and public-URL resolution for reverse-proxied deploys. |
| `public_paths.py` | Shared allowlist of ``/api/*`` paths that bypass dashboard auth. Imported by BOTH gates — ``web_server.auth_middleware`` (loopback / ``--insecure``) and ``dashboard_auth.middleware.gated_auth_middleware`` (OAuth cookie)… |
| `refresh_singleflight.py` | Single-flight + short replay cache for rotating refresh tokens (both refresh paths). |
| `registry.py` | Module-level registry for DashboardAuthProvider instances. Plugins call ``register_provider`` via the plugin context hook at startup; the auth gate iterates ``list_providers()`` and uses ``get_provider`` to dispatch on… |
| `request_utils.py` | Request-level helpers shared by the auth routes and both middlewares. |
| `routes.py` | HTTP routes for the dashboard-auth OAuth round trip. |
| `token_auth.py` | Route-agnostic non-interactive (bearer-token) auth seam for the dashboard. |
| `ws_tickets.py` | WS-upgrade auth credentials for gated mode. |

## `hermes_cli/local_runtime/`

| File | What it does |
|---|---|
| `__init__.py` | Managed llama.cpp runtime. |
| `binaries.py` | Hardware selection for PM-owned llama.cpp binaries; mutable runtime state stays separate. |
| `bootstrap.py` | Bootstrap for the managed runtime: config -> installed binaries -> running supervised server. |
| `capabilities.py` | Capability answers for models served by the managed runtime. |
| `catalog.json` | JSON object with keys `schema_version`, `models` |
| `catalog.py` | Curated starter catalog for the managed local runtime. |
| `context_policy.py` | Context policy — the window ladder for managed local models. |
| `detect.py` | Detection of running llama-server instances. |
| `devices.py` | Ask the installed llama.cpp build which accelerators it sees, in a disposable process. |
| `endpoint.py` | Endpoint resolution for llamacpp-alias requests (provider integration). |
| `estimator.py` | Per-layer context-memory estimator + physics check. |
| `gguf.py` | GGUF metadata + tensor-table reader (stdlib only). |
| `growth.py` | In-session context growth for the managed llama.cpp runtime. |
| `hardware.py` | Live hardware budget probe. |
| `hf_browse.py` | Browse Hugging Face for GGUF models the user can run. |
| `load_progress.py` | Live model-load progress from the managed llama-server router. |
| `presets.py` | Per-model preset generation (--models-preset INI) — the router-side carrier for context-policy launch decisions. |
| `processes.py` | Contain each managed Windows router tree without adopting the owner process. |
| `recovery.py` | Conservative recovery of the one router recorded by this managed runtime. |
| `supervisor.py` | Supervision of one llama-server in router mode. |

## `hermes_cli/observability/`

| File | What it does |
|---|---|
| `__init__.py` | First-party Hermes observability integrations. |
| `relay_shared_metrics.py` | Direct NeMo Relay integration for Hermes shared client metrics. |
| `schemas/hermes.shared_metrics.v1.schema.json` | Hermes Shared Metrics Package v1 |
| `schemas/hermes.shared_metrics.v2.schema.json` | Hermes Shared Metrics Package v2 |
| `schemas/hermes.shared_metrics.v3.schema.json` | JSON data/configuration |
| `schemas/hermes.shared_metrics.v4.schema.json` | JSON data/configuration |
| `shared_metrics.py` | Durable aggregation and local export for Hermes shared metrics. |
| `shared_metrics_catalog.py` | Public-name catalogs for shared metrics: the only non-enum names a package may carry. |
| `shared_metrics_connectors.py` | Connector work in the shared metrics: the search-to-execute chain and the batch and search rows. |
| `shared_metrics_consent.py` | The one shared-metrics consent answer, and the terminal's first-run offer. |
| `shared_metrics_contract.py` | Bounded product contract for the first Hermes shared-metrics slice. |
| `shared_metrics_desktop.py` | Shared-metrics facts the Desktop app reports about itself: area use, friction, first-run steps, dislike signals, and one daily report (Bot Mode / Sessions split, button presses per action). |
| `shared_metrics_disabled.py` | hermes.feature_disabled.count: a user turns off something Hermes ships on, or removes something shipped. |
| `shared_metrics_drift.py` | Rows an earlier build or catalog stored whose values the current contract no longer lists. |
| `shared_metrics_efficiency.py` | Efficiency shared metrics: what one user turn costs, what users throw away, and where Hermes spends tokens it did not have to (spilled tool output, idle tool schemas, prompt-cache breaks). |
| `shared_metrics_engagement.py` | Daily engagement rollup, per-conversation session tally and turns-before-switch. |
| `shared_metrics_events.py` | Call-site API for process-level shared-metrics facts. |
| `shared_metrics_fields.py` | Bounded field builders for the decision-data shared metrics. |
| `shared_metrics_gateway.py` | Call-site API for messaging-gateway and cron shared metrics. |
| `shared_metrics_harness.py` | Agent-harness accuracy shared metrics: file-edit matching, loop guards, recovery after a tool error, terminal command outcomes and bad model replies. |
| `shared_metrics_install.py` | Install-snapshot fields for version lag, release channel and coarse hardware. |
| `shared_metrics_install_run.py` | hermes.install.run: fresh installs through scripts/install.sh and scripts/install.ps1. |
| `shared_metrics_loop.py` | Learning-loop, delegation and execution-backend shared metrics. |
| `shared_metrics_model.py` | Per-model quality, friction and context-pressure shared metrics. |
| `shared_metrics_prepared_compaction.py` | Prepared compaction (``compression.prepare_ahead``): adoption and every way a prepared pass is wasted. |
| `shared_metrics_process.py` | hermes.process.exit: how Hermes processes (and watchdog-killed turns) end. |
| `shared_metrics_send_config.py` | Configuration for shared-metrics transmission. |
| `shared_metrics_sender.py` | Transmit exported shared-metrics packages to the Nous telemetry service. |
| `shared_metrics_setup.py` | hermes.provider_setup.count: where connecting a model provider starts, succeeds, fails or is walked away from. |
| `shared_metrics_signals.py` | v5 signals: which disabled built-in tools models reach for, and when an install first adopts a feature. |
| `shared_metrics_snapshot.py` | Collect the once-a-day install configuration snapshot for shared metrics. |
| `shared_metrics_startup.py` | Startup / attach latency: one bucketed row per process start and surface. |
| `shared_metrics_subscriber.py` | Relay subscriber for the persisted Hermes shared-metrics slice. |
| `shared_metrics_update.py` | Shared-metrics facts for ``hermes update`` runs and Desktop self-updates. |

## `hermes_cli/proxy/`

| File | What it does |
|---|---|
| `__init__.py` | Local OpenAI-compatible proxy that forwards to OAuth-authenticated upstreams. |
| `adapters/__init__.py` | Upstream adapter registry for the local proxy server (see :class:`UpstreamAdapter`). |
| `adapters/base.py` | Abstract base for proxy upstream adapters; the proxy server is otherwise provider-agnostic. |
| `adapters/nous_portal.py` | Nous Portal upstream adapter. |
| `adapters/xai.py` | xAI Grok OAuth upstream adapter. |
| `cli.py` | CLI handlers for the ``hermes proxy`` subcommand. |
| `server.py` | HTTP server that forwards OpenAI-compatible requests to a configured upstream. |
| `sse_done.py` | SSE ``[DONE]`` sentinel normalization for OpenAI-compatible proxies. |

## `hermes_cli/subcommands/`

| File | What it does |
|---|---|
| `__init__.py` | CLI subcommand parser builders for ``hermes <subcommand>``. |
| `_shared.py` | Shared argparse helpers for the ``hermes_cli/subcommands/*`` builders. |
| `acp.py` | ``hermes acp`` subcommand parser. |
| `approvals.py` | ``hermes approvals`` subcommand parser. |
| `auth.py` | ``hermes auth`` subcommand parser. |
| `backup.py` | ``hermes backup`` subcommand parser. |
| `browser.py` | ``hermes browser`` subcommand parser. |
| `bundles.py` | ``hermes bundles`` subcommand parser. |
| `checkpoints.py` | ``hermes checkpoints`` subcommand parser. |
| `codex_runtime.py` | ``hermes codex-runtime`` — noninteractive counterpart of the ``/codex-runtime`` slash command. |
| `completion.py` | ``hermes completion`` subcommand parser. |
| `computer_use.py` | ``hermes computer-use`` subcommand parser. |
| `computer_use_screen.py` | ``hermes computer-use screen`` — the Bot Desktop screen a profile's ``computer_use`` drives on a headless Linux gateway host, viewable from Hermes Desktop. ``status`` / ``start`` / ``stop`` / ``install`` mirror the Desk… |
| `config.py` | ``hermes config`` subcommand parser. |
| `connectors.py` | ``hermes connectors`` subcommand parser. |
| `console.py` | ``hermes console`` subcommand parser. |
| `cron.py` | ``hermes cron`` subcommand parser. |
| `curator.py` | ``hermes curator`` subcommand parser. |
| `dashboard.py` | ``hermes dashboard`` / ``hermes serve`` subcommand parsers. |
| `debug.py` | ``hermes debug`` subcommand parser. |
| `doctor.py` | ``hermes doctor`` subcommand parser. |
| `dump.py` | ``hermes dump`` subcommand parser. |
| `egress.py` | ``hermes egress`` subcommand parser. |
| `fallback.py` | ``hermes fallback`` subcommand parser. |
| `gateway.py` | ``hermes gateway`` and ``hermes proxy`` subcommand parsers. |
| `gui.py` | ``hermes gui`` subcommand parser. |
| `hooks.py` | ``hermes hooks`` subcommand parser. |
| `import_cmd.py` | ``hermes import`` subcommand parser. |
| `insights.py` | ``hermes insights`` subcommand parser. |
| `journey.py` | ``hermes journey`` subcommand parser. |
| `login.py` | ``hermes login`` subcommand parser. |
| `logout.py` | ``hermes logout`` subcommand parser. |
| `logs.py` | ``hermes logs`` subcommand parser. |
| `mcp.py` | ``hermes mcp`` subcommand parser. |
| `memory.py` | ``hermes memory`` subcommand parser. |
| `migrate.py` | ``hermes migrate`` subcommand parser. |
| `moa.py` | ``hermes moa`` subcommand parser. |
| `model.py` | ``hermes model`` subcommand parser. |
| `monitoring.py` | ``hermes monitoring`` subcommand parser (gateway health/diagnostics export control). |
| `pairing.py` | ``hermes pairing`` subcommand parser. |
| `pause.py` | ``hermes pause`` / ``hermes resume`` — the global emergency stop. |
| `peer.py` | ``hermes peer`` — bot-to-bot DMs across machines/gateways. |
| `pets.py` | ``hermes pets`` subcommand parser. |
| `plugins.py` | ``hermes plugins`` subcommand parser. |
| `profile.py` | ``hermes profile`` subcommand parser. |
| `prompt_size.py` | ``hermes prompt-size`` subcommand parser. |
| `secrets.py` | ``hermes secrets`` subcommand parser. |
| `security.py` | ``hermes security`` subcommand parser. |
| `sessions.py` | ``hermes sessions`` subcommand parser. |
| `setup.py` | ``hermes setup`` subcommand parser. |
| `skills.py` | ``hermes skills`` subcommand parser. |
| `skin.py` | ``hermes skin`` subcommand parser. |
| `slack.py` | ``hermes slack`` subcommand parser. |
| `status.py` | ``hermes status`` subcommand parser. |
| `tools.py` | ``hermes tools`` subcommand parser. |
| `uninstall.py` | ``hermes uninstall`` subcommand parser. |
| `update.py` | ``hermes update`` subcommand parser. |
| `usage.py` | ``hermes usage`` — the account-limits block of the REPL ``/usage`` without starting a session. |
| `vault.py` | ``hermes vault`` subcommand parser. |
| `verify.py` | ``hermes verify`` subcommand parser. |
| `webapp.py` | ``hermes webapp``: open the Desktop workspace in a browser, served by the gateway. |
| `webhook.py` | ``hermes webhook`` subcommand parser. |
| `whatsapp.py` | ``hermes whatsapp`` subcommand parser. |
| `worktree.py` | ``hermes worktree`` subcommand parser. |

## `hermes_cli/web_routers/`

| File | What it does |
|---|---|
| `__init__.py` | Extracted APIRouter modules for the dashboard web server. |
| `_common.py` | Shared plumbing for the extracted dashboard routers — thin wrappers over the late-binding seam in :mod:`hermes_cli.web_deps` (web_server owns helpers/state; every access resolves at call time so ``monkeypatch.setattr(<o… |
| `actions.py` | Gateway restart/drain, Hermes update and background-action status dashboard routes. |
| `analytics.py` | Raw-YAML config and token/cost analytics dashboard routes. |
| `audio.py` | Audio dashboard routes: transcription upload + live transcribe-stream, voice config, ElevenLabs voices, TTS speak/lease and the speak-stream WebSocket. |
| `chat_workspaces.py` | Chat workspace picker: which host directories a NEW dashboard chat can start in. |
| `chat_ws.py` | Chat-tab WebSocket routes: /api/console, /api/pty, the /api/ws gateway sidecar and /api/pub + /api/events broadcast. |
| `chat_ws_errors.py` | User-facing copy for dashboard chat (``/api/pty``) start failures. |
| `config_env.py` | Config, env var and provider custom-endpoint dashboard routes. |
| `cron.py` | Cron dashboard routes. |
| `dashboard_ui.py` | Dashboard theme/font and dashboard-plugin (discovery, hub, install/enable, asset serving) routes. |
| `delegation.py` | Delegation routing routes: which ``delegation.backend`` runs subagents, and each plugin backend's routes under ``delegation.backends.<name>``. |
| `desktop_plugins.py` | The Webapp's door to this host's desktop plugins (``<root>/desktop-plugins/<name>/plugin.js``). |
| `display.py` | ``/api/display/ws`` — raw RFB over WebSocket for the Bot Desktop viewer. |
| `files.py` | Managed-files, chat image upload, /api/media and /api/fs dashboard routes. |
| `git.py` | Git dashboard routes — the remote half of the desktop coding rail + review pane. |
| `local_models.py` | Local-models dashboard routes — the desktop's window into the managed llama.cpp runtime. |
| `mcp.py` | MCP dashboard routes. |
| `memory_providers.py` | Memory-provider setup dashboard routes (schema, existing values, external dependency install). |
| `messaging.py` | Messaging dashboard routes: WhatsApp/Telegram onboarding and per-platform enable/config/test. |
| `models.py` | Model assignment dashboard routes: model info/options/recommended default, auxiliary + MoA slots, /api/model/set. |
| `oauth.py` | OAuth provider dashboard routes: catalog/status, disconnect, and in-browser device-code login flows. |
| `ops.py` | Pairing, webhooks, gateway lifecycle, credential pool, memory provider and operations (doctor/backup/import/hooks/checkpoints) dashboard routes. |
| `profiles.py` | Profiles dashboard routes. |
| `sessions.py` | Session dashboard routes. |
| `shared_metrics.py` | ``/api/shared-metrics/consent``: the dashboard's first-run shared-metrics offer. |
| `skills.py` | Skills dashboard routes. |
| `status.py` | Status dashboard routes: health, /api/status, system stats, curator, learning graph, portal and diagnostics actions. |
| `tools.py` | Toolset / terminal-backend dashboard routes. |
| `ui_preferences.py` | ``/api/ui-preferences``: the Webapp's door to this machine's UI preferences store (#145213). |
| `uploads.py` | Authenticated browser-to-host attachment staging for Hermes Webapp. |
| `webapp.py` | Webapp-only routes: the host terminal (loopback or authenticated binds), the one-use ticket each browser socket dial mints (``/api/webapp/socket-ticket?socket=`` for ``/api/ws`` on this same origin, the host terminal an… |
| `webapp_access.py` | Web Access routes: Desktop's Web Access pane turns the gateway-served Webapp on and off here. |
