# File reference: `cron`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | cron/ (+ kanban) — scheduled jobs and the multi-agent work queue |
| `__init__.py` | Cron job scheduling for Hermes Agent: scheduled tasks (cron expressions, intervals, one-shot), self-scheduled reminders, isolated sessions. The gateway daemon (``hermes gateway [install]``) ticks the scheduler every 60… |
| `blueprint_catalog.py` | Automation Blueprints — one slot-schema definition per automation that every surface renders natively: dashboard form (``blueprint_form_schema``), pre-filled ``/blueprint`` slash command (``blueprint_slash_command``), a… |
| `blueprint_plugins.py` | Plugin-contributed Automation Blueprints (``ctx.register_automation_blueprint``). |
| `bot_chat_legacy.py` | ``cron/bot_chat_pending``: Bot Chat outputs whose target owner was not running yet. |
| `constants.py` | Fire-claim timing bounds shared by the job store and its siblings. |
| `delivery_outcome.py` | Write a queued cron delivery's terminal outcome back onto the run that queued it. |
| `delivery_queue.py` | Profile-local durable handoff for cron delivery through live gateway adapters. |
| `env_settings.py` | Profile-scoped reads of the ``HERMES_*`` tuning settings cron honours from ``.env``. |
| `execution_identity.py` | Which cron execution the current code runs inside, for plugins (``ctx.current_cron_execution()``). |
| `executions.py` | Profile-local durable audit ledger for cron execution attempts. |
| `extra_fire.py` | Manual runs are EXTRA fires: a run-now (``cronjob run``, ``hermes cron run``, dashboard Run, gateway-forwarded ``trigger_job``) leaves the job's pending scheduled occurrence and its ``repeat`` budget alone. Without this… |
| `incidents.py` | Durable cron failure incidents with signature dedup and ack. |
| `job_definition.py` | Job-definition schema shared by importers of a foreign cron store. |
| `jobs.py` | Cron job storage: ~/.hermes/cron/jobs.json; output in ~/.hermes/cron/output/{job_id}/{timestamp}.md |
| `jobs_invariants.py` | Execution-mode invariants every cron job definition must satisfy. |
| `jobs_model_pin.py` | The main agent's current ``(provider, model)``, which ``pinned=True`` locks onto a cron job. |
| `jobs_oneshot_diagnostics.py` | Operator-visible traces left in a job's output dir when the due scan or the dispatch-limit guard removes a one-shot that never completed (``cron/jobs.py`` late-imports these). |
| `jobs_time.py` | Per-job ``timezone`` and ``grace_minutes`` knobs (sibling of ``cron/jobs.py``). |
| `lifecycle_guard.py` | Gateway lifecycle guard for cron job creation. |
| `monitor.py` | Monitor-mode cron support — hash-suppressed change detection. |
| `notepad.py` | Per-job durable KV notepad (cursors, watermarks) carried across cron wake-ups; profile-local SQLite next to the executions ledger (same connection/pragma pattern as ``cron/executions.py``). |
| `occurrences.py` | Exact scheduled identities, independent of mutable jobs.json dispatch stamps, plus the profile-local stale-schedule catch-up counter marker. |
| `quota_hold.py` | Hold a job's fires while a provider's usage window is known to be closed (#89376). |
| `scheduler.py` | Cron job scheduler: tick() runs due jobs (gateway calls it every 60s from a background thread). A file lock (~/.hermes/cron/.tick.lock) keeps overlapping processes to one tick at a time. |
| `scheduler_authority.py` | Transport-only cron execution; output/delivery remain with the firing scheduler. |
| `scheduler_bookkeeping.py` | Terminal bookkeeping phases shared by scheduler execution paths. |
| `scheduler_delivery.py` | Cron delivery: target resolution (origin/home/explicit/bot-chat), transcript mirroring and session seeding, live-adapter / relay / standalone send lanes, and ``_deliver_result``. |
| `scheduler_delivery_origin.py` | Relay egress discriminators a cron fire carries from its persisted job origin. |
| `scheduler_detached_worker.py` | Cron: teardown of a worker that outlived its ``run_job``. |
| `scheduler_diagnostics.py` | Private run-document diagnostics, kept separate from delivery summaries. |
| `scheduler_failure_copy.py` | Plain-language copy for the one-line cron failure notice delivered to a job's chat. |
| `scheduler_gateway_gate.py` | Headless tick gate: agent jobs need a live gateway; a headless tick never starts one. |
| `scheduler_liveness.py` | Liveness side of a running cron job: the inactivity watchdog loop and the execution-ledger progress stamps. |
| `scheduler_ownership.py` | Which profile homes THIS process ticks, and who owns the cron tick for a given home. |
| `scheduler_preflight.py` | Cron pre-run preflight: transient provider-resolution error classification, provider-key / delivery-target / skills checks, and the shared-route adapter view used by satellite profiles. |
| `scheduler_prompt.py` | Cron job prompt assembly: context_from injection, skill loading, the assembled-prompt injection scan, and the credential-exfil / config-block guards. |
| `scheduler_provider.py` | CronScheduler provider interface (Axis B — the trigger). EXPERIMENTAL: shape MAY change until a second provider validates it; growth MUST be additive (optional method with a default), never a changed start() signature o… |
| `scheduler_script.py` | Cron pre-run script execution: timeouts, Windows venv bootstrap, process-tree termination, and the claim-heartbeat thread that keeps a long script's run claim alive. |
| `scheduler_thread.py` | Supervised daemon thread for the in-process cron ticker. |
| `scheduler_tick.py` | In-process tick admission and dispatch; job execution stays in scheduler.py. |
| `scheduler_worker_env.py` | Cron: import path of the restart-safe external worker. |
| `scheduler_worker_failure.py` | Job-level visibility for a recovered, acknowledged worker death. |
| `scheduler_worktree_maintenance.py` | Process-wide coordination for the cron tick's worktree prune (``cron.scheduler`` runs in here). |
| `scripts/__init__.py` | Scripts shipped with the cron subsystem (runnable via ``python3 -m cron.scripts.<name>``). |
| `scripts/classify_items.py` | Classify candidate items by urgency/importance and emit only the urgent ones. |
| `store_health.py` | Degraded state for an unwritable cron store (ENOSPC, EROFS, EACCES). |
| `suggestion_catalog.py` | Curated catalog of starter cron-job suggestions. |
| `suggestions.py` | Suggested cron jobs — proposed automations the user accepts with one tap. |
| `unreachable_retry.py` | Automatic bounded re-runs for scheduled fires that never reached the model. |
| `worker_bootstrap.py` | Cron external worker: the PM dependency boot its own entry point never gets. |
