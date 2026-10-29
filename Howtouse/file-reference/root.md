# File reference: `(repository root)`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `.coderabbit.yaml` | CodeRabbit configuration. Auto-review is DISABLED repo-wide: the app was enabled at the org level on |
| `.dockerignore` | Docker build-context ignore rules |
| `.env.example` | Template for `.env` (secrets/API keys only) — copy and fill in |
| `.envrc` | direnv hook that activates the dev environment |
| `.gitattributes` | Auto-generated files — collapse diffs and exclude from language stats |
| `.gitignore` | Git ignore rules |
| `.hadolint.yaml` | hadolint configuration for the Hermes Agent Dockerfile. See https://github.com/hadolint/hadolint#configure for rules. |
| `.mailmap` | .mailmap — canonical author mapping for git shortlog / git log / GitHub Format: Canonical Name <canonical@email> <commit@email> See: https://git-scm.com/docs/gitmailmap |
| `.npmrc` | needed to prevent bad npm that has min-release-age but not exclude |
| `.nvmrc` | Node version pin |
| `.prettierignore` | Lockfiles must never be reformatted — main has a repo rule requiring team approval when lockfiles change, so an autofix PR touching one would hang waiting for review. |
| `.prettierrc` | Prettier formatter configuration |
| `.python-version` | Python version pin |
| `AGENTS.md` | Hermes Agent - Development Guide |
| `CONTRIBUTING.es.md` | Contribuir a Hermes Agent |
| `CONTRIBUTING.md` | Contributing to Hermes Agent |
| `Dockerfile` | Debian 13 still ships SQLite 3.46.1, which contains the upstream WAL-reset corruption bug. Build a pinned shared library for the runtime image instead of relying on a distro backport that trixie does not currently provi… |
| `LICENSE` | Software license text |
| `README.es.md` | Hermes Agent ☤ |
| `README.md` | Hermes Agent ☤ |
| `README.ur-pk.md` | ہرمیس ایجنٹ ☤ (Hermes Agent) |
| `README.zh-CN.md` | Hermes Agent ☤ |
| `SECURITY.es.md` | Política de Seguridad de Hermes Agent |
| `SECURITY.md` | Hermes Agent Security Policy |
| `SOUL.md` | You are Hermes Agent, built by Nous Research. Be direct: match the length of your reply to the weight of the ask — a one-line question gets a one-line answer, and finished work gets a short report of what changed, what'… |
| `activate` | ============================================================================ venv-style activation of the Hermes dev environment for an interactive shell. |
| `activate.fish` | Data/support file |
| `activate.ps1` | Source this file to sync and apply the PM environment; deactivate restores it. Trusts the recorded tool digest. `hermes pm install` re-checks the bytes. -TestExtras a,b selects runtime extras in the test environment (de… |
| `batch_runner.py` | Batch Agent Runner — run the agent over a JSONL prompt dataset in parallel. |
| `cli-config.yaml.example` | Annotated example of `config.yaml` showing available settings |
| `cli.py` | Hermes Agent CLI — interactive terminal interface (``python cli.py --help`` for usage). |
| `docker-compose.windows.yml` | docker-compose.windows.yml — Windows Docker Desktop compatible Differences from docker-compose.yml: |
| `docker-compose.yml` | docker-compose.yml for Hermes Agent Usage: |
| `eslint.config.shared.mjs` | Shared ESLint flat config for all Hermes TS workspaces. Usage in a workspace's eslint.config.mjs: import config from '../../eslint.config.shared.mjs' export default [ ...config, // workspace-specific overrides here ] |
| `flake.lock` | Nix flake lock file |
| `flake.nix` | Nix flake definition |
| `hermes` | Hermes Agent CLI launcher. |
| `hermes_bootstrap.py` | Process bootstrap for Hermes entry points: Windows UTF-8 stdio and ANSI console, import-path hardening, durable lazy-install target, and dual-stack (Happy Eyeballs) connects. |
| `hermes_constants.py` | Shared constants for Hermes Agent. |
| `hermes_constants_scratch.py` | Scratch-dir retention: idle detection plus the reaping an idle tree needs before it goes. |
| `hermes_constants_scratch_detach.py` | The hourly scratch prune runs in a detached child process, not in the process that is due it. |
| `hermes_constants_scratch_stuck.py` | Scratch entries the prune cannot delete as this user: remembered once, skipped until fixed. |
| `hermes_dir_acl.py` | Directories an elevated Windows process creates must stay usable by the same user unelevated. |
| `hermes_logging.py` | Centralized logging setup for Hermes Agent. |
| `hermes_startup_watchdog.py` | Startup-liveness watchdog — respawn a gateway that wedges before its loop runs (OOF-298). |
| `hermes_state.py` | SQLite state store for Hermes Agent: session metadata, message history, model config, FTS5 search. WAL mode (concurrent readers + one writer); compression splits sessions via parent_session_id chains; sessions are sourc… |
| `hermes_state_api_content.py` | The ``api_content`` sidecar backfill writers for SessionDB (#124102 FILE_LINES split). |
| `hermes_state_common.py` | Shared constants and helpers for the SessionDB family of modules. Lives outside hermes_state so the mixin modules can import it without a cycle. |
| `hermes_state_compaction_display.py` | Display reads paint a compacted tool result once, as its archived original (#132939, #135655). |
| `hermes_state_compression.py` | Compression lineage, cooldown/streak counters, locks and turn leases for SessionDB. |
| `hermes_state_coverage.py` | Held-row coverage resolution for in-place compaction: which durable rows the compressor actually held. |
| `hermes_state_dbfile.py` | state.db file-level health helpers, split out of ``hermes_state.py``. |
| `hermes_state_detached_results.py` | Results that arrive between turns, recorded once as user rows: a detached API delegation's delivery and an unviewed local completion's note (#134889 LC-7). Split out of ``hermes_state_messages`` and bound onto SessionDB… |
| `hermes_state_errors.py` | Exception types and error-classification predicates for the state store. Shared by hermes_state and its mixins; string predicates match wrapped RPC strings as well as live sqlite3 exceptions. |
| `hermes_state_fts.py` | FTS5 index setup for SessionDB: the CJK-bigram (cjk_unicode61) index DDL and tokenizer loader, per-table schema ensure with tokenizer-capability fallback, FTS-scoped corruption detection and the atomic fail-open trigger… |
| `hermes_state_gateway.py` | Gateway-facing SessionDB persistence: routing index, peers, orphans, heartbeats, handoffs. |
| `hermes_state_guard.py` | Live-DB test-isolation guard and the per-process "last init error" record. Every SessionDB construction resolves its path through _ensure_test_isolation so a pytest-context process (env OR ancestry) can never open a pro… |
| `hermes_state_health.py` | Profile-level session-storage health: one process-wide latch per state.db path. |
| `hermes_state_holders.py` | Process and descriptor authority for state.db structural maintenance. |
| `hermes_state_identity.py` | Durable message-identity columns for SessionDB (schema v31): the codec between the live identity keys (``agent.message_metadata``) and the ``message_uid`` / ``absorbed_message_uids`` / ``tool_call_uids`` / ``tool_call_u… |
| `hermes_state_ids.py` | Session-id minting: the ONE place that knows the ``YYYYMMDD_HHMMSS_<hex>`` shape. |
| `hermes_state_keys.py` | Pure identity derivations the canonical store and the gateway both need. |
| `hermes_state_local.py` | Private local creation receipts in the canonical runtime transaction owner. |
| `hermes_state_local_lineage.py` | Local physical-target handoff inside the existing publication transaction. |
| `hermes_state_local_migration.py` | Transactional legacy binding; never a second transcript writer. |
| `hermes_state_lockguard.py` | Hold a state.db writer's WAL-mode file locks in a form a stray ``close()`` cannot cancel. |
| `hermes_state_lockowners.py` | Who holds the SQLite write lock on state.db right now (Linux ``/proc/locks``). |
| `hermes_state_maintenance.py` | Retention pruning, stale-session archiving and VACUUM policy mixin for SessionDB. |
| `hermes_state_media.py` | Durable media retirement candidates survive transcript deletion and failed cleanup. |
| `hermes_state_messages.py` | Transcript persistence for SessionDB: message append/replace/rewind, reactions, resume assembly, replayed-user dedupe. Mixin bound via the MRO, built on SessionDB's _read_ctx/_execute_write/_read_* primitives. |
| `hermes_state_mutation_binding.py` | Control-only ownership for unbound legacy history; never an execution policy. |
| `hermes_state_mutation_branch.py` | An independent local route, transcript and frozen policy in one receipt commit. |
| `hermes_state_mutation_chat_pick.py` | Exact-retry receipts for a viewer's pick on a messaging chat (gateway/session_messaging_picks.py). |
| `hermes_state_mutation_compress.py` | Commit a prepared summary, physical target, generation and receipt atomically. |
| `hermes_state_mutation_guards.py` | Transcript mutation guards evaluated on the receipt's writer connection. |
| `hermes_state_mutation_prepared.py` | Optimistic preparation snapshots revalidated inside the receipt transaction. |
| `hermes_state_mutation_reset.py` | Prepare and publish a local reset inside the mutation receipt transaction. |
| `hermes_state_mutation_retirement.py` | Durable deletion fences outside prunable transcript rows. |
| `hermes_state_mutation_transcript.py` | Transaction-scoped rewind shared by storage and canonical mutations. |
| `hermes_state_mutations.py` | Closed action handlers inside the runtime mutation receipt transaction. |
| `hermes_state_pidns.py` | PID-namespace identity for state.db lock/lease holders. |
| `hermes_state_portability.py` | Session listing/rich rows, export, and import (portability) for SessionDB. |
| `hermes_state_profile_repair.py` | Crossed-profile durable state in ONE ``state.db`` — finders and fixers for ``hermes sessions repair-profiles`` (#88715 PR-6). |
| `hermes_state_prompt_refresh.py` | Operator-requested system prompt refresh epochs (``hermes sessions refresh-prompts``). |
| `hermes_state_prune_rewrite.py` | In-place row-rewrite persistence for the proactive prune (#124102). |
| `hermes_state_readpool.py` | Read-connection budgeting for SessionDB's WAL read path: per-file and process-wide permit ceilings plus a descriptor-headroom gate, so N handles on one state.db cannot walk the process into EMFILE. Idle pooled connectio… |
| `hermes_state_reconcile.py` | Additive state.db schema drift: detection, the one-shot browse reconcile, and explicit repair. |
| `hermes_state_registry.py` | Process-wide shared SessionDB registry. |
| `hermes_state_repair.py` | state.db repair, backup and writability preflight (split from hermes_state). |
| `hermes_state_rewind.py` | Carrier-aware user-turn rewind (``/undo``, ``/retry``) — the ONE implementation behind the CLI, the gateway and the TUI. Rewind is a persisted-history operation: the durable transcript is the authority, the warm (in-mem… |
| `hermes_state_runtime.py` | Canonical runtime transactions; callers authorize and resolve session identity. |
| `hermes_state_runtime_workers.py` | Worker exclusion follows the logical conversation and its physical transcript lineage. |
| `hermes_state_schema.py` | Schema creation, column reconciliation, and FTS DDL management for SessionDB. |
| `hermes_state_search.py` | Full-text / trigram / CJK message search and FTS maintenance for SessionDB. |
| `hermes_state_session_list.py` | Session-list page projection for ``SessionDB.list_sessions_rich``. |
| `hermes_state_sessions.py` | Session lifecycle mixin for SessionDB: row upsert/inheritance, lifecycle flags (end/reopen/archive/pin/hide/read), model_config patching, listing and counting, delete cascades, and the auto-archive sweep. |
| `hermes_state_sessions_model_config.py` | Conversation-wide ``sessions.model_config`` keys: read-modify-write at the compression tip and the key scan. Bodies of :class:`hermes_state_sessions.SessionSessionsMixin`'s two methods of the same names. |
| `hermes_state_telegram.py` | Telegram DM topic-mode mixin for :class:`hermes_state.SessionDB`. |
| `hermes_state_terminal.py` | Private terminal-only tombstone queries; never reconstruct executable history. |
| `hermes_state_timeline.py` | Read-only prompt index and bounded transcript jumps; no transcript-wide payload hydration. |
| `hermes_state_titles.py` | Session title mixin for SessionDB: sanitizing, auto/user provenance ranking, and lineage-aware lookups. |
| `hermes_state_todo.py` | The newest Todo result a resume restores: an indexed, bounded search of the resume display scope. Split out of ``hermes_state_messages`` and bound onto SessionDB through ``SessionMessagesMixin``; built on its _resume_li… |
| `hermes_state_usage.py` | Token/usage accounting mixin for SessionDB: the coalescing background token writer, per-model usage rows, and billing-route columns. Writer thread state lives on the instance. |
| `hermes_state_user_copy.py` | Plain-language copy for "session storage is unavailable / could not be written" notices. |
| `hermes_state_wal.py` | SQLite journal-mode and PRAGMA policy for state.db (split from hermes_state). |
| `hermes_state_worker_compression.py` | Closed compression operations on the worker receipt's connection. |
| `hermes_state_worker_context.py` | Closed constructor-context operations inside the worker receipt transaction. |
| `hermes_state_worker_lifecycle.py` | Closed worker lifecycle handlers, called only inside the receipt transaction. |
| `hermes_time.py` | Timezone-aware clock for Hermes. |
| `hermes_yaml.py` | Shared YAML 1.1 policy for config, manifests, and frontmatter. |
| `justfile` | `just` task-runner recipes |
| `lefthook.yml` | YAML configuration/data |
| `mini_swe_runner.py` | SWE Runner with Hermes Trajectory Format |
| `model_tools.py` | Thin orchestration layer over the tool registry. |
| `package-lock.json` | npm dependency lock file |
| `package.json` | `hermes-agent` — An AI agent with advanced tool-calling capabilities, featuring a flexible toolsets system for organizing and managing tools. |
| `pyproject.toml` | Python project metadata and dependencies |
| `registration_lifecycle.py` | Ownership leases for replaceable runtime registrations. |
| `ruff.pre-commit.toml` | Same as Black. |
| `ruff.toml` | Same as Black. |
| `run_agent.py` | AIAgent: the tool-calling agent runner (conversation loop, tool execution, session lifecycle). |
| `setup-hermes.ps1` | ============================================================================ Hermes Agent Setup Script (Windows) — THE dev-environment entry point. =======================================================================… |
| `setup-hermes.sh` | ============================================================================ Hermes Agent Setup Script — THE dev-environment entry point. ============================================================================ |
| `setup.py` | setup.py — wheel/sdist build guard. |
| `toolset_distributions.py` | Toolset distributions for batch data-generation runs. |
| `toolsets.py` | Toolset helpers: get/resolve/validate named tool groups (static TOOLSETS + registry-registered). |
| `trajectory_compressor.py` | Trajectory Compressor — post-process agent trajectories into a token budget. |
| `utils.py` | Shared utility functions for hermes-agent. |
| `uv.lock` | uv dependency lock file |
