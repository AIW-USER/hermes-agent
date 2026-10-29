# File reference: `tools`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | tools/ + toolsets.py + model_tools.py — model tools |
| `__init__.py` | Tools package namespace. Kept side-effect free: importing ``tools`` must not load the tool stack (some subsystems import it while ``hermes_cli.config`` is still initializing). Import concrete submodules directly. |
| `annotate_preview_tool.py` | Persistent element annotations in the Hermes desktop GUI's in-app browser. |
| `ansi_strip.py` | Strip ANSI escape sequences from subprocess output so they never reach the model's context (models otherwise copy them into file writes). Covers full ECMA-48: CSI, OSC (BEL/ST), DCS/SOS/PM/APC, nF, Fp/Fe/Fs and 8-bit C1… |
| `approval.py` | Dangerous command approval -- the gate flow and per-session state. |
| `approval_context.py` | Approval context: who is asking, from where, under which policy. |
| `approval_detection.py` | Dangerous-command detection: normalization, tokenizing, and pattern tables. |
| `approval_floors.py` | Pre-gate floors for :mod:`tools.approval`: decisions that never reach a prompt. |
| `approval_gateway_wait.py` | Blocking gateway approval wait for :mod:`tools.approval`. |
| `approval_human_wait.py` | Human-wait accounting for :mod:`tools.approval` (per session). |
| `approval_prompt.py` | Human prompt surfaces for :mod:`tools.approval`. |
| `approval_smart.py` | Smart approval: auxiliary-LLM risk assessment for :mod:`tools.approval`. |
| `approval_yolo.py` | Session ``/yolo``: the one toggle / restore / carry contract every surface calls. |
| `arg_coercion.py` | Tool-argument type coercion: repair string-typed values the model emitted against a tool's JSON Schema. |
| `async_delegation.py` | Async (background) delegation registry behind ``delegate_task(background=true)``. |
| `async_delegation_recovery_hints.py` | Forensic hints attached to an abandoned-delegation recovery event. |
| `async_delegation_worker.py` | Process-bound worker ledger routing through the existing durable outbox. |
| `audio_container.py` | Shared magic-byte audio/AV container detection — the ONE sniffer for the codebase. |
| `binary_extensions.py` | Binary file extensions to skip for text-based operations (ported from free-code src/constants/files.ts). |
| `blueprints.py` | Blueprints: shareable plain-language automations layered on skills + cron. |
| `bot_desktop/__init__.py` | Bot Desktop: per-profile headless Xfce desktop over RFB, viewed from Hermes Desktop. |
| `bot_desktop/browser.py` | The bot's browser on its Bot Desktop: one executable, one persistent user-data-dir per profile. |
| `bot_desktop/install.py` | Install the Bot Desktop packages on the gateway host from a Desktop client. |
| `bot_desktop/launcher.sh` | Hermes Bot Desktop — one headless Xfce desktop per Hermes profile, served over RFB. |
| `bot_desktop/lease.py` | Who may drive a profile's Bot Desktop screen: the agent (default) or exactly one human viewer. |
| `bot_desktop/placement.py` | Where this profile's desktop lives: the gateway host or inside the configured terminal backend. |
| `bot_desktop/resources.py` | Host resources the screen needs before it starts: memory. |
| `bot_desktop/rfb_filter.py` | Byte-level RFB client→server gate for the Bot Desktop WebSocket bridge. |
| `bot_desktop/runtime.py` | Bot Desktop runtime: one headless Xfce desktop per Hermes profile, served over RFB on a private Unix socket, viewed and driven from Hermes Desktop. |
| `bot_desktop/sandbox_host.py` | Bot Desktop hosted INSIDE the configured terminal backend (docker / ssh / a plugin backend with streams). |
| `bot_desktop/thumbnail.py` | Thumbnail of a bot's screen: one JPEG grab of the profile's Xvnc display. |
| `bot_desktop/wallpaper.png` | PNG image asset |
| `bot_failure_reasons.py` | Typed failure-reason codes for bot turns and relay replies. |
| `bot_live_delivery.py` | Canonical Bot Chat transport and durable legacy delivery receipts. |
| `bot_mode_dm.py` | Bot Mode agent-to-agent DM tool — ``message_agent``. |
| `bot_mode_probe.py` | Bot Mode roster probe — canonical Bot Chat system prompt section. |
| `bot_relay.py` | Bot Mode cross-connection relay — connections ARE the peer set. |
| `browser_cdp_tool.py` | Raw Chrome DevTools Protocol (CDP) passthrough tool ``browser_cdp``. |
| `browser_dialog_tool.py` | Agent-facing tool: respond to a native JS dialog captured by the CDP supervisor. |
| `browser_harness_dirs.py` | Per-profile runtime and tmp dirs for browser-harness daemons (Browser Use mode). |
| `browser_launcher.py` | Launch, track and stop the Chromium processes ``browser_exec`` drives. |
| `browser_launcher_holders.py` | Cross-process holders of a shared-profile Chromium (``tools/browser_launcher.py``). |
| `browser_lightpanda.py` | Lightpanda local engine. |
| `browser_session.py` | Browser sessions for ``browser_exec``: one session per cache key, created in a fixed precedence and always carrying a ``cdp_url``. |
| `browser_session_cdp.py` | User-supplied CDP endpoints (live ``/browser connect``, ``BROWSER_CDP_URL``, ``browser.cdp_url``), dialog-policy config and the per-task CDP supervisor lifecycle. |
| `browser_session_cloud.py` | ``browser.*`` config knobs and cloud browser provider resolution (explicit ``browser.cloud_provider``, auto-detect, per-profile cache). |
| `browser_session_lifecycle.py` | Browser session lifecycle: inactivity janitor, orphan reap, per-session teardown, ``cleanup_*`` entry points and the atexit sweep. |
| `browser_session_real_profile.py` | Real-profile local browsing: snapshot the user's default Chromium profile into a Hermes-owned copy and launch the user's REAL browser binary on it through the launcher. |
| `browser_session_sandbox.py` | The bot's Chromium INSIDE the terminal backend's sandbox (Bot Desktop placed there). |
| `browser_supervisor.py` | Persistent CDP supervisor for browser dialog + frame detection. |
| `browser_supervisor_capture.py` | Captured CDP connection handle for trusted in-process plugins. |
| `browser_supervisor_dialogs.py` | Dialog capture + response half of the CDP supervisor. |
| `browser_supervisor_frames.py` | Frame / OOPIF target tracking half of the CDP supervisor. |
| `browser_tool.py` | Frozen old-updater compatibility stub (tests/compat/old_updater_surface.json, ``bare`` list). |
| `browser_tool_install.py` | Frozen old-updater compatibility stub (tests/compat/old_updater_surface.json, ``bare`` list). |
| `browser_url_policy.py` | URL safety for ``browser_exec`` (pre-scan of URL literals, hybrid local routing) and the SSRF helpers ``browser_cdp`` uses on raw CDP calls. |
| `browser_use_cli.py` | ``browser_exec``: drive a real browser through the Browser Use CLI engine (browser-harness, https://browser-use.com), Hermes' only core browser tool. |
| `browser_use_shot.py` | Screenshot and tab helpers that browser_exec installs over browser-harness's own. |
| `browser_vault_context.py` | Run a vault fill, or an automatic one-time-code entry, inside the selected backend's ``fill_context`` (a plugin backend's lock/snapshot/manager session). |
| `browser_vault_tool.py` | Vault-backed model-blind browser autofill tools. |
| `budget_config.py` | Configurable budget constants for tool result persistence. Per-tool resolution: pinned > config overrides > registry > default. |
| `checkpoint_maintenance.py` | Checkpoint store retention, orphan pruning, status and cleanup. |
| `checkpoint_manager.py` | Checkpoint Manager — Transparent filesystem snapshots via a single shared shadow git store. |
| `checkpoint_manager_profile_rename.py` | Rekey profile-local checkpoint projects after a named profile directory moves (#112973). |
| `checkpoint_pruning.py` | Checked history rewrites shared by snapshot limits and store maintenance. |
| `clarify_batch.py` | The terminal result of a batch clarify, shared by every registry that holds one. |
| `clarify_gateway.py` | Gateway-side clarify primitive (blocking event-based queue). The agent runs on a worker thread while the event loop handles the user's reply, so a pending clarify is stored module-level (same shape as ``tools.approval``… |
| `clarify_tool.py` | Clarify tool: structured multiple-choice / open-ended questions to the user. Schema, validation and a thin dispatcher; the UI lives in a platform-provided callback (cli.py, gateway/run.py, tui_gateway). |
| `close_preview_tool.py` | Close the Hermes desktop GUI's preview pane, or one tab (``preview.close``). Registration lives in `desktop_preview`. The renderer drops the matching tab — or the whole pane when no url is given — only for the window th… |
| `close_terminal_tool.py` | Close a read-only agent terminal tab in the Hermes desktop GUI WITHOUT killing the mirrored ``terminal(background=true)`` process (output keeps buffering; the user can reopen it). Routes through the process registry's `… |
| `code_execution_env.py` | Child-process environment for execute_code: env scrubbing, interpreter and cwd resolution. |
| `code_execution_rpc.py` | Host-side RPC servers for execute_code sandboxes. |
| `code_execution_tool.py` | Code Execution Tool -- Programmatic Tool Calling (PTC). |
| `code_kernel.py` | Session-persistent Python kernels for execute_code: one child per (owner, mode, interpreter, cwd, tool-set), one code cell per call, state survives across calls. |
| `code_kernel_remote.py` | Session-persistent kernels for REMOTE terminal backends (docker/ssh/modal). |
| `computer_use/__init__.py` | Computer use toolset — universal (any-model) desktop control via cua-driver. |
| `computer_use/backend.py` | Abstract backend interface for computer use. Any implementation (cua-driver over MCP, a plugin driver, the test noop) returns the shapes below. All methods are synchronous; async is handled inside the backend implementa… |
| `computer_use/cua_backend.py` | Cua-driver backend (macOS, Windows, Linux): MCP over stdio to `cua-driver`. The async `mcp` SDK runs on a background loop (``cua_backend_session``); the same tool surface works on all three platforms, and per-host gaps… |
| `computer_use/cua_backend_capture.py` | Capture side of the cua-driver backend: window discovery, capture-target selection and capture()/list_windows()/ list_apps()/focus_app() (mixed into ``CuaDriverBackend``). Logger name stays ``tools.computer_use.cua_back… |
| `computer_use/cua_backend_daemon.py` | Private embedded cua-driver daemon for non-standard permission modes, plus the macOS CuaDriver.app identity checks its launch path depends on. Config/policy helpers are looked up lazily through the facade. |
| `computer_use/cua_backend_driver.py` | PM-backed cua-driver selection, MCP discovery and the runtime contract gate. Config-derived policy (``_cua_no_overlay``, ``_run_driver`` ...) is looked up lazily through the facade. |
| `computer_use/cua_backend_input.py` | Input side of the cua-driver backend: delivery-mode handling and the pointer / keyboard / value-setter methods (mixed into ``CuaDriverBackend``). |
| `computer_use/cua_backend_parse.py` | Pure parsing helpers for the cua-driver backend: MCP result flattening, ``list_windows`` / ``get_window_state`` payload normalisation, key combos. No I/O, no module state — every function depends only on its inputs, so… |
| `computer_use/cua_backend_session.py` | cua-driver MCP session plumbing: the asyncio bridge thread and the lazily-started, self-healing ``_CuaDriverSession`` (MCP transport with a ``cua-driver call`` CLI fallback). Config/policy helpers are looked up lazily t… |
| `computer_use/doctor.py` | `hermes computer-use doctor` — thin client for cua-driver's `health_report` MCP tool. cua-driver owns the health model; we drive the stdio JSON-RPC handshake, call `health_report` and render the stable ``schema_version=… |
| `computer_use/permissions.py` | Cross-platform Computer Use readiness + macOS permission helpers. "Ready to drive" differs per platform: macOS needs explicit TCC grants (Accessibility + Screen Recording) via cua-driver ``permissions status`` / ``permi… |
| `computer_use/schema.py` | Schema for the generic `computer_use` tool (model-facing; value is byte-frozen — the schema goes to the model every turn, so prompt-cache parity depends on it). |
| `computer_use/tool.py` | `computer_use` tool entry point: any-model desktop control (macOS/Windows/Linux) via cua-driver. Return contract: text-only results are a JSON string; captures / `capture_after=True` return ``{"_multimodal": True, "cont… |
| `computer_use_tool.py` | Discovery shim: tools.registry auto-imports ``tools/*.py``, so this top-level module registers ``computer_use`` for the ``tools/computer_use/`` package. |
| `connectors/__init__.py` | Connector integration boundary for managed gateway accounts and local MCP servers. |
| `connectors/account.py` | Defines `AccountOperationStart`, `_matching_open_operation`, `find_or_start_operation`, `_run`, `wait_for_prepare` |
| `connectors/catalog.py` | ``manage_catalog`` install targets: catalog plugins and hub skills, installed through the card. |
| `connectors/catalog_tool.py` | ``manage_catalog``: a desktop chat's catalog search and install-through-the-card. |
| `connectors/contract.py` | Connection contract: the states a target moves through, who may cause each move, and the reasons an operation settles. ``operation.py`` enforces it; the desktop reads a generated copy. |
| `connectors/data_use.py` | Data-use requirements of connector results, collected while one tool call dispatches. |
| `connectors/dispatch.py` | Route connector calls through the normal dispatch policy pipeline. |
| `connectors/display.py` | ``manage_connections`` action ``display``: the desktop's browsable connector card. |
| `connectors/gateway/__init__.py` | Connector tool-gateway package: typed client-side plumbing for remote tools. |
| `connectors/gateway/bridge.py` | Defines `ConnectorLeg`, `_leg_failure`, `_default_client_factory`, `connector_search_hits`, `connector_describe`, `run_remote` … |
| `connectors/gateway/client.py` | HTTP client for managed gateway connector routes. |
| `connectors/gateway/config.py` | Configuration and availability gate for connector tools. |
| `connectors/gateway/errors.py` | Gateway HTTP errors and envelope parsing. |
| `connectors/gateway/files.py` | File inputs and outputs of connector tools. |
| `connectors/gateway/merge.py` | Pure partitioning, result splicing, and rendering for mixed tool-call batches. |
| `connectors/gateway/names.py` | Codec for model-facing connector tool names. |
| `connectors/gateway/wire.py` | Wire models for the gateway connector routes. |
| `connectors/live.py` | Live operations, one open per (profile, session), found by ``op_id``. The RPC layer reads and drives operations through here; the tool thread that minted one closes it on settle. |
| `connectors/managed.py` | Defines `managed_client`, `managed_kind`, `_note_connected`, `_status_by_slug`, `mint`, `_status_for` … |
| `connectors/mcp.py` | Defines `_catalog_names`, `_configured_names`, `validate_mcp_names`, `_catalog_entry`, `_CatalogBackend`, `_check_declared` … |
| `connectors/mcp_oauth.py` | MCP OAuth worker and callback receivers used by connection cards and gateway RPC flows. |
| `connectors/operation.py` | One backend-owned connection operation per ``manage_connections`` call. Pure data; its only I/O is one local log line per state change and per settle. |
| `connectors/portal/__init__.py` | Package marker / package-level exports |
| `connectors/portal/client.py` | Defines `Transport`, `NotModified`, `validate_slug`, `_default_transport`, `_default_endpoint_resolver`, `_default_header_provider` … |
| `connectors/portal/errors.py` | Defines `InvalidConnectorSlug`, `PortalConnectorUnavailable`, `PortalToolsUnavailable` |
| `connectors/portal/policy.py` | Defines `InvalidMemberPolicy`, `_layer`, `_slug`, `_validated_tools`, `compose_connector_write`, `compose_tools_write` |
| `connectors/portal/tools_cache.py` | Defines `ToolsClient`, `ToolsRead`, `_member_key`, `_cache_path`, `_cached`, `_store` … |
| `connectors/portal/wire.py` | Defines `_PortalWire`, `ConnectorTool`, `ConnectorToolsListing`, `ConnectorCatalogRow`, `ConnectorCatalogResponse`, `PolicyTags` … |
| `connectors/run.py` | The one lifecycle every ``manage_connections`` operation follows, whatever the target kind. |
| `connectors/search.py` | Defines `connections_in_scope`, `connectors_unavailable`, `_connector_entry`, `connector_entries_by_group`, `remote_schemas_for` |
| `connectors/targets.py` | Defines `HostedTarget`, `_bad_alias`, `normalize_targets`, `validate_action`, `_validate_accounts`, `catalog_names` … |
| `connectors/tool.py` | Connection lifecycle tool for managed gateway accounts and local MCP servers. |
| `connectors/turn.py` | Defines `connection_surface`, `agent_connection_surface`, `side_agent_tool_drops`, `scoped_connection_surface` |
| `credential_files.py` | File passthrough registry for remote terminal backends (Docker, Modal, SSH). |
| `cronjob_job_args.py` | Cron job argument normalization, validation and result shaping (re-exported by tools/cronjob_tools.py). |
| `cronjob_prompt_scan.py` | Cron prompt threat scanning: the small user-authored prompt gets the strict pattern set; the assembled prompt (with skill bodies) gets only prose-proof directives. |
| `cronjob_tools.py` | Cron job management tool: one compressed action-oriented `cronjob_manage` tool (schema/context bloat avoided); `cronjob()` stays callable for direct Python callers. |
| `daemon_pool.py` | Shared daemon-thread ThreadPoolExecutor. |
| `debug_helpers.py` | Shared per-tool debug session: records tool calls to a JSON log when a tool-specific env var (e.g. WEB_TOOLS_DEBUG=true) is set; no-ops otherwise. |
| `delegate_tool.py` | Delegate Tool -- Subagent Architecture |
| `delegate_tool_child_run.py` | Running ONE pre-built child agent: heartbeat, registry entry, workspace seeding, timeout/failure handling, result-entry assembly and cleanup (``_ChildRun``). |
| `delegate_tool_config.py` | Delegation config knobs (delegation.* keys) and child credential/provider resolution. |
| `delegate_tool_dispatch.py` | Batch execution + background dispatch for delegate_task: ``delegate_task`` builds a ``_Batch`` (children + origin identity) and hands it to ``_run_batch``, which runs it synchronously or as detached async units — one pe… |
| `delegate_tool_progress.py` | Child progress relay, console formatting and child system-prompt construction for delegate_task. |
| `delegate_tool_registry.py` | Live-subagent registry + model-facing control plane (list/steer/stop) for delegate_task. |
| `delegate_tool_results.py` | Subagent result post-processing: summary budget/spill, tool-trace summaries, lifecycle hooks and cost rollup. |
| `delegate_tool_routes.py` | Per-task child routes from the active delegation provider (``delegation.backend``). |
| `delegate_tool_tasks.py` | delegate_task input validation: tasks=[...] / legacy goal normalisation, per-task output schemas and images. |
| `delegate_tool_toolsets.py` | Child toolset resolution for delegate_task: what a child may and may never use. |
| `delegate_tool_tuning.py` | Speed tier for ``delegate_task`` children. |
| `delegation_live_log.py` | Live, tail-able transcripts for delegated subagents. |
| `delegation_output_schema.py` | Structured-output schema helpers for delegate_task. |
| `delegation_redaction.py` | Delegation-owned output projections, using the existing text redactor. |
| `desktop_ui.py` | Bridge desktop-only tools to Hermes-desktop renderer events. |
| `discord_tool.py` | Discord server introspection and management tool (REST API + bot token). |
| `drive_preview_tool.py` | Interact with the in-app browser / preview pane in the Hermes desktop GUI (click, type, scroll). |
| `env_passthrough.py` | Environment variable passthrough registry: the session-scoped allowlist of vars a skill's ``required_environment_variables`` (registered by ``skill_view``) or ``terminal.env_passthrough`` in config.yaml may forward into… |
| `env_probe.py` | Local-environment toolchain probe for the system prompt: when the terminal backend is local, one deterministic line about Python tooling (python3/python versions, missing pip, pip bound to another Python, PEP 668) so mo… |
| `environments/__init__.py` | Hermes execution environment backends: one BaseEnvironment ABC for running shell commands in a specific context (local, Docker, SSH, Modal direct/Nous-managed, Daytona, Vercel Sandbox; plugin backends register through `… |
| `environments/base.py` | Base class for all Hermes execution environment backends. |
| `environments/base_output.py` | Process-handle plumbing for ``tools.environments.base``. |
| `environments/base_session_env.py` | Bash session-snapshot scripting for ``tools.environments.base``. |
| `environments/base_wait.py` | Opt-in interrupt/poll tracing for ``BaseEnvironment._wait_for_process`` (``HERMES_DEBUG_INTERRUPT=1``): loop entry/exit, interrupt/timeout detection and ~30s heartbeats so "agent never sees the interrupt" reports can be… |
| `environments/daytona.py` | Daytona cloud execution environment. |
| `environments/docker.py` | Docker execution environment for sandboxed command execution. |
| `environments/docker_egress.py` | Egress-proxy (iron-proxy) plumbing for the Docker backend. |
| `environments/docker_ownership.py` | Hand root-written sandbox files back to the host user when a root Docker container is removed. |
| `environments/fd_wait.py` | POSIX fd-readiness helper shared by the stdout drains and the PTY bridge. |
| `environments/file_sync.py` | Shared file sync manager for remote execution backends. |
| `environments/local.py` | Local execution environment — spawn-per-call with session snapshot. |
| `environments/local_env_policy.py` | Secret-scrub policy for Hermes child processes: pure data + predicates for which env names are Hermes-managed credentials. The env *builders* applying it (``_make_run_env``, ``_sanitize_subprocess_env``, ``hermes_subpro… |
| `environments/local_pythonpath.py` | Hermes-owned PYTHONPATH stripping for child processes. Launchers prepend the repo root and the Hermes venv's site-packages so the backend can ``import tools``; leaked into a child Python of a DIFFERENT version they load… |
| `environments/managed_modal.py` | Managed Modal environment backed by tool-gateway. |
| `environments/modal.py` | Modal cloud execution environment using the native Modal SDK directly (``Sandbox.create()`` + ``Sandbox.exec()``) with persistent snapshots across sessions. |
| `environments/path_utils.py` | Path-component helpers shared by execution environment backends. Kept separate from the base class so lazy backend imports do not depend on newly added exports from a large module cached earlier in a long-lived process. |
| `environments/remote_common.py` | Helpers shared by the non-local terminal backends (docker, ssh, cloud SDKs). |
| `environments/ssh.py` | SSH remote execution environment with ControlMaster connection persistence. |
| `environments/streams.py` | A long-lived process INSIDE a terminal backend with both stdio pipes open. |
| `environments/vercel_sandbox.py` | Vercel Sandbox execution environment. |
| `escape_drift_autocorrect.py` | Conservative correction of escape drift before shared fuzzy matching. |
| `fal_common.py` | Shared FAL.ai SDK plumbing: lazy import, managed-gateway sync client, small helpers. |
| `feishu_doc_tool.py` | Feishu Document Tool -- read document content via Feishu/Lark API. |
| `feishu_drive_tool.py` | Feishu Drive Tools -- document comment operations via Feishu/Lark API. |
| `feishu_lark.py` | Shared lark_oapi plumbing for the feishu_doc / feishu_drive tool modules. |
| `file_operations.py` | File operations (read, write, patch, search) over any terminal backend. |
| `file_operations_common.py` | Result dataclasses and pure text helpers shared by ``tools.file_operations`` and its search/lint mixins. Leaf module (imports nothing from ``tools`` at module scope) so nothing cycles. The ``to_dict`` output of every cl… |
| `file_operations_lint.py` | Syntax-lint and LSP-diagnostics tier for ``tools.file_operations``. |
| `file_operations_native.py` | In-process write primitives for the local POSIX backend. |
| `file_operations_search.py` | Content/file search tier for ``tools.file_operations``. |
| `file_state.py` | Cross-agent file state coordination. |
| `file_tools.py` | File Tools Module - LLM agent file manipulation tools. |
| `file_tools_paths.py` | Path resolution for the file tools: task-aware base dir, ``~`` expansion, workspace-divergence warning. |
| `file_tools_read_tracking.py` | Per-task read/search bookkeeping for the file tools. |
| `file_tools_write_guards.py` | Write-side safety guards for write_file / patch. |
| `focus_pane_tool.py` | Reveal/focus a pane in the Hermes desktop GUI (``pane.reveal`` via ``desktop_ui``). |
| `fuzzy_match.py` | Fuzzy find-and-replace for LLM-generated edits. |
| `hook_output_spill.py` | Spill oversized hook-injected context to disk with a preview placeholder. |
| `human_input_hooks.py` | Plugin observers for every point where the agent blocks waiting on a human (#132333). |
| `image_generation_catalog.py` | FAL image model catalog + upscaler constants for ``tools.image_generation_tool``. |
| `image_generation_managed.py` | Managed ("Nous Subscription") image generation: one picker row, one model catalog. |
| `image_generation_tool.py` | Image generation via FAL.ai (model picked in ``hermes tools``, persisted to ``image_gen.model``). |
| `image_source.py` | Single resolver for every media source (data:/http(s)/file/local/container) -> bytes + mime. |
| `interpreter_shutdown.py` | Shared interpreter-shutdown predicate for background threads that can outlive process teardown (cron delivery, concurrent tool submission, retry paths). |
| `interrupt.py` | Per-thread interrupt signaling for all tools: thread-scoped so interrupting one agent session does not kill tools in other sessions (the gateway runs many agents in one process). The agent passes its execution thread id… |
| `kanban_tools.py` | Kanban tools — structured tool-call surface for worker + orchestrator agents. |
| `kanban_tools_schemas.py` | Tool schemas for tools.kanban_tools (model-facing; strings are byte-frozen). |
| `kanban_toolset_context.py` | Explicit Kanban selection during one model-schema build. |
| `lazy_deps.py` | Shims to suppress old updater work until relaunch. New code must not use these. |
| `managed_gateway_auth.py` | First-party gateway bearer trust, ported from connectors-only 43608084f4. |
| `managed_gateway_identity.py` | Caller identity for requests to the first-party gateways: who is calling, and which turn asked. |
| `managed_tool_gateway.py` | Generic managed-tool gateway helpers for Nous-hosted vendor passthroughs. |
| `mcp_dashboard_oauth.py` | Dashboard-mediated callback bridge for MCP OAuth: the SDK still does discovery, DCR, PKCE, state validation and token exchange; this only moves the two human/browser callbacks from a loopback listener into the already-a… |
| `mcp_death_supervisor.py` | One parent-death supervisor per Hermes process, shared by all stdio MCP servers. |
| `mcp_liveness.py` | Application-backed MCP liveness parsing and user-facing status descriptions. |
| `mcp_oauth.py` | MCP OAuth 2.1 client support: browser authorization-code flow with PKCE. |
| `mcp_oauth_device.py` | Explicit RFC 8628 MCP login, sharing SDK discovery, client auth and token storage. |
| `mcp_oauth_manager.py` | Central manager for per-server MCP OAuth state (one instance per process): per-server providers, cross-process token reload (mtime-based disk watch so tokens refreshed by cron/another CLI are picked up without a restart… |
| `mcp_oauth_provider.py` | Shared ``OAuthClientProvider`` customizations for Hermes MCP OAuth. |
| `mcp_schema_cache.py` | Persistent MCP tool-schema cache for lazy server startup: per-server tool manifests on disk so Hermes can register MCP tools into the agent snapshot without spawning the stdio child at idle dashboard startup. Entries ar… |
| `mcp_tool.py` | MCP (Model Context Protocol) client: connects to the ``mcp_servers`` configured in ~/.hermes/config.yaml (stdio, Streamable HTTP or SSE), discovers their tools and registers them into the hermes tool registry. The ``mcp… |
| `mcp_tool_agent.py` | Live-agent tool-list maintenance after MCP (re)discovery: refreshing an AIAgent's tools/tool names, preserving the cached tools[] prefix across rebuilds, and re-injecting post-build tools. |
| `mcp_tool_common.py` | Small pure helpers shared by the tools.mcp_tool_* modules: SDK 1.x/2.x field access, error-text sanitising, numeric/bool coercion, timeouts and jitter. No origin state. |
| `mcp_tool_config.py` | MCP server config loading and stdio launch environment: ${VAR}/Cursor-style interpolation, hidden-whitespace and suspicious-entry filtering, the filtered subprocess env, command resolution, the cached-npx binary shortcu… |
| `mcp_tool_content.py` | Rendering of MCP tool-result content blocks into model-facing text: size capping, _meta filtering, image/audio caching to MEDIA tags, resource links and embedded resources. |
| `mcp_tool_costs.py` | Declared per-tool MCP costs and the per-chat spend tally behind the budget gate. |
| `mcp_tool_discovery.py` | Connecting and discovery for tools.mcp_tool: per-server connect cooldown, connect / lazy-start / recycled-stdio wake-up, ``register_mcp_servers`` / ``discover_mcp_tools`` and the status / probe public API. Origin state… |
| `mcp_tool_errors.py` | MCP connection/transport error classification: URL validation, TLS client certs, identity headers, redirect header stripping, exception-group unwrapping, auth/session-expired/ method-not-found detection and connect-erro… |
| `mcp_tool_events.py` | MCP Events client, webhook delivery (the experimental ``events/*`` extension of the Triggers & Events WG: modelcontextprotocol/experimental-ext-triggers-events ``docs/design-sketch-proposal.md``). |
| `mcp_tool_handlers.py` | Registry-facing sync handlers for MCP tools and utility tools (resources/prompts), plus the per-call recovery ladder: trust gating, circuit breaker, auth (401) refresh, session-expired reconnect and dead-stdio respawn r… |
| `mcp_tool_health.py` | Session health for MCPServerTask: dynamic tool refresh on list_changed notifications, server log forwarding, keepalive probes, suspect-mark / lazy-verify, in-flight call fail-fast, stdio child liveness and stdio idle/li… |
| `mcp_tool_lifecycle.py` | MCP process lifecycle: stdio child PID tracking and orphan cleanup, graceful server shutdown and draining of the background MCP loop. |
| `mcp_tool_loop.py` | Background-loop plumbing for tools.mcp_tool: cross-process discovery file lock, scheduling coroutines onto the MCP loop from caller threads (with profile HOME override and dashboard OAuth flow propagation) and the loop'… |
| `mcp_tool_node_abi.py` | Stdio MCP servers whose native addon was built for a different Node.js (#124264). |
| `mcp_tool_registration.py` | Registering a connected (or schema-cached) MCP server's tools into the tool registry: include/exclude filtering, trust-tier metadata capture, utility-tool selection, name-collision resolution and the schema-cache write-… |
| `mcp_tool_sampling.py` | MCP client-side handlers for server-initiated requests: sampling (sampling/createMessage, text and tool-use results) and elicitation. |
| `mcp_tool_schema.py` | MCP tool schema conversion and naming: JSON-schema normalisation for provider compatibility, mcp__server__tool naming, utility-tool schemas, include/exclude filters and description injection scanning. |
| `mcp_tool_scope.py` | Connection-ledger keys for tools.mcp_tool under a profile multiplexer. |
| `mcp_tool_server_run.py` | Lifecycle of :class:`tools.mcp_tool.MCPServerTask`: the long-lived ``run`` state machine (connect -> serve -> reconnect/park/recycle), keepalive-driven lifecycle waits, start/shutdown and tool deregistration. Origin sta… |
| `mcp_tool_transport.py` | Transport bring-up for MCPServerTask: stdio spawn (OSV preflight, cached-npx swap, child PID ledger + death-supervisor registration), Streamable HTTP / SSE connect (preflight, identity header, client certs, OAuth), prot… |
| `memory_tool.py` | Memory Tool - persistent curated memory (MEMORY.md = agent notes, USER.md = user profile). Both enter the system prompt as a FROZEN snapshot at session start; mid-session writes hit disk but never change the prompt (pre… |
| `memory_tool_store.py` | MemoryStore — bounded, file-backed curated memory (MEMORY.md / USER.md). Entries are joined by ``ENTRY_DELIMITER``; budgets are in chars (model-independent). Module state that tests monkeypatch (``get_memory_dir``, ``fc… |
| `microsoft_graph_auth.py` | Microsoft Graph app-only (client-credentials) authentication helpers. |
| `microsoft_graph_client.py` | Reusable Microsoft Graph REST client helpers. |
| `neutts_samples/jo.txt` | Plain-text file |
| `neutts_samples/jo.wav` | Audio asset |
| `neutts_synth.py` | Standalone NeuTTS synthesis helper. |
| `open_preview_tool.py` | Open a URL, dev server, or file in the Hermes desktop GUI's preview pane. |
| `openrouter_client.py` | OpenRouter API key probe shared by Hermes tools. |
| `osv_check.py` | OSV malware check for MCP extension packages. |
| `patch_parser.py` | V4A patch parser/applier (codex, cline). ``*** Begin Patch``/``*** End Patch`` wrap ops: ``*** Update File: p`` + hunks (``@@ hint @@``, `` ctx``, ``-old``, ``+new``); ``*** Add File: n`` + ``+`` lines; ``*** Delete Fil… |
| `path_security.py` | Shared path validation helpers for tool implementations (skills, cron, credential files). |
| `plugin_guard.py` | Plugin Guard — ``skills_guard`` engine applied to ``hermes plugins install``/``update``. |
| `plugin_guard_context.py` | Context demotions for plugin install-scan findings (``tools.plugin_guard``). |
| `preview_tool.py` | The `desktop_preview` tool — the preview pane beside the chat, as ONE tool. |
| `process_registry.py` | Process Registry -- in-memory registry for background processes spawned via terminal(background=true): rolling 200KB output buffer, poll/log/wait/kill, JSON checkpoint for crash recovery, session-scoped tracking for gat… |
| `process_registry_awaiting.py` | Whether a background process will still report back to the agent that spawned it. |
| `process_registry_checkpoint.py` | Running-process checkpoint persistence and PID-safe recovery. |
| `process_registry_env_log.py` | Incremental sandbox log reads for ProcessRegistry's non-local poller. |
| `process_registry_notifications.py` | Human-readable rendering of ``ProcessRegistry.completion_queue`` events (completion, watch_match, watch_disabled, watch_overflow_*, async_delegation) into the ``[IMPORTANT: ...]`` / ``[ASYNC DELEGATION ...]`` text the C… |
| `process_registry_output_log.py` | File-backed output for background processes a registered worker starts. |
| `process_registry_results.py` | Bounded, profile-local receipts for completed terminal processes. |
| `process_registry_stdin.py` | Why a background process has no writable stdin, phrased as the fix the agent can act on. |
| `process_registry_termination.py` | Process-tree termination and post-kill survivor verification for ProcessRegistry. |
| `process_registry_wait_policy.py` | Stop repeated ``process_manage`` wait/poll calls on a silent running process. |
| `process_registry_wsl.py` | Detect background spawns routed through a ``wsl[.exe]`` launcher chain (#120546). |
| `project_tools.py` | Project tools — the agent's INTENTIONAL handle on first-class Projects (per-profile ``projects.db``, the desktop sidebar's named workspaces). Creating/switching is an explicit tool call, never a side effect of ``cd``. G… |
| `pty_query_responder.py` | Answer a bounded set of blocking terminal queries from PTY subprocesses. |
| `react_to_message_tool.py` | Agent emoji reaction in the Hermes desktop app: the counterpart to the user's tapback (same store, one-per-author, ``author="agent"``). Lives in the ``desktop_ui`` toolset so it costs nothing elsewhere (adapters expose… |
| `read_extract.py` | Document-to-text extraction for ``read_file``: stdlib Jupyter/DOCX/XLSX (always authoritative for those three), plus legacy Office/OpenDocument/RTF/EPUB/PDF when the optional ``firecrawl-anydoc`` package (imports as ``a… |
| `read_preview_tool.py` | Read the in-app browser / preview pane in the Hermes desktop GUI. |
| `read_terminal_tool.py` | Read the in-app terminal pane in the Hermes desktop GUI. |
| `read_window_tool.py` | Read which OS window sits directly underneath the Hermes desktop window. |
| `registry.py` | Central registry for all hermes-agent tools: each tool file calls ``registry.register()`` at import to declare schema, handler, toolset membership and availability check; ``model_tools.py`` queries the registry instead… |
| `schema_sanitizer.py` | Sanitize tool JSON schemas for strict LLM backends. llama.cpp's grammar converter fails on ``{"type": "object"}`` without ``properties``, bare-string schemas and ``type`` arrays; Anthropic rejects nullable ``anyOf`` at… |
| `self_repo_guard.py` | Detect Git operations that can rewrite the checkout backing this process. |
| `send_message_senders.py` | Standalone per-platform senders and error helpers for send_message. |
| `send_message_targets.py` | Target parsing and resolution for send_message (platform:chat_id[:thread] → ids). |
| `send_message_tool.py` | Send Message Tool -- cross-channel messaging via platform APIs (send, list targets, react); works in both CLI and gateway contexts. |
| `session_search_tool.py` | Session Search Tool - long-term conversation recall over the SQLite session DB. |
| `set_theme_tool.py` | Set the Hermes desktop app's accent colour, light/dark mode and layout, or show a picker card. |
| `setup_beat_tool.py` | ``setup_beat``: the one onboarding-only tool. It shows a beat's card through the desktop, waits for the user (``CARD_TIMEOUT_S``), and returns their answer with a short reminder of the next beat. |
| `shell_heredoc.py` | Conservative heredoc masking for shell-command scanners ('&' guard, blocked-command checks, cron lifecycle_guard) that false-positive on heredoc *bodies*. Stripping every body is unsafe the other way (a fake ``<<`` in q… |
| `skill_ledger.py` | Per-mutation skill audit ledger + single-edit rollback. |
| `skill_linter.py` | Structural + convention linter for SKILL.md files. |
| `skill_manager_batch.py` | Atomic multi-op batch path for ``skill_manage``. Origin state (``skill_manage``/``_find_skill``/``_skill_gate_bypass``) is reached lazily through ``tools.skill_manager_tool`` so that module owns it. |
| `skill_manager_guards.py` | Write/delete guards for ``skill_manage``. Every guard returns ``None`` when the operation may proceed, else a refusal (error dict or message). Origin-owned state (``_find_skill``, ``_skills_dir``) is reached lazily via… |
| `skill_manager_tool.py` | Skill Manager Tool — agent-managed skill creation & editing. |
| `skill_provenance.py` | Skill write-origin provenance: a ContextVar separating background-review skill writes from foreground user-directed writes (the curator only curates skills the self-improvement review fork created; skills a user asked f… |
| `skill_usage.py` | Skill usage telemetry + provenance for the Curator: a sidecar ``~/.hermes/skills/.usage.json`` keyed by skill name (never frontmatter — keeps telemetry out of user-authored SKILL.md and off bundled/hub skills). Counter… |
| `skillevaluator_scan.py` | Advisory NVIDIA SkillEvaluator Tier 1 scan for skill installs — alongside (never instead of) skills_guard, the enforcement layer. Contract: warn, don't block (the upstream PII scanner false-positives on ``git@github.com… |
| `skills_ast_audit.py` | AST-level deep audit for skill Python files — opt-in diagnostic (``hermes skills audit --deep``), not a security gate (SECURITY.md §2.4). Flags dynamic import / attribute access for human review; every pattern has legit… |
| `skills_guard.py` | Skills Guard — regex static scan of externally-sourced skills plus a trust-aware install policy. |
| `skills_hub.py` | Skills Hub — hub state management and the public facade for the source adapters. |
| `skills_hub_clawhub.py` | Skills Hub ClawHub adapter (clawhub.ai HTTP API). |
| `skills_hub_github.py` | Skills Hub GitHub adapter: API auth, tap providers, and the Contents/Trees source. |
| `skills_hub_install.py` | Skills Hub install/uninstall/update operations: quarantine staging, install- target safety (symlink/junction, category-bucket and nested-skill checks), lock-file-backed uninstall, bundle hashing and upstream update chec… |
| `skills_hub_models.py` | Skills Hub data models, path validators, and SKILL.md helpers. Leaf module (no imports from tools.skills_hub) so every source adapter module can import it at top level without cycles. |
| `skills_hub_official.py` | Skills Hub official sources: repo-shipped optional skills and the centralized Hermes index. |
| `skills_hub_search.py` | Skills Hub discovery: the centralized Hermes index fetch (cached, stale- fallback), the source router, and parallel/unified search across source adapters. |
| `skills_hub_skillssh.py` | Skills Hub skills.sh adapter: catalog discovery via skills.sh, content via GitHub. |
| `skills_hub_sources.py` | Skills Hub adapters for well-known endpoints, direct URLs, LobeHub, and browse.sh. |
| `skills_sync.py` | Skills Sync -- manifest-based seeding and updating of bundled skills. Copies repo skills/ into ~/.hermes/skills/, tracking each synced skill's origin hash in .bundled_manifest (v2 "name:hash" lines; v1 plain names auto-… |
| `skills_sync_bundled_ops.py` | Bundled-skill maintenance ops: reset, diff, list-modified, opt-out, remove-pristine. Profile-scoped paths and patchable helpers resolve through ``_ss()`` at call time. |
| `skills_sync_optional.py` | Official optional-skill provenance: hub-lock backfill and restore. Profile-scoped paths and patchable helpers resolve through ``_ss()`` at call time so ``tools.skills_sync`` patches work. |
| `skills_tool.py` | Skills Tool — list and view skill documents (progressive disclosure). A skill is a directory holding SKILL.md (YAML frontmatter + instructions) plus optional references/, templates/, assets/, scripts/. `skills_list` ret… |
| `skills_tool_dedup.py` | skill_view repeat-view dedup registry: per-task cache of (resolved skill name, file_path) -> digest of the skill_view result served. A repeat view whose result is byte-identical returns a short stub — the earlier tool r… |
| `skills_tool_plugin.py` | Plugin-provided skill serving for ``skill_view`` (``plugin:skill`` names) plus the JSON / file-serving helpers shared with the local-skill path. Helpers tests patch on the origin module (``_is_skill_disabled``, ``_parse… |
| `skills_tool_setup.py` | Skill readiness: required env vars, secret capture, and setup notes. Split out of ``tools.skills_tool`` (names re-imported there); module state (``_secret_capture_callback``, ``load_env``) stays there and is read lazily… |
| `slash_confirm.py` | Generic slash-command confirmation primitive (gateway-side). |
| `spill_safety.py` | Symlink-safe creation helpers for spill/cache files under ``~/.hermes``, where a plain ``open(path, "w")`` would follow a pre-planted symlink onto ``~/.bashrc`` etc. New files use ``O_CREAT \| O_EXCL`` (fails on ANY exi… |
| `stt_lease.py` | Local-STT lifecycle for the desktop voice-input path: warm-up leases. |
| `subagent_worktree.py` | Opt-in git worktree isolation for delegated subagents (``delegation.worktree_isolation``). |
| `terminal_hints.py` | Output-pattern failure hints for the terminal tool. |
| `terminal_scope.py` | Per-turn terminal scope: profile-scoped TERMINAL_* policy. |
| `terminal_tool.py` | Terminal tool: run shell commands in the configured backend. |
| `terminal_tool_backends.py` | Execution-environment backends for the terminal tool: per-backend builders, config-to-kwargs shapers, and requirement checkers, routed by dispatch/spec tables. Split out of ``tools/terminal_tool.py``; the terminal tool… |
| `terminal_tool_background.py` | Background-process launch path: ``terminal(background=true)`` spawns a tracked process via the process registry (Popen locally, ``env.execute`` in a sandbox), stamps gateway routing metadata for completion / watch-patte… |
| `terminal_tool_config.py` | Terminal backend configuration: scope-aware TERMINAL_* reads, env-var parsing, container-cwd sanity checks, plugin-backend classification, and the ``_quiet`` best-effort block shared by the terminal_tool_* modules. |
| `terminal_tool_guards.py` | Pre-execution guards for the terminal tool. |
| `terminal_tool_lifecycle.py` | Sandbox lifecycle for the terminal tool: idle reaping, teardown, manual/atexit cleanup, and the lazy ensure_task_env bring-up. The env cache dicts and locks stay in tools.terminal_tool (tests patch them there) and are r… |
| `terminal_tool_macos_open.py` | macOS ``open`` frontmost raise-ladder for the terminal tool. |
| `terminal_tool_result.py` | Foreground result post-processing for the terminal tool (cwd dual-write, sudo handling, transform hook, truncation, ANSI strip, redaction, exit-code notes/hints, spill redaction, verification evidence) + exit-code table… |
| `terminal_tool_sudo.py` | Sudo password plumbing and shell-command rewrites for the terminal tool: per-scope password cache, /dev/tty prompt, the quote-aware shell scanner behind the real-sudo rewrite (``sudo -S -p ''``) and the compound-backgro… |
| `thread_context.py` | Propagate agent-turn context into worker threads that dispatch Hermes tools. |
| `threat_patterns.py` | Shared threat-pattern library (prompt injection / promptware / exfiltration) for ``agent/prompt_builder.py``, ``tools/memory_tool.py`` and ``agent/tool_dispatch_helpers.py``. Each pattern is ``(regex, pattern_id, scope)… |
| `tip_tool.py` | Point at something in the Hermes desktop GUI and say one line about it — the quiet sibling of ``tour`` (same ``data-tour`` handles) with no scrim/spotlight/paging. Fire-and-forget: a tip is not a question, so blocking o… |
| `todo_tool.py` | Todo tool: in-memory, revisioned task list for multi-step work. State lives on the AIAgent (one per session), is re-injected after context compression, and every write bumps a monotonic revision so UI clients can reject… |
| `tool_backend_helpers.py` | Shared helpers for tool backend selection. |
| `tool_labels.py` | Defines `ToolLabel`, `app_title`, `_action_phrase`, `_registry_emoji`, `_arg_preview`, `_local_tool_label` … |
| `tool_output_limits.py` | Configurable tool-output truncation limits (``tool_output`` in config.yaml): ``max_bytes`` (terminal output cap), ``max_lines`` (read_file pagination cap), ``max_line_length`` (per-line cap before '... [truncated]'). De… |
| `tool_output_truncate.py` | Head/tail truncation for oversized tool output (terminal, execute_code, MCP results). |
| `tool_result_storage.py` | Tool result persistence -- preserves large outputs instead of truncating. Layers against context overflow: (1) per-tool caps inside each tool; (2) ``maybe_persist_tool_result`` — output over the tool's threshold is pers… |
| `tool_search.py` | Progressive tool disclosure ("tool search"): MCP/plugin tools and a curated set of event-triggered core tools are replaced in the model-visible array by three bridge tools — tool_search / tool_describe / tool_call. Inva… |
| `tool_search_catalog.py` | Deferred-tool catalog for tool search: BM25 retrieval over deferrable tool defs plus the budgeted, byte-stable catalog listing embedded in the bridge. |
| `tool_search_validation.py` | Local argument validation for ``tool_call`` against a deferred tool's schema. |
| `tour_presets.py` | The built-in tour presets ``gui_tour`` start-without-steps accepts. |
| `tour_tool.py` | Guided tour (highlight + narrate UI elements) in the Hermes desktop GUI: ``start`` with no steps runs the app's own built-in tour (``preset`` quick or full); for a custom one the agent discovers targets (``action="targe… |
| `transcription_audio.py` | Audio preprocessing for STT. |
| `transcription_chunking.py` | Per-provider upload limits and long-audio splitting for cloud STT. |
| `transcription_cloud.py` | Cloud STT providers. |
| `transcription_command.py` | User-declared and plugin STT providers. |
| `transcription_common.py` | Constants, result envelopes and tiny config readers shared by every STT module. |
| `transcription_local.py` | Local STT backends. |
| `transcription_streaming.py` | Live speech-to-text: feed microphone PCM while the user speaks, get partial and final text. |
| `transcription_tools.py` | Speech-to-text transcription used by the gateway for voice messages. |
| `transcription_whisper_cpp.py` | Managed whisper.cpp command and first-use, verified model acquisition. |
| `tts_command_provider.py` | Shared runner for user-configured shell ("command") TTS/STT providers. |
| `tts_elevenlabs_voices.py` | ElevenLabs voice search behind ``text_to_speech``'s ``find_voices`` argument. |
| `tts_streaming.py` | Provider-agnostic streaming TTS: sentence text → int16 mono PCM chunk iterator. |
| `tts_text_normalize.py` | Deterministic cleanup turning assistant Markdown into a spoken script. |
| `tts_tool.py` | Text-to-speech tool: config resolution, built-in provider dispatch, output policy, registration. |
| `tts_tool_delivery.py` | Long-form chunking, ffmpeg encoding, container repair and delivery packing (``tools.tts_tool``). |
| `tts_tool_lifecycle.py` | Local-engine lifecycle for ``tools.tts_tool``: warm-up / release leases. |
| `tts_tool_local.py` | Local on-device TTS engines for ``tools.tts_tool``: NeuTTS, Piper, KittenTTS. |
| `tts_tool_openai.py` | OpenAI-compatible TTS backends for ``tools.tts_tool``: OpenAI and DeepInfra. |
| `tts_tool_plugins.py` | Plugin-registered TTS providers for ``tools.tts_tool``: routes ``tts.provider: <name>`` values that are neither built-in nor ``type: command`` to a plugin :class:`agent.tts_provider.TTSProvider`. Discovery goes through… |
| `tts_tool_providers.py` | Cloud TTS backends for ``tools.tts_tool``: Edge, ElevenLabs, xAI, MiniMax, Mistral, Gemini. |
| `tts_tool_speaker.py` | Speaker-side streaming pipeline: ``stream_tts_to_speaker``. |
| `url_safety.py` | URL safety checks — blocks requests to private/internal network addresses (SSRF). |
| `video_generation_tool.py` | ``video_generate``: one tool dispatching to a plugin-registered :class:`VideoGenProvider` (``agent/video_gen_provider.py`` ABC, ``agent/video_gen_registry.py``, ``plugins/video_gen/<name>/``). |
| `vision_tools.py` | Vision tools: ``vision_analyze`` (image) and ``video_analyze``. |
| `vision_tools_history_budget.py` | History-reuse budgets for native vision embeds (config section ``vision``). |
| `vision_tools_image_prep.py` | Image format detection, normalization and region cropping for vision tools. |
| `voice_client_config.py` | Resolve the active profile's STT/TTS config for CLIENT-DIRECT voice. |
| `voice_live.py` | GPT-Live voice chat mode: the full-duplex voice frontend that delegates to Hermes. |
| `voice_mode.py` | Voice Mode -- push-to-talk recording and playback for the CLI. |
| `voice_mode_transcript.py` | Pure-text helpers for voice mode: Whisper hallucination filter, voice-chat stop phrases, and the TTS self-echo guard. No audio dependencies. |
| `wake_word.py` | Wake-word ("Hey Hermes") detection — hands-free session trigger. |
| `wake_word_engines.py` | Wake-word hotword engines (pyopen-wakeword / sherpa-onnx KWS / Porcupine). |
| `wakewords/README.md` | Bundled wake-word models |
| `wakewords/hey_hermes.tflite` | TensorFlow Lite model (wake-word detection) |
| `web_result_cache.py` | Result caching for web_search / web_extract; both caches TTL-bounded (default 20 min, ``web.cache_ttl_minutes``; disable with ``web.cache_enabled: false``), only successful responses cache. * **Search memo** — in-memory… |
| `web_tools.py` | Generic web_search / web_extract tools over pluggable backends. |
| `web_tools_extract.py` | web_extract helpers: URL validation, provider resolution, cache-aware dispatch. |
| `web_tools_rescue.py` | One-shot keyless-ring rescue for failed keyed/configured web calls. |
| `web_tools_truncate.py` | Truncate-and-store pipeline for web_extract (no LLM). |
| `website_policy.py` | Website access policy helpers for URL-capable tools. |
| `working_diff.py` | Working-tree git diff collection shared by the CLI and gateway ``/diff``. |
| `write_approval.py` | Write-approval gate + pending store for memory and skill writes. |
| `x_search_tool.py` | X Search tool backed by xAI's built-in ``x_search`` Responses API tool. |
| `xai_http.py` | Shared helpers for direct xAI HTTP integrations. |
| `xai_video_tools.py` | xAI-specific Imagine video edit and extend tools. |
| `yuanbao_tools.py` | yuanbao_tools.py - 元宝平台工具集 (the "hermes-yuanbao" toolset). |
