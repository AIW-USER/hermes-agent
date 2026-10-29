# File reference: `agent`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | agent/ — AIAgent, turn loop, prompt, compression |
| `__init__.py` | Agent internals extracted from run_agent.py so it stays focused on AIAgent. |
| `account_usage.py` | Defines `_utc_now`, `AccountUsageWindow`, `AccountUsageSnapshot`, `_snapshot`, `_title_case_slug`, `_parse_dt` … |
| `account_usage_cache.py` | What ``model.options`` knows about subscription usage without waiting on the network. |
| `acp_client.py` | Generic ACP (Agent Client Protocol) stdio client behind a minimal OpenAI-client facade. |
| `acp_openai_bridge.py` | OpenAI-shape bridge shared by Hermes' ACP clients. |
| `activity_tracking.py` | Turn-liveness activity tracking for ``AIAgent`` (gateway watchdog + session activity persistence). |
| `agent_init.py` | Implementation of :meth:`AIAgent.__init__` as ``init_agent(agent, ...)``. |
| `agent_init_compression_notice.py` | Init-time compression banner and the once-per-profile Codex gpt-5.x autoraise notice. |
| `agent_init_fallback.py` | Init-time fallback chain: entry normalization, chain setup, and the fallback's api_mode. |
| `agent_init_memory_provider.py` | Resolve the configured memory provider at agent init, telling the user once why it will not run. |
| `agent_init_ollama.py` | Init-time local-server (Ollama) num_ctx detection and the compressor clamp to it. |
| `agent_init_params.py` | Names of the ``AIAgent`` constructor params that ``init_agent`` copies onto the agent. |
| `agent_runtime_helpers.py` | Assorted AIAgent runtime helpers (message repair/sanitization, credential recovery, primary runtime restore, prompt-cache policy, client construction, model switching, tool invocation). Each function takes the parent ``… |
| `agent_runtime_helpers_dead_connections.py` | Pre-turn dead-connection sweep over an agent's OpenAI client pools (primary + cached request client). Sibling of ``agent.agent_runtime_helpers``, which owns the pool-socket walk. |
| `agent_runtime_helpers_placeholders.py` | Interrupt placeholder wording substituted into empty non-final wire rows. |
| `anthropic_adapter.py` | Anthropic Messages API adapter: client construction + the Messages call for Hermes's OpenAI-style internals. Auth: Console API keys (``sk-ant-api*``/``-usr*``/``-svc*``/``-admin*``) -> x-api-key; OAuth setup-tokens (``s… |
| `anthropic_credentials.py` | Anthropic credential sources, OAuth flows, and token resolution. |
| `anthropic_endpoints.py` | Endpoint-family detection for Anthropic-compatible base URLs. |
| `anthropic_message_convert.py` | OpenAI-style -> Anthropic Messages API request conversion: model-id normalization, tool schemas, and the message list (content blocks, thinking blocks and their signatures, tool_use/tool_result pairing, cache_control pl… |
| `anthropic_thinking_policy.py` | Shared Anthropic prior-turn thinking retention policy. |
| `anthropic_thinking_replay.py` | Durable request-local suppression for Anthropic thinking rejected by signature validation. |
| `api_error_summary.py` | Provider API error summarising for ``AIAgent``. |
| `api_request_hooks.py` | Lifecycle-hook payloads for ``AIAgent`` API requests. |
| `async_utils.py` | Async/sync bridging helpers. |
| `aux_accounting.py` | Ambient session-accounting context for auxiliary LLM calls. |
| `auxiliary_async_rebuild.py` | Carry a sync OpenAI client's credential and configured headers onto its async rebuild. |
| `auxiliary_call_outcome.py` | How one auxiliary logical call ended, for its Relay ``hermes.logical_llm_call`` scope. |
| `auxiliary_client.py` | Shared auxiliary client router for side tasks (compression, search, vision, ...). |
| `auxiliary_client_registry.py` | ``auth_type`` dispatch table for the auxiliary registry branch. |
| `auxiliary_codex_response.py` | Codex Responses → chat.completions normalization for auxiliary callers. |
| `auxiliary_fallback_recovery.py` | Parameter-rejection recovery for auxiliary fallback candidates. |
| `auxiliary_health.py` | Endpoint identity for auxiliary custom-provider health checks. |
| `auxiliary_hooks.py` | Plugin events for auxiliary LLM calls (#79733). |
| `auxiliary_key_rotation.py` | Rotate the published auxiliary main-runtime key after a credential refresh. |
| `auxiliary_local_runtime.py` | Managed llama.cpp endpoint for auxiliary and fallback client resolution. |
| `auxiliary_managed_local.py` | Which endpoint is the llama-server this Hermes manages (sibling of ``auxiliary_client``). |
| `auxiliary_plugin_oauth.py` | Auxiliary client for OAuth-shaped model-provider plugins (``auth_type`` oauth_external / oauth_device_code). |
| `auxiliary_reasoning_floor.py` | Reasoning floor for auxiliary requests: when a route refuses to switch reasoning OFF, step it UP. |
| `auxiliary_stream_watchdog.py` | No-progress watchdog for streamed chat-completions auxiliary calls (#100501). |
| `auxiliary_structured_output.py` | Structured-output (``response_format``) capability for auxiliary requests. |
| `auxiliary_task_config.py` | Read-time resolution of an ``auxiliary.<task>`` config block. |
| `auxiliary_unavailable.py` | Why an auxiliary client could not be built — and the Nous credential failure behind it. |
| `auxiliary_wire.py` | Message hygiene at the resolved auxiliary client boundary. |
| `azure_identity_adapter.py` | Microsoft Entra ID adapter for Microsoft Foundry. |
| `backend_identity.py` | Single owner for backend identity and failure-scoped skip decisions. |
| `background_review.py` | Background memory/skill review — fork the agent to evaluate the turn. After every turn ``AIAgent.run_conversation`` may spawn a daemon thread that replays the conversation snapshot in a forked :class:`AIAgent` and asks… |
| `battery.py` | System-battery read-out for the CLI/TUI status bar. |
| `bedrock_adapter.py` | AWS Bedrock Converse API adapter (boto3, optional dependency). |
| `billing_links.py` | Provider-agnostic billing/credit recovery links for billing-classified failures. |
| `billing_usage.py` | Shared dollar-denominated usage model for the ``/usage`` and ``/subscription`` bars. |
| `billing_view.py` | Surface-agnostic core for the Remote Spending screens (CLI ``_show_billing``, TUI JSON-RPC). |
| `bounded_response.py` | Bounded reads of HTTP error response bodies. |
| `browser_page_backend.py` | Browser page backend ABC: a browser that owns its pages outside Hermes's CDP session. |
| `browser_page_registry.py` | Browser page backends registered by plugins via :meth:`PluginContext.register_browser_page_backend`, consumed by ``tools.browser_vault_tool``. The backend holding the task's live page wins over the CDP session; with non… |
| `browser_provider.py` | Browser Provider ABC: pluggable cloud browser backends (Browserbase, Browser Use, Firecrawl, …). |
| `browser_registry.py` | Browser provider registry: cloud browser backends registered by plugins via :meth:`PluginContext.register_browser_provider`, consumed by ``tools.browser_session_cloud.get_cloud_provider``. |
| `chat_completion_headers.py` | Non-streaming chat completions that still feed response headers to the credits capture. |
| `chat_completion_helpers.py` | API-call helpers extracted from :class:`AIAgent`: non-streaming and streaming request drivers, request kwargs builder, assistant-message materializer, provider-fallback activator, max-iterations handler, per-turn resour… |
| `chat_completion_helpers_relay.py` | Relay-side accumulator for the chat_completions streaming wire. |
| `chat_completion_helpers_tool_calls.py` | Streamed tool-call delta assembly for the chat-completions stream (and Relay's accumulator). |
| `chat_completion_local.py` | Chat completions against llama-server (sibling of ``chat_completion_helpers``). |
| `chat_completion_nonstream.py` | Request-local worker lifecycle, watchdog polling, and wait status. |
| `chat_completion_stream_monitor.py` | Display and heartbeat phase of the request-local streaming monitor. |
| `chat_completion_wait_notice.py` | Operator-facing wait notice for long provider silences (#92550). |
| `client_lifecycle.py` | Tool-resource teardown, wire-client lifecycle and credential refresh for ``AIAgent``. |
| `codex_headers.py` | Codex request identity helpers shared by agent client builders. |
| `codex_responses_adapter.py` | Codex Responses API adapter: stateless format conversion and normalization for the OpenAI Responses API (OpenAI Codex, xAI and other compatible endpoints; per-endpoint quirks come from the provider profile that claims t… |
| `codex_runtime.py` | Codex API runtime — App Server and Responses-API streaming paths. Every entry point takes the parent AIAgent first: ``run_codex_app_server_turn`` drives one ``codex app-server`` subprocess turn; ``run_codex_stream`` run… |
| `codex_runtime_history_seed.py` | Render Hermes' prior transcript as a one-shot seed for a FRESH codex app-server thread. |
| `codex_service_tiers.py` | Account-scoped speed metadata from the existing authenticated Codex catalogue. |
| `coding_context.py` | Coding-context awareness: the single place that decides "are we coding?". |
| `command_token_source.py` | Mint a provider API key by running a command (``key_cmd``). |
| `compaction_display.py` | Client-facing projection helpers for model-only compaction carriers. |
| `compaction_events.py` | Content-free ``hermes.compaction`` v1 records for every history rewrite, and their fan-out. |
| `compression_automation.py` | Carry automation at a compression boundary without opening worker storage. |
| `compression_facade.py` | Host-side ``AIAgent._compress_context`` wrapper. |
| `compression_marker.py` | The model-visible compression/elision marker and its matcher. |
| `context_breakdown.py` | Live session context-window breakdown for UI surfaces. |
| `context_compressor.py` | Automatic context window compression: a cheap auxiliary model summarizes middle turns while head and tail are protected (iterative summaries, token-budget tail, tool-output pruning first, scaled budgets). |
| `context_compressor_prellm.py` | Pre-LLM summary skips for ContextCompressor: compact deterministically without calling a summary model. |
| `context_compressor_prune.py` | The proactive tool-result prune: deterministic passes plus the in-place row commit (#124102). |
| `context_compressor_retry.py` | Lossless /retry text extraction for a user-originated turn's live content. |
| `context_compressor_summary.py` | Summary-hook dispatch and cancellation rollback for context compression. |
| `context_compressor_tail.py` | Lean-mode stale-tail demotion for ContextCompressor (old tail tool results become one-line recovery stubs), and the Skill Safety Rule the compaction handoff carries whenever its transcript holds a skill prune marker. |
| `context_compressor_telemetry.py` | Content-free per-attempt compression telemetry for ContextCompressor. |
| `context_compressor_window.py` | Compaction window planning for ContextCompressor: the head/middle/tail boundaries that compress() and the opt-in prepared-compaction pass (agent/prepared_compaction.py) both plan, and the splice of a prepared summary in… |
| `context_engine.py` | Abstract base class for pluggable context engines. |
| `context_file_sources.py` | Per-file manifest of the context/instruction files behind the ``/context`` "Rules" figure. |
| `context_pin.py` | ``model.context_length`` is an explicit pin: it wins over provider metadata (#66168). |
| `context_references.py` | @-reference expansion (``@file:``, ``@folder:``, ``@diff``, ``@git:``, ``@url:`` + plugin prefixes). |
| `conversation_compression.py` | Context compression: feasibility probe, warning replay, compress, image fix. |
| `conversation_compression_archive.py` | Exact held-row coverage for an in-place archive. |
| `conversation_compression_checkpoint.py` | Fail-closed pre-compress checkpoint gate for ``agent.conversation_compression``. |
| `conversation_compression_codex.py` | Codex app-server compaction: the route ``compress_context`` takes for Codex-owned threads. |
| `conversation_compression_deadline.py` | Compression time limits: the configured idle and total limits, and the fence deadline shared live with the summary stream (sibling of ``conversation_compression``). |
| `conversation_compression_manual.py` | Manual ``/compress`` core shared by the CLI, gateway, TUI and ACP surfaces. |
| `conversation_compression_reply_anchor.py` | Keep the just-delivered assistant reply live across a compaction commit (#118900). |
| `conversation_compression_telemetry.py` | Content-free per-attempt compression telemetry (attempt log line, Relay mark, shared metric). |
| `conversation_compression_watermark.py` | The held-row watermark cap and its lease-less staleness gate (#124102). |
| `conversation_loop.py` | The agent conversation loop — extracted from ``run_agent.AIAgent``. |
| `copilot_acp_client.py` | Deprecated alias module: use :class:`agent.acp_client.ACPClient`. |
| `credential_persistence.py` | Credential-pool disk-boundary sanitization: strip raw secrets from *borrowed* pool entries before they reach ``auth.json``. Deliberately free of ``hermes_cli.auth`` imports so the pool model and the auth-store write bou… |
| `credential_pool.py` | Persistent multi-credential pool for same-provider failover. |
| `credential_pool_admin.py` | Locked credential-pool administration and target resolution. |
| `credential_pool_model_cooldowns.py` | Model-scoped rate-limit cooldowns for pooled credentials. |
| `credential_pool_plugin.py` | Plugin-provider refresh support for the credential pool (#116408). |
| `credential_pool_timestamps.py` | Timestamp parsing shared by credential-pool status, refresh, and cooldown bookkeeping. |
| `credential_source.py` | Name a callable API key's credential source without calling it. |
| `credential_sources.py` | Unified removal contract for every credential source Hermes reads from. |
| `credits_tracker.py` | Nous credits: parse ``x-nous-credits-*`` / ``x-nous-tool-pool-*`` response headers into a validated CreditsState (depletion = paid_access, subscription-cap used_fraction, warn-once schema-version gating) and drive the n… |
| `curator.py` | Curator — background skill maintenance orchestrator. |
| `curator_backup.py` | Curator snapshot + rollback. Before any mutating curator pass, ``~/.hermes/skills/`` is tar.gz'd under ``~/.hermes/skills/.curator_backups/<utc-iso>/`` with a ``manifest.json``. Rollback first snapshots the CURRENT tree… |
| `custom_entry_pool.py` | Credential ownership for ``providers:`` entries whose pool slug is also a built-in's pool id. |
| `deadline.py` | Unified deadline layer — one bounded-execution primitive, one timeout resolver (#85125). |
| `delegation_backends.py` | Which delegation backend Hermes uses: the public API behind a ``/delegation`` command. |
| `delegation_context.py` | Context-local state for delegate_task child execution. |
| `delegation_provider.py` | Delegation Provider ABC. |
| `delegation_registry.py` | Delegation provider registry. |
| `display.py` | CLI presentation -- spinner, kawaii faces, tool preview formatting. |
| `empty_response_guard.py` | Deterministic-empty detection and cost-aware retry budgets. |
| `error_classifier.py` | API error classification for smart failover and recovery. |
| `error_surface.py` | Structured error-surface descriptors for UI clients (Desktop/TUI). |
| `errors.py` | Defines `EmptyStreamError`, `MoAPresetNotFoundError` |
| `estop.py` | Global emergency stop (ESTOP) — a resumable pause for NEW work only. |
| `fallback_cooldown.py` | Primary rate-limit cooldown arming and per-session model rejection markers, shared by the fallback walk (chat_completion_helpers) and restore_primary_runtime (agent_runtime_helpers). |
| `fast_mode.py` | Bounded fast-mode windows (``/fast auto`` and ``/fast cold``). |
| `file_safety.py` | Shared file safety rules used by both tools and ACP shims. |
| `gemini_long_decode.py` | Gemini long decode: one response spread over several generateContent hops. |
| `gemini_native_adapter.py` | OpenAI-compatible facade over Google AI Studio's native Gemini API: the ``gemini`` provider keeps ``api_mode='chat_completions'`` so the agent loop stays OpenAI-shaped, and this shim converts ``messages[]``/``tools[]``… |
| `gemini_schema.py` | Tool-schema preparation for Gemini's native API. |
| `history_commentary.py` | Display-only Codex commentary projection shared by REST and gateway history. |
| `i18n.py` | Lightweight i18n for Hermes' static user-facing strings (approval prompts, gateway replies, CLI, tips). |
| `i18n_languages.py` | Language identity for the bundled locales — endonym and script direction — plus the picker list. |
| `i18n_layers.py` | Catalog layers above the bundled ``locales/`` tree: plugin language packs and the user overlay. |
| `image_eviction_policy.py` | Send-path image eviction policy shared by both stateless outbound passes. |
| `image_gen_provider.py` | Image generation provider ABC. |
| `image_gen_registry.py` | Image generation provider registry. |
| `image_replay.py` | Re-attach user images on turns whose history was rebuilt from the session DB. |
| `image_routing.py` | Routing helpers for inbound user-attached images. |
| `image_token_cost.py` | Per-image token cost learned from the provider's own usage, never from a vendor formula. |
| `inline_tool_executors.py` | Agent-level ("inline") tool executors shared by the sequential and concurrent tool paths. |
| `insights.py` | Session Insights Engine: aggregates the SQLite state DB into usage insights (tokens, cost estimates, tool/skill usage, activity, model/platform breakdowns). ``InsightsEngine(db).generate(days=30)`` → ``format_terminal(r… |
| `interrupt_compat.py` | Compatibility helper for explicit agent stop producers. |
| `interrupt_control.py` | Interrupt / steer / redirect control surface for ``AIAgent``. |
| `interrupt_scope.py` | Host-owned cancellation for agents created deep inside synchronous work. |
| `iteration_budget.py` | Per-agent iteration budget — thread-safe consume/refund counter. |
| `jiter_preload.py` | Best-effort early import of the OpenAI SDK's native streaming parser: on some Windows installs ``jiter``'s native extension imports fine from the venv but fails when first imported inside the threaded streaming path. Lo… |
| `kanban_stop.py` | Turn-end guard for kanban workers, which must end with a terminal board tool that hands the card to whoever owns it next (``kanban_complete``, ``kanban_block``, ``kanban_request_review``, ``kanban_request_changes``). So… |
| `kanban_turn_recovery.py` | In-place recovery for kanban worker turns that die on a retryable failure. |
| `lazy_forward.py` | Lazy forwarding helpers shared by the AIAgent façade and its mixins. |
| `learn_prompt.py` | ``/learn`` — build the ONE prompt that turns whatever the user described (code dir, doc URL, "what we just did", pasted notes) into a reusable skill. The live agent gathers sources with its existing tools and authors th… |
| `learning_graph.py` | Assemble the "learning made visible" graph for desktop. |
| `learning_graph_render.py` | Terminal renderer for the learning timeline (learned skills + memories): the desktop starmap's data (``apps/desktop/src/app/starmap``) drawn as a timeline bar chart (date rows, skill/memory bars colored by dominant cate… |
| `learning_mutations.py` | User-initiated edit/delete for journey nodes (learned skills + memories). |
| `legacy_cli.py` | Argument layer for the legacy ``hermes-agent`` runner (``run_agent.main``). |
| `lmstudio_reasoning.py` | LM Studio reasoning-effort resolution (used by the lmstudio provider profile). LM Studio publishes per-model ``capabilities.reasoning.allowed_options`` (``["off","on"]`` for toggle models, ``["off","minimal","low"]`` fo… |
| `local_prompt_progress.py` | Prompt-reading progress from llama-server. |
| `lsp/__init__.py` | Language Server Protocol (LSP) integration for Hermes Agent. |
| `lsp/cli.py` | ``hermes lsp`` CLI subcommand: status / list / install / install-all / restart / which. |
| `lsp/client.py` | Async LSP client over stdin/stdout — one per ``(server, workspace_root)``. |
| `lsp/deferred.py` | LSP diagnostics for a write, delivered after the write's tool result instead of inside it. |
| `lsp/edit_check.py` | Post-write LSP check that never holds the write. |
| `lsp/eventlog.py` | Structured logging with steady-state silence for the LSP layer. |
| `lsp/install.py` | Auto-installation of LSP server binaries. |
| `lsp/manager.py` | Service-level orchestration for LSP clients. |
| `lsp/protocol.py` | Minimal LSP JSON-RPC 2.0 framer over async streams. |
| `lsp/range_shift.py` | Diff-aware line-shift map for cross-edit LSP delta filtering. |
| `lsp/reporter.py` | Format LSP diagnostics for inclusion in tool output. |
| `lsp/servers.py` | Server registry — per-language LSP server definitions. |
| `lsp/sync_diagnostics.py` | Synchronous diagnostics requests, for servers that answer "what is wrong with this file now" directly. |
| `lsp/workspace.py` | Workspace and project-root resolution for LSP. |
| `managed_worker.py` | Private exec entry. No agent/config imports before adopted process authority. |
| `manual_compression_feedback.py` | User-facing summaries for manual compression commands. |
| `markdown_tables.py` | CJK/wide-character-aware re-alignment of model-emitted markdown tables. |
| `memory_caller_scope.py` | Which profile a memory-provider call or hook belongs to (#140058). |
| `memory_context.py` | Memory-context fencing: how recalled memory is wrapped for the model and kept out of output. |
| `memory_manager.py` | MemoryManager — fans the agent's memory hooks out to registered providers. |
| `memory_manager_tools.py` | Memory-provider tool-schema plumbing: the gate that decides whether external memory-provider tools are exposed on an agent's tool surface, and the injection of their schemas. |
| `memory_provider.py` | Abstract base class for pluggable memory providers. |
| `message_content.py` | Defines `_field`, `_text_from_part`, `flatten_message_text` |
| `message_metadata.py` | Internal metadata attached to durable conversation messages. |
| `message_sanitization.py` | Message and tool-payload sanitization helpers (pure; documented in-place mutation). |
| `micro_compaction.py` | Micro-compaction mixin for ContextCompressor. |
| `moa_alternation.py` | Reactive same-role merge for the MoA aggregator request (#112358, last atom). |
| `moa_loop.py` | Mixture-of-Agents runtime helpers for /moa turns. |
| `moa_trace.py` | Full MoA turn trace persistence (opt-in via config ``moa.save_traces``). |
| `model_metadata.py` | Model metadata, context lengths, and token estimation utilities. |
| `model_metadata_cache.py` | ``context_length_cache.yaml`` writes and their cross-process serialization. |
| `model_metadata_http.py` | Model probes share chat's TLS policy, with scoped redirect credentials. |
| `model_metadata_llamacpp.py` | llama.cpp context-window probes (sibling of ``model_metadata``). |
| `model_metadata_token_memo.py` | Release a closed conversation's entries from the per-message token-estimate memo. |
| `models_dev.py` | Models.dev registry integration — primary database for providers and models. |
| `monitoring/__init__.py` | Hermes gateway monitoring: service health + redacted diagnostics over OTLP. |
| `monitoring/cron_health.py` | Content-free cron service-health and execution telemetry projection. |
| `monitoring/emitter.py` | Monitoring emitter: fire-and-forget queue + background dispatcher — the single seam between producers (gateway status hooks, diagnostic log handler) and consumers (OTLP streamers). Hot-path invariant: ``emit()`` MUST re… |
| `monitoring/events.py` | Typed gateway monitoring events. |
| `monitoring/gateway_health.py` | Gateway health and diagnostics signal producer. |
| `monitoring/gateway_health_export.py` | Gateway Health & Diagnostics OTLP export runtime. |
| `monitoring/otlp_exporter.py` | Export monitoring events to an OpenTelemetry Collector over OTLP/HTTP. |
| `monitoring/policy.py` | Install identity for gateway monitoring. |
| `monitoring/redaction.py` | Redaction applied to monitoring data before egress. |
| `moonshot_schema.py` | Translate OpenAI-style tool schemas to Moonshot's (Kimi) stricter JSON Schema subset. |
| `native_compaction.py` | Native OpenAI Responses server-side compaction on supported OpenAI routes. |
| `notification_presentation.py` | Turn-local presentation of diagnostic-only wakes; execution and controls stay live. |
| `nous_rate_guard.py` | Cross-session rate limit guard for Nous Portal. |
| `nous_wire.py` | Nous Portal ``anthropic/*`` wire selection when ``nous.anthropic_wire`` is ``auto``. |
| `onboarding.py` | Contextual first-touch onboarding hints, and the entry points of desktop first-run onboarding. |
| `onboarding_facts.py` | The safe facts (class A) a first-run onboarding is built from, read once when the run starts. |
| `onboarding_first_tasks.py` | The first-task catalog of onboarding's build beat: what the model may put on the build card. |
| `onboarding_flow.py` | First-run onboarding as data: the beats, the run record, and how each event moves the record. |
| `onboarding_record.py` | Where a first-run onboarding run lives: one ``onboarding_run`` key in the session's ``sessions.model_config`` (no schema change; a compression rotation carries it, see ``hermes_state_compression._CONVERSATION_MODEL_CONF… |
| `onboarding_session.py` | The onboarding chat's per-session pieces, shared by every runtime that hosts it (the session authority's local turns and the old sidecar): the ``onboarding`` toolset fold-in, the scripted opening and the per-turn note.… |
| `onboarding_text.py` | The words of first-run onboarding: the scripted greeting, the opening prompt, and the reminder that rides on every ``setup_beat`` result. Pure; ``reminder(key, record, facts)`` renders the key ``agent/onboarding_flow.py… |
| `oneshot.py` | Shared one-off LLM requests for non-conversational helpers. |
| `oneshot_footprint.py` | What a finite one-shot session (``hermes chat -q`` / ``--oneshot``, ``hermes -z``) does NOT do. |
| `opencode_affinity.py` | Conversation-affinity request headers for session-aware relays and proxies. |
| `outbound_webhooks.py` | Outbound webhooks: ``hooks.outbound`` entries (url, events, secret_env\|secret, matcher for pre/post_tool_call, timeout clamped to [1, 60], name) -> notify-only callbacks on the plugin hook manager, so every ``invoke_ho… |
| `periodic_scheduler.py` | One process-wide timer thread for periodic maintenance callbacks. |
| `persisted_turn_receipt.py` | ``message.complete.persisted_turn``: the committed row addresses of the agent's current turn. |
| `pet/__init__.py` | Petdex pet engine — shared core for the CLI, TUI, and desktop surfaces. |
| `pet/constants.py` | Pet sprite geometry + animation-state taxonomy. |
| `pet/generate/__init__.py` | Pet generation — base-draft → hatch pipeline. |
| `pet/generate/atlas.py` | Deterministic spritesheet assembly — generated row strips → Hermes atlas. |
| `pet/generate/imagegen.py` | Thin image-generation layer for pet sprites. |
| `pet/generate/orchestrate.py` | Pet generation orchestration — the base-draft → hatch flow. |
| `pet/generate/prompts.py` | Prompt builders for pet generation. |
| `pet/manifest.py` | Fetch the public petdex manifest. |
| `pet/render.py` | Decode a pet spritesheet and encode frames for a terminal. |
| `pet/state.py` | Map agent activity → a :class:`PetState`. |
| `pet/store.py` | On-disk pet store — install / list / resolve pets. |
| `plan_limits.py` | Usage-window plans: what a limit blocks, and what to offer instead. |
| `plan_prompt.py` | ``/plan`` — build the plan-mode prompt: a saved markdown implementation plan, no execution. |
| `plan_snapshot_sync.py` | Keep the cached plan snapshot in step with what the gateway says on each reply. |
| `plugin_live_notes.py` | Tell an open chat about a plugin that went live while it runs, once, without breaking its cache. |
| `plugin_llm.py` | Plugin LLM facade — host-owned LLM access for trusted plugins (``ctx.llm``). |
| `plugin_stream_hooks.py` | Asynchronous per-consumer plugin observers for streaming LLM output. |
| `portal_tags.py` | Centralized Nous Portal request tags. |
| `prepared_compaction.py` | Opt-in prepared compaction (``compression.prepare_ahead``, default off). |
| `primary_runtime_snapshot.py` | The ``_primary_runtime`` snapshot: the route a fallback turn restores on the next turn. |
| `process_bootstrap.py` | Process-level bootstrap helpers for ``run_agent``. |
| `prompt_builder.py` | System prompt assembly -- identity, platform hints, skills index, context files. |
| `prompt_cache_boundary.py` | Builder-declared stable prefixes for Anthropic prompt caching. |
| `prompt_cache_scope.py` | Rotation-stable logical cache scope for prompt_cache_key derivation. |
| `prompt_caching.py` | Anthropic prompt caching strategy — pure functions, no AIAgent dependency. |
| `prompt_refresh.py` | Adopt an operator's prompt refresh request on a continuing session's next turn. |
| `provider_base.py` | Shared base classes for the pluggable-backend provider ABCs. |
| `provider_media.py` | ``$HERMES_HOME/cache/<kind>/`` materialisation helpers for the image/video generation provider ABCs. |
| `provider_projection.py` | Fold an agent-as-provider's own activity back into Hermes' turn state. |
| `provider_registry.py` | Shared engine behind the ``agent.*_registry`` provider registries. |
| `provider_route_hooks.py` | Ask provider profiles about an endpoint: the named provider first, then the profile serving the host. |
| `proxy_bypass.py` | NO_PROXY matching shared by the LLM transport (``agent/process_bootstrap.py``) and the gateway platform adapters (``gateway/platforms/base.py``). |
| `proxy_sources/__init__.py` | Egress proxy integrations — see :mod:`agent.proxy_sources.iron_proxy` (ironsh/iron-proxy wrapper). |
| `proxy_sources/iron_proxy.py` | iron-proxy (``ironsh/iron-proxy``) integration for credential-injecting egress control. |
| `rate_limit_credits.py` | Rate-limit / credits header capture and low-credit notices for ``AIAgent``. |
| `rate_limit_tracker.py` | Rate limit tracking for inference API responses. |
| `reactions.py` | Token-free (regex) detection of user *reactions* to the agent. |
| `reasoning_carriers.py` | Provider-native assistant reasoning carriers outside the standard reasoning fields. |
| `reasoning_effort.py` | Canonical reasoning-effort vocabulary and wire clamping. |
| `reasoning_params.py` | Provider reasoning-parameter policy for ``AIAgent``. |
| `reasoning_promotion.py` | Whether a reasoning-only clean stop may be promoted to the visible answer. |
| `reasoning_summaries.py` | Boundary repair for providers that stream reasoning as discrete summary parts. |
| `reasoning_timeouts.py` | Per-model stale-timeout FLOOR for known reasoning models. |
| `redact.py` | Regex-based secret redaction for logs and tool output. |
| `relay_compaction.py` | Emit ``hermes.compaction`` records as NeMo Relay marks on the owning session's scope stack. |
| `relay_cwd.py` | Resolve logical working directories for Hermes-owned Relay scopes. |
| `relay_llm.py` | Core NeMo Relay adapters for physical Hermes provider attempts. |
| `relay_runtime.py` | Profile-scoped NeMo Relay runtimes owned by the Hermes agent core. |
| `relay_tools.py` | Core NeMo Relay adapter for Hermes tool execution. |
| `repetition_guard.py` | Cheap content-sanity checks for model output, completed or still streaming. |
| `replay_cleanup.py` | Replay-history sanitization shared by EVERY resume surface (messaging gateway, TUI/WebUI gateway). |
| `retry_utils.py` | Retry utilities — jittered backoff for decorrelated retries. |
| `review_engine.py` | Shared engine for the /review command — every surface calls this. |
| `review_idle_queue.py` | Idle deferral for background reviews on the managed local runtime. |
| `route_binding.py` | Bind a provider route onto a live agent in place, and put the primary route back. |
| `runtime_cwd.py` | Single source of truth for the agent working directory. |
| `runtime_self_protection.py` | The running Hermes runtime's own interpreter/venv is not agent-deletable. |
| `runtime_session_child.py` | A delegated child's store inside a worker: owner-reserved, never self-registered (#141793). |
| `runtime_session_compression.py` | Concrete worker compression APIs; scope and receipts stay in RuntimeSessionStore. |
| `runtime_session_lifecycle.py` | Explicit lifecycle methods for the assignment-bound worker store. |
| `runtime_session_store.py` | Explicit worker persistence facade; never opens the canonical SQLite store. |
| `safe_worker_policy.py` | Private bootstrap policy for admission-owned workers: the frozen session config every config reader returns, plus (troubleshooting workers only) the safe/ignore-user-config bypass. |
| `sdk_transform_bypass.py` | Route bulk request payloads around the OpenAI SDK's request transform (#93650). |
| `search_policy.py` | Shared directory pruning policy for broad recursive scans. |
| `secret_scope.py` | Profile-scoped credential resolution for multi-profile gateway multiplexing. |
| `secret_sources/__init__.py` | External secret source integrations. |
| `secret_sources/_cache.py` | Shared cache substrate for external secret-source backends. |
| `secret_sources/base.py` | Secret-source contract: the ABC every secret backend implements. |
| `secret_sources/bitwarden.py` | Bitwarden Secrets Manager (`bws` CLI) integration. |
| `secret_sources/command.py` | ``command`` secret source — resolve secrets via a user-configured helper. |
| `secret_sources/onepassword.py` | 1Password (`op` CLI) secret source. |
| `secret_sources/registry.py` | Secret-source registry + apply orchestrator. |
| `served_model.py` | Per-response *served model* capture for routing proxies (#54864). |
| `session_activity.py` | Shared session activity observation contract: timestamp + bounded description/provenance, observation only (notification, timeout, kill and retry policy live elsewhere). Provenance is a small closed enum of *noun* sourc… |
| `session_client_env.py` | A local session's client environment: the allowlisted values a shell-launched client (classic CLI, Ink TUI) sends as ``session.create``'s ``client_env``. Main's ``hermes`` process read them from its own shell; the one g… |
| `session_persistence.py` | Durable transcript persistence for ``AIAgent`` (mixin; MRO-resolved from ``run_agent``): SQLite flush with intrinsic ``_DB_PERSISTED_MARKER`` dedup, ephemeral-scaffolding filtering, explicit trajectory export. |
| `session_source.py` | Session source vocabulary: the ``source`` label a session row carries, and which sources have a person reading the turn as it runs. A leaf (its one import is the stdlib-only session context), so the ``run_agent`` facade… |
| `shell_hooks.py` | Shell-script hooks bridge: ``hooks:`` config → first-use consent per ``(event, command)`` → callbacks on the plugin hook manager, so every ``invoke_hook()`` site dispatches to the scripts. Wire: stdin JSON ``{hook_event… |
| `side_question.py` | Context-aware side questions (``/btw``): answer a question ABOUT the conversation without touching it (no synthetic turns, no role-alternation risk, no prompt-cache invalidation). |
| `side_question_lease.py` | Turn leases for plugin side questions (``ctx.side_question``). |
| `side_question_request.py` | One text-only request on a detached cache-parity fork of the live session agent, for plugins (``ctx.side_question``). |
| `skill_bundles.py` | Skill bundles — aliases that load multiple skills under one slash command. |
| `skill_commands.py` | Shared slash command helpers for skills (CLI and gateway both invoke /skill-name). |
| `skill_preprocessing.py` | Shared SKILL.md preprocessing helpers: ``${HERMES_*}`` template tokens and inline ``!`cmd``` shell expansion. |
| `skill_utils.py` | Lightweight skill metadata utilities shared by prompt_builder and skills_tool. Import-light by design: no tool registry, CLI config, or provider resolution. |
| `skills_index_delta.py` | Skills that change mid-conversation reach the model without a prompt rebuild. |
| `sleep_clock.py` | Clocks that stop while the computer sleeps. |
| `ssl_verify.py` | TLS trust for Hermes. One authority, one trust source. |
| `status_output.py` | User-facing status / warning / notice plumbing for ``AIAgent``. |
| `stream_delivery.py` | Streaming / interim-message delivery for ``AIAgent``. |
| `stream_diag.py` | Stream diagnostics — per-attempt counters, exception chains, retry logging. |
| `stream_single_writer.py` | Best-effort accessors for the single-writer stream fence. |
| `subagent_lifecycle.py` | Public, plugin-safe lifecycle API for delegated Hermes subagents: immutable contracts, not ``AIAgent`` objects. Plugins obtain it via ``PluginContext.subagent_lifecycle``. |
| `subdirectory_hints.py` | Progressive subdirectory hint discovery: as the agent navigates into subdirectories via tool calls, load project context files (AGENTS.md, CLAUDE.md, .cursorrules) from them and append to the tool result — context arriv… |
| `subscription_view.py` | Surface-agnostic core for the ``/subscription`` TUI screen. |
| `surface_switch.py` | Surface switch without a prompt rebuild (#104414). |
| `system_prompt.py` | System-prompt assembly for :class:`AIAgent`. |
| `terminal_approval_batch.py` | Prepare desktop terminal consent without running shells ahead of their turn. |
| `terminal_env_provider.py` | Terminal Environment Provider ABC. |
| `terminal_env_registry.py` | Terminal Environment Registry. |
| `think_scrubber.py` | Stateful scrubber for reasoning/thinking blocks in streamed assistant text. |
| `thinking_timeout_guidance.py` | Thinking-timeout detection and user-facing guidance for reasoning models. |
| `thread_scoped_output.py` | Thread-scoped stdout/stderr silencing for background worker threads. |
| `title_generator.py` | Auto-generate short session titles from the user's opening message. |
| `tool_call_batches.py` | Normalize local bridge batches before persistence and per-tool execution. |
| `tool_dispatch_helpers.py` | Tool-dispatch helpers — parallelism gating, multimodal envelopes, mutation tracking. |
| `tool_executor.py` | Tool-call execution: sequential and concurrent dispatch, extracted from AIAgent. |
| `tool_guardrails.py` | Pure tool-call loop guardrail primitives. |
| `tool_progress_relay.py` | Live progress from inside a running tool call (MCP ``notifications/progress``) onto the agent's ``tool_progress_callback`` as ``tool.progress`` events. |
| `tool_result_classification.py` | Shared helpers for classifying tool result payloads. |
| `trace_upload.py` | Upload a Hermes session transcript to Hugging Face as an agent trace, re-emitted in the **Claude Code JSONL** shape the HF Agent Trace Viewer auto-detects (https://huggingface.co/docs/hub/agent-traces). Deterministic, z… |
| `trajectory.py` | Trajectory saving + scratchpad helpers (``_convert_to_trajectory_format`` stays an AIAgent method — batch_runner.py calls it). |
| `transcript_repair.py` | Transcript repair for SessionDB batch appends: reconcile in-memory rows with committed SQLite rows (in-place sanitizer rewrites, assistant blank-row repair, concurrent-winner adoption, watermark-compaction clone lookup)… |
| `transcription_provider.py` | Transcription Provider ABC — pluggable speech-to-text backends. |
| `transcription_registry.py` | Transcription Provider Registry. |
| `transports/__init__.py` | Transport registry for provider response normalization. transport = get_transport("anthropic_messages") result = transport.normalize_response(raw_response) |
| `transports/anthropic.py` | Anthropic Messages API transport: conversion via agent/anthropic_adapter.py, normalization here. |
| `transports/base.py` | Abstract base for provider transports. A transport owns one api_mode's data path (convert_messages -> convert_tools -> build_kwargs -> normalize_response), NOT client construction, streaming, credentials, caching, inter… |
| `transports/bedrock.py` | AWS Bedrock Converse API transport. |
| `transports/chat_completions.py` | OpenAI Chat Completions transport (default api_mode for OpenAI-compatible providers). |
| `transports/codex.py` | OpenAI Responses API (Codex) transport. |
| `transports/codex_app_server.py` | Codex app-server JSON-RPC client (newline-delimited JSON-RPC 2.0 over stdio, codex 0.125+). |
| `transports/codex_app_server_session.py` | Session adapter for codex app-server runtime. |
| `transports/codex_event_projector.py` | Projects codex app-server ``item/*`` notifications into OpenAI-shaped messages. |
| `transports/hermes_tools_mcp_server.py` | Hermes-tools-as-MCP server for the codex_app_server runtime. |
| `transports/types.py` | Shared types for normalized provider responses. |
| `tts_provider.py` | Text-to-Speech Provider ABC. |
| `tts_registry.py` | TTS Provider Registry. |
| `turn_api_call.py` | The provider call for the conversation turn's retry loop: ``nous_rate_limit_guard`` (skip the attempt while another session's Nous Portal rate limit is active), ``perform_api_call`` (streaming decision, MoA prepared-req… |
| `turn_api_error.py` | API-call exception handler for the conversation turn's retry loop: pre-/post-classification recovery, interpreter-shutdown abandon, classified-error routing, overflow recovery, the non-retryable client-error exit, max-r… |
| `turn_api_request.py` | Per-attempt request assembly for the conversation turn's retry loop: re-apply the reasoning echo pad and prompt-cache decoration for the CURRENT provider (a fallback may differ from the primary), build ``api_kwargs``, r… |
| `turn_author.py` | Who wrote the user side of a turn, carried from the dispatcher into the recipient's turn. |
| `turn_context.py` | Per-turn setup for ``run_conversation`` (the turn prologue). |
| `turn_context_compaction.py` | Turn-start compaction for ``build_turn_context`` plus the small compression-attempt helpers shared with the pre-API / post-tool sites in ``turn_preflight``. |
| `turn_empty_response.py` | Empty / thinking-only final-response recovery ladder for the conversation turn loop. |
| `turn_explainers.py` | File-mutation verification footers and turn-completion explanations for ``AIAgent``. |
| `turn_facade.py` | ``AIAgent.run_conversation`` / ``chat`` façade. |
| `turn_facade_lease.py` | Durable cross-process session turn lease for ``TurnFacadeMixin.run_conversation``. |
| `turn_failure_copy.py` | User-facing copy and ``failure_reason`` stamping for terminal failed-turn results. |
| `turn_final_response.py` | No-tool-call (final text) branch of the conversation turn loop: empty/think-only recovery, intent-ack / stall-guard continuation, length-continuation joining, dropped-tool-call re-prompt, scaffolding pop, stop gates, th… |
| `turn_finalizer.py` | Post-loop turn finalization for ``run_conversation``. |
| `turn_iteration_prep.py` | Outer-iteration bookkeeping for the conversation turn loop, in call order: ``begin_iteration`` (pending redirect, interrupt / review-budget / iteration-budget exits), ``prepare_iteration`` (``agent:step`` callback, skil… |
| `turn_liveness.py` | Turn liveness watchdog: force-abort turns that stall silently. |
| `turn_loop_errors.py` | Outer-loop exception handler for the conversation turn loop: phase-aware classification (interpreter shutdown, deterministic local post-processing bug vs API-path failure), unanswered tool_call error results, and the pe… |
| `turn_overflow.py` | Overflow recovery for the conversation turn loop: 413 payload-too-large and context-length errors after ``classify_api_error``. |
| `turn_preflight.py` | Pre-API preflight compression gate and post-tool compression for the turn loop. |
| `turn_preflight_gate.py` | Pre-API pressure gate for the conversation turn loop: the Ollama runtime-context floor, the provider-overflow re-check arming, the insufficient-progress blocker (compares fully assembled requests, not raw ``messages``)… |
| `turn_recovery.py` | Recovery-branch handlers for the conversation turn's inner retry loop. |
| `turn_recovery_autorecover.py` | Bounded post-exhaustion auto-recovery ladder for a pre-delivery turn (#85426, #107307). |
| `turn_recovery_codex.py` | Codex Responses recovery rungs: stale encrypted-reasoning strip and the replay verdict reset. |
| `turn_request_assembly.py` | Per-iteration API request assembly for the conversation turn loop: build ``api_messages`` from the transcript, append MoA context, inject prefills, run the context-engine selection hook and the send-time sanitizers, can… |
| `turn_response_check.py` | Post-call response verification for the conversation turn's retry loop: stop the thinking spinner, validate the response shape (retry / eager fallback / terminal invalid-response result), derive ``finish_reason`` per ap… |
| `turn_response_intake.py` | Response intake for the conversation turn loop: normalize the raw provider response into the assistant message, splice agent-as-provider projections, fire ``post_api_request``, relay reasoning to the progress callback,… |
| `turn_retry_state.py` | Per-attempt recovery bookkeeping (``TurnRetryState``) for the conversation turn loop. Dependency-free so it imports without a cycle. |
| `turn_scripted_prelude.py` | Scripted prelude: tool calls a prompt built-in plays before the turn's first model call. |
| `turn_stop_gates.py` | Text-response stop gates for the conversation turn loop. |
| `turn_summary.py` | Per-turn accounting for the interactive CLI (display-only, pure). |
| `turn_tool_round.py` | One tool-calling round of the conversation turn loop: validate/cap/dedupe the model's tool calls, persist the tool-call turn BEFORE any side effect, execute the tools, honour guardrail halts / persistence failures, then… |
| `turn_tool_validation.py` | Tool-call validation for the conversation turn loop: unknown tool names (with auto-repair and the 3-strike partial exit) and malformed JSON arguments (retry, then recovery tool results). |
| `turn_truncation.py` | Truncation recovery (``finish_reason == "length"``) for the conversation turn loop. |
| `turn_usage.py` | Per-response usage accounting for the conversation turn loop. |
| `usage_anchor.py` | Usage-anchored token accounting: the provider's real ``usage.prompt_tokens`` is the only authoritative context size; the local ``bytes/4`` estimate covers ONLY messages appended since. |
| `usage_gauges.py` | Usage-window allowances as the server sends them: one list, in display order. |
| `usage_pricing.py` | Defines `format_cost_label`, `CanonicalUsage`, `BillingRoute`, `PricingEntry`, `CostResult`, `_snap` … |
| `vault_backend_registry.py` | Profile-scoped browser-vault login backends registered by trusted in-process plugins. |
| `vault_backends/__init__.py` | Login backends for the browser credential vault. |
| `vault_backends/base.py` | Login-backend contract + registry for the browser credential vault. |
| `vault_backends/bitwarden.py` | Bitwarden Password Manager logins as a vault backend (``bw`` CLI). |
| `vault_backends/local.py` | Local Fernet vault as a login backend (the always-on default). |
| `vault_backends/onepassword.py` | 1Password Login items as a vault backend (``op`` CLI). |
| `vault_backends/plugin.py` | Core-owned wrapper around a plugin-registered login backend. |
| `vault_backends/unlock.py` | Per-process unlock state for external password managers. |
| `vault_keychain.py` | OS-keychain storage for the local vault key (opt-in: ``vault.key_storage: keychain``). |
| `vault_login_classifier.py` | Login / checkout form control classifier for vault autofill. |
| `vault_store.py` | Local encrypted vault for browser autofill secrets. |
| `verification_evidence.py` | Coding verification evidence ledger: records what the agent actually proved in a code workspace. Deliberately passive — it never runs a suite, never blocks completion, and never upgrades targeted checks into "repo green… |
| `verification_stop.py` | Turn-end verification guard for coding edits. Policy-only: it never runs checks itself, it turns the passive verification ledger into a bounded follow-up when the model tries to finish right after editing code without f… |
| `verify/__init__.py` | Project verification subsystem. |
| `verify/environment.py` | Environment manifest for project verification. |
| `verify/recipes.py` | Static run-recipe detection for project verification. |
| `verify/runner.py` | Verification runner: bootstrap -> build -> test -> start in background -> readiness loop -> teardown (scoped port of grok-cli's verify flow). |
| `verify_hooks.py` | Verification-loop helpers for the ``pre_verify`` round-end gate. |
| `vertex_adapter.py` | Vertex AI (Google Cloud) auth + base-URL resolution for its OpenAI-compatible endpoint. |
| `video_gen_provider.py` | Video Generation Provider ABC. |
| `video_gen_registry.py` | Video Generation Provider Registry. |
| `vision_message_prep.py` | Image-part handling for ``AIAgent`` API messages. |
| `voice_turn_route.py` | Per-turn model route for voice chat: ``auxiliary.voice_chat``. |
| `web_search_provider.py` | Web Search Provider ABC. |
| `web_search_registry.py` | Web Search Provider Registry. |
