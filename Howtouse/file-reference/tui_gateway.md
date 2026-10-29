# File reference: `tui_gateway`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | tui_gateway/ + ui-tui/ — the TUI and its JSON-RPC backend |
| `__init__.py` | Package marker / package-level exports |
| `_env.py` | Tolerant env-var knob parsing shared by the gateway entry points: a bare ``float(os.environ[...])`` would raise at import on a typo (``...POLL_S=2s``) and kill a worker before it serves a command; these fall back to ``d… |
| `_stdin_recovery.py` | Shared spurious stdin-EOF recovery for the TUI gateway entry point and slash worker. |
| `agent_callbacks.py` | Agent callback wiring: child-session live mirror, per-session agent callbacks, personality overlay, background/preview agent kwargs, agent reset. Bodies are rebound onto server.py's globals at install time (method_ctx.b… |
| `agent_factory.py` | TUI agent_factory seam; functions bind to the server namespace at registration. |
| `billing_view.py` | Billing / usage / subscription serializers for the TUI RPC surface. |
| `change_watcher.py` | Skin + config-change watcher: on-disk signatures for skin/pet/cron/sessions/platforms/ pairing/bot-relay state and the broadcast loop that pushes *.changed events. Bodies are rebound onto server.py's globals at install… |
| `checkpoints.py` | Checkpoint-enablement resolution for TUI-created agents (issue #79625). |
| `command_discovery.py` | Shared slash discovery data; no server import or session execution runtime. |
| `compute_host.py` | Persistent dashboard compute-host child: owns live AIAgent objects when ``dashboard.turn_isolation`` is enabled; frames are line-JSON over stdin/stdout. |
| `compute_host_bridge.py` | Compute-host (turn isolation) bridge: relay prompts/controls to the child process and mirror its metadata/clarify/compress acks back into the session. Bodies are rebound onto server.py's globals at install time (method_… |
| `connector_payload.py` | Connector UI payload redaction. |
| `connector_refusals.py` | Connector refusals both connector handlers send: the legacy one (``methods_connectors``) and the session authority's (``gateway/session_connections``). Each entry is ``(code, ConnectorErrorReason, message)``. |
| `contracts/__init__.py` | Wire contracts (see ``base.py``). Importing this package fills the registry tables; every topic module is listed here so the generator and the runtime see the same catalog. |
| `contracts/base.py` | Wire contract primitives for the TUI/desktop gateway. |
| `contracts/billing_delegation_pets.py` | Contracts: billing / subscription / usage envelopes, delegation controls, handoff, message reactions, pet generation and ``project.facts`` (handlers in ``tui_gateway/methods_session.py``). |
| `contracts/canonical.py` | Canonical ``hermes-gateway-v1`` methods that only the session authority serves. |
| `contracts/canonical_projections.py` | Canonical projections with demonstrated differences from standalone wire. |
| `contracts/canonical_sessions.py` | Shared method names whose canonical session wire differs from standalone serve. |
| `contracts/common.py` | Value shapes shared by several methods and events (declared once, imported everywhere). |
| `contracts/config_free_tier_control.py` | Contracts: config, setup readiness, free tier, model inventory, connectors, diagnostics, image generation and structured session control. |
| `contracts/connectors.py` | Contracts for connector catalog, authorization, and tool-list reads. |
| `contracts/connectors_operation.py` | The connection operation (``manage_connections`` card): the request event that opens a card, the update frames that drive it, and the RPCs the card answers through. |
| `contracts/display.py` | Bot Screen (``methods_display.py`` / ``methods_display_watch.py``): a profile's headless Xfce desktop, its takeover lease, the noVNC ticket and the on-host package install. |
| `contracts/events.py` | Notification payloads: every ``event`` frame the gateway emits (``params.payload``). |
| `contracts/groups_bot_relay.py` | Hosted Group Chat rooms (``groups.*``) and cross-connection bot relay (``bot_relay.*``). |
| `contracts/i18n.py` | Pluggable languages (``methods_i18n.py``): the language list and the pack/overlay catalog layer a renderer merges over its own bundled English. Both ride ``profile`` so a multiplexed backend answers for the profile whos… |
| `contracts/liveness.py` | Transport liveness + build capability probes (``methods_voice.py`` hosts them). |
| `contracts/machine.py` | This machine (``methods_machine.py``): host facts from ``hermes_platform.host.summary``. |
| `contracts/profiles_vault_complete_foreign_subagents.py` | Contracts for ``methods_profiles``, ``methods_vault``, ``methods_complete``, ``methods_session_foreign`` and ``methods_subagents``. |
| `contracts/projects_pets.py` | Projects (``projects.*`` — per-profile multi-folder workspaces, repo discovery, sidebar tree) and the pet mascot surface (``pet.*`` — gallery, sprite payloads, adopt/remove/rename). |
| `contracts/prompt_voice.py` | Prompt submission, attachments, side agents, approvals, batch-clarify locks (``methods_prompt.py``) and voice / wake-word control (``methods_voice.py``). |
| `contracts/registry.py` | The contract catalog: every method, server→client request and event the gateway speaks. |
| `contracts/server_requests.py` | Server→client requests: the backend asks the renderer a question (``server_requests.send``). |
| `contracts/sessions.py` | Session lifecycle contracts (``tui_gateway/methods_session.py``): create / resume / activate / close, the live-session snapshot those share, history + compression + undo, mid-turn corrections, listing/browsing stored ro… |
| `contracts/tools_commands.py` | Contracts: system / process / slash-command / rollback / cron / browser / config RPCs (handlers in ``tui_gateway/methods_tools.py``, browser helpers in ``methods_browser.py``). |
| `contracts/tools_mcp_plugins.py` | Tools / toolsets / MCP servers / plugins / skills / learning graph / reload contracts (``tui_gateway/methods_tools.py``). |
| `entry.py` | Defines `_close_rpc_stdin_on_exec`, `_private_rpc_stdin_windows`, `_install_sidecar_publisher`, `_shutdown_grace_seconds`, `_mcp_startup_call`, `_spawn_discovery` … |
| `event_publisher.py` | Best-effort WebSocket publisher transport for the PTY-side gateway. |
| `event_replay.py` | Per-session event sequencing + bounded replay for WS reconnects. |
| `free_tier_task_done.py` | Detects a task finishing on its own on the free tier, which (re)arms the sign-in offer (``hermes_cli.free_tier_offer``). |
| `git_probe.py` | Git working-tree probing for the gateway: run git, resolve repo roots, fold linked worktrees. Probing runs where the gateway runs (covers remote backends). Roots go through a thread-safe single-flight cache so concurren… |
| `host_supervisor.py` | Supervisor for the dashboard compute-host child: with ``dashboard.turn_isolation`` agent turns run in one persistent ``python -m tui_gateway.compute_host`` child so heavy agent threads do not contend with the serving pr… |
| `hosted_room_driver.py` | Runtime adapter for gateway-owned hosted room turns. |
| `hosted_room_member_activity.py` | Project a hosted room member's live runtime events to the ``on_room_member_activity`` plugin hook. |
| `hosted_room_peer_http.py` | Scoped HTTP client for peer hosted-room member turns. |
| `hosted_room_peer_transport.py` | Peer-backed session transport for one hosted-room member task: implements :class:`InternalSessionRPC` without canonical Bot Chat. The remote client must resolve a hidden ``Group: <room_id>`` session with ``source=bot_ro… |
| `hosted_room_prepare_stall.py` | Bound the room driver's retries of a room preparation that keeps failing, and say so in the room. |
| `hosted_room_server_rpc.py` | In-process session adapter for the hosted room driver: the room worker uses the same installed session handlers as every TUI/Desktop turn (no WebSocket transport), passing the task proof as an in-process-only Python obj… |
| `hosted_room_service.py` | Production coordinator for same-gateway hosted Discussion rooms. |
| `launch_profile_policy.py` | Launch-profile policy for a process that hosts several profile homes (``hermes serve`` / ``hermes dashboard`` pooling, ``?profile=``, hosted rooms; the multiplexed gateway's own worker). |
| `loop_noise.py` | Suppress benign event-loop teardown noise on the gateway serving loop. |
| `mcp_oauth_sessions.py` | Session-backed MCP OAuth flows for gateway RPC and connection-card callback relays. |
| `mcp_rpc_helpers.py` | Shared helpers for the per-profile MCP lifecycle RPCs (mcp.servers.*). |
| `method_ctx.py` | Seam for the server.py handler/helper split. server.py's JSON-RPC handlers and helpers close over its module globals (``_sessions``, ``_ok``, ``_err``, ...). Split modules define their code normally and server.py calls… |
| `methods_bot_relay.py` | Bot-relay JSON-RPC handlers — the gateway side of cross-connection A2A. Connections ARE the peer set: the Desktop owns every gateway socket and relays between them via four doors on EACH gateway: ``roster.sync`` (push O… |
| `methods_browser.py` | Browser connect/disconnect helpers for the browser.* RPCs (CDP probing, no network I/O on status). Bodies are rebound onto server.py's globals at install time (method_ctx.bind_module). |
| `methods_complete.py` | Completion / model-key / paste JSON-RPC handlers. |
| `methods_complete_helpers.py` | Completion helpers (@-mention / path fuzzy ranking, repo file listing) for the complete.* RPCs. |
| `methods_config.py` | Config / projects / setup JSON-RPC handlers. Bodies are rebound onto server.py's globals (method_ctx.bind_module) and reference them bare. ``config.set`` lives in methods_config_set. |
| `methods_config_set.py` | ``config.set`` — one JSON-RPC method, dispatched on ``key`` through ``_CONFIG_SETTERS``. Bodies are rebound onto server.py's globals (method_ctx.bind_module) and reference them bare. Each ``_set_*`` takes ``(rid, params… |
| `methods_connectors.py` | Defines `_capture_connector_rpc_owner`, `_connector_rpc_error`, `_refusals`, `_connector_auth_error`, `_connector_guard`, `_connector_owner_matches` … |
| `methods_connectors_account.py` | Defines `_account_method`, `_`, `_`, `_`, `_account_row`, `_` … |
| `methods_display.py` | Bot Desktop JSON-RPC handlers: the Desktop app's door to a profile's headless screen. |
| `methods_display_watch.py` | Cross-process lease watcher: ``display.lease`` for transitions made OUTSIDE ``hermes serve``. |
| `methods_free_tier.py` | Nous free-tier JSON-RPC handlers. ``free_tier.status`` answers from the auth store with zero network and zero side effects; ``free_tier.provision`` retries a welcome-trial claim that failed (desktop-only entry); ``free_… |
| `methods_groups.py` | Hosted-room JSON-RPC contract: durable room identity, replay, and the process-owned same-gateway Discussion driver; ``groups.capabilities`` keeps that boundary machine-readable. |
| `methods_groups_forward.py` | Standalone backend -> owning gateway for Group Chat calls (WA-19). |
| `methods_i18n.py` | Pluggable-language JSON-RPC handlers: ``i18n.languages`` and ``i18n.catalog``. |
| `methods_images.py` | Image-generation JSON-RPC handler (ws twin of the image_generate tool) for UI surfaces (avatar pickers, artifact panes). The result is a data URL: a remote desktop can't read a gateway file path and hosted URLs are ofte… |
| `methods_machine.py` | ``machine.facts``: the host summary the desktop first-run onboarding branches on. |
| `methods_onboarding.py` | Defines `_`, `_`, `_run_state`, `_due_now`, `_due_stamp`, `_shared_nous_store` … |
| `methods_plugin_catalog.py` | ``plugins.catalog.lookup``: one curated-catalog entry, resolved by the backend. |
| `methods_profiles.py` | Profile JSON-RPC handlers — the ws twin of the dashboard's /api/profiles (desktop plugins only have the ws door), on the same `hermes_cli.profiles` primitives. Bodies are rebound onto server.py's globals (method_ctx.bin… |
| `methods_projects.py` | Projects RPC surface: per-profile multi-folder workspaces, repo discovery, sidebar tree. Bodies are rebound onto server.py's globals at install (method_ctx.bind_module). |
| `methods_prompt.py` | Prompt / attachment / respond JSON-RPC handlers. |
| `methods_session.py` | Session / delegation / spawn-tree / billing / pet JSON-RPC handlers. |
| `methods_session_branch.py` | Branch (session.branch / session.branch_whole) helpers (``methods_session`` split). |
| `methods_session_control.py` | Structured Desktop controls for persisted goal, loop, and heartbeat state. |
| `methods_session_foreign.py` | Desktop foreign-history browsing, scoped to the serving backend and profile. |
| `methods_session_interrupt.py` | Interrupt / steer / redirect session handlers (``methods_session`` split). |
| `methods_session_model_guard.py` | ``session.create`` composer overrides and the model×provider coherence gate (#96817). |
| `methods_shared_metrics.py` | Shared-metrics consent JSON-RPC handlers (the Desktop twin of ``hermes setup``'s Shared Metrics section). Both opt-ins live in the focused profile's config.yaml exactly where the wizard writes them — ``telemetry.shared_… |
| `methods_slash.py` | slash.exec helpers: live-session command output + side-effect mirroring after a worker slash command. |
| `methods_subagents.py` | Session-scoped roster and bounded live transcript snapshots for shared clients. |
| `methods_tools.py` | Tools & system / slash / insights / rollback / plugins / cron / skills / MCP JSON-RPC handlers. |
| `methods_tools_plugin_servers.py` | Per-server rows of an installed portable plugin for ``plugins.manage list`` (``methods_tools._plugin_rows``). |
| `methods_vault.py` | Credential-vault JSON-RPC handlers — the Desktop's door to the local vault. |
| `methods_voice.py` | Voice / TTS / wake-word JSON-RPC handlers and their process-global state (one mic, one speaker per process). Bodies are rebound onto server.py's globals (method_ctx.bind_module), used bare. |
| `model_switch.py` | Model switching for a live session: persist, snapshot/restore runtime, /model apply with guards, bot-capability + config sync. Bodies are rebound onto server.py's globals at install time (method_ctx.bind_module), so the… |
| `owner_forward.py` | Serve -> owner cutover for one typed prompt (RT-37, #140385). |
| `pet_sheet.py` | Pure pet spritesheet helpers (revision id, per-row frame counts, row taxonomy, payload clone) for the ``pet.*`` RPCs in ``tui_gateway.server``. |
| `plugin_inject.py` | Ink TUI / desktop host for ``PluginContext.inject_message``. |
| `profile_roster_cache.py` | Memos for ``profiles.list``'s per-profile fields, each keyed on the file(s) it derives from. |
| `project_tree.py` | Authoritative project -> repo -> lane -> session tree builder (pure; git via ``resolve``). |
| `prompt_attachments.py` | Attachment staging: image sniffing, size caps, per-session attachment dirs, path resolution. |
| `prompt_turn.py` | The prompt turn: ``_run_prompt_submit`` and the per-phase helpers it drives. |
| `render.py` | Rendering bridge — routes TUI content through Python-side renderers. |
| `rpc_dispatch.py` | JSON-RPC admission and worker dispatch. Rebound onto the server namespace. |
| `server.py` | Defines `_record_crash`, `_panic_hook`, `_ws_orphan_setting`, `_resolve_ws_orphan_reap_grace`, `_DropTransport`, `_prepend_tool_paths` … |
| `server_requests.py` | Server→client JSON-RPC requests: the backend asks the renderer a question and waits for the response frame carrying the same ``id``. |
| `session_auto_continue.py` | Auto-continue: resume a turn killed by a process/machine death, plus queued-prompt drain and busy-submit handling. Bodies are rebound onto server.py's globals at install time (method_ctx.bind_module), so they reference… |
| `session_compression.py` | Live compression: config hot-reload onto a running agent, pending model switch apply, /compress (CompressionLockHeld when a turn holds the lock), session-key sync after compress. Bodies are rebound onto server.py's glob… |
| `session_history.py` | Session history/message shaping: image-ref messages, content coercion, history->wire messages, in-flight turn tracking and turn-failure detail. Bodies are rebound onto server.py's globals (method_ctx.bind_module). |
| `session_lifecycle.py` | Session lifecycle: active-session slot leases, finalize/teardown/close, turn interrupt, WS-orphan reap scheduling, transport-scoped close. Bodies are rebound onto server.py's globals at install time (method_ctx.bind_mod… |
| `session_notifications.py` | Per-session notification poller: kanban/loop/delegation events routed to the owning session, desktop UI wiring, HUD surface note. Bodies are rebound onto server.py's globals at install time (method_ctx.bind_module), so… |
| `session_reaper.py` | Session flush / reaping / orphan sweep / cross-backend heartbeat: exit-flush signal handlers, idle + LRU eviction, orphaned session-row sweep, backend heartbeat refresher. Bodies are rebound onto server.py's globals at… |
| `session_registry.py` | TUI session_registry seam; functions bind to the server namespace at registration. |
| `session_transports.py` | Additive transport membership for shared live sessions. |
| `session_workdir.py` | Session working-directory + durable session row: cwd resolution/healing, session.db row ensure, branch seed, history rewind, git meta persistence. Bodies are rebound onto server.py's globals at install time (method_ctx.… |
| `slash_fuzzy.py` | Description-aware fuzzy scoring for slash-menu completions (ported from superagent-ai/grok-cli ``src/ui/slash-menu.ts``; mirrored in ``ui-tui/src/app/slash/fuzzyScore.ts``). Tiers: exact command token (0), prefix (1), s… |
| `slash_worker.py` | Persistent slash-command worker — one HermesCLI per TUI session. |
| `stream_segments.py` | Wire identity for one turn's streamed reply. |
| `synthetic_turn.py` | Synthetic GIL-heavy turn driver for the AC-4 isolation certify harness. The regime under test is interpreter-wide GIL starvation (serving-process turn threads park the WebSocket loop in ``take_gil``), so the driver must… |
| `theme_bridge.py` | set_theme's desktop bridge: ``theme.apply`` for values (the renderer answers with what it applied) or ``theme.pick`` for a card that waits for the user. |
| `tool_progress.py` | Tool lifecycle callbacks (tool.start/complete/progress events), verbose-text capping/redaction, todo-state projection. Bodies are rebound onto server.py's globals (method_ctx.bind_module) and reference them bare. |
| `transport.py` | Transport abstraction for the tui_gateway JSON-RPC server. |
| `turn_marker.py` | Durable interrupted-turn markers for the desktop/TUI auto-continue path. A running turn's progress lives only in process memory (the agent flushes to SQLite at turn end), so a marker is written at turn start and cleared… |
| `user_messages.py` | User-facing copy for gateway refusals and session-level failures. |
| `ws.py` | WebSocket transport for the tui_gateway JSON-RPC server: reuses :func:`tui_gateway.server.dispatch` verbatim so every RPC, slash command, approval flow and agent event takes the same handlers as Ink over stdio. Wire pro… |
| `ws_legacy_fallback.py` | Legacy-handler fallback for authority-backed WebSocket connections. |
