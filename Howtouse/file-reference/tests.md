# File reference: `tests`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `tests/`

| File | What it does |
|---|---|
| `AGENTS.md` | tests/ — how Hermes tests are written and run |
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Shared fixtures for the hermes-agent test suite. |
| `file_write_observer.py` | Run a "concurrent reader" at the exact instant a writer emits bytes (torn-read regression tests). |
| `git_safety.py` | Classify accidental Git mutations before tests can touch their checkout. |
| `home_io_guard.py` | Guard Python filesystem calls in tests, not arbitrary native/subprocess I/O. |
| `installation_launcher_fixture.py` | A real published launcher driving a disposable CLI, without installing deps. |
| `live_process_fixtures.py` | Sleeper script used by the live process-topology E2Es to stand in for real Hermes processes. |
| `lock_contention.py` | Event-driven replacements for "give the other writer N seconds" in serialization tests. |
| `module_clock.py` | One module's view of ``time`` with a test-driven ``monotonic``. |
| `posix_lock_probe.py` | This process's POSIX advisory locks on a file, read from ``/proc/self/fdinfo`` (Linux). |
| `run_interrupt_test.py` | Run a real interrupt test with actual AIAgent + delegate child. |
| `termux_fixtures.py` | Small, structurally valid Termux archives with independent integrity checks. |
| `test_agent_close_lifecycle.py` | Side-agent AIAgent instances must be closed on every exit path (#50197). |
| `test_atomic_json_writers_unified.py` | Invariant for the non-secret atomic JSON writers that used to inline ``utils._atomic_write``. |
| `test_atomic_replace_symlinks.py` | Regression tests for GitHub #16743 — atomic writes must preserve symlinks. |
| `test_atomic_write_fsync_dir_target.py` | ``atomic_write_text(..., fsync_dir=True)`` must sync the directory that actually received the replacement file. |
| `test_atomic_write_text_metadata.py` | ``atomic_write_text``'s opt-in metadata preservation (mode + owner). |
| `test_audit_old_updater_imports.py` | Exercise updater archaeology against real Git DAGs, not today's filenames. |
| `test_base_url_hostname.py` | Targeted tests for ``utils.base_url_hostname`` and ``base_url_host_matches``. |
| `test_basetemp_isolation.py` | pytest's basetemp must never sit inside the operator's platform-native Hermes home. |
| `test_batch_runner_checkpoint.py` | Tests for batch_runner checkpoint behavior — incremental writes, resume, atomicity. |
| `test_batch_runner_discard_resume.py` | Discarded samples must be visible to --resume (#93527). |
| `test_batch_runner_durability.py` | Tests for batch_runner trajectory durability and pool cleanup. |
| `test_credential_file_permissions.py` | Read-time permission warnings for on-disk credential/token files. |
| `test_dispatch_session_id.py` | Tests that handle_function_call forwards session_id into registry.dispatch. |
| `test_display_hermes_home.py` | display_hermes_home() renders POSIX separators on every platform. |
| `test_engines_satisfiable.py` | The manifest's ``engines`` must be satisfiable by a toolchain we can actually ship. |
| `test_fast_safe_load.py` | Invariants for utils.fast_safe_load. |
| `test_get_tool_definitions_cache_isolation.py` | Regression tests for issue #17335. |
| `test_git_safety_boundary.py` | A removed live-checkout guard can damage only disposable repositories here. |
| `test_hermes_bootstrap.py` | Tests for hermes_bootstrap — Windows UTF-8 stdio shim. |
| `test_hermes_constants.py` | Tests for hermes_constants module. |
| `test_hermes_dir_acl.py` | ``make_user_dir`` contract off Windows and its grant selection (the Windows ACL effect itself is proved by ``test_hermes_dir_acl_windows.py`` on Windows CI). |
| `test_hermes_dir_acl_windows.py` | #139845 / #134889 W8 + W2 on real Windows ACLs. |
| `test_hermes_home_key_cache.py` | Tests for the remembered results in `hermes_home_key`. |
| `test_hermes_home_profile_warning.py` | Tests for get_hermes_home() profile-mode fallback warning. |
| `test_hermes_logging.py` | Tests for hermes_logging — centralized logging setup. |
| `test_hermes_yaml.py` | Contracts for Hermes' shared YAML reader and writer. |
| `test_ipv4_preference.py` | Tests for network.force_ipv4 — the socket.getaddrinfo monkey-patch. |
| `test_live_nous_services_fence.py` | No test reaches a live Nous service unless it is a ``live`` canary (``tests/conftest.py``). |
| `test_live_system_guard.py` | Regression tests for the conftest live-system guard's argv handling. |
| `test_live_system_guard_self_test.py` | Self-test for the live-system guard fixture in tests/conftest.py. |
| `test_load_yaml_file_readonly.py` | ``load_yaml_file_readonly`` re-parses only when the file signature changes. |
| `test_log_isolation.py` | The test suite must never write into the operator's real Hermes logs. |
| `test_managed_runtime_resolution.py` | Guard: Hermes-owned subprocesses must not resolve managed runtimes by bare PATH. |
| `test_mini_swe_runner.py` | Tests: `test_run_task_kimi_omits_temperature` |
| `test_model_forces_max_completion_tokens.py` | Targeted tests for ``utils.model_forces_max_completion_tokens``. |
| `test_model_tools_async_bridge.py` | Regression tests for the _run_async() event-loop lifecycle. |
| `test_no_shadowed_test_definitions.py` | No test module may define the same name twice in one scope. |
| `test_old_updater_compat_surface.py` | An old `hermes update` must still find every name it loads mid-swap. |
| `test_os_marker_gating.py` | Run the real collection hook; skip-all and unregistered guards must fail. |
| `test_packaging_build_guard.py` | Behavioral regression coverage for the wheel/sdist distribution guard. |
| `test_packaging_metadata.py` | Independent core/optional dependency and reviewed CVE policies. |
| `test_packaging_py_modules.py` | Packaging invariant: every root-level module that packaged code imports ships in the wheel. |
| `test_platforms_marker.py` | Native platform policy table; collection wiring lives in test_os_marker_gating. |
| `test_project_metadata.py` | Regression tests for packaging metadata in pyproject.toml. |
| `test_sanitize_tool_error.py` | Tests for `_sanitize_tool_error` in model_tools. |
| `test_scratch_dir.py` | Scratch dir contract: TMPDIR/TMP/TEMP follow HERMES_HOME/cache/scratch unless the user set them. |
| `test_scratch_prune_undeletable.py` | An idle scratch entry this user cannot read or delete is reported once and not re-walked hourly. |
| `test_scratch_registered_clock_step.py` | The spawn ledger's boot-relative identity: a registered gateway's scratch survives a wall-clock step (NTP, VM resume), and boot ticks never vouch for a process across a reboot. |
| `test_scratch_scan_failures.py` | Cleanup needs a complete idle scan before deleting a scratch tree. |
| `test_search_cjk_prefix_wildcard.py` | CJK search must survive the prefix wildcard callers append (#90636). |
| `test_session_daemon_reaper.py` | The session teardown stops processes left running against this run's Hermes homes. |
| `test_session_spillover_cleanup.py` | Session-tied spillover unlinking (#126351): an archive referenced by a retained session stays available exactly as long as that session does. |
| `test_state_config_contention.py` | Existing databases remain usable while a config writer finishes publication. |
| `test_tests_tree_layout.py` | The tests/ tree mirrors the source tree. |
| `test_trajectory_compressor.py` | Tests for trajectory_compressor.py — config, metrics, and compression logic. |
| `test_trajectory_compressor_async.py` | Tests for trajectory_compressor AsyncOpenAI event loop binding. |
| `test_utils_atomic_roundtrip_yaml_save.py` | Tests for atomic_roundtrip_yaml_save() — comment-preserving full-state writes. |
| `test_utils_atomic_writers_deleted_profile.py` | Atomic writers must not resurrect a deleted named profile home. |
| `test_utils_no_proxy_sanitize.py` | NO_PROXY entries httpx cannot compile are rewritten to the bare-IPv6 form (#118159). |
| `test_utils_rmtree_readonly.py` | ``utils.rmtree_readonly`` removes trees that ``shutil.rmtree`` refuses. |
| `test_utils_truthy_values.py` | Tests for shared truthy-value helpers. |
| `test_utils_unlink_files_older_than.py` | ``utils.unlink_files_older_than``: the shared age-based file sweep. |
| `test_wal_reset_repair_hint.py` | Behavior tests for hermes_state._wal_reset_repair_hint. |
| `test_windows_subprocess_no_window_flags.py` | Tests: `_Completed`, `_spawns`, `_is_git_spawn`, `_make_fake_popen`, `test_bounded_git_probe_fast_path_spawn_contract_windows`, `test_bounded_git_probe_nonzero_returncode_returns_empty` … |
| `test_yaml_indent_consistency.py` | All YAML write paths use indented block sequences (#31999). |
| `usage_window_fixtures.py` | Test helper: the server's usage-window gauge list from the old per-window keyword names. |
| `waiting.py` | Wait for a condition instead of the clock (the HX013 fix). |

## `tests/_fixtures/`

| File | What it does |
|---|---|
| `__init__.py` | Topic modules of the suite-wide ``tests/conftest.py``, imported by it. |
| `env_filter.py` | Env-var names the hermetic ``_hermetic_environment`` fixture blanks before every test. |
| `live_system_guard.py` | The autouse live-system guard: no real kills, Hermes-unit systemctl writes, gateway spawns or checkout writes. |
| `model_peer.py` | Loopback OpenAI-compatible model peer shared by the ordinary-daemon wire tests. |
| `platform_gating.py` | Host-OS gating for ``@pytest.mark.platforms(...)``, applied by the conftest collection hook. |

## `tests/acp_adapter/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Shared fixtures for tests/acp_adapter. |
| `test_acp_commands.py` | Tests: `FakeAgent`, `CaptureConn`, `NoopDb`, `make_agent_and_state`, `test_acp_real_agent_gets_session_db_for_recall`, `test_acp_steer_slash_command_injects_into_running_agent` … |
| `test_acp_dashboard_model_switch_validation.py` | ACP ``session/set_model`` and the dashboard main slot validate through ``switch_model``. |
| `test_acp_discard_review.py` | ACP ``/discard`` while a lost turn pauses the session (review #141357, GW-10). |
| `test_acp_image_staging_boundary.py` | prompt.submit attachments and ACP image staging stay inside the profile image cache (PR #106742 security lane). |
| `test_acp_image_strict_reject.py` | An ACP image part admission cannot carry degrades to a text note; the user's text still runs (B2-12). |
| `test_acp_images.py` | Tests: `test_acp_image_blocks_convert_to_openai_multimodal_content`, `test_text_only_acp_blocks_stay_string_for_legacy_prompt_path`, `test_acp_resource_link_file_is_inlined_as_text`, `test_native_drive_path_and_file_uri… |
| `test_acp_logging_redaction.py` | ACP adapter stderr logging must go through RedactingFormatter. |
| `test_acp_mcp_discovery.py` | Behavioral regression tests for ACP background MCP discovery + late-refresh. |
| `test_acp_reattach_unknown_notice.py` | A reconnect that re-attaches a session with a lost turn tells the editor at once, like load/resume (JM44 r1-P1-4), and one that finds the turn discarded admits the next prompt (#140521): real websockets, the real Gatewa… |
| `test_acp_unacked_identity_retry.py` | ACP keeps a retained submission identity through its own retry: a failed reconnect keeps an un-acked prompt's input_id, and a slash control's retry keeps its prepared request_id. |
| `test_adversarial_unknown_follower.py` | Terminal results cannot be replaced by a successor's unknown queue state. |
| `test_approval_isolation.py` | Tests for GHSA-96vc-wcxf-jjff and GHSA-qg5c-hvr5-hjgr. |
| `test_auth.py` | Tests for acp_adapter.auth — provider detection. |
| `test_catalog_read_only.py` | Browsing ACP history is not an execution/storage owner. |
| `test_detect_provider_entra.py` | Regression tests for ACP adapter detection under Azure Foundry Entra ID. |
| `test_edit_approval.py` | Tests for ACP pre-edit approval gating. |
| `test_empty_session_persistence.py` | Only new, contentless ACP sessions are ephemeral; existing state remains durable. |
| `test_entry.py` | Tests for acp_adapter.entry startup wiring. |
| `test_events.py` | Tests for acp_adapter.events — callback factories for ACP notifications. |
| `test_failed_turn_closure.py` | A failed turn must not leave its accepted user row as the durable conversation tail. |
| `test_finish_turn_finally.py` | Mid-tail failure in _finish_turn must not wedge the session running (#115588). |
| `test_gateway_acp_session_end.py` | ACP v0.9 has no per-session destroy: the last viewer leaving an idle ACP session is its end (#118216). |
| `test_gateway_attach_mode_race.py` | A first attach's reply shows the edit policy the owner enforces when it replies, not when it started. |
| `test_gateway_attach_shutdown.py` | Post-attach notices (command list, context indicator) never outlive ``aclose``. |
| `test_gateway_cancel_admission.py` | session/cancel cancels the ACP-owned admission, never another surface's running turn. |
| `test_gateway_catalog_cwd.py` | Read-only ACP picker understands canonical column-backed cwd. |
| `test_gateway_catalog_local_rows.py` | session/list finds editor threads the gateway owner stores as ``local`` (#143547 ACP-24). |
| `test_gateway_catalog_reset_owner.py` | An explicit canonical reset on an ACP session is offered and reopened by its retained owner. |
| `test_gateway_client_boundary.py` | The normal ACP constructor is a transport client, not an embedded owner. |
| `test_gateway_compressed_reopen.py` | A compressed editor chat reopens under its logical id (real authority + SQLite, real dispatch). |
| `test_gateway_config_options.py` | Zed renders its model and effort pickers only from ``configOptions`` (#143547 ACP-24). |
| `test_gateway_config_projection.py` | Zed reads its pickers only from ``configOptions`` once an agent sends them, so another surface's mode or effort change must reach it as ``config_option_update``, not ``current_mode_update`` alone. |
| `test_gateway_controls.py` | ACP controls retain generation fences and reject unavailable mutations. |
| `test_gateway_delivery_shapes.py` | Every delivery shape the owner publishes reaches the editor exactly once, through one live pump. |
| `test_gateway_editor_clarify.py` | A canonical clarify question reaches the ACP editor and its answer reaches the model. |
| `test_gateway_editor_cwd.py` | Editor diff preparation must use the same cwd as the actual file tool. |
| `test_gateway_editor_mcp.py` | Native ACP stdio through ordinary gateway source, real model and MCP peers. |
| `test_gateway_editor_mcp_held.py` | Held editor MCP connections follow the session's committed selection (#134889 ACP-8, ACP-10). |
| `test_gateway_editor_policy.py` | Frozen editor policy and execution-owned edits, without an editor process. |
| `test_gateway_editor_v4a.py` | V4A edit cards resolve every referenced path in the session workspace. |
| `test_gateway_editor_wire.py` | Real ACP editor permissions over an ordinary daemon's canonical ACP route. |
| `test_gateway_entry_lifecycle.py` | The ACP transport owns neither MCP discovery nor a surviving client socket. |
| `test_gateway_event_mapping.py` | The gateway's turn events reach the editor as the in-process ACP agent projected them (#134889 ACP-5, ACP-15): native plan updates, the executor's tool verdict, closed tool and permission bubbles, and ``messageId`` on a… |
| `test_gateway_launch_flags.py` | `hermes acp` launch flags freeze into the gateway session they create (#134889 ACP-13). |
| `test_gateway_model_pick_provider.py` | ACP ``session/set_model`` on the gateway path: the advertised ``provider:model`` id switches the session's provider too (#139165, #134889 MP-10), over the real ACP stdio wire and a real gateway. |
| `test_gateway_model_provider.py` | Regression for #139165: ACP picker identity reaches canonical model mutations. |
| `test_gateway_new_cold.py` | New ACP handoff advert and unmodified cold canonical ACP restoration. |
| `test_gateway_overlay_home.py` | ``hermes acp`` with a per-task overlay ``HERMES_HOME`` (#138949, #134889 ACP-18). |
| `test_gateway_prompt_content.py` | ACP prompt blocks reach canonical admission with the same conversion main's server uses. |
| `test_gateway_prompt_reoffer.py` | A shared prompt whose ACP card got no accepted answer is shown again on reattach, never auto-answered. |
| `test_gateway_queued_unknown.py` | Editor prompts fail recoverably when their FIFO becomes unknown. |
| `test_gateway_reasoning.py` | Live reasoning for editors on the gateway path (#134889 ACP-4). |
| `test_gateway_reconnect.py` | An ACP editor survives a gateway restart: real websockets, the real GatewayClient, two owners. |
| `test_gateway_registry_commands.py` | Registry commands ACP does not answer itself, over the real ACP stdio wire and a real gateway. |
| `test_gateway_remote_image_submit.py` | A remote image URL is fetched once per logical prompt: an un-acked submit's retry reuses what the first attempt staged (never a re-download that could change the content and so the input_id), and the editor's Stop durin… |
| `test_gateway_replay_gap.py` | ACP across a ``session.replay_gap``: the pump re-attaches that session and survives; a cut prompt settles once, live or from one receipt read the pump owns; terminal evidence beats a recovery error; an interim stays who… |
| `test_gateway_retry_command.py` | ACP ``/retry`` on the gateway path: real authority, SQLite and ``AuthorityConnection.dispatch`` behind ``GatewayACPAgent.prompt`` (#140190 review). |
| `test_gateway_session_commands.py` | ``/queue``, ``/steer`` and the edit-policy mode on the gateway path, against a fake owner. |
| `test_gateway_session_metadata.py` | Editor session metadata and commands on the shipped gateway path (tracker ACP-1/2/3/6/7/11). |
| `test_gateway_sessions.py` | Actual ACP stdio and WS clients against an ordinary isolated gateway. |
| `test_gateway_slash_text.py` | Only registered Hermes commands are slash commands; other text starting with '/' is a prompt. |
| `test_gateway_snapshot_adoption.py` | Every fresh ``session.resume`` the editor installs advances the event watermark, so a ``session.info`` queued behind it (another viewer's mode change) is skipped by the pump. Each such install projects the snapshot's ow… |
| `test_gateway_submit_retry.py` | An editor retry of a prompt whose submit ack was lost reuses its identity: one admission, one turn. |
| `test_gateway_terminal_projection.py` | Terminal ACP responses describe the exact admission, not the session's latest turn. |
| `test_gateway_terminal_receipt_claim.py` | A retried submit's terminal receipt and the live message.complete deliver one reply between them. |
| `test_gateway_tool_projection.py` | Live ACP tool events carry the same identity, arguments and result the replay shows. |
| `test_gateway_unacked_slash.py` | Slash work retires an un-acked prompt's retained identity: a later identical prompt is new work. |
| `test_gateway_voice_stopped.py` | TUI-26: the owner's canonical prompt.submit may answer ``{voice_stopped: true}`` (a bare stop phrase typed into a LOCAL session whose owner /voice mode is on: the voice chat ends and nothing is admitted). The ACP adapte… |
| `test_gateway_wire_controls.py` | Additional real-wire controls for the ACP authority client. |
| `test_mcp_e2e.py` | End-to-end tests for ACP MCP server registration and tool-result reporting. |
| `test_named_provider_catalogs.py` | Tests for named user-defined provider entries in the ACP model selector. |
| `test_permissions.py` | Tests for acp_adapter.permissions. |
| `test_ping_suppression.py` | Tests for acp_adapter.entry._BenignProbeMethodFilter. |
| `test_policy_identity_compat.py` | Absent optional editor state cannot revoke an older credential reference. |
| `test_retained_identity_retirement.py` | Class: a retained submission identity (an un-acked prompt's input_id, a prepared control's request_id) is only for the retry that is the session's very next verb. Every native surface that retains one must retire it whe… |
| `test_runtime_identity.py` | Runtime identity contracts for ACP's human and machine surfaces. |
| `test_server.py` | Tests for acp_adapter.server — HermesACPAgent ACP server. |
| `test_session.py` | Tests for acp_adapter.session — SessionManager and SessionState. |
| `test_session_construction_off_loop.py` | ACP session construction runs off the event loop. |
| `test_session_cwd_column.py` | ACP sessions must populate the cwd COLUMN, not only model_config. |
| `test_session_db_private_access.py` | Tests for the update_session_meta fix. |
| `test_session_mcp_branch_gate.py` | A fork's editor MCP discovery runs only after the branch's own fences pass (#134889 ACP-12). |
| `test_session_mcp_frozen.py` | Selected editor schemas never refresh inside an execution or escape discovery. |
| `test_session_mcp_ownership.py` | The gateway owns each session's editor MCP servers as session state (#134889 ACP-8/ACP-10). |
| `test_session_mcp_policy.py` | Editor MCP credentials are borrowed and tools are frozen per canonical owner. |
| `test_session_mcp_selection.py` | Which editor MCP servers a session freezes, and under which names (#134889 ACP-8, ACP-9). |
| `test_session_mcp_workspace_move.py` | A held editor connection follows a committed workspace move (#134889 ACP-12). |
| `test_session_provenance.py` | Tests for ACP session-provenance derivation (issue #33617). |
| `test_session_reasoning_config.py` | ACP sessions honor the configured reasoning setting (#85153). |
| `test_tools.py` | Tests for acp_adapter.tools — tool kind mapping and ACP content building. |

## `tests/agent/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Fast-path fixtures shared across tests/agent/. |
| `lsp/__init__.py` | Pytest helpers for LSP-related tests. |
| `lsp/_mock_lsp_server.py` | A minimal in-process LSP server used by tests. |
| `lsp/test_backend_gate.py` | Integration test: LSP layer is skipped on non-local backends. |
| `lsp/test_broken_set.py` | Tests for the broken-set short-circuit added to handle outer-timeout failures. |
| `lsp/test_client_e2e.py` | End-to-end client tests against the in-process mock LSP server. |
| `lsp/test_compound_extensions.py` | Compound extensions (``.blade.php``) route to their own server; the last segment alone keeps its server. |
| `lsp/test_custom_servers.py` | Config-declared LSP servers (``lsp.servers.<id>`` with ``extensions``) route files and spawn like built-ins. |
| `lsp/test_delta_key.py` | Tests for cross-edit LSP delta filtering. |
| `lsp/test_diagnostics_field.py` | Tests for the ``lsp_diagnostics`` field on WriteResult / PatchResult. |
| `lsp/test_eventlog.py` | Tests for the structured logging dedup model. |
| `lsp/test_incremental_unicode.py` | The server's document mirror must match disk after each incremental replacement. |
| `lsp/test_install_and_lint_fixes.py` | Tests for follow-up fixes to the LSP integration (PR after #24168). |
| `lsp/test_lifecycle.py` | Tests for service-singleton lifecycle: atexit handler, idempotent shutdown. |
| `lsp/test_manager_locking.py` | Concurrency invariants for the LSP service state lock. |
| `lsp/test_multi_root.py` | Multi-root servers share ONE process across project roots. |
| `lsp/test_nested_root_current_diagnostics.py` | ``_current_diags_async`` must find a single-root client under the root it was spawned with. |
| `lsp/test_powershell_server.py` | Tests for the PowerShellEditorServices (PSES) server registration. |
| `lsp/test_protocol.py` | Tests for the LSP protocol framing layer. |
| `lsp/test_python_discovery.py` | Pyright uses the project environment before the Hermes runtime fallback. |
| `lsp/test_reporter.py` | Tests for the diagnostic reporter (formatting layer). |
| `lsp/test_root_policy.py` | Per-root policy knobs of :class:`LSPService` (#116446): ``lsp.exclude_roots`` gates a workspace off without disabling the server fleet-wide, and ``lsp.warmup_timeout`` gives a cold root one long wait instead of the stea… |
| `lsp/test_service.py` | Tests for the synchronous LSPService wrapper. |
| `lsp/test_shell_linter_lsp_skip.py` | Skip the per-file shell linter when LSP will handle the same file. |
| `lsp/test_stale_diagnostics.py` | Regression tests for the "ghost diagnostics" staleness bug. |
| `lsp/test_versionless_push_during_send.py` | A versionless publishDiagnostics read while didChange is still being written must count as fresh. |
| `lsp/test_vue_server.py` | Tests for the Vue server registration. |
| `lsp/test_windows_binary_resolution.py` | Windows binary resolution must prefer the runnable ``.cmd``/``.exe``/``.bat`` wrapper over npm's POSIX ``#!/bin/sh`` shim, which shares the bare name and fails ``CreateProcess`` with WinError 193. |
| `lsp/test_workspace.py` | Tests for workspace + project-root resolution. |
| `lsp/test_workspace_release.py` | Workspace-scoped teardown: removed worktrees and deleted roots must not keep language servers alive. |
| `lsp/test_workspace_trust.py` | Nothing a checkout ships runs unless the operator trusts that workspace. |
| `lsp/test_write_never_waits_on_lsp.py` | Invariant: a write never waits on the language server, and its diagnostics still reach the model (the session that made the edit, and only that session). |
| `metadata_transport.py` | Socket-free response data for tests that exercise the real metadata transport. |
| `repro_image_shrink_brick.py` | Runnable proof for issue #48013 — image-dimension 400 session brick. |
| `test_413_compression.py` | Tests for payload/context-length → compression retry logic in AIAgent. |
| `test_413_image_payload_recovery.py` | Regression tests: HTTP 413 recovery must score progress in BYTES. |
| `test_860_dedup.py` | Tests for issue #860 — SQLite session transcript deduplication. |
| `test_account_policy_block.py` | An upstream account ban relayed as HTTP 200 + an SSE ``error`` event is permanent. |
| `test_account_usage.py` | Tests: `_FakeResponse`, `_FakeClient`, `codex_usage_payload`, `test_codex_usage_prefers_explicit_live_agent_credentials`, `test_codex_usage_falls_back_to_native_credential_pool`, `_explicit_creds_snapshot` … |
| `test_account_usage_fetch.py` | Tests: `_UsageProfile`, `_Response`, `_Client`, `_RoutingClient`, `test_fetch_account_usage_codex`, `_register_profile` … |
| `test_account_usage_pool_fetch.py` | Real-path source parsing and routing for per-credential usage fetches. |
| `test_acp_client.py` | Contracts of the public ACP stdio client (``agent.acp_client.ACPClient``) and its deprecated alias. |
| `test_acp_client_invariants.py` | Safety and lifecycle invariants of the public ACP stdio client (``agent.acp_client.ACPClient``). |
| `test_acp_openai_bridge.py` | The ACP text bridge is what makes Hermes' own tools reachable on an ACP provider. |
| `test_acp_provider_rails.py` | Two core decisions must key on the ``acp://`` scheme, not on one vendor. |
| `test_activity_persist_off_relay_loop.py` | A managed worker's activity heartbeat must not reach the synchronous persistence RPC on Relay's event loop (#139029). |
| `test_actual_auxiliary_routing.py` | Actual background tasks exercise the same configured route as foreground chat. |
| `test_affordable_402_main_loop.py` | Main-loop credit-limited 402: retry once with the affordable output cap (#49769). |
| `test_agent_guardrails.py` | Unit tests for AIAgent pre/post-LLM-call guardrails. |
| `test_anthropic_adapter.py` | Tests for agent/anthropic_adapter.py — Anthropic Messages API adapter. |
| `test_anthropic_adapter_extra_headers.py` | Anthropic-messages clients honour ``custom_providers[].extra_headers`` (#24293, #9721). |
| `test_anthropic_billing_guidance.py` | Tests for the Anthropic-subscription branch of ``agent.conversation_loop._billing_or_entitlement_message``. |
| `test_anthropic_borrowed_row_authority.py` | The borrowed ``claude_code`` row is a reference, never a token authority. |
| `test_anthropic_client_auth.py` | Auth-boundary shard for the Anthropic adapter. |
| `test_anthropic_credential_persist_failure.py` | Failure-injection coverage for the Anthropic refresh *commit* step. |
| `test_anthropic_dead_grant_hints.py` | Hermes credential hints and the Anthropic token-endpoint error shape (#113023). |
| `test_anthropic_external_login_optout.py` | ``auth.adopt_external_logins: false`` keeps Hermes off the Claude Code login (#113023). |
| `test_anthropic_keychain.py` | Tests for Bug #12905 fixes in agent/anthropic_adapter.py — macOS Keychain support. |
| `test_anthropic_kimi_signed_thinking_replay.py` | Kimi-family endpoints don't need thinking blocks stripped on replay; DeepSeek does. |
| `test_anthropic_kwargs_sanitize.py` | Tests for sanitize_anthropic_kwargs (#31673). |
| `test_anthropic_mcp_prefix_strip.py` | Tests for GH-25255: Anthropic OAuth ``mcp__`` tool-name round-trip. |
| `test_anthropic_message_stop.py` | Regression coverage for incomplete native Anthropic Messages streams (#121320). |
| `test_anthropic_mid_tool_call_drop.py` | The Anthropic streaming path must not accept a tool_use block whose stream died before its input arrived (#80498 sibling). |
| `test_anthropic_model_cooldowns.py` | A generic Anthropic 429 benches only the model that was rate-limited (#111769, #61451). |
| `test_anthropic_oauth_pkce.py` | Regression tests for the Anthropic OAuth PKCE flow. |
| `test_anthropic_oauth_stress.py` | Load / stress test for the Anthropic OAuth cross-process refresh race fix. |
| `test_anthropic_oauth_ua_prefix.py` | Regression tests for the OAuth User-Agent header in anthropic_adapter.py. |
| `test_anthropic_output_field_leak.py` | Regression: output-only SDK fields must not leak into Anthropic request input. |
| `test_anthropic_owned_routing.py` | Owned OAuth must win without rotating an unrelated borrowed grant. |
| `test_anthropic_preserved_thinking_replay.py` | Tests: `_signed_turn`, `_carrier`, `_native_turn`, `_session_db`, `_agent`, `_patch_assembly_loop` … |
| `test_anthropic_prompt_cache_policy.py` | Tests for AIAgent._anthropic_prompt_cache_policy(). |
| `test_anthropic_request_blank_block_guard.py` | Regression: the final Anthropic request must carry no blank text block. |
| `test_anthropic_request_client_reuse.py` | Per-request Anthropic wire client reuse across sequential LLM calls. |
| `test_anthropic_route_oauth_identity.py` | A ``key_cmd`` Claude Code OAuth token keeps its OAuth identity on native api.anthropic.com routes (#114967). |
| `test_anthropic_signed_platform_replay.py` | Signed thinking reaches the wire wherever the upstream can verify it, and only there. |
| `test_anthropic_spent_rotation_verdict.py` | A rotation that was consumed but never committed must stay unusable. |
| `test_anthropic_stream_fallbacks.py` | Invariants: Anthropic stream failures fall back or stub in a shape the loop accepts. |
| `test_anthropic_structured_output.py` | Structured-output translation for Anthropic auxiliary calls. |
| `test_anthropic_thinking_block_order.py` | Regression test for the Anthropic interleaved thinking-block 400. |
| `test_anthropic_thinking_disable.py` | 'Thinking off' on the native Anthropic Messages wire. |
| `test_anthropic_third_party_oauth_guard.py` | Tests for ``_is_anthropic_oauth`` guard against third-party Anthropic-compatible providers. |
| `test_anthropic_token_scope_isolation.py` | Regression tests: resolve_anthropic_token() must honour the profile secret scope. |
| `test_anthropic_truncation_continuation.py` | Regression test for anthropic_messages truncation continuation. |
| `test_anthropic_whitespace_text_blocks.py` | Regression: whitespace-only text blocks must be coerced, not sent verbatim. |
| `test_api_content_row_addressed_backfill.py` | Row-addressed ``api_content`` backfill (NousResearch/hermes-agent#102194). |
| `test_api_content_sidecar.py` | Tests for the ``api_content`` sidecar ("persist what you send"). |
| `test_api_max_retries_config.py` | Tests for agent.api_max_retries config surface. |
| `test_arcee_trinity_overrides.py` | Tests for Arcee Trinity Large Thinking per-model overrides. |
| `test_astra_baseline_runtime.py` | Focused real-path coverage for the GPT-6 Astra baseline contract. |
| `test_astra_oauth_native_compaction.py` | gpt-6-astra (and its ``-900k`` picker alias) is native-compaction eligible only on official Codex OAuth (#103720). |
| `test_async_httpx_del_neuter.py` | Tests for the AsyncHttpxClientWrapper.__del__ neuter fix. |
| `test_async_token_accounting.py` | Async token accounting — SessionDB background writer queue. |
| `test_async_utils.py` | Tests for agent.async_utils.safe_schedule_threadsafe. |
| `test_auth_provider_failover.py` | Auth-failure provider failover (conversation loop). |
| `test_authorization_gate.py` | Tests for the concurrent authorization gate and human-wait accounting (#79719). |
| `test_aux_affordable_402_retry.py` | Credit-limited 402 handling: clamp to the affordable budget and retry. |
| `test_aux_alias_home_scope.py` | The aux provider alias table follows the bound profile home and later plugin installs. |
| `test_aux_custom_endpoint_headers.py` | The aux client's anonymous custom arm (``provider: custom`` + a base URL) sends the ``extra_headers`` of the custom provider entry whose base URL is that endpoint, as the main agent's client does, and never another entr… |
| `test_aux_progress_streaming.py` | Tests for the auxiliary forward-progress streaming layer. |
| `test_aux_relay_progress_seam.py` | Every relay attempt (retries, recovery rungs, fallbacks) streams through the progress hook (#98466). |
| `test_aux_session_endpoint_affinity.py` | Auxiliary routing sticks to the session's configured OpenAI endpoint; a rejection elsewhere is not a dead key. |
| `test_aux_stream_host_deadline.py` | #99692 — the streamed auxiliary summary must not outlive its compression host. |
| `test_aux_stream_host_deadline_sibling_wires.py` | #99692 sibling wires — the host compression deadline must stop EVERY aux stream consumer, not only the chat.completions accumulator. |
| `test_aux_summary_stream_hard_cancel.py` | A hard cancel (/stop, session boundary) of a compression summary closes the provider stream. |
| `test_auxiliary_anthropic_pool_fallback_regression.py` | Regression: _try_anthropic() must fall back to the legacy token resolver when the credential pool is present but has no usable entry. |
| `test_auxiliary_auth_rung_fallthrough.py` | The auxiliary recovery ladder must not let a failed auth-refresh retry escape. |
| `test_auxiliary_auto_never_guesses_provider.py` | ``auxiliary.*.provider: auto`` never bills a provider the user did not select. |
| `test_auxiliary_auto_route_xai_oauth_refresh.py` | Auto-routed auxiliary calls on xAI OAuth refresh the grant after a 403 bad-credentials (#84845). |
| `test_auxiliary_client.py` | Tests for agent.auxiliary_client resolution chain, provider overrides, and model overrides. |
| `test_auxiliary_client_anthropic_custom.py` | Tests for agent.auxiliary_client._try_custom_endpoint's anthropic_messages branch. |
| `test_auxiliary_client_azure_foundry.py` | Tests for auxiliary client routing of the ``azure-foundry`` provider. |
| `test_auxiliary_client_base_url_host_validation.py` | Regression tests for issue #52608. |
| `test_auxiliary_client_bootstrap_skew.py` | Regression for #64333 — auxiliary client must survive a version-skewed agent.process_bootstrap that lacks build_keepalive_http_client. |
| `test_auxiliary_client_cache_eviction.py` | Regression coverage for provider-scoped auxiliary cache eviction (#113022). |
| `test_auxiliary_client_cache_follows_credential.py` | Regression coverage: the auxiliary client cache key follows the pooled credential (#113022). |
| `test_auxiliary_client_minimax_oauth.py` | Regression: ``resolve_provider_client("minimax-oauth", ...)`` must build a refresh-capable Anthropic auxiliary client, not silently return (None, None). |
| `test_auxiliary_client_nous_401_cache_key.py` | A Nous 401 refresh must replace the auxiliary client under the SAME cache key ``call_llm`` acquired it with (model dimension #56889, task dimension #58894). Otherwise the expired client is never evicted and every auxili… |
| `test_auxiliary_client_proxy_env.py` | Regression guard: auxiliary OpenAI clients must use env-only proxy policy. |
| `test_auxiliary_client_resolve_dedup.py` | Tests for resolve_provider_client fall-through log dedup (salvage #56283). |
| `test_auxiliary_client_ssl_verify.py` | Regression: auxiliary-client keepalive httpx client must honor custom CA bundles. |
| `test_auxiliary_client_xai_oauth_recovery.py` | Tests for xAI OAuth 403 error recovery in auxiliary_client. |
| `test_auxiliary_codex_completion_status.py` | Auxiliary Responses normalization must not certify a partial checkpoint. |
| `test_auxiliary_compression_timeout_floor.py` | Regression tests for the compression-scoped auxiliary timeout floor (#54915). |
| `test_auxiliary_concurrency.py` | Tests for per-task concurrency limiting on auxiliary LLM calls (#23324). |
| `test_auxiliary_error_classification.py` | Auxiliary error classification shares the main classifier's billing table and labels quarantines truthfully. |
| `test_auxiliary_explicit_base_anthropic.py` | Tests for resolve_provider_client's ``custom`` + ``explicit_base_url`` branch when the endpoint speaks Anthropic Messages. |
| `test_auxiliary_explicit_cancellation.py` | Deterministic cross-thread cancellation tests for compression aux transports. |
| `test_auxiliary_fallback_multihop.py` | Auxiliary ``provider: auto`` fallback walk is multi-hop (#106367). |
| `test_auxiliary_hooks.py` | ``pre_auxiliary_call`` / ``post_auxiliary_call`` fire for auxiliary LLM calls (#79733). |
| `test_auxiliary_main_first.py` | Regression tests for the ``auto`` → main-model-first policy. |
| `test_auxiliary_named_custom_providers.py` | Tests for named custom provider and 'main' alias resolution in auxiliary_client. |
| `test_auxiliary_ollama_local_provider.py` | Explicit ``provider: ollama`` (and the sibling local-server aliases ``vllm`` / ``llamacpp``) must route through the ``custom`` branch in the auxiliary client, as it already does in ``hermes_cli.auth``: a lane pointing a… |
| `test_auxiliary_opencode_routing.py` | Auxiliary clients for OpenCode Zen/Go follow the per-model wire table the main runtime uses (#98799). |
| `test_auxiliary_openrouter_max_tokens.py` | Test that _build_call_kwargs preserves max_tokens for OpenRouter endpoints. |
| `test_auxiliary_parameter_rung_chaining.py` | Auxiliary parameter-rejection rungs chain in any order, on the primary AND the fallback path. |
| `test_auxiliary_provider_supplied_client.py` | Auxiliary ``api_key`` routes honor ``ProviderProfile.create_client()`` — parity with the main agent. |
| `test_auxiliary_reasoning_catalog_floor.py` | The route's model catalog decides the title lane's first request (no guaranteed 400 on mandatory routes). |
| `test_auxiliary_reasoning_field_rejection_retry.py` | Reasoning-field rejection retry in ``agent.auxiliary_client`` (#112781). |
| `test_auxiliary_reasoning_floor.py` | Reasoning-required rejection → step the aux effort up to the floor and remember the route. |
| `test_auxiliary_relay.py` | Tests: `relay_turn`, `test_auxiliary_retries_share_logical_relay_identity`, `test_auxiliary_provider_fallback_closes_one_real_logical_call`, `test_auxiliary_provider_fallback_records_one_terminal_model_route`, `_Provide… |
| `test_auxiliary_runtime_cache_key.py` | Regression coverage for implicit live-runtime auxiliary cache keys. |
| `test_auxiliary_structured_output.py` | Structured-output (``response_format``) handling on auxiliary routes that reject it. |
| `test_auxiliary_title_timeout_bound.py` | Auto-title timeouts are bounded by ONE ``auxiliary.title_generation.timeout`` window and named as timeouts (#89445, #66251). |
| `test_auxiliary_transient_retry.py` | Per-model client-cache isolation: two concurrent auxiliary calls to the same provider/base_url/key but DIFFERENT models (e.g. MoA advisors) never share one cache entry. |
| `test_auxiliary_transport_autodetect.py` | Tests for transport auto-detection in agent.auxiliary_client. |
| `test_auxiliary_unavailable_nous_reason.py` | The goal judge names a Nous auxiliary auth failure instead of an opaque judge error (#42177). |
| `test_auxiliary_user_default_headers.py` | Tests for user-configured ``model.default_headers`` in the auxiliary client. |
| `test_auxiliary_wire_messages.py` | The final auxiliary destination owns message sanitation, not virtual MoA. |
| `test_azure_identity_adapter.py` | Tests for the Microsoft Entra ID adapter (agent/azure_identity_adapter.py). |
| `test_backend_identity.py` | Owner-level tests for agent.backend_identity. |
| `test_background_review.py` | Regression tests for background review agent cleanup. |
| `test_background_review_cache_parity.py` | Tests that the background review fork inherits the parent's cached system prompt. |
| `test_background_review_cost_controls.py` | Unit coverage for the background-review aux-model selector + routed digest. |
| `test_background_review_input_budget.py` | Regression tests for the background-review aggregate input budget (#93057). |
| `test_background_review_list_shapes.py` | Regression tests for the list-shape AttributeError guards in ``agent.background_review.summarize_background_review_actions`` (#59437). |
| `test_background_review_memory_scope.py` | The review fork's memory access must follow the trigger that fired (#105921). |
| `test_background_review_routed_effort.py` | Routed background reviews honor ``auxiliary.background_review.reasoning_effort`` (#94825). |
| `test_background_review_summary.py` | Tests for AIAgent._summarize_background_review_actions. |
| `test_background_review_tool_call_guard.py` | The background-review fork must not spawn when it could only no-op. |
| `test_background_review_toolset_restriction.py` | Tests that the background review agent restricts tools at runtime, not at schema time. |
| `test_background_review_usage.py` | Background-review usage attribution (issue #87250). |
| `test_battery.py` | Behavior tests for the status-bar battery helper (agent/battery.py). |
| `test_bedrock_1m_context.py` | Tests for the 1M-context beta header on AWS Bedrock Claude models. |
| `test_bedrock_adapter.py` | Tests for the AWS Bedrock Converse API adapter. |
| `test_bedrock_anthropic_foreign_reasoning.py` | Bedrock GPT -> Claude: another model's sealed reasoning never reaches Claude on the Anthropic Messages path. |
| `test_bedrock_context_cache.py` | Bedrock cache provenance and compressor budgets across disk-backed restarts. |
| `test_bedrock_converse_reasoning_replay.py` | Claude reasons on Bedrock Converse, and each Converse model gets back only the reasoning it can take. |
| `test_bedrock_credential_probe.py` | The AWS credential probe the provider ladder runs: one walk of boto3's chain per question, and no instance-metadata lookup from the desktop's own backend (a laptop, where it only costs seconds). |
| `test_bedrock_empty_text_blocks.py` | Regression tests for Bedrock Converse empty/whitespace text block rejection. |
| `test_bedrock_guardrail_claude_route.py` | ``bedrock.guardrail`` must be enforced on the Claude route, not only Converse. The AnthropicBedrock SDK speaks InvokeModel, whose body has no ``guardrailConfig``; Bedrock reads the guardrail from ``X-Amzn-Bedrock-Guardr… |
| `test_bedrock_integration.py` | Integration tests for the AWS Bedrock provider wiring. |
| `test_bedrock_interrupt_post_worker.py` | Regression: /stop must not be swallowed on the Bedrock streaming path. |
| `test_bedrock_request_timeout.py` | Bedrock request timeouts reach the clients that serve the call. |
| `test_bedrock_stream_completion.py` | Audit: actual boto3 HTTP/EventStream parsing before Hermes normalization. |
| `test_bedrock_transport_replay.py` | Production Bedrock transport/history replay regressions. |
| `test_billing_links.py` | Tests for provider-agnostic billing recovery links (agent/billing_links.py). |
| `test_billing_unverified_carrythrough.py` | #82154: an unverified billing verdict must carry its ambiguity through every downstream surface — the returned terminal response, the structured result fields, the credential-pool failure_reason, and the persisted entry… |
| `test_billing_usage.py` | Tests for the shared dollar usage model (agent/billing_usage.py). |
| `test_billing_view.py` | Unit tests for the Phase 2b Remote Spending core + HTTP client. |
| `test_bitwarden_secrets.py` | Hermetic tests for the Bitwarden Secrets Manager integration. |
| `test_bot_chat_toolset_refresh.py` | #124211: a Bot Chat capability refresh must rebuild tools[] through the surface's own builder (what a fresh desktop/TUI session gets), not just the system prompt. |
| `test_bot_profile_prompt_isolation.py` | Regression: a bot profile's system prompt must reflect ITS OWN skills/home, never the launch (default) profile's — even when the agent build runs on a thread that did not bind the HERMES_HOME ContextVar. |
| `test_bounded_response.py` | Tests for bounded reads of streaming HTTP error response bodies. |
| `test_budget_reasoning_details_exclusion.py` | Regression tests for #73298 (second site): the tail-budget walk must not charge the signed/base64 ``reasoning_details`` envelope at chars/4. |
| `test_builtin_memory_disabled_surface.py` | Built-in memory disabled in config must leave no dead surface behind. |
| `test_cache_disabled_on_stubs.py` | Regression for #76085: prompt_caching.cache_ttl off on stub policy paths. |
| `test_callable_api_key.py` | Tests that callable api_key (Entra ID bearer provider) flows through the agent stack without coercion. |
| `test_canon_args_memo_parity.py` | Byte-parity + complexity proof for the memoized send-path tool-call argument canonicalization (agent/conversation_loop.py). |
| `test_capability_probe_credentials.py` | Capability probes materialize credentials without consuming the chat source. |
| `test_cascading_interrupt.py` | Regression guard for the cascading-interrupt hang (PR #6600). |
| `test_chat_completion_helpers_provider_sort.py` | Tests: `test_validated_openrouter_provider_sort_accepts_valid_values`, `test_validated_openrouter_provider_sort_rejects_invalid_values` |
| `test_chat_completion_helpers_tool_calls.py` | Slot assignment of streamed tool-call deltas whose id changes at a reused index. |
| `test_chat_sdk_transform_bypass.py` | Chat-completions request-transform bypass (#93650 extended to chat.completions). |
| `test_cjk_token_estimation.py` | Tests: `test_message_estimate_counts_korean_content_as_token_dense`, `test_cjk_tail_does_not_expand_to_english_char_budget`, `_reference_per_char_estimate`, `test_perf_gated_estimator_matches_per_char_reference`, `test_… |
| `test_claude_code_version_path.py` | Claude Code version detection must see the CLI from a GUI-launched process. |
| `test_cleanup_task_resources_headed.py` | Per-turn browser cleanup skips headed sessions by ``browser.headed`` (config) alone. |
| `test_close_interrupted_tool_sequence.py` | Regression tests for ``close_interrupted_tool_sequence`` (#48879 follow-up). |
| `test_codex_app_server_compaction.py` | Tests: `FakeCodexSession`, `SlowCodexSession`, `_wait_for_touch`, `DummyAgent`, `test_codex_app_server_native_auto_mode_leaves_thread_compaction_to_codex`, `test_codex_app_server_compaction_heartbeat_refreshes_activity_… |
| `test_codex_app_server_event_bridge.py` | Regression tests for the codex_app_server → Hermes UI event bridge. |
| `test_codex_app_server_integration.py` | Integration test for the codex_app_server runtime path through AIAgent. |
| `test_codex_app_server_lifecycle.py` | Codex app-server session lifecycle on hard agent teardown (#65260). |
| `test_codex_app_server_persist.py` | Regression for #49225 — codex app-server turns must reach the session DB exactly once. |
| `test_codex_app_server_thread_resume.py` | #100531 — the codex app-server thread survives an AIAgent rebuild (API-server restart, per-request agents). |
| `test_codex_app_server_transform.py` | The codex app-server runtime runs ``transform_llm_output`` like the generic loop. |
| `test_codex_aux_no_progress_timeout.py` | Progress-aware deadlines for the Codex auxiliary Responses stream. |
| `test_codex_aux_timeout_fd_ownership.py` | Regression: the timeout watchdog must not release the client's FDs. |
| `test_codex_cloudflare_headers.py` | Regression coverage for required Codex identity and account headers. |
| `test_codex_echo_ownership.py` | The accepted input owns its row; transport echoes do not own new rows. |
| `test_codex_first_event_timing.py` | Tests: `_agent`, `_completed_events`, `test_codex_stream_records_first_lifecycle_event_before_text`, `test_codex_stream_without_accepted_event_keeps_timing_unset` |
| `test_codex_gpt55_autoraise_notice.py` | Regression tests for the Codex gpt-5.x autoraise notice gate. |
| `test_codex_happy_eyeballs.py` | Tests: `no_proxy_env`, `_client_backends`, `test_codex_sync_client_uses_happy_eyeballs_backend`, `test_other_sync_clients_keep_httpcore_default_backend`, `test_connection_staggers_past_blackholed_ipv6`, `test_async_code… |
| `test_codex_incomplete_budget_escalation.py` | Responses-wire ``status=incomplete`` continuation must change the request when reasoning consumed the whole output budget (#90393): a retry with the same ``max_output_tokens`` and the same effort re-burns the budget ide… |
| `test_codex_model_entitlement_rotation.py` | A Codex ChatGPT-account model entitlement 400 rotates to the next pool credential (#71970). |
| `test_codex_multimodal_tool_result.py` | Tests for codex_responses_adapter multimodal tool-result handling. |
| `test_codex_no_tools_nonetype.py` | Regression coverage for #32892. |
| `test_codex_pending_tool_text.py` | Answer text a Responses stream sends beside a tool call, without that message item's done event, must reach the assistant turn (#143893). |
| `test_codex_reasoning_only_streak.py` | Codex Responses reasoning-only stall recovery (#67321). |
| `test_codex_request_compression.py` | Codex Responses bodies go out zstd-compressed to the official backend only (official-client parity). |
| `test_codex_request_transport_diagnostics.py` | Diagnostics for Codex Responses transport failures. |
| `test_codex_responses_adapter.py` | Tests: `_strict_tool`, `_main_transport_wire_tools`, `_auxiliary_adapter_wire_tools`, `test_responses_wire_tools_preserve_explicit_boolean_strictness`, `test_chat_content_drops_images_from_assistant_role`, `test_chat_co… |
| `test_codex_responses_settle_pending_tool_calls.py` | Regression: settle pending function calls when a Responses stream completes successfully without ``response.output_item.done``. |
| `test_codex_runtime_history_seed.py` | A codex app-server thread started from scratch is seeded with the session's prior turns (#26035, #74712). |
| `test_codex_runtime_live_events.py` | Regression tests for live Codex app-server events. |
| `test_codex_runtime_prompt_handoff.py` | The codex_app_server runtime hands Hermes' composed system prompt to the codex thread (#74712, #26035). |
| `test_codex_sdk_transform_bypass.py` | Regression tests for the SDK request-transform bypass (#93650). |
| `test_codex_service_tiers.py` | Selected-credential speed ceiling regression for #135024 (no live accounts). |
| `test_codex_soft_failure_pool_rotation.py` | Codex Responses HTTP-200 soft failures (``response.status == "failed"``) must reach the same-provider credential pool before cross-provider fallback (#24159). |
| `test_codex_stream_rotating_item_ids.py` | Copilot rotates opaque item IDs within a call; output_index remains stable. |
| `test_codex_stream_supersession.py` | A Codex Responses stream that loses the delta sink to a newer attempt keeps consuming (#69486). |
| `test_codex_token_expired_replay_recovery.py` | A persisted Codex session must not loop on 401 ``token_expired`` when the credential is fine. |
| `test_codex_ttfb_watchdog.py` | Regression tests for the Codex TTFB (first parsed stream event) watchdog. |
| `test_codex_usage_attribution.py` | Exercise required Codex attribution through real SDK request construction. |
| `test_codex_watchdog_reasoning_effort.py` | Codex non-stream watchdogs honour the request's reasoning effort (#112909). |
| `test_codex_xai_oauth_recovery.py` | Regression tests for the May 2026 xAI OAuth (SuperGrok / X Premium) bugs. |
| `test_coding_context.py` | Tests for agent.coding_context — RuntimeMode seam, resolver, toolset, git probe. |
| `test_coding_worktree_note.py` | A gateway-owned session opened in a linked git worktree gets the isolated-worktree guidance. |
| `test_command_secret_source.py` | E2E tests for the ``command`` secret source. |
| `test_command_token_source.py` | ``key_cmd``: derive a provider API key by running a command. |
| `test_commit_memory_session_context_engine.py` | Regression tests for AIAgent.commit_memory_session. |
| `test_compaction_anti_thrash.py` | The anti-thrashing guard must actually fire. |
| `test_compaction_events.py` | ``hermes.compaction`` v1 records: one content-free record per history rewrite, on every path. |
| `test_compaction_ops_notification_anchor.py` | Operational notifications must not anchor compaction or auto-focus (#92703). |
| `test_compaction_prompt_rebuild.py` | Compaction ALWAYS rebuilds the system prompt from the live builder (#95681). |
| `test_compaction_redaction_boundaries.py` | Strict redaction at every compaction text boundary (issue #43666 item 2). |
| `test_compress_context_progress_timeout.py` | Progress-aware timeout around in-agent compress_context (#72016). |
| `test_compress_focus.py` | Tests for focus_topic flowing through the compressor. |
| `test_compress_signal_leak.py` | Invariant: stale signal leak between consecutive compress_context calls. |
| `test_compressed_summary_metadata.py` | Regression tests for the compressed-summary metadata flag (#38389). |
| `test_compression_abort_state_reset.py` | Regression tests for #58630: every compression abort path must reset per-attempt in-place compaction state. |
| `test_compression_adoption_preserves_live_tail.py` | Regression: preflight durable-snapshot adoption must not drop the live turn's un-persisted user input. |
| `test_compression_anti_thrash_persistence.py` | Anti-thrash state must survive process restarts (#54923). |
| `test_compression_anti_thrash_recovery.py` | Anti-thrash recovery: the tripped guard must not be permanent (#14694). |
| `test_compression_attempt_effect.py` | Attempt telemetry names why a compression ran, what it changed, and how the summary was made. |
| `test_compression_attempt_lifecycle.py` | Attempt-lifecycle regression tests for #97488 / #96775. |
| `test_compression_attempt_ownership.py` | Attempt-ownership guards for overlapping compression attempts (#96634). |
| `test_compression_attempt_telemetry.py` | Tests: `_TodoStore`, `_Agent`, `_messages`, `_extract_telemetry`, `test_compression_attempt_telemetry_is_metadata_only`, `test_aux_call_telemetry_records_durations_without_content` … |
| `test_compression_auto_summary_fallback.py` | #116472: an ``auto``-resolved compression summary model that fails (e.g. a proxy channel answering HTTP 200 with empty content) must fall back to the main model. ``auto`` resolves a model per call without setting ``summ… |
| `test_compression_aux_fallback_authority.py` | Current-main regressions for #113322 / #130895 auxiliary compression fallback routing. |
| `test_compression_aux_fallback_route.py` | The aux-summary fallback must actually reach the main model (#123362). |
| `test_compression_boundary.py` | Tests for context compression boundary alignment. |
| `test_compression_boundary_hook.py` | Test: the context engine is notified of a compression-boundary rollover. |
| `test_compression_budget_rearm.py` | Regression test for re-arming the compression budget after tool progress. |
| `test_compression_budget_refund.py` | Behavioral tests for provider-confirmed compression-budget rearming. |
| `test_compression_busy_steer_anchor.py` | Regression coverage for busy-steer preservation across compaction (#100053). |
| `test_compression_call_llm_fallback_reported.py` | A compression summary that ``call_llm`` recovered on a fallback route is reported as a fallback. |
| `test_compression_child_source.py` | A compression child is the same conversation as its parent: it keeps the parent's persisted source (``--source tool``, ``oneshot``, an inherited ``kanban``) instead of degrading to ``agent.platform`` (#112550). |
| `test_compression_closed_adoption.py` | Compression race at the flush chokepoint: a turn writing against a session already closed by compression must adopt the LIVE continuation tip instead of dying with ``session_persistence_failed`` and a misleading "full d… |
| `test_compression_commit_fence_race.py` | Regression: out-of-order completion of overlapping ``_compress_context`` calls must not corrupt ``_active_compression_commit_fence``. |
| `test_compression_concurrent_fork.py` | Regression: prevent transcript fork when two paths compress the same session_id. |
| `test_compression_config_defaults.py` | A failed config load hands ``_parse_compression_config`` ``{}``; every key must fall back to DEFAULT_CONFIG, and an explicit ``threshold_tokens: null`` must stay the ratio-only opt-out. |
| `test_compression_count_warning.py` | Regression for #36908: the repeated-compression warning must reach the TUI / gateway, not just CLI stdout. |
| `test_compression_fallback_budget.py` | Tests for #62452 — compression fallback timeout independence + escalating timeout cooldown. |
| `test_compression_feasibility.py` | Tests for _check_compression_model_feasibility() — warns when the auxiliary compression model's context is smaller than the main model's compression threshold. |
| `test_compression_interrupt_protection.py` | Regression for #23975: context compression must survive a mid-flight gateway interrupt. |
| `test_compression_last_assistant_anchor.py` | Compaction must not deactivate the just-delivered assistant reply (#118900). |
| `test_compression_lock_defer.py` | Lock-contended compression no-ops must soft-DEFER, never exhaust (#49874). |
| `test_compression_logging_session_context.py` | Regression: compaction must move the LOGGING session context with the id. |
| `test_compression_marker.py` | #121548: model-visible elision mints the non-imitable compression marker. |
| `test_compression_max_attempts_config.py` | compression.max_attempts — config-driven compression retry cap. |
| `test_compression_orphan_recovery.py` | Recovery for legacy compression parents with no continuation child. |
| `test_compression_persistence.py` | Tests for context compression persistence in the gateway. |
| `test_compression_progress.py` | Regression: detect compression progress by tokens, not just rows. |
| `test_compression_prompt_reading.py` | Compression leaves llama-server's prompt reading out of its total time limit. |
| `test_compression_refusal_restores_transcript.py` | Regression: a refused compression candidate hands back the original transcript. |
| `test_compression_review.py` | Regressions for the #76354 review of the compression timeout architecture. |
| `test_compression_rotation_state.py` | Compression rotation hardening — state-loss fixes at the compaction boundary. |
| `test_compression_skill_safety_single_copy.py` | A compacted transcript carries the Skill Safety Rule exactly once. |
| `test_compression_small_ctx_threshold_floor.py` | Compression hygiene: small-context threshold floor, reasoning-trace exclusion, and bounded summary size. |
| `test_compression_stall_deterministic_fallback.py` | A repeated summary stall escalates to the deterministic fallback summary — #112420. |
| `test_compression_stall_fallback.py` | Compression falls back after an aborted (stalled) summary — #78981. |
| `test_compression_stall_interrupt.py` | Stall-interrupted preflight compression must persist a durable backoff. |
| `test_compression_supersession_split.py` | Candidate supersession must key on working attempts, not entry claims. |
| `test_compression_tail_threshold_share.py` | A configured trigger far below the window must leave compaction room under that trigger. |
| `test_compression_terminal_activity_persist.py` | Terminal compression activity stamps must reach the DURABLE activity projection. |
| `test_compression_timeout_terminal.py` | Host compression timeout terminates the turn before provider re-entry (#98722). |
| `test_compression_trigger_labels.py` | Each automatic compression entry point names itself in the attempt record. |
| `test_compression_worker_isolation.py` | Regressions for #76354 review F3/F4/F5 — worker isolation, durable lease cancellation, and session ContextVar repair. |
| `test_compressor_actionable_tail_anchor.py` | Regression tests for blank user echoes displacing actionable compaction state. |
| `test_compressor_assistant_tail_anchor.py` | Regression coverage for #29824 — the WebUI session viewer (and TUI chat panel) was showing the ``[CONTEXT COMPACTION — REFERENCE ONLY]`` handoff block in the slot where the user had just been reading the assistant's act… |
| `test_compressor_fallback_update.py` | Tests that _try_activate_fallback updates the context compressor. |
| `test_compressor_handoff_tail_price.py` | A handoff row never stays in the protected tail, so it must not decide where the tail cut lands. |
| `test_compressor_historical_media.py` | Tests for post-compression historical-media stripping. |
| `test_compressor_image_tokens.py` | Tests for image-token accounting in the context compressor. |
| `test_compressor_media_stripping.py` | Tests for MEDIA directive stripping in context compaction (#14665). |
| `test_compressor_stale_tool_images.py` | Retire stale vision_analyze / screenshot tool images inside the protected tail. |
| `test_compressor_tail_cut_oob_fix.py` | Regression test for #75588 — short tool-only suffix can make context compressor scan past messages, causing IndexError in _find_context_summaries(). |
| `test_compressor_tail_cut_tool_pair_floor.py` | Regression coverage: the minimum-progress floor must not split a tool group. |
| `test_compressor_tool_call_budget.py` | Regression tests for tool_call envelope accounting in the compression tail-protection budget walks (issue #28053). |
| `test_compressor_truncated_summary_guard.py` | Truncated compaction summaries must never become checkpoints. |
| `test_compressor_zero_user_guard.py` | Regression coverage for #58753 — compression could drop the only user-role message, leaving a transcript with ZERO user turns. |
| `test_concurrent_interrupt.py` | Tests for interrupt handling in concurrent tool execution. |
| `test_config_load_warning.py` | Agent config-load failures must be visible without losing defaults (#125919). |
| `test_content_policy_blocked.py` | Regression guard for #18028: provider content-policy / safety-filter blocks must classify as ``content_policy_blocked``, be non-retryable, and trigger the ``is_client_error`` abort path so the loop jumps straight to a c… |
| `test_content_policy_refusal_stop_details.py` | handle_content_policy_refusal: an Anthropic refusal with an empty body still tells the user why. |
| `test_context_breakdown.py` | Tests for live session context breakdown. |
| `test_context_compressor.py` | Tests for agent/context_compressor.py — compression logic, thresholds, and fallbacks. |
| `test_context_compressor_bench_probe.py` | The summary-model bench (fallback streak >= 2) and its persisted probe window. |
| `test_context_compressor_cross_session_guard.py` | Tests for cross-session _previous_summary contamination bug (#38788). |
| `test_context_compressor_custom_providers.py` | Per-model ``context_length`` overrides from custom_providers reach the compressor's deferred resolution (#83324). |
| `test_context_compressor_overload.py` | Sustained summary-provider overload: the abort budget, its escalation and its resets. |
| `test_context_compressor_reasoning_fallback.py` | Reasoning-model summaries must not trip the empty-content failure path. |
| `test_context_compressor_session_end_clears_state.py` | Tests for on_session_end() clearing all per-session compressor state. |
| `test_context_compressor_structural_backoff.py` | Structural no-op backoff (#93022). |
| `test_context_compressor_summary_continuity.py` | Regression tests for iterative context-summary continuity. |
| `test_context_compressor_summary_hook_compat.py` | Compatibility coverage for third-party summary hook overrides. |
| `test_context_compressor_tail.py` | Lean stale-tail demotion: a demoted ``skill_view`` body keeps its reload marker (#32106). |
| `test_context_compressor_task_heading.py` | Task-snapshot heading identity across the summarizer prompt, the template, and grounding. |
| `test_context_compressor_temporal_anchoring.py` | Tests for temporal anchoring in context-compaction summaries. |
| `test_context_compressor_zero_user_provenance.py` | Regression coverage for zero-user compaction integrity (#64539). |
| `test_context_display_provenance.py` | Estimated occupancy must not masquerade as provider usage (or vice versa). |
| `test_context_engine.py` | Tests for the ContextEngine ABC and plugin slot. |
| `test_context_engine_host_contract.py` | Regressions for the context-engine host contract. |
| `test_context_engine_message_uid.py` | A context engine sees ``message_uid`` on every message the host hands it. |
| `test_context_engine_on_turn_complete_usage.py` | Integration test: ``finalize_turn`` forwards the turn's real usage to the ``ContextEngine.on_turn_complete()`` observation hook. |
| `test_context_engine_select_context.py` | Tests for the per-turn ``ContextEngine.select_context()`` hook. |
| `test_context_estimator_multimodal.py` | Stale-call watchdog estimator prices images at the learned per-image cost, not their base64 length (#63871 / #76411; salvage of #76471 by @crdesign8). A single native screenshot read as ~100K+ tokens and selected the 60… |
| `test_context_file_sources.py` | Per-file context manifest (``agent/context_file_sources.py``) behind the ``/context`` Rules figure. |
| `test_context_pin.py` | ``model.context_length`` is a visible pin: one warning when it disagrees with the advertised window, and a ``(pinned)`` label wherever the window is rendered (#66168). |
| `test_context_references.py` | Tests: `_git`, `sample_repo`, `test_parse_typed_references_ignores_emails_and_handles`, `test_folder_listing_falls_back_when_rg_is_blocked`, `test_folder_listing_outside_cwd_inside_widened_allowed_root`, `test_folder_li… |
| `test_context_refs_concurrent.py` | Tests for concurrent @-reference expansion in context_references. |
| `test_context_route_mismatch.py` | Tests for agent_init._context_route_mismatch context-pin scoping. |
| `test_context_token_tracking.py` | Tests for context token tracking in run_agent.py's usage extraction. |
| `test_continuation_ceiling_wedge.py` | Regression tests for the post-ceiling session wedge. |
| `test_continuation_repetition_guard.py` | Regression tests for repetition-dominated response handling. |
| `test_conversation_compression_manual.py` | Invariants for the shared manual-/compress core (``agent/conversation_compression_manual``). |
| `test_conversation_fallback_state.py` | Regression tests for conversation loop fallback state management. |
| `test_conversation_loop_interpreter_shutdown.py` | Regression guard: interpreter-shutdown errors must abort the conversation loop immediately instead of retrying. |
| `test_copilot_acp_alias_compat.py` | The deprecated ``agent.copilot_acp_client`` alias keeps every listed catalog ACP plugin working. |
| `test_corruption_recovery_guidance.py` | Regression tests for #88235 — state.db corruption must surface a warning to the user's messaging platform, not stay silently in the logs. |
| `test_create_openai_client_disables_sdk_retries.py` | Regression guard: _create_openai_client must disable SDK-level retries. |
| `test_create_openai_client_kwargs_isolation.py` | Guardrail: _create_openai_client must not mutate its input kwargs. |
| `test_create_openai_client_proxy_env.py` | Regression guard: _create_openai_client must honor HTTP(S)_PROXY env vars. |
| `test_create_openai_client_reuse.py` | Regression guardrail: sequential _create_openai_client calls must not share a closed transport across invocations. |
| `test_create_openai_client_ssl_verify.py` | Regression: keepalive httpx client must honor custom CA bundles for HTTPS providers. |
| `test_credential_pool.py` | Tests for multi-credential runtime pooling and rotation. |
| `test_credential_pool_anthropic_refresh_race.py` | Regression tests for cross-process races refreshing Anthropic OAuth tokens. |
| `test_credential_pool_auto_detect.py` | Reproduction test for issue #63425: Provider auto-detection discards credential pools. |
| `test_credential_pool_codex_singleton_isolation.py` | Codex pool entries and the auth.json singleton: who may adopt whose tokens. |
| `test_credential_pool_connectors_guest.py` | A guest that does not carry inference here never serves inference through the credential pool. |
| `test_credential_pool_deferred_refresh.py` | Thread-safety of the deferred single-use-token refresh path (#71775). |
| `test_credential_pool_interrupt.py` | Regression test for #26145: credential pool rotation after interrupt-resume. |
| `test_credential_pool_key_rotation.py` | Tests for credential pool upsert — key rotation clears exhaustion state. |
| `test_credential_pool_lease_refresh_reselect.py` | acquire_lease must re-select after a deferred single-use-token refresh. |
| `test_credential_pool_no_entries_log_throttle.py` | Regression: the credential-pool "no available entries" INFO line must be throttled so an empty/exhausted pool cannot storm the shared rotating log. |
| `test_credential_pool_nous_refresh_stampede.py` | Concurrent Nous 401 recovery must not stampede the shared OAuth grant. |
| `test_credential_pool_oat_authtype.py` | Regression tests for #63737: sk-ant-oat pool entries are OAuth. |
| `test_credential_pool_oauth_writethrough.py` | Regression tests for credential-pool OAuth refresh write-through to root. |
| `test_credential_pool_operations.py` | Durable pool administration and selection invariants. |
| `test_credential_pool_plugin_seam.py` | Plugin providers in the credential pool (#116408): opaque metadata round-trips and refresh goes through the profile's ``refresh_credential`` hook — eligibility derives from the hook, never a name set. |
| `test_credential_pool_profile_oauth_fork.py` | Regression tests for #100339: cloned / borrowed single-use Anthropic OAuth grants must never fork across profiles. |
| `test_credential_pool_provider_boundary.py` | Credential pools must never cross provider or custom-endpoint boundaries. |
| `test_credential_pool_refresh_sweep_spacing.py` | A multi-entry deferred refresh sweep must leave waiter windows between holds (#124533). |
| `test_credential_pool_routing.py` | Tests for credential pool preservation through turn config and 429 recovery. |
| `test_credential_pool_seed_existing_env_sources.py` | Env-backed pool rows outside the registry tuple are hydrated on load. |
| `test_credential_pool_sole_cooldown.py` | Sole-credential cooldown: a pool with nothing to rotate to should not bench its only key for an hour on a transient throttle (429/403/5xx). |
| `test_credential_pool_sole_rotate_recovery.py` | #97315: a rotation that can only hand back the entry that was just marked exhausted is no recovery — it must return None so the turn fails. |
| `test_credential_pool_terminal_refresh_visibility.py` | A terminally rejected OAuth refresh token must leave a trace at the default log level. |
| `test_credential_pool_unmatched_rotation_bound.py` | #70401: the unmatched-identity rotation branch in ``mark_exhausted_and_rotate()`` must be bounded and must not write cooldowns onto innocent healthy keys. |
| `test_credential_rotation_route_settings.py` | Credential rotation must not carry route-scoped TLS policy. |
| `test_credential_source_labels.py` | A callable API key is labelled by its credential source, never by "is it callable". |
| `test_credit_404_fallback.py` | Regression for #115702: a paid Nous model behind an empty credit balance answers HTTP 404 ``insufficient_credits_for_paid_model``. The code must classify as billing (fallback chain armed, no retry burn) and the resultin… |
| `test_credits_cold_start.py` | Tests for cold-start credits hydration at session open. |
| `test_credits_notices_toggle.py` | Tests for the display.credits_notices config gate on _emit_credits_notices. |
| `test_credits_policy.py` | Tests for evaluate_credits_notices — pure threshold reconciliation policy (L4.1). |
| `test_credits_tracker.py` | Tests for agent.credits_tracker — CreditsState + parse_credits_headers. |
| `test_credits_usage_window.py` | Usage-window plans in agent.credits_tracker & friends. |
| `test_credits_view.py` | Tests for the /credits command — shared view core + gateway handler. |
| `test_cron_inflight_prompt_reappend.py` | Regression coverage for #100818: compaction of a single-prompt session (the cron shape) must not leave the model with nothing to obey. |
| `test_cron_inline_api_call.py` | Regression guard for #62151 — gateway cron must not wedge on the 2nd+ call. |
| `test_cross_process_turn_lease.py` | AIAgent enters turns only after acquiring and reloading durable state. |
| `test_cross_turn_reasoning_continuity.py` | Responses routes whose model renders earlier-turn reasoning keep it on the wire and through compaction. |
| `test_crossloop_client_cache.py` | Tests for cross-loop client cache isolation fix (#2681). |
| `test_ctx_halving_fix.py` | Tests for the context-halving bugfix. |
| `test_curator.py` | Tests for agent/curator.py — orchestrator, idle gating, state transitions. |
| `test_curator_activity.py` | Regression tests for curator skill activity timestamps. |
| `test_curator_backup.py` | Tests for agent/curator_backup.py — snapshot + rollback of the skills tree. |
| `test_curator_classification.py` | Tests for the curator consolidated-vs-pruned classifier. |
| `test_curator_reports.py` | Tests for the curator per-run report writer (run.json + REPORT.md). |
| `test_curator_rollback_staging.py` | Failed recovery must retain the staged files omitted from safety snapshots. |
| `test_curator_run_hygiene.py` | Curator run hygiene: what a pass costs on disk and who gets to run it. |
| `test_cursor_optimizations_parity.py` | Byte-parity checks for the per-iteration cursor optimizations. |
| `test_custom_pool_mismatch_guard.py` | Regression tests for the credential-pool provider-mismatch guard with custom providers (Bernard's Fireworks report, June 2026). |
| `test_custom_provider_ca_probes.py` | Probe-specific policy edges; real TLS handshakes live in test_ssl_transport_contracts. |
| `test_custom_provider_extra_body.py` | Tests: `test_custom_provider_extra_body_preserves_caller_override`, `test_named_custom_provider_extra_body_matches_provider_key` |
| `test_custom_provider_extra_body_matching.py` | Tests for custom-provider model matching (extra_body / service_tier drop bug). |
| `test_custom_provider_extra_headers_client.py` | Per-provider ``extra_headers`` applied to the OpenAI client (#3526 salvage). |
| `test_custom_providers_vision.py` | Tests for custom_providers[].models[].supports_vision override (#41036). |
| `test_dead_connection_cleanup.py` | Regression tests for stale provider sockets in agent-owned client pools. |
| `test_deadline.py` | Tests for agent/deadline.py — the unified deadline layer (#85125). |
| `test_deadline_fork_race.py` | Real-process deadline regression; the probe owns and reaps its whole subtree. |
| `test_declared_conversation_scope.py` | Host-declared conversation scope on the affinity-key path (issue #96811). |
| `test_deepseek_anthropic_thinking.py` | Regression guard: preserve thinking blocks on DeepSeek's /anthropic endpoint. |
| `test_deepseek_reasoning_content_echo.py` | Regression test: DeepSeek V4 thinking mode reasoning_content echo. |
| `test_degenerate_final_recovery.py` | Degenerate-final recovery (#103483). |
| `test_delegation_switch_next_session.py` | ``/delegation <backend>`` saves for the next session; ``--now`` rebuilds this session's tools. |
| `test_detached_fork_lifecycle_hooks.py` | Lifecycle-hook isolation for persistence-disabled internal forks. |
| `test_dict_tool_call_args.py` | Tests: `_tool_call`, `_response_with_tool_call`, `_FakeChatCompletions`, `_FakeClient`, `test_tool_call_validation_accepts_dict_arguments` |
| `test_direct_contexts_stream_inline.py` | Delegated children and cron turns stream on the wire (#90202, #100260). |
| `test_direct_provider_url_detection.py` | Tests: `_agent_with_base_url`, `test_direct_openai_url_requires_openai_host`, `test_direct_openai_url_accepts_native_host` |
| `test_display.py` | Tests for agent/display.py — build_tool_preview() and inline diff previews. |
| `test_display_emoji.py` | Tests for get_tool_emoji in agent/display.py — skin + registry integration. |
| `test_display_todo_progress.py` | Tests for get_cute_tool_message todo progress display. |
| `test_display_tool_failure.py` | Tests for _detect_tool_failure + _trim_error + get_cute_tool_message inline failure suffix rendering. |
| `test_dropped_tool_call_recovery.py` | Regression tests for dropped tool-call recovery. |
| `test_empty_response_fallback_refund.py` | Empty-response fallback hop refunds its API call (#77305). |
| `test_empty_response_guard.py` | Tests for agent/empty_response_guard.py (NS-503). |
| `test_empty_response_recovery_persistence.py` | Regression tests for empty-response recovery transcript persistence. |
| `test_empty_terminal_reasoning_surface.py` | Tests for reasoning-only final responses. |
| `test_empty_tool_name_loop_dampening.py` | Regression for #47967 — empty-name phantom tool calls. |
| `test_endpoint_blackhole.py` | Tests for short-circuiting probes to endpoints that blackhole TCP connects. |
| `test_endpoint_profile_seams.py` | Generic endpoint seams (``hostnames`` via ``providers.profile_for_host`` + the L3 fields/hooks) through a fake relay profile. |
| `test_engine_preflight_wire.py` | Engine-driven sub-threshold preflight maintenance (#20316, salvaged from #20424). |
| `test_entitlement_fail_closed.py` | #106475: with a single credential, a Codex ChatGPT-account entitlement 400 must fail closed — the rejected slug is skipped by the fallback walk and restore_primary_runtime must not switch back and announce an unverified… |
| `test_env_credential_turn_refresh.py` | Per-turn adoption of ~/.hermes/.env credential edits (#67821). |
| `test_env_loader_applied_homes.py` | Regression tests for #40597: _APPLIED_HOMES must be marked AFTER a real fetch attempt, so early failures (malformed config, disabled sources) stay retryable within the process instead of being permanently skipped. |
| `test_env_loader_reload_restore.py` | load_hermes_dotenv() reloads must not clobber values an external secret source resolved (#74265). |
| `test_env_loader_secret_sources.py` | Tests for the secret-source tracking in ``hermes_cli.env_loader``. |
| `test_error_classifier.py` | Tests for agent.error_classifier — structured API error classification. |
| `test_error_classifier_content_policy.py` | Provider safety-filter refusals classify as content_policy_blocked, never as a retryable outage. |
| `test_error_classifier_data_policy.py` | A Nous 403 ``data_policy_denied`` is deterministic for this context: no retry, no rotation, no fallback. |
| `test_error_classifier_observed.py` | Provider error bodies observed in real sessions, through the real SDK exception types. |
| `test_error_classifier_reasoning_level.py` | A 400 that names the reasoning field and refuses its *value* against a closed level set. |
| `test_error_classifier_upstream_blocked.py` | A 403 written by a WAF/CDN in front of the provider is not an API-key rejection (#53099, #70566). |
| `test_error_surface.py` | Tests for agent/error_surface.py — turn-error → UI layer descriptors. |
| `test_estimator_parity.py` | Regression tests for #84371 — compaction dead-loop on reasoning-heavy codex_responses sessions. |
| `test_exit_cleanup_interrupt.py` | A second Ctrl+C during cron finalization must not skip resource cleanup. |
| `test_export_current_turn_boundary.py` | The loop exports ``{turn_id, current_turn_user_idx}`` beside the exact ``messages`` it addresses, and only when that row is this turn's user message verbatim. |
| `test_external_process_provider_init.py` | External-process profiles receive their resolved ACP launch details at client construction. |
| `test_external_process_streaming.py` | Streaming is a provider capability, not an authentication mechanism. |
| `test_external_skills.py` | Tests for external skill directories (skills.external_dirs config). |
| `test_external_skills_dirs_cache.py` | Guards for ``get_external_skills_dirs`` mtime-based memo. |
| `test_failed_turn_chat_copy.py` | Terminal failed-turn results carry a specific ``failure_reason`` and plain-language chat copy on every surface (the CLI-only 💡 hints used to be the only place with a next step). |
| `test_failed_turn_site_codes.py` | Deterministic loop outcomes (context overflow, empty reply, persistence failure) end as failed turns whose chat copy names the slash command to run, and whose ``failure_reason`` lets the desktop card pick a code-specifi… |
| `test_failover_identity.py` | Tests for system-prompt model-identity sync across provider failover. |
| `test_fallback_429_after_timeout.py` | Regression test for #32646: fallback_providers not activated when HTTP 429 follows a successful primary-transport recovery. |
| `test_fallback_api_mode_preservation.py` | Fallback activation must preserve the Anthropic wire signal (PR #79787). |
| `test_fallback_credential_isolation.py` | Tests for fallback credential pool isolation. |
| `test_fallback_dynamic_credential.py` | Fallback rebuilds retain the credential source, not its last token. |
| `test_fallback_entry_base_url.py` | A ``fallback_providers`` entry's ``base_url`` must reach the client (#121359). |
| `test_fallback_exhaustion_cooldown.py` | Regression tests for #24996 — fallback-switch storm on host memory. |
| `test_fallback_reasoning_override.py` | Tests for per-model reasoning_effort override during fallback activation. |
| `test_fallback_restore_codex_early_reopen.py` | A session pinned to its fallback returns to a Codex primary whose quota window reopened early. |
| `test_fast_compression_lane.py` | Contract tests for the opt-in non-reasoning compression fast lane. |
| `test_fast_mode_auto.py` | Bounded /fast auto\|cold windows and the shared route-aware gate. |
| `test_file_mutation_verifier.py` | Tests for the per-turn file-mutation verifier footer. |
| `test_file_safety.py` | Tests for agent/file_safety.py read guards — env file blocking. |
| `test_file_safety_container_mirror.py` | Tests for the container-context sandbox-mirror guard (#32049 follow-up). |
| `test_file_safety_credentials.py` | Tests for HERMES_HOME credential-file read blocking in file_safety. |
| `test_file_safety_cross_profile.py` | Tests for the active-profile resolver in agent/file_safety. |
| `test_file_safety_sandbox_mirror.py` | Tests for the sandbox-mirror write guard in agent/file_safety. |
| `test_file_safety_session_state.py` | Session transcript stores are read-only to agent file tools. |
| `test_file_safety_write_credentials.py` | Secret stores under HERMES_HOME are write-denied; control files stay writable (#110464). |
| `test_first_chunk_at_hook.py` | Regression tests for first_chunk_at in the post_api_request hook (#98555). |
| `test_flush_diverts_on_corrupt_state_db.py` | Agent flush path: a quarantined (structurally corrupt) SessionDB diverts to JSONL. |
| `test_flush_uid_reinsert_guard.py` | Regression test: restored rows must not be re-INSERTed by the flush. |
| `test_free_tier_rate_limit_class.py` | Every free-tier refusal offers sign-in: any anonymous 429 (reason or not) and a 402 from the welcome host classify as a welcome refusal; a signed-in account's identical response does not. |
| `test_future_timeout_worker_death.py` | A worker that DIES raising a timeout-class error must not be mistaken for a live one. |
| `test_gateway_turn_sidecar.py` | Gateway must-deliver notes on the current user message. |
| `test_gemini_alias_native_route.py` | Provider aliases preserve the native-vs-compatible client boundary. |
| `test_gemini_fast_fallback.py` | Regression tests for #11314 — credential-pool rotation vs. fallback. |
| `test_gemini_free_tier_gate.py` | Tests for Gemini free-tier detection and blocking. |
| `test_gemini_key_surface_guidance.py` | Tests for the 403 PERMISSION_DENIED key-surface guidance (#115306). |
| `test_gemini_long_decode.py` | Gemini long decode: dropped streams resume from the last checkpoint, hops are bounded, usage splits billing from context. |
| `test_gemini_native_adapter.py` | Tests for the native Google AI Studio Gemini adapter. |
| `test_gemini_native_reservation.py` | Native Gemini output-token reservation at agent init (#57275 claim 4). |
| `test_gemini_schema.py` | Tests for agent.gemini_schema — OpenAI→Gemini tool parameter translation. |
| `test_gemini_standard_key_guidance.py` | Tests for Gemini legacy Standard-key auth guidance. |
| `test_gemini_thinking_config.py` | Disabling reasoning must actually stop (or minimise) Gemini thinking (#91927). |
| `test_gemini_type_arrays.py` | Native tool translation must preserve union alternatives at every depth. |
| `test_generated_media_durable.py` | Generated image/video output must survive the gateway media sweep (#126445). |
| `test_ghost_skill_pruning.py` | Ghost-skill defense tests (#32106, salvage of PR #44166). |
| `test_glm_context_window_resolution.py` | GLM context windows: hyphenated relay slugs, provider-level custom overrides, and the aux feasibility check inherit the right window instead of the ``glm`` 202,752 catch-all (#97398, #98387, #89500). |
| `test_grid_sweep_cli_tui_stream_diagnostics.py` | Code-flow grid sweep (NOUS-368, wave 2): pre-existing automatic diagnostics on the CLI/TUI/stream rails that bypassed the warning boundary. Each cell: absent/false = legacy bytes, true = only the diagnostic disappears;… |
| `test_hermetic_side_effect_guards.py` | Regression tests for hermetic guards around local desktop side effects. |
| `test_hold_stream_agent.py` | A ``hold_stream`` plugin holds the agent's user-facing text until its rewrite lands. |
| `test_hold_stream_edges.py` | A held turn (``hold_stream=True`` transform) never lets the original text out by a side path. |
| `test_hold_stream_exits.py` | Every exit of a held turn (``hold_stream=True`` transform) goes through the turn-start transform snapshot, and every assistant row the user did not get stays out of history. |
| `test_hygiene_timeout_cooldown_isolation.py` | Pre-agent hygiene retry spacing must not block in-agent compression. |
| `test_i18n.py` | Tests for agent.i18n -- catalog parity, fallback, language resolution. |
| `test_i18n_languages.py` | Language identity: every bundled catalog has an endonym row and vice versa; ``language_options`` is ``en`` first, endonym-only, and reports where each language comes from. |
| `test_i18n_layers.py` | Layered i18n: user overlay > bundled, plugin pack > overlay, partial packs fall through, pack-only languages become supported, and unload drops the layer. Real temp homes, a real plugin directory with a manifest loaded… |
| `test_i18n_tui_packs.py` | Bundled TUI packs: ``locales/<lang>.tui.yaml`` mirror ``locales/_keys.tui.json`` and are served by ``i18n.catalog {surface: 'tui'}`` underneath overlay and plugin packs. |
| `test_identity_flush.py` | Regression tests for identity-based SessionDB flushing (#46053). |
| `test_idle_compaction.py` | Tests for the opt-in idle-triggered compaction policy. |
| `test_idle_compaction_lock_and_guards.py` | Idle-triggered compaction: interaction with the compression guards. |
| `test_image_corrupt_recovery.py` | Tests for reactive recovery when a provider rejects an image as corrupt. |
| `test_image_eviction_policy.py` | Arithmetic contract of the shared send-path image-eviction policy (#113517). |
| `test_image_gen_registry.py` | Tests for agent/image_gen_registry.py — provider registration & active lookup. |
| `test_image_generate_parallel.py` | Regression tests for parallel image-generation tool batches. |
| `test_image_rejection_fallback.py` | Tests for the image-rejection fallback in run_agent. |
| `test_image_replay.py` | Turns rebuilt from the session DB re-attach the newest retained user images (agent/image_replay.py). |
| `test_image_routing.py` | Tests for agent/image_routing.py — the per-turn image input mode decision. |
| `test_image_shrink_recovery.py` | Tests for reactive image-shrink recovery. |
| `test_image_token_cost.py` | Per-image token cost learned from provider usage (agent/image_token_cost.py, #70328). |
| `test_in_place_commit_rollback.py` | Regression test for #99477: a FAILED in-place compaction commit must roll the live transcript back to its pre-compression snapshot. |
| `test_in_place_compaction.py` | Tests for in-place context compaction (config: compression.in_place, #38763). |
| `test_in_place_merged_user_rows.py` | In-place compaction over a turn that was killed before it finished. |
| `test_in_place_persist_marker.py` | Regression test for #98450: in-place batch compaction commit must stamp _DB_PERSISTED_MARKER on the committed dicts. |
| `test_in_place_preflight_rewind.py` | In-place compaction's positional rewind must land on the carried tail's own originals. |
| `test_infinite_compaction_loop.py` | Tests for the infinite compaction loop fix (issue #40803). |
| `test_init_exhausted_pool_billing_error.py` | An exhausted (402) provider pool must be named as a billing failure at init. |
| `test_init_fallback_on_exhausted_pool.py` | Regression test for #17929: AIAgent.__init__ should try fallback_model when primary provider credentials are exhausted. |
| `test_init_fallback_refusal_warning.py` | A fully-refusing init-time fallback ladder must say why at WARNING before dying. |
| `test_injected_param_strip_retry_registry.py` | Registry walk for the injected-parameter strip-and-retry safety class. |
| `test_inline_edit_persistence.py` | Real edit -> executor -> SQLite -> history projection, without model calls. |
| `test_inline_session_search_profile.py` | The inline ``session_search`` executor forwards ``profile`` so a routed gateway agent can read a named profile's store instead of silently searching the injected (default) DB (#82903). |
| `test_inline_tool_executors_memory_args.py` | The inline memory alias persists writes and preserves content precedence. |
| `test_insights.py` | Tests for agent/insights.py — InsightsEngine analytics and reporting. |
| `test_intent_ack_continuation.py` | Intent-ack continuation gate + detector behavior. |
| `test_interpreter_shutdown_turn_exit.py` | Interpreter-shutdown handling in the conversation loop's outer retry path. |
| `test_interrupt_compat.py` | Compatibility contract for explicit hard-stop producers. |
| `test_interrupt_issuer_attribution.py` | ``interrupt()`` records who asked for the stop, so the turn exit reason can attribute it (#112647). |
| `test_interrupt_propagation.py` | Test interrupt propagation from parent to child agents. |
| `test_invalid_context_length_warning.py` | Tests that invalid context_length values in config produce visible warnings. |
| `test_iron_proxy.py` | Hermetic tests for the iron-proxy egress integration. |
| `test_iron_proxy_e2e.py` | End-to-end smoke test for the iron-proxy egress integration. |
| `test_iteration_budget_race.py` | Tests for IterationBudget thread safety. |
| `test_iteration_budget_warning.py` | Iteration checkpoints preserve the transcript and the hard budget. |
| `test_iteration_summary_reasoning_details.py` | The max-iterations summary call treats ``reasoning_details`` per api_mode: the anthropic_messages converter rebuilds signed thinking blocks from it, so the summary messages must keep it; a strict chat-completions route… |
| `test_jiter_preload.py` | Tests: `test_preload_jiter_native_extension_loads_sdk_parser_dependency`, `test_preload_jiter_native_extension_is_best_effort` |
| `test_kanban_budget_checkpoint.py` | Checkpoint eligibility follows explicit opt-in or dispatcher ownership. |
| `test_kanban_stop.py` | Tests for the kanban worker turn-end stop guard. |
| `test_kanban_turn_recovery.py` | Tests for kanban worker in-place turn recovery and the shared exit policy. |
| `test_kimi_coding_anthropic_thinking.py` | Kimi / Moonshot thinking behavior on the Anthropic-Messages wire. |
| `test_kimi_coding_openai_base_url.py` | Tests: `_fake_openai_factory`, `test_create_openai_client_normalizes_kimi_coding_base_url`, `test_create_openai_client_preserves_already_suffixed_kimi_url` |
| `test_last_total_tokens.py` | Test that last_total_tokens is correctly set by ContextCompressor. |
| `test_lean_single_aux_call.py` | Lean compaction makes EXACTLY ONE auxiliary LLM request per attempt. |
| `test_learn_prompt.py` | Tests for /learn — open-ended skill distillation. |
| `test_learning_graph.py` | Behavior contracts for the learning-graph assembler. |
| `test_learning_graph_render.py` | Behavior contracts for the terminal Star Map renderer. |
| `test_learning_mutations.py` | Behavior contracts for journey node edit/delete (agent.learning_mutations). |
| `test_left_core_kept_notice_delivery.py` | Notices a left-core migration kept for a home (a gateway start, a CLI resolution) reach the first turn someone sees: an agent nobody watches (cron run, subagent, background fork) starts and runs without claiming them, s… |
| `test_legacy_cli.py` | The packaged ``hermes-agent`` console script honours argv (#54648). |
| `test_length_continuation_thinking_exhaustion.py` | Regression tests for thinking-only length truncations. |
| `test_length_continuation_window_headroom.py` | Length continuation stops when the PROMPT filled the context window (#106120). |
| `test_litellm_tool_part_cache_markers.py` | Regression tests for #89886: part-level cache_control on role:tool messages must be suppressed on LiteLLM-style envelope routes. |
| `test_live_db_preview_locks.py` | File previews may not cancel SQLite's live POSIX locks (including WAL sidecars). |
| `test_llamacpp_alias_managed_endpoint.py` | A bare llama.cpp alias resolves to the profile's managed local server, and only to it. |
| `test_lmstudio_load_mode.py` | Tests: `_agent`, `test_lmstudio_jit_load_mode_skips_explicit_preload`, `test_explicit_budget_below_loaded_runtime_limits_effective_context` |
| `test_lmstudio_reasoning.py` | Reasoning-effort resolution for LM Studio. |
| `test_load_time_durability_stamp.py` | Regression (#92231): resumed transcripts must not re-append to state.db. |
| `test_local_probe_disk_cache.py` | Tests for the local-endpoint probe disk L2 cache in agent/model_metadata. |
| `test_local_prompt_progress.py` | llama-server prompt progress, sleep-aware stall timers, and the local stale-breaker reset. |
| `test_local_stream_timeout.py` | Tests for local provider stream read timeout auto-detection. |
| `test_local_tool_batches.py` | Local batches use the live agent pipeline, not registry fan-out. |
| `test_lock_fallback_base_semantics.py` | Steer requeue/drain semantics and the ``_is_openai_client_closed`` truth table. |
| `test_malformed_tool_args_no_fallback.py` | A 400 for the model's own malformed tool-call JSON must not walk the fallback chain (#12770). |
| `test_malformed_tool_arguments.py` | Malformed model tool arguments are rejected at the dispatch boundary. |
| `test_manual_compression_feedback.py` | Behavioral coverage for manual compression status messages. |
| `test_manual_compression_refusal_feedback.py` | Regression tests: manual /compress feedback for a would-grow refusal. |
| `test_markdown_tables.py` | Tests for `agent.markdown_tables.realign_markdown_tables`. |
| `test_materialize_data_url_cleanup.py` | Regression test: temp file cleanup when materializing data URLs for vision. |
| `test_max_iteration_handoff.py` | Shared classification of a non-failed iteration-cap turn (#102213). |
| `test_mcp_execution_deadline.py` | A server-owned deadline must survive the outer executor without widening a sibling batch. |
| `test_memory_agent_context.py` | Regression for #80646: the ``agent_context`` handed to memory providers follows the platform (``cron`` / ``subagent`` skip writes per the ``MemoryProvider.initialize`` contract) instead of a hardcoded ``"primary"`` that… |
| `test_memory_async_sync.py` | Regression guard: end-of-turn memory sync must not block the turn. |
| `test_memory_boundary_commit.py` | Tests for MemoryManager.commit_session_boundary_async. |
| `test_memory_context_dedupe.py` | A recalled bullet is stated once per ``<memory-context>`` block. |
| `test_memory_migration_notifications.py` | A configured memory provider that cannot be recovered at agent start is shown to the user, never only logged (#119769): the CLI prints it; other drivers get a warn notice, which a messaging-gateway agent (callbacks wire… |
| `test_memory_provider.py` | Tests for the memory provider interface, manager, and builtin provider. |
| `test_memory_provider_caller_profile.py` | PLG-11 (#140058): a memory-provider tool call belongs to the calling turn's profile. |
| `test_memory_provider_init.py` | Regression tests for memory provider selection during AIAgent init. |
| `test_memory_provider_unavailable_warning.py` | Regression tests for NousResearch/hermes-agent#2765. |
| `test_memory_recall_indicator.py` | MemoryManager.describe_recall — the deterministic recall indicator. |
| `test_memory_session_switch.py` | Tests for the on_session_switch hook and session_id propagation. |
| `test_memory_skill_scaffolding.py` | MemoryManager strips slash-skill scaffolding for every provider. |
| `test_memory_stalled_background_call.py` | A background provider call that never returns pins its mem-sync worker thread forever (Python cannot stop a thread), and MemoryManagers are rebuilt per agent. The process-wide gate skips calls once _MAX_STUCK_CALLS call… |
| `test_memory_sync_interrupted.py` | Regression guard for #15218 — external memory sync must skip interrupted turns. |
| `test_memory_sync_redaction.py` | Every MemoryManager fan-out scrubs secrets before a memory provider sees them (#115104). |
| `test_memory_user_id.py` | Tests for per-user memory scoping via user_id threading. |
| `test_memory_write_bridge.py` | Behavior tests for the built-in memory → external provider bridge. |
| `test_merged_user_override.py` | A replayed merged row keeps the unanswered request and exact wire sidecar. |
| `test_message_content.py` | Tests: `test_flatten_message_text_accepts_chat_and_responses_text_parts`, `test_flatten_message_text_accepts_object_parts` |
| `test_message_metadata.py` | Tests: `test_stamp_preserves_source_timestamp`, `test_append_stamps_same_mapping_at_append_time` |
| `test_message_reactions.py` | Message reactions: persistence, tapback semantics, and cache safety. |
| `test_message_sanitization_policy.py` | Tests for the single-owner call_id + reasoning_content policies. |
| `test_message_sequence_repair.py` | Tests for pre-API-call message-sequence repair. |
| `test_meta_agent_init.py` | Tests for AIAgent provider=meta host-mandated api_mode. |
| `test_meta_usage_cache_reporting.py` | Usage cache reporting for Meta Responses path. |
| `test_micro_compaction.py` | Tests for per-turn micro-compaction in ``ContextCompressor``. |
| `test_mid_turn_compaction_turn_boundary.py` | Tests: `test_post_tool_compression_reanchors_the_active_user_boundary`, `_response`, `test_pre_api_compression_mid_turn_keeps_this_turns_tool_pair_on_the_wire` |
| `test_minimax_auxiliary_url.py` | Tests for Anthropic-to-OpenAI auxiliary URL normalization. |
| `test_minimax_provider.py` | Tests for MiniMax provider hardening — context lengths, thinking, catalog, beta headers, transport. |
| `test_missing_provider_credentials_hint.py` | The "no credentials" error for an explicit provider names a remedy that can actually work. |
| `test_mistral_tool_ids.py` | Mistral rejects any tool id that is not exactly 9 alphanumeric characters. |
| `test_moa_aggregator_cache_control.py` | MoA aggregator cache decoration: the acting aggregator (``MoAChatCompletions``) and advisor fan-out are re-read across iterations and stay decorated; the one-shot ``/moa <prompt>`` synthesis (``aggregate_moa_context``)… |
| `test_moa_aggregator_cost_slot.py` | Tests for MoA aggregator-slot exposure used by session cost accounting. |
| `test_moa_aggregator_prefix_stability.py` | MoA aggregator requests must grow as a byte-stable prefix across tool-loop iterations. |
| `test_moa_alternation_recovery.py` | MoA aggregator: strict-alternation destinations get their adjacent same-role messages merged reactively and per destination (#112358, last atom). |
| `test_moa_cold_start_cache.py` | Regression tests for MoA cold-start caching (#66793). |
| `test_moa_context_max_tokens.py` | Regression test for aggregate_moa_context's reference/aggregator max_tokens split. |
| `test_moa_fanout_cadence.py` | every_n fanout cadence: advisors refresh every Nth tool iteration and off-cadence iterations reuse the cached guidance from the last on-cadence run. |
| `test_moa_fanout_liveness.py` | MoA fan-out must stamp the turn-liveness activity clock (#110015). |
| `test_moa_loop_mode.py` | Tests: `_response`, `test_moa_virtual_provider_aggregator_is_actor`, `test_moa_runtime_provider_uses_virtual_endpoint`, `test_moa_primary_restore_rebuilds_virtual_facade`, `test_moa_restored_facade_still_emits_reference… |
| `test_moa_observability_bridge.py` | Per-advisor MoA metrics crossing the plugin-hook boundary. |
| `test_moa_prepared_request_client_swap.py` | `_moa_prepared_request` must never reach a client that cannot consume it. |
| `test_moa_prepared_request_leak.py` | Test: _moa_prepared_request does not leak to native OpenAI clients (#78382). |
| `test_moa_privacy_filter.py` | MoA privacy redaction filter (config: moa.privacy_filter — display \| full). |
| `test_moa_progress.py` | Tests for the MOA progress indicator added in issue #59546. |
| `test_moa_quiet_reference_output.py` | MoA display events honour the ``-Q`` quiet contract. |
| `test_moa_reasoning_effort.py` | Tests: `_response`, `test_slot_reasoning_config_parses_effort_and_none`, `test_moa_reference_passes_per_slot_reasoning_config`, `TestAggregatorGlobalFallback` |
| `test_moa_slot_api_mode.py` | Tests for MoA slot_runtime api_mode propagation (issue #54379). |
| `test_moa_slot_max_tokens.py` | Tests for per-slot max_tokens in MoA reference calls. |
| `test_moa_slot_request_headers.py` | MoA reference slots ask a provider's ``request_headers`` through the same route as the main loop: memoized, and a failing hook keeps the agent's session on the generic answer. |
| `test_moa_stale_guidance_note.py` | Cached advisor guidance must announce that it predates the tool results below it. |
| `test_moa_streaming.py` | Tests for MoA aggregator streaming. |
| `test_moa_switch_api_mode.py` | Regression test for MoA primary-call routing on persisted preset switches. |
| `test_moa_trace_streamed_capture.py` | Tests for MoA trace aggregator-output capture across streaming modes. |
| `test_model_extra_type_guard.py` | Regression test for PR #15157: non-dict ``model_extra`` must not crash tool-call normalization. |
| `test_model_metadata.py` | Tests for agent/model_metadata.py — token estimation, context lengths, probing, caching, and error parsing. |
| `test_model_metadata_cache.py` | Concurrent writers of ``context_length_cache.yaml`` (race audit lostupdate-7). |
| `test_model_metadata_http.py` | Exercise probe transport redirects, proxies, and early response closure. |
| `test_model_metadata_local_ctx.py` | Tests for _query_local_context_length and the local server fallback in get_model_context_length. |
| `test_model_metadata_probe_deadline.py` | Model-metadata probes have a total wall-clock bound, not just per-op httpx timeouts. |
| `test_model_streaming_config.py` | ``model.streaming`` config seeds the session's streaming decision (#72901). |
| `test_models_dev.py` | Tests for agent.models_dev — models.dev registry integration. |
| `test_models_dev_fetch_deadline.py` | The models.dev download has a total wall-clock bound, not just a per-read timeout. |
| `test_models_dev_provider_capabilities.py` | Plugin-declared per-model capabilities (#102115): one declaration on ``ProviderProfile`` feeds every models.dev consumer — capability lookup, context lookup, the picker's reasoning badge and image routing. |
| `test_moonshot_schema.py` | Tests for Moonshot/Kimi flavored-JSON-Schema sanitizer. |
| `test_multimodal_interim.py` | Tests for issue #66267 — multimodal (list) tool-result content must not crash interim-assistant-message handling or non-streaming message building. |
| `test_multimodal_tool_content_recovery.py` | Tests for reactive multimodal-tool-content recovery. |
| `test_multimodal_tool_result_spill.py` | Oversized TEXT parts inside a multimodal tool envelope must go through the same persistence policy as string results (#95429): a ``browser_exec`` call that captured a screenshot bakes its whole stdout into the envelope'… |
| `test_multiplex_base_url_scope.py` | Multiplex invariant: a scoped API key is never paired with the DEFAULT profile's base URL / proxy. |
| `test_multiplex_cloud_credential_clients.py` | Cloud-SDK credential clients under ``gateway.multiplex_profiles``: boto3 and azure-identity freeze the credential chain into the client at construction, so a slot keyed by region / config alone would sign a served profi… |
| `test_native_compaction.py` | Tests for native OpenAI Responses server-side compaction (gpt-5.6 only). |
| `test_native_compaction_nontext_retention.py` | Regression coverage for image-only user content across native compaction. |
| `test_native_compaction_summary_retention.py` | Tests for native compaction summary retention during pre-checkpoint pruning (#90975). |
| `test_native_compaction_switch_capabilities.py` | Tests: `_agent`, `test_trusted_destination_capabilities_are_explicitly_enabled`, `test_untrusted_destination_capabilities_are_explicitly_denied`, `test_default_openai_destination_is_enabled_without_explicit_base_url`, `… |
| `test_native_compaction_typed_user_retention.py` | Retain the newest typed (input_text) ask at a native checkpoint boundary. |
| `test_native_preflight_estimate.py` | Native Responses preflight must count the checkpoint-pruned wire (#96155). |
| `test_non_chat_primary_restore.py` | A primary already known to be non-chat must not be restored on the next turn. |
| `test_non_stream_stale_timeout.py` | Tests for the non-stream stale-call detector context estimator. |
| `test_none_deref_guards.py` | Regression tests for None-dereference guards on ``.get(key, "").method()`` patterns (#55997 salvage + config-derived sibling sites). |
| `test_nonretryable_error_html_summary.py` | Regression: non-retryable API failures must not leak raw HTML pages. |
| `test_nonretryable_result_carries_verdict.py` | A non-retryable 4xx (rejected OAuth token, bad key) must reach UI clients with the classifier's verdict: without ``failure_reason`` the desktop error card read a 401 as a retryable "Provider error" and offered Retry ins… |
| `test_nonstream_wait_notice.py` | Wait status describes request-local silence, never active generation. |
| `test_notice_spine.py` | Regression tests for the notice-spine (AgentNotice + emitter callbacks). |
| `test_notification_persistence.py` | A muted wake keeps durable evidence while hiding only its new presentation rows. |
| `test_nous_credits_gauge.py` | Tests for the Nous-credits subscription % gauge in build_nous_credits_snapshot. |
| `test_nous_credits_snapshot.py` | Tests for build_nous_credits_snapshot (L6-A, magnitudes-only). |
| `test_nous_fallback_unavailable.py` | Tests for Nous fallback local-availability suppression. |
| `test_nous_key_pre_expiry_adoption.py` | Nous agent keys live ~1 h. Every agent in a process must not learn about expiry from its own 401. |
| `test_nous_portal_anthropic_wire.py` | Nous Portal ``anthropic/*`` models route on the native Messages wire. |
| `test_nous_rate_guard.py` | Tests for agent/nous_rate_guard.py — cross-session Nous Portal rate limit guard. |
| `test_nous_usage_profile_context.py` | Tests: `test_nous_account_fetch_preserves_profile_home_in_timeout_worker` |
| `test_nous_welcome_client_contract.py` | The client side of the Nous welcome tier's gateway contract: auxiliary calls on the welcome host use its one model, the ``x-nous-model-switch`` header moves a session off ``nous/welcome``, and refusal copy names the way… |
| `test_nous_wire_auto.py` | ``nous.anthropic_wire: auto`` decides a session's wire once, from its first response. |
| `test_nt_namespace_guard.py` | Windows NT/device-namespace paths are rejected on the RAW string, before any resolution. |
| `test_ollama_num_ctx.py` | Tests for Ollama num_ctx context length detection and injection. |
| `test_onboarding.py` | Tests for agent/onboarding.py — contextual first-touch hint helpers. |
| `test_onboarding_first_tasks.py` | ``agent/onboarding_first_tasks.py``: which first tasks the model may put on the build card. |
| `test_onboarding_flow.py` | ``agent/onboarding_flow.py``: the beats, the run record and every event, across machine fixtures. |
| `test_onepassword_secrets.py` | Hermetic tests for the 1Password (`op` CLI) secret source. |
| `test_oneshot.py` | Tests for agent.oneshot — shared one-off (stateless) LLM requests. |
| `test_oneshot_footprint.py` | One-shot sessions (``hermes chat -q``) trim the self-improvement prompt footprint. |
| `test_oneshot_interactive_surface.py` | A one-shot run (``hermes chat -q`` / ``-z``) has nobody to ask, steer, or live-control children for. |
| `test_openai_client_lifecycle.py` | Tests: `FakeRequestClient`, `FakeSharedClient`, `OpenAIFactory`, `_build_agent`, `_connection_error`, `test_retry_after_api_connection_error_recreates_request_client` … |
| `test_openai_ultrafast.py` | OpenAI Ultrafast (``service_tier: "ultrafast"``): one tier word table, a per-model request gate, and pricing from the tier the response was SERVED at. Relationship tests, no catalog snapshots. |
| `test_opencode_session_affinity.py` | x-opencode-session rides on every OpenCode request, on every transport. |
| `test_openrouter_response_cache.py` | Tests for OpenRouter response caching header injection. |
| `test_openrouter_silent_default_purge.py` | Regression tests for issue #81952 — aux free default + env-ingestion WARNING. |
| `test_outbound_stale_vision.py` | Send-path eviction of stale vision_analyze / screenshot tool payloads. |
| `test_outbound_webhooks.py` | Tests for the outbound webhook dispatcher (agent.outbound_webhooks). |
| `test_outer_error_retry_bound.py` | Tests for issue #92450 — outer-loop error retries must be bounded even when the turn budget (``max_iterations``) is unlimited. |
| `test_output_cap_parsing.py` | Tests: `TestParseOpenRouterOutputCap`, `TestParseCharBasedOutputCap`, `TestParseDashScopeOutputCap`, `TestParseMaximumOutputTokensCap`, `TestIsOutputCapError`, `TestParseVllmTokenBasedOutputCap` … |
| `test_over_window_compression_fail_closed.py` | An over-window session that compression cannot shrink must not block the host toward the compression ceiling or send a request the model cannot accept (#116472). |
| `test_overflow_overhead_aware_tokens.py` | Overflow recovery handlers (413, context overflow, Anthropic long-context tier 429) must hand the compressor an overhead-aware token estimate that counts tool schemas, not a messages-only estimate (LCM issue 441). Also:… |
| `test_overflow_partial_terminal.py` | Regression tests for #106260: a context-overflow error after partial stream delivery must NOT seed a continuation stub with the recovered text. |
| `test_owned_process_cleanup.py` | Agent teardown owns processes, not their shared terminal environment. |
| `test_partial_stream_continuation_prompt.py` | After a mid-stream transport cut the continuation must keep tools on the table (#74990). |
| `test_partial_stream_finish_reason.py` | Regression tests for issue #30963 — partial-stream stub finish_reason. |
| `test_per_model_compression_threshold.py` | Tests for per-model compression threshold overrides. |
| `test_per_model_provider_routing.py` | ``provider_routing.models.<id>`` overlays the flat OpenRouter routing for the CURRENT agent.model. |
| `test_per_model_threshold_init_ordering.py` | Follow-up regression tests for per-model compression threshold overrides. |
| `test_percentage_clamp.py` | Tests for percentage clamping at 100% across display paths. |
| `test_periodic_scheduler.py` | agent/periodic_scheduler: one timer thread dispatches isolated callbacks. |
| `test_periodic_scheduler_context.py` | Context propagation contract for the shared periodic scheduler. |
| `test_pet_engine.py` | Tests for the petdex pet engine (agent/pet/*). |
| `test_phantom_tool_references.py` | Phantom tool references: system-prompt blocks must not name tools the session can't call (Blank Slate audit, Aug 2026). |
| `test_plan_limits.py` | agent/plan_limits.py: the one rule (what a full allowance blocks), the suggestions after a usage-window refusal (the plan's recommended models that still work), and the copy for surfaces without buttons. |
| `test_plan_prompt.py` | Tests for the built-in /plan command (formerly the bundled `plan` skill). |
| `test_plan_snapshot_sync.py` | Reply headers that contradict the cached plan refresh it once, in the background. |
| `test_platform_hint_cron_delivery.py` | A cron agent's system prompt carries its delivery channel's hint. |
| `test_platform_hint_desktop.py` | System-prompt assembly for the desktop chat surface. |
| `test_platform_hint_overrides.py` | Tests for per-platform prompt-hint overrides (config.yaml → platform_hints). |
| `test_plugin_context_engine_clone.py` | A plugin-registered context engine is one shared instance; agent init hands each agent its own copy through ``clone_for_agent()`` (default deepcopy), so engines with uncopyable state (locks, SQLite connections — hermes-… |
| `test_plugin_context_engine_init.py` | Tests that plugin context engines get update_model() called during init. |
| `test_plugin_context_references.py` | Tests for plugin context reference provider API (Issue #26193). |
| `test_plugin_live_notes_delivery.py` | A plugin that goes live while a turn runs is told to the model in that turn, once. |
| `test_plugin_llm.py` | Unit tests for the plugin LLM facade (``agent.plugin_llm``). |
| `test_plugin_llm_task_routing.py` | Tests for plugin auxiliary-task routing via ``ctx.llm.complete(task=...)``. |
| `test_plugin_prompt_sections.py` | Tests: `_real_agent`, `_install_test_section`, `test_real_aiagent_freezes_section_within_life_and_rerenders_on_invalidate`, `test_fresh_process_resume_restores_identical_full_prompt_without_callback` |
| `test_plugin_stream_hooks.py` | Tests: `_agent`, `_wait_for`, `_make_stream_chunk`, `_callbacks`, `test_stream_delta_plugin_hook_is_queued_off_token_path`, `test_stream_delta_plugin_hook_error_does_not_break_streaming` … |
| `test_pool_revert_after_cooldown.py` | A live session rotated off a quota-benched credential moves back once the bench lifts. |
| `test_pool_rotation_endpoint_veto.py` | Mid-run credential rotation never rebinds a session to a same-provider entry for another endpoint. |
| `test_portal_tags.py` | Tests for agent.portal_tags — Nous Portal request tag contract. |
| `test_post_compaction_hook.py` | ``post_compaction`` fires once per committed compaction, never for an attempt that changed nothing, and a raising plugin never changes what the compaction returns (#118382). |
| `test_post_compression_trim.py` | A successful compaction hands allocator pages back to the OS. |
| `test_post_tool_compression_attempt_cap.py` | Behavioral regression tests for the post-tool compression attempt cap. |
| `test_pre_compress_checkpoint_contract.py` | Host-side contract tests for the opt-in pre-compress checkpoint API (v2). |
| `test_pre_compress_memory_context.py` | Behavior contracts for memory-provider context in compression prompts. |
| `test_pre_compress_memory_context_handoff.py` | Behavior contracts for the pre-compression memory-context handoff. |
| `test_preflight_compression_cap_e2e.py` | E2E: compression.max_attempts=6 drives a 4th+ preflight compaction pass. |
| `test_preflight_compression_gate.py` | Regression tests for issue #27405. |
| `test_preflight_compression_timeout_fail_closed.py` | Regression coverage for stalled preflight compression. |
| `test_preflight_lock_defer.py` | Preflight lock-defer must not arm the insufficient-progress blocker. |
| `test_preflight_timeout_typed_result.py` | The turn-start preflight timeout surfaces as a typed result, not a traceback. |
| `test_prepared_compaction.py` | Opt-in prepared compaction (``compression.prepare_ahead``, agent/prepared_compaction.py). |
| `test_primary_runtime_restore.py` | Tests for per-turn primary runtime restoration and transport recovery. |
| `test_private_credential_writers.py` | Cross-writer invariant: every private-credential file is 0600 from the moment its temp file exists. |
| `test_proactive_prune_config.py` | compression.proactive_prune_* — config parse seam for the proactive prune. |
| `test_proactive_prune_loop_wiring.py` | Behavioral tests for the post-tool proactive tool-result prune wiring. |
| `test_proactive_prune_rearm_threshold.py` | Proactive-prune rearm must not lock out an over-threshold session (#101889). |
| `test_proactive_prune_restart_safety.py` | Restart-safety regressions for proactive tool-result pruning. |
| `test_proactive_tool_result_pruning.py` | Tests for proactive tool-result pruning. |
| `test_probe_cache_followups.py` | Tests for probe-cache follow-ups on the #29988/#37595/#50572 salvage. |
| `test_profile_declared_core_sets.py` | Core sets that used to name one provider now come from the registered provider profiles. |
| `test_profile_home_override_precedence.py` | Regression: multiplex gateway profile scoping + full-prompt wiring. |
| `test_project_skills.py` | Tests for project-local skill discovery (skills.trusted_project_dirs). |
| `test_prompt_builder.py` | Tests for agent/prompt_builder.py — context scanning, truncation, skills index. |
| `test_prompt_cache_boundary.py` | Builder-declared stable-prefix cache boundaries (#81867). |
| `test_prompt_cache_prefix_contract.py` | Prompt-cache prefix contract on caching routes, through a real AIAgent and a recording fake provider. |
| `test_prompt_cache_scope.py` | Tests for the rotation-stable prompt-cache scope (issue #79017). |
| `test_prompt_cache_ttl_auto.py` | ``prompt_caching.cache_ttl: auto`` picks the Anthropic cache tier by who paces the session. |
| `test_prompt_cache_ttl_propagation.py` | #84733: prompt-cache TTL/prefix propagation into MoA/aux paths + failover re-preflight. |
| `test_prompt_caching.py` | Tests for agent/prompt_caching.py — Anthropic cache control injection. |
| `test_protected_tail_pressure.py` | Algorithmic reproduction and regression for issue #61932. |
| `test_provider_attribution_headers.py` | Attribution default_headers applied per provider via base-URL detection. |
| `test_provider_client_cancel.py` | Request-owned non-HTTP transports must participate in interruption. |
| `test_provider_client_seam.py` | A provider profile can supply its own client — the registration seam. |
| `test_provider_credential_seams.py` | Generic credential seams on ``ProviderProfile``: a profile that seeds, removes and re-mints its own credentials is honoured by core with no provider name in core, and a plain profile keeps the generic path. |
| `test_provider_fallback.py` | Tests for ordered provider fallback chain (salvage of PR #1761). |
| `test_provider_history_parity.py` | Provider-native replay carriers stay private to their owning provider. |
| `test_provider_hook_policy.py` | Per-request ProviderProfile hooks on the request-build hot path: bounded calls, one failure policy. |
| `test_provider_id_mint_normalization.py` | Provider-minted parallel tool-call ids are normalized once, at mint time (#130363). |
| `test_provider_media.py` | Tests: `_save_video`, `_stub_fetch`, `test_save_url_forwards_headers_and_streams_to_cache`, `test_save_url_strict_content_type_rejects_non_video`, `test_save_url_redirect_scopes_caller_headers_to_first_hop_and_fails_clo… |
| `test_provider_parity.py` | Provider parity tests: verify that AIAgent builds correct API kwargs and handles responses properly for all supported providers. |
| `test_provider_profile_recovery_seam.py` | A pure model-provider plugin participates in error classification and the 401 refresh path through its ``ProviderProfile`` hooks — no PluginManager hook lifecycle, no core provider-name table (#116408 §4). |
| `test_provider_projection.py` | Agent-as-provider transcript projection + skill-nudge tick. |
| `test_provider_refresh_hook_failures.py` | A provider's credential-refresh hooks run inside the API-error handler: a raising hook (a plugin bug, a plugin host that disconnected or timed out) answers "not refreshed" and the original API error walks the fallback c… |
| `test_provider_reset_cooldown.py` | Provider-declared reset windows govern primary fallback cooldowns (#117484). |
| `test_provider_scope_keys.py` | Equivalent home paths address one provider slot and generation. |
| `test_provider_wire_seams.py` | Generic ProviderProfile wire seams, exercised through a fake plugin profile. |
| `test_proxy_and_url_validation.py` | Tests for malformed proxy env var and base URL validation. |
| `test_proxy_bypass_shared.py` | Invariant: the LLM transport (``agent/process_bootstrap``) and the platform adapters (``gateway/platforms/base``) answer "is this host in NO_PROXY" with the same matcher, so a corporate ``NO_PROXY=10.0.0.0/8`` bypasses… |
| `test_pydantic_dump_warning_leak.py` | Serializer-warning leak regression tests (#82xxx). |
| `test_rate_limit_reset_hint.py` | A rate-limit retry names the provider's reset window on the status line (#26889). |
| `test_rate_limit_tracker.py` | Tests for agent.rate_limit_tracker — header parsing and formatting. |
| `test_reactions.py` | Behavior tests for the token-free reaction detector. |
| `test_read_dedup_rewrite_boundaries.py` | Repeat-read dedup across transcript rewrites that are not a compaction boundary. |
| `test_reasoning_carriers.py` | Gemini text-turn signatures survive capture and reach only their route. |
| `test_reasoning_disable_recovery.py` | Main-loop recovery for a route that rejects a reasoning disable by field name (#114460). |
| `test_reasoning_echo_resolver_e2e.py` | Production-shape coverage for reasoning_echo: real resolver + real init read. |
| `test_reasoning_effort_labels.py` | #61634: ``ultra`` is Hermes-internal and every wire clamps it; the display label used by the effort pickers and ``/reasoning`` status must say what the route really sends. |
| `test_reasoning_effort_module.py` | Tests for agent.reasoning_effort — the canonical effort ladder + clamp. |
| `test_reasoning_effort_wire_translation.py` | Wire translation for Hermes' extended reasoning-effort vocabulary (#89503). |
| `test_reasoning_gate_claimed_hosts.py` | A plugin claiming a host in ``hostnames`` (catalog / aux routing) never replaces the reasoning gate core owns for that host (OpenRouter, Ollama Cloud): only hosts no core gate covers follow ``reasoning_payload``. |
| `test_reasoning_only_stop_persistence.py` | Reasoning promoted on a reasoning-only clean stop is returned, never persisted as a reply. |
| `test_reasoning_replay_routes.py` | Stored reasoning is replayed to every chat-completions route that can read it, on the carriers that route reads; strict schemas never receive a reasoning key; a route that still rejects one is learned per (provider, hos… |
| `test_reasoning_shape_boundaries.py` | Structured reasoning keeps text and answer channels intact on every chat consumer. |
| `test_reasoning_stale_timeout_floor.py` | Regression tests for the reasoning-model stale-timeout floor (issue #52217). |
| `test_reasoning_summaries.py` | Reasoning summary-part boundary repair (agent/reasoning_summaries.py). |
| `test_recovery_diagnostic_producers.py` | Real recovery producers retain work/evidence while hiding diagnostic copies. |
| `test_redact.py` | Tests for agent.redact -- secret masking in logs and output. |
| `test_redaction_registry.py` | Tests for the plugin redaction-pattern registry. |
| `test_reference_handoff_active_turn.py` | Regression coverage for #80622: a reference-only compaction handoff must never become the active user turn after a completed assistant response. |
| `test_refine_focus.py` | Tests for the /refine focus parameter on spawn_background_review_thread. |
| `test_refine_snapshot_isolation.py` | Every review path hands the fork a snapshot that cannot alias the live transcript. |
| `test_relay_atof_cwd.py` | Hermes scope cwd export through the real NeMo Relay ATOF plugin. |
| `test_relay_compaction.py` | Compaction marks land on the owning session's Relay scope stack. |
| `test_relay_compaction_atof.py` | Compaction marks through the real NeMo Relay ATOF plugin, and the freshness reset they drive. |
| `test_relay_cwd.py` | Logical working directories attached to Hermes-owned Relay scopes. |
| `test_relay_llm.py` | Tests for the core Relay-managed physical LLM attempt adapter. |
| `test_relay_nested_execution.py` | Regression tests for nested managed Relay execution (#77244). |
| `test_relay_runtime_bounded_scope_ops.py` | Bounded native scope operations in the Relay session coordinator. |
| `test_relay_runtime_plugins.py` | Tests for native NeMo Relay plugin configuration ownership. |
| `test_relay_scope_pop_metadata.py` | Regression for #78993: scope.pop metadata kwarg on older NeMo Relay. |
| `test_relay_session_segments.py` | Session-span segmentation for continuous sessions. |
| `test_relay_tools.py` | Tests for the core Relay-managed Hermes tool adapter. |
| `test_remote_fetch_ssrf_guard.py` | Every remote-party-supplied URL fetch refuses internal targets before a socket opens. |
| `test_repair_reanchors_current_turn_user_idx.py` | ``prepare_iteration`` runs the alternation repair, which merges adjacent user rows in place (after a compaction the role=user summary sits next to the protected first user message). The index recorded at turn start then… |
| `test_repair_tool_call_arguments.py` | Tests for _repair_tool_call_arguments — malformed JSON repair pipeline. |
| `test_repair_tool_call_name.py` | Tests for AIAgent._repair_tool_call — tool-name normalization. |
| `test_repeated_dropped_tool_args.py` | Dropped streams must not dispatch repetition-dominated tool arguments. |
| `test_repetition_guard.py` | Unit tests for repetition-dominated model output detection. |
| `test_replay_budget_accounting.py` | Tests for provider-aware replay-field accounting in tail-budget walks (#73624). |
| `test_replay_cleanup.py` | Tests for agent.replay_cleanup — shared replay-tail sanitizers. |
| `test_replay_echo_retirement.py` | Replay-echo retirement for interrupt placeholders (#132949, alongside #81841). |
| `test_reply_line_before_silence.py` | A bare silence marker after the model already wrote its reply ends the turn on that reply. |
| `test_request_client_reuse.py` | Per-request OpenAI wire client reuse across sequential LLM calls. |
| `test_request_client_reuse_abort_races.py` | Races between the request-client reuse cache and the abort machinery. |
| `test_reset_aware_primary_restore.py` | Reset-aware primary restore — stay on fallback until the primary's rate-limit window actually resets. |
| `test_responses_empty_tool_replay.py` | Responses replay must not invent a blank assistant turn before a tool call. |
| `test_responses_watchdog_accommodations.py` | Regression tests for #86444 - large-context watchdog accommodations for codex_responses transports. |
| `test_restore_primary_pool_reselect.py` | Test that _restore_primary_runtime re-selects from the credential pool instead of using a stale snapshot key. |
| `test_resume_stale_active_task.py` | Regression coverage for #35344: a resumed session must not let a stale historical task snapshot from an inherited compaction handoff hijack the reply to a new, unrelated user message. |
| `test_retry_delay_parsers_shared.py` | Invariants for the shared retry-delay parsers in ``agent/retry_utils.py``. |
| `test_retry_exhaustion_partial_retention.py` | #119001: an API error that ends the turn AFTER partial output was delivered must retain that output instead of ending the turn error-only, and must not persist the dangling continuation trail. |
| `test_retry_status_buffer.py` | Tests for the retry/fallback status buffer helpers on AIAgent. |
| `test_retry_utils.py` | Tests for agent.retry_utils jittered backoff. |
| `test_review_engine.py` | Tests for the /review command engine — agent/review_engine.py. |
| `test_review_fork_cache_scope.py` | A background-review fork gets its OWN cache scope on xAI once it has compacted. |
| `test_review_idle_queue.py` | Deferred background review on the managed local runtime. |
| `test_rotation_flush_persisted_boundary.py` | Regression (#68196): rotating preflight compression must not re-append the already-persisted transcript to the parent session on cold resume. |
| `test_router_timeout_shim.py` | HTTP-200 router timeout shim (#68396) in the OpenAI-compatible consumers that bypass ``validate_response``: the stream assembler and the auxiliary ``_validate_llm_response``. |
| `test_run_agent.py` | Unit tests for run_agent.py (AIAgent). |
| `test_run_agent_codex_responses.py` | Tests: `_no_codex_backoff`, `_patch_agent_bootstrap`, `_build_agent`, `_build_relay_agent`, `_build_azure_foundry_agent`, `_codex_message_response` … |
| `test_run_agent_interrupt_hook.py` | Sequential and concurrent tool execution: Ctrl-C emits a cancelled ``post_tool_call`` hook. |
| `test_run_agent_multimodal_prologue.py` | Regression tests for run_conversation's prologue handling of multimodal content. |
| `test_run_budget.py` | Tests for the optional wall-clock run budget (agent.run_budget_seconds / --run-budget). |
| `test_runtime_cwd.py` | Tests for agent/runtime_cwd.py — the single source of truth for the agent working directory. |
| `test_runtime_self_protection.py` | The runtime's own interpreter/venv is not agent-deletable (#58748). |
| `test_runtime_session_store.py` | Tests: `test_outbox_freezes_failed_payload_and_reopens_exclusively`, `test_outbox_has_private_posix_mode`, `test_outbox_capacity_failure_does_not_advance_or_discard`, `test_worker_turn_wait_callbacks_remain_local`, `tes… |
| `test_runtime_session_store_lease_refresh.py` | A managed worker's turn lease survives its periodic refresh (the store is the agent's session_db). |
| `test_runtime_session_store_proxy.py` | A managed worker's owner RPC is a loopback dial: a user's HTTPS_PROXY must never carry it. |
| `test_runtime_session_store_surface_parity.py` | A managed worker's agent gets a RuntimeSessionStore as its session_db. Every SessionDB method the agent core calls must exist on the store, accept the same keywords, and answer like the owner's SessionDB (Adolanium reg-… |
| `test_safe_worker_policy.py` | Fresh exec probes for the private managed safe-worker bootstrap contract. |
| `test_salvage_grown_transcript.py` | Mechanical salvage for compression candidates that would grow. |
| `test_sanitiser_escalation.py` | Empty-transcript sanitizer: stop the per-send heal/WARNING loop (#96870). |
| `test_save_url_image.py` | Direct tests for ``agent.image_gen_provider.save_url_image`` (#26942). |
| `test_secret_scope.py` | Tests for the profile-scoped credential primitive (Workstream A / Phase 2). |
| `test_secret_scope_env_cache.py` | The per-path ``load_env_file()`` memo in ``agent.secret_scope``. |
| `test_secret_scope_pinned_launch_home.py` | The launch home is pinned once the process serves several profiles (#119242). |
| `test_secret_scope_tier1_migration.py` | Regression tests for the Tier-1 core-gateway secret-scope migration. |
| `test_secret_scope_user_message.py` | UnscopedSecretError reaches end users verbatim (compression-aborted replies, cron notices), so `str(exc)` must be the one actionable sentence; the developer diagnosis stays in `__notes__`/logs. |
| `test_send_path_history_isolation.py` | Send-path transforms must never write through into persisted history. |
| `test_sequential_deadline_delegate_exempt.py` | ``delegate_task`` runs a nested orchestrator's whole batch inside one tool call by design, so it must not sit under the generic sequential-call deadline: with it, every batch longer than the deadline "timed out" while i… |
| `test_sequential_tool_interrupt.py` | Sequential tool execution must abandon the wait when the user interrupts. |
| `test_sequential_tool_timeout.py` | Sequential tool calls recover when one dispatch never returns. |
| `test_served_model.py` | agent.served_model — per-response served-model capture behind routing proxies (#54864). |
| `test_serves_routed_profile_pin.py` | A host that mirrors the served profile into HERMES_HOME must not flip launch-home identity. |
| `test_session_activity.py` | Unit tests for the shared session activity observation contract. |
| `test_session_activity_persist.py` | Durable session activity projection from AIAgent._touch_activity (#72016). |
| `test_session_affinity_header.py` | Per-provider ``session_affinity_header`` (#86241, #104449). |
| `test_session_id_env.py` | Test that HERMES_SESSION_ID is exposed as an env var and ContextVar. |
| `test_session_meta_filtering.py` | Tests for session_meta filtering — issue #4715. |
| `test_session_prompt_refresh.py` | ``hermes sessions refresh-prompts``: a continuing session adopts updated prompt sources once. |
| `test_session_reset_fix.py` | Tests for session reset completeness (fixes #2635). |
| `test_session_rotation_flush_cold_resume.py` | Regression (#68454): /new, /resume, /branch must not re-append cold-resumed transcript rows when flushing before session rotation. |
| `test_session_row_under_live_agent_persist.py` | A session row deleted under a live agent must heal on the next flush (#123583). |
| `test_session_snapshot_removal.py` | Automatic persistence stays in SQLite; explicit exports remain available. |
| `test_session_source.py` | Tests: `_reset_contextvars`, `test_session_source_context_overrides_platform`, `test_session_source_falls_back_to_platform`, `test_oneshot_run_gets_distinct_source`, `test_oneshot_marker_does_not_relabel_subagents`, `te… |
| `test_set_runtime_main_custom_provider.py` | Regression test: set_runtime_main() must pass base_url/api_key/api_mode so that _resolve_auto_route() can route custom: providers in Step 1. |
| `test_setup_beat_card_round.py` | A setup_beat round in the turn loop. It never ends in the empty-response nudge: the line written with the card is the turn's reply when the follow-up comes back empty (agent/turn_tool_round.py ``_LINE_IS_REPLY_TOOLS``).… |
| `test_setup_logging_profile_scope.py` | #125974 — ``agent.agent_init._setup_logging`` must honor the active profile scope. |
| `test_shared_client_fd_corruption.py` | #70773: the shared OpenAI-wire client must never be pool-closed from a non-owner thread. |
| `test_shared_http_transport.py` | Keepalive httpx clients share one HTTPTransport per (verify, proxy) identity. |
| `test_shell_hooks.py` | Tests for the shell-hooks subprocess bridge (agent.shell_hooks). |
| `test_shell_hooks_consent.py` | Consent-flow tests for the shell-hook allowlist. |
| `test_shell_hooks_tree_kill.py` | Process-tree cleanup for timed-out shell hooks (port of openai/codex#37527). |
| `test_short_housekeeping_reply.py` | Recovered housekeeping replies remain successful even when short or transformed. |
| `test_side_question.py` | Tests for agent/side_question.py — the /btw context-aware side question engine. |
| `test_side_question_lease.py` | Turn leases for plugin side questions (``agent/side_question_lease.py``, ``ctx.side_question``). |
| `test_side_question_request.py` | Plugin side questions on the live session agent (``agent/side_question_request.py``). |
| `test_skill_app_snapshot.py` | Application requirements survive disk and in-process skill-index reuse. |
| `test_skill_applied_notifications.py` | Tests: `_messages`, `test_applied_skill_operations_notify_with_names`, `test_unapplied_skill_operations_never_notify` |
| `test_skill_bundles.py` | Tests for agent/skill_bundles.py — YAML-defined skill bundles. |
| `test_skill_cache_thrash.py` | Regression test for #104849: skill command cache thrash from platform/home flapping. |
| `test_skill_commands.py` | Tests for agent/skill_commands.py — skill slash command scanning and platform filtering. |
| `test_skill_commands_freshness.py` | CFG-8: a skill installed from another terminal reaches the long-lived gateway's slash map. |
| `test_skill_commands_reload.py` | Tests for ``agent.skill_commands.reload_skills``. |
| `test_skill_inline_bash_windows.py` | Native Windows execution contract for opt-in skill snippets. |
| `test_skill_inline_shell_output.py` | Inline-shell snippets never turn a silent failure into an empty (looks-fine) result. |
| `test_skill_inline_shell_trust.py` | Inline-shell expansion is trust-scoped (#63307): community hub installs never auto-execute `` !`cmd` `` snippets, mirroring the hub scan's INSTALL_POLICY trust gate — a ``--force`` or pre-scanner community install must… |
| `test_skill_invocation_description.py` | describe_skill_invocation() — recovering what the user typed from a /skill turn. |
| `test_skill_session_platform_gate.py` | The session_platforms frontmatter gate (skills-index slim PR). |
| `test_skill_todo_retention_parity.py` | Retention parity at the compaction boundary (#84718). |
| `test_skill_utils.py` | Tests for agent/skill_utils.py. |
| `test_skills_auto_load.py` | skills.auto_load: pinned skills land in every new session's prompt, resolved once per agent. |
| `test_skills_guidance_content_filter.py` | SKILLS_GUIDANCE must not carry the phrasing Anthropic's content filter rejects. |
| `test_skills_index_delta.py` | Skills that change mid-conversation reach the model, behind the cached system prompt. |
| `test_skills_index_format.py` | Shape of the <available_skills> index rows (single-skill categories, headers, clipped descriptions). |
| `test_skip_background_review.py` | Tests for the skip_background_review constructor flag. |
| `test_skip_memory_store.py` | Regression test for issue #65429. |
| `test_soul_legacy_bot_protocol.py` | The plugin-era "## Messaging other agents" SOUL append is dead weight: the server injects the live section in Bot Chat only, so every copy in SOUL.md must vanish — at load time for sessions that start before the migrati… |
| `test_soul_md_profile_isolation.py` | Regression (#50233, SOUL.md half): a profile agent's SOUL.md must load from ITS OWN home, never the ambient/launch home — even on a thread that did not bind the HERMES_HOME ContextVar. Same bug class as the skills-index… |
| `test_split_turn_compaction.py` | Regression for #80449 — an oversized in-progress turn must stay compressible. |
| `test_ssl_transport_contracts.py` | TLS assertions reach real client transports, never the host certificate store. |
| `test_ssl_verify.py` | TLS trust contract: the OS certificate store, with explicit config on top. |
| `test_stale_replay_prune.py` | Tests for compaction's codex_reasoning_items handling (#71058, #71077 by @webtecnica). |
| `test_stall_guards.py` | Runtime anti-stall guards (agent.stall_guards). |
| `test_start_order_gate.py` | Tests for the concurrent start-order gate (PR #79571 / issue #79569). |
| `test_steer.py` | Tests for AIAgent.steer() — mid-run user message injection. |
| `test_steer_compaction_persistence.py` | Regression coverage for steer display identity across compactions (#117137). |
| `test_stream_chunk_byte_estimate.py` | Tests for _estimate_chunk_bytes — the cheap per-chunk stream size proxy. |
| `test_stream_drop_logging.py` | Tests for richer stream-drop diagnostics in agent.log. |
| `test_stream_interrupt_abort_socket.py` | An interrupt abort must reach the in-flight stream's socket (#98974). |
| `test_stream_interrupt_retry.py` | Tests that /stop interrupts streaming retry loops immediately. |
| `test_stream_reasoning_details.py` | Opaque reasoning records survive both collectors and durable replay. |
| `test_stream_retry_backoff.py` | Stream-level reconnects back off exponentially and stay interruptible (#60029). |
| `test_stream_retry_route_switch.py` | A stream retry never replays a request built for a route the agent has since left. |
| `test_stream_runaway_repetition.py` | A stream stuck in a repetition loop must not keep the turn alive for as long as it streams. |
| `test_stream_serving_provider.py` | Regression tests for the serving-provider field in stream diagnostics (#90216). |
| `test_stream_single_writer.py` | Regression tests for the streaming single-writer invariant (#65991). |
| `test_stream_single_writer_guard.py` | Regression tests for the best-effort single-writer fence accessors. |
| `test_stream_stale_abandon.py` | A streaming worker that stale kills cannot unwind must not stall the turn forever. |
| `test_stream_stale_breaker_reset.py` | Follow-up for the cross-turn stream-stale circuit breaker (#58962). |
| `test_stream_stale_circuit_breaker.py` | Cross-turn stream-stale circuit breaker (issue #58962). |
| `test_stream_stale_kill_unwedge.py` | A stale-killed provider stream must actually unwedge its reader. |
| `test_stream_unmask_5xx.py` | Streaming 5xx unmasking: the non-streaming probe surfaces the provider's real error. |
| `test_stream_wait_notice.py` | Resumed chunks clear only the stream monitor's own silence notice. |
| `test_streamed_reasoning_details.py` | Streamed ``reasoning_details`` survive to the assembled response (replay continuity). |
| `test_streamed_text_accumulation.py` | Tests for how a turn's streamed assistant text is built up. |
| `test_streaming.py` | Tests for streaming token delivery infrastructure. |
| `test_streaming_context_scrubber.py` | Unit tests for StreamingContextScrubber (agent/memory_context.py). |
| `test_streaming_tool_call_repair.py` | Tests for tool call argument repair in the streaming assembly path. |
| `test_strict_api_validation.py` | Test validation error prevention for strict APIs (Fireworks, etc.) |
| `test_strip_reasoning_tags_cli.py` | Tests for cli.py::_strip_reasoning_tags — specifically the tool-call XML stripping added in openclaw/openclaw#67318 port. |
| `test_structured_output_rejection_retry.py` | Regression tests for the structured-output rejection retry in ``agent.auxiliary_client``. |
| `test_studio_bridge_affinity.py` | Affinity contract on Hermes Studio's group-chat bridge shape (#96811). |
| `test_subagent_lifecycle.py` | Contract tests for the public plugin subagent lifecycle API. |
| `test_subagent_progress.py` | Tests for subagent progress relay (issue #169). |
| `test_subagent_stop_hook.py` | Tests for the subagent_stop hook event. |
| `test_subdirectory_hints.py` | Tests for progressive subdirectory hint discovery. |
| `test_subdirectory_hints_tilde.py` | Regression tests for the home-directory RuntimeError bug. |
| `test_subprocess_env_guard.py` | Lint guard: no new raw ``os.environ.copy()`` / ``**os.environ`` spawn-env sites. |
| `test_subscription_view.py` | Tests for agent.subscription_view — the surface-agnostic /subscription core. |
| `test_summarize_api_error.py` | Regression: empty-body HTTP 4xx errors must still surface a real provider message. |
| `test_summarize_tool_result_type_safety.py` | Type safety tests for _summarize_tool_result. |
| `test_summary_prefix_semantics.py` | Pin the semantics of SUMMARY_PREFIX so the compaction handoff doesn't re-introduce conflicting instructions. |
| `test_summary_prefix_tool_use.py` | Regression tests for the SUMMARY_PREFIX tool-use clause (#65848 class). |
| `test_summary_role_template_alternation.py` | Regression coverage: the compaction summary role must alternate against TEMPLATE-VISIBLE neighbours, not literal list neighbours. |
| `test_surrogate_chokepoints.py` | Lone-surrogate chokepoint regression tests. |
| `test_switch_model_bedrock_sigv4.py` | Every non-startup Bedrock client rebuild (/model switch, fallback-to-Bedrock, fallback restore) must land on the same wire startup uses: AnthropicBedrock SDK for Claude, boto3-direct for Converse, with region and guardr… |
| `test_switch_model_context.py` | Tests that switch_model does not inherit stale context_length overrides. |
| `test_switch_model_fallback_prune.py` | Regression test for TUI v2 blitz bug: explicit /model --provider switch silently fell back to the old primary provider on the next turn because the fallback chain — seeded from config at agent __init__ — kept entries fo… |
| `test_switch_model_pool_reload.py` | Regression tests for #52727: switch_model() must reload the credential pool when the provider changes. |
| `test_switch_model_reapplies_config_context_pin.py` | A live model/provider switch must re-derive the durable ``model.context_length`` pin. |
| `test_switch_model_reapplies_headers.py` | Regression tests for #61099: switch_model must reapply provider-specific default headers when it rebuilds _client_kwargs from scratch. |
| `test_switch_model_reasoning_override.py` | Tests for per-model reasoning_effort override during /model switch. |
| `test_switch_model_request_overrides.py` | Regression tests for the in-place /model switch (CLI/TUI) carrying a custom provider's request_overrides (extra_body) — _apply_switched_provider_request_overrides. |
| `test_switch_model_rollback.py` | Regression test for #33175: switch_model() must roll back to the pre-swap state if the client rebuild raises. |
| `test_switch_model_stale_base_url.py` | Regression tests for #47828: switch_model must not pair a new provider label with the previous provider's base_url when the resolver returns no new base_url for a genuine provider change. |
| `test_synthetic_turn_display_kind.py` | A synthesized turn's row is typed when it is WRITTEN, not when it ends. |
| `test_system_prompt.py` | Tests for agent/system_prompt.py — context-file cwd wiring. |
| `test_system_prompt_restore.py` | Tests for ``agent.conversation_loop._restore_or_build_system_prompt``. |
| `test_system_prompt_switch_invalidation.py` | A /model (or route) commit must not null a continuing session's stored system prompt. |
| `test_terminal_approval_batch.py` | Desktop batches publish consent together, never shell effects together. |
| `test_terminal_env_registry.py` | Tests for the terminal environment provider registry + ABC. |
| `test_text_turn_incremental_persistence.py` | Behavior contract: a completed pure-text assistant turn is durable before the conversation loop yields control (#81641). |
| `test_think_scrubber.py` | Tests for StreamingThinkScrubber. |
| `test_thinking_only_sanitizer.py` | Tests for the thinking-only assistant message sanitizer. |
| `test_thinking_prefill_trailing_turn.py` | Regression test for the thinking-only prefill reaching the wire. |
| `test_thinking_timeout_guidance.py` | Tests for the reasoning-model thinking-timeout detection + guidance. |
| `test_thread_scoped_output.py` | Tests for agent.thread_scoped_output.thread_scoped_silence. |
| `test_title_generator.py` | Tests for agent.title_generator — auto-generated session titles. |
| `test_title_input.py` | Title-only input must not change history, eligibility, or fallback behavior. |
| `test_tls_fd_recycle_corruption.py` | Regressions for issue #29507 — cross-thread close of the per-request OpenAI client could release a TLS socket FD whose integer was still cached in the owning httpx worker's SSL BIO. The kernel then recycled the FD into… |
| `test_token_estimator_shared.py` | Invariant: every rough token estimate in the tree derives from ``estimate_tokens_rough`` / ``CHARS_PER_TOKEN`` in ``agent/model_metadata.py``, so the ``/context`` breakdown's static categories, the conversation slice an… |
| `test_token_guard_session_source.py` | The token-accounting guard never mints an anonymous session row (#111999). |
| `test_token_memo_release_on_close.py` | A closed agent's message bodies leave the token-estimate memo. |
| `test_token_persistence_non_cli.py` | Tests: `_mock_response`, `_make_agent`, `test_run_conversation_persists_tokens_for_telegram_sessions`, `test_session_search_lazily_opens_db_when_entrypoint_did_not_pass_one` |
| `test_token_read_barrier_on_loop.py` | A session read on an event-loop thread never waits on the token writer (#141966). |
| `test_tool_activity_heartbeat.py` | Tests for the in-flight tool activity heartbeat (#84491). |
| `test_tool_arg_coercion.py` | Tests for tool argument type coercion. |
| `test_tool_batch_segmentation.py` | Segment-aware mixed tool-batch dispatch. |
| `test_tool_call_arg_no_redaction.py` | Regression test for #43083. |
| `test_tool_call_args_sanitizer.py` | Tests for AIAgent._sanitize_tool_call_arguments. |
| `test_tool_call_guardrail_runtime.py` | Runtime tests for tool-call loop guardrails. |
| `test_tool_call_incremental_persistence.py` | Behavior contracts for incremental tool-call persistence (#49045). |
| `test_tool_dispatch_helpers.py` | Tests for the tool-result message builder — focuses on the untrusted-content delimiter wrapping that hardens against indirect prompt injection (#496). |
| `test_tool_executor_checkpoint_paths.py` | Behavioral coverage for checkpoint path resolution across terminal backends. |
| `test_tool_guardrails.py` | Pure tool-call guardrail primitive tests. |
| `test_tool_name_db_persistence.py` | Test that tool_name is correctly persisted to the session DB for tool-result messages. |
| `test_tool_result_classification.py` | Tests for shared tool result classification helpers. |
| `test_tool_result_memory_trim.py` | A >=1 MB tool result hands allocator pages back via ``trim_memory`` — after the batch (#70684). |
| `test_trace_upload.py` | Tests for agent.trace_upload — Hugging Face session-trace upload. |
| `test_trajectory_file_locking.py` | ``save_trajectory()`` appends must be serialized across processes (#12684). |
| `test_transcript_decoration_idempotence.py` | Idempotence law for transcript decoration passes: f(f(x)) == f(x). |
| `test_transcription_registry.py` | Tests for agent/transcription_registry.py and agent/transcription_provider.py. |
| `test_transform_llm_output_persistence.py` | #44239: what ``transform_llm_output`` shows the user is what the session stores and replays. |
| `test_treekill_consolidation.py` | #85125 Phase 4d — site-local tree-kills delegate to agent.deadline. |
| `test_truncated_tool_call_boost.py` | Truncation retries must send a larger output budget than the failed request (#72770), without exceeding the model's known output limit (#79715). |
| `test_tts_registry.py` | Tests for agent/tts_registry.py and agent/tts_provider.py. |
| `test_turn_api_call_interrupt.py` | Tests for ``agent/turn_api_call.py::handle_api_interrupt`` — the plain (non-redirect) interrupt that lands mid provider call and records the streamed partial as the interrupted assistant row. |
| `test_turn_api_error_stream_parse.py` | jiter SSE parse ValueErrors are transient provider failures, not local bugs (#65147). |
| `test_turn_author.py` | Tests for agent.turn_author: the per-turn author carried from a dispatcher to memory hooks. |
| `test_turn_base_display_anchor.py` | Turn-base display anchor: the context meter shows durable-transcript cost. |
| `test_turn_budget_durable_rows.py` | A tool result the per-turn budget spills must replay as the stub it was sent as. |
| `test_turn_completion_explainer.py` | Tests for the end-of-turn completion explainer (#34452). |
| `test_turn_context.py` | Unit tests for the extracted turn prologue (``agent/turn_context.py``). |
| `test_turn_context_compaction.py` | Unit tests for ``agent.turn_context_compaction`` (turn-start compaction extracted from ``build_turn_context``). |
| `test_turn_context_overflow_warning.py` | Tests for the silent-context-overflow warning (the fix for the bug where a session crosses the compression threshold but compression is blocked — by the summary-LLM cooldown (#11529) or anti-thrashing (#40803) — and the… |
| `test_turn_end_stall_diagnostics.py` | Regression coverage for #131740: the turn-end activity stamp and the watchdog stall stack dump. |
| `test_turn_facade_lease.py` | Unit tests for agent.turn_facade_lease (admission + lease bracket). |
| `test_turn_finalizer_cleanup_guard.py` | Regression test for #8049. |
| `test_turn_finalizer_final_response_persistence.py` | Tests: `FakeAgent`, `test_final_response_closes_tool_tail_before_persistence`, `test_fallback_timestamp_survives_delayed_sqlite_persistence`, `test_final_response_fills_pure_tool_call_tail`, `test_final_response_fill_in… |
| `test_turn_finalizer_interrupt_alternation.py` | Regression test for #48879. |
| `test_turn_finalizer_iteration_limit_exit.py` | Regression tests for iteration-limit exit normalization (#61631). |
| `test_turn_iteration_prep.py` | ``apply_retry_restarts`` bounds the refunding restarts (#106108). |
| `test_turn_liveness.py` | Unit coverage for agent/turn_liveness.py config resolution (#95548/#95663). |
| `test_turn_liveness_watchdog.py` | Turn liveness watchdog (#95548): force-abort turns that stall silently. |
| `test_turn_overlap_tripwire.py` | note_turn_start / note_turn_persisted — the concurrent-turn tripwire. |
| `test_turn_recovery_autorecover.py` | Bounded post-exhaustion auto-recovery ladder (#85426, #107307): fallback first, transient outages only, visible on every surface, interrupt cancels. |
| `test_turn_response_intake_relay.py` | ``reasoning.available`` carries extracted reasoning, never the reply text (#132477). |
| `test_turn_retry_state.py` | Provider detection used by the turn-retry credential-refresh gates. |
| `test_turn_scripted_prelude.py` | A scripted prelude's tool call id is unique per chat: a rerun of onboarding plays the same name card at the same place in a new chat, and the desktop keys tool rows by that id. |
| `test_turn_summary.py` | Tests for per-turn accounting: summary formatter, collector, spinner flow, gating. |
| `test_turn_usage_log_line.py` | The per-call log line carries what a cost or cache investigation needs: the cache write count, the provider's response id, and the serving upstream when the route reports one. Existing parsers read a prefix of the line,… |
| `test_turn_user_intervened.py` | A turn reports ``user_intervened`` when the user steered, redirected or interrupted it, even when the correction was fully absorbed and the turn still ``completed`` (first-task-done detection). |
| `test_uncompressed_context_guardrail.py` | Uncompressed context overflow guardrail (#89297). |
| `test_unicode_ascii_codec.py` | Tests for UnicodeEncodeError recovery with ASCII codec. |
| `test_unset_reasoning_effort_default.py` | An unset ``agent.reasoning_effort`` resolves to ``medium`` on custom / OpenAI-compatible routes. |
| `test_unsupported_parameter_retry.py` | Regression tests for the generic unsupported-parameter detector in ``agent.auxiliary_client``. |
| `test_unsupported_temperature_retry.py` | Regression tests for the universal "unsupported temperature" retry in ``agent.auxiliary_client``. |
| `test_usage_anchor.py` | Usage-anchored context accounting (agent/usage_anchor.py). |
| `test_usage_pricing.py` | Tests: `test_astra_whole_request_price_tier_includes_cache_writes`, `models_dev_registry`, `test_direct_first_party_route_prices_models_missing_from_snapshot`, `test_normalize_usage_reads_deepseek_native_cache_hit_token… |
| `test_vault_backend_registry.py` | Plugin vault registration uses existing scoped leases; no browser/secrets. |
| `test_vault_backends.py` | Invariants for external password-manager vault backends (1Password / Bitwarden). |
| `test_vault_key_storage.py` | Where the local vault key lives: the 0600 ``vault.key`` file (default) or the OS keychain. |
| `test_vault_keychain_native.py` | The vault key against the host's REAL OS keychain (macOS Keychain, Windows Credential Manager). |
| `test_vault_store.py` | ``VaultStore._read_all`` must surface every decryptable-but-malformed vault file as ``VaultError`` so callers that catch ``VaultError`` (the ``hermes vault`` commands, ``vault.*`` RPC handlers) get the designed error pa… |
| `test_vault_unlock_tokens.py` | Password-manager session tokens: in memory, out of reach of a plain import, gone at the idle TTL, and handed to exactly the manager invocation that needs them. |
| `test_verification_continuation_budget.py` | End-to-end regression coverage for verification budget exhaustion (#61631, #65919 §7). |
| `test_verification_evidence.py` | Tests: `_ledger_on`, `_node_project`, `_python_project`, `test_lint_and_typecheck_are_not_reported_as_full_tests`, `test_shell_wrappers_match_but_echo_does_not`, `test_piped_verifier_uses_its_own_pipeline_status` … |
| `test_verification_evidence_disabled.py` | With verify-on-stop off (the default) the evidence ledger must be fully inert: no recording, no staleness tracking, and no ``verification_evidence.db`` ever created. The ledger's only consumer is the stop guard; an unco… |
| `test_verification_evidence_fd_leak.py` | Regression: the verification-evidence ledger must close every connection. |
| `test_verification_stop.py` | Tests: `_node_project`, `_make_project`, `_ledger_on`, `clear_verify_env`, `test_verify_on_stop_env_can_enable`, `test_verify_on_stop_auto_on_for_interactive_surfaces` … |
| `test_verification_stop_caching.py` | Verification-loop synthetic scaffolding must never reach durable session state. |
| `test_verify_hooks.py` | Unit tests for the verification-loop policy (agent/verify_hooks.py). |
| `test_vertex_adapter.py` | Tests for the Vertex AI adapter (agent/vertex_adapter.py). |
| `test_video_gen_registry.py` | Tests for agent/video_gen_registry.py — provider registration & active lookup. |
| `test_vision_aware_preprocessing.py` | Tests for the vision-aware image preprocessing in run_agent.py. |
| `test_vision_resolved_args.py` | Test that call_llm vision path passes resolved provider args, not raw ones. |
| `test_vision_routing.py` | Regression tests for issue #31179. |
| `test_vision_tool_messages.py` | Tests for proactive vision-tool-message downgrade (issue #41072). |
| `test_voice_turn_route.py` | ``auxiliary.voice_chat``: a voice turn runs on the voice model, the next turn on the main one. |
| `test_wait_notice_cadence.py` | The long-wait status line is one neutral notice per silence, not a 30s warning drumbeat (#92550). |
| `test_wait_state_visibility.py` | Tests for wait-state visibility — the live "what are we waiting on" notices. |
| `test_warning_presentation.py` | Notification policy changes presentation, not diagnostic state or task content. |
| `test_welcome_error_identity.py` | The anonymous UI is a property of the request credential, not a free model or host (#111970). |
| `test_welcome_tier_recovery.py` | Nous free tier, inference side: the dark-tier 403 keyed on the route, the one-shot model move after ``model_not_free``, the wrong-host heal, the long-wait rule for structured ``rate_limited`` refusals, and the plain out… |
| `test_worker_outbox_adoption.py` | A retained worker outbox follows verified owner adoption (epoch replacement, physical-target rotation) without a second receipt, and is still refused for anything but the verified successor. |
| `test_worker_outbox_reopen.py` | A worker reopening an acknowledged-but-unjournaled write reconciles before its next write. |
| `test_worker_rpc_connection_reuse.py` | A managed worker keeps one authenticated owner connection instead of dialing per persistence call. |
| `test_worker_rpc_loop_diagnostic.py` | The on-loop guard names its caller at WARNING (#139029): a best-effort write swallows the raise at debug, and only the sticky follow-up failures reached the logs. |
| `test_worker_rpc_proxy.py` | Private loopback worker persistence does not use ambient HTTP proxies. |
| `test_would_grow_refusal_runway.py` | Regression: a would-grow refusal must not disarm the proactive-prune runway. |
| `transports/__init__.py` | Package marker / package-level exports |
| `transports/test_bedrock_transport.py` | Tests for the BedrockTransport. |
| `transports/test_chat_completions.py` | Tests for the ChatCompletionsTransport. |
| `transports/test_chat_completions_empty_tool_calls.py` | Tests for empty / null ``tool_calls`` stripping in ChatCompletionsTransport. |
| `transports/test_chat_completions_reasoning_details_replay.py` | ``reasoning_details`` replay is route-scoped: OpenRouter-format gateways (OpenRouter, Kilo, Vercel AI Gateway, Nous Portal) and vendors documenting it read it; strict schemas (Groq, Mistral, Cerebras, Fireworks direct)… |
| `transports/test_chat_completions_xai_tool_search_alias.py` | Tests for the xAI ``tool_search`` reserved-name alias (#95003). |
| `transports/test_codex_app_server.py` | Invariants for CodexAppServerClient's transport-loss contract (#87433, #83127). |
| `transports/test_codex_app_server_runtime.py` | Tests for the optional codex app-server runtime gate. |
| `transports/test_codex_app_server_session.py` | Tests for CodexAppServerSession — drive turns through a mock client. |
| `transports/test_codex_event_projector.py` | Tests for CodexEventProjector — codex item/* events → Hermes messages list. |
| `transports/test_codex_transport.py` | Tests for the ResponsesApiTransport (Codex). |
| `transports/test_codex_transport_cron_scope.py` | Unified-runtime cron fires share one Codex prompt-cache scope per job (#139434). |
| `transports/test_codex_transport_github_reasoning.py` | GitHub/Copilot Responses reasoning fields on the Codex transport. |
| `transports/test_codex_worker_mcp_overrides.py` | Kanban worker MCP overrides must target the server entry the runtime migration registers. |
| `transports/test_finish_reason_normalization.py` | Uppercase wire finish reasons (STOP / MAX_TOKENS from Gemini-fronting OpenAI-compatible gateways) must fold to the lowercase OpenAI contract at both wire-intake choke points — the chat_completions transport and the stre… |
| `transports/test_hermes_tools_mcp_server.py` | Tests for the hermes-tools-as-MCP server module surface. |
| `transports/test_meta_codex_cache.py` | Tests for Meta api.meta.ai prompt_cache_retention and transport plumbing. |
| `transports/test_plugin_transport_api_mode.py` | A provider plugin's own ``api_mode`` reaches the runtime transport (#53054). |
| `transports/test_profile_hook_keyword_compat.py` | A plugin profile's ``build_api_kwargs_extras`` written against the older keyword set keeps working. |
| `transports/test_provider_wire_snapshot.py` | Golden wire snapshot: the exact request every registered provider is sent. |
| `transports/test_reasoning_effort_sibling_sites.py` | Sibling-site coverage for the reasoning-effort wire-vocabulary class (#89503). |
| `transports/test_router_codex_efforts.py` | Router catalog-declared reasoning-effort clamping on the codex transport. |
| `transports/test_transport.py` | Tests for the transport ABC, registry, and AnthropicTransport. |
| `transports/test_types.py` | Tests for agent/transports/types.py — dataclass construction + helpers. |

## `tests/ci/`

| File | What it does |
|---|---|
| `_gha_expr.py` | A small evaluator for the GitHub Actions expression subset our workflows gate on. |
| `desktop_release_roles.py` | Find desktop release workflow jobs by what they do, not by their ids. |
| `test_assemble_review_comment.py` | Tests for scripts/ci/assemble_review_comment.py. |
| `test_cache_report.py` | Protect archive accounting, not report wording or markup. |
| `test_cache_report_collection.py` | The API token must not reach a redirected log download. |
| `test_channel_build_publication.py` | Execute channel workflow seams and receipt transport; fixture bytes are not native qualification. |
| `test_check_blob_size.py` | scripts/ci/check_blob_size.py on real temp git repos: what a PR may add, and what it may not. |
| `test_check_catalog_cors.py` | scripts/ci/check_catalog_cors.py against a loopback docs host that redirects like the real one. |
| `test_check_os_marker_fakes.py` | The unmarked-macOS-fake guard (#111866): flags fakes, ignores honest reads and marked files. |
| `test_classify_changes.py` | Tests for scripts/ci/classify_changes.py. |
| `test_clean_worktree_check.py` | Every job of the main CI lanes ends by checking that it left the checkout clean. |
| `test_commit_build_staging.py` | Execute commit staging and summary steps against a disposable object store. |
| `test_desktop_bundle_smoke.py` | Replay artifact handoffs and publication against a fake R2. |
| `test_desktop_release_commit_admission.py` | Commit-build admission rejects mixed inputs before repository code runs. |
| `test_desktop_release_tag_admission.py` | Tag admission for .github/workflows/desktop-bundled-release.yml (plan item 7). |
| `test_desktop_store_eligibility.py` | Execute the packaging workflow branches; nonstable never builds Store identities. |
| `test_docs_drift.py` | Docs drift ratchet: every DEFAULT_CONFIG key and slash command is documented, or baselined. |
| `test_e2e_screenshot_status.py` | Tests for scripts/ci/e2e_screenshot_status.py. |
| `test_e2e_strict_acceptance.py` | Delivery gap guards must not excuse failures owned by a strict acceptance run. |
| `test_e2e_tmux_required.py` | The release/dispatch E2E lane fails, not skips, when the classic-CLI tmux suites lose tmux. |
| `test_list_os_marked_tests.py` | Tests for scripts/ci/list_os_marked_tests.py. |
| `test_live_comment.py` | Tests for scripts/ci/live_comment.py run selection. |
| `test_lockfile_diff.py` | Tests for scripts/ci/lockfile_diff.py. |
| `test_messaging_gated_selection.py` | Dependency-gated gateway cases run in a job that has their dependency. |
| `test_pending_fixes_strict.py` | ``known_failure`` under strict acceptance: the gap fails the run instead of XFAILing. |
| `test_plugin_catalog_ci_confinement.py` | The catalog admission gate must validate the pinned clone's own files only. |
| `test_plugin_validate_action.py` | The external action must never install Hermes into the plugin checkout. |
| `test_prompt_surface.py` | The committed prompt-surface snapshot is exactly what the code renders. |
| `test_protected_canary_publication.py` | Execute protected canary workflow/controller with local Git and HTTP only. |
| `test_required_results.py` | Behavior tests for the strict CI aggregate gate (scripts/ci/required_results.py). |
| `test_stable_release_commit_threading.py` | Stable runs on the default branch, so every lane must be told which commit to test. |
| `test_stable_release_graph.py` | The release workflow's dependency graph enforces publication ordering. |
| `test_strict_ruff_target.py` | The strict lint config may only rewrite code to syntax the oldest supported Python runs. |
| `test_tag_builds_summary.py` | Run the tagged-build summary step against a disposable R2 transport. |
| `test_termux_input_archive.py` | CI runs archival before the exact tool and payload consumers. |
| `test_timings_report.py` | Tests for scripts/ci/timings_report.py — generate_review_status(). |
| `test_update_ci_routing.py` | Update-path CI routing: ownership-derived selectors and the full dispatch chain. |
| `test_update_transitive_routing.py` | Executed second-hop update dependencies must retain their real-update routes. |
| `test_windows_update_crash_oracles.py` | The Windows update E2E, judged on this OS: the workflow's selection runs every cell, and a verdict the crash cells can only reach on a Windows runner says pass exactly when the user's update was what the cell claims. |
| `test_workflow_job_graph.py` | A job reads another job's result only through a `needs` entry it declares. |
| `workflow_steps.py` | Local receipts for the few safe routing steps, NOT a hosted workflow runner. |

## `tests/compat/`

| File | What it does |
|---|---|
| `README.md` | Running updater compatibility |
| `old_updater_dependencies.py` | Frozen historical updater function, executed by test_old_updater_shims. |
| `old_updater_support.py` | Shared guards for historical exports; real child execution lives in test_old_updater_takeover. |
| `old_updater_surface.json` | JSON data/configuration |

## `tests/computer_use/`

| File | What it does |
|---|---|
| `driver_fixture.py` | Independent CUA process fixture shared by selection and doctor callers. |
| `live_cua_0_9_smoke.py` | Opt-in macOS smoke test for the installed cua-driver live MCP contract. |
| `test_cua_atexit_teardown.py` | Tests for cua-driver subprocess teardown on interpreter exit. |
| `test_cua_no_overlay.py` | Tests for the cua-driver --no-overlay policy. |
| `test_cua_perf_knobs.py` | Behavior contracts for computer_use latency knobs. |
| `test_cua_pm_selection.py` | CUA selection uses PM facts, never a second installer or stale vendor tree. |
| `test_cua_spawn_env_sanitization.py` | Regression tests: every remaining cua-driver spawn site must sanitize the subprocess environment. |
| `test_cua_telemetry.py` | Tests for the cua-driver telemetry opt-in policy. |
| `test_cua_wayland_env.py` | Tests: `_child_env`, `test_configured_native_wayland_reaches_linux_wayland_child`, `test_native_wayland_not_injected_without_wayland_display_or_opt_in` |
| `test_cua_wsl_manifest_path.py` | Tests: `test_wsl_windows_manifest_path_translates_to_drvfs`, `test_resolve_mcp_invocation_normalizes_windows_manifest_command_in_wsl` |
| `test_doctor.py` | Tests for ``tools.computer_use.doctor``. |
| `test_permissions_resolution.py` | Computer Use readiness resolves PM state even under a thin GUI PATH. |

## `tests/conformance/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `persistence/README.md` | Crash/resume persistence conformance cells |
| `persistence/__init__.py` | Package marker / package-level exports |
| `persistence/_harness.py` | Shared harness for the crash/resume persistence conformance cells (#80921). |
| `persistence/test_cell1_prefix_durability.py` | Cell 1 — prefix continuation + recovery determinism under real SIGKILL. |
| `persistence/test_cell2_consume_once.py` | Cell 2 — consume-once under cross-process concurrent delivery. |
| `persistence/test_cell3_rotation_atomicity.py` | Cell 3 — crash mid-compression-rotation: the atomic-publication contract. |
| `persistence/test_cell5_delivery_outbox_exactly_once.py` | Cell 5 — effect exactly-once across the delivery-outbox boundary. |
| `test_profile_write_tripwire.py` | Profile-isolation write tripwire: no cross-profile writes to the default home. |
| `test_vector_generator.py` | Conformance vector generator tests (Phase 5 oracle workstream). |
| `vectors/discord.json` | JSON object with keys `$comment`, `oracle`, `platform`, `vectors` |
| `vectors/slack.json` | JSON object with keys `$comment`, `oracle`, `platform`, `vectors` |
| `vectors/telegram.json` | JSON object with keys `$comment`, `oracle`, `platform`, `vectors` |
| `vectors/whatsapp.json` | JSON object with keys `$comment`, `oracle`, `platform`, `vectors` |

## `tests/cron/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Cron-test fixtures. |
| `test_agent_scheduling_gate.py` | Behavior contract for the cron.allow_agent_scheduling config gate. |
| `test_atomic_paused_creation.py` | Creation is either armed normally or durably paused before registration. |
| `test_blueprint_catalog.py` | Tests for Automation Blueprints — the parameterized automation blueprint system. |
| `test_bot_chat_delivery_no_owner.py` | A Bot Chat cron delivery whose target owner is not running is parked, never booked failed: a later tick admits it to the owner once, under the same delivery id. |
| `test_bot_chat_legacy_isolation.py` | One malformed legacy ``cron/bot_chat_pending`` record must not stop the profile's cron. |
| `test_canonical_completion_retention.py` | A recurring canonical cron job's completion tombstones stay bounded: an id is retired once its admission journal is gone (nothing can replay it), never while recovery could still replay it. |
| `test_canonical_cron.py` | Agent cron must enter the owner before importing any agent-side storage. |
| `test_canonical_firer_give_up.py` | An in-gateway firer that gives up on a canonical run records its own attempt as given up. |
| `test_canonical_receipt_bookkeeping.py` | Canonical cron recovery settles attempts and never re-pauses an explicitly resumed job. |
| `test_catchup_policy.py` | The local missed-run policy preserves grace and manual triggers. |
| `test_claim_job_for_fire.py` | Tests for the store-level CAS fire claim (Phase 4C). |
| `test_cleanup_timeout.py` | Regression tests for bounded cron post-run cleanup. |
| `test_codex_execution_paths.py` | Tests: `_run_owned_job`, `_patch_agent_bootstrap`, `_codex_message_response`, `_UnauthorizedError`, `_FakeOpenAI`, `_Codex401ThenSuccessAgent` … |
| `test_compute_next_run_dst.py` | Regression: ``compute_next_run`` must hold a cron job's wall-clock hour in the configured IANA timezone across DST. |
| `test_compute_next_run_last_run_at.py` | Test that compute_next_run uses last_run_at for cron jobs. |
| `test_context_from_response_extraction.py` | context_from must inject the previous run's answer, not its prompt (#117290). |
| `test_continuity_silent_audits.py` | Silent audit records must not replace useful continuity output (#104541). |
| `test_cron_bot_chat_create_if_missing.py` | Cron Bot Chat delivery creates the profile's canonical Bot Chat when it does not exist yet. |
| `test_cron_bot_chat_delivery.py` | Bot Chat cron delivery: deliver='bot-chat[:<profile>]' injects job output into a local profile's canonical Bot Chat session as a real inbound turn. |
| `test_cron_context_from.py` | Tests for cron job context_from feature (issue #5439 Option C). |
| `test_cron_created_delivery.py` | Create-time delivery resolution for cron-context job creation. |
| `test_cron_delivery_redaction.py` | Cron output is secret-redacted on every outward lane, fail-closed. |
| `test_cron_direct_api_call.py` | Regression guard for #62151 — gateway cron must not wedge on 2nd+ API call. |
| `test_cron_direct_api_call_watchdog.py` | Regression guard for #80759 — the inline non-streaming call must be bounded. |
| `test_cron_emfile_stall.py` | Regression tests for #87644 — cron scheduler silently stalls after EMFILE. |
| `test_cron_empty_payload.py` | Regression tests for empty-payload cron jobs (incident a5e29e688dc0). |
| `test_cron_empty_turn_stays_silent.py` | An abnormal empty turn (``empty_response_exhausted``) is delivered as silence, not as a '⚠️ Cron ... failed' alert: the finalizer stamps ``failure_reason`` for the UI but keeps ``failed`` False, and the scheduler recogn… |
| `test_cron_execution_identity.py` | Plugins can tell which cron execution they run inside (#130722). |
| `test_cron_explicit_empty_toolsets.py` | An explicitly-set EMPTY per-job toolset allowlist must mean 'nothing allowed' end to end. |
| `test_cron_failure_deliver.py` | Per-job ``failure_deliver`` routing (NS-788). |
| `test_cron_failure_notice_copy.py` | User-facing cron failure notices: plain words, the real output path, and the exact `hermes cron` command to act on. Contract tests, not snapshots (root AGENTS.md). |
| `test_cron_failure_summarizer_inactivity.py` | _summarize_cron_failure_for_delivery must not mislabel the scheduler's own inactivity-timeout abort as a provider/fallback-chain failure, and must not claim a fallback chain was "exhausted" when none is configured. |
| `test_cron_home_target_profile_scope.py` | Regression: multiplex cron delivery destination must follow the OWNING profile. |
| `test_cron_import_error_skew_hint.py` | Import-class cron failures name gateway code skew when it exists (#95294). |
| `test_cron_inactivity_timeout.py` | Tests for the cron inactivity watchdog loop (runs on its own daemon thread). |
| `test_cron_incidents.py` | Durable cron failure incidents: signature dedup, lifecycle, ack, CLI. |
| `test_cron_incidents_resolve.py` | A successful run resolves the job's open incidents; the same error afterwards re-opens them. |
| `test_cron_journal_terminal_exits.py` | Bug class: a canonical cron firer books its own terminal ledger row on a non-completion exit (ownership lost, shutdown interrupt, crashed tail) but leaves the admission journal behind; receipt recovery then replays the… |
| `test_cron_kanban_env_isolation.py` | Cron sessions must not inherit a kanban worker's dispatcher identity. |
| `test_cron_live_bot_delivery.py` | Cron admission must not become a second writer or a completed-delivery claim. |
| `test_cron_live_delivery_confirmation.py` | Live-adapter delivery confirmation for cron (#77763). |
| `test_cron_manage_profile_scope.py` | cron.manage optional ``profile`` param — per-profile store scoping. |
| `test_cron_mcp_toolset_allowlist.py` | A per-job MCP allowlist stays narrow whichever spelling names the server (#141468). |
| `test_cron_mcp_toolset_empty_block.py` | A cron job whose ``enabled_toolsets`` names an MCP server that resolves to zero tools is blocked as ``blocked_config`` instead of running tool-less and booking success (#109050). |
| `test_cron_memory_contract.py` | Contract pin: cron <-> persistent-memory loading. |
| `test_cron_multiplex_desktop_ticker_scope.py` | Regression tests for #100489 — desktop multiplex ticker must not deliver a secondary profile's cron output through the default profile's identity. |
| `test_cron_multiplex_inflight_release.py` | One process ticks every profile: a claim must be released under the key it was registered with. |
| `test_cron_multiplex_liveness_and_pools.py` | Per-home cron liveness and worker-pool lifetime under one multiplexing process. |
| `test_cron_multiplex_profile_route_preflight.py` | Multiplex profile_routes must rescue cron preflight from false blocks. |
| `test_cron_multiplex_served_profile_parity.py` | Standalone-vs-served parity for the cron subsystem under ``gateway.multiplex_profiles``. |
| `test_cron_multiplex_shared_route_delivery.py` | Regression tests for #101113 — a credentialless satellite profile under ``gateway.profile_routes`` delivers cron output through the PRIMARY adapter for exactly the targets the primary routes to it, and fails closed othe… |
| `test_cron_multiplex_tick_ownership.py` | One host process ticks every profile: cron ownership and state must be per profile. |
| `test_cron_next_run_profile_timezone.py` | Regression test for #97905 / carrier PR #92489. |
| `test_cron_no_agent.py` | Tests for cronjob no_agent mode — script-driven jobs that skip the LLM. |
| `test_cron_non_push_origin.py` | Cron deliver=origin on a non-push surface (#69304). |
| `test_cron_origin_synthetic_thread.py` | Cron origin capture: Slack per-message session-key threads are not routing. |
| `test_cron_pinned_job_fallback.py` | A cron job with its own provider/model/base_url pin never walks the global fallback chain (#100437). |
| `test_cron_pre_agent_fallback_notice.py` | A cron job whose primary provider failed credential resolution and ran on a fallback entry must say so in the delivered report (#74349): the cron agent has no status rail, so the pre-agent switch would otherwise live on… |
| `test_cron_profile_isolation.py` | Regression tests for #4707 — cron must be per-profile. |
| `test_cron_prompt_injection_skill.py` | Regression guard: skill content loaded at cron runtime must be scanned. |
| `test_cron_provider_pin.py` | Unpinned cron jobs run on the main agent model at fire time; ``pinned`` locks it. |
| `test_cron_reasoning_effort.py` | Per-job reasoning_effort override: store contract + scheduler precedence. |
| `test_cron_reconnect_only_rejection.py` | A cron payload the live lane rejected as reconnect-only is not lost when standalone fails (#125363). |
| `test_cron_recover_after_commit.py` | A cron submit that fails after the owner committed the admission is observed, not paused (N61). |
| `test_cron_recover_pause.py` | Receipt recovery: a ``missing`` admission is a definite non-admission (booked failed, never a pause), and a verified terminal receipt lifts the pause its own ``CronExecutionUnknown`` caused. |
| `test_cron_recovery.py` | Terminal owner receipts recover delivery without replay or double bookkeeping. |
| `test_cron_relay_delivery_guards.py` | Fire-time guards: stale Slack creation-thread routing + relay-fronted preflight. |
| `test_cron_relay_dm_origin_user_id.py` | A cron fire into a relay DM carries the origin's ``user_id``, so a COLD routing cache still egresses. |
| `test_cron_relay_run_forward.py` | Manual `hermes cron run` forwarding for relay-fronted delivery targets. |
| `test_cron_run_metrics.py` | hermes.cron.run: one row per terminal execution and per dropped occurrence. |
| `test_cron_run_stale_claim_reap.py` | Regression for #86721 — a one-shot `hermes cron run` invocation's dispatched runner thread dies with the exiting process, leaving a stale 'claimed'/'running' row in cron/executions.db that blocks every subsequent manual… |
| `test_cron_script.py` | Tests for cron job script injection feature. |
| `test_cron_session_workdir.py` | Cron sessions stamp the job's workdir on their session row (#108205). |
| `test_cron_thread_seed_dm_keying.py` | Cron thread-seed must key EXACTLY like the reply that will continue it. |
| `test_cron_tick_stale_yield.py` | Stale-code cron tick yield gate. |
| `test_cron_ticker_drift.py` | Ticker loop period contract: the sleep is to a deadline, not for a duration. |
| `test_cron_timezone_migration_catchup.py` | Timezone-migration silent misfire on the cron fire path. |
| `test_cron_windows_venv_abi.py` | Windows cron scripts overlay the committed generation, never the stale in-tree venv. |
| `test_cron_workdir.py` | Tests for per-job workdir support in cron jobs. |
| `test_cronjob_gateway_liveness.py` | Tests for issue #87033 — the cronjob tool must surface gateway liveness. |
| `test_dead_owner_claim_reclaim.py` | Dead-owner cron claim reclaim + one-shot CLI `cron run` sync gate (#86721). |
| `test_delivery_outcome_writeback.py` | A queued cron delivery's real outcome is written back onto the run that queued it. |
| `test_delivery_queue.py` | Durable at-most-once delivery handoff for restart-safe cron workers. |
| `test_delivery_queue_retention_race.py` | A delivery must stay terminal when retention races a repeated enqueue. |
| `test_dispatch_lateness_stamp.py` | Missed-run dispatch visibility (#99879). |
| `test_due_scan_dst_fold.py` | Due-scan comparisons must use absolute instants across a repeated DST hour. |
| `test_due_scan_save_failure.py` | The due scan must still hand back its due jobs when the store cannot be written. |
| `test_due_stale_cron_edit.py` | Stale-schedule guard on the cron fire path (#93049). |
| `test_duration_dst.py` | Duration schedules measure elapsed time, including across UTC offset changes. |
| `test_estop.py` | Global emergency stop (`hermes pause` / `hermes resume`) — agent/estop.py. |
| `test_execution_ledger.py` | Durable cron execution-ledger behavior. |
| `test_execution_progress_stamp.py` | The run monitor stamps ``progress_at`` on the execution row while the agent is active. |
| `test_external_worker_config_hooks.py` | External cron workers must register the owning profile's config-declared hooks (#131764). |
| `test_external_worker_secret_sources.py` | External cron workers must see plugin-registered secret sources (#121929). |
| `test_file_permissions.py` | Tests for file permissions hardening on sensitive files. |
| `test_fire_claim_lost_after_delivery.py` | #105861 / #113357: a fire-claim that only *reads* as lost must not overwrite a completed run's terminal status — an ok, or a failure notice carrying its real error. |
| `test_fire_forward_failure_stamp.py` | Tests for the last_fire_error stamp (missed scheduled fires made visible). |
| `test_idle_tick_config_skip.py` | Idle cron ticks must not load config (#33612 salvage). |
| `test_inflight_stale_guard.py` | RED-first regression test for the cron in-flight claim leak (t_27b59583). |
| `test_jobs.py` | Tests for cron/jobs.py — schedule parsing, job CRUD, and due-job detection. |
| `test_jobs_changed_notify.py` | Tests for on_jobs_changed wiring (Phase 4F.1). |
| `test_jobs_crossprocess_lock.py` | Regression test for the jobs.json cross-process lock. |
| `test_jobs_file_ownership.py` | Regression tests for issue #68483. |
| `test_jobs_shrink_merge.py` | Regression for #80624 — concurrent creates must not be clobbered on save. |
| `test_jobs_time.py` | Unit contract for the per-job schedule knobs: ``cron/jobs_time.py``. |
| `test_last_failure_stamp.py` | Tests for the sticky ``last_failure`` stamp (#118354). |
| `test_lifecycle_guard_budget.py` | Whole-walk work budget for the gateway lifecycle guard (#78398). |
| `test_lifecycle_guard_heredoc_walk.py` | The referenced-script walk sees the same inert-heredoc-masked view as the direct scan (#110422). |
| `test_lifecycle_guard_live_db.py` | Regression tests for raw lifecycle-guard reads of live SQLite files. |
| `test_lifecycle_guard_profile_scan.py` | Profile scanning must terminate without dropping long commands (#129281). |
| `test_live_firer_receipt_recovery.py` | Receipt reconciliation keeps its journal while a live foreign firer still owns the ledger row. |
| `test_manual_run_extra_fire.py` | A manual run is an EXTRA fire: it never consumes the job's scheduled occurrence or repeat budget. |
| `test_media_delivery_parity.py` | Cron media-delivery parity — manual runs must not silently drop attachments. |
| `test_media_send_timeout.py` | Cron media-send timeout resolution and failure-reason formatting. |
| `test_mirror_origin_fallback.py` | Mirror eligibility for origin-fallback and explicit cron delivery targets. |
| `test_misfire_backstop_oneshot_grace.py` | Misfire-backstop grace gate for one-shot cron jobs (#93526). |
| `test_misfire_catchup.py` | Tests for fire_overdue_jobs — misfire catch-up for external cron providers. |
| `test_missed_window_catchup.py` | A recurring occurrence that a tick took off the schedule but never dispatched must fire once after the scheduler restarts — never be silently lost, never fire twice (#107485). |
| `test_monitor_kind.py` | Tests for monitor-mode cron jobs — cheap source each tick, hash-suppressed agent runs. |
| `test_notepad.py` | Per-job durable cron notepad: KV scratchpad surviving scheduled wake-ups. |
| `test_oneshot_dispatch_failure_run_claim.py` | Regression tests for #86522 — one-shot run_claim cleared on dispatch failure. |
| `test_oneshot_grace_due_scan.py` | Due-scan grace gate for one-shot cron jobs. |
| `test_oneshot_guard_warning.py` | Due-scan dispatch-limit guard: removal of a re-armed consumed one-shot is operator-visible (#93524 follow-up to #93615). |
| `test_owner_start_time_drift.py` | Start-time fingerprint drift between claim and recovery reads (#117505). |
| `test_parallel_pool.py` | Tests for the persistent parallel pool and running-job guard in cron/scheduler.py. |
| `test_per_job_timezone.py` | Per-job ``timezone``: one store, several zones, each job on its own wall clock. |
| `test_persisted_error_rearm_legality.py` | The persisted-error re-arm must respect cron schedule legality. |
| `test_preflight_config.py` | Cron pre-dispatch configuration validation (T1-26). |
| `test_preflight_credential_verdict_names_home.py` | A ``blocked_config`` credential verdict names the profile + HERMES_HOME the scheduler actually read (#116213): "No Codex credentials stored" from a gateway whose home differs from the shell that works is otherwise indis… |
| `test_preflight_managed_routes.py` | Managed-scope ``gateway.profile_routes`` must reach the satellite cron path (#121212). |
| `test_queued_delivery_fencing.py` | The canonical delivery queue row is the cron run's send: it obeys the same fire-claim fence, receipt and settlement rules as a direct send. |
| `test_quota_hold.py` | Provider quota windows park a cron job instead of re-firing into them (#89376; ai-velho-oy/chairman#3). |
| `test_recurring_persisted_error_recovery.py` | Persisted-state stale-error recovery for recurring cron jobs (t_8b5480b3). |
| `test_recurring_wedge_selfheal.py` | Deterministic reproduction of the recurring-cron wedge (t_8b5480b3) — RED/GREEN. |
| `test_registration_ownership.py` | Live direct runs and successor registrations must survive stale cleanup. |
| `test_relay_fronted_delivery.py` | Cron delivery for relay-fronted logical platforms. |
| `test_restart_safe_worker.py` | Restart-safe cron worker handoff and ownership contracts. |
| `test_restart_safe_worker_death_evidence.py` | Post-adoption failure visibility (#128509, #129254), not the unknown crash cause. |
| `test_retirement_dispatch.py` | The tick-to-worker handoff must have no retirement-sized gap after can_dispatch. |
| `test_rewrite_skill_refs.py` | Tests for cron.jobs.rewrite_skill_refs — the curator integration that keeps scheduled cron jobs pointing at the right skill names after a consolidation / pruning pass. |
| `test_run_error_diagnostics.py` | Failure detail belongs in the local audit, not the delivery summary. |
| `test_run_one_job.py` | Characterization + unit tests for the `run_one_job` shared helper (Phase 4A). |
| `test_scheduled_occurrence.py` | Completed scheduled attempts survive a jobs.json rollback, not just a process restart. |
| `test_scheduler.py` | Tests for cron/scheduler.py — origin resolution, delivery routing, and error logging. |
| `test_scheduler_completion_verification.py` | Fail-closed completion booking for cron runs (#93820). |
| `test_scheduler_cron_session_isolation.py` | Regression test for cron-session approval isolation. |
| `test_scheduler_media_voice_flag.py` | Cron media delivery forwards the voice flag to ``send_voice`` (#132120): the adapter decides voice bubble vs plain audio from ``is_voice``, matching the gateway dispatch. |
| `test_scheduler_provider.py` | Characterization tests for the cron trigger before/after the provider refactor. |
| `test_scheduler_session_title_nudge.py` | Tests for cron/scheduler.py — cron session titling and the repeated-failure review nudge. |
| `test_scheduler_shutdown_guard.py` | Regression coverage for #58720 / #55924 — cron scheduling races interpreter finalization. |
| `test_script_claim_heartbeat.py` | Regression coverage for one-shot claims during blocking cron scripts. |
| `test_sessiondb_init_hang.py` | Canonical cron must bound store acquisition without unpersisted inference. |
| `test_shutdown_interrupt.py` | Tests for #60432: cron jobs must not be silently invisible to gateway shutdown, and a job whose tool subprocess got killed by shutdown must never be reported as a successful run. |
| `test_stale_module_leaf_imports.py` | Regression tests for lazy consumers importing from stale cached modules. |
| `test_stale_running_recovery.py` | Live-but-deadlocked cron workers (#115692). |
| `test_suggestions.py` | Tests for the Suggested Cron Jobs feature. |
| `test_terminal_job_rearm.py` | Behavioral coverage for terminal cron jobs and explicit one-shot re-arm. |
| `test_tick_without_gateway.py` | ``hermes cron tick`` with no live gateway refuses agent jobs instead of spawning one. |
| `test_ticker_stall.py` | Regression tests for #60703 — cron ticker silently stalls after gateway restart. |
| `test_ticker_startup_survival.py` | The ticker contract — "an exception must not silently kill the cron thread" — holds for every step that runs on the cron-scheduler thread, not only the tick body: startup recovery, the multiplex per-cycle enumeration/ga… |
| `test_timezone.py` | Tests for timezone support (hermes_time module + integration points). |
| `test_unreachable_retry.py` | Cowork-inspired bounded automatic re-runs for cron fires that never reached the model. |
| `test_upgrade_module_skew.py` | Cron imports remain usable when a daemon spans an on-disk upgrade. |
| `test_usage_audit_logger.py` | Tests for the cron usage_audit.jsonl logger. |
| `test_warning_delivery_policy.py` | Failure classification survives durable delivery and drain-time policy changes. |
| `test_warning_execution_outcome.py` | Suppressed automatic diagnostics retain failed jobs without invented delivery receipts. |
| `test_warning_transport_contract.py` | Real cron router/queue with local transport doubles; no external network. |
| `test_worktree_maintenance_isolation.py` | Background worktree maintenance must not initialize the interactive CLI. |
| `test_worktree_maintenance_once_per_repo.py` | Worktree maintenance must not multiply whole-``.worktrees/`` disk walks. |
| `test_worktree_maintenance_one_sweep_at_a_time.py` | The cron tick's worktree prune must not fan its git work out with the profile count (#143255). |

## `tests/dashboard/`

| File | What it does |
|---|---|
| `test_ws_client_host.py` | Regression tests for the in-container WebSocket client host resolution. |

## `tests/desktop/`

| File | What it does |
|---|---|
| `test_appinstaller_check_script.py` | App Installer checker output contracts and native WinRT dependency coverage. |
| `test_check_store_update.py` | Store update contracts use the actual API's sequence and result shapes. |

## `tests/docker/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Shared fixtures for docker-image integration tests. |
| `test_config_migration.py` | Runtime smoke test for Docker config-schema migration on boot. |
| `test_container_restart.py` | Container-restart survives per-profile gateway registrations. |
| `test_dashboard.py` | Harness: dashboard opt-in via HERMES_DASHBOARD. |
| `test_docker_exec_privilege_drop.py` | Regression tests for the docker-exec privilege-drop shim. |
| `test_dump_build_sha.py` | Regression test: ``hermes dump`` reports a real git SHA inside the container. |
| `test_gateway_bootstrap_state.py` | Runtime smoke tests for Docker gateway_state.json bootstrap seeding. |
| `test_gateway_run_supervised.py` | Harness: `docker run <image> gateway run` redirects to supervised mode. |
| `test_home_override_scripts.py` | Runtime smoke tests for Docker HOME overrides and script behavior. |
| `test_image_payload.py` | The image's non-root runtime uses its staged tools and generated assets. |
| `test_immutable_install.py` | Runtime smoke tests for Docker immutable install tree and install-method stamp. |
| `test_immutable_install_permissions.py` | Docker smoke tests for immutable install permissions. |
| `test_interactive_logging.py` | Keep supervised output away from an interactive Docker CMD's terminal. |
| `test_license_file_present.py` | Runtime smoke test for Docker image license-file presence. |
| `test_log_dir_seed.py` | Runtime smoke test for Docker $HERMES_HOME/logs/gateways seeding. |
| `test_main_invocation.py` | Harness: docker run <image> [cmd...] invocation patterns. |
| `test_poll_stalled_exec.py` | A stalled ``docker exec`` is one failed poll attempt, never the poll's verdict. |
| `test_profile_gateway.py` | Harness: a named profile does not get a gateway of its own inside the container. |
| `test_puid_pgid_remap.py` | Runtime smoke tests for Docker PUID/PGID and UID/GID remap. |
| `test_s6_gateway_planned_stop.py` | E2E: ``hermes gateway stop`` inside the s6 image is a PLANNED stop. |
| `test_s6_profile_gateway_integration.py` | Harness: in-container integration tests for S6ServiceManager. |
| `test_smoke.py` | Runtime smoke tests for the Docker image entrypoint and subcommands. |
| `test_sqlite_runtime.py` | Runtime qualification for SQLite in the published Docker image. |
| `test_stage2_browser_discovery.py` | Verify the Docker image bakes a runnable full Chromium executable. |
| `test_tini_compat_shim.py` | Runtime smoke test for the Docker tini compatibility shim (#34192, #66679). |
| `test_toplevel_chown.py` | Runtime smoke tests for Docker top-level state-file ownership repair. |
| `test_tui_gateway_startup.py` | Ink's real bootstrap starts its s6 owner without sharing the terminal. |
| `test_tui_passthrough.py` | Harness: interactive TUI TTY passthrough. |
| `test_tui_prebuilt_bundle.py` | Harness: the image ships a prebuilt TUI bundle, not a runtime npm install. |
| `test_user_flag_guard.py` | Runtime smoke tests for Docker --user flag guard. |
| `test_webapp_bundle.py` | The image ships a current Webapp renderer that the unprivileged user can use. |
| `test_zombie_reaping.py` | Harness: PID 1 must reap orphaned zombie processes. |

## `tests/e2e/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conftest.py` | Shared fixtures for gateway e2e tests (Telegram, Discord). |
| `core/__init__.py` | Package marker / package-level exports |
| `core/_pending_fixes.py` | Merge-order-safe expected failures for live gaps whose fix is an open PR. |
| `core/_pm_dependencies.py` | Select prepared test dependencies for subprocesses with isolated E2E homes. |
| `core/chaos/__init__.py` | Package marker / package-level exports |
| `core/chaos/_agent_driver.py` | Child-process driver: one real AIAgent + real SessionDB, several turns, stdin control. |
| `core/chaos/_gateway_fake_platform.py` | In-memory messaging platform for the gateway chaos suite, loaded as a REAL user plugin. |
| `core/chaos/_gateway_harness.py` | Test-side driver for a real ``python -m gateway.run`` process with the chaos fake platform. |
| `core/chaos/_helpers.py` | Shared oracle helpers for the chaos (agent-turn liveness) E2E lane. |
| `core/chaos/_tui_rpc.py` | Stdio JSON-RPC driver for a REAL ``python -m tui_gateway.entry`` subprocess. |
| `core/chaos/test_agent_turn_liveness.py` | C8 chaos: agent-turn liveness of a REAL AIAgent (child process) under provider and tool faults. |
| `core/chaos/test_gateway_turn_liveness.py` | C8 chaos: agent-turn liveness through the REAL messaging gateway (``python -m gateway.run``). |
| `core/chaos/test_tui_gateway_turn_liveness.py` | C8 chaos: agent-turn liveness through the REAL tui_gateway JSON-RPC subprocess. |
| `core/cli_tmux/__init__.py` | Package marker / package-level exports |
| `core/cli_tmux/_classic.py` | Shared harness for the classic-CLI tmux suites (``display.interface: cli``). |
| `core/cli_tmux/test_classic_cli_live_session.py` | The classic CLI's long live session, with a per-process witness (#134889 T24). |
| `core/cli_tmux/test_classic_cli_main_parity.py` | The classic CLI keeps main's behaviour under the one gateway: the 15-step main-vs-branch comparison. |
| `core/cli_tmux/test_resize_scrollback.py` | #95375 on a reflowing terminal: resizing the classic CLI leaves every transcript line in tmux's scrollback + screen exactly once, with no stray blank or prompt rows. |
| `core/cli_tmux/witness/sitecustomize.py` | Per-process witness for the classic-CLI live session (``test_classic_cli_live_session.py``). |
| `core/compaction/__init__.py` | Package marker / package-level exports |
| `core/compaction/_helpers.py` | Lane-private harness for the compaction property / liveness suites (class C4). |
| `core/compaction/conftest.py` | Lane-private fixtures for the compaction suites (one fake provider per module, one session per test). |
| `core/compaction/test_compaction_auto.py` | C4 automatic compaction: property + liveness suite on seeded random sessions (good summarizer). |
| `core/compaction/test_compaction_kill9.py` | C4 compaction atomicity: kill -9 a real child process mid-compaction, then prove state.db is intact and the session is resumable. |
| `core/compaction/test_compaction_manual.py` | C4 manual compaction: ``/compress``, ``/compress here N`` and rolling micro-compaction, end to end. |
| `core/compaction/test_compaction_summary_faults.py` | C4 summarizer faults: a failed summary never commits, and failure is bounded and visible. |
| `core/dashboard/__init__.py` | Package marker / package-level exports |
| `core/dashboard/_helpers.py` | Lane-private harness for the dashboard (``hermes dashboard``) E2E suite. |
| `core/dashboard/_issue_helpers.py` | Shared bits for the dashboard lane's open-issue cells (#120527, #120937). |
| `core/dashboard/_pty_helpers.py` | Client side of the dashboard's embedded-TUI WebSocket (``/api/pty``), as the browser xterm speaks it. |
| `core/dashboard/_reaper.py` | The ONE place the dashboard lane cleans up processes a test left behind. |
| `core/dashboard/fixture_catalog_mcp.py` | Tiny offline stdio MCP server installed through the dashboard's MCP catalog (#120527 cell). |
| `core/dashboard/test_api_session_chat_limits.py` | #120937: session chat on the gateway API server must never silently truncate a long message. |
| `core/dashboard/test_dashboard_auth.py` | Dashboard auth: every mounted ``/api/*`` route and every WebSocket route refuses a caller without the session token (issue class: unauthenticated dashboard access, GHSA-ppp5-vxwm-4cf7 family). |
| `core/dashboard/test_dashboard_mcp_install.py` | #120527: a dashboard MCP catalog install must never wedge the web server. |
| `core/dashboard/test_dashboard_profiles.py` | Profile switching through the dashboard API never crosses profiles, and a Config-page save round-trips the user's file. |
| `core/dashboard/test_dashboard_pty.py` | Dashboard embedded chat: the ``/api/pty`` WebSocket drives a REAL ``hermes --tui`` end to end. |
| `core/dashboard/test_dashboard_sessions.py` | Dashboard session browser against a live ``state.db`` while another process writes to it. |
| `core/delivery/__init__.py` | Package marker / package-level exports |
| `core/delivery/_cron_clock.py` | Lane-private harness for the C13 virtual-clock cron soak (test_cron_virtual_clock_soak.py). |
| `core/delivery/_fake_platform.py` | Lane-private harness for the C12 messaging exactly-once suite (test_messaging_exactly_once.py). |
| `core/delivery/_pending_fixes.py` | Merge-order-safe expected failures for live gaps whose fix is an open PR. |
| `core/delivery/test_cron_virtual_clock_soak.py` | C13 — virtual-clock soak of the REAL cron ticker loop (~30 virtual days per scenario). |
| `core/delivery/test_messaging_exactly_once.py` | C12 — messaging-platform delivery exactly-once, through the REAL gateway and the REAL agent. |
| `core/history/__init__.py` | Package marker / package-level exports |
| `core/history/_helpers.py` | Transcript-ledger harness for the conversation-history (C3) and prompt-cache (C17) suites. |
| `core/history/test_prefix_stability.py` | C17 prompt-cache prefix byte-stability + usage accounting across REAL processes and surfaces. |
| `core/history/test_transcript_ledger.py` | C3 transcript ledger: what is persisted == what is replayed == what a resume shows, per step. |
| `core/kanban/__init__.py` | Package marker / package-level exports |
| `core/kanban/_helpers.py` | Real-process Kanban board harness: a scratch HOME/HERMES_HOME, the recording fake provider, and the real ``hermes kanban`` CLI (dispatcher ticks spawn real ``hermes chat -q`` workers). |
| `core/kanban/test_kanban_decompose_billing.py` | Auto-decompose billing bounds, proven against a REAL ``hermes gateway run`` embedded dispatcher. |
| `core/kanban/test_kanban_dispatcher_restart.py` | Dispatcher SIGKILLed mid-tick and restarted: the board keeps every real task row (#119003 class). |
| `core/kanban/test_kanban_rate_limit_review.py` | A rate-limited implementer run must stay a neutral, once-billed requeue — and must not strand the card's later review handoff (#119070). |
| `core/kanban/test_kanban_worker_contract.py` | Worker-side board contracts through the real dispatcher and a real ``hermes chat -q`` worker. |
| `core/kanban/test_kanban_worker_sigkill.py` | Kanban worker SIGKILLed mid-run, through the real dispatcher CLI and real ``hermes chat -q`` workers. |
| `core/live/__init__.py` | Package marker / package-level exports |
| `core/live/_helpers.py` | Shared machinery for the secrets-gated LIVE provider canary (``-m live``). |
| `core/live/test_live_providers.py` | LIVE provider canary: real AIAgent + real adapters against real vendor APIs. |
| `core/mcp_plugins/__init__.py` | Package marker / package-level exports |
| `core/mcp_plugins/_helpers.py` | Shared harness for the MCP + plugin conformance suite. |
| `core/mcp_plugins/_plugin_helpers.py` | Plugin-side helpers for the MCP + plugin suite: portable (Agent Plugins v1) packages on disk, and a ``tui_gateway`` stdio host (the Ink TUI's backend) driven over JSON-RPC in an ``E2EHome``. |
| `core/mcp_plugins/mcp_fixture_server.py` | Real MCP server (installed ``mcp`` 2.x SDK) for the MCP + plugin conformance suite. |
| `core/mcp_plugins/test_mcp_stdio_conformance.py` | MCP conformance over stdio against a REAL ``mcp`` 2.x server (``mcp_fixture_server.py``). |
| `core/mcp_plugins/test_mcp_streamable_http.py` | MCP over streamable HTTP against a REAL ``mcp`` 2.x server subprocess (``mcp_fixture_server.py``). |
| `core/mcp_plugins/test_plugin_activation.py` | Plugin activation with REAL MCP servers (Agent Plugins v1 portable packages). |
| `core/parity/__init__.py` | Package marker / package-level exports |
| `core/parity/_boot_contract.py` | Bridge to the Desktop's real READY-sentinel parser (``apps/desktop/electron/backend-ready.ts``). |
| `core/parity/_drive_acp.py` | Entrypoint driver for the parity matrix: the ACP stdio server (``hermes acp``). |
| `core/parity/_drive_cli.py` | Entrypoint drivers for the parity matrix: CLI subprocess entrypoints. |
| `core/parity/_drive_cron.py` | Entrypoint driver for the parity matrix: cron run-now (``hermes cron run <id>``). |
| `core/parity/_drive_gateway.py` | Entrypoint drivers for the parity matrix: messaging gateway + OpenAI-compatible API server. |
| `core/parity/_drive_rpc.py` | Entrypoint drivers for the parity matrix: the JSON-RPC surfaces. |
| `core/parity/_gateway_child.py` | Lane-private child process for ``_drive_gateway.drive_gateway``. |
| `core/parity/_helpers.py` | Shared fixture HERMES_HOME + invariant checks for the entrypoint-parity suite. |
| `core/parity/desktop_ready_parse.mjs` | Feed bytes (stdin) through the Desktop's REAL READY-sentinel parser. Imports apps/desktop/electron/backend-ready.ts itself (Node >= 22.18 strips the types natively) and drives `waitForDashboardPort` with a child-shaped… |
| `core/parity/fixture_mcp_server.py` | Tiny stdio MCP server used by the entrypoint-parity suite. |
| `core/parity/test_boot_contract.py` | Backend boot handshake contract, Python side (issue class C5). |
| `core/parity/test_entrypoint_parity.py` | Entrypoint parity matrix (issue classes C19 + C15). |
| `core/parity/test_mcp_lifecycle.py` | MCP server lifecycle on the long-lived host (issue class C15). |
| `core/platforms/__init__.py` | Package marker / package-level exports |
| `core/platforms/_contract.py` | The messaging-adapter contract: scenarios every real adapter must pass through a real gateway. |
| `core/platforms/_drv_discord.py` | Discord driver for the adapter contract: binds the shared contract to ``DiscordStandin``. |
| `core/platforms/_drv_slack.py` | Slack driver for the adapter contract: binds the shared contract to ``SlackStandin``. |
| `core/platforms/_drv_telegram.py` | Telegram driver for the adapter contract: binds the shared contract to ``TelegramStandin``. |
| `core/platforms/_helpers.py` | Harness for the messaging-adapter contract suite. |
| `core/platforms/_suite.py` | Binds the shared contract (``_contract.py``) to one adapter driver for a test module. |
| `core/platforms/test_discord_contract.py` | Messaging-adapter contract, Discord leg: the REAL gateway + REAL ``plugins/platforms/discord`` adapter. |
| `core/platforms/test_discord_thread_rename_ordering.py` | Real SDK dispatch must preserve moderator names before cached callbacks run. |
| `core/platforms/test_slack_contract.py` | Messaging-adapter contract, Slack leg: the REAL gateway + REAL ``plugins/platforms/slack`` adapter. |
| `core/platforms/test_telegram_contract.py` | Messaging-adapter contract, Telegram leg: the REAL gateway + REAL ``plugins/platforms/telegram`` adapter. |
| `core/providers/__init__.py` | Package marker / package-level exports |
| `core/providers/_anthropic_helpers.py` | Hermetic rig for the Anthropic Messages wire-conformance E2E suite. |
| `core/providers/_catalog_helpers.py` | Shared harness for the provider-catalog E2E matrix. |
| `core/providers/_native_helpers.py` | Shared harness for the native-dialect provider wire suites (``test_native_*.py``). |
| `core/providers/_oauth_helpers.py` | Hermetic subprocess harness for the OAuth E2E tests (fake HOME, tagged tree). |
| `core/providers/_openai_helpers.py` | Shared harness for the OpenAI-dialect provider wire-conformance suite. |
| `core/providers/_openai_tui.py` | Minimal stdio JSON-RPC driver for a REAL ``python -m tui_gateway.entry`` process — the backend the Ink TUI and Desktop talk to (one long-lived agent across turns). |
| `core/providers/test_anthropic_compaction.py` | Anthropic Messages wire conformance: compaction in a session full of signed thinking. |
| `core/providers/test_anthropic_discovery_and_aliases.py` | Anthropic route plumbing: model discovery endpoint and OAuth wire tool-name aliases. |
| `core/providers/test_anthropic_errors.py` | Anthropic Messages wire conformance: documented error envelopes and stream faults. |
| `core/providers/test_anthropic_oracle.py` | The SDK-oracle fake itself: it must be able to fail. |
| `core/providers/test_anthropic_thinking_replay.py` | Anthropic Messages wire conformance: thinking signatures + tool pairing. |
| `core/providers/test_catalog_fallback.py` | fallback_providers across the discovered catalog: a dead provider falls through to the next. |
| `core/providers/test_catalog_listing.py` | Model listing and ``/model --provider`` switching per discovered provider. |
| `core/providers/test_catalog_matrix_0.py` | Provider-catalog matrix, shard 0/3: one real oneshot turn per discovered provider. |
| `core/providers/test_catalog_matrix_1.py` | Provider-catalog matrix, shard 1/3: one real oneshot turn per discovered provider. |
| `core/providers/test_catalog_matrix_2.py` | Provider-catalog matrix, shard 2/3: one real oneshot turn per discovered provider. |
| `core/providers/test_catalog_oauth.py` | Real-process E2E: OAuth / device-code providers against a loopback vendor. |
| `core/providers/test_chat_custom_endpoint.py` | Custom / Ollama-style chat-completions endpoints through REAL ``hermes -z`` processes. |
| `core/providers/test_chat_errors.py` | Chat-completions provider faults through REAL ``hermes -z`` processes. |
| `core/providers/test_chat_reasoning_variants.py` | Chat-completions reasoning dialects through REAL Hermes processes. |
| `core/providers/test_fallback_providers.py` | Provider fallback (``fallback_providers``) through REAL ``hermes -z`` processes. |
| `core/providers/test_native_acp_agent.py` | ACP agent wire conformance, part 1: the multi-call tool flow, resume, and the process lifecycle. |
| `core/providers/test_native_acp_agent_errors.py` | ACP agent wire conformance, part 2: ACP error responses and agent crashes. |
| `core/providers/test_native_acp_agent_streaming.py` | ACP agent wire conformance, part 3: a long deep-reasoning turn must stream progress while in flight. |
| `core/providers/test_native_bedrock_converse_faults.py` | Bedrock Converse / ConverseStream fault semantics through the real ``hermes chat -q`` CLI. |
| `core/providers/test_native_bedrock_converse_turns.py` | Bedrock Converse / ConverseStream wire conformance: tools, signed reasoning, resume, compaction. |
| `core/providers/test_native_codex_app_server.py` | codex_app_server wire conformance: real ``hermes chat -q`` against a fake ``codex app-server``. |
| `core/providers/test_native_codex_app_server_faults.py` | codex_app_server faults and approval edges: real ``hermes chat -q`` against a fake ``codex app-server``. |
| `core/providers/test_native_codex_app_server_tui.py` | codex_app_server on an interactive viewer: a real ``hermes --tui`` attached to the gateway. |
| `core/providers/test_native_gemini_compaction.py` | Gemini native wire conformance: auto-compaction inside a thought-signature session. |
| `core/providers/test_native_gemini_errors.py` | Gemini native wire conformance: documented errors, blocked candidates and a mid-stream drop. |
| `core/providers/test_native_gemini_schema.py` | Gemini native wire conformance: MCP tool schemas Google's parser rejects arrive sanitized. |
| `core/providers/test_native_gemini_tools.py` | Gemini native wire conformance: the tool loop and thought-signature replay across ``--resume``. |
| `core/providers/test_native_vertex_cli_background.py` | Vertex AI through the classic CLI's gateway path: ``/config`` and ``/bg`` (#134889 T6). |
| `core/providers/test_native_vertex_errors.py` | Vertex AI documented errors through the real CLI: retried per semantics or surfaced exactly once. |
| `core/providers/test_native_vertex_recovery.py` | Vertex AI recovery paths: compaction in a signed reasoning session, and a mid-stream drop. |
| `core/providers/test_native_vertex_tools.py` | Vertex AI wire conformance: OAuth minting, multi-turn tools, thought-signature replay after resume. |
| `core/providers/test_oauth_anthropic_refresh.py` | Anthropic OAuth access token expires mid-turn: one refresh, the turn completes, the rotation persists. |
| `core/providers/test_oauth_device_flow.py` | RFC 8628 device-code login: the real ``hermes auth add nous`` CLI against a fake portal. |
| `core/providers/test_oauth_shared_pool.py` | Two real ``hermes -z`` processes share one auth.json pool row and hit its expiry at the same moment. |
| `core/providers/test_openai_codex_pool.py` | Codex credential pool: a dead refresh grant retires only the rows tied to that grant. |
| `core/providers/test_openai_pricing.py` | Model-picker pricing for a config-defined twin of a priced aggregator (#120757). |
| `core/providers/test_openai_responses.py` | OpenAI Responses (Codex) wire conformance through REAL Hermes processes. |
| `core/security/__init__.py` | Package marker / package-level exports |
| `core/security/_helpers.py` | Shared harness for the security-boundary E2E suite. |
| `core/security/_redact.py` | Private harness for test_secret_redaction*.py: scenario table, scripted model, sink collection. |
| `core/security/_scope.py` | Private harness for ``test_profile_secret_scope.py``: one real ``hermes serve`` hosting two profiles, a user dashboard plugin whose API route reads a credential through ``get_secret``, and a stdio MCP server per profile… |
| `core/security/_traversal.py` | Private harness for the traversal sub-lane (store traversal + workspace escape). |
| `core/security/test_approval_boundary.py` | Dangerous terminal commands need a human's approval — through the REAL terminal tool path. |
| `core/security/test_attach_handshake.py` | Session-attach handshake: ``hermes --tui --resume SID`` must hand the TUI only the REAL owner's socket. |
| `core/security/test_profile_secret_scope.py` | Per-profile secret scope on ONE multi-profile ``hermes serve`` host. |
| `core/security/test_secret_redaction.py` | Secrets never reach disk or the next provider request through the classic CLI (``hermes chat -q``). |
| `core/security/test_secret_redaction_gateway.py` | Secrets never reach disk, the platform, or the next provider request through the messaging gateway. |
| `core/security/test_store_traversal.py` | Write-approval pending store and skill-delete guards hold against path-shaped names. |
| `core/security/test_workspace_escape.py` | File tools keep the documented write sandbox, write denylist and read denylist under ../ and symlink spellings. |
| `core/sqlite/__init__.py` | Package marker / package-level exports |
| `core/sqlite/_helpers.py` | Harness for the multi-process SQLite torture chamber (issue class C1: state.db integrity). |
| `core/sqlite/_roles.py` | Child-process roles for the SQLite torture chamber. |
| `core/sqlite/test_compaction_contention.py` | Compaction persistence under multi-process contention (issue class C1, "state.db corrupting from compaction"). |
| `core/sqlite/test_torture_chamber.py` | SQLite torture chamber: state.db integrity under real multi-process load (issue class C1). |
| `core/tenancy/__init__.py` | Package marker / package-level exports |
| `core/tenancy/_helpers.py` | Lane-private harness for the C7 two-tenant canary suites. |
| `core/tenancy/_routing_helpers.py` | Lane-private harness for the C11 routing truth table. |
| `core/tenancy/test_routing_truth_table.py` | C11 routing truth table: every config shape users write routes the prompt AND the key to exactly one host. |
| `core/tenancy/test_two_tenant_desktop_backend.py` | C7 two-tenant canary: ONE Desktop backend (``hermes serve``) serving three profiles over /api/ws. |
| `core/tenancy/test_two_tenant_gateway.py` | C7 two-tenant canary: ONE multiplexed messaging gateway serving three profiles. |
| `core/terminal/__init__.py` | Package marker / package-level exports |
| `core/terminal/_gateway_client.py` | Real ``hermes serve`` backend + WebSocket JSON-RPC clients for the terminal lane E2E suites. |
| `core/terminal/_pty.py` | Drive a real ``hermes`` CLI / Ink TUI process under a real PTY, rendered through :mod:`._vt`. |
| `core/terminal/_vt.py` | A small, dependency-free VT100/xterm screen emulator for PTY transcript assertions. |
| `core/terminal/test_interactive_roundtrip.py` | C20 — interactive prompts (clarify / dangerous-command approval) round-trip over the REAL backend. |
| `core/terminal/test_multiclient_session_model.py` | C14 — multi-client session ownership, routing and switching over the REAL backend. |
| `core/terminal/test_terminal_transcript_pty.py` | C2 on terminal surfaces: what the classic CLI and the Ink TUI finally show is the transcript, exactly once, unmangled, and matches what was persisted. |
| `core/tui_pty/__init__.py` | Package marker / package-level exports |
| `core/tui_pty/_helpers.py` | Drive a real ``hermes --tui`` inside a private tmux server and read what the user would see. |
| `core/tui_pty/test_modals_resize.py` | Blocking modals and streaming tool output in the Ink TUI survive terminal resizes: the clarify and approval cards stay on screen exactly once while the window is resized, the answer given after the resize reaches the to… |
| `core/tui_pty/test_resize_ledger.py` | The Ink TUI keeps every transcript word exactly once, in order, through terminal resizes — idle and mid-stream, shrinking, growing and dragging — and its content width follows the terminal (#96372 history cleared on res… |
| `core/tui_pty/test_resume_compress.py` | A long Ink TUI session renders every transcript word at most once after ``/compress`` and when it is resumed later (``hermes --tui --resume <id>`` and ``/resume <id>`` from a fresh TUI): a compressed-transcript block is… |
| `core/tui_pty/test_wide_chars_interrupt.py` | Wide characters and Ctrl+C in the Ink TUI keep the transcript consistent. |
| `core/upgrade/__init__.py` | Package marker / package-level exports |
| `core/upgrade/_helpers.py` | Lane-private helpers for the upgrade / install-integrity and config round-trip suites. |
| `core/upgrade/_install_helpers.py` | Helpers for the fresh-install / update-with-user-state / profile-update suites. |
| `core/upgrade/git/__init__.py` | Package marker / package-level exports |
| `core/upgrade/git/_git_world.py` | A real install served over real smart HTTP, and the real ``hermes update`` against it. |
| `core/upgrade/git/_smart_http.py` | A real git smart-HTTP origin on loopback, with faults the test arms on command. |
| `core/upgrade/git/test_foreign_state.py` | Concurrent and foreign git state in the install, through a real ``hermes update``. |
| `core/upgrade/git/test_hostile_commit.py` | The source swap of ``hermes update`` is one crash-safe commit point (lane LP-COMMIT). |
| `core/upgrade/git/test_hostile_lock.py` | Hostile-concurrency cells for the update lock, with real ``hermes update`` processes. |
| `core/upgrade/git/test_hostile_pause.py` | Linux/macOS ``hermes update`` pauses this install's gateways before the first checkout move. |
| `core/upgrade/git/test_hostile_post.py` | Once ``hermes update`` has committed the new code, the update never fails (contract C3). |
| `core/upgrade/git/test_local_modifications.py` | Local modifications through a real ``hermes update``: tracked edits, untracked files, local commits. |
| `core/upgrade/git/test_partial_clone.py` | Partial and full clones updated N-1 -> HEAD -> next release through the real ``hermes update``. |
| `core/upgrade/git/test_shallow_install.py` | Shallow and stale installs through the real ``hermes update``. |
| `core/upgrade/git/test_truthful_outcome.py` | Truthful outcome of ``hermes update`` when the git transport fails. |
| `core/upgrade/handoff/__init__.py` | Package marker / package-level exports |
| `core/upgrade/handoff/_handoff.py` | Staging for the hand-off suite: a real install at release N-1 (or HEAD), processes running from it, and the real ``hermes update`` to the next commit, all in one shared PID namespace. |
| `core/upgrade/handoff/_ns_agent.py` | In-sandbox command agent for the hand-off suite (stdlib only, run as a plain script). |
| `core/upgrade/handoff/_nshost.py` | Host side of the shared-PID-namespace sandbox (see ``_ns_agent.py``). |
| `core/upgrade/handoff/_scenario.py` | One user's machine across one real ``hermes update``, observed once per column. |
| `core/upgrade/handoff/conftest.py` | Fixtures for the hand-off suite. |
| `core/upgrade/handoff/test_handoff_from_head.py` | The hand-off suite, HEAD to NEXT. |
| `core/upgrade/handoff/test_handoff_from_n1.py` | The hand-off suite, release N-1 to HEAD. |
| `core/upgrade/handoff/test_update_network_failure.py` | A network failure during ``hermes update`` must never take down a healthy gateway (the exit-75 class, #123370: keep it closed). |
| `core/upgrade/hosts/__init__.py` | Package marker / package-level exports |
| `core/upgrade/hosts/_hosts.py` | Shared staging for the host-shape suites (odd paths, PATH shapes, permissions, libc). |
| `core/upgrade/hosts/test_hostile_pause_record.py` | The paused-gateway record survives an update that runs under a partner's claim. |
| `core/upgrade/hosts/test_libc_musl.py` | Install on a musl libc host (Alpine) through the real ``scripts/install.sh``. |
| `core/upgrade/hosts/test_path_shapes.py` | Install and run on hosts whose PATH and shell startup files are not a fresh skeleton. |
| `core/upgrade/hosts/test_paths.py` | Install, update, gateway and a turn in a home whose path has spaces and non-ASCII bytes. |
| `core/upgrade/hosts/test_paths_symlinked.py` | Launches through a symlinked ``~/.hermes`` and a per-task home that links back to it. |
| `core/upgrade/hosts/test_permissions.py` | Install trees the running user cannot write: turns keep working, updates fail and say why. |
| `core/upgrade/network/__init__.py` | Package marker / package-level exports |
| `core/upgrade/network/_netedge.py` | The network edge for the hostile-network suites: every byte a sandboxed install/update sends leaves through something this module owns. |
| `core/upgrade/network/_nsbridge.py` | First process inside the sandbox's private network namespace (run with ``python -I``). |
| `core/upgrade/network/_seed.py` | One real install per module, then every cell runs inside a private network namespace. |
| `core/upgrade/network/test_mirrors.py` | Package mirrors: with a pip index mirror and an npm registry configured, nothing contacts the public indexes, and the locked install paths accept the mirror. |
| `core/upgrade/network/test_offline_and_flaky.py` | Offline and flaky networks: fail fast, loud and truthfully, or retry within bounds. |
| `core/upgrade/network/test_proxy_only_egress.py` | Proxy-only egress: ``hermes update`` on a network whose ONLY way out is an HTTP(S) proxy. |
| `core/upgrade/network/test_release_channel_records.py` | Stable releases: the updater follows the latest published GitHub release exactly, or refuses. |
| `core/upgrade/pm/__init__.py` | Package marker / package-level exports |
| `core/upgrade/pm/_pm.py` | Shared staging for the PM lifecycle suite (``tests/e2e/core/upgrade/pm``). |
| `core/upgrade/pm/test_configured_features.py` | Configured features survive every dependency rebuild (PM lifecycle, failure class 1). |
| `core/upgrade/pm/test_gateway_install_force.py` | The PM runtime lock is where PM commands look for it (PM lifecycle, class 6; #124075). |
| `core/upgrade/pm/test_generation_gc.py` | Repeated updates and repairs don't grow the install without bound (PM lifecycle, failure class 5; #123340). |
| `core/upgrade/pm/test_interpreter_hygiene.py` | Interpreter hygiene after an update (PM lifecycle, failure class 4). |
| `core/upgrade/pm/test_interrupted_update.py` | Interrupted dependency updates recover (PM lifecycle, failure class 2). |
| `core/upgrade/pm/test_restart_generations.py` | Restarts never build or accumulate dependency generations (PM lifecycle, failure class 5; #123340). |
| `core/upgrade/pm/test_stamps_and_doctor.py` | Stamps, receipts and doctor tell the truth about a PM install (PM lifecycle, failure class 3). |
| `core/upgrade/test_config_roundtrip_properties.py` | C18 — config and settings persistence round-trip properties. |
| `core/upgrade/test_fresh_process_entrypoints.py` | C6: every shipped module and every entrypoint works in a FRESH process after an update. |
| `core/upgrade/test_install_fresh.py` | Fresh install through the real `scripts/install.sh` into an empty HOME, then a re-run. |
| `core/upgrade/test_profile_update_cron.py` | `hermes profile install` / `hermes profile update` against a real distribution with cron jobs. |
| `core/upgrade/test_update_userstate_import.py` | `hermes import` of a broken backup archive must report failure, never "restored". |
| `core/upgrade/test_update_userstate_realistic.py` | `hermes update` on a realistic user home: everything the user owns survives, sessions resume. |
| `core/upgrade/test_upgrade_path.py` | Upgrade-path E2E: a real release N-1 git install updated to HEAD by the real `hermes update`. |
| `core/windows/__init__.py` | Package marker / package-level exports |
| `core/windows/_helpers.py` | Shared harness for the native-Windows end-to-end suite. |
| `core/windows/_rpc.py` | Minimal stdio JSON-RPC client for ``python -m tui_gateway.entry`` — the process the Ink TUI spawns on every OS. Frames are UTF-8 JSON lines with non-ASCII left literal, exactly what Node's ``JSON.stringify`` + ``stdin.w… |
| `core/windows/conftest.py` | Windows lane teardown: a prompt auto-starts the profile's gateway, which outlives the turn. |
| `core/windows/test_boot_lifecycle.py` | Boot and lifecycle of the real Hermes processes on native Windows. |
| `core/windows/test_cron_scripts.py` | Cron script jobs on native Windows (``hermes cron create --script`` + ``hermes cron run``). |
| `core/windows/test_prompt_paths.py` | Prompt assembly with native Windows paths, through real Hermes processes. |
| `core/windows/test_state_db_guard.py` | The state.db write-guard sees a live foreign holder on native Windows. |
| `core/windows/test_terminal_tool.py` | The real terminal tool on native Windows, driven by a model turn through ``hermes chat -q``. |
| `core/windows/test_unicode_input.py` | Non-ASCII / emoji user input on native Windows reaches the model intact. |
| `core/windows_update/__init__.py` | Package marker / package-level exports |
| `core/windows_update/_machine.py` | A fresh Windows machine for the PR-time install.ps1 -> ``hermes update`` suite. |
| `core/windows_update/_tokens.py` | Standard-user tokens for the Windows install/update journeys (the runner session is elevated). |
| `core/windows_update/test_crash_cells.py` | ``hermes update`` killed mid-flight on native Windows, then the user's next launch. |
| `core/windows_update/test_damaged_checkout.py` | A checkout whose ``.git`` git rejects, on native Windows. |
| `core/windows_update/test_elevated_gateway_attach.py` | A standard-user client dialing an elevated gateway's control pipe (#140706, #134889 W9). |
| `core/windows_update/test_fresh_install_update.py` | Fresh source install on native Windows, then ``hermes update`` HEAD -> NEXT. |
| `core/windows_update/test_gateway_across_update.py` | A running gateway across ``hermes update`` on native Windows. |
| `core/windows_update/test_git_and_holders.py` | Git and process-holder edges of ``hermes update`` on native Windows. |
| `core/windows_update/test_interpreter.py` | Which site-packages a Windows gateway and CLI load after an update. |
| `core/windows_update/test_paths_and_acls.py` | A Windows user profile path with non-ASCII characters and a space, and tool ACLs. |
| `core/windows_update/test_pause_custody.py` | Restart debt survives every custody transfer of a Windows update pause (review R7). |
| `core/windows_update/test_pause_durable.py` | A killed or failed ``hermes update`` never strands — or wrongly starts — a paused gateway. |
| `core/windows_update/test_update_lock_tree.py` | One ``hermes update`` owns an installed checkout on native Windows, and its whole tree. |
| `core/windows_update/test_update_spares_other_installs.py` | Two Hermes installs on one Windows host: one install's ``hermes update`` leaves the other's gateway alone (#124659). |
| `core/windows_update/test_upgrade_over_old_gateway.py` | Upgrading a real pre-#106742 install over its running gateway, elevated and not (#134889 W4). |
| `test_discord_adapter.py` | Minimal e2e tests for Discord mention stripping + /command detection. |
| `test_platform_commands.py` | E2E tests for gateway slash commands (Telegram, Discord). |
| `test_relay_native_anthropic_stream.py` | Native Anthropic SDK streaming through Relay's managed execution path. |
| `test_relay_native_openai_stream.py` | Native OpenAI SDK streaming through Relay's managed execution path. |

## `tests/evals/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `test_codebase_navigability.py` | Guardrail for the navigability eval: its symbol resolver must follow the facade/sibling layout. |
| `test_compaction_jev_arm.py` | Invariants of the fast-jev-compaction eval arm (evals/compaction/jev_arm.py). |
| `test_core_tool_deferral_sandbox.py` | The core-tool-deferral worker's host sandbox (evals/core_tool_deferral/sandbox.py). |

## `tests/fakes/`

| File | What it does |
|---|---|
| `cron_owner.py` | A real profile gateway authority that admits cron fires without running an agent turn. |
| `fake_llm_provider.py` | Scripted, recording loopback LLM provider for end-to-end tests. |
| `platforms/__init__.py` | Package marker / package-level exports |
| `platforms/_standin.py` | Shared plumbing for local stand-in messaging platform servers. |
| `platforms/discord_shim/sitecustomize.py` | Point discord.py at a local Discord stand-in (tests only). |
| `platforms/discord_standin.py` | Discord stand-in: REST API v10 + Gateway websocket (https://discord.com/developers/docs). |
| `platforms/slack_shim/sitecustomize.py` | Point slack_sdk (and raw ``https://slack.com/api/`` aiohttp posts) at a local Slack stand-in. |
| `platforms/slack_standin.py` | Slack Web API + Socket Mode stand-in (https://api.slack.com/methods, /apis/socket-mode). |
| `platforms/telegram_standin.py` | Telegram Bot API stand-in (https://core.telegram.org/bots/api). |
| `providers/__init__.py` | Package marker / package-level exports |
| `providers/anthropic_messages.py` | Scripted, recording loopback server speaking the Anthropic Messages API. |
| `providers/bedrock_converse.py` | Loopback fake of the AWS Bedrock Runtime Converse / ConverseStream API. |
| `providers/catalog_fake.py` | Multi-dialect recording loopback provider for the provider-catalog E2E matrix. |
| `providers/catalog_oauth.py` | Loopback OAuth authorization server + bearer-checking inference server for the OAuth E2E cells. |
| `providers/chat_variants.py` | Scripted, recording loopback server for OpenAI **chat-completions** dialect variants. |
| `providers/codex_app_server.py` | Fake ``codex app-server``: newline-delimited JSON-RPC over stdio, validated against the protocol. |
| `providers/fake_acp_agent.py` | Fake ACP agent executable for an ``external_process`` model provider (``agent.acp_client.ACPClient``). |
| `providers/gemini_native.py` | Fake Google AI Studio ``generateContent`` / ``streamGenerateContent`` endpoint behind a real TLS boundary. |
| `providers/oauth_token_server.py` | Recording loopback OAuth 2.0 authorization server for end-to-end tests. |
| `providers/openai_responses.py` | Scripted, recording loopback server for the OpenAI **Responses** wire dialect. |
| `providers/vertex.py` | Loopback fake of Google Vertex AI (Gemini behind the OpenAI-compatible endpoint) + Google OAuth. |
| `redactor_plugin.py` | A redaction plugin for ``transform_llm_output`` stream-hold tests. |

## `tests/fixtures/`

| File | What it does |
|---|---|
| `cua_driver_0_9_tools_list.json` | JSON object with keys `format`, `contract_epoch`, `observed_reported_version`, `capability_version`, `observed_tool_count`, `tools` |
| `identifier_speech_corpus.json` | Identifier-dense tokens both speech normalizers must agree on (#119207). Unspeakable machine tokens become silence — never hardcoded English placeholder words (#86602). identifier_tokens: [text, mustNotContain[], mustCo… |
| `legacy_desktop/update-marker-be3fd671.mts` | The update-marker reader a packaged Desktop shipped at be3fd671d70 (apps/desktop/electron/update-marker.ts lines 1-160, verbatim): the old reader new hand-off scripts must keep parked. Never edit it. |
| `plugin_component_detection.json` | JSON object with keys `schema`, `doc`, `cases` |
| `plugins/example-dashboard/dashboard/manifest.json` | `example` — Test-only dashboard plugin fixture — installed by tests that need a stable plugin API endpoint to verify auth + static-asset behaviour |
| `plugins/example-dashboard/dashboard/plugin_api.py` | Example dashboard plugin — backend API routes (test fixture). |
| `prompt_surface/prompts/cli-code.claude.txt` | Plain-text file |
| `prompt_surface/prompts/cli.claude.txt` | Plain-text file |
| `prompt_surface/prompts/cli.gemini.txt` | Plain-text file |
| `prompt_surface/prompts/cli.gpt.txt` | Plain-text file |
| `prompt_surface/prompts/cli.hermes.txt` | Plain-text file |
| `prompt_surface/prompts/cron.claude.txt` | Plain-text file |
| `prompt_surface/prompts/desktop.claude.txt` | Plain-text file |
| `prompt_surface/prompts/discord.claude.txt` | Plain-text file |
| `prompt_surface/prompts/telegram.claude.txt` | Plain-text file |
| `prompt_surface/surfaces.json` | JSON object with keys `cli-code.claude`, `cli.claude`, `cli.gemini`, `cli.gpt`, `cli.hermes`, `cron.claude` |
| `prompt_surface/tools/browser_cdp.json` | `browser_cdp` — Send a raw Chrome DevTools Protocol (CDP) command. Escape hatch for browser operations the other browser tools don't cover. **Requires a reachable CDP endpoint.** Available when the user has run '/browse… |
| `prompt_surface/tools/browser_dialog.json` | `browser_dialog` — Accept or dismiss a native JS dialog (alert/confirm/prompt) blocking the page. **Workflow:** when a page is blocked by a native dialog the CDP supervisor captured, call this tool with ``action='accept… |
| `prompt_surface/tools/browser_exec.json` | `browser_exec` — Drive a real browser for JS pages, logins, forms and clicks (Browser Use CLI). `code` runs as full Python (stdlib available) with pre-imported browser helpers; stdout comes back in the result. Start `co… |
| `prompt_surface/tools/clarify.json` | `clarify` — Ask the user one or more questions when you need a decision or feedback. Pass every question in `questions` (1-5 entries) — a single question is a one-entry array, and several INDEPENDENT questions belong in… |
| `prompt_surface/tools/delegate_task.json` | `delegate_task` — Spawn isolated subagents for parallel or context-heavy work. Each gets its own conversation, terminal session, and toolset, and only its final summary returns to you. Pass every task in `tasks` — one e… |
| `prompt_surface/tools/execute_code.json` | `execute_code` — Run Python that calls Hermes tools programmatically. Use when you need 3+ tool calls with logic between them: filtering/reducing large outputs before they enter context, branching, or loops (N pages/fil… |
| `prompt_surface/tools/manage_connections.json` | `manage_connections` — Connect the user to apps. Two kinds: a hosted connector account (Gmail, Notion, ...) served through the tool gateway, and a local MCP server from the bundled catalog. Targets go in 'connectors': a… |
| `prompt_surface/tools/memory.json` | `memory` — Save durable facts to persistent memory that survive across sessions. Memory is injected into every future turn, so keep entries compact and high-signal. HOW: make ALL your changes to one target in ONE call v… |
| `prompt_surface/tools/patch.cli.gpt.json` | `patch` — Targeted find-and-replace edits in files. Use this instead of sed/awk in terminal. Uses fuzzy matching (9 strategies) so minor whitespace/indentation differences won't break it. Returns a unified diff. Auto-ru… |
| `prompt_surface/tools/patch.json` | `patch` — Targeted find-and-replace edits in files. Use this instead of sed/awk in terminal. Uses fuzzy matching (9 strategies) so minor whitespace/indentation differences won't break it. Returns a unified diff. Auto-ru… |
| `prompt_surface/tools/react_to_message.json` | `react_to_message` — React to a message with a single emoji, the way you'd tapback in iMessage. Reach for it when a reaction is what a person would do: something funny gets a 😂, warmth gets a ❤️, a plan you're on board… |
| `prompt_surface/tools/read_file.json` | `read_file` — Read a text file with line numbers and pagination. Use this instead of cat/head/tail in terminal. Output format: 'LINE_NUM\|CONTENT'. Suggests similar filenames if not found. Use offset and limit for large… |
| `prompt_surface/tools/search_files.json` | `search_files` — Search file contents or find files by name. Use this instead of grep/rg/find/ls in terminal. Ripgrep-backed, faster than shell equivalents. Content search (target='content'): Regex search inside files.… |
| `prompt_surface/tools/skill_manage.json` | `skill_manage` — Create, update or delete skills: your procedural memory for recurring tasks. The call is an operations array (a single edit is a list of one); it applies atomically — any failure rolls every touched ski… |
| `prompt_surface/tools/skill_view.json` | `skill_view` — Load a skill's SKILL.md, or one of its linked references, templates or scripts. The first call returns SKILL.md plus a 'linked_files' dict; call again with file_path to read one. |
| `prompt_surface/tools/skills_list.json` | `skills_list` — List available skills (name + description). Use skill_view(name) to load full content. |
| `prompt_surface/tools/terminal.json` | `terminal` — Run shell commands on the OS/shell/backend named in your environment section. The working directory, files and exported variables persist between calls: activate a virtualenv or export once, not before ever… |
| `prompt_surface/tools/text_to_speech.json` | `text_to_speech` — Convert text to speech audio. Returns a MEDIA: path that the platform delivers as native audio. Compatible providers render as a voice bubble on Telegram; otherwise audio is sent as a regular attachme… |
| `prompt_surface/tools/tool_call.json` | `tool_call` — Invoke deferred tools: `calls` is an array of {name, arguments}, one entry per invocation (batch independent calls; results come back in order). Arguments match the schema from `tool_describe`; approvals a… |
| `prompt_surface/tools/tool_describe.json` | `tool_describe` — Load the full JSON schemas for tools returned by `tool_search`. Required before `tool_call` if a tool's parameters are unknown. Batch every schema you need into one call. |
| `prompt_surface/tools/tool_search.desktop.claude.json` | `tool_search` — Search 19 additional tools that are loaded on demand. Send one keyword query per capability you need; returns matching tool names and descriptions. Then `tool_describe` loads schemas and `tool_call` invo… |
| `prompt_surface/tools/tool_search.json` | `tool_search` — Search 7 additional tools that are loaded on demand. Send one keyword query per capability you need; returns matching tool names and descriptions. Then `tool_describe` loads schemas and `tool_call` invok… |
| `prompt_surface/tools/vision_analyze.json` | `vision_analyze` — Load an image into the conversation so you can see it. Call it any time the user references an image — then answer from what you see. |
| `prompt_surface/tools/web_extract.json` | `web_extract` — Extract content from web page URLs. Returns clean page content in markdown/text (no LLM summarization — fast). Also works with PDF URLs (arxiv papers, documents) — pass the PDF link directly. Pages withi… |
| `prompt_surface/tools/web_search.json` | `web_search` — Search the web: returns titles, URLs and snippets (5 by default). Read pages with web_extract. The query is passed through to the configured backend, so operators such as site:domain, filetype:pdf, intitl… |
| `prompt_surface/tools/write_file.json` | `write_file` — Write content to a file, completely replacing existing content. Use this instead of echo/cat heredoc in terminal. Creates parent directories automatically. OVERWRITES the entire file — use 'patch' for tar… |
| `provider_wire_snapshot.json` | JSON data/configuration |
| `resolution_allowlist.json` | JSON list (131 entries) |
| `room_link_protocol_v2.json` | JSON object with keys `protocol_version`, `catalog` |
| `session-resume-active-turn.json` | JSON object with keys `info`, `inflight`, `message_count`, `messages`, `messages_omitted`, `resumed` |
| `spark_failing_turn_shape.json` | JSON list (9 entries) |
| `update_marker_corpus.json` | JSON object with keys `schema`, `contract`, `now`, `own_ct_epsilon`, `ct_tolerance`, `v1_max_age` |

## `tests/gateway/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `_plugin_adapter_loader.py` | Shared helper for loading platform-plugin ``adapter.py`` modules in tests. |
| `conftest.py` | Shared fixtures for gateway tests. |
| `feishu_helpers.py` | Shared fixtures for Feishu adapter tests (admission, group policy, dispatch). |
| `fixtures/agent_persistence_worker.py` | Real AIAgent in a separate interpreter, using only the worker transport. |
| `fixtures/ancillary_reads_peer.py` | Authenticated TCP fixture with owner-seeded state; no external inference. |
| `fixtures/api_authority_peer.py` | Real HTTP/WS API execution probe with a loopback inference peer. |
| `fixtures/api_daemon_witness.py` | Observe real agent identities without replacing daemon boot or execution. |
| `fixtures/api_recovery_daemon.py` | Hold only execution scheduling after a real API commit and HTTP ACK. |
| `fixtures/api_usage_peer.py` | Loopback peer with explicit SSE usage for per-admission accounting probes. |
| `fixtures/authority_clarify_lock_peer.py` | #140400 end to end: a `hermes chat`-shaped turn's clarify batch answered from a second viewer. |
| `fixtures/authority_clarify_peer.py` | Owned loopback model, real clarify tool, native card, two authenticated sockets. |
| `fixtures/authority_controls_peer.py` | Disposable real approval worker, loopback model, authenticated WS clients. |
| `fixtures/authority_events_peer.py` | Real authority execution with an OS-full observer and independent reader. |
| `fixtures/authority_stream_peer.py` | Real SSE execution and authenticated authority observers in a disposable process. |
| `fixtures/automation_peer.py` | Ordinary daemon, real terminal child, loopback-only relay/provider peers. |
| `fixtures/bot_authority_peer.py` | Authenticated production WebSockets and loopback-only inference. |
| `fixtures/browser_scope_peer.py` | Authenticated WS fixture: browser.manage actions on the shared owner, scoped to the session's profile (CLI-9); no inference, no browser. |
| `fixtures/cli_launch_policy_probe.py` | Ordinary daemon + concurrent classic CLI, loopback-only launch receipts. |
| `fixtures/cli_plugin_free_startup.py` | The classic CLI's real startup and command dispatch, in a fresh process, recording every plugin discovery / execution entry point it reaches (#134889 PLG-7). |
| `fixtures/compression_persistence_worker.py` | Registered worker invokes real AIAgent compression over an ordinary daemon. |
| `fixtures/config_policy_recovery_probe.py` | Unmodified daemon/config-source restart over actual loopback inference. |
| `fixtures/control_boundaries.py` | Defines `exercise_control_boundaries` |
| `fixtures/desktop_process_verbs_peer.py` | Authenticated WS fixture: Desktop's exact process/MCP frames on the shared owner; no inference. |
| `fixtures/estop_interactive_peer.py` | GW-1 fixture: `hermes pause` holds every gateway turn, including interactive (TUI/Desktop/CLI) ones. |
| `fixtures/execution_frames_capture.py` | Capture real ``SessionEvents.publish`` frames for the Desktop execution-authority fence tests. |
| `fixtures/hosted_auth_probe.py` | Loopback OIDC/model boundaries; daemon, auth, tickets and room controls are real. |
| `fixtures/kanban_owner_probe.py` | Actual dispatcher argv, ordinary daemon, loopback tool round, disposable board. |
| `fixtures/kanban_recovery_probe.py` | Disposable ordinary owner, actual dispatcher, custom paths and process death. |
| `fixtures/ledger_tool_worker.py` | Real registered worker with the production terminal tool enabled. |
| `fixtures/legacy_bot_mailbox.py` | Executed with the pre-authority checkout on PYTHONPATH, not the new writer. |
| `fixtures/legacy_migration_probe.py` | Actual classic CLI persistence followed by native owner migration (loopback). |
| `fixtures/lifecycle_persistence_worker.py` | Lifecycle extension of the existing separate-interpreter worker fixture. |
| `fixtures/local_automation_daemon.py` | Crash barrier after real automation commit, before producer ACK/first claim. |
| `fixtures/local_automation_peer.py` | Ordinary daemon + local authenticated clients + actual terminal completion. |
| `fixtures/local_lineage_daemon.py` | Pause only after real rotation/reset publication and durable queued admission. |
| `fixtures/local_lineage_probe.py` | Separate ordinary daemon restarts after the production physical-target handoff. |
| `fixtures/local_recovery_daemon.py` | Test-only committed-before-schedule crash barrier around the ordinary daemon. |
| `fixtures/local_recovery_probe.py` | Real daemon restart driver; model and preclaim crash barriers are owned fixtures. |
| `fixtures/local_session_peer.py` | Owned loopback fixture: no native credentials or alternative agent runtime. |
| `fixtures/local_status_notice_peer.py` | Real owner, real AIAgent turn, authenticated local WS viewer: agent status and notices. |
| `fixtures/native_ingress_media_peer.py` | Owned temp-profile native admission/recovery with real loopback inference. |
| `fixtures/native_ingress_trust_multiplex.py` | Opposing transport/runtime policy and restart controls, no vendor credentials. |
| `fixtures/native_ingress_trust_peer.py` | Real native callback/runner/SQLite probe in an owned interpreter. |
| `fixtures/native_reply_crash_daemon.py` | Test-only crash barriers around a native reply's terminal commit; every recovery boot is ordinary. |
| `fixtures/native_role_fences.py` | Owned await-race and fresh-interpreter retention controls. |
| `fixtures/native_role_peer.py` | Owned Discord SDK peer + actual public adapter/TurnRunner/HTTP execution. |
| `fixtures/native_telegram_recovery_daemon.py` | First-owner-only scheduler barrier; every recovery boot is ordinary. |
| `fixtures/operator_cross_surface_peer.py` | Disposable gateway; only the IdP and loopback model wire are synthetic. |
| `fixtures/owner_process.py` | A real gateway owner (``python -m gateway.run``) in a throwaway home, for tests that dial it. |
| `fixtures/persistence_worker.py` | Owned inert tool witness. Commands arrive through a private test pipe. |
| `fixtures/plugin_mcp_daemon.py` | Test-only: the ordinary daemon with a fake MCP server in its own registry (no MCP SDK, no network). |
| `fixtures/process_scope_peer.py` | Authenticated WS fixture: process-global sidecar verbs on the shared owner; no inference. |
| `fixtures/replay_gap_owner.py` | A real owner (SessionAuthority, AuthorityConnection, FanoutTransport overflow, the drain's publish sequence) for one session ``s`` and one viewer whose socket stops reading while paused (Ctrl-Z). #140292 raised the fram… |
| `fixtures/rotation_persistence_worker.py` | Registered worker invokes real AIAgent compression over an ordinary daemon. |
| `fixtures/session_policy_peer.py` | Real concurrent source/model/tool/cwd launch proof; no external provider. |
| `fixtures/shared_authority_peer.py` | Disposable production-runtime peer; only provider and vendor wire are synthetic. |
| `fixtures/shared_authority_recovery.py` | Crash/restart scenarios for the existing real shared-authority peer. |
| `fixtures/shell_exec_peer.py` | Authenticated WS fixture: Ink ``!cmd`` on the shared owner; no inference. |
| `fixtures/stack_dump_daemon.py` | Ordinary daemon plus delayed diagnostics (native-runner readiness stalls only). |
| `fixtures/staged_file_attach_peer.py` | Authenticated WS fixture: a browser pick's ``staged_upload`` receipt attached on the shared owner. |
| `fixtures/subagent_controls_peer.py` | Authenticated owner fixture: Desktop's per-child Steer/Stop reach only this session's children. |
| `fixtures/terminal_commit_daemon.py` | Stop the actual owner after the result commit, before any publication. |
| `fixtures/trampoline_daemon.py` | Test-only: the daemon believes its interpreter is a launcher trampoline. |
| `fixtures/tui_desktop_routes_peer.py` | Authenticated TCP fixture for the Ink/Desktop verbs the owner serves itself; no inference. |
| `fixtures/webapp_fallback_peer.py` | Start the gateway's listener the way the runtime does and report what native clients and a browser get. |
| `fixtures/webapp_gated_sign_out_peer.py` | A real gateway serving the Webapp behind the sign-in gate; a browser signs in, then the owner signs out. |
| `fixtures/webapp_listener_peer.py` | Start the gateway listener with the Webapp on or off; report what a browser and a native client get. |
| `fixtures/webhook_route_authority.py` | Real durable admission for route tests; only execution is held at scheduling. |
| `platforms/__init__.py` | Package marker / package-level exports |
| `platforms/test_yuanbao_recall_db_only.py` | Yuanbao recall: branch A1 (exact id) and A2 (content-match) against DB-only transcripts. |
| `platforms/test_yuanbao_state_cleanup.py` | Yuanbao per-turn state cleanup: RecallGuard tracking dicts + member cache TTL. |
| `relay/__init__.py` | Package marker / package-level exports |
| `relay/stub_connector.py` | Test-only in-memory stub connector implementing RelayTransport. |
| `relay/test_auth.py` | Unit tests for gateway/relay/auth.py — the gateway-side relay auth primitives. |
| `relay/test_channel_context_consume.py` | Unit tests for relay channel-context consumption (design relay-channel-context). |
| `relay/test_cold_opt_out.py` | Standalone relay routing must not bootstrap the gateway or reload secrets. |
| `relay/test_descriptor.py` | Tests for the experimental CapabilityDescriptor (relay Phase 0, Task 0.2). |
| `relay/test_explicit_disable.py` | ``platforms.relay.enabled: false`` beats a deployment-injected relay URL. |
| `relay/test_handoff_relay_aliasing.py` | Unit tests for /handoff platform aliasing over relay (Phase 1 parity). |
| `relay/test_identity_token_resolver.py` | Unit tests for the generic-OIDC / Nous-Portal caller-identity token resolver. |
| `relay/test_live_cards_flow_trace.py` | Local integration trace: REAL StreamConsumer + REAL RelayAdapter + stub transport. Reproduces the multi-segment live-cards turn to reveal the exact op sequence the connector sees (finding #4/#5 forensics — Alice canary). |
| `relay/test_provision_secret_optional.py` | Lockstep contract with the connector's F-004 change (gateway-gateway #223). |
| `relay/test_relay_ack_ambiguity.py` | Regression: the transport's timeout-shaped RESULT is ambiguous, not a rejection (PR 85796 review round 2, finding 1). |
| `relay/test_relay_adapter.py` | RelayAdapter capability-advertisement tests (relay Phase 1, Task 1.1). |
| `relay/test_relay_attachment_filenames.py` | Relay attachments keep their original filenames for the agent. |
| `relay/test_relay_connector_profile_admission.py` | A connector-stamped ``source.profile`` is a route, on single-profile and multiplexed gateways. |
| `relay/test_relay_discord_interaction_labels.py` | A relayed Discord interaction carries the same chat/user labels as a relayed message in that chat. |
| `relay/test_relay_egress_declines.py` | P5(b): connector egress DECLINES surface as real errors, not swallowed successes. |
| `relay/test_relay_follow_up.py` | A2 outbound capability action: the token-less ``follow_up`` op. |
| `relay/test_relay_format_hints.py` | Relay lane parity: block formatting hints on outbound frames (Coatue F2). |
| `relay/test_relay_going_idle.py` | Phase 5 §5.3 — going-idle / buffered-flip primitive (gateway side). |
| `relay/test_relay_inbound_dedupe.py` | Inbound replay dedupe on the relay adapter (transplanted from the live-cards branch for the rc.4 relay-fixes train). |
| `relay/test_relay_inchannel_continuable.py` | Relay lane parity: flat in_channel continuable cron surface (Coatue F1). |
| `relay/test_relay_interactive.py` | Relay Phase 3 interactive tests — prompt op egress, prompt_response consumption, and the react ack lifecycle. |
| `relay/test_relay_interrupt.py` | Relay /stop interrupt routing (relay Phase 1, Task 1.4). |
| `relay/test_relay_live_cards.py` | Relay Slack live cards — gateway half (NS-658). |
| `relay/test_relay_media.py` | Relay Phase 2 media tests — send_media egress lanes + inbound media localization. |
| `relay/test_relay_multiplatform.py` | Unit tests for Phase 1.5 multi-platform-per-agent (relay). |
| `relay/test_relay_multiplatform_semantics.py` | Regression: stream semantics and draft capability resolve PER CHAT on a multi-platform relay (PR 85796 review round 2, finding 2). |
| `relay/test_relay_native_refusal_ack.py` | A refused relay native admission is acknowledged on the same socket, never a replay loop. |
| `relay/test_relay_native_turn_lifecycle.py` | A relay chat message admitted natively (``admit_producer``) gets the adapter processing lifecycle. |
| `relay/test_relay_passthrough.py` | Relay passthrough-over-WS forwarding (Phase 5 §5.1). |
| `relay/test_relay_passthrough_authority.py` | A relayed Discord interaction reaches the default native session authority only through the authenticated WS reader: real frame dispatcher -> relay adapter -> GatewayRunner/SQLite authority. |
| `relay/test_relay_per_platform_caps.py` | Per-platform capability descriptors on the relay (multi-platform Phase 1.5). |
| `relay/test_relay_policy_send.py` | Unit tests for the gateway-side relay relevance-policy declaration (Phase 6 ζ). |
| `relay/test_relay_prompt_ack_stream_isolation.py` | Prompt-ack sends must never seal an open draft stream. |
| `relay/test_relay_registration.py` | RelayAdapter registration via the platform registry. |
| `relay/test_relay_roundtrip.py` | End-to-end relay round-trip against the in-memory stub connector. |
| `relay/test_relay_roundtrip_telegram.py` | End-to-end relay round-trip for Telegram against the in-memory stub. |
| `relay/test_relay_seal_cancellation.py` | Regression: cancellation during the final seal must not orphan the remote stream (PR 85796 review round 2, finding 4). |
| `relay/test_relay_sheds_crypto.py` | Invariant: the relay path sheds platform crypto — it re-validates nothing. |
| `relay/test_relay_slack_dm_streaming.py` | Slack relay: edit-based streaming of the reply must fire in a DM. |
| `relay/test_relay_slack_prompt_dm_root.py` | Slack relay: interactive prompts follow the turn's thread stamp. |
| `relay/test_relay_slack_unfurl.py` | Relay-side Slack unfurl suppression: gateway-directed metadata stamping. |
| `relay/test_relay_state_bounds.py` | Regression: draft/seal coordination dicts are bounded (PR 85796 review, M1). |
| `relay/test_relay_stream_semantics_gating.py` | Regression: stream-is-the-message is a SLACK semantic, not a relay semantic (PR 85796 review, B4). |
| `relay/test_relay_task_card_failures.py` | Regression: task-card transport failures degrade, never raise (PR 85796 review, B7). |
| `relay/test_relay_threads.py` | Relay Phase 4 tests — thread lifecycle ops, reply_to enrichment parse, auto-thread markers, and the hello command manifest. |
| `relay/test_relay_turn_keying.py` | Regression: per-TURN stream/card identity (PR 85796 review, B2). |
| `relay/test_self_provision.py` | Unit tests for boot-time relay self-provisioning. |
| `relay/test_wire_user_identity.py` | Unit tests for relay wire-field hygiene (Phase 1 parity). |
| `relay/test_wire_voice_media.py` | Unit tests for relay voice-note + per-attachment media-type mapping. |
| `relay/test_ws_transport.py` | WebSocketRelayTransport against a real in-process WebSocket server. |
| `relay/test_ws_transport_hardening.py` | Regression tests for the relay WS transport hardening fix. |
| `restart_test_helpers.py` | Defines `RestartTestAdapter`, `make_restart_source`, `make_restart_runner` |
| `test_abandoned_turn_process_cleanup.py` | Regression coverage for abandoned gateway-turn subprocess cleanup (#76115). |
| `test_access_policy_mixin.py` | Every own-policy adapter must reach the same allow/deny verdict for the same policy inputs. |
| `test_active_lease_release_off_loop.py` | A turn end's active-session lease release never runs on the caller (the gateway loop). |
| `test_active_lease_release_order.py` | A turn end's queued lease release is already in effect for the next claim in this process. |
| `test_active_session_refusal_completion.py` | A refused turn still ends with message.complete, so the viewer never hangs. |
| `test_active_session_text_merge.py` | Regression tests for active-session TEXT follow-up queueing. |
| `test_active_turn_recovery.py` | Regression tests for exact durable active-turn restart recovery. |
| `test_adapter_authz_secret_scope.py` | Adapter authz gates must read GATEWAY_/PLATFORM_ allow-all + allowlists through the profile secret scope (#77548 cluster; #72348 / #86905 precedent). |
| `test_adapter_connect_classification.py` | Connect-failure classification + reconnect-queue escalation (OOF-156). |
| `test_adapter_guard_cache_race.py` | Regression tests for the adapter-guard cache race (empty ``ERROR:`` flake). |
| `test_adapter_session_key_seam.py` | Every adapter-side session key goes through one seam (#88715, invariant 4). |
| `test_adapter_settings_profile_parity.py` | Standalone-vs-served parity for adapter SETTINGS (not credentials) under ``gateway.multiplex_profiles``. |
| `test_adapter_settings_scoped_precedence.py` | Per-profile adapter settings resolve explicit scoped env → the profile's own YAML → default. |
| `test_adapter_startup_secret_scope.py` | Regression tests — Slack-pattern scoped credential reads at adapter startup. |
| `test_admission_queue_cap.py` | A session's durable FIFO holds at most main's busy-queue cap of queued inputs (N62), paused or not (B2-07). |
| `test_admission_queue_cap_notice.py` | A messaging follow-up past the FIFO cap gets a plain queue_full notice, not a turn error (N62). |
| `test_admission_result_reply_once.py` | LC-9: a settled turn result stores the reply once, and every reader still gets it exactly. |
| `test_admission_results.py` | Structured results are claim-owned and visible only after settlement. |
| `test_adversarial_mutation_lifecycle.py` | Independent review probes: mutation publication survives caller cancellation and retirement. |
| `test_adversarial_responses_eviction.py` | Durable exact Responses retries keep their output after response-body LRU eviction. |
| `test_adversarial_responses_pending.py` | A Responses retry stays pinned to its first admission's target, including after pointer loss. |
| `test_adversarial_settlement_review.py` | Independent probes for failed-settlement cleanup and ownership races. |
| `test_agent_cache.py` | Integration tests for gateway AIAgent caching. |
| `test_agent_cache_memory_lifecycle.py` | Memory-provider lifecycle of cached gateway agents: soft eviction (``release_clients``) versus end-of-session teardown (``shutdown_memory_provider`` / ``close``). |
| `test_agent_cache_pressure.py` | Memory-pressure eviction for the gateway agent cache (#80764). |
| `test_agent_cache_release_profile_scope.py` | Multiplex invariant: agent-cache eviction commits end-of-session memory under the OWNING profile. |
| `test_agent_error_reply_401_hint.py` | The gateway's 401 exception reply names the turn's provider and the failing profile's own sign-in (93889b770da: a bare ``hermes auth add <provider>`` from a named profile re-signs the ROOT store — the loop #114012 measu… |
| `test_agent_error_reply_local_detail.py` | A turn that raises on the gateway keeps its real cause for a local client (CLI, TUI, Desktop), whose panel otherwise read ``Details: ⚠️ Something went wrong and I couldn't finish this reply.`` Messaging platforms keep t… |
| `test_agent_loop_stopped_hook.py` | Tests that the ``agent_loop_stopped`` plugin hook fires when the gateway interrupts a running agent turn — both via ``/stop`` and via the running-agent fast-path inside ``/new``. |
| `test_agents_command_delegations.py` | Gateway /agents surfaces background delegations with live activity (#51690). |
| `test_allowed_channels_widening.py` | Tests for the allowed_{channels,chats,rooms} whitelist extension added alongside PR #7401 (Slack). |
| `test_allowlist_qualified_ids.py` | Allowlist matching compares qualified user_ids, not bare '@' localparts. |
| `test_allowlist_warning_platform_gate.py` | The startup "No env user allowlists configured" reminder fires only when a messaging platform is enabled — an API-server-only gateway has no sender to gate (#115439). |
| `test_api_admission_off_loop.py` | API admission never blocks the shared owner loop on a held SQLite writer (every HTTP door). |
| `test_api_admission_queued_on_drain.py` | An API caller whose input is still queued when the gateway retires is told it is saved (#134889). |
| `test_api_authority_continuity.py` | A declared API conversation restores at its current physical compression tip. |
| `test_api_authority_controls.py` | Run controls are fenced to the exact canonical admission. |
| `test_api_authority_daemon.py` | Ordinary daemon/API listener and private authenticated WS share execution. |
| `test_api_authority_execution.py` | API and authenticated WS share the existing selected cached agent. |
| `test_api_authority_retry.py` | Busy API retries observe one committed execution. |
| `test_api_authority_runs.py` | Run acceptance follows the same durable FIFO as HTTP/WS turns. |
| `test_api_authority_store.py` | API storage selection borrows the runtime's store, never another profile's. |
| `test_api_binding_served_profile.py` | A ``/p/<profile>/`` API session runs under the profile whose authority admitted it. |
| `test_api_canonical_projection.py` | Canonical API admissions project the real turn: media, tool payloads, controls, outcomes. |
| `test_api_chat_run_owner.py` | A chat completion admission carries the caller's run owner scope durably. |
| `test_api_compressed_receipt_history.py` | Responses chaining preserves a turn's compressed replacement, while ordinary receipts stay compact. |
| `test_api_crash_recovery.py` | SIGKILL recovery exercises authenticated HTTP on ordinary fresh daemons. |
| `test_api_cutover_contract.py` | Private API ingress preserves caller content and conversation authority. |
| `test_api_cutover_results.py` | Runs retain caller-selected history and exact terminal status. |
| `test_api_delegation_delivery_contract.py` | A detached API result must have an addressable consumer and one durable row. |
| `test_api_doors_logical_owner.py` | Every API door admits a compression continuation's id on its lineage root (the admission owner). |
| `test_api_hosted_binding.py` | Hosted source binding preserves the canonical hidden room identity. |
| `test_api_hosted_daemon.py` | Real invitation/grant HTTP inference and hidden room restoration. |
| `test_api_idempotency_after_delete.py` | An Idempotency-Key stays exactly-once after its session is deleted. |
| `test_api_idempotency_namespace.py` | Canonical OpenAI-compat idempotency is scoped to the authenticated key namespace. |
| `test_api_image_capture_lease.py` | An accepted API image keeps its bytes while its admission is still committing. |
| `test_api_image_delete_scale.py` | Deleting a session and recovering API turns stay under SQLite's expression limit (#140090). |
| `test_api_image_mislabelled_mime.py` | A data URL whose label disagrees with its image bytes (``data:image/png`` carrying JPEG, a common SDK default) is admitted under the sniffed type, as main forwarded it to the provider. |
| `test_api_implicit_session_after_delete.py` | A header-less Chat Completions conversation that opens like a deleted one is a new conversation. |
| `test_api_media_admission_bounds.py` | API data: images are validated as a batch before any byte is staged or committed. |
| `test_api_media_profile_scope.py` | Startup collection of retained API images pairs each profile's media root with its own state.db. |
| `test_api_media_retention.py` | Native scratch cleanup must not retire API image context sharing its bytes. |
| `test_api_model_lock_fallback.py` | A confirmed Browser model lock on a canonical API turn never falls back (main parity). |
| `test_api_notification_outcomes.py` | Diagnostic presentation does not rewrite execution evidence or next-turn callbacks. |
| `test_api_observe_settled.py` | An API observer never waits on an admission the FIFO already settled or cancelled. |
| `test_api_observer_gone_session.py` | An exact streaming Chat retry after its session was deleted replays the receipt, not a 500. |
| `test_api_pending_daemon.py` | API controls and WS views resolve the same real blocking tool waiter. |
| `test_api_relay_metadata_handoff.py` | Relay metadata a client sends on an API request reaches the canonical turn that executes it (main forwarded ``body.metadata`` to ``run_conversation(relay_metadata=...)``). |
| `test_api_request_one_target.py` | One API Idempotency-Key names one admission: a second session target never runs it again. |
| `test_api_responses_replay_frozen_tool_events.py` | A keyed streaming Responses retry replays the incremental tool frames exactly as first sent: terminal trimming of a long tool result must not reach the recorded events. |
| `test_api_responses_store_off_loop.py` | Responses persistence runs off the event loop and stays readable at once (#142641). |
| `test_api_responses_stream_retry.py` | An exact streaming Responses retry replays the recorded stream, never a new admission. |
| `test_api_retired_media.py` | Canonical API turns retain logical identity, reachable controls and owned image bytes. |
| `test_api_room_policy_settings.py` | A saved room execution policy is honoured only alongside the room dispatch it was issued for. |
| `test_api_route_heal_minted.py` | An API route the stale-route heal (#54878) handed to an empty minted session goes back to its caller. |
| `test_api_run_steer_before_adopt.py` | POST /v1/runs/{id}/steer accepted while the claimed turn is still building its agent reaches it. |
| `test_api_runs_admission_storage_error.py` | POST /v1/runs whose admission write loses the state.db writer answers a retryable 503 and keeps no reservation: an exact Idempotency-Key retry then runs the work, never replays a ghost. |
| `test_api_runs_legacy_declared_key.py` | #139835 (LC-13): an API session written by an earlier release stored the client's declared ``X-Hermes-Session-Key`` in ``sessions.session_key``; the caller that declares that same key is adopted onto the canonical route… |
| `test_api_runs_native_session_refusal.py` | /v1/runs against a natively owned session is a bounded 409, never a 500 with a phantom reservation. |
| `test_api_runs_poll_shape.py` | GET /v1/runs/{id} keeps the documented poll shape when the canonical admission answers. |
| `test_api_server.py` | Tests for the OpenAI-compatible API server gateway adapter. |
| `test_api_server_active_work_drain.py` | Regression coverage for #63529 API-server shutdown draining. |
| `test_api_server_bind_guard.py` | Tests for the API server bind-address startup guard. |
| `test_api_server_bot_chat_title_fallback.py` | The peer-dm title fallback for a reset LOCAL Bot Chat honours the listing's own filters. |
| `test_api_server_compaction_projection.py` | Client projections must not expose model-only compaction scaffolding. |
| `test_api_server_declared_conversation.py` | Declared-conversation identity on the API server (#96811). |
| `test_api_server_jobs.py` | Tests for the Cron Jobs API endpoints on the API server adapter. |
| `test_api_server_media_data_urls.py` | MEDIA: tag → base64 data-URL resolution for the API server (salvage of #2696). |
| `test_api_server_memory_sessions.py` | api_server keeps one memory provider per session across requests (#120116). |
| `test_api_server_model_options_include_unconfigured.py` | GET /api/model/options must forward ``include_unconfigured`` from the query string (default true) to ``build_model_options_payload`` instead of hardcoding it — external API consumers need a way to request the explicit-o… |
| `test_api_server_multimodal.py` | End-to-end tests for inline image inputs on /v1/chat/completions and /v1/responses. |
| `test_api_server_multiplex_secret_scope.py` | Regression for #61276: api_server agent entry under multiplex isolation. |
| `test_api_server_normalize.py` | Tests for _normalize_chat_content in the API server adapter. |
| `test_api_server_profile_prefix_misdelivery.py` | A ``/p/<profile>/`` prefix on a non-multiplexed gateway must not misdeliver. |
| `test_api_server_reasoning_ladder.py` | API-server reasoning-effort request parsing accepts the full ladder. |
| `test_api_server_reasoning_nonstream.py` | Reasoning on the non-streaming OpenAI-compatible routes and the Responses input parser (#99552). |
| `test_api_server_reasoning_stream.py` | Reasoning on the OpenAI-compatible SSE writers (#99552). |
| `test_api_server_response_store_profile_scope.py` | /v1/responses state belongs to the routed profile (#84253). |
| `test_api_server_responses_history_cap.py` | Opt-in byte cap on tool outputs in the stored /v1/responses conversation history. |
| `test_api_server_responses_history_dedupe.py` | Stored /v1/responses transcripts must not duplicate history across chained turns. |
| `test_api_server_room_dispatch.py` | Compatibility seams for extracted RoomLink dispatch handling. |
| `test_api_server_room_grants.py` | RoomLink grant authority: policy drift, gateway-owned secret, superseded authority. |
| `test_api_server_runs.py` | Tests for /v1/runs endpoints: start, status, events, steer, and stop. |
| `test_api_server_runs_hosted_room.py` | Tests for /v1/runs under hosted-room grants (``HermesRoom`` authorization). |
| `test_api_server_runs_import_isolation.py` | Import-time invariant: a missing ``RequestKey`` must not take ``web`` down with it. |
| `test_api_server_runs_room_policy_grant.py` | /v1/runs honours a room execution policy only when it comes from a verified room grant. |
| `test_api_server_sse_keepalive.py` | API-server SSE keepalive cadence while the agent is silent (preflight compression, long tool calls). Remote OpenAI-compatible clients commonly drop an idle stream after ~20 s and the disconnect interrupts the turn, so e… |
| `test_api_server_status_stream.py` | Agent status lines reach the OpenAI-compatible SSE writers as ``hermes.status`` events (#85426): the auto-recovery countdown must not leave an API client staring at a silent socket. |
| `test_api_server_toolset.py` | Tests for hermes-api-server toolset and API server tool availability. |
| `test_api_server_transform_llm_output.py` | ``transform_llm_output`` on the api_server streaming routes (#119323). |
| `test_api_server_turn_boundary.py` | The Responses current-turn boundary is anchored on this turn's user row, not on prefix equality with the client history (#89891). |
| `test_api_server_turn_executor.py` | API-server agent turns must not occupy asyncio's default executor (#144362). |
| `test_api_session_compression_exhaustion.py` | An API conversation whose turn exhausts compression stays addressable, and the session-chat door's re-run continues the failed attempt's row (#115325) on the admitted path too, never past completed tool work. |
| `test_api_session_create_after_delete.py` | ``POST /api/sessions`` with the explicit id of a deleted session is refused when it is created. |
| `test_api_session_preflight.py` | The browser can send the advertised continuation header only from allowed origins. |
| `test_api_settled_history_release.py` | Settlement itself drops a text-only API row's client history, not only the next restart's sweep. |
| `test_api_settled_payload_compaction.py` | A settled API admission keeps its committed image by reference, not as a second base64 copy. |
| `test_api_settled_row_retention.py` | A settled API admission row keeps only what exact-retry projections read. |
| `test_api_source_binding.py` | API source restoration cannot mint a parallel native conversation. |
| `test_api_stop_claim_race.py` | Stop of a queued API run that the drain claims mid-stop interrupts the claim, never 409s. |
| `test_api_store_error_status.py` | Canonical API refusals keep their retry semantics on the wire: a retiring profile's admission is a retryable 503 (Retry-After), a malformed control body is 400, and a generation/ownership refusal stays 409. |
| `test_api_synthetic_nudge_receipt.py` | An internal user-role recovery nudge must not erase earlier output in the same API turn. |
| `test_api_terminal_http.py` | Transport projections never report a non-successful result as completion. |
| `test_api_unknown_resolution.py` | HTTP run owners can acknowledge an exact unknown API admission after restart. |
| `test_approval_boundary.py` | Tests for approval boundary handling in WeCom native streaming. |
| `test_approval_prompt_redaction.py` | Regression test for approval prompt credential redaction (issue #48456). |
| `test_approval_send_timeout_ambiguity.py` | Approval prompt-send TIMEOUT must not trigger the re-ask/fallback lane. |
| `test_approval_timeout_notice.py` | Invariants for the exec-approval timeout notice hook (gateway/run_turn_runner_approval_settle.py). |
| `test_approvals_command.py` | Gateway contract and live dispatch for /approvals. |
| `test_approve_deny_commands.py` | Tests for /approve and /deny gateway commands. |
| `test_async_delegation_session_binding.py` | Gateway-side session binding for async delegations (#57498, #55578). |
| `test_async_delivery_capability.py` | Tests for the async-delivery capability gate (issue #10760). |
| `test_async_media_cache.py` | Tests: `test_async_cache_wrappers_keep_event_loop_responsive`, `test_async_cache_wrapper_propagates_validation_errors`, `test_cache_media_bytes_async_runs_off_loop_and_forwards_kwargs`, `test_async_cache_wrapper_uses_ac… |
| `test_async_session_db.py` | AsyncSessionDB offload facade. |
| `test_attachment_retry_mixed_staging.py` | A missing staging file must not hide a changed sibling on an exact retry. |
| `test_audio_cache.py` | Tests for audio cache utilities in gateway/platforms/base.py. |
| `test_auth_fallback.py` | Test that AuthError triggers fallback provider resolution (#7230). |
| `test_authenticated_session_identity.py` | Verified dashboard identities must own separate durable authority receipts. |
| `test_authority_active_list.py` | ``session.active_list`` is answered by the session authority from its own live turns. |
| `test_authority_approval_projection.py` | The authority answers the Desktop's approval replay reads for its own sessions. |
| `test_authority_automation.py` | Completion producers must commit to the same FIFO as human input. |
| `test_authority_busy_plaintext_approval.py` | Under the session authority a busy bare "yes" still answers a blocking approval (#46866). |
| `test_authority_busy_preempt_parity.py` | The authority's busy preempt keeps main's busy handler: voice steers, steer folds, busy ack. |
| `test_authority_cold_route_recovery.py` | A cold messaging-platform session mounts for a local viewer (TUI-8, NousResearch/hermes-agent#134889). |
| `test_authority_complete_persisted_turn.py` | The session authority's message.complete carries the turn's committed row receipt and precedes the idle session.info. |
| `test_authority_complete_reused_final.py` | A reused final keeps main's message.complete contract through the session authority. |
| `test_authority_connection.py` | Connection membership against the real authority and temporary SQLite. |
| `test_authority_events.py` | Authority event contracts, separate from the transport's queue unit tests. |
| `test_authority_lane_moves_on.py` | After a chat moves to a new conversation, an app view of its old one keeps working, off the chat. |
| `test_authority_listing_loop_turns.py` | The live listings walk every live session; their store reads must not run on the gateway's loop. |
| `test_authority_pause_recovery.py` | Paused FIFO heads release observers and resume after their compute worker finishes. |
| `test_authority_principal.py` | Server-stamped grants retain their scope through connection admission. |
| `test_authority_reconnect_gap.py` | A reconnecting viewer receives what its session published between the replay answer and its resume. |
| `test_authority_resident_stop.py` | Authority Stop must reach a running agent after its reusable cache entry is evicted. |
| `test_authority_stream.py` | Canonical execution stream through production API binding and real model SSE. |
| `test_authority_turn_error_surface.py` | A turn that fails on the session authority completes with the same ``error_surface`` the TUI path sends, so the Desktop renders the failure's own card (free tier at capacity, rate limit) instead of the generic one. |
| `test_authority_unknown_resolution.py` | An owner restart leaves a started admission `unknown`; a client must be able to acknowledge it. |
| `test_auto_continue.py` | Tests for the auto-continue feature (#4493 / #45232). |
| `test_auto_reset_clean_context.py` | Regression tests for #35809 — compression-exhaustion auto-reset loop. |
| `test_auto_reset_evicts_cached_agent.py` | Auto-reset is a full conversation boundary: per-session caches must not survive it (#58403). |
| `test_auto_skill_title_input.py` | Title input is user intent, not the gateway's model-facing skill payload. |
| `test_auto_voice_reply_format.py` | Tests for gateway auto-TTS voice reply audio format selection. |
| `test_automation_compression_media.py` | Producer completions and heartbeats keep entering a messaging conversation after compression moved its route to a child and after a prior input's retained media was released. |
| `test_automation_notification_category.py` | Diagnostic-only metadata survives the canonical FIFO, without inference. |
| `test_automation_retry.py` | Durable producer retries retain batch identities after an owner restart. |
| `test_automation_wake_route.py` | A producer wake enters its route as the committed human turn, whatever the route's stored origin says about labels and speakers, from a subagent's process, and over the relay. |
| `test_background_command.py` | Tests for /bg gateway slash command. |
| `test_background_process_notifications.py` | Tests for configurable background process notification modes. |
| `test_background_process_served_apiserver_wake.py` | A served profile's background-process completion wakes its ``api_server`` session in-process. |
| `test_bare_custom_launch_keeps_profile_route.py` | A bare ``custom`` launch pick stays on the profile's own route whenever that route can serve it. |
| `test_bare_custom_route_identity.py` | A bare ``custom`` provider is the billing class every named endpoint reports, never a route. |
| `test_base_auto_tts_output_format.py` | Base-adapter auto-TTS must pass a platform-aware explicit output path. |
| `test_base_topic_sessions.py` | Tests for BasePlatformAdapter topic-aware session handling. |
| `test_base_warning_owner_scope.py` | Composed delivery policy: real profile files, runner scopes and adapter transport. |
| `test_baseexception_turn_notify.py` | Regression: _process_message_background must notify the user when a turn raises a BaseException such as SystemExit/KeyboardInterrupt (#86651). |
| `test_bluebubbles_plugin.py` | Tests for the BlueBubbles iMessage gateway adapter. |
| `test_boot_reserve_lock_probe.py` | A client's lock probe never refuses a gateway boot. |
| `test_bootstrap_deferred_integrity_scan.py` | start_gateway runs the unclean-exit state.db scan off the event loop, after the runner is live. |
| `test_bootstrap_early_exit_teardown.py` | start_gateway exits that never reach running mode must not look like a clean shutdown. |
| `test_bot_authority.py` | Bot relay uses the ordinary daemon's durable FIFO, not an attached viewer. |
| `test_bot_chat_follows_profile.py` | A Bot Chat follows its profile's current route, whoever creates it. |
| `test_bot_chat_unadoptable_local_title.py` | A local row that holds the canonical "Bot Chat" title but no native open can ever adopt does not refuse every Bot Chat delivery for good (#141243, #143715). |
| `test_bot_dm_held_by_session_writer.py` | A Bot Chat DM the owner refuses before any admission, because another session writer holds the chat (a pre-#106742 Desktop backend's lease on a legacy Bot Chat), is a definite, named no-send: the tool says the message w… |
| `test_bot_door_message_cap.py` | The shared Bot door caps a relayed bot DM like main's relay edge (16,200), never a trusted producer's report: a cron bot-chat digest over that size is admitted whole. |
| `test_bot_loop_guard.py` | Bot-to-bot loop guard: ``_is_user_authorized`` refuses a chat in cooldown, ``_admit_bot_message`` counts. |
| `test_bot_mailbox_async.py` | Bot receipt polling is local and mailbox serialization never parks the event loop. |
| `test_bot_mailbox_cancellation.py` | Startup cancellation cannot release ownership before mailbox I/O physically ends. |
| `test_bot_paused_waiter.py` | The legacy Bot watcher survives a recoverable shared FIFO pause. |
| `test_bot_receipt_corruption.py` | Bulk Bot receipt recovery isolates bad files without weakening exact-id failures. |
| `test_bot_receipt_pin_fifo.py` | Legacy Bot mailbox tickets keep FIFO order across a pre-admission pin (#139138). |
| `test_bot_receipt_queue_full.py` | A Bot Chat delivery the FIFO refuses ``queue_full`` withdraws its pre-admission pin, so the same-id retry admits once the backlog drains instead of answering ``unknown_execution`` forever. |
| `test_bot_receipt_recovery_logs.py` | Startup Bot receipt recovery says what it could not answer, and where. |
| `test_bot_receipt_refusal.py` | A Bot Chat delivery the FIFO definitely refused (nothing committed, e.g. ``permission_denied``) turns its pre-admission pin into a terminal ``failed`` receipt the bulk scan reads without a warning and never re-sends (#1… |
| `test_bot_receipt_stale_pin.py` | A pre-admission pin left on disk by an older build (or by a transient refusal on the legacy migration path) whose ``bot:<key>`` admission never committed is withdrawn by the owner's scan once past the grace window, so t… |
| `test_bot_receipt_tombstone_expiry.py` | A deleted session's admission tombstones age out after the retry horizon; the receipts and pointers that name them do not. None of them may turn into ``storage_unavailable``: a Bot receipt re-read at every owner start w… |
| `test_bot_result_recovery.py` | Bot receipts recover only their exact committed admission result. |
| `test_bot_roster_fleet.py` | Regression for #139227: on a multiplexed gateway, every Bots roster row resolves its own profile's Bot Chat (the status dot's session id and the row's age), however that chat was created. |
| `test_bot_roster_worker_session.py` | Regression for #140977: the canonical Bots roster answers ``worker_session``. |
| `test_boundary_evict_commits_memory.py` | ``/new`` and ``/compress`` are session boundaries for memory providers, not resource evictions. |
| `test_bounded_adapter_teardown.py` | Regression tests: the shutdown teardown loop must not hang on a wedged adapter. |
| `test_branch_after_compressed_root_delete.py` | #134889 NF4: deleting a compressed, branched conversation leaves its branch a working conversation. |
| `test_branch_routing_columns.py` | Regression test for /branch losing gateway routing columns (#NNNNN). |
| `test_branch_secondary_profile_origin.py` | A branched local session keeps its owning profile's origin and resumes after restart. |
| `test_branch_thread_command.py` | /branch on thread-capable platforms opens a sibling thread and keeps the origin (#66023). |
| `test_browser_manage_shared_owner.py` | /browser connect\|disconnect through the real WS legacy fallback (dokterdok N25, #134889 CLI-9). |
| `test_builtin_platform_status.py` | gateway.config_env.builtin_platform_status: the gateway's (enabled, connected) for one built-in platform, from a profile's config dict, without load_gateway_config(). Run here without a multiplexer, so the env pass's ex… |
| `test_busy_burst_merge_shared.py` | A busy same-sender burst is one authority admission, as main merged it into one turn (N54). |
| `test_busy_burst_serial_reader.py` | A serial receive loop's busy burst still merges, and the loop never waits out the hold window. |
| `test_busy_command.py` | Smoke tests for gateway /busy command dispatch. |
| `test_busy_durable_acceptance.py` | Serial transports regain their receive loop once input is durable. |
| `test_busy_followup_after_session_release.py` | Follow-ups routed while a session finishes must not be stranded (#121393). |
| `test_busy_followup_guard_release.py` | Regression for #120999: a busy follow-up must not be parked when the turn it queued behind finishes while the runner's busy handler is still deciding. |
| `test_busy_followup_marker_handoff.py` | A busy follow-up's crash marker survives until its reply is in the delivery ledger (N49). |
| `test_busy_photo_interrupt_once.py` | A photo sent while a gateway turn is running is one next turn, not two. |
| `test_busy_redirect_anchor.py` | A successful busy redirect re-anchors the running turn's reply to the redirecting message. |
| `test_busy_reply_internal_anchor.py` | A busy-path reply to an internal wake never hands the wake's producer identity to the adapter. |
| `test_busy_requeue_hot_loop.py` | Regression: a busy follow-up the runner re-queues must not hot-loop through the adapter drain. |
| `test_busy_session_ack.py` | Tests for busy-session acknowledgment when user sends messages during active agent runs. |
| `test_busy_session_auth_bypass.py` | Tests for #17775: unauthorized users must be blocked in the busy-session path. |
| `test_busy_session_profile_scope.py` | Regression for #103717: a secondary multiplex profile's busy-session follow-ups must authorize against THAT profile's allowlist, not whatever ``os.environ`` happens to hold (the primary profile's first-writer-bridged va… |
| `test_busy_steer_origin.py` | Per-injection origin survives every busy steer/redirect entry point. |
| `test_busy_steer_subagent_fanout.py` | Busy-mode steer reaches the subagent the parent is blocked on (#112095, Telegram surface). |
| `test_busy_wake_admission.py` | Trusted wakes cross the real adapter busy boundary, not external-user auth. |
| `test_buzz_adapter.py` | Tests for the Buzz platform adapter plugin. |
| `test_buzz_authz.py` | Gateway authz tests: BUZZ_ALLOWED_USERS accepts npub or hex (#78428). |
| `test_buzz_forum_kinds.py` | Regression tests for Buzz forum-kind dispatch (#90309). |
| `test_buzz_mention_resolution.py` | Tests for the Buzz adapter's @mention resolution (PR #83414). |
| `test_buzz_progress_thread_routing.py` | Buzz progress/status thread-routing regressions. |
| `test_buzz_thread_topology.py` | E2E regression tests for the Buzz thread-topology salvage cluster. |
| `test_buzz_websocket.py` | Tests for the Buzz WebSocket transport (NIP-42) and Nostr signing module. |
| `test_cached_agent_history_guard.py` | Regression tests for cached gateway transcript selection. |
| `test_cached_agent_max_iterations.py` | Regression tests for PR #48127: cached agent max_iterations refresh. |
| `test_cancel_background_drain.py` | Regression test: cancel_background_tasks must drain late-arrival tasks. |
| `test_canonical_complete_path.py` | The Ink TUI's ``complete.path`` over the canonical connection lists the session's own folder. |
| `test_canonical_desktop_metadata.py` | Canonical GUI metadata follows the authenticated local-session route. |
| `test_canonical_file_attach_staged.py` | A browser pick attaches through the shared owner, copied only from a profile it may reach. |
| `test_canonical_file_attach_staged_sources.py` | A browser pick reaches the session only from the exact upload it names, through the owner's ``file.attach``. |
| `test_canonical_resume_display_projection.py` | A resumed canonical session renders through main's display projection (TUI parity, PR #106742). |
| `test_canonical_resume_reasoning_snapshot.py` | B22 / C-hx-3: a cold Desktop resume settles the reasoning pill from the canonical snapshot. |
| `test_canonical_session_inventory.py` | A canonical session's snapshot carries main's banner/status inventory for its frozen policy. |
| `test_canonical_stop_hard_cancel.py` | Canonical Stop (Desktop, Ink, classic CLI view, ACP) hard-cancels the turn and leaves background delegations running: a background subagent is independent of the chat that spawned it (Teknium ruling); `/stop` ends them. |
| `test_canonical_tui_desktop_routes.py` | Ink/Desktop verbs the owner answered -32601 or refused now run their gateway handlers. |
| `test_canonical_typed_voice_stop.py` | TUI-26: a bare stop phrase TYPED into a voice chat on the shared gateway ends the voice chat instead of reaching the agent. Ink sends prompts to the canonical ``prompt.submit``; the request goes through the real ``Autho… |
| `test_canonical_wire_contract.py` | The canonical dispatcher speaks only the declared wire contract (``tui_gateway/contracts``). |
| `test_canonical_wire_contracts.py` | Canonical RPC validation must not reuse the independently shipped serve wire. |
| `test_cgroup_cleanup.py` | Tests for the systemd ExecStopPost cgroup reaper (issue #37454). |
| `test_channel_continuity_hint.py` | Tests for the lightweight Slack/Discord channel session-continuity hint. |
| `test_channel_directory.py` | Tests for gateway/channel_directory.py — channel resolution and display. |
| `test_channel_directory_connected_only.py` | Session-based channel discovery must not resurrect disconnected platforms. |
| `test_channel_overrides.py` | Tests for per-channel model and system prompt overrides (Fixes #1955). |
| `test_chat_completions_approval.py` | Legacy /v1/chat/completions streams surface approval requests that the client can resolve through ``POST /v1/runs/{completion_id}/approval`` (#51871). |
| `test_chat_completions_final_fallback.py` | Streaming /v1/chat/completions must surface final_response when no content delta was streamed (guardrail halt / partial_stream_recovery paths, #31449). |
| `test_chat_completions_tool_progress_optout.py` | ``platforms.api_server.tool_progress_events: false`` drops the custom ``hermes.tool.progress`` SSE frames from streaming Chat Completions (#12020). |
| `test_checkpoint_config.py` | Runtime coverage for gateway filesystem-checkpoint configuration. |
| `test_checkpoint_prune_housekeeping.py` | Checkpoint store pruning rides the gateway housekeeping tick, not the constructor. |
| `test_child_notice_profile_admission.py` | Child-process notices across profiles: every consumer follows the owning profile's policy and live ownership. |
| `test_choice_picker.py` | Tests for the gateway interactive choice picker (/reasoning, /fast). |
| `test_cjk_fts_config_bridge.py` | config.yaml sessions.* bridges for the search-index knobs (config-authoritative). |
| `test_claim_reopen_off_loop.py` | The claim phase's reopen of a finalized local row is a write: it runs off the owner loop. |
| `test_clarify_active_session_bypass.py` | Regression tests for clarify replies while a gateway session is busy. |
| `test_clarify_batch_settlement_parity.py` | One settlement rule for a batch clarify, whichever registry holds it. |
| `test_clarify_card_retire_on_timeout.py` | A clarify that ends without a click retires the adapter's native card (#110821, #111019). |
| `test_clarify_delivery_fallback.py` | A clarify card that cannot render is retried as plain text, and a card that fails late does not pass for user inactivity (#112684). |
| `test_clarify_lock_keeps_locked_answers.py` | A batch answer already locked with ``clarify.lock`` survives every way the wait can end, as on main's sidecar (``tui_gateway/server_requests.py``: "locked answers survive a timeout"): a timeout returns ``{answers: <lock… |
| `test_clarify_lock_owner.py` | #140400: the batch ``clarify`` request a local viewer gets is answered with ``clarify.lock``. |
| `test_clarify_progress_leak.py` | Regression tests for #52374 — raw clarify tool-call JSON must never leak into the chat as a tool-progress bubble. |
| `test_clarify_send_timeout_ambiguity.py` | Clarify prompt-send TIMEOUT must not tear down the registration. |
| `test_clarify_thread_followup_not_swallowed.py` | Regression tests for #62034 — pending multi-choice clarify prompts must not swallow unrelated thread follow-up messages. |
| `test_classic_slot_holds_fifo_head.py` | A user message admitted while a classic fallback wake holds the route's slot waits queued and runs as its own admitted turn; it is never handed to the wake's busy path and booked completed unrun (N82). Real GatewayRunne… |
| `test_clean_shutdown_marker.py` | Tests for the clean shutdown marker that prevents unwanted session auto-resets. |
| `test_cleanup_off_loop.py` | Regression test for #53175: gateway event loop wedged by synchronous agent-resource cleanup run inline from loop coroutines. |
| `test_cli_plugin_command_in_gateway.py` | A classic CLI plugin command runs in the gateway and its ``ctx.call_mcp`` reaches the gateway's MCP registry (#134889 CLI-13, PLG-7). |
| `test_cli_plugin_command_own_socket.py` | A classic CLI plugin command never holds the CLI's own gateway connection (#134889 PLG-7). |
| `test_code_fence_tracking.py` | Tests for code fence tracking across message split / truncation / streaming paths. |
| `test_codex_hygiene_compaction.py` | Regression tests for #73503 — codex_app_server compression must not be a no-op. |
| `test_cold_platform_activation.py` | Cold gateway config load imports only the platform adapters the profile configures. |
| `test_command_bypass_active_session.py` | Regression tests: slash commands must bypass the base adapter's active-session guard. |
| `test_command_discovery.py` | Discovery stays transport-independent and cannot select another profile. |
| `test_compaction_heartbeat_gateway_filter.py` | The compaction heartbeat (#98371) must be classified like COMPACTION_STATUS. |
| `test_complete_path_at_filter.py` | Regression tests for the TUI gateway's `complete.path` handler. |
| `test_completion_admission.py` | Real adapter admission is the completion acknowledgement boundary. |
| `test_completion_admission_compression_race.py` | Regression for the compression-after-admission result-loss window in #136225. |
| `test_completion_delivery.py` | Lifecycle-scoped gateway delivery regressions for terminal completions. |
| `test_completion_owner_retry.py` | Durable delivery retries uncertain delegate ancestry without moving the route. |
| `test_completion_ownership_proof.py` | An admitted completion keeps main's post-compression guarantee: the executed event carries the ownership proof, so one transient owner read in the turn's resolver never drops it (N77). |
| `test_completion_session_boundary.py` | Session-boundary gating for background-process completion delivery. |
| `test_compress_command.py` | Tests for gateway /compress user-facing messaging. |
| `test_compress_focus.py` | Tests for gateway /compress <focus> — focus topic on the gateway side. |
| `test_compress_plugin_engine.py` | Regression test: /compress works with context engine plugins. |
| `test_compress_preview.py` | Tests for gateway /compress --preview/--dry-run/--aggressive flags (PR #3243 salvage). |
| `test_compression_concurrent_sessions.py` | Behavioral tests for concurrent compression across distinct and shared sessions. |
| `test_compression_failure_session_sync.py` | Tests: `_SessionStore`, `_CompressionThenFailureAgent`, `_StreamConsumer`, `_Adapter`, `_runner`, `_install_compression_failure_agent` … |
| `test_compression_in_flight_check.py` | #5 regression: _session_has_compression_in_flight must offload both blocking sources to thread pool. |
| `test_compression_interrupt_demotion.py` | Regression tests for #56391. |
| `test_compression_progress_notices.py` | Opt-in compression progress notices on chat gateways (#52995). |
| `test_config.py` | Tests for gateway configuration management. |
| `test_config_driven_access_policy.py` | Tests for config-driven platform access policies at the gateway layer. |
| `test_config_env_bridge_authority.py` | Regression tests for the config.yaml → env var bridge in gateway/run.py. |
| `test_config_policy_daemon.py` | Tests: `test_config_policy_recovery_on_ordinary_daemon` |
| `test_config_policy_recovery.py` | Config credentials borrow only their frozen profile source across restart. |
| `test_config_secret_scope.py` | CFG-10 (#140290): a frozen config-secret reference is bound to the secrets it carries and the endpoints they authenticate, not to every byte of the policy. |
| `test_context_ref_expansion_runtime.py` | Regression test for the "@" context-reference-expansion block in ``GatewayRunner._prepare_inbound_message_text``. |
| `test_control_publish_off_loop.py` | Control-card publishes read their snapshot off the loop and still land in the order they were scheduled. |
| `test_control_socket.py` | Tests for the gateway control socket (#92091 migration step 1). |
| `test_control_socket_forwarded_subject.py` | A forwarded mutation acts as the dashboard's authenticated principal, not the socket UID (#138915). |
| `test_control_socket_pause.py` | pause-for-update control-socket verb (#92091 step 2, campaign #91277). |
| `test_control_socket_peer_security.py` | Control-socket trust boundary: server identity, home writability, pointer mode, fallback root. |
| `test_control_socket_windows_live.py` | LIVE Windows E2E for the gateway control socket named-pipe transport. |
| `test_conversation_scope_funnel.py` | Behavior tests for _clear_conversation_scope — the single conversation- boundary funnel (#64934 follow-up). |
| `test_cron_active_work_drain.py` | Tests for #60432: the gateway shutdown drain was structurally blind to in-flight cron work. Cron jobs run through cron/scheduler.py's own thread pool, entirely outside ``GatewayRunner._running_agents`` -- the dict every… |
| `test_cron_admission_error_surface.py` | A message typed into a cron session fails with a renderable read-only descriptor (#141348). |
| `test_cron_canonical_receipt_regression.py` | Cron consumes the real Bot Chat receipt over an owned daemon's WebSocket. |
| `test_cron_delivery_housekeeping.py` | Gateway-independent draining of restart-safe cron deliveries. |
| `test_cron_drain_floor.py` | Regression tests for #82161. |
| `test_cron_fire_startup_gate.py` | A Chronos fire that lands while the gateway is still starting waits for its adapters (cold boot race). |
| `test_cron_fire_webhook.py` | Tests for the Chronos cron-fire webhook (POST /api/cron/fire) — Phase 4E.2. |
| `test_cron_interrupt_notification.py` | Regression tests for #82232. |
| `test_cron_owner_progress_stamp.py` | An owner-side canonical cron run proves progress on the FIRER's ledger row. |
| `test_cron_profile_gate.py` | The gateway ticker stands down for a profile whose OWN gateway process ticks it. |
| `test_cron_shutdown_drain.py` | Regression tests for #58818. |
| `test_cron_ticks_every_profile.py` | The host gateway's cron ticker visits every profile, flag or no flag. |
| `test_custom_provider_request_overrides.py` | Regression tests for gateway preservation of provider-derived request_overrides. |
| `test_cwd_placeholder.py` | Unit tests for gateway.cwd_placeholder.resolve_placeholder_terminal_cwd. |
| `test_dashboard_mount_close_race.py` | A gateway stop that wins the race with the dashboard's lifespan start never leaves it mounted. |
| `test_dead_targets.py` | Tests for confirmed-dead delivery-target short-circuiting (deleted Telegram groups, blocked/kicked bots, deactivated users). |
| `test_decline_fallback_suppression.py` | Caller-level fallback suppression — the branches that actually stop the leak. |
| `test_dedupe_user_turns.py` | Regression tests for issue #47237. |
| `test_delegation_session_id_leak.py` | Delegated children must not replace their parent's session identity. |
| `test_delete_secondary_profile_multiplex.py` | A multiplexed secondary profile's delete retires routing under one owner (#138826). |
| `test_delete_session_no_resurrect.py` | Hard-deleted gateway sessions must not resurrect through the routing index (#42422). |
| `test_delivery.py` | Tests for the delivery routing module. |
| `test_delivery_flood_invariants.py` | Delivery retries honor the platform deadline without crossing ownership boundaries. |
| `test_delivery_ledger.py` | Tests for the gateway delivery-obligation ledger (gateway/delivery_ledger.py). |
| `test_delivery_ledger_fd_leak.py` | Regression: the gateway delivery ledger must close every SQLite connection. |
| `test_delivery_ledger_process_home.py` | A served profile's reply is ledgered where the boot sweep looks for it. |
| `test_delivery_ledger_producer.py` | Producer-hook tests: _process_message_background records delivery obligations around the final send (gateway/platforms/base.py). |
| `test_delivery_ledger_single_connection.py` | Recording a reply opens exactly one SQLite connection. |
| `test_delivery_silence_filter.py` | Tests for the outbound silence-narration filter (anti-loop control). |
| `test_delivery_unknown_target.py` | Unknown destinations must not acknowledge a successful local delivery. |
| `test_derived_generation_after_sweep.py` | A derived conversation resumed after a housekeeping sweep stays on its new session. |
| `test_derived_session_after_delete.py` | A hosted-room member or an A2A peer context whose session was deleted continues on a new one. |
| `test_desktop_process_verbs.py` | Desktop's /stop, per-process Stop, MCP reload and file attach are served by the shared owner (dokterdok N27). |
| `test_destructive_slash_always_persist_report.py` | Answering "Always Approve" must not claim an opt-out that was not saved. |
| `test_destructive_slash_confirm.py` | Tests for the gateway's destructive-slash-confirm wrapper. |
| `test_detached_conversation_lifecycle.py` | The lifecycle of a conversation its chat moved past (review of #144840 at 03d04918dde). |
| `test_detached_conversation_results.py` | What an old conversation started keeps landing in it after its chat moved on (re-review of #144840). |
| `test_diagnostic_wake_presentation.py` | Diagnostic-only wakes execute while their unsolicited free-form reply stays private. |
| `test_diff_command.py` | End-to-end tests for the gateway ``/diff`` command. |
| `test_dingtalk.py` | Tests for DingTalk platform adapter. |
| `test_dingtalk_reconnect_circuit_breaker.py` | #24851 — DingTalk stream reconnect loop must not storm on a persistent error. |
| `test_discard_delivers_captured_answer.py` | Discard of a turn whose settlement failed commits its captured answer AND delivers it to the chat the answer was owed to, exactly once; nothing is sent while the turn is unknown. |
| `test_discord_admission_thread_exemption.py` | A thread the bot joined is exempt from the mention requirement on every ingress path. |
| `test_discord_allow_bots_yaml_config.py` | config.yaml `discord.allow_bots` must reach the adapter's bot gate. |
| `test_discord_allowed_mentions.py` | Tests for the Discord ``allowed_mentions`` safe-default helper. |
| `test_discord_approval_lifecycle.py` | Approval cards must release their view and preserve terminal state across edits. |
| `test_discord_approval_mentions.py` | Discord approval prompts can opt into owner mentions. |
| `test_discord_attachment_download.py` | Tests for Discord attachment downloads via the authenticated bot session. |
| `test_discord_attachment_receipts.py` | Media targets and receipts must describe the attachment, not a fallback notice. |
| `test_discord_audio_delivery.py` | Discord audio delivery: plain audio is an attachment, voice messages are real Ogg/Opus. |
| `test_discord_auto_thread_prompt_parity.py` | An auto-threaded @mention reads the new thread's topic, as the thread's next message does. |
| `test_discord_auto_thread_rename_pin.py` | Hermes's own auto-thread title rename keeps the pinned session-context prompt. |
| `test_discord_bot_auth_bypass.py` | Regression guard for #4466: DISCORD_ALLOW_BOTS works without DISCORD_ALLOWED_USERS. |
| `test_discord_bot_inline_mentions.py` | Bot-authored Discord messages need a typed ``<@bot>`` by default; a reply ping alone no longer wakes the bot (two bots otherwise volley replies forever). Salvage of #106874. |
| `test_discord_channel_controls.py` | Tests for Discord ignored_channels and no_thread_channels config. |
| `test_discord_channel_obfuscation.py` | Discord channel obfuscation (Aug 2026 privacy change, HTTP omission mandatory Nov 16 2026): channels a bot lacks VIEW_CHANNEL on arrive named "___hidden___" with flag 1 << 17 set. Enumeration sites must skip them. #90154 |
| `test_discord_channel_prompts.py` | Tests for Discord channel_prompts resolution and injection. |
| `test_discord_channel_skills.py` | Tests for Discord channel_skill_bindings auto-skill resolution. |
| `test_discord_clarify_buttons.py` | Tests for Discord clarify button rendering and resolution. |
| `test_discord_component_auth.py` | Security regression tests: Discord component views honor allowlists. |
| `test_discord_config_allowlist_multiplex.py` | A Discord allowlist written only in config.yaml (``discord.allow_from``) under multiplex. |
| `test_discord_connect.py` | Tests: `_FakeAllowedMentions`, `_ensure_discord_mock`, `_speed_up_command_sync_mutation_pacing`, `FakeTree`, `FakeBot`, `test_resolve_allowed_usernames_preserves_wildcard` … |
| `test_discord_document_handling.py` | Tests for Discord incoming document/file attachment handling. |
| `test_discord_double_dispatch.py` | Tests for Discord double-dispatch prevention (#51057). |
| `test_discord_edit_message_overflow.py` | Regression tests for Discord oversized edit_message split-and-deliver. |
| `test_discord_event_silence.py` | Dispatch-side liveness for the Discord adapter (#109521 incident 2). |
| `test_discord_exec_approval_content.py` | Tests: `_capture_channel`, `test_exec_approval_prompt_uses_visible_content_with_command_and_reason`, `test_exec_approval_content_stays_within_discord_cap_for_long_reason`, `test_exec_approval_view_honors_discord_timeout… |
| `test_discord_format.py` | Discord format_message: tables converted to bullet groups. |
| `test_discord_free_response.py` | Tests for Discord free-response defaults and mention gating. |
| `test_discord_home_link.py` | Discord channel links are accepted wherever a channel id is (#115216). |
| `test_discord_imports.py` | Import-safety tests for the Discord gateway adapter. |
| `test_discord_liveness.py` | Regression tests for Discord Gateway WebSocket liveness. |
| `test_discord_missed_message_backfill.py` | Tests for Discord missed-message startup backfill. |
| `test_discord_model_picker.py` | Regression tests for the Discord /model picker. |
| `test_discord_model_picker_partition.py` | Regression test: Discord /model picker must surface ALL models for a provider whose list exceeds 25 entries (e.g. Nous curated + Portal free recommendations), not silently truncate the tail at 25 options. |
| `test_discord_pending_text_batch_shutdown.py` | Regression guard for Discord text-batch flush during gateway shutdown. |
| `test_discord_platform_events.py` | Discord ``gateway_platform_event`` fire-sites (#64176 remaining scope). |
| `test_discord_plugin_setup.py` | Tests for the Discord plugin's interactive_setup wizard. |
| `test_discord_prompt_content_siblings.py` | Sibling coverage for the embed-invisibility fix (send_exec_approval got it in the same PR): slash confirm, clarify, and update prompts must also mirror their payload into plain message content, since embeds don't render… |
| `test_discord_prompt_timeout_config.py` | Tests for the configurable Discord interactive-view timeout. |
| `test_discord_race_polish.py` | Discord adapter race polish: concurrent join_voice_channel must not double-invoke channel.connect() on the same guild. |
| `test_discord_reactions.py` | Tests for Discord message reactions tied to processing lifecycle hooks. |
| `test_discord_reply_mode.py` | Tests for Discord reply_to_mode functionality. |
| `test_discord_roles_dm_scope.py` | Regression guard: DISCORD_ALLOWED_ROLES must be guild-scoped, not global. |
| `test_discord_send.py` | Tests: `_ensure_discord_mock`, `test_send_rejects_whitespace_and_records_failed_final_reply`, `_voice_adapter`, `_native_voice_payload`, `test_send_retries_without_reference_when_reply_target_is_deleted`, `test_forum_po… |
| `test_discord_slash_auth.py` | Security regression tests: slash commands honor on_message authorization gates. |
| `test_discord_slash_commands.py` | Tests for native Discord slash command fast-paths (thread creation & auto-thread). |
| `test_discord_split_cap.py` | Regression tests for the Discord split-delivery cap (issue #86581). |
| `test_discord_sync_limit.py` | Test Discord slash command sync respects the 100-command hard limit. |
| `test_discord_thread_persistence.py` | Tests for Discord thread participation persistence. |
| `test_discord_thread_slash_expired_defer.py` | Sibling coverage for expired slash defer handling: /thread creation must still run when the interaction token has expired (Discord error 10062), just skipping the ephemeral followups. |
| `test_discord_triggering_note_persistence.py` | The Discord ``[Triggering message id: …]`` note is a model instruction: it rides the API-bound user message but must never be persisted as the user row's ``content`` (every transcript surface rendered it as if the user… |
| `test_discord_turn_prompt_parity.py` | Discord turns built outside on_message carry the same prompt inputs as a message in that chat. |
| `test_discord_username_allowlist_env_reload.py` | Gateway authz must survive the per-turn .env hot-reload when DISCORD_ALLOWED_USERS contains usernames (Aug 2026 incident). |
| `test_discord_view_base_parity.py` | Parity tests for the shared ``_HermesView`` base behind the Discord component views. |
| `test_discord_voice_mixer.py` | Tests for the Discord continuous voice mixer (ambient + ducked speech) and the verbal-ack-before-tool-calls hook. |
| `test_discord_voice_rekey.py` | VoiceReceiver re-key resilience — credentials must track the live connection. |
| `test_discord_voice_role_grant.py` | A spoken turn from a member admitted by ``DISCORD_ALLOWED_ROLES`` reaches the agent. |
| `test_discord_voice_stale_binding.py` | An utterance is dispatched only into the conversation it was captured for. |
| `test_disk_status.py` | Tests for gateway.disk_status — the /api/status disk rollup (NS-656). |
| `test_display_admission.py` | Desktop large-paste ``title_preview`` and hidden ``display_kind`` sends survive canonical admission (N3). |
| `test_display_config.py` | Tests for gateway.display_config — per-platform display/verbosity resolver. |
| `test_display_null_turn_wiring.py` | A profile config with `display: null` must not crash turn wiring. |
| `test_dm_topics.py` | Tests for Telegram DM Private Chat Topics (Bot API 9.4). |
| `test_docker_session_workspace.py` | #140665 (#134889 CLI-39): a gateway-owned session's client cwd reaches the Docker terminal backend. |
| `test_document_cache.py` | Tests for document cache utilities in gateway/platforms/base.py. |
| `test_document_context_note.py` | Tests for the document context note prepended to user turns with attachments. |
| `test_draft_id_restart_uniqueness.py` | Regression: draft ids must be unique across gateway incarnations (PR 85796 review, B3; hardened per r2 follow-up). |
| `test_drain_active_work_report.py` | A draining gateway names the work it is waiting on, and the updater's wait prints it. |
| `test_duplicate_reply_suppression.py` | Tests for duplicate reply suppression across the gateway stack. |
| `test_duplicate_user_message.py` | Tests for #42039 — user messages stored twice in state.db. |
| `test_email.py` | Tests for the Email gateway platform adapter. |
| `test_email_charset_fallback.py` | Email charset robustness: unknown/malformed charsets must never drop mail. |
| `test_email_imap_id_protocol.py` | Exercise IMAP ID negotiation with real imaplib and a local protocol peer. |
| `test_email_robustness.py` | Email adapter robustness against malformed IMAP responses (salvage of #2794). |
| `test_email_secret_scope.py` | Tests for email adapter credential isolation under multiplexing. |
| `test_empty_model_fallback.py` | Tests for empty model fallback — when provider is configured but model is missing. |
| `test_empty_model_recovery.py` | Regression tests for #35314 — empty model on the post-interrupt recovery turn. |
| `test_empty_sentinel_rewrite_copy.py` | The gateway's ``(empty)`` sentinel rewrite reads from the same constant as the CLI explainer (``agent.turn_explainers.EMPTY_RESPONSE_EXPLANATION``), so a chat user and a terminal user see one text for "the model produce… |
| `test_env_override_explicit_disable.py` | Regression tests for #48820 Bug 2: an explicit ``platforms.<x>.enabled: false`` in config.yaml must survive ``_apply_env_overrides`` when that platform's credentials are present in the environment. |
| `test_ephemeral_reply.py` | Tests for EphemeralReply — system-notice auto-delete in gateway adapters. |
| `test_escape_reasoning_fences.py` | Tests for escape_code_fences_for_display. |
| `test_estop_interactive_turns.py` | GW-1 (#134889): `hermes pause` holds every gateway turn, interactive ones included. |
| `test_exec_approval_template.py` | Invariants for the exec-approval template method on BasePlatformAdapter. |
| `test_exec_approval_timeout_notice.py` | When a messaging-platform approval prompt times out, the chat must say so. |
| `test_exec_quick_command_tree.py` | A ``type: exec`` quick command that times out or is cancelled leaves nothing running. |
| `test_executor_pool_isolation.py` | Best-effort session housekeeping must not be able to starve agent turn bodies. |
| `test_external_drain_control.py` | Tests for the external drain-control marker contract + gateway state machine. |
| `test_extract_local_files.py` | Tests for extract_local_files() — auto-detection of bare local file paths in model response text for native media delivery. |
| `test_failure_writer_ownership.py` | Accepted inbound turns have one durable owner, including exception fallback. |
| `test_fallback_chain_reload.py` | Regression tests for #60955: gateway must not freeze fallback_providers. |
| `test_fast_command.py` | Tests for gateway /fast support and Priority Processing routing. |
| `test_faulthandler_no_stderr.py` | Regression: #71671 — gateway must survive faulthandler.enable() with sys.stderr=None. |
| `test_feishu.py` | Tests for the Feishu gateway integration. |
| `test_feishu_approval_buttons.py` | Tests for Feishu interactive card approval buttons. |
| `test_feishu_audio_delivery.py` | Feishu audio delivery: plain audio MEDIA is a named file, only voice intent is a voice note. |
| `test_feishu_bot_admission.py` | Adapter-layer tests for Feishu bot-sender admission (``FeishuAdapter._admit``). |
| `test_feishu_bot_auth_bypass.py` | Regression guard for Feishu bot-sender authorization bypass. |
| `test_feishu_card_action_gateway_authz.py` | Feishu approval / update-prompt card clicks with no Feishu allowlist or admins. |
| `test_feishu_channel_prompts.py` | Tests for Feishu per-channel prompt resolution. |
| `test_feishu_comment.py` | Tests for feishu_comment — event filtering, access control integration, wiki reverse lookup. |
| `test_feishu_comment_rules.py` | Tests for feishu_comment_rules — 3-tier access control rule engine. |
| `test_feishu_group_policy_surfacing.py` | Operator-facing surfacing of the empty-allowlist default deny in Feishu group admission. |
| `test_feishu_lazy_import.py` | Regression coverage for deferred Feishu SDK loading. |
| `test_feishu_meeting_invite.py` | Tests for Feishu vc.bot.meeting_invited_v1 event handling. |
| `test_feishu_onboard.py` | Tests for plugins.platforms.feishu.adapter — Feishu scan-to-create registration. |
| `test_feishu_profile_scope_hops.py` | Profile scope must survive the Feishu adapter's thread hops under a multiplexed gateway. |
| `test_feishu_sdk_executor.py` | Regression tests for the Feishu adapter's owned SDK executor. |
| `test_feishu_table_markdown.py` | Tests for Feishu adapter outbound markdown payload construction. |
| `test_feishu_voice_message_type.py` | Regression tests for Feishu native voice-note classification. |
| `test_feishu_ws_multiplex_isolation.py` | Multiplex isolation for the lark_oapi WS client (issue #73779). |
| `test_fence_chunker.py` | Invariant tests for the shared fence-aware markdown chunker core. |
| `test_fifo_overflow_rescue.py` | Regression tests for #99882: FIFO overflow orphan rescue. |
| `test_finalize_session_off_loop.py` | Session-finalize plugin hooks must not block the gateway event loop. |
| `test_finite_unattended_wire_grant.py` | B1-17: an unattended (auto-approving) finite turn is ``hermes -z`` only. Main set HERMES_YOLO_MODE inside the one-shot's own process; over the wire only the local bootstrap principal on its own CLI session may ask for i… |
| `test_finite_viewer_final_send.py` | Regression coverage for #139666 — a finite viewer's turn must not mark the reply ``already_sent`` off the stream consumer's transport confirmation. |
| `test_first_contact_dm.py` | A messaging gateway's first-ever DM carries the baseline profile-build offer. |
| `test_first_turn_session_meta_rebaseline.py` | Regression: first-turn ``session_meta`` row must be re-baselined into the agent cache's message_count snapshot. |
| `test_follow_profile_followups.py` | follow_profile_config follow-ups (andrexibiza C14-C18, C03): one profile read per turn, explicit create-time choices over followed defaults, a held pick still follows the rotated key, followed secrets are never recovere… |
| `test_follower_marker_handoff.py` | A queued follower is not claimed while the settled turn's crash marker is still with its adapter. |
| `test_footer_command_mid_run.py` | Regression: /footer must dispatch to its handler while an agent is running. |
| `test_foreign_stale_gateway_lock.py` | A gateway.lock this user cannot read, so cannot flock to prove unheld (a root run), is refused with a terminal reason and the exact recovery command, never guessed at. |
| `test_fresh_reset_skill_injection.py` | Regression tests for topic/channel skill auto-injection after /new or /reset. |
| `test_gateway_api_session_platform.py` | #134889 T22: a session created over the gateway's own API is platform ``LOCAL`` whether the client is on this host or remote (Desktop -> remote gateway). The platform is not renamed (stored rows and shipped client filte… |
| `test_gateway_api_token_exposure.py` | The always-on gateway HTTP listener must not hand its bearer token to any loopback peer. |
| `test_gateway_command_dispatch_minimal.py` | Tests: `_make_source`, `_make_event`, `_session_entry`, `_make_runner`, `test_idle_queue_sends_payload_as_next_turn` |
| `test_gateway_command_help.py` | Gateway command help rendering tests. |
| `test_gateway_command_line_matcher.py` | Tests for the strict gateway command-line matcher. |
| `test_gateway_delegation_mode.py` | Gateway delegation joins inside the turn when interim assistant messages are off. |
| `test_gateway_history_persistence_stamp.py` | Tests: `test_db_flush_collect_does_not_recollect_gateway_history_rows` |
| `test_gateway_inline_bootstrap_identity.py` | A gateway started through one of Hermes' own inline bootstraps is a gateway on every OS (#124318). |
| `test_gateway_liveness_home_guard.py` | A profile directory copied out of another HERMES_HOME must never read as running. |
| `test_gateway_mcp_oauth_unattended.py` | No gateway MCP path may start a browser OAuth flow (nobody can complete it), and the gateway tracks ``mcp_servers`` edits made after boot. |
| `test_gateway_platform_event_hook.py` | Tests for the ``gateway_platform_event`` observer hook (#64176's observer half). |
| `test_gateway_process_exit.py` | Tests: `_ExitCalled`, `_raise_exit`, `test_main_terminates_via_os_exit_not_systemexit`, `test_main_routes_systemexit_through_os_exit`, `test_exit_backstop_releases_pid_file_and_runtime_lock` |
| `test_gateway_serves_webapp.py` | The gateway's own listener serves the browser-hosted Desktop when ``webapp.enabled`` is on. |
| `test_gateway_shutdown.py` | Tests: `test_cancel_background_tasks_cancels_inflight_message_processing`, `test_cron_provider_stop_cannot_override_gateway_exit_code`, `test_gateway_stop_interrupts_running_agents_and_cancels_adapter_tasks`, `test_gate… |
| `test_gateway_silence_tokens.py` | Gateway intentional-silence token behavior. |
| `test_gateway_streaming_nested_config.py` | Regression test for #25676 — nested gateway.streaming config must be loaded. |
| `test_gateway_trust_env.py` | gateway.trust_env — one config key controls aiohttp proxy-env honoring at every adapter site (#48820). |
| `test_gateway_utf8_encoding.py` | Static guard: every ``read_text`` / ``write_text`` call in the gateway and bundled update-response adapters must pass an explicit ``encoding=`` keyword argument so non-UTF-8 Windows locales don't corrupt file IPC. Mirro… |
| `test_gateway_watchdog_host_sleep.py` | Gateway inactivity watchdogs must not charge host sleep (laptop lid closed) as turn idleness. |
| `test_goal_continuation_drain.py` | Regression: /goal continuations enqueued via the adapter FIFO are drained automatically — no extra user message required (#47699). |
| `test_goal_gate_access.py` | Gateway authorization tests for shell-backed goal quality gates. |
| `test_goal_max_turns_config.py` | Tests: `_FakeSessionEntry`, `_FakeSessionStore`, `_make_runner`, `_make_goal_event`, `test_gateway_goal_uses_goals_max_turns_from_full_config`, `test_goal_command_slow_db_init_still_persists` |
| `test_goal_resume_restart.py` | #75362 — /goal resume must restart work, not just flip persisted state. |
| `test_goal_status_notice.py` | Tests: `FakeAdapter`, `_goal_continuation_event`, `test_goal_status_notice_defers_until_post_delivery_callback` |
| `test_goal_verdict_send.py` | Tests for gateway /goal verdict-message delivery. |
| `test_google_chat.py` | Tests for Google Chat platform adapter. |
| `test_google_chat_oauth_dependencies.py` | Google Chat dependency installation crosses PM's declared-feature interface. |
| `test_grid_sweep_gateway_diagnostics.py` | Code-flow grid sweep (NOUS-368, wave 1): three pre-existing automatic gateway diagnostics that bypassed the warning boundary. absent/false = legacy bytes; true suppresses ONLY the diagnostic; requested outcomes (an in-c… |
| `test_handoff_completion_parent_context.py` | A process a subagent hands to its parent completes into a PARENT turn, in the parent's context. |
| `test_handoff_local_receipt.py` | A local chat handed off to a messaging lane keeps opening there (#143286). |
| `test_handoff_owned_recovery.py` | A row a COMPLETED ``/handoff`` owns must stay recoverable even when the source interface's teardown stamps a non-recoverable ``end_reason`` (``cli_close``) after ownership moved to the gateway; otherwise the stale-route… |
| `test_handoff_secondary_profile_adapter.py` | A secondary profile's handoff must deliver through ITS OWN adapter/config. |
| `test_handoff_thread_session_key.py` | Regression: CLI→Discord handoff must key a thread destination on the thread's OWN id, matching how the platform adapter keys organic in-thread messages. |
| `test_handoff_watcher_async_db.py` | Regression test for #40695 (salvage of keystone PR #40782). |
| `test_handoff_watcher_multiprofile.py` | Handoff watcher must poll EVERY served profile's store, not just the root. |
| `test_handoff_watcher_resilience.py` | Handoff watcher resilience: no head-of-line blocking, no stranded rows. |
| `test_heartbeat_acceptance.py` | An adapter slot is not proof a heartbeat reached execution. |
| `test_heartbeat_execution_ownership.py` | Admitted heartbeat work belongs to a conversation, not a reusable route. |
| `test_heartbeat_inflight_owner_scan.py` | The heartbeat poller coalesces behind an in-flight heartbeat admission wherever it lives: on the route's logical owner after compression, and as a LOCAL route's local_automation_v1 row. |
| `test_heartbeat_poller.py` | Heartbeat polls wake idle adapters, never accumulate deferred ticks. |
| `test_heartbeat_session_boundaries.py` | Heartbeat ownership follows compression, but ends at a conversation boundary. |
| `test_heartbeat_watch_lifecycle.py` | Heartbeat watches follow their route and profile, not the poller's creator. |
| `test_heartbeat_watch_restore.py` | Restart recovery uses current routing and never borrows another profile's heartbeat. |
| `test_history_media_current_turn.py` | Regression: current-turn TTS media must not be dedup-stripped (#B, staging 2026-07-29). |
| `test_hold_stream_api_server.py` | API server: a ``hold_stream`` redactor's session streams no raw text to OpenAI-compatible clients. |
| `test_hold_stream_codex_failure.py` | A held Codex turn reaches the chat only as the rewrite, also when the subprocess failed after its agentMessage completed (the gateway still delivers that text). Real GatewayRunner and final-send path; only the external… |
| `test_hold_stream_delivery.py` | A ``hold_stream`` plugin's session shows the user only the rewritten final, on every chat shape. |
| `test_hold_stream_local_viewer.py` | TUI, Desktop and the classic CLI (local viewers of the canonical gateway) show a held reply only as its rewrite. |
| `test_home_target_env_var.py` | Regression tests for /sethome env-var resolution. |
| `test_hook_consent_resync.py` | #132993: a running gateway registers a shell hook once its consent is recorded, and drops it once revoked, without a restart or a session open, for the launch profile of a single-profile gateway and for a profile a mult… |
| `test_hooks.py` | Tests for gateway/hooks.py — event hook system. |
| `test_host_attach_lifecycle.py` | The gateway lifecycle verbs mean "the ONE host process", not "this profile's gateway". |
| `test_host_attach_standalone.py` | A configured standalone profile may coexist, but never double-bind a served profile. |
| `test_host_gateway_lock_refusal.py` | The host gateway lock REFUSES a second gateway instead of observing it (multiplex-only). |
| `test_host_gateway_profile_env.py` | A host gateway spawned from a profile-scoped process must not adopt that profile. |
| `test_host_rendezvous.py` | Host-wide singleton invariants (multiplex-only): one lock per host, staleness is proved. |
| `test_host_rendezvous_windows.py` | Windows confidentiality for the host rendezvous token + lock (``platforms("windows")``). |
| `test_host_topology.py` | Host topology: the DEFAULT profile is a served profile, not a special owner. |
| `test_hosted_attachment_bridge.py` | Tests: `test_authorized_upload_send_download_and_task_consumption`, `test_rpc_accepts_only_bound_manifest_after_producer_authorization` |
| `test_hosted_clarification_refusal.py` | Persisted hosted policies decline a question without a reply channel; local ones still ask. |
| `test_hosted_discussion_manifests.py` | Exact event-bound media survives deterministic planning and reconstruction. |
| `test_hosted_document_custody.py` | Hosted non-image documents are retained inputs like any other: the native GC's holder scan keeps the bytes a live hosted row still needs, and the row's own terminal release collects them. |
| `test_hosted_group_members.py` | Which local bots a Desktop group may seat, on a default install with no ``hosted_rooms`` key. |
| `test_hosted_mux_runtime.py` | Hosted multiplexing through real owners and private sockets, without inference. |
| `test_hosted_observation_bounded.py` | Cross-profile hosted observation stays bounded when the member transcript is large. |
| `test_hosted_room_attachment_publication.py` | Canonical message insertion and attachment rollback share one write fence. |
| `test_hosted_room_attachments.py` | Tests: `_put`, `_manifest`, `test_store_is_private_atomic_deduplicated_and_upload_idempotent`, `test_orphan_sweep_serializes_with_concurrent_canonical_blob_commit`, `test_upload_id_conflict_and_manifest_metadata_conflic… |
| `test_hosted_room_auth_daemon.py` | Hosted rooms over real OIDC-authenticated ordinary daemon sockets: one owner, many tabs. |
| `test_hosted_room_discussion.py` | Behavior tests for deterministic same-gateway Discussion policy. |
| `test_hosted_room_driver.py` | Behavior tests for the hosted-room driver state machine. |
| `test_hosted_room_execution_policy.py` | Target-issued execution-policy regressions for text-only RoomLink turns. |
| `test_hosted_room_expired_commit.py` | Expired staged bytes cannot be revived by a delayed share. |
| `test_hosted_room_file_refusal.py` | A member's bound file is prepared before its turn is submitted, on both server routes. |
| `test_hosted_room_gateway_lifecycle.py` | Messaging-gateway ownership tests for the hosted Group Chat worker. |
| `test_hosted_room_handoff_send.py` | A Group Chat the gateway took over keeps answering, and a stored Send is never reported as failed. |
| `test_hosted_room_links.py` | Private negotiated RoomLink storage tests. |
| `test_hosted_room_member_binding.py` | A per-member hosted producer refuses a submit that names another member. |
| `test_hosted_room_peer.py` | Contracts for autonomous cross-gateway hosted-room members. |
| `test_hosted_room_replicas.py` | Tests for gateway/hosted_room_replicas.py — replica ingest, promotion, and stale-authority demotion for hosted Group Chat rooms. |
| `test_hosted_room_retention_restart.py` | Real process reopen and SQL failures preserve the accepted file boundary. |
| `test_hosted_room_runtime_attachments.py` | The canonical authority route still carries a member turn's bound file end to end. |
| `test_hosted_rooms.py` | Behavior tests for the gateway-hosted room event log. |
| `test_hosted_rooms_gateway_import.py` | The gateway takes over the standalone backend's Group Chats once, and each room keeps one driver (WA-19). |
| `test_hosted_rooms_read_path.py` | Focused lock-behavior coverage for hosted Group Chat reads. |
| `test_hosted_submission_capture_lease.py` | A hosted-room submission holds the documents it captured until its admission commits. |
| `test_housekeeping_profile_scope.py` | Housekeeping chores that read a profile's home, config or credentials run under the OWNING profile's runtime scope on a multiplexed gateway. |
| `test_hygiene_compaction_keeps_seeded_prompt.py` | Gateway hygiene / gateway /compress must not persist a reduced-toolset prompt over a live session. |
| `test_hygiene_compaction_trigger_label.py` | Each automatic compression entry point names itself in the attempt record. |
| `test_hygiene_deferred_work_drain.py` | Shutdown accounting for executor work detached by hygiene timeouts. |
| `test_hygiene_failure_cooldown_ladder.py` | Session-hygiene compression must escalate its cooldown for repeat failures. |
| `test_hygiene_no_commit_reason.py` | Hygiene adopt step: an uncommitted attempt keeps the transcript, a committed in-place one is adopted (#71097). |
| `test_hygiene_wait_moved_deadline.py` | The gateway's hygiene wait follows the compression fence when prompt reading moves its deadline. |
| `test_hygiene_warning_lifecycle.py` | Real hygiene turn admission, durable cooldown and notice sink in three modes. |
| `test_identity_canonical_ingress.py` | Identity is canonicalized FIRST on every ingress path (#88715 phase 3). |
| `test_image_input_routing_runtime.py` | Tests: `_make_runner`, `_source`, `_image_event`, `_auto_config`, `test_pre_turn_named_custom_provider_identity_selects_vision_override`, `test_prepare_route_identity_check_keeps_event_loop_responsive` |
| `test_import_preserves_tui_cwd.py` | Importing gateway helpers must not apply messaging-only cwd defaults. |
| `test_inactivity_timeout_receipt.py` | A watchdog timeout remains failed when the handler projects its diagnostic as text. |
| `test_inbound_media_profile_scope.py` | Inbound attachments on a multiplexed gateway live in the ROUTED profile's cache (#101134). |
| `test_incomplete_gateway_turns.py` | Regression tests for hidden-reasoning-only incomplete gateway turns. |
| `test_ingress_admission_off_loop.py` | Ingress admissions commit off the owner loop: a SQLite writer held by another process must not freeze every session, timer and socket while a producer waits for its ACK (andrexibiza-21, JoaoMarcos44-R7). One row per ing… |
| `test_ingress_binding_user_id_route.py` | Regression: a profile route declared by ``user_id`` must resolve inside admission. |
| `test_interactive_prompt_base.py` | Tests for the shared interactive-prompt formatting cores in BasePlatformAdapter. |
| `test_interim_only_consumer_warning.py` | Regression coverage for #105341 — interim-only stream consumers must not fire the duplicate-send diagnostic. |
| `test_interim_send_lanes.py` | Regression: every gateway-side mid-turn send lane is marked interim (PR 85796 review, B5 + heartbeat/inactivity findings). |
| `test_internal_event_bypass_pairing.py` | Tests that internal synthetic events (e.g. background process completion) bypass user authorization and do not trigger DM pairing. |
| `test_internal_event_never_interrupts_busy_session.py` | Regression test: internal synthetic events must never interrupt a busy session. |
| `test_internal_event_pin_wiring.py` | Call-site wiring guard for the internal-event session-context pin. |
| `test_internal_notification_marker.py` | Regression tests for #82888 — internal synthetic turns are persisted typed. |
| `test_internal_wake_never_interrupts.py` | An internal wake never interrupts or steers an admitted user turn (N44, sequence 1). |
| `test_internal_wake_reply_anchor.py` | An internal (synthetic) wake never reply-anchors to its ``message_id``. |
| `test_interrupt_keeps_parked_internal_wake.py` | Invariant: interrupting a session (/stop, /new, /reset) discards a parked human follow-up but never a parked internal wake (async-delegation completion, notify+wake). See #114456. |
| `test_irc_adapter.py` | Tests for the IRC platform adapter plugin. |
| `test_journey_compress_restart_fifo.py` | Journey: queued followers -> automatic compression -> gateway restart before drain. |
| `test_journey_new_session_queued_work.py` | Journey: client `/new` while the earlier session still holds durable queued work. |
| `test_journey_restart_open_prompts.py` | Journey: restart while one session waits on an approval and another on a clarification. |
| `test_kanban_auto_decompose_live.py` | Tests for live auto-decompose settings resolution (issue #49638). |
| `test_kanban_auto_decompose_secret_scope.py` | Auto-decompose tick under multiplex. |
| `test_kanban_changes_requested_notifier.py` | Tests: `RecordingAdapter`, `_run_one_tick`, `_runner`, `_create_review_block`, `_unseen`, `test_changes_requested_notify_wake_is_actionable_and_exactly_routed` … |
| `test_kanban_finite_admission.py` | Regression for #138992: dispatched cards retain headless approval semantics. |
| `test_kanban_multiplex_served_profile_parity.py` | Standalone-vs-served parity for the kanban dispatcher and notifier under ``gateway.multiplex_profiles``: a worker spawned for served profile X gets the env a standalone ``hermes -p X`` dispatcher would build, and X's no… |
| `test_kanban_notifier.py` | Tests: `RecordingAdapter`, `DisconnectedAdapters`, `_run_one_notifier_tick`, `_make_runner`, `_create_completed_subscription`, `_unseen_terminal_events` … |
| `test_kanban_notifier_apiserver_wake.py` | Kanban notifier behavior on stateless (api_server) subscriptions. |
| `test_kanban_notifier_served_apiserver_wake.py` | A served profile's multiplexed ``api_server`` Kanban wake delivers in-process, in its own scope. |
| `test_kanban_notifier_wake_only_ordering.py` | Wake-only (delivery_mode='wake') push-adapter delivery ordering. |
| `test_kanban_notifier_watcher_dispatch_gate.py` | Notifier polling has an independent gateway config gate. |
| `test_kanban_notifier_zero_sub_gate.py` | Tests for the kanban notifier zero-subscription early exit. |
| `test_kanban_reconcile_orphans.py` | Tests: orphaned-card reconciliation for the kanban dispatcher. |
| `test_kanban_recovery.py` | Real dispatch preserves custom board identity and unknown attempts. |
| `test_kanban_result_exit.py` | Canonical Kanban receipts retain the shared one-shot outcome semantics. |
| `test_kanban_route_anchor_capture.py` | Route anchors survive gateway background/subprocess producers without stale fallback. |
| `test_kanban_routed_transport.py` | Persisted notification routes authorize exactly one transport, including route-only profiles. |
| `test_kanban_wake_acceptance.py` | Push admission and durable notifier retries use real adapter/SQLite lifecycles. |
| `test_kanban_wake_scope.py` | Kanban wake events must key to the same session as inbound messages. |
| `test_keep_typing_timeout.py` | Tests for BasePlatformAdapter._keep_typing timeout-per-tick behavior. |
| `test_late_plugin_rewire.py` | #87770 — plugins loaded after the gateway started get their platform handlers wired. |
| `test_launch_credentials_refusal_copy.py` | A chat whose own route key changed since it started is refused by design (a session never sends a different key than it started with). The refusal must name the way out (/new), never /retry. |
| `test_launch_key_resume_rebind.py` | A launch-only key revoked by an owner restart can be re-supplied on session.resume, and only the key the session was launched with (its durable fingerprint); never persisted. |
| `test_launch_profile_scope_fallback.py` | Who owns a body with no routed profile home — and who must NOT. |
| `test_launch_secret_retirement.py` | Deleting a local session drops the launch key and frozen config secrets it held in memory. |
| `test_launchd_exit_timeout_drain_cap.py` | Signal-driven stops under launchd must fit the live ``ExitTimeOut``. |
| `test_legacy_acp_route.py` | A thread main's in-process ACP server wrote resumes on the route it saved (``model_config``). |
| `test_legacy_desktop_source.py` | Every old local row the native resume adopts also takes a sidebar edit (#106742). |
| `test_legacy_session_continue_label.py` | Continuing an adopted pre-authority session keeps the label main wrote on its row (T20). |
| `test_legacy_session_migration.py` | Pre-authority rows never grant ownership to the first remote claimant. |
| `test_legacy_session_owner_backfill.py` | The owner migrates pre-ownership NULL session rows itself (#94724). |
| `test_legacy_session_route_turn.py` | #138912: a session a pre-0.22.1 surface wrote resumes on ITS route, with only that route's credential. |
| `test_legacy_session_row_parity.py` | Resuming a session main created leaves its row as main would (TUI parity, PR #106742 row 35). |
| `test_legacy_stamped_bot_chat.py` | RT-32 (#140156): Desktop's Bot Chat lookup adopts a legacy local row stamped with the caller's own subject. |
| `test_lifecycle_ledger.py` | Tests for gateway.lifecycle_ledger — unclean-shutdown detection (NS-608). |
| `test_lifecycle_state_db_check.py` | An unclean gateway death must trigger a state.db integrity check. |
| `test_line_plugin.py` | Tests for the LINE platform adapter plugin. |
| `test_live_settlement_recovery.py` | An owner that is still alive must expose a failed settlement as recoverable uncertainty. |
| `test_load_transcript_db_only.py` | Verify load_transcript returns SQLite messages without any JSONL file. |
| `test_local_authority_transitions.py` | Local mutation replay and pause episodes respect the durable FIFO; ``local_session`` is shared. |
| `test_local_automation.py` | Local automation belongs to the owner, never an attached client. |
| `test_local_chat_delivery.py` | Producers that target a local (Desktop/TUI/CLI) chat reach its owner's FIFO (#143547 KB-22, RT-90, CRON-11). |
| `test_local_context_ref_session_cwd.py` | ``@`` references on a local (CLI/TUI/Desktop) session resolve in that session's cwd. |
| `test_local_context_ref_turn_text.py` | ``@`` references reach the model on every local route now that the classic CLI leaves them to the gateway: its API-only text (voice prefix, model-switch notes), managed workers (``--safe-mode`` / ``--ignore-user-config`… |
| `test_local_control_compression_child.py` | Rename and archive of a cold compressed local conversation by its physical id (LC-22). |
| `test_local_create_alias_retry.py` | An exact retry of an alias ``session.create`` is the same request whatever the owner's ``.env`` now expands the alias to: retry identity is what the client sent (the alias name and its own fields), checked the same way… |
| `test_local_create_env_refs.py` | A new local session expands ``config.yaml`` ``${VAR}`` refs against the profile's CURRENT ``.env`` (the source tool env already refreshes from), not the daemon's start-time ``os.environ`` (CFG-4). |
| `test_local_debug_never_uploads.py` | ``/debug local`` on a local session never uploads (T7). |
| `test_local_desktop_identity.py` | Who counts as the Desktop app on this machine, on the unified gateway. |
| `test_local_desktop_ui.py` | Desktop window bridges for a local viewer's turn on the session authority. |
| `test_local_display_key.py` | ``/reasoning show\|hide`` and ``/footer`` on a local session take effect on every local surface (T7). |
| `test_local_goal_gate_owner_admin.py` | ``/goal gate add`` on a local session: its owner counts as the admin (T7). |
| `test_local_live_route_heal.py` | A live local session whose route entry the loaded store cannot see rebuilds it from its receipt. |
| `test_local_moa_then_refine.py` | ``/moa`` then ``/refine`` on a local session (T7). |
| `test_local_model_connection_reply.py` | Regression tests for #86570 / #116323: gateway provider error connection messaging. |
| `test_local_producer_admission.py` | Background producers reach the chat that started them, through the real authorities, adapters, turn path and SQLite. Only the model call is stubbed; it records the frozen session policy each turn resolved. Regression co… |
| `test_local_reasoning_projection.py` | Tests: `test_local_final_does_not_receive_platform_reasoning_projection` |
| `test_local_receipt_missing_profile.py` | Regression for #140099: old local receipts omit the served profile in origin. |
| `test_local_receipt_untracked_compression.py` | A local session created under 0.22.1 and then used under 0.22.2 opens again on the gateway (#140060). |
| `test_local_recovery_pre_profile_origin.py` | A served profile's refused local receipt names its failing check in gateway.log (#140099). |
| `test_local_refine_keeps_session_resources.py` | A cold ``/refine`` on a local session leaves the session's tool resources alone (T7). |
| `test_local_refine_review_guard.py` | A cold ``/refine`` review belongs to the session, not to its throwaway side agent (T7). |
| `test_local_refine_skips_memory_provider.py` | A cold ``/refine`` on a local session never builds or starts an external memory provider. |
| `test_local_reset_lineage_one_conversation.py` | N18: a local reset lineage is ONE conversation in the listing, the gateway delete and the legacy store delete (creation id S0 owns policy/FIFO; the transcript moved to reset child S1). |
| `test_local_restore_lock_free.py` | Restoring a live local session never waits on the SessionStore lock when its route is already current. |
| `test_local_resume_compression_child.py` | ``session.resume`` by a compressed local conversation's physical transcript id (LC-12, #139306). |
| `test_local_review_summary_event.py` | A local viewer sees the background review's summary as a ``review.summary`` event. |
| `test_local_review_without_cached_agent.py` | ``/review`` on a local session whose cached agent is gone. |
| `test_local_route_orphan_reap_stamp.py` | A local route the authority owns keeps its conversation when its row is stamped ended (#140642). |
| `test_local_session.py` | Fresh sessions use the composed authority, real TurnRunner and local tools. |
| `test_local_session_info_fields.py` | ``session.info`` carries what main's classic CLI read off itself for /status, the status bar and the exit summary (wave A2): title, started/last-active times, yolo, api_mode, tool_count and a masked credential hint (nev… |
| `test_local_session_lineage.py` | A local conversation keeps one admission owner across physical transcript boundaries. |
| `test_local_session_orphan_end.py` | Local sessions nobody closed end on the gateway, and only open ones come back at boot (#143547). |
| `test_local_session_recovery.py` | Local creation is durable before publication and restart never replays a claim. |
| `test_local_session_voice_tts.py` | A local session's ``/voice tts`` must not make the owner synthesize audio. |
| `test_local_source_labels.py` | A canonical local session keeps the source label it was created with, and human pickers hide the non-conversation labels (``tool`` integrations, finite ``oneshot`` runs) as on the classic surfaces. |
| `test_local_turn_origin_execute_code_gate.py` | Which turns of a local session skip the whole-script ``execute_code`` approval (T2). |
| `test_local_viewer_clarify_batch.py` | A classic-CLI viewer's clarify batch goes out as ONE ``clarify`` request (main's batch panel shows every question at once); the messaging path still asks one card per question. |
| `test_local_viewer_events_submit.py` | The classic CLI's per-turn ``prompt.submit`` fields survive canonical admission (CALLMAP W2). |
| `test_local_viewer_events_turn.py` | Local-viewer turn events the classic CLI renders through its own callbacks (CALLMAP W1). |
| `test_local_viewer_reasoning.py` | Reasoning a local viewer's turn sends Ink and Desktop: the live stream by default, the final reasoning on ``message.complete``, and never the messaging platforms' reasoning block in the reply text. |
| `test_local_viewer_secret_prompt.py` | A local viewer's turn asks for a skill's missing env var through main's masked secret panel (``secret`` server→client request), and the gateway saves the answer in the profile ``.env``. Before, a gateway surface only re… |
| `test_local_viewer_status_notice.py` | A local viewer sees the agent's status lines and notices, as main's TUI and CLI showed them. |
| `test_local_viewer_sudo_prompt.py` | A local viewer's turn asks for the sudo password through the TUI's masked prompt, as main's sidecar did (``tui_gateway/agent_callbacks.py`` ``set_sudo_password_callback``): FINDINGS row 9, where the canonical owner regi… |
| `test_local_viewer_transformed_final.py` | A ``transform_llm_output`` rewrite reaches a local viewer (Ink TUI, Desktop) on ``message.complete``. |
| `test_local_viewer_usage.py` | ``session.usage`` / ``session.stats``: the session-cumulative counters main's HermesCLI read off its in-process agent (status bar, /usage, exit summary), published from the gateway (wave A2, CALLMAP W3). |
| `test_local_viewer_vault_prompt.py` | A local viewer's turn asks for browser-vault input (a site's one-time code, a login to save, a password manager's master password) through the Desktop/Ink cards, as main's sidecar did (``tui_gateway/agent_callbacks.py``… |
| `test_local_yolo_cold_restore.py` | An explicit /yolo OFF on a local session survives a cold owner restore of its creation receipt. |
| `test_login_command.py` | Tests: `_source`, `_runner`, `_event`, `_finish_tasks`, `test_non_direct_chats_are_refused_without_starting_anything`, `test_a_dm_without_a_chat_id_is_refused` … |
| `test_loop_command.py` | Gateway /loop command tests — dispatch, routing capture, mid-run guard. |
| `test_loop_exception_handler.py` | Tests for the gateway loop-level transient-network-error safety net. |
| `test_loop_liveness_watchdog.py` | Gateway event-loop freeze backstops for issue #69089. |
| `test_lost_worker_receipt_compaction.py` | A managed worker closed by loss or by a reset's orphan discard keeps no full-history read receipt (dokterdok N41, the N19 residual): every terminal path compacts like execution.finish. |
| `test_managed_runtime_live_drain.py` | A real managed child persists its final receipt while the ordinary daemon drains. |
| `test_managed_spawn_cancellation.py` | Cancelling threaded Popen acquisition still reaps the child it eventually creates. |
| `test_managed_turn_contract.py` | Managed turns carry finite approval policy, accounting, and live tool details. |
| `test_managed_turn_shutdown_drain.py` | R10: managed-worker turns are part of the bounded shutdown drain. |
| `test_managed_unstarted_cancel.py` | Cancellation before reservation closes any acquired child and settles the unexecuted claim. |
| `test_managed_worker_background_output.py` | A background process a managed worker starts keeps its output past the worker's exit. |
| `test_managed_worker_bypass.py` | Bypass sessions execute in the admission-owned worker, which binds the safe policy first. |
| `test_managed_worker_checkpoint_limits.py` | A managed worker builds its agent with the session's frozen checkpoint limits, not only the enable flag (andrexibiza 27 / P3.b, kshitijk4poor): ``max_snapshots`` reaches the store's trim. |
| `test_managed_worker_clarify_timeout.py` | A managed worker's clarify wait honours the profile's clarify timeout (<= 0 = unlimited). |
| `test_managed_worker_client_env.py` | T3 / LC-8 on a real gateway: CLI sessions attached through the gateway's own ticket run their tools in managed workers under their client's toolchain, and the client environment never shows in a public projection (sessi… |
| `test_managed_worker_construct.py` | Managed execution gets the same owner-resolved agent-construction inputs as the in-process turn (``construct_v1``): the configured fallback chain (andrexibiza N3) and the configured instruction + prefill examples (andre… |
| `test_managed_worker_delegation.py` | delegate_task inside a managed worker (#141793): real daemon, real worker, loopback model. |
| `test_managed_worker_detached_work.py` | A managed worker exits at its turn boundary, so it must never hand out detached work. |
| `test_managed_worker_drain.py` | Already-reserved compute remains able to persist while new work is refused. |
| `test_managed_worker_env_boundary.py` | Managed worker boundary: a worker FOR another profile never inherits the launch profile's credentials, and a ledger id never names a path outside worker-outboxes (PR #106742 security lane). |
| `test_managed_worker_fencing.py` | Loss is not success; delayed parent results cannot revive an admission. |
| `test_managed_worker_finished_exit.py` | A managed turn whose worker acknowledged its durable finish keeps its answer even when the worker's interpreter is slow to exit or exits non-zero afterwards (interpreter teardown, a lingering non-daemon thread, a Window… |
| `test_managed_worker_frozen_config.py` | An ordinary managed worker serves its session's frozen config, never the live profile file. |
| `test_managed_worker_group_close.py` | Owner-initiated managed-worker teardown reaps the worker's process group (N55). |
| `test_managed_worker_hard_stop_frame_fence.py` | Managed-worker Stop parity and per-frame fence (N84 / B1-11 follow-ups). |
| `test_managed_worker_hooks.py` | Ordinary managed runs register the session's shell hooks and outbound webhooks in the worker, where tools and model calls actually run (unsupportedpastels §2.4); bypass sessions register none. |
| `test_managed_worker_images.py` | A managed assignment preserves the image bytes committed at admission. |
| `test_managed_worker_kill_escalation.py` | close() always finishes its teardown: a worker whose handle still has not exited five seconds after SIGKILL (a Windows launcher, an uninterruptible exit) must not raise out of close() and leave the pipes, reader and std… |
| `test_managed_worker_late_stop.py` | A Stop requested long after hello still receives its full acknowledgement window: only the first actual Stop opens the budget, and repeated Stops share that one deadline (real child). |
| `test_managed_worker_launch.py` | The ordinary daemon, not a fixture launcher, owns the real tool worker. |
| `test_managed_worker_lineage.py` | Real owner parity: stable admission IDs, physical history and terminal publication. |
| `test_managed_worker_parent_death.py` | A managed worker dies with its owner, descendants included, even when its turn ignores the interrupt (andrexibiza 29 / P3.g). The owner spawns it in its own session; the owner's death closes the control pipe, and the wo… |
| `test_managed_worker_profile_env.py` | A served secondary profile's managed worker never inherits launch-profile residue. |
| `test_managed_worker_reader_thread.py` | Managed-worker pipe reads never occupy the loop's shared default executor: with as many parked (silent) workers as the pool has threads, an unrelated ``asyncio.to_thread`` still runs, and a cancelled read never leaves a… |
| `test_managed_worker_reservation_off_loop.py` | The managed worker's reservation and loss writes run off the owner loop (B1-13): a state.db writer held by another process (up to _WRITE_PATIENCE_S) must not freeze every other session, timer, socket and Stop on the loo… |
| `test_managed_worker_result_usage.py` | A managed turn's receipt keeps its spend: the worker's result frame carries the bounded accounting fields of ``run_conversation`` and the owner commits them with ``usage``, so ``-z --usage-file`` on a managed session re… |
| `test_managed_worker_retire.py` | A managed worker's turn-final memory work drains before the provider shuts down. |
| `test_managed_worker_route_key.py` | A managed worker without a launch key (every Kanban run) resolves its route's credential the way the in-process runner does (``_resolve_policy_agent_runtime``), so an ``anthropic_messages`` provider other than Anthropic… |
| `test_managed_worker_routing_kwargs.py` | A managed worker (every Kanban run, opt-in CLI sessions) builds its agent with the session's provider routing and service tier, as ``hermes chat`` did on main (``HermesCLI._init_agent``): ``provider_routing.ignore``/``d… |
| `test_managed_worker_rpc_close.py` | A managed worker closes its owner connection when ``execute`` ends, after the store, on success and on a start failure; a failing close never replaces the turn's own outcome. |
| `test_managed_worker_stderr_log.py` | Managed-worker stderr (its tracebacks and redirected prints) lands in the owning profile's private, redacted, size-capped ``logs/managed-worker.log`` instead of being discarded. |
| `test_managed_worker_stop_before_hello.py` | Stop is never acknowledged into a queue nobody drains: a managed child that stays alive without ever sending hello is terminated on Stop and the admission settles as interrupted. |
| `test_managed_worker_stop_deadline.py` | Stop bounds managed-worker supervision by ONE deadline from the first Stop: a child that keeps emitting valid frames after Stop is escalated on the same budget as a silent one (real child). |
| `test_managed_worker_tool_events.py` | A managed worker's tool events reach every viewer in the shape an in-process turn publishes. |
| `test_managed_worker_trampoline.py` | Worker identity is verified by the owner through launcher chains, never asserted by the worker. |
| `test_managed_worker_turn_author.py` | A managed worker's turn carries its author so memory providers attribute it like the owner path. |
| `test_managed_worker_turn_flags.py` | A managed worker applies the same per-turn approval facts as the in-process turn: the admission's one-shot flags (``chat -q`` / ``-z``) and the route's current YOLO bypass, including its revocation. |
| `test_managed_worker_unknown_status.py` | A lost managed worker's message.complete carries the contract's error TurnStatus next to outcome 'unknown' (N117), so a client that renders by status never shows a normal finish. |
| `test_matrix.py` | Tests for Matrix platform adapter (mautrix-python backend). |
| `test_matrix_approval_reaction_fail_closed.py` | Tests for Matrix adapter fail-closed approval reaction auth. |
| `test_matrix_crypto_store_per_profile.py` | Matrix crypto store must be pinned per profile at connect(), not at import. |
| `test_matrix_deps_rebind.py` | Regression: ensure_matrix_deps() fresh-dependency rebind must not NameError. |
| `test_matrix_dm_invite_recording.py` | Tests for Matrix DM room recording on invite (issue #44679). |
| `test_matrix_encrypted_drop_warning.py` | Matrix fails loud when encrypted room events arrive with no E2EE decryptor (#131778). |
| `test_matrix_exec_approval.py` | Tests: `TestMatrixExecApprovalReactions` |
| `test_matrix_handoff_thread.py` | Tests for MatrixAdapter.create_handoff_thread. |
| `test_matrix_latex_maths.py` | Outbound ``$...$`` / ``$$...$$`` become Element ``data-mx-maths`` markup (#106458). |
| `test_matrix_media_filename.py` | Tests for Matrix adapter media-filename blanking. |
| `test_matrix_media_gate_before_download.py` | Matrix must gate (require_mention / allowed rooms) BEFORE downloading inbound media. |
| `test_matrix_mention.py` | Tests for Matrix require-mention gating and auto-thread features. |
| `test_matrix_message_event_metadata.py` | Tests for Matrix MessageEvent metadata (sender, reply context). |
| `test_matrix_message_length.py` | Tests for Matrix outbound message length configuration (#53026). |
| `test_matrix_pending_invite_auth.py` | Tests for the inviter allowlist gate on pending-invite reconciliation. |
| `test_matrix_plugin_setup.py` | Tests for the Matrix plugin's interactive_setup wizard home-channel flow. |
| `test_matrix_project_context_isolation.py` | Matrix Project A / Project B context-isolation regressions. |
| `test_matrix_recovery_key_scope.py` | Regression test for #69090: MATRIX_RECOVERY_KEY must honor the active profile's secret scope under ``gateway.multiplex_profiles`` so that a secondary profile resolves its own recovery key (not the default profile's), ot… |
| `test_matrix_send_voice_dispatch.py` | Regression tests for Matrix ``send_voice`` dispatch compatibility (#116776). |
| `test_matrix_voice.py` | Tests for Matrix voice message support (MSC3245). |
| `test_mattermost.py` | Tests for Mattermost platform adapter. |
| `test_mattermost_native_admission.py` | Mattermost posts pass native admission and run a turn, with or without attachments. |
| `test_mattermost_plugin_setup.py` | Tests for the Mattermost plugin's interactive_setup wizard home-channel flow. |
| `test_max_concurrent_sessions.py` | Tests for the gateway max_concurrent_sessions active-session cap. |
| `test_mcp_reload_held_revision.py` | A ``reload.mcp`` that names the revision the calling session already holds has nothing left to load: it answers the success shape (naming the configured server that is down) instead of the named refusal, so a client tha… |
| `test_mcp_reload_new_server.py` | CFG-3: an MCP server added to a profile's config after a local session started reaches that session only through a gateway-committed policy generation (``reload.mcp`` for the calling idle session, or the CFG-2 refresh w… |
| `test_mcp_reload_refreshes_cached_agents.py` | Regression test for /reload-mcp refreshing cached agent tool lists. |
| `test_mcp_shutdown_profile_passes.py` | MCP teardown at shutdown: the caller's budget is divided, and the wildcard pass is not poisoned. |
| `test_media_cache.py` | Contract tests for gateway.platforms.media_cache — the shared mime↔ext dispatch — plus per-adapter parity spot-checks that hardcode each adapter's HISTORICAL (pre-refactor) mappings as the contract. |
| `test_media_cache_cleanup_signature.py` | Every cache cleanup the gateway housekeeping loop iterates accepts the loop's call shape. |
| `test_media_download_retry.py` | Tests for media download retry logic added in PR #2982. |
| `test_media_extraction.py` | Tests for MEDIA tag extraction from tool results. |
| `test_media_metadata_contract.py` | Contract: media-send overrides must accept the ``metadata`` kwarg. |
| `test_media_only_outcome.py` | Regression tests for #106153 — media-only turns reported FAILURE. |
| `test_media_resend_dedup.py` | Regression tests for #73771 — session-wide MEDIA dedup swallowing explicit resend requests. |
| `test_media_spaced_paths_and_history_dedupe.py` | Regression tests: spaced paths, GIS extensions, cross-turn dedupe plumbing, and code-block-safe streaming display strip. |
| `test_media_tag_cleanup.py` | Tests for MEDIA_TAG_CLEANUP_RE regex matching behavior (#63632). |
| `test_media_tag_formatting_variants.py` | Regression tests: MEDIA tag formatting variants that previously broke delivery. |
| `test_media_tag_separator.py` | Regression tests for #68773 — MEDIA tags without a separator merge paths. |
| `test_media_terminal_sentinel.py` | A leaked terminal ``<\|eos\|>`` sentinel must not hide a MEDIA attachment (#111046). |
| `test_memory_flush_on_reset.py` | Regression tests for #73297: memory rollback after /reset. |
| `test_memory_monitor.py` | Tests for gateway.memory_monitor — periodic process memory logging. |
| `test_memory_status.py` | Tests for gateway.memory_status — the /api/status memory rollup (NS-656). |
| `test_memory_trim_housekeeping.py` | Memory-trim coverage for the long-lived messaging gateway housekeeper. |
| `test_message_deduplicator.py` | Tests for MessageDeduplicator TTL enforcement (#10306). |
| `test_message_timestamps.py` | Tests: `_epoch`, `test_render_numeric_timestamp_preserves_instant_in_system_timezone`, `test_early_naive_iso_preserves_system_local_instant`, `test_early_embedded_local_time_preserves_instant`, `test_early_embedded_loca… |
| `test_messaging_discard_reach.py` | Messaging ``/discard`` reaches every lost turn it promises to (review #141357, GW-10). |
| `test_messaging_new_drops_claimed_turn.py` | A /new between the drain's claim and the turn's session lookup drops the claimed turn. |
| `test_messaging_refine_without_cached_agent.py` | Messaging ``/refine`` on a session whose cached agent is gone. |
| `test_messaging_session_moved_on.py` | Messaging-session reads after the conversation moved on (RT-18, TUI-19 on messaging rows, #134889). |
| `test_messaging_session_picks.py` | Desktop/TUI model and reasoning picks on a messaging chat (#141152). |
| `test_messaging_slash_command_fifo.py` | A slash command that becomes a turn (``/queue``, ``/steer``, ``/plan``, a skill) joins the chat's durable FIFO like text, so it runs after the turns already admitted, never inside the running one. |
| `test_messaging_stop_new_cancel_queued.py` | Messaging /stop and /new drop the durable queued follow-up, as main dropped the adapter slot. |
| `test_messaging_stop_owner_turn.py` | Messaging /stop and /new reach the authority's claimed turn and its queued follow-up. |
| `test_mirror.py` | Tests for gateway/mirror.py — session mirroring. |
| `test_mixed_attachment_routing.py` | Regression tests for mixed-attachment routing in gateway/run.py. |
| `test_moa_one_shot_restore.py` | One-shot model overrides (``/moa <prompt>``, ``/model --once``) must be restored on every exit. |
| `test_model_alias_credential.py` | ``/model <alias>`` keeps the alias endpoint's own credential on the next turn. |
| `test_model_alias_credential_restart.py` | N48/N30/E02: ``/model <alias>`` with a LITERAL alias key commits a reference to the alias entry, so a restarted owner re-derives it (no ``launch_credentials_unavailable`` wedge), and the key is read from this owner's pr… |
| `test_model_alias_scalar_model.py` | A scalar ``model: <name>`` config is valid; the alias credential reader must not crash on it (N105). |
| `test_model_command_async_offload.py` | Gateway ``/model`` picker listing is a read path (#41289, #74003): it must ask for cache-only catalogs and live-probe only the currently selected custom endpoint, so a stale provider cache cannot freeze the gateway on b… |
| `test_model_command_context_offload.py` | ``/model`` context-length resolution must not block the gateway event loop. |
| `test_model_command_custom_providers.py` | Regression tests for gateway /model support of config.yaml custom_providers. |
| `test_model_command_expensive_confirm.py` | Gateway typed ``/model <name>`` must route through the expensive-model confirmation gate. |
| `test_model_command_flat_string_config.py` | Regression tests for gateway /model --global persistence when config.yaml has a flat-string ``model:`` value instead of a nested dict. |
| `test_model_command_profile_config.py` | Regression coverage for profile-scoped gateway ``/model`` reads. |
| `test_model_command_reasoning_flag.py` | Gateway ``/model <m> --reasoning <level>``: the effort rides with the pick through the same applier ``/reasoning`` uses (session override by default, ``agent.reasoning_effort`` on --global). |
| `test_model_command_request_overrides.py` | Regression tests for gateway /model preserving named-custom request_overrides. |
| `test_model_confirmation_clients.py` | Every native surface collects the owner's guarded-model confirmation (same as main's CLI). |
| `test_model_picker_persist.py` | Regression tests for gateway inline-keyboard model-picker persistence. |
| `test_model_switch_persistence.py` | Tests that gateway /model switch persists across messages. |
| `test_moved_platforms_yaml_allowlist.py` | config.yaml ``platforms.<name>.allowed_users`` gates DMs on the platforms moved from core into plugins. |
| `test_msgraph_authority.py` | Graph boundary uses the canonical internal queue, not a background ACK. |
| `test_msgraph_webhook.py` | Tests for the Microsoft Graph webhook adapter. |
| `test_multiplex_adapter_registry.py` | Phase 3: secondary-profile adapter registry + same-token conflict detection. |
| `test_multiplex_adapter_session_key_namespace.py` | Regression tests: adapter-level session keys must carry the profile (#88391). |
| `test_multiplex_api_server_routing.py` | Multiplex /p/<profile>/ routing for the api_server adapter. |
| `test_multiplex_background_task_scope.py` | Regression: background tasks respect profile secret scope when multiplexing. |
| `test_multiplex_busy_input_mode.py` | Profile-specific busy-input behavior for multiplexed gateways. |
| `test_multiplex_cold_profile_sidebar_mutation.py` | Cold-profile sidebar mutations reach the served profile's own authority under multiplex. |
| `test_multiplex_credential_isolation.py` | End-to-end credential isolation proof for multiplex mode (Workstream A). |
| `test_multiplex_docker_media_delivery_scope.py` | Regression for #109024: a multiplexed secondary's Docker ``MEDIA:`` paths must be validated under THAT profile's home + terminal policy on the adapter delivery side. |
| `test_multiplex_endpoint_identity_scope.py` | Invariant: an adapter's endpoint/identity resolves through the SAME profile scope as its secret. |
| `test_multiplex_hot_serve.py` | Hot-serve invariants for ``gateway.multiplex_profiles`` (``gateway/run_profile_reconcile.py``). |
| `test_multiplex_hot_serve_live.py` | Live hot-serve contract of a real ``python -m gateway.run`` multiplexer (Linux; loopback model). |
| `test_multiplex_http_routing.py` | Phase 1: HTTP-inbound /p/<profile>/ routing for the webhook adapter. |
| `test_multiplex_interactive_auth.py` | Multiplex interactive-auth regressions (#86296, #92840, #72657, #87240 egress). |
| `test_multiplex_lifecycle.py` | Phase 4: lifecycle guard + per-profile observability. |
| `test_multiplex_log_routing.py` | Multiplex gateway log routing (#82936, salvage of #84954). |
| `test_multiplex_mcp_discovery.py` | Multiplexed gateways discover and reload MCP servers per profile (#95518). |
| `test_multiplex_notice_egress_profile_adapter.py` | Out-of-band gateway egress for a SECONDARY profile session leaves through that profile's bot. |
| `test_multiplex_pairing_stores.py` | Regression: per-profile PairingStore creation in _start_secondary_profile_adapters. |
| `test_multiplex_phase0.py` | Phase 0 foundations for multi-profile gateway multiplexing. |
| `test_multiplex_primary_token_scope.py` | #64674 — multiplex primary gateway must not fail forever without bot tokens. |
| `test_multiplex_process_global_sinks.py` | Per-profile isolation for the remaining process-global sinks under gateway.multiplex_profiles: Yuanbao auto-sethome env write, the config ``terminal.env_passthrough`` allowlist, and the runner-level Slack ignored-channe… |
| `test_multiplex_process_memo_scope.py` | Multiplexed-gateway invariants: per-turn config, credentials and hooks follow the ROUTED profile (HERMES_HOME override), not the launch home the module constants were frozen from. |
| `test_multiplex_profile_authz.py` | Regression tests for multiplex profile-aware own-policy authorization. |
| `test_multiplex_requires_default_profile.py` | Only the default profile runs the multiplexer; a named launch would split default's sessions. |
| `test_multiplex_residue_parity.py` | Multiplex parity: a served profile reads ITS ``sessions.*`` / proxy env, never the launch profile's; a stale served route never re-scaffolds an archived profile; MCP discovery runs once per served profile home. |
| `test_multiplex_routing_authz.py` | Routing/authorization invariants for a multiplexed gateway (#104933, #103717). |
| `test_multiplex_secondary_port_binding_env.py` | A secondary profile's port-binding credential wires the key without claiming the listener (#100397). |
| `test_multiplex_served_profile_parity.py` | Standalone-vs-served parity for goals/loops, completion notices and process recovery under ``gateway.multiplex_profiles``: every read that decides FOR a served profile must run inside that profile's runtime scope, and e… |
| `test_multiplex_session_db_profile_scope.py` | Regression coverage for #88532. |
| `test_multiplex_shared_ingress.py` | Inbound-port platforms of a SECONDARY profile are served on the default profile's shared listener at ``/p/<profile>/<path>`` (gateway/platforms/shared_ingress.py). |
| `test_multiplex_toolsets_profile_isolation.py` | Per-profile toolset isolation on the multiplexed api_server (#91583 defect 2). |
| `test_multiplex_transport_matrix.py` | The intake / delivery transport matrix (#88715 phase 4; gateway/AGENTS.md § Profile scope). |
| `test_multiplex_unserved_shared_ingress.py` | Multiplex secondaries that enable shared-ingress Relay must not be silently unserved: one INFO per skipped platform, a stamped ``<profile>:<platform>`` status entry, and the loud "not being served" WARNING when no profi… |
| `test_multiplex_yaml_env_bridge_isolation.py` | A multiplexed secondary profile's config.yaml must never be bridged into the process env. |
| `test_mutation_prepare_off_loop.py` | The model/compress prepare transaction runs off the owner loop like its commit. |
| `test_named_custom_provider_session_identity.py` | Named custom provider identity survives gateway sync and canonical resume reads. |
| `test_native_admission_arrival_order.py` | A chat's inputs reach its FIFO in arrival order, whatever off-loop media capture each needs. |
| `test_native_admission_edit.py` | An edited message re-sends its message id with new text: native admission takes it as its own input, never as a changed replay of the original send (``admission_conflict``, #140845). |
| `test_native_admission_metadata.py` | Native admission keeps main's inbound contract: real adapter events run a turn (N78-N80). |
| `test_native_admission_named_refusal.py` | A native admission refusal names the failing clause in the error and the log, and in the chat reply only for content clauses; trust and provenance clauses stay generic there. |
| `test_native_admission_path_text.py` | A message whose first token is a filesystem path is text, even when the adapter typed it COMMAND on its leading ``/``: native admission queues it and replays it as text (#141221). |
| `test_native_admission_remote_media.py` | An attachment an adapter could not cache locally (a remote URL left in ``media_urls``, as DingTalk always does) is dropped with a note; the message and its other media are still admitted. |
| `test_native_config_owner_scope.py` | A native ticket binds its own home even when a foreign home override is ambient. |
| `test_native_epoch_timestamp.py` | Producers that pin epoch 0 for a stable retry fingerprint still record local time (not 1970). |
| `test_native_execution_secret_scope_off_loop.py` | Admitted native turns hydrate profile secret sources off the owner loop (main #99519 parity). |
| `test_native_fifo_compression_identity.py` | Native FIFO identity survives a compression that moves the physical route to a child. |
| `test_native_fifo_context_exhaustion.py` | Native messages queued behind a turn that exhausts its context run once, in order, on the fresh session the auto-reset creates; the exhausted turn is not replayed and a transport retry of a re-homed message still dedupe… |
| `test_native_http_auth.py` | Private native grants authenticate HTTP, never another purpose or profile. |
| `test_native_http_per_profile_edits.py` | Old local rows take the Desktop's sidebar edits over each profile's own native grant (#106742). |
| `test_native_http_secondary_profile_binding.py` | A secondary-profile native ticket binds every implicit profile selector to its own home. |
| `test_native_image_buffer_isolation.py` | Tests: `_make_runner`, `_source`, `_image_event`, `test_native_image_buffer_isolated_per_session`, `test_native_image_buffer_not_cleared_by_other_sessions_without_images`, `test_native_image_buffer_uses_resolved_session… |
| `test_native_ingress_media.py` | Native attachments are committed bytes, not mutable adapter paths. |
| `test_native_ingress_trust.py` | Trust is minted at native callbacks, never by serialized source flags. |
| `test_native_media_acl_provenance.py` | Review-9 (a): native media capture keeps the Hermes-home provenance of its store for elevated grants. |
| `test_native_media_alias_safety.py` | Shared publication and physical alias custody without executing a turn. |
| `test_native_media_budget.py` | Public attachments are bounded per admission and their retained bytes are released. |
| `test_native_media_capture_lease.py` | Retained media a capture published or reused is held from capture until its admission commits or is refused (andrexibiza-7, JoaoMarcos44-R2), and a refused admission leaves no capture behind (andrexibiza-17). One row pe… |
| `test_native_media_capture_off_loop.py` | Native media capture (copy + SHA-256 + fsyncs) runs off the owner loop, under the admission lease. |
| `test_native_media_history_retention.py` | A settled native input stays on disk while the transcript still tells a follow-up turn where it is saved (dokterdok N28), in whichever spelling the note used, and is bounded by main's 24 h media age once settled, as mai… |
| `test_native_media_ownership.py` | Retained native bytes always have an owner: no orphan from a rejected batch, no leftover when equal bytes were admitted under different basenames. |
| `test_native_media_redelivery.py` | A provider redelivery of a committed media message is the same admission, whatever staging name its re-download got; changed bytes under the same provider id still conflict. |
| `test_native_operator_provenance.py` | Security fences for durable operator provenance on native-session recovery. |
| `test_native_pause_notice.py` | A messaging user whose session FIFO is paused is told once, and can /reset out of it. |
| `test_native_plugin_ws_auth.py` | Desktop plugin WebSockets on a local gateway ride the private native-HTTP grant (PLG-1). |
| `test_native_producer_owner_matrix.py` | Native media producers keep routed owner decisions across alternating homes. |
| `test_native_profile_create.py` | A dedicated same-user grant creates profiles without widening profile HTTP grants. |
| `test_native_profile_registry_grant.py` | Desktop rename/delete of a served profile over a native grant (#134889 DB-5, #140345, #140791). |
| `test_native_recovery_viewer_queue.py` | Native restart recovery accepts viewer work actually admitted by the authority. |
| `test_native_reply_crash_recovery.py` | A settled native reply survives an owner death before it reached the delivery ledger; an uncommitted one is never delivered. Real Telegram polling ingress, SIGKILL, ordinary restart. |
| `test_native_reply_delivered_once.py` | A native reply reaches the chat exactly once even when an already-running drain claims and runs the admission before ``admit_message`` resumes to register its delivery waiter (andrexibiza-6, andrexibiza-5480238075-1). E… |
| `test_native_role_reauthorization.py` | Current connector membership, not role flags, authorizes durable work. |
| `test_native_startup_recovery.py` | Ordinary startup recovers native admissions without a recovery fixture call. |
| `test_native_stream_warning_composition.py` | Actual warning callback and media producer beside an armed native Slack stream. |
| `test_native_telegram_startup_recovery.py` | Actual Telegram polling ingress, SIGKILL, and uninstrumented owner recovery. |
| `test_native_warning_coverage.py` | Native diagnostic producers keep captions, controls and truthful receipts. |
| `test_new_moves_automation_wake.py` | Messaging /new keeps a queued automation wake and runs it on the fresh session, as main's #114456 kept a parked internal wake across /new; it is never stranded queued on the abandoned owner (N83). Real GatewayRunner, Di… |
| `test_normal_runtime_boot.py` | The ordinary no-platform process must earn its bootstrap readiness. |
| `test_normalize_empty_agent_response.py` | Unit tests for persistence-failure-aware messaging in ``_normalize_empty_agent_response``. |
| `test_notice_delivery.py` | Tests: `_make_source`, `_make_runner`, `test_deliver_platform_notice_uses_private_delivery_when_configured` |
| `test_notice_rendering.py` | Unit tests for messaging-gateway credit-notice rendering. |
| `test_notify_fatal_error_shield.py` | Regression test for #81335 — fatal-error handler must survive cancellation of the task that awaits ``_notify_fatal_error``. |
| `test_ntfy_plugin.py` | Tests for the ntfy platform-plugin adapter. |
| `test_offloop_write_retirement_join.py` | An authority write moved off the owner loop is still the authority's work: retirement joins it before answering True, and the shutdown close gate counts it before closing state.db. |
| `test_ogg_opus_transcode_routing.py` | ``transcode_to_ogg_opus`` in-place repair never destroys the source on failure. |
| `test_onboarding_on_the_authority.py` | The desktop's onboarding chat on the unified gateway: the window resumes the chat that ``onboarding.start`` opened. |
| `test_onboarding_reset.py` | ``/new`` (a canonical reset) inside the onboarding chat, then Skip setup: the run ends and the install stops being mid-onboarding. The reset child is its own conversation, so it carries no copy of the run that Skip (whi… |
| `test_one_turn_route_publish.py` | A one-turn model override must not become the route other clients read, and a same-provider override must keep the session endpoint and key. |
| `test_operator_cross_surface.py` | Real native bootstrap and dashboard login share one canonical worker as one owner identity. |
| `test_orphan_exit_grace.py` | A retiring gateway must get long enough to finish its WAL checkpoint. |
| `test_output_caps_removed.py` | User configuration cannot impose generation caps; wire budgets remain internal. |
| `test_own_policy_startup_gate.py` | Regression tests for own-policy open startup gate in gateway/run.py. |
| `test_owner_backfill_live_owner.py` | Desktop's per-boot owner backfill no longer 409s against the live owner (#106742 live sweep row 24). |
| `test_owner_liveness_drift.py` | Sibling owner-liveness checks tolerate a drifted start-time fingerprint (#117505). |
| `test_owner_loop_writes_a2a_hosted_create.py` | A2A forward and hosted-room member creation commit their session off the owner loop (N90 siblings): a held SQLite writer must not stall every session, Stop and socket while either creates. |
| `test_owner_loop_writes_bot_chat_create.py` | The Bot Chat a first delivery mints commits off the owner loop (N90): a held SQLite writer must not stall every session, Stop and socket the owner serves while the profile's Bot Chat is created; concurrent first deliver… |
| `test_owner_loop_writes_class.py` | Bug class: a synchronous SQLite write reached from an ``async def`` on the owner loop. |
| `test_owner_loop_writes_create_api.py` | N50: session.create's creation commit and an API turn's settings write run off the owner loop. |
| `test_owner_loop_writes_cron_create.py` | Cron fire creation commits its session off the owner loop: a held SQLite writer must not stall every session, Stop and socket the owner serves while ``cron.submit`` creates the fire's session. |
| `test_pairing.py` | Tests for gateway/pairing.py — DM pairing security system. |
| `test_pairing_allowlist_bypass.py` | Pairing store <-> allowlist consolidation (#23778). |
| `test_pairing_reply_off_loop.py` | Unauthorized-DM pairing replies must not block the gateway event loop on the pairing lock. |
| `test_parked_profile_ingress.py` | Ingress for a parked secondary is never acknowledged and then dropped. |
| `test_parked_profile_platform_refusal.py` | A message a direct platform bot routes to a parked profile is refused out loud, never dropped. |
| `test_parked_profile_rescan.py` | A secondary parked at boot (its startup Bot recovery failed) and served again by the control-socket rescan is fully served: its local sessions work, and the durable work queued before the park is recovered the way a col… |
| `test_parked_profile_served_set.py` | A profile whose retirement misses its deadline keeps its slot (its writer may still run) but refuses every admission: it must leave the published served set and the ticket store at once, so discovery stops reporting it… |
| `test_parked_profile_unserved_ingress.py` | Ingress the parked-profile checks miss when they read only the URL prefix and the parked map. |
| `test_parked_route_refusal_discord.py` | A parked-profile refusal on Discord is an outage notice: it never hides the message from backfill. |
| `test_parked_route_refusal_google_chat.py` | A Google Chat HTTP event routed to a parked profile is answered retryably; Pub/Sub is refused in chat. |
| `test_parked_route_refusal_relay.py` | A parked-profile notice sent through relay never seals another turn's open Slack stream. |
| `test_parked_route_refusal_send.py` | A parked-profile refusal whose send fails is logged, with safe fields only. |
| `test_peer_client_unknown_run.py` | A hosted-room peer whose member gateway restarted mid-turn reports the run ``unknown``: the room's poll resolves that exact admission and settles the run interrupted, and the member's queued follower then runs once (the… |
| `test_peer_dm_bot_chat_authority.py` | A peer turn into the canonical Bot Chat under session authority is that chat's own admission. |
| `test_peer_dm_bot_chat_context_overflow.py` | A peer DM that overflows the LOCAL Bot Chat's context auto-resets it, and the follow-up is answered. |
| `test_peer_dm_bot_chat_headless.py` | A headless gateway's first peer DM lands in a Bot Chat its own authority FIFO owns. |
| `test_peer_dm_hidden_e2e.py` | E2E: ``hermes peer dm`` against a REAL api_server gateway whose canonical Bot Chat session is HIDDEN (issue #91583). |
| `test_peer_dm_into_open_bot_chat.py` | A peer DM into a Bot Chat is answered by that chat, never by a second writer. |
| `test_peer_dm_transient_retry.py` | #115325: the peer-DM transport (``POST /api/sessions/{id}/chat``) retries a transiently failed turn once, resuming the DM row the failed attempt already persisted. |
| `test_pending_drain_no_recursion.py` | Regression test for #17758 — chained pending-message drains must not grow the call stack. |
| `test_pending_drain_race.py` | Regression tests: pending-drain + finally-cleanup races must not spawn duplicate agents OR silently drop messages that arrived during cleanup. |
| `test_pending_queue_spool.py` | Regression tests for runtime spool-on-drop of the pending transcript queue. |
| `test_pending_steer_drain.py` | Regression for #131644: late steering retains FIFO messages and channel inputs. |
| `test_personality_routed_profile.py` | #89161: a routed multiplex profile's personality must reach its turns. |
| `test_pii_redaction.py` | Tests for PII redaction in gateway session context prompts. |
| `test_plain_audio_not_voice_note.py` | A plain audio MEDIA file (``is_voice=False``: music, a sound effect) is never sent as a voice note. |
| `test_plaintext_approval_routing.py` | Tests for #46866: plain-text approval responses must resolve a blocking dangerous-command approval instead of being steered/queued. |
| `test_planned_restart_marker_cli.py` | A CLI ``restart`` must stamp the planned-restart marker itself. |
| `test_planned_restart_notice_multiplex.py` | A planned restart notifies EVERY served profile's home channels, not just the launch profile's. |
| `test_planned_stop_accepted_debt.py` | The gateway's planned-stop consumer and the accepted-stop evidence a Windows update pause relies on. |
| `test_planned_stop_watcher.py` | Tests for the planned-stop marker watcher thread (gateway/run.py). |
| `test_platform_adapter_i18n.py` | Telegram + Discord adapters read their chat copy from the i18n catalog at call time. |
| `test_platform_authz_scope.py` | Platform authorization reads must honor the per-profile secret scope (#93522). |
| `test_platform_base.py` | Tests for gateway/platforms/base.py — MessageEvent, media extraction, message truncation. |
| `test_platform_bundled_authz_fallback.py` | Authorization env names of bundled platforms survive a registry entry that lacks them. |
| `test_platform_connected_checkers.py` | Verify that every gateway platform — built-in and plugin — has a connection checker so ``GatewayConfig.get_connected_platforms()`` doesn't silently drop platforms with bespoke auth requirements. |
| `test_platform_entry_authz_fields.py` | Bot-bypass and own-policy startup gates read the plugin's PlatformEntry, not a core table. |
| `test_platform_entry_plugin_seams.py` | PlatformEntry seams a plugin platform uses instead of a core special case. |
| `test_platform_env_overrides.py` | Invariants for the env -> GatewayConfig bridge that platform plugins declare on their ``PlatformEntry`` (``env_overrides`` / ``env_enable_credentials``, applied by ``gateway.config_env._apply_env_overrides``). |
| `test_platform_http_client_limits.py` | Tests for the shared httpx.Limits helper that all long-lived platform adapters use to tighten their keep-alive pool. |
| `test_platform_plugin_canonical_class.py` | Plugins whose own code imports siblings by absolute path must register by that same path. |
| `test_platform_plugin_handlers.py` | Tests for plugin-registered native platform handler factories. |
| `test_platform_reconnect.py` | Tests for the gateway platform reconnection watcher. |
| `test_platform_reconnect_fd_leak.py` | Regression tests for the gateway platform fd-leak fix (#37011). |
| `test_platform_registry.py` | Tests for the platform adapter registry and dynamic Platform enum. |
| `test_platform_shared_metrics.py` | Gateway platform health / delivery / first-reply shared metrics through the real runner seams. |
| `test_plugin_check_housekeeping.py` | Plugin checks are due-gated from startup, not delayed for an hour. |
| `test_plugin_command_choice.py` | A plugin slash command asks its user to pick an option (``PluginContext.ask_choice``) and gets the picked value back, on the surfaces the gateway serves: |
| `test_plugin_gateway_session_parity.py` | Plugin code running inside the gateway sees the session it runs for (LC-5). |
| `test_plugin_keyless_inject.py` | A key-less ``ctx.inject_message(text)`` from plugin code the gateway runs (#134889 PLG-7, B2-11). |
| `test_plugin_message_injection.py` | Tests for plugin-triggered turns in existing gateway sessions. |
| `test_plugin_origin_injection.py` | ``ctx.inject_message(origin=...)`` starts a gateway session in the plugin's OWN profile (#132609). |
| `test_plugin_origin_injection_authority.py` | ``inject_message(origin=...)`` under the session authority answers ``False`` up front for a chat the FIFO cannot admit it into (no human message admitted there yet), instead of ``True`` for a message the dispatch then d… |
| `test_plugin_post_message.py` | ``PluginContext.post_message``: one message in the calling session's chat, edited in place. |
| `test_pm_activation.py` | Gateway startup remains fail-open when PM admission itself fails. |
| `test_policy_secret_projections.py` | Tests: `test_terminal_and_config_secret_projections_recover_without_durable_values` |
| `test_poller_fd_lifecycle.py` | Poller socket lifecycle — proxied fd-leak regressions (#79889). |
| `test_post_delivery_callback_chaining.py` | Tests for ``BasePlatformAdapter.register_post_delivery_callback`` chaining. |
| `test_post_gateway_admission.py` | ``post_gateway_admission``: a fail-open plugin hook that may consume an admitted message (#129958). |
| `test_post_stream_media_delivery.py` | Post-stream media delivery is explicit-only (#20834). |
| `test_pre_agent_fallback_notice.py` | A fallback resolved during gateway credential resolution (before any AIAgent exists) must carry a user-visible notice through the agent's one-shot fallback-notice mechanism (#74349). |
| `test_pre_command_in_gateway.py` | ``pre_command`` fires once, in the gateway, for every local surface, and the classic CLI's ``/plugins`` reads the gateway's loaded plugins (#134889 PLG-7). |
| `test_pre_gateway_dispatch.py` | Tests for the pre_gateway_dispatch plugin hook. |
| `test_pre_gateway_dispatch_relay_reader.py` | ``pre_gateway_dispatch`` on relay deliveries runs at admission, before the commit, but never on the relay socket reader: a hook may await ``adapter.send()``, whose ``outbound_result`` only that reader delivers, or wait… |
| `test_preclaim_conflict_settles_head.py` | A preclaim ``admission_conflict`` settles that head instead of pausing its FIFO for good. |
| `test_priority_path_compression_demotion.py` | Regression test: the ``_handle_message`` PRIORITY busy-path must also demote ``busy_input_mode='interrupt'`` to queue semantics when context compression is in flight (#56391), the same as ``_handle_active_session_busy_m… |
| `test_process_cmdline_source.py` | ``_read_process_cmdline`` asks the cheapest source that can answer, and still answers. |
| `test_process_hermes_home_expansion.py` | Gateway identity-file readers expand a literal ``~`` in HERMES_HOME. |
| `test_producer_owner_continuity.py` | Background and room producers retain source ownership across media and transcript lifetimes. |
| `test_profile_authority_park_reason.py` | A reserved profile parked for an unusable store names the open failure, not an ownership mismatch. |
| `test_profile_identity_purge.py` | Profile identity purge for `hermes profile delete`: the delete-only path, and what an unserve must leave alone. |
| `test_profile_isolation_runtime.py` | Profile-isolation regression tests for single-process multi-profile runtimes. |
| `test_profile_resolution.py` | Tests for GatewayRunner._resolve_profile_home_for_source — profile resolution logic. |
| `test_profile_retire_stops_turns.py` | Unserving a profile stops and joins its running turns before ownership is released. |
| `test_profile_routing.py` | Tests for gateway/profile_routing.py — profile-based routing. |
| `test_profile_serve_signature.py` | #111105: the profile re-scan watcher must rebuild adapters after a config.yaml replacement that keeps mtime and size (``cp -p``, ``rsync -t``, a timestamp-pinning writer). |
| `test_profile_signature_during_connect.py` | A config saved while a profile connects must remain pending for the next scan. |
| `test_profile_spool_recovery.py` | Boot recovery must replay a routed profile's spooled transcript backlog (#123584). |
| `test_profile_store_open_off_loop.py` | A multiplexed boot opens each secondary profile's state.db off the event loop, under its own scope. |
| `test_profiles_adopted_bot_chat.py` | Regression for #139227: adopted local chats stay visible in the bot roster. |
| `test_project_plugins_warning.py` | LC-4: the gateway runs every local session and never loads ``./.hermes/plugins``. A session whose client opted in (``HERMES_ENABLE_PROJECT_PLUGINS``, forwarded in ``client_env``) from a folder that has project plugins g… |
| `test_prompt_attachments.py` | Public ``prompt.submit`` attachments: scoped to the profile staging dir, committed as bytes. |
| `test_prompt_cancel_claimed.py` | prompt.cancel on a row the drain claims between the client's queued read and the cancel commit stops that claim (as API and ACP do) instead of refusing while the withdrawn prompt runs (N113). |
| `test_prompt_cancel_started.py` | prompt.cancel on a started admission stops it in the same RPC (#143547 ACP-23): an editor that exits right after its cancel never sends the follow-up ``session.interrupt``. |
| `test_prompt_decline_no_fallback.py` | P5(b) at the CALLER: a connector egress decline must not fall back. |
| `test_prompt_queued_controls.py` | prompt.steer_queued / prompt.replace_queued: Desktop's Steer and Edit on a canonical queued row (RT-35). Both verbs consume the still-queued admission in the owner's own write transaction, so it can never both run as a… |
| `test_prompt_queued_transfer.py` | prompt.steer_queued / prompt.replace_queued failure windows (RT-35 review): a durable queued prompt is never reported steered unless its text reached the turn that settled, the steer's storage wait never holds a lock th… |
| `test_prompt_tail_freeze.py` | Byte-stable gateway system prompts (the ephemeral session-context pin). |
| `test_proxy_mode.py` | Tests for gateway proxy mode — forwarding messages to a remote API server. |
| `test_publish_execution_stamp_fence.py` | publish_execution (per token / tool event, under event_stream.lock) fences on the claim's execution stamp, not a per-delta ledger read (get_session + pending-admission decode) (B1-11). |
| `test_purge_profile_routing.py` | In-memory routing purge for `hermes profile delete`. |
| `test_qqbot.py` | Tests for the QQ Bot platform adapter. |
| `test_qqbot_credential_isolation.py` | Credential isolation for the QQ (qqbot) gateway adapter. |
| `test_qqbot_scope_paths.py` | End-to-end profile-scope coverage for the QQ (qqbot) authorization, startup-validation, and direct-send paths. |
| `test_qqbot_update_prompt_key.py` | The QQ update-prompt authz key comes from ``build_session_key`` (profile-namespaced), not a hard-coded ``agent:main:`` literal — a multiplexed secondary bot's clicks were rejected otherwise. |
| `test_queue_command.py` | Tests for the gateway /queue command handler (running-agent path). |
| `test_queue_consumption.py` | Tests for /queue message consumption after normal agent completion. |
| `test_queued_final_ledger.py` | A queued-lane final is ledger-bracketed like the normal final send. |
| `test_queued_followup_final_delivery.py` | Queued-follow-up lane: the fallback first-response send and the normal completion send share one "already delivered" source of truth (#81052). |
| `test_queued_followup_processing_hooks.py` | Processing-hook parity for queued follow-up turns. |
| `test_queued_native_image_session_key.py` | Tests: `CaptureAdapter`, `CaptureQueuedNativeImageAgent`, `CompressionExhaustedAgent`, `_make_runner`, `test_queued_followup_uses_pending_event_session_key_for_native_images`, `test_compression_exhaustion_defers_queued_… |
| `test_raft_adapter.py` | Tests for the Raft channel adapter. |
| `test_readiness.py` | Tests: `test_collect_runtime_readiness_reports_healthy_local_runtime`, `test_collect_runtime_readiness_degrades_on_invalid_config_and_stopped_gateway`, `test_readiness_uses_running_session_store_state_over_independent_p… |
| `test_reaped_eviction_interrupts_run.py` | Regression tests for interrupting work evicted from a gateway turn slot. |
| `test_reaped_session_recovery.py` | Regression tests for the durable-reaped session guard in _handle_message (#99106). |
| `test_reaper_profile_scope.py` | Regression coverage for profile scope on abandoned-turn reaper threads. |
| `test_reasoning_command.py` | Tests for gateway /reasoning command and hot reload behavior. |
| `test_reasoning_config_per_model.py` | Tests for per-model reasoning_effort override in gateway _load_reasoning_config. |
| `test_reconcile_probe_skip_keeps_parked.py` | A profile skipped by the own-gateway probe this cycle keeps its parked verdict (N114). |
| `test_reconnect_attention_profile_scope.py` | ``agent.reconnect_attention_after`` is read from the profile whose scope is bound at call time. |
| `test_recovered_reply_transform_stream.py` | A transformed recovered final replaces its prior streamed segment, not its neighbors. |
| `test_refused_delete_read_detach.py` | A refused picker delete must not leave the closed session in the live list (#134889 TUI-19). |
| `test_refused_followup_reply.py` | A queued messaging follow-up the drain refuses is told it was not answered, never that it is saved. |
| `test_refused_owner_windows.py` | #139845 / #140252 real Windows probes behind the named refusal states. |
| `test_rekey_profile_routing.py` | In-memory routing rekey for `hermes profile rename`. |
| `test_relay_authority.py` | Real authenticated relay ingress shares the ordinary execution authority. |
| `test_relay_completion_injection_routing.py` | Regression: completion injection must resolve the RELAY adapter for fronted platforms. |
| `test_relay_delivery_followups.py` | Follow-up regressions for the 2026-08-09 relay delivery fixes (#82592). |
| `test_relay_final_delivery_incident.py` | Regression: relay-plane delivery defects (staging incident 2026-08-09). |
| `test_relay_injection_egress_priming.py` | Regression: synthetic injections must prime relay egress routing metadata. |
| `test_relay_seal_failure.py` | Regression: seal-time transport failure must never lose or duplicate the final answer (silent-loss class — PR 85796 review finding B1/B3-adjacent). |
| `test_relay_source_platform_metrics.py` | Replies the relay connector carries are labelled with the platform the conversation lives on. |
| `test_relay_teardown_drain.py` | Regression: relay transport teardown must drain in-flight outbound frames. |
| `test_relay_upstream_authz.py` | Tests for relay upstream-enforced authorization at the gateway layer. |
| `test_reload_plugins_connects_mcp.py` | The gateway's ``reload-plugins`` verb connects an enabled plugin's MCP servers before it answers. |
| `test_reload_signal_logs_graceful_restart.py` | SIGUSR1 (systemd ``ExecReload`` / ``hermes gateway restart``) is a graceful restart, and the gateway says so in its log when the signal lands (#117267). |
| `test_reload_skills_command.py` | Tests for the ``/reload-skills`` gateway slash command handler. |
| `test_reload_skills_discord_resync.py` | Tests for `/reload-skills` resyncing the Discord ``/skill`` autocomplete. |
| `test_remote_media_fetch.py` | MEDIA tags pointing into a remote terminal sandbox are fetched for delivery (#466). |
| `test_replace_child_reap.py` | Tests for --replace child-process reaping (POSIX taskkill /T parity). |
| `test_replace_ownership_guard.py` | Tests for issue #89315 — ``--replace`` must never signal a gateway it cannot prove belongs to this HERMES_HOME. |
| `test_replay_entry_fields.py` | Tests for ``gateway.run._build_replay_entry``. |
| `test_reply_to_injection.py` | Tests for reply-to pointer injection in _prepare_inbound_message_text. |
| `test_reset_button_deadlock.py` | Regression test for #35994: Telegram /new confirm-button deadlock. |
| `test_reset_lineage_session_count.py` | andrexibiza 26: the session counts that page a listing count a local reset lineage once, the same way list_sessions_rich lists it (an earlier reset segment is not a second conversation). |
| `test_reset_tip_unknown_barrier.py` | A local conversation reset before a crash keeps its admissions on the creation id while the store routes the physical reset child. The unknown-turn barrier must resolve the child to that owner: neither the crash marker… |
| `test_response_filters.py` | Tests: `test_exact_silence_tokens_are_intentional_silence`, `test_autonomous_silence_accepts_marker_with_own_line_note`, `test_translated_sentinel_is_silence_in_every_form_the_english_one_is`, `test_prose_mentioning_the… |
| `test_responses_cancel_keeps_terminal.py` | A cancel landing while the terminal snapshot commits off the loop never overwrites it with ``incomplete``: the commit's worker keeps running after its awaiting handler is cancelled. |
| `test_responses_chain_api_content.py` | A chained Responses turn replays the earlier turn's user row as the model saw it, including its ``api_content`` (memory prefetch, plugin context), not a synthetic row rebuilt from the raw request text. |
| `test_responses_compressed_chain.py` | ``previous_response_id`` follows the logical conversation across an out-of-place compression. |
| `test_responses_disconnected_identity.py` | A Responses identity settles from its admission's terminal outcome, even when the streaming client left before the replay record could be written. |
| `test_responses_idem_replay_record.py` | Only the publishing Responses stream writes the durable ``idem:`` replay record. |
| `test_responses_identity_bound_on_open.py` | A reopened Responses store enforces its settled-identity bound before serving a request. |
| `test_responses_identity_migration.py` | Identities migrated from a store that predates settlement tracking join the bounded lifecycle. |
| `test_responses_identity_retention.py` | Accepted Idempotency-Key identity has a bounded lifecycle beside the response-body LRU. |
| `test_responses_output_order.py` | Responses output ids and indexes stay identical across observers, late joiners and eviction. |
| `test_responses_request_identity.py` | Canonical response retry identity is fixed before concurrent admission. |
| `test_responses_stream_flush_race.py` | Keyed Responses streaming: the end-of-stream flush waits for a timer flush still opening the message item. The keyed output index is now read off the loop, so that open yields; an end-of-stream flush that skipped the lo… |
| `test_responses_unkeyed_stream_no_recording.py` | An unkeyed streaming Responses request keeps no replay copy of its frames: only a keyed request's replay record ever reads them. |
| `test_restart_after_turn.py` | Unit tests for in-band restart after-turn deferral helpers (#77184). |
| `test_restart_drain.py` | Tests: `test_restart_command_while_busy_requests_drain_without_interrupt`, `test_load_busy_text_mode_follows_input_mode_and_honors_legacy`, `test_load_signal_interrupt_grace_timeout_from_typed_config`, `test_request_res… |
| `test_restart_drain_recovery_dedup.py` | Restart drain-window recovery must be able to dedup an interrupted turn. |
| `test_restart_interrupt_notice.py` | #134889 F1: ``agent.restart_drain_timeout`` stays 0, and a turn a restart interrupts says so. |
| `test_restart_notice_replay.py` | Planned-restart online notice survives an offline home-channel transport at boot. |
| `test_restart_notification.py` | Tests for /restart notification — the gateway notifies the requester on comeback. |
| `test_restart_redelivery_dedup.py` | Tests for /restart idempotency guard against Telegram update re-delivery. |
| `test_restart_resume_pending.py` | Tests for the resume_pending session continuity path. |
| `test_restart_service_detection.py` | Tests for /restart service-manager detection (launchd vs interactive). |
| `test_restart_wait_prompt_reach.py` | A graceful restart's after-turn wait stays reachable for a turn parked on a human prompt (#139041). |
| `test_resume_command.py` | Tests for /resume gateway slash command. |
| `test_resume_display_history.py` | A resume after a compression shows the whole display history: the turns the compression summarized away come back marked ``archived``, and only the live rows stay undo/retry targets. An undone turn stays gone, a merged… |
| `test_resume_latest_local_cli.py` | ``session.resume latest='cli'`` finds the CLI's own gateway sessions. |
| `test_resume_omit_messages.py` | A resume that asks ``omit_messages`` (Desktop, which pages the transcript over REST) gets no transcript rows, so opening a long compressed chat no longer reads its whole compression lineage; a resume without it still ge… |
| `test_resume_todo_state.py` | ``session.resume`` carries the session's todo snapshot (``todo_state``): a viewer attaching to a session with a plan (the classic CLI's /resume or ``-c``) shows it before the next ``todo.updated``. |
| `test_retained_response_chain_after_delete.py` | A retained Responses chain whose transcript was deleted, continued with a fresh Idempotency-Key, moves to a new generation: it is neither refused forever (``not_found``) nor allowed to recreate the deleted transcript id… |
| `test_retire_settles_waiters.py` | A successful profile retirement settles every observer still waiting on a queued admission: API/webhook/Bot futures fail with runtime_draining instead of hanging, the native set is cleared, and the durable row stays que… |
| `test_retired_authority_cron_fence.py` | A retired profile authority refuses every verb that writes the home it released, from a stale connection: its ownership is released, but until a successor advances the runtime epoch its epoch would still pass the store'… |
| `test_retired_media_ownership.py` | Receipt retries preserve transcript boundaries, successor ownership and media identity. |
| `test_retired_media_scan_bound.py` | Retired-media collection: one bounded messages pass per collection, never on the event loop. |
| `test_retired_session_reset_notice.py` | Gateway startup names every served profile whose config still declares a retired timed reset. |
| `test_retry_authority_refusal.py` | Messaging /retry under a session authority answers the authority's admission refusals BEFORE it rewrites the transcript (#139257). |
| `test_retry_native_provenance.py` | Regression: messaging /retry must re-admit natively under session authority. |
| `test_retry_replacement.py` | Regression tests for /retry replacement and carrier-aware undo semantics. |
| `test_review_command.py` | Gateway /review command — direct handler tests. |
| `test_rich_sent_store_off_loop.py` | The rich-sent index write runs off the event loop for coroutine callers. |
| `test_room_work_evidence.py` | Passive receipts survive owner changes without granting replay rights. |
| `test_room_work_receipt_capture.py` | A real peer receipt insertion immediately updates passive evidence. |
| `test_room_work_service_capture.py` | Canonical hosted producer reaches passive capture without an explicit publisher. |
| `test_room_work_transition_capture.py` | Real driver transitions retain passive evidence without becoming replay authority. |
| `test_route_transition_racing_turn.py` | A chat's /new (or /resume) wins over a turn that finishes on its previous conversation. |
| `test_routing_save_fast_path.py` | Single-row routing save fast path. |
| `test_run_cleanup_progress.py` | Tests for opt-in cleanup of temporary progress bubbles. |
| `test_run_progress_interrupt.py` | Tests for interrupt-aware tool-progress suppression in gateway. |
| `test_run_progress_topics.py` | Tests for topic-aware gateway progress updates. |
| `test_run_progress_verbose_args.py` | Verbose tool-progress args on markdown platforms: a code block on both progress paths. |
| `test_run_runtime_hot_serve_cleanup.py` | Failed hot-serve initialization retires all authority task families before release. |
| `test_run_tool_media_re.py` | Tests for _TOOL_MEDIA_RE regex patterns in gateway/run.py. |
| `test_runner_compressed_receipt.py` | A TurnRunner result that compressed the transcript is stored whole, never cut to a turn suffix. |
| `test_runner_fatal_adapter.py` | Tests: `_FatalAdapter`, `_RuntimeRetryableAdapter`, `_ReplacementDeliveryAdapter`, `test_runner_queues_retryable_runtime_fatal_for_reconnection`, `test_retryable_fatal_queues_reconnect_after_cancellation_swallowing_disc… |
| `test_runner_startup_failures.py` | Tests: `_host_attach_gate_is_not_under_test`, `test_is_global_startup_conflict_matches_lock_code_families`, `_RetryableFailureAdapter`, `_DisabledAdapter`, `_SuccessfulAdapter`, `test_start_gateway_verbosity_imports_red… |
| `test_running_agent_session_toggles.py` | Regression tests: /yolo and /verbose dispatch mid-agent-run. |
| `test_runtime_api.py` | Real TCP HTTP/WS coverage for the gateway-owned API lifecycle. |
| `test_runtime_bootstrap.py` | Tests: `test_private_control_peer_mints_profile_bound_ticket`, `test_ticket_atomic_single_use_profile_purpose_expiry_and_capacity`, `test_old_socket_cleanup_cannot_unlink_replacement`, `test_native_pipe_authenticated_pe… |
| `test_runtime_bootstrap_lifecycle.py` | Live runtime HTTP lifecycle boundaries, with no provider inference. |
| `test_runtime_bootstrap_server_identity.py` | #140706: a non-elevated client identifies an elevated gateway from the control pipe itself. |
| `test_runtime_config_env_expansion.py` | Regression tests for gateway runtime config env-var expansion. |
| `test_runtime_describe_skin.py` | ``runtime.describe`` carries the owning profile's resolved skin: main's TUI booted its theme from ``gateway.ready.skin`` (``tui_gateway/entry.py`` / ``ws.py`` ``resolve_skin()``), and the canonical client publishes its… |
| `test_runtime_downgrade_exit.py` | A gateway stops once its checkout is moved back to a release that predates the gateway runtime. |
| `test_runtime_env_reload_config_authority.py` | Regression tests for gateway per-turn env reload preserving config authority. |
| `test_runtime_footer.py` | Unit tests for gateway.runtime_footer — the opt-in runtime-metadata footer appended to final gateway replies. |
| `test_runtime_listener_supervision.py` | A dead session listener must never leave a ready gateway behind. |
| `test_runtime_ownership.py` | Real process exclusion before writable gateway construction. |
| `test_runtime_provider_override_target_model.py` | Gateway provider-override credential resolution keys off the override's MODEL (#112600). |
| `test_runtime_token_identity.py` | Legacy token authentication must become an explicit authority principal. |
| `test_runtime_worker_shutdown.py` | Shutdown counts managed claims and retains profile ownership until actual threads stop. |
| `test_runtime_writer_drain.py` | Real startup threads retain runtime exclusion after a drain deadline. |
| `test_safe_adapter_disconnect.py` | Regression tests: failed-connect path must call adapter.disconnect(). |
| `test_save_command_delivery.py` | Gateway /save: the export document is delivered through the requester's live adapter. |
| `test_scalar_model_config_policy.py` | N46: a scalar ``model: <id>`` config.yaml (a supported form main's loaders accept) must not crash ``session.create``: Desktop's normal create (no explicit model) and a ``--provider`` launch. |
| `test_scale_to_zero.py` | Unit tests for the scale-to-zero idle-detection pure logic (Phase 0). |
| `test_scale_to_zero_dashboard_client.py` | Scale-to-zero: an attached dashboard/desktop/TUI WS client counts as activity. |
| `test_scale_to_zero_watcher.py` | Watcher-level tests for scale-to-zero: the idle watcher's dormant sequence and the arm-gate wiring, exercised against the real GatewayRunner methods bound onto a lightweight stand-in (booting a full gateway is unnecessa… |
| `test_scoped_lock_dir_unusable.py` | #134889 W2: a token-lock dir this user may not write gives one named warning, never a crash loop. |
| `test_scoped_process_reservations.py` | Non-gateway setup processes can reserve an existing adapter lock. |
| `test_secondary_local_pick_multiplex.py` | A secondary profile's local model pick reaches its next turn under multiplexing (#139060). |
| `test_secondary_route_fence_scope.py` | Retirement is keyed by (profile, id): a multiplexed secondary's delete or prune retires the id there, never in the launch profile. |
| `test_send_error_classification.py` | Tests for structured send-error classification (SendResult.error_kind). |
| `test_send_image_file.py` | Tests for send_image_file() on Telegram, Discord, and Slack platforms, and MEDIA: .png extraction/routing in the base platform adapter. |
| `test_send_multiple_images.py` | Tests for ``send_multiple_images`` native batching across platforms. |
| `test_send_retry.py` | Tests for BasePlatformAdapter._send_with_retry and _is_retryable_error. |
| `test_send_retry_hooks.py` | Invariants for the shared send-retry path. |
| `test_send_voice_dispatch_signatures.py` | Every platform adapter's ``send_voice`` must accept the ``is_voice`` keyword the base media dispatch passes (``BasePlatformAdapter._deliver_media_from_response`` → ``send_voice(..., is_voice=is_voice)``). An explicit si… |
| `test_send_voice_reply_notify.py` | Regression test for issue #27970 Bug 2. |
| `test_server_request_resume_replay.py` | A viewer that reconnects while the owner's server→client request waits gets that request again. |
| `test_serving_authorities.py` | Readers of every served ledger skip a slot that serves nothing. |
| `test_session.py` | Tests for gateway session management. |
| `test_session_a2a.py` | Forwarded profile identity is owner-bound, not a title or latest-row guess. |
| `test_session_activity_ordering.py` | Recovered UTC routes coexist with legacy local-time routes. |
| `test_session_ancillary_reads.py` | Canonical observers read owner state without bootstrapping legacy services. |
| `test_session_api.py` | Focused tests for API server session-control endpoints. |
| `test_session_approval_commands.py` | Typed /approve and /deny on a LOCAL session resolve the same waiting tool call as approval.respond. |
| `test_session_authoring_commands.py` | Authoring/workflow slash commands run the messaging gateway's own handler for a LOCAL session. |
| `test_session_authorities_multiplex.py` | One session authority per served profile home under gateway.multiplex_profiles. |
| `test_session_authority.py` | Real messaging ingress and authenticated WS must share one warm agent. |
| `test_session_authority_adopted_stop.py` | A Stop after the turn adopted its agent reaches that agent even if the cache no longer holds it. |
| `test_session_authority_cancel_settlement.py` | Cancelling a queued admission settles every observer kind in the authority, not per caller. |
| `test_session_authority_late_stop.py` | A Stop for a finishing turn reaches only that turn, never the next one on the cached agent. |
| `test_session_authority_preadopt_stop.py` | A Stop accepted before the claimed turn adopts its agent reaches the agent that turn runs. |
| `test_session_authority_returned_stop.py` | A Stop for a turn whose execution already returned never reaches the next turn's agent (#143290). |
| `test_session_bot_retry.py` | The owner retries a transiently failed Bot DM delivery exactly once, never unknown execution. |
| `test_session_bot_target_lifecycle.py` | The auto-created Bot Chat target can be replaced: rename and delete spend its creation identity. |
| `test_session_boundary_security_state.py` | Tests: `_clear_approval_state`, `_make_source`, `_make_event`, `_make_entry`, `_make_resume_runner`, `_make_branch_runner` … |
| `test_session_busy_compression_refusal.py` | A rewind refused because another writer holds the conversation's compression lock says so. |
| `test_session_busy_controls.py` | Public owner controls never become a second admission or change the cached prefix. |
| `test_session_bypass_policy.py` | Bypass launches freeze a typed isolation policy chosen before any profile read. |
| `test_session_chat_approval.py` | Session chat streams surface approval requests keyed by run id (#58856). |
| `test_session_client_env.py` | LC-8: a shell-launched client's allowlisted ``HERMES_*`` behaviour values ride ``session.create`` (``client_env``) and apply to that session only; an auto-started gateway stops inheriting them from whichever client star… |
| `test_session_commands.py` | Local slash resolution is not another execution owner. |
| `test_session_commands_session_scope.py` | Slash commands and discovery on a local session resolve against THAT session: ``/diff session`` through ``slash.exec`` follows its frozen checkpoint policy (``--checkpoints`` on a profile that leaves them off), and its… |
| `test_session_config_loaders.py` | A gateway-owned session runs with ``provider_routing`` and ``prefill_messages_file`` from its own profile's config as of its creation, as a new ``hermes chat`` process read them once at startup on pre-merge main (CFG-6,… |
| `test_session_config_projection.py` | Native config/model reads cross the authenticated owner without executing. |
| `test_session_context_inheritance.py` | Cross-session ContextVar *inheritance* leak guard. |
| `test_session_continuity.py` | Regression tests for gateway session continuity (#82616). |
| `test_session_create_tier_cwd.py` | Desktop create parity on the shared owner: speed tier and cwd provenance (B09 / C-hx-1). |
| `test_session_cron.py` | Cron admissions retain exact job identity and stored-job model policy. |
| `test_session_db_corrupt_fallback.py` | Gateway SessionStore must divert, not retry forever, after structural corruption. |
| `test_session_db_handle_sharing.py` | One gateway process must not hold two SessionDB handles on one state.db. |
| `test_session_db_recovery.py` | Regression coverage for recoverable gateway SessionDB opens (#93088). |
| `test_session_db_replaced_fallback.py` | Gateway SessionStore must not FTS-repair a replaced state.db (#89332). |
| `test_session_db_warning_recheck.py` | #108031: the startup state.db warning must not be broadcast once the store has healed. |
| `test_session_deferred_pick_restart.py` | A guarded deferred model pick stays answerable across a real owner restart (#139604 review). |
| `test_session_deferred_reasoning.py` | A reasoning level picked while a reply streams lands for the next turn, like a model pick (MP-24). |
| `test_session_degraded_db_continuity.py` | Regression tests: session continuity when the default/global state.db is unavailable. |
| `test_session_detach_end_reason.py` | ``session.detach {end_reason}``: the last viewer leaving an idle local session ends its row with the reason main's classic CLI wrote itself (``cli_close`` on quit, ``new_session`` / ``resumed_other`` / ``branched`` on a… |
| `test_session_dm_thread_seeding.py` | Tests for DM thread session isolation. |
| `test_session_edit_policy.py` | ACP-7: an ACP session's edit-approval policy (Default / Accept Edits / Don't Ask) is owner data. |
| `test_session_end_delegations.py` | ``exit`` and ``/new`` end that session's own async delegations in the gateway; a completion for a local session no viewer is watching is written into it as a note, not an unattended turn. |
| `test_session_env.py` | Tests: `_reset_contextvars`, `test_set_session_env_sets_contextvars`, `test_clear_session_env_restores_previous_state`, `test_get_session_env_falls_back_to_os_environ`, `test_session_key_falls_back_to_os_environ`, `test… |
| `test_session_event_observer_isolation.py` | A failed same-thread projection cannot abort canonical event publication. |
| `test_session_events_execution_stamp.py` | The execution stamp on published events marks exactly one claimed, unsettled execution. |
| `test_session_events_overflow.py` | A subscriber that overflows its bounded mailbox must learn it, not stay silently stale. |
| `test_session_follow_profile_config.py` | Bot Chat's ``follow_profile_config`` on the shared owner (B23 / C-hx-4). |
| `test_session_group_controls.py` | Canonical group management is profile-bound and never starts inference. |
| `test_session_group_execution_controls.py` | Native room controls retain the service protocol and authenticated ownership. |
| `test_session_history_canonical.py` | ``session.history`` on the canonical owner: the durable display transcript with each row's ``row_id``. |
| `test_session_hosted_controls.py` | Canonical room controls retain the original attempt fence. |
| `test_session_hosted_daemon.py` | Real native socket and canonical room member inference in a disposable daemon. |
| `test_session_hosted_rpc.py` | Room worker threads use the real authority ledger, never TUI dispatch. |
| `test_session_hosted_service.py` | Tests: `test_room_owner_survives_service_restart_and_foreign_actor_cannot_claim`, `test_private_hosted_policy_restores_without_public_source_admission`, `test_hosted_dequeue_checks_exact_task_member_and_frozen_input`, `… |
| `test_session_hosted_transport.py` | Real private owner sockets; no public identity or foreign database access. |
| `test_session_hygiene.py` | Tests for gateway session hygiene — auto-compression of large sessions. |
| `test_session_hygiene_turnhold_adoption.py` | Regression tests for #97963 — hygiene turn-hold must not burn a watermark-fenced compression attempt. |
| `test_session_id_cache_coherence.py` | Regression tests for #54947 — cross-process guard must not invalidate the agent cache when the active ``session_id`` differs from the snapshot's ``session_id``, even when both share the same ``session_key``. |
| `test_session_identity.py` | Invariants for ``gateway/session_identity.py`` (#88715 phase 1). |
| `test_session_identity_restore.py` | Identity survives restore (#88715 phase 5). |
| `test_session_images.py` | Canonical uploads stage bytes only after viewer and owner authorization. |
| `test_session_images_profile.py` | image.attach_bytes accepts its declared ``profile`` selector for the owner's own home (dokterdok N73). |
| `test_session_import_chain_ownership.py` | Import parent links and chain-aware deletes never cross principals (review M4). |
| `test_session_info.py` | Tests for GatewayRunner._format_session_info — session config surfacing. |
| `test_session_kanban.py` | Task claims, not caller-supplied launch policy, authorize Kanban execution. |
| `test_session_kanban_run_off_loop.py` | Kanban run_task's claim check and owner_admitted marker run off the owner loop (B1-26): the Kanban DB is the cross-profile dispatch bus (busy_timeout up to 120 s), so a dispatcher holding its writer must not freeze ever… |
| `test_session_kanban_turn_recovery.py` | Owner-side kanban workers retry a failed turn in place, proven from the bound frame's claim. |
| `test_session_list_allowed_sources.py` | Regression tests for the TUI gateway's ``session.list`` handler. |
| `test_session_list_live_hidden.py` | The live session.list picker honours hidden/archived like every stored picker (N110). |
| `test_session_listener_lazy_dashboard.py` | The gateway's session listener serves local sessions without importing the dashboard app. |
| `test_session_llm_oneshot.py` | Desktop's ``llm.oneshot`` on the shared gateway borrows the chat's model, as main's sidecar did. |
| `test_session_llm_oneshot_pool.py` | The owner's one-shot pool: bounded, scoped like the handler, and owned by connection and owner. |
| `test_session_load_bool.py` | Regression tests for issue #46994. |
| `test_session_local_mcp_refreeze.py` | The admission-start editor MCP re-check is best-effort, bounded and runs only for an authorized head. |
| `test_session_local_reopen_on_turn.py` | Mounting a finalized local session is a read; the first admitted turn reopens it (#85303). |
| `test_session_local_route.py` | ``-m <alias>`` at session.create is decoded by the owner against the profile's own aliases. |
| `test_session_local_title.py` | Authority-side title selection: main's classic rule, without leaking foreign titles. |
| `test_session_memory_review.py` | /memory and /skills review verbs on a LOCAL session match the classic CLI (#138901). |
| `test_session_messages_shutdown_preserve.py` | Regression tests for #72680 (retargeted). |
| `test_session_model_command_commits.py` | A typed ``/model`` admitted as a prompt on a local session commits the session's policy (#138814). |
| `test_session_model_override_credential_pool.py` | Session /model overrides must attach credential_pool for 402 rotation. |
| `test_session_model_override_persistence.py` | Per-session /model overrides must survive gateway restarts (#3659 salvage). |
| `test_session_model_override_routing.py` | Regression tests for session-scoped model/provider overrides in gateway agents. |
| `test_session_model_reset.py` | Tests that /new (and its /reset alias) clears session-scoped overrides. |
| `test_session_mutation_branch.py` | Branches are independent frozen local owners, never route aliases. |
| `test_session_mutation_branch_boundary.py` | A selected-message branch copies exactly the requested prefix (helix4u #5). |
| `test_session_mutation_cold.py` | Cold history authorization does not manufacture an execution route. |
| `test_session_mutation_compress.py` | Real summary preparation commits only against the unchanged local transcript. |
| `test_session_mutation_compress_managed.py` | Real summary preparation under the managed_workers opt-in: each turn runs out of process. |
| `test_session_mutation_compress_plugin_engine.py` | Gateway ``/compress`` runs through the session's configured plugin context engine (#143587). |
| `test_session_mutation_compress_preview.py` | ``/compress --preview`` is read-only on the canonical mutation path, every surface. |
| `test_session_mutation_coordinator.py` | Shared mutation publication and live-state coordination. |
| `test_session_mutation_delete_fences.py` | Deletion covers live descendants before their durable claim. |
| `test_session_mutation_import_owner.py` | The importer owns cold control in its receipt transaction. Hermes is single-user: the dashboard login is the machine owner, so it continues the owner's import (an exact retry), never a stranger. |
| `test_session_mutation_lineage_delete.py` | Deleting a logical local owner retires its current physical transcript too. |
| `test_session_mutation_model.py` | Explicit model changes cross the real provider wire, not profile defaults. |
| `test_session_mutation_model_busy.py` | A model pick on a session with a running turn lands for the next turn (RT-12, #138771). |
| `test_session_mutation_model_provider_identity.py` | A model pick freezes only the picked provider: an unrelated legacy entry it displaces keeps its own secret, and a respelled ``providers:`` key replaces its stale spelling (real policy/resolver). |
| `test_session_mutation_model_provider_replacement.py` | A model pick replaces the picked provider's frozen entry whole: real picker/config/runtime and a loopback wire (never a vendor), plus a real gateway process for the withdrawn-key case. |
| `test_session_mutation_model_route.py` | A canonical model pick switches FROM the route the session runs now, as one tuple. |
| `test_session_mutation_reset.py` | Reset commits the prepared physical target without changing logical ownership. |
| `test_session_mutation_retirement.py` | Native deletion retires routing and keeps only exact authorized retries. |
| `test_session_mutation_retry_repair.py` | An exact mutation retry reconciles the runtime projection the failed first attempt left behind. |
| `test_session_mutation_rpc.py` | Competing viewers must not overwrite a newer metadata revision. |
| `test_session_operator_scope.py` | Operator scope changes access, not durable authorship or execution fences. |
| `test_session_override_thread_recovery.py` | Regression tests for #30479 — session-scoped /model and /reasoning overrides silently lost on Telegram forum/DM topics and after compression session splits. |
| `test_session_policy.py` | Fresh local policy is frozen and scoped, not process launcher state. |
| `test_session_policy_coding_posture.py` | The gateway, not the client, applies the coding posture to a session that did not pick toolsets. |
| `test_session_policy_refusal_fields.py` | Every create refusal names the check that fired. |
| `test_session_policy_remote_cwd.py` | A remote or container terminal backend never runs in the client's host launch folder. |
| `test_session_policy_shadowed_custom_create.py` | A Desktop pick of a custom endpoint named like a built-in freezes the endpoint's own route (#140107). |
| `test_session_policy_verbs.py` | Desktop's typed /reasoning and Move to project on the shared owner (B14, B21 / C-hx-2). |
| `test_session_policy_workspace_readiness.py` | A removed workspace keeps a local chat readable and movable; only a turn refuses (N87). |
| `test_session_process_scope.py` | Process-global sidecar verbs never reach the shared owner's other sessions (dokterdok N2). |
| `test_session_race_guard.py` | Tests for the session race guard that prevents concurrent agent runs. |
| `test_session_read_commands.py` | Read/report slash commands run their real gateway handler for a LOCAL session (and only reads). |
| `test_session_recovery.py` | Tests for SessionRecoveryMixin.resolve_session_id_for_key — flush-recovery session_key → session_id resolution (profile aware). |
| `test_session_reset_notify.py` | Internal turns preserve the user activity clock. |
| `test_session_resume_compression_tip.py` | Fast unit test of session.resume's legacy-source branch: a pre-authority cli/tui/gui tip is handed to resolve_local_target (monkeypatched here). Canonical ``source=local`` segments are covered end to end, with a real au… |
| `test_session_resume_config_refresh.py` | CFG-2: a resumed local session runs the profile's CURRENT config-derived settings. |
| `test_session_route_identity.py` | Launch-route gates compare what the runtime resolves, not how the provider was spelled. |
| `test_session_row_cwd.py` | Session-row ``cwd`` is row metadata, split from the execution cwd: the classic CLI records what main's own lazy create stamped (``row_cwd``: the launch dir, or none for ``/new`` and ``--create-if-missing``) while the fr… |
| `test_session_setting_commands.py` | Per-session setting commands run their real gateway handler for a LOCAL session. |
| `test_session_shell.py` | Ink ``!cmd`` runs for its own local session, in that session's directory (dokterdok N22). |
| `test_session_split_brain.py` | Regression tests for issue #11016 — Telegram sessions trapped in repeated 'Interrupting current task...' while /stop reports no active task. |
| `test_session_stall_watchdog.py` | Tests for gateway session stall watchdog (#72016 item 2). |
| `test_session_state_cleanup.py` | Regression tests for _release_running_agent_state and SessionDB shutdown. |
| `test_session_steer_before_adopt.py` | A steer accepted while the claimed turn is still building its agent reaches that agent. |
| `test_session_steer_stale_busy_refusal.py` | A correction for a claimed turn with no live agent is refused, not errored (#141644). |
| `test_session_store_expiry_finalized.py` | Session expiry finalization closes sessions as session_reset. |
| `test_session_store_lock_io.py` | Regression: blocking I/O must not run while session_store._lock is held. |
| `test_session_store_prune.py` | Tests for SessionStore.prune_old_entries and the gateway watcher that calls it. |
| `test_session_store_runtime_stale_guard.py` | Runtime self-heal for stale sessions.json routing entries (#54878). |
| `test_session_store_stale_prune.py` | Tests for SessionStore._prune_stale_sessions_locked — crash self-healing. |
| `test_session_subagent_controls.py` | Desktop's subagent Steer / Stop are served by the shared owner (dokterdok N56). |
| `test_session_time_persistence.py` | Elapsed time cannot replace a durable conversation; explicit boundaries still can. |
| `test_session_title_rename_lane.py` | Which title stage is allowed to spend a platform rename. |
| `test_session_tui_config.py` | The TUI's profile preferences (/statusbar /mouse /density /details /focus /battery /theme /indicator) are written by the shared owner into the OWNING profile's config.yaml, like main's per-TUI sidecar ``config.set`` — n… |
| `test_session_tui_ops.py` | Ink's /save, /reload, /agents pause and /rollback on the shared owner (main's sidecar parity). |
| `test_session_tui_ops_session_diff.py` | The classic CLI's ``/diff session`` on the shared owner (``rollback.session_diff``): the session's frozen checkpoint policy decides, so a ``--checkpoints`` launch on a profile whose config leaves checkpoints off still d… |
| `test_session_tui_side.py` | Ink's /bg and /btw on the shared owner: a detached side agent off the session's FIFO. |
| `test_session_viewer_automation.py` | ``session.automation``: the classic CLI's /goal, /subgoal, /loop, /heartbeat managers run by the owner. |
| `test_session_ws_upgrade_failure_logged.py` | An owner that fails a session WebSocket upgrade names the cause in gateway.log (#139922). |
| `test_sethome_synthetic_thread.py` | /sethome must not persist Slack's synthetic per-message session thread. |
| `test_settled_result_size.py` | A settled turn result stores this turn's output and accounting, never per-session copies. |
| `test_settlement_lock_liveness.py` | A settlement waiting on a contended SQLite writer never stalls the owner event loop. |
| `test_settlement_off_loop.py` | Settlement's write runs off the owner loop; completion, idle info and waiters keep their order. |
| `test_setup_feishu.py` | Tests for _setup_feishu() in hermes_cli/gateway.py. |
| `test_shared_adapter_utils.py` | Adapters share the three tiny lifecycle utilities in ``gateway.platforms.helpers`` instead of re-declaring them: ``cancel_task`` (cancel + await, self-cancel safe), ``MessageDeduplicator`` (TTL + size bound) and ``bound… |
| `test_shared_busy_receive_loop.py` | A busy-session follow-up releases the adapter's serial receive loop once it is durably queued. |
| `test_shared_clarify.py` | Clarification response survives viewer detach through the real gateway worker. |
| `test_shared_gateway_harness.py` | Acceptance reports must cover the required manifest, not only successes. |
| `test_shared_group_sender_prefix.py` | Tests: `_make_runner`, `test_preprocess_includes_slack_author_mention_for_shared_thread` |
| `test_shared_platform_boilerplate.py` | Invariants for the shared adapter boilerplate in ``gateway/platforms/_shared.py``. |
| `test_shared_session_controls.py` | Shared control behavior through real execution and transport boundaries. |
| `test_shell_hook_resync.py` | CLI-5 (#134889): shell hooks under the one-gateway runtime. |
| `test_shutdown_cache_cleanup.py` | Regression tests for gateway shutdown cleaning up cached agent memory providers (issue #11205). |
| `test_shutdown_executor_quiesce.py` | Gateway shutdown quiesces its thread pool before closing state.db (#101093). |
| `test_shutdown_flush.py` | Tests for gateway/shutdown_flush.py — pending message durability (#72680). |
| `test_shutdown_flush_recovery.py` | Cross-restart recovery of cap-dropped transcript spool files (#78182). |
| `test_shutdown_forensics.py` | Tests for gateway.shutdown_forensics — fast snapshot + async diag spawn. |
| `test_shutdown_inflight_transcript_flush.py` | Regression tests for #13121 — gateway restart/shutdown must persist an in-flight (interrupted) turn's transcript to the SQLite session store so the immediate pre-restart context survives ``load_transcript()`` on resume. |
| `test_shutdown_kill_off_loop.py` | Gateway shutdown must not run process teardown on the event loop (#116327). |
| `test_shutdown_memory_provider_messages.py` | Regression tests for #15165 — gateway session shutdown must pass the agent's conversation transcript to ``shutdown_memory_provider`` so memory providers' ``on_session_end`` hooks see the real messages instead of an empt… |
| `test_shutdown_runtime_ownership.py` | Exit-state persistence is not the end of canonical writer lifetime. |
| `test_shutdown_settle_leash.py` | A gateway stop settles authority work within the watchdog leash it has left, and never closes state.db under an authority turn that outlived the settle (N59). |
| `test_shutdown_spool_limits.py` | Recovery must not retain every decoded spool payload while sorting. |
| `test_shutdown_teardown_profile_scope.py` | Multiplex invariant: gateway-hosted teardown fires memory-provider lifecycle hooks under the OWNING profile's scope (#110622). |
| `test_shutdown_watchdog.py` | Shutdown watchdog + loop heartbeat coverage for #66892. |
| `test_sibling_attach_while_profile_starting.py` | A shared socket's frame naming a profile that hot-serve is still starting. |
| `test_sibling_route_reserve.py` | A host-scoped connection's sibling route follows the profile's current authority. |
| `test_sibling_server_request_response.py` | #142849: a viewer's answer to a sibling profile's server request settles it over the shared socket. |
| `test_signal.py` | Tests for Signal messenger platform adapter. |
| `test_signal_format.py` | Tests for Signal markdown_to_signal() formatting. |
| `test_signal_plugin.py` | Signal ships as a bundled platform plugin: the registry entry carries what core used to hard-wire (requirements probe, config gate, out-of-process sender, chunking cap, setup wizard). |
| `test_signal_rate_limit.py` | Tests for the SignalAttachmentScheduler token-bucket simulator. |
| `test_silence_after_reply_line.py` | The gateway tells the agent, per turn, when a bare silence marker may not stay silent. |
| `test_silence_reply_composed.py` | Real provider-scripted AIAgent through TurnRunner and gateway response shaping. |
| `test_silence_reply_composed_stream.py` | Streamed variant: a real AIAgent streams through TurnRunner into the real stream consumer. |
| `test_silent_partial_delivery.py` | Regression coverage for #95382 / #98552 — silent partial delivery. |
| `test_simplex_plugin.py` | Tests for the SimpleX Chat platform-plugin adapter. |
| `test_single_profile_flip_keeps_launch_work.py` | A single-profile gateway that starts multiplexing in place for a newly created profile must keep the DEFAULT profile's own work running: keys injected only into the process env (docker -e, systemd Environment=, op run)… |
| `test_single_profile_host_serves_new_profile.py` | A host gateway that booted with ONE profile comes up standalone (``SINGLE_PROFILE_REASON``), and multiplexing is settled once per boot. A profile created afterwards (Desktop's New Agent, ``hermes profile create``) was t… |
| `test_skill_slash_native_boundary.py` | The messaging gateway's skill slash path stays filesystem-only: plugin skills (``ctx.register_skill``) are offered on interactive surfaces (CLI/TUI/Desktop) only. |
| `test_skill_slash_offloop.py` | Skill-slash fallthrough must not hold the gateway event loop (#111091). |
| `test_skip_context_files_wiring.py` | Per-platform ``skip_context_files`` gateway wiring (#26860). |
| `test_slack.py` | Tests for Slack platform adapter. |
| `test_slack_agent_sessions_api.py` | Slack adapter routing onto the slack-sdk Agent Sessions API (agents.sessions.*). |
| `test_slack_api_human_senders.py` | Tests for the Slack ``api_human_users`` allowlist. |
| `test_slack_approval_buttons.py` | Tests for Slack Block Kit approval buttons and thread context fetching. |
| `test_slack_block_kit.py` | Unit tests for the Slack Block Kit renderer (pure function, no adapter). |
| `test_slack_block_kit_adapter.py` | Integration tests: SlackAdapter wiring of Block Kit into send paths. |
| `test_slack_bot_auth_bypass.py` | Regression guard for Slack bot/workflow-sender authorization bypass. |
| `test_slack_channel_session_scope.py` | Regression guard for #15421 bug 1 — Slack channel session scoping. |
| `test_slack_channel_skills.py` | Tests for Slack channel_skill_bindings auto-skill resolution. |
| `test_slack_clarify_buttons.py` | Tests for Slack Block Kit interactive clarify buttons. |
| `test_slack_cron_continuable_surface.py` | Tests for the Slack ``cron_continuable_surface`` extra key and its pairing warning. |
| `test_slack_dedup_ttl.py` | Tests for Slack Socket Mode dedup TTL (#4777). |
| `test_slack_download_redirects.py` | Authenticated Slack downloads retain the token only on validated CDN hops. |
| `test_slack_download_ssrf.py` | SSRF regression tests for inbound Slack file downloads. |
| `test_slack_ignore_other_user_mentions.py` | Tests for the Slack ``ignore_other_user_mentions`` option. |
| `test_slack_log_noise.py` | C13 — Slack log noise & log privacy invariants. |
| `test_slack_mention.py` | Tests for Slack mention gating (require_mention / free_response_channels). |
| `test_slack_mention_humanization.py` | Tests for Slack inbound mention humanization + bot identity grounding. |
| `test_slack_model_picker.py` | Tests for the Slack Block Kit interactive model picker. |
| `test_slack_native_streaming.py` | Tests: SlackAdapter native streaming (chat.startStream/appendStream/stopStream). |
| `test_slack_pasted_tables.py` | Slack pasted-table recovery. |
| `test_slack_peer_agent_smoke.py` | Repeatable smoke tests for Slack peer-agent routing invariants. |
| `test_slack_plugin_action_handlers.py` | Tests for plugin-registered Slack Block Kit action handlers. |
| `test_slack_plugin_setup.py` | Tests for the Slack plugin's interactive_setup wizard. |
| `test_slack_relay_parent_command.py` | Tests: `_wire`, `test_slack_relay_parent_becomes_gateway_command` |
| `test_slack_reply_expected.py` | The Slack adapter tells the gateway whether an admitted message was addressed to the bot. |
| `test_slack_require_mention_channels.py` | Tests for the Slack ``require_mention_channels`` per-channel override. |
| `test_slack_runner_ignored_channels.py` | Tests: `_config_with_slack_extra`, `test_runner_drops_slack_ignored_channel_before_auth_hooks_and_sessions`, `test_slack_ignored_channels_env_bridge_fallback`, `test_slack_ignored_channels_extra_wins_over_env` |
| `test_slack_sdk_response.py` | Slack Web API responses must be read as real SDK responses, not dicts. |
| `test_slack_send_retry.py` | Regression: Slack send() must surface retryable + retry_after on 429. |
| `test_slack_socket_reconnect_heal.py` | Tests for Slack Socket Mode teardown (issue #46990). |
| `test_slack_status_update.py` | Tests for SlackAdapter.send_or_update_status (issue #30045, Slack). |
| `test_slack_thread_require_mention.py` | Tests: `run`, `make_adapter`, `slack_event`, `test_thread_require_mention_env_bridge`, `test_thread_require_mention_parses_yaml_and_env`, `test_thread_require_mention_allows_top_level_free_response` … |
| `test_slack_turn_recipient_identity.py` | Per-turn Slack egress identity (R3-5, connector PR gateway-gateway#210). |
| `test_slack_unfurl_duplicate_turn.py` | Regression: a link unfurl must not become a second user turn. |
| `test_slack_unfurl_nested_blocks_budget.py` | Nested ``attachments[].blocks[]`` text in link unfurls shares one bounded budget. |
| `test_slack_wake_external_bot_messages.py` | Regression tests for #63530 — Slack adapter drops human replies in threads whose root was posted by the bot via direct chat.postMessage (outside the gateway's send() path). |
| `test_slash_access.py` | Unit tests for gateway.slash_access — per-platform slash command access control. |
| `test_slash_access_dispatch.py` | Integration tests for slash command access control gating in gateway/run.py. |
| `test_slash_command_metrics.py` | Messaging-gateway slash commands reach shared metrics once each, tagged surface ``gateway``. |
| `test_slash_command_profile_scope.py` | Gateway slash commands must do their blocking work inside the routed profile. |
| `test_slash_config_writes_routed_profile.py` | Slash-command config writes must land in the routed profile's config.yaml. |
| `test_slash_dispatch_routed_scope.py` | Slash dispatch binds the ROUTED profile's runtime scope around every table handler (#119915). |
| `test_sms.py` | Tests for SMS (Twilio) platform integration. |
| `test_split_final_suffix_reconcile.py` | Regression: an authoritative final that prefix-extends a SPLIT delivery reconciles by suffix, not by full resend (PR 85796 review round 2, finding 3). |
| `test_sse_agent_cancel.py` | Tests for SSE client disconnect → agent task cancellation. |
| `test_sse_frame.py` | Byte-contract tests for the shared ``_sse_frame`` SSE encoder. |
| `test_ssl_cert_detection.py` | Gateway imports must not replace the platform trust store with a bundled CA file. |
| `test_stacked_skill_platform_disabled.py` | Regression test for stacked slash-skill invocations bypassing the per-platform ``skills.platform_disabled`` gate. |
| `test_stale_base_url_api_mode.py` | Regression tests for #25107: gateway /model switch left a stale ``base_url``/never persisted ``api_mode`` in config.yaml when switching to a custom provider whose resolver returned an empty ``base_url``. |
| `test_stale_confirmation_expiry.py` | Tests for stale confirmation text expiry in gateway history. |
| `test_stale_finalize_suppression.py` | Regression coverage for #71643 — stale streamed finalize suppression. |
| `test_stale_platform_lock_retryable.py` | Regression tests for platform-lock acquire behavior. |
| `test_stale_self_heal_agent_cache_eviction.py` | Regression test for the #54878 x #54947 interaction. |
| `test_standalone_gateway_launch_scope.py` | A standalone gateway (``multiplex_profiles`` off) keeps resolving the launch profile's credentials after a native hosted room activated the process-wide secret guard (#112878). |
| `test_standalone_injected_config.py` | The runner boundary honours a profile opt-out even for explicit --config inputs. |
| `test_standalone_send_redaction.py` | Invariant: a standalone sender's failure envelope never carries vendor secrets to the model. |
| `test_startup_agent_budget_log.py` | The startup "Agent budget" line reports the budget the turn loop enforces (#116888). |
| `test_startup_connect_parallel.py` | Regression tests for parallel platform connect at gateway startup (#83791). |
| `test_startup_environment_probe.py` | The gateway boot warm-up primes the local toolchain probe the first prompt build reads (#106064). |
| `test_startup_failed_platform_reports_degraded.py` | A configured platform that fails to start must not let the gateway report a normal run. |
| `test_startup_launch_profile_hooks_scope.py` | Multiplex invariant: the launch profile's ``hooks:`` block registers at gateway startup. |
| `test_startup_model_context_warmup.py` | Model-context warm-up inside the gateway boot warm-up (#105986). |
| `test_startup_no_eager_platform_install.py` | Regression tests: ``_apply_env_overrides`` must not lazy-install platform SDKs for platforms the user has not configured. |
| `test_startup_recovery_parks_profile.py` | Startup Bot Chat recovery of one served profile can never stop the gateway: a secondary whose durable leftovers cannot be recovered is parked like one whose store cannot be opened, and every other profile still starts (… |
| `test_startup_restart_race.py` | Tests: `StartupRaceAdapter`, `make_startup_runner`, `patch_startup_side_effects`, `test_startup_aborts_when_restart_begins_during_platform_connect`, `_patch_aborted_startup`, `test_start_gateway_does_not_start_cron_afte… |
| `test_startup_warmup_logger_offloop.py` | Boot-time warning in ``_wait_bounded_or_release`` must not park the asyncio loop on ``logging.Handler.lock`` (P1: gateway watchdog exit-75 death loop). |
| `test_startup_warmup_profile_scope.py` | Boot probes run inside the launch profile's scope under multiplex. |
| `test_startup_watchdog.py` | Startup-liveness watchdog tests (OOF-298). |
| `test_static_token_session_mutations.py` | The same verified static token owns the same session on HTTP and WebSocket. |
| `test_status.py` | Tests for gateway runtime status tracking. |
| `test_status_command.py` | Tests: `_make_source`, `_make_event`, `_make_runner`, `test_status_command_reads_token_totals_from_session_db`, `test_status_command_includes_live_agent_model_and_context`, `test_status_command_uses_most_recent_persiste… |
| `test_status_phrases.py` | Tests: `test_status_phrase_does_not_leak_raw_preview_or_args`, `test_status_phrase_path_can_load_relative_directory`, `test_choose_status_phrase_uses_custom_catalog_without_leaking_args` |
| `test_status_strict_identity_live.py` | Strict gateway identity against a REAL process holding ``gateway.lock``. |
| `test_stderr_formatting.py` | Regression tests for operator-visible gateway stderr formatting. |
| `test_steer_command.py` | Tests for the gateway /steer command handler. |
| `test_steer_fifo_overwrite.py` | Regression tests for #75164 — /steer fallback must not overwrite FIFO head. |
| `test_sticker_cache.py` | Tests for gateway/sticker_cache.py — sticker description cache. |
| `test_sticker_cache_off_loop.py` | The sticker-description cache write must not block the event loop. |
| `test_stop_chat_scope.py` | Regression tests: /stop falls back to a running turn in the SAME chat when the caller's exact session key and thread-sibling key both miss. |
| `test_stop_claim_race_class.py` | Stop of a queued admission the drain claims between the read and the cancel commit stops the claim instead of refusing ``stale_generation`` while it runs (N57 class: hosted RPC, cron). |
| `test_stop_ends_background_delegations.py` | Invariant: ``/stop`` ends the session's BACKGROUND delegate_task children too — whether the session is mid-turn (busy fast path) or idle after the dispatching turn already ended — instead of only the in-turn children, l… |
| `test_stop_thread_sibling.py` | Regression tests: /stop can interrupt a sibling participant's run in a per-user thread. |
| `test_stored_history_mount.py` | Old stored chats no loader restores open read-only for their owner (#143547 RT-30b, RT-48, RT-49, RT-54). |
| `test_stored_picker_routed_sources.py` | Regression for TUI-8 (#134889): the native picker's stored feed lists messaging and cron sessions. |
| `test_stored_session_picker.py` | The native picker enumerates old transcripts without adopting them on read. |
| `test_stream_abandon_on_turn_death.py` | Regression: a dying turn closes its native stream (PR 85796 review, B8). |
| `test_stream_consumer.py` | Tests for GatewayStreamConsumer — media directive stripping in streaming. |
| `test_stream_consumer_continuation_cut.py` | Regression tests for the word-boundary fallback continuation cut (#116312). |
| `test_stream_consumer_draft.py` | Tests for native draft streaming in GatewayStreamConsumer. |
| `test_stream_consumer_fresh_final.py` | Regression tests for the fresh-final-for-long-lived-previews path. |
| `test_stream_consumer_hot_reload.py` | Hot-reload tolerance (#72628): new consumer code paired with an old in-memory adapter. |
| `test_stream_consumer_oversized_leftover.py` | A seal must not leave an oversized leftover on the non-final send lane. |
| `test_stream_consumer_pending_media.py` | A streamed reply must never show a MEDIA:/[[...]] directive while it is still being typed. |
| `test_stream_consumer_silence.py` | Streaming intentional-silence suppression. |
| `test_stream_consumer_thread_routing.py` | Regression tests for stream consumer thread/topic routing fix. |
| `test_stream_consumer_tool_progress.py` | Tests for tool-progress-in-native-stream (single bubble) feature. |
| `test_stream_consumer_wecom_native.py` | Tests for native streaming in GatewayStreamConsumer (WeCom-style transport). |
| `test_stream_edit_flood_retry_after.py` | A flood-refused streaming edit honours the server's ``retry_after`` (#116312). |
| `test_stream_events.py` | Structured stream-event protocol + dispatcher behavior. |
| `test_stream_final_contract.py` | Regression: the consumer-declared final + interim-send contract (live findings, 2026-08-16 canary — the duplicate-final class). |
| `test_streamed_markdown_images.py` | A streamed reply's markdown/HTML images must arrive as attachments (#141806). |
| `test_streaming_tts_consumer.py` | Tests for the gateway streaming-TTS consumer and adapter contract (#60671). |
| `test_streaming_tts_gateway_regression.py` | Gateway regression: the outer finalisation path must not NameError on the streaming-TTS consumer (#60671). |
| `test_strip_markdown_links.py` | ``strip_markdown`` link handling: the default drops a link target (SMS, IRC, Feishu, QQ rely on it); ``keep_link_targets=True`` leaves a bare http(s) URL for platforms whose data detection re-links it. |
| `test_stt_config.py` | Gateway STT config tests — honor stt.enabled: false from config.yaml. |
| `test_stt_transcript_echo_config.py` | Tests: `test_stt_echo_transcripts_defaults_on_for_backwards_compatibility`, `test_top_level_stt_echo_transcripts_takes_precedence` |
| `test_stuck_loop.py` | Tests for stuck-session loop detection (#7536). |
| `test_subagent_failure_notice.py` | Subagent failures surface as one clean user-facing notice. |
| `test_subagent_protection.py` | Regression tests for #30170. |
| `test_submission_row_identity.py` | The user row a canonical admission persists names the client's ``submission_id``. |
| `test_submit_after_delete_gate.py` | A submit waiting on deletion must revalidate the session before staging its input. |
| `test_suppression_contract_matrix.py` | Contract matrix for the gateway's final-send suppression (#82656). |
| `test_surface_admission.py` | HUD / live-voice submit fields survive canonical admission and reach the model as a per-turn note. |
| `test_swept_bot_chat_fence.py` | A Bot Chat retired by a housekeeping sweep keeps its deletion fence past the retry horizon. |
| `test_switch_session_keeps_model_override.py` | A /model pin belongs to the chat route (session_key), not to one session_id (#119864). |
| `test_systemd_notify.py` | Tests for the optional systemd event-loop watchdog protocol. |
| `test_systemd_stop_mark.py` | Supervisor-ordered stops exit cleanly instead of logging a failure. |
| `test_systemd_watchdog_lifecycle.py` | Gateway lifecycle contract for the opt-in systemd watchdog. |
| `test_table_helpers.py` | Shared GFM table → bullet conversion helpers. |
| `test_task_card_destination_preflight.py` | Destination eligibility must precede transport failure and its text fallback. |
| `test_teams.py` | Tests for the Microsoft Teams platform adapter plugin. |
| `test_teams_dotenv_isolation.py` | Canaries for Teams SDK import-time dotenv isolation (#62935 / #62947). |
| `test_teams_pipeline_runtime_wiring.py` | Tests for Teams pipeline runtime wiring into the gateway. |
| `test_telegram_approval_buttons.py` | Tests for Telegram inline keyboard approval buttons. |
| `test_telegram_audio_vs_voice.py` | Tests for #24870 — Telegram: audio file attachments must NOT be routed to STT. |
| `test_telegram_auth_check.py` | Tests for Telegram adapter early authorization check. |
| `test_telegram_bot_auth_bypass.py` | Regression guard for Telegram bot-origin authorization (#32188). |
| `test_telegram_callback_auth_fail_closed.py` | Tests for Telegram adapter fail-closed auth fallback (#24457). |
| `test_telegram_caption_merge.py` | Tests for TelegramPlatform._merge_caption caption deduplication logic. |
| `test_telegram_channel_posts.py` | Regression tests for Telegram channel_post updates. |
| `test_telegram_clarify_buttons.py` | Tests for Telegram inline keyboard clarify buttons. |
| `test_telegram_closewait_limits.py` | Regression test for #31599 — Telegram general-pool CLOSE_WAIT fd leak. |
| `test_telegram_closewait_windows_live.py` | Windows live E2E probes for the CLOSE-WAIT getUpdates reconnect fix (#87057). |
| `test_telegram_cold_boot_queue.py` | Cold-boot pending-queue knob for the Telegram adapter. |
| `test_telegram_conflict.py` | Tests: `_no_auto_discovery`, `_cancel_heartbeat`, `test_polling_conflict_retries_before_fatal`, `test_conflict_retry_drops_pending_updates`, `test_conflict_retry_progress_does_not_reset_retry_ladder`, `test_polling_conf… |
| `test_telegram_connect.py` | Tests for Telegram connect() non-retryable fatal error on missing credentials. |
| `test_telegram_dm_topic_auto_transfer.py` | Telegram ``/topic`` mode: opt-in root-DM auto transfer (``dm_topic_auto_transfer``, #139136). |
| `test_telegram_documents.py` | Tests for Telegram document handling in gateway/platforms/telegram.py. |
| `test_telegram_error_redaction.py` | Regression tests for remaining unredacted Telegram transport-error sites. |
| `test_telegram_fallback_pool_release.py` | Regression test for #71593 / #63311 — Telegram fallback-pool FD leak. |
| `test_telegram_final_delivery.py` | Regression coverage for Telegram final delivery after streamed edit failure. |
| `test_telegram_format.py` | Tests for Telegram MarkdownV2 formatting in gateway/platforms/telegram.py. |
| `test_telegram_forum_commands.py` | Tests for lazy forum command registration in TelegramAdapter. |
| `test_telegram_group_gating.py` | Tests: `_restore_telegram_env`, `_make_adapter`, `_group_message`, `_dm_message`, `_mention_entity`, `_mention_entities` … |
| `test_telegram_image_precompress.py` | Tests for Telegram large-image pre-compression (salvage of PR #74893). |
| `test_telegram_inbound_warning_owner.py` | Inbound cache diagnostics use the routed owner before agent admission. |
| `test_telegram_ingress_delivery_gap.py` | Telegram ingress dispatch accounting (#102260, #130407). |
| `test_telegram_init_deadline.py` | Tests: `test_await_with_thread_deadline_abandons_and_runs_cleanup_on_timeout`, `test_await_with_thread_deadline_cleanup_error_is_swallowed`, `test_blocked_loop_after_expiry_dumps_diagnostics` |
| `test_telegram_inline_picker.py` | Tests for the Telegram inline command picker (@botname <query>). |
| `test_telegram_lazy_install_typehandler.py` | Regression test for the Telegram lazy-install rebind path (#85272). |
| `test_telegram_long_command_batching.py` | Regression tests for long slash-command pastes split by Telegram clients. |
| `test_telegram_max_doc_bytes.py` | Tests for Telegram document-size cap. |
| `test_telegram_media_read_timeout.py` | Every Telegram media upload passes the long media read timeout. |
| `test_telegram_mention_boundaries.py` | Tests for Telegram bot mention detection (bug #12545). |
| `test_telegram_mention_context.py` | Multi-bot addressing must survive routing into the agent's event without destabilising the session prompt. |
| `test_telegram_model_picker.py` | Tests for Telegram model picker thread fallback. |
| `test_telegram_network.py` | Tests for plugins.platforms.telegram.telegram_network – fallback transport layer. |
| `test_telegram_network_reconnect.py` | Tests for Telegram polling network error recovery. |
| `test_telegram_new_topic_opener.py` | Client-created Telegram DM topic: thread-less opener adopts the new topic (#136567). |
| `test_telegram_noise_filter.py` | Gateway noise/secret filtering across chat surfaces (Telegram + siblings). |
| `test_telegram_overflow_partial.py` | Regression coverage for partial Telegram overflow delivery. |
| `test_telegram_pending_update_probe.py` | TelegramAdapter wedged-getUpdates detection via pending_update_count. |
| `test_telegram_photo_interrupts.py` | Tests: `_PendingAdapter`, `_make_runner`, `test_handle_message_does_not_priority_interrupt_photo_followup` |
| `test_telegram_polling_health_confirmation.py` | Regression tests for the Telegram polling health-confirmation log (#90504). |
| `test_telegram_polling_progress.py` | Behavior contract for generation-safe Telegram polling progress. |
| `test_telegram_polling_stall_watchdog.py` | TelegramAdapter polling-stall watchdog (#92991). |
| `test_telegram_prune_stale_topic_binding.py` | Regression tests for #31501 — prune stale Telegram DM topic bindings. |
| `test_telegram_reactions.py` | Tests for Telegram message reactions tied to processing lifecycle hooks. |
| `test_telegram_reply_mode.py` | Tests for Telegram reply_to_mode functionality. |
| `test_telegram_reply_quote.py` | Tests for Telegram native partial-quote handling in _build_message_event. |
| `test_telegram_rich_messages.py` | Tests for Bot API 10.1 Rich Messages (sendRichMessage) on Telegram. |
| `test_telegram_rich_newlines.py` | Tests for rich-message newline normalization (issue #46070). |
| `test_telegram_send_draft_format.py` | TelegramAdapter.send_draft MarkdownV2 formatting parity. |
| `test_telegram_send_path_health.py` | TelegramAdapter send-path health gating after reconnect storms. |
| `test_telegram_send_reconnect_wait.py` | Telegram send() must wait for reconnect instead of dropping the final reply. |
| `test_telegram_shared_outbound_budget.py` | Shared per-chat send+edit pacing budget (#116312). |
| `test_telegram_slash_confirm.py` | Regression guard: send_slash_confirm must use format_message + MARKDOWN_V2. |
| `test_telegram_split_send_flood.py` | Split Telegram replies under flood control: no duplicated head, no interleaving, no hammering. |
| `test_telegram_start_polling_timeout.py` | Regression tests for #59614: start_polling() must be time-bounded. |
| `test_telegram_status_indicator.py` | Tests for the Telegram bot status indicator. |
| `test_telegram_status_update.py` | Tests for TelegramAdapter.send_or_update_status (issue #30045). |
| `test_telegram_text_batch_perf.py` | Regression tests for the Telegram text-batch adaptive-delay fast-path and _env_float_clamped helper introduced by PR #10388 (Telegram latency tuning). |
| `test_telegram_text_batching.py` | Tests for Telegram text message aggregation. |
| `test_telegram_text_link_expansion.py` | Tests for Telegram ``text_link`` entity expansion in inbound messages. |
| `test_telegram_thread_fallback.py` | Tests for Telegram topic/thread routing fallbacks. |
| `test_telegram_topic_mode.py` | Tests for Telegram private-chat topic-mode routing. |
| `test_telegram_topic_profile_isolation.py` | Issue #76423 — SessionDB: telegram topic tables namespace by profile. |
| `test_telegram_topic_profile_routing.py` | Issue #76423 — Gateway routes source.profile into telegram topic state. |
| `test_telegram_typing_backoff.py` | Telegram typing indicator transient backoff tests. |
| `test_telegram_typing_retrigger.py` | Telegram post-send typing re-arm is scheduled off the send path and collapsed per chat (#111727). |
| `test_telegram_username_chat_id.py` | Tests for Telegram username (non-numeric) chat_id handling (#13206). |
| `test_telegram_video_metadata.py` | Telegram videos over ~10 MB must carry explicit geometry and a thumbnail. |
| `test_telegram_voice_caption_markdown.py` | Telegram voice-message captions must render markdown (#32029). |
| `test_telegram_voice_duration.py` | Telegram voice/audio messages must carry an explicit duration. |
| `test_telegram_voice_v0_regressions.py` | Tests: `_source`, `_runner`, `_PendingVoiceAdapter`, `_PendingVoiceAgent`, `_run_agent_runner`, `test_pending_voice_interrupt_reuses_transcript_and_echo` … |
| `test_telegram_webhook_secret.py` | Tests for GHSA-3vpc-7q5r-276h — Telegram webhook secret required. |
| `test_terminal_commit_crash.py` | A committed result survives owner SIGKILL without pausing its follower. |
| `test_text_batch_delay_defaults.py` | Text-batch debounce defaults must not exceed Telegram's cadence (#44883, #25056). |
| `test_text_batch_flush_invariants.py` | Invariants for BasePlatformAdapter's inbound text-batch flush. |
| `test_text_batching.py` | Tests for text message batching across all gateway adapters. |
| `test_thread_tracker_mark_off_loop.py` | The thread-participation tracker's persist must not block the event loop. |
| `test_ticket_profile_scope.py` | An issued interactive ticket keeps its profile scope across sibling selectors (#106742 W1). |
| `test_timestamp_sidecar_replay.py` | Timestamp rendering must not discard the exact sent user-message prefix. |
| `test_tini_shim.py` | Unit tests for docker/tini-shim.sh argument stripping (#66679). |
| `test_title_command.py` | Tests for /title gateway slash command. |
| `test_tool_log_mode.py` | Tests for the `log` tool_progress mode (salvage of #3459 / #3458). |
| `test_tool_response_drop_recovery.py` | Regression tests for tool-using response silent drop (issue #29346). |
| `test_transcript_offset.py` | Tests for transcript history offset fix. |
| `test_transcript_read_failure.py` | A failed transcript read must not masquerade as an empty history (#100788). |
| `test_transient_failure_transcript.py` | Tests for #7100 — transient failures (429/timeout) must not drop the user message from the transcript. |
| `test_tts_media_routing.py` | Tests for cross-platform audio/voice media routing. |
| `test_tui_approval_redaction.py` | Regression test for TUI approval-prompt credential redaction (#48456). |
| `test_tui_busy_default.py` | A TUI session with no explicit ``display.busy_input_mode`` reports main's TUI default ``queue`` (``ui-tui/src/app/useConfigSync.ts`` TUI_BUSY_DEFAULT): typing while the agent works queues the next prompt instead of redi… |
| `test_tui_context_breakdown_scope.py` | ``session.context_breakdown`` (Desktop context popover) and TUI ``/context`` measure the compression tip's model history, and the popover's categories survive a session with no resident agent. |
| `test_tui_detach_end_stamp.py` | The TUI's close of a canonical session stamps the row as main's sidecar did (PR #106742 rows 28/35/38). |
| `test_tui_session_reads.py` | A TUI session's /status, /context and /cron on the shared owner read as main's TUI sidecar did; every local session's /cron reads run main's handler on the owner, and its writes run there only when the classic CLI sends… |
| `test_tui_slash_worker_path.py` | Regression test for slash_worker PATH construction (#83845). |
| `test_turn_context.py` | Unit tests for the TurnContext/TurnRunner seam extracted from ``GatewayRunner._run_agent_inner`` (gateway/turn_context.py + gateway/run.py). |
| `test_turn_executor_reuse.py` | The turn executor reuses parked workers, and a reused thread carries nothing from its last turn. |
| `test_turn_lease.py` | Behavior tests for the per-session turn lease (#64934). |
| `test_turn_pool_unbounded.py` | An accepted turn must never queue behind other turn bodies on the gateway's turn pool. |
| `test_turn_request_overrides.py` | Regression tests: the gateway must preserve a custom provider's ``request_overrides`` on per-turn agent config. |
| `test_turn_result_retention.py` | Receipt retries preserve transcript boundaries, successor ownership and media identity. |
| `test_turn_runner_reply_identity.py` | The session-authority turn stamps its reply frames with the same wire identity as tui_gateway's ``_emit``. |
| `test_typing_indicator_toggle.py` | Per-platform typing-indicator toggle (PlatformConfig.typing_indicator). |
| `test_unauthorized_dm_behavior.py` | Tests: `_clear_auth_env`, `_make_event`, `_make_runner`, `test_whatsapp_lid_user_matches_phone_allowlist_via_modern_session_mapping`, `test_simplex_allowlist_matches_contact_id_not_display_name`, `test_telegram_group_us… |
| `test_unauthorized_sender_notices.py` | Unauthorized-sender copy: the pairing DM tells a stranger what happens next, and an ignored DM (allowlist configured) stays silent toward the stranger while the owner gets the approve command in the log and, once, in th… |
| `test_unavailable_skill_hint.py` | Tests for gateway.run._check_unavailable_skill. |
| `test_undo_rewind_session.py` | Tests for SessionStore.rewind_session — the gateway /undo [N] primitive. |
| `test_unified_gateway_native_live.py` | Native live proof of the unified gateway runtime on the CURRENT host OS. |
| `test_unified_runtime_init_multiplex.py` | The unified runtime's init path must build per-profile registries, not process-wide ones. |
| `test_unknown_automation_settles.py` | GW-10 (#139532): an ``unknown`` admission no person is waiting on settles as interrupted. |
| `test_unknown_command.py` | Tests for gateway warning when an unrecognized /command is dispatched. |
| `test_unknown_receipt_boundaries.py` | Receipt retries preserve transcript boundaries, successor ownership and media identity. |
| `test_unknown_resolution_physical_worker.py` | Resolving an unknown admission must also retire its physical worker assignment. |
| `test_unmanaged_idle_exit.py` | An auto-started (``--idle-exit``) gateway exits once idle; anything it serves keeps it up. |
| `test_unmanaged_idle_exit_restart_pending.py` | An auto-started gateway that installed a dependency it cannot load retires once its turn ends. |
| `test_unserve_release_order.py` | Unserve releases a profile's gateway.lock only after its handles in that home close (N97). |
| `test_unviewed_completion_notes.py` | An unviewed local completion becomes a note through the gateway FIFO, never a lost or early one. |
| `test_update_command.py` | Tests for /update gateway slash command. |
| `test_update_cron_drain.py` | Regression tests for #60432. |
| `test_update_streaming.py` | Tests for /update live streaming, prompt forwarding, and gateway IPC. |
| `test_upstream_native_admission.py` | A fresh native input from an adapter that declares ``authorization_is_upstream`` is admitted without a principal allowlist (#139199). |
| `test_usage_command.py` | Tests: `_make_mock_agent`, `_make_runner`, `TestUsageCachedAgent`, `TestUsageAccountSection`, `TestUsageReset`, `TestUsageContextBreakdown` |
| `test_usage_limit_offer.py` | Messaging: after a usage-window refusal the gateway offers the plan's recommended model as a choice button on platforms that already have them, else one line of text. Never a credits button (anyone in the room could spe… |
| `test_used_delete_restart.py` | Real daemon delete/restart: history disappears, exact authorized retries survive. |
| `test_verbose_command.py` | Tests for gateway /verbose command (config-gated tool progress cycling). |
| `test_video_context_note.py` | Tests for video attachment context notes in gateway turns. |
| `test_viewer_close_lifecycle.py` | The owner runs a session's end-of-conversation lifecycle when its last viewer closes it. |
| `test_vision_memory_leak.py` | Tests for _enrich_message_with_vision — regression for #5719. |
| `test_vision_preprocess.py` | Gateway vision pre-process merges the analysis with the user text. |
| `test_voice_command.py` | Tests for the /voice command and auto voice reply in the gateway. |
| `test_voice_mode_platform_isolation.py` | Tests for voice mode platform isolation (bug #12542). |
| `test_voice_transcode.py` | Voice transcode arc (#97873): [[audio_as_voice]] works for every audio format. |
| `test_voice_transcript_dedup_scope.py` | Voice-transcript dedup belongs to the bot that heard the utterance and the conversation it is bound to. |
| `test_wake_admitted_before_drain.py` | A wake admitted before a restart drain begins must still run. |
| `test_wake_admitted_before_drain_authority.py` | A wake receipted before a restart drain must run exactly once on the authority route too. |
| `test_wake_delivery.py` | Tests for gateway/wake.py — background wake delivery. |
| `test_wake_during_restart_drain.py` | A wake that arrives while the gateway drains for a restart must be refused, not lost. |
| `test_wake_during_restart_drain_authority.py` | A wake that arrives while the gateway drains must be refused retryably on the authority route too. |
| `test_warning_delivery_real_producers.py` | Actual adapter producers; only vendor transport and pacing clocks replaced. |
| `test_warning_emission_boundary.py` | Shared channel warning boundary: policy, actual receipt, and stream isolation. |
| `test_warning_notification_contracts.py` | Diagnostic suppression preserves real producer outcomes and control paths. |
| `test_warning_notifications.py` | Warning delivery is independent of normal replies and operational state. |
| `test_warning_notifications_transport.py` | Real native/relay send paths and profile-scoped effective warning policy. |
| `test_warning_render_boundary.py` | UI sink gating never suppresses the producer or interprets its return value. |
| `test_warning_wiring_conservation.py` | Actual per-turn wiring must retain observers before presentation scope binds. |
| `test_watch_automation_identity.py` | Distinct pattern hits must not collapse into one completion identity. |
| `test_watch_notification_reset_pin.py` | A watch notice pinned to a session that ended at a user boundary (/new) is dropped, not requeued forever: the session authority refuses it ``admission_conflict`` on every drain tick (#141562). Real GatewayRunner, Discor… |
| `test_watchdog_review.py` | Regressions for #76354 review S1/S2/S4 — activity write budget, watchdog pre-delivery revalidation, and import/export activity asymmetry. |
| `test_weak_credential_guard.py` | Tests for gateway weak credential rejection at startup. |
| `test_webapp_browser_credential.py` | The Webapp's browser credential file stays private to the gateway's OS user. |
| `test_webapp_bundle.py` | A Webapp whose bundle is not built is reported unavailable, with how to build it. |
| `test_webapp_cookie_writes.py` | The gateway's Webapp on a wildcard host takes cookie-authenticated writes only from its own page. |
| `test_webapp_gated_sign_out.py` | Signing out of a gateway's Webapp behind the sign-in gate signs the browsers out (a real gateway). |
| `test_webapp_listener.py` | The browser-hosted Desktop on the gateway's own listener: config, bind address and browser credential. |
| `test_webapp_listener_fallback.py` | The gateway keeps a listener for native clients whatever happens to the Webapp's. |
| `test_webapp_owner_identity.py` | The Webapp is the machine owner: a signed-in tab and native Desktop share Group Chats and history. |
| `test_webapp_public_url.py` | The Webapp's own public URL, ``webapp.public_url``, and never ``dashboard.public_url``. |
| `test_webapp_settings.py` | A ``webapp:`` block that asks for the Webapp but cannot be used says why. |
| `test_webhook_adapter.py` | Unit tests for the generic webhook platform adapter. |
| `test_webhook_authority.py` | Signed TCP ingress must not acknowledge an uncommitted input. |
| `test_webhook_coalescing.py` | Per-route webhook event coalescing (#92066): rapid distinct events on one entity debounce into a single agent run on the latest event's state; unrelated or unkeyed events are never merged. |
| `test_webhook_cron_trigger.py` | Tests for the webhook adapter's ``cron_job`` route mode. |
| `test_webhook_deliver_only.py` | Tests for the webhook adapter's ``deliver_only`` route mode. |
| `test_webhook_durable_destination.py` | Admission owns the exact destination, never process-local send state. |
| `test_webhook_dynamic_routes.py` | Tests for webhook adapter dynamic route loading. |
| `test_webhook_filter_interpreter.py` | Webhook filter scripts run under the Git-Bash-safe interpreter and log silent failures. |
| `test_webhook_finalization_recovery.py` | Settled webhook admissions remain closeable without repeating their turn. |
| `test_webhook_integration.py` | Integration tests for the generic webhook platform adapter. |
| `test_webhook_mcp_events.py` | Webhook deliveries on MCP event routes: the signed verification challenge is echoed without an agent run, control envelopes update or drop the route, and an occurrence is deduplicated by its ``eventId`` rather than the… |
| `test_webhook_offloop_delivery.py` | Event-loop liveness for webhook GitHub-comment delivery (Pattern A). |
| `test_webhook_profile_egress.py` | Webhook egress under multiplex stays bound to the routed profile (#65939, #84266). |
| `test_webhook_replay_scope.py` | Webhook replay/credential invariants that the durable ledger does not cover (PR #106742 security lane). |
| `test_webhook_route_toolsets.py` | Per-route webhook toolset overrides (adapter.toolsets_for_source). |
| `test_webhook_session_close.py` | A late webhook finalizer cannot end a replacement route or generation. |
| `test_webhook_signature_rate_limit.py` | Test that HMAC signature validation happens BEFORE rate limiting. |
| `test_webhook_startup_restore_admission.py` | GW-2: an admission the authority is executing is never parked by the startup-restore gate. |
| `test_wecom.py` | Tests for the WeCom platform adapter. |
| `test_wecom_callback.py` | Tests for the WeCom callback-mode adapter. |
| `test_wecom_double_send.py` | Repro tests for the WeCom native-streaming "同一回复发两条" duplicate. |
| `test_wecom_per_turn.py` | Tests for per-turn stream isolation and concurrent consumer scenarios. |
| `test_wecom_stream_dup_fix.py` | Behavior-contract tests for the WeCom native-streaming "重复气泡" fix. |
| `test_weixin_plugin.py` | Tests for the Weixin platform adapter. |
| `test_weixin_secret_scope.py` | Weixin adapter secret-scope regression tests. |
| `test_weixin_typing.py` | Tests for WeChat iLink typing ticket refresh logic (issue #38085). |
| `test_weixin_voice_warning_policy.py` | Voice downgrade diagnostic is optional; the actual attachment is not. |
| `test_whatsapp_allowlist_lid_resolution.py` | WhatsApp DM/group allowlist must resolve phone↔LID aliases at intake. |
| `test_whatsapp_bridge_dir_resolution.py` | Tests for resolve_whatsapp_bridge_dir() — read-only install tree handling. |
| `test_whatsapp_bridge_pidfile.py` | Regression tests: the WhatsApp stale-bridge cleanup must never kill a stranger. |
| `test_whatsapp_bridge_port_release.py` | Behavior tests: the old WhatsApp bridge must release its port before the new one spawns. |
| `test_whatsapp_cloud.py` | Tests for the WhatsApp Cloud API adapter (Phase 2). |
| `test_whatsapp_cloud_allowed_users.py` | Regression tests for PR #58448 salvage: the documented WHATSAPP_CLOUD_ALLOWED_USERS / WHATSAPP_CLOUD_ALLOW_ALL_USERS env vars must actually drive the DM intake gate. |
| `test_whatsapp_connect.py` | Tests for WhatsApp connect() error handling. |
| `test_whatsapp_delivery_status_log.py` | Delivery/read status of messages Hermes sends on WhatsApp is logged to gateway.log, one line per change. |
| `test_whatsapp_formatting.py` | Tests for WhatsApp message formatting and chunking. |
| `test_whatsapp_from_owner.py` | Tests for WhatsApp owner-message metadata and source-level text tagging. |
| `test_whatsapp_group_allowlist_env.py` | Regression for #72529 — the WhatsApp adapter never read WHATSAPP_GROUP_ALLOWED_USERS. |
| `test_whatsapp_group_gating.py` | Tests: `_make_adapter`, `_group_message`, `_dm_message`, `test_group_messages_can_require_direct_trigger_via_config`, `test_regex_mention_patterns_allow_custom_wake_words`, `test_invalid_regex_patterns_are_ignored` … |
| `test_whatsapp_identity.py` | Tests for gateway.whatsapp_identity alias resolution path. |
| `test_whatsapp_media_path_profile.py` | Regression: the WhatsApp inbound-media path validator follows the active profile override. |
| `test_whatsapp_multiplex.py` | Profile-local WhatsApp credentials and non-destructive secondary startup. |
| `test_whatsapp_multiplex_secret_scope.py` | Regression test for #75349 — WhatsApp bridge loses WHATSAPP_* vars under multiplex. |
| `test_whatsapp_native_delivery.py` | Tests: `TestWhatsAppNativeFormatting`, `test_send_location_posts_to_bridge_location_endpoint` |
| `test_whatsapp_reply_prefix.py` | Tests for WhatsApp reply_prefix config.yaml support. |
| `test_whatsapp_stale_bridge.py` | Tests for the WhatsApp stale-bridge staleness handshake. |
| `test_whatsapp_text_batching.py` | Text-debounce batching for the WhatsApp adapter (issue #35301). |
| `test_whatsapp_to_jid.py` | Unit tests for gateway.whatsapp_identity.to_whatsapp_jid. |
| `test_windows_venv_import_guard.py` | Gateway Windows venv import guards (#122183, #57467, #139085). |
| `test_worker_admission_reservation.py` | Owner-issued admission reservations never weaken idle public registration. |
| `test_worker_agent_execution.py` | Unmocked worker AIAgent / loopback inference / ordinary owner transport. |
| `test_worker_compression_admission.py` | Admission-backed automatic compression over the ordinary owner and HTTP model. |
| `test_worker_compression_execution.py` | Real compression, real registered worker, real ordinary owner transport. |
| `test_worker_delegation_bridge.py` | Authenticated worker ledger bridge publishes committed owner events. |
| `test_worker_delegation_receipts.py` | Ledger retry durability shares the worker sequence and epoch boundary. |
| `test_worker_ledger_tool_execution.py` | Tool-enabled ordinary-daemon proof, distinct from unregistered ledger hooks. |
| `test_worker_lifecycle_execution.py` | Ordinary owner and worker exercise lifecycle parity without worker SQLite. |
| `test_worker_persistence.py` | Separate worker, ordinary daemon, production private control and authenticated WS. |
| `test_worker_register_restriction.py` | worker.register requires the worker-adoption capability a launched worker's ticket carries (B1-14): an interactive client (session:control) must not park a 'registered' compute row that nothing reaps, pausing the sessio… |
| `test_worker_reservation_automation_principal.py` | A managed worker adopts an automation admission's reservation as the owner's own OS user (#144139). |
| `test_worker_rotation_adoption.py` | Real compression, real registered worker, real ordinary owner transport. |
| `test_worker_rotation_execution.py` | Real compression, real registered worker, real ordinary owner transport. |
| `test_ws_auth_retry.py` | Tests for auth-aware retry in the Mattermost WS loop. |
| `test_ws_auth_retry_verifier_probe.py` | Adversarial verifier probes for the mattermost-ws-401-classify fix (commit fdd1a11ac5). |
| `test_ws_dial_happy_eyeballs.py` | Cold-start WebSocket dials race IPv6/IPv4 (#114265). |
| `test_yolo_command.py` | Tests for gateway /yolo session scoping. |
| `test_yolo_launch_tristate.py` | Routing entries nobody toggled follow the ``--yolo`` launch policy; only an explicit OFF revokes it. |
| `test_yolo_restart_revocation.py` | An explicitly revoked --yolo launch stays off in a fresh gateway interpreter. |
| `test_yuanbao_forwarded_heartbeat.py` | ForwardedRecordsParseMiddleware must actually send its loading heartbeat. |
| `test_yuanbao_integration.py` | test_yuanbao_integration.py - Yuanbao 模块集成测试 |
| `test_yuanbao_markdown.py` | test_yuanbao_markdown.py - Unit tests for yuanbao_markdown.py |
| `test_yuanbao_media_ssrf.py` | SSRF protection tests for yuanbao_media.download_url(). |
| `test_yuanbao_pipeline.py` | test_yuanbao_pipeline.py - Unit tests for the inbound middleware pipeline. |
| `test_yuanbao_plugin_registration.py` | Yuanbao ships as a bundled platform plugin: registry entry shape + no core wiring left. |
| `test_yuanbao_proto.py` | test_yuanbao_proto.py - yuanbao_proto 单元测试 |
| `test_yuanbao_reconnect_set_active.py` | test_yuanbao_reconnect_set_active.py - Verify _do_reconnect restores the active singleton. |
| `test_yuanbao_secret_scope.py` | Yuanbao authorization-scope regression tests (#93522). |
| `test_yuanbao_shutdown.py` | test_yuanbao_shutdown.py - Yuanbao adapter shutdown teardown timing. |

## `tests/hermes_cli/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `anon_portal.py` | The fake NAS anonymous surface shared by the free-tier tests. |
| `benchmark_session_timeline.py` | Reproducible HTTP payload benchmark using generated data, never a live store. |
| `conftest.py` | Fixtures shared across hermes_cli tests. |
| `conftest_dashboard_auth.py` | Stub auth provider + shared fixtures for dashboard-auth tests. |
| `fixtures/plugin_compat_legacy/__init__.py` | Frozen legacy plugin used by the behavior compatibility suite. |
| `fixtures/plugin_compat_legacy/plugin.yaml` | Frozen plugin fixture for native behavior compatibility |
| `gateway_client_options.py` | Explicit two-checkout native client/runtime compatibility probe option. |
| `native_gateway_client.py` | A test client that reaches the dashboard app as native Desktop reaches the gateway's own listener. |
| `plugin_worker_support.py` | Offline plugin command fixtures; only tool acquisition is substituted. |
| `test_active_session_exclusivity.py` | Per-session exclusivity in the active-session registry. |
| `test_active_sessions.py` | Tests: `_backdate_leases`, `test_resolve_max_concurrent_sessions_values`, `test_cross_process_acquire_claims_only_one_last_slot`, `test_release_orphaned_leases_reclaims_only_unowned_own_pid_entries`, `test_release_orpha… |
| `test_actual_provider.py` | Regression tests for the Actual Computer provider wiring. |
| `test_agent_env_advertisement.py` | Tests for the AI_AGENT / HERMES_AGENT harness-attribution env vars. |
| `test_agent_import_left_core.py` | `hermes import-agent` and `hermes claw` (OpenClaw migration) left core for the agent-importers catalog plugin. |
| `test_agent_plugins.py` | Agent Plugins v1 portable package validation tests. |
| `test_aggregator_overlap_twin_upstream.py` | Aggregator overlap strip vs a user row that IS the same upstream as a built-in aggregator (#115623). |
| `test_ai_gateway_models.py` | AI Gateway model list and pricing translation. |
| `test_alibaba_coding_plan_cn_provider_listing.py` | alibaba-coding-plan and alibaba-coding-plan-cn must not both appear in the /model picker off a single shared key (#101122). |
| `test_anon_auth_core.py` | Nous free tier core: identity lifecycle, token-acquisition seam, routing pin, opt-out. |
| `test_anon_challenge.py` | Nous free tier: the browser challenge in front of a token exchange (``hermes_cli.anon_challenge``). |
| `test_anon_connectors_token.py` | Nous free tier: the connectors-only guest token (NAS hermes-portal#1516). |
| `test_anon_desktop_signin.py` | Desktop (dashboard API) Nous sign-in: the plain device-code login, then the free tier's handoff. |
| `test_anon_failure_modes.py` | Nous free tier: every way the account service or the wire can refuse the free tier, and what Hermes does with each (the failure-mode contract behind the desktop's onboarding copy). |
| `test_anon_first_notice.py` | The one-time free-tier notice flag: pending once for a guest that carries the trial, then never again. |
| `test_anon_picker.py` | Model pickers under a Nous free-tier identity. |
| `test_anon_sign_in_flow.py` | ``anon_auth.run_sign_in``: the one plain device-code sign-in every surface renders. |
| `test_anon_surfaces.py` | Nous free tier on the read-only display surfaces and the keepalive. |
| `test_anon_upgrade.py` | ``hermes auth upgrade``: the plain device-code sign-in, then the free tier's apps move over. |
| `test_anthropic_model_flow_stale_oauth.py` | Tests for Bug #12905 fix — stale OAuth token detection in hermes model flow. |
| `test_anthropic_models_pagination.py` | Anthropic /v1/models cursor pagination — regression tests. |
| `test_anthropic_oauth_flow.py` | Tests for Anthropic OAuth setup flow behavior. |
| `test_anthropic_oauth_routes_to_messages_api.py` | Regression coverage for issue #32243. |
| `test_anthropic_picker_curated.py` | Regression tests for the Anthropic model-picker dropping curated aliases. |
| `test_anthropic_pool_model_discovery.py` | Tests: `_Response`, `test_anthropic_picker_discovers_models_with_pool_api_key`, `test_anthropic_pool_api_key_overrides_conflicting_active_endpoint` |
| `test_anthropic_provider_persistence.py` | Tests for Anthropic credential persistence helpers. |
| `test_api_key_providers.py` | Tests for API-key provider support (z.ai/GLM, Kimi, MiniMax, AI Gateway). |
| `test_api_mode_aliases.py` | Legacy ``api_mode`` spellings must keep selecting the transport they named. |
| `test_apply_model_switch_result_context.py` | Regression test for the `/model` picker confirmation display. |
| `test_apply_profile_override.py` | Regression tests for _apply_profile_override HERMES_HOME guard (issue #22502). |
| `test_approval_transport.py` | Approval transport plugin contract and fail-closed host routing. |
| `test_approvals_command.py` | Cross-surface contract for the persistent /approvals mode command. |
| `test_approvals_suggest.py` | Tests for ``hermes approvals suggest`` (hermes_cli/approvals_suggest.py). |
| `test_approvals_test.py` | Tests for ``hermes approvals test`` — dry-run approval verdict CLI. |
| `test_arcee_provider.py` | Tests for Arcee AI provider support — standard direct API provider. |
| `test_archive_safe.py` | Tests for the shared tar.gz writer (``hermes_cli.archive_safe.make_targz``). |
| `test_argparse_flag_propagation.py` | Tests for parent→subparser flag propagation. |
| `test_at_context_completion_filter.py` | Regression test: `@folder:` completion must only surface directories and `@file:` must only surface regular files. |
| `test_atomic_json_write.py` | Tests for utils.atomic_json_write — crash-safe JSON file writes. |
| `test_atomic_yaml_write.py` | Tests for utils.atomic_yaml_write — crash-safe YAML file writes. |
| `test_audio_playback_guard.py` | Regression tests for the test-suite audio-playback guard. |
| `test_audio_router_scope.py` | Scope-isolation regression for the ElevenLabs voices route's env fallback. |
| `test_audio_stream_native_ws.py` | A local Desktop's voice sockets ride the grant of its ``/api/ws`` dial (RT-71, RT-80). |
| `test_auth_codex_bounded_body.py` | Codex OAuth/device-auth responses are read through a 1 MiB body cap (#55253). |
| `test_auth_codex_browser_login.py` | ``hermes auth add openai-codex --browser``: opt-in loopback authorization-code + PKCE (#95743). |
| `test_auth_codex_no_proxy_ipv6.py` | ``_codex_http_client`` survives a bracketed-IPv6 NO_PROXY environment (#118159). |
| `test_auth_codex_provider.py` | Tests for Codex auth — tokens stored in Hermes auth store (~/.hermes/auth.json). |
| `test_auth_codex_quota_probe.py` | Tests for the Codex upstream-quota-restored probe and cooldown clearing. |
| `test_auth_codex_self_heal.py` | Regression tests for Codex refresh_token self-heal (cross-store rotation). |
| `test_auth_commands.py` | Tests for auth subcommands backed by the credential pool. |
| `test_auth_key_prefix_skip.py` | Regression tests for #93593: a malformed provider key in .env must not silently shadow a valid credential-pool key. |
| `test_auth_lock_timeout_diagnosis.py` | The auth-store lock timeout must name the lock file, and a holder only when one is real. |
| `test_auth_model_key_env.py` | Regression tests for #106336: Desktop-saved registry-provider credentials. |
| `test_auth_nous_provider.py` | Regression tests for Nous OAuth refresh and inference JWT interactions. |
| `test_auth_placeholder_rejection.py` | Placeholder credentials must read as "not configured", never as a usable secret. |
| `test_auth_pool_operations.py` | OAuth control commands against a loopback token endpoint. |
| `test_auth_profile_fallback.py` | Tests for cross-profile auth fallback. |
| `test_auth_provider_gate.py` | Tests for is_provider_explicitly_configured(). |
| `test_auth_provider_scope.py` | resolve_provider auto-detection must read provider keys through the profile secret scope under multiplex (#86917). |
| `test_auth_qwen_provider.py` | Tests for Qwen OAuth provider authentication (hermes_cli/auth.py). |
| `test_auth_registry_home_scope.py` | Auth registry rows and provider aliases belong to the profile home that declares them. |
| `test_auth_registry_profile_rows.py` | A plugin profile's mirrored ``hermes auth`` registry row: shape, place, and env auto-detect. |
| `test_auth_store_read_failure.py` | A transient read failure on auth.json must not degrade to an empty store. |
| `test_auth_store_windows_encoding.py` | Regression tests for auth store encoding on Windows. |
| `test_auth_toctou_file_modes.py` | Regression tests for TOCTOU-safe credential file writers in ``hermes_cli.auth``. |
| `test_auth_xai_oauth_provider.py` | Tests for xAI Grok OAuth — tokens stored in Hermes auth store (~/.hermes/auth.json). |
| `test_authenticated_providers_exhausted_pool.py` | Regression test for #45759. |
| `test_aux_assignment_reasoning_effort.py` | Desktop Settings → Model → Auxiliary can set a task's reasoning effort (#89259, salvage #90649). |
| `test_aux_config.py` | Tests for the auxiliary-model configuration UI in ``hermes model``. |
| `test_aux_picker_inventory.py` | Auxiliary-task pickers share one provider-inventory substrate. |
| `test_azure_detect.py` | Tests for hermes_cli.azure_detect — transport & model auto-detection. |
| `test_azure_foundry_entra.py` | Tests for Azure Foundry Entra ID runtime resolution. |
| `test_backend_retirement.py` | Cooperative retirement is a reservation, never a sampled idle verdict. |
| `test_backup.py` | Tests for hermes backup and import commands. |
| `test_backup_all_profiles.py` | Tests for the #66140 fix: pre-update snapshots cover every profile. |
| `test_backup_cron_prompts_lock.py` | Cron prompt recovery (#82990) must serialize with cron writers: it re-reads jobs.json under the canonical cron lock and publishes via the locked, merge-aware save path, so cron edits committed while recovery runs are ne… |
| `test_backup_import_deleted_holder.py` | Invariant: importing a backup must not publish a NEW state.db inode while a live process still holds the deleted one (#110179). |
| `test_backup_path_errors.py` | Regression test: `hermes backup -o <bad path>` errors cleanly (round-3 SUB-01). |
| `test_backup_preflight.py` | Preflight must work while the app is broken and its database is still live. |
| `test_backup_preflight_staging.py` | A stopped or killed update pre-flight must not leave full-size staging copies behind. |
| `test_backup_remote_config.py` | The post-update model/MoA safety net in a Remote Config deployment (#122509). |
| `test_backup_retention_roundtrip.py` | Tests for hermes backup retention (--keep) and the session-store import round trip. |
| `test_backup_stability.py` | Tests: `test_backup_lock_rejects_a_second_operation`, `test_atomic_output_publishes_only_after_clean_close`, `test_atomic_output_keeps_previous_file_after_failure`, `test_quick_snapshot_is_published_with_manifest`, `tes… |
| `test_backup_zip_serialization.py` | The manual and automatic archive paths use the same WAL-safe serialization. |
| `test_bang_shell_mode.py` | Tests for `!<command>` shell mode in the interactive CLI. |
| `test_banner.py` | Tests for banner toolset name normalization and skin color usage. |
| `test_banner_distribution_label.py` | The banner names the desktop shell shape, not just "desktop-app". |
| `test_banner_release_channel.py` | Passive checks use the same release selection as explicit source updates. |
| `test_banner_skills.py` | Tests for banner get_available_skills() — disabled and platform filtering. |
| `test_banner_skills_width.py` | Tests for banner skills display — terminal-width-aware truncation. |
| `test_bare_custom_picker_row.py` | The bare ``model.provider: custom`` picker row must survive switching away. |
| `test_base_url_host_identity.py` | Regression tests: provider-identity checks must compare URL *hostnames*, not raw substrings. |
| `test_bedrock_mantle_key_env.py` | Bedrock API-key setup must produce a config that actually authenticates. |
| `test_bedrock_model_picker.py` | Tests for AWS Bedrock integration in the model picker and provider catalog. |
| `test_bedrock_region_scoped_picker.py` | Regression tests for #28156 — Bedrock picker must be region-scoped. |
| `test_billing_portal_url.py` | Portal-URL resolution for Phase 2b billing errors (nous_billing). |
| `test_billing_scope_stepup.py` | Tests for the Phase 2b billing:manage scope step-up (auth.py). |
| `test_boot_bootstrap.py` | Boot-time post-update bootstrap: identity, records, locks, single-flight. |
| `test_boot_convergence.py` | Real startup paths share one passive PM verdict, including fast dispatch. |
| `test_boot_preset_staleness.py` | Every staged model must launch with a policy decision, never stock fit. |
| `test_boot_wiring.py` | C26 wiring: the boot registry is reached by the real entry points, and the cadence has a production caller. |
| `test_borrowed_home_launch.py` | A launch under a data root that does not own the checkout leaves the checkout to its owner (#123238). |
| `test_bot_desktop_screen_status.py` | ``hermes computer-use screen status`` shows the lease the way every RPC surface does: the holder's viewer id is a capability (whoever presents it co-drives or releases the lease), so only its short hash leaves the gatew… |
| `test_bot_desktop_screen_stop.py` | The documented CLI stop --force is also recovery for a disconnected viewer's lease. |
| `test_bounded_probe_run.py` | ``bounded_probe_run`` — deadlock-safe capture for fail-open probes (#87134). |
| `test_bracketed_paste_timeout.py` | Tests for bracketed-paste timeout safety valve (#16263). |
| `test_branch_command.py` | Tests for the /branch (/fork) command — session branching. |
| `test_browse_schema_drift.py` | A store that lags SCHEMA_SQL must stay browsable (#140315). |
| `test_browser_connect_default_chromium.py` | Default-Chromium detection and profile-dir resolution (hermes_cli.browser_connect). |
| `test_browser_connect_dual_stack.py` | Dual-stack loopback discovery + port-squatter handling for /browser connect. |
| `test_browser_connect_media_permissions.py` | The chrome-debug Chromium profile and Hermes media-cache dirs are created owner-only. |
| `test_browser_connect_real_profile_snapshot_errors.py` | Real-profile snapshot while the browser runs, and the error when cookies can't be read. |
| `test_browser_credential.py` | The browser credential has one generation check and one rotation that ends every grant. |
| `test_browser_runtime.py` | Browser resolution uses installed PM facts and config without provisioning a browser. |
| `test_bundled_desktop_launch.py` | ``hermes desktop`` from inside a BUNDLED desktop payload. |
| `test_bundles.py` | Tests for hermes_cli/bundles.py — the `hermes bundles` CLI subcommand. |
| `test_busy_input_mode_command.py` | Tests for the /busy CLI command and busy-input-mode config handling. |
| `test_busy_policy_invariants.py` | Invariant tests for the declarative busy_policy on CommandDef. |
| `test_bytecode_sweep.py` | Tests for the launch-time stale-bytecode sweep (checkout fingerprint guard). |
| `test_cached_fetch_api_models.py` | Cache-contract tests for ``cached_fetch_api_models()``. |
| `test_canonical_custom_identity.py` | ``canonical_custom_identity`` must return the durable config-key identity. |
| `test_catalog_json.py` | The pulled catalog: packaged JSON is the offline truth, a GitHub fetch swaps entries in memory only, and min_engine gates day-0 models. |
| `test_catalog_variants.py` | Variant-selection contracts: fit the catalog's single Q4-class build to a machine and price it honestly. Pure decision-table tests over synthetic budgets. |
| `test_chat_c_fail_loudly.py` | Tests for `chat -c <title>` failing loudly (stderr) and `--create-if-missing`. |
| `test_chat_catalog_excludes_generation_models.py` | Chat catalogs must not offer generation models, and a direct switch must reject them. |
| `test_chat_q_exit_clear.py` | Regression tests for #53009: chat -q final response erased by exit-summary clear. |
| `test_chat_query_file.py` | --query-file: single-query text arrives verbatim, never shell-interpreted. |
| `test_chat_skills_flag.py` | Tests: `test_top_level_skills_flag_defaults_to_chat`, `test_continue_worktree_and_skills_flags_work_together` |
| `test_chat_turn_streaming_tts_arming.py` | Streaming-TTS arm gate regression (#84046): ``_chat_setup_turn_audio`` used to gate streaming TTS on a ``sounddevice`` import, which raises on macOS (PortAudio/CoreAudio init triggers a kTCCServiceMediaLibrary prompt) e… |
| `test_checkout_mutation_guards.py` | The test suite must never mutate the LIVE checkout or its venv. |
| `test_checkpoints_clear_legacy.py` | `hermes checkpoints clear-legacy` exit code must reflect whether the archives are gone. |
| `test_checkpoints_prune.py` | Tests for `hermes checkpoints prune`'s orphan confirmation flow. |
| `test_classic_browser_manage.py` | CLI-9: the classic CLI's /browser goes to the gateway (``browser.manage``), like Ink and Desktop. |
| `test_classic_cli_gateway_session.py` | The classic CLI's gateway session across /new and a gateway restart: the reasoning flag follows the session, and a turn lost in the restart is shown and discarded instead of blocking the next prompt. |
| `test_classic_cli_routing.py` | The classic CLI is main's HermesCLI again: `hermes` / `hermes chat` (interactive and -q) reach ``cli.main``; only stream-json and the safe-mode bypass keep the gateway transport client. |
| `test_claude_code_account_connection.py` | Accounts Connected must follow Claude Code token validity, not token presence. |
| `test_clear_stale_base_url.py` | Tests for _clear_stale_openai_base_url() cleanup after provider switch (#5161). |
| `test_cli_active_session_limit.py` | Tests: `test_cli_claim_active_session_respects_global_limit` |
| `test_cli_approval_ui.py` | Tests: `_FakeBuffer`, `_make_cli_stub`, `_make_background_cli_stub`, `TestCliApprovalUi`, `_make_real_paint_cli_stub`, `TestModalPaintNow` … |
| `test_cli_async_delegation_delivery.py` | Regression coverage for CLI async-delegation completion ownership. |
| `test_cli_background_busy_path.py` | Regression tests for classic-CLI mid-run /bg and /btw dispatch. |
| `test_cli_background_status_indicator.py` | Tests for the /bg indicator in the CLI status bar. |
| `test_cli_billing_i18n.py` | The billing/subscription CLI copy resolves through the i18n catalog at call time. |
| `test_cli_billing_keep_going_on_credits.py` | /topup "Keep going on credits" (window plans): the terminal flow for the account setting. |
| `test_cli_bracketed_paste_sanitizer.py` | Tests for defensive bracketed-paste wrapper stripping in the CLI. |
| `test_cli_browser_connect.py` | Tests for CLI browser CDP auto-launch helpers. |
| `test_cli_clarify_batch.py` | Batch (multi-question) clarify panel state machine — CLI side. |
| `test_cli_clarify_panel_height.py` | Batch clarify panel stays inside the viewport so choices remain selectable. |
| `test_cli_cmd_backspace.py` | Verify Cmd+Backspace / Cmd+ForwardDelete byte sequences from CSI-u terminals reach prompt_toolkit's readline kill bindings instead of leaking into the buffer as literal text. |
| `test_cli_command_messages.py` | User-facing message contracts for `hermes skills/plugins/mcp/cron/doctor` failure paths. |
| `test_cli_config_load_launch_cwd.py` | The local CLI runs in its launch directory even when started from a gateway agent's terminal. |
| `test_cli_config_vertex_label.py` | T6 (#134889): classic-CLI ``/config`` on a Vertex route names the credential honestly. |
| `test_cli_context_reference_passthrough.py` | The classic CLI leaves ``@`` references to the gateway, which expands them once against the session's cwd; a client-side pass first expanded them twice (PLG-4). |
| `test_cli_context_warning.py` | Tests for the low context length warning in the CLI banner. |
| `test_cli_copy_command.py` | Tests for CLI /copy command. |
| `test_cli_ctrl_c_draft_priority.py` | Ctrl+C / Ctrl+Q in the classic CLI: a typed draft wins over interrupting a running turn. |
| `test_cli_custom_provider_vision.py` | End-to-end CLI coverage for named custom-provider vision routing. |
| `test_cli_delegate_background_notice.py` | The CLI spells out auto-resume when a delegate_task goes to the background. |
| `test_cli_enter_burst.py` | Text + Enter arriving in ONE read (``tmux send-keys 'text' Enter``, a PTY write of ``text\r``) submits, while Enters inside an unbracketed multi-line paste stay newlines (#10994). |
| `test_cli_extension_hooks.py` | Tests for protected HermesCLI TUI extension hooks. |
| `test_cli_external_editor.py` | Tests for CLI external-editor support. |
| `test_cli_fallback_chain_hot_reload.py` | An open classic-CLI chat adopts a ``fallback_providers`` chain added after it started (#95066). |
| `test_cli_file_drop.py` | Tests for _detect_file_drop — file path detection that prevents dragged/pasted absolute paths from being mistaken for slash commands. |
| `test_cli_first_message.py` | A fresh install's first CLI message reaches the model exactly as typed. |
| `test_cli_first_run_setup.py` | First-run onboarding routing for a completely unconfigured install. |
| `test_cli_footer_split.py` | The classic CLI footer never paints prompt_toolkit's "Window too small..." placeholder. |
| `test_cli_force_redraw.py` | Tests for CLI redraw helpers used to recover from terminal buffer drift. |
| `test_cli_gateway_model_route.py` | The classic CLI's model choices reach the gateway session. |
| `test_cli_gateway_model_scope.py` | ``/model --once`` is one turn; a session ``/model`` is the session's route. |
| `test_cli_goal_interrupt.py` | Tests for CLI goal-continuation interrupt handling. |
| `test_cli_goal_kick_prompt.py` | `/goal <text>` kicks the loop with a short pointer when the user's last message already carries the goal. |
| `test_cli_goal_parked_resume.py` | A parked /goal resumes from the idle hook once its barrier lifts, without waiting for another turn. |
| `test_cli_image_command.py` | Tests: `_make_cli`, `_make_image`, `TestImageCommand`, `TestCollectQueryImages`, `TestImageBadgeFormatting` |
| `test_cli_import_without_patch_stdout.py` | ``cli`` must import even when ``prompt_toolkit.patch_stdout`` is missing (#96075). |
| `test_cli_info_i18n.py` | CLI info/help copy resolves through the i18n catalog: /help consumes ``CommandDef.describe()``, module-level label tables became call-time lookups, and error copy follows the active language. |
| `test_cli_init.py` | Tests for HermesCLI initialization -- catches configuration bugs that only manifest at runtime (not in mocked unit tests). |
| `test_cli_insights_command.py` | Tests: `existing_store`, `_InsightsEngineStub`, `_run_show_insights`, `test_cli_insights_accepts_positional_days`, `test_cli_insights_keeps_days_flag_and_source`, `test_insights_skips_open_when_store_missing` … |
| `test_cli_interrupt_ack_race.py` | Regression tests for the CLI interrupt-acknowledgement race. |
| `test_cli_interrupt_drain_regression.py` | Regression test for #20271: classic-CLI hangs when messages typed during an agent turn never leave ``_interrupt_queue``. |
| `test_cli_interrupt_subagent.py` | End-to-end test simulating CLI interrupt during subagent execution. |
| `test_cli_light_mode.py` | Tests for the light-mode terminal detection + color remap in cli.py. |
| `test_cli_loading_indicator.py` | Regression tests for loading feedback on slow slash commands. |
| `test_cli_lost_turn_notice.py` | The classic CLI's refusal behind a lost turn and its ``/discard`` reply say only what is true. |
| `test_cli_manual_compress.py` | Tests: `DummyAgent`, `test_manual_compress_does_not_pass_cached_system_prompt`, `test_manual_compress_flush_failure_discards_notification` |
| `test_cli_markdown_rendering.py` | Tests: `_render_to_text`, `test_final_assistant_content_uses_markdown_renderable`, `test_final_assistant_content_keeps_non_path_markdown_escapes`, `test_strip_mode_preserves_lists`, `test_strip_mode_preserves_blockquote… |
| `test_cli_mcp_config_watch.py` | Tests for automatic MCP reload when config.yaml mcp_servers section changes. |
| `test_cli_model_once.py` | Tests: `_FakeAgent`, `_StubCLI`, `test_cli_model_once_records_restore_and_does_not_persist`, `test_cli_restore_model_runtime_snapshot_restores_agent`, `test_cli_restore_model_runtime_prefers_primary_runtime` |
| `test_cli_model_switch_i18n.py` | The /model switch mixin's CLI copy resolves through the i18n catalog at call time. |
| `test_cli_modern_layout.py` | The glyph CLI layout (``display.cli_layout: modern``): scrollback rows never depend on the terminal width, and the status line renders under the composer instead of above it. |
| `test_cli_new_session.py` | Regression tests for CLI fresh-session commands. |
| `test_cli_output.py` | Tests: `_TTY`, `_NotTTY`, `test_line_input_supports_cursor_and_emacs_navigation`, `test_line_input_preserves_builtin_input_for_redirected_stdin`, `test_line_input_falls_back_to_input_on_any_prompt_toolkit_failure`, `tes… |
| `test_cli_partial_update_hint.py` | Chat startup must explain a mixed-version ImportError (#96900). |
| `test_cli_pet_pane.py` | The base-CLI petdex pane: reactive half-block sprite above the prompt. |
| `test_cli_prefix_matching.py` | Tests for slash command prefix matching in HermesCLI.process_command. |
| `test_cli_profile_toolsets.py` | A stale ``platform_toolsets.cli`` entry (a toolset whose plugin was uninstalled) must not refuse every `hermes chat` (#138670): the profile default is the gateway's to resolve, only a picked list rides session.create. T… |
| `test_cli_provider_resolution.py` | Tests: `_reset_modules`, `_restore_cli_and_tool_modules`, `_install_prompt_toolkit_stubs`, `_import_cli`, `test_provider_flag_uses_named_custom_default_model`, `test_explicit_model_wins_over_provider_default_model` … |
| `test_cli_queue_gateway_fifo.py` | The classic CLI's ``/queue`` goes into the gateway's durable FIFO (refs #134889, N5). |
| `test_cli_queue_paste.py` | Regression tests for collapsed paste references passed to /queue. |
| `test_cli_quiet_stdout_leak.py` | `hermes chat -Q` must not leak presentation output into stdout (#93220). |
| `test_cli_reload_skills.py` | Tests for the ``/reload-skills`` CLI slash command (``HermesCLI._reload_skills``). |
| `test_cli_resume_command.py` | Tests: `_make_cli`, `TestCliResumeCommand`, `TestCliResumeRestoresCwd`, `TestPendingResumeNumberedSelection`, `TestResumeFlushesBeforeEndSession`, `TestResumeOpensTheTargetOnTheGateway` |
| `test_cli_retire_agent.py` | The interactive CLI must release the old AIAgent's LLM clients when it drops the instance for a rebuild (/personality, /reasoning, /fast, model/route/credential change, MoA one-shot): on the codex_app_server route the a… |
| `test_cli_retry.py` | Regression tests for CLI /retry and carrier-aware rewind semantics. |
| `test_cli_save_config_value.py` | Tests for save_config_value() in cli.py — atomic write behavior. |
| `test_cli_secret_capture.py` | Tests: `_FakeBuffer`, `_FakeApp`, `_make_cli_stub`, `test_secret_capture_callback_can_be_completed_from_cli_state_machine`, `test_cancel_secret_capture_marks_setup_skipped`, `test_secret_capture_uses_masked_prompt_witho… |
| `test_cli_session_store_shared_registry.py` | The CLI's session store is the gateway's, never a state.db writer in the CLI process. |
| `test_cli_sessions_behind_newer_surfaces.py` | CLI session lookups must page by creating surface, not by a fixed local window. |
| `test_cli_shift_enter_newline.py` | Verify Shift+Enter byte sequences parse to the same key tuple Alt+Enter produces, so the existing Alt+Enter newline handler in `cli.py` fires for terminals that emit a distinct Shift+Enter under the Kitty keyboard proto… |
| `test_cli_shutdown_memory_messages.py` | Regression tests for #15165 (CLI sibling site) — CLI exit cleanup must forward the agent's conversation transcript to ``shutdown_memory_provider`` so memory providers' ``on_session_end`` hooks see the real messages. |
| `test_cli_skin_integration.py` | Tests: `_make_cli_stub`, `TestCliSkinPromptIntegration`, `TestCompactBannerSkinIntegration`, `TestAnsiRichTextHelper` |
| `test_cli_startup_maintenance_off_main_thread.py` | The CLI's startup housekeeping (curator pass, skill sync) must never hold the prompt. |
| `test_cli_startup_model_cost_guard.py` | Tests: `_NonInteractiveStdin`, `_chat_args`, `main_mod`, `fake_cli`, `codex_config`, `_set_startup_config` … |
| `test_cli_startup_trim.py` | Startup/exit work that belongs to the gateway never runs in the classic CLI's process. |
| `test_cli_status_bar.py` | Tests: `_make_cli`, `_attach_agent`, `TestCLIStatusBar`, `TestCLIUsageNoAgentAccountLimits`, `TestStatusBarWidthSource`, `TestIdleSinceLastTurn` … |
| `test_cli_status_bar_goal.py` | Status-bar goal segment (⊙ goal N/M) — active-goal-only rendering. |
| `test_cli_status_canonical_session_id.py` | T16 (#134889): classic-CLI ``/status`` names a gateway session by its canonical ``local-…`` id. |
| `test_cli_status_command.py` | Tests for CLI /status command behavior. |
| `test_cli_steer_busy_path.py` | Regression tests for classic-CLI mid-run /steer dispatch. |
| `test_cli_terminal_response_sanitizer.py` | Tests for defensive terminal control-response stripping in the CLI. |
| `test_cli_terminal_shortcuts.py` | Regression tests for terminal navigation/focus escape sequences. |
| `test_cli_tools_command.py` | Tests for /tools slash command handler in the interactive CLI. |
| `test_cli_tui_i18n_lazy_labels.py` | TUI approval labels and modal hints are catalog lookups at render time, not import-time text. |
| `test_cli_user_message_preview.py` | Tests: `_make_cli`, `TestSubmittedUserMessagePreview` |
| `test_cli_yolo_resume_persistence.py` | Regression tests: YOLO mode persists across ``hermes --resume``. |
| `test_cli_yolo_toggle.py` | Regression tests for the CLI ``/yolo`` in-chat toggle. |
| `test_clipboard_text_write.py` | Tests for native clipboard text write (hermes_cli/clipboard.py). |
| `test_cmd_uninstall.py` | The real uninstall parser must select the data path, never code removal. |
| `test_cmd_update.py` | Git trampoline recovery; branch updates use the real target-identity suite. |
| `test_cmd_update_docker.py` | Tests for ``hermes update`` / ``--check`` inside the Docker container. |
| `test_coalesce_session_args.py` | Tests for _coalesce_session_name_args — multi-word session name merging. |
| `test_code_skew.py` | Tests for gateway code-skew detection (stale-checkout guard). |
| `test_codex_cli_model_picker.py` | Regression tests for the /model picker's credential-discovery paths. |
| `test_codex_credential_host_binding.py` | A Codex credential is only ever sent to the host it belongs to (#121486). |
| `test_codex_device_login_ssl_hint.py` | Codex device-login transport errors keep the underlying SSL detail and add a hint (#106384). |
| `test_codex_device_login_transient_retry.py` | Codex device-login survives transient transport blips. |
| `test_codex_models.py` | Tests: `_codex_jwt`, `_pro_slugs`, `test_codex_catalog_never_offers_chatgpt_rejected_pro_slugs`, `test_picker_synthesizes_900k_variants_for_verified_slugs`, `test_picker_never_synthesizes_900k_for_pro_or_unknown_slugs`,… |
| `test_codex_relogin_copy_names_profile.py` | Codex credential-failure copy sends the user to THIS profile's own sign-in. |
| `test_codex_runtime_plugin_migration.py` | Tests for the codex MCP plugin migration helper. |
| `test_codex_runtime_switch.py` | Tests for the /codex-runtime slash-command shared logic. |
| `test_codex_token_writethrough.py` | Codex OAuth refresh writes back to the store the grant was resolved FROM (#87503). |
| `test_command_palette.py` | Tests for /help declutter + Ctrl+P command palette (C-04 / C-05). |
| `test_commands.py` | Tests for the central command registry and autocomplete. |
| `test_commands_execute.py` | Invariant for registry-owned slash execution (CommandDef.execute). |
| `test_commit_build_cli.py` | Exercise the installed CLI with a sealed code copy and its build stamp. |
| `test_commit_build_updates.py` | A one-commit artifact cannot enter any self-update path. |
| `test_completer_config_reads.py` | The /personality completer memoises the parsed config per keystroke, but a config edit on disk must show up in the next completion (never a stale list). |
| `test_completion.py` | Tests for hermes_cli/completion.py — shell completion script generation. |
| `test_completion_backlog.py` | Completion backlogs preserve results without multiplying autonomous turns. |
| `test_compress_flags.py` | Tests for /compress --preview/--dry-run/--aggressive flags and the /compact alias (PR #3243 salvage). |
| `test_compress_here.py` | Tests for /compress here [N] — boundary-aware partial compression. |
| `test_computer_use_cli.py` | CLI coverage for the public Computer Use command surface. |
| `test_computer_use_screen_install.py` | `hermes computer-use screen install` shares the Desktop pane's installer (one lock, list-form spawn). |
| `test_config.py` | Tests for hermes_cli configuration management. |
| `test_config_backend.py` | The ConfigBackend seam (config-config design §4.1, D10) and its reader gate. |
| `test_config_backend_kinds.py` | ``HERMES_CONFIG_BACKEND=<kind>`` resolves to the package ``plugins/config_backends/<kind>/`` through one entry point (``get_backend()``), and everything core needs from a backend is a protocol method (teknium1 P2-1 on #… |
| `test_config_backups.py` | config.yaml backups: one dir, deduped, bounded — never a pile of siblings in HERMES_HOME. |
| `test_config_browser_env_first_stamp.py` | AGENT_BROWSER_* settings survive homes that never run the versioned v52 step. |
| `test_config_cache_signature.py` | #111105: a config.yaml replacement that keeps mtime and size (``cp -p``, ``rsync -t``, a timestamp-pinning writer) must still invalidate the load_config() cache, while an unchanged file keeps serving the cached object. |
| `test_config_check_diagnostics.py` | Config check reports stale saved capabilities without changing profile state. |
| `test_config_client_env_passthrough.py` | ``terminal.client_env_passthrough`` (a shell client's extra toolchain names) is a registered key. |
| `test_config_display_language.py` | ``hermes config set display.language`` accepts every ``supported_languages()`` id — bundled, alias, and a plugin language pack found through real discovery — and refuses unknown ids naming the options. |
| `test_config_dotted_key_names.py` | Regression tests for dotted config key names (#84064 bug class). |
| `test_config_edit_seed.py` | Every writer that seeds or first-configures config.yaml must leave each messaging platform's display defaults alone (#121230). The gateway loader merges no DEFAULT_CONFIG, so any written global ``display.<key>`` beats e… |
| `test_config_effective.py` | Invariants for ``hermes_cli.config_effective.load_user_config_effective`` — the one loader every defaults-free config reader (gateway runtime, TUI gateway, cron, ``hermes send`` bridge, doctor, bootstrap modules) goes t… |
| `test_config_env_expansion.py` | Tests for ${ENV_VAR} substitution in config.yaml values. |
| `test_config_env_ref_parity.py` | Config `${env:VAR}` SecretRef parity (salvaged from PR #59516). |
| `test_config_env_refs.py` | Tests: `_write_config`, `_read_config`, `test_save_config_preserves_unresolved_env_refs`, `test_save_config_allows_intentional_secret_value_change` |
| `test_config_guard_surfaces.py` | Fail-closed corrupt-config guards on gateway, serve, and cron surfaces. |
| `test_config_lkg_backup.py` | A fresh process recovers the last successfully parsed config.yaml when the file is broken. |
| `test_config_loader_e2e.py` | E2E for the canonical-loader migration (managed-scope/env-expansion drift fix). |
| `test_config_lock_free_cache_hit.py` | A cached config read must not block behind a config WRITER. |
| `test_config_migration_45_connections.py` | Migration 44→45: saved ``platform_toolsets`` lists gain the ``connections`` toolset. |
| `test_config_migration_48_sandbox_image.py` | Migration 47→48: the container sandbox default becomes nousresearch/hermes-sandbox:desktop. |
| `test_config_migration_49_vercel_image.py` | Migration 48→49: Vercel Sandbox moves from the deprecated `node24` runtime to a managed image. |
| `test_config_migration_50_tirith.py` | Config v50: the bundled tirith scanner left Hermes. |
| `test_config_migration_52_browser.py` | Config v52: agent-browser and the built-in browser tools left Hermes. |
| `test_config_migration_nested_guards.py` | Config migrations survive malformed nested values (#116593). |
| `test_config_platform_env_routing.py` | ``hermes config set/get/unset`` route every name Hermes registers as an environment variable to ``.env`` — the file the platform setup flows and ``/sethome`` already write (#111848). |
| `test_config_provider_id_string.py` | Regression for #117345: ``model.provider`` must survive config load as a string. |
| `test_config_read_guard.py` | Lint guard: no new raw yaml.safe_load(config.yaml) reads outside owner modules. |
| `test_config_retired_key_migrations.py` | Config migrations that retire or rewrite obsolete keys (v43 / v44 / v51, stamp-independent steps). |
| `test_config_rmw_lock.py` | Concurrent dashboard config writers must not drop each other's mutations. |
| `test_config_runtime_keys.py` | `hermes config get/set` must recognize keys the runtime reads but DEFAULT_CONFIG leaves unseeded: core provider selections (``browser.cloud_provider``, ``<category>.use_gateway``), core-owned keys with a known reader (`… |
| `test_config_same_tick_rewrite.py` | Config caches see a same-size in-place rewrite made in the timestamp tick of the cached read. |
| `test_config_save_integrity.py` | config.yaml write integrity: a failed read never reaches disk, and a save keeps what the user wrote. |
| `test_config_set_coercion.py` | Regression tests for `config set` value coercion + key validation (round-3 CFG). |
| `test_config_set_list_values.py` | ``hermes config set`` must parse list/mapping literals, not store them as strings. |
| `test_config_set_platforms_redirect.py` | Regression tests for #71047 (Problem A): per-platform display settings. |
| `test_config_unversioned_migration.py` | A config.yaml without ``_config_version`` is current-schema content that was never stamped: the installers seed it from cli-config.yaml.example and targeted writers (``hermes config set``, /personality) never stamp. The… |
| `test_config_validation.py` | Tests for config.yaml structure validation (validate_config_structure). |
| `test_config_worker_save_deletion.py` | A frozen managed worker's config write-back never resurrects a branch the operator deleted. |
| `test_config_yaml_comment_preservation.py` | Regression guard for #92554: every config.yaml writer preserves user comments and key order. |
| `test_configured_builtin_models.py` | Configured models extend built-in picker rows. |
| `test_connectors_cmd.py` | Behaviour contracts for ``hermes connectors``. |
| `test_console_engine.py` | Tests: `test_sessions_optimize_accepts_the_force_override_it_advertises`, `test_sessions_list_and_stats_use_isolated_session_store`, `test_sessions_export_rejects_oversized_single_before_touching_output`, `test_sessions… |
| `test_container_aware_cli.py` | Tests for container-aware CLI routing (NixOS container mode). |
| `test_container_boot.py` | Tests for hermes_cli.container_boot — the cont-init.d-time reconciliation that recreates per-profile gateway s6 service slots from the persistent profiles directory. |
| `test_context_cache_switch_guard.py` | Context-cache model-switch guard. |
| `test_context_policy.py` | Context-policy decision-table tests (Rollout 3). |
| `test_context_switch_guard.py` | Tests for hermes_cli.context_switch_guard. |
| `test_corelane_frozen_worker_skill_env.py` | A frozen-policy worker never opens the profile's ``.env`` -- including the skill readiness probe. |
| `test_cpr_local_leak.py` | Classic-CLI prompt_toolkit output selection: native Windows keeps prompt_toolkit's default output unless PROMPT_TOOLKIT_NO_CPR opts in to the CPR-disabled output. |
| `test_cprint_bg_thread.py` | Tests for cli._cprint's bg-thread cooperation with prompt_toolkit. |
| `test_credential_lifecycle.py` | E2E tests for the unified provider-credential lifecycle (#51071 #59761 #62269). |
| `test_credential_pool_off_loop.py` | Regression tests for the #91912 salvage — credential-pool handlers off-loop. |
| `test_cron.py` | Tests for hermes_cli.cron command handling. |
| `test_cron_dashboard_off_loop.py` | Regression tests: cron dashboard handlers must not run profile I/O on the event loop. |
| `test_cron_delivery_targets_scope.py` | Regression: the delivery-targets route read a profile secret unscoped. |
| `test_cron_dispatch_visibility.py` | CLI rendering of missed-run dispatch visibility (#99879). |
| `test_cron_fire_dashboard.py` | Tests for the Chronos cron-fire webhook ON THE DASHBOARD APP (web_server). |
| `test_cron_parser_builder.py` | Unit tests for the extracted ``hermes cron`` parser builder. |
| `test_cron_run_history_sessions.py` | Dashboard/Desktop run history for agent cron runs the unified gateway runtime creates (#138812). |
| `test_cron_run_scheduler_ownership.py` | A never-closed cron run is live while the scheduler OWNS it, not while it ticked recently (#88443). |
| `test_cron_satellite_diagnostics.py` | Tests: `served_root`, `test_status_preserves_profile_health_contract`, `test_host_record_rung_names_the_roster_and_a_runnable_restart`, `test_satellite_list_and_create_require_own_heartbeat`, `test_standalone_guidance_m… |
| `test_cron_status_next_run.py` | Cron status orders persisted next runs by instant, including a DST fold. |
| `test_cron_status_profile_isolation.py` | Regression guard for #98790 — profile isolation in cron status. |
| `test_cross_profile_kill_refusal.py` | Cross-profile kill refusal regression tests (#89315). |
| `test_ctrl_enter_newline.py` | Regression tests for issue #22379 — Ctrl+Enter newline over SSH/WSL. |
| `test_ctrlg_editor_submit.py` | Tests for Ctrl+G external-editor submit in the classic CLI. |
| `test_curator_archive_prune.py` | `hermes curator archive` refuses pinned skills (with an `unpin` hint) and never archives them. |
| `test_curator_pin_unmanaged.py` | Pin/unpin messaging on unmanaged skills (#92993). |
| `test_curator_pin_visibility.py` | Regression tests for issue #92993 — `curator pin` false success + invisible pin. |
| `test_curator_recent_run_notice.py` | Tests for `_print_curator_recent_run_notice`. |
| `test_curator_run.py` | Tests for `hermes curator run` CLI behavior. |
| `test_curator_status.py` | Tests for `hermes curator status` output. |
| `test_curator_usage.py` | Tests for `hermes curator usage` — the all-skills usage view. |
| `test_curses_arrow_keys.py` | Regression tests for arrow-key decoding in the curses menus. |
| `test_curses_gauge_bars.py` | Gauge colouring in curses/ANSI descriptions only touches real ``render_bar`` gauges. |
| `test_curses_radiolist_viewport.py` | Exercise radiolist rendering and navigation with a bounded terminal surface. |
| `test_curses_ui_fuzzy_rank.py` | Tests for the ranked fuzzy scorer used by the searchable curses pickers. |
| `test_curses_ui_search.py` | Tests: `_FakeCurses`, `test_reconcile_cursor_moves_to_first_visible_match`, `test_active_search_consumes_query_editing_and_confirm_keys` |
| `test_custom_entry_shadow_key_env.py` | A ``providers:`` entry keyed like a built-in sends its own ``key_env``, never the built-in's key. |
| `test_custom_opencode_family_runtime.py` | Custom OpenCode-family provider runtime resolution (#85589). |
| `test_custom_provider_context_feedback.py` | #2513: a blank context-length prompt in the custom-endpoint wizard tells the user whether the runtime resolver detected a value or will run on the silent default. |
| `test_custom_provider_context_length.py` | Regression tests for custom_providers per-model context_length resolution. |
| `test_custom_provider_extra_headers.py` | Tests for per-provider ``extra_headers`` in providers / custom_providers config. |
| `test_custom_provider_identity.py` | Unit tests for find_custom_provider_identity (base_url → custom:<name>). |
| `test_custom_provider_key_env_scope.py` | Custom-provider ``key_env`` reads in the CLI picker/catalog helpers go through the profile secret scope (#67935): a key that lives only in the profile's ``.env`` must be found, and another profile's process-env value mu… |
| `test_custom_provider_model_switch.py` | Tests that `hermes model` always shows the model selection menu for custom providers, even when a model is already saved. |
| `test_custom_provider_normalize_no_mutate.py` | Regression: _normalize_custom_provider_entry must never mutate its input. |
| `test_custom_provider_tls.py` | Tests for per-provider TLS settings in custom_providers config. |
| `test_daemon_env_profile_donation.py` | A named-profile client that auto-starts the host daemon never donates its own dotenv to it (N43). |
| `test_daemon_launch_env_strip.py` | One launch's hook consent and Kanban/terminal pins never reach the auto-started shared daemon. |
| `test_dashboard_admin_endpoints.py` | Tests for the dashboard admin API endpoints (MCP, pairing, webhooks, credential pool, memory, gateway lifecycle, ops, skills hub). |
| `test_dashboard_auth_401_reauth.py` | Phase 6 — 401 re-auth + ``next=`` propagation tests. |
| `test_dashboard_auth_audit.py` | Audit log for dashboard-auth events. |
| `test_dashboard_auth_body_limit.py` | Body budgets apply before parsing public auth requests, not to uploads. |
| `test_dashboard_auth_cookies.py` | Tests for the dashboard-auth cookie helpers. |
| `test_dashboard_auth_gate.py` | Regression harness for the dashboard auth gate. |
| `test_dashboard_auth_middleware.py` | End-to-end behavioural tests for the dashboard auth gate. |
| `test_dashboard_auth_native_cookie_writes.py` | Native Desktop's cookie-session writes through the real dashboard auth gate. |
| `test_dashboard_auth_native_flow.py` | E2E + unit tests for the RFC 8252 native-app (system-browser + loopback + PKCE) dashboard-auth flow. |
| `test_dashboard_auth_page_icons.py` | Page icons answer without a session, like ``/favicon.ico``; other public files stay gated. |
| `test_dashboard_auth_password_login.py` | Tests for the password (non-redirect) dashboard-auth login flow. |
| `test_dashboard_auth_plugin_hook.py` | The plugin context exposes register_dashboard_auth_provider. |
| `test_dashboard_auth_prefix.py` | Path-prefix (X-Forwarded-Prefix) awareness for the dashboard-auth gate. |
| `test_dashboard_auth_session_token_gate.py` | End-to-end gate tests for the session-token auth provider. |
| `test_dashboard_auth_status_endpoint.py` | Phase 7 — /api/status exposes auth-gate state + AuthWidget integration. |
| `test_dashboard_auth_ws_auth.py` | Tests for the WS-upgrade auth helper (Phase 5 task 5.2). |
| `test_dashboard_auth_ws_tickets.py` | Tests for the WS-upgrade ticket store (Phase 5 task 5.1). |
| `test_dashboard_basic_auth_plugin_enable.py` | Regression tests for dashboard basic-auth plugin enablement (#54489). |
| `test_dashboard_initial_profile_bootstrap.py` | Tests: `test_spa_bootstrap_includes_dashboard_initial_profile`, `test_spa_bootstrap_escapes_initial_profile_for_script_context` |
| `test_dashboard_lifecycle_flags.py` | Tests for ``hermes dashboard --stop`` / ``--status`` flags. |
| `test_dashboard_oauth_endpoints_server_gate.py` | Regression guard for PR #61281 (mobile/hosted dashboard OAuth). |
| `test_dashboard_param_clamps.py` | Dashboard query-param clamps (#39200 + #74778 salvage). |
| `test_dashboard_plugin_routes_secret_scope.py` | Dashboard agent-plugin mutations run in the request's profile scope, off the event loop. |
| `test_dashboard_procs_kill_grace.py` | The dashboard SIGTERM→SIGKILL grace must outlast the lifespan teardown (#111912), and a descendant that outlives it must not survive the stop (#112631). |
| `test_dashboard_register.py` | Tests for ``hermes dashboard register``. |
| `test_dashboard_session_token_file.py` | The dashboard session token resolves from the environment, or a file it names. |
| `test_dashboard_stop_spare_caller.py` | Root selection for ``dashboard --stop`` / update cleanup must spare the caller. |
| `test_dashboard_system_gateway_elevation.py` | Dashboard gateway lifecycle actions must elevate on a system-scope install. |
| `test_dashboard_token_auth.py` | Contract tests for the generic non-interactive (bearer-token) auth seam. |
| `test_dashboard_tui_backcompat.py` | Regression test: `hermes dashboard --tui` must not hard-crash. |
| `test_dashboard_unified_launch.py` | Tests for the unified profile→machine dashboard launch routing. |
| `test_dashboard_web_dist_validation.py` | Regression tests: `hermes dashboard` validates HERMES_WEB_DIST before serving. |
| `test_data_dir_suffix.py` | Default-root isolation through the real Python resolution chain. |
| `test_data_uninstall.py` | Data deletion respects declared runtime ownership, confirmation and scope. |
| `test_data_uninstall_holders.py` | Data deletion must establish quiescence, never infer it from a signal count. |
| `test_debug.py` | Tests for ``hermes debug`` CLI command and debug utilities. |
| `test_debug_share_update_logs.py` | Regression tests: debug share captures update.log + desktop-update-handoff.log. |
| `test_default_interface_resolution.py` | Tests for the configurable default interface (cli vs tui). |
| `test_deferred_platform_client_tools.py` | Deferred platform plugins must still register their *client* tools. |
| `test_deleted_profile_tombstone.py` | Deleted named profiles must stay gone until explicitly recreated. |
| `test_deprecated_cwd_warning.py` | Tests for warn_deprecated_cwd_env_vars() migration warning. |
| `test_desktop_apparmor_install_non_linux.py` | ``hermes desktop --install-apparmor-profile`` outside Linux (#130177 review). |
| `test_desktop_apparmor_sandbox.py` | The Linux launcher asks the Hermes binary itself whether Chromium's sandbox starts (#130177). |
| `test_desktop_build_git_windows.py` | The installer stage and later desktop product build are separate processes. |
| `test_desktop_build_lock.py` | Behavior tests for the Desktop build's cross-process lock. |
| `test_desktop_build_reuse.py` | ``hermes update`` reuses the packaged desktop app across commits that changed no desktop input. |
| `test_desktop_console.py` | Real child output must drain even when no interactive console is consuming it. |
| `test_desktop_cron_ticker_gateway_standdown.py` | Desktop cron ticker yields to a live gateway that owns cron on the same HERMES_HOME (#52202). |
| `test_desktop_cron_ticker_profiles.py` | Desktop cron ticker: every local profile's store must be ticked. |
| `test_desktop_esbuild_ignore_scripts.py` | Regression tests for the esbuild / ignore-scripts build-failure diagnosis (#53082). |
| `test_desktop_exe_integrity.py` | Behavior tests for the Windows desktop-exe integrity gate (#69179). |
| `test_desktop_install_after_update.py` | ``hermes update`` refreshes the installed macOS ``Hermes.app`` from the rebuilt bundle (#52339). |
| `test_desktop_lifecycle_windows_live.py` | LIVE Windows E2E for the Desktop-lifecycle cold-start skip (#76129/#76745). |
| `test_desktop_local_flag.py` | The desktop subcommand's --local launch flag. |
| `test_desktop_native_deps_stale.py` | A matching source stamp must not hide a packaged app whose node-pty has no native binary. |
| `test_desktop_plugin_halves_linked.py` | A dev checkout linked into ``plugins/`` with its ``plugin.js`` at the root publishes a real copy. |
| `test_desktop_plugin_install.py` | ``hermes_cli.desktop_plugin_install``: cloning a desktop plugin onto the host that serves the Webapp. |
| `test_desktop_profile_launch.py` | hermes desktop forwards an explicit profile into the packaged Electron launch. |
| `test_desktop_release_holder_windows_live.py` | A program outside Hermes whose working folder is inside release/ blocks the Desktop swap (#101789). |
| `test_desktop_release_holders.py` | Release-folder holders are named, and closed only with consent (#101789). |
| `test_desktop_repo_discovery_config.py` | Tests: `test_desktop_repo_discovery_defaults_are_opt_in_by_root`, `test_desktop_repo_discovery_keys_are_in_generated_schema` |
| `test_desktop_signin_long_poll.py` | The desktop's sign-in and handoff reads are long-polls. |
| `test_desktop_slash_registry.py` | The desktop's offline slash block-list is a dump of COMMAND_REGISTRY, never hand-authored. |
| `test_desktop_socket_tmpdir.py` | The Electron child needs a socket-safe temp root, not a long CLI scratch path (#124688). |
| `test_desktop_source_build.py` | Desktop launch prepares once, then stages and publishes the local pack. |
| `test_desktop_startup_cost.py` | Startup regressions exercised against real source trees on the current host. |
| `test_desktop_swap_crash_recovery.py` | A desktop app swap that died between its two renames is finished on the next swap, never erased: the previous app must survive a crash at the commit point and a failing retry. |
| `test_desktop_swap_file_lock_retry.py` | Desktop stage-and-swap promotion rides out a transient Windows file lock (#112544). |
| `test_desktop_update_verify.py` | Receipt validation uses packaged output, not just a source stamp. |
| `test_desktop_wsl_gpu.py` | ``hermes gui`` under WSLg selects the installed Mesa D3D12 driver before Electron spawns its GPU process (#106117) — and never overrides an explicit Mesa choice or fires off-WSL. |
| `test_destructive_slash_confirm.py` | Tests for cli.HermesCLI._confirm_destructive_slash. |
| `test_destructive_slash_confirm_gate.py` | Tests for the approvals.destructive_slash_confirm config gate. |
| `test_destructive_slash_inline_skip_e2e.py` | End-to-end integration test for the destructive-slash inline-skip path. |
| `test_detect_api_mode_for_url.py` | Tests for hermes_cli.runtime_provider._detect_api_mode_for_url. |
| `test_determine_api_mode_hostname.py` | Regression tests for ``determine_api_mode`` hostname handling. |
| `test_device_poll_waf_backoff.py` | Regression tests: edge/WAF non-JSON error responses must not abort an in-flight device-code login. |
| `test_diagnostics_upload.py` | Tests for ``hermes_cli.diagnostics_upload`` — the Nous-S3 upload client. |
| `test_diff_command.py` | Tests for the CLI ``/diff`` command handler. |
| `test_dingtalk_auth.py` | Unit tests for hermes_cli/dingtalk_auth.py (QR device-flow registration). |
| `test_disabled_toolsets_subset_cleanup.py` | #134593: Blank Slate wrote the subset toolset `search` (only web_search) into agent.disabled_toolsets; enabling `web` via `hermes tools` left it there, silently stripping web_search. |
| `test_discard_lockfile_churn.py` | `hermes update` lockfile-churn cleanup must respect npm workspace ownership (#112378). |
| `test_discord_skill_clamp_warning.py` | Tests for Discord /skill 32-char clamp collision warnings. |
| `test_display_ws_drop_keeps_lease.py` | A dropped viewer link (1006: lid closed, Wi-Fi) must NOT hand the screen back to the agent — the human may be mid-login on it. Only a clean close (1000/1001) releases. |
| `test_display_ws_ticket.py` | The display bridge admits only a display ticket minted for THIS profile's socket: a gateway ticket, an expired ticket, or one for another provider is refused before any socket is dialled. |
| `test_doctor.py` | Tests for hermes_cli.doctor. |
| `test_doctor_audit_remedy.py` | Doctor npm-audit remedy guidance — the fix must persist across `hermes update`. |
| `test_doctor_azure_foundry_probe.py` | ``hermes doctor`` connectivity probe for Azure Foundry Anthropic-style endpoints (#66756). |
| `test_doctor_cache_hogs.py` | ``hermes doctor`` names cache-root dirs that no pruner covers once they are big enough. |
| `test_doctor_channel_hygiene.py` | Doctor's channel-record hygiene check (_check_channel_record_hygiene). |
| `test_doctor_command_install.py` | Command diagnostics use the same selection and launch contract as setup. |
| `test_doctor_dedicated_provider_skip.py` | Regression: hermes doctor must not run a generic Bearer-auth health check for providers that already have a dedicated check (Anthropic, OpenRouter, Bedrock). |
| `test_doctor_exit_status.py` | Regression for #117276: ``hermes doctor``'s exit status must agree with its unresolved findings. |
| `test_doctor_github_token_probe.py` | ``hermes doctor`` validates a configured GITHUB_TOKEN/GH_TOKEN against api.github.com (#115257). |
| `test_doctor_ipv6_probe.py` | ``hermes doctor`` dead-IPv6 probe (#114265 secondary finding 1). |
| `test_doctor_journal_modes.py` | Tests for doctor's per-database journal-mode report. |
| `test_doctor_legacy_checkout.py` | Tests for the legacy-desktop-checkout report in hermes doctor. |
| `test_doctor_live.py` | Tests for ``hermes doctor --live`` — opt-in bounded real-call tool-backend probes. |
| `test_doctor_no_proxy_ipv6.py` | ``hermes doctor`` probes survive a bracketed-IPv6 NO_PROXY environment (#118159). |
| `test_doctor_plugins_in_both_lists.py` | `hermes doctor` reports a plugin listed in both plugins.enabled and plugins.disabled. |
| `test_doctor_pm_store_probe.py` | Doctor and launched commands share PM's read-only installed selection. |
| `test_doctor_relay_plugins.py` | ``hermes doctor`` names the Relay plugin files the runtime actually loads. |
| `test_doctor_structural_corruption.py` | #88587 — doctor must name STRUCTURAL state.db corruption honestly. |
| `test_doctor_terminal_backends.py` | Invariants for the terminal-backend doctor lines (tools-runtime-30): each failure names the backend in plain words and points at `hermes setup terminal`, never at raw TERMINAL_* env vars. |
| `test_doctor_update_provenance.py` | Doctor's plugin update-provenance check (SPEC-05 warning surface). |
| `test_doctor_wal_checkpoint_guard.py` | #103339 item 2: ``hermes doctor --fix`` never checkpoints state.db through a bare writable ``sqlite3.connect`` — the checkpoint runs on the exclusive repair guard, so an opener arriving after the holder scan is refused. |
| `test_doctor_wal_holder_guard.py` | Regression: ``hermes doctor --fix`` must not checkpoint the live WAL under a running gateway. |
| `test_doctor_web_dashboard_import.py` | ``hermes doctor`` reports a dashboard web surface that dies at import (#124214). |
| `test_doctor_workspace_audit.py` | Workspace audit warnings must reflect their runtime and build dependency scope. |
| `test_dump_env_visibility.py` | `hermes debug` must not report a shell-only API key as plainly "set". |
| `test_dump_gateway_status.py` | ``hermes dump`` gateway line for a supervised gateway with no scannable PID (#125390). |
| `test_dump_git_commit.py` | Tests for hermes_cli.dump._get_git_commit — git SHA resolution for ``hermes dump``. |
| `test_dump_terminal_backend.py` | `hermes debug` must report the EFFECTIVE terminal backend. |
| `test_early_recovery.py` | Startup triggers PM recovery without importing the damaged dependencies. |
| `test_empty_session_hygiene.py` | Tests for empty-session hygiene — gemini-cli#27770 port. |
| `test_enable_no_capabilities.py` | Enable asks for declared privileges, not an unsolicited override grant. |
| `test_ensure_acp_launcher.py` | `hermes update` must self-heal the ``hermes-acp`` launcher. |
| `test_ensure_gateway_service.py` | Service setup failure reporting; consent integration lives in test_gateway_service_choice. |
| `test_ensure_hermes_home_memo.py` | ensure_hermes_home is memoized per home path (perf: it runs on every load_config), but a deleted home must still be recreated on the next call. |
| `test_ensure_hermes_home_uid.py` | Regression tests for #34107 — Docker UID/GID handling in ensure_hermes_home. |
| `test_ensure_utf8_locale.py` | Regression tests for hermes_cli._ensure_utf8(). |
| `test_ensure_windows_bin_launchers.py` | ``hermes`` must survive git operations on the checkout (launcher layout). |
| `test_env_custom_keys.py` | GET /api/env surfaces arbitrary/custom .env keys (not just catalogued ones). |
| `test_env_deprecation_truthtable.py` | Truth-table regression test for the 'Deprecated .env settings' warning. |
| `test_env_export_line_lifecycle.py` | Regression tests for the Tools & Keys GitHub PAT save/remove path (#40041). |
| `test_env_export_prefix.py` | Tests for ``export `` prefix handling in the hand-rolled .env parsers. |
| `test_env_load_cache.py` | Tests for the load_env() process-level cache. |
| `test_env_loader.py` | Tests: `test_recovered_update_retry_skips_external_secret_sources`, `test_utf8_bom_does_not_mangle_first_key`, `test_bom_first_key_is_seen_by_installer_and_scrub_alike`, `test_utf8_bom_plus_invalid_utf8_preserves_first_… |
| `test_env_loader_op_bootstrap.py` | Tests for the 1Password bootstrap-token reliability patches. |
| `test_env_loader_self_reference.py` | Self-referential .env lines (``PATH=/x:${PATH}``) must resolve once per process, not grow on every reload (#109902: gateway per-turn and cron per-fire reloads grew PATH until child spawns died with E2BIG). |
| `test_env_sanitize_on_load.py` | Tests for .env sanitization during load to prevent token duplication (#8908). |
| `test_env_write_race.py` | Concurrent ``.env`` writers must not clobber each other (#77187). |
| `test_exit_delete_session.py` | Tests for `/exit --delete` and `/quit --delete` session deletion. |
| `test_exit_summary_resume_hint.py` | Tests for the CLI exit summary's resume hint, including profile-flag support. |
| `test_exit_watchdog_signal_arm.py` | Exit watchdog: arm on shutdown *intent* (signal), never at chat startup. |
| `test_external_process_auth_status.py` | Tests for external-process provider auth status and Accounts-tab wiring. |
| `test_external_process_cli_prefixes.py` | A Claude Code CLI outside PATH is found by every core check, not only by the Anthropic adapter. |
| `test_external_process_launch_env.py` | Launch-env policy for external-process (ACP) providers comes from their profiles' ``process_*`` fields. |
| `test_external_process_provider_seam.py` | An external-process (ACP) provider can ship from outside this tree. |
| `test_fallback_chain_alias_dedup.py` | Test that fallback-chain identity dedup normalizes provider aliases. |
| `test_fallback_cmd.py` | Tests for `hermes fallback` — chain reading, add/remove/clear, legacy migration. |
| `test_fallback_config.py` | Tests for hermes_cli/fallback_config.py — fallback entry API-key resolution. |
| `test_fast_command.py` | Tests for the /fast CLI command and service-tier config handling. |
| `test_fast_serve_launch.py` | Tests: `_capture`, `test_lean_serve_parser_matches_full_subcommand_parser`, `test_fast_serve_launch_dispatches_only_unambiguous_serve` |
| `test_file_cache_same_tick_rewrite.py` | Credential and allowlist file caches see a same-size in-place rewrite made in the tick of the cached read. |
| `test_finite_chat_delegation.py` | Finite chat must consume parallel delegated results before the CLI exits. |
| `test_fireworks_provider.py` | Focused tests for Fireworks AI first-class provider wiring. |
| `test_fleet_config_migration_windows_live.py` | LIVE Windows E2E for the fleet-wide config migration (wine2e lane). |
| `test_fleet_matrix_down_state.py` | Fleet matrix DOWN-state coverage (Phase-1 verification gap, #91277). |
| `test_fleet_matrix_self_restart_pending.py` | A gateway this updater runs INSIDE (cron update in the gateway tree, #100179) accepted a self-restart request and can only restart after the updater exits — so at fleet-matrix time it is still on the pre-update code by… |
| `test_focus_view.py` | Tests for ``/focus`` — the display-only reduced-output view. |
| `test_foreign_sessions.py` | Tests for hermes_cli.foreign_sessions — Claude Code / Codex CLI import. |
| `test_foreign_sessions_browser.py` | Discovery keeps readable sessions available when a neighboring log is inaccessible. |
| `test_free_tier_offer.py` | The install-wide record behind the free tier's sign-in offer: first due a fixed delay after the first finished task, then again only after another finished task and never sooner than the back-off since the previous offe… |
| `test_fts_optimize_notice.py` | Regression coverage for FTS storage upgrade discoverability. |
| `test_gateway.py` | Tests for hermes_cli.gateway. |
| `test_gateway_agent.py` | GatewayAgent drives main's HermesCLI callbacks from a scripted gateway (no live gateway). |
| `test_gateway_agent_compress.py` | Classic CLI ``/compress`` through GatewayAgent: main's ``compress_now`` is the gateway's ``session.mutate compress``, and the CLI prints the owner's report (no live gateway). |
| `test_gateway_agent_replay_gap.py` | Classic CLI (`hermes`, `hermes chat` -> GatewayAgent) across a ``session.replay_gap``: it re-attaches, shows the settled reply once and never leaves a later turn waiting on a retired subscription. A recovery belongs to… |
| `test_gateway_automation.py` | The classic CLI's /goal, /loop, /heartbeat managers on a gateway session are proxies over ``session.automation``: no local GoalManager (so no read-write state.db in the CLI pid, no judge model call), main's read helpers… |
| `test_gateway_chat.py` | Client launch must not silently downgrade policy or own execution. |
| `test_gateway_chat_blocking_controls.py` | Finite gateway chat tracks session-blocking controls without leaking foreign output. |
| `test_gateway_chat_commands_live.py` | Classic `hermes --cli chat` session commands on the shared gateway, driven in a real PTY. |
| `test_gateway_chat_failures.py` | Failure-path and terminal-receipt contracts for the transport-only CLI. |
| `test_gateway_chat_flags_live.py` | Launch flags on the classic CLI (main's HermesCLI, gateway-backed): bare -c, --resume latest, --list-tools, resume footer. Expectations are main's (git archive 3b63f7b0a4c, lanes/pushready/probe_oneshot.py). |
| `test_gateway_chat_native.py` | Native PTY clients against an ordinary daemon and loopback model only. |
| `test_gateway_chat_pending_preview.py` | A resumed classic CLI shows what each pending admission will run, safely, from the real snapshot. |
| `test_gateway_chat_plugin_inject.py` | `ctx.inject_message(text)` with no session_key/origin (plugins.md "Active CLI conversation") reaches the attached classic `hermes chat` session as a queued prompt, from a plugin's own thread (B2-11). |
| `test_gateway_chat_query_file_read.py` | The live --query-file read keeps main's contract (B2-09): undecodable bytes are replaced; an unreadable or empty file exits 2 naming it, with a failed ``result`` line under stream-json. |
| `test_gateway_chat_retry_lost_refresh.py` | Classic /retry keeps its prepared rewind until the post-rewind refresh lands: real authority, SQLite and AuthorityConnection.dispatch; the one session.resume after the rewind is dropped, so the user's repeat must replay… |
| `test_gateway_chat_retry_validate.py` | Classic /retry validates the target turn before rewinding it (dokterdok N92): real authority, SQLite and AuthorityConnection.dispatch; an image turn is refused with nothing archived, a text-parts turn is resubmitted as… |
| `test_gateway_chat_send_directive.py` | The classic CLI view submits a ``send`` directive from slash.exec as its own durable turn. |
| `test_gateway_chat_title_live.py` | Title-keyed resume on the classic CLI (main's HermesCLI, gateway-backed) against an ordinary daemon. The CLI process may read state.db but never writes it: the gateway is the single writer. |
| `test_gateway_chat_unknown.py` | Resume must expose the admission needed by the existing fenced discard control. |
| `test_gateway_chat_view_replay_gap.py` | GatewayChatView (`chat -q`, stream-json, `-z`, the thin chat) across a ``session.replay_gap``: it re-attaches; a one-shot prints the reply once; stream-json emits no ``text`` after the gap and its ``result`` carries the… |
| `test_gateway_cli_commands.py` | Classic CLI commands whose state lives in the gateway session are answered there (tracker #134889 CLI-8, CLI-17, CLI-21): ``/diff session`` (the gateway tools' checkpoint baseline), ``/reload`` (the gateway's ``.env``)… |
| `test_gateway_client_backlog.py` | A client's own event backlog never fails its turn (#134889). |
| `test_gateway_client_env.py` | LC-8 / T3 client side: the classic CLI and the Ink TUI launcher send this shell's allowlisted environment as ``session.create``'s ``client_env``, and only to a gateway that lists the field. |
| `test_gateway_client_recovery_backlog.py` | Recovery RPCs awaited from a client's only event consumer (#134889 CLI-35/CLI-37 review). |
| `test_gateway_client_rpc.py` | The viewer RPC client keeps an owner refusal's structured verdict (code + bounded data). |
| `test_gateway_client_ws_target.py` | Every owner dial (viewer, worker RPC, A2A forward, bot delivery, Ink bootstrap) builds the same target. |
| `test_gateway_command_parity.py` | The gateway command parity table is generated from the code and must be regenerated with it. |
| `test_gateway_command_parity_live_session.py` | A sidecar live-session RPC (``@_rpc(..., live_session=True)``) resolves ``session_id`` in the sidecar's own session map, which never holds a shared-gateway session: the parity table must not list a client that calls one… |
| `test_gateway_connection_command_socket.py` | ``GatewayConnection.call_until`` sends its one request on a socket of its own (#134889 PLG-7): never on the viewer's socket, never twice, and the socket is closed on the reply, on Ctrl+C (``wake``), on ``close()`` (CLI… |
| `test_gateway_connection_reconnect.py` | The classic CLI dials the gateway again after it restarts (#134889). |
| `test_gateway_disconnect_outcome.py` | Expected keepalive close preserves an honest unknown outcome and no task traceback. |
| `test_gateway_enroll_multiplex_warning.py` | Gateway enroll: secondary-multiplex-profile warning for relay routing stamps. |
| `test_gateway_external_supervisor.py` | Tests for explicit ownership by a wrapped external gateway supervisor. |
| `test_gateway_first_run_live.py` | First-run guidance on the real CLI without a configured executor. |
| `test_gateway_foreign_unit_guard.py` | `hermes gateway stop\|restart\|start` from a sandbox home must never operate ANOTHER install's systemd unit. |
| `test_gateway_foreign_xdg_runtime.py` | Regression tests for a foreign/leaked ``XDG_RUNTIME_DIR`` in the user-systemd preflight (#86558). |
| `test_gateway_host_stop_refusal.py` | The host multiplexer is never the pid a served profile's ``gateway stop`` may SIGTERM (#141133). |
| `test_gateway_host_verbs.py` | ``gateway start/restart --all`` and ``gateway run`` mean "the ONE host multiplexer". |
| `test_gateway_job_teardown_live.py` | LIVE Windows E2E for #48820 (4th repro): Job-Object teardown vs the gateway restart watcher, with real processes on a real windows-latest runner. |
| `test_gateway_launch_lifetime.py` | Detached owners must not lose the checkout their session still uses. |
| `test_gateway_launch_supervisor.py` | Local readers of a gateway's ``identify`` answer see what launched it, not the protocol's "none". |
| `test_gateway_launchd_runtime.py` | An unmanaged macOS gateway runs as a one-off launchd job through osascript, not as its caller's child. |
| `test_gateway_lifecycle_guards.py` | Gateway lifecycle verbs never take down a gateway they must not touch. |
| `test_gateway_linger.py` | Tests for gateway linger auto-enable behavior on headless Linux installs. |
| `test_gateway_migrate_compensator_resume.py` | The compensator's outcome, and a stranded host's recovery, under the flipped host lock. |
| `test_gateway_migrate_converged_host.py` | A CONVERGED host is a no-op for ``hermes gateway migrate --multiplex``, run after run. |
| `test_gateway_migrate_multiplex.py` | ``hermes gateway migrate``: preflight verdicts, apply/rollback bookkeeping, and the update hook. |
| `test_gateway_model_switch_cli.py` | The classic CLI's model switches over the shared gateway session (#134889 M1, review of #138717). |
| `test_gateway_multiplex_lifecycle.py` | Per-profile lifecycle never stops the shared host or hides an installed profile. |
| `test_gateway_multiplex_mode.py` | ``gateway.multiplex_profiles`` defaults to ON, but an UNSET flag is settled at boot by ``hermes_cli.gateway_multiplex_mode.resolve_multiplex_mode`` — the same preflight ``hermes gateway migrate --multiplex`` runs — so f… |
| `test_gateway_multiplex_refusal.py` | ``gateway.standalone`` and the multiplexer refusal: ``_named_profile_refused_under_multiplexer``. |
| `test_gateway_multiplex_s6.py` | s6 container: the unset multiplex default resolves ON when the boot has parked every named slot, ``hermes gateway migrate --multiplex`` folds an UP slot in-process, a guard refusal on a multi-profile host is loud, and t… |
| `test_gateway_multiplex_served_record.py` | The live multiplexer's recorded ``served_profiles`` decides "served"; every start verb honours it. |
| `test_gateway_multiplex_status.py` | PR #69118: a named profile served by the default multiplexer reports as running. |
| `test_gateway_no_new_standalone_profile.py` | A named profile cannot create a NEW standalone gateway — multiplexer running or not (#109417). |
| `test_gateway_platform_gating.py` | Host-specific gating in ``hermes_cli.gateway._all_platforms()``. |
| `test_gateway_plugin_commands.py` | Plugin slash commands typed in the classic CLI run in the gateway (#134889 PLG-7, CLI-13). |
| `test_gateway_proc_fallback.py` | Tests for /proc-based gateway PID detection in Docker environments. |
| `test_gateway_queued_unknown.py` | A finite queued viewer detaches when its predecessor becomes unknown. |
| `test_gateway_refused_owner.py` | #139845 / #140252: a same-user gateway that refuses the client is named, not ``authorization``. |
| `test_gateway_reload_mcp.py` | /reload-mcp on the shared gateway: the gateway reconciles its MCP servers and refreshes its agents (``reload.mcp``); the CLI never touches its GatewayAgent stand-in's tools. |
| `test_gateway_restart_all_marker.py` | ``gateway restart --all`` owes the same "Gateway online" notice as ``gateway restart``. |
| `test_gateway_restart_external_supervisor.py` | ``hermes gateway restart`` must hand an externally-supervised gateway back to its supervisor. |
| `test_gateway_restart_loop.py` | Tests for gateway restart-loop defenses (#30719). |
| `test_gateway_restart_no_unit_linger.py` | ``hermes gateway restart`` without an installed service unit must actually restart. |
| `test_gateway_restart_warm_probe_cache.py` | ``hermes gateway restart`` of a manual gateway must not attach to the gateway it just stopped. |
| `test_gateway_restart_watcher_bare_python.py` | The detached gateway restart watcher must survive on an interpreter without the dependency env. |
| `test_gateway_resume_launch_key.py` | The classic CLI re-supplies its launch-only key on every resume (refs #134889, RV-14). |
| `test_gateway_rollback.py` | /rollback on the shared gateway: the checkpoints are the gateway's, so list/diff/restore go to the owner's ``rollback.*`` verbs and print main's text (the CLI process has no manager). |
| `test_gateway_run_hard_exit.py` | Regression tests for CLI gateway run exit behavior. |
| `test_gateway_runtime.py` | Runtime discovery must distinguish absence from an unsafe/live owner. |
| `test_gateway_runtime_discovery.py` | Private discovery must not assume another process shares its temp root. |
| `test_gateway_runtime_ensure.py` | Real local-control and subprocess boundaries, never real service mutations. |
| `test_gateway_runtime_health.py` | Tests: `_iso_age`, `_stale_lines`, `test_runtime_health_lines_flags_stale_running_with_dead_pid`, `test_runtime_health_lines_include_fatal_platform_and_startup_reason`, `test_runtime_health_lines_flag_stale_heartbeat_wi… |
| `test_gateway_runtime_home_identity.py` | Endpoint discovery matches served homes by canonical identity on BOTH sides. |
| `test_gateway_runtime_replace_incompatible.py` | An owner from an older Hermes on the SAME home is replaced by ensure, never reported forever. |
| `test_gateway_runtime_service.py` | Installed identity proofs at inert native supervisor executable boundaries. |
| `test_gateway_runtime_service_roots.py` | Explicit requested-root naming and start-response encoding contracts. |
| `test_gateway_s6_dispatch.py` | Tests for the Phase 4 s6 dispatch helper in hermes_cli.gateway. |
| `test_gateway_scan_home_identity.py` | The gateway pid scan follows a process's real home. |
| `test_gateway_scm_feature_removed.py` | Pins the REMOVAL of the MSIX SCM Windows service feature (audit C06/C07). |
| `test_gateway_served_guard_ownership.py` | The CLI served-profile guard only counts a host gateway that is OURS and NOT our own process. |
| `test_gateway_service.py` | Tests for gateway service management helpers. |
| `test_gateway_service_choice.py` | Service consent through real config/discovery/install; only OS peers are fake. |
| `test_gateway_service_dbus_wait.py` | ``_wait_for_user_dbus_socket``: readiness found on poll_until's final check still exports the env. |
| `test_gateway_service_owner.py` | Gateway service-definition writes belong to the home the definition pins. |
| `test_gateway_service_paths.py` | Tests: `test_service_path_skips_nonexistent_node_modules`, `test_service_path_includes_node_modules_when_present` |
| `test_gateway_session_end_ownership.py` | A gateway-backed classic CLI leaves the end of its session to the gateway. |
| `test_gateway_session_store.py` | GatewaySessionStore: main's ``_session_db`` facade over gateway verbs (scripted gateway, no live one). |
| `test_gateway_setting_commands.py` | Per-session settings typed in the classic CLI run the gateway's handler (slash.exec) when the session is on the gateway; client-enforced state (/busy) is mirrored after the owner accepts. |
| `test_gateway_setup_moved_platforms_status.py` | Setup-menu status for the messaging platforms that moved from core into bundled plugins. |
| `test_gateway_side.py` | /bg and /btw on the shared gateway: the side task runs in the gateway (prompt.background / prompt.btw) and its answer is routed off the event stream by task id, never built in the CLI. |
| `test_gateway_snapshot_restore_guards.py` | CLI-16: the restore's own outcome decides the reply; a supervised owner or bad id never drains. |
| `test_gateway_snapshot_restore_live.py` | CLI-16 in #134889: restore offline, then keep chatting on the restored authority. |
| `test_gateway_start_attestation.py` | Tests for the #91675 gateway-start honesty fixes. |
| `test_gateway_startup_consent.py` | A consented launch reaches main's HermesCLI (``cli.main``) with its scoped options. |
| `test_gateway_startup_validation.py` | Invalid launch options must not inspect configuration they bypass. |
| `test_gateway_tools.py` | Main's process dock, status-bar ``⚙ N`` and ``/stop`` read the gateway session's processes. |
| `test_gateway_tools_notify.py` | A notification turn the gateway admits while the classic CLI is idle reaches main's screen. |
| `test_gateway_unit_paths.py` | User systemd unit location and identity: the account home owns the unit dir (#98699) and a bare ``hermes-gateway.service`` pinning THIS home is this home's service (#109476). |
| `test_gateway_unnamed_default_home_verbs.py` | Unnamed dashboard gateway lifecycle verbs issued from the DEFAULT home must name ``-p default`` explicitly (``_own_profile_selector``), so the spawned child can never re-read the sticky ``active_profile`` and restart an… |
| `test_gateway_user_bus_adoption.py` | #104893: a gateway started by a system-level systemd unit adopts its own user bus at boot. |
| `test_gateway_windows.py` | Tests for hermes_cli.gateway_windows. |
| `test_gateway_windows_restart_marker.py` | The Windows CLI restart stamps the planned-restart marker — after the old gateway is gone. |
| `test_gateway_windows_wsh_live.py` | Live Windows probe: Windows Script Host decodes the UTF-16 Startup chainer, so a target under a non-ASCII directory is found and launched (W13, #143547). |
| `test_gateway_wsl.py` | Tests for WSL detection and WSL-aware gateway behavior. |
| `test_gemini_express_key_probes.py` | Key-validation surfaces never reroute a key by its prefix, matching chat (#115306). |
| `test_gemini_free_tier_setup_block.py` | Tests for the Gemini free-tier block in the setup wizard. |
| `test_gemini_provider.py` | Tests for Google AI Studio (Gemini) provider integration. |
| `test_get_env_value_scope.py` | get_env_value must be scope-aware — the last scope-blind reader (#67027). |
| `test_git_pack_tidy.py` | Progressive partial-clone pack cleanup (#129712), on real git: partial clones of a local upstream. |
| `test_git_probe_no_lazy_fetch.py` | Read-only git probes never lazy-fetch from a partial clone's promisor remote. |
| `test_git_probe_tree_kill.py` | POSIX process-tree cleanup for ``bounded_git_probe`` (port of openai/codex#36793). |
| `test_git_trampoline_windows_live.py` | Live Windows E2E for the Git-for-Windows trampoline self-heal (#87876). |
| `test_gitlock.py` | Tests for hermes_cli.gitlock — stale git lock recovery + ancestry probe. |
| `test_gitlock_tmp_packs.py` | Aborted-fetch tmp_pack debris sweep (#93732, campaign #91277). |
| `test_global_auth_store_memo.py` | Measured-work pins for the _load_global_auth_store() memo. |
| `test_global_switch_persists_base_url_api_mode.py` | Regression tests for #25106: CLI `/model <name> --global` never persisted ``model.base_url``/``model.api_mode`` to config.yaml, so a global provider switch left the PREVIOUS provider's endpoint/wire-protocol on disk. Th… |
| `test_gmi_provider.py` | Focused tests for GMI Cloud first-class provider wiring. |
| `test_goal_dispatch.py` | Every goal surface applies the same commands to real persisted state. |
| `test_goal_gates.py` | Tests for /goal quality gates (GoalGate, run_gate, GoalManager gate flow). |
| `test_goal_judge_delegations.py` | The goal judge knows about delegated subagents. |
| `test_goal_judge_timeout_config.py` | `auxiliary.goal_judge.timeout` must actually reach the judge (#91022). |
| `test_goals.py` | Tests for hermes_cli/goals.py — persistent cross-turn goals. |
| `test_goals_db_bootstrap_off_loop.py` | SessionDB bootstrap must never run schema init on an event-loop thread. |
| `test_gpt56_registration.py` | Behavior contracts for the GPT-5.6 (Sol/Terra/Luna) registration. |
| `test_gpt6_tiers_registration.py` | Behavior contracts for the GPT-6 Sol/Terra/Luna registration (the 5.6 tier successors). |
| `test_graphical_browser_detection.py` | Tests for `_can_open_graphical_browser()` in hermes_cli.auth. |
| `test_guest_handoff.py` | The guest handoff step: a Nous account replacing the free tier moves the free tier's apps into it. |
| `test_guest_handoff_refresh.py` | A token refresh renews the identity the shared Nous store holds; only a sign-in replaces it. |
| `test_gui_command.py` | Tests for ``hermes gui`` desktop launcher wiring. |
| `test_gui_uninstall.py` | Tests for hermes_cli.gui_uninstall — GUI-only uninstall + install discovery. |
| `test_gui_uninstall_retention.py` | Regression for #128974: GUI dry-run and GUI removal preserve shared state. |
| `test_handoff_cleanup_race.py` | Regression tests for #88234 — CLI cleanup must NOT finalize a session that was handed off to the gateway. |
| `test_handoff_slow_dispatch_timeout.py` | Regression tests: a slow gateway handoff dispatch must not be misreported as "gateway not running" — and no waiter may stomp a claimed (running) row. |
| `test_hatch_prompt_thread_safety.py` | Regression test: bare /hatch must not call raw input() off the main thread. |
| `test_heartbeat.py` | Tests for /heartbeat (hermes_cli/heartbeat.py). |
| `test_hermes_home_shared_launchers.py` | A launch under another HERMES_HOME must not rebind shared launchers (#123238). |
| `test_hf_browse.py` | The HF browser: search the firehose, price it roughly, and let any GGUF become a normal staged model. |
| `test_history_commentary_display.py` | Public Codex commentary is a display projection, never a replay mutation. |
| `test_hold_stream_replay_gap.py` | The classic CLI viewer of a held turn paints and speaks only the rewrite, also when a replay gap makes it recover the reply from the settled receipt (built from a real held agent result). |
| `test_home_directory_diagnostics.py` | Home initialization must respect operator-owned links and diagnose storage. |
| `test_home_init_soul_symlink.py` | Home initialization must survive a SOUL.md symlink the seed cannot write through. |
| `test_hooks_cli.py` | Tests for the ``hermes hooks`` CLI subcommand. |
| `test_host_terminal_redraw.py` | The resize pair that redraws a host terminal's program reaches it as two observed sizes. |
| `test_host_terminal_viewer_ownership.py` | Viewer takeover linearizes at the PTY sink, including off-loop writes. |
| `test_ignore_user_config_flags.py` | Tests for --ignore-user-config and --ignore-rules flags on `hermes chat`. |
| `test_image_gen_picker.py` | Tests for plugin image_gen providers injecting themselves into the picker. |
| `test_imagegen_managed_gateway.py` | Regression tests for image_gen provider persistence (managed FAL clobber). |
| `test_indicator_command.py` | Tests for the /indicator CLI command and busy-indicator style config. |
| `test_init_command.py` | Tests for /init — generate or update AGENTS.md from a project scan. |
| `test_input_sanitize.py` | Tests for shared user prompt input sanitization. |
| `test_install_bucket_separation.py` | Uninstall and profile cloning respect the install/profile bucket split. |
| `test_install_cua_driver.py` | CUA runtime validation, explicit PM setup, and native host integration. |
| `test_install_identity.py` | Tests: `_race_first_install_id`, `test_concurrent_first_use_returns_one_persisted_identity`, `test_existing_identity_survives_read_only_root_or_racing_publication`, `test_independent_first_callers_return_the_single_comm… |
| `test_install_lock_timeout.py` | A backend binds even while another process holds the install lock. |
| `test_install_state.py` | Behaviour of the machine-level install probe (``hermes_cli.install_state``). |
| `test_installed_hub_identifiers.py` | Installed state for hub skills: the ``installed`` map that ``/api/skills/hub/sources``, ``/search`` and ``/official`` return. Desktop catalog cards look themselves up by the id they install; the dashboard looks a hub hi… |
| `test_interrupt_output_history_regression.py` | Regression tests for #60920/#60941: interrupt marker duplication on redraw. |
| `test_interrupt_requeue_image_payload.py` | #110737: an interrupting message that carries image attachments is a ``(text, images)`` tuple on ``_interrupt_queue``; the re-queue block in ``_chat_render_turn`` must hand it to ``_pending_input`` intact instead of str… |
| `test_inventory.py` | Behavior tests for hermes_cli.inventory. |
| `test_inventory_featured.py` | Regression tests for the ``featured_models`` shortlist in hermes_cli.inventory. |
| `test_inventory_pricing.py` | Tests for inventory._apply_pricing — the pricing/tier enrichment that |
| `test_inventory_reasoning_caps.py` | Tests for the reasoning detail inventory._apply_capabilities puts on the |
| `test_ipv6_url_authorities.py` | IPv6 binds must render as bracketed URL authorities everywhere a URL is built. |
| `test_iron_proxy_cli.py` | Unit tests for ``hermes_cli.proxy_cli`` command handlers. |
| `test_isolated_serve_ledger_marker.py` | An isolated serve says so in the spawn ledger; an ordinary serve does not. |
| `test_jobs_json_utf8_bom.py` | UTF-8 BOM tolerance for independent jobs.json readers (dump/status). |
| `test_journey_render.py` | Behavior contracts for /journey output routing. |
| `test_kanban_aux_affinity.py` | Kanban specify/decompose run headless (no agent turn), yet their auxiliary calls must still carry a relay-affinity key — the OpenCode Go relay rejects a request without ``x-opencode-session`` with 400 MissingSessionID (… |
| `test_kanban_block_classify.py` | block_task() classifies an untyped breaker block in place (#117363). |
| `test_kanban_block_kinds.py` | Tests for typed block reasons + the unblock-loop breaker. |
| `test_kanban_blocked_sticky.py` | Regression tests for #28712 — kanban dispatcher must not auto-promote worker-initiated ``kanban_block`` (sticky blocks), but must keep auto-recovering circuit-breaker blocks. |
| `test_kanban_board_path_priority.py` | Regression tests for _board_path priority: explicit board trumps env pin. |
| `test_kanban_board_project.py` | Board→project scoping in kanban_db. |
| `test_kanban_boards.py` | Tests for the multi-board kanban layer (``hermes kanban boards …``). |
| `test_kanban_cli.py` | Tests for the kanban CLI surface (hermes_cli.kanban). |
| `test_kanban_cli_dispatch_passthrough.py` | Regression tests for #33488 (CLI max_in_progress / max_spawn / per-profile config passthrough) and #29415 (kanban_swarm humanizer skill ref). |
| `test_kanban_cli_exit_status.py` | Regression coverage for Kanban CLI process exit status propagation. |
| `test_kanban_comment_queries.py` | Comment-watermark queries in kanban_db. |
| `test_kanban_complete_live_claim_guard.py` | Invariant: ``complete_task`` never closes a live worker's run for a caller that neither owns the run nor asked for an operator override (issue #111764). |
| `test_kanban_core_functionality.py` | Core-functionality tests for the kanban kernel + CLI additions. |
| `test_kanban_count_notify_subs.py` | Tests for ``kanban_db.count_notify_subs`` — the read-only subscription probe. |
| `test_kanban_create_body_file.py` | `kanban create --body-file` — shell-proof body delivery (#115432). |
| `test_kanban_creator_origin.py` | All explicit creator paths share durable lineage without graph coupling. |
| `test_kanban_credential_startup_exit.py` | Credential rejection before a turn must retain the Kanban exit contract. |
| `test_kanban_db.py` | Tests for the Kanban DB layer (hermes_cli.kanban_db). |
| `test_kanban_db_init.py` | Tests: `_make_legacy_db`, `_setup_home`, `_table_struct`, `test_legacy_text_pk_tables_rebuilt_to_integer_autoincrement`, `test_migration_is_idempotent`, `_default_board_db` … |
| `test_kanban_db_repair.py` | Tests for kanban DB corruption repair, backup retention, WAL checkpointing, and the ``hermes kanban repair`` CLI verb. |
| `test_kanban_decompose.py` | Tests for the decomposer module + `hermes kanban decompose` CLI surface. |
| `test_kanban_decompose_db.py` | Tests for decompose_triage_task — the DB-layer atomic fan-out from the triage column. LLM-free by design. |
| `test_kanban_default_assignee.py` | Regression tests for #27145 — kanban.default_assignee for unassigned ready tasks. |
| `test_kanban_diagnostics.py` | Tests for hermes_cli.kanban_diagnostics — rule-engine that produces structured distress signals (diagnostics) for kanban tasks. |
| `test_kanban_dispatch_claim_allowlist.py` | kanban.dispatch_profiles: per-home claim allowlist for shared boards (#110995). |
| `test_kanban_dispatch_lock.py` | Tests for the kanban dispatcher single-writer lock (issue #35240). |
| `test_kanban_dispatch_tick_hook.py` | Tests for the ``on_kanban_dispatch_tick`` observer hook. |
| `test_kanban_dispatch_unknown_assignee_event.py` | Dispatcher must leave per-task diagnostics for unknown assignees (#122422). |
| `test_kanban_empty_completion.py` | ``complete_task`` refuses empty / whitespace-only evidence (#117483). |
| `test_kanban_gateway_restart_handoff.py` | Managed-gateway isolation for dispatcher-owned Kanban workers. |
| `test_kanban_gc_retention.py` | Retention bounds for ``kanban gc``: a negative window builds a future cutoff that matches every row; zero disables the sweep rather than deleting all. |
| `test_kanban_goal_judge_affinity.py` | Goal-judge handoff gates: per-task relay-affinity scope + fail-open on transport failure. |
| `test_kanban_goal_mode.py` | Tests for kanban goal_mode — per-card Ralph-style goal loop. |
| `test_kanban_goal_mode_worker_log.py` | A goal_mode Kanban worker keeps the live tool feed in its worker log. |
| `test_kanban_graph_identity.py` | Graph identity is completion history, not prerequisite edges. |
| `test_kanban_host_cap.py` | Host-level concurrency accounting + review-lane fairness (OOF-30 review). |
| `test_kanban_init_lock_bounded.py` | Tests for the bounded kanban init lock (issue #36644). |
| `test_kanban_lifecycle_hooks.py` | Tests for kanban lifecycle plugin hooks. |
| `test_kanban_list_undecodable_text.py` | Invariant: one task row with an undecodable text field cannot take down the board listing (issue #111743). |
| `test_kanban_managed_exit_reconciliation.py` | Join authority-owned worker receipts with main's exit classification. |
| `test_kanban_managed_result_pid.py` | A managed Kanban run's lost-ACK recovery honours the exit its authority recorded. |
| `test_kanban_managed_worker_loss.py` | A lost managed worker must be DISPOSED OF on the board, within one dispatcher tick. |
| `test_kanban_memory_guard.py` | Memory-aware kanban dispatch guard (OOF-30 / OOF-77). |
| `test_kanban_notify.py` | Tests: `kanban_home`, `test_notify_sub_delivery_mode_persists_and_last_write_wins`, `test_notify_subscribe_cli_records_discord_multiplex_anchors`, `test_notify_sub_chat_type_persists_and_last_write_wins`, `test_notify_s… |
| `test_kanban_owner_receipt_reclaim.py` | A dead attempt behind an unresolved owner receipt must not hold its claim forever. |
| `test_kanban_parent_reopen_invalidation.py` | Regressions for domain-layer descendant invalidation on ancestor reopen. |
| `test_kanban_per_profile_cap.py` | Regression tests for #21582 — per-profile concurrency cap in dispatcher. |
| `test_kanban_pr_acceptance.py` | Two lifecycle invariants, using real SQLite and a local GitHub HTTP contract. |
| `test_kanban_project_link.py` | Kanban <-> Projects integration: project-linked tasks get a deterministic worktree path + branch instead of the random ``wt/<task-id>`` fallback. |
| `test_kanban_promote.py` | Tests for the kanban `promote` verb (issue #28822). |
| `test_kanban_reclaim_claim_lock_guard.py` | Tests: reclaim paths are claim-lock-aware so they can't desync a re-claimed task (issue #36910). |
| `test_kanban_resume_guard.py` | Kanban worker transcripts must not resume as ordinary write-capable sessions (#68779). |
| `test_kanban_review_lifecycle.py` | Review-lifecycle tests: the first-class ``running -> review`` transition. |
| `test_kanban_review_lifecycle_complete.py` | End-to-end regressions for the Kanban review lifecycle. |
| `test_kanban_review_surfaces.py` | Cross-surface regressions for the complete Kanban review lifecycle. |
| `test_kanban_specify.py` | Tests for the specifier module + `hermes kanban specify` CLI surface. |
| `test_kanban_specify_db.py` | Tests for kb.specify_triage_task — the DB-layer atomic promotion from the triage column to todo. LLM-free by design. |
| `test_kanban_swarm.py` | Tests: `test_create_swarm_builds_parallel_workers_verifier_and_synthesizer`, `test_create_swarm_graph_is_atomic_and_rolls_back_partial_build`, `test_plain_write_txn_nesting_raises_and_allow_nested_composes`, `test_swarm… |
| `test_kanban_task_updated_hook.py` | Tests for the ``on_kanban_task_updated`` mutation observer (RFC #58548). |
| `test_kanban_terminal_worker_reaper.py` | Invariant: a worker that outlives its own terminal transition is still reachable and gets reaped by the dispatcher (issue #111791). |
| `test_kanban_transfer.py` | Tests for kanban board export / import (``hermes_cli.kanban_transfer``). |
| `test_kanban_watch_banner.py` | Watch identifies the board selected by the production command parser. |
| `test_kanban_worker_admission_wait.py` | KB-7: the Kanban submitter waits for ``kanban.run``'s admission answer past the default RPC budget. |
| `test_kanban_worker_exit_decode.py` | Worker exit classification must not depend on POSIX-only ``os.WIF*`` helpers. |
| `test_kanban_worker_exit_trailer.py` | A dead Kanban worker is booked the same way whichever process notices it. |
| `test_kanban_worker_image_extraction.py` | Worker-side image enrichment for kanban tasks. |
| `test_kanban_worker_lifecycle_hooks.py` | Tests for the ``on_kanban_worker_*`` observer hooks (RFC #58548). |
| `test_kanban_worker_owner_wait.py` | A Kanban worker spawned while `hermes update` drains the owner waits for it instead of failing. |
| `test_kanban_worker_pid_fingerprint.py` | A recycled worker PID is never mistaken for our worker. |
| `test_kanban_worker_session_source.py` | Kanban worker runs must not surface as user conversations. |
| `test_kanban_worker_socket_recovery.py` | A Kanban worker whose gateway socket dies mid-turn resumes the same attempt on a new connection. |
| `test_kanban_worker_spawn_toolsets.py` | Tests: `_make_task`, `test_default_spawn_pins_assignee_profile_cli_toolsets`, `test_default_spawn_does_not_pass_mutable_launch_overrides`, `test_default_spawn_resolves_env_passthrough_under_multiplex`, `test_worker_tool… |
| `test_kanban_worker_terminal_cwd.py` | Tests: kanban worker spawn pins TERMINAL_CWD to the task workspace. |
| `test_kanban_worker_terminal_scope.py` | A kanban worker spawned for profile B must not inherit the DISPATCHER's credentials. |
| `test_kanban_workflow.py` | Kanban workflow definition: shape, validation, and the copies that derive from it. |
| `test_kanban_worktree_isolation.py` | Per-task worktree isolation for decompose siblings. |
| `test_kanban_worktree_teardown.py` | Tests for worktree workspace teardown at task completion/archive. |
| `test_kanban_worktree_unicode_path.py` | Regression: a composed (NFC) workspace path must resolve against its repo root. |
| `test_kanban_write_guard.py` | #69283: kanban write guard prevents tests from writing to real ~/.hermes. |
| `test_kanban_write_txn_busy_retry.py` | write_txn BUSY-retry behaviour. |
| `test_keyed_provider_credential_pool.py` | Keyed ``providers.<key>`` entries must use the durable pool slug. |
| `test_kimi_cn_provider_listing.py` | Test that kimi-coding and kimi-coding-cn both appear in the /model picker. |
| `test_kitty_keypad_parity.py` | Modified kitty keypad keys must behave like their non-keypad twins (#97290). |
| `test_launch_readonly.py` | Launch metadata reads cannot create or migrate canonical storage. |
| `test_launch_relaunch_loop.py` | A launch whose dependencies stay stale boots; it never re-execs itself forever. |
| `test_launchd_force_install_retry.py` | Forced launchd reinstall must wait out the old supervised process before bootstrap (#120629). |
| `test_launchd_install_start_now.py` | `hermes gateway install --no-start-now` and the setup wizard's "Start the gateway now?" = No on launchd. |
| `test_launchd_plist_guard.py` | Regression tests for the launchd plist scan's malformed-file tolerance. |
| `test_launchd_refresh_reporting.py` | launchd plist refresh must not report success when launchd never registered the service (#12866). |
| `test_launchd_restart_refresh.py` | ``launchd_restart`` must never kickstart a stale service definition. |
| `test_launcher.py` | Tests for the top-level `./hermes` launcher script. |
| `test_launcher_runtime_selection.py` | Launch-time dependency selection survives a change after launcher minting. |
| `test_lazy_command_exports.py` | The frozen updater surface on hermes_cli.main stays lazy and resolvable. |
| `test_lazy_secrets_dispatch.py` | End-to-end tests for lazy cryptography loading. |
| `test_lazy_secrets_import.py` | Regression test: hermes update must not load cryptography eagerly. |
| `test_left_core_camofox.py` | Camofox left core for the ``camofox`` catalog plugin: a home that ran core's Camofox backend gets the plugin once, and its core-era ``browser`` toolset (Camofox's browser_* tools then; browser_exec now) becomes the plug… |
| `test_left_core_migration.py` | ``hermes_cli.left_core_migration``: homes that used a feature that left core get its catalog plugin. |
| `test_left_core_provider_rows.py` | ``LEFT_CORE`` rows for a model provider that moved into a catalog plugin. |
| `test_left_core_provider_runtime.py` | Runtime wiring of the ``LEFT_CORE`` provider rows: the real ``resolve_runtime_provider`` installs the plugin of a provider that left core for a home that uses it, once per process, honouring the failure backoff and ``se… |
| `test_left_core_singularity.py` | The Singularity terminal backend left core for the ``singularity`` catalog plugin: homes whose backend is ``singularity`` get the plugin once, the name is free for the plugin to register, and a home without it hears the… |
| `test_legacy_launchers_windows_live.py` | Live Windows probe: pre-suffix gateway launchers are reported by ``status`` and removed by ``uninstall`` (#116157). |
| `test_legacy_pump_close_reason.py` | The dashboard's legacy /chat pump (no ``?attach=`` token) closes as on main. |
| `test_lifecycle.py` | Tests: `test_invoke_hook_notifies_builtin_observers_before_plugins`, `test_finalize_session_closes_core_before_plugin_export`, `test_plugin_only_dispatch_does_not_reenter_builtin_observers` |
| `test_linux_desktop_entry.py` | Tests for the Linux XDG desktop entry installed by ``hermes desktop``. |
| `test_linux_launcher_management.py` | Native Linux launcher management through real config and filesystem I/O. |
| `test_linux_ram_probe.py` | Linux RAM availability must include reclaimable page cache (#102252). |
| `test_linux_sandbox_fixup.py` | Tests for the Linux desktop sandbox-helper fixup and the userns probe. |
| `test_list_picker_providers.py` | Tests for ``list_picker_providers`` — the /model picker filter. |
| `test_list_recent_user_messages_handoffs.py` | list_recent_user_messages must skip legacy compaction handoffs (#80622). |
| `test_lmstudio_context_policy.py` | Tests: `_JsonResponse`, `_catalog`, `_capture_load`, `test_missing_echo_refreshes_loaded_state`, `test_explicit_override_above_known_maximum_rejects_even_when_loaded` |
| `test_load_progress.py` | Model-load progress: SSE events -> composite percent -> wait notices. |
| `test_local_abandoned_requests.py` | Abandoned-request lifecycle: work sent to the managed local server must die when its caller goes away, and teardown must never orphan VRAM. |
| `test_local_component_jobs.py` | Desktop component jobs pause real PM archive transfers before activation. |
| `test_local_context_resolution.py` | Context-length resolution for the managed llama.cpp router. |
| `test_local_download_jobs.py` | Local-model jobs use PM transfers for every entry point. |
| `test_local_external_draft.py` | An external DFlash draft on a recurrent model: replaces MTP when it fits, on one slot. |
| `test_local_growth.py` | In-session growth contracts (growth.py + the presets override seam). |
| `test_local_job_registry.py` | Paused work remains discoverable, and terminal phase changes honor pause intent. |
| `test_local_launch_budget.py` | Launch windows are sized beside what other programs hold on the card, not from capacity alone. |
| `test_local_legacy_engine.py` | A pre-PM engine under runtimes/llamacpp/ moves into PM's store instead of forcing first-run setup. |
| `test_local_legacy_models_dir.py` | Models staged under the old per-profile ``<profile home>/models`` layout are moved into the machine-scoped ``<root>/models`` so they keep loading. |
| `test_local_models_activate_rescan.py` | The activate flow's rescan must fire even when another process owns the local server (#115237). |
| `test_local_models_routes.py` | Contract tests for the local-models dashboard routes (Rollout 4). |
| `test_local_mtp_head.py` | A model whose MTP head ships as its own file. |
| `test_local_n1x_pci_identity.py` | Verify N1X recommendations use PCI identity rather than driver display names. |
| `test_local_picker_identity.py` | The managed local server owns its picker identity. |
| `test_local_preset_admission.py` | The router must serve only admitted presets, retaining refusal and spill facts on read-back. |
| `test_local_provider_alias_parity.py` | Parity contract for local OpenAI-compatible provider aliases (issue #62213). |
| `test_local_quickstart.py` | Quickstart route: one POST from nothing to a working local default. |
| `test_local_reasoning_default.py` | Managed reasoning defaults belong to the model preset, below explicit client choices. |
| `test_local_recommendation.py` | The recommendation decision table — the reviewable matrix. |
| `test_local_recommendation_policy.py` | Automatic recommendations require residency; manual choices may spill. |
| `test_local_residency_admission.py` | Residency admission is priced against the card, not a constant count. |
| `test_local_router_autoload.py` | Status reads never load a model. |
| `test_local_runtime.py` | Contract tests for hermes_cli.local_runtime — Rollouts 1+2. |
| `test_local_runtime_child_env.py` | A managed llama-server child never inherits credential-shaped environment variables. |
| `test_local_runtime_gguf.py` | Behavior contracts for the managed local runtime's GGUF reader. |
| `test_local_runtime_gguf_split.py` | A split GGUF is priced as the SET of its shards, never as its first file. |
| `test_local_runtime_gguf_swa.py` | profile_from_gguf must trust the GGUF file's own per-layer SWA pattern over the hardcoded architecture-name table (#109551): an architecture absent from `_SWA_LAYER_FRACTION` that still declares `attention.sliding_windo… |
| `test_local_runtime_lazy_read.py` | Tensors llama.cpp reads from disk on demand are not priced as loaded weights. |
| `test_local_runtime_legacy_state.py` | Legacy local-runtime records must not adopt a reused PID. |
| `test_local_runtime_load_mode.py` | Managed launch preserves direct I/O across engine command-line versions. |
| `test_local_runtime_package_import.py` | Shipped updaters import ``hermes_cli.local_runtime.processes`` from the new tree mid-update. |
| `test_local_runtime_picker_row.py` | The llamacpp provider row in the model picker payload. |
| `test_local_runtime_pm.py` | Backend selection uses reviewed target pins and never installs on lookup. |
| `test_local_runtime_processes.py` | Native containment tests; all processes and homes are disposable. |
| `test_local_runtime_recovery.py` | Recovery only targets the recorded managed router, never a process-name sweep. |
| `test_local_runtime_updates.py` | Engine updates read PM pins; boot retains installed bytes without downloading. |
| `test_local_server_lifecycle.py` | Server on/off lifecycle route (round-9 feedback: 'we should be able to completely turn off the local engine'). Contract: stop tears the server down AND persists enabled=false (durable, unlike eject); start persists enab… |
| `test_local_window_compute.py` | Compute buffers that grow with the window are priced at the launch posture. |
| `test_local_windows_commit_budget.py` | Windows unified memory: the model and its prompt cache must fit in commit. |
| `test_local_windows_igpu_pool.py` | An integrated GPU on Windows is budgeted from what Windows lets it allocate, never all of RAM. |
| `test_login_backend_provenance.py` | Who may register a password-manager login backend (``ctx.register_login_backend``). |
| `test_login_cli_command.py` | Tests: `_Thread`, `_cli`, `test_the_cli_handler_prints_the_code_then_drains_off_thread`, `test_the_drain_only_moves_the_free_tier_model_on_completion`, `test_a_precondition_prints_without_starting_a_thread`, `test_ctrl_… |
| `test_logs.py` | Tests for hermes_cli.logs — log viewing and filtering. |
| `test_loops.py` | Tests for hermes_cli/loops.py — /loop recurring in-session wakeups. |
| `test_macos_fda_guidance.py` | macOS Full Disk Access onboarding guidance (issue #52010 follow-up). |
| `test_macos_tcc_anchor.py` | Tests for the dylib-complete macOS TCC anchor (issue #95596). |
| `test_main_merge_lifecycle.py` | Behavior parity at lifecycle helpers extracted before the main merge. |
| `test_main_model_custom_provider_normalization.py` | Dashboard main-model writes preserve declared provider identities. |
| `test_managed_install_shapes.py` | Managed-mode detection across the Nix install shapes. |
| `test_managed_installs.py` | Tests: `test_recommended_update_command_defaults_to_hermes_update`, `test_get_managed_system_false_values`, `test_optional_skill_source_honors_env_override` |
| `test_managed_scope.py` | Unit tests for hermes_cli.managed_scope (resolver + loaders + key helpers). |
| `test_managed_scope_cli_config.py` | Managed scope must reach cli.py's independent config loader (CLI_CONFIG). |
| `test_managed_scope_config.py` | Config integration tests — managed scope wins over user config at the leaf. |
| `test_managed_scope_env.py` | Env integration tests — managed .env applied last with override. |
| `test_managed_scope_loaders.py` | Each standalone config loader (gateway, TUI/desktop, cron) must honor managed scope. |
| `test_managed_scope_overlay.py` | apply_managed_overlay() — the shared helper used by every standalone loader. |
| `test_managed_scope_regression.py` | Regression harness — pins config/env load behavior BEFORE managed scope exists. |
| `test_managed_scope_surfacing.py` | Surfacing tests — managed scope shown in `config show` and `hermes doctor`. |
| `test_managed_scope_writeguard.py` | Write-guard tests — managed keys can't be set/removed by the user. |
| `test_managed_vision_capability.py` | Vision capability for managed local models answers from ground truth. |
| `test_manual_compress.py` | Tests for CLI manual compression messaging. |
| `test_manual_serve_deferral.py` | Manual serve restart obligations survive gateway completion and receipt rotation (#107224). |
| `test_mcp_catalog.py` | Tests for hermes_cli.mcp_catalog and hermes_cli.mcp_picker. |
| `test_mcp_catalog_env_boundary.py` | Security boundary tests for dashboard MCP catalog credential writes. |
| `test_mcp_config.py` | Tests for hermes_cli.mcp_config — ``hermes mcp`` subcommands. |
| `test_mcp_dashboard_oauth.py` | Dashboard HTTP contract for hosted MCP OAuth. |
| `test_mcp_discovery_timing.py` | Regression tests for MCP discovery timing in non-interactive sessions. |
| `test_mcp_helper_ledger.py` | Tests for stdio MCP helper children in the spawn ledger (#61514). |
| `test_mcp_login_window.py` | An OAuth login waits as long as ``oauth.timeout`` says, and a probe timeout names itself (#116278). |
| `test_mcp_probe_redaction.py` | MCP test/dashboard must not fingerprint Authorization credentials (#97460). |
| `test_mcp_security.py` | Tests for MCP server exfiltration hardening. |
| `test_mcp_startup.py` | Regression tests for bounded/lazy CLI MCP startup. |
| `test_mcp_tools_config.py` | Tests for MCP tools interactive configuration in hermes_cli.tools_config. |
| `test_mem_trim.py` | Tests for the long-lived gateway heap-trim helper. |
| `test_memory_dependency_admission.py` | Memory setup admits a complete candidate before saving its selection. |
| `test_memory_provider_core_sentinels.py` | ``memory.provider`` set to a core sentinel (``builtin``/``default``/``none``) names the built-in store, not a plugin: doctor and the provider migration must not report it as missing (#75647, #115113). |
| `test_memory_provider_migration.py` | A memory provider that left core is installed from the catalog, config untouched; a provider the catalog does not know is reported with the one-liner instead of silently dropping memory. |
| `test_memory_setup.py` | Tests: `test_cmd_setup_generic_choice_cancel_writes_nothing`, `test_install_dependencies_prepares_declared_extra_even_if_importable`, `test_cmd_status_memory_tool_gate_disabled`, `test_cmd_status_memory_tool_gate_enable… |
| `test_memory_setup_env_denylist.py` | Tests for the env-write denylist on the memory-setup ``.env`` writer. |
| `test_memory_setup_provider_arg.py` | Tests for `hermes memory setup [provider]` routing. |
| `test_memory_status_env_hint.py` | `hermes memory status` should explain *why* a provider is unavailable. |
| `test_merge_profile_tree.py` | _merge_profile_tree folds projects across profiles by normalized path. |
| `test_messaging_catalog_plugin_metadata.py` | A platform plugin's PlatformEntry is the single source of its dashboard card and write checks. |
| `test_meta_prompt_cache.py` | Behavior contracts for Meta Muse prompt-caching host mandate. |
| `test_migrate_xai.py` | Tests for ``hermes migrate xai`` — apply path with ruamel round-trip. |
| `test_minimax_model_validation.py` | Tests for MiniMax model validation via static catalog (issues #12611, #12460, #12399, #12547). |
| `test_minimax_oauth.py` | Tests for MiniMax OAuth provider (hermes_cli/auth.py). |
| `test_moa_command.py` | Tests: `_make_cli`, `test_moa_bare_shows_usage_no_switch`, `test_moa_arg_is_always_one_shot_prompt`, `test_moa_non_preset_is_one_shot_prompt`, `TestNormalizeMoaModel` |
| `test_moa_config.py` | Tests: `test_moa_slot_picker_excludes_unconfigured_providers`, `_enabled_refs`, `test_normalize_moa_config_uses_default_named_preset`, `test_exact_preset_matching_skips_disabled_presets`, `test_resolve_missing_moa_prese… |
| `test_moa_numeric_config.py` | Malformed numeric MoA settings must degrade to defaults, not break the CLI or JSON. |
| `test_moa_preset_config_warnings.py` | A user's named MoA presets are not schema-defaulted config options. |
| `test_moa_preset_deletion.py` | A MoA preset dropped from the payload must leave config.yaml. |
| `test_moa_set_models_preserves_extra_keys.py` | Regression tests for ``set_moa_models`` preserving undeclared config keys. |
| `test_model_alias_credentials.py` | Direct-alias (``model_aliases:``) credential resolution (#83612). |
| `test_model_assignment_env_key_mirror.py` | #88990: Desktop model assignment must not copy env-backed keys into model.api_key. |
| `test_model_cache_fallback_rows.py` | A curated fallback served because the live catalog fetch failed must never be pinned in the disk cache as if it were the account's real catalog (#107391): a transient Copilot outage wrote the 17-model static list over t… |
| `test_model_cache_parallel_prefetch.py` | Tests for parallel model-catalog prefetch and thread-safe cache writes. |
| `test_model_cache_swr.py` | Stale-while-revalidate behavior for the model-id disk cache and the remote model-catalog manifest. |
| `test_model_catalog.py` | Tests for hermes_cli.model_catalog — remote manifest fetch + cache + fallback. |
| `test_model_cost_guard.py` | Tests: `test_no_warning_when_known_prices_are_at_threshold`, `test_warns_when_models_dev_input_price_exceeds_threshold`, `test_skips_foreign_models_dev_pricing_for_custom_or_unknown_providers`, `test_skips_untrusted_pro… |
| `test_model_data_policy_guard.py` | Tests for the data-training-tier selection guard. |
| `test_model_flow_external_process_setup.py` | `hermes model` for a process provider gates on the CLI's login and lists its live picker. |
| `test_model_flow_local.py` | ``hermes model`` → Local models runs the desktop's Local Models setup in the terminal. |
| `test_model_flow_pooled_credentials.py` | Pool-only credentials must be visible to interactive model setup flows. |
| `test_model_info_probe_timeout.py` | /api/model/info must bound its context-length probe (#63214). |
| `test_model_normalize.py` | Tests for hermes_cli.model_normalize — provider-aware model name normalization. |
| `test_model_options_account_usage.py` | The model picker shows subscription usage before the wall, without ever waiting on a usage API. |
| `test_model_options_pool_usage.py` | Pool-aware model-picker usage: per-account rows, cache isolation, honest failures. |
| `test_model_options_rate_limited_pool.py` | A rate-limited provider stays in the GUI model picker (#103829, #124510). |
| `test_model_options_read_path_catalogs.py` | ``model.options`` is a READ path: opening the picker must not wait on a provider catalog probe. |
| `test_model_persist_one_shape.py` | One config.yaml shape for a persisted model selection, whichever surface wrote it. |
| `test_model_picker_excluded_providers.py` | Tests that ``model_catalog.excluded_providers`` hides providers from the interactive ``hermes model`` CLI picker. |
| `test_model_picker_expensive_confirm.py` | Tests: `_bound`, `test_prompt_toolkit_model_picker_defers_confirmation_off_key_handler` |
| `test_model_picker_filter.py` | Tests for the /model picker fuzzy filter (C-01). |
| `test_model_picker_secret_scope.py` | The /model picker must read provider keys through the per-profile scope. |
| `test_model_picker_usage.py` | Window vs. credit-grant chrome for the model pickers. |
| `test_model_picker_viewport.py` | Tests for the prompt_toolkit /model picker scroll viewport. |
| `test_model_prefix_routing.py` | Regression tests for vendor-prefix model routing and dict model.aliases (#87189). |
| `test_model_provider_persistence.py` | Tests that provider selection via `hermes model` always persists correctly. |
| `test_model_search.py` | Picker search aliases for brand-less wire model ids. |
| `test_model_search_alias_dedup.py` | Picker dedup must fold live bare wire-ids into their curated public slug. |
| `test_model_selection_atomic_persistence.py` | A saved model route is one publication, including stale credential removal. |
| `test_model_selection_guards.py` | Tests for the unified model-selection guard registry. |
| `test_model_set_explicit_custom_endpoint.py` | #145466: the Local / custom endpoint wizard posts ``provider: custom`` + a NEW ``base_url`` to POST /api/model/set. With a named custom provider already configured, the legacy bare-``custom`` recovery bound the request… |
| `test_model_set_preserve_custom_endpoint.py` | Red test for #76324: POST /api/model/set preserving a CLI-configured bare ``custom`` endpoint. |
| `test_model_set_secret_copy.py` | POST /api/model/set must never copy an env-expanded secret into config.yaml. |
| `test_model_setup_public.py` | Public helpers a provider plugin's ``model_setup_flow`` calls (documented in model-provider-plugin.md). |
| `test_model_switch_configured_provider_routing.py` | Regression tests for #45006: typed `/model <name>` resolution must route a model declared in user/custom provider config to that provider instead of leaving it on the current provider and soft-accepting it. |
| `test_model_switch_confirm_thread.py` | The /model <name> --provider <p> path must run the expensive-model confirm + apply sequence off the main thread. |
| `test_model_switch_context_display.py` | Regression test for /model context-length display on provider-capped models. |
| `test_model_switch_custom_providers.py` | Regression tests for /model support of config.yaml custom_providers. |
| `test_model_switch_external_process_alias.py` | `/model <alias>` stays on an external-process provider that declares the alias. |
| `test_model_switch_filter_unresolved.py` | Picker rows must resolve to a runtime provider (#57503). |
| `test_model_switch_openai_api_mode.py` | Regression tests for OpenAI-direct api_mode recomputation during /model switch. |
| `test_model_switch_opencode_anthropic.py` | Regression tests for OpenCode /v1 stripping during /model switch. |
| `test_model_switch_parsing.py` | Single-owner /model argument parsing (hermes_cli.model_switch.parse_model_switch_args). |
| `test_model_switch_persist_default.py` | Tests for session-scoped-by-default model switching. |
| `test_model_switch_reasoning_flag.py` | ``/model <name> --reasoning <level>`` — one request carries a model pick AND its effort. |
| `test_model_switch_reasoning_reresolve.py` | The CLI-level ``reasoning_config`` follows the model on every path that moves ``cli.model``. |
| `test_model_switch_user_provider_slug_verbatim.py` | A model the user selected on their own ``providers.<key>`` endpoint survives ``/model`` verbatim — whether the slug arrives as ``custom:<key>`` or as the bare config key the Desktop picker rows carry. Its ``/v1/models``… |
| `test_model_switch_variant_tags.py` | Tests for OpenRouter variant tag preservation in model switching. |
| `test_model_validation.py` | Tests for provider-aware `/model` validation in hermes_cli.models. |
| `test_model_validation_managed_local.py` | Tests for the managed llama.cpp runtime branch in /model validation (#115237). |
| `test_models.py` | Tests for the hermes_cli models module. |
| `test_models_analytics_attribution.py` | Models analytics must attribute usage per API call, not per session (#71778). |
| `test_models_analytics_dedup.py` | Models analytics must emit one row per (model, provider) pair (#89631). |
| `test_models_catalog_late_plugin_provider.py` | A provider registered after ``hermes_cli.models`` was imported still reaches the picker catalog. |
| `test_models_detect_credential_gate.py` | Auto-detection must never hand the user a provider they hold no credentials for. |
| `test_models_detect_live_catalog.py` | ``detect_provider_for_model`` must not re-route a model the CURRENT provider already serves. |
| `test_models_detect_vendor_ownership.py` | A first-party session never re-routes its own vendor's model when the live catalog cannot vouch. |
| `test_models_dev_preferred_merge.py` | Tests for the models.dev-preferred merge behavior in provider_model_ids and list_authenticated_providers. |
| `test_models_relay_base_url.py` | `model.base_url` relays must be probed instead of the vendor's canonical host (#121387). |
| `test_modify_other_keys_aliases.py` | Regression tests for issue #87711 — Ctrl+key / Alt+key combos broken under modifyOtherKeys level 2. |
| `test_multiplex_cli_cache_scope.py` | Multiplexed gateway: hermes_cli's process-wide caches must not hand profile A's value to profile B. |
| `test_multiplex_host_topology_reporting.py` | Multiplex-only reporting: one host gateway serving N profiles must be reported as such. |
| `test_native_profile_route_names.py` | Profiles NAMED like a collection route (``active``, ``import``, ``sessions``) are ordinary profiles. |
| `test_native_profile_scope_threads.py` | A secondary-profile native ticket's implicit scope must reach the audio worker thread. |
| `test_nebius_token_factory_provider.py` | Focused tests for Nebius Token Factory provider wiring. |
| `test_node_runtime_npm_resolution.py` | POSIX npm path classification: only Windows shims are refused (#112041, #30271). |
| `test_non_ascii_credential.py` | Tests for non-ASCII credential detection and sanitization. |
| `test_noninteractive_config_guard.py` | Regression coverage for fail-closed non-interactive config startup. |
| `test_noninteractive_git.py` | Non-interactive internal git invocations (port of openai/codex#34540/#34612). |
| `test_normalize_main_model_assignment.py` | Regression tests for ``_normalize_main_model_assignment`` (POST /api/model/set). |
| `test_nous_account.py` | Tests for normalized Nous Portal account entitlement helpers. |
| `test_nous_anthropic_wire_default.py` | ``nous.anthropic_wire`` selects the Portal route for ``anthropic/*``: ``chat`` (default) rides /v1/chat/completions, ``native`` rides /v1/messages. Read through the real config loader against a temp HERMES_HOME (the loa… |
| `test_nous_auth_keepalive.py` | Tests: `test_refresh_always_fires_before_expiry_for_observed_lifetimes`, `test_interval_precedence_and_disable`, `test_keepalive_refreshes_stale_pool_entry`, `test_keepalive_falls_back_to_singleton_state`, `test_keepali… |
| `test_nous_auth_status_cache.py` | Tests for the get_nous_auth_status() process-level cache. |
| `test_nous_billing_request.py` | Tests for the hermes_cli.nous_billing HTTP client's response handling. |
| `test_nous_hermes_non_agentic.py` | Tests for the Nous-Hermes-3/4 non-agentic warning detector. |
| `test_nous_inference_url_validation.py` | Regression tests for Nous Portal inference_base_url host-allowlist validation. |
| `test_nous_nonproduction_inference_host.py` | Operator authority over Nous routing overrides and Portal-returned inference hosts. |
| `test_nous_picker_cached_only_key.py` | The GUI/in-chat picker's on-sale union reads what the prewarm actually cached. |
| `test_nous_picker_on_sale.py` | Paid-tier Nous pickers surface every model the gateway is discounting, not only curated ones. |
| `test_nous_picker_pricing_cached_only.py` | The Nous picker row never starts a pricing fetch: the picker only uses the ids the Portal unions append, and a cold pricing cache must not hold the picker open (salvage of #102099). |
| `test_nous_policy_filter.py` | Narrowing the Nous model lists to an org's policy. |
| `test_nous_policy_surfaces.py` | Every Nous model list is narrowed to the org's policy before it is shown. |
| `test_nous_portal_staging_allowlist.py` | Regression tests for the Nous Portal env-override bypassing the host allowlist, mirroring the existing NOUS_INFERENCE_BASE_URL / _ALLOWED_NOUS_INFERENCE_HOSTS treatment. |
| `test_nous_reasoning_metadata.py` | Tests for Nous Portal reasoning-capability metadata. |
| `test_nous_recommendation_disk_cache.py` | Recommendation requests reuse disk entries and negotiate gzip across real processes. |
| `test_nous_recommendation_mirror.py` | Nous recommendations come from each Portal's static mirror (the Portal itself when the mirror has no copy or stalls), and the gateway's background refresh fetches them only for a profile with a Nous account. |
| `test_nous_session_validity.py` | Tests for the local-only Nous session classifier exposed on /api/status. |
| `test_nous_subscription.py` | Tests for Nous subscription feature detection. |
| `test_npm_engine.py` | The frozen npm retry import hands off, never provisioning in the old parent. |
| `test_oauth_status_pool_observation.py` | A status snapshot observes the credential pool; it never leases (refreshes / rotates) an entry. |
| `test_observational_sessiondb_modes.py` | Regression coverage for #110173: observational `hermes sessions` readers stay read-only. |
| `test_official_openai_host.py` | Security + parity contract for ``is_official_openai_host``. |
| `test_old_updater_additional_shims.py` | Retired import names hand off old updater work without claiming success. |
| `test_old_updater_main_shims.py` | Historical main imports must not restart pre-PM updater work after a swap. |
| `test_old_updater_shims.py` | The post-swap import boundary must never revive retired installers. |
| `test_old_updater_takeover.py` | Historical frames stay old; completion runs once in a clean child. |
| `test_ollama_cloud_auth.py` | Tests for Ollama Cloud authentication and /model switch fixes. |
| `test_ollama_cloud_provider.py` | Tests for Ollama Cloud provider integration. |
| `test_onboarding_due.py` | The boot-time onboarding due answer (``hermes_cli.onboarding_due``): a reader during the boot computation waits for it, and a writer that moves the answer mid-computation is never lost. |
| `test_onboarding_run.py` | ``onboarding.run`` lives in the root profile's config.yaml: unset runs onboarding only on a machine that never used Hermes, an explicit bool wins, and a backend launched under a named profile reads and writes the same r… |
| `test_oneshot_exit_contract.py` | ``hermes -z`` exit-code contract: the outcome is judged from the turn result, not from whether any text was printed (#111770 — an incomplete or failed run that left an explanation on stdout used to exit 0, so scripts tr… |
| `test_oneshot_fallback.py` | #81209: ``hermes -z`` must consult the fallback chain at *resolution* time. |
| `test_oneshot_resume.py` | Tests for `hermes -z --resume <session>` (#105892). |
| `test_oneshot_resumed_session_persist.py` | Regression tests for #88583 — one-shot resumed-session turns must persist. |
| `test_oneshot_skills.py` | Regression tests: -z/--oneshot must honor -s/--skills (#31548, #65119). |
| `test_oneshot_streamed_live.py` | `hermes -z` against a real gateway with streaming on: the one-shot prints the reply (#139666). |
| `test_oneshot_surrogate.py` | Oneshot stdout must survive lone UTF-16 surrogates in model text (#80366). |
| `test_oneshot_usage_file.py` | Tests for hermes -z --usage-file (per-run JSON usage report). |
| `test_openai_codex_model_validation_fallback.py` | Regression tests for OpenAI Codex model validation when the listing lags behind actually usable backend model IDs. |
| `test_openai_discovery_endpoint.py` | Discovery honors ``model.base_url`` and cache identity tracks the endpoint. |
| `test_openai_listing_authority.py` | Live-listing authority on official OpenAI hosts (model switching). |
| `test_openai_picker_curated.py` | Regression tests for two OpenAI/OpenRouter model-picker bugs. |
| `test_opencode_go_flat_namespace.py` | Tests for opencode-go / opencode-zen flat-namespace model handling. |
| `test_opencode_go_in_model_list.py` | Test that opencode-go appears in /model list when credentials are set. |
| `test_opencode_go_validation_fallback.py` | Tests for the static-catalog fallback in validate_requested_model. |
| `test_opencode_zen_model_limit.py` | Regression tests for OpenCode Zen model picker limits. |
| `test_openrouter_preset_validation.py` | Regression coverage for OpenRouter preset references (issue #31739). |
| `test_openrouter_reasoning_metadata.py` | Tests for OpenRouter reasoning-capability metadata (prime-agent#1258 port). |
| `test_orphan_desktop_serve_reap.py` | Orphan Desktop-local ``hermes serve`` reap at backend start. |
| `test_overlay_slug_resolution.py` | Test that overlay providers with mismatched models.dev keys resolve correctly. |
| `test_pairing.py` | Tests: `test_cli_listed_request_id_and_bot_code_can_be_approved` |
| `test_parser_help_home.py` | The top-level parser's help text must not trip the wrong-profile fallback warning. |
| `test_partial_compress.py` | Tests for hermes_cli.partial_compress — the pure split/parse helpers behind ``/compress here [N]`` (boundary-aware "summarize up to here"). |
| `test_passive_update_opt_out.py` | Passive opt-out keeps explicit update checks available. |
| `test_path_completion.py` | Tests for file path autocomplete in the CLI completer. |
| `test_peer_cmd.py` | Tests for ``hermes peer`` — cross-machine bot-to-bot DMs. |
| `test_peer_dm_reporting.py` | What ``hermes peer dm`` tells the sender when the turn does not come back. |
| `test_pending_supervisor_recovery.py` | A pending restart is discharged by supervisor evidence, not an empty PID scan. |
| `test_personality_none.py` | Tests for /personality none — clearing personality overlay. |
| `test_personality_single_owner.py` | Tests for hermes_cli.personality — the single owner of personality state — and the v34 one-time personality reset migration. |
| `test_pet_toggle.py` | Tests for pet slash-command config helpers. |
| `test_picker_key_cmd_discovery.py` | Command-auth discovery is lazy, credential-scoped, and never persists bearers. |
| `test_picker_prewarm.py` | Tests for the /model picker background cache prewarm. |
| `test_picker_probe_budget_decoupling.py` | Regression test for the probe-budget decoupling on #103843. |
| `test_pin_kanban_board_env.py` | Tests for `_pin_kanban_board_env` helper invoked by `cmd_chat`. |
| `test_pip_install_detection.py` | Tests: `test_code_scoped_stamp_wins_over_home_stamp`, `test_container_without_stamp_is_not_docker` |
| `test_plain_login_settle.py` | Every plain device login that saves a Nous account over the free tier settles the config itself. |
| `test_plan_reconciliation_windows_live.py` | LIVE Windows E2E for plan-reconciliation (#92902) on windows-latest. |
| `test_platform_actions.py` | Tests for the capability-gated platform action facade (#64176, action half). |
| `test_platform_plugin_env_injection.py` | User-installed platform plugins feed OPTIONAL_ENV_VARS like bundled ones (#46600, redo of #46964). |
| `test_plugin_api_compat.py` | Behavior-contract compatibility tests for native Hermes plugins. |
| `test_plugin_api_consent_gate.py` | The runtime plugin gate holds on every transport and for every profile a multiplexed daemon serves. |
| `test_plugin_api_hot_mount.py` | A plugin installed and enabled after the web server imported must serve its backend API on the first request — no restart — and stop serving once disabled. |
| `test_plugin_ask_choice.py` | A plugin slash command asks the classic CLI's user to pick an option (``ctx.ask_choice``) with the CLI's own clarify panel, and gets the picked choice's value back: |
| `test_plugin_aux_tasks_dashboard.py` | Plugin-registered auxiliary tasks reach the dashboard/Desktop Models settings. |
| `test_plugin_auxiliary_tasks.py` | Plugin-registered auxiliary tasks merge into the built-in task list and ``_reset_aux_to_auto``. |
| `test_plugin_call_mcp.py` | Tests for the capability-gated ``ctx.call_mcp`` plugin surface (#64204). |
| `test_plugin_capabilities.py` | Tests for the plugin capability model + consent flow (#64228). |
| `test_plugin_catalog.py` | Plugin catalog contracts (hermes_cli/plugin_catalog.py): the in-tree seed is valid, bad entries are skipped not raised, kill-list matching is name-or-repo, and the live catalog degrades to in-tree. |
| `test_plugin_catalog_known_issues.py` | #124058: catalog ``known_issues`` is an informational field. |
| `test_plugin_catalog_presence.py` | The onboarding card's catalog plugins: curated flag, platform filter, and the pinned app declaration. |
| `test_plugin_cli_registration.py` | Memory plugin CLI discovery: only the active provider's ``cli.py`` commands are exposed. |
| `test_plugin_command_source.py` | Plugin slash-command handlers receive only the calling-session context they declare. |
| `test_plugin_config_state_bridge.py` | End-to-end coverage for the profile-scoped plugin config/state bridge (#64227). |
| `test_plugin_dependency_consent.py` | Only declared Python dependencies require Python install consent. |
| `test_plugin_dependency_restart.py` | A plugin whose Python dependencies were installed after a process booted needs a restart there. |
| `test_plugin_dev.py` | Tests: `test_doctor_uses_registration_to_reject_bad_hook_and_callback_signature`, `test_doctor_accepts_manifest_defaults_from_runtime_parser`, `test_doctor_restores_global_tool_policy_and_module_state`, `test_doctor_blo… |
| `test_plugin_doctor_desktop_copy.py` | ``hermes plugins doctor`` warns when Desktop runs a stale copy of a unified package's desktop half. |
| `test_plugin_doctor_unload.py` | `plugins doctor` must unload the plugin before removing the temp home (#99918). |
| `test_plugin_event_bus.py` | Tests for the inter-plugin event bus (PluginContext.emit / subscribe). |
| `test_plugin_events.py` | Public event bridge for plugin backends (#116305 item 8, salvage of #116419). |
| `test_plugin_historic_compat.py` | Shipped plugin callers keep their contract without owning PM publication. |
| `test_plugin_hold_stream.py` | ``register_hook("transform_llm_output", fn, hold_stream=True)``: the declaration and its scope. |
| `test_plugin_hook_failure_reporting.py` | A plugin hook that fails identically on every call is reported once, not once per call. |
| `test_plugin_host.py` | plugins.isolation: host — third-party plugins run in a per-profile host process, reached only via ctx. |
| `test_plugin_host_delegation.py` | plugins.isolation: host — a delegation provider plugin runs out of process and still routes tasks. |
| `test_plugin_host_mixed_profiles.py` | plugins.isolation: host — a profile that cannot cross the host boundary never takes its siblings down. |
| `test_plugin_host_profiles_launch_dir.py` | Plugin-host profile extraction runs the Hermes tree's code, never a same-named package in the cwd. |
| `test_plugin_host_return_types.py` | plugins.isolation: host — values a hosted provider returns reach core as the types its ABC promises. |
| `test_plugin_host_route_auth.py` | Regression for #140499: upstream admission survives credential-free hosting. |
| `test_plugin_host_seeded_credentials.py` | plugins.isolation: host — a hosted provider that seeds its own pool rows gets plain data and the ambient token it declares, exactly as it would in-process. |
| `test_plugin_install_inspected_sha.py` | An install dialog's ``plugins.manage install`` is held to the commit its ``inspect`` read. |
| `test_plugin_install_inspected_sha_catalog.py` | A catalog install dialog's ``plugins.manage install`` is held to the commit its ``inspect`` read. |
| `test_plugin_install_manifest_version.py` | Installer accepts every manifest_version the runtime loader supports (#85879). |
| `test_plugin_install_prompt_activation.py` | Enabling a plugin at the install prompt loads it where it can go live, like ``--enable`` does. |
| `test_plugin_install_records_concurrent.py` | Plugins installed a second apart both keep their install record. |
| `test_plugin_install_ref.py` | Exact-commit plugin installation and source metadata. |
| `test_plugin_loader_module_eviction.py` | Regression: ``_evict_modules`` must survive concurrent mutation of ``sys.modules``. |
| `test_plugin_manifest_v2.py` | Tests for plugin manifest v2 (#64165). |
| `test_plugin_message_injection.py` | Tests for plugin message injection across CLI and gateway hosts. |
| `test_plugin_module_eviction_race.py` | A module mapping that grows while ``_evict_modules`` walks it must not fail the eviction (refs #139134). |
| `test_plugin_native_ws_scope.py` | A Desktop plugin socket's native grant decides its consent and its scope before plugin code (PLG-1). |
| `test_plugin_oauth.py` | Plugin-declared OAuth clients: Hermes signs in, stores and refreshes the grant; plugin code never holds a token. |
| `test_plugin_ownership_ledger.py` | End-to-end coverage for plugin registration ownership and reload cleanup. |
| `test_plugin_packs.py` | Plugin packs (#64166): parse/validate, SHA enforcement, install fan-out, export round-trip, consent-not-bypassed, partial-failure exit codes. |
| `test_plugin_platform_toolset_rows.py` | ``platform_toolsets`` rows for plugin platforms (teams, google_chat, homeassistant) that the installers seeded from cli-config.yaml.example: inert until the plugin loads, so they must not log the #38798 "no valid toolse… |
| `test_plugin_presence_by_name.py` | ``presence_for(names)``: catalog plugins by name for the desktop questionnaire — unknown and removed names dropped, other-OS entries dropped, order kept, manifests read in parallel, ``unknown`` when the pinned manifest… |
| `test_plugin_private_repo_auth.py` | Private-repo plugin installs attach the user's stored HTTPS credential to git without persisting it. |
| `test_plugin_prompt_sections.py` | Tests: `_context`, `test_registration_validates_stable_id_position_budget_and_duplicates`, `test_render_is_deterministic_bounded_and_session_info_is_read_only`, `test_render_fails_open_for_callback_failure_wrong_type_an… |
| `test_plugin_provider_picker_admission.py` | Picker admission for out-of-tree provider plugins with non-api-key auth types. |
| `test_plugin_provider_picker_residue.py` | An admitted plugin provider is selectable and status-accurate on every surface (#116408). |
| `test_plugin_provider_requests.py` | Core makes Codex-signed requests for plugins; the token never reaches plugin code. |
| `test_plugin_runtime_disable_gate.py` | Regression tests for runtime plugin disable gating. |
| `test_plugin_scan_dunder_dirs.py` | Plugin directory scans must skip dunder dirs and survive OSError (#86996). |
| `test_plugin_scanner_recursion.py` | Tests for PR1 pluggable image gen: scanner recursion, kinds, path keys. |
| `test_plugin_secondary_profile_host.py` | PLG-3: a secondary served profile's dashboard plugins run in that profile's own plugin host. |
| `test_plugin_surface_desktop.py` | A re-pin that adds a desktop half is a widened surface whichever layout the half uses. |
| `test_plugin_uninstall_windows_live.py` | LIVE Windows E2E: ``hermes plugins uninstall`` while a real gateway has the plugin loaded. |
| `test_plugin_update_recovery.py` | Process death cannot leave new plugin code paired with the old dependency selection. |
| `test_plugin_update_scan_override.py` | Updating a git-installed plugin scans the new code on every surface, and a caution verdict can be overridden: ``hermes plugins update NAME`` asks ``Update anyway? [y/N]`` (``--force`` skips the question), and Desktop/da… |
| `test_plugin_update_transaction.py` | Catalog pins and custom Git updates publish only a validated dependency set. |
| `test_plugin_validate.py` | Tests for ``hermes plugins validate`` (hermes_cli/plugin_validate.py). |
| `test_plugin_validate_locales.py` | ``hermes plugins validate`` on language packs: bad keys WARN by name, non-text leaves fail, a manifest-only pack is loadable, a declared id with no file fails. |
| `test_plugin_validate_private_imports.py` | ``hermes plugins validate`` warns (never fails) on imports of private Hermes core modules. |
| `test_plugin_version_order.py` | Plugin update consumers share strict version ordering and unknown results. |
| `test_plugin_worker_lifecycle.py` | Command → real PM worker → offline wheels → persisted state → fresh imports. |
| `test_plugins.py` | Tests for the Hermes plugin system (hermes_cli.plugins). |
| `test_plugins_admission_setter.py` | Publication failures through the command and real worker, not a fake sync. |
| `test_plugins_cadence.py` | Tests: the plugin update-check cadence — clock-gated, receipt-surfaced, apply-explicit. All seams injected; hermetic. |
| `test_plugins_catalog_requires_hermes.py` | The catalog entry's ``requires_hermes`` is enforced, not just displayed: an install by catalog name refuses on a Hermes the spec rejects (CLI, dashboard/Desktop, TUI RPC and the left-core auto-install all go through one… |
| `test_plugins_check_updates.py` | Tests: check-updates — address resolution, saved-tag security, feeds. |
| `test_plugins_cmd.py` | Tests for hermes_cli.plugins_cmd — the ``hermes plugins`` CLI subcommand. |
| `test_plugins_cmd_activation_keys.py` | Plugin activation writes and reads the SAME key on every surface (#27548, #73131, #82898). |
| `test_plugins_cmd_catalog.py` | Catalog-aware ``hermes plugins`` surface (hermes_cli/plugins_cmd_catalog.py): a bare catalog name installs the PINNED sha and records provenance; the kill list blocks every install path (CLI needs an explicit bypass, da… |
| `test_plugins_cmd_category_discovery.py` | Tests for the nested category plugin discovery fix (issue #41066). |
| `test_plugins_cmd_enable_disable_nested.py` | Canonical keys and privilege consent through real admission. |
| `test_plugins_cmd_inspect.py` | ``plugins_cmd_inspect.inspect_plugin_source``: the install dialog's read-only repository check. |
| `test_plugins_cmd_list.py` | Tests: `_args`, `test_filter_plugin_entries_enabled_only`, `test_cmd_list_plain_compact_output`, `test_discover_all_plugins_includes_entrypoint_plugins`, `test_declared_capabilities_for_entrypoint_uses_distribution_meta… |
| `test_plugins_cmd_remove_bookkeeping.py` | ``plugins remove`` (CLI, dashboard, ``plugins.manage`` RPC) leaves no config residue and never follows a symlink (#54336, plugin-scan L2-F1/F2/F5). |
| `test_plugins_disable_reaches_gateway.py` | ``hermes plugins disable`` must reach the running gateway, or say a restart is needed (LC-3). |
| `test_plugins_hub_live_catalog.py` | Live plugin-catalog lookups must not multiply per installed plugin. |
| `test_plugins_hub_perf_guard.py` | Tests: `_patch_minimal_hub_dependencies`, `test_plugins_hub_does_not_probe_cold_check_fns`, `test_plugins_hub_cold_cache_schedules_background_probe`, `test_plugins_hub_uses_cached_failed_check_fn_verdict`, `test_plugins… |
| `test_plugins_live_notice.py` | ``live_notice``: what an open chat is told when a plugin goes live in it. |
| `test_plugins_loader.py` | Tests: `test_nested_plugin_load_runs_inline_on_deadline_worker` |
| `test_plugins_middleware_chain.py` | Request middleware chaining (#128638): rewrites compose in registration order. |
| `test_plugins_picker_effective_state.py` | The bare ``hermes plugins`` picker writes only the rows the user flipped. |
| `test_plugins_provenance.py` | Tests: plugin provenance reconciliation — the 2x2. |
| `test_plugins_transcription_registration.py` | Tests for PluginContext.register_transcription_provider(). |
| `test_plugins_tts_registration.py` | Tests for PluginContext.register_tts_provider() (issue #30398). |
| `test_plugins_update_all.py` | `hermes plugins update` with no name: offer every plugin that has an update, never move one silently. |
| `test_plugins_update_sync.py` | Every update surface validates staged code before changing an active plugin. |
| `test_pool_missing_endpoint.py` | Endpoint-less manual credentials resolve through the public runtime ladder. |
| `test_pooled_served_profile_backend_unscoped.py` | A pooled Desktop backend (``hermes --profile X serve``, HERMES_HOME=<root>/profiles/X) answers its REST without ``?profile=``. Those UNSCOPED reads/verbs are about X — a profile the live default multiplexer serves — and… |
| `test_portable_skill_name_clashes.py` | Portable plugins whose names slug to the same skill prefix (``foo.bar`` and ``foo-bar``). |
| `test_post_setup_gating.py` | Tests for the post_setup install-state gate in `_toolset_needs_configuration_prompt`. |
| `test_post_update.py` | post_update step registry: scopes, isolation, and the migrate contract. |
| `test_post_update_adoption.py` | step_adopt_blessed_checkout — one-time birth certificate for shipped stampless installs. |
| `test_post_update_expose_cli.py` | expose_cli — the launcher owner repairs PATH conveniences. |
| `test_pre_command_hook.py` | Tests for the ``pre_command`` observer hook (#64204). |
| `test_prefill_config.py` | Regression tests for CLI prefill config key compatibility. |
| `test_prepend_note_to_message.py` | Tests for cli._prepend_note_to_message. |
| `test_pricing_cache_auth_key.py` | ``_pricing_cache`` keys on the credential, not just the base URL. |
| `test_process_dock.py` | Background processes share the classic CLI live-work dock with subagents (Processes block). |
| `test_process_identity.py` | Tests for hermes_cli.process_identity — spawn tags, the machine spawn ledger, and the updater's ledger-identified reap rung. |
| `test_process_identity_canonical_matchers.py` | Process-identity contract: the two kill/relaunch predicates and the profile liveness probe defer to the canonical matchers instead of argv substrings (root AGENTS.md process-identity rule). |
| `test_process_notification_display.py` | Background-process completions paint a compact title while the model keeps the raw wall. |
| `test_profile_alias_orphan_removal.py` | `hermes profile alias <name> --remove` must clean up an ORPHAN alias (#90983). |
| `test_profile_cleanup_foreign_unit.py` | `hermes profile delete\|rename` never removes another install's gateway service. |
| `test_profile_clone_channels.py` | ``hermes profile create --clone`` leaves messaging channels behind (``hermes_cli.profile_channels``). |
| `test_profile_credential_collisions.py` | Regression for #118388: a platform singleton secret (``TELEGRAM_BOT_TOKEN``) duplicated across local profile homes was invisible to ``hermes doctor`` / ``hermes gateway status``; the only signal was the losing standalon… |
| `test_profile_delete_held_lock.py` | A profile delete (or multiplexed rename) never removes/moves a home whose gateway.lock a live runtime still holds (N60). |
| `test_profile_delete_log_handlers.py` | Profile deletion must release the profile-routed log handlers this process holds (#112538). |
| `test_profile_delete_mcp_log.py` | Profile deletion after a real stdio MCP probe must release its log file. |
| `test_profile_delete_read_only_copy.py` | A read-only profile copy (0555 dirs, 0444 files) can still be deleted (N106): the owner check cannot reserve gateway.lock there, so it proves the lock unheld through a read-only flock. |
| `test_profile_delete_service_name.py` | Deleting a profile from a multiplexed process removes THAT profile's service, never the host's. |
| `test_profile_delete_wrapper.py` | `hermes profile delete` removes the profile's wrapper (#131753). |
| `test_profile_describer.py` | Tests for the profile.yaml metadata layer (description + description_auto) and the profile_describer LLM module. |
| `test_profile_display_name.py` | Profile display_name (#45624): presentation-only label in profile.yaml. |
| `test_profile_distribution.py` | Tests for hermes_cli.profile_distribution — git-based profile installs. |
| `test_profile_export_credentials.py` | Tests for credential exclusion + secret scrubbing during profile export. |
| `test_profile_export_default_path.py` | Regression coverage for safe automatic profile-export destinations. |
| `test_profile_export_special_files.py` | Tests for special-file handling during profile export. |
| `test_profile_identity_purge_cmd.py` | The `hermes profile purge-identity` retry path: dispatched, and honest about failure. |
| `test_profile_install_env_encoding.py` | Regression: the distribution-install preview must read .env as UTF-8. |
| `test_profile_listing_cache.py` | ``list_profiles`` re-reads a profile's YAML only when that file has changed. |
| `test_profile_memory_config.py` | cloned_memory_provider: a best-effort post-clone notice that never fails ``hermes profile create``. |
| `test_profile_model_id_seam.py` | ``ProviderProfile.normalize_model_id``: a profile that owns its id space repairs ids before the generic rules. |
| `test_profile_model_seed.py` | Fresh profiles retain the selected custom endpoint, without copying its neighbors. |
| `test_profile_pm_portability.py` | Portable transfers keep user files, not machine-specific PM state. |
| `test_profile_rename_checkpoints.py` | Profile rename must preserve profile-local checkpoint history (#112973). |
| `test_profile_rename_service.py` | Renaming a profile removes the gateway service registered under its old name. |
| `test_profile_service_cleanup_scopes.py` | Deleting or renaming a profile removes its system-scope systemd unit and Windows Scheduled Task, not only the user unit / launchd plist. Both carry ``--profile <old>`` with HERMES_HOME pinned to a dir that no longer exi… |
| `test_profile_setup_login_seams.py` | Provider-profile setup/sign-in seams (``providers.base`` L6 block) through the real routes. |
| `test_profiles.py` | Comprehensive tests for hermes_cli.profiles module. |
| `test_profiles_alias_names.py` | ``hermes profile`` alias names: profiles named like Hermes' server subcommands keep their alias. |
| `test_profiles_s6_hooks.py` | Tests for the Phase 4 s6 hooks in hermes_cli.profiles. |
| `test_profiles_session_archived_pages.py` | Archived profile pages count archived rows even when live pins back-fill. |
| `test_profiles_sidebar_cache.py` | Regression tests for dashboard sidebar scan coalescing. |
| `test_profiles_sidebar_failed_load.py` | A failed profile scan must not look like an empty session list. |
| `test_profiles_sidebar_scope.py` | The sidebar's profile scope, across both endpoints that serve it. |
| `test_project_plugin_rce_bypass.py` | Regression coverage for GHSA-5qr3-c538-wm9j (#29156) — Remote Code Execution via the ``HERMES_ENABLE_PROJECT_PLUGINS`` bypass in the web server's dashboard plugin loader. |
| `test_projects_cli.py` | Tests for the `hermes project` CLI dispatch (hermes_cli/projects_cmd). |
| `test_projects_db.py` | Tests for the per-profile Projects store (hermes_cli/projects_db). |
| `test_prompt_api_key.py` | Tests for ``_prompt_api_key`` — the shared Keep/Replace/Clear menu used by ``hermes setup`` / ``hermes model`` when an API key already exists in ``.env``. |
| `test_prompt_compose_command.py` | Tests for the CLI `/prompt` editor-compose command. |
| `test_prompt_size.py` | Tests for the ``hermes prompt-size`` diagnostic (issue #34667). |
| `test_prompt_stash.py` | Tests for the Ctrl+S prompt stash state machine (hermes_cli.prompt_stash). |
| `test_prompt_stash_cli.py` | Tests for the Ctrl+S prompt stash wiring inside HermesCLI. |
| `test_prompt_text_input_thread_safety.py` | Tests for ``HermesCLI._prompt_text_input`` thread-safe input dispatch. |
| `test_prompt_turn_ack_order.py` | /plan, /learn, /init acknowledge on the same paint channel as the turn they queue. |
| `test_provider_auth_seam.py` | OAuth-shaped model-provider plugins are first-class in `hermes auth` (#116408). |
| `test_provider_catalog.py` | Tests for the unified provider catalog (hermes_cli.provider_catalog). |
| `test_provider_catalog_hooks.py` | Provider-owned catalog seams, exercised through a fake non-Copilot profile: a profile's ``picker_catalog`` / ``static_models`` / ``probe_models`` / ``invalidate_catalog_cache`` / ``catalog_credential_files`` drive core'… |
| `test_provider_config_validation.py` | Tests for providers config entry validation and normalization. |
| `test_provider_groups.py` | Tests for provider-group folding (display-only picker grouping). |
| `test_provider_live_curated_merge.py` | Tests for live+curated merge in the generic profile-based provider path. |
| `test_provider_normalize_cost.py` | ``normalize_provider`` answers built-in ids without reading the provider-profile list (R4 H3). |
| `test_provider_parity.py` | End-to-end provider parity contract: the desktop Providers tabs must show the SAME provider universe as ``hermes model`` (the CLI/TUI picker). |
| `test_provider_plugin_alias_identity.py` | A provider plugin's alias names the same provider whether or not models.dev is reachable. |
| `test_provider_precedence.py` | Regression tests for #29285 — provider precedence in resolve_provider("auto"). |
| `test_provider_profile_identity.py` | Plugin ProviderProfiles resolve wherever a provider NAME is resolved at switch time (#69576). |
| `test_provider_registry_override.py` | A `$HERMES_HOME` provider plugin re-registering a bundled name reaches the runtime (#48450). |
| `test_provider_section3_grouping.py` | Regression tests for section-3 (``providers:``) same-endpoint grouping in ``list_authenticated_providers`` and for ``format_model_for_display``. |
| `test_provider_table_placement.py` | Plugin profiles place themselves in the core provider tables through generic fields. |
| `test_proxy.py` | Tests for the `hermes proxy` subcommand and its upstream adapters. |
| `test_proxy_off_loop.py` | `hermes proxy` must resolve upstream credentials off the event loop. |
| `test_prune_advisor.py` | Low-disk auto-prune prompt: asks only while undecided, says when pruning will not help. |
| `test_prune_spares_pinned.py` | Regression tests: pinned sessions survive bulk prune/archive (round-3 SES-01). |
| `test_pty_bridge.py` | Unit tests for hermes_cli.pty_bridge — PTY spawning + byte forwarding. |
| `test_pty_keepalive_ws.py` | Tests: `FakeBridge`, `pty_keepalive_harness`, `test_attach_token_reuses_same_session`, `test_stalled_input_closes_only_the_keepalive_socket`, `test_chat_without_a_pty_bridge_says_what_to_install_as_on_main`, `test_a_tak… |
| `test_pty_session.py` | Tests: `test_ringbuffer_keeps_everything_under_capacity`, `test_ringbuffer_drops_oldest_over_capacity`, `FakeBridge`, `FakeWS`, `FailingWS`, `test_attach_replays_buffer_then_streams_live` … |
| `test_pty_session_close_reason.py` | 4410 also ends a shell the server closed (expiry, a deleted profile, shutdown). Only a shell that exited by itself says so in the close reason, so a viewer can end its tab the way native Desktop does when its shell exit… |
| `test_pty_session_continuity.py` | Ownership, replay ordering, and spawn reservation contracts for PTY sessions. |
| `test_quarantine_forensic_logging.py` | Redaction-safe forensic logging at the Nous OAuth quarantine path. |
| `test_quarantine_orphan_rescue.py` | Regression tests: a failed quarantine restore must never strand `hermes`. |
| `test_quick_commands.py` | Tests for user-defined quick commands that bypass the agent loop. |
| `test_quiet_turn_author.py` | ``hermes chat -Q`` passes the dispatcher's HERMES_TURN_AUTHOR to ``run_conversation`` as ``turn_author``. |
| `test_read_raw_config_readonly.py` | Tests for read_raw_config_readonly() — the no-deepcopy raw config read. |
| `test_readers_concurrent_owner.py` | Real CLI readers stay usable while the canonical store has a writer. |
| `test_real_home_tripwire.py` | Real-home guards are exercised against disposable protected roots only. |
| `test_reasoning_caps_disk_cache.py` | The reasoning-capability disk mirror. |
| `test_reasoning_command.py` | Tests for the combined /reasoning command. |
| `test_reasoning_effort_menu.py` | Tests: `test_reasoning_menu_orders_minimal_before_low`, `test_current_reasoning_effort_reads_dict_form`, `test_hermes_model_offers_reasoning_whenever_a_pick_is_saved` |
| `test_reasoning_full_command.py` | Tests for the CLI `/reasoning full` / `/reasoning clamp` recap toggle. |
| `test_redact_config_bridge.py` | Regression test for config.yaml `security.redact_secrets: false` toggle. |
| `test_refresh_singleflight.py` | Native HTTP replay boundaries and deterministic provider-level concurrency. |
| `test_regression.py` | Regression coverage for issue #16767. |
| `test_relaunch.py` | Tests for hermes_cli.relaunch — unified self-relaunch utility. |
| `test_relaunch_verify_budget_starts_at_respawn.py` | The relaunch liveness budget has to start when the replacement process appears. |
| `test_relay_plugin_cutover.py` | Regression tests for migration from the removed Hermes Relay plugin. |
| `test_relay_plugin_migrate.py` | ``hermes update`` / ``hermes migrate relay``: legacy ``HERMES_NEMO_RELAY_ATIF_*``/``ATOF_*`` vars become a validated ``relay-plugins.toml`` per profile home, selected from ``.env``. |
| `test_relay_shared_metrics.py` | Focused tests for the Hermes shared-metrics durable store. |
| `test_relay_shared_metrics_runtime.py` | Tests for the direct Hermes-to-Relay shared-metrics runtime. |
| `test_release_channels.py` | Public channel resolution is strict, pinned, and independent of name registries. |
| `test_remote_spending_gate_contract.py` | Tests for the Remote-Spending gate denial contract (NAS PR #481). |
| `test_resolve_ephemeral_system_prompt.py` | Unit tests for resolve_ephemeral_system_prompt_from_config. |
| `test_resolve_last_session.py` | Verify `hermes -c` picks the session the user most recently used. |
| `test_resolve_provider_corrupt_config.py` | Regression tests for issue #81952 (silent OpenRouter paid-default class fix). |
| `test_resolve_provider_custom_endpoint.py` | A configured custom (OpenAI-compatible) endpoint is explicit provider intent. |
| `test_resolve_provider_openrouter_pool.py` | Regression tests for issue #42130. |
| `test_resolve_token_memo.py` | Tests for the resolve_nous_access_token startup-burst memo (PR #66016). |
| `test_resolve_turn_limit.py` | Tests for :func:`hermes_cli.config.resolve_turn_limit` and the ``TURN_LIMIT_UNLIMITED`` sentinel. |
| `test_resource_limits.py` | Tests for configurable RLIMIT_NOFILE startup handling. |
| `test_restart_plan_reconciliation.py` | Plan-vs-execution reconciliation (#91277 Phase 2: restart via declared mechanism). |
| `test_restore_own_holder_guard.py` | Regression tests: restore paths must fail closed under an IN-PROCESS live connection to the destination database (#90837 / #90950 own-holder gap). |
| `test_restore_source_integrity.py` | Restore must read the literal source path and validate it before mutating a live database. |
| `test_resume_alias_model.py` | Repeating the creation `-m <alias>` on resume is the same frozen route, not an override. |
| `test_resume_alias_remote_config.py` | A repeated `-m alias` on resume is judged by the owner's creation provenance, not the client's own alias map (andrexibiza C19): the owner maps `fast` to model A, the remote client's home maps it to model B; the same ali… |
| `test_resume_compressed_gateway_id.py` | Classic CLI ``--resume <root>`` of a twice-compressed local conversation addresses the gateway by the id it owns a receipt for (live-pass finding, package 10). |
| `test_resume_display.py` | Tests for session resume history display — _display_resumed_history() and _preload_resumed_session(). |
| `test_resume_latest_and_in_dir.py` | Tests for `--resume latest` and `--in DIR` launch sugar. |
| `test_resume_model_restore.py` | Tests for CLI resume model restoration and /model session persistence. |
| `test_resume_quiet_stderr.py` | Tests for /resume status lines going to stderr in quiet mode (#11793). |
| `test_retirement_atomicity.py` | Freeze admission before consulting ledgers, without holding a lock across their locks. |
| `test_review_update_runtime.py` | Source update safety at the bootstrap and completion boundaries. |
| `test_router_provider.py` | Behavior contracts for the Ramp Router (api.router.com) provider. |
| `test_runtime_api_mode_profile_default.py` | ``api_mode_for_model`` answering None keeps the profile's declared ``api_mode`` at runtime resolution (``providers/base.py`` contract), so a Responses-default provider with a few chat-only exceptions never sends its oth… |
| `test_runtime_install_progress.py` | PM download bytes and install phases remain separate, faithful UI facts. |
| `test_runtime_machine_scope.py` | The managed runtime is machine-scoped, not profile-scoped. |
| `test_runtime_maintenance_exclusion.py` | Maintenance must not replace the database behind a live authority. |
| `test_runtime_paths.py` | Payload stores follow the payload, not the launching shell's home. |
| `test_runtime_provider_late_binding.py` | Regression: runtime_provider's config helpers must be late-bound. |
| `test_runtime_provider_openai_runtime.py` | Runtime provider resolution: model.openai_runtime overlay, the ``openai`` alias, and launch keys. |
| `test_runtime_provider_qwen.py` | Tests: `test_qwen_oauth_supplied_token_keeps_the_base_url_override` |
| `test_runtime_provider_resolution.py` | Tests: `test_configured_api_key_provider_without_key_fails_closed`, `test_noauth_lmstudio_still_resolves`, `_fake_invoke_jwt`, `test_resolve_runtime_provider_uses_credential_pool`, `test_codex_pool_honors_hermes_codex_b… |
| `test_runtime_transport_precedence.py` | Runtime transport precedence: declared provider transport is the fallback. |
| `test_safe_mode.py` | `hermes chat --safe-mode` is an owner-frozen policy executed out of process, not client env. |
| `test_sale_pricing.py` | Sale UI pricing helpers: gateway pricing.original → discount chrome. |
| `test_sandbox_image_switch.py` | The default sandbox image change is a decision, not a surprise. |
| `test_save_conversation_location.py` | Tests for /save — the conversation snapshot slash command. |
| `test_save_transcript_history.py` | /save md (CLI and gateway) carries the display history; /save json (CLI, gateway, TUI/Desktop) every kept row. |
| `test_scan_venv_blockers.py` | The retired scanner's historical import and desktop CLI contracts. |
| `test_scroll_list_panel_row_layout.py` | Invariants for ``CLITuiMixin._render_scroll_list_panel`` (the ``/model`` picker's model stage and the command palette) with labels long enough to fill the panel body. |
| `test_secret_prompt.py` | Tests: `_run_collect`, `test_collect_masked_input_shows_feedback_without_echoing_secret`, `test_collect_masked_input_raises_keyboard_interrupt`, `test_masked_secret_prompt_falls_back_to_getpass_for_non_tty` |
| `test_secret_source_bootstrap.py` | Tests for plugin secret-source first-process re-pull (#64177). |
| `test_secrets_bitwarden_non_tty.py` | Regression tests for hermes secrets bitwarden setup non-TTY guard. |
| `test_secrets_token_rotation.py` | Tests for `hermes secrets bitwarden token` / `hermes secrets onepassword token`. |
| `test_security_advisories.py` | Tests for hermes_cli.security_advisories. |
| `test_security_audit.py` | Unit tests for hermes_cli.security_audit — parsers + OSV plumbing. |
| `test_security_audit_startup.py` | Tests for the startup security posture audit (hermes_cli.security_audit_startup). |
| `test_seeded_interactive_query.py` | Seeded interactive ``-q`` behavior (Aug 2026). |
| `test_send_cmd.py` | Tests for the ``hermes send`` CLI subcommand. |
| `test_serve_command.py` | Contract for the headless ``hermes serve`` backend command. |
| `test_serve_host_attach.py` | A second `hermes serve` attaches to the host backend instead of binding a second port. |
| `test_serve_mcp_discovery_after_bind.py` | Desktop `serve` starts background MCP discovery only after the socket binds; a standalone `hermes dashboard` arms it at boot and the first /api/ws client (or agent build) fires it (#58733). |
| `test_serve_parent_watchdog.py` | Regression tests for Desktop-owned ``hermes serve`` lifecycle tracking. |
| `test_serve_parent_watchdog_live_macos.py` | #95693 / #93958 — live macOS proof for the parent-death watchdog. |
| `test_serve_port_in_use.py` | #93608 — port bind conflict must be machine-readable, not a bare exit 1. |
| `test_serve_runtime_inventory.py` | Serve-kind runtime inventory (#63206, campaign #91277). |
| `test_serve_skill_maintenance.py` | Exercise the real periodic maintenance loop with isolated on-disk state. |
| `test_serve_windows_loop_factory.py` | Windows serve must run uvicorn on a SelectorEventLoop. |
| `test_served_profile_mirror_platforms.py` | A served secondary's api_server/webhook are MIRRORS of the default's listener (``/p/<profile>/...``), never adapters of their own, so the multiplexer record has no ``<profile>:api_server`` entry. Every status reader use… |
| `test_service_manager.py` | Tests for hermes_cli.service_manager — the abstract ServiceManager protocol, the detect_service_manager() entry point, and the host-side adapter wrappers (Systemd / Launchd / Windows). |
| `test_session_boundary_hooks.py` | Tests: `test_session_finalize_on_reset`, `test_session_finalize_on_cleanup`, `test_interrupted_session_end_helper_emits_observer_shape`, `test_hook_errors_are_caught` |
| `test_session_browse.py` | Tests for the interactive session browser (`hermes sessions browse`). |
| `test_session_detail_malformed_db.py` | A corrupt state.db must not be reported as a missing session. |
| `test_session_dock.py` | Active /goal and queued /queue prompts share the classic CLI live-work dock. |
| `test_session_end_messages.py` | Plugin ``on_session_finalize`` return values reach the user out-of-band on every surface. |
| `test_session_export.py` | Tests: `_sample_session`, `test_html_export_escapes_tool_call_names`, `test_export_record_count_switches_unit_for_prompt_only_exports`, `test_sessions_export_cli_prompt_only_stdout` |
| `test_session_export_batch.py` | Tests: `test_export_all_batches_message_reads_without_changing_export_rows` |
| `test_session_export_html.py` | Tests for the HTML session export renderer. |
| `test_session_export_html_escape.py` | Tests: `test_role_is_escaped_in_html_export` |
| `test_session_export_md.py` | Tests: `_session`, `test_safe_session_filename_is_deterministic_and_path_safe`, `test_verify_export_file_checks_count_and_sha` |
| `test_session_filters.py` | Tests for hermes_cli.session_filters — CLI time/filter parsing for `hermes sessions prune` / `hermes sessions archive`. |
| `test_session_handoff.py` | Tests for session handoff (CLI to gateway platform). |
| `test_session_list_reader_disposable.py` | Read-only session-list opens must stay disposable. |
| `test_session_listing.py` | Tests for the shared session-listing helpers (hermes_cli/session_listing.py). |
| `test_session_maintenance_http.py` | Legacy bulk maintenance must exclude the real gateway owner reservation. |
| `test_session_message_page_owner.py` | Tests: `test_message_pages_identify_the_serving_profile`, `test_message_pages_type_untyped_failed_turn_rows` |
| `test_session_messages_inline_images.py` | ``GET /api/sessions/{id}/messages`` honors ``inline_images=false`` (#116511). |
| `test_session_mutation_http.py` | Real HTTP and WS clients share the owner revision and retry receipt. |
| `test_session_mutation_legacy_client.py` | A pre-fence client (Desktop 0.22.2) gets a named upgrade refusal it can render (#139742). |
| `test_session_mutation_models.py` | Mutation identities and boolean intent must survive HTTP parsing unchanged. |
| `test_session_mutation_snapshot.py` | HTTP mutation preparation reads the owner's exact persisted counters. |
| `test_session_mutation_standalone.py` | Standalone ``hermes serve``/``dashboard`` (no gateway authority) keeps session edits. |
| `test_session_owner_backfill.py` | Legacy NULL-profile session owner backfill (#94724). |
| `test_session_recap.py` | Unit tests for hermes_cli.session_recap. |
| `test_session_recovery.py` | Tests: `_sha256`, `_make_source`, `_orphan_fts_schema`, `_make_page_spanning_source`, `_make_many_sessions_source`, `_btree_leaf_pages` … |
| `test_session_recovery_lost_and_found.py` | Tests for recovery-tooling gaps: issue #80205 (range-query budget can omit a recoverable tail row) and the lost_and_found last-resort lane for sources whose table schemas are unreadable. |
| `test_session_recovery_model_config.py` | Invariant: session recovery neutralises unparseable ``sessions.model_config``. |
| `test_session_recovery_timestamps.py` | Invariant: session recovery never ships an out-of-window timestamp cell (#91536). |
| `test_session_save.py` | Tests for the /save current-session export helpers. |
| `test_session_schema_history.py` | ``hermes_cli.session_schema_history`` must track SCHEMA_SQL. |
| `test_session_search_context_batch.py` | Batched context preserves neighboring rows and projection fast paths. |
| `test_session_skill_previews.py` | Session previews must never surface a /skill's own body. |
| `test_session_switch_mid_turn_guard.py` | /branch, /resume and /sessions <id> refuse to switch sessions while a turn is in flight. |
| `test_session_system_prompt_dedup.py` | Behavior coverage for content-addressed session system prompts. |
| `test_session_timeline.py` | Real read-only timeline requests against temporary profile stores. |
| `test_session_vacuum_config.py` | Tests: `test_explicit_auto_prune_false_is_respected`, `test_negative_retention_days_in_config_deletes_nothing`, `test_cli_auto_maintenance_forwards_vacuum_interval` |
| `test_sessions_adopt.py` | `hermes sessions adopt` brings a profile's pre-gateway chats under its gateway, as the host. |
| `test_sessions_delete.py` | Tests: `test_sessions_delete_accepts_unique_id_prefix`, `test_sessions_delete_with_unfinished_turn_points_to_discard`, `_run_prune`, `test_sessions_prune_bare_keeps_90_day_default`, `test_archive_include_open_flag_reach… |
| `test_sessions_discard.py` | `hermes sessions discard`: a script can clear a turn lost in a gateway crash without a REPL. |
| `test_sessions_error_exit_codes.py` | Regression tests: `hermes sessions` error paths return non-zero (SES-04). |
| `test_sessions_export_backup_round_trip.py` | `hermes sessions export` JSONL — the documented backup format — must round-trip a compacted session: import restores the turns in-place compaction archived, still archived (#122679 fixed only the console export; the pri… |
| `test_sessions_export_md_cli.py` | Tests: `test_sessions_export_md_writes_single_session`, `test_sessions_export_verified_delete_keeps_file`, `test_sessions_export_redact_scrubs_secrets` |
| `test_sessions_export_output_dir.py` | `hermes sessions export` single-file formats accept a directory as OUTPUT. |
| `test_sessions_export_retention.py` | Regression for #131075: a retention backup must cover the rows prune can delete. |
| `test_sessions_failure_exit_codes.py` | `hermes sessions` exit status tracks the outcome: a subcommand that fails, refuses, or could not ask for its confirmation exits non-zero, so cron/CI wrappers and `hermes sessions repair && ...` chains can tell. |
| `test_sessions_held_store_gate.py` | `hermes sessions optimize\|optimize-storage\|prune` refuse while another process holds state.db (#110054). |
| `test_sessions_list_truncation.py` | ``hermes sessions list`` tells the user when ``--limit`` cut the listing (#111989). |
| `test_sessions_observation.py` | Session listings must not initialize or migrate canonical storage. |
| `test_sessions_pin.py` | CLI pin / unpin / pinned subcommands (issue #52955). |
| `test_sessions_prune_via_owner.py` | `hermes sessions prune` while the always-on gateway owns state.db (live smoke LS-F7). |
| `test_sessions_repair_check_only_exit.py` | `hermes sessions repair --check-only` must fail (non-zero) when the store is unhealthy. |
| `test_sessions_repair_declarative.py` | Explicit repair must restore browsing after additive schema drift (#140315). |
| `test_sessions_repair_profiles.py` | ``hermes sessions repair-profiles``: the backward-looking half of the per-profile store model. |
| `test_sessions_repair_prompts.py` | Behavior contracts for hermes sessions repair-prompts (#122822). |
| `test_sessions_rest_scaffold_notices.py` | REST session transcripts must not ship untyped gateway scaffold notices as user rows. |
| `test_sessions_set_journal_mode.py` | `hermes sessions set-journal-mode` converts an existing WAL store offline and refuses under a foreign holder. |
| `test_sessions_size_delta_label.py` | Tests for the session-store size-delta label (`hermes sessions optimize*`). |
| `test_sessions_source_local.py` | ``hermes sessions list\|browse\|stats --source cli`` must see gateway rows stored as ``local``. |
| `test_set_config_value.py` | Tests for set_config_value — verifying secrets route to .env and config to config.yaml. |
| `test_settings_only_provider_block_validation.py` | Regression tests for #120020: a settings-only ``providers.<slug>`` block must not reroute model validation into the custom-endpoint branch. |
| `test_setup.py` | Tests for setup.py configuration flows. |
| `test_setup_agent_import.py` | `hermes setup`'s "Coming from another agent?" step: it offers only the agents found on disk, installs the agent-importers plugin through the catalog install only after a yes, then runs that plugin's import for each pick. |
| `test_setup_agent_settings.py` | Tests for agent-settings copy in the interactive setup wizard. |
| `test_setup_blank_slate.py` | Tests for Blank Slate setup mode (hermes_cli/setup.py). |
| `test_setup_hermes_script.py` | Tests: `test_setup_hermes_script_is_valid_shell` |
| `test_setup_hidden_env.py` | Setup surfaces ask only for what a platform can't start without. |
| `test_setup_irc.py` | Tests for IRC gateway configuration via `hermes setup gateway` UI. |
| `test_setup_model_provider.py` | Regression tests for interactive setup provider/model persistence. |
| `test_setup_noninteractive.py` | Tests for non-interactive setup and first-run headless behavior. |
| `test_setup_pin_values.py` | Cold setup consumes lock values before executing any downloaded tool. |
| `test_setup_prompt_menus.py` | Tests: `test_prompt_choice_escape_keeps_default_without_numbered_fallback`, `test_setup_navigation_escape_cancels_and_left_goes_back`, `test_setup_steps_move_to_previous_section_or_restart_current_section`, `test_nested… |
| `test_setup_provider_catalog.py` | First-time setup must consume the registered provider catalog (#116408). |
| `test_setup_quick_import.py` | First-time Quick Setup after an agent import: a model the import brought is kept by default instead of being replaced by the Nous Portal login/model step. |
| `test_setup_reconfigure.py` | Tests for the setup wizard's returning-user behavior. |
| `test_setup_reset_backup.py` | Ordering guarantees for the setup wizard's config.yaml backup (#3522). |
| `test_setup_summary_provider_warning.py` | Setup summary must warn loudly when no provider got configured. |
| `test_setup_telemetry.py` | Tests for shared-metrics configuration discovery and setup. |
| `test_setup_terminal.py` | Tests for hermes_cli/setup_terminal.py backend wizards. |
| `test_setup_tts_xai_oauth.py` | Regression: TTS/setup xAI OAuth must not hijack the active chat provider. |
| `test_shallow_boundary_repair.py` | Repair of shallow boundaries dropped by the stale-graft prune (#108286). |
| `test_shallow_graft_prune.py` | Stale shallow-graft pruning after depth-1 update checks (#105951). |
| `test_shared_metrics_closed_turn_marks.py` | Process-level shared-metrics marks from background work that outlives the turn it was spawned in. |
| `test_shared_metrics_compression_outcome.py` | ``hermes.compression.count`` keeps a committed fallback's class instead of reading as a clean success. |
| `test_shared_metrics_connectors.py` | Connector work in the shared metrics: per-entry tool counting, gateway error classes, the search-to-execute chain, and the tool_search / tool_batch / connector_chain rows. |
| `test_shared_metrics_consent_windows.py` | Property tests for the consent-interval model. |
| `test_shared_metrics_desktop.py` | v5 desktop: hermes.desktop.{feature_use,friction,onboarding,dislike,mode_use,action_use}. |
| `test_shared_metrics_efficiency.py` | v5 efficiency metrics: per-turn cost, wasted tokens, tool output truncation, tool overhead and prompt-cache breaks. |
| `test_shared_metrics_engagement.py` | Engagement invariants: the daily rollup reports each closed day once per profile, a compressed conversation is one session row with its whole volume, and turns-before-switch names the model left. |
| `test_shared_metrics_exit_flush.py` | Graceful ``os._exit`` paths run the shared-metrics exit flush their skipped atexit hook would have run. |
| `test_shared_metrics_gateway.py` | Invariants for gateway / cron shared metrics: bounded platform names with proven catalog provenance, opt-in gating, and contract-valid rows. |
| `test_shared_metrics_harness.py` | Agent-harness accuracy shared metrics: file edits, loop guards, tool-error recovery, terminal command outcomes and model reply issues. |
| `test_shared_metrics_install_failures.py` | Why installs and updates fail: failure_class on hermes.extension.install.count and hermes.update.run, registry on hub skill installs (closed sets, never error text). |
| `test_shared_metrics_install_run.py` | hermes.install.run: the installers' local receipt, counted by a later start only while collection is on. |
| `test_shared_metrics_install_v4.py` | Startup latency and the install snapshot's version-lag, channel and hardware fields. |
| `test_shared_metrics_loop.py` | Learning-loop, delegation and execution-backend shared metrics, read back from the real store. |
| `test_shared_metrics_model.py` | Per-model tool-call quality, friction and context-peak shared metrics. |
| `test_shared_metrics_model_attribution.py` | Provider/model attribution invariants for the per-model shared metrics: which route a row names, that user-named models never leave the machine, which profile records it, and how often. |
| `test_shared_metrics_prepared_compaction.py` | Opt-in shared metrics for prepared compaction (``compression.prepare_ahead``). |
| `test_shared_metrics_reliability.py` | v4 reliability metrics: hermes.update.run / hermes.update.stage from the final update receipt, hermes.process.exit from per-process markers and turn watchdogs. |
| `test_shared_metrics_send_config.py` | Tests for shared-metrics send configuration resolution. |
| `test_shared_metrics_send_migration.py` | Tests for the additive send-state migration on ``package_outbox``. |
| `test_shared_metrics_send_wiring.py` | Tests for wiring the sender into the shared-metrics export hook. |
| `test_shared_metrics_sender.py` | Tests for the shared-metrics sender. |
| `test_shared_metrics_sender_e2e.py` | End-to-end test: the real sender against a real HTTP server. |
| `test_shared_metrics_signals.py` | v5 signals: hermes.tool_unavailable.count, hermes.provider_setup.count, hermes.feature_adoption.count. |
| `test_shared_metrics_surface_attribution.py` | Every AIAgent construction path must attribute its execution surface. |
| `test_shared_metrics_tools_toggle.py` | Tests for the `hermes tools` shared-metrics consent toggle. |
| `test_shared_metrics_update_stop_reasons.py` | Every `hermes update` exit before the apply step names its closed reason (hermes.update.run ``failure_class``), in-process and through the parked copy alike; exits that fire before the receipt opens still count once; a… |
| `test_shared_profile_warning.py` | Live subprocesses, real ledger I/O, and isolated profile homes. |
| `test_shared_session_attach.py` | Local owner discovery must fence profile and lease identity. |
| `test_show_config_credential.py` | Regression test: /config must show the LIVE agent credential. |
| `test_show_model_picker_exhausted_pool.py` | Regression test for #103829: the interactive CLI's main ``/model`` picker (``/model`` with no args) must request exhausted-pool visibility. |
| `test_sibling_config_migration.py` | Fleet-wide config migration (#91277 Phase 2 — #20438/#54926/#79048 class). |
| `test_signal_handler_kanban_worker.py` | Regression test for #28181 — kanban worker SIGTERM must terminate the process. |
| `test_single_query_clarify.py` | Regression tests for the single-query clarify guard (#94943). |
| `test_single_query_exit_contract.py` | One-shot ``chat -q`` runs report their outcome in the exit code, like ``-Q`` always did. |
| `test_single_query_plugin_cli_ref.py` | ``hermes chat -q``/``-Q`` runs leave this process's plugin manager alone. |
| `test_single_query_session_finalize.py` | Tests: `reset_single_query_finalize_state`, `test_finalize_single_query_releases_lease_before_cleanup`, `test_finalize_single_query_runs_cleanup_when_finalize_hook_fails`, `test_finalize_settles_session_before_a_success… |
| `test_single_query_turn_author.py` | A dispatcher-authored ``chat -q`` run carries its turn author, as ``chat -Q`` already does. |
| `test_sizefmt.py` | Tests for the shared byte formatter (hermes_cli.sizefmt). |
| `test_skill_collision_visibility.py` | A skill named like a built-in command is kept out of auto-registration (the 370ebf2d3 guard) and every listing surface says so where the user looks: the ``/skills`` table, ``/help skills`` and the ``commands.catalog`` p… |
| `test_skills_config.py` | Tests for hermes_cli/skills_config.py and skills_tool disabled filtering. |
| `test_skills_failure_exit_code.py` | A failed ``hermes skills install\|update\|uninstall\|snapshot import`` exits non-zero (#118301). |
| `test_skills_hub.py` | Tests: `_DummyLockFile`, `hub_env`, `three_source_env`, `_capture`, `_capture_check`, `_capture_update` … |
| `test_skills_install_flags.py` | Tests for --yes / --force flag separation in `hermes skills install`. |
| `test_skills_provider_filter.py` | Provider filters must run before a source's result limit can discard matches. |
| `test_skills_skip_confirm.py` | Tests for skip_confirm and invalidate_cache behavior in /skills install and /skills uninstall slash commands. |
| `test_skills_uninstall_flags.py` | Tests for --yes / -y flag in `hermes skills uninstall` CLI subcommand. |
| `test_skin_cmd.py` | `hermes skin set` — deterministic single-color tweak of the active skin. |
| `test_skin_engine.py` | Tests for hermes_cli.skin_engine — the data-driven skin/theme system. |
| `test_skin_palettes.py` | Built-in skin palette audit: completeness + WCAG contrast, per polarity. |
| `test_slack_cli.py` | Tests for Slack CLI helpers. |
| `test_slash_command_interrupt.py` | Tests for the KeyboardInterrupt guard around slash command dispatch. |
| `test_slash_command_metrics.py` | Classic-CLI slash commands reach shared metrics once each: canonical name, surface ``cli``. |
| `test_slash_confirm_windows.py` | Regression tests for #30768, #32383, and #33961. |
| `test_slash_dispatch_table.py` | Slash-command dispatch semantics in cli.HermesCLI. |
| `test_slash_undo_title_robustness.py` | Regression tests for slash-command dispatch robustness (round-3 QA). |
| `test_smart_app_control_block.py` | Windows Smart App Control detection in the dashboard deps check (#63796). |
| `test_snapshot_restore_gateway_session.py` | /snapshot restore in a gateway-backed classic CLI keeps the CLI on its gateway session. |
| `test_snapshot_restore_oauth.py` | Quick snapshot auth restore must not roll back rotated single-use OAuth grants. |
| `test_source_build.py` | Source orchestration uses real node-deps/npm in an isolated checkout. |
| `test_source_channel_integration.py` | Source channel tracers through real HTTP, Git, and completion boundaries. |
| `test_source_check.py` | Exercise the passive checker with real linked worktrees and loopback HTTP. |
| `test_source_check_refused_token.py` | #134335: a token GitHub refuses with 403 (suspended/restricted account, still printed by `gh auth token`) falls back to anonymous like a 401 does; a spent rate limit does not. |
| `test_source_completion_stamp.py` | A source checkout publishes identity only after successful completion. |
| `test_source_launcher_publication.py` | Source launchers keep custom-home and selected-generation state at boot. |
| `test_source_release_channels.py` | Release-channel checks and updates against actual repositories and HTTP feeds. |
| `test_source_release_probe.py` | A desktop check must not reinterpret unreadable channel config as main. |
| `test_source_stamp.py` | Source checkout identity is written only from the checkout itself. |
| `test_spa_document_policy.py` | Every privileged SPA document uses the same bootstrap policy: uncached, prefixed, and tokenless whenever the gate or the surface withholds the session token. Where the surface's policy keeps the token out of HTML (the W… |
| `test_spa_static_asset_misses.py` | Asset requests never get the SPA shell. The sign-in page's brand fonts load on the Webapp surface too, whose bundle carries no ``fonts/`` dir, and a missing file under a static asset prefix is a 404 on both surfaces ins… |
| `test_spawn_gateway_restart_cooldown.py` | Tests for the _spawn_gateway_restart repeat-request cooldown (#89034). |
| `test_spawn_gateway_restart_reap.py` | The gateway-restart flow refuses BEFORE it stops anything (#125394, #77276). |
| `test_sqlite3_cli_salvage_gate.py` | #100368 regression: the corruption guidance must not direct a WAL-reset- vulnerable sqlite3 CLI at a live Hermes database. |
| `test_sqlite_runtime.py` | Behavioral tests for exact-interpreter SQLite runtime inspection. |
| `test_sqlite_util_canonical.py` | Invariants for the canonical SQLite connect/transaction layer (``hermes_cli/sqlite_util.py``). |
| `test_sse_done.py` | Unit tests for SSE [DONE] sentinel tracking (issue #90848). |
| `test_ssh_ownership_endpoint.py` | Tests: `test_ssh_ownership_endpoint_requires_token_and_returns_exact_nonce`, `test_ssh_ownership_reports_replaced_runtime`, `test_ssh_runtime_marker_detects_recreated_venv_even_with_reused_inode`, `test_ssh_runtime_mark… |
| `test_ssh_session_token_parser.py` | Tests: `test_token_file_is_read_and_unlinked_through_private_directory`, `test_token_anchor_is_os_home_not_active_profile`, `test_token_under_profile_desktop_ssh_is_rejected`, `test_token_file_rejects_symlink`, `test_to… |
| `test_ssh_workspace_fs.py` | Tests: `FakeEnv`, `_entry`, `test_ssh_workspace_fs_lists_and_reads_remote_paths`, `test_ssh_workspace_fs_maps_remote_size_failure`, `test_ssh_workspace_fs_inspects_resolved_file_before_streaming`, `test_ssh_workspace_fa… |
| `test_stable_forward_only_shallow.py` | An unchosen default channel never moves a checkout backward on a guess, and an ancestry probe that never answered never refuses the update (regression for #137646). |
| `test_stable_lookup_github_auth.py` | The stable lookup spends the user's GitHub credential, not the shared anonymous budget. |
| `test_stale_aux_local_endpoint.py` | Aux pins on local/LAN endpoints are not "stale" — they never bill a provider (#106228). |
| `test_stale_pid_guard.py` | Regression tests for the fail-closed PID-ownership guard. |
| `test_stale_root_module_bridge.py` | Bridge for pre-hand-off ``hermes update``: a stale root ``utils`` must not kill restart. |
| `test_startup_fast_guards.py` | Guards for hermes_cli._startup_fast — the pre-import version fast path. |
| `test_startup_model_routing.py` | Regression tests for startup model/provider routing (#87189). |
| `test_startup_plugin_gating.py` | Guards for CLI startup performance regression. |
| `test_state_db_guard.py` | Tests for the state.db integrity guard used by the update flow (#68474). |
| `test_static_models_home_scope.py` | A plugin profile's ``static_models`` belong to the home that registered it. |
| `test_status.py` | Tests: `test_show_status_all_does_not_print_keenable_key_value`, `test_show_status_all_does_not_print_tavily_key_value`, `test_show_status_termux_gateway_section_skips_systemctl`, `test_show_status_reports_vercel_backen… |
| `test_status_bar_git_branch.py` | Invariant tests for the opt-in git-branch status-bar field. |
| `test_status_lines_held_during_stream_box.py` | Agent status lines (subagent ``✓ [set n · i/N]`` completions, background-process notices) arrive on other threads mid-stream. The CLI's ``agent._print_fn`` must park them while a response box is open and release them at… |
| `test_status_model_provider.py` | Tests for hermes_cli.status model/provider display. |
| `test_status_probe_off_loop.py` | /api/status does its local file reads off the event loop (#143561). |
| `test_status_provider_label.py` | `hermes status` provider label honors config.yaml model.base_url (#3296). |
| `test_status_readonly.py` | Status must not bootstrap the session writer it merely observes. |
| `test_status_report_contract.py` | Contract: the CLI, gateway and TUI /status renderers report the SAME common facts. |
| `test_stderr_timestamp.py` | Tests for hermes_cli.stderr_timestamp. |
| `test_stepfun_picker_merge.py` | StepFun /model picker merges the Step Plan live catalog with the curated list. |
| `test_steward_detection.py` | Steward detection reads the install stamp beside the code, not markers. |
| `test_stream_delta_think_tag.py` | Tests for _stream_delta's handling of <think> tags in prose vs real reasoning blocks. |
| `test_stream_flush_left.py` | Streamed response lines must be flush-left (no leading indent). |
| `test_stream_json.py` | ``hermes chat -q … --format stream-json`` emits a parseable JSONL event stream and nothing else on stdout. |
| `test_stream_partial_line_flush.py` | Streaming display: logical lines are emitted ONLY at real newlines. |
| `test_stt_picker.py` | Tests for the Speech-to-Text category in `hermes tools` (tools_config). |
| `test_subagent_dock_collapse.py` | Collapsing the passive dock never takes space or focus from the editor. |
| `test_subagent_dock_surface.py` | A passive dock paints a bounded surface without acquiring the editor. |
| `test_subagent_monitor.py` | The dock is bounded, session-owned, and only repaints changing live work. |
| `test_subagent_monitor_gateway.py` | CLI-12: the Ctrl+T monitor and dock read the gateway session's subagents. |
| `test_subagent_monitor_prompts.py` | Blocking prompts reclaim input from the nested monitor without a keypress. |
| `test_subagent_monitor_resize.py` | A queued composer resize must not erase the alternate-screen monitor. |
| `test_subagent_monitor_ui.py` | Monitor navigation keeps controls pinned while live children finish. |
| `test_subagent_notification_display.py` | Completion notices stay human-facing while the parent retains full results. |
| `test_subagent_shortcut.py` | The shared TUI shortcut routes without editing the classic composer. |
| `test_subcommands_batch.py` | Smoke tests for the batch-extracted subcommand parser builders. |
| `test_subcommands_final_batch.py` | Smoke tests for the final batch of subcommand builders extracted from main(). |
| `test_subcommands_followup.py` | Smoke tests for the Phase 2 follow-up subcommand builders (promoted handlers). |
| `test_subcommands_profile_gateway.py` | Unit tests for extracted subcommand parser builders (profile, gateway). |
| `test_subprocess_text_encoding.py` | Guard: every text-mode subprocess call in hermes_cli pins utf-8 decoding (#55658). |
| `test_subprocess_timeouts.py` | Tests for subprocess.run() timeout coverage in CLI utilities. |
| `test_subscription_cli.py` | Tests for the /subscription CLI change flow (cli.py::_show_subscription). |
| `test_system_stats_platform.py` | Tests: `test_windows_11_build_displays_as_windows_11`, `test_non_windows_platform_unchanged` |
| `test_systemd_optional_directives.py` | Tests for systemd optional-directive normalization (issue #41119). |
| `test_systemd_replace_dropin.py` | A Hermes-authored systemd ``--replace`` drop-in must not survive unit refresh. |
| `test_systemd_watchdog_unit.py` | Generated service behavior for the opt-in systemd watchdog. |
| `test_tag_fetch_partial_clone.py` | The post-update tag fetch must not convert a full clone into a partial one. |
| `test_taskkill_identity_windows_live.py` | Live Windows probes for the fail-closed taskkill process-identity guard. |
| `test_teams_pipeline_plugin_cli.py` | Tests for the teams_pipeline plugin CLI. |
| `test_telegram_managed_bot.py` | Tests for hermes_cli.telegram_managed_bot — QR codes, deep links, pairing. |
| `test_tencent_tokenhub_provider.py` | Tests for Tencent TokenHub provider support (Hy4 preview). |
| `test_terminal_backend_docker_probe.py` | Dashboard docker-backend probe must follow the same runtime resolution as the agent. |
| `test_terminal_breadcrumbs.py` | Tests for hermes_cli/terminal_breadcrumbs.py — per-terminal ``hermes -c``. |
| `test_terminal_bridge_profile_scope.py` | Regression: the terminal config→env re-bridge is scoped to the *true* process profile, never a per-task ``set_hermes_home_override``. |
| `test_terminal_interrupt_recovery.py` | Regression tests for #33271: terminal recovery after interrupt. |
| `test_terminal_io_broken.py` | CLI freezes UI paints after stdout/PTY EIO (#81521). |
| `test_terminal_menu_fallbacks.py` | Regression tests for numbered fallbacks when the interactive curses menu cannot initialize (e.g. non-TTY, curses unavailable, terminal error). |
| `test_terminal_notify.py` | display.bell_on_prompt / bell_on_complete also drive OSC 9 + Warp OSC 777 via _ring_bell. |
| `test_termios_drift_heal.py` | Regression tests for cooked-mode termios drift healing (cli._heal_cooked_mode_drift). |
| `test_termux_gateway_launch.py` | Termux's interactive fast launch keeps main's deferred-startup hints (main's HermesCLI runs again). |
| `test_timeouts.py` | Tests: `_write_config`, `test_anthropic_adapter_honors_timeout_kwarg`, `test_resolved_api_call_timeout_priority` |
| `test_timestamps_command.py` | Tests for the CLI `/timestamps` toggle and timestamps in `/history`. |
| `test_tips_catalog.py` | hermes_cli.tips reads its catalog through i18n: count follows the English catalog, text follows the active language, and a partial translation falls back to English per tip. |
| `test_tool_availability_notices.py` | Invariants for the CLI startup 'some tools disabled' notice (tools-runtime-01 / -02). |
| `test_tool_gen_start_dedupe.py` | A batch of parallel tool calls announces "preparing <tool>…" once per tool, not once per call (#10478). |
| `test_tool_progress_scrollback.py` | Tests for stacked tool progress scrollback lines in the CLI TUI. |
| `test_tool_token_estimation.py` | Tests for tool token estimation and curses_ui status_fn support. |
| `test_tools_config.py` | Tests for hermes_cli.tools_config platform tool persistence. |
| `test_tools_config_post_setup.py` | Provider setup delegates package policy to PM and external server owners. |
| `test_tools_disable_enable.py` | Tests for hermes tools disable/enable/list command (backend). |
| `test_toolset_validation.py` | Unit tests for hermes_cli.toolset_validation (see #38798). |
| `test_top_level_value_flags_parity.py` | Top-level value-flag classification must match the real parser (#93530). |
| `test_transformed_stream_output.py` | Regression coverage for CLI delivery after transform_llm_output streaming. |
| `test_tts_picker.py` | Tests for the TTS plugin picker surface in hermes_cli/tools_config.py (issue #30398). |
| `test_tui_bundled.py` | Tests: `test_tui_finds_bundled_entry_js` |
| `test_tui_exit_summary_short_id.py` | The TUI exit epilogue names a canonical session as compactly as main did (PR #106742 row 36). |
| `test_tui_first_run_routing.py` | First-run routing between the classic CLI guard, the TUI and the shared-metrics offer. |
| `test_tui_heap_sizing.py` | Tests for cgroup-aware TUI V8 heap sizing. |
| `test_tui_launcher_skips_plugin_discovery.py` | Regression test: the TUI launcher must not spend time on plugin discovery. |
| `test_tui_mouse_residue_suppression.py` | Tests for the TUI-hot-path mouse-residue suppression. |
| `test_tui_npm_install.py` | TUI launch consumes the shared dependency preparation and compiler. |
| `test_tui_rapid_enter_paste.py` | Enter arriving mid-paste (no bracketed paste; each newline is its own key event) must not submit / steer the partial line (#10994). Only the Enter-vs-recent-text-change timing is exercised; the real prompt_toolkit Buffe… |
| `test_tui_resume_flow.py` | Tests: `_args`, `_raise_exit`, `main_mod`, `test_exit_after_oneshot_flushes_stdio_and_calls_os_exit`, `test_oneshot_subprocess_exits_without_teardown_abort`, `_stub_plugin_discovery` … |
| `test_tui_terminal_reset_on_exit.py` | Regression tests for GitHub #36823 — the TUI must reset terminal input modes on exit so focus-reporting / mouse-tracking escape sequences don't leak into the next shell session sharing the tab. |
| `test_tui_worktree_clean_quit.py` | N8: quitting ``hermes --tui -w`` removes a clean worktree (and its branch), as ``main`` did before #106742; a dirty one, or one the gateway still has queued/started work in, is kept. |
| `test_tui_worktree_resume_recreate.py` | N8 review 2.2: quitting a clean ``hermes --tui -w`` session that had a conversation removes its tree and branch, but the session's policy froze that cwd, so a later resume had every turn refused ``workspace_unavailable`… |
| `test_ui_preferences.py` | The machine's UI preferences store (#145213): one file beside the ROOT Hermes home, shared by native Desktop and every browser that opens this machine's Webapp. |
| `test_unified_pool_quirk.py` | The unified-pool vendor quirk must never misclassify a discrete card. |
| `test_uninstall_dry_run.py` | Tests: `test_dry_run_prints_plan_without_mutating`, `test_dry_run_lists_named_profiles_without_desktop_userdata`, `test_build_uninstall_parser_accepts_dry_run` |
| `test_uninstall_full_wipe_sweep.py` | Full-uninstall macOS sweep: dashboard/serve launchd jobs and Electron/setup caches that live OUTSIDE HERMES_HOME and survive the home rmtree (#62209). |
| `test_uninstall_gateway_service.py` | Tests for ``uninstall_gateway_service`` — the per-platform service dispatch. |
| `test_uninstall_gui_userdata.py` | Keep-data uninstall must not delete the desktop app's Electron userData dir. |
| `test_uninstall_install_kind.py` | Tests for the install-kind uninstall gate + the data-only mode. |
| `test_uninstall_leftovers.py` | Uninstall sweeps every leftover: both LaunchAgent label patterns, macOS Library app-store entries and the XDG cache/data dirs outside HERMES_HOME (#62209 — uninstalls reported success yet launchd respawned the gateway a… |
| `test_uninstall_node_symlinks.py` | Tests for hermes_cli.uninstall.remove_node_symlinks. |
| `test_uninstall_shell_configs.py` | Tests for ``remove_path_from_shell_configs`` — the uninstaller's shell-rc rewrite. |
| `test_uninstall_windows_bin_launchers.py` | Uninstall must not leave a dangling ``hermes`` command on Windows. |
| `test_unsupervised_pid1_warning.py` | The PID-1-with-no-init startup warning (#111577): a Compose ``entrypoint:`` override makes hermes PID 1 with no reaper above it, so orphaned children pile up as zombies. |
| `test_update_apply_shallow_count.py` | Shallow-checkout guard on the ``hermes update`` apply path (#53479, mirroring #86257). |
| `test_update_autostash.py` | Real Git local-work safety: caller divergence, restore faults and rescue retention. |
| `test_update_autostash_orphan_warning.py` | Orphaned update-autostash surfacing (#63717 problem 6). |
| `test_update_behind_count_recovery.py` | Behind-count recovery via the GitHub compare API (source_check.py). |
| `test_update_bootstrap_cache_refresh.py` | Tests for _refresh_bootstrap_cache_scripts (the stale-installer-cache fix). |
| `test_update_channel.py` | Per-install update-channel records (hermes_cli/update_channel.py). |
| `test_update_channel_release_hold.py` | A channel whose release predates the gateway runtime holds the install where it is (#140729). |
| `test_update_channel_stable.py` | Source-update channel selection policy. |
| `test_update_cold_start_gateway_liveness.py` | #84185: a Windows gateway cold-started after update that dies immediately (e.g. a job object denying breakaway) must not be reported as started. |
| `test_update_command.py` | Tests for the /update slash command in the classic CLI and TUI launcher. |
| `test_update_commit_obligations.py` | The commit point's obligations: armed before the tree moves, handed back only when still ours. |
| `test_update_completion_lease.py` | L3: the Windows bootstrap completion child joins the checkout lock (with its own R5b lease) before it writes the checkout. |
| `test_update_completion_process.py` | A checkout transition must not finish in the old interpreter's module graph. |
| `test_update_completion_routing.py` | All source selection routes hand off once, without old-process maintenance. |
| `test_update_concurrent_quarantine.py` | Windows gateway service invariants and launcher identity after PM cutover. |
| `test_update_config_clears_custom_fields.py` | Tests for hermes_cli.auth._update_config_for_provider clearing stale fields. |
| `test_update_config_migration_on_current.py` | Migration UX policy; selected-child and real profile writes live in completion tests. |
| `test_update_contract.py` | Image-managed refusal contract tests (#91277 Phase 3). |
| `test_update_cron_deadlock_guard.py` | Regression tests for #100179: cron-update three-way restart deadlock. |
| `test_update_cua_pm.py` | Updates reconcile owned CUA pins without bypassing native host setup. |
| `test_update_custody.py` | R2: every updater git runner shares ONE custody policy (hermes_cli.update_custody). |
| `test_update_custody_tree.py` | #144439: where there is no parent-death signal (macOS), updater git custody owns the git TREE, not git's pid: a timeout, or the owner's death, ends the helpers git started too. |
| `test_update_detached_rescue_ref.py` | `hermes update` must not orphan commits made on a detached HEAD. |
| `test_update_diverged_rescue_ref.py` | `hermes update` must not drop local commits without leaving a named way back. |
| `test_update_downgrade_guard.py` | `hermes update` refuses a target that predates the gateway runtime once a state.db holds ledger rows. |
| `test_update_downgrade_guard_named_profile.py` | A named-profile update's refusal tells the user to reopen THAT profile for its snapshot. |
| `test_update_eol_churn.py` | Regression: ``hermes update`` should take a managed checkout off autocrlf=true. |
| `test_update_existing_branch_baseline.py` | Real Git regression coverage for updates that land via an existing branch. |
| `test_update_exit_code_publication.py` | Every writer of ``.update_exit_code`` publishes it atomically. |
| `test_update_external_checkout.py` | Regression coverage for separate-checkout gateways (#117449). |
| `test_update_external_profile_reconciliation.py` | A symlinked profile that is really another install must not fail `hermes update` (#120240). |
| `test_update_failed_unit_proven_current.py` | A unit the restart phase recorded failed, but whose own gateway verification proves current. |
| `test_update_fetch_failure_classifier.py` | Fetch-failure classification for `hermes update` / `hermes update --check`. |
| `test_update_fetch_timeout.py` | A dead-stalled network fetch ends `hermes update` with an error, never a hang (#93759, #95777). |
| `test_update_finish.py` | Historical takeover completion in a fresh, dependency-selected process. |
| `test_update_finish_stamp.py` | Historical takeover publishes source identity before restarting runtimes. |
| `test_update_flat_install_state_gitignore.py` | Flat-install runtime state must be gitignored so ``hermes update``'s untracked autostash cannot sweep the live state.db (#110648). |
| `test_update_fleet_check_fail_closed.py` | Regression for #93406 — post-update fleet version check must fail closed. |
| `test_update_fleet_checkout_build_stamp.py` | ``checkout_contains`` on a build-stamped image (no ``.git``): ancestry collapses to stamp equality. |
| `test_update_fleet_completion.py` | SQLite completion and fleet verification remain independent update outcomes. |
| `test_update_fleet_home_scope.py` | #93349 — ``hermes update`` restarts only the gateways of the home it is updating. |
| `test_update_fleet_incomplete_warning.py` | Incomplete-fleet-restart hint on a systemd host (Linux arm of ``_warn_incomplete_gateway_fleet_restart``; the macOS arm lives in test_update_launchd_fleet_restart.py). Regression for #111866: this class used to sit in t… |
| `test_update_fleet_probe_resume_token.py` | Regression for #93406 (residual) — the Windows pause/resume token is NOT a fleet runtime and must not be counted by ``_fleet_probe_expected_runtimes``. |
| `test_update_fleet_restart_pending.py` | Interrupted-update fleet-restart obligation (#95294 parts 1+2). |
| `test_update_fleet_restart_timeout.py` | Regression for #68523 — one systemctl timeout must not abort fleet restarts. |
| `test_update_fleet_snapshot_settle.py` | Regression for #111272: wait for a supervised gateway to publish its state. |
| `test_update_fork_sync_identity.py` | The fork sync acts on ONE upstream commit (review R6 m2). |
| `test_update_gateway_launcher_refresh.py` | Legacy pythonw launcher normalization + post-update launcher refresh. |
| `test_update_gateway_restart_aborted.py` | Regression for #78574 — a crashed gateway-restart phase must not stay silent. |
| `test_update_gateway_restart_fallback.py` | Regression coverage for #88654. |
| `test_update_hangup_protection.py` | Tests for SIGHUP protection and stdout mirroring in ``hermes update``. |
| `test_update_head_moved_gate.py` | Tests for the post-pull HEAD-movement gate in ``hermes update``. |
| `test_update_host_obligation.py` | The update→restart obligation is HOST-scoped, and one update restarts the host gateway once. |
| `test_update_import_guard.py` | Tests for the post-update *import* guard in ``hermes update``. |
| `test_update_interrupted_pull.py` | A `hermes update` killed while git writes the new tree must leave a recoverable install. |
| `test_update_inventory.py` | Tests for hermes_cli.update_inventory — the plan phase (#91277 Phase 2). |
| `test_update_launch_completion.py` | A fresh launch finishes a source update using PM's success record, not a marker. |
| `test_update_launchd_fleet_restart.py` | Regression for #41403 — ``hermes update`` must restart ALL macOS launchd gateways. |
| `test_update_launchd_restart_verification.py` | Regression for #88848 - a launchd restart the update never verified. |
| `test_update_launchd_unloaded_gateway.py` | Regression for #74973 — `hermes update` must not leave the gateway down. |
| `test_update_left_alone_notice_once.py` | A gateway of another Hermes home is announced once per update run, not once per discovery pass. |
| `test_update_list_venv_holders.py` | ``hermes update --list-venv-holders``: read-only JSON twin of the Windows venv-holder refusal. |
| `test_update_live_output.py` | Live output must reach disk before exit, without concealing silence. |
| `test_update_lock.py` | Cross-process update mutual exclusion (``hermes_cli.update_lock``). |
| `test_update_lock_fd_provenance.py` | A same-process status reader cannot donate a descriptor to checkout custody. |
| `test_update_lock_probe_readers.py` | The update fence never reads another reader's probe of the checkout lock as a held lock. |
| `test_update_lock_protocol.py` | Marker mutation protocol (A7) and checkout custody (R2/R11) with real processes and files. |
| `test_update_lock_windows_live.py` | Windows live cells for the checkout lock (contract C1.7): msvcrt byte lock + kill-on-close job. |
| `test_update_marker_corpus.py` | The shared update-marker corpus, run against the Python reader/releaser (A7 rule 7). |
| `test_update_messages.py` | User-facing wording contracts for ``hermes update`` failure/partial output. |
| `test_update_missing_configured_deps.py` | Configured-feature warnings must describe the selected update child (#10651). |
| `test_update_modified_notice.py` | Skill sync keeps user edits and tells the updater's user how to inspect them. |
| `test_update_narrow_clone_compare_ref.py` | Regression for #125112: the updater must resolve its compare ref on narrow clones. |
| `test_update_narrow_clone_refspec.py` | Regression test for #125112: `hermes update --check` on a narrow clone. |
| `test_update_no_gateway_restart.py` | The PM completion child honors --no-gateway-restart without skipping preparation (#93649). |
| `test_update_obligation_identity.py` | A historical receipt cannot outweigh complete, identity-matched live evidence. |
| `test_update_owning_install.py` | ``hermes update`` from a PM environment's workspace goes to the checkout that owns it (#122627). |
| `test_update_parked_branch_guard.py` | Regression tests for the parked-branch guard in ``hermes update``. |
| `test_update_pause_boundaries.py` | Real-process pause/consume/recovery contracts, not native Windows SCM evidence. |
| `test_update_pause_checkout_moves.py` | Every checkout-writing step binds the paused gateways' tree gate first (#132338 R3, thread 5). |
| `test_update_pause_debt_windows_live.py` | Native Windows restart-debt boundaries of the update pause (#132338 R8): real files held the way Windows readers hold them, a real SCM service, real processes and taskkill. Nothing here is mocked. |
| `test_update_pause_moved_head_gate.py` | The paused gateways' tree gate judges a MOVED HEAD too (#132338 R3 follow-up). |
| `test_update_pause_record.py` | Paused-gateway record and update-claim adoption, with real processes and a real checkout. |
| `test_update_pause_recover_backoff.py` | A launch's paused-gateway recovery never makes every command wait on the same unready relaunch. |
| `test_update_pause_recovery_stdout.py` | Startup recovery never writes to the stdout of the command it runs ahead of. |
| `test_update_pause_service_rollback.py` | A failed service pause keeps its record exactly when its rollback left gateways down. |
| `test_update_pause_step_interruptions.py` | The stash and churn steps bind the paused gateways' tree gate too (#132338 R3 follow-up). |
| `test_update_pause_stop_evidence.py` | Accepted-stop evidence the pause record cannot read or could not write: the debt stays owed. |
| `test_update_pause_unmapped_home_proof.py` | A paused unmapped gateway keeps the home discovery proved for it (#132338 R2 / review thread 7). |
| `test_update_pause_unmapped_identity.py` | An unmapped gateway's restart debt is retired only by ITS runtime (#132338 review C). |
| `test_update_pm_git.py` | Windows installs whose git is PM's: install.ps1 stages it, PM's facts must record it. |
| `test_update_posix_pause.py` | POSIX pre-swap gateway pause: what survives a killed updater, and what a paused update asks. |
| `test_update_post_commit_followups.py` | Contract C3: after the commit point nothing fails `hermes update`. |
| `test_update_post_commit_safety.py` | Post-commit completion keeps exit status, runtime safety and owed debt as separate facts. |
| `test_update_post_pull_syntax_guard.py` | Tests for the post-pull syntax guard in ``hermes update``. |
| `test_update_products.py` | Update retries use the same dependency transaction as a newly pulled tree. |
| `test_update_proxy_env.py` | Tests: `test_marked_update_proxy_env_is_undone_and_the_users_own_env_kept`, `test_a_proxy_the_users_dotenv_sets_survives_the_restore`, `_desktop_injected_env`, `test_hermes_update_sends_the_update_to_the_users_dotenv_pr… |
| `test_update_receipt.py` | Tests for hermes_cli.update_receipt — Phase 1 of the fleet-update plan (#91277). |
| `test_update_receipt_durability.py` | Receipt recovery must preserve terminal and user-action facts across processes. |
| `test_update_receipt_endpoint.py` | Phase-1 bullet 3 (#91277): the dashboard/Desktop READ the update receipt. |
| `test_update_receipt_owe_followup.py` | A post-commit follow-up lands on the run exactly once, whether its receipt is still open or closed. |
| `test_update_receipt_pm_embed.py` | Tests: update receipts embed ONLY their own pm sync sections. |
| `test_update_receipt_profile_store.py` | Under a named profile the updater (root store) and pm (profile store) still see each other's receipts. |
| `test_update_receipt_run_record.py` | A run's own archive is read through one lookup: an unreadable record is a missing record. |
| `test_update_receipt_scope.py` | Nested command boundaries and copied contexts cannot close an outer receipt. |
| `test_update_receipt_truthfulness.py` | Truthfulness invariants for the update pipeline at the RECEIPT layer. |
| `test_update_recovery_closure.py` | A killed tree move that tears the launch repair's own code is still repaired at the next launch. |
| `test_update_recovery_custody.py` | Broken custody imports never authorize repair of a possibly live checkout. |
| `test_update_release_tag_fetch.py` | A stable update names the checkout by the release it moved to (#143656). |
| `test_update_restart_recovery.py` | Regression coverage for fresh-process recovery after an update restart abort. |
| `test_update_restore_authority.py` | Maintenance must not replace the database behind a live authority. |
| `test_update_scoped_reconciliation.py` | Marker settlement uses its own inventory, never a historical receipt's ownership. |
| `test_update_secret_import_lock.py` | Regression coverage for Windows updater self-locking native dependencies. |
| `test_update_serve_generation_recovery.py` | Regression coverage for stale ``hermes serve`` generations after an abort. |
| `test_update_shallow_heal.py` | A shallow checkout is unshallowed (commit graph only) before the updater's bounded fetch. |
| `test_update_shim_self_lock.py` | Pending-rename filter for the Windows console-shim update self-lock (#88838, #89599, #86093). |
| `test_update_slow_unit_stop.py` | A systemd unit whose stop outlives the updater's ``systemctl`` timeout. |
| `test_update_sqlite_remediation.py` | Selected-runtime admission and dashboard completion bookkeeping. |
| `test_update_ssl_cert_file.py` | SSL_CERT_FILE → GIT_SSL_CAINFO for the updater's git children (#124654). |
| `test_update_stage.py` | Stage publishing into a watching desktop-update UI (hermes_cli.update_stage). |
| `test_update_stage_relay.py` | The Desktop hand-off window names the update stage that is actually running. |
| `test_update_stale_dashboard.py` | Tests for the stale-dashboard handling run at the end of ``hermes update``. |
| `test_update_stale_gateway_yield.py` | #117275: a stale-code ticker that yields every tick must never read as healthy, and the updater must hand a proven-stale survivor to the request_restart path. |
| `test_update_state_autorestore.py` | Updater restore must publish snapshot rows without replaying the old WAL. |
| `test_update_system_dashboard_unit.py` | ``hermes update`` on a system-scope ``hermes-dashboard`` unit without root (#141021). |
| `test_update_target_identity.py` | Stable updates consume one remote commit across Git and archive transports. |
| `test_update_unit_client_budget.py` | Update clients cover unit transactions without hiding manager failures. |
| `test_update_upstream_prompt_noninteractive.py` | The fork-upstream prompt must never block a non-interactive update (#60240). |
| `test_update_venv_holder_retirement.py` | PM updates do not require the currently running venv to become unoccupied. |
| `test_update_version_report.py` | Version transition reporting after ``hermes update``. |
| `test_update_wedged_gateway.py` | Tests for the wedged-gateway health probe + bounded escalation (#81642). |
| `test_update_windows_cross_install_gateway.py` | ``hermes update`` on Windows pauses only its own install's gateways (#124659). |
| `test_update_windows_home_acl.py` | Windows update ACL repair contracts (the Windows ACL effect: ``tests/test_hermes_dir_acl_windows.py``). |
| `test_update_zip_completion.py` | ZIP completion uses the Git maintenance/fleet path after a real local swap. |
| `test_update_zip_fallback_guards.py` | ZIP fallback must not fire on dependency failures or clobber a dirty tree. |
| `test_update_zip_release_preserve.py` | #70337/#87331/#90495: the ZIP swap must preserve the gitignored build outputs. |
| `test_update_zip_symlink_reject.py` | Regression: _update_via_zip must reject ZIP members with symlink mode. |
| `test_update_zip_sync_failure.py` | ZIP and Git-error fallback return the completion owner's exact failure. |
| `test_update_zip_two_phase.py` | Tests for the two-phase ZIP replace and the shared venv-layout helpers. |
| `test_update_zip_webapp_preserve.py` | Source ZIP updates preserve the separately built Webapp renderer. |
| `test_upstage_provider.py` | Focused tests for Upstage Solar first-class provider wiring. |
| `test_urllib_security.py` | Wire-level tests for credential-safe stdlib urllib redirects. |
| `test_usage_command.py` | ``hermes usage`` — the non-interactive /usage surface (issue #33094). |
| `test_user_provider_timeout_only_entry.py` | Regression for #110402: a ``providers.<name>`` block with no endpoint (only tuning keys like ``stale_timeout_seconds``/``request_timeout_seconds``) must not shadow a BUILT-IN provider of the same name. ``providers.bedro… |
| `test_user_providers_model_switch.py` | Tests for user-defined providers (providers: dict) in /model. |
| `test_ux_messages_chat_sessions.py` | Plain-language contracts for chat/session failure copy (CLI UX message campaign, cluster D). |
| `test_ux_messages_startup.py` | Invariant tests for the plain-language startup messages of the ``hermes`` CLI. |
| `test_vault_key_cli.py` | `hermes vault key migrate --to keychain\|file` through the real argparse tree: the key moves, the vault still opens, and ``vault.key_storage`` follows so a recreated vault lands in the same place. |
| `test_vault_sources_shape.py` | `hermes vault sources --disable` must not crash on a hand-edited non-dict ``vault:`` section in config.yaml (the same YAML-shape hazard class ``_voice_cfg_dict`` guards for voice.*, #19835): the malformed section is coe… |
| `test_venv_current_launch.py` | prepare_launch() recognizes the store interpreter it would re-exec into (#122513). |
| `test_venv_holder_classifier.py` | Cross-platform unit tests for the venv-holder message classifier (#90778). |
| `test_venv_holder_windows_live.py` | LIVE Windows E2E for retained lifecycle holder discovery (fleet-update #91277). |
| `test_venv_sync.py` | venv_sync must work on trees where the venv does not exist yet. |
| `test_venv_sync_currency.py` | Checkout freshness follows the selected PM generation, not a second stamp. |
| `test_venv_sync_update_tree.py` | A launch never runs the completion tail beside a live update tree whose marker is gone. |
| `test_verify_console_scripts.py` | Orphan launcher discovery follows the declared console script names. |
| `test_version_command.py` | Tests for the /version slash command. |
| `test_version_info.py` | Tests: `setup_function`, `test_derived_version_shows_plus_question_for_dirty_unknown_distance`, `test_display_version_names_the_distance_without_the_commit`, `test_display_version_keeps_tagless_stamp_identity`, `test_di… |
| `test_version_info_startup_git.py` | A Hermes start from a git checkout must not walk git for the release it never uses. |
| `test_vertex_model_picker.py` | Vertex visibility in the /model picker (follow-up to PR #56688). |
| `test_vertex_provider.py` | Tests for Vertex AI runtime-provider resolution and profile registration. |
| `test_video_gen_picker.py` | Tests for plugin video_gen providers in the tools picker. |
| `test_vim_mode_command.py` | display.vim_mode: config-only vi keybindings for the CLI composer. |
| `test_voice_wrapper.py` | Tests for ``hermes_cli.voice`` — the TUI gateway's voice wrapper. |
| `test_wake_word_config_schema.py` | The config UI offers the same wake providers the runtime resolves. |
| `test_warning_callback_conservation.py` | Concrete CLI sinks own filtering; generic agent callbacks remain observable. |
| `test_web_analytics_corrupt_store.py` | A malformed state.db must not turn dashboard analytics polling into a traceback storm (#96591). |
| `test_web_build_limits.py` | Web dashboard build resource caps (issue #63338). |
| `test_web_capability_gateway_route.py` | Each web capability picks its own route: the user's own key or the Nous Tool Gateway. |
| `test_web_delegation_routing.py` | Settings › Subagents routes: ``delegation.backend`` and ``delegation.backends.*`` are read, validated and written in the TARGET profile (``?profile=``). Real plugin directory registering real delegation providers, the r… |
| `test_web_git_gh_stderr.py` | Behavioral tests for the gh wrappers' failure reporting (#87731). |
| `test_web_git_identity.py` | Review commits preserve native Git identity without enabling hooks. |
| `test_web_host_terminal.py` | Webapp host terminal: request policy, the /api/host-terminal gate, and argv resolution. |
| `test_web_host_terminal_drain_pool.py` | Retained host shells must not hold the event loop's default executor. |
| `test_web_host_terminal_lifespan.py` | Overlapping app lifespans must keep requests and shells under a live owner. |
| `test_web_host_terminal_locale.py` | Webapp host shells start with a locale the host's C library accepts. |
| `test_web_host_terminal_persistence.py` | Native shell continuity through the real /api/host-terminal route, isolated from user state. |
| `test_web_logs_async.py` | Tests: `test_get_logs_yields_while_reading_and_filtering` |
| `test_web_memory_provider_setup_install.py` | CLI/dashboard setup resolves declarations, not ambient importability. |
| `test_web_memory_user_dir_provider.py` | A memory provider installed under ``$HERMES_HOME/plugins/`` (catalog install) keeps the Desktop surfaces a bundled copy has: host-block config storage and the OAuth connect routes resolve the provider's own ``client`` /… |
| `test_web_messaging_platform_profile_scope.py` | The dashboard's channel edit routes resolve the platform against the TARGET profile's platforms, the same catalog ``GET /api/messaging/platforms?profile=`` shows: a platform plugin installed only in a secondary profile… |
| `test_web_multi_profile_scope.py` | Dashboard routers that read a named profile's config/credentials run under that profile's FULL scope (home + secrets) and never mutate the dashboard process environment. |
| `test_web_oauth_dispatch.py` | Regression tests for the OAuth dispatcher in hermes_cli.web_server. |
| `test_web_plugins_catalog.py` | Dashboard plugin-catalog surface: GET /api/dashboard/plugins/catalog merges installed state via the installer-owned install-metadata ``catalog`` record; the install endpoint has no kill-list bypass. |
| `test_web_profile_delete_settlement.py` | ``DELETE /api/profiles/{name}``: a settle-pending delete reports a partial success, not a 500. |
| `test_web_profile_soul_writes.py` | ``PUT /api/profiles/{name}/soul`` must not destroy an existing SOUL.md. |
| `test_web_profiles_model_scope.py` | ``PUT /api/profiles/{name}/model`` must validate under the target profile's secret scope. |
| `test_web_profiles_off_loop.py` | Regression tests: ``/api/profiles`` handlers must not block the event loop. |
| `test_web_provider_selection.py` | Web setup reports the selected backend without interrupting config writes. |
| `test_web_read_coalescing.py` | GET /api/profiles coalesces a poll burst before AnyIO threadpool admission (#105179). |
| `test_web_read_confinement.py` | Locked preview and review routes share the managed-file read boundary. |
| `test_web_recommended_default_profile.py` | ``GET /api/model/recommended-default?provider=nous`` answers for the requested profile. |
| `test_web_routers_destructive_profile_scope.py` | One backend serves every profile, so a REST handler that reads ``get_hermes_home()`` directly mutates the LAUNCH profile's data no matter which profile the request named. |
| `test_web_routers_endpoint_probe.py` | Endpoint-probe contract for the Desktop local/custom endpoint validators (#63472). |
| `test_web_routers_status_health.py` | ``GET /api/health`` ``commit`` contract (review G4). |
| `test_web_routers_tools_install_on_enable.py` | Install-on-enable for toolset toggles (dashboard/desktop PUT endpoint). |
| `test_web_server.py` | Tests for hermes_cli.web_server and related config utilities. |
| `test_web_server_approvals_broadcast.py` | Approvals config saves must re-emit session.info to live gateway sessions. |
| `test_web_server_asset_mime.py` | Dashboard asset MIME types are platform-independent (#28987). |
| `test_web_server_auto_archive_gateway_lock.py` | Invariant: `hermes serve`'s opportunistic auto-archive never opens a WRITABLE SessionDB for a profile whose gateway is live (#110405). |
| `test_web_server_auto_archive_profile_config.py` | Invariant: a profile's OWN ``sessions:`` config governs its store's auto-archive. |
| `test_web_server_boot_handshake.py` | Integration tests for the desktop boot handshake fix (PR #50231 / issue #50209). |
| `test_web_server_chat_workspaces.py` | Dashboard chat workspace picker: ``GET /api/chat/workspaces`` + ``/api/pty?cwd=``. |
| `test_web_server_config_offloop.py` | GET /api/config must not block the event loop on _SKILLS_PROFILE_LOCK. |
| `test_web_server_console_ws.py` | Dashboard Hermes Console websocket tests. |
| `test_web_server_cors_preflight.py` | Tests for CORS preflight ordering on the dashboard web server. |
| `test_web_server_cron_profiles.py` | Regression tests for dashboard cron job profile routing. |
| `test_web_server_cron_repeat.py` | Regression coverage for finite repeat counts in the dashboard cron create API (#68012). |
| `test_web_server_executor_isolation.py` | Control-plane routes stay available when asyncio's default pool is wedged. |
| `test_web_server_file_ticket_generations.py` | Real HTTP file tickets die with the named profile they belong to. |
| `test_web_server_file_ticket_retries.py` | A browser retry of the same download URL redeems its ticket again, a few times (#144667). |
| `test_web_server_files.py` | Tests for the dashboard-managed file browser API. |
| `test_web_server_fs.py` | Tests: `client`, `docker_volumes`, `_no_scope_builder`, `test_fs_list_sorts_and_hides_noise`, `test_fs_routes_workspace_reads_to_ssh_backend`, `test_fs_backend_resolves_ssh_connection_from_profile_env` … |
| `test_web_server_fs_session_workspace.py` | WA-5: a Webapp file route that names a session resolves ``/workspace`` in THAT session's per-workspace Docker sandbox (#143655's mapping), and refuses a session it cannot see. |
| `test_web_server_gateway_health.py` | Tests for _probe_gateway_health() — cross-container gateway detection, including the bounded JSON response body reads (moved from test_web_server.py so that file keeps its main-pinned line cap; moved code keeps its cap). |
| `test_web_server_gateway_topology.py` | Tests for the /api/status profile + gateway topology readout. |
| `test_web_server_git.py` | Tests: `reset_gh_auth_probe_state`, `_GhProbe`, `test_gh_auth_concurrent_cache_misses_share_one_probe`, `test_gh_auth_refresh_waits_out_a_probe_started_before_it`, `client`, `_git` … |
| `test_web_server_host_header.py` | Tests for GHSA-ppp5-vxwm-4cf7 — Host-header validation. |
| `test_web_server_idle_exit.py` | A Desktop-owned ``serve --isolated`` backend over SSH must retire itself once no client has been connected for the grace window and no turn is running (#101626): it is detached from any parent on purpose, so the client… |
| `test_web_server_idle_proof.py` | A Desktop-pooled ``hermes serve`` child must PROVE it is idle before the Desktop may retire it for a foreground open (supersedes #104871, whose idle signal was renderer bookkeeping). |
| `test_web_server_launch_env_freeze.py` | The launch-env freeze is the LAST boot step, not the first. |
| `test_web_server_listener_logging.py` | Building a listener's ``uvicorn.Config`` must leave Hermes's own file logging alone. |
| `test_web_server_media_async.py` | Dashboard media reads must not run on the event-loop thread. |
| `test_web_server_messaging_posture.py` | The Channels "Test" button must answer the auth-posture question too (#66030). |
| `test_web_server_messaging_profiles.py` | Regression tests for profile-scoped dashboard Channels endpoints. |
| `test_web_server_messaging_stale_runtime.py` | A stopped gateway's per-platform verdict is history, not current state. |
| `test_web_server_nous_recommended_default.py` | Dashboard recommended-default model: the paid-tier Nous cost-safe policy (#51491). |
| `test_web_server_owner_exit.py` | A Desktop-over-SSH ``serve --isolated`` backend retires itself once the Desktop's ownership lock names a newer spawn (#132034): a reconnect that cannot prove the old pid is its own drops the lock without signalling it,… |
| `test_web_server_plugin_secret_scope.py` | A plugin API handler's ``get_secret()`` resolves the requested profile's credentials (#120310), through the real mount path: the launch profile's copy in-process, a ``?profile=`` profile's own copy in its plugin host (P… |
| `test_web_server_profile_unification.py` | Regression tests for the machine-dashboard multi-profile unification. |
| `test_web_server_pty_idle_backoff.py` | Regression: dashboard PTY pump must back off when the terminal is idle. |
| `test_web_server_pty_import.py` | Test the platform-branched PTY bridge import in hermes_cli.web_server_chat. |
| `test_web_server_pty_reconnect.py` | Focused tests for dashboard PTY reconnect breadcrumbs. |
| `test_web_server_session_owner_forward.py` | A standalone dashboard's mutations must reach the live gateway owner (#138915). |
| `test_web_server_session_search.py` | Tests: `_FakeSessionDB`, `test_desktop_session_search_merges_id_matches_before_content_matches`, `test_desktop_session_search_stamps_the_requested_profile`, `test_desktop_session_search_attaches_profile_to_rich_results`… |
| `test_web_server_session_search_titles.py` | GET /api/sessions/search must match session titles, not only ids and FTS5 message content. |
| `test_web_server_sessiondb_eventloop.py` | Dashboard session routes must run SessionDB open + work off the event loop. |
| `test_web_server_sessions_compression.py` | Dashboard sessions endpoints vs compression-continuation children (#54298, #57543). |
| `test_web_server_skew_exit.py` | A Desktop-over-SSH ``serve --isolated`` backend retires itself once the install under it moved to new code: nothing on its host may restart it (only the remote client holds its token), so without this it runs the pre-up… |
| `test_web_server_skill_editor.py` | Tests for the dashboard skill editor endpoints and cron skill attachment. |
| `test_web_server_skills_profiles.py` | Regression tests for dashboard profile-scoped skills/toolsets management. |
| `test_web_server_speak_stream.py` | /api/audio/speak-stream — desktop streaming TTS over WebSocket. |
| `test_web_server_ssh_media_stream.py` | WA-5 part 4: an SSH profile's audio/video streams from the SSH workspace with HTTP Range, behind the same ticket, profile and file checks as the host path. Fake SSH adapters only. |
| `test_web_server_status_topology_cache.py` | Regression tests for the /api/status profile-topology cache. |
| `test_web_server_stt_lease.py` | ``POST /api/audio/stt-lease`` — desktop voice input as STT warm-up/release. |
| `test_web_server_surface.py` | Routes only the Webapp or native Desktop's Web Access pane use exist only on the surfaces that use them. |
| `test_web_server_tts_lease.py` | ``POST /api/audio/tts-lease`` — desktop speech toggles as TTS warm-up/release. |
| `test_web_server_update_status.py` | Dashboard update status reads the ROOT home's shared update.log, correlated by action id. |
| `test_web_server_ws_ping.py` | Test that start_server configures ws-ping keepalive. |
| `test_web_status_watchdog_surfaces.py` | ``/api/status`` agrees with ``hermes gateway status`` on the two #113372 shapes: |
| `test_web_terminal_backend_profile_scope.py` | ``PUT /api/tools/terminal/backend`` validates the backend against the TARGET profile's plugin backends, the same list ``GET /api/tools/terminal/backends?profile=`` shows: a backend plugin installed only in a secondary p… |
| `test_web_toolset_profile_scope.py` | The dashboard's toolset routes validate the toolset name against the TARGET profile's toolsets, the same list ``GET /api/tools/toolsets?profile=`` shows: a plugin toolset installed only in a secondary profile (spotify,… |
| `test_web_ui_build.py` | Web launch keeps freshness/serialization but never masks a failed build. |
| `test_web_unknown_profile_404.py` | An unknown ``?profile=`` is the profile scope's 404 on every dashboard route, never a generic 500 from a handler's catch-all. |
| `test_webapp_access.py` | Remote Webapp access (``hermes_cli.webapp_access``, ``/api/webapp-access/*``). |
| `test_webapp_access_ports.py` | Which port Web Access serves a gateway's Webapp on (``hermes_cli.webapp_access._port_to_serve``). |
| `test_webapp_access_restart_failure.py` | A Web Access restart whose child exits without replacing the gateway says why on ``/status``. |
| `test_webapp_access_status_lock.py` | The Web Access pane's status poll never holds the process-wide skills lock across its gateway query. |
| `test_webapp_desktop_plugin_halves.py` | On a headless host the Webapp itself copies agent+desktop packages' desktop halves into ``<root>/desktop-plugins``, the copy native Desktop makes in Electron (``reconcileUnifiedDesktopHalves``) and nothing else makes wh… |
| `test_webapp_desktop_plugins.py` | The Webapp serves this host's desktop plugins to the browser's plugin loader. |
| `test_webapp_file_urls.py` | The gateway resolves the Webapp's requests for a ``file:`` URL to the file the URL names. |
| `test_webapp_gated_sign_out.py` | Behind the sign-in gate, signing the Webapp out signs every browser out. |
| `test_webapp_gateway_ticket.py` | The Webapp's live socket ticket is minted by the server that serves the page. |
| `test_webapp_launch.py` | The private launch ticket crosses a browser launcher's argv, so only the server user may spend it. |
| `test_webapp_launcher.py` | ``hermes webapp`` opens the browser-hosted Desktop that the gateway serves. |
| `test_webapp_launcher_reasons.py` | ``hermes webapp`` says why the Webapp is off. |
| `test_webapp_page_csp.py` | The privileged page authorizes its bootstrap and bundle, never arbitrary inline script. |
| `test_webapp_page_previews.py` | Preview CDN loads use the isolated document policy, never the app policy. |
| `test_webapp_preview_documents.py` | Preview policy is independent of the app, without a new private-content endpoint. |
| `test_webapp_private_bootstrap.py` | Webapp's public HTML must not grant the privileged RPC/host-file credential. |
| `test_webapp_private_launch.py` | ``hermes webapp`` where nothing checks who redeems a one-use launch link (macOS, the BSDs, illumos, WSL). |
| `test_webapp_renderer_build.py` | The Webapp renderer (``dist-webapp``): verified reuse, one build at a time, rebuilt only when stale. |
| `test_webapp_sign_out_sockets.py` | Signing the Webapp out closes every socket the old browser credential opened. |
| `test_webapp_socket_profile_scope.py` | The Webapp's gateway socket answers for the profile its ticket names, on a multiplexed gateway. |
| `test_webapp_socket_tickets.py` | Each Webapp socket ticket opens only the socket it was minted for. |
| `test_webapp_status_signed_out.py` | The gateway's Webapp answers a signed-out ``/api/status`` with liveness and the sign-in shape only. |
| `test_webapp_ticket_profile.py` | A Webapp tab's socket answers for the profile its gateway ticket names. |
| `test_webapp_upload_limit.py` | Real ASGI regressions for the Webapp's pre-parser upload limit (``hermes_cli/web_upload_limit.py``). |
| `test_webapp_upload_security.py` | Real ASGI checks of the Webapp's same-origin gate for cookie-authenticated writes. |
| `test_webapp_uploads.py` | Tests: `_client`, `_docx_upload`, `test_browser_document_upload_remains_extractable_after_file_attach`, `test_safe_upload_filename_is_bounded_basename_with_document_suffix`, `test_browser_upload_stages_bytes_under_herme… |
| `test_webapp_window_handoff.py` | A child tab may receive local authority only through a one-use handoff. |
| `test_webhook_cli.py` | Tests for hermes_cli/webhook.py — webhook subscription CLI. |
| `test_webhook_cron_profile.py` | Webhook cron references belong to the route's profile (#139332). |
| `test_welcome_trial.py` | The desktop's welcome trial (``hermes_cli.welcome_trial``): who may claim it, what a claim leaves behind, which guests keep the free model, and that a connector guest never asks for inference. |
| `test_whatsapp_cloud_setup.py` | Tests for the WhatsApp Cloud API setup wizard. |
| `test_whatsapp_dashboard_repair.py` | Dashboard recovery must bypass revoked credentials without losing them. |
| `test_whatsapp_missing_runtime.py` | A successful PM preparation must still supply a runnable bridge binary. |
| `test_whatsapp_onboarding.py` | Tests: `_FakeProc`, `test_apply_whatsapp_onboarding_saves_pairing_policy`, `test_start_whatsapp_onboarding_existing_creds_returns_linked_account` |
| `test_whatsapp_setup_ordering.py` | Regression tests for ``cmd_whatsapp`` env-var write ordering. |
| `test_win_pty_bridge.py` | Unit tests for hermes_cli.win_pty_bridge — ConPTY spawning + byte forwarding. |
| `test_windows_gateway_cold_start_desktop_lifecycle.py` | #76129: post-update Windows cold-start must not steal Desktop-owned lifecycle. |
| `test_windows_gateway_job_teardown.py` | Regression tests for #48820 (4th repro): job-object teardown killed the post-update respawned gateway silently, and the updater printed "✓ Restarting Windows gateway profile(s)" anyway. |
| `test_windows_relaunch_ready_poll.py` | Post-update relaunch verification polls every paused target at once (#132338 review, kshitij). |
| `test_windows_relaunch_verify_budget.py` | Post-update gateway relaunch verification: watcher identity and liveness budget (#107002). |
| `test_windows_ssh_runtime_inventory.py` | Desktop's Windows SSH inventory reads through the canonical root and profile predicate. |
| `test_windows_ssh_runtime_ownership.py` | Boot-selecting runtime ownership uses the actual argv parser on native processes. |
| `test_windows_update_restart_reconciliation.py` | Regression: Windows gateway pause/resume must feed the #91277 Phase 2 plan-vs-execution reconciliation, not report a correctly-relaunched Windows gateway as "unaccounted". |
| `test_worker_first_always_grant.py` | An "Always" approval inside a frozen managed worker reaches config.yaml. |
| `test_worktree.py` | Tests for git worktree isolation (CLI --worktree / -w flag). |
| `test_worktree_command.py` | Tests for the CLI ``/worktree`` command handler. |
| `test_worktree_gc.py` | Behavior contracts for hermes_cli.worktree_gc (attended reclaim). |
| `test_worktree_lock_old_git.py` | Worktree lock state without ``git worktree list --porcelain -z`` (git < 2.36, e.g. Ubuntu 22.04). |
| `test_worktree_pushed_tier.py` | Pushed-branch tier of the worktree pruners (#A, Aug 2026). |
| `test_worktree_retained_cwd_identity.py` | A retained ``--tui -w`` tree stays live when its session's stored cwd spells the same native path differently (Windows: case-insensitive, either separator). |
| `test_worktree_security.py` | Security-focused integration tests for CLI worktree setup. |
| `test_worktree_selfheal.py` | Tests for git self-heal: atomic worktree-add failure cleanup + pack maintenance. |
| `test_worktree_snapshot_prune.py` | Invariants of the snapshot-then-delete worktree sweep (``worktrees.archive_dirty``). |
| `test_worktree_sync_base.py` | Tests for worktree base-ref resolution — branch from the fresh remote tip. |
| `test_ws_auth_display_ticket.py` | A Bot Desktop display ticket admits one RFB bridge on ``/api/display/ws`` — it must never pass as a full login on ``/api/ws`` (the reverse of ``test_display_ws_ticket``, which refuses gateway tickets there). |
| `test_xai_curated_models.py` | Regression tests for xAI curated + models.dev picker-time merge. |
| `test_xai_model_flow.py` | Tests: `test_xai_model_flow_reauth_uses_standard_radio_prompt`, `test_xai_model_flow_cancel_skips_reauth`, `test_auth_credentials_choice_falls_back_to_numbered_prompt` |
| `test_xai_oauth_profile_auth.py` | Regression tests for xAI OAuth auth resolution in profile/cron contexts. |
| `test_xai_oauth_refresh.py` | Tests: `_jwt_with_exp`, `test_xai_oauth_token_expiring_uses_one_hour_skew`, `test_xai_proactive_refresh_skew_short_lived_token` |
| `test_xai_oauth_writethrough.py` | Regression tests for xAI OAuth refresh write-through to the global root. |
| `test_xai_provider_labels.py` | Regression tests for xAI provider label disambiguation. |
| `test_xai_retirement.py` | Unit tests for hermes_cli.xai_retirement (May 15, 2026 model retirement). |
| `test_xiaomi_provider.py` | Tests for Xiaomi MiMo provider support. |
| `test_yolo_startup_order.py` | Regression tests for #60328: --yolo must set HERMES_YOLO_MODE in main() before _prepare_agent_startup() triggers tool imports. |
| `web_routers/__init__.py` | Package marker / package-level exports |
| `web_routers/test_chat_ws_keepalive_takeover.py` | A takeover that cancels a keep-alive /api/pty write is not an input stall. |
| `web_routers/test_chat_ws_lease_holder.py` | The dashboard reads a resumed chat's lease holder from the HOME that chat runs in. |
| `web_routers/test_codex_device_login_transient_retry.py` | Dashboard/Desktop Codex device-code login survives transient transport blips. |

## `tests/hermes_platform/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `test_declaration.py` | Declaration parser, availability, and skill-gate contracts. |
| `test_facts.py` | Tests: `test_normalize_arch`, `test_windows_native_arch_precedence`, `test_windows_display_adapters_classify_the_gpu`, `test_cpu_vendor_from_cpuinfo`, `test_parse_cpuinfo_fallbacks`, `cleared_fact_caches` … |
| `test_gpu_adapters.py` | DXGI's adapter list, read live on Windows. |
| `test_host_summary.py` | ``hermes_platform.host.summary``: the machine and account facts desktop first-run onboarding reads. |
| `test_import_hygiene.py` | Tests: `test_platform_modules_only_import_stdlib_and_hermes_platform` |
| `test_products.py` | Tests: `test_nvidia_platform_from_host_facts`, `test_linux_nvidia_gpus_come_from_the_driver_files_without_a_process` |
| `test_resolver_app.py` | Tests: `_bundle`, `_server_json`, `_resolver`, `test_locate_reports_expanded_path_when_missing`, `test_bundle_presence_and_plist_version`, `test_star_segment_tries_the_highest_version_first` … |
| `test_resolver_core.py` | Tests: `_make_exe`, `test_path_hit_comes_first_and_known_dirs_are_still_recorded`, `test_known_dir_hit_when_path_misses`, `test_empty_path_is_a_miss_not_ambient`, `test_absent_and_none_both_mean_ambient`, `test_explicit… |

## `tests/hermes_state/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `_wal_generation_harness.py` | Shared harness for the lost-WAL-generation tests (#105670 / #105726). |
| `conftest.py` | Shared fixtures for tests/hermes_state. |
| `test_append_message_after_close.py` | Regression tests for #94736 — append_message after close() raced a live writer. |
| `test_append_messages_batch.py` | Tests for SessionDB.append_messages_batch (#23254 salvage). |
| `test_auto_archived_lineage_reactivation.py` | A chat the idle sweep archived must reappear once it is live again (#117713). |
| `test_auto_vacuum_holder_gate.py` | Automatic state.db maintenance never VACUUMs under a foreign writer (#110054). |
| `test_auto_vacuum_in_process_holder_gate.py` | Automatic VACUUM is refused under a LIVE in-process holder — and never under a retired one. |
| `test_automatic_ended_stamp.py` | Regression tests for #88197 — a dirty automatic ``ended_at`` stamp on a live compression parent must not wedge rotation. |
| `test_aux_usage_accounting.py` | Tests for auxiliary usage accounting (issue #23270). |
| `test_background_review_session_isolation.py` | Tests for background-review session-store isolation (hermes_state). |
| `test_bounded_recent_sessions.py` | Regression coverage for latency-bounded recent-session browsing. |
| `test_canonical_title_guard.py` | The canonical Bot Chat's title is its identity — renames must be refused. |
| `test_clean_close_residual_poison.py` | A clean ``SessionDB.close()`` racing a live caller must never be classified as an externally deleted WAL generation (regression for #116244, sibling of #105567). |
| `test_compacted_message_reactions.py` | Visible archived messages keep the same once-only reaction contract. |
| `test_compacted_tool_result_paints_once.py` | A compaction carries a tool result forward as a shortened stub (same ``message_uid``). Every display read paints that tool result once, as the archived full original, while the model keeps the stub and no stored row cha… |
| `test_compaction_carried_tail_not_cloned.py` | Regression for #137197: a compaction must not store a carried message twice. |
| `test_composite_carrier_rewind.py` | Transactional persistence contracts for composite compaction carriers. |
| `test_compression_created_source.py` | A managed worker's usage write heals a NULL compression child to the agent surface. |
| `test_compression_lease_refresh_before_publish.py` | Tests for RC2: pre-publication lease refresh in publish_compression_child. |
| `test_compression_lineage_guard.py` | Regression tests for stale writes after a compression session split. |
| `test_compression_watermark_commit.py` | Watermark commit: concurrent appends survive in-place compaction (#75316). |
| `test_conftest_wal_gate.py` | The conftest WAL gate must agree with hermes_state, and must not import it. |
| `test_conversation_root.py` | Tests for SessionDB.get_conversation_root — stable conversation id resolution. |
| `test_corrupt_row_robustness.py` | One corrupt timestamp row must degrade to one '?' cell, never kill a whole listing/export/report. |
| `test_cron_run_sessions.py` | A cron job's run history includes the runs the unified gateway runtime creates (#138812). |
| `test_cross_vm_fs_wal_refusal.py` | Cross-VM filesystem (virtiofs/9p) WAL refusal — port of openclaw#120597. |
| `test_dedupe_migration_contention.py` | The v25 dedupe migration must degrade gracefully on a contended DB. |
| `test_delegate_cascade.py` | Regression tests for delegate-child cascade collection (#49148). |
| `test_delegate_child_routing_inheritance.py` | A delegate/branch child must never inherit its parent's gateway routing columns. |
| `test_delete_branched_root_leftovers.py` | Delete of a compressed + branched root (NF4): the /branch child survives as its own conversation, its ``_branched_from`` naming the deleted segment, and the delete's tombstones age out after the retry horizon. The retir… |
| `test_delete_compression_chain.py` | Chain-aware deletion invariants for the dashboard delete endpoints (#57543). |
| `test_delete_mode_read_busy_wait.py` | DELETE-journal readers wait out another process's commit instead of raising ``database is locked``. |
| `test_delete_session_write_guards.py` | Invariant tests for entry-side deletion refusal on active write guards (#123583). |
| `test_deleted_wal_checkpoint_guard.py` | Regression for #105670: a halted split-brain/replaced handle must not run ANY checkpoint. |
| `test_deleted_wal_generation_guard.py` | Refuse SessionDB open/write when a deleted WAL generation is still held. |
| `test_disk_full_error.py` | is_disk_full_error classifies ENOSPC / SQLITE_FULL failures. |
| `test_display_dedupe_pruned_tool_payload.py` | #117750: a prune rewrite of a carried-forward tool call must not split the logical event into a second display identity. |
| `test_display_projection_parity.py` | Every display projection of a compacted session must agree. |
| `test_display_read_identity_work.py` | A display read hashes a display identity only where a removed copy could match it (RT-39). |
| `test_display_read_removed_rows.py` | Display reads hide a message whose newest copy was removed (rewound, or replaced by a newer copy), so they need the removed rows' identities, but never their bodies: ``assert_resume_safe`` does not count those rows, and… |
| `test_display_split_heal.py` | A split display generation must still project as one message (issue #122167). |
| `test_downgrade_delete_guard.py` | A release that predates the gateway runtime refuses, in words, to delete a ledgered session. |
| `test_empty_sweep_archived_transcript.py` | The empty-session sweep must not eat a rewound / compacted transcript (#95868). |
| `test_fts_cjk_bigram.py` | Tests for the messages_fts_cjk CJK-bigram index (salvaged from PR #65544). |
| `test_fts_fresh_bootstrap_admission.py` | Fresh state.db FTS bootstrap must honor cross-process rebuild admission. |
| `test_fts_holder_instance_scope.py` | Instance-scoping of the uninspectable-holder fallback. |
| `test_fts_index_fail_open.py` | Regression tests for #97794: an FTS5-index-only failure must not kill the turn, and an FTS-scoped error that escapes must not be rendered as whole-file damage. |
| `test_fts_layout_drift.py` | FTS storage-layout drift: one structural answer shared by the stamp, the update notice and doctor. |
| `test_fts_optimize_progress.py` | `hermes sessions optimize-storage` runs in the foreground behind the held-store refusal, so it must report real progress in every phase, never idle between chunks, and end (not spin) when a chunk cannot succeed. |
| `test_fts_orphan_shadow_repair.py` | #103840: a ``sqlite3 .recover`` restore re-emits FTS5 shadow tables as ordinary tables but cannot re-emit the ``CREATE VIRTUAL TABLE`` row. The next SessionDB open then failed in ``_ensure_fts_schema`` with "fts5: error… |
| `test_fts_projection_integrity.py` | Regression for the ``messages_fts`` external-content drift (issue #114169). |
| `test_fts_rebuild_admission.py` | Cross-process admission for full structural FTS rebuilds (PR #93200 class). |
| `test_fts_rebuild_corruption_class.py` | ``rebuild_fts()`` must catch the corruption class it exists to recover from (#133375). |
| `test_fts_runtime_rebuild.py` | Bounded FTS-corruption recovery on live SessionDB paths. |
| `test_fts_tool_write_bounds.py` | Tests: `_long_message`, `db`, `test_new_tool_rows_bound_fts_content_but_explicit_tool_search_is_complete`, `test_reopen_keeps_bounded_rows_consistent_without_a_marker`, `test_full_rebuild_keeps_every_tool_row_bounded`,… |
| `test_fts_trigram_cron_exclusion.py` | Cron-source exclusion from the external-content trigram FTS index. |
| `test_fts_trigram_subagent_exclusion.py` | Delegate-child (subagent) transcripts stay out of the trigram FTS index (v30). |
| `test_fts_update_of_narrowing.py` | FTS UPDATE OF narrowing + migration (#73639 retargeted onto split SessionDB). |
| `test_get_anchored_view.py` | Tests for SessionDB.get_anchored_view — anchored window + session bookends. |
| `test_get_messages_around.py` | Tests for SessionDB.get_messages_around (anchored-window primitive). |
| `test_get_messages_include_compacted.py` | Tests for SessionDB.get_messages(include_compacted=...). |
| `test_guest_durability_barriers.py` | Guest ledger connections must inherit the configured database.synchronous. |
| `test_hermes_state.py` | Tests for hermes_state.py — SessionDB SQLite CRUD, FTS5 search, export. |
| `test_hermes_state_archive_open.py` | `hermes sessions archive --include-open`: archive (reversible) may reach never-ended sessions (#139597). |
| `test_hermes_state_compression_busy_retry.py` | Appends flow freely during compression; the commit preserves them (#75316). |
| `test_hermes_state_compression_locks.py` | Tests for ``SessionDB`` compression-lock primitives. |
| `test_hermes_state_ids.py` | Session-id minting contract: every surface that creates a session mints through ``hermes_state_ids.new_session_id`` and the id it produces is what lost-and-found salvage classifies as a session id (the shape is the reco… |
| `test_hermes_state_readonly_preflight.py` | Tests for the read-only DB preflight (port of Kilo-Org/kilocode#12508). |
| `test_hermes_state_ux_messages.py` | Plain-language contracts for hermes_state user-facing errors (CLI UX message campaign, cluster D). |
| `test_hermes_state_wal_fallback.py` | Tests for the WAL→DELETE journal-mode fallback on NFS / SMB / FUSE. |
| `test_history_login_label.py` | A dashboard login may act on the ``<provider>:<user>`` rows Desktop stamps for it. |
| `test_import_deleted_session.py` | An import never restores a user-deleted session id: it refuses it by name at import time. |
| `test_isolation_marker_env.py` | Subprocess-surviving isolation marker (#82770). |
| `test_journal_mode_config.py` | Behavioral coverage for #68545's centralized journal-mode setting. |
| `test_journal_mode_upgrade_warning.py` | An existing database's journal mode must not be rewritten silently (#89293). |
| `test_lease_pid_namespace.py` | PID-namespace qualification for state.db lock/lease holder probes. |
| `test_ledger_delete_consistency.py` | Legacy delete/prune paths, local reset and adopted-worker settlement stay consistent with the ``session_admissions`` / ``worker_executions`` ledger (ON DELETE RESTRICT). |
| `test_list_sessions_recency.py` | Recency order of ``list_sessions_rich(order_by_last_active=True)``. |
| `test_live_db_guard_ancestry.py` | The live-DB guard must survive a scrubbed child environment (#82770). |
| `test_live_db_isolation_guard.py` | Behavioral tests for the live-DB test-isolation guard. |
| `test_local_lineage_cache.py` | Regression for #143833: reuse reset projections without stale SQLite snapshots. |
| `test_lockguard_fcntl_tolerance.py` | A partial or lookalike ``fcntl`` must disable the WAL lock guard, never kill the process. |
| `test_message_uid.py` | ``messages.message_uid``: a durable per-message id that survives every host copy path. |
| `test_named_profile_session_db.py` | Named-profile agents must FAIL CLOSED when their profile state.db won't open. |
| `test_never_active_keyed_prune.py` | Sweeping never-active keyed gateway rows (#82770). |
| `test_no_locked_readers_gate.py` | Pattern-C gate: pure-read SessionDB methods must not take the writer lock. |
| `test_no_more_rows_retry.py` | Retry of transient 'no more rows available' engine errors (#74934 port). |
| `test_orphan_gateway_session_repair.py` | Repair of gateway sessions that lost their routing identity (#82616). |
| `test_orphan_sweep_cross_backend.py` | Regression tests for #94895: startup orphan sweep must respect cross-backend liveness. |
| `test_pinned_archived_sidebar.py` | Pinned rows must stay reachable from the sidebar session query. |
| `test_pinned_lineage.py` | A pin covers the whole conversation, including segments compression publishes after it. |
| `test_placeholder_provenance.py` | Placeholder-first creation must not hide real CLI sessions (#138831). |
| `test_prune_activity_recency.py` | Tests: `test_prune_sessions_respects_touch_session_activity`, `test_prune_keeps_the_compressed_segments_of_a_chat_still_in_use` |
| `test_purge_profile_state.py` | Regression tests for profile-keyed state purge on `hermes profile delete`. |
| `test_read_path_transient_ioerr.py` | #100871: a transient SQLITE_IOERR on a warm pooled read connection is retried on the same connection, then surfaced -- never quarantined, never a close+reopen. |
| `test_readonly_fts_decode_error.py` | Test that read-only SessionDB survives invalid UTF-8 in FTS content (issue #98924). |
| `test_reasoning_roundtrip.py` | Round-trip tests for the structured reasoning columns. |
| `test_rebuild_table_atomic.py` | ``_rebuild_table`` is one write transaction (port of qwibitai/nanoclaw#3766's idea: hold the write lock across a migration so two openers cannot interleave). |
| `test_recent_model_route.py` | get_recent_session_model_route picks the newest route deterministically on equal last_seen. |
| `test_rekey_profile_state.py` | Regression tests for profile-name-keyed state migration on `hermes profile rename`. |
| `test_remove_session_files_glob_escape.py` | Pruned-session file removal is id-scoped even when the id carries glob metacharacters. |
| `test_repaired_history_commit_coverage.py` | The alternation repair's provenance keeps compaction from archiving rows the compressor never held. |
| `test_replace_messages_archive_siblings.py` | Sibling-site regression tests for the #80216 bug class. |
| `test_replace_messages_archives_suffix_only.py` | #82956: ``replace_messages(archive_dropped=True)`` must archive only the dropped suffix. |
| `test_reset_lineage_delete_queued_work.py` | A local reset conversation with accepted queued work survives every legacy delete and sweep of its current physical segment (JoaoMarcos44 R1, andrexibiza 8, dokterdok corr-reset-delete). |
| `test_reset_owner_housekeeping.py` | Housekeeping keeps the logical owner of a retained local reset child. |
| `test_resolve_resume_session_id.py` | Regression guard for #15000: --resume <id> after compression loses messages. |
| `test_restore_alternation_repair.py` | get_messages_as_conversation(repair_alternation=True) — heal durable alternation violations at the restore boundary. |
| `test_resume_summary_carrier_once.py` | Resuming a compressed conversation shows each message once. |
| `test_retired_fence_outlives_horizon.py` | The retired-session marker is the deletion fence: the prune pass reclaims a deleted session's tombstones after the retry horizon, but never a user delete's marker, so the id stays deleted. A housekeeping sweep's marker… |
| `test_retired_wal_generation_capture.py` | Durable capture of a lost WAL generation (#105670 follow-up). |
| `test_rewind_surfaces_invariant.py` | Invariant: every /undo + /retry surface persists through ``SessionDB.rewind_user_turn``, so the same session rewound through the CLI, the gateway store, or the TUI helper leaves the IDENTICAL active message set, and an… |
| `test_runtime_admission.py` | Transactional contracts against exclusively owned temporary profile databases. |
| `test_runtime_adoption.py` | Tests: `append`, `test_explicit_worker_adoption_preserves_claim_without_reexecution`, `test_unknown_resolution_atomically_revokes_worker_before_unblocking` |
| `test_runtime_destructive_mutations.py` | Deletion cannot erase an admitted input or an adopted worker. |
| `test_runtime_import_mutations.py` | Import rows and retry receipt either commit together or not at all. |
| `test_runtime_mutation_actions.py` | Action-specific mutations share the canonical receipt transaction. |
| `test_runtime_mutation_retired_import.py` | A retired physical ID cannot be assigned to a different imported transcript. |
| `test_runtime_mutations.py` | Revision, replay and business-rule invariants on real isolated SQLite. |
| `test_runtime_recovery.py` | Tests: `legacy`, `row`, `test_frozen_legacy_import_preserves_work_without_branch_theft`, `test_legacy_import_failure_rolls_back_rows_and_marker` |
| `test_runtime_rewind_carrier_handoff.py` | An owner ``rewind`` of a composite compaction carrier keeps its handoff (main parity). |
| `test_runtime_rewind_mutations.py` | Rewind fences the generation and preserves archived history. |
| `test_runtime_schema.py` | Real SQLite schema reconciliation and storage-failure controls. |
| `test_runtime_worker.py` | Tests: `setup_worker`, `append`, `finish`, `test_worker_receipts_require_exact_sequence_assignment_and_adoption`, `test_worker_mutation_and_receipt_roll_back_together`, `test_worker_append_preserves_compression_write_gu… |
| `test_runtime_worker_children.py` | Owner-reserved delegated children of a worker execution (#141793): the owner mints every child, caps them, scopes their writes to their own row, and retires them with their parent. |
| `test_runtime_worker_compaction.py` | Watermarked compaction and rotation share the worker receipt transaction. |
| `test_runtime_worker_compression.py` | Worker compression retains local guard and transcript contracts. |
| `test_runtime_worker_compression_admission.py` | Physical worker rotation cannot re-key an accepted input or unblock its FIFO. |
| `test_runtime_worker_compression_annotations.py` | Compaction receipts must refresh the producer's row identities. |
| `test_runtime_worker_compression_cleanup.py` | Compression cleanup keeps physical and logical lease identities separate. |
| `test_runtime_worker_compression_flush.py` | Compression's pre-publication flush uses the ordinary annotated append helper. |
| `test_runtime_worker_context.py` | Constructor context is assignment-scoped and shares durable mutation receipts. |
| `test_runtime_worker_history.py` | Read receipts preserve replay markers and distinct cache/attribution roots. |
| `test_runtime_worker_lifecycle.py` | Worker lifecycle parity on reserved rows; compose the documented parent hooks. |
| `test_runtime_worker_metadata.py` | Ranked labels and exact provider-side data share assignment receipts. |
| `test_runtime_worker_operations.py` | Worker receipts cover the real transcript serializer, not a text-only substitute. |
| `test_runtime_worker_read_fence.py` | Worker read receipts leave the session CAS fence where a client last saw it (W14). |
| `test_runtime_worker_rotation_automation.py` | Worker rotation carries automation in the publication transaction. |
| `test_runtime_worker_title_retry.py` | Expected title conflicts are committed outcomes, not failed persistence. |
| `test_runtime_worker_turn_cleanup.py` | Logical turn cleanup remains holder-fenced after physical rotation. |
| `test_runtime_worker_usage.py` | Tests: `test_usage_receipt_includes_route_rows_and_rolls_back_on_receipt_failure`, `test_worker_voice_turn_usage_counts_but_never_rewrites_the_session_route` |
| `test_schema_read_probe.py` | Contract tests for schema_read_probe_statements(). |
| `test_search_or_relaxed_fallback.py` | OR-relaxed zero-result retry for paraphrased session search recall. |
| `test_session_archived_round_trip.py` | Round-trip export/import must restore archived message state (#122679). |
| `test_session_archiving.py` | Tests: `db`, `_compression_pair`, `test_archiving_compression_tip_archives_projected_root`, `test_unarchiving_compression_tip_unarchives_projected_root`, `test_archived_only_view_includes_hidden_archived_sessions`, `_st… |
| `test_session_db_acp_cwd_backfill.py` | Repair ACP rows whose workspace lives only in the model_config JSON. |
| `test_session_db_context_manager.py` | ``SessionDB`` must support ``with``, so an owning scope releases its fds. |
| `test_session_db_leak_sweep.py` | Suite-wide SessionDB leak-closing contract (OOM incident 20260816). |
| `test_session_db_profile_stamp.py` | SessionDB stamps its own store's profile onto new session rows (#99222). |
| `test_session_db_read_conn_pool.py` | The SessionDB read path must not leak one connection per (SessionDB x thread). |
| `test_session_db_read_path_split.py` | Tests for the SessionDB read-path split (pooled read-only connections). |
| `test_session_delete_hook.py` | ``on_session_delete`` (#124511): every committed delete or deliberate archive notifies plugins once. |
| `test_session_delete_profile_isolation.py` | Real-path proof for #78836: DELETE against the wrong profile is already_absent. |
| `test_session_export_timings.py` | Session export timing evidence. |
| `test_session_git_metadata_generation.py` | Cross-process ordering for asynchronous session Git metadata probes. |
| `test_session_hidden.py` | Tests: `db`, `test_hidden_excluded_by_default_included_on_request` |
| `test_session_id_recognition_recovery.py` | Session recovery must recognise every session-id shape this repo really mints. |
| `test_session_import_keep_flags.py` | A restored or adopted session keeps the user's durable flags. |
| `test_session_import_value_validation.py` | Session-import boundary validation for values later read by session APIs. |
| `test_session_lifecycle_status.py` | Lifecycle status classification for session pickers. |
| `test_session_list_index_choice.py` | Session-list reads stay on the (session_id, timestamp) index whatever the planner stats say (#119403). |
| `test_session_list_page_cost.py` | A recency-ordered session page pays the row projection only for its own rows (#119403). |
| `test_session_md_export.py` | Tests: `test_export_candidates_via_prune_filters_ended_old_sessions`, `test_get_compression_lineage_returns_only_compression_chain`, `test_fork_children_created_before_continuation_do_not_hijack_lineage` |
| `test_session_model_usage_pk_heal.py` | Unconditional session_model_usage PK heal (#73823, salvage of #73838). |
| `test_session_read_state.py` | Tests: `db`, `_last_read`, `_row`, `test_untracked_sessions_are_read`, `test_mark_read_then_new_activity_flips_back_to_unread`, `test_mark_unread_explicitly` … |
| `test_session_turn_lease.py` | Cross-process session turn lease behavior (#84234). |
| `test_session_workspace_binding.py` | Session <-> workspace grouping key (hermes_state_sessions.workspace_key). |
| `test_shared_session_db_registry.py` | Shared SessionDB registry lifecycle regressions (#90837 review). |
| `test_show_subagents_listing.py` | ``sessions.show_subagents`` re-admits delegate runs to human-facing session lists (#97202). |
| `test_sqlite_lock_safe_inspection.py` | POSIX advisory locks must survive Hermes' own database inspection. |
| `test_sqlite_wal_reset_gate.py` | SQLite WAL-reset vulnerability gate (issue #69784). |
| `test_stale_tool_call_marker_session_repair.py` | Tests for stale tool-call marker session repair (hermes_state, #78148). |
| `test_startup_maintenance_lease.py` | Construction-time state.db maintenance must keep the startup watchdog's progress lease alive (#111092). |
| `test_state_db_corrupt_quarantine.py` | Quarantine of a live SessionDB handle after structural (non-FTS) corruption. |
| `test_state_db_darwin_fd_scan_hang.py` | A kernel-blocked vnode must not wedge Hermes startup (#113187). |
| `test_state_db_file_identity.py` | File-identity guard on SessionDB writes (#89332). |
| `test_state_db_fts_segment_collision_probe.py` | Segment-dependent FTS5 trigram corruption (#100227). |
| `test_state_db_holders.py` | Behavioral tests for the state-holder and repair-admission authority. |
| `test_state_db_holders_windows_live.py` | Live Windows proof for #120205: structural maintenance sees a real foreign SQLite holder. |
| `test_state_db_lock_fail_closed.py` | Unopenable admission lock files must fail CLOSED (#100368). |
| `test_state_db_maintenance_conformance.py` | Conformance suite: state.db maintenance must be guard-aware and copy-honest. |
| `test_state_db_malformed_repair.py` | Recovery from a malformed state.db schema (duplicate sqlite_master rows). |
| `test_state_db_notadb_fail_closed.py` | Tests for fail-closed state.db NOTADB handling and journal-mode EIO retries. |
| `test_state_db_repair_live_writer_guard.py` | Regression: the state.db repair path must never run surgery against a database another connection is still writing. |
| `test_state_db_repair_loop_cap.py` | #86747 regression: the state.db repair loop must be bounded across restarts and must not accumulate identical multi-hundred-MB forensic backups. |
| `test_state_db_repair_loop_mtime.py` | Regression: the state.db repair-loop guards must survive an mtime change. |
| `test_state_db_repair_non_destructive.py` | A failed state.db schema repair must preserve the recovery image. |
| `test_state_db_second_process_maintenance.py` | #103339 item 2: structural maintenance from a second PROCESS must refuse while ANY other process holds state.db, even where SQLite's own lock probe is blind (``journal_mode=DELETE`` reader; malformed file). |
| `test_state_db_stats.py` | Tests for state.db health/stats collection (hermes doctor section). |
| `test_state_db_wal_unlink_race.py` | Regression coverage for WAL restoration during state.db repair (#101064). |
| `test_state_db_write_durability.py` | Regression: state.db repair-path writes must be durable on macOS. |
| `test_state_synchronous_pragma.py` | ``database.synchronous`` is configurable, validated, and floored on macOS. |
| `test_storage_failure_copy.py` | One copy table for "session storage unavailable / not written" across CLI, gateway and RPC. |
| `test_storage_health_latch.py` | A structurally corrupt state.db is published once and read the same way everywhere (#72046). |
| `test_storage_import_boundary.py` | The canonical store must not import gateway/ to compute its own identities (latent cycle). |
| `test_sweep_orphaned_sessions.py` | Tests for #65194: startup-time sweep of orphaned UI-stack sessions. |
| `test_tail_rewind_semantics.py` | Tests for issue #86366 — carried-forward compaction tail must not satisfy the search recall filter as "summarized away" content. |
| `test_target_advance_fence.py` | Target-advancing mutations (reset, compress/model prepare) fence executing work only. |
| `test_telegram_topic_selfheal.py` | Regression for #103363 — reading pre-v3 telegram topic tables self-heals to v3. |
| `test_terminal_retirement.py` | Deletion removes history but retains exact, scoped terminal evidence. |
| `test_unaddressed_rewrite_identity.py` | Durable logical-message identity for unaddressed live-replay rewrites (#129065). |
| `test_wal_active_confirmed.py` | #86515: the lock-free mode=ro read pool needs a CONFIRMED WAL header. When the on-disk probe at open is blocked by a concurrent opener, apply_wal_with_fallback reports "wal" as the assumed mode with nothing touched; Ses… |
| `test_wal_checkpoint_strategy.py` | Tests for SessionDB WAL checkpoint strategy (issue #45383). |
| `test_wal_lock_guard.py` | A live writer's WAL generation survives lock cancellation and sibling closes. |
| `test_wal_lock_guard_lifecycle.py` | The WAL lock guard tracks the lifecycle of the handle it protects. |
| `test_watermark_interplay.py` | Regression tests for #86366 × watermark interplay in archive_and_compact. |
| `test_worker_lineage_exclusion.py` | A physical worker excludes its whole FIFO lineage; an explicit reset revokes orphan unknowns. |
| `test_worker_lineage_index.py` | Lineage worker exclusion is one indexed probe, also on a state.db created before the index. |
| `test_write_lock_owner_attribution.py` | Regression: a state.db write-lock timeout names the process holding the lock. |
| `test_write_lock_patience.py` | Write-lock patience for the shared state.db (#74478). |
| `test_writer_conn_thread_safety.py` | Cross-thread races on the shared writer connection (2026-08-20 incident). |
| `test_zeroed_db_quarantine_race.py` | A concurrent opener's writability preflight must not race another opener's quarantine. |
| `test_zeroed_state_db.py` | #68474 hardening: zeroed state.db detection + quarantine. |

## `tests/install/`

| File | What it does |
|---|---|
| `BUNDLED_UPDATES.md` | Bundled application update acceptance |
| `KNOWN_FAILURES.md` | Confirmed historical upgrade limitations |
| `README.md` | Install and Update E2E Tests |
| `e2e-assets/bundle-inputs.mjs` | Exports `downloadArtifact`, `stageBundleInputs` |
| `e2e-assets/bundle-manifest.cjs` | Shared admission for remote inputs and resumed native acceptance phases. |
| `e2e-assets/bundle-plan.mjs` | JavaScript (ES module): `bundle-plan` |
| `e2e-assets/bundle-smoke-metadata.mjs` | Fresh-install admission is separate from the stricter OLD -> NEW update contract. |
| `e2e-assets/desktop-smoke-windows.ps1` | Journey-owned mock and ordinary window close, shared by source and MSIX drivers. Callers supply a checkout-provisioned Node; never resolve tooling from OLD. |
| `e2e-assets/desktop-smoke.ts` | Exports `candidateSmokeHermesHomes`, `predictSmokeHermesHome`, `resolveSmokeLaunch`, `settleSourceDesktopRuntime`, `LaunchElectron`, `runInstalledDesktopSmoke` |
| `e2e-assets/drive-dmg-install.sh` | Drive the Hermes-Setup dmg bootstrap through its first-run GUI. |
| `e2e-assets/drive-update.cjs` | drive-update.cjs — launch the INSTALLED Hermes.exe (real Electron desktop app) under Playwright's Electron driver and perform the update the way a user does: Settings -> About -> "Update now". Screenshots at every step. |
| `e2e-assets/install-and-launch.ahk` | Data/support file |
| `e2e-assets/install-button.png` | PNG image asset |
| `e2e-assets/installer-common.sh` | Driver-only setup; these helpers never install into the caller's real HOME. |
| `e2e-assets/known-failures.cjs` | JavaScript (CommonJS) |
| `e2e-assets/known-failures.json` | JSON list (2 entries) |
| `e2e-assets/launch-button.png` | PNG image asset |
| `e2e-assets/launch-capture/pm-launch.py` | Run an installed PM CLI with driver-side launch capture under its own -I interpreter. |
| `e2e-assets/launch-capture/sitecustomize.py` | Driver-side spawn interception for hermes desktop E2E legs. |
| `e2e-assets/launch-from-spec.mjs` | Exports `resolveLaunch` |
| `e2e-assets/mac-bundled-feed.mjs` | Exports `sha512Base64`, `buildMacFeedText`, `feedFileNames`, `materializeFeed` |
| `e2e-assets/mac-bundled-manifest.cjs` | Independent native signature and installed-stamp assertions. |
| `e2e-assets/mac-bundled-relaunch-watch.cjs` | JavaScript (CommonJS) |
| `e2e-assets/mac-bundled-serve.mjs` | Exports `safeJoin` |
| `e2e-assets/mac-bundled-update-driver.mjs` | mac-bundled-update-driver.mjs — click the REAL in-app update flow on the macOS packaged app: launch the installed OLD bundle binary under Playwright, reach Settings -> About, click "Update now", and wait for the |
| `e2e-assets/mac-bundled-verify.mjs` | JavaScript (ES module): `mac-bundled-verify` |
| `e2e-assets/mock-provider.mjs` | Driver-side wrapper around tests-js/scripts/mock-server.ts (the desktop E2E suite's OpenAI-compatible mock): starts the server as a LIBRARY (importing, not executing, so the dev-launcher block never runs) and |
| `e2e-assets/mock-provider.sh` | Start/stop the mock inference server and point the app at it as a REAL configured provider. |
| `e2e-assets/playback.html` | HTML page/template |
| `e2e-assets/preserve-plugins.sh` | Shared plugin upgrade-preservation hooks for the install E2E drivers (POSIX + macOS). Sourced by tests/install/installer-script-e2e.sh and tests/install/macos-desktop-e2e.sh. |
| `e2e-assets/preserve-user-state.sh` | Shared user-state preservation hooks for the install E2E drivers (POSIX + macOS + Windows-via-bash). Sourced by installer-script-e2e.sh and scripts under tests/install/. |
| `e2e-assets/process-close.cjs` | Observe at launch: a renderer can close before the native process and its stdio pipes. Playwright's driver exit cleanup tree-kills until that close. |
| `e2e-assets/pty-run.py` | Run a command under a Windows pseudoconsole, capturing its output. |
| `e2e-assets/record-start.ps1` | Start a continuous ffmpeg screen recording in the background (windows). |
| `e2e-assets/record-start.sh` | Start a continuous ffmpeg screen recording in the background. |
| `e2e-assets/record-stop.ps1` | Stop a recording started by record-start.ps1 and verify the file is real. |
| `e2e-assets/record-stop.sh` | Stop a recording started by record-start.sh and verify the file is real. |
| `e2e-assets/red-tracker.mjs` | Exports `LABEL`, `planTracker` |
| `e2e-assets/smoke-env.d.mts` | Exports `SmokeEnvironment`, `within`, `smokeEnvironment`, `isolateUpdateWindowEnvironment`, `isolatedElectronArgs`, `updateWindowEnvironment` |
| `e2e-assets/smoke-env.mjs` | Environment shaping shared by the desktop smoke drivers and the source-update window. Dependency-free on purpose: `tests/scripts/test_source_build_env.py` runs it under a bare `node` with no workspace install, so nothin… |
| `e2e-assets/source-branch-probe.cjs` | Test-only preload for the unpublished Git main used by source-install E2E. The shipped source checker accepts --branch main, but Desktop's automatic check normally resolves the published main channel. Intercept only that |
| `e2e-assets/source-build-env.ps1` | Child installers/builds stamp their checkout; restore the workflow identity even on failure. |
| `e2e-assets/source-build-env.sh` | OLD and NEW must stamp the checked-out source, not the CI driver's ref. A subshell preserves the workflow's identity and the git URL redirect. |
| `e2e-assets/source-desktop-smoke.mjs` | Read-only source checkpoint adapter. Tooling is resolved from the CI checkout, never from the historical installation. The standalone driver owns the app. |
| `e2e-assets/source-driver.ps1` | Dot-source only. Prefer the published command; never rescue a broken one through PATH, the user's shared bin, or an obsolete checkout venv. |
| `e2e-assets/source-driver.sh` | Source-only helpers: never search PATH for a different installation. |
| `e2e-assets/source-runtime-settle.d.mts` | Exports `SourceRuntimeSettleCommand`, `sourceRuntimeSettleCommand` |
| `e2e-assets/source-runtime-settle.mjs` | Resolve the installation-owned launcher used to finish a source update. Windows PM installs can contain two launchers during an update. A locked executable can remain beside the current command file. Select the command… |
| `e2e-assets/source-update-command.sh` | Build the installed CLI's invocation for a source-to-source update. Older releases do not accept either flag, so probe their own help first. |
| `e2e-assets/source-update-observer.mjs` | A checkout reset is the start of preparation, not its completion. |
| `e2e-assets/source_driver.py` | Read-only source-install acceptance, before a CLI launch can repair it. |
| `e2e-assets/ts-prefix.ps1` | Add-TsPrefix: prefix each pipeline line with [+MM:SS] relative to the moment the pipeline started (the playback.html leg player's sync axis). |
| `e2e-assets/ts-prefix.sh` | ts_prefix: prefix each stdin line with [+MM:SS] relative to the DRIVER's start (TS_BASE), not this pipe's start -- every log in a leg shares one time base, so the playback.html sync (one offset slider against the |
| `e2e-assets/update-ui.cjs` | Shared clicks only. Each route owns its receipt/process/relaunch observer. |
| `e2e-assets/update-window-chat.d.mts` | Exports `UpdateWindowIdentity`, `UpdateWindowChatOptions`, `UpdateWindowProcess`, `assertUpdateWindowProcess`, `assertUpdateWindowBackendOrigin`, `runUpdateWindowChat` |
| `e2e-assets/update-window-chat.mjs` | The caller owns OLD's lifetime. Record backend provenance in the same receipt as the shared chat assertion without launching a second app or provider. |
| `e2e-assets/user-state-actions.sh` | Produce the user state that preserve-user-state.sh verifies — through the ORDINARY user surface, including editing a profile's user-owned SOUL.md. |
| `e2e-assets/verify-plugin-preservation.py` | Plugin upgrade-preservation verifier (Hermes release-harness hook). |
| `e2e-assets/verify-user-state.py` | User-state upgrade-preservation verifier (Hermes install/update E2E hook). |
| `e2e-assets/window-input.cjs` | Shared input setup for the install drivers. Only the selected app window is changed; helper windows retain their own coordinate system. |
| `e2e-assets/windows-bundle-metadata.ps1` | Metadata-only readers shared by native admission and pure XML/archive tests. |
| `e2e-assets/windows-bundle-metadata.test.ps1` | Pure archive/XML admission tests: no package deployment or host impersonation. |
| `e2e-assets/windows-bundle-plugin-smoke.ps1` | Install and enable a plugin with Python dependencies through the installed package's CLI execution alias, as a basic (non-admin) user. Dot-sourced by windows-bundle-smoke.ps1 after the chat smoke; throws on failure. |
| `e2e-assets/windows-bundled-drive-update.ps1` | ============================================================================ windows-bundled-drive-update.ps1 — drive the REAL in-app update surface of the INSTALLED (MSIX) desktop app via UI Automation. |
| `e2e-assets/windows-bundled-helpers.mjs` | Windows packaged-app acceptance helpers. Release Python owns descriptor XML; msix-shared supplies the expected publisher and content types. --msix-shared selects the checkout whose release module and native facts are un… |
| `e2e-assets/windows-bundled-helpers.test.mjs` | windows-bundled-helpers — unit tests for the pure helpers of the Windows packaged-app E2E arm. Pure manifest validation plus real descriptor CLI calls through the release Python module; no Windows installation needed. |
| `e2e-assets/windows-bundled-processes.test.ps1` | Pipeline/array contracts only; no package installation or live process changes. |
| `installer-script-e2e.sh` | Prove a user who installed OLD via the installer script can reach HEAD. |
| `macos-bundle-smoke.sh` | Consumes receipt-verified bytes; never builds, repairs, or relaxes Gatekeeper. |
| `macos-bundled-e2e.sh` | Prove the macOS packaged-app update route: a user on a REAL signed OLD bundle, installed in an isolated location, clicks About -> "Update now" and Squirrel.Mac swaps in a REAL signed NEW bundle and relaunches it — |
| `macos-desktop-e2e.sh` | Prove a macOS user who installed OLD via the published desktop installer (Hermes-Setup.dmg from the website) can reach HEAD. |
| `windows-bundle-smoke.ps1` | Real deployment of receipt-verified bytes. Never run on a developer desktop. |
| `windows-bundled-e2e.ps1` | Native package replacement acceptance. Never run on a developer desktop. |
| `windows-e2e.ps1` | ============================================================================ Windows Desktop GUI install + update E2E driver (the REAL user flow) =========================================================================… |

## `tests/installation/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `test_installer_common.py` | Driver setup against private Git/script artifacts, never an installed app. |

## `tests/integration/`

| File | What it does |
|---|---|
| `test_local_runtime_pm_download.py` | Opt-in live acceptance: download the actual pinned CUDA engine and run it. |

## `tests/manual/`

| File | What it does |
|---|---|
| `cron_inchannel_dm_e2e.py` | DM-path verification for in_channel continuable cron (Option A scoping). |
| `cron_inchannel_e2e.py` | Offline E2E for continuable in-channel cron (specs/cron-inchannel-continuable). |

## `tests/monitoring/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `test_cron_health_export.py` | Tests: `_metric`, `test_execution_projection_is_opaque_bounded_and_content_free`, `test_cron_store_writability_is_exported`, `test_error_classification_avoids_auth_substring_false_positives`, `test_terminal_execution_em… |
| `test_emitter.py` | Tests for the monitoring emitter: hot-path invariant + subscriber fan-out. |
| `test_export_redaction.py` | Export redaction tests — the security-critical layer. |
| `test_gateway_health_export.py` | Tests: `test_otlp_attrs_redact_strings_and_never_export_profile`, `test_resource_attributes_are_allowlisted_and_sanitized`, `test_diagnostic_log_attributes_are_allowlisted_redacted_and_profile_free`, `test_gateway_healt… |
| `test_otlp_exporter.py` | OTLP exporter tests: config resolution, span mapping, streaming subscriber. |

## `tests/perf_guards/`

| File | What it does |
|---|---|
| `test_pattern_b_scaling.py` | Pattern-B perf-regression guards: hot paths must not degrade to O(N·M). |

## `tests/plugins/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `browser/__init__.py` | Package marker / package-level exports |
| `browser/check_parity_vs_main.py` | Behavior-parity check for the browser-provider plugin migration (#25214). |
| `browser/test_browser_provider_plugins.py` | Plugin-side tests for the browser provider migration (PR #25214). |
| `config_backends/__init__.py` | Package marker / package-level exports |
| `config_backends/stub_plane.py` | A contract-faithful stub of the config plane's agent routes (contract.md §7.1, §7.2, §8) plus an OAuth2 client-credentials token endpoint, for driving the remote backend without gg. |
| `config_backends/test_config_set_destination.py` | `hermes config set/unset` name where the write actually landed. |
| `config_backends/test_remote_backend.py` | Remote config backend against a contract-faithful stub plane (``stub_plane.py``). |
| `config_backends/test_remote_conformance.py` | Vendored config-plane conformance fixtures, run against the agent's client-side rules (contract.md §13): path grammar, secret-shaped keys, the profile-level write check fed ``expect.locks``, and ``defaultsMerge`` agains… |
| `config_backends/test_remote_credential_destination.py` | Credential destination policy (andrexibiza P1-A): the plane bearer and the IdP client secret go only to the configured https origin (plain http only to loopback) and never follow a redirect. |
| `config_backends/test_remote_grouped_and_migration_reads.py` | Remote config review round 7: grouped edits are one write, and readers see only completed in-memory migrations. |
| `config_backends/test_remote_multiprocess.py` | Every Hermes process type reads and writes through the remote backend with the same credential (design §4.4 step 6, G3): a CLI ``config set`` in one process is seen by a gateway-boot process and a TUI-gateway (dashboard… |
| `config_backends/test_remote_pinned_sets.py` | A keyed ``config set`` stores its value at the profile level even when it equals the inherited one (the file backend writes every keyed set into config.yaml), and a rotated IdP client secret takes effect on the next req… |
| `config_backends/test_remote_unavailable_consumers.py` | andrexibiza P1-B: ``ConfigBackendUnavailable`` is a ``SystemExit`` on purpose (a fail-open reader must never serve defaults instead of the selected backend's config; boot fails closed), so an ``except Exception`` / ``su… |
| `dashboard_auth/test_basic_provider.py` | Tests for the BasicAuthProvider plugin (username/password, scrypt, signed tokens). |
| `dashboard_auth/test_basic_secret_shell_text.py` | BasicAuthProvider must not sign sessions with a secret that is unexpanded shell text. |
| `dashboard_auth/test_drain_provider.py` | Tests for the DrainSecretProvider plugin (non-interactive bearer secret). |
| `dashboard_auth/test_jwt_clock_skew_leeway.py` | Clock-skew leeway for dashboard-auth JWT verification (#47815). |
| `dashboard_auth/test_nous_provider.py` | Tests for the bundled Nous dashboard-auth plugin. |
| `dashboard_auth/test_opaque_bearer_not_unreachable.py` | #94558 — a non-JWT bearer must not be reported as "Auth provider unreachable". |
| `dashboard_auth/test_self_hosted_provider.py` | Tests for the bundled self-hosted OIDC dashboard-auth plugin. |
| `dashboard_auth/test_session_token_provider.py` | Tests for the SessionTokenProvider plugin (the deployment session token as a gated-mode credential). |
| `fixtures/kanban_touch_drag_probe.js` | Behavioral probe for attachTouchDrag() (#115568): extracts the function from the shipped dashboard bundle (no build step — the bundle IS the source) and drives it through real pointerdown/pointermove/pointerup sequences… |
| `image_gen/__init__.py` | Package marker / package-level exports |
| `image_gen/check_parity_vs_main.py` | Behavior-parity check for the image-gen FAL plugin migration (#26241). |
| `image_gen/test_deepinfra_provider.py` | Tests for the bundled DeepInfra image_gen plugin. |
| `image_gen/test_fal_provider.py` | Tests for the FAL.ai image generation plugin. |
| `image_gen/test_krea_provider.py` | Tests for Krea image generation provider. |
| `image_gen/test_meta_ai_provider.py` | Tests for the bundled Meta Model API image_gen plugin (muse-image). |
| `image_gen/test_openai_codex_provider.py` | Tests for the bundled ``openai-codex`` image_gen plugin. |
| `image_gen/test_openai_provider.py` | Tests for the bundled OpenAI image_gen plugin (gpt-image-2, three tiers). |
| `image_gen/test_openrouter_compat_provider.py` | Tests for the OpenRouter-compatible image gen provider (OpenRouter + Nous). |
| `image_gen/test_xai_provider.py` | Tests for xAI image generation provider. |
| `memory/__init__.py` | Package marker / package-level exports |
| `memory/test_bom_tolerant_config_reads.py` | User-editable plugin/auth JSON survives a Windows-editor BOM. |
| `memory/test_byterover_multiplex_child_env.py` | ByteRover's ``brv`` child carries the SERVED profile's cloud identity, never the launch profile's. |
| `memory/test_byterover_provider.py` | Tests for the ByteRover memory provider config gates. |
| `memory/test_config_schema.py` | Tests for config-schema loading from memory provider plugin dirs. |
| `memory/test_disabled_provider_not_loaded.py` | A user-installed memory provider parked in ``plugins.disabled`` must not load. |
| `memory/test_discovery_sources.py` | Discovery parity for out-of-tree memory providers. |
| `memory/test_multiplex_memory_identity_scope.py` | Multiplex invariant: memory-provider identity/tenant/endpoint never comes from the default profile. |
| `memory/test_provider_multiplex_contract.py` | PLG-11 (#140058): the in-repo memory providers meet the multiplexing contract. |
| `memory/test_provider_threads_inherit_profile.py` | Multiplex invariant: every memory provider's background thread runs under the spawner's profile. |
| `memory/test_retaindb_provider.py` | Tests: `test_write_queue_closes_owner_connection`, `test_write_queue_ignores_enqueue_after_shutdown`, `test_prefetch_does_not_spawn_when_previous_batch_is_alive`, `test_upload_file_rejects_hermes_credential_store`, `tes… |
| `model_providers/test_commandcode_profile.py` | Unit tests for the CommandCode provider profiles. |
| `model_providers/test_custom_profile.py` | Unit tests for the custom provider profile's reasoning wiring. |
| `model_providers/test_deepinfra_profile.py` | DeepInfra profile puts the reasoning switch on the wire (#111872). |
| `model_providers/test_deepseek_profile.py` | Unit tests for the DeepSeek provider profile's thinking-mode wiring. |
| `model_providers/test_fireworks_profile.py` | Unit tests for the Fireworks AI provider profile. |
| `model_providers/test_gemini_profile.py` | Contract tests for the native Google Gemini provider profile. |
| `model_providers/test_kimi_profile.py` | Unit tests for the Kimi/Moonshot provider profile's reasoning wiring. |
| `model_providers/test_minimax_profile.py` | Unit tests for the MiniMax provider profile. |
| `model_providers/test_nous_profile.py` | Unit tests for the Nous Portal profile's reasoning wiring. |
| `model_providers/test_ollama_cloud_profile.py` | Unit tests for the Ollama Cloud provider profile's reasoning-effort wiring. |
| `model_providers/test_opencode_go_profile.py` | Unit tests for OpenCode Go reasoning-control wiring. |
| `model_providers/test_solstice_profile.py` | Solstice invariants: a pre-release provider stays off every discovery surface until signed in, and a brokered OAuth row with an opaque bearer rotates on its stored expiry. |
| `model_providers/test_thinking_toggle_parity.py` | Thinking-toggle / reasoning_effort wire invariants shared by the Moonshot- and DeepSeek-style chat_completions profiles (all route through ``agent.reasoning_effort.thinking_toggle_extras``). |
| `model_providers/test_upstage_profile.py` | Unit tests for the Upstage Solar provider profile. |
| `model_providers/test_zai_profile.py` | Unit tests for the Z.AI / GLM provider profile's reasoning wiring. |
| `platforms/buzz/test_buzz_unscoped_requirement_gate.py` | Regression tests for the Buzz requirement gate vs external secrets (#95216). |
| `platforms/matrix/test_blank_config_env_fallback.py` | A present-but-blank ``matrix:`` key in config.yaml means "unset": the env-var fallback must fire exactly as it does when the key is absent (0.21.2 started seeding blank YAML values into ``config.extra``, which flipped t… |
| `platforms/matrix/test_event_size.py` | Every event the Matrix plugin builds fits the homeserver's byte cap, whatever the script or shape of the text: sends, stream/progress edits at the adapter's advertised budget, and the standalone sender. |
| `platforms/photon/test_auth.py` | Tests for the Photon auth module (device login + dashboard API). |
| `platforms/photon/test_check_requirements_risks.py` | Tests for check_requirements() diagnostic logging (fix) and remaining risks. |
| `platforms/photon/test_fatal_notify_self_cancel.py` | Photon's fatal-error notification must not be cancelled by its own teardown. |
| `platforms/photon/test_inbound.py` | Inbound dispatch + dedup tests for PhotonAdapter. |
| `platforms/photon/test_markdown.py` | Markdown handling tests for PhotonAdapter. |
| `platforms/photon/test_mention_gating.py` | Group-chat mention-gating tests for PhotonAdapter. |
| `platforms/photon/test_multiplex_profile_scope.py` | Multiplex secondary-profile scope tests for the Photon adapter + auth module. |
| `platforms/photon/test_npm_error_log_regression.py` | Regression tests for the npm stderr capture + error log persistence fix. |
| `platforms/photon/test_outbound_media.py` | Outbound-media tests for PhotonAdapter. |
| `platforms/photon/test_overflow_recovery.py` | Photon adapter resilience to transient Spectrum/Envoy upstream overflow. |
| `platforms/photon/test_poll_clarify.py` | Native-poll clarify tests for PhotonAdapter. |
| `platforms/photon/test_presence_watchdog.py` | Presence-watchdog tests. |
| `platforms/photon/test_reactions.py` | Reaction (tapback) tests for PhotonAdapter. |
| `platforms/photon/test_rich_links.py` | Rich-link handling tests for PhotonAdapter. |
| `platforms/photon/test_runtime_record.py` | Sidecar runtime-record persistence tests (issue #69960). |
| `platforms/photon/test_setup_access.py` | Tests for `hermes photon setup`'s access auto-configuration. |
| `platforms/photon/test_sidecar_deps_stale.py` | Regression tests for the Photon sidecar stale-dependency self-heal. |
| `platforms/photon/test_sidecar_lifecycle.py` | Sidecar lifecycle tests: orphan reaping and parent-death wiring. |
| `platforms/photon/test_sidecar_paths.py` | Tests for the Photon sidecar directory resolver (NS-606). |
| `platforms/photon/test_spectrum_patch.py` | Regression tests for Hermes' Spectrum mixed text+attachment workaround. |
| `platforms/photon/test_threaded_replies.py` | Inbound iMessage threaded (swipe) replies for PhotonAdapter (#100663). |
| `platforms/photon/test_url_send_path.py` | Behavior tests for Photon raw-URL outbound routing (issue: markdown 500s). |
| `platforms/photon/test_zombie_stream_watchdog.py` | Zombie-stream watchdog tests (half-open gRPC stream, issue #54036). |
| `platforms/slack/test_slash_command_channel_prompt.py` | Slack slash-command turns carry the same channel prompt, skill binding and source names as messages. |
| `platforms/telegram/test_allowlist_json_adapter.py` | ``hermes config set telegram.allowed_chats '["a","b"]'`` stores a JSON-encoded *string*; every Telegram allowlist reader must decode it instead of comma-splitting the brackets onto the ids. |
| `platforms/telegram/test_inline_picker_offset.py` | Negative or malformed ``offset`` values must not corrupt inline-picker pagination. |
| `platforms/telegram/test_notification_kwargs.py` | Telegram notification-mode gating (#132516): "important" mode silences ordinary sends, but a human-decision prompt (``is_approval_prompt``) must always push — a silently delivered prompt is indistinguishable from "no pr… |
| `platforms/test_bracket_list_allowlists.py` | Allowlists stored as a JSON-list *string* are honoured by every platform gate (issue #76457). |
| `platforms/test_discord_gate_isolation.py` | Per-profile isolation of Discord/Telegram allow/deny gates (issue #72348). |
| `platforms/test_discord_reauthorize_allowed_roles.py` | Durable Discord re-authorization resolves ``allowed_roles`` like ingress, from current config (#139148). |
| `platforms/test_interactive_setup_reconfigure_gate.py` | Every platform plugin's ``interactive_setup`` routes its "already configured? Reconfigure?" gate through ``hermes_cli.setup_platforms.declines_reconfigure``. |
| `platforms/test_qqbot_plugin.py` | QQ Bot is a bundled platform plugin: env seeding and cron delivery, no live gateway. |
| `test_a2a_forwarded_cancel_retry.py` | A2A forwarded tasks: a resend stays a retry after the process-local id memory forgot it (andrexibiza 5480715949 P2c). |
| `test_a2a_no_token_guards.py` | Edges of the A2A no-token browser and Host guards: malformed Host values fail closed, a POST without a Content-Type is refused, and a token-authenticated listener is left unchanged. |
| `test_a2a_phase23.py` | Streaming / push / anti-loop / task-store tests for the A2A plugin (v1.0). |
| `test_a2a_plugin.py` | Tests for the A2A (Agent-to-Agent) platform plugin — protocol v1.0. |
| `test_a2a_rejected_resend.py` | A forwarded message refused by an admission guard stays refused on its exact resend. |
| `test_a2a_tools_gate.py` | a2a client tools config gate (#95681, maintainer-directed). |
| `test_achievements_plugin.py` | Tests for the bundled hermes-achievements dashboard plugin. |
| `test_chronos_cron.py` | Unit tests for the Chronos NAS-mediated cron provider (Phase 4D). |
| `test_chronos_verify.py` | Tests for the Chronos inbound cron-fire JWT verifier (Phase 4E.1). |
| `test_context_engine_user_dir.py` | ``context.engine: <name>`` names the active engine, so an engine dropped into ``$HERMES_HOME/plugins/<name>/`` loads without a ``plugins.enabled`` entry and never trips the "Context engine 'X' not found — falling back t… |
| `test_discord_runtime_failure.py` | Tests: `test_discord_bot_task_runtime_exit_notifies_gateway_for_reconnect` |
| `test_disk_cleanup_plugin.py` | Tests for the disk-cleanup plugin. |
| `test_google_meet_audio.py` | Tests for plugins.google_meet.audio_bridge (v2). |
| `test_google_meet_node.py` | Tests for the google_meet node primitive. |
| `test_google_meet_plugin.py` | Tests for the google_meet plugin. |
| `test_google_meet_realtime.py` | Tests for plugins.google_meet.realtime.openai_client (v2). |
| `test_irc_inbound_identity.py` | Distinct IRC lines must remain distinct inputs in the gateway's durable FIFO. |
| `test_kanban_attachments.py` | Tests for Kanban task file attachments (#35338). |
| `test_kanban_board_done_order.py` | Kanban dashboard plugin: the board's done column is completion history. |
| `test_kanban_board_lifecycle_api.py` | Kanban dashboard plugin: board rename + delete over the REST surface. |
| `test_kanban_board_project_api.py` | Kanban dashboard plugin: project listing + project-scoped boards. |
| `test_kanban_dashboard_plugin.py` | Tests for the Kanban dashboard plugin backend (plugins/kanban/dashboard/plugin_api.py). |
| `test_kanban_dashboard_task_updated_hook.py` | Dashboard mutation-boundary coverage for ``on_kanban_task_updated``. |
| `test_kanban_estimate.py` | Kanban dashboard plugin: task effort estimate. |
| `test_kanban_events_tail.py` | The kanban events stream starts at the board's tail unless the client names a cursor. |
| `test_kanban_link_tasks.py` | GET /tasks/:id includes `link_tasks` — {id, title, status} rows for every parent/child — so the desktop drawer renders titles instead of raw ids (#kanban-modal). Same router-on-bare-FastAPI harness as the attachments te… |
| `test_kanban_model_override.py` | Per-task model/provider override — DB layer, worker spawn, dashboard API. |
| `test_kanban_read_admission.py` | HTTP admission regression: board bursts must not consume every worker. |
| `test_kanban_workflow_matrix.py` | Manual move matrix: ``DEFAULT_WORKFLOW.manual`` vs. the live ``PATCH /tasks/{id}``. |
| `test_kanban_ws_idle_disconnect.py` | Regressions for the kanban events WebSocket connection lifecycle. |
| `test_memory_hook_registration.py` | Exercise dual-kind plugins through the real general and memory loaders. |
| `test_multiplex_plugin_cache_scope.py` | Plugin module-level caches must not hand profile A's state to profile B under a multiplexed HERMES_HOME override (``hermes_constants.set_hermes_home_override``). |
| `test_plugin_automation_blueprints.py` | Plugins register Automation Blueprints via ``ctx.register_automation_blueprint``. |
| `test_plugin_loader.py` | Regression tests for directory-plugin module loading. |
| `test_plugin_loader_unreadable.py` | One mode-000 / ACL-denied child under a plugin root must not abort the listing (#111804). |
| `test_plugin_paths_follow_profile.py` | Plugin data paths follow the active profile's HERMES_HOME, including the ContextVar override. |
| `test_plugin_storage.py` | Tests for the per-plugin durable storage convention (plugins/plugin_storage). |
| `test_plugin_utils.py` | Tests for plugins/plugin_utils.py — thread-safe lazy singleton helpers. |
| `test_plugins_manage_profile_scope.py` | plugins.manage optional ``profile`` param — per-profile plugins scoping. |
| `test_retaindb_plugin.py` | Tests for the RetainDB memory plugin. |
| `test_scoped_secret_readers_fail_closed.py` | Credential shims outside the memory plugins honour the secret-scope contract. |
| `test_secret_scope_plugin_families.py` | Regression tests: plugin-family credential reads honor the profile secret scope. |
| `test_security_guidance_plugin.py` | Tests for the security-guidance plugin. |
| `test_teams_duplicate_job_claim.py` | One Graph batch carrying the same no-id notification twice runs its durable job once. |
| `test_teams_pipeline_meetings.py` | Tests: `FakeGraphClient`, `test_join_url_can_use_organizer_scoped_graph_lookup`, `test_transcript_download_requests_graph_vtt_content` |
| `test_teams_pipeline_plugin.py` | Tests for the Teams pipeline plugin package. |
| `test_telegram_polling_progress_ptb.py` | Integration coverage for polling progress against the installed PTB runtime. |
| `test_telegram_update_admission.py` | Telegram replay admission through real PTB dispatch (Refs #68502). |
| `test_transform_api_error_classification_hook.py` | Tests for the ``transform_api_error_classification`` plugin hook. |
| `test_transform_tool_result_hook.py` | Tests for the ``transform_tool_result`` plugin hook wired into ``model_tools.handle_function_call``. |
| `transcription/__init__.py` | Package marker / package-level exports |
| `transcription/check_parity_vs_main.py` | Behavior-parity check for the STT plugin hook + command-provider registry. |
| `tts/__init__.py` | Package marker / package-level exports |
| `tts/check_parity_vs_main.py` | Behavior-parity check for the TTS plugin hook (issue #30398). |
| `video_gen/__init__.py` | Make tests/plugins/video_gen a package. |
| `video_gen/test_deepinfra_provider.py` | Tests for the bundled DeepInfra video_gen plugin. |
| `video_gen/test_fal_plugin.py` | Tests for the FAL video gen plugin — family routing, payload shape. |
| `video_gen/test_openrouter.py` | OpenRouter video_gen plugin — live-catalog shape, per-model clamping, and the submit→poll→download flow. |
| `video_gen/test_xai_plugin.py` | Smoke tests for the xAI video gen plugin — load & register surface. |
| `video_gen/test_xai_plugin_integration.py` | Integration tests for the xAI video gen plugin's simplified surface. |
| `web/__init__.py` | Package marker / package-level exports |
| `web/test_extract_origin_status.py` | web_extract must report a target page's HTTP >= 400 as an error, on every extract provider. |
| `web/test_firecrawl_redirect_recheck.py` | Firecrawl extract re-checks the website policy against the URL it was redirected to. |
| `web/test_web_search_provider_plugins.py` | Plugin-side tests for the web search provider migration (PR #25182). |

## `tests/pm/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `_fixtures.py` | Real artifacts and isolated PM workers shared by lifecycle tests. |
| `_range_server.py` | Shared Range-honoring loopback server for pm downloader tests. |
| `activation_support.py` | Fixtures shared by the shell-activation tests. |
| `conftest.py` | Shared fixtures for the PM suite. |
| `test_activate_fish.py` | ``activate.fish``: fish takes on the environment and gives it back, as ``activate`` does for bash. |
| `test_activate_scripts.py` | ``activate`` / ``activate.ps1``: an interactive shell takes on the environment and gives it back. |
| `test_activation_runtime.py` | Activation syncs through setup before selecting or changing the caller's env. |
| `test_activation_setup.py` | Bash activation crosses real setup, PM install, and uv dependency publication. |
| `test_archive_safety.py` | Hostile archives must not write outside the store entry being staged. |
| `test_artifact_mirror.py` | PM installation and cross-target staging consume the public pinned mirror. |
| `test_baked_selection.py` | A Docker image records the extras it bakes, and boot recovery restores them. |
| `test_bootstrap_import_closure.py` | The tool-only build stage imports PM without third-party dependencies. |
| `test_build_operations.py` | Offline behavior contracts for PM's caller-owned build operations. |
| `test_chromium.py` | One browser payload serves both headed and headless callers. |
| `test_cli_progress.py` | `pm cli` progress renders in place on a terminal and line-per-tick off one. |
| `test_cold_runtime_e2e.py` | Cold CLI provisioning and repair, with real tools and no mocked child code. |
| `test_cua_driver_package.py` | CUA archive staging preserves the native host payload, without running it. |
| `test_custom_root_union.py` | Real default, custom and active-profile roots all discover sibling members. |
| `test_darwin_build.py` | Native static-library builds use PM's archiver, not PBS's build directory. |
| `test_deb_safety.py` | DebPackage.unpack containment regressions (via pm.store.extract_tar). |
| `test_dmgbuild_package.py` | The build-only DMG supplier preserves its paired runtime without executing it. |
| `test_download_continuity.py` | Durable checkpoints preserve downloads across interruptions and process termination. |
| `test_download_mirrors.py` | Pinned downloads keep their identity when the upstream disappears. |
| `test_download_progress.py` | Download progress describes actual whole-plan bytes on fresh and resumed runs. |
| `test_download_retry_limits.py` | The real downloader bounds retries and pauses without publishing partial bytes. |
| `test_download_serial_fallback.py` | A CDN refusal downgrades this transfer once, including later network retries. |
| `test_download_state.py` | GC and downloads acquire the same partial owner before changing its files. |
| `test_downloader.py` | pm/downloader: resumable, hash-verified, 8-way parallel downloads. |
| `test_downloader_integrity.py` | Every ranged worker must prove which representation and bytes it received. |
| `test_environment_build.py` | Real, offline uv construction below PM selection and distribution packaging. |
| `test_environment_command.py` | `hermes pm environment`: the shell entry skills use for a named side environment. |
| `test_environment_script.py` | ``pm.environments.shell_exports``: the composed environment as a script a shell can evaluate. |
| `test_extras.py` | pm.extras: anchor availability, ensure_import, ensure_and_bind, and the spec→extra install shim. Network-free — sync_venv is stubbed at the client seam used by extras; the engine and worker have separate transaction tes… |
| `test_feature_inventory.py` | Feature inventory reads the selected dependency tree, not the builder. |
| `test_features.py` | pm.features: the frozen bundle feature set (enabled-features.json). |
| `test_ffmpeg_resolution.py` | Ffmpeg pin resolution uses the advertised version and target, never a guessed URL. |
| `test_filesystem_is_junction.py` | is_junction answers for any path, including one that does not exist yet. |
| `test_fixture_wheels.py` | The shared wheel fixture models an index: one name/version is one artifact. |
| `test_generation_durability.py` | A generation's selection record is its completion marker, so it may only be written after the finished tree has been flushed to disk. Otherwise a power loss mid-publish can persist the (fsynced) record while the venv's… |
| `test_held_entry_windows_live.py` | Live Windows obstacles to removing a replaced PM entry. |
| `test_held_identical_entry_windows_live.py` | A live process holding a tools entry that already matches the update's bytes (#139088). |
| `test_index_bridging.py` | Mirrored and air-gapped networks configure indexes through pip or uv; PM forwards exactly that into uv while still refusing every other ambient uv setting. |
| `test_install_default_closure.py` | The default `pm install` closure must stage the interpreter boot requires. |
| `test_install_download_control.py` | Install controls reach real archive transfers without publishing partial packages. |
| `test_install_extra.py` | `hermes pm install --extra NAME` is the one command every missing-extra hint names. |
| `test_install_lock_reclaim_race.py` | Reclaiming an orphan install state never leaves two holders of its install lock (``pm/install_states.py``, ``hermes_cli.runtime_state.runtime_lock``). |
| `test_install_state_permissions.py` | Permission failures in install state must explain the actual access problem. |
| `test_install_states_gc.py` | Dependency state of a deleted checkout is reclaimed; state anything live could still read, or whose checkout this process merely cannot see, is kept (``pm/install_states.py``). |
| `test_installed_package.py` | Installed runtime lookup uses the same shipped/addition precedence as ensure. |
| `test_lazy_install_policy.py` | PM reads boolean install policy from real config, without CLI output. |
| `test_lease_reselection.py` | A reader that lost the install lock still ends up leasing the generation it imports from. |
| `test_llamacpp_pins.py` | Every supported local engine backend installs only reviewed PM artifacts. |
| `test_lockfile_publication.py` | Independent pin editors preserve winners and reject changed evidence. |
| `test_long_path_exits.py` | A store root spelled in Windows' extended-length form (``\\?\C:\...``) stays inside PM. |
| `test_long_paths_windows_live.py` | Live Windows proof for PM under ``LongPathsEnabled = 0`` (#130242, #130232). |
| `test_member_selection.py` | The workspace and admission paths agree on scoped keys and disabled plugins. |
| `test_network.py` | Network retry policy keeps permanent errors immediate and attempts bounded. |
| `test_network_retries.py` | PM retries transient HTTP failures before publishing verified bytes. |
| `test_no_lazy_deps.py` | Contract tests for scripts/ci/check_lazy_deps_imports.py. |
| `test_node_libatomic_install_boundary.py` | Regression tests for #124926: libatomic repair belongs to install, not verify. |
| `test_node_release_candidates.py` | The package lock must never choose an unstable Node release. |
| `test_node_resolution.py` | Node discovery reads PM state; legacy home-local trees are never activated. |
| `test_node_sidecar.py` | Plugin-local npm installs retain PM's paired Node and consent policy. |
| `test_npm_dist_tags.py` | npm metadata keeps escaped names, caller headers and retry policy. |
| `test_npm_self_install.py` | npm's self-install keeps its cache out of the store's download entry. |
| `test_pip_check.py` | PM's `uv pip check` accepts exactly the mismatches the lock's overrides resolved. |
| `test_plugin_declarations.py` | Plugin declaration safeguards from #113851, through PM's real resolver. |
| `test_plugin_inputs.py` | The worker receives the same plugin input the caller built. |
| `test_plugin_survival_contract.py` | Plugin survival + upgrade contracts (mnemosyne-oss/mnemosyne#859). |
| `test_plugins_state.py` | pm.plugins_state: complete, order-preserving cross-profile discovery. |
| `test_plugins_state_remote_config.py` | PM's dependency runtime in a Remote Config deployment (#122509): the runtime has no remote backend client and no plane credential, so reading a home's plugin selection there must neither fail closed nor reach for the pl… |
| `test_pm_authority.py` | pm authority spine: digest-bound facts, tree_digest + doctor re-hash, repair logging. |
| `test_pm_bionic.py` | Behavior contracts for pm's bionic target + DebPackage + stage_only. |
| `test_pm_core.py` | pm end-to-end: install a fake tool from a loopback server, prove the lockfile/installed-state split, env composition, single-flight, adoption, and gc behavior. Real downloads, real archives, real locks — no mocked store… |
| `test_pm_musl.py` | A native musl userland resolves PM to musl-native runtime artifacts (#123682). |
| `test_progress.py` | Contained child output: CI keeps every line, interactive runs never hide a failure. |
| `test_project_relock.py` | `hermes pm lock` with no arguments relocks uv.lock through PM and nothing else. |
| `test_publish_entry.py` | Publication behavior when a live Windows process holds an existing entry. |
| `test_python_release_identity.py` | Automatic Python candidates reconstruct only filenames the release advertises. |
| `test_receipt.py` | pm.receipt: the universal machine-readable surface for venv ops. |
| `test_recorded_env_refresh.py` | An entry recorded with an env the package code no longer produces is re-recorded on the next prepare, without re-fetching, so build admission accepts stores built before the change (a Desktop bundle restoring a pm-store… |
| `test_recovery.py` | PM repair replays the selected dependency graph without broken app imports. |
| `test_registry_gap_refusal.py` | A registry gap is refused in the caller, never by a PM worker round trip. |
| `test_restart_needed.py` | restart_needed / adopt_selected against real generations: real uv, offline wheels, temp HERMES_HOME. |
| `test_retired_agent_browser.py` | An install made while agent-browser was a pm package keeps working after it left. |
| `test_ripgrep_vc_runtime.py` | ARM64 Windows ripgrep carries the VC++ runtime it links against. |
| `test_runtime.py` | PM's resolver must not depend on the application it is repairing. |
| `test_runtime_boot_gc.py` | A real bootstrap reader pins its generation before GC can select victims. |
| `test_runtime_bootstrap_tls.py` | The shell-staged uv can prepare TLS support before PM downloads Python. |
| `test_runtime_context_home.py` | Context-only homes use the same dependency state as their own process. |
| `test_runtime_entrypoints.py` | Bootstrap entrypoints must hand dependency operations to PM's own interpreter. |
| `test_runtime_gc.py` | Superseded and aborted PM runtime generations are collected; running workers are not. |
| `test_runtime_journal_concurrent_edit.py` | Recovery does not overwrite a config edited after interrupted publication. |
| `test_runtime_journal_safety.py` | Recovery refuses corrupted metadata and never overwrites unrelated config. |
| `test_runtime_lease_cleanup.py` | Lease pruning keeps its exclusion through deletion and retains uncertain owners. |
| `test_runtime_selection.py` | Install-scoped dependency selection is readable before third-party imports. |
| `test_runtime_wheelhouse.py` | Exercise offline PM staging with real wheels, not the application's environment. |
| `test_security_consumers.py` | Security consumers cross the real PM worker/HTTP/publication boundary. |
| `test_setup_lock_format.py` | Exercise setup's pre-Python pin reader through real downloads and extraction. |
| `test_shell_candidates.py` | Windows bash resolution as pure data: Program Files Git beats PATH, and the WSL / MSIX stubs never win (#116818). Host-independent — the candidate ladder takes the ``which`` result and env as arguments. |
| `test_shell_discovery.py` | The local transport can use Git Bash without a PATH entry. |
| `test_source_launcher_stages.py` | Native whole-script publication; POSIX setup/install lives in the fresh E2E. |
| `test_source_update_launch.py` | Source-update launch completion must publish a real PM generation. |
| `test_stage_only.py` | Native/cross-target execution and Windows directory-hold staging contracts. |
| `test_startup_activation.py` | Startup consumes one real PM verdict; activation never serves a partial toolchain. |
| `test_startup_recovery.py` | Bare startup repairs through real PM workers before activating dependencies. |
| `test_store_extensions.py` | A bundle reuses shipped bytes and adds missing pinned tools outside its seal. |
| `test_store_extract.py` | Regression for the Ubuntu 22.04 bootstrap interpreter: python-build-standalone tarballs carry relative terminfo symlinks (``share/terminfo/1/1178 -> ../a/adm1178``). |
| `test_store_lock_wait.py` | A writer queued behind the store lock says so instead of blocking silently. |
| `test_store_resume.py` | Store scratch cleanup retains resumable bytes outside the scratch directory. |
| `test_sync_bytecode_compile_fallback.py` | uv --compile-bytecode is an optimization. A compile-step failure must not fail the dependency sync (#124268). |
| `test_takeover_preparation.py` | Fresh takeover bootstrap prepares actual dependencies before completion. |
| `test_termux_libs.py` | The termux pool pin authority: parse the index, retire, repin. |
| `test_tree_digest_links.py` | Realized digests bind link text without reading the linked directory. |
| `test_update.py` | Independent resolution decisions; HTTP parsing lives in request-reuse tests. |
| `test_update_artifact_refresh.py` | Minor-style updates follow advertised artifacts without dropping other pins. |
| `test_update_auth_scope.py` | Index credentials stay on their exact HTTPS origin, including redirects. |
| `test_update_bootstrap_pins.py` | A uv re-pin carries the installers' bootstrap pins with it. |
| `test_update_dependency_legs.py` | Optional dependency refreshes run in PM's repository with its installed tools. |
| `test_update_failure_status.py` | A failed update lookup is not a current result or permission to apply. |
| `test_update_pin_isolation.py` | #125386: one failing pin must not zero out the whole `pm update` run. |
| `test_update_request_reuse.py` | An update reads each successful index/artifact once, not once per target. |
| `test_user_facing.py` | The terminal runs the user's own tools first and Hermes's after them (pm.user_facing). |
| `test_uv_cache.py` | PM caches are writable; shipped dependency environments stay immutable. |
| `test_uv_cache_publication.py` | Cache readers must never see an unfinished payload seed copy. |
| `test_uv_cache_seed.py` | A failed uv-cache seed must not record completion. |
| `test_uv_python.py` | PM-owned uv commands use the installed interpreter, never host discovery. |
| `test_venv_command.py` | A sealed payload enters its venvs on its own interpreter, never through their redirectors. |
| `test_venv_sync_ambient_config.py` | Ambient uv settings cannot steer PM; project configuration still can. |
| `test_windows_build_deps.py` | Native PowerShell prerequisite selection without downloading build tools. |
| `test_worker.py` | Real isolated workers: no parent imports or callables cross the wire. |
| `test_worker_observers.py` | Progress observers cannot stall other range writers in the isolated worker. |
| `test_worker_publication.py` | Plugin publication runs in PM's independent worker, not application callbacks. |
| `test_worker_receipts.py` | Worker receipts cross the process seam by identity, never latest.json. |
| `test_worker_registry.py` | Registered package declarations survive a fresh, isolated interpreter. |
| `test_worker_stdio.py` | Worker control traffic must never become a subprocess's standard input. |
| `test_workspace.py` | pm.workspace: the generated uv-workspace root for plugin deps. |
| `test_workspace_build_inputs.py` | Workspace generation carries the source inputs of a buildable core. |
| `test_workspace_output_encoding.py` | Captured package-tool output must not depend on the host's ANSI code page. |
| `test_zip_symlinks.py` | Zip extraction must preserve symlinks — and refuse hostile ones. |

## `tests/providers/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `fake_pkce_idp.py` | Local fake OAuth IdP on 127.0.0.1 for the PKCE plugin helper (tests + live evidence). |
| `test_auth_registry_import_order.py` | Regression coverage for provider auth registration during TUI imports. |
| `test_auth_registry_mid_discovery.py` | Regression tests for #102123: plugins discovered after ``hermes_cli.auth`` is first imported must still reach ``PROVIDER_REGISTRY``. |
| `test_e2e_wiring.py` | E2E tests: verify _build_kwargs_from_profile produces correct output. |
| `test_entry_point_discovery.py` | Tests for pip entry-point provider discovery (hermes_agent.plugins group). |
| `test_fetch_models_base_url.py` | Tests for ProviderProfile.fetch_models base_url override (issue #47009). |
| `test_installed_plugin_discovery.py` | A provider installed by ``hermes plugins install`` must actually be found. |
| `test_meta_ai_profile.py` | Tests for the bundled Meta Model API (Muse Spark) provider plugin. |
| `test_missing_credentials_hints.py` | Missing-credential guidance seams: ``ProviderProfile.missing_credentials_hint`` on every "No usable credentials found" surface and ``ACPClient.auth_required_hint`` on ACP's auth-required error. |
| `test_named_custom_reasoning.py` | Named custom routes use the same reasoning contract as bare custom. |
| `test_oauth_pkce_plugin.py` | Invariants for the declarative OAuth PKCE helper an out-of-tree provider plugin plugs into ``ProviderProfile.auth_handler`` / ``refresh_credential``. |
| `test_plugin_discovery.py` | Tests for the model-providers plugin discovery system. |
| `test_profile_home_layers.py` | ``$HERMES_HOME`` model-provider plugins resolve for the profile home bound at lookup time (#88143). |
| `test_profile_host_seams.py` | Host -> profile seams: ``hostnames`` / ``metadata_hostnames`` claims and the live context hook. |
| `test_profile_miss_ttl.py` | Repeated profile misses honour the plugin-dir stamp TTL (R4 H4). |
| `test_profile_wiring.py` | Profile-path parity tests: verify profile path produces identical output to legacy flags. |
| `test_provider_profiles.py` | Tests for the provider module registry and profiles. |
| `test_provider_registry.py` | Tests: `isolate_provider_registry`, `_profile`, `_reset_registry`, `test_list_providers_reuses_cached_snapshot_until_registration_changes`, `test_list_providers_dedupes_aliases_in_cached_snapshot`, `test_provider_lookup… |
| `test_registry_home_scope.py` | Plugin-mirrored ``PROVIDER_REGISTRY`` rows are per profile home. |
| `test_transport_parity.py` | Parity tests: pin the exact current transport behavior per provider. |

## `tests/scripts/`

| File | What it does |
|---|---|
| `desktop_update/legacy_desktop_reader.py` | Run the update-marker reader an old packaged Desktop shipped (not collected). |
| `desktop_update/lineage_rule_cases.py` | The launcher-lineage rule shared by marker.sh (marker_launcher_rule) and marker-claim.ps1 (Test-MarkerLauncherRule): one table, every consumer runs it. |
| `desktop_update/test_desktop_update_gateway_flag.py` | The hand-off's `--gateway` flag, exercised against the real posix script. |
| `desktop_update/test_desktop_update_linux_gate.py` | The linux relaunch gate must compare canonical paths, not spellings. |
| `desktop_update/test_desktop_update_linux_gate_arm.py` | ARM64 unpacked-dir coverage for the linux relaunch gate (#94703). |
| `desktop_update/test_desktop_update_mac_swap_interrupt.py` | An interrupted macOS app swap always comes back as one complete bundle. |
| `desktop_update/test_desktop_update_macos_no_browser.py` | The macOS hand-off never launches a second browser instance (#96374). |
| `desktop_update/test_desktop_update_marker_gnu_date.py` | marker.sh reads macOS creation times with BSD date even under GNU coreutils (#137925). |
| `desktop_update/test_desktop_update_posix_handoff_protocol.py` | posix.sh / marker.sh hand-off protocol 2 and the A7 marker lock, against real processes. |
| `desktop_update/test_desktop_update_posix_marker.py` | posix.sh owns the update marker like a lock (contract C1/C2) and reports a committed update as committed (contract C3). Every case runs the real script against a disposable install; liveness is decided against real proc… |
| `desktop_update/test_desktop_update_posix_marker_corpus.py` | marker.sh runs EVERY case of the shared update-marker corpus (A7 rule 7). |
| `desktop_update/test_desktop_update_posix_marker_locale.py` | The POSIX hand-off records creation times with a dot under any numeric locale (#135183). |
| `desktop_update/test_desktop_update_relaunch_proxy_env.py` | posix.sh relaunches the Desktop with the user's proxy env, not the one the update was given. |
| `desktop_update/test_desktop_update_runtime_unicode.py` | runtime.ps1 must decode the launcher's UTF-8 path output on Windows (#124526). |
| `desktop_update/test_desktop_update_shim_profile_cleanup.py` | The update hand-off cleans only an atomically claimed browser profile. |
| `desktop_update/test_desktop_update_shim_progress.py` | The shim's /progress contract, exercised against the real posix hand-off. |
| `desktop_update/test_desktop_update_tcc_heal.py` | Desktop hand-off self-heal for venvs bricked by the reverted macOS TCC anchor (#95759), exercised against the REAL ``posix.sh`` functions. |
| `desktop_update/test_desktop_update_windows_child_stage.py` | The Windows hand-off relays the stages `hermes update` publishes, instead of one static line. |
| `desktop_update/test_desktop_update_windows_commit_outcome.py` | Post-commit outcomes (contract C3) on the real Windows hand-off script. |
| `desktop_update/test_desktop_update_windows_cwd.py` | Native regression coverage for the Windows Desktop handoff cwd. |
| `desktop_update/test_desktop_update_windows_handoff_lineage.py` | Who may adopt a pre-written claim (real processes): an OLD packaged Desktop's ``cmd.exe`` wrapper v1 overwrite is accepted by lineage only (R4), and with ``-HandoffRun`` only the Desktop bridge for that run is adopted (… |
| `desktop_update/test_desktop_update_windows_log_concurrency.py` | Regression: concurrent writers must not lose hand-off log lines. |
| `desktop_update/test_desktop_update_windows_log_exit_flush.py` | Every production exit of ``windows.ps1`` flushes the hand-off log lines it could not write yet. |
| `desktop_update/test_desktop_update_windows_marker.py` | Update-marker contract C1 v2 on the real Windows hand-off script. |
| `desktop_update/test_desktop_update_windows_marker_corpus.py` | The shared update-marker corpus (A7 rule 7) on the PowerShell reader/releaser. |
| `desktop_update/test_desktop_update_windows_marker_lock.py` | A7 on the real Windows hand-off script: every marker mutation happens inside one hold of the kernel lock on ``<marker>.lock`` and the update child is the marker's delegate before it runs a single instruction. |
| `desktop_update/test_desktop_update_windows_marker_ops.py` | Protocol-2 helper ops (``windows.ps1 -MarkerOp reclaim\|withdraw``) and the production release / heartbeat functions, on real processes and files. |
| `desktop_update/test_desktop_update_windows_pipe_drain.py` | Regression: Windows Desktop update steps must drain and terminate reliably. |
| `desktop_update/test_desktop_update_windows_progress.py` | The Windows hand-off keeps serving progress while its main thread blocks. |
| `desktop_update/test_desktop_update_windows_python_handoff.py` | Native launch/result acceptance: real publisher, no checkout-local venv. |
| `desktop_update/test_desktop_update_windows_relaunch_cwd.py` | The Desktop the Windows hand-off relaunches never runs from its own app folder. |
| `desktop_update/test_desktop_update_windows_release_holders.py` | #101789 on the real Windows hand-off script: a Desktop swap blocked by a program outside Hermes. |
| `desktop_update/test_desktop_update_windows_timestamp.py` | The Windows handoff writes numeric Unix seconds under comma-decimal locales. |
| `desktop_update/test_desktop_update_windows_ui_delivery.py` | The real Windows update server retains terminal events until acknowledged. |
| `desktop_update/test_handoff_delegate_publication.py` | Exercise the real handoff's publication barrier with owned inert processes. |
| `desktop_update/test_handoff_result_identity.py` | Real PowerShell producer/heartbeat/result contract (portable, not native UI proof). |
| `desktop_update/test_posix_handoff_pid_export.py` | A later generation of a POSIX Desktop hand-off's update adopts the hand-off's own claim. |
| `desktop_update/windows_handoff_support.py` | Shared helpers for the real-process Windows hand-off protocol tests (not collected). |
| `install/test_dmg_install_driver.py` | The DMG driver must wait for native bootstrap completion, not install.sh's marker. |
| `install/test_install_clone_throttle_fallback.py` | A throttled clone is retried without publishing a partial checkout. |
| `install/test_install_desktop_product_present.py` | Installer repair/upgrade reruns detect a built desktop app on every arch (#94703). |
| `install/test_install_diverged_rescue_ref.py` | Regression: the installer's update reset must not drop local commits unanchored. |
| `install/test_install_ps1_execution_policy.py` | The iex'd installer must reach its runtime helper under the Restricted policy. |
| `install/test_install_ps1_iex_failure.py` | A failed install run through `iex (irm ...)` must not end the caller's session. |
| `install/test_install_ps1_json_failure_frame.py` | A fatal stage under -Stage -Json yields exactly one failure frame carrying the reason. |
| `install/test_install_ps1_managed_python_provenance.py` | The real installer waits for bootstrap uv before it delegates to PM. |
| `install/test_install_ps1_native_calls.py` | install.ps1 native calls survive Windows PowerShell 5.1, and reruns keep local work. |
| `install/test_install_ps1_pinned_git_extract.py` | Pinned git staging must not need a bzip2-capable tar (#122512, #122774). |
| `install/test_install_ps1_script_suites.py` | install.ps1's self-contained PowerShell suites, under Windows PowerShell 5.1 and pwsh 7. |
| `install/test_install_ps1_skipsetup_alias.py` | Regression for #125350: -SkipSetup must keep binding after the staged-installer rework. |
| `install/test_install_ps1_staged_git.py` | The bootstrap's separately launched stages must each use PM's pinned Git. |
| `install/test_install_sh_existing_destination.py` | A fresh clone never lands inside, or on top of, an unrelated destination. |
| `install/test_install_sh_git_prerequisite.py` | install.sh prerequisites: a git on PATH that cannot run is not git. |
| `install/test_install_sh_musl_uv_bootstrap.py` | install.sh bootstraps musl uv when the native userland is musl (#123682). |
| `install/test_install_sh_node_tarball_without_xz.py` | PM's shared Node unpacker needs no host xz executable (#11197). |
| `install/test_install_sh_output.py` | install.sh child output: one status line on a terminal, the full stream in CI. |
| `install/test_install_sh_repository_stage.py` | install.sh reruns, pins and invocation modes, driven through the real stage functions. |
| `install/test_install_sh_reuse_supported_python.py` | Bootstrap reuses a supported base Python and reports failures (#10778). |
| `install/test_install_sh_shell_path.py` | install.sh wires ~/.local/bin into the startup file a login bash reads, without duplicating it (#123424). |
| `install/test_install_sh_termux_refusal.py` | install.sh sends Termux hosts to the APT package instead of building a source install. |
| `install/test_pm_desktop_launch_capture.py` | The installer E2E's capture must survive the installed PM launcher's -I. |
| `test_activation_guard.py` | The guard repo scripts call to require an activated shell. |
| `test_agent_build.py` | Prepared inputs become runnable products without acquiring dependencies. |
| `test_appinstaller.py` | App Installer descriptors bind explicit package facts to explicit feed URLs. |
| `test_archive_inputs.py` | CI archives exact pinned inputs and supplies the real staging consumers. |
| `test_baked_bytecode.py` | Baked bytecode: staging contract and launcher marker behavior. |
| `test_bash_shebangs.py` | The repository shebang checker scans tracked scripts and embedded payloads. |
| `test_bootstrap_mirror.py` | Real bootstrap downloads preserve the pin across an upstream outage. |
| `test_bootstrap_pins_fragment.py` | Generated bootstrap pins must match the shared pin and mirror authorities. |
| `test_build_skills_index_health.py` | Invariants for scripts/build_skills_index.py's health-check guard. |
| `test_build_skills_index_resolve.py` | Invariants for scripts/build_skills_index.py's skills.sh path resolution. |
| `test_bundle_native.py` | The native bundle pipeline publishes only after a real staged sync succeeds. |
| `test_bundle_npm.py` | Bundle commands run the prepared npm, including Nix's shell wrapper. |
| `test_bundle_payload.py` | Shared bundle operations use real filesystem and entrypoint contracts. |
| `test_case_collision_check.py` | Wrappers for scripts/check-case-collisions.py. |
| `test_channel_build_versions.py` | A channel request is a complete, immutable input, not a commit flavor. |
| `test_check_agents_md_size.py` | scripts/ci/check_agents_md_size.py: every AGENTS.md chain an agent can load stays under the cap it is truncated at. |
| `test_check_no_tmp_literals.py` | scripts/check_no_tmp_literals.py: literal /tmp paths are flagged; idioms, comments, markers and tests are not. |
| `test_check_profile_archive_boundary.py` | Behavioral tests for the profile archive CI guard. |
| `test_check_profile_scope_patterns.py` | scripts/check_profile_scope_patterns.py flags a known profile-scope hazard and stays silent on clean code. |
| `test_check_public_surface.py` | scripts/ci/check_public_surface.py detects silently dropped public names, methods and test defs. |
| `test_code_health.py` | Invariants of the code-health ratchet (scripts/code_health), on a real git repo + pinned ruff. |
| `test_code_health_cli.py` | scripts/check runner, git hooks, CLI output modes and regex-rule scope, on real git repos. |
| `test_code_health_identity.py` | Unit identity in the code-health ratchet: moves between files, repeated names, TypeScript. |
| `test_code_health_rules.py` | Rule and structure precision of the code-health ratchet (scripts/code_health): each case is a reviewer's repro paired with the control that must keep its verdict. |
| `test_code_health_sleep_rule.py` | HX013: a new wall-clock sleep in a test blocks; existing ones are grandfathered (moved code keeps its debt) and the shared ``tests.waiting`` helper is the compliant way to wait. |
| `test_commit_bundle_entrypoints.py` | Tagless packaging enters the real builder with an exact source identity. |
| `test_commit_stamp_identity.py` | The Python stamp writer binds tagless identity to the built checkout. |
| `test_contributor_map.py` | Tests for the conflict-free contributor mapping system. |
| `test_desktop_build_cache.py` | The cache transport describes candidates without bootstrapping their owners. |
| `test_desktop_cli_wrapper.py` | Unit tests for the bundled payload's win32 launcher wrapper. |
| `test_desktop_preparation.py` | Prepared desktop inputs bind a source and reject stale files before building. |
| `test_desktop_toolchain.py` | Desktop preparation keeps dependency acquisition out of live installs. |
| `test_desktop_update_target.py` | Run the real handoffs against a disposable CLI, never an installed updater. |
| `test_dev_sandbox.py` | Both development entrypoints keep their data identities and cleanup contract. |
| `test_dispatch_log.py` | The pre-build log must name the release.py command that started the run. |
| `test_dmgbuild_diagnostics.py` | DMG diagnostics observe failures without changing the native result. |
| `test_footgun_encoding_direction.py` | Encoding-direction diagnostics through the real file scanner, not a cloned loop. |
| `test_footgun_subprocess_encoding.py` | Tests for the ``subprocess text=True without explicit encoding=`` footgun rule in ``scripts/check-windows-footguns.py``. |
| `test_fresh_source_install.py` | Whole current installer, real PM worker and local application dependency. |
| `test_icon_flavors.py` | Build native icons on the runtime interpreter. Measure pixels, not SVG text. |
| `test_icon_generation_exit.py` | Icon generation reports per-target failures without hiding later targets. |
| `test_install_ps1_chosen_channel.py` | install.ps1 reads the update channel a checkout chose, as Hermes wrote it (#137714). |
| `test_install_ps1_desktop_stage.py` | install.ps1 desktop stage + single authoritative stage list (audit C27). |
| `test_install_ps1_stable_default.py` | install.ps1 lands a new or rerun official install on the latest stable release. |
| `test_install_sh_chosen_channel.py` | An installer rerun keeps a checkout on the update channel it chose (#137714). |
| `test_install_sh_launch_handoff.py` | Post-PM installer stages use the real installation-bound publication. |
| `test_install_sh_python_pin_indent.py` | install.sh reads the python pin from pm/lock.json by structure, not layout. |
| `test_install_sh_stable_default.py` | A new or rerun install of the official repository lands on the latest stable release. |
| `test_install_stage_frames.py` | The real Bash stage dispatcher emits one JSON result for every exit. |
| `test_install_stamp_distance.py` | A dev install's distance counts from the highest reachable release, not a prerelease. |
| `test_job_groups.py` | Behavior contract for the `jobs` input parser (no workflow YAML is read). |
| `test_macos_channel_artifact_record.py` | Native artifact metadata stays bound to tagged or tagless package inputs. |
| `test_mint_launchers.py` | Live tests for the win32 launcher mint (scripts/build/mint_launchers.py). |
| `test_native_build.py` | PM Bundle shares preparation, not the desktop product dependency closure. |
| `test_payload_digests.py` | Packaged facts describe final tool bytes without changing their identity. |
| `test_pick_release_tags.py` | The release-tag picker reads origin, not the local checkout, and keeps CalVer order. |
| `test_pm_build_consumers.py` | Build adapters consume selected Python environments, never install commands. |
| `test_pm_runtime_bundle.py` | A payload carries PM's independent dependency graph, not the app's imports. |
| `test_powershell_script_syntax.py` | The repo's PowerShell scripts must parse — checked with the REAL parser. |
| `test_release_artifacts.py` | Native metadata and artifact publication use the same verified bytes. |
| `test_release_build_commit.py` | Commit-build entry points resolve real Git refs without publishing releases. |
| `test_release_canary_git.py` | Canary policy on real Git refs; GitHub publication stays an inert boundary. |
| `test_release_changelog.py` | --no-changelog keeps the release body's frame and drops the commit sections. |
| `test_release_channel_build.py` | Channel dispatch names an exact pushed Git commit; CI allocates and builds. |
| `test_release_channels.py` | Exercise publisher/reader through the real signed HTTP transport. |
| `test_release_darwin.py` | tests/scripts/test_release_darwin.py — contract tests for the macOS electron-updater feed publication (port of tests-js/darwin-feed.test.mjs). Feed merge/validation is pure; publication runs against a REAL loopback |
| `test_release_docker_cli.py` | Docker receipt CLI validates identity and hashes actual local archive bytes. |
| `test_release_entrypoint.py` | The release entrypoint claims an attempt, cuts a draft, and dispatches the gate. |
| `test_release_handoff.py` | Release handoffs use exact R2 bytes without advancing a channel. |
| `test_release_lanes.py` | The stable release lanes: what a lane set builds, tests, and records in its claim. |
| `test_release_progress.py` | Release progress logging: stderr only, grouped, and commands stay readable. |
| `test_release_r2.py` | tests/scripts/test_release_r2.py — contract tests for the Python R2 release transport (port of tests-js/r2-release.test.mjs). The SigV4 vectors pin the signer against botocore (the reference implementation, |
| `test_release_revision_anchor.py` | Changelog attribution is anchored to the selected release range. |
| `test_release_sequencer.py` | Stable publication is ordered, held by default, and idempotent. |
| `test_release_store.py` | The green run commits the Store build held; publication tries to switch it to Immediate. |
| `test_release_tag_sampling.py` | Release sampling follows tag chronology across CalVer and SemVer, local tags or not. |
| `test_release_tags.py` | Release-tag policy accepts only the current stable and canary grammars. |
| `test_release_version_from_ref.py` | A ref names a version, and the next version is derived, never read from the tree. |
| `test_render_builds_binding.py` | Commit rows bind a literal producer's receipt, not merely object names. |
| `test_render_builds_publication.py` | Tag pages and release bodies publish the same independently named objects. |
| `test_run_in_hermes_env.py` | ``scripts/run-in-hermes-env``: run a command in the Hermes environment, syncing only when needed. |
| `test_run_tests_parallel.py` | Verify scripts/run_tests_parallel.py kills test-spawned grandchildren. |
| `test_run_tests_parallel_stdio.py` | The runner's status glyphs must not crash narrow console encodings. |
| `test_run_tests_parallel_timeout_scaling.py` | Duration-aware per-file timeout scaling in scripts/run_tests_parallel.py. |
| `test_run_tests_shell.py` | The canonical shell must run tests and propagate a failing test's status. |
| `test_scan_plugin_payloads.py` | Unit tests for the catalog payload scanner (README rule 17). |
| `test_setup_toolchain.py` | The CI bootstrap reads PM's pins without importing installed dependencies. |
| `test_smoke_nemo_relay_shared_metrics.py` | Tests for the shared-metrics smoke artifact. |
| `test_source_build_env.py` | Source E2E children stamp their own checkout, not the workflow's NEW ref. |
| `test_source_driver.py` | Cheap source-driver checks: real shells, disposable installs, no installer. |
| `test_source_update_command.py` | Source E2E updates must follow the staged git branch when supported. |
| `test_stable_admission.py` | Stable admission reads the version and the attempt from the attempt ref, not from the checkout. |
| `test_stable_release.py` | Release gates and package transitions bind the intended immutable artifacts. |
| `test_stage_apt_repo.py` | Tests for scripts/termux/stage_apt_repo.py — stdlib + pytest, no network. |
| `test_termux_agent_assembly.py` | Bionic assembly consumes prepared bytes without running foreign binaries. |
| `test_termux_assembly_permissions.py` | Exercise the build mount's real Linux UID permissions, not Android binaries. |
| `test_termux_build_driver.py` | Exercise the Termux sequencing boundary with real child executables. |
| `test_termux_build_wheels.py` | Pinned source dependencies build online and install from wheelhouse offline. |
| `test_termux_commit_identity.py` | Termux packaging refuses identity mistakes before modifying its payload. |
| `test_termux_deb_version.py` | Literal tag boundaries and real Debian ordering (not a second parser). |
| `test_termux_launchers.py` | Run generated launchers with a real interpreter and captured entrypoint. |
| `test_termux_python_linkage.py` | Exercise the linker repair against a real native extension on Linux. |
| `test_termux_retag_wheel.py` | Behavior contracts for scripts/termux/retag_wheel.py (PEP 738 retagger). |
| `test_termux_runtime_libs.py` | Tests for scripts/termux/stage_runtime_libs.py — cache correctness. |
| `test_termux_update_refusal.py` | The installed-package gate distinguishes commit builds from release packages. |
| `test_termux_wheelhouse_cache.py` | A restored cache is usable only for the exact proven build inputs. |
| `test_tool_store_pins.py` | run_tests.sh shares the account's tool store only when it can run from it as is. |
| `test_upload_summary.py` | Every verified R2 upload lands in the GitHub step summary, with its public URL. |
| `test_validate_plugin_catalog.py` | Behavior tests for scripts/validate_plugin_catalog.py. |
| `test_verify_bootstrap_version_stamp.py` | Tests for scripts/verify-bootstrap-version-stamp.py. |
| `test_verify_plugin_preservation.py` | Unit tests for the plugin upgrade-preservation verifier. |
| `test_verify_user_state.py` | Unit tests for the user-state upgrade-preservation verifier. |
| `test_version_stamping.py` | Release stamping changes only metadata consumed by external builders. |
| `test_webapp_renderer_freshness.py` | A Webapp renderer receipt is current only under the renderer environment it was built with. |
| `test_write_install_stamp.py` | The emitted stamp must preserve build identity and reach the runtime reader. |

## `tests/secret_sources/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `conformance.py` | Conformance kit for :class:`agent.secret_sources.base.SecretSource`. |
| `test_error_remediation.py` | Error remediation for secret sources. |
| `test_profile_secrets.py` | Orchestrator-level profile secret handling. |
| `test_secret_source_registry.py` | Tests for the secret-source contract + orchestrator. |

## `tests/security/`

| File | What it does |
|---|---|
| `test_gitspawn_config_injection.py` | GitSpawn / GHSA-7x36-8jrh-v4pw regression suite. |

## `tests/skills/`

| File | What it does |
|---|---|
| `test_authoring_standards.py` | CI enforcement of the skill authoring standards (AGENTS.md hardline). |
| `test_bundled_skill_doc_placeholders.py` | Bundled skill files must not carry bare chat-role tags. |
| `test_cloudflare_temporary_deploy_skill.py` | Tests for optional-skills/web-development/cloudflare-temporary-deploy/scripts/parse_deploy_output.py |
| `test_comfyui_skill.py` | Invariant tests for the bundled comfyui skill. |
| `test_evidence_store.py` | Tests: `test_evidence_store_add`, `test_evidence_store_sequential_ids`, `test_evidence_store_verify_integrity`, `test_evidence_store_query_searches_multiple_fields`, `test_evidence_store_chain_of_custody`, `test_evidenc… |
| `test_fetch_transcript.py` | Tests for skills/media/youtube-content/scripts/fetch_transcript.py (issue #22243). |
| `test_github_credential_token.py` | Regression tests for scanner-safe GitHub credential extraction (#22722). |
| `test_google_workspace_api.py` | Tests for Google Workspace gws bridge and CLI wrapper. |
| `test_google_workspace_credential_files.py` | Regression test: google-workspace SKILL.md must declare required_credential_files. |
| `test_google_workspace_setup.py` | Google Workspace setup delegates dependency ownership to PM. |
| `test_google_workspace_setup_deps.py` | OAuth must not run against an unavailable or newly selected environment. |
| `test_grounded_citations_skill.py` | Tests for the grounded-citations bundled skill. |
| `test_har_derived_api_client_skill.py` | Tests for the har-derived-api-client optional skill. |
| `test_hyperliquid_skill.py` | Tests: `load_module`, `test_normalize_perp_markets_extracts_change_and_volume`, `test_main_markets_json_prints_normalized_payload`, `test_env_lookup_reads_hermes_dotenv`, `test_user_dotenv_overrides_project_dotenv` |
| `test_live_dashboard_skill.py` | Tests for the live-dashboard optional skill. |
| `test_mcp_oauth_remote_gateway_skill.py` | Tests for the mcp-oauth-remote-gateway optional skill. |
| `test_memento_cards.py` | Tests for optional-skills/productivity/memento-flashcards/scripts/memento_cards.py |
| `test_optional_skill_scripts.py` | Execute optional research helpers offline; upstream/SDK doubles are boundary spies. |
| `test_optional_skill_self_paths.py` | Contract: a skill's self-referencing install paths match its own location. |
| `test_product_price_monitor_skill.py` | Tests for the product-price-monitor skill's price-watch blueprint. |
| `test_property_listings_skill.py` | Property card recipes are optional, discoverable, and loadable on demand. |
| `test_reddit_reading_skill.py` | Tests for optional-skills/social-media/reddit-reading/scripts/reddit.py — backend selection and throttle handling. |
| `test_rss_feeds_skill.py` | Tests for optional-skills/research/rss-feeds/scripts/feed.py — parsing and discovery contracts. |
| `test_skill_blueprint_contracts.py` | Blueprint-to-skill relationships, independent of the generic catalog/renderer tests. |
| `test_skill_docs_contract.py` | Contract: the committed skill docs stay in sync with the shipped skill tree. |
| `test_skill_document_contracts.py` | Specific shipped-document obligations; generic policy lives in test_authoring_standards. |
| `test_skill_pages_match_shipped_skills.py` | Contract: a generated per-skill page exists only while its skill ships. |
| `test_telephony_skill.py` | Tests: `load_module`, `test_save_twilio_writes_env_and_state`, `test_upsert_env_updates_existing_values`, `test_twilio_buy_number_saves_env_and_state`, `test_diagnose_includes_decision_tree_and_saved_state` |
| `test_unbroker_skill.py` | Hermetic tests for the unbroker skill. |
| `test_weekly_review_planning_skill.py` | Invariant: every skill a cron blueprint loads ships as a bundled skill. |
| `test_youtube_quiz.py` | Tests for optional-skills/productivity/memento-flashcards/scripts/youtube_quiz.py |

## `tests/tools/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `_child_env_fixtures.py` | Isolated, real processes for the child-environment contract tests. |
| `browser_launcher_fakes.py` | A fake ``chromium`` for launcher tests that behaves like the real one where the launcher depends on it. |
| `conftest.py` | Shared fixtures for tests/tools/ web-provider tests. |
| `environments/__init__.py` | Package marker / package-level exports |
| `environments/test_local_path_completion.py` | Terminal-subshell PATH completion in ``tools/environments/local.py``. |
| `file_ops_fakes.py` | Fakes for ``ShellFileOperations``' compound shell probes. |
| `test_a2a_reason_roundtrip.py` | Tests: typed reason codes survive the A2A relay roundtrip (#93091). |
| `test_accretion_caps.py` | Accretion caps for _read_tracker (file_tools) and _completion_consumed (process_registry). |
| `test_allowlist_legacy_config.py` | Tests: `test_legacy_string_allowlist_recovers_only_string_lists`, `test_malformed_allowlist_does_not_grant_approval` |
| `test_allowlist_quoted_metachars.py` | Tests for the quote-aware allowlist shell-operator check. |
| `test_annotate_preview_tool.py` | Tests for the GUI-surface ``annotate_preview`` tool. |
| `test_ansi_strip.py` | Comprehensive tests for ANSI escape sequence stripping (ECMA-48). |
| `test_approval.py` | Tests for the dangerous command approval module. |
| `test_approval_bun_deno_eval.py` | Bun and Deno evaluate inline scripts through forms the interpreter flag tables did not know: ``bun -e/--eval``, and Deno's bare ``eval`` subcommand (``deno eval "code"``). They must reach the same approval classificatio… |
| `test_approval_cancelled_attribution.py` | A gateway approval wait that ends without a user answer must not be reported as a user deny. |
| `test_approval_config_readonly.py` | Regression tests: the approval guard path reads config via load_config_readonly() (no per-call deepcopy). |
| `test_approval_deny_rules.py` | Tests for user-defined deny rules (approvals.deny in config.yaml). |
| `test_approval_gateway_wait_coalesce_race.py` | Coalesced gateway approvals under concurrent leader/follower threads. |
| `test_approval_gateway_wait_late_choice.py` | A gateway approval choice that lands after the deadline check is an answer, not a timeout (#112548). |
| `test_approval_global_flag_scan.py` | Global-flag rules must terminate on long flag runs without dropping long commands (#129281). |
| `test_approval_grep_in_substitution.py` | A grep nested inside a command substitution must lex as its own simple command. |
| `test_approval_hook_session_id.py` | Approval hooks must carry the Hermes session id to observer plugins. |
| `test_approval_interrupt.py` | Regression: a blocking gateway approval wait must honor an interrupt (#8697). |
| `test_approval_launchctl_performance.py` | Long non-launchctl inputs must not starve other Gateway threads. |
| `test_approval_lifecycle_guard_parity.py` | Parity between the approval layer and the in-gateway lifecycle hard block (launchctl verbs). |
| `test_approval_mode_parity.py` | Cross-surface approval mode/timeout parity invariant. |
| `test_approval_outcome_parity.py` | Gateway-tail outcome parity + sudo human-wait exclusion (#85125 Phase 2e). |
| `test_approval_plugin_hooks.py` | Tests for pre_approval_request / post_approval_response plugin hooks. |
| `test_approval_timeout_overflow.py` | Regression tests for #83220: oversized approvals.timeout must never overflow platform wait primitives (macOS time_t OverflowError). |
| `test_approval_unattended_presence.py` | Unattended-platform runs resolve flagged commands from ``approvals.unattended_mode`` unless a client can actually answer the card. The gateway exports ``HERMES_EXEC_ASK=1`` to every session it runs, so without this a we… |
| `test_approval_user_summary.py` | Approval and background-task outcomes carry one plain sentence for the person at the keyboard. |
| `test_approval_windows.py` | Windows destructive-command approval coverage (#69472). |
| `test_approval_yolo.py` | The session /yolo contract every surface shares (``tools.approval_yolo``): a toggle persists before it flips the live flag, a fresh process re-arms it from the stored copy, a row created after the toggle records it, and… |
| `test_approved_command_clean_slate.py` | Regression tests: a user-approved command runs from a clean interrupt slate. |
| `test_async_batch_task_failure_notice.py` | A failed child of a still-running detached fan-out is surfaced to the parent immediately. |
| `test_async_delegation.py` | Tests for async (background) delegation — tools/async_delegation.py. |
| `test_async_delegation_failed_surface.py` | Failed async delegations stay visible after the live roster forgets them (#97202). |
| `test_async_delegation_fd_leak.py` | Regression: the async-delegation ledger must close every SQLite connection. |
| `test_async_delegation_orphan_sweep.py` | A completion whose owner process died is re-offered by processes that are ALREADY running (#97202). |
| `test_async_delegation_requeue.py` | An acknowledged completion goes back to the delivery queue when its turn could not confirm the owner. |
| `test_async_delegation_retirement.py` | Background delegations cannot outlive the admission proof used to retire their process. |
| `test_async_delegation_stale_profile_scope.py` | Profile-scope regression for async-delegation stale finalization. |
| `test_async_delegation_worker.py` | Closed ledger authority and token-guarded retry contracts. |
| `test_async_delegation_worker_routing.py` | Worker routing never falls through to raw canonical SQLite. |
| `test_audio_container.py` | Tests for the shared magic-byte audio container sniffer. |
| `test_base_environment.py` | Tests for BaseEnvironment unified execution model. |
| `test_binary_document_write_guard.py` | Tests for the binary-document write guard (port of nearai/ironclaw#7109). |
| `test_blocked_command_guidance.py` | Tests for blocked-command recovery guidance (parser-limit + backgrounding). |
| `test_blueprints.py` | Tests for the blueprints layer (skill frontmatter <-> cron automation bridge). |
| `test_bot_delivery_install_launcher.py` | Bot deliveries must not pin the caller's obsolete dependency generation. |
| `test_bot_desktop_browser.py` | The dock's Browser and the agent's Chromium resolve to one identity: same executable, same user-data-dir — and when a human opened that browser first, the agent attaches to it instead of launching a second one (Chromium… |
| `test_bot_desktop_browser_fence.py` | The bot's browser tools obey the screen lease: while a human holds the shared browser, nothing is dispatched, and a command whose run crossed a takeover loses its result. |
| `test_bot_desktop_idle.py` | Bot Desktop idle auto-stop: a screen nobody used past ``bot_desktop.idle_stop_minutes`` is stopped, one a human holds or that saw recent use is not. |
| `test_bot_desktop_install.py` | Bot Desktop package install: sudo hand-off and single-flight invariants. |
| `test_bot_desktop_launcher_seed.py` | Bot Desktop launcher seeds: the dock only points at programs that exist, the look is applied. |
| `test_bot_desktop_launcher_xvnc.py` | The Bot Desktop's Xvnc is started with the RFB options the lease design relies on. |
| `test_bot_desktop_lease.py` | Bot Desktop invariants: the byte-level RFB input gate follows the lease, and computer_use refuses every action (capture included) while a human holds the screen. |
| `test_bot_desktop_placement.py` | Bot Desktop placement: the screen (and with it computer_use and the browser) follows the terminal backend. |
| `test_bot_desktop_resources.py` | Bot Desktop memory gate: the screen is refused, with a reason clients can show, while the host cannot spare ``bot_desktop.min_free_memory_mb``; a host we cannot read is never treated as small. |
| `test_bot_desktop_rfb_filter_limits.py` | RFB client-message framing at the bridge: a client-declared ClientCutText length is bounded at the header (the bridge must not buffer up to 2 GiB for a viewer that holds a ticket but no lease), and every message type Xv… |
| `test_bot_desktop_runtime.py` | Bot Desktop runtime: thumbnail and display-number allocation invariants. |
| `test_bot_desktop_thumbnail.py` | ``thumbnail_data_url`` swaps the process-wide XAUTHORITY around the grab; two profiles grabbed on worker threads at once must each see their own cookie file, not the other's. |
| `test_bot_dm_payload_cache.py` | DM payload files must be reaped by gateway housekeeping, not only in-band. |
| `test_bot_failure_reasons.py` | Tests: typed failure-reason codes (tools/bot_failure_reasons.py, #93091). |
| `test_bot_legacy_producer.py` | A stale owner advertisement must never create another execution queue. |
| `test_bot_live_delivery_windows_acl.py` | #139485 / #138872 on real Windows ACLs. |
| `test_bot_live_owner_delivery.py` | Canonical delivery invariants: stable envelope IDs, authority-only admission, immutable receipts. The mailbox is receipt storage, never an execution queue. |
| `test_bot_mode_canonical_chat_resolution.py` | Property-style regression suite: Bot Mode canonical-chat resolution algebra. |
| `test_bot_mode_dm.py` | Tests for tools/bot_mode_dm.py — the Bot-Chat-only ``message_agent`` tool. |
| `test_bot_mode_dm_entry.py` | The ``bot_mode_dm.py`` runner entry boots Hermes' dependency environment itself. |
| `test_bot_mode_hermes_handle.py` | @hermes is the default profile's handle only while no real profile is named 'hermes'. |
| `test_bot_mode_probe.py` | Tests for tools/bot_mode_probe.py — the Bot Mode teammate-protocol section. |
| `test_bot_mode_refusal_contract.py` | Tests: `test_one_shot_cli_preserves_refusal_reason` |
| `test_bot_no_fallback.py` | Unavailable authority is a refusal, never permission for another executor. |
| `test_bot_profile_relay.py` | Relay discovery and mailbox ownership are profile scoped. |
| `test_bot_receipt_read_lock.py` | Receipt polling joins the writer's short lock even when replacement rewrites in place. |
| `test_bot_relay.py` | Tests: cross-connection bot relay (tools/bot_relay.py + message_agent route). |
| `test_bot_relay_windows_paths.py` | Windows-path viability and venv CLI resolution for bot relay (#93590). |
| `test_bot_reply_receipt.py` | A relay reply is an immutable delivery receipt, not a last-writer-wins file. |
| `test_bot_retry_policy.py` | Tests: bot-turn retry session policy (#93091 item 5). |
| `test_bot_turn_lock.py` | Tests: per-profile bot turn lock (#93091 — tools/bot_relay.py). |
| `test_browser_cdp_override.py` | Tests: `_no_sessions`, `TestResolveCdpOverride`, `TestGetCdpOverride`, `TestCreateCdpSession`, `TestCDPSupervisorTimeoutRedaction`, `TestCDPSupervisorStartErrorRedaction` … |
| `test_browser_cdp_tool.py` | Unit tests for browser_cdp tool. |
| `test_browser_cleanup.py` | Regression tests for browser session cleanup (tools/browser_session_lifecycle.py). |
| `test_browser_cleanup_owner_scope.py` | Shutdown teardown runs each session under the profile that owns it. |
| `test_browser_cloud_fallback.py` | Tests for cloud browser provider runtime fallback to local Chromium. |
| `test_browser_cloud_provider_cache.py` | Tests for ``browser_session_cloud.get_cloud_provider()`` caching policy. |
| `test_browser_command_timeout_race.py` | Regression tests for the browser command-timeout cache (#14331). |
| `test_browser_computer_use_profile_cache_keys.py` | Browser-exec and computer_use backend caches are namespaced by the served profile. |
| `test_browser_config_effective.py` | ``browser.*`` reads go through the effective user config: the managed overlay wins over the profile's file and ``${VAR}`` references expand, as for every other runtime reader (hermes_cli/AGENTS.md, Three loaders). A raw… |
| `test_browser_env_loopback_no_proxy.py` | Loopback CDP dials must never go through a proxy (#110565). |
| `test_browser_eval_ssrf.py` | Page-driven JS must not bypass the browser SSRF guard via URL literals. |
| `test_browser_eval_supervisor_path.py` | Unit tests for ``CDPSupervisor.evaluate_runtime`` response shaping (the eval path browser_vault and browser_exec's supervisor share), using mocks — no real browser, no real WebSocket. Real-CDP coverage lives in ``tests/… |
| `test_browser_hardening.py` | Browser hardening: config-driven inactivity timeout and URL-encoded secret exfiltration. |
| `test_browser_headed_mode.py` | Tests for headed browser mode: config resolution, the headed local launch, and the per-turn cleanup skip that keeps headed sessions alive between turns. |
| `test_browser_hybrid_routing.py` | Tests for hybrid browser-backend routing (LAN/localhost auto-local). |
| `test_browser_launcher.py` | Behaviour contracts of the Python Chromium launcher (tools/browser_launcher.py). |
| `test_browser_launcher_alias.py` | A shared profile reached through a symlink is the same browser launch: adopting it keeps its launch identity. |
| `test_browser_launcher_foreign_attach.py` | A shared-profile Chromium held from an environment this process cannot verify (a container gateway's browser seen from the host CLI, or the other way round) is never launched over, deleted or reaped from here. |
| `test_browser_launcher_holders_lock.py` | The Windows holder lock (``tools/browser_launcher_holders.records_lock``) retries only lock contention, and only for a bounded time: a lock leaked by a hung process fails the caller with a clear error instead of hanging… |
| `test_browser_launcher_identity.py` | A browser in launcher state is ONE launch: its PID namespace and boot, pid, process start time and profile (``--user-data-dir`` realpath), never its pid number alone. |
| `test_browser_launcher_pidns.py` | A pid in launcher state means something only inside the PID namespace and boot that wrote it. |
| `test_browser_launcher_reclaim.py` | The reaper never deletes the throwaway profile of a Chromium that is still running on it. |
| `test_browser_launcher_shared_profile.py` | One persistent (shared) profile has ONE Chromium, whichever Hermes home or launcher key reaches it. |
| `test_browser_launcher_shared_start.py` | Starting a persistent (shared) profile's browser is one step under the profile's cross-process lock. |
| `test_browser_launcher_unresponsive.py` | A live browser whose DevTools endpoint stops answering for a while is still the profile's browser. |
| `test_browser_lightpanda.py` | Tests for the Lightpanda engine (``browser.engine: lightpanda``) in the browser session layer. |
| `test_browser_lightpanda_serve.py` | Tests for tools/browser_lightpanda.py — the ``lightpanda serve`` launcher Browser Use mode uses when ``browser.engine`` is ``lightpanda``. |
| `test_browser_open_timeout.py` | Tests for the Chromium first-launch timeout floor and the sandbox-bypass host probe. |
| `test_browser_orphan_reaper.py` | Tests for the browser orphan reaper: Chromium launched by a Hermes process that exited without cleaning up is found through the launcher's per-profile records and stopped, but only after its identity is proven (``tools.… |
| `test_browser_pm.py` | Browser consumers use real PM facts, not ambient caches: the launcher's Chromium is PM's pinned Chromium (or the user's explicit override), acquired through PM at most once per process. |
| `test_browser_profile_live_cdp.py` | CLI-9 (#134889): a live ``/browser connect`` belongs to ONE profile on a multiplexed gateway. |
| `test_browser_profile_scope_edges.py` | GW-23 (#134889): per-profile browser scope edges left after CLI-9. |
| `test_browser_real_profile.py` | Tests for real-profile browsing: resolvers, snapshot, launch routing, consent. |
| `test_browser_real_profile_copy_lock.py` | The real-profile snapshot (the overlay of the user's Cookies / Login Data onto the profile copy) is part of the launch step under the copy dir's cross-process launcher lock: two Hermes processes of one profile never cop… |
| `test_browser_real_profile_pin.py` | Tests for the LOCAL real_profile_pin patch (browser.real_profile_pin). |
| `test_browser_redact_depth.py` | Page-controlled JSON must not crash browser output redaction (#137067). |
| `test_browser_sandbox_stop_identity.py` | The sandbox Chromium is signalled only while its pid still names the browser this process launched. |
| `test_browser_secret_exfil.py` | Tests for secret exfiltration prevention in browser and web tools. |
| `test_browser_session_profile_keys.py` | Served-profile isolation of local browsers: one process serving profile A, then B, then A again must hand each profile its OWN Chromium (profile dir under that profile's HERMES_HOME), and A's browser again on the return… |
| `test_browser_ssrf_local.py` | SSRF checks respect local-backend mode and the allow_private_urls setting. |
| `test_browser_supervisor.py` | Integration tests for tools.browser_supervisor. |
| `test_browser_supervisor_capture.py` | Behavior contract for ``SUPERVISOR_REGISTRY.capture`` (public CDP seam for trusted plugins). |
| `test_browser_supervisor_capture_dispatch.py` | Dispatch/lossless-wait extension exercised through the real public capture API. |
| `test_browser_supervisor_healthcheck.py` | Unit tests for _SupervisorRegistry cache-hit healthcheck. |
| `test_browser_supervisor_reconnect.py` | CDPSupervisor reconnect budget: a supervisor that attached once must not retry a dead endpoint forever (#114172). No real Chrome — ``websockets.connect`` is stubbed. |
| `test_browser_use_cli.py` | Tests for ``browser_exec`` (tools/browser_use_cli.py), Hermes' only core browser tool. |
| `test_browser_use_harness.py` | Browser Use caller -> browser-harness on Hermes's own interpreter -> actual child. |
| `test_browser_use_session_expiry.py` | Regression coverage for provider-authoritative cloud browser expiry. |
| `test_browser_use_shot.py` | browser_exec ``capture_screenshot()`` on a hidden tab (tools/browser_use_shot.py). |
| `test_browser_vault.py` | Tests for the vault-backed password-blind browser autofill feature. |
| `test_browser_vault_origin_guard.py` | Every secret-bearing browser_vault fill is bound to the item's saved origins. |
| `test_browser_vault_page_backend.py` | browser_vault on a plugin browser with no CDP endpoint (Camofox): the registered ``BrowserPageBackend`` holding the task's page carries every vault script, and the secret path never lets a page or backend error echo the… |
| `test_browser_vault_plugin_isolation.py` | Isolation contract for plugin-registered browser-vault login backends. |
| `test_browser_windows_headless.py` | Regression for #64867: local Chromium stays headless on Windows Desktop. |
| `test_budget_config.py` | Unit tests for tools/budget_config.py. |
| `test_build_subprocess_env.py` | Real children observe factory scrubbing, overrides and routed profile homes. |
| `test_capability_fingerprint_skill_scope.py` | The capability epoch tracks the skills the model can actually invoke. |
| `test_checkpoint_footprint_notice.py` | ``checkpoint_footprint_notice``: tells a user their /rollback store is on and large. |
| `test_checkpoint_gitlinks.py` | Real-Git rollback contracts for checkpoints containing uncaptured gitlinks. |
| `test_checkpoint_manager.py` | Tests for tools/checkpoint_manager.py — CheckpointManager (v2 single-store). |
| `test_checkpoint_path_roundtrip.py` | Checkpoint file names must survive Git's machine-readable path output. |
| `test_checkpoint_size_cap.py` | Real history retention and failure propagation at the public pruning callers. |
| `test_checkpoint_store_ownership.py` | Maintenance cannot prune objects another checkpoint process has not published. |
| `test_child_env_supervisor_identity.py` | A supervisor's identity describes only the process it started, never that process's children. |
| `test_clarify_gateway.py` | Tests for the gateway-side clarify primitive (tools/clarify_gateway.py). |
| `test_clarify_tool.py` | Tests for tools/clarify_tool.py - Interactive clarifying questions. |
| `test_clawhub_owner_http.py` | Owner-qualified ClawHub fetches retain identity across actual HTTP requests. |
| `test_clawhub_zip_stream.py` | Bound the archive before extraction, without buffering response.content. |
| `test_cli_approval_exec_ask_leak.py` | Regression: interactive CLI must not lose the Dangerous Command panel. |
| `test_clipboard.py` | Tests for clipboard image paste — clipboard extraction, multimodal conversion, and CLI integration. |
| `test_close_preview_tool.py` | Tests for the GUI-surface ``close_preview`` tool. |
| `test_code_execution.py` | Tests for the code execution sandbox (programmatic tool calling). |
| `test_code_execution_file_rpc.py` | Generated stubs and the production file poller over real shell/filesystem I/O. |
| `test_code_execution_hermes_home.py` | execute_code child env honors the multiplexed per-turn HERMES_HOME override (#110303). |
| `test_code_execution_modes.py` | Real interpreter, environment and RPC contracts for both execution modes. |
| `test_code_execution_pm_runtime.py` | PM runtime dependencies survive the kernel child boundary (#124049). |
| `test_code_execution_windows_env.py` | Windows essentials and the native Winsock control. |
| `test_code_kernel.py` | Tests for execute_code's session kernel. |
| `test_code_kernel_remote.py` | Remote session kernels (tools/code_kernel_remote.py) — hermes-agent#96873. |
| `test_command_guards.py` | Tests for check_all_command_guards() — the combined floor + dangerous-command guard. |
| `test_compaction_tool_refresh.py` | Compaction rebuilds dynamic tool schemas (forever-session fix, #95681 arc). |
| `test_completed_process_results.py` | Completed work remains retrievable when its finite CLI owner exits. |
| `test_computer_use.py` | Tests for the computer_use toolset (cua-driver backend, universal schema). |
| `test_computer_use_approval_isolation.py` | computer_use approval is the shared ``tools.approval`` gate — no private grant store, no default-allow. |
| `test_computer_use_ax_walk_bound.py` | Bound on the driver's accessibility-tree walk per capture (``computer_use.ax_max_elements``). |
| `test_computer_use_backend_lifecycle.py` | Backend admission during Bot Screen rebind/release; extracted from #114565 for #108914. |
| `test_computer_use_backend_plugins.py` | Computer-use provider plugins: ``computer_use.backend`` selects exactly one provider per profile, only that one is imported, the built-in ``cua`` stays the default, and an unknown name fails loudly instead of falling ba… |
| `test_computer_use_backend_rebind.py` | A cached computer_use backend is bound to the display it spawned on; the identity helpers notice a change. |
| `test_computer_use_capture_fence.py` | A frame captured across a human takeover never leaves the process: the lease fence runs as soon as the backend hands the frame back, before it is persisted to the media cache, spilled, or routed to aux vision. |
| `test_computer_use_capture_routing.py` | End-to-end regression for #24015 — capture routing via auxiliary.vision. |
| `test_computer_use_capture_self_window.py` | Capture target selection must never implicitly target Cua Driver itself. |
| `test_computer_use_cua_0_10_permissions.py` | Behavior contracts for cua-driver 0.10 permission-mode integration. |
| `test_computer_use_cua_0_9.py` | Behavior contracts for cua-driver's verify/escalate and typed-browser ladder. |
| `test_computer_use_cua_backend_linux.py` | Regression tests for Linux/X11 capture target selection (#58026, #54173). |
| `test_computer_use_cua_macos_identity.py` | macOS CuaDriver.app path and signing identity contracts. |
| `test_computer_use_delivery_ladder.py` | Regression tests for the cua-driver verify → escalate ladder. |
| `test_computer_use_display_count_guard.py` | macOS ScreenCaptureKit display_count=0 diagnosability. |
| `test_computer_use_doctor_stale_units.py` | `hermes computer-use doctor` names a daemon unit whose cua-driver Exec target was pruned, and a configured `cua-driver serve` unit whose daemon is not listening (#114748). |
| `test_computer_use_empty_discovery_diagnosis.py` | Diagnosability of empty window discovery + CLI-fallback fail-fast. |
| `test_computer_use_fullscreen_capture.py` | Full-screen vs desktop-shell capture routing (#60081, wallpaper-only bug). |
| `test_computer_use_input_target_guard.py` | Input actions must not silently deliver to a different app than requested. |
| `test_computer_use_native_platform.py` | Exercise existing computer-use actions on the actual Windows/macOS CI hosts. |
| `test_computer_use_null_pid_windows.py` | Regression for the X11 null-PID `list_windows` crash. |
| `test_computer_use_placeholder_ids.py` | A zero-filled ``pid``/``window_id`` must not be read as exact targeting. |
| `test_computer_use_screenshot_dedup.py` | Screenshot dedup — unchanged frames are delivered without their image. |
| `test_computer_use_zero_bounds.py` | Zero-rect AX bounds must read as 'unknown', never as a clickable position. |
| `test_computer_use_zero_delivery_verdict.py` | Zero-delivery `type` verdict: web inputs behind trusted-event checks swallow synthetic keystrokes entirely (delivered 0 of N). Retrying the same delivery rung cannot help; the actionable next step is the AX set_value pa… |
| `test_config_null_guard.py` | Tests for config.get() null-coalescing in tool configuration. |
| `test_connector_accounts.py` | Several accounts of one connector, each addressed by its name (alias). |
| `test_connector_bridge_wiring.py` | Behavior tests for the connector leg of the tool_search bridge. |
| `test_connector_dispatch_policy.py` | Real connector dispatch must run policies against each composed name. |
| `test_connector_files.py` | Connector file inputs and outputs: the model passes local paths, the agent stages them through the tool gateway and storage, and files a tool returns are saved under the profile's downloads folder. |
| `test_connector_local_batches.py` | Local deferred tools retain the live agent path; batches must not bypass it. |
| `test_connector_names.py` | Invariant tests for model-facing connector names and wire-slug recovery. |
| `test_connector_session_scope.py` | Connector capabilities follow session grants, not process-wide credentials. |
| `test_connector_wire_identity.py` | Caller identity on connector requests: the User-Agent always, correlation ids only with consent, the gateway's request id logged on every outcome, and ``initiator`` on each connect path. |
| `test_connectors_catalog.py` | ``manage_catalog`` (catalog install through the connection card). |
| `test_connectors_contract.py` | Connection contract: target states, who may cause each transition, settle reasons. |
| `test_connectors_display.py` | ``manage_connections`` action ``display``: the desktop directory card. |
| `test_connectors_execute_status.py` | Single-call execute: every failure status becomes the call's own error entry, the model-facing shape stays what the array envelope produced, and an older gateway still works through the array form. |
| `test_connectors_gateway_client.py` | Behavior tests for ConnectorClient and the bridge entry points. |
| `test_connectors_gateway_merge.py` | Behavior tests for the pure connectors.gateway merge/partition/name logic. |
| `test_connectors_gateway_wire.py` | Gateway wire model: the status vocabulary the gateway sends is typed, unknown values fail loud, and the execute-path CONNECTION_REQUIRED error carries a link only where no card exists. |
| `test_connectors_guest_on_first_use.py` | A guest identity for connectors is created on the first hosted connector action. |
| `test_connectors_import_deadlock.py` | Regression tests for the ``tools.connectors`` import surface. |
| `test_connectors_live.py` | Live operation registry: one open op per session, found by op_id, closed on settle. |
| `test_connectors_managed.py` | Managed connectors on the connection operation. |
| `test_connectors_mcp.py` | MCP targets of manage_connections (the fold that retired setup_mcp). |
| `test_connectors_operation.py` | Connection operation: transitions checked against the contract, exactly-once settlement, server-owned deadline as a constant, wake on every change. |
| `test_connectors_tool.py` | Behavior tests for manage_connections. |
| `test_container_cwd_sanitize.py` | Regression tests for host-path cwd sanitization on container backends. |
| `test_credential_files.py` | Tests for credential file passthrough and skills directory mounting. |
| `test_credential_pool_env_fallback.py` | Tests for credential_pool .env fallback and auth credential_pool lookup. |
| `test_cron_approval_mode.py` | Tests for approvals.cron_mode — configurable approval behavior for cron jobs. |
| `test_cron_not_interactive.py` | Unattended approval contexts never resolve as interactive (#110932). |
| `test_cron_prompt_injection.py` | Regression tests for cron prompt injection scanner bypass. |
| `test_cron_run_notice_usage.py` | A manual cron run's completion notice reports the model and API calls its run session recorded. |
| `test_cronjob_job_args.py` | Tests for tools/cronjob_job_args.py::_validate_cron_script_path (issue #105761). |
| `test_cronjob_run_background.py` | Tests for cronjob action='run' background dispatch. |
| `test_cronjob_run_delivery_notice.py` | Honesty of the manual-run delivery notice (issue #83993). |
| `test_cronjob_run_immediate.py` | Tests for cronjob action='run' immediate execution (#41037). |
| `test_cronjob_run_primary_routed.py` | Manual runs of a satellite job that delivers through the primary gateway's profile route. |
| `test_cronjob_tools.py` | Tests for tools/cronjob_tools.py — prompt scanning, schedule/list/remove dispatchers. |
| `test_cross_profile_guard.py` | Tests for the cross-profile soft guard wired into write_file / patch / skill_manage. |
| `test_daemon_pool.py` | Tests for tools.daemon_pool.DaemonThreadPoolExecutor. |
| `test_daytona_environment.py` | Unit tests for the Daytona cloud sandbox environment backend. |
| `test_debug_helpers.py` | Tests for tools/debug_helpers.py — DebugSession class. |
| `test_deferral_fixes.py` | Deferral-layer fixes: behavior regression suite. |
| `test_delegate.py` | Tests for the subagent delegation tool. |
| `test_delegate_apiserver_background.py` | delegate_task(background=true) on stateless API-server sessions. |
| `test_delegate_batch_tag.py` | Batch tag on delegation progress lines (#p1-campaign feedback, Sep 2026). |
| `test_delegate_batch_validation.py` | Batch input validation for delegate_task(tasks=[...]). |
| `test_delegate_capability_inheritance.py` | Subagent capability inheritance (follow-up to #94036/#97292). |
| `test_delegate_capacity_interrupt.py` | A rejected background batch retains synchronous cancellation ownership. |
| `test_delegate_child_cache_ttl.py` | Subagents never inherit the 1h prompt-cache tier: with ``prompt_caching.cache_ttl: 1h`` the parent keeps 1h, the child is built at 5m, and the child's wire markers carry no ``ttl``. A disabled cache stays disabled (the… |
| `test_delegate_child_compression_cap.py` | ``delegation.compression_threshold_tokens`` is an OPTIONAL absolute cap on a subagent's compaction trigger, off by default, and its value is validated rather than coerced. |
| `test_delegate_child_transcript_release.py` | Finished delegate children must not pin their transcripts in the parent heap. |
| `test_delegate_completion_model.py` | The async completion header names the model the children actually run on. |
| `test_delegate_composite_toolsets.py` | Tests for composite toolset expansion in delegate_task intersection. |
| `test_delegate_control_actions.py` | delegate_task(action=...) — model-facing live orchestration of subagents. |
| `test_delegate_cost_footer.py` | Per-delegation cost in the serialized result entry. |
| `test_delegate_cron_sync_fallback.py` | Regression test for #86632: cron's synchronous delegate_task fallback must return after the child completes — the automatic background review must not fire inside the delegated child. |
| `test_delegate_depth_prompt.py` | Child-facing nesting guidance must agree with depth-derived capability. |
| `test_delegate_external_provider.py` | A pinned command keeps the provider whose runtime resolved it through child command resolution. |
| `test_delegate_failure_copy.py` | Subagent failure lines gloss the classified `failure_reason` instead of echoing the child's raw exception, and always name the next step (/agents). Contract tests, not snapshots. |
| `test_delegate_fallback_matrix.py` | Pin x delegation.fallback_providers decision table for child agents (#80450, #65038). |
| `test_delegate_gateway_inline.py` | A session's ``delegate_task`` schema decides whether its children join in the call. |
| `test_delegate_group_schema.py` | Grouping is advertised only when the delivery policy consumes it. |
| `test_delegate_images.py` | Per-task image forwarding on delegate_task: a task's ``images`` (local paths, http(s) or data: URLs) reach a vision-capable child as native ``image_url`` content parts on its goal turn; non-vision children get ``[Image… |
| `test_delegate_interrupted_partial_output.py` | Invariant: a child stopped mid-work reports what it HAD so far. The loop's ``final_response`` for an interrupted turn is the placeholder ``"Operation interrupted."`` (also appended as the closing assistant row); the par… |
| `test_delegate_kanban_isolation.py` | Regression tests for delegate_task isolation from parent Kanban workers. |
| `test_delegate_late_child_inherits_stop.py` | A stop that lands on an orchestrator subagent mid-fan-out reaches every grandchild it builds afterwards. |
| `test_delegate_liveness_timeout.py` | ``delegation.child_timeout_seconds`` bounds INACTIVITY, not total runtime (#116001). |
| `test_delegate_native_vision.py` | Delegated children keep the route identity required by native vision. |
| `test_delegate_output_schema.py` | T1-24: structured-output schema on delegate_task. |
| `test_delegate_parallel_interrupt_join.py` | A wedged child must not hold the parent past an interrupt (#116435). |
| `test_delegate_request_overrides.py` | Regression tests for the delegation.request_overrides config key. |
| `test_delegate_stale_heartbeat_collect.py` | A child whose worker settles shortly AFTER the heartbeat's stale verdict must be COLLECTED — its recorded result wins over a synthesized timeout (#113222). |
| `test_delegate_stale_wait_release.py` | A child whose worker never returns after the heartbeat declares it stale must not hold the parent forever (#109749: sync delegation in a -Q one-shot kept the Bot Chat lease). |
| `test_delegate_subagent_timeout_diagnostic.py` | Regression tests for subagent timeout diagnostic dump (issue #14726). |
| `test_delegate_summary_budget.py` | Tests for subagent summary budgeting (PR #9126). |
| `test_delegate_sync_failure_echo_policy.py` | Salt R11-B1: synchronous child failure echo above the CLI spinner is an automatic diagnostic presentation and honors display.suppress_warning_notifications under the parent's turn snapshot; the child result and the rela… |
| `test_delegate_timeout_cleanup.py` | Regression coverage for timed-out delegation teardown. |
| `test_delegate_toolset_scope.py` | Tests for delegate_tool toolset scoping. |
| `test_delegated_output_redaction.py` | Completed child output must be redacted before delegation consumers (#137594). |
| `test_delegation_backends.py` | delegation.backend: pluggable delegation providers decide each delegate_task task's route. |
| `test_delegation_live_log.py` | Tests for tools/delegation_live_log.py — live subagent transcripts. |
| `test_delegation_profile_route.py` | A profile route runs the child AS that profile: its config, model, credentials and SOUL, never the launching profile's — through the same scope binding a multiplexed gateway uses for a routed turn. |
| `test_delegation_recovery_diagnostics.py` | Public dispatch/restart diagnostics for an owner lost before any child finishes. |
| `test_delegation_route_fields.py` | Route fields a delegation backend returns: ``service_tier`` is checked like ``/fast`` and survives child construction, an unknown ``reasoning_effort`` refuses that task, and a backend-routed result reports what the chil… |
| `test_denial_circuit_breaker.py` | Tests for the consecutive-denial circuit breaker in smart approvals. |
| `test_desktop_tools_diet.py` | Desktop tool consolidation + diet (#95681, maintainer-directed). |
| `test_desktop_ui.py` | Tests for the desktop-only renderer-event bridge. |
| `test_discord_send_message_caption.py` | Discord standalone MEDIA:<path> caption delivery. |
| `test_discord_tool.py` | Tests for the Discord server introspection and management tool. |
| `test_display_toggles.py` | The desktop's Appearance switches, as the AGENT experiences them. |
| `test_docker_backend_real.py` | The Docker terminal backend against a real daemon and a real container. |
| `test_docker_cgroup_limits.py` | Tests for cgroup resource-limit gating in the docker backend. |
| `test_docker_config_migrate.py` | Tests: `_load_script_module`, `_run_migration`, `test_docker_config_migrate_backs_up_and_migrates_legacy_config`, `test_docker_config_migrate_skips_below_floor_config_untouched`, `test_docker_config_migrate_stamps_unver… |
| `test_docker_daemon_redirect.py` | Docker/Podman daemon-redirect and lifecycle flag-insertion detection. |
| `test_docker_environment.py` | Tests: `_mock_subprocess_run`, `_make_dummy_env`, `test_ensure_docker_available_raises_when_not_found`, `test_auto_mount_host_cwd_adds_volume`, `_make_execute_only_env`, `test_init_env_args_uses_hermes_dotenv_for_allowl… |
| `test_docker_find.py` | Tests for tools.environments.docker.find_docker — Docker CLI discovery. |
| `test_docker_mounted_host_session_cwd.py` | A session cwd that IS the directory mounted at /workspace must not be a container cd. |
| `test_docker_network_config.py` | Regression tests for the Docker terminal network toggle. |
| `test_docker_orphan_reaper_integration.py` | Integration tests for the docker orphan-reaper wiring in terminal_tool. |
| `test_docker_ownership_handback.py` | Root-run Docker sandboxes hand their bind-mounted files back to the host user after the container stops and before it is removed; the next root container takes back exactly those files. |
| `test_docker_rebootstrap_nous_session.py` | Unit tests for scripts/docker_rebootstrap_nous_session.py. |
| `test_docker_session_isolation.py` | Per-session docker container isolation (docker + container_persistent: false). |
| `test_docker_teardown_drain.py` | #86317: a container-teardown worker must be joined at exit even after the idle reaper popped its env out of ``_active_environments`` (the atexit drain only knew the registry, so ``docker rm`` for a detached env died wit… |
| `test_docker_windows_cwd_mount.py` | Docker must bind a configured Windows workspace even when /workspace is taken. |
| `test_drain_fd_windows.py` | Windows stdout drain: bounded when a grandchild keeps the pipe's write handle open. |
| `test_drain_high_fd.py` | Regression for #94928: no output reader may lose output once its fd is at or above FD_SETSIZE (1024). |
| `test_drive_preview_tool.py` | Tests for the GUI-surface ``drive_preview`` tool. |
| `test_ensure_task_env.py` | Unit tests for terminal_tool.ensure_task_env — the lazy sandbox bring-up used by vision_analyze so a session's first action can be an in-sandbox file read without a prior terminal command (issue #62825). |
| `test_env_passthrough.py` | Tests for tools.env_passthrough — skill and config env var passthrough. |
| `test_env_probe.py` | Tests for tools/env_probe.py — local Python toolchain probe. |
| `test_escape_drift_autocorrect.py` | Tests for escape-drift auto-correction on ``patch`` (tools/escape_drift_autocorrect.py). |
| `test_execute_code_approval_cluster.py` | Regression tests for the execute_code approval-bypass cluster. |
| `test_execute_code_lifecycle_guard_deadline.py` | execute_code's gateway-lifecycle identity probe shares the cell deadline (#111922). |
| `test_execute_code_local_session_approval.py` | execute_code approval in a gateway-run local session (T2). |
| `test_execute_helper_contract.py` | Execute the helper usage taught by the public schema and recovery hints. |
| `test_execution_flag_detection.py` | Execution-bearing option detection across interpreters and read-only tools. |
| `test_explicit_mcp_schema_reload.py` | Explicit reloads refresh a changed MCP schema even when tool names are unchanged. |
| `test_fal_common.py` | Tests for tools/fal_common.py — shared FAL.ai SDK plumbing. |
| `test_fal_sdk.py` | Managed FAL adapter against the installed SDK; only HTTP leaves are replaced. |
| `test_file_operations.py` | Tests for tools/file_operations.py — deny list, result dataclasses, helpers. |
| `test_file_operations_delete.py` | Behavior tests for ``ShellFileOperations.delete_file`` (real LocalEnvironment shell). |
| `test_file_operations_edge_cases.py` | Tests for edge cases in tools/file_operations.py. |
| `test_file_ops_cwd_tracking.py` | Regression tests for cwd-staleness in ShellFileOperations. |
| `test_file_ops_env_not_ready.py` | A terminal environment that cannot run commands (container still starting, removed out-of-band, transport down) must surface as an environment error, never as "File not found": the model trusts a false negative for the… |
| `test_file_ops_single_roundtrip.py` | ``read_file`` / ``write_file`` cost one shell round-trip, not four. |
| `test_file_read_guards.py` | Tests for read_file_tool safety guards: device-path blocking, character-count limits, file deduplication, and dedup reset on context compression. |
| `test_file_staleness.py` | Tests for file staleness detection in write_file and patch. |
| `test_file_state_registry.py` | Tests for the cross-agent FileStateRegistry (tools/file_state.py). |
| `test_file_sync.py` | Tests for FileSyncManager — mtime tracking, deletion detection, transactional rollback. |
| `test_file_sync_back.py` | Tests for FileSyncManager.sync_back() — pull remote changes to host. |
| `test_file_sync_sigint.py` | Cross-platform regression for the deferred-SIGINT re-delivery in sync-back. |
| `test_file_sync_upload_snapshot.py` | Upload hashes must describe the bytes received by the remote sandbox. |
| `test_file_tools.py` | Tests for the file tools module (schema, handler wiring, error paths). |
| `test_file_tools_confined_backend.py` | A backend that confines execution keeps the file tools inside it. |
| `test_file_tools_container_config.py` | Tests for docker container_config key propagation in file_tools. |
| `test_file_tools_cwd_resolution.py` | Regression tests for file-tool path resolution base correctness. |
| `test_file_tools_live.py` | Live integration tests for file operations and terminal tools. |
| `test_file_tools_plugin_container_cwd.py` | The file-tools env creation path applies the container cwd guard through the same predicate the terminal tool uses, so a plugin backend declaring ``is_container`` gets a host-path override sanitized exactly like docker… |
| `test_file_tools_tilde_profile.py` | Regression tests for profile-aware tilde expansion in file tools. |
| `test_file_write_safety.py` | Tests for file write safety and HERMES_WRITE_SAFE_ROOT sandboxing. |
| `test_file_write_surrogate_roundtrip.py` | Surrogate-safe stdin piping for the local execution environment (#79178). |
| `test_find_shell.py` | Tests for _find_shell — user-login-shell preference on POSIX. |
| `test_finite_delegation_outcomes.py` | Finite dispatch returns sibling outcomes, not an orphaned async handle. |
| `test_focus_pane_tool.py` | Tests for the GUI-surface ``focus_pane`` tool. |
| `test_fuzzy_match.py` | Tests for the fuzzy matching module. |
| `test_gateway_cwd_contract.py` | Tool-surface cwd contract tests for gateway workspaces. |
| `test_generation_source_confinement.py` | Tests for the generation-tool source-image confinement chokepoint. |
| `test_git_consumer_environment.py` | Git consumers use the selected package environment without owning its layout. |
| `test_gnu_long_option_abbreviation_bypass.py` | Tests for GNU long-option abbreviation bypass in DANGEROUS_PATTERNS. |
| `test_hardline_blocklist.py` | Tests for the unconditional hardline command blocklist. |
| `test_hardline_escaped_quote_state.py` | The hardline floor judges shell quoting on the AUTHOR's text, not on normalized text. |
| `test_hermes_subprocess_env.py` | Tests for hermes_subprocess_env() — the centralized credential-safe env builder for the non-terminal subprocess spawn surface. |
| `test_hook_output_spill.py` | Tests for tools.hook_output_spill. |
| `test_hub_lock_non_utf8.py` | Regression test for #68053 — hub lock.json with Windows-1252 bytes. |
| `test_human_input_hooks.py` | on_human_input_request / on_human_input_resolved fire wherever the agent blocks for a human (#132333). |
| `test_image_generate_schema.py` | image_generate dynamic schema — capability-gated params (#95681 diet). |
| `test_image_generation.py` | Tests for tools/image_generation_tool.py — FAL multi-model support. |
| `test_image_generation_artifacts.py` | Tests: `test_postprocess_adds_agent_visible_image_for_active_ssh_env`, `test_concurrent_image_results_preserve_shared_remote_sync_state`, `test_handle_image_generate_postprocesses_plugin_result` |
| `test_image_generation_env.py` | FAL_KEY env var normalization (whitespace-only treated as unset). |
| `test_image_generation_image_to_image.py` | Tests for the image-to-image / editing surface of ``image_generate``. |
| `test_image_generation_interrupt.py` | _wait_fal_result must notice a user interrupt while the FAL job runs. |
| `test_image_generation_managed.py` | The single managed image row: model id → gateway, and a de-duplicated union catalog. |
| `test_image_generation_plugin_dispatch.py` | Tests: `_reset_registry`, `TestPluginDispatch` |
| `test_image_source.py` | Tests for tools/image_source.py — the unified vision image-source resolver. |
| `test_init_session_cwd_respect.py` | Tests that init_session() respects the configured cwd. |
| `test_interrupt.py` | Tests for the interrupt system. |
| `test_interrupted_command_cwd.py` | An interrupted command must not adopt the shared environment's cwd. |
| `test_kanban_comment_injection.py` | Live operator-note injection into a running kanban worker. |
| `test_kanban_complete_parents_tool.py` | Dependency refusals name the open parents on every surface. |
| `test_kanban_descendant_scope.py` | Real shell/CLI ingress: inherited context is not a board-write grant. |
| `test_kanban_persisted_identity.py` | Board identity follows the profile a kanban call runs FOR, never the generic ``"worker"``. |
| `test_kanban_provenance.py` | Worker provenance is not a dependency edge or a transient runtime session. |
| `test_kanban_redaction.py` | Tests: redact_sensitive_text is applied in kanban tool handlers. |
| `test_kanban_tools.py` | Tests for the Kanban tool surface (tools/kanban_tools.py). |
| `test_kanban_toolset_opt_in.py` | Saved tool opt-ins must reach the real schema without leaking across platforms. |
| `test_kanban_unknown_arguments.py` | Unknown review arguments must not silently mutate the board (#115641). |
| `test_kill_verify_tree_death.py` | Post-kill tree-death verification (#115490). |
| `test_known_file_write_baseline.py` | Whole-file knowledge survives what does not change it. |
| `test_launchctl_guard_diagnostic.py` | Diagnostics must distinguish policy rejection from inspected job properties. |
| `test_lazy_deps_runtime.py` | Retired runtime installers must not turn agent construction into an update. |
| `test_line_ending_preservation.py` | Tests for CRLF line-ending preservation in write_file and patch. |
| `test_live_env_cwd_override_sanitize.py` | Invariants for cwd overrides written into LIVE cached envs (#113894, #98723). |
| `test_llm_content_none_guard.py` | Tests for None guard on response.choices[0].message.content.strip(). |
| `test_local_background_child_hang.py` | Regression tests for issue #8340. |
| `test_local_cwd_permission_fallback.py` | Regression tests for inaccessible-cwd fallback (#65583). |
| `test_local_env_blocklist.py` | Child-observed terminal policy, profile lifetime and PYTHONPATH provenance. |
| `test_local_env_bot_desktop.py` | Terminal child envs route GUI launches to the running Bot Desktop (#125830). |
| `test_local_env_cwd_recovery.py` | Tests for LocalEnvironment recovery when ``self.cwd`` is deleted. |
| `test_local_env_relative_cwd.py` | Regression tests for local terminal initial cwd normalization. |
| `test_local_env_session_leak.py` | Cross-session HERMES_SESSION_* leak guard for the local terminal backend. |
| `test_local_env_windows_msys.py` | Tests for the Windows / Git Bash MSYS-path normalization in ``LocalEnvironment``. |
| `test_local_interrupt_cleanup.py` | Regression tests for _wait_for_process subprocess cleanup on exception exit. |
| `test_local_persistent_shell.py` | TERMINAL_LOCAL_PERSISTENT end to end on a real local bash: on (the default) carries exported env vars between commands, off starts every command from the login-time env. cwd carries in both modes (file tools rely on it)… |
| `test_local_setsid_descendant_sweep.py` | Regression tests for #85125 Phase 4b (terminal flavor of the #71148 class). |
| `test_local_shell_init.py` | Tests for terminal.shell_init_files / terminal.auto_source_bashrc. |
| `test_local_temp_dir.py` | Tests for ``LocalEnvironment.get_temp_dir`` temp-dir redirect. |
| `test_macos_protected_search.py` | macOS TCC-safe behavior for broad file searches. |
| `test_managed_browserbase_and_modal.py` | Tests: `_load_tool_module`, `_load_plugin_module`, `_reset_modules`, `_restore_tool_and_agent_modules`, `_enable_managed_nous_tools`, `_install_fake_tools_package` … |
| `test_managed_media_gateways.py` | Tests: `_load_tool_module`, `_restore_tool_and_agent_modules`, `_enable_managed_nous_tools`, `_install_fake_tools_package`, `_install_fake_fal_client`, `_install_fake_openai_module` … |
| `test_managed_modal_environment.py` | Tests: `_load_tool_module`, `_reset_modules`, `_restore_tool_and_agent_modules`, `_install_fake_tools_package`, `_FakeResponse`, `test_managed_modal_execute_polls_until_completed` … |
| `test_managed_tool_gateway.py` | Tests: `test_resolve_managed_tool_gateway_derives_vendor_origin_from_shared_domain`, `test_resolve_managed_tool_gateway_uses_vendor_specific_override`, `test_resolve_managed_tool_gateway_is_inactive_without_nous_token`,… |
| `test_managed_worker_tool_diagnostics.py` | A tool this session cannot reach must never be answered with "call it directly". |
| `test_mcp_app_gate.py` | Application requirements compose with live, recycled, and lazy MCP connections. |
| `test_mcp_auth_park_discovery_nudge.py` | An OAuth server parked on an auth failure must not be revived by discovery passes until a re-authorization rewrites its credentials: every nudge replayed the same rejected refresh token, once per agent build, until the… |
| `test_mcp_bridge_single_failure.py` | Regression test for #50394. |
| `test_mcp_cancelled_error_propagation.py` | Regression tests for ``MCPServerTask.run`` + ``asyncio.CancelledError``. |
| `test_mcp_capability_gating.py` | Tests for capability-gated MCP tool discovery and keepalive. |
| `test_mcp_cimd.py` | Tests for CIMD (Client ID Metadata Document) support in MCP OAuth. |
| `test_mcp_circuit_breaker.py` | Tests for MCP tool-handler circuit-breaker recovery. |
| `test_mcp_client_cert.py` | Tests for mTLS client certificate config on MCP HTTP/SSE transports. |
| `test_mcp_config_change_rebind.py` | A remote MCP server definition edited in config.yaml while the process runs must take effect on the next transport rebuild (#113907): ``run()`` used to keep its start-time dict forever, so a URL change (catalog migratio… |
| `test_mcp_config_whitespace_warning.py` | Tests for MCP config hidden-whitespace warnings. |
| `test_mcp_connect_secret_scope.py` | MCP connect resolves credentials under the connection owner's profile secret scope. |
| `test_mcp_dashboard_oauth.py` | Hosted-dashboard bridge for MCP OAuth browser callbacks. |
| `test_mcp_death_supervisor.py` | Contract tests for the shared parent-death supervisor for stdio MCP servers. |
| `test_mcp_device_flow.py` | RFC 8628 login invariants through the production CLI and local HTTP. |
| `test_mcp_dynamic_discovery.py` | Tests for MCP dynamic tool discovery (notifications/tools/list_changed). |
| `test_mcp_elicitation.py` | Tests for the MCP elicitation handler in tools.mcp_tool_sampling. |
| `test_mcp_empty_error_message.py` | Regression tests for MCP error messages when str(exc) is empty. |
| `test_mcp_enabled_reader.py` | Every reader of ``mcp_servers.<name>.enabled`` gives one answer per value. |
| `test_mcp_events.py` | MCP Events client (webhook delivery): opt-in utility tools, subscribe/unsubscribe against the dynamic webhook route store, and the refresh loop's re-subscription rules. |
| `test_mcp_failure_classification.py` | Tests for exception-group unwrapping and failure classification in ``tools/mcp_tool.py`` (#65673, #66092). |
| `test_mcp_google_offline_access.py` | Google-hosted MCP OAuth: offline access and the device-flow issuer mismatch (#117510). |
| `test_mcp_http_body_cap.py` | Wire-body cap for MCP HTTP/SSE transports. |
| `test_mcp_http_proxy.py` | Proxy support for MCP HTTP/SSE transports (#111794). |
| `test_mcp_identity_header.py` | Tests for the per-server MCP identity header (``identity_header``). |
| `test_mcp_image_content.py` | Regression tests for MCP ImageContent block handling. |
| `test_mcp_initial_connect_shutdown.py` | Regression tests for initial MCP failure ownership and teardown. |
| `test_mcp_invalid_url.py` | Tests for the MCP remote-URL validator. |
| `test_mcp_large_sse_event.py` | One MCP response delivered as a single SSE event larger than 1 MiB. |
| `test_mcp_lazy_start.py` | Behavior-contract tests for lazy MCP server startup (#56832). |
| `test_mcp_list_pagination.py` | Tests for MCP list_* pagination (nextCursor draining). |
| `test_mcp_liveness.py` | Tests: `_decl`, `test_parse_liveness_contract`, `test_invalid_registered_liveness_degrades_to_static`, `test_live_endpoint_reloads_file_and_registers_token_before_use`, `test_runtime_file_without_token_connects_without_… |
| `test_mcp_liveness_catalog.py` | Tests: `_schema`, `_decl`, `test_hidden_declared_server_appears_in_listing_and_empty_summary`, `test_hidden_undeclared_server_is_absent` |
| `test_mcp_loop_profile_override.py` | Regression tests for HERMES_HOME override propagation onto the MCP loop. |
| `test_mcp_multiplex_connection_keys.py` | Two multiplexed profiles that name the same MCP server with different credentials are two connections (#106005, #91654): the ledgers in ``tools.mcp_tool`` are keyed per owning profile scope, and an owner's scoped reload… |
| `test_mcp_node_abi.py` | A stdio MCP server whose native addon was built by another Node.js (#124264). |
| `test_mcp_npx_cached_bin.py` | ``npx -y <pkg>`` should spawn the cached binary, not a resident `npm exec`. |
| `test_mcp_oauth.py` | Tests for tools/mcp_oauth.py — OAuth 2.1 PKCE support for MCP servers. |
| `test_mcp_oauth_bidirectional.py` | Regression test for the ``HermesMCPOAuthProvider.async_auth_flow`` bidirectional generator bridge. |
| `test_mcp_oauth_callback_latch.py` | The loopback OAuth callback latches the first terminal result (#116278). |
| `test_mcp_oauth_cold_load_expiry.py` | Tests for cold-load token expiry tracking in MCP OAuth. |
| `test_mcp_oauth_discovery_requests.py` | SDK-built OAuth discovery/registration requests: default User-Agent, and discovery context on failure. |
| `test_mcp_oauth_integration.py` | End-to-end integration tests for the MCP OAuth consolidation. |
| `test_mcp_oauth_issuer_binding.py` | Refresh tokens are bound to the authorization-server issuer that granted them. |
| `test_mcp_oauth_issuer_origin.py` | A path-scoped authorization server whose RFC 8414 metadata names its origin (#116233). |
| `test_mcp_oauth_manager.py` | Tests for the MCP OAuth manager (tools/mcp_oauth_manager.py). |
| `test_mcp_oauth_metadata.py` | Tests for OAuth server metadata persistence across process restarts. |
| `test_mcp_oauth_missing_iss.py` | Regression for #111135: Figma advertises RFC 9207 ``iss`` support and then omits ``iss`` from the redirect, so the SDK rejected every valid authorization code. Only that issuer is tolerated. |
| `test_mcp_oauth_stdin_console.py` | ``_is_interactive()`` must not trust ``isatty()`` alone on Windows: the CRT reports a DEVNULL / detached stdin as a TTY, so the background gateway looked interactive and launched browser OAuth. |
| `test_mcp_oauth_user_agent.py` | Tests for the per-server ``oauth.user_agent`` on MCP OAuth token requests. |
| `test_mcp_park_log_dedupe.py` | Tests for parked-MCP-server log dedupe (#115713). |
| `test_mcp_parked_probe_no_browser.py` | A parked MCP server's timed self-probe is unattended: it must never start a browser OAuth flow. Left interactive, an expired refresh token opened a new authorize tab every ``_PARKED_RETRY_INTERVAL`` for the life of the… |
| `test_mcp_parked_probe_skips_disabled.py` | A parked server's timed self-probe must honour ``enabled: false`` / a deleted config entry: the probe rebuilds the transport from the config captured at start, so without the gate a disabled server re-runs its OAuth set… |
| `test_mcp_parked_self_probe.py` | Tests for the parked-server self-probe revival path (#57129). |
| `test_mcp_poll_loop_oom_integration.py` | End-to-end coverage for the MCP poll-loop OOM spin (#63892). |
| `test_mcp_preflight_content_type.py` | Tests for MCPServerTask._preflight_content_type fast-fail behaviour. |
| `test_mcp_probe.py` | Tests for probe_mcp_server_tools() in tools.mcp_tool. |
| `test_mcp_protocol_negotiation.py` | MCP 2026-07-28 protocol-era negotiation (_negotiate_session). |
| `test_mcp_rapid_drop_budget.py` | Tests for the MCP rapid-drop reconnect budget (#62212). |
| `test_mcp_reconcile_with_config.py` | Live MCP servers follow ``mcp_servers`` as it is on disk: an entry removed (or disabled) after boot is torn down instead of self-probing for the life of the process. |
| `test_mcp_reconnect_log_hygiene.py` | Tests for MCP reconnect log hygiene and backoff jitter (#65673, #66092). |
| `test_mcp_reconnect_retry_reset.py` | Tests for MCP reconnect retry counter reset (#57604). |
| `test_mcp_reconnect_signal.py` | Tests for the MCPServerTask reconnect signal. |
| `test_mcp_register_wakes_stale.py` | New sessions must wake parked/stale cached MCP servers immediately. |
| `test_mcp_resource_content.py` | Tests for MCP ResourceLink / EmbeddedResource / AudioContent handling. |
| `test_mcp_restart_on_new_inputs.py` | A plugin settings save reconnects only the MCP servers whose resolved launch inputs changed: a new ``${VAR}`` value the server's ``env`` passes through restarts it with that value; a save that changes nothing it launche… |
| `test_mcp_result_size_limit.py` | Regression tests for the MCP hard result cap (#56059). |
| `test_mcp_schema_cache.py` | Unit tests for the on-disk MCP schema cache (tools/mcp_schema_cache.py). |
| `test_mcp_schema_cache_ttl.py` | SEP-2549 schema-cache TTL expiry (tools/mcp_schema_cache.py). |
| `test_mcp_server_log_notifications.py` | Tests for MCP server log notification handling (port of anomalyco/opencode#34529). |
| `test_mcp_server_reconnecting_predicate.py` | ``mcp_server_reconnecting`` (cron preflight's "is this outage healing on its own?" question) must say True only for a transient park. A server parked on a PERMANENT error (revoked credentials, endpoint gone) fails its s… |
| `test_mcp_session_scope.py` | Real stdio registrations must not become sibling-session capabilities. |
| `test_mcp_shared_connection_resolved_identity.py` | A multiplexed profile never adopts another profile's live MCP connection when the inputs that connection was opened with resolve differently for it: external secret-source env on a stdio child, or ``identity_header.valu… |
| `test_mcp_sse_fallback.py` | Invariant tests: automatic Streamable HTTP -> SSE transport fallback (#53676, #104343). |
| `test_mcp_sse_transport.py` | Regression tests for SSE transport in ``MCPServerTask._run_http``. |
| `test_mcp_stability.py` | Tests for MCP stability fixes — event loop handler, PID tracking, shutdown robustness. |
| `test_mcp_startup_summary_names_failures.py` | The MCP startup summary names every failing server with its reason (#114746). |
| `test_mcp_stderr_lifecycle.py` | MCP shutdown releases only the selected profile's cached stderr handle. |
| `test_mcp_stdio_children_dead.py` | Regression tests for MCP stdio aggregate liveness (#94335 / #94637). |
| `test_mcp_stdio_dead_reconnect.py` | Regression test for #115483: dead stdio child past the proof deadline. |
| `test_mcp_stdio_encoding_handler.py` | Tests for MCP stdio encoding error handler fix (issue #46099). |
| `test_mcp_stdio_env_unset_ref.py` | Stdio MCP launch env: an env entry rendered from one unset ``${VAR}`` counts as absent. |
| `test_mcp_stdio_fastfail_reconnect.py` | Regression tests for dead stdio subprocess recovery (#95626 salvage). |
| `test_mcp_stdio_init_timeout.py` | Regression test for the stdio-MCP subprocess/FD leak (#59349). |
| `test_mcp_streamable_http_arity.py` | The streamable-HTTP transport must accept both SDK generations' arity. |
| `test_mcp_structured_content.py` | Tests for MCP tool structuredContent preservation. |
| `test_mcp_timeout_resolution.py` | Contract tests for MCP tool-timeout resolution (#85125 Phase 2g). |
| `test_mcp_tool.py` | Tests for the MCP (Model Context Protocol) client support. |
| `test_mcp_tool_401_handling.py` | Tests for MCP tool-handler auth-failure detection. |
| `test_mcp_tool_client_info.py` | The MCP handshake names hermes-agent and its release, not the SDK default ("mcp"/"0.1.0"). |
| `test_mcp_tool_costs.py` | Declared MCP tool costs and the per-chat spend limit (``tools.mcp_tool_costs``). |
| `test_mcp_tool_errors.py` | Invariants for ``tools/mcp_tool_errors._format_connect_error`` on malformed exception chains. |
| `test_mcp_tool_issue_948.py` | Tests: `test_resolve_stdio_command_keeps_the_child_path_order`, `test_resolve_stdio_command_skips_unknown_commands`, `test_resolve_stdio_command_absent_path_is_a_miss`, `test_resolve_stdio_command_empty_path_is_a_miss`,… |
| `test_mcp_tool_progress.py` | An MCP server's ``notifications/progress`` during ``tools/call`` reaches the agent's ``tool_progress_callback`` as throttled ``tool.progress`` events for that call id. Real stdio child, real config, real SDK progress to… |
| `test_mcp_tool_session_expired.py` | Tests for MCP tool-handler transport-session auto-reconnect. |
| `test_mcp_transport_group_reconnect.py` | Regression tests for issue #66092. |
| `test_mcp_trust_approval_scope.py` | MCP trust-gate approval scopes: what a prompt offers is what the answer does. |
| `test_mcp_trust_gating.py` | Tests for MCP tool trust-tier gating via readOnlyHint annotations. |
| `test_mcp_trust_yolo.py` | YOLO and ``approvals.mode: off`` against the MCP trust gate and the spend limit. |
| `test_mcp_utility_capability_gating.py` | Regression tests for capability-gated MCP utility schema registration. |
| `test_mcp_windows_orphan_fix.py` | Tests for the Windows MCP orphan fix (#61059). |
| `test_media_caption_split.py` | Guard test for the MEDIA:<path> caption chokepoint (_media_caption_split). |
| `test_memory_patch_action.py` | Regression for #124582: the memory tool had no find-and-splice edit, so a partial edit of one clause of a packed multi-fact entry could only be expressed as a whole-entry ``replace`` — silently discarding the sibling fa… |
| `test_memory_target_contract.py` | Memory calls must name one store before writing or staging a proposal. |
| `test_memory_tool.py` | Tests for tools/memory_tool.py — MemoryStore, security scanning, and tool dispatcher. |
| `test_memory_tool_import_fallback.py` | Regression tests for memory-tool import fallbacks. |
| `test_memory_tool_schema.py` | Schema-shape tests for the built-in memory tool. |
| `test_microsoft_graph_auth.py` | Tests for tools/microsoft_graph_auth.py. |
| `test_microsoft_graph_client.py` | Tests for tools/microsoft_graph_client.py. |
| `test_modal_bulk_upload.py` | Tests for Modal bulk upload via tar/base64 archive. |
| `test_modal_sandbox_fixes.py` | Tests for Modal sandbox infrastructure fixes (TBLite baseline). |
| `test_modal_snapshot_isolation.py` | Tests: `_load_module`, `_reset_modules`, `_restore_tool_modules`, `_install_modal_test_modules`, `test_modal_environment_migrates_legacy_snapshot_key_and_uses_snapshot_id`, `test_resolve_modal_image_uses_snapshot_ids_an… |
| `test_model_tools.py` | Tests for model_tools.py — function call dispatch, agent-loop interception, legacy toolsets. |
| `test_multiplex_tool_cache_scope.py` | Multiplexed gateway: module-level caches in tools/ and agent/ must not hand profile A's config/.env-derived value to profile B. Real temp homes, real config.yaml/.env, real modules; only HTTP transports are stubbed. |
| `test_multiplex_tool_credential_scope.py` | Multiplex invariant: tool-side profile credentials / targets never leak from the default profile. |
| `test_multiplex_tool_memo_scope.py` | Under ``gateway.multiplex_profiles`` one process serves every profile; each routed turn runs with a context-local HERMES_HOME override. Tool-side state resolved once at import, or cached in a single unkeyed slot, would… |
| `test_multiplex_turn_parity.py` | Multiplexed-gateway parity for what a TURN sees: a profile served by the default multiplexer (``_profile_runtime_scope``) must observe the same tool-side policy its standalone gateway (``HERMES_HOME=<profile>``) would —… |
| `test_notebook_recovery_path.py` | Recovery hints must name the user-visible notebook, not its byte-transport copy. |
| `test_notify_on_complete.py` | Tests for notify_on_complete background process feature. |
| `test_oneshot_completion_linger.py` | One-shot CLI exit linger for notify_on_complete background processes (#90879). |
| `test_open_preview_tool.py` | Tests for the GUI-surface ``open_preview`` tool. |
| `test_osv_check.py` | Tests for OSV malware check on MCP extension packages. |
| `test_parse_env_var.py` | Tests for _parse_env_var and _get_env_config env-var validation. |
| `test_patch_already_applied.py` | Tests for already-applied patch detection (success-shaped no-op). |
| `test_patch_multimatch_locations.py` | Tests for multi-match location listing in patch ambiguity errors. |
| `test_patch_parser.py` | Tests for the V4A patch format parser. |
| `test_patch_v4a_gate.py` | patch V4A provider gate (#95681). |
| `test_patch_ws_diagnosis.py` | Tests for whitespace-visualized mismatch diagnosis in patch no-match hints. |
| `test_permanent_allowlist_live_reload.py` | A hand edit to ``command_allowlist`` must reach a long-lived process's approval check. |
| `test_permanent_allowlist_reconcile.py` | `command_allowlist` is a file the operator edits; a save must not clobber it. |
| `test_persist_on_release.py` | Lifecycle kill sweeps must skip terminal(background=true, persist_on_release=true) jobs (#41225). |
| `test_pgid_starttime_drift.py` | PGID start-time guards tolerate same-host start-time drift (#117505; follow-up to #131910). |
| `test_plugin_guard.py` | Tests for tools/plugin_guard.py — plugin install security scanning. |
| `test_plugin_guard_block_reason.py` | Behavior contracts for plugin-guard dangerous-install diagnostics. |
| `test_plugin_skills.py` | Tests for namespaced plugin skill registration and resolution. |
| `test_pr_6656_regressions.py` | Regression tests for PR #6656 — skill uninstall + bundle hash + pairing lock. |
| `test_pre_transcription_hook.py` | Tests for the ``pre_transcription`` plugin hook and STT prompt threading (issue #64168) wired into ``tools.transcription_tools.transcribe_audio``. |
| `test_preview_scope_gate.py` | tool_call scope gate for session-gated GUI tools (#120413). |
| `test_process_checkpoint_readopt.py` | Checkpoint recovery must not invent an exit for a live child. |
| `test_process_checkpoint_worker_handoff.py` | processes.json keeps the worker handoffs its writer does not track (ahrazzle B2-04). |
| `test_process_heartbeat.py` | Heartbeat notifications for long background processes. |
| `test_process_registry.py` | Tests for tools/process_registry.py — ProcessRegistry query methods, pruning, checkpoint. |
| `test_process_registry_completion_races.py` | A process's completion is published once, by its owner, and only with its final output. |
| `test_process_registry_env_spawn_cwd.py` | Background launches on environment-backed backends run in the requested cwd. |
| `test_process_registry_import_fence.py` | Importing a tool module must never open the canonical store. |
| `test_process_registry_lazy_restore.py` | Importing the tool registry must not touch state.db; the durable completion replay runs when a consumer asks for it (#123265). |
| `test_process_registry_list_exit.py` | List refresh observes the child, not its descendants' capture-pipe lifetime. |
| `test_process_registry_owner_chain.py` | RED tests for #120546: background WSL work leaves ownerless PIDs. |
| `test_process_registry_pty_kill.py` | Killing a PTY background process must return while a descendant that escapes it holds the PTY. |
| `test_process_registry_submit.py` | submit_stdin presses Enter the way the child's input expects it: CR on a POSIX PTY, LF on a pipe. |
| `test_process_registry_windows_live.py` | LIVE Windows E2E for background-executor spawn parity (#70716 / PR salvage). |
| `test_process_registry_write_stdin_surrogates.py` | Sibling regression test for #79178: background-PTY stdin must round-trip surrogateescape content instead of crashing on the strict UTF-8 encode. |
| `test_process_schema_diet.py` | process schema diet contract (#95681). |
| `test_process_stdin_unavailable_error.py` | process_manage write/submit on a background process without stdin names the fix that works. |
| `test_process_wait_auto_notify.py` | Repeated process_manage wait/poll on a silent running process promotes it to notify_on_complete. |
| `test_process_wait_clarity.py` | Tests for process wait timeout-result clarity (not-an-error semantics). |
| `test_profile_gate_env_isolation.py` | A child spawned FOR another profile never inherits this process's authorization gates (#113270). |
| `test_profile_gate_env_shape.py` | A profile gate is a PLATFORM prefix plus a gate-shaped suffix; an operator's own variable that merely contains ``_ALLOWED_`` is script data and must survive the routed-child strip (#119539). |
| `test_project_tools.py` | Tests: `_use_projects_db`, `test_agent_session_project_create_keeps_profile_active_pointer_and_moves_session`, `test_legacy_project_create_sets_profile_active_pointer`, `test_legacy_project_switch_sets_profile_active_po… |
| `test_protected_instruction_cli_channel.py` | Protected-instruction approval fails closed at once, without asking anyone, where nobody can answer. |
| `test_pty_query_responder.py` | Tests for tools.pty_query_responder (port of openai/codex#41436). |
| `test_qqbot_send_message_media.py` | QQ Bot proactive MEDIA delivery via send_message / _send_to_platform (#37315). |
| `test_react_to_message_tool.py` | Ownership tests for desktop message reactions. |
| `test_reaction_session_identity.py` | Agent reactions address durable session ids, not routing keys (#139102). |
| `test_read_binary_type_disclosure.py` | Tests for magic-byte type disclosure in the binary-file refusal. |
| `test_read_extract.py` | Tests for structured-document extraction in the read_file tool. |
| `test_read_file_schema_gating.py` | read_file schema diet (#95681): static unconditional format list (anydoc bundled in core) + PDF-coverage teaching moved to the response-time warning. |
| `test_read_file_utf8_binary_regression.py` | End-to-end regression tests for the UTF-8 'flagged as binary' class. |
| `test_read_loop_detection.py` | Tests for the read-loop detection mechanism in file_tools. |
| `test_read_past_eof_note.py` | Tests for the past-EOF and empty-file notes in read_file. |
| `test_read_preview_tool.py` | Tests for the GUI-surface ``read_preview`` tool. |
| `test_read_shell_line_clamp.py` | Shell-pipeline per-line clamp in ShellFileOperations.read_file. |
| `test_read_special_file_guard.py` | Tests for the stat-based special-file guard in read_file_tool. |
| `test_read_unicode_filename_retry.py` | Tests for unicode-equivalent filename retry + near-miss suggestions. |
| `test_read_window_tool.py` | Tests for the GUI-surface ``read_window_below`` tool. |
| `test_refresh_agent_mcp_tools.py` | Tests for the shared MCP agent-tool refresh helper and discovery-wait bound. |
| `test_registry.py` | Tests for the central tool registry. |
| `test_remote_binary_write_guard.py` | Binary-document overwrite guard must decide WHERE THE WRITE WILL EXECUTE. |
| `test_removed_backend_migration.py` | Removed-backend migration warnings (registry added in #100540). |
| `test_request_tool_approval.py` | Tests for tools.approval.request_tool_approval — the plugin pre_tool_call ``{"action": "approve"}`` escalation into the human-approval gate. |
| `test_resolve_path.py` | Tests for _resolve_path_for_task() — TERMINAL_CWD-aware path resolution in file_tools_paths. |
| `test_restored_delegation_ownership.py` | Regression coverage for #64484 — durable-restored delegation completions must never be adopted by a session that cannot positively prove ownership. |
| `test_rollback_all_directories.py` | Regression tests for the /rollback all-directories fallback (#10505). |
| `test_safe_getcwd_permission_error.py` | Regression tests for _safe_getcwd() PermissionError handling (macOS TCC). |
| `test_safe_worker_mcp.py` | Fresh-interpreter proof that a safe worker never spawns MCP servers; config-only keeps them. |
| `test_safe_worker_tools.py` | Fresh-interpreter proof of the safe worker's reviewed tool import closure. |
| `test_sandbox_failure_hints.py` | Tests for execute_code sandbox failure hints. |
| `test_sandbox_port_forward.py` | The sandbox port forward (tools/environments/streams.py) reports connections that never reached their target: the sandbox browser's liveness is re-checked only after one (tools/browser_session_sandbox.py). |
| `test_schema_boolean_required.py` | Tests: `test_boolean_required_preserves_parent_intent`, `test_boolean_required_does_not_modify_literal_data` |
| `test_schema_sanitizer.py` | Tests for tools/schema_sanitizer.py. |
| `test_search_auto_multiline.py` | Tests for search_files auto-multiline routing on \n patterns. |
| `test_search_budget_truncation.py` | Tests: `ops`, `timeout_output`, `path_exists_or`, `assert_timed_out`, `test_timeout_helper_strips_only_trailing_marker`, `test_rg_timeout_returns_partial_results_without_marker` … |
| `test_search_error_guard.py` | Regression tests for the rg/grep error guard in content search. |
| `test_search_files_cpu_windows.py` | Concurrency admission tests for expensive filename walks. |
| `test_search_files_engine_selection.py` | Behavior tests for file-search ordering and ripgrep selection. |
| `test_search_files_schema_platform.py` | search_files advertises macOS protected-folder pruning only on the host that prunes. |
| `test_search_giant_line_containment.py` | Giant single-line file containment in content search (cline/cline#13525 port). |
| `test_search_grep_pruned_permissions.py` | Live regression tests: the pruned grep fallback reports unreadable subtrees. |
| `test_search_hidden_dirs.py` | Tests that search_files excludes hidden directories by default. |
| `test_search_multi_root_warnings.py` | Live regression: a multi-root search keeps every root's partial-result warning. |
| `test_search_native_rg.py` | Local POSIX content/file search runs rg as a direct argv subprocess. |
| `test_search_permission_degradation.py` | Regression tests: search_files degrades on unreadable (EACCES) paths. |
| `test_search_unreadable_bound.py` | Unreadable directories under a search root never cost search_files its results. |
| `test_search_zero_match_and_multipath.py` | Tests for search_files zero-match probes and multi-path recovery. |
| `test_self_repo_guard.py` | Tests for tools/self_repo_guard.py — the running-source-checkout git guard. |
| `test_send_message_cross_loop.py` | Regression tests for the cross-event-loop deadlock fix in send_message. |
| `test_send_message_missing_platforms.py` | Tests for _send_mattermost, _send_matrix, _send_dingtalk. |
| `test_send_message_multiplex_profile_adapter.py` | send_message must deliver through the ACTIVE PROFILE's gateway adapter under multiplex. |
| `test_send_message_plugin_extensibility.py` | Cross-surface regressions for standalone platform send extensibility (#64900). |
| `test_send_message_react.py` | Tests for send_message action='react'/'unreact' dispatch. |
| `test_send_message_relay_target_authz.py` | P5(a): `send_message` cannot silently name an arbitrary relay target. |
| `test_send_message_slack.py` | Slack-specific send_message delivery regressions. |
| `test_send_message_surrogate_sanitization.py` | Outbound send bodies must not carry lone surrogate code points (#113799). |
| `test_send_message_target_parse.py` | Parser-only and lightweight routing tests for send_message targets. |
| `test_send_message_telegram_proxy.py` | Regression tests for the standalone Telegram send path's proxy support. |
| `test_send_message_tool.py` | Tests for tools/send_message_tool.py. |
| `test_session_cwd_store.py` | Session-cwd record store (cwd rearchitecture, step 1: dual-write). |
| `test_session_search.py` | Tests for the single-shape session_search tool. |
| `test_session_search_readonly.py` | Search never becomes another session-database initializer. |
| `test_session_search_worker_store.py` | Recall in a gateway-managed worker (#141705). |
| `test_session_tool_env.py` | T3: a local session's tool subprocesses (terminal, background processes, execute_code) start with its client's allowlisted toolchain environment (PATH, an activated venv, nvm/pyenv/conda), not the gateway daemon's. Appl… |
| `test_set_theme_tool.py` | ``set_theme``: the model hears what the desktop applied, never a success it assumed. |
| `test_setup_beat_plugin_skills.py` | The build beat names a plugin's skill by the name it registered under. |
| `test_setup_beat_tool.py` | ``setup_beat`` through the agent's inline executor, with a real session store and a fake card answer standing in for the desktop. |
| `test_shared_container_task_id.py` | Regression tests for the shared-container task_id mapping. |
| `test_shell_arg_transport.py` | Non-path values survive local argv and serialized POSIX-script transport. |
| `test_shell_bypass_denylist.py` | Shell-obfuscation bypass coverage for the dangerous-command denylist. |
| `test_signal_media.py` | Tests for Signal media delivery in send_message_tool.py. |
| `test_single_query_approval_mode.py` | Tests for approvals.single_query_mode — configurable approval behavior for single-query (-q) sessions. |
| `test_skill_bundle_provenance.py` | Multi-file third-party skill bundles and scanner provenance (#60598). |
| `test_skill_create_dir.py` | Tests for ``skills.create_dir`` — config-driven skill creation directory. |
| `test_skill_env_passthrough.py` | Test that skill_view registers required env vars in the passthrough registry. |
| `test_skill_improvements.py` | Tests for skill fuzzy patching via tools.fuzzy_match. |
| `test_skill_ledger.py` | Tests for tools/skill_ledger.py — per-mutation audit ledger + rollback. |
| `test_skill_ledger_delta.py` | Ledger entries carry deltas, not whole-package manifests. |
| `test_skill_linter.py` | Tests for tools/skill_linter.py — the advisory SKILL.md convention linter. |
| `test_skill_manage_batch.py` | skill_manage operations[] batch (#95681 arc, maintainer-approved). |
| `test_skill_manage_schema_diet.py` | skill_manage schema diet contract (#95681, second pass). |
| `test_skill_manager_tool.py` | Tests for tools/skill_manager_tool.py — skill creation, editing, and deletion. |
| `test_skill_pending_diff_batch.py` | Batch pending diff for /skills diff <id> (#123315). |
| `test_skill_provenance.py` | Tests for tools/skill_provenance.py — write-origin ContextVar. |
| `test_skill_provenance_external.py` | #108032: external-dir skills get an 'external' provenance tier, not 'agent'. |
| `test_skill_size_limits.py` | Tests for skill content size limits. |
| `test_skill_usage.py` | Tests for tools/skill_usage.py — sidecar telemetry + provenance filtering. |
| `test_skill_view_dedup.py` | Tests for skill_view repeat-view dedup (unchanged-skill stub). |
| `test_skill_view_traversal.py` | Tests for path traversal prevention in skill_view. |
| `test_skillevaluator_scan.py` | Tests for the advisory SkillEvaluator Tier 1 install scan. |
| `test_skills_ast_audit.py` | Tests for tools.skills_ast_audit — opt-in AST diagnostic scanner. |
| `test_skills_guard.py` | Tests for tools/skills_guard.py - security scanner for skills. |
| `test_skills_guard_agent_config.py` | Regression tests for skills-guard agent-config persistence patterns (#92021). |
| `test_skills_hub.py` | Tests for tools/skills_hub.py — source adapters, lock file, taps, dedup logic. |
| `test_skills_hub_browse_sh.py` | !/usr/bin/env python3 |
| `test_skills_hub_clawhub.py` | !/usr/bin/env python3 |
| `test_skills_hub_generic_dir.py` | Skills hub: a skills.sh skill kept in a generic dir (``skills/SKILL.md``) resolves and installs under its slug. |
| `test_skills_hub_github_fetch.py` | GitHubSource file downloads: which host serves a skill's files. |
| `test_skills_hub_lock_file.py` | skills/.hub/lock.json and taps.json survive concurrent writers from different processes. |
| `test_skills_list_modified_diff.py` | Tests for discovering and diffing user-modified bundled skills. |
| `test_skills_runtime_cache.py` | Runtime caches must not take ownership of updater-managed skill packages. |
| `test_skills_sync.py` | Tests for tools/skills_sync.py — manifest-based skill seeding and updating. |
| `test_skills_tool.py` | Tests for tools/skills_tool.py — skill discovery and viewing. |
| `test_skills_tool_discovery_cache.py` | Regression tests for the find_all_skills discovery cache (#58985 salvage). |
| `test_skills_tool_profile_scope.py` | Regression tests for profile-scoped skills_tool path resolution. |
| `test_slack_send_message_media.py` | Slack media delivery for send_message. |
| `test_slash_confirm.py` | Tests for tools/slash_confirm.py — the generic slash-command confirmation primitive. |
| `test_smart_approval_injection.py` | Regression tests for prompt injection hardening in smart approvals. |
| `test_smart_approval_policy.py` | Tests for the operator-customizable smart-approval policy. |
| `test_smart_approval_reasoning.py` | The smart-approval guardian asks for its verdict with thinking off, unless the operator chose. |
| `test_snapshot_multiline_session_env_injection.py` | Newline in bridged session env must not become shell code via the snapshot. |
| `test_snapshot_session_id_leak.py` | Cross-session HERMES_SESSION_ID leak via the shared bash snapshot. |
| `test_spawn_site_child_env.py` | Real children started by the production spawn sites observe the secret scrub. |
| `test_spill_safety.py` | Symlink-refusal and permission tests for tools.spill_safety. |
| `test_ssh_bulk_upload.py` | Tests for SSH bulk upload via tar pipe. |
| `test_ssh_environment.py` | Tests for the SSH remote execution environment backend. |
| `test_ssh_remote_cwd.py` | SSH file paths and cwds live in the remote namespace, never the Hermes host's. |
| `test_ssh_session_cwd.py` | Late session cwd updates must stay in the SSH peer's namespace. |
| `test_stage2_hook_api_server_keygen.py` | Regression tests for the stage2 API_SERVER_KEY bootstrap (OOF-285). |
| `test_stage2_hook_nous_routing_env.py` | Regression tests for the stage2 Nous routing-override sync. |
| `test_stage2_hook_remote_config_skip.py` | stage2 skips ``docker_config_migrate.py`` in remote config mode (config-config P4, D12): the agent migrates the fetched document in memory, so a leftover local config.yaml must not be migrated. stage2 decides with the a… |
| `test_stage2_hook_seed_one_symlinks.py` | Regression tests for symlink-safe Docker stage2 first-boot seeds. |
| `test_stage2_hook_symlink_chown.py` | Regression tests for symlink-safe Docker stage2 ownership repair. |
| `test_startup_latency_regressions.py` | Startup-latency regressions: probe-mode aux clients, lazy MCP SDK, non-blocking banner update check. |
| `test_strict_provider_selection.py` | Strict tool-provider selection: the `hermes tools` choice always wins. |
| `test_stt_cloud_trim.py` | Tests for the cloud STT pre-upload silence trim. |
| `test_stt_idle_unload.py` | Tests for the local whisper model idle-unload mechanism. |
| `test_stt_language_resolution.py` | Tests for the unified STT language resolution (_resolve_stt_language). |
| `test_stt_resolution_passive.py` | STT provider RESOLUTION never installs; transcription still does. |
| `test_stt_silence_hallucinations.py` | Tests for the local faster-whisper silence-hallucination hardening. |
| `test_subagent_process_handoff.py` | Subagent → parent background-process handoff (process_manage action='handoff'). |
| `test_subagent_steer.py` | steer_subagent — redirecting a live delegated child without stopping it. |
| `test_subagent_sudo_prompt.py` | delegate_task children must never trigger the interactive sudo prompt. |
| `test_subagent_worktree.py` | Tests for opt-in subagent worktree isolation (tools/subagent_worktree.py). |
| `test_subprocess_home_isolation.py` | Tests for subprocess HOME handling in profile mode. |
| `test_subprocess_stdin_guard.py` | Verify that TUI-context subprocess calls specify stdin=. |
| `test_subprocess_utf8_encoding.py` | Regression test for #53428 (fix PR #55339): ``subprocess.run(text=True)`` decoding of secret-manager CLI output must never crash on undecodable bytes. |
| `test_sync_back_backends.py` | Tests for backend-specific bulk download implementations and cleanup() wiring. |
| `test_telegram_send_message_caption.py` | Standalone Telegram MEDIA:<path> caption delivery. |
| `test_telegram_send_message_video_metadata.py` | The standalone ``hermes send`` Telegram path must carry video metadata too. |
| `test_terminal_backend_unavailable_reason.py` | Invariant: when a terminal backend's requirements check fails, the human reason is captured so the CLI startup notice / doctor can tell the user WHY the terminal tool is missing (tools-runtime-01). |
| `test_terminal_background_spawn_failure.py` | A background launch that never started must be reported as an error, not a session. |
| `test_terminal_bounded_execute.py` | Foreground terminal execute must return when the inner wait loop wedges. |
| `test_terminal_compound_background.py` | Regression tests for _rewrite_compound_background. |
| `test_terminal_config_env_sync.py` | Regression tests for terminal config -> env-var bridging. |
| `test_terminal_cwd_echo.py` | Tests for the terminal result cwd echo (feat/terminal-cwd-echo). |
| `test_terminal_degraded_mode.py` | Remote terminal backend graceful degradation (terminal.degraded_mode). |
| `test_terminal_env_bridge.py` | Behavioral regressions for the terminal config → env bridge. |
| `test_terminal_environment_recreated_notice.py` | The model must be told when the backend replaced its container/sandbox mid-command (ported from lobehub/lobehub#19329): silent recovery leaves the agent assuming background processes and unsynced files survived. |
| `test_terminal_error_redaction.py` | Terminal tool result errors must not leak credential-shaped strings. |
| `test_terminal_exit_semantics.py` | Tests for terminal command exit code semantic interpretation. |
| `test_terminal_foreground_timeout_cap.py` | Tests for foreground timeout cap in terminal_tool. |
| `test_terminal_heredoc_background_guard.py` | Regression tests for conservative heredoc-aware background-'&' detection. |
| `test_terminal_hints.py` | Tests for tools/terminal_hints.py — output-pattern failure hints. |
| `test_terminal_inflight_reap_guard.py` | The idle reaper must not tear down an environment while a foreground call is running in it. |
| `test_terminal_macos_open.py` | Regression tests for the macOS `open` frontmost raise-ladder. |
| `test_terminal_none_command_guard.py` | Regression tests for invalid/None terminal command handling. |
| `test_terminal_output_transform_hook.py` | Tests: `_make_env_config`, `_run_terminal`, `test_terminal_output_unchanged_when_transform_hook_not_registered`, `test_terminal_output_transform_still_runs_strip_and_redact`, `test_large_process_output_is_bounded_before… |
| `test_terminal_pipeline_status.py` | The bash wrapper reports each pipeline segment's own exit status. |
| `test_terminal_plugin_cwd_and_streams.py` | Plugin terminal backends declare where commands start (``default_cwd``) and whether Bot Desktop, computer_use and the browser can follow the terminal into them (``supports_streams`` plus the environment's ``exec_prefix`… |
| `test_terminal_plugin_host_isolation.py` | A user terminal backend under ``plugins.isolation: host``: the plugin's environment object cannot cross the host boundary (its methods would run outside the Hermes process's interrupt, activity and terminal-scope state)… |
| `test_terminal_plugin_image_override.py` | A plugin terminal backend gets its per-task image override (``<backend>_image``, what batch runs register for the active backend), and that override marks the task as an isolated rollout like a built-in backend's image… |
| `test_terminal_pre_guard_deadline.py` | Terminal pre-execution guards share the command's wall-clock deadline (#111922). |
| `test_terminal_requirements.py` | Tests: `_clear_terminal_env`, `test_local_terminal_requirements`, `test_unknown_terminal_env_logs_error_and_returns_false`, `test_modal_backend_managed_mode_without_feature_flag_logs_clear_error`, `test_vercel_backend_w… |
| `test_terminal_sandbox_builder_dispatch.py` | Regression coverage for sandbox backend builder dispatch (#112715). |
| `test_terminal_scope_multiplex.py` | Per-turn terminal scope isolation under profile multiplexing (#68559 class). |
| `test_terminal_self_repo_guard.py` | terminal_tool wiring tests for the self-repo git mutation guard. |
| `test_terminal_signal_exit.py` | Tests for signal-termination exit code interpretation. |
| `test_terminal_task_cwd.py` | Regression tests for task/session cwd propagation in terminal_tool. |
| `test_terminal_timeout_output.py` | Verify that terminal command timeouts preserve partial output. |
| `test_terminal_tool.py` | Regression tests for sudo detection and sudo password handling. |
| `test_terminal_tool_exception_redaction.py` | Terminal-tool exception paths must redact secrets before returning to the model. |
| `test_terminal_tool_pty_fallback.py` | Tests: `_base_config`, `test_command_requires_pipe_stdin_detects_gh_with_token`, `test_terminal_background_keeps_pty_for_regular_interactive_commands` |
| `test_terminal_tool_requirements.py` | Tests for terminal/file tool availability in local dev environments. |
| `test_terminal_trailing_amp_auto_background.py` | A foreground command whose ONLY backgrounding is a trailing `&` runs as terminal(background=true). |
| `test_terminal_truncation_spill.py` | Tests for terminal truncation spill + metadata (deferred retrieval). |
| `test_terminal_watcher_arming.py` | Gateway completion watchers are armed at launch, not only after the turn ends. |
| `test_terminal_yield_to_background.py` | A user message sent while a foreground terminal command runs must not wait for the command. |
| `test_termux_api_detection.py` | Regression tests for issue #31015 — Termux:API app detection. |
| `test_threaded_process_handle.py` | Tests for _ThreadedProcessHandle — the adapter for SDK backends. |
| `test_threat_patterns.py` | Tests for tools/threat_patterns.py — shared threat-pattern library. |
| `test_timeout_transport_drain.py` | #94248 (native half): delegation timeout must drain transports FD-safely. |
| `test_tip_tool.py` | Tests for the GUI-surface ``tip`` tool. |
| `test_todo_nested.py` | Tests for nested subtasks in the todo tool (parent field). |
| `test_todo_tool.py` | Tests for the todo tool module. |
| `test_todo_tool_type_coercion.py` | Tests for defensive type coercion in todo_tool (issue #14185). |
| `test_tool_backend_helpers.py` | Unit tests for tools/tool_backend_helpers.py. |
| `test_tool_output_limits.py` | Tests for tools.tool_output_limits. |
| `test_tool_output_truncate.py` | Invariant: terminal, execute_code, MCP and the bounded output collector truncate through one head/tail algorithm — 40% head / 60% tail, exactly one notice, kept text equal to the budget. |
| `test_tool_result_storage.py` | Tests for tools/tool_result_storage.py -- 3-layer tool result persistence. |
| `test_tool_search.py` | Tests for tools/tool_search.py — progressive tool disclosure. |
| `test_tool_search_context_provider.py` | Regression coverage for provider-aware context sizing in the tool-search gate. |
| `test_tool_search_listing_layout.py` | Layout of the deferred-tool catalog embedded in the tool_search description. |
| `test_tool_search_multiquery.py` | Multi-query ``tool_search``, batched ``tool_describe``, and stemming. |
| `test_toolset_distributions.py` | Tests for toolset_distributions.py — distribution CRUD, sampling, validation. |
| `test_toolsets.py` | Tests for toolsets.py — toolset resolution, validation, and composition. |
| `test_tour_tool.py` | Tests for the GUI-surface ``tour`` tool. |
| `test_transcription.py` | Tests for transcription_tools.py — local (faster-whisper) and OpenAI providers. |
| `test_transcription_chunking.py` | Cloud STT inputs over the provider's upload cap are fitted, not rejected (real ffmpeg, real files). |
| `test_transcription_command_providers.py` | Tests for the STT command-provider registry (``stt.providers.<name>``). |
| `test_transcription_deepinfra.py` | Tests for the DeepInfra STT provider. |
| `test_transcription_dotenv_fallback.py` | Regression tests for the transcription_tools variant of #17140. |
| `test_transcription_plugin_dispatch.py` | Tests for STT plugin dispatch in tools/transcription_tools.py. |
| `test_transcription_streaming.py` | Live STT sessions: wire behaviour over a real socket, and the recorder hand-off. |
| `test_transcription_tools.py` | Tests for tools.transcription_tools — three-provider STT pipeline. |
| `test_transcription_whisper_cpp.py` | The managed command remains passive until transcription and caches verified models. |
| `test_translate_execute_context.py` | Translation threats must not discard unrelated role instructions. |
| `test_truncation_footer_sandbox_paths.py` | Truncation footers tell the AGENT where the full text lives, and the agent's read_file runs inside the active terminal backend: under docker the mounted cache is at /root/.hermes, so a host path in the footer is unreada… |
| `test_tts_command_providers.py` | Tests for custom command-type TTS providers. |
| `test_tts_container_repair.py` | Tests for the class-level TTS .ogg container repair. |
| `test_tts_deepinfra.py` | Tests for the DeepInfra TTS provider. |
| `test_tts_dotenv_fallback.py` | Regression tests for #17140. |
| `test_tts_failure_preserves_existing.py` | A failed text_to_speech call must never destroy a file that already lived at output_path. |
| `test_tts_gemini.py` | Tests for the Google Gemini TTS provider in tools/tts_tool.py. |
| `test_tts_identifier_speech.py` | Identifier-to-speech normalization (#119207). |
| `test_tts_importers.py` | SDK import fallback uses the real import system and exact PM feature mapping. |
| `test_tts_instructions.py` | Tests for the OpenAI TTS `instructions` field passthrough. |
| `test_tts_kittentts.py` | Tests for the KittenTTS local provider in tools/tts_tool.py. |
| `test_tts_lifecycle_leases.py` | TTS engine lifecycle driven by speech-output toggles (issue #100881). |
| `test_tts_long_form_chunking.py` | Tests for the long-form TTS chunking and delivery packing pipeline. |
| `test_tts_macos_output.py` | macOS output policy for streaming TTS. |
| `test_tts_max_text_length.py` | Tests for per-provider TTS input-character limits. |
| `test_tts_minimax_region.py` | MiniMax TTS region, endpoint, and credential selection tests. |
| `test_tts_mistral.py` | Tests for the Mistral (Voxtral) TTS provider in tools/tts_tool.py. |
| `test_tts_model_cache_lru.py` | LRU bound on the Piper/KittenTTS model caches. |
| `test_tts_openai_config.py` | tts.openai.api_key / base_url from config.yaml drive the OpenAI audio client. |
| `test_tts_opus_routing.py` | Tests: `_reset_session_context`, `_clean_session_platform`, `_write_edge_output`, `test_edge_cli_preserves_native_mp3`, `test_edge_telegram_converts_to_opus_voice`, `test_edge_matrix_converts_to_opus_voice` |
| `test_tts_output_dir_profile_scope.py` | Regression tests for profile-scoped TTS default output dir (#98749). |
| `test_tts_output_timestamp.py` | Regression test for salvaged PR #43911 — microsecond TTS output timestamps. |
| `test_tts_path_traversal.py` | Regression: text_to_speech_tool output_path must reject '..' traversal. |
| `test_tts_piper.py` | Tests for the native Piper TTS provider. |
| `test_tts_plugin_dispatch.py` | Tests for TTS plugin dispatch in tools/tts_tool.py (issue #30398). |
| `test_tts_prepare_spoken.py` | Unit tests for the shared TTS text cleaner (tools/tts_text_normalize). |
| `test_tts_provider_authority.py` | Tests for config-authoritative TTS provider selection (#90109). |
| `test_tts_pythonpath_fallback.py` | Regression tests for #53259. |
| `test_tts_requirements_passive.py` | ``check_tts_requirements`` is the ``text_to_speech`` tool's ``check_fn``: a PASSIVE probe. |
| `test_tts_response_body_cap.py` | Regression tests for bounded upstream TTS response reads. |
| `test_tts_speed.py` | Tests for TTS speed configuration across providers. |
| `test_tts_streaming.py` | Tests for the provider-agnostic streaming TTS backend (tools.tts_streaming) and its dispatch through tools.tts_tool_speaker.stream_tts_to_speaker. |
| `test_tts_text_normalize.py` | Tests: `_DummyAdapter`, `test_prepare_spoken_text_expands_celsius_and_weather_units`, `test_prepare_spoken_text_polish_edge_cases`, `test_prepare_spoken_text_strips_media_file_links`, `test_prepare_spoken_text_keeps_sen… |
| `test_tts_voice_selection.py` | Model-selected ElevenLabs voices: ``text_to_speech`` gains ``voice_id`` and ``find_voices`` (a paginated voice search) only while ElevenLabs is the configured provider. |
| `test_tts_xai_speech_tags.py` | Tests for xAI TTS speech-tag handling. |
| `test_unicode_tag_strip.py` | Tests for Unicode TAG character stripping (U+E0000–U+E007F). |
| `test_url_safety.py` | Tests for SSRF protection in url_safety module. |
| `test_url_safety_authority.py` | URLs whose authority urllib.parse and WHATWG clients (browsers, Node) read differently. |
| `test_url_safety_authority_floor.py` | What the metadata floor refuses, and host forms WHATWG clients normalise away. |
| `test_utf16_read.py` | Tests for UTF-16 text file reading (transcode to UTF-8). |
| `test_vercel_sandbox_environment.py` | Unit tests for the Vercel Sandbox terminal backend. |
| `test_vercel_sandbox_transient_errors.py` | Vercel sandbox retries treat transport failures from the SDK's HTTP stack as transient. |
| `test_video_analyze.py` | Tests for video_analyze tool in tools/vision_tools.py. |
| `test_video_generate_schema.py` | video_generate dynamic schema — capability-gated params (#95681 diet). |
| `test_video_generation_dispatch.py` | Tests for the unified ``video_generate`` tool dispatch surface. |
| `test_video_generation_dynamic_schema.py` | Tests for the dynamic schema builder. |
| `test_video_generation_tool_surface_matrix.py` | Tool-surface routing matrix: every (provider, model, modality) combo. |
| `test_vision_history_budget.py` | Invariants for the native-embed history budgets (#112095). |
| `test_vision_native_fast_path.py` | Tests for the native-vision fast path inside vision_analyze. |
| `test_vision_region.py` | Tests for the optional region crop parameter on vision_analyze. |
| `test_vision_scale_disclosure.py` | Downscale coordinate-scale disclosure tests. |
| `test_vision_tools.py` | Tests for tools/vision_tools.py — URL validation, type hints, error logging. |
| `test_voice_cli_integration.py` | Tests for CLI voice mode integration -- markdown stripping, voice state management, TTS/STT wiring, barge-in and the full-duplex listener. |
| `test_voice_client_config.py` | E2E tests for tools.voice_client_config — the /api/audio/voice-config resolver. |
| `test_voice_credential_pool_resolution.py` | Tests for ``resolve_provider_secret`` — the single owner of STT/TTS provider key resolution (#68003). |
| `test_voice_max_recording_seconds.py` | Regression test: voice.max_recording_seconds is actually enforced. |
| `test_voice_mode.py` | Tests for tools.voice_mode -- all mocked, no real microphone or API calls. |
| `test_voice_mode_playback_env_scrub.py` | Voice-mode system playback must scrub credential env (sibling of #70342). |
| `test_voice_silence_threshold_stop.py` | Bug-fix regression tests for #84046: ``AudioRecorder.stop()`` must apply the CONFIGURED silence threshold (``self._silence_threshold``, wired from ``voice.silence_threshold`` by the CLI before each recording), not the h… |
| `test_voice_stop_phrase.py` | Tests for the voice-chat stop phrase (say "stop" and nothing else to end). |
| `test_voice_thinking_sound.py` | Tests for the ambient voice-chat "thinking" sound (tools/voice_mode.py). |
| `test_voice_tts_echo_guard.py` | Tests for the playback-phase TTS-echo guard (#75780). |
| `test_voice_wsl_pipewire.py` | Regression: WSL voice detection must honor PIPEWIRE_REMOTE, not only PULSE_SERVER. |
| `test_wake_word.py` | Tests for tools.wake_word — the "Hey Hermes" hotword detector. |
| `test_wake_word_stream_recovery.py` | Regression for #118001: a read error must not permanently disarm wake detection. |
| `test_watch_patterns.py` | Tests for watch_patterns background process monitoring feature. |
| `test_web_backend_capability_isolation.py` | A per-capability web backend key must not reroute the other capability. |
| `test_web_extract_cache_final_url.py` | A web_extract cache hit re-runs the website policy / SSRF gates on the URL its content came from. |
| `test_web_extract_redirect_gate.py` | web_extract re-gates every page a provider reports under a URL it was not asked for. |
| `test_web_extract_robustness.py` | Tests for web_extract truncate-store robustness (findings from #54843 review). |
| `test_web_extract_timeout.py` | web_extract provider dispatch must be wall-clock bounded (#57155, salvage #57180). |
| `test_web_free_fast_search.py` | Free managed Perplexity fast search for any Nous identity: anonymous guest, or signed in with no usable credits and no tool pool. The gateway serves ``POST /search`` + ``search_type: "fast"`` without funding checks, so… |
| `test_web_keyless_fallback.py` | Keyless free-tier web search/extract fallback (Parallel + Exa MCP). |
| `test_web_keyless_rescue.py` | One-shot keyless rescue: keyed/configured backend fails → THIS call rides the keyless ring; the NEXT call attempts the chosen backend again. |
| `test_web_managed_routing.py` | Real config, dispatch and local HTTP must preserve web billing boundaries. |
| `test_web_picker_active_rows.py` | Picker row highlighting for per-capability web backends. |
| `test_web_providers.py` | Tests for the web tools provider architecture. |
| `test_web_providers_brave_free.py` | Tests for the Brave Search (free tier) web search provider. |
| `test_web_providers_ddgs.py` | Tests for the DuckDuckGo (ddgs) web search provider. |
| `test_web_providers_searxng.py` | Tests for the SearXNG web search provider. |
| `test_web_providers_xai.py` | Tests for the xAI Web Search provider (plugins/web/xai/). |
| `test_web_result_cache.py` | Tests for tools/web_result_cache.py — TTL memo for web_search and the disk-backed extract cache, plus their wiring into web_tools. |
| `test_web_tools_config.py` | Tests for web backend client configuration and singleton behavior. |
| `test_web_tools_dict_urls.py` | Regression tests for model-forwarded web-search result objects. |
| `test_web_tools_perplexity.py` | Perplexity web backend — search + snippets dispatch through the real tools. |
| `test_web_tools_tavily.py` | Tests for Tavily web backend integration. |
| `test_web_tools_truncate.py` | Unit tests for the truncate-and-store web_extract path (no LLM). |
| `test_website_policy_cache_scope.py` | Regression tests for website-policy cache scope and TTL. |
| `test_whatsapp_send_message_media.py` | WhatsApp media delivery for send_message (#19105). |
| `test_windows_agent_loop_papercuts.py` | Windows agent-loop correctness regressions. |
| `test_windows_native_support.py` | Behavioral tests for Windows-specific compatibility fixes. |
| `test_working_diff.py` | Tests for tools.working_diff.collect_working_diff — the git collection layer shared by the CLI and gateway ``/diff`` command. |
| `test_write_approval.py` | Tests for the memory/skill write-approval gate (tools/write_approval.py) and the shared slash-command handlers (hermes_cli/write_approval_commands.py). |
| `test_write_deny.py` | Tests for _is_write_denied() — verifies deny list blocks sensitive paths on all platforms. |
| `test_write_file_rewrite_hint.py` | write_file tells the caller when it just re-sent a large file that was already on disk. |
| `test_write_file_syntax_gate.py` | Tests for the fail-closed pre-write syntax gate on write_file. |
| `test_write_verification.py` | Tests for write_file post-write content verification (verified flag). |
| `test_x_search_tool.py` | Tests for the X (Twitter) Search tool backed by xAI Responses API. |
| `test_xai_http_credentials.py` | Tests: `_set_xai_oauth_unavailable`, `test_xai_credentials_fail_closed_without_profile_scope`, `test_xai_credentials_do_not_fall_back_to_environ_when_scope_has_no_key`, `_install_fake_oauth_pool`, `test_prefer_api_key_w… |
| `test_xai_http_storage.py` | Tests for xAI Imagine storage helper behavior. |
| `test_xlsx_phonetic_text.py` | Phonetic guides (XLSX ``rPh``, DOCX ``w:rt`` ruby) annotate base text; they are not the value. |
| `test_yolo_mode.py` | Tests for --yolo (HERMES_YOLO_MODE) approval bypass. |
| `test_zombie_process_cleanup.py` | Tests for zombie process cleanup — verifies processes spawned by tools are properly reaped when agent sessions end. |

## `tests/tui_gateway/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `_compute_host_frames.py` | Causal, thread-safe compute-host frame capture for protocol tests. |
| `_turn_marker_backend.py` | Sibling-backend child for the turn-marker cross-process race test (spawned, so importable). |
| `conftest.py` | tui_gateway test fixtures. |
| `contracts/__init__.py` | Package marker / package-level exports |
| `contracts/test_generated.py` | The committed TypeScript + OpenRPC contract files are exactly what ``tui_gateway/contracts`` renders, and the contract catalog covers the whole wire. |
| `contracts/test_profile_rename_history.py` | Regression for #117696: roster rename history belongs to the wire contract. |
| `test_adversarial_sidecar_availability.py` | Native interactive viewers retain registered presentation sidecars. |
| `test_approval_cancelled_on_reap.py` | Pending gateway approvals dropped by interrupt/reap/teardown must be loud, not silent (#106678). |
| `test_attach_does_not_wait_for_agent.py` | Attach RPCs must not block on the deferred agent build. |
| `test_auto_continue.py` | Crash-interrupted turns auto-continue on the next session.resume. |
| `test_backend_dir_entries_preconfirmed.py` | Backend path completion must arrive at ``terminal_tool`` pre-confirmed. |
| `test_backend_heartbeat.py` | Tests for #94895: gateway-side heartbeat refresher wiring. |
| `test_background_thread_profile_scope.py` | Background threads started from a profile-scoped turn carry that profile's scope. |
| `test_billing_plan_usage.py` | ``plan_usage`` on billing.state / subscription.state: window plans only. |
| `test_billing_profile_scope.py` | Regression for #132728: registered Portal RPCs bind the selected profile. |
| `test_billing_rpc.py` | Tests for the Phase 2b billing JSON-RPC methods (tui_gateway/server.py). |
| `test_bot_live_owner_delivery.py` | Imported turns retain their receipt and cannot bypass the local FIFO. |
| `test_bot_mode_silence_delivery.py` | Bot Mode never renders or relays a bare intentional-silence marker (#110782). |
| `test_bot_relay_methods.py` | Tests: bot_relay.* JSON-RPC handlers (tui_gateway/methods_bot_relay.py). |
| `test_branch_system_prompt.py` | A TUI/Desktop branch child sends the bytes its parent already sends. |
| `test_busy_compression_demotion.py` | Compression in flight demotes busy-mode steer/interrupt to queue (#61042). |
| `test_canonical_voice_events.py` | Push-to-talk events for a shared-owner session reach the client that started the capture. |
| `test_canonical_voice_mode_writers.py` | One voice-mode state for a shared-owner session (T9 review round 1). |
| `test_change_watcher.py` | The generalized change watcher (#73618): cheap on-disk signatures → ``pet.changed`` / ``cron.changed`` / ``sessions.changed`` global broadcasts. |
| `test_change_watcher_sessions.py` | Tests: `_seed_store`, `test_sessions_signature_ignores_gateway_heartbeat_only_writes`, `test_sessions_signature_changes_for_session_metadata_updates`, `test_sessions_signature_sees_a_commit_inside_the_same_mtime_tick` |
| `test_checkpoints_config_fallback.py` | Tests for TUI/desktop checkpoint config fallback (#79625). |
| `test_closed_session_turn_lease.py` | A turn that reaches admission after ``session.close`` must not leave an active-session lease. |
| `test_codex_app_server_live_events.py` | Cross-layer regression for Codex app-server tool cards in the TUI. |
| `test_cold_start_gil_stall.py` | Tests for cold-start GIL stall mitigations (#60800). |
| `test_command_catalog_plugin_discovery.py` | ``commands.catalog`` says when its plugin discovery failed (#134889 PLG-7, CLI-13). |
| `test_command_description_fidelity.py` | Command descriptions survive both catalog and completion transport. |
| `test_compaction_status.py` | Auto-compaction status re-tagging for TUI/desktop summarizing indicators. |
| `test_completion_cwd_profile_fallback.py` | A pooled profile's sessions land in THAT profile's workspace (#87584). |
| `test_composite_carrier_rewind.py` | Regression contracts for TUI rewind of live compaction carriers. |
| `test_compress_lock_skip.py` | Tests for TUI gateway /compress lock-hold signalling. |
| `test_compress_session_cwd.py` | Manual /compress rebuilds the system prompt on the RPC thread; it must see the session's workspace. |
| `test_compression_config_hot_reload.py` | Desktop/TUI sessions must adopt live compression config on the next turn. |
| `test_compute_host.py` | Tests: `_stdout_queue`, `_read_json_line`, `test_compute_host_line_json_hello_and_shutdown` |
| `test_compute_host_borrowed_lease.py` | Regression tests for #101416: isolated (compute-host) turns refused their own session. |
| `test_compute_host_late_compress_ack.py` | Regression tests for #97948 symptom A (salvaged from #99630). |
| `test_compute_host_pending_model_switch.py` | Regression tests for #79509: a model switch on a compute-host (turn-isolation) session must cross the process boundary and be applied by the CHILD's live agent. |
| `test_compute_host_phase1.py` | Tests: `_json_lines`, `_wait_for_frame`, `test_compute_host_workers_inherit_tui_pool_env`, `test_compute_host_routes_relayed_response_and_lock_to_its_open_request`, `test_compute_host_withdraws_its_open_request_when_the… |
| `test_compute_host_routed_secret_hydration.py` | A routed compute-host session hydrates the profile's EXTERNAL secret sources before building its scope (#119521): the isolated turn process never ran the launch dotenv path for that profile, so without hydration a vault… |
| `test_compute_host_turn_protocol.py` | Turn-protocol coverage for the compute host's REAL (non-seeded) frame path. |
| `test_config_profile_scope.py` | config.get / config.set must honor params.profile (issue #95760). |
| `test_config_set_display_toggles.py` | `config.set` has to accept the Appearance switches the desktop mirrors. |
| `test_config_set_session_profile_scope.py` | ``config.set`` bound by ``session_id`` alone persists into the session's profile (issue #85669). |
| `test_config_set_voice_chat_mode.py` | `config.set voice.voice_chat_mode` is how the composer's voice menu swaps engines. |
| `test_connector_account_surface.py` | Account-owned connector RPCs come only from the desktop Connectors page, so their gateway requests name the ``desktop`` surface even on a backend started without ``HERMES_DESKTOP`` (a URL, SSH-less or cloud backend the… |
| `test_connector_accounts_rpc.py` | Named connector accounts over the real RPC dispatch. |
| `test_connector_operation_e2e.py` | Real-path desktop connection-operation lifecycle through the TUI gateway. |
| `test_connector_operation_rpc.py` | Connector operation RPCs and events over the real dispatch path. |
| `test_connectors_page_identity.py` | The desktop Connectors page, the CLI and the agent tool, and the guest identity behind hosted connectors. |
| `test_container_backend_workdir.py` | #103147: a container backend's ``terminal.cwd`` (docker ``/workspace``) lives inside the sandbox. |
| `test_context_local_slash.py` | ``/context`` must be answered IN-PROCESS for a local (non-compute-host) session. |
| `test_credit_producer_suppression.py` | Actual response-header capture -> credit latches -> CLI/TUI presentation. |
| `test_cross_process_orphan_ownership.py` | Tests: `_spawn_lease_holder`, `_wait_for_child_file`, `_stop_child`, `test_unlimited_session_lease_is_real_even_without_a_cap`, `test_orphan_guard_fails_closed_when_registry_is_unavailable`, `test_desktop_claim_fails_cl… |
| `test_custom_provider_session_persistence.py` | Session persistence must not strip a custom provider's identity. |
| `test_default_profile_session_name.py` | Default-profile session names must be derived from the home path, not its basename. |
| `test_deferred_lease_reaper.py` | Stale deferred active-session leases are reaped, not held forever (#62823). |
| `test_deferred_model_history.py` | Bounded Desktop hydration salvaged from Benjamin Brumbaugh's PR #106838. |
| `test_deferred_model_switch_confirm.py` | A model picked mid-turn must still get its selection-guard confirm step. |
| `test_delegation_session_lifecycle.py` | Fail-closed ownership + session-scoped delegation lifecycle (#55578). |
| `test_desktop_session_login_identity.py` | A Desktop session's state.db row must record the login that created it. |
| `test_desktop_session_row_git_meta.py` | A Desktop session's lazily created row must get git_branch/git_repo_root (#108784). |
| `test_desktop_session_workspace_persistence.py` | Desktop-provided project workspaces remain durable session metadata (#108205). |
| `test_detached_loop_keepalive.py` | A detached Desktop/TUI session that owns an active /loop must survive the orphan reapers. |
| `test_detached_process_notify_keepalive.py` | A detached Desktop/TUI session waiting on a background process's completion notice must survive the reapers. |
| `test_diagnostic_notification_presentation.py` | Diagnostic wake execution and structured controls survive a presentation veto. |
| `test_diagnostic_turn_end_to_end.py` | Diagnostic wake exercises the actual TUI turn, event transport, and control callback. |
| `test_diagnostics_share_nous.py` | diagnostics.share_nous RPC — Desktop "Send Diagnostics" upload path. |
| `test_display_methods.py` | display.install runs its worker inside the caller's profile scope; display.observe mints the viewer identity. |
| `test_display_watch.py` | Lease transitions made by ANOTHER process reach `hermes serve` clients as ``display.lease``. |
| `test_eager_multiplex_activation.py` | Eager multi-profile activation: when a host arms the fail-closed secret guard, and when it must not. |
| `test_empty_fast_status.py` | ``config.set fast status`` reports "normal" for an explicit-normal pin. |
| `test_entry_home_ownership.py` | The standalone stdio entry is never a second state.db writer beside a gateway. |
| `test_entry_import_off_main_thread.py` | Regression test: importing tui_gateway.entry off the main thread must not crash. |
| `test_entry_inline_handler_error.py` | Regression coverage for stdio inline-handler failures (#112816). |
| `test_entry_picker_prewarm.py` | Regression test: the stdio TUI entry point prewarms the /model picker cache. |
| `test_entry_rpc_stdin_cloexec.py` | Regression coverage for the stdio gateway's child-process boundary. |
| `test_entry_rpc_stdin_windows.py` | The stdio TUI gateway's RPC pipe never reaches a child launched without ``stdin=`` on Windows. |
| `test_entry_sys_path.py` | Regression test for tui_gateway/entry.py sys.path hardening (#15989, #51286). |
| `test_ephemeral_profile_override.py` | Regression tests: profile HERMES_HOME override in ephemeral agent threads (#50233). |
| `test_external_process_picker.py` | A user-installed ``external_process`` provider must survive shared picker discovery and native selection. |
| `test_failed_agent_build_retry.py` | A failed agent build must not wedge the session. |
| `test_failed_turn_retention.py` | Failed turns must retain a replayable ``inflight`` snapshot. |
| `test_fallback_chain_hot_reload.py` | Desktop/TUI sessions must adopt a ``fallback_providers`` chain added after the chat was opened. |
| `test_fanout_burst_batching.py` | The per-peer fanout drain sends what is queued as ONE batch on the socket's loop, not one cross-thread round trip per frame: a producer with no per-frame I/O (an in-process turn streaming tokens) otherwise outruns a hea… |
| `test_fanout_send_membership.py` | Session detach revokes queued fanout frames without closing a shared socket. |
| `test_fast_session_scope.py` | Fast-mode (service tier) session scoping in the TUI gateway (desktop backend). |
| `test_file_attachment_allocation.py` | File attachment uploads retain their bytes in the shared profile namespace. |
| `test_finalize_session_cancels_background_review.py` | Regression for #102895: deleting/closing a session must stop its in-flight background memory/skill review fork. |
| `test_finalize_session_persist.py` | Integration test: verify _finalize_session persists messages on force-quit. |
| `test_first_contact_onboarding.py` | Desktop/TUI first-contact profile-build onboarding via tui_gateway (#82750). |
| `test_foreground_notification_snapshot.py` | Foreground decisions stay stable through file changes and child callbacks. |
| `test_free_tier_rpc.py` | ``free_tier.status`` / ``free_tier.ack_notice`` (pull) and the free-tier branch of ``billing.state``, driven through the registered RPC handlers against a claimed welcome trial on the desktop's local backend (the fake a… |
| `test_free_tier_task_done.py` | A finished task on the free tier: a turn that completed on its own with a reply arms the sign-in offer (``hermes_cli.free_tier_offer``); any user intervention while it ran disqualifies it. |
| `test_gateway_bootstrap_control_home.py` | Ink bootstrap must acquire a served secondary's ticket from its multiplexer control home. |
| `test_gateway_bootstrap_recover.py` | Ink reconnect re-ensures an owner that is gone, however it went (W11, P2). |
| `test_gateway_owned_session_reap.py` | Tests for #60609: the TUI backend must not end gateway-owned sessions. |
| `test_goal_command.py` | Tests for /goal handling in tui_gateway. |
| `test_groups_forward_parity.py` | The standalone route reaches every room method the gateway route serves (#145960). |
| `test_groups_log_member_actor.py` | ``groups.log`` serves member replies whose actor carries the profile/display/connection stamp. |
| `test_groups_methods.py` | Tests for the gateway-hosted ``groups.*`` JSON-RPC contract. |
| `test_groups_owner_forward.py` | A standalone backend sends Group Chat calls to the gateway that owns the profile (WA-19). |
| `test_groups_replication_methods.py` | Tests for the ``groups.replicate`` / ``groups.promote`` / ``groups.demote`` JSON-RPC surface — cross-gateway room durability. |
| `test_groups_retry_coordinates.py` | Standalone ``groups.state`` retry rows carry the exact attempt ``groups.retry`` accepts back. |
| `test_groups_route_parity.py` | Both server routes answer the group composer alike (#145184 points 2 and 4). |
| `test_gui_surface_toolsets.py` | GUI capability follows the SESSION's client, not the backend's process env. |
| `test_heartbeat_tui_tick.py` | /heartbeat firing from the TUI/Desktop session-owner process (#102056, #103044). |
| `test_heartbeat_wakes.py` | A background-process heartbeat is a wake for the model, not a message from the user. |
| `test_history_identity.py` | Repeated content cannot stand in for persisted transcript identity. |
| `test_history_inline_images.py` | ``inline_images=false`` history reads (#116511): the reachable ``[image]`` projection. |
| `test_hosted_file_publication.py` | Service share and raced publication preserve the original durable task. |
| `test_hosted_room_attachment_routes.py` | A member turn with a bound file must not reach a route that cannot carry it. |
| `test_hosted_room_discussion_limits.py` | Owner-scoped configuration and durable native Discussion budget contracts. |
| `test_hosted_room_discussion_retry_budget.py` | A retried deferred turn must not stall a discussion configured to its full reply budget. |
| `test_hosted_room_driver_runtime.py` | Runtime tests for the hosted-room session adapter. |
| `test_hosted_room_error_logging.py` | Hosted task diagnostics persist fixed reason codes, never exception bodies. |
| `test_hosted_room_frozen_publication.py` | Frozen admissions reconstruct from canonical storage, not display caches. |
| `test_hosted_room_member_activity.py` | groups.state names the member answering, so Desktop can show per-bot activity. |
| `test_hosted_room_member_activity_hook.py` | on_room_member_activity: a room member's hidden-session runtime events reach plugins with room coordinates; an ordinary session's identical events never do. |
| `test_hosted_room_member_submit.py` | The driver must name the member on every submit it hands to a transport. |
| `test_hosted_room_peer_http.py` | Scoped peer Runs adapter tests. |
| `test_hosted_room_peer_transport.py` | Peer transport tests for hosted-room member turns. |
| `test_hosted_room_policy_upgrade.py` | Late-receipt indexing upgrades derived caches, never accepted inputs or history. |
| `test_hosted_room_prompt_fence.py` | Older Desktop clients cannot start a second driver for hosted rooms. |
| `test_hosted_room_server_rpc.py` | Tests for the in-process hosted room session adapter. |
| `test_hosted_room_service.py` | Integration tests for the hosted Discussion coordinator. |
| `test_hosted_room_settled_retry.py` | Deferred results survive discussion and bounded-transcript cleanup. |
| `test_hosted_room_turn_slot_release.py` | A hosted room member turn releases the profile's ``bot_room`` active-session slot when it ends. |
| `test_hosted_room_two_gateway_scoped.py` | Scoped grant UAT: home service to a real peer API adapter, no Desktop. |
| `test_hud_surface_note.py` | HUD mode reaches the model as a per-turn note, not as a platform hint. |
| `test_human_input_hooks_tui.py` | The Ink TUI / Desktop sudo card fires the human-input hook pair without the typed password (#132333). |
| `test_i18n_methods.py` | ``i18n.languages`` lists bundled + pack languages; ``i18n.catalog`` returns the pack/overlay layer per surface and nothing bundled; both answer for the requested profile's home. |
| `test_image_history_display.py` | Native image history projection regression for #120083. |
| `test_image_ref_message.py` | Desktop image submit path must never block on vision calls (#83291). |
| `test_image_routing_stale_model.py` | Regression coverage for live TUI image-routing identity. |
| `test_init_targets_session_cwd.py` | ``/init`` on the TUI/desktop surface must target the SESSION's active directory. |
| `test_ink_helper_dependencies.py` | Ink's Python helpers boot PM's committed dependency generation themselves (regression for #138878). |
| `test_inline_rpc_gil_starvation.py` | Tests for tui_gateway inline-RPC pool routing under GIL pressure (#50005). |
| `test_interim_assistant_callback.py` | Tests for the interim_assistant_callback config gating in tui_gateway. |
| `test_interrupt_agent_loop_stopped_hook.py` | The TUI/desktop ``session.interrupt`` path is a sibling of the gateway's ``_interrupt_and_clear_session``: when a live turn is stopped, plugins holding per-turn external resources need the same ``agent_loop_stopped`` si… |
| `test_interrupt_dead_compute_host.py` | session.interrupt on a compute host that is gone (hermes-agent 82603). |
| `test_interrupt_does_not_wait_for_agent.py` | session.interrupt must not wait on, or start, the deferred agent build (#133262). |
| `test_iso_certify_seam.py` | The AC-4 synthetic heavy-turn agent (``tui_gateway/synthetic_turn.py``) is a test seam: it must stay dead unless ``HERMES_ISO_CERTIFY_SYNTH_TURN=1``. |
| `test_isolated_orphan_activity.py` | Detached Desktop/TUI turns use child-owned activity, not process heartbeats. |
| `test_kanban_notify_poller.py` | Tests for the TUI-side kanban notification poller (issue #59890). |
| `test_kanban_resume_guard.py` | Gateway/desktop `session.resume` must refuse a Kanban worker transcript (#68779). |
| `test_launch_db_home_override_race.py` | Regression for #102526. |
| `test_launch_home_isolation.py` | The launch home the TUI server binds launch-profile turns to must follow the process home. |
| `test_launch_profile_scope_plugin_hooks.py` | Plugin hooks fired from a launch-profile turn see a bound profile scope under multiplexing. |
| `test_lazy_session_regressions.py` | Reproduction tests for #18370 fallout: lazy session creation regressions. |
| `test_legacy_events_since_replay_epoch.py` | Legacy ``session.events.since`` replays a reconnect that includes ``replay_epoch``. |
| `test_legacy_fallback_launch_explicit_profile.py` | A launch-profile socket that names another profile runs that verb in the named profile. |
| `test_legacy_fallback_profile_scope.py` | B11: a ticket bound to a secondary profile reads ITS profile through the legacy session fallback. |
| `test_legacy_fallback_ticket_profile_verbs.py` | N86: every legacy-fallback verb from a ticket bound to a secondary profile runs in THAT profile. |
| `test_legacy_paste_profile_home.py` | A legacy ``paste.collapse`` on the shared owner writes under the ticket's profile home. |
| `test_legacy_submit_forwards_to_owner.py` | RT-37 (#140385): a Desktop prompt on a session whose gateway owner is running a turn (a Bot Chat delivery) is admitted into the OWNER's durable FIFO and runs after that turn, exactly once. It is not refused ``SESSION_NO… |
| `test_legacy_turn_canonical_barrier.py` | Standalone ``serve`` (no session authority) must not run a legacy turn past the gateway's durable ledger: an ``unknown`` admission is never replayed, queued input runs in FIFO order. |
| `test_live_config_context_pin_mirror.py` | Desktop/TUI config hot-reload must keep the agent's cached context pin in step with the compressor's. |
| `test_live_usage_window_gate.py` | slash.exec /usage: the Nous block gets the last reply's window gauges only on a session already known to be on a usage-window plan; every other session makes exactly main's call. |
| `test_local_model_session_identity.py` | A local selection must survive session.info, a new chat and stored-session resume. |
| `test_loop_command.py` | Tests for /loop handling in tui_gateway. |
| `test_machine_facts_rpc.py` | ``machine.facts`` answers the host summary through the registered handler and its contract, and answers the same for every profile one backend serves. |
| `test_main_merge_projections.py` | Extracted discovery and snapshot projections retain main's wire contracts. |
| `test_make_agent_personality_prompt.py` | _make_agent resolves ephemeral prompt from display.personality. |
| `test_make_agent_prefill.py` | Desktop/TUI agents honor ``prefill_messages_file`` from the active profile. |
| `test_make_agent_provider.py` | Regression test for #11884: _make_agent must resolve runtime provider. |
| `test_manual_compress_history_fence.py` | Manual compression must not publish a snapshot invalidated before lease admission. |
| `test_mcp_late_refresh_thread_owner.py` | Regression test for issue #51587. |
| `test_mcp_oauth_cancel.py` | Cancellation wakes the actual callback worker without crossing profile ownership. |
| `test_mcp_oauth_client_callback.py` | Tests for the client-side callback (remote-backend) variant of the session-backed MCP OAuth flow (tui_gateway/mcp_oauth_sessions.py). |
| `test_mcp_profile_rpcs.py` | E2E tests for the per-profile MCP lifecycle RPCs (mcp.servers.*). |
| `test_mcp_reload_all_sessions.py` | reload.mcp refreshes the tool snapshot of EVERY live session, not only the requester's. |
| `test_mcp_reload_rev.py` | reload.mcp revision-aware coalescing (review on #20379, finding 1). |
| `test_moa_reference_emit.py` | Tests for the TUI gateway relaying MoA reference events to the client. |
| `test_model_options_profile_scope.py` | Tests: `test_model_options_binds_requested_profile_home` |
| `test_model_rpc_skew_guard.py` | #99859 (R2): the TUI gateway's model-serving JSON-RPCs refuse on code skew. |
| `test_model_switch_marker_role.py` | Tests for _append_model_switch_marker role fix (issue #48338). |
| `test_model_switch_reasoning_flag.py` | ``config.set model "X --reasoning <level>"`` on the TUI gateway: the effort rides with the pick. |
| `test_multi_client_fanout.py` | Shared-session routing and backpressure, exercised through real OS pipes. |
| `test_multi_profile_hosting_fail_closed.py` | Multi-profile hosting in the TUI gateway is fail-closed and every profile-scoped RPC runs under the FULL runtime scope of the requested profile (home + secrets + terminal), the launch profile included once the process m… |
| `test_multi_profile_hosting_transitions.py` | Serve / dashboard profile scopes stay authoritative across the first-secondary transition. |
| `test_none_agent_turn_guard.py` | A turn must never run against a session record whose agent is ``None``. |
| `test_notification_admission_refusal.py` | A refused legacy turn is not a completion delivery receipt. |
| `test_notification_refusal_backoff.py` | Refused producer turns must not hot-loop against the canonical ledger (#140385). |
| `test_notification_turn_release.py` | A notification that claims the session's turn must hand it back whenever no turn runs. |
| `test_onboarding_e2e.py` | First-run onboarding end to end through the gateway's real card path: setup_beat runs in the agent's inline executor, its card goes out as the ``setup_beat`` server request (params checked against the contract), a fake… |
| `test_onboarding_endings.py` | Deleting the onboarding chat: the run ends only once the delete succeeded, on every compression copy. |
| `test_onboarding_fresh_launch.py` | Closing the app before onboarding finishes does not count: the next launch's ``onboarding.start`` (``fresh_launch``) deletes the unfinished chat and starts over at the name beat, while a second window or a reconnect in… |
| `test_onboarding_run_rpc.py` | ``onboarding.state`` / ``onboarding.set_run`` read and write the ROOT profile's config.yaml, even from a pooled backend launched under a named profile, and answer ``{run, eligible, session_id}``. |
| `test_onboarding_session.py` | The onboarding chat in the gateway: ``onboarding.start`` / ``onboarding.state`` / ``onboarding.skip``, the toolset fold-in that gives setup_beat to that chat only, the scripted opening, the turn note, and the run record… |
| `test_onboarding_welcome_claim.py` | ``onboarding.state`` / ``onboarding.start`` and the desktop's welcome trial: a new run on a first install claims it with the install already marked due, a rerun never does, a failed claim leaves no guest and no chat and… |
| `test_out_of_band_history_adoption.py` | Regression for #42962: a turn another surface (Telegram, cron) appended to a live desktop/TUI session must reach the model on the next local prompt, not only the repainted transcript. |
| `test_pending_hidden_consumption.py` | Regression for #116126: a session born hidden stays un-hidden once the user un-hides it. |
| `test_personality_clobbers_system_prompt.py` | Reproduction: /personality (desktop config.set) clobbers agent.system_prompt. |
| `test_ping_probe.py` | Tests for the ``ping`` liveness probe (tui_gateway/server.py). |
| `test_plugin_inject_host.py` | Plugin inject_message reaches the Ink TUI / desktop session it names. |
| `test_plugin_skill_slash.py` | Plugin-registered skills in the TUI/Desktop slash menu (``/plugin:skill``). |
| `test_plugins_catalog_lookup.py` | ``plugins.catalog.lookup``: the deep link's catalog lookup, resolved by the backend (hermes-agent 136483). |
| `test_plugins_manage_inspect.py` | Gateway ``plugins.manage inspect``: the browser-hosted app's repository check before install. |
| `test_plugins_manage_install.py` | Gateway plugins.manage install action. |
| `test_plugins_manage_install_desktop.py` | Gateway ``plugins.manage install_desktop`` / ``remove_desktop``: the browser-hosted app's install. |
| `test_plugins_manage_late_activation.py` | #87770 — a Desktop/TUI ``plugins.manage install`` is a mid-run load path too: the install performs a REAL forced rescan in the serving process, ``PluginManager.on_plugin_loaded`` fires from inside it for the newcomer, a… |
| `test_plugins_manage_remove.py` | Gateway ``plugins.manage remove`` — the Desktop Plugins hub's Uninstall door. |
| `test_plugins_manage_settings.py` | Gateway ``plugins.manage`` — manifest ``config_schema`` rendered as settings fields (#46600, #87934). |
| `test_plugins_manage_tool_ownership.py` | ``plugins.manage list`` names the tools each package's own code produces (``tools``): Desktop lets a plugin's desktop half render media only from those, so the answer must come from what the loader actually registered,… |
| `test_pre_agent_fallback_notice.py` | A TUI/Desktop agent built on a credential-resolution fallback (primary AuthError -> fallback_providers entry) must carry the same one-shot switch notice the messaging gateway surfaces (#74349), and the private notice ke… |
| `test_preview_action_bridge_fail_fast.py` | A desktop client that cannot answer the ``preview.act`` server request must not cost a full bridge timeout per drive_preview / annotate_preview call. |
| `test_profile_db_readonly.py` | Foreign-profile _profile_db handles must not write-lock another profile's live store. |
| `test_profile_rebuild_commit.py` | Session-only tools ingress and rebuild failure preserve profile isolation. |
| `test_profile_resume_cwd.py` | A resumed session for a NAMED profile lands in THAT profile's workspace (#87584). |
| `test_profile_resume_cwd_persist.py` | Every ``session.resume`` path repairs a named profile's saved workspace (#87584). |
| `test_profile_roster_reader_cache.py` | The canonical gateway's roster memo (``cached_reader_session_fields``, #139227) keys on the reader as well as the store: one principal's answer is never served to another, and ``invalidate`` drops it like the other memo… |
| `test_profile_shell_hooks.py` | Profile-bound agent construction must arm real shell policy. |
| `test_profile_target_unavailable.py` | An unavailable explicit target must never become the launch profile. |
| `test_profile_terminal_scope_entrypoints.py` | Terminal-scope invariants for the TUI gateway's off-turn profile entrypoints under multiplexing. |
| `test_profiles_configure.py` | profiles.describe / profiles.configure use the MCP ``enabled`` key the runtime reads. |
| `test_profiles_configure_model_guard.py` | profiles.configure honours the model selection guard (#95293 remainder). |
| `test_profiles_create_env_refs.py` | A bot created from the launch profile gets its ``${VAR}`` refs, never their resolved values. |
| `test_profiles_describe_secret_scope.py` | profiles.describe / profiles.configure resolve credentials from the described profile's scope. |
| `test_profiles_inherit_launch_model.py` | profiles.create inherits the launch profile's model together with the custom gateway backing it. |
| `test_profiles_list_canonical_session.py` | Tests: profiles.list ``canonical_session`` registry summaries. |
| `test_profiles_list_session_field_cache.py` | ``profiles.list`` reuses a profile's session fields only while its session store has not moved. |
| `test_profiles_list_ui_meta_cache.py` | ``profiles.list`` re-parses a profile's ``profile.yaml`` for ui_meta only when it has changed. |
| `test_profiles_list_worker_session.py` | Tests: profiles.list ``worker_session`` (freshest kanban/tool worker). |
| `test_profiles_toolset_pin.py` | profiles.configure ``enabled_toolsets`` must pin the key the runtime reads. |
| `test_profiles_ui_meta_cas.py` | Gateway-owned revisions for concurrent profile UI metadata updates. |
| `test_project_tree.py` | Invariants for the authoritative project-tree builder (tui_gateway.project_tree). |
| `test_projects_rpc.py` | Tests for the projects.* JSON-RPC methods on the tui_gateway server. |
| `test_prompt_accept_logging.py` | Desktop/TUI turn-dispatch observability (#86647). |
| `test_protocol.py` | Tests for tui_gateway JSON-RPC protocol plumbing. |
| `test_provider_not_configured_code.py` | A session that cannot start for lack of a provider says so in a machine-readable way. |
| `test_queued_prompt_persistence.py` | A prompt accepted while the agent is busy is durable at ACCEPT time. |
| `test_queued_prompt_restart_retire.py` | A restart discards the in-memory busy-queue, but the accept-time user row it wrote stays active — the next cold resume's alternation repair glues the never-run prompt into the previous turn's user message (#125577). |
| `test_raw_config_cache_stat_errors.py` | The TUI raw-config cache never treats an unreadable config.yaml as an absent one. |
| `test_readiness_singleflight.py` | Overlapping readiness polls must not saturate the shared RPC pool (#65151). |
| `test_reap_respects_canonical_ledger.py` | A viewer's reap never stamps a session ended while the gateway's ledger holds its turn (#140642). |
| `test_reaper_flush_profile_scope.py` | The reaper/exit-flush transcript persistence: right home, no external-secret hydration. |
| `test_reasoning_config_per_model.py` | Tests for per-model reasoning_effort override in TUI gateway _load_reasoning_config. |
| `test_reasoning_session_scope.py` | Reasoning-effort session scoping in the TUI gateway (desktop backend). |
| `test_relay_live_author.py` | A relayed dm into a live Bot Chat keeps its sender all the way into ``run_conversation``. |
| `test_remote_backend_launch_cwd.py` | A TUI/dashboard session on a sandbox backend never sends the gateway's launch directory to the sandbox. |
| `test_resolve_model_silent_default.py` | Tests: the TUI's no-model fallback follows the one silent-default constant. |
| `test_restored_delegation_transport.py` | A completion replayed at process start requires a real notification consumer (#138348). |
| `test_resume_child_run_profile_scope.py` | The child-run liveness registry must be profile-scoped on the resume path. |
| `test_resume_live_lazy_session.py` | Tests: session.resume finds LIVE lazy (never-persisted) sessions. |
| `test_resume_live_profile_scope.py` | ``session.resume`` reuses a live session only within the requested profile. |
| `test_resume_profile_scope.py` | ``session.resume`` resolves a stored session's provider overrides under the SESSION profile's scope. |
| `test_resume_readonly_mount.py` | Mounting a finalized session is read-only (#85303): session.resume / its deferred hydration / the lazy watch path must NOT clear ``ended_at``/``end_reason`` — only the first real turn (prompt.submit) reopens the row, so… |
| `test_resume_session_yolo.py` | A session /yolo (TUI Shift+Tab, the Desktop zap) survives a backend restart: persisted on the session row and re-armed by ``session.resume`` in a process whose in-memory approval set starts empty. |
| `test_resume_switched_provider_endpoint.py` | A chat switched to another provider must resume on THAT provider's endpoint. |
| `test_retirement_admission.py` | Every admission source participates in the same process retirement fence. |
| `test_retirement_continuations.py` | Retirement cannot splice between a turn's completion and its automatic successors. |
| `test_retirement_workers.py` | Detached work must retain process admission, including scoped side-agent cleanup. |
| `test_review_summary_callback.py` | Tests for tui_gateway background-review summary delivery. |
| `test_rollback_container_refusal.py` | ``rollback.diff`` refuses a container-backed session like every other ``/rollback diff`` surface. |
| `test_rollback_restore_safe.py` | The sidecar's whole-tree ``rollback.restore`` keeps the user's hand-edits like the owner's. |
| `test_routing_provenance_reopen.py` | #106459: a stale explicit-close stamp (``tui_close`` on a session the TUI still routes) wedged compression forever, because publish fails closed on it and ``end_session()`` is first-stamp-wins. The TUI clears it under `… |
| `test_runtime_identity.py` | Runtime identity contract for TUI gateway machine protocol fields. |
| `test_secondary_profile_model_and_key.py` | One Desktop backend serving two profiles: a secondary session's key save and model belong to IT. |
| `test_secret_capture_session.py` | Skill credential prompts go to the session that owns the turn, never the last wired one. |
| `test_seeded_branch_title_routing.py` | Seeded Desktop branches keep generated titles out of memory identity. |
| `test_seeded_session_create.py` | session.create with seeded messages: the seed is durable before the first prompt, and durable once. |
| `test_serve_exit_flush.py` | A killed ``hermes serve`` must not lose in-memory session transcripts. |
| `test_served_profile_child_env.py` | A child spawned FOR a served profile carries that profile's env, never the launch profile's. |
| `test_served_profile_child_env_authority.py` | A routed profile's child never receives a launch-profile credential — whatever its provenance. |
| `test_server_requests.py` | Server→client request ordering on the wire (tui_gateway/server_requests.py). |
| `test_session_agent_cwd.py` | Workspace changes reach new Codex threads without rebinding memory or prompts. |
| `test_session_archive_rpc.py` | RPC-level tests for ``session.archive`` (tui_gateway, #47168). |
| `test_session_control.py` | Behavioral contract tests for Desktop session-control JSON-RPC methods. |
| `test_session_create_model_provider_guard.py` | ``session.create`` rejects a model the selected provider cannot serve (#96817). |
| `test_session_cwd_follow.py` | A session that settles into another git worktree re-anchors onto it. |
| `test_session_cwd_profile_key.py` | A secondary profile's session.create cwd record is readable inside that profile's turn scope. |
| `test_session_db_ownership_teardown.py` | Dedicated profile ``SessionDB`` handles must be closed by whoever ends up owning them. |
| `test_session_delete_rpc.py` | ``session.delete``: argument checks, the live-session refusal, the profile's db and sessions dir, and the onboarding run a deleted chat ends first (moved out of test_tui_gateway_server.py). |
| `test_session_finalize_reaps_kernels.py` | Session finalize disposes the owner's execute_code kernels (TUI-owned only). |
| `test_session_foreign.py` | Real foreign logs through the registered desktop RPCs and profile stores. |
| `test_session_git_metadata_generation.py` | Gateway wiring for generation-scoped Git metadata publication. |
| `test_session_hidden_rpc.py` | RPC-level tests for the generic hidden-session surface (tui_gateway). |
| `test_session_history_codex_sidecar.py` | RPC history must retain visible Responses-API assistant sidecars (#68321). |
| `test_session_id_injection.py` | Contract test: tui_gateway._set_session_context must inject the live session id into HERMES_SESSION_ID so terminal/execute_code subprocesses can read the current session's id. |
| `test_session_images_dir.py` | Write-side scoping for desktop/clipboard image uploads (#69575). |
| `test_session_interrupt_cancels_background_review.py` | Regression for #102895 (sibling path): an explicit /stop must also cancel a running background memory/skill review, not only the foreground turn. |
| `test_session_list_lineage_rpc.py` | ``session.list`` must forward the durable lineage root. Regression for #66663. |
| `test_session_platform_resolution.py` | Platform/source tagging for the desktop chat surface. |
| `test_session_profile_db.py` | Session-scoped transcript ops must resolve against the session's own DB. |
| `test_session_reclaim_notify.py` | A backend-reclaimed session must tell the clients still holding it. |
| `test_session_resume_db_ownership.py` | ``session.resume`` must not abandon the profile-scoped SessionDB it opens. |
| `test_session_resume_materializes_minted_key.py` | ``session.resume`` materializes a row for a minted-but-never-persisted key. |
| `test_session_usage_account_lines.py` | Desktop/TUI ``/usage`` (``slash.exec``) shows provider account limits before the first turn. |
| `test_shared_metrics_consent_rpc.py` | shared_metrics.status / shared_metrics.set: the Desktop consent path keeps the CLI wizard's invariants (sending needs collection, every change reconciles the consent windows) and lands in the profile the request names,… |
| `test_shared_metrics_slash_command_rpc.py` | shared_metrics.slash_command: the TUI/Desktop client reports each typed slash command once, and the gateway no longer counts the slash.exec / command.dispatch hops a command may or may not take. |
| `test_shared_metrics_update_run_rpc.py` | shared_metrics.update_run: Desktop reports a packaged self-update as bounded kind=desktop dims only. |
| `test_shared_session_delivery.py` | Session observers retain output across attachment and disconnect. |
| `test_shell_exec_security.py` | Security-boundary regressions for the TUI ``shell.exec`` RPC. |
| `test_show_reasoning_display_gate.py` | Display gates on the live callback path. |
| `test_skills_manage_install.py` | Tests: skills.manage install path (tui_gateway/methods_tools.py::_skills_install). |
| `test_skin_watcher_profile_scope.py` | The shared gateway's skin watcher repaints each attached TUI with ITS profile's skin. |
| `test_slash_fuzzy.py` | Tests for the description-aware slash fuzzy scorer (grok-cli port). |
| `test_slash_prompt_compose_seed.py` | Worker-routed slash commands that queue a next-turn prompt must actually send it. |
| `test_slash_refine_live.py` | /refine from a completed Desktop/TUI session. The in-memory agent cache may be absent (or its history empty) on a session that was reattached from disk — refine must replay the PERSISTED transcript and spawn the backgro… |
| `test_slash_review_owner.py` | /review from slash.exec runs on the RPC pool, outside any turn. The reviewer it dispatches must still be registered under the parent Desktop/TUI session (HERMES_UI_SESSION_ID + exact steer authority), or `subagent.list`… |
| `test_slash_worker_ansi.py` | The slash worker feeds desktop chat bubbles, which render plain text — so any ANSI a worker-routed command emits (e.g. /journey's own Rich Console) must be stripped from the worker's return value. |
| `test_slash_worker_mcp_discovery.py` | Integration coverage for profile-local MCP discovery in slash workers. |
| `test_slash_worker_provider.py` | The slash worker inherits the parent agent's provider, not the config default (#57283). |
| `test_slash_worker_skill_refuse.py` | Skill slashes must not ok-reply a loading banner from the slash worker. |
| `test_slash_worker_sys_path.py` | Regression tests for tui_gateway/slash_worker.py sys.path hardening (issue #51286). |
| `test_slash_worker_watchdog.py` | Tests: `test_module_import_does_not_load_cli_before_watchdog_can_start`, `test_is_orphaned_true_when_ppid_changes`, `test_is_orphaned_false_when_direct_parent_is_unchanged`, `test_main_arms_watchdog_then_imports_cli_bef… |
| `test_spawn_tree_records.py` | Tests: spawn_tree.* JSON-RPC handlers (tui_gateway/methods_session.py). |
| `test_ssh_session_cwd_persistence.py` | An ssh session's launch directory is a host path: kept in memory, never persisted as its remote workspace. |
| `test_stale_provider_resume_live.py` | LIVE E2E: Desktop/TUI ``session.resume`` with a stale (deleted/renamed) custom provider, through the REAL gateway dispatch path. |
| `test_startup_orphan_sweep.py` | Tests for #65194: the gateway's startup-time orphaned-session sweep. |
| `test_status_profile_home.py` | Profile-owned /status path rendering for multiplexed TUI/Desktop sessions (#124500). |
| `test_stranded_session_adoption.py` | Stranded bot-session adoption (#93296 follow-up). |
| `test_stream_interrupt_recovery_orphan.py` | A stream that dies mid-answer must not leave an anonymous session behind (#111999). |
| `test_stream_segment_identity.py` | A prompt turn's message.* frames carry its wire identity (tui_gateway/stream_segments.py). |
| `test_subagent_child_mirror.py` | Tests for the gateway's child-session live mirror. |
| `test_subagent_snapshot.py` | Shared RPC contracts exercised against real registries and transcript I/O. |
| `test_submit_row_session_target.py` | One Desktop turn writes its user row and its tool rows into TWO sessions (#123545, evidence A + B). |
| `test_submit_time_user_row.py` | prompt.submit writes the user's message at send time, and the turn that follows adopts that row instead of writing a second one (#111868: a Desktop freeze during a slow first agent build left a session row with no messa… |
| `test_subprocess_encoding.py` | Regression tests for lossy UTF-8 decoding of TUI gateway subprocess output (#53137). |
| `test_sudo_command_context.py` | Sudo questions carry the original, redacted command through the real request path. |
| `test_theme_bridge.py` | ``set_theme`` picker bridge: the model can tell a pick, a dismissed card and an expired one apart. See tui_gateway.theme_bridge.theme_request. |
| `test_todo_state_events.py` | Todo snapshots bypass optional tool-progress display settings. |
| `test_tools_readback_scope.py` | tools.list / tools.show read back the SESSION's effective toolsets (#117977). |
| `test_tour_bridge_fail_fast.py` | A desktop client that cannot answer the ``tour`` server request must not cost a full bridge timeout per call. |
| `test_tui_entry_mcp_owner.py` | Regression tests: the stdio TUI consults the shared MCP discovery owner. |
| `test_tui_gateway_event_replay.py` | Tests for tui_gateway.event_replay — per-session event seq + replay ring. |
| `test_tui_gateway_loop_noise.py` | Tests for tui_gateway.loop_noise — the WS peer-hangup teardown filter (#50005). |
| `test_tui_gateway_notification_poller.py` | One live notification poller per TUI session across agent rebuilds (#138806). |
| `test_tui_gateway_queue_on_busy.py` | A prompt that lands mid-turn is redirected or queued, never dropped. |
| `test_tui_gateway_server.py` | Tests: `_dispatch_sync`, `_neuter_agent_prewarm_timer`, `_reap_leaked_notification_pollers`, `test_session_slot_is_claimed_on_first_turn_not_on_create`, `test_session_context_uses_session_cwd`, `test_handoff_fail_marks_… |
| `test_tui_gateway_server_attach_errors.py` | An attach payload over its cap is refused in one sentence naming its size and the cap. |
| `test_tui_gateway_server_branch_idempotency.py` | TUI gateway ``session.branch`` idempotency: a retried branch returns the same child (#65410). |
| `test_tui_gateway_server_browser_manage.py` | ``browser.manage`` RPCs: connect/disconnect/status (split from ``test_tui_gateway_server.py``). |
| `test_tui_gateway_server_crash_history.py` | Regression coverage for crashed TUI gateway turns. |
| `test_tui_gateway_server_deep_truncate.py` | prompt.submit history-cut opt-ins: ``confirm_empty_truncate`` (wipe) and ``confirm_deep_truncate`` (#133716: a cut that archives more than one user turn — a valid anchor can still name the wrong, stale row). |
| `test_tui_gateway_ws.py` | Tests: `_run_disconnect`, `test_ws_disconnect_reaps_flagged_session_and_closes_worker`, `test_ws_connection_registers_then_disconnect_unregisters_live_transport`, `test_ws_disconnect_releases_wake_word_owner`, `test_ws_… |
| `test_tui_mcp_late_refresh.py` | Tests for the TUI gateway's late MCP tool-snapshot refresh. |
| `test_turn_finished_failure_cause.py` | A failed TUI turn must say why in its own record (#89117). |
| `test_turn_payload_interim_final.py` | message.complete marks a final already delivered as an interim as previewed (#125951). |
| `test_turn_payload_response_transformed.py` | message.complete forwards ``response_transformed`` (#96465). |
| `test_turn_payload_reused_final.py` | message.complete names a final that reuses a response the turn already delivered. |
| `test_undo_command.py` | Tests for /undo handling in tui_gateway. |
| `test_user_messages.py` | User-facing copy for assistant-start failures must match the failure's actual cause. |
| `test_vault_methods.py` | Tests: vault.* JSON-RPC handlers (tui_gateway/methods_vault.py). |
| `test_voice_live_delegation.py` | GPT-Live voice chat mode: the full-duplex voice frontend that delegates to Hermes. |
| `test_voice_stopped_consumers.py` | TUI-26: every Python caller of the owner's canonical ``prompt.submit`` treats the declared ``{voice_stopped: true}`` reply (a bare stop phrase typed into a LOCAL voice chat: the chat ends and nothing is admitted) as set… |
| `test_wait_for_mcp_discovery.py` | Tests for tui_gateway.entry.wait_for_mcp_discovery (PR #35245). |
| `test_warning_callback_conservation.py` | Real callback and queue boundaries; renderer preference never hides operator logs. |
| `test_ws_concurrent_reads.py` | The WS concurrent-read lane (#134889 GW-18 review): waiting context reads stay bounded, a server shutdown or client hang-up never waits for reads that have not started, and a reply the read lane cannot send never cancel… |
| `test_ws_keepalive.py` | Regression tests for WebSocket dead-peer detection via TCP keepalive. |
| `test_ws_keepalive_config.py` | Config propagation tests for the WS keepalive + orphan-reap grace knobs (#79635). |
| `test_ws_orphan_races.py` | Orphan callbacks own only their detachment, never a later reconnect. |
| `test_ws_send_timeout.py` | A stalled ``send_text`` must have a bounded lifetime (#106369). |
| `test_ws_surrogate_send.py` | Lone UTF-16 surrogates must not tear down the Desktop WebSocket (#97288). |

## `tests/verify/`

| File | What it does |
|---|---|
| `test_environment_and_runner.py` | Tests for the verify environment manifest and the smoke runner. |
| `test_ledger_and_nudge_integration.py` | Integration of the verify subsystem with the existing verification stack. |
| `test_recipes.py` | Tests for agent/verify/recipes.py — static run-recipe detection. |
| `test_verify_cmd.py` | Tests for the ``hermes verify`` CLI command implementation. |

## `tests/website/`

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `test_catalog_rules_mirror.py` | The catalog submission guide mirrors the canonical admission rules word for word. |
| `test_check_doc_links.py` | Tests for website/scripts/check_doc_links.py. |
| `test_extract_plugins.py` | Tests for website/scripts/extract-plugins.py. |
| `test_extract_skills.py` | Tests for website/scripts/extract-skills.py helpers. |
| `test_fetch_plugin_stars.py` | fetch-plugin-stars.py: plugin-catalog star counts, GitHub consulted only from the scheduled run. |
| `test_generate_llms_txt.py` | `llms.txt` is how an LLM learns what Hermes can do. |
| `test_generate_skill_docs.py` | Tests for website/scripts/generate-skill-docs.py. |
