# File reference: `evals`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `__init__.py` | Package marker / package-level exports |
| `acp_empty_session_wire.py` | Native ACP stdio + SQLite probe; local HTTP model fixture, never paid inference. |
| `anthropic_proxy_thinking_replay.py` | Local wire-contract probe: which thinking blocks a real AIAgent replays to an Anthropic-compatible relay. Synthetic SSE fixtures; NOT live-provider proof. |
| `api_delegation_http_probe.py` | Loopback HTTP + real API executor/session bindings, with inference replaced. |
| `api_delegation_sync_probe.py` | Model-free API delegation delivery probe; run in an isolated HERMES_HOME. |
| `approval_deny_dispatch.py` | Offline production-dispatch receipt; never invokes a privileged binary. |
| `auth_pool_controls.py` | Live PTY auth controls with isolated homes and a loopback OAuth server. |
| `auxiliary_resource_exhausted.py` | Local HTTP contract probe; no vendor request or personal Hermes state. |
| `botmode-dm-delivery/README.md` | Native Bot Mode delivery probe |
| `botmode-dm-delivery/mock-trigger.patch` | Patch file |
| `botmode-dm-delivery/probe-cron-root.spec.ts` | Tests: ordinary cron pins an unowned named target under a custom root |
| `botmode-dm-delivery/probe-dm-delivery.spec.ts` | Tests: cron output waits for a CLI-only owner and arrives after owner release; named Bot Chat receives a nested one-shot message_agent delivery once |
| `botmode-dm-matrix/README.md` | Bot Mode native delivery matrix |
| `botmode-dm-matrix/mock-trigger.patch` | Patch file |
| `botmode-dm-matrix/probe-dm-matrix.spec.ts` | Tests: default live owner does not capture named unowned nested quiet CLI deliveries; incoming live sender card is rendered before any reload |
| `browser_use/README.md` | Browser Use Mode Benchmark |
| `browser_use/benchmark_browser_eval.py` | Quick benchmark: supervisor-WS ``Runtime.evaluate`` latency against a live Chrome. |
| `browser_use/orchestrate.py` | Local-CDP battery orchestrator: tasks x arms x models x reps. |
| `browser_use/orchestrate_cloud.py` | Cloud-backend battery: pr arm attached to a provisioned cloud browser per cell. |
| `browser_use/report.py` | Aggregate results.jsonl into the scorecard tables. |
| `browser_use/results/.gitignore` | Git ignore rules |
| `browser_use/single_run.py` | One benchmark cell: task x arm x model x rep. |
| `browser_use/tasks/easy.json` | JSON object with keys `simple_price`, `multi_extract`, `count_aggregate`, `form_login`, `pagination_nav` |
| `browser_use/tasks/hard.json` | JSON object with keys `multi_page_filter`, `rating_aggregate`, `js_rendered`, `delayed_render`, `login_then_extract`, `cross_category_compare` |
| `cli_deferred_notice.py` | Drive the real CLI with a FIFO update-cache result under a Linux PTY. |
| `cli_fallback_add_picker_error.py` | Drive the real ``hermes fallback add`` under a Linux PTY into an ordinary picker error. |
| `codebase_navigability/README.md` | Codebase navigability eval |
| `codebase_navigability/__init__.py` | Package marker / package-level exports |
| `codebase_navigability/bench.py` | Agent-navigability benchmark: what does it cost an LLM agent to find and read a symbol? |
| `codebase_navigability/lookup_sim.py` | Simulated agent lookups: how many tool calls / tokens to answer "show me the definition of X"? |
| `codebase_navigability/runtime_bench.py` | Runtime benchmarks for one tree. Usage: python runtime_bench.py <tree> <label> [reps] |
| `codebase_navigability/static_metrics.py` | Static code metrics for one tree. Usage: python static_metrics.py <tree> <label> -> writes <label>.static.json |
| `codex_echo/README.md` | Codex input ownership probe |
| `codex_echo/fixture_server.py` | Offline Codex JSON-RPC peer; no provider or authentication calls. |
| `codex_echo/probe.py` | Run from the checkout: PYTHONPATH=. python evals/codex_echo/probe.py. |
| `codex_masked_replay_review.py` | Local HTTP contract review of masked-error recovery; NOT live-provider proof. |
| `compaction/README.md` | Compaction Eval Harness |
| `compaction/fixtures.py` | Transcript fixtures for the compaction eval harness. |
| `compaction/jev_arm.py` | fast-jev-compaction as a compaction eval arm. |
| `compaction/policies.py` | Compaction policy matrix. |
| `compaction/report.py` | Render a compaction-eval scorecard as a terminal table + markdown. |
| `compaction/results/SCORECARD-2026-08-15.md` | Compaction v2 — 4-transcript scorecard (2026-08-15, anchor-index build) |
| `compaction/results/SCORECARD-2026-09-19-jev.md` | fast-jev-compaction vs Hermes compaction — 3-transcript scorecard (2026-09-19) |
| `compaction/results/codex-arm-2026-08-15/acp.json` | JSON object with keys `summary`, `results` |
| `compaction/results/codex-arm-2026-08-15/gui.json` | JSON object with keys `summary`, `results` |
| `compaction/results/codex-arm-2026-08-15/prmerge.json` | JSON object with keys `summary`, `results` |
| `compaction/results/codex-arm-2026-08-15/sweep.json` | JSON object with keys `summary`, `results` |
| `compaction/results/jev-cycles-2026-09-19/cycles-afff57-500k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/results/jev-cycles-2026-09-19/cycles-prreview-160k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/results/jev-cycles-2026-09-19/cycles-prreview-500k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/results/jev-cycles-2026-09-19/cycles-sigsegv-160k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/results/jev-cycles-2026-09-19/cycles-sigsegv-500k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/results/jev-cycles-2026-09-19/cycles-sysprompt-500k.json` | JSON object with keys `transcript`, `threshold`, `raw_tokens_consumed`, `raw_total`, `msgs_consumed`, `cycles` |
| `compaction/runner.py` | Compaction eval runner. |
| `compaction/scripts/build_html_report.py` | Build a self-contained HTML report comparing compaction runs. |
| `compaction/scripts/codex_arm.py` | Run the codex CLI as an eval arm on the same transcripts + question banks. |
| `compaction/scripts/jev_cycles.py` | Simulate repeated Jev compaction over a growing session. |
| `compaction/scripts/jev_cycles_report.py` | Render the repeated-compaction table from jev_cycles.py outputs. |
| `compaction/scripts/reconstruct_lineage.py` | Reconstruct the full uncompacted transcript of a session LINEAGE. |
| `compaction/scripts/replay_lineage.py` | Replay a ~500K-token prefix of a reconstructed lineage through compaction. |
| `compaction/test_region_scoping.py` | Region-scoping tripwire: the summarizer must only see the compacted region. |
| `completion_backlog_probe.py` | Local I/O probe for completion batching, not a hosted-model or native UI test. |
| `core_tool_deferral/README.md` | core_tool_deferral — live A/B harness for tool-visibility changes |
| `core_tool_deferral/orchestrator.py` | Orchestrate the PR #97979 A/B battery. Resume-safe; per-run wall timeout. |
| `core_tool_deferral/report.py` | Aggregate A/B results. Usage: report.py [model_short ...] |
| `core_tool_deferral/results/.gitignore` | Git ignore rules |
| `core_tool_deferral/results/SUMMARY.md` | PR #97979 A/B verdict — core-tool deferral (288 live runs) |
| `core_tool_deferral/sandbox.py` | Keep an eval agent's host-level side effects inside the run's sandbox. |
| `core_tool_deferral/tasks.py` | Task battery for PR #97979 core-tool-deferral A/B. |
| `core_tool_deferral/worker.py` | Run ONE (arm, model, task, rep) cell of the PR #97979 A/B in an isolated process. |
| `cron_error_diagnostics.py` | Local-I/O A/B for #104538; no inference, external APIs, or deliveries. |
| `cron_timeout_fork_race.py` | Linux live cron race probe: real PID map, synchronized fork, owned-only cleanup. |
| `dashboard_auth/refresh_singleflight_live_e2e.py` | Live E2E for #55712: real uvicorn, stub rotating IdP with reuse detection. |
| `delegation_group_schema/README.md` | Delegation grouping schema receipts |
| `delegation_group_schema/probe.py` | Offline same-config schema probe. Run in a fresh interpreter for each tree/policy. |
| `delivery_flood_wire.py` | Local-wire delivery ledger A/B, not a real Telegram bot or model run. |
| `desktop-pane-fixture/README.md` | Saved-pane fixture import-delay control |
| `desktop-pane-fixture/vitest.config.mts` | From apps/desktop: npx vitest run --config ../../evals/desktop-pane-fixture/vitest.config.mts Replay a slow module evaluation without changing any pane behavior or deadlines. |
| `desktop-reap-clock-pressure.cjs` | Replay scheduling pressure without changing Date.now() results: NODE_OPTIONS="--require=$PWD/evals/desktop-reap-clock-pressure.cjs" \ npm run test:desktop:platforms -w apps/desktop -- electron/backend-ownership.test.ts |
| `desktop_bug_campaign/async-report-README.md` | Async report rendering probe |
| `desktop_bug_campaign/async-report-live.mjs` | JavaScript (ES module): `async-report-live` |
| `desktop_bug_campaign/async-report-probe.html` | HTML page/template |
| `desktop_bug_campaign/async-report-probe.tsx` | TypeScript React component: `async-report-probe` |
| `desktop_bug_campaign/async-report-producer.py` | Real offline completion producers -> durable SQLite rows; never run a model. |
| `desktop_bug_campaign/async-report-vite.mjs` | JavaScript (ES module): `async-report-vite` |
| `desktop_bug_campaign/history_live.py` | Real serve/HTTP/WS history witness. No provider calls; seeded SQLite data. |
| `desktop_bug_campaign/hooks_live.py` | Real serve + WebSocket + local HTTP inference fixture hook probe (no vendor calls). |
| `desktop_bug_campaign/leases_live.py` | Real WS/backend-process lease recovery probe; deterministic HTTP inference. |
| `desktop_bug_campaign/linux_launcher_probe.py` | Real Linux venv/XDG I/O probe; help-launch is NOT a native UI proof. |
| `desktop_bug_campaign/markdown-README.md` | Markdown whitespace live probe |
| `desktop_bug_campaign/markdown-producer.py` | Collect real cron completion producer + durable delivery, without inference. |
| `desktop_bug_campaign/native_ready_probe.mjs` | Real backend + production READY parser; no Electron renderer is exercised. |
| `desktop_bug_campaign/navigation-markdown-README.md` | Navigation / Markdown campaign probe |
| `desktop_bug_campaign/navigation-markdown-live.mjs` | JavaScript (ES module): `navigation-markdown-live` |
| `desktop_bug_campaign/navigation-markdown-probe.html` | HTML page/template |
| `desktop_bug_campaign/navigation-markdown-probe.tsx` | TypeScript React component: `navigation-markdown-probe` |
| `desktop_bug_campaign/navigation-vite.mjs` | JavaScript (ES module): `navigation-vite` |
| `desktop_bug_campaign/persistence_live.py` | Real serve/WS profile-rebuild probe; deterministic loopback model, no vendor inference. |
| `desktop_bug_campaign/rebuild_observer.py` | Probe-only serve bootstrap: observe real ownership and inject config-read failure. |
| `desktop_bug_campaign/thread-scroll/README.md` | Thread reading-intent probe |
| `desktop_bug_campaign/thread-scroll/fixture.html` | HTML page/template |
| `desktop_bug_campaign/thread-scroll/fixture.tsx` | TypeScript React component: `fixture` |
| `desktop_bug_campaign/thread-scroll/ownership-probe.mjs` | JavaScript (ES module): `ownership-probe` |
| `desktop_bug_campaign/thread-scroll/probe.mjs` | JavaScript (ES module): `probe` |
| `desktop_gateway_ticket_native/.gitignore` | Git ignore rules |
| `desktop_gateway_ticket_native/README.md` | Native Electron local-gateway ticket probe |
| `desktop_gateway_ticket_native/build.mjs` | JavaScript (ES module): `build` |
| `desktop_gateway_ticket_native/electron-main-multiplex.ts` | Multiplex attach + cold-profile sidebar mutation, in real Electron main against one `gateway.run` that serves default + warm + cold. Every step is the production Desktop code path: `runGatewayEnsure` → `ensureLocalGatew… |
| `desktop_gateway_ticket_native/electron-main.ts` | TypeScript source: `electron-main` |
| `desktop_gateway_ticket_native/run.py` | Run an actual Electron main against ordinary, disposable gateway daemons. |
| `desktop_gateway_ticket_native/run_multiplex.py` | Real Electron main against one multiplexing gateway (default + warm + cold): Desktop attach for every profile through the production ensure/ticket code, then archive/unarchive of a COLD profile's session over the exact… |
| `desktop_gateway_ticket_native/workflow.yml` | DISPOSABLE: copy to .github/workflows/native-ticket-temp.yml on a probe-only branch. Do not merge this workflow; delete the temporary branch after evidence. |
| `desktop_mcp_oauth/README.md` | Desktop MCP OAuth integration checks |
| `desktop_mcp_oauth/backend_http_fixture.py` | Credential-free live OAuth/MCP persistence probe (no production mocks). |
| `desktop_mcp_oauth/renderer_lifecycle.mjs` | JavaScript (ES module): `renderer_lifecycle` |
| `fanout_resource_bench.py` | Fan-out resource benchmark for hermes-agent. |
| `gateway/session_time_persistence_ab.py` | Real SessionStore/SQLite A/B, isolated fresh process; no provider calls. |
| `gateway/session_time_persistence_controls.py` | Isolated production-library controls; no transport/provider calls. |
| `gateway_completion/README.md` | Completion delivery lifecycle probe |
| `gateway_completion/delivery_lifecycle.py` | Defines `main` |
| `gateway_failure_ownership/README.md` | Gateway failure-writer ownership |
| `gateway_failure_ownership/foreign_writer.py` | Independent durable writer used only by the loopback ownership probe. |
| `gateway_failure_ownership/probe.py` | Defines `_external`, `local_connect`, `local_connect_ex`, `Peer`, `ControlledAgent`, `voice_policy` … |
| `gateway_status_render/iteration_ceiling_ab.py` | A/B probe: what the three user-facing gateway status lines render for the iteration counter. |
| `gemini_type_array_probe.py` | Offline A/B native adapter + Google SDK schema validation (no API calls). |
| `goal_command_parity.py` | CLI /goal semantic oracle, with real storage and no model calls. |
| `heartbeat_idle_wire.py` | Wire-contract probe: real poller, SQLite, adapter lifecycle; fake model/transport. |
| `hosted_attachment_transfer/.gitignore` | Git ignore rules |
| `hosted_attachment_transfer/bench.py` | Hosted-room attachment transfer cost over the real private control socket. |
| `kanban_graph_identity.py` | Credential-free SQLite integration probe; run with --repo PATH. |
| `kanban_pr_acceptance_live.py` | Local HTTP/lifecycle probe; no external GitHub writes or inference. Run: python evals/kanban_pr_acceptance_live.py ROOT |
| `kanban_scope_probe.py` | Credential-free app-server/MCP scope probe; writes only its temporary board. |
| `key_cmd_picker_live.py` | Live key_cmd catalog A/B: local authenticated HTTP, real helper, CLI PTY. |
| `liveness/ws_orphan_reconnect.py` | Real WS/session.create/disconnect/timers/RPC integration; offline model boundary. Usage: python evals/liveness/ws_orphan_reconnect.py REPO [redetach] Seeds a post-interrupt queued envelope to reproduce the bypass-writer… |
| `mcp_device_flow.py` | Local RFC 8628 wire fixture; no external credentials or provider claims. |
| `native_compaction/ab_checkpoint_preflight.py` | A/B probe: does a freshly captured / restored native compaction checkpoint false-trigger local compression on the next preflight? (#100611) |
| `openrouter_pkce_ab/harness.py` | Local A/B harness for `hermes auth add openrouter --type oauth` against a FAKE OpenRouter. |
| `output_caps_local_capture.py` | Zero-cost local SDK wire capture. Fixtures are not vendor inference evidence. |
| `output_caps_scope.md` | Output-cap removal: scope and local evidence |
| `output_caps_surfaces.py` | Full local execution controls; never sends a request to an inference vendor. |
| `plugin_isolation/audit_catalog.py` | Run the plugin-host readiness audit over every plugin-catalog entry at its pinned commit. |
| `postmortem/README.md` | Post-mortem harness: forensics + live A/B for the 1,393-agent run fixes |
| `postmortem/__init__.py` | Package marker / package-level exports |
| `postmortem/forensics/__init__.py` | Package marker / package-level exports |
| `postmortem/forensics/common.py` | Shared loaders for the post-mortem forensics: point at ANY Hermes ``state.db`` (a copy, never the live file) and get the run tree, the in-run session set, fitted pricing and message iterators. |
| `postmortem/forensics/delegation.py` | Lane 2: delegation behaviour — nested-delegate timeouts, orphaned children, polling cost, batch-join delivery delay, and summary truncation. All OBSERVED from ``messages`` in the run tree. |
| `postmortem/forensics/goal_loop.py` | Lane 4: /goal loop behaviour — nudges, judge verdicts, parked time. OBSERVED from the root session's messages and the persisted goal state. |
| `postmortem/forensics/logcalls.py` | Lane 1b: per-call cache behaviour from ``agent.log`` (OBSERVED provider usage per call). |
| `postmortem/forensics/rework.py` | Lane 5: post-open rework inventory for a large PR — reproducible part only. |
| `postmortem/forensics/tokens.py` | Lane 1: where the money went, context sizes, and the compression-cap counterfactual. |
| `postmortem/forensics/tools.py` | Lane 3: tool-layer friction — hardline false blocks, foreground refusals, whole-file rewrites, output volume by tool. All OBSERVED from ``messages`` (role='tool') in the run tree. |
| `postmortem/live_ab/__init__.py` | Package marker / package-level exports |
| `postmortem/live_ab/auth_stampede.py` | Live A/B of the Nous hourly-expiry stampede, no real network. |
| `postmortem/live_ab/batch_failure_notice.py` | Live: detached delegate_task batch, one child fails immediately, siblings run ~8 s. Does the parent's completion queue see the per-task failure notice BEFORE the consolidated batch result? Usage: python notice_live.py <… |
| `postmortem/live_ab/cache_concurrency_probe.py` | Live prompt-cache concurrency probe: does a route keep cache routing sticky under a fan-out? |
| `postmortem/live_ab/cache_prefix_live.py` | Live A/B for the thinking-strip cache miss (F0). Runs a short real tool loop through AIAgent on Fable 5.1 via Nous and prints per-call cache hit ratios from agent.log. ~10 calls, well under $1. Arm A = current code. Arm… |
| `postmortem/live_ab/cache_prefix_wire.py` | Definitive F0 test: capture consecutive wire payloads on a real Fable 5.1 tool loop and diff the message prefix between call N and N+1. If Hermes strips prior-turn thinking, call N+1's messages[:k] will NOT equal call N… |
| `postmortem/live_ab/goal_judge_wait.py` | Live judge A/B on the run's real "waiting" response shape. Usage: python judge_ab.py <repo_root> [n] |
| `postmortem/live_ab/hardline_scanner_matrix.py` | Python module: `hardline_scanner_matrix` |
| `postmortem/live_ab/nested_delegate_deadline.py` | Live A/B for the nested-delegate deadline. A depth-1 orchestrator child dispatches one leaf that runs a ~460 s task (longer than the 420 s sequential deadline). On main the orchestrator's delegate_task call returns 'tim… |
| `postmortem/live_ab/subagent_context_cap.py` | Live: build a real child through delegate_tool's spawn path (real imports, temp HERMES_HOME) and read the trigger it resolves on a 1M-window model. Run against main and the branch. |
| `postmortem/review_probes/__init__.py` | Package marker / package-level exports |
| `postmortem/review_probes/cache_estimator_probe.py` | #103476: preflight estimate vs Anthropic wire size with retained thinking |
| `postmortem/review_probes/context_cap_probe.py` | #103513: child cap through repeated compression and persistence |
| `postmortem/review_probes/credential_identity_probe.py` | #103526: explicit account-A key must not be replaced by the singleton's account-B key (real SDK -> loopback) |
| `postmortem/review_probes/deadline_probe.py` | #103486: nested delegate deadline through actual dispatch |
| `postmortem/review_probes/finalizer_schedule_probe.py` | #103507: pytest plugin forcing the consumer-first schedule (-p finalizer_schedule_probe --finalizer-probe=consumer-first) |
| `postmortem/review_probes/goal_repaste_probe.py` | #103553: /goal re-paste vs option-selecting fragment |
| `postmortem/review_probes/goal_scope_probe.py` | #103496/#103534: judge process scoping and delegation WAIT lifecycle |
| `postmortem/review_probes/notice_delivery_probe.py` | #103549: interim notice must not claim/ack/dedup the batch's final result |
| `postmortem/review_probes/rewrite_hint_probe.py` | #103551: remote backend, FIFO, and quadratic-time hazards of the rewrite hint |
| `postmortem/review_probes/scanner_bypass_probe.py` | #103492: a hardline command hidden after a NEWLINE inside a double-quoted $(grep …) must stay blocked by the public guard with no approval callback; a grep with a backtick operand must stay allowed. |
| `postmortem/run.py` | Run the post-mortem harness against one or two checkouts and print a comparison table. |
| `postmortem/tests/__init__.py` | Package marker / package-level exports |
| `postmortem/tests/test_postmortem_harness.py` | The post-mortem forensics run end-to-end on a synthetic state.db and report the run population correctly. |
| `prefix_rediet/README.md` | prefix_rediet — live A/B for the fixed-prefix re-diet |
| `prefix_rediet/run.py` | Battery runner + readout for the fixed-prefix re-diet A/B. |
| `prefix_rediet/worker.py` | Run ONE (arm, model, task, rep) cell of the fixed-prefix re-diet A/B in an isolated process. |
| `process_result_receipt_probe.py` | Live process I/O proof, without model calls: python probe.py REPO OUT_DIR. |
| `prompt_footprint/property_guidance.py` | Offline prompt A/B and real optional catalog -> skill_view probe. Run with the repository venv; tiktoken must be available. No model API calls. |
| `provider_fallback/probe_104120.py` | Defines `local_connect`, `Handler` |
| `provider_fallback/probe_104260.py` | Offline production-import reproduction: no repo edits or real credentials. |
| `provider_fallback/probe_104360.py` | Defines `connect`, `Handler`, `request`, `ProbeAgent` |
| `provider_wire/issue_103944.py` | Credential-free named-route reasoning parity probe over localhost SDK HTTP. |
| `provider_wire/issue_104282.py` | Live localhost Responses adapter video rejection/control probe. |
| `provider_wire/issue_104359.py` | Offline production-path wire probe; only loopback HTTP is permitted. |
| `providers/reasoning_shapes.py` | Local HTTP/SDK reasoning-shape probe; no vendor inference or credentials. |
| `readtool/README.md` | Read-Tool Eval |
| `readtool/fixtures.py` | Hostile-workspace fixture generator for the read-tool eval. |
| `readtool/report.py` | Compare read-tool eval result sets (baseline vs feature labels). |
| `readtool/results/.gitignore` | Git ignore rules |
| `readtool/results/SUMMARY.md` | Read-Tool Eval — Results Log |
| `readtool/runner.py` | Run the read-tool eval through the REAL Hermes AIAgent. |
| `readtool/tasks.py` | Task battery for the read-tool eval. |
| `reasoning_replay/README.md` | Reasoning-replay consumption eval |
| `reasoning_replay/harness.py` | Reasoning-replay CONSUMPTION eval: does a provider/model actually read replayed reasoning? |
| `session_search_schema/README.md` | session_search Schema A/B Eval |
| `session_search_schema/fixtures.py` | Seed the synthetic session DBs for the session_search schema A/B eval. |
| `session_search_schema/report.py` | Summarize session_search schema A/B results. |
| `session_search_schema/results/pr95570/openai_gpt-5.6-luna.jsonl` | JSON-lines dataset/fixture |
| `session_search_schema/results/pr95570/openai_gpt-5.6-terra.jsonl` | JSON-lines dataset/fixture |
| `session_search_schema/results/pr95570/qwen_qwen3-coder-30b-a3b-instruct.jsonl` | JSON-lines dataset/fixture |
| `session_search_schema/runner.py` | Live A/B runner: session_search schema variants, extracted from git refs. |
| `session_search_schema/tasks.py` | Task prompts + programmatic oracles for the session_search schema A/B eval. |
| `session_snapshot_removal.py` | Real config → SQLite persistence → explicit /save A/B, without provider calls. |
| `shared_gateway/README.md` | Shared gateway acceptance coverage |
| `shared_gateway/cases.json` | JSON object with keys `schema`, `cases` |
| `shared_gateway/normal_boot.py` | Live POSIX bootstrap descriptor check, not an execution/readiness handshake proof. |
| `shared_gateway/search_readonly_ab.py` | Fresh-process production tool A/B; all storage is disposable. |
| `shared_gateway/session_readers_cli_ab.py` | Actual CLI A/B for observational commands; no user state or credentials. |
| `shared_gateway/verify_receipt.py` | Check measured shared-gateway receipts against the full required case set. |
| `slack_stream_wire_contract.py` | Wire-contract A/B for Slack native task-card streams (#87743). |
| `subagent_process_handoff/stress_handoff_live.py` | Live stress harness for PR #105125 (subagent background-process accounting) with a real orchestrator AND real children on one model. Each scenario: the parent is asked to delegate; the children do things with background… |
| `token_accounting/ab_image_cost_calibration.py` | A/B probe: does the compaction trigger learn the real per-image cost from provider usage? (#70328) |
| `token_accounting/display_provenance.py` | Credential-free production CLI PTY / live slash display A/B. |
| `token_accounting/replay_gates.py` | Token-accounting replay: do the compaction gates follow the provider's REAL usage or the local ``bytes/4`` estimate? (#104462) |
| `token_accounting/worktree_prompt_prefix.py` | Offline real-worktree prompt prefix probe (no provider requests). |
| `tool_search/README.md` | Tool Search live test harness |
| `tool_search/analyze_livetest.py` | Compare enabled vs disabled runs and produce a readable report. |
| `tool_search/tool_search_livetest.py` | Live test harness for Hermes Agent's Tool Search feature. |
| `tool_search/tool_search_livetest2.py` | Tool Search live benchmark v2 — real token accounting + more scenarios + reps. |
| `tool_search/tool_search_livetest_ue.py` | Live benchmark v3: Epic Unreal Engine 5.8 MCP surface (830 REAL schemas), replayed. |
| `tool_search/tool_search_livetest_ue_disc.py` | Live benchmark v5 — DISCOVERY-BOUND tasks at 830 tools. Opus 4.8, bridge vs listing. |
| `tool_search/tool_search_livetest_ue_hard.py` | Live benchmark v4 — ADVERSARIAL Unreal tool selection at 830 tools. |
| `toolperf_abeval/README.md` | Core-Toolset A/B Eval Harness |
| `toolperf_abeval/ab_eval.py` | Hard A/B evaluation for core-toolset changes: baseline vs fixes. |
| `toolperf_abeval/run_all.sh` | Full A/B eval: N models x 2 arms x 9 tasks x R reps. |
| `update_check_ssh_pty.py` | Linux live Git/OpenSSH PTY probe; fixture ssh config, no user state. |
| `update_obligation_identity.py` | Disposable process/state-file A/B: run with the checkout path as argv[1]. |
| `update_pipeline/interrupted_pull_ab.sh` | Live A/B for the interrupted-pull repair (hermes_cli/_early_recovery.py::restore_interrupted_pull). |
| `update_pipeline/post_swap_handoff_ab.sh` | Live A/B for the post-swap hand-off (hermes_cli/update_handoff.py). |
| `update_streaming/live_output.py` | Disposable subprocess/tee probe; never invokes an actual update. |
| `update_streaming/watchdog.ps1` | PowerShell script |
| `update_unit_client_budget.py` | Real disposable user-systemd transaction, never a production gateway. |
| `vault_fill_live_e2e.py` | Live E2E: vault fill through the REAL browser_exec path (Browser Use CLI + Hermes' packaged Chromium). |
| `webhook_auth/standard_webhooks_ab.py` | Live A/B probe: Standard Webhooks (webhook-id/-timestamp/-signature) against the REAL webhook adapter. |
