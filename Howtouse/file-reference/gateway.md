# File reference: `gateway`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | gateway/ — messaging gateway, adapters, delivery |
| `__init__.py` | Hermes Gateway - multi-platform messaging integration (sessions, context injection, delivery routing, platform-specific toolsets). |
| `active_lease_io.py` | Active-session lease releases off the gateway event loop. |
| `agent_cache_pressure.py` | Memory-pressure bounds for the gateway's per-session AIAgent cache. |
| `assets/status_phrases.yaml` | YAML configuration/data |
| `assets/telegram-botfather-threads-settings.jpg` | JPEG image asset |
| `authz_mixin.py` | User-authorization mixin for ``GatewayRunner``: may this user/chat talk to the agent, the per-adapter DM policy, the unauthorized-DM behavior, and the bot loop guard. |
| `bot_loop_guard.py` | Sliding-window budget for bot-authored inbound messages. |
| `builtin_hooks/__init__.py` | Built-in gateway hooks that are always registered. |
| `cgroup_cleanup.py` | SIGKILL any process left in this systemd unit's cgroup. |
| `channel_directory.py` | Channel directory -- cached map of reachable channels/contacts per platform. |
| `code_skew.py` | Detect when the gateway is running stale code after a hot ``git pull``. |
| `config.py` | Gateway configuration: connected platforms, home channels, session reset policies and delivery preferences, loaded from config.yaml / gateway.json / env. |
| `config_env.py` | Environment-variable overrides for the gateway config (``_apply_env_overrides``). |
| `config_loader.py` | config.yaml / gateway.json → ``GatewayConfig.from_dict`` schema (the ``load_gateway_config`` phases). |
| `control_socket.py` | Gateway control socket — the gateway-owned local coordination surface: a local-only socket answering versioned JSON verbs (``identify``, ``status``). A connectable socket with a well-formed ``identify`` answer IS livene… |
| `cron_store_notices.py` | Home-channel notices for cron store degraded-state transitions (see ``cron/store_health.py``). |
| `cwd_placeholder.py` | Resolve gateway ``terminal.cwd`` placeholder values to ``TERMINAL_CWD``. |
| `dead_targets.py` | Persistent registry of delivery targets confirmed unreachable. Re-sending to a permanently gone chat (deleted group, bot kicked/blocked, deactivated user) every cron tick wastes flood-control budget; delivery short-circ… |
| `delivery.py` | Delivery routing for cron job outputs and agent responses, by target: explicit ("telegram:123456789"), platform home channel ("telegram"), origin (back to where the job was created), or local (files). |
| `delivery_ledger.py` | Durable delivery-obligation ledger for gateway final responses (rows in the shared ``state.db``; WAL, owner pid + process-start liveness, bounded retention) so a crash between finalize and platform ACK cannot lose a res… |
| `disk_status.py` | Disk-usage rollup for ``/api/status``. |
| `display_config.py` | Per-platform display/verbosity resolver (``resolve_display_setting``). |
| `drain_control.py` | External drain-control marker contract (dashboard → gateway). |
| `hooks.py` | Event hook system: fires handlers at gateway lifecycle points. |
| `host_attach.py` | Is there ONE live host gateway, and does it already serve this profile? |
| `host_rendezvous.py` | Host-wide singleton rendezvous: one lock + one record per ROLE per OS user. |
| `host_topology.py` | Who owns the gateway role on THIS host, and which profiles does that one process serve? |
| `hosted_room_attachments.py` | Durable, private attachment storage for gateway-owned Group Chats. |
| `hosted_room_authority_history.py` | Bounded replay context for committed authority changes, never election proof. |
| `hosted_room_discussion.py` | Deterministic policy for same-gateway hosted-room Discussions. |
| `hosted_room_driver.py` | Durable execution state for a same-gateway hosted room driver. |
| `hosted_room_execution_policy.py` | Target-issued execution authority for RoomLink member turns. |
| `hosted_room_links.py` | Private SQLite storage for negotiated hosted-room links. |
| `hosted_room_peer.py` | Typed contracts for autonomous cross-gateway hosted-room members. |
| `hosted_room_policy_checkpoint.py` | Durable bounded policy projection for hosted Group Chat preparation. |
| `hosted_room_replicas.py` | Replica store and takeover primitives for hosted Group Chat rooms. |
| `hosted_room_task_input.py` | Bounded immutable input references carried by compacting policy callers. |
| `hosted_room_work_lineage.py` | Validate passive evidence against committed authority spans, never elect an owner. |
| `hosted_room_work_records.py` | Bounded room-scoped evidence, never executable driver state or authority. |
| `hosted_room_work_storage.py` | Producer-scoped passive evidence storage and durable older-writer guards. |
| `hosted_rooms.py` | Durable state for gateway-hosted Bot Mode rooms. |
| `hosted_rooms_common.py` | Shared leaf helpers for the gateway hosted-room modules. |
| `hosted_rooms_gateway_import.py` | Hand the standalone backend's Group Chats to the gateway that owns the profile (WA-19). |
| `hosted_rooms_legacy_import.py` | One-shot import of the pre-isolation ``hosted_room*`` rows into ``shared-state.db``. |
| `kanban_watchers.py` | Kanban board watcher methods for GatewayRunner. |
| `kanban_watchers_common.py` | Plumbing shared by the kanban notifier and dispatcher loops. |
| `kanban_watchers_dispatcher.py` | Embedded kanban dispatcher: settings resolution and per-tick board work. |
| `kanban_watchers_notifier.py` | Kanban notifier: claim terminal task events per subscription and deliver them. |
| `lifecycle_ledger.py` | Gateway lifecycle ledger — durable termination-reason evidence. |
| `local_desktop_ui.py` | The desktop window bridges for a local viewer's turn on the session authority. |
| `local_viewer_events.py` | Turn events a local viewer (the classic CLI, TUI, Desktop) reads from the canonical stream. |
| `media_fetch.py` | Deliver ``MEDIA:<path>`` files that live inside a remote terminal sandbox (#466). |
| `media_policy.py` | Shared config→env bridge for media-delivery policy. |
| `media_repair.py` | Repair model-mangled ``computer_use`` screenshot paths in final responses. |
| `memory_monitor.py` | Periodic process memory usage logging for the gateway. |
| `memory_status.py` | Memory status rollup for ``/api/status``. |
| `message_timestamps.py` | Helpers for rendering gateway message timestamps exactly once. |
| `mirror.py` | Session mirroring for cross-platform message delivery. |
| `owner_identity.py` | The Webapp is the machine owner: one identity for every signed-in surface of this host. |
| `pairing.py` | DM pairing: code-based approval of new users on messaging platforms. |
| `parked_route_refusal.py` | A message a direct platform bot routes to a parked profile is refused out loud, never dropped. |
| `platform_activation.py` | Which deferred platform adapters a gateway config/env pass must import. |
| `platform_env.py` | Declarative env-credential bridge a platform plugin attaches to its ``PlatformEntry``. |
| `platform_registry.py` | Platform adapter registry. |
| `platforms/ADDING_A_PLATFORM.md` | Adding a New Messaging Platform |
| `platforms/__init__.py` | Platform adapters for messaging integrations (receive, send, auth, media). |
| `platforms/_http_client_limits.py` | Shared HTTP client factory for long-lived platform adapters. |
| `platforms/_shared.py` | Cross-adapter helpers shared by gateway/platforms/* and plugins/platforms/*. |
| `platforms/access_policy_mixin.py` | Config-driven DM / group intake policy shared by the adapters that gate access themselves (Weixin, WeCom, QQBot, WhatsApp, Yuanbao's ``AccessPolicy``). |
| `platforms/api_server.py` | OpenAI-compatible API server platform adapter (aiohttp). |
| `platforms/api_server_authority_runs.py` | API run controls resolve durable claims, never adapter agent/task ownership. |
| `platforms/api_server_bot_chat.py` | Peer turns into the canonical Bot Chat under session authority. |
| `platforms/api_server_config_guard.py` | aiohttp middleware answering a config-backend outage instead of letting it end the gateway. |
| `platforms/api_server_fire_startup.py` | Startup gate for the Chronos fire webhook (``POST /api/cron/fire``). |
| `platforms/api_server_memory_sessions.py` | Memory-provider continuity across api_server requests (#120116). |
| `platforms/api_server_openai_routes.py` | OpenAI-compatible routes for the API server adapter. |
| `platforms/api_server_profile_prefix.py` | ``/p/<profile>/`` prefix resolution for the shared api_server listener. |
| `platforms/api_server_request_options.py` | Per-request ``model_options`` decoding, lifted from ``platforms/api_server.py``. |
| `platforms/api_server_response_admissions.py` | Responses retries observe their original admission before resolving mutable conversation names. |
| `platforms/api_server_response_identity.py` | Stable presentation identity for a durable Responses admission. |
| `platforms/api_server_response_store.py` | SQLite-backed store for Responses API state (``previous_response_id`` chaining, named conversations). |
| `platforms/api_server_room_dispatch.py` | RoomLink dispatch validation and hidden member-session ownership. |
| `platforms/api_server_room_grants.py` | RoomLink room-member grants and capability HTTP handlers. |
| `platforms/api_server_run_idempotency.py` | Durable idempotency reservations for API server runs. |
| `platforms/api_server_runs.py` | Durable ``/v1/runs`` admission, status, events, and control handlers. |
| `platforms/api_server_store.py` | Runtime-bound API storage selection; borrowed stores are never adapter-owned. |
| `platforms/api_server_turn_boundary.py` | Current-turn boundary inside an agent transcript returned to the OpenAI-compat routes. |
| `platforms/base.py` | Base platform adapter interface; every platform adapter inherits from BasePlatformAdapter. |
| `platforms/base_exec_approval.py` | Shared wording for the exec-approval prompt every messaging surface renders. |
| `platforms/base_log_safety.py` | Log-safe URL rendering for adapter logs (split from :mod:`gateway.platforms.base`). |
| `platforms/base_streaming_tts.py` | Streaming-TTS format descriptor, handle and turn-scoped suppression helpers (#60671). |
| `platforms/docker_media_paths.py` | Host directories that stand in for a Docker container's ``/workspace`` and ``/root``. |
| `platforms/event.py` | Inbound message event types shared by every gateway platform adapter. |
| `platforms/helpers.py` | Shared helpers for gateway platform adapters: message dedup, markdown stripping, thread participation tracking, GFM table → bullets, mention-pattern compilation, and fence-aware markdown chunking. |
| `platforms/media_cache.py` | Shared mime↔extension dispatch for inbound (downloaded) platform media. |
| `platforms/msgraph_webhook.py` | Microsoft Graph webhook adapter for change-notification ingress. |
| `platforms/send_targets.py` | Public send_message contract pieces a platform plugin declares on its ``PlatformEntry``. |
| `platforms/shared_ingress.py` | Shared-listener ingress for inbound-port platforms under ``gateway.multiplex_profiles``. |
| `platforms/tcp_site.py` | Bind an aiohttp ``TCPSite`` for the HTTP-serving adapters (webhook, api_server): exclusive on macOS, yet able to rebind over a lingering TIME_WAIT socket right after a gateway restart. |
| `platforms/webhook.py` | Generic webhook platform adapter: aiohttp server that validates HMAC-signed POSTs (GitHub, GitLab, Svix, Linear, generic), renders payloads into agent prompts, and routes responses back (github_comment or any gateway pl… |
| `platforms/webhook_coalesce.py` | Per-route event coalescing for the webhook adapter (opt-in ``coalesce`` route block). |
| `platforms/webhook_delivery.py` | Validated webhook destinations live in the owner's admitted input, not a TTL cache. |
| `platforms/webhook_filters.py` | Route-local filters and script transforms for the webhook adapter. |
| `platforms/webhook_ingress.py` | Receipt-only adapter ingress: the authority, not an HTTP/WS task, owns execution. |
| `platforms/webhook_mcp_events.py` | MCP Events deliveries on routes that ``tools/mcp_tool_events.py`` created (the route carries an ``mcp_event`` block). The endpoint-verification echo and the ``terminated`` / ``gap`` control envelopes are answered here w… |
| `platforms/whatsapp_common.py` | Transport-agnostic WhatsApp behavior shared by the Baileys bridge adapter and the Cloud API adapter: allow-list / DM / group gating, mention detection, quoted-reply- to-bot detection, broadcast filtering, WhatsApp markd… |
| `plugin_command_choice.py` | The gateway's askers for ``PluginContext.ask_choice`` (``hermes_cli/plugin_choices.py``). |
| `plugin_keyless_inject.py` | Where a key-less ``PluginContext.inject_message(text)`` goes when plugin code runs for the gateway. |
| `plugin_messages.py` | Where ``PluginContext.post_message`` lands: the conversation the calling plugin code works for. |
| `profile_routing.py` | Profile-based routing: route senders/locations to different profiles. |
| `readiness.py` | Bounded, non-destructive readiness probes for authenticated health surfaces. |
| `relay/__init__.py` | Relay/connector support package for the Hermes gateway. |
| `relay/adapter.py` | RelayAdapter — one generic gateway adapter fronted by the connector. EXPERIMENTAL. |
| `relay/adapter_discord_interaction.py` | Forwarded Discord interaction -> ``MessageEvent`` normalization for the relay adapter. |
| `relay/auth.py` | Gateway-side relay authentication primitives. EXPERIMENTAL. |
| `relay/command_manifest.py` | Gateway-declared Discord slash-command manifest for the relay lane (Phase 4). |
| `relay/descriptor.py` | CapabilityDescriptor — the relay handshake payload. EXPERIMENTAL. |
| `relay/egress.py` | Gateway-side relay EGRESS AUTHORIZATION (P5). |
| `relay/inbound_admission.py` | Native admission of a connector-delivered relay message (``RelayAdapter._on_inbound``). |
| `relay/media.py` | Relay media client — gateway↔connector media plane (Phase 2). EXPERIMENTAL. |
| `relay/transport.py` | Relay transport protocol — the gateway<->connector wire contract. EXPERIMENTAL. |
| `relay/ws_transport.py` | Production WebSocket RelayTransport — the gateway's live link to the connector. |
| `response_filters.py` | Gateway response filtering helpers. |
| `restart.py` | Shared gateway restart constants and supervisor detection helpers. |
| `restart_loop_guard.py` | Auto-resume restart-loop breaker (defense-3). |
| `restart_notice.py` | Planned-restart marker: the CLI stamps it so the next boot says the gateway is back online. |
| `rich_sent_store.py` | Local index of what we've sent (and, for WhatsApp, received) keyed by ``(chat_id, message_id)``. |
| `run.py` | Gateway runner - entry point for messaging platform integrations. |
| `run_active_work_verb.py` | ``active-work`` control verb: what a stop/restart of this gateway would interrupt, answered live. |
| `run_adapters.py` | Adapter connect/disconnect, fatal-error recovery, reconnect watcher and multiplex profile adapters for GatewayRunner (mixin bound via the MRO). |
| `run_agent_cache.py` | Agent cache, session model overrides, turn leases, run generations and conversation-scope reset for GatewayRunner (MRO mixin). ``gateway.run`` internals are imported lazily inside method bodies (import cycle), so ``patc… |
| `run_api.py` | The gateway's local HTTP/WS listener: the native session WebSocket plus the dashboard API. |
| `run_bootstrap.py` | Process startup phases; diagnostics remain in the gateway facade. |
| `run_busy.py` | Busy-session queueing, slot claims, slash dispatch tables and destructive-slash confirmation for GatewayRunner (mixin bound via the MRO). |
| `run_common.py` | Leaf constants shared by ``gateway/run.py`` and its ``run_*`` mixin modules. |
| `run_config_loaders.py` | Config/env loaders (busy modes, reasoning, service tier, timeouts, fallback) for GatewayRunner. |
| `run_delivery_queue_watch.py` | Wake the restart-safe cron delivery drain when a worker writes the queue (#117307). |
| `run_goals.py` | Goal/heartbeat continuation, post-turn hooks and loop-wakeup watcher methods for GatewayRunner. |
| `run_heartbeat_acceptance.py` | Accounting at completion of an exact heartbeat admission attempt. |
| `run_heartbeat_restore.py` | Recover heartbeat watches from the gateway's canonical persisted routing index. |
| `run_housekeeping_disk.py` | Gateway housekeeping chores that keep the data disk healthy: stale media-cache cleanup and the home-channel prompt for the low-disk auto-prune decision (see ``hermes_cli/prune_advisor.py``). |
| `run_idle_exit.py` | Idle exit for an auto-started (unmanaged) gateway. |
| `run_idle_gates.py` | Idle gates for the gateway's per-profile pollers (heartbeat restore, handoff watcher, loop wakeup). |
| `run_inbound.py` | Inbound message pipeline (_handle_message, text/media preparation, durable-turn markers, plugin injection) for GatewayRunner. |
| `run_inbound_consumer.py` | ``post_gateway_admission``: let a plugin consume an admitted inbound message (#129958). |
| `run_inbound_hooks.py` | Plugin and user extension points on the inbound pipeline (moved out of ``gateway/run_inbound.py``). |
| `run_inbound_media.py` | Inbound attachment re-homing for multiplexed gateways (moved out of ``gateway/run_inbound.py``). |
| `run_inbound_transcription.py` | Voice-clip transcription for inbound messages (moved out of ``gateway/run_inbound.py``). |
| `run_inbound_unauthorized.py` | Copy and owner-side signalling for unauthorized inbound senders. |
| `run_notifications.py` | Process/completion/update notifications, media delivery and async-delegation delivery for GatewayRunner. |
| `run_notifications_ownership.py` | Completion ownership for GatewayRunner: the session a pinned completion belongs to. |
| `run_notifications_update.py` | ``hermes update --gateway`` progress/completion notifications for GatewayRunner. |
| `run_plugin_injection.py` | Plugin-triggered gateway turns (``PluginContext.inject_message``): the process-wide injector this runner publishes, the thread-safe scheduler, and the dispatch through the adapter message path. |
| `run_plugin_rewire.py` | Late plugin loads re-wire the running adapters (#87770). |
| `run_profile_reconcile.py` | Hot-serve for ``gateway.multiplex_profiles``: keep the served-profile set in step with ``profiles/`` while the multiplexer runs, instead of snapshotting it once at boot. |
| `run_runtime.py` | Session-runtime lifecycle owned by the ordinary gateway bootstrap. |
| `run_runtime_init.py` | Writable runner initialization, separate from process ownership. |
| `run_shutdown.py` | Stop/drain/restart, scale-to-zero and active-work accounting methods for GatewayRunner. |
| `run_shutdown_session_end.py` | Session finalize dispatch and delivery of plugin ``on_session_finalize`` messages for GatewayRunner. |
| `run_startup.py` | Startup sequence, resume/restore and handoff methods for GatewayRunner. |
| `run_topics.py` | Telegram forum-topic and Discord auto-thread binding/rename methods for GatewayRunner (MRO mixin). ``gateway.run`` internals are imported lazily inside method bodies (import cycle), so ``patch("gateway.run.X")`` keeps i… |
| `run_turn.py` | Agent-turn execution for GatewayRunner: _handle_message_with_agent, _run_agent*, proxy path, background tasks, MCP reload. Bound onto ``GatewayRunner`` via the MRO; ``gateway.run`` internals are imported lazily inside m… |
| `run_turn_followup_ack.py` | Processing-lifecycle hooks for runner-drained queued follow-ups. |
| `run_turn_hygiene.py` | Gateway turn hygiene phases; inherited by GatewayTurnMixin. |
| `run_turn_persistence.py` | Gateway turn persistence phases; inherited by GatewayTurnMixin. |
| `run_turn_prepare.py` | Gateway turn prepare phases; inherited by GatewayTurnMixin. |
| `run_turn_progress.py` | Extracted gateway run_turn_progress responsibility; consumed by TurnRunner. |
| `run_turn_runner.py` | Per-turn callback runner (progress/status/voice/run_sync) for the gateway agent turn. |
| `run_turn_runner_approval_settle.py` | Tell the chat when an exec-approval prompt times out (messaging platforms). |
| `run_turn_runner_clarify_delivery.py` | Clarify prompt delivery on messaging platforms: send disposition, plain-text fallback, bounded wait. |
| `run_voice.py` | Voice-channel / auto-TTS methods for GatewayRunner (split out of ``gateway/run.py``; bound via the MRO). ``gateway.run`` internals are imported lazily inside method bodies (import cycle), so ``patch("gateway.run.X")`` k… |
| `run_watchers.py` | Session housekeeping / stall / catalog-refresh watcher loops, bound onto ``GatewayRunner`` via the MRO. |
| `runtime_bootstrap.py` | Private local bootstrap grants; never put these credentials in discovery. |
| `runtime_bootstrap_windows.py` | Native local-only bootstrap pipes with cancellable overlapped I/O. |
| `runtime_contract.py` | Gateway launch decisions independent of operating-system probes. |
| `runtime_downgrade_exit.py` | Stop a gateway whose checkout was moved back to a release that predates the gateway runtime. |
| `runtime_footer.py` | Gateway runtime-metadata footer (model · context % · cwd), off by default to keep replies minimal. Config: ``display.runtime_footer: {enabled: bool, fields: [model, context_pct, cwd]}`` (order shown; drop any to hide),… |
| `runtime_ownership.py` | Nonblocking, all-or-nothing reservations of canonical profile homes. |
| `scale_to_zero.py` | Scale-to-zero idle detection + dormant-quiesce for the gateway. |
| `session.py` | Gateway session management: message sources, the persisted routing index (SessionStore), explicit resets and the dynamic "Current Session Context" system prompt section. |
| `session_a2a.py` | Profile forwarding through the canonical owner, with exact conversation identity. |
| `session_acp_lifecycle.py` | ACP v0.9 has no per-session destroy: the last viewer leaving an idle ACP session ends it (#118216). |
| `session_active_list.py` | ``session.active_list`` on the session authority: the live state of the turns it owns. |
| `session_admission.py` | Canonical payload identity after authorization and immutable media capture. |
| `session_ancillary.py` | Desktop/Ink projections of existing owner state, plus the session-scoped process verbs. |
| `session_api.py` | Server-only binding of API transcript identities to the existing TurnRunner. |
| `session_api_media.py` | API image parts become committed media references that outlive the transient turn. |
| `session_api_turn.py` | Trusted API preparation and observation of the canonical durable FIFO. |
| `session_authorities.py` | One SessionAuthority per reserved profile home; resolved by the active runtime scope. |
| `session_authority.py` | Gateway-owned live sessions and canonical durable FIFO scheduling. |
| `session_automation.py` | Trusted producer admission; not a client-selectable internal input flag. |
| `session_bot.py` | Bot Chat ingress into the existing authority FIFO; viewers never own delivery. |
| `session_bot_mailbox.py` | Authority-local async serialization; file locks cover only short synchronous mailbox I/O. |
| `session_busy_controls.py` | Session-scoped busy preferences and controls of the existing execution only. |
| `session_clarify_batch.py` | The clarify tool's whole question batch for a classic-CLI viewer's turn, in one request. |
| `session_clarify_lock.py` | ``clarify.lock`` on the session owner (#140400). |
| `session_cli_turn.py` | Per-admission turn inputs the classic CLI sends with ``prompt.submit`` (CALLMAP W2). |
| `session_cold_review.py` | ``/review`` and messaging ``/refine`` for a session whose cached agent is gone. |
| `session_command_sink.py` | What a messaging command handler would have SENT, captured for a local ``slash.exec``. |
| `session_commands.py` | Bound local slash commands; prompt directives use the client's durable submit. |
| `session_complete_path.py` | ``complete.path`` on the shared gateway: the sidecar's path / ``@`` listing, rooted in one session's folder. |
| `session_completion_notes.py` | A completion for a local session no viewer is watching is written into it as a note (#134889 LC-7). |
| `session_config.py` | Owner-bound native settings and model inventory, never legacy execution. |
| `session_connections.py` | The ``manage_connections`` card on the session authority: ``connection.respond``, the operation's ``status``/``wake`` and the card's Try again (``connectors.connect`` with ``reconnect``), plus the open card a resume res… |
| `session_context.py` | Session-scoped context variables for the Hermes gateway. |
| `session_context_refs.py` | ``@`` references of one turn: expanded once, in the session's workspace, on the text the model reads. |
| `session_contract.py` | Public session authority contract; live execution state never crosses this boundary. |
| `session_control_actions.py` | Desktop's goal / loop / heartbeat / subgoal card buttons (``session.control``) on the owner. |
| `session_controls.py` | Authenticated WS projection of the gateway authority; no TUI execution fallback. |
| `session_cron.py` | Trusted cron producer and owner execution of the existing scheduler contract. |
| `session_cron_commands.py` | ``/cron`` on the shared gateway: the classic CLI's handler (hermes_cli/cli_cron_lines.py), run by the owner. |
| `session_db_recovery.py` | Recoverable per-path SessionDB handle caches for the gateway. |
| `session_deferred_pick.py` | A model or reasoning pick on a session with a running turn lands for the next turn (RT-12, MP-24). |
| `session_detached.py` | A messaging conversation its chat moved past stays usable from the apps (Teknium's ruling). |
| `session_discovery.py` | Authenticated, profile-bound discovery without legacy execution dispatch. |
| `session_display.py` | Per-turn client presentation (hidden widget intents, large-paste title preview) through canonical admission. |
| `session_envelope.py` | Owner-only durable native input codec; never a client-supplied wire format. |
| `session_events.py` | Authority-local subscription ordering over the existing bounded transports/replay. |
| `session_execution.py` | Extracted gateway session_execution responsibility; consumed by TurnRunner. |
| `session_finite.py` | Admission-scoped finite consumers, independent of viewer or daemon lifetime. |
| `session_group_controls.py` | Profile-owned room controls over the canonical hosted service. |
| `session_history_mount.py` | Read-only mount of stored history no receipt, route or binding restores (#143547 RT-30b/48/49). |
| `session_hosted_attachments.py` | Owner-authorized room byte RPCs and committed task input materialization. |
| `session_hosted_controls.py` | Exact operator controls for canonical hosted attempts, never legacy replay. |
| `session_hosted_members.py` | Which local profiles a hosted group on one authority may seat (#139002). |
| `session_hosted_rpc.py` | Private hosted-room producer over the gateway's canonical local-session FIFO. |
| `session_hosted_service.py` | Authority-bound hosted service; no legacy session server is constructed. |
| `session_hosted_transport.py` | Hosted producers between independently owned local profile daemons. |
| `session_identity.py` | One frozen routing identity per inbound gateway event. |
| `session_images.py` | Staging-only image uploads on the authenticated session authority. |
| `session_info_reads.py` | Reports with no messaging handler that the shared gateway serves a local session itself. |
| `session_ingress.py` | Trusted messaging admission and the existing TurnRunner invocation boundary. |
| `session_ingress_burst.py` | Busy same-sender bursts become one shared-runtime admission. |
| `session_ingress_context.py` | Process-local callback provenance; private snapshots are revalidated, not grants. |
| `session_ingress_media.py` | Immutable local-media references for owner-only native admission. |
| `session_kanban.py` | Trusted dispatcher claims enter the ordinary owner's durable admission queue. |
| `session_lifecycle.py` | SessionStore explicit suspension, crash-recovery markers, pruning and shared clock/id helpers. |
| `session_listing.py` | Read-only native picker history; enumeration never adopts a transcript. |
| `session_live_listing.py` | The live session feeds (``session.list`` live scope, ``session.active_list``) read off the loop. |
| `session_llm_oneshot.py` | ``llm.oneshot`` on the shared gateway: a session-bound one-shot borrows that session's model. |
| `session_local.py` | Fresh local routes owned by the authenticated gateway, not by a viewer. |
| `session_local_adoption.py` | A local receipt's compression catch-up (#140060), committed off the owner loop. |
| `session_local_close.py` | The picker's view of a canonical local session its last viewer closed, as main listed it. |
| `session_local_editor.py` | Editor policy lives with execution; an ACP connection is only a viewer. |
| `session_local_inventory.py` | Main's banner / status-bar inventory for a canonical local session. |
| `session_local_mcp.py` | Editor MCP servers are session state the gateway owns; an ACP connection only requests them. |
| `session_local_migration.py` | Owner-only adoption of pre-authority local transcripts. |
| `session_local_recovery.py` | Restore only private, profile-bound local policy into the existing authority. |
| `session_local_route.py` | ``-m <alias \| provider:model \| provider/model>`` at ``session.create``, resolved by the owner. |
| `session_local_title.py` | Title-keyed local session selection, resolved read-only by the authority. |
| `session_managed_worker.py` | Admission-owned production exec; observers never own the worker lifetime. |
| `session_managed_worker_log.py` | Bounded, redacted per-profile sink for managed-worker stderr. |
| `session_messaging_picks.py` | A viewer's model and reasoning picks on a messaging chat (Telegram, Discord, ...), #141152. |
| `session_mutation_compress.py` | Summary preparation has no canonical store; publication owns the only write. |
| `session_mutation_model.py` | Resolve explicit model changes using the existing source model switch pipeline. |
| `session_mutation_policy.py` | Prepare the policy-only session edits: session-scope reasoning and the workspace (Move to project). |
| `session_mutations.py` | Action-specific authority mutations, shared by WS and authenticated HTTP. |
| `session_onboarding.py` | First-run onboarding on the session authority: ``onboarding.start`` and ``onboarding.skip``. |
| `session_operator.py` | Private provenance for already-authorized operator input. |
| `session_pending_controls.py` | Generation-bound projection/control of the existing blocking approval queue. |
| `session_persistence.py` | SessionStore storage plumbing: per-profile SessionDB handle resolution and the routing-index load/save paths (state.db gateway_routing primary, sessions.json legacy mirror). Mixin split out of ``gateway/session.py``; bo… |
| `session_policy.py` | Frozen, explicit local-client launch policy for the existing TurnRunner. |
| `session_policy_credentials.py` | Borrow frozen config credentials from the existing profile source, not a vault. |
| `session_policy_refresh.py` | A resumed local session re-reads its config-derived settings (CFG-2); its MCP servers change the same way (CFG-3). |
| `session_producer_lifecycle.py` | The adapter processing lifecycle of a producer-admitted turn (relay, webhook: ``admit_producer``). |
| `session_prompt_pin.py` | SessionStore prompt pins: the durable snapshot of the system-prompt inputs internal turns reuse. |
| `session_prune.py` | ``session.prune``: the owner runs `hermes sessions prune` for its own store. |
| `session_queued_controls.py` | Steer and Edit of a still-queued admission: ``prompt.steer_queued`` / ``prompt.replace_queued``. |
| `session_reactions.py` | Desktop's message reactions (``message.react``) on the owner's transcript. |
| `session_readiness.py` | Profile-bound setup checks without legacy session execution dispatch. |
| `session_recovery.py` | SessionStore durable-row recovery: session-key generation, legacy Slack key migration, rebuilding a routing entry from state.db, and the SQLite side of routing transitions (promote/reopen/create/ peer). Mixin split out… |
| `session_refine.py` | ``/refine`` for a local session whose cached agent is gone (T7). |
| `session_results.py` | Exact execution results commit with settlement, before delivery/publication. |
| `session_retry_admission.py` | Messaging ``/retry`` under a session authority: the transcript rewrite commits in the re-sent turn's own admission transaction (#139257 step 2, MSG-11). |
| `session_route_identity.py` | One resolved-route identity for launch-route gates. |
| `session_route_recovery.py` | Mount a cold messaging-platform session into the authority for a local viewer (TUI-8). |
| `session_runtime_workers.py` | Physical worker liveness and cooperative Stop across every served authority. |
| `session_secret_prompt.py` | The masked skill-secret prompt for a local viewer's turn. |
| `session_server_requests.py` | The session owner's server→client requests to a local viewer, and who may settle them. |
| `session_setting_commands.py` | The messaging setting handlers (``/reasoning`` ``/busy`` ``/verbose`` ``/fast`` ...) on a LOCAL session. |
| `session_settlement_recovery.py` | Fence an unsettled claim in a live owner without inventing a terminal result. |
| `session_shell.py` | Ink ``!cmd`` / ``{!cmd}`` on the shared owner: one captured shell command for a local session. |
| `session_skin.py` | The owning profile's resolved skin for a canonical client's readiness. |
| `session_stall.py` | Gateway session stall notification policy. |
| `session_state.py` | Per-session gateway state in one container (replaces ~19 session_key-keyed dicts on GatewayRunner that bred boundary drift and wholesale-reset races). Scopes follow where each dict was CLEARED: ``turn`` at the end of ev… |
| `session_sudo_prompt.py` | The masked sudo password prompt for a local viewer's turn. |
| `session_surface.py` | Per-turn client surface (floating HUD, live voice) carried through canonical admission. |
| `session_tool_events.py` | Viewer payload limits; the full tool input/output stays in canonical history. |
| `session_transcript.py` | SessionStore transcript I/O: SQLite append with a per-session retry queue, compression-reroute following, FTS corruption recovery, rewrite/rewind/load. Mixin split out of ``gateway/session.py``; bound onto ``SessionStor… |
| `session_tui_config.py` | Owner ``config.set`` for the TUI's profile preferences. |
| `session_tui_ops.py` | Ink's session utilities on the shared owner: ``/save`` (``session.save``), ``/reload`` (``reload.env``), ``/agents pause\|resume`` (``delegation.pause``) and ``/rollback`` (``rollback.list`` / ``rollback.diff`` / ``roll… |
| `session_tui_reads.py` | Main's TUI text for the session reads its sidecar answered itself: /status, /context. |
| `session_tui_side.py` | Ink's ``/bg`` (``prompt.background``) and ``/btw`` (``prompt.btw``) on the shared owner. |
| `session_unattended_unknown.py` | An ``unknown`` turn nobody is waiting on settles as interrupted (#134889 GW-10, #139532). |
| `session_usage.py` | Session-cumulative usage for a local viewer (wave A2 / CALLMAP W3). |
| `session_vault_prompt.py` | The browser vault's prompts (unlock, save login, one-time code) for a local viewer's turn. |
| `session_viewer_automation.py` | ``session.automation``: the classic CLI's /goal, /subgoal, /loop and /heartbeat managers, run here. |
| `session_viewer_close.py` | The last viewer closing a session ends it on the owner, lifecycle included (#134889 LC-1/LC-2/LC-6). |
| `session_worker.py` | Execution-scoped worker operations on the ordinary authenticated authority. |
| `session_worker_child.py` | Owner-reserved delegated children of a verified worker execution (#141793). |
| `session_worker_construct.py` | Agent-construction inputs the owner resolves for a managed worker (``construct_v1``). |
| `session_worker_delegation.py` | Closed delegation-ledger operations in the existing worker receipt transaction. |
| `session_worker_reservation.py` | Private owner-side reservation for a concrete already-started admission. |
| `session_worker_spawn.py` | Cancellation-safe handoff of a managed subprocess acquired off the owner loop. |
| `shutdown_flush.py` | Flush pending messages and agent transcripts to disk before shutdown to prevent data loss. |
| `shutdown_forensics.py` | Shutdown forensics — capture context when the gateway receives SIGTERM/SIGINT. |
| `shutdown_watchdog.py` | Out-of-loop shutdown and event-loop liveness backstops. |
| `slash_access.py` | Per-platform slash command access control. |
| `slash_commands.py` | Gateway slash-command handlers for GatewayRunner: lifted out of ``gateway/run.py`` into a mixin so ``self._handle_*_command`` keeps resolving via the MRO. Cohesive clusters live in the sibling mixins (``slash_commands_m… |
| `slash_commands_branch_thread.py` | ``/branch`` destination on thread-capable platforms (#66023). |
| `slash_commands_goals.py` | Autonomy-loop gateway commands: /goal, /subgoal, /heartbeat, /loop, /refine, /review. Bound onto ``GatewayRunner`` through ``GatewaySlashCommandsMixin``. |
| `slash_commands_login.py` | The off-turn, paired-DM-only ``/login`` command. |
| `slash_commands_model.py` | Gateway slash commands that switch or tune the model route: /model, /codex-runtime, /reasoning, /fast, /personality. |
| `slash_commands_session.py` | Gateway slash commands that rotate, switch, fork or rewrite the session transcript: /new, /resume, /sessions, /branch, /title, /save, /undo, /retry, /topic, /compress. Split out of ``gateway/slash_commands.py``; bound o… |
| `slash_commands_status.py` | Read-only gateway introspection commands: /status, /context, /usage, /agents, /insights, /topup. Bound onto ``GatewayRunner`` through ``GatewaySlashCommandsMixin``. |
| `status.py` | Gateway runtime status helpers: PID/lock/marker files under ``{HERMES_HOME}`` (one set per home/profile) that tell whether the gateway daemon is running. |
| `status_inline_source.py` | Inline-source (``python -c <src> …``) command-line parsing for gateway process identity. |
| `status_lock_dir.py` | The unusable scoped-lock dir report (#134889 W2). :mod:`gateway.status` raises it from ``acquire_scoped_lock``; nothing here reads back into that module. |
| `status_phrases.py` | Human-friendly generic gateway status phrases: short chat-safe lines for the long-running status surface without relaying raw model scratch text — only configured phrase strings are used; tool args, commands, previews,… |
| `status_pid_records.py` | Which runtime records name the gateway that holds ``gateway.lock`` right now. |
| `status_scoped_locks.py` | Scoped-lock ownership and release, split from :mod:`gateway.status` (acquire stays there). |
| `status_served.py` | Which runtime record describes a profile the host multiplexer may serve. |
| `sticker_cache.py` | Sticker description cache for Telegram. |
| `stream_consumer.py` | Gateway streaming consumer — bridges sync agent callbacks to async platform delivery. |
| `stream_consumer_directives.py` | Hold-back check for attachments still being streamed: ``MEDIA:<path>``, ``[[…]]`` flags and markdown/HTML image tags (the display cleaner hides each one only once it is complete). |
| `stream_consumer_fallback.py` | Fallback delivery for GatewayStreamConsumer: continuation sends after edits stop working, chunking, cursor cleanup, commentary and silence retraction. |
| `stream_consumer_fences.py` | Code-fence helpers shared by the stream consumer and the gateway final send. |
| `stream_consumer_think.py` | Think-block filtering for GatewayStreamConsumer. |
| `stream_consumer_transport.py` | Transport layer of GatewayStreamConsumer: native frames, drafts, edit/send. |
| `stream_dispatch.py` | Adapter-driven dispatch of structured stream events (gateway/stream_events.py). |
| `stream_events.py` | Structured streaming events — the agent→gateway delivery contract. |
| `streaming_tts_consumer.py` | Gateway streaming-TTS consumer — LLM deltas to adapter PCM audio sink. |
| `stuck_loop_counts.py` | Persisted per-session restart-failure counters (``.restart_failure_counts``, #7536). |
| `systemd_notify.py` | Minimal, optional systemd ``sd_notify`` support for the gateway. |
| `systemd_stop_mark.py` | Mark a supervisor-ordered stop as planned so SIGTERM exits cleanly. |
| `turn_context.py` | Per-turn context shared between ``GatewayRunner._run_agent_inner`` and ``TurnRunner``. |
| `turn_executor.py` | Unbounded executor for gateway turn bodies (see ``GatewayRunner._get_executor`` in gateway/run.py). |
| `turn_lease.py` | Per-session turn lease — serializes the [load history -> run -> flush] region. |
| `turn_thread_reset.py` | Make a reused turn-executor thread look like a new one to its next item. |
| `wake.py` | Wake an existing agent session from a background completion event. Push-capable adapters (``supports_async_delivery``) get a synthetic ``MessageEvent(internal=True)`` via handle_message; stateless adapters (API server)… |
| `warning_notifications.py` | Delivery policy for engine diagnostics, never assistant or command responses. |
| `webapp_listener.py` | The browser-hosted Desktop (Webapp) on the gateway's own HTTP listener. |
| `whatsapp_identity.py` | Shared helpers for canonicalising WhatsApp sender identity. |
