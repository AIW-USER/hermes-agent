# File reference: `scripts`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `_activation.py` | Activation guard for repository scripts. |
| `_activation.sh` | Sourced, never executed: how a POSIX shell gets the Hermes dev environment. `activate` (interactive, reversible) and `scripts/run-in-hermes-env` (a child process, one-way) both build on it; neither owns any of it. |
| `aa_quality_sync.py` | Propose catalog quality updates from Artificial Analysis. |
| `add_contributor.py` | Add a contributor email → GitHub login mapping. |
| `audit-old-updater-imports.py` | What an OLD `hermes update` can still import from a NEW tree. |
| `audit_pr_attribution.py` | Audit (and auto-fix) contributor email mappings for a PR branch. |
| `build-bundle.ps1` | PowerShell script |
| `build-bundle.sh` | Build the desktop bundle for the commit checked out here, on this machine. |
| `build/README.md` | Shared product builders |
| `build/agent.py` | Assemble a runnable agent from prepared inputs, without downloads or live state. |
| `build/desktop-reuse.mjs` | Can a packaged desktop app built at an earlier commit stand for HEAD? The freshness receipt already proves the bundle's inputs are byte-identical (sources, lockfile, build scripts, prepared icons/native trees, renderer… |
| `build/desktop.mjs` | Exports `buildDesktop` |
| `build/electron-runtime.mjs` | Exports `prepareElectronRuntime` |
| `build/freshness.mjs` | Product receipts belong to the compilers, not PM dependency receipts or profiles. |
| `build/frontend-common.mjs` | Exports `repoRoot`, `workspaceTool`, `productOutput`, `retryHeld`, `publishDirectory`, `withProduct` … |
| `build/icon_environment.py` | Prepare an interpreter that can run the icon generator without a Hermes install. |
| `build/inputs.py` | Build-time paths, not a second runtime configuration or dependency resolver. |
| `build/launcher_wrapper.py` | Bundled-payload CLI entry wrapper — the distlib launcher's zip overlay. |
| `build/launchers.py` | Shared payload launcher rendering; all paths are supplied by the assembler. |
| `build/mint_launchers.py` | Mint the bundled payload's win32 CLI launchers with distlib. |
| `build/node-deps.mjs` | Exports `npmCommand`, `prepareNodeDependencies` |
| `build/python.mjs` | Exports `runPython` |
| `build/tui.mjs` | Exports `buildTui` |
| `build/web.mjs` | Exports `buildWeb` |
| `build/webapp.mjs` | Exports `keepPreviousGeneration`, `buildWebapp` |
| `build/windows-deps.ps1` | Build-only prerequisites; setup-hermes.ps1 uses the same installer functions. |
| `build_model_catalog.py` | Build the Hermes Model Catalog — a centralized JSON manifest of curated models. |
| `build_skills_index.py` | Build the Hermes Skills Index — a centralized JSON catalog of all skills. |
| `bundle-store-msixbundle.mjs` | JavaScript (ES module): `bundle-store-msixbundle` |
| `bundles/bytecode.py` | Bake the payload's bytecode cache at staging time. |
| `bundles/channel_artifacts.py` | One native manifest/feed writer for admitted previews and protected releases. |
| `bundles/desktop.py` | Build a complete desktop bundle with the shared Python payload tools. |
| `bundles/desktop_inputs.py` | Build identity and process environment from an admitted preparation. |
| `bundles/desktop_prepare.py` | Complete desktop dependency preparation and its job-local consume contract. |
| `bundles/desktop_toolchain.py` | Child-scoped desktop build tools, independent of the invoking Hermes install. |
| `bundles/dmgbuild_diagnostics.py` | Run the supplier's dmgbuild with failure-time, read-only handle diagnostics. |
| `bundles/native.py` | Native payload staging through PM's existing package authority. |
| `bundles/native_build.py` | Prepare or consume the standalone PM payload, without desktop products. |
| `bundles/native_prepared.py` | Job-local native preparation admission; never a portable environment cache. |
| `bundles/payload.py` | Distribution snapshots, PM facts and portable link sealing. |
| `bundles/release_artifacts.py` | Record, stage and promote the exact native release artifacts. |
| `bundles/set_dmg_volume_icon.sh` | Replace the volume icon of a finished DMG (the same .VolumeIcon.icns + custom-icon flag dmgbuild sets). Tauri's bundler always uses the app's .icns as the volume icon and offers no override, so the bootstrap |
| `bundles/stage.py` | Select complete frontend products and stage the runnable native agent. |
| `capture-cage-terminal.sh` | Shell script: `capture-cage-terminal` |
| `check` | Run every blocking lint check CI runs, locally, with the same pinned tools: the lint the workflow's guards, ruff and the code-health ratchet, plus the case-collision, lazy-deps, profile-archive and blob-size guards that… |
| `check-case-collisions.py` | Blocking check for tracked files whose paths collide when case is ignored. |
| `check-windows-footguns.py` | Grep-based checker for Windows cross-platform footguns. |
| `check_bash_shebangs.py` | Require PATH-resolved Bash in scripts, generated scripts, and examples. |
| `check_config_yaml_readers.py` | Fail when a user ``config.yaml`` is read by anything but the config backend. |
| `check_config_yaml_writers.py` | Fail when a ``config.yaml`` is written by anything but the comment-preserving writer. |
| `check_no_tmp_literals.py` | Fail when production code, skills, docs or prompts hard-code a literal ``/tmp`` path. |
| `check_profile_scope_patterns.py` | Advisory lint: profile-scope hazard patterns on the lines a change adds. |
| `check_subprocess_stdin.py` | Check that subprocess calls in TUI-context code specify stdin=. |
| `ci/archive_inputs.py` | Archive pinned binary inputs in R2 and seed existing CI consumers. |
| `ci/assemble_review_comment.py` | Assemble the unified CI review comment for a pull request. |
| `ci/cache_report.py` | Cache archive observability from ordinary actions/cache logs (no inventory scans). |
| `ci/catalog_test_files.py` | Print the test files the ``catalog`` CI lane runs (catalog-tests.yml). |
| `ci/check_agents_md_size.py` | Fail when a tracked AGENTS.md would be truncated when an agent loads it. |
| `ci/check_blob_size.py` | Fail when a change adds a large binary, or a large new file, to the repository. |
| `ci/check_catalog_cors.py` | Fetch a docs catalog URL the way Hermes Desktop does, and fail when a browser would block it. |
| `ci/check_docs_drift.py` | Docs drift ratchet: every DEFAULT_CONFIG key and slash command must be documented. |
| `ci/check_lazy_deps_imports.py` | Fail when tracked production code imports the tools.lazy_deps stub. |
| `ci/check_os_marker_fakes.py` | Fail when a test file fakes macOS without carrying ``@pytest.mark.platforms("macos")``. |
| `ci/check_profile_archive_boundary.py` | Reject profile export archives before publication. |
| `ci/check_public_surface.py` | Public-surface diff against a base ref: dropped public names and dropped test functions. |
| `ci/classify_changes.py` | Classify a PR's changed files into CI work lanes. |
| `ci/desktop_build_cache.py` | Describe the desktop dependency snapshot using only the runner's stdlib. |
| `ci/desktop_commands.py` | Expose already-prepared tools to later CI audit/upload steps; never install. |
| `ci/docs_drift_baseline.json` | JSON object with keys `config`, `slash_commands` |
| `ci/e2e_screenshot_status.py` | Select Desktop E2E visual evidence and build its CI review status. |
| `ci/list_os_marked_tests.py` | List the test files that carry a platforms() gate for a given platform. |
| `ci/live_comment.py` | Live-updating CI review comment. |
| `ci/lockfile_diff.py` | Semantic diff of npm ``package-lock.json`` files for PR comments. |
| `ci/pm_cache_log.py` | Log setup-pm's restore results and write policy without traversing cache trees. |
| `ci/profile_scope_patterns.json` | JSON object with keys `meta`, `patterns` |
| `ci/prompt_surface.py` | Render the model-facing prompt surface of a checkout, deterministically. |
| `ci/python_packages.py` | Prepare isolated CI tools, then export their Python or run it directly. |
| `ci/required_results.py` | Strict CI aggregate gate (shared by ci.yaml and the stable orchestrator). |
| `ci/setup_toolchain.py` | GitHub Actions file commands around the real, stdlib-only PM bootstrap. |
| `ci/start_test_sshd.sh` | Start a throwaway sshd container for the real SSH terminal-backend tests. |
| `ci/test_sshd_container_setup.sh` | Runs INSIDE the throwaway sshd container started by scripts/ci/start_test_sshd.sh (mounted read-only at /setup). Expects the keys at /keys: host_ed25519{,.pub} and authorized_keys. Installs openssh-server, adds user `he… |
| `ci/timings_report.py` | Collect CI timings and cache transfers from GitHub and generate an HTML diff report. |
| `code_health/__init__.py` | Code-health ratchet: per-unit caps that only go down. Entry point: ``scripts/check``. |
| `code_health/__main__.py` | Python module: `__main__` |
| `code_health/cli.py` | ``python -m scripts.code_health`` / ``scripts/check``: the code-health ratchet. |
| `code_health/compare.py` | Base vs head: the ratchet verdict. |
| `code_health/config.py` | Targets, file scope and the rule table: the one place a rule's id, scope and fix text live. |
| `code_health/gitio.py` | Git plumbing: which files changed between two trees, and their contents on either side. |
| `code_health/measure.py` | Measure a set of files in one tree (a revision or the working tree). |
| `code_health/model.py` | Data shapes shared by the measurers and the comparison. |
| `code_health/py_ast.py` | AST helpers shared by the HX checkers (``py_rules`` and its ``py_rules_*`` siblings). |
| `code_health/py_rules.py` | Hermes-specific AST rules (the ``HX`` ids in ``config.RULES``). |
| `code_health/py_rules_sleep.py` | HX013: a wall-clock sleep in a test (registered in ``py_rules.CHECKERS``). |
| `code_health/py_structure.py` | Python structure: functions (qualname, length, nesting, body hash) and scope lookup. |
| `code_health/replay.py` | Replay the ratchet over recently merged PRs: what would it have blocked? |
| `code_health/report.py` | Allow comments and the agent-facing report. |
| `code_health/ruff_runner.py` | Run the pinned ruff and split its output into per-function CC and pattern hits. |
| `code_health/ts_measure.py` | TypeScript measurement: runs ``ts_units.mjs`` under node with the lockfile's typescript. |
| `code_health/ts_units.mjs` | TypeScript structure for the code-health ratchet: per-function CC, length, nesting. Parses only (no type check), so it is fast and needs nothing but the `typescript` package. node ts_units.mjs <typescript-module-path> <… |
| `contributor_audit.py` | Contributor Audit Script |
| `desktop-update.ps1` | COMPAT FORWARDER — do not add logic here. |
| `desktop-update/marker-claim.ps1` | marker-claim.ps1 -- claim / delegate / release / heartbeat / helper ops of the update marker, dot-sourced by marker.ps1 (still before any Add-Type). Every function here mutates the marker only inside one Open-MarkerLock… |
| `desktop-update/marker.ps1` | marker.ps1 -- the update marker (contract C1 v2, hand-off protocol 2 / A7) for windows.ps1, which dot-sources it as its first act. Pure PowerShell + CIM on purpose: the claim runs before the first Add-Type (CLM, #66753). |
| `desktop-update/marker.sh` | marker.sh -- the update marker for posix.sh, which sources it. Bash 3.2 (macOS /bin/bash) compatible: no associative arrays, no {fd} redirections. |
| `desktop-update/posix.sh` | posix.sh -- repo-owned macOS/Linux Desktop update hand-off. |
| `desktop-update/repro.sh` | repro.sh -- reproduce desktop-update paths against a sandboxed HERMES_HOME. |
| `desktop-update/runtime.ps1` | PowerShell script |
| `desktop-update/serve-ui.py` | Loopback shim server for the desktop update hand-off. |
| `desktop-update/swap-selftest.sh` | swap-selftest.sh -- posix.sh --self-test-swap-interrupt (tests only). Bash 3.2 (macOS /bin/bash) compatible. shellcheck shell=bash disable=SC2034 # sets posix.sh globals its mac_swap reads |
| `desktop-update/ui.html` | HTML page/template |
| `desktop-update/update-job.ps1` | update-job.ps1 -- the Win32 job/process helper windows.ps1 runs every hermes step through (dot-sourced after the marker claim, never before it: Add-Type is not allowed in the claim path). StartAssigned creates the step |
| `desktop-update/update-panel.js` | Clone of ui.html for systems without chromium. /usr/bin/osascript -l JavaScript update-panel.js <status-file> Must remain here, next to posix.sh. The desktop spawns this directory as-is (see resolvePosixScriptHandoff) a… |
| `desktop-update/windows.ps1` | windows.ps1 -- repo-owned Windows Desktop update hand-off. |
| `dev-minimal-sandbox.sh` | Preserve this entrypoint's separate identity without duplicating sandbox lifecycle. |
| `dev-sandbox.sh` | Run a Hermes instance in an isolated sandbox — separate HERMES_HOME, separate Electron userData, and a distinct Desktop app name so it doesn't compete with your main desktop instance's single-instance lock. |
| `discord-voice-doctor.py` | Discord Voice Doctor — diagnostic tool for voice channel support. |
| `docker_config_migrate.py` | Run Docker boot-time config migrations safely. |
| `docker_rebootstrap_nous_session.py` | Boot-time re-seed of a terminally-dead Nous bootstrap session. |
| `dump_desktop_slash_registry.py` | Regenerate apps/desktop/src/lib/desktop-slash-registry.json from COMMAND_REGISTRY. |
| `e2e_shared_metrics_staging.py` | Live staging E2E for the shared-metrics exporter. |
| `gen-bootstrap-pins.py` | Generate the bootstrap pin fragments inside the installers. |
| `gen_gateway_command_parity.py` | Regenerate website/docs/developer-guide/gateway-command-parity.md from the code. |
| `gen_gateway_contracts.py` | Render ``tui_gateway/contracts`` into TypeScript and OpenRPC. |
| `generate-icons.mjs` | Exports `generateIcons` |
| `generate_conformance_vectors.py` | Conformance-vector generator — the native adapters as executable spec. |
| `generate_icons.py` | Generate every app icon in the repo from the nous-girl art + platform backgrounds. |
| `hermes-gateway` | Historical script entry; service policy belongs to ``hermes gateway``. |
| `install.cmd` | Data/support file |
| `install.ps1` | Hermes Agent bootstrap: git checkout + venv + hermes command on PATH. Heavy dependencies (tool binaries, browsers, node) are pm's job after this: `hermes pm install`. Stage protocol kept for Hermes-Setup: |
| `install.sh` | Hermes Agent bootstrap: clone, acquire uv/Python, then hand the checkout to the same completion an update runs -- command publication, product builds and post-build maintenance -- so a fresh install and a finished updat… |
| `iso-certify.py` | iso-certify — AC-4 dashboard turn-isolation certify harness. |
| `keystroke_diagnostic.py` | Diagnose how prompt_toolkit identifies keystrokes in the current terminal. |
| `kill_modal.sh` | Kill all running Modal apps (sandboxes, deployments, etc.) |
| `launch_capture_probe.sh` | Probe-the-probe for launch-capture/sitecustomize.py, no real install needed. Control rows FIRST: without the opt-in env var, and for non-launch argv shapes, subprocess.run must behave untouched. Then treatment rows: both |
| `lint_diff.py` | Diff ruff + ty diagnostic reports between two git refs. |
| `micro_compaction_report.py` | Summarize micro-compaction telemetry from Hermes logs. |
| `msix-shared.mjs` | Native MSIX identity/version derivation and artifact content types. App Installer XML and feed publication belong to scripts.bundles.release_artifacts. |
| `observability/gateway_health_export_probe.py` | Exercise Gateway Health & Diagnostics Export against a local OTLP capture collector. |
| `observability/otel_capture_collector.py` | Tiny local OTLP/HTTP capture collector for Hermes gateway health smoke tests. |
| `probe_active_session_exclusivity.py` | Cross-process falsification of the per-session fence. |
| `profile-tui.py` | Drive the Hermes TUI under HERMES_DEV_PERF and summarize the pipeline. |
| `release-content-types.json` | JSON object with keys `.appinstaller`, `.html`, `.msixbundle`, `.msix`, `.deb`, `.gz` |
| `release.py` | Hermes Agent release entrypoint. |
| `releases/authors.py` | Map commit authors to GitHub logins for release notes and attribution checks. |
| `releases/authors_legacy.py` | Frozen legacy commit-email → GitHub login mappings. Data only; never append. |
| `releases/bundle_env.py` | Non-secret environment defaults and explicit clears carried by a desktop bundle. |
| `releases/channel_build.py` | Channel dispatch: the local command names intent; CI allocates and builds. |
| `releases/channel_disposable.py` | Privileged allocation: probe CAS/CDN and allocate the channel this run builds. |
| `releases/channel_publish.py` | Admit channel requests and publish only complete, native-smoked build manifests. |
| `releases/channel_releases.py` | Advance protected R2 heads from the release transaction's accepted native bytes. |
| `releases/channels.py` | Authenticated channel administration; mutable records use ETag CAS, never CDN state. |
| `releases/commit_build.py` | Admit and dispatch tagless builds without changing release channels. |
| `releases/darwin.py` | Validate and conditionally publish macOS update feeds. |
| `releases/dispatch_log.py` | Print the release.py command and receipt identity for this bundle run. |
| `releases/distance.py` | Dev-install version distance, counted from a release tag rather than a claim. |
| `releases/docker.py` | Validate staged Docker artifact identities and publish receipts. |
| `releases/draft_warning.py` | Fenced draft-body warning and its strip, shared by the entrypoint and publish. |
| `releases/entrypoint.py` | The thin release entrypoint: claim an attempt, cut the draft, dispatch the gate. |
| `releases/handoff.py` | Transfer immutable release files through R2 without publishing a feed. |
| `releases/job_groups.py` | The desktop-bundled-release `jobs` input: one parser for the job groups. |
| `releases/lanes.py` | The stable release lanes, defined once. |
| `releases/pick_tags.py` | Sample installed release baselines by creation time across version schemes. |
| `releases/progress.py` | Progress logging for release automation. |
| `releases/r2.py` | Stream and verify release objects through the signed R2 transport. |
| `releases/r2_multipart.py` | Multipart transport for release files larger than a single upload part. |
| `releases/r2_scope.py` | Disposable CI namespaces at the object-key boundary, never in bucket names. |
| `releases/semver.py` | Compare stable and canary versions accepted by release feeds. |
| `releases/sequencer.py` | Discover and reconcile stable releases in version order. |
| `releases/stable.py` | Stable release admission, signed-package transitions and final release receipt. |
| `releases/stamping.py` | Stamp only release metadata consumed by external package builders. |
| `releases/store.py` | Store submission control for the release pipeline. |
| `releases/upload_summary.py` | Record each verified R2 upload for the GitHub job summary. |
| `releases/versioning.py` | Ref name to version, and the next version from the published stable head. |
| `render-builds-table.py` | Render the release download tables into <!-- HERMES_BUILDS_TABLE -->, and the same rows as standalone pages in the bucket. |
| `run-in-hermes-env` | Run a command in the Hermes dev environment, whatever shell or cwd it is launched from: `scripts/run-in-hermes-env CMD [ARGS...]`. |
| `run_tests.sh` | Canonical test runner for hermes-agent. Run this instead of calling `pytest` directly to guarantee your local run matches CI behavior. |
| `run_tests_parallel.py` | Per-file parallel test runner. |
| `sample_and_compress.py` | Sample and Compress HuggingFace Datasets |
| `sandbox/generate-e2e-matrix.mjs` | Exports `legId`, `bundledMatrix`, `startsFor`, `SPEC`, `expandMethod`, `generateEnvironments` … |
| `sandbox/pick-release-tags.sh` | Pick the release tags the install/update E2E should update FROM. |
| `scan_plugin_payloads.py` | Scan a pinned plugin tree for unscannable executable payloads (catalog rule 17). |
| `smoke-payload.sh` | Exercise the published launch contract after relocation. Network isolation is the runner's responsibility (Linux CI uses unshare --net), not a lazy-deps flag. |
| `smoke_nemo_relay_shared_metrics.py` | Run a real Hermes CLI turn and validate the Relay shared-metrics output. |
| `stage-msixbundle.mjs` | JavaScript (ES module): `stage-msixbundle` |
| `termux/assembly_permissions.sh` | Host-side ownership handoff for the disposable environment assembly mount. |
| `termux/build.py` | Build the TUI and package a prepared bionic payload as a Termux .deb. |
| `termux/build_builder_image.sh` | Build + push the derived termux builder image (toolchain pre-baked). |
| `termux/build_config.sh` | Build constants for the termux wheelhouse / .deb pipeline. |
| `termux/build_cpython.sh` | Stage the pinned bionic CPython (pm package `python`, linux-arm64-bionic lock row -- a TUR .deb) into <payload>/python/. Thin wrapper around the shared termux_pkg_build.sh; pm owns the pins. |
| `termux/build_deb.sh` | Fat .deb assembly for the Termux hermes-agent bundle (Task 4 of .hermes/plans/2026-08-31_termux-deb.md). Runs AFTER termux_build.sh (wheelhouse) and build_cpython.sh / build_node.sh have populated the |
| `termux/build_environment.py` | Wire staged bionic inputs to PM without exposing its installer executable. |
| `termux/build_node.sh` | Stage the pinned bionic node (pm package `node`, linux-arm64-bionic lock row -- the termux-main nodejs .deb) into <payload>/node/. Thin wrapper around the shared termux_pkg_build.sh; pm owns the pins. |
| `termux/build_uv.sh` | Stage the pinned bionic uv (pm package `uv`, linux-arm64-bionic lock row -- the termux-main uv .deb) into <payload>/uv/. Same pm-consumer shape as build_cpython/build_node: pm owns the pin, the download, the hardened |
| `termux/build_wheels.py` | Container-side wheelhouse build: build the android build set from sdist against THIS container's bionic python, retag, and run the offline completeness + import gates. Invoked by termux_build.sh inside the digest-pinned… |
| `termux/check_apt.sh` | Verify the signed repository with the same non-root APT used on a phone. |
| `termux/check_deb.sh` | Install and test the real package in a fresh, offline Termux rootfs. |
| `termux/deb_version.py` | Derive a Debian package version (or channel) from a hermes-agent release tag. |
| `termux/launchers.py` | APT maintainer hooks; agent entrypoints belong to scripts.build.launchers. |
| `termux/payload_facts.py` | Record bionic tools and assemble the prepared fixed-prefix agent. |
| `termux/python_linkage.py` | Link Python extensions explicitly for bionic's local symbol lookup. |
| `termux/retag_wheel.py` | PEP 738 wheel retagger for the Termux/Android wheelhouse. |
| `termux/stage_apt_repo.py` | Stage a static APT repository layout (dists/ + pool/) from a pool of .debs. |
| `termux/stage_runtime_libs.py` | Stage the termux runtime libs into <payload>/runtime-libs/lib/. |
| `termux/termux-builder.Dockerfile` | Docker image build recipe |
| `termux/termux_build.sh` | Android/Termux wheelhouse builder -- the ONE entry point. Two halves: |
| `termux/termux_pkg_build.sh` | Stage the pinned bionic python/node .debs into the payload, via pm. |
| `termux/validate_installed.py` | Exercise a freshly installed Termux bundle with networking disabled. |
| `termux/wheelhouse_cache.py` | The wheelhouse manifest is the proof used to admit restored build output. |
| `tests/test-install-ps1-longpath.ps1` | Tests for install.ps1's 8.3 short-path normalization. |
| `tests/test-install-ps1-node-compatibility.ps1` | PM owns Node provisioning. Verify the pre-Python bootstrap handoff. |
| `tests/test-install-ps1-store-guard.ps1` | Tests for install.ps1's HermesHome/InstallDir separation guard (#124526). |
| `tests/test-install-ps1-utf8.ps1` | Regression: uv's UTF-8 stdout must remain an executable path under PS 5.1. The existing test_install_ps1_script_suites.py runs this under 5.1 and 7. Native fixtures write raw bytes to a pipe: a PowerShell function retur… |
| `tool_store_pins.py` | Exit 0 only when a tool store already holds this checkout's pins. |
| `update-test/HANDOFF.md` | testing the bundles branch against your normal hermes install |
| `update-test/hermes-update-rehearsal.ps1` | PowerShell script |
| `update-test/hermes-update-rehearsal.sh` | hermes-update-rehearsal.sh — for an EXISTING Hermes install. |
| `update-test/smoke-test.ps1` | PowerShell script |
| `update-test/smoke-test.sh` | Smoke test for hermes-update-rehearsal.sh (this directory). Builds a synthetic install in a temp tree and drives pre/post/status for real. Runs on macOS/Linux directly, and under git-bash on Windows (native paths). |
| `validate_plugin_catalog.py` | Standalone structural validator for plugin-catalog entry files. |
| `verify-bootstrap-version-stamp.py` | Verify the version stamp a bootstrap installer ships. |
| `whatsapp-bridge/allowlist.js` | Exports `normalizeWhatsAppIdentifier`, `parseAllowedUsers`, `expandWhatsAppIdentifiers`, `matchesAllowedSender`, `matchesInboundWhatsAppGroup`, `matchesAllowedUser` |
| `whatsapp-bridge/allowlist.test.mjs` | Tests: normalizeWhatsAppIdentifier strips jid syntax and plus prefix; expandWhatsAppIdentifiers resolves phone and lid aliases from session files; matchesAllowedUser accepts mapped lid sender when allowlist only contain… |
| `whatsapp-bridge/bridge.js` | JavaScript source: `bridge` |
| `whatsapp-bridge/bridge.native.test.mjs` | Unit tests for WhatsApp-native bridge payload helpers. These tests avoid importing bridge.js because that file starts an HTTP server and Baileys socket at module load. Keep the helper module pure. |
| `whatsapp-bridge/bridge.reconnect.test.mjs` | Unit tests for the reconnect scheduling and version resolution guards. Regression tests for the reconnect-wedge trap: startSocket() awaits network I/O (fetchLatestBaileysVersion has no AbortSignal) before it creates a s… |
| `whatsapp-bridge/bridge_helpers.js` | Exports `MIME_MAP`, `normalizeWhatsAppId`, `getMessageContent`, `getContextInfo`, `createBoundedMessageStore`, `createQuotedMediaCache` … |
| `whatsapp-bridge/bridge_helpers.timestamp.test.mjs` | Unit tests for the bridge's log-line stamping: formatLogStamp, installConsoleStamps and writeJsonLine. Regression for issue #97021: startup/connection lifecycle console.log/ console.warn lines (bridge listening, connect… |
| `whatsapp-bridge/delivery_status.test.mjs` | Delivery/read status events for messages Hermes sent (logged to gateway.log by the adapter). |
| `whatsapp-bridge/outbound_ids.js` | Bounded FIFO set of outbound message IDs. Used by the WhatsApp bridge to distinguish "echo of our own /send" from "owner-typed message on the linked device" when forwarding `fromMe` inbound events back to the Python ada… |
| `whatsapp-bridge/outbound_ids.test.mjs` | Tests: remembers and recognises an outbound id; ignores empty / falsy ids; evicts oldest entry once the cap is exceeded; rejects non-positive maxSize |
| `whatsapp-bridge/owner_message_gate.js` | Pure classifier for the WhatsApp bridge's bot-mode dispatch loop. Centralises the "should this fromMe message be forwarded as fromOwner?" decision so the gate can be unit-tested without spinning up Baileys or the Expres… |
| `whatsapp-bridge/owner_message_gate.test.mjs` | Tests: non-fromMe messages always pass through; fromMe echo of our own /send is dropped; fromMe is dropped when forwarding is disabled; fromMe is dropped when chatId is not on the allowlist (regression) |
| `whatsapp-bridge/package-lock.json` | npm dependency lock file |
| `whatsapp-bridge/package.json` | `hermes-whatsapp-bridge` — WhatsApp bridge for Hermes Agent using Baileys |
| `windows-build-deps.ps1` | Native build dependencies are separate from PM's application environment. An interactive console sees one status line per build command, with the full output in $script:HermesBuildLog; CI and a redirected stdout (pm und… |
| `windows_e2e_harness.ps1` | Local harness for windows-e2e.ps1's non-GUI logic, runnable under linux pwsh (nix run nixpkgs#powershell). Exercises the pieces that cost CI round-trips when wrong: parameter surface, ref-flag probing, and the |
| `write_install_stamp.py` | Generate canonical install-stamp.json for packaged Hermes builds. |
