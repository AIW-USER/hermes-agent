# File reference: `apps`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `apps/bootstrap-installer/`

| File | What it does |
|---|---|
| `.gitignore` | Rust / Cargo |
| `eslint.config.mjs` | JavaScript (ES module): `eslint.config` |
| `index.html` | HTML page/template |
| `package.json` | `@hermes/bootstrap-installer` — Hermes Setup — signed installer that drives scripts/install.ps1 with a polished native UI. |
| `public/nous-girl.png` | PNG image asset |
| `src-tauri/Cargo.toml` | TOML configuration |
| `src-tauri/Info.plist` | macOS property list |
| `src-tauri/build.rs` | Rust source file |
| `src-tauri/capabilities/default.json` | Capabilities required by Hermes Setup. Narrowly scoped: we don't write user files outside HERMES_HOME, we don't read arbitrary paths, and the only external network call goes through reqwest (Rust side, not exposed to th… |
| `src-tauri/entitlements.plist` | macOS property list |
| `src-tauri/hermes-setup.manifest` | Data/support file |
| `src-tauri/icons/128x128.png` | PNG image asset |
| `src-tauri/icons/128x128@2x.png` | PNG image asset |
| `src-tauri/icons/32x32.png` | PNG image asset |
| `src-tauri/icons/icon.icns` | macOS icon bundle |
| `src-tauri/icons/icon.ico` | Icon file |
| `src-tauri/icons/icon.icon/Assets/art-dark.png` | PNG image asset |
| `src-tauri/icons/icon.icon/Assets/art-light.png` | PNG image asset |
| `src-tauri/icons/icon.icon/Assets/mono.png` | PNG image asset |
| `src-tauri/icons/icon.icon/icon.json` | JSON object with keys `fill-specializations`, `groups`, `supported-platforms` |
| `src-tauri/src/bootstrap.rs` | ! Bootstrap orchestration. ! ! Direct port of `runBootstrap` from `apps/desktop/electron/bootstrap-runner.ts`. |
| `src-tauri/src/events.rs` | ! Event types streamed from Rust → React. ! ! These mirror `apps/desktop/electron/bootstrap-runner.ts`'s event shape |
| `src-tauri/src/install_script.rs` | ! Resolves and downloads `scripts/install.ps1` (and `install.sh`). ! ! Resolution order: |
| `src-tauri/src/lib.rs` | ! Hermes Setup — Tauri entrypoint. ! ! Spawns a single window pointed at the React frontend (apps/bootstrap-installer/src/). |
| `src-tauri/src/main.rs` | Hermes Setup — process entrypoint. All logic lives in lib.rs so it can be unit-tested as a library; this file just calls into it. The windows_subsystem attribute MUST live here on the binary crate |
| `src-tauri/src/marker.rs` | ! The "update in progress" marker: the Desktop launch gate and the ! cross-process update lock shared with `hermes_cli/update_lock.py` and the ! Electron gate (`apps/desktop/electron/update-marker.ts`). |
| `src-tauri/src/marker_tests.rs` | ! `marker.rs` tests (split out to keep the module under the size gate). |
| `src-tauri/src/paths.rs` | ! Filesystem paths + logging setup. ! ! Mirrors `hermes_constants.get_hermes_home()` from the Python CLI: |
| `src-tauri/src/powershell.rs` | ! Drives PowerShell (Windows) or bash (Unix) for install.ps1 / install.sh. ! ! Port of `spawnPowerShell` from bootstrap-runner.ts, with the same |
| `src-tauri/src/update.rs` | ! Update orchestration. ! ! Driven when the installer is launched as `Hermes-Setup.exe --update` (see |
| `src-tauri/tauri.conf.json` | JSON object with keys `$schema`, `productName`, `version`, `identifier`, `build`, `app` |
| `src/app.tsx` | App shell — Hermes Setup. No header chrome (the OS title bar already says "Hermes Setup"; an in-window repeat of the H mark + words was redundant slop). Route state lives in a single $route atom — 4 screens, no react-ro… |
| `src/components/brand-mark.tsx` | Exports `BrandMark` |
| `src/components/button.tsx` | Button — copied verbatim from apps/desktop/src/components/ui/button.tsx. We import the desktop's local shadcn-style Button rather than |
| `src/components/hackery-button.tsx` | HackeryButton — the onboarding "Begin" CTA, ported standalone. Bracketed [ LABEL ], mono/uppercase, primary accent on a --stroke-nous hairline. Lifted from apps/desktop's desktop-onboarding-overlay.tsx (sans the exit-sc… |
| `src/components/loader.tsx` | Loader — the desktop's "Fourier Flow" curve, ported standalone. The shim can't import apps/desktop's 559-line multi-curve <Loader> (cross-app coupling + bundle bloat that defeats the point of a lightweight installer), s… |
| `src/lib/format.ts` | Duration formatters for the stage list. Pure functions, no React — kept out of progress.tsx so tests-js can exercise them without dragging in the Tauri renderer. |
| `src/lib/utils.ts` | cn — Tailwind-aware class merger. Same util the desktop and dashboard use. clsx handles conditional classes; twMerge resolves utility conflicts so `cn('px-2', condition && 'px-4')` ends up with px-4 only, not both. |
| `src/main.tsx` | Follow the OS light/dark appearance. theme.ts paints the first frame on import (synchronously, from the media query); this subscribes to live OS theme changes via the authoritative Tauri window theme. |
| `src/routes/failure.tsx` | Exports `Failure` |
| `src/routes/progress.tsx` | Exports `ProgressScreen` |
| `src/routes/success.tsx` | Success screen. HERMES AGENT wordmark stays as the visual anchor (same Collapse Bold treatment as Welcome + the desktop chat intro), with a status line below. Launching the desktop can fail (e.g. Stage-Desktop was skipp… |
| `src/routes/welcome.tsx` | Welcome screen. Mirrors the desktop's chat intro (apps/desktop/src/components/chat/intro.tsx): - HERMES AGENT wordmark rendered in Collapse Bold, uppercase, tracked - mix-blend-plus-lighter so the type "glows" on the ca… |
| `src/store.ts` | Bootstrap state store — single source of truth for installer screens. Lives in nanostores per the project's TypeScript guidelines (apps/desktop AGENTS.md): "Prefer small nanostores over component state when state is sha… |
| `src/styles.css` | Hermes Setup — defer entirely to the desktop's styles.css. Rather than re-implement the Hermes design system (and inevitably drift from it), we import apps/desktop/src/styles.css wholesale. The desktop is the canonical… |
| `src/theme.ts` | OS appearance follower. The installer ships no in-app theme switcher, so it tracks the system the way the desktop overlays do. Two Tauri realities shape this: 1. The strict `script-src 'self'` CSP (tauri.conf.json) forb… |
| `src/vite-env.d.ts` | TypeScript source: `vite-env.d` |
| `tsconfig.json` | JSON object with keys `compilerOptions`, `include`, `references` |
| `tsconfig.node.json` | JSON object with keys `compilerOptions`, `include` |
| `vite.config.ts` | Hermes Setup — Tauri-targeted Vite config. Port 5175 keeps us out of the way of: web (vite default 5173) |

## `apps/desktop/`

| File | What it does |
|---|---|
| `AGENTS.md` | Desktop Engineering Guide |
| `BUILDING.md` | Building the Desktop Installers |
| `DESIGN.md` | Desktop Design System |
| `ENGINEERING.md` | Desktop engineering: the long form |
| `README.md` | Hermes Desktop ☤ |
| `assets/appx/Square150x150Logo.png` | PNG image asset |
| `assets/appx/Square150x150Logo.scale-125.png` | PNG image asset |
| `assets/appx/Square150x150Logo.scale-150.png` | PNG image asset |
| `assets/appx/Square150x150Logo.scale-200.png` | PNG image asset |
| `assets/appx/Square150x150Logo.scale-400.png` | PNG image asset |
| `assets/appx/Square44x44Logo.png` | PNG image asset |
| `assets/appx/Square44x44Logo.scale-125.png` | PNG image asset |
| `assets/appx/Square44x44Logo.scale-150.png` | PNG image asset |
| `assets/appx/Square44x44Logo.scale-200.png` | PNG image asset |
| `assets/appx/Square44x44Logo.scale-400.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-16.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-16_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-16_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-20.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-20_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-20_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-24.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-24_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-24_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-256.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-256_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-256_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-30.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-30_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-30_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-32.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-32_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-32_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-36.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-36_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-36_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-40.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-40_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-40_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-48.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-48_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-48_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-60.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-60_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-60_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-64.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-64_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-64_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-72.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-72_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-72_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-80.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-80_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-80_altform-unplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-96.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-96_altform-lightunplated.png` | PNG image asset |
| `assets/appx/Square44x44Logo.targetsize-96_altform-unplated.png` | PNG image asset |
| `assets/appx/StoreLogo.png` | PNG image asset |
| `assets/appx/StoreLogo.scale-125.png` | PNG image asset |
| `assets/appx/StoreLogo.scale-150.png` | PNG image asset |
| `assets/appx/StoreLogo.scale-200.png` | PNG image asset |
| `assets/appx/StoreLogo.scale-400.png` | PNG image asset |
| `assets/appx/Wide310x150Logo.png` | PNG image asset |
| `assets/appx/Wide310x150Logo.scale-125.png` | PNG image asset |
| `assets/appx/Wide310x150Logo.scale-150.png` | PNG image asset |
| `assets/appx/Wide310x150Logo.scale-200.png` | PNG image asset |
| `assets/appx/Wide310x150Logo.scale-400.png` | PNG image asset |
| `assets/icon-dark.icns` | macOS icon bundle |
| `assets/icon-dark.ico` | Icon file |
| `assets/icon-dark.png` | PNG image asset |
| `assets/icon-mac.png` | PNG image asset |
| `assets/icon.icns` | macOS icon bundle |
| `assets/icon.ico` | Icon file |
| `assets/icon.icon/Assets/art-dark.png` | PNG image asset |
| `assets/icon.icon/Assets/art-light.png` | PNG image asset |
| `assets/icon.icon/Assets/mono.png` | PNG image asset |
| `assets/icon.icon/icon.json` | JSON object with keys `fill-specializations`, `groups`, `supported-platforms` |
| `assets/icon.png` | PNG image asset |
| `assets/msix-manifest.xml` | XML file |
| `components.json` | JSON object with keys `$schema`, `style`, `rsc`, `tsx`, `tailwind`, `aliases` |
| `docs/canonical-gateway-protocol.md` | Canonical local gateway protocol |
| `docs/canonical-groups.md` | Gateway-owned groups in Desktop |
| `e2e/at-rest-connection-token.spec.ts` | E2E at-rest contract for the remote-gateway session token (issue #77486). The reported bug: configuring a remote gateway persisted the dashboard session token as PLAINTEXT into `connection.json` under the app's userData… |
| `e2e/batch-clarify.spec.ts` | E2E batch clarify test — the multi-question clarify card must mount ONCE. Regression coverage for the duplicated-card bug: `tool.start` carries the model's tool_call_id while `clarify.request` carries a gateway-generate… |
| `e2e/boot-failure.spec.ts` | E2E boot-failure tests — verify the app shows an error overlay when the backend can't start. Injects a fake boot error (HERMES_DESKTOP_BOOT_FAKE_ERROR) so the backend resolution fails with a controlled error message. Th… |
| `e2e/boot.spec.ts` | E2E smoke tests for the dev-mode desktop app. These tests launch the Electron app from the built dist/ (not the packaged binary) with a real `hermes serve` backend pointed at a mock inference server. The full chain is e… |
| `e2e/bot-screen-stale-status-reply.spec.ts` | Tests: a stale portal display.status reply does not roll back the newer stopped state; pushed display.status / display.lease events keep updating the shipped listeners without a page error |
| `e2e/chat.spec.ts` | E2E chat tests — send a message and verify a response appears. Requires the full boot chain to complete (hermes serve + mock inference provider). The mock server returns a canned reply, so we verify the response text sh… |
| `e2e/completed-reply-refresh.spec.ts` | Real Electron, backend, SQLite and stream. Only delivery of one real history request is delayed: admit while idle, read while the next turn is held, then deliver after completion. The mock provider intentionally repeats… |
| `e2e/connection-version-label.spec.ts` | The status bar's client version label follows the ACTIVE connection. Two loopback fake gateways registered in connections.json (v2): A is the primary (reports 0.21.5), B is a second remote (reports 0.22.1, display 0.22.… |
| `e2e/core/README.md` | Desktop core suite (required CI lane) |
| `e2e/core/behind-window-send.spec.ts` | C2 core: a send from a window that is behind its chat goes through. Two Desktop windows on one chat. Window 2 stops hearing window 1's "turn finished" pings (the cross-window transcript bus is held in that window), so w… |
| `e2e/core/boot-lifecycle.spec.ts` | C5 core: boot handshake and backend process lifecycle. Real Electron + real `hermes serve`; only the LLM is faked. Process facts come from a /proc census of every process carrying this sandbox's HERMES_HOME (so an orpha… |
| `e2e/core/fleet-condensed-default.spec.ts` | Every gateway's default profile has a door in the condensed profile menu (#106017, #131632). A second registered gateway puts the sidebar rail in fleet mode, which drops the default ↔ all home pill; past the condensed t… |
| `e2e/core/harness.ts` | Lane-private harness for the core Desktop suite: an isolated sandbox with a fake HOME, a launch helper, a per-socket WebSocket recorder, a /proc-based process census for the backend, and the transcript oracle. Synchroni… |
| `e2e/core/interactive-prompts.spec.ts` | C20 core: blocking interactive prompts round-trip through the real chain. Real Electron + real `hermes serve`, approvals in manual mode; only the LLM is faked. For each prompt kind the invariant is end to end, not "a ca… |
| `e2e/core/interrupted-reply.spec.ts` | Stop mid-stream: the reply on screen is the reply the session saved (#121594). Stop seals the live bubble at the click and the renderer drops every later message.delta, but the agent keeps streaming until it honours the… |
| `e2e/core/known.ts` | KNOWN bugs for the core suite: merge-order-safe expected failures, the Playwright twin of tests/e2e/core/_pending_fixes.py::known_failure. A strict marker (`test.fail()` up front, or an XPASS error) turns main red the m… |
| `e2e/core/lineage-compaction-prompt.spec.ts` | #121088 — an acknowledged Desktop prompt is appended a second time, after its own reply, when refreshed history carries synthetic user-role rows written by an in-place compaction inside that prompt's turn. Mechanism (ap… |
| `e2e/core/lineage-rotation.spec.ts` | #121148 with REAL rotated session rows: one Electron app + one `hermes serve`, only the LLM is faked. `compression.in_place: false` + a low `threshold_tokens` make the backend's own auto-compaction rotate the live conve… |
| `e2e/core/lineage-sidebar.spec.ts` | Session lineage and sidebar integrity for branches. One real Electron app + one real `hermes serve`; only the LLM is faked. - a branch child is born with a title (#121062) and is a sidebar row of its own; - switching be… |
| `e2e/core/local-gateway-attach.spec.ts` | Desktop attaching to a local gateway that was already running (#134889 W3). The shape every Windows login item, `hermes gateway run` console and CLI session leaves behind: the profile's gateway is up BEFORE the Desktop… |
| `e2e/core/no-idle-reap.spec.ts` | Support f502bc6f: a "This device" profile's local backend was SIGTERM'd by the Desktop pool idle reaper (60 min with nothing streamed), leaving "This device · Backend offline". A local profile's backend hosts its cron j… |
| `e2e/core/onboarding-first-chat.spec.ts` | C2 core: onboarding completion, then the first chat. Fresh sandbox, NO provider configured: the real first-run onboarding shows. The user picks the local / custom endpoint path and enters the fake provider's URL; the re… |
| `e2e/core/oracle.ts` | The transcript oracle. Invariant, checked after every transition: each persisted user/assistant message is rendered EXACTLY ONCE, in persisted order; nothing scenario-made is rendered that is not persisted; the persiste… |
| `e2e/core/packaged-smoke.spec.ts` | Packaged-build smoke: the artifact users actually run, not the dev tree. Every other core spec launches the dev Electron binary against apps/desktop, so a broken `electron-builder` output (asarUnpack not honoured, the m… |
| `e2e/core/playwright.config.ts` | The core Desktop suite: a small, deterministic, REQUIRED lane. Deliberately different from ../../playwright.config.ts: - retries: 0 — a required job that retries hides exactly the flake it should expose (the old lane re… |
| `e2e/core/process-census.ts` | Process census for the core lane, per platform. Linux reads /proc: a process belongs to a sandbox when its environment names the sandbox HERMES_HOME (orphans reparented to init included). Other platforms have no readabl… |
| `e2e/core/process-census.unit.test.ts` | Tests for `process-census.unit` |
| `e2e/core/provider.ts` | Scripted, recording OpenAI-compatible provider for the core Desktop suite. Unlike the shared tests-js mock (trigger keywords + module-global counters, one of the reasons the old lane drifted), every reply here is keyed… |
| `e2e/core/reattach-running-turn.spec.ts` | C2 core: a window that re-attaches to a turn that is still running. The turn persists its narrated tool round before the tool runs, so the history a re-attaching window fetches already holds that round while the live st… |
| `e2e/core/reconnect-turn-state.spec.ts` | NF2: after a lost connection Desktop shows the turn's REAL state, and a follow-up never hangs behind a turn whose outcome is unknown (#134889 NF2). Real Electron + real gateway; only the LLM is scripted. Three faults: 1… |
| `e2e/core/relay-managed-steer.spec.ts` | C2 core: steering and queueing with NeMo Relay managed execution on. Opting into shared metrics routes every provider stream through Relay's managed pipeline. Relay pulls the next provider chunk before it hands over the… |
| `e2e/core/remote-helpers.ts` | Remote-backend topology for the core suite: a real `hermes serve` the TEST spawns (not the app) under its OWN sandbox HOME / HERMES_HOME / cwd, reached by the Desktop only by URL + token (HERMES_DESKTOP_REMOTE_URL/_TOKE… |
| `e2e/core/remote-secondary.spec.ts` | Bot Mode across two machines (#120730, the reported shape): the Desktop runs its OWN local primary backend (Electron-spawned `hermes serve`, the default profile only) and has a second, REMOTE connection registered in co… |
| `e2e/core/remote-topology.spec.ts` | Remote-backend topology: the Desktop attached by URL + token to a real `hermes serve` it did NOT spawn, running under a different HOME and filesystem root (./remote-helpers.ts). Only the LLM is faked. - first chat over… |
| `e2e/core/reply-painted-once.spec.ts` | C2 core: a reply is painted ONCE inside its bubble, whatever tool round the turn ends on. Report: "Hermes Desktop sometimes duplicates the same agent output twice consecutively within a single message bubble, with no li… |
| `e2e/core/reply-settle-paths.spec.ts` | C2 core: the timings that turn one reply into two bubbles. One stored reply reaches the renderer twice: as live events and again in the history the app fetches on reload, switch-back or reconnect. Each path that merges… |
| `e2e/core/reply-tail-after-reconnect.spec.ts` | A socket drop while the answer after a tool streams must not leave the reply on its first chunk. The reconnect replay (`session.events.since`) is answered before `session.resume` rebinds the new socket, so a turn that c… |
| `e2e/core/switch-back-race.spec.ts` | C2 core: switch back to a session whose reply completes while the switch-back hydrate is in flight. Session B streams (provider held) -> user opens A -> user returns to B. The return issues a REST page read (/api/sessio… |
| `e2e/core/tail-resync-merge.spec.ts` | C2 core: a refreshed newest page merged onto a long chat's live turn. Every settled turn re-reads the newest stored page (120 rows) and merges it onto what the live stream drew. Once a chat holds more rows than one page… |
| `e2e/core/transcript-integrity.spec.ts` | C2 core: transcript integrity across every transition that has shipped a duplicate / vanishing / reordered message bug. One real Electron app + one real `hermes serve` backend (only the LLM is faked, by a scripted recor… |
| `e2e/core/webapp-gateway-attach.spec.ts` | The browser-hosted Desktop is served by the profile gateway's own listener, exactly like local Electron Desktop talks to that gateway: one process runs every turn and owns the profile's store. `webapp.enabled` in the ho… |
| `e2e/correction-session-switch.spec.ts` | Regression coverage for a correction sent during a live response, then a warm session switch away and back. The correction is an accepted user turn, not an optimistic duplicate of the original prompt, and its relative p… |
| `e2e/electron-binary.ts` | Locating the dev Electron binary for the e2e fixtures. Kept in its own module so the resolution rules can be unit-tested without importing the Playwright runner (fixtures.ts pulls in `_electron`, the mock server and the… |
| `e2e/electron-binary.unit.test.ts` | Platform is a parameter everywhere below rather than read from process.platform, so the Windows rules are pinned on the Linux CI runner too. Reading the real platform would leave every Windows-only rule untested. |
| `e2e/fix-electron-tracing.ts` | Monkey-patch: playwright's test runner never calls tracing.start() on Electron's internal BrowserContext because: 1. Playwright._allContexts() only returns [chromium, firefox, webkit] contexts — Electron's context is ex… |
| `e2e/fixtures.ts` | Shared E2E fixtures for the Hermes desktop Playwright suite. Two fixture modes: 1. `mockBackend` — starts a mock inference server, writes a config.yaml that points at it, and launches the desktop app so the full chain (… |
| `e2e/fleet-profile-rail.spec.ts` | E2E: the fleet profile rail with two registered gateways. "This device" is the Electron-managed local backend (mock inference). The second gateway, "Homelab", is a REAL second `hermes serve` this spec spawns with its ow… |
| `e2e/group-approval-click-submits.spec.ts` | #91706: a command-approval card in a Bot Mode group room could highlight the clicked choice but never send it — the footer "Respond" button was off-screen or covered, so the member's hidden session stayed blocked until |
| `e2e/group-member-backend-failure.spec.ts` | Tests: a member whose backend fails the turn is reported at once, not read as busy (#92760); a member that fails after pre-tool text is reported, and that text is not its reply |
| `e2e/group-turn-integrity.spec.ts` | Tests: group follow-up waits for its active member and retains the reply; quiet group still harvests a late answer after sixty observation ticks; a rejected member turn stays visible when the room settles; Stop clears a… |
| `e2e/hidden-history-messages.spec.ts` | E2E regression: desktop resume must hide agent-only transcript rows. Compaction handoffs are active user rows because the model needs them for context continuity. They are not authored chat content, so the desktop trans… |
| `e2e/image-attachment-resume.spec.ts` | Regression coverage for an attached image in a durable session. The gateway persists the turn, the builder exits, and desktop renders it from SessionDB for the first time — the "quit and relaunch" case, where the transc… |
| `e2e/interim-messages.spec.ts` | E2E test for the interim-assistant-message preservation fix (#65919). Reproduces the bug across all three layers (agent core → tui_gateway → desktop renderer): when the agent emits assistant text alongside a tool call,… |
| `e2e/large-session-resume.spec.ts` | Tests: large session resume; cold resume of an unchanged session has one user row and bounded transcript paints; ${resumeKind} resume keeps background inference attached without duplicate messages |
| `e2e/legacy-desktop-history.spec.ts` | Pre-cutover Desktop rows as main writes them (source='desktop', profile stamped, optional Nous user_id), on an install with a second profile that has history of its own. A native HTTP grant covers one profile, so every… |
| `e2e/markdown-overflow.spec.ts` | Tests: constrains prose while tables and code scroll inside their own cards |
| `e2e/messages-below-position.spec.ts` | Tests: messages-below reads stay bounded with real content-visibility groups |
| `e2e/new-bot-config-on-disk.spec.ts` | A bot created from the New Bot dialog WITHOUT a clone source (the "inherited from launch profile" path) must land on disk with a usable `model:` block in its own config.yaml and its introduction turn must actually run —… |
| `e2e/onboarding.spec.ts` | E2E onboarding tests — verify the provider picker appears when no inference provider is configured. Launches the app with an empty config.yaml (no providers). The renderer should detect the unconfigured state and show t… |
| `e2e/peer-device-reset.spec.ts` | A generic peer window inherits its initial owner, not a permanent New session target. Exercise two real gateways; only inference uses the shared mock. Requires the built desktop and a repo venv (or HERMES_DESKTOP_PYTHON… |
| `e2e/profile-soul-missing.spec.ts` | Tests: both SOUL editors explain a missing file and save it without changing personality config |
| `e2e/provider-setup-owner.spec.ts` | Provider setup must keep the Settings owner's gateway AND profile. Two real serve backends; only OpenAI-compatible model discovery is a fixture. Build dist/ separately, then run this spec with HERMES_DESKTOP_PYTHON poin… |
| `e2e/queue-turn-boundary.spec.ts` | A queued prompt must remain local until the current inference turn settles. Hold the first streamed reply open after its first token. This gives the composer a live, busy turn while the user queues a follow-up, then let… |
| `e2e/real-session-builder.ts` | Exports `RealSessionTurn`, `RealSessionSpec`, `RealSession`, `RealSessionBuilder` |
| `e2e/remote-oauth-recovery.spec.ts` | Tests: unsigned gateway ${status} leaves recovery settings usable |
| `e2e/run-tmp-reaper.ts` | Stop the backends E2E runs start, at three points. Desktop dials its backend through `hermes gateway ensure`, which spawns a detached `gateway run` that outlives the app on purpose (production attach mode). Closing the… |
| `e2e/run-tmp-reaper.unit.test.ts` | Tests: stops a killed runner |
| `e2e/run-tmp.ts` | One temp root per Playwright run, removed when the runner exits. Playwright (artifact and stack-trace dirs), the Electron app, its backend and every sandbox mkdtemp under os.tmpdir(), and a run that fails or times out i… |
| `e2e/session-compression-and-queue-stop.spec.ts` | E2E coverage for session compression, which rotates a live backend session. |
| `e2e/sidebar-search-profile-scope.spec.ts` | E2E: sidebar full-text search is keyed to the sidebar's profile. Two real profile homes on This device — `default` and `ssprobe-b` — each hold one durable session. Both transcripts contain the shared word "zebra" only i… |
| `e2e/sidebar-states.spec.ts` | E2E tests for desktop sidebar states — background processes, subagents, and session dot transitions. The mock server returns scripted tool_calls that the agent executes for real (trivial commands + real subagent delegat… |
| `e2e/sticky-prompt-clip.spec.ts` | Tests: the sticky-prompt clip applies to its host without inheriting into the turn |
| `e2e/submit-drift.spec.ts` | Regression coverage for #69578: harmless route-token churn during a send must not make the desktop silently drop the prompt before prompt.submit. |
| `e2e/test.ts` | Extended Playwright test fixture that auto-fails any test if an error banner (notification toast with role="alert") appears in the DOM. The desktop app surfaces errors as `[data-slot="alert"][role="alert"]` elements (se… |
| `e2e/timeline-position.spec.ts` | Native Chromium geometry, without a backend or the app's other scroll observers. |
| `e2e/unread-dot-restart.spec.ts` | E2E test for PERSISTED unread state — the green "Finished — unread" dot must survive an app restart. Regression coverage for the reset-on-restart bug: the unread flag used to live only in the in-memory `$unreadFinishedS… |
| `e2e/update/app-update.spec.ts` | Failure class: APP-DRIVEN UPDATE completes. A user on a healthy local install (scripts/install.sh + `hermes desktop`) sees "Update now" in Settings → About when upstream main moves, clicks it, and the app hands off to t… |
| `e2e/update/build-fail.spec.ts` | Failure class: APP-DRIVEN UPDATE whose Desktop build fails. #124040: the Desktop build failed inside the update takeover's completion stage and the failure was swallowed / kept looping instead of reaching the user. Here… |
| `e2e/update/first-run.spec.ts` | Failure class: FIRST RUN on a healthy install. A user who installed Hermes with scripts/install.sh and built the Desktop app with `hermes desktop` opens the app. It must find that install and go straight to chat — on th… |
| `e2e/update/gates.spec.ts` | The gates' signatures are part of the suite's contract: each must match the exact failing assertion its bug produces and nothing else, or a gate turns an unrelated regression into a silent expected-failure. |
| `e2e/update/gates.ts` | Message-gated gaps for open bugs (the Playwright twin of tests/e2e/core/_pending_fixes.py::known_failure). Wrap ONLY a final assertion, after every wait has settled. When it fails and the failure text matches the bug's… |
| `e2e/update/github-edge.ts` | The GitHub edge for the Desktop update suite: a local stand-in for the two api.github.com resources the source update check reads, answered from the local bare origin, behind an HTTPS forward proxy the install is pointe… |
| `e2e/update/global-setup.ts` | Refuse to run where an update could reach the developer's own Hermes. The cells run `hermes update --gateway`, which stops gateways it can see; CI runners have none, and locally the suite must run in its own PID namespa… |
| `e2e/update/harness.ts` | Harness for the Desktop install/update suite: a REAL local install (made by scripts/install.sh + `hermes desktop --build-only` in the upgrade suite's sandbox, see seed.py), a local bare origin standing in for GitHub, th… |
| `e2e/update/harness.unit.test.ts` | Electron 44 zeroes its processes' /proc/<pid>/environ, so the installed app shows no HERMES_HOME. A copy of node under the install's release dir, started with an empty environment, is that process. |
| `e2e/update/playwright.config.ts` | Desktop install/update suite (PR-time, Linux). Every spec drives the packaged app a real install built, against that install's real backend, and updates it through the app's own "Update now". globalSetup builds the inst… |
| `e2e/update/seed.py` | Seed and reset the real local install the Desktop update suite drives. |
| `e2e/update/update-concurrency.spec.ts` | Failure class: ABOUT PANEL / UPDATE UX — one update at a time, and the panel tells the truth afterwards. #123117: the About panel's update buttons let a second update start while one was already running, and the panel's… |
| `e2e/visual-snapshot.ts` | Visual snapshot helper — wraps `toHaveScreenshot` so visual diffs are reported without failing the test suite. On CI, the JSON reporter + post-test script parse the results and post a summary to the GitHub Actions step… |
| `e2e/warm-resume-jitter.spec.ts` | E2E regression: warm-route resume must not re-render the transcript more than once. When a session is already in the runtime-id cache (the "warm" path in `resumeSession()`), clicking its sidebar row should paint the tra… |
| `e2e/window-input.unit.test.ts` | Tests: does not finish when IPC reports 100% before the window factor settles; reapplies zoom when startup overwrites the first request; awaits the zoom response instead of accepting a truthy Promise |
| `electron-builder.config.cjs` | THE electron-builder configuration — the whole thing, one file. There is no "build" field in package.json: run-electron-builder.mjs always passes --config for this file, so a stray package.json field would be silently |
| `electron/active-runtime-state.test.ts` | Tests: hasValidBootstrapMarker accepts the current schema with a real-looking commit; hasValidBootstrapMarker rejects missing, wrong-schema, and too-short markers; classifyActiveRuntime uses a healthy active runtime eve… |
| `electron/active-runtime-state.ts` | Exports `BootstrapMarkerLike`, `ActiveRuntimeState`, `hasValidBootstrapMarker`, `classifyActiveRuntime` |
| `electron/api-expected-404.test.ts` | Tests: a handler-produced sentinel is recognized; real backend payloads are never mistaken for a sentinel; unwrap rethrows the sentinel as the exact rejection the renderer expects; unwrap passes real responses through u… |
| `electron/api-expected-404.ts` | The `hermes:api` expected-404 seam, shared by the main-process handler and preload so both sides agree on one literal. Electron logs "Error occurred in handler for 'hermes:api'" with a full stack |
| `electron/api-transport.test.ts` | Unit + live-transport tests for the Electron main process's Hermes REST retry policy (#92976 / PR #92977 salvage). The live tests run REAL node http servers that misbehave the way the reported backend does (closing sock… |
| `electron/api-transport.ts` | Shared HTTP transport policy for the Electron main process's Hermes REST helpers (fetchJson / fetchPublicJson / downloadViaTokenToFile). Two concerns live here so they can be unit-tested without Electron: 1. Connection-… |
| `electron/app-icon.test.ts` | Regression: a packaged app.asar can contain a TRUNCATED apple-touch-icon.png (interrupted electron-builder run, partial copy). Electron's BrowserWindow({ icon }) / app.dock.setIcon() decode synchronously and THROW |
| `electron/app-icon.ts` | Validate that a candidate app-icon file exists and decodes as an image. Electron's `new BrowserWindow({ icon })` and `app.dock.setIcon()` decode the file synchronously on the main process and THROW when the bytes are no… |
| `electron/app-installer-file.test.ts` | Tests: stages an actual HTTP descriptor and leaves a valid file intact on download failure |
| `electron/app-installer-file.ts` | Download the descriptor before teardown. Windows verifies the referenced package. |
| `electron/app-relaunch.test.ts` | Tests: a self-relaunch never hands the launcher ready-pipe fd number to the new process; macOS and Windows keep Electron app.relaunch |
| `electron/app-relaunch.ts` | Exports `relaunchApp`, `AppRelauncher`, `createAppRelauncher` |
| `electron/app-updater.ts` | app-updater.ts — the win32 update arm for bundled desktop installs. win32 — the OS App Installer owns the apply. The package was installed from an .appinstaller, which registered the feed URI as the |
| `electron/app-version.test.ts` | Tests: artifact version identity; reports baked channel source version independently of native sequence version; keeps source installs on their runtime version without a fixed package channel; uses the local bootstrap r… |
| `electron/app-version.ts` | Exports `AppVersionInfo`, `packagedReleaseChannel`, `nativeAboutVersion`, `appVersionInfo`, `assertSourceUpdateChannel` |
| `electron/appinstaller-checker.test.ts` | Tests: runAppInstallerChecker; runs python on the script, hidden and with the default deadline; a nonzero exit keeps the checker stdout (the JSON ; a kill at the deadline resolves the caller-unknown shape |
| `electron/appinstaller-checker.ts` | appinstaller-checker.ts Bounded child run for the App Installer update checker (hermes_cli/windows_appinstaller_update.py). The checker runs on the update-check path, so a wedged child must never hang the check: the dea… |
| `electron/application-menu-startup.test.ts` | #115332: a key equivalent routed through the application menu's delegate before any window exists segfaults the macOS shell on the updater relaunch. |
| `electron/application-menu-startup.ts` | Orders the macOS application menu relative to the first BrowserWindow. AppKit routes every key equivalent through the installed application menu's delegate (`_populateFromDelegateWithEventProvider`), and Electron's dele… |
| `electron/backend-child.ts` | backend-child.ts Windows-aware teardown for the desktop's managed backend child process. Node's `child.kill()` only signals the direct child. On Windows a backend that spawned its own grandchildren (a `hermes` REPL, a p… |
| `electron/backend-claim.test.ts` | --- real probe: drives the actual OS helper (PowerShell on the Windows lane) --- |
| `electron/backend-claim.ts` | backend-claim.ts Process start-marker probes used to match backend ownership records against live processes. |
| `electron/backend-connection-state.test.ts` | Tests: an invalidated remote attempt cannot publish a late descriptor; a stale backend exit cannot clear a newer connection attempt; the current backend exit clears its process and connection promise; a stale rejected a… |
| `electron/backend-connection-state.ts` | Exports `BackendConnectionAttempt`, `BackendProcessOwner`, `BackendConnectionState`, `createBackendConnectionState` |
| `electron/backend-descriptor-cache.test.ts` | The descriptor cache never owns a process: an entry is a promise for a gateway descriptor. Two invariants keep concurrent dials and profile mutations honest around the `gateway ensure` await. |
| `electron/backend-descriptor-cache.ts` | Ownership helpers for the main-process descriptor cache (`backendPool` in main.ts): keyed promises for gateway connection descriptors, never process handles. A dial yields at the `gateway ensure` / update-clearance awai… |
| `electron/backend-dial-claim.test.ts` | Tests: BackendDialClaims (#90812); coalesces two concurrent dials for the same (connectionId, profile) onto ONE backend spawn; scopes claims by key: different (connectionId, profile) pairs dial independently; releases t… |
| `electron/backend-dial-claim.ts` | backend-dial-claim.ts Single-owner reconnect/dial claim for backend spawns, keyed by the pool scope key from backendScopeKey(connectionId, profile) (#90812). Why this exists: reconnectGateway()'s in-flight lock lives at… |
| `electron/backend-discovery.ts` | Host-level backend discovery — the Desktop half of multiplex-only. Exactly ONE `hermes serve` runs per HOST and multiplexes every profile, so Desktop must ATTACH to a backend that is already listening and spawn only |
| `electron/backend-env.test.ts` | Tests: backend env scrubs PYTHONPATH and PYTHONHOME; POSIX backend PATH keeps the inherited PATH first and appends missing sane entries; backend runs the store toolchain even after the login-shell PATH is merged in fron… |
| `electron/backend-env.ts` | macOS apps launched from Finder/Dock inherit only /usr/bin:/bin:/usr/sbin:/sbin, which misses Homebrew and user-installed CLI tools (codex, git credential helpers). Hermes' own managed tools need no PATH help — the back… |
| `electron/backend-exit.test.ts` | Tests: backend exit escalation rejects within its bound when no exit or close arrives; a failed escalation is not evidence that the child exited |
| `electron/backend-health.test.ts` | Tests: uses lightweight /api/health for current backends; falls back to /api/status only for old backends without /api/health; does not fall back to heavyweight /api/status for transient health failures; probes health o… |
| `electron/backend-health.ts` | A cold backend boot (plugin discovery + route mounting at web_server import time) can take 45-60s on slower hardware. A 45s deadline makes first-boot readiness a coin flip: every lost race tears down a healthy-but-slow… |
| `electron/backend-ownership.test.ts` | Tests: claim persists the caller-supplied exact identity before resolving; incomplete claims and persisted records are rejected; failed persistence awaits asynchronous cleanup of the exact identity; startup reap drops a… |
| `electron/backend-ownership.ts` | Exports `BackendIdentity`, `BackendOwnershipEntry`, `BackendOwnershipStore`, `BackendOwnershipDeps`, `REAP_ORPHANS_DEADLINE_MS`, `BackendClaim` … |
| `electron/backend-probes-runtime.test.ts` | Tests: the real bootstrap supplies ruamel-only dependencies and rejects foreign-path rescue |
| `electron/backend-probes.test.ts` | Tests for electron/backend-probes.ts. Run with: node --test electron/backend-probes.test.ts (Wired into npm test:desktop:platforms in package.json.) |
| `electron/backend-probes.ts` | Bounded backend probes. A file on disk is not proof of a usable runtime. |
| `electron/backend-ready.test.ts` | Tests for electron/backend-ready.ts. Run with: node --test electron/backend-ready.test.ts (Wired into npm test:desktop:platforms in package.json.) Covers the cold-start port-announcement deadline (issue #50209): the clo… |
| `electron/backend-ready.ts` | `hermes serve` announces HERMES_BACKEND_READY; the legacy `hermes dashboard` backend announces HERMES_DASHBOARD_READY. Accept either so the desktop spawn works against both the headless backend and old/dashboard runtime… |
| `electron/backend-recycle.test.ts` | Tests: recycleOwnedBackendTarget; treats an empty or matching profile as the primary backend; treats any other named profile as a pooled backend; recycleOwnedBackend |
| `electron/backend-recycle.ts` | Recycle the backend behind a code-skew 503 ("Restart required" after `hermes update`). Closing the local tunnel/child is not enough for SSH: `serve --isolated` detaches with setsid/nohup, so a reconnect would reuse the… |
| `electron/backend-release-gate.test.ts` | backend-release-gate.test.ts The #74805 first-attempt race, pinned as a contract on the extracted gate: the desktop must not hand off to the updater while PIDs it signalled are still in the process table, even when the… |
| `electron/backend-release-gate.ts` | backend-release-gate.ts The Windows pre-update unlock gate: after the desktop tree-kills its own backends, decide when it is actually safe to hand off to the updater. Why this exists (#74805): `taskkill /T /F` returns o… |
| `electron/backend-resolution.test.ts` | Tests: installed runtime gate; uses the installed runtime without the flag; skips the installed runtime without probing it when HERMES_DESKTOP_IGNORE_EXISTING=1; honours only the value the CLI exports |
| `electron/backend-resolution.ts` | HERMES_DESKTOP_IGNORE_EXISTING=1 (`hermes desktop --ignore-existing`) keeps Desktop off installed runtimes (ACTIVE_HERMES_ROOT, or the install a published user-bin launcher reports). Backend resolution then falls throug… |
| `electron/backend-spawn-env.test.ts` | Tests: desktopBackendSpawnEnv keeps the base env and stamps stay_alive last |
| `electron/backend-spawn-env.ts` | Exports `desktopBackendSpawnEnv` |
| `electron/backend-start-cancellation.ts` | Cancel a startup wait, and check ownership before invoking its continuation. |
| `electron/backend-start-failure.test.ts` | Tests: latches a LOCAL backend failure so the install-retry loop is broken; never latches a REMOTE failure so recovery stays retryable without a restart; never latches a supervisor-owned respawn failure (it has its own… |
| `electron/backend-start-failure.ts` | backend-start-failure.ts Decides whether a failed primary-backend boot should *latch* into `backendStartFailure`. A latched failure makes every subsequent startHermes() re-throw the cached error without re-attempting th… |
| `electron/bootstrap-failure-copy.ts` | User-facing copy for a failed first-run install (bootstrap). The install runner reports the manifest stage name that failed (see electron/bootstrap-runner.ts and the stage manifests in scripts/install.ps1 / scripts/inst… |
| `electron/bootstrap-platform.test.ts` | Tests: isWslEnvironment detects WSL2 env vars on linux; isWindowsBinaryPathInWsl blocks Windows binary types on WSL; detectRemoteDisplay keeps GPU on for local sessions; detectRemoteDisplay does not treat WSLg as remote |
| `electron/bootstrap-platform.ts` | TypeScript source: `bootstrap-platform` |
| `electron/bootstrap-quit.test.ts` | Tests for `bootstrap-quit` |
| `electron/bootstrap-repair-guard.test.ts` | Tests: first soft attempt with alive backend returns soft restart; soft restart budget exhausts at maxSoftAttempts+1 and escalates; attempt exactly at maxSoftAttempts is still soft; custom maxSoftAttempts is honored |
| `electron/bootstrap-repair-guard.ts` | Repair-loop guard for the desktop bootstrap. Why this exists ─────────────── Hermes desktop can request a "repair" of its bundled backend when the renderer observes a transient backend failure (see issue #74874). The cl… |
| `electron/bootstrap-runner-git-binary.test.ts` | Tests: resolveCheckoutHead runs the probed git binary, not the first PATH hit (#114718) |
| `electron/bootstrap-runner.test.ts` | Tests: runBootstrap bails immediately when the signal is already aborted; existing checkout detection requires git metadata; fresh bootstrap args include the packaged commit pin; existing-checkout bootstrap args keep br… |
| `electron/bootstrap-runner.ts` | bootstrap-runner.ts Drives apps/desktop's first-launch install of Hermes Agent by spawning scripts/install.ps1 stage-by-stage and streaming progress events back to the renderer. Wired from electron/main.ts: import { run… |
| `electron/bootstrap-state.test.ts` | Tests for `bootstrap-state` |
| `electron/bootstrap-state.ts` | Exports `bootstrapSnapshot` |
| `electron/browser-windows.test.ts` | Tests: buildBrowserWindowUrl puts win=browser before the hash (dev server); buildBrowserWindowUrl encodes the tab id; buildBrowserWindowUrl avoids a double slash when the dev server has a trailing slash; buildBrowserWin… |
| `electron/browser-windows.ts` | Popped-out in-app Browser windows. Same query-before-hash contract as session-windows / hud-url: `?win=browser` MUST sit in the search string before the '#', or HashRouter swallows it as part of the route. |
| `electron/bundle-skew.test.ts` | Tests: coalesces polls, backs off failures, and skips checks while an update owns the checkout; an asynchronous isUpdating defers only while it answers true; isFallbackCommit; matches the all-zero placeholder at any sta… |
| `electron/bundle-skew.ts` | Renderer-bundle skew detection. The desktop UI (including bundled plugins like Bot Mode) is compiled into the app binary at build time, while `hermes update` only moves the source tree. A user who updates from the termi… |
| `electron/bundle-swap.test.ts` | Tests: reads only the installed stamp for swap detection, without schema conversion; detectBundleSwap; reports a swap when the on-disk stamp carries a different commit; reports a swap when the same commit was rebuilt (b… |
| `electron/bundle-swap.ts` | Swapped-bundle detection. The detached updater (scripts/desktop-update/posix.sh mac_swap / windows.ps1) rebuilds and swaps the packaged app on disk AFTER `hermes update` exits. An instance that was launched from the PRE… |
| `electron/challenge-window-ipc.ts` | The renderer's `hermes:freeTierChallenge:run` invoke (preload `freeTierChallenge.run`). |
| `electron/challenge-window.test.ts` | Tests: only <portal>/challenge URLs are ever loadable; the phase is the URL fragment, and nothing else is a phase; the window is hidden, hardened, isolated, and not throttled; a pass while hidden closes the window witho… |
| `electron/challenge-window.ts` | The free tier's browser challenge, desktop half. The Nous account service can ask an anonymous install to clear a challenge before it mints a token (`hermes_cli/anon_challenge.py`). The challenge is a portal page; every… |
| `electron/channel-build-version.test.ts` | Tests: channel packaging reuses admitted identity and rejects unsupported or unsafe identities; a channel that copies the stable identity packages and runs as the regular app; channel stamps verify the real checkout and… |
| `electron/cli-provision.test.ts` | Tests: repairs owned dangling CLI links without changing foreign or live entries; qualified CLI paths expose their filenames, not shared canonical command keys; a failed link swap preserves its source and target, then p… |
| `electron/cli-provision.ts` | Exports `removeBundleCliLinks`, `provisionCliLinks` |
| `electron/clipboard-image.test.ts` | Tests: readClipboardImagePng returns PNG bytes from an image/png clipboard item; readClipboardImagePng skips items without an image/png type; readClipboardImagePng keeps scanning when getType rejects for a vanished type… |
| `electron/clipboard-image.ts` | Electron 44 rearchitected the clipboard onto the W3C async API: readText / writeText return Promises, and image reads no longer have a readImage() shortcut — the bytes arrive through clipboard.read() (ClipboardItem[]) a… |
| `electron/clipboard-ipc.ts` | Clipboard text IPC for the renderer. Electron 44's clipboard calls follow the async W3C clipboard API, so each handler settles only after the OS clipboard call does. |
| `electron/close-stop-kill.test.ts` | Tests: close/stop surfaces a taskkill failure and does not clear a lock a live holder still owns; close/stop inventories owned PIDs after the tree kill and clears only unheld locks; a lock whose delete fails is kept and… |
| `electron/close-stop-kill.ts` | Windows Desktop close/stop after the existing tree-kill. taskkill /T /F is not widened: the caller passes the owned PIDs and the same tree-kill. This module does not discover extra processes to signal. A taskkill error… |
| `electron/cloud-boot-cascade.test.ts` | Regression tests for electron/cloud-boot-cascade.ts. A Hermes Cloud agent whose session cookie had expired failed at boot with "Remote Hermes gateway uses OAuth, but you are not signed in" and latched, although the port… |
| `electron/cloud-boot-cascade.ts` | cloud-boot-cascade.ts Pure decision seam for self-healing a Hermes Cloud agent connection at boot. A `cloud` connection authenticates to its agent through the silent per-agent cascade (main.ts `cloudAgentSilentSignIn`):… |
| `electron/cloud-discovery.test.ts` | Tests: a stale team falls back once to current memberships; unrelated failures retain their meaning |
| `electron/cloud-discovery.ts` | The NAS (status, error code) pairs that mean the remembered team itself is gone for this user, as opposed to the credential or the request being bad. |
| `electron/cloud-session-recovery.test.ts` | Tests: Cloud cookie session recovery; recovers an expired cookie session before minting a new ticket; does not recover non-Cloud, non-401 or native-session failures; coalesces recovery without reusing single-use tickets |
| `electron/cloud-session-recovery.ts` | Exports `createCloudSessionRecovery` |
| `electron/command-screenshot-capture.test.ts` | Tests: Command screenshot capture; binds a single-use gesture to its original renderer and exact window, never another screen; drops denied, expired, concurrent and disabled captures without leaking a late image |
| `electron/command-screenshot-capture.ts` | Exports `createScreenshotCapture` |
| `electron/command-screenshot-monitor.test.ts` | Tests: launches the unpacked helper without prompting and delivers only validated capture messages; bounds startup and termination, preserves permission failures, and isolates restarts; stopping from the starting callba… |
| `electron/command-screenshot-monitor.ts` | Exports `CommandScreenshotCapture`, `CommandScreenshotStatus`, `resolveCommandScreenshotMonitorPath`, `CommandScreenshotMonitor` |
| `electron/command-screenshot-types.ts` | Exports `ScreenshotStatus`, `ScreenshotWindow`, `ScreenshotResult`, `ScreenshotApi` |
| `electron/command-screenshot.ts` | Device-local, opt-in native gesture. No renderer can request an arbitrary screenshot. |
| `electron/composer-image-name.test.ts` | Tests for electron/composer-image-name.ts. Run with: vitest run --project electron composer-image-name (Wired into npm test:desktop:platforms in package.json.) Regression (issue #96403): pasted composer screenshots were… |
| `electron/composer-image-name.ts` | Filename stamping for pasted composer images (composer-images/). The timestamp embedded in a composer image filename must be the user's LOCAL wall-clock time: these files are browsed and sorted by humans alongside their… |
| `electron/composer-paste.test.ts` | Tests: writeComposerPaste; lands the paste directly under <HERMES_HOME>/composer-pastes so the backend admits it |
| `electron/composer-paste.ts` | Exports `COMPOSER_PASTES_DIRNAME`, `writeComposerPaste` |
| `electron/connection-apply.test.ts` | Tests: applyConnectionChange; serializes connection changes behind bootstrap rollback before teardown and apply; tears down only a non-primary scope without applying the primary connection; resolveTerminalConnection |
| `electron/connection-apply.ts` | TypeScript source: `connection-apply` |
| `electron/connection-caches.test.ts` | Tests: evicting a connection id forgets every cache keyed by it; an evicted id enumerates from the live target again instead of serving the old one; evicting an unknown or empty id is a no-op |
| `electron/connection-caches.ts` | Main-process caches keyed by connection id. Every entry here answers "what is at connection <id>", so it is only valid while that id keeps pointing at the same machine. Two lifecycle events break that: removing a connec… |
| `electron/connection-config-apply.test.ts` | Tests: applyConnectionConfigAtomically; commits legacy and registry state before activation; rolls both stores back when activation fails; rolls legacy state back when the registry write fails |
| `electron/connection-config-apply.ts` | Exports `applyConnectionConfigAtomically` |
| `electron/connection-config.test.ts` | Tests for electron/connection-config.ts. Run with: node --test electron/connection-config.test.ts (Wire into npm test:desktop:platforms in package.json.) These are the pure helpers behind the remote-gateway connection s… |
| `electron/connection-config.ts` | connection-config.ts Pure, electron-free helpers for the desktop's remote-gateway connection config: URL normalization, WS-URL construction (token vs OAuth ticket), auth-mode classification, and the auth-mode coercion r… |
| `electron/connection-registry.test.ts` | Tests for electron/connection-registry.ts — the v2 multi-connection registry: label rules (required, unique, |
| `electron/connection-registry.ts` | connection-registry.ts Pure, electron-free helpers for the desktop's multi-connection registry — the v2 successor to the single global `mode` + `remote` block in connection.json. The registry is a named list of agent SO… |
| `electron/connection-route-identity.ts` | Canonical registry route identity for Desktop. Identity is frozen before dialing, while the complete auth/transport envelope still exists. Compatibility callers may reuse the same contract, but must never reconstruct a… |
| `electron/connection-window-state.test.ts` | Tests: liveWindowState; reads the SENDER window state, not a cached snapshot (#102451); falls back to the primary window when the reply carries no sender; returns undefined when no usable window exists |
| `electron/connection-window-state.ts` | Live window state to attach to a connection reply (#102451). A republished connection must carry the calling window's CURRENT chrome state (fullscreen, maximized, …), not whatever `startHermes()` baked into the cached b… |
| `electron/crash-forensics.test.ts` | Tests: describeCrashReason; prefers a stack, then a message, for thrown errors; renders non-error rejections without throwing; installCrashForensics |
| `electron/crash-forensics.ts` | Last-chance forensics for the Electron main process. Electron installs its own `uncaughtException` listener and only warns on unhandled rejections, so the app usually survives — but the reason lands on stderr alone, whi… |
| `electron/dashboard-token.test.ts` | Tests for electron/dashboard-token.ts. Run with: node --test electron/dashboard-token.test.ts (Wired into npm test:desktop:platforms in package.json.) |
| `electron/dashboard-token.ts` | Helpers for local dashboard session-token discovery. The desktop main process can pass HERMES_DASHBOARD_SESSION_TOKEN when it spawns the local dashboard, but the dashboard is the source of truth for the token it actuall… |
| `electron/data-paths.d.mts` | Exports `platformDefaultHermesHome`, `resolveDesktopUserData`, `HermesHomeOptions`, `resolveDesktopHermesHome` |
| `electron/data-paths.mjs` | data-paths.mjs — the pure path-resolution core, shared by the desktop app (via data-paths.ts, a typed re-export) and the CI smoke driver (which runs under Node's type-stripping and therefore cannot import the app's |
| `electron/data-paths.test.ts` | Tests: default data roots append the suffix literally on each platform; explicit homes and userData retain precedence, and suffixed Windows homes never use legacy state |
| `electron/data-paths.ts` | data-paths.ts — typed re-export of the shared pure resolver in data-paths.mjs. The app imports these names here (extensionless, for the tsc/esbuild build); the CI smoke driver imports the .mjs directly because Node's ty… |
| `electron/deep-link-protocol.test.ts` | Tests: the E2E/dev guard leaves the OS hermes:// handler untouched; normal launches still register |
| `electron/deep-link-protocol.ts` | `hermes://` deep-link registration. Every launch rewrites the OS handler (on Windows, HKCU\Software\Classes\<protocol>), so a test or dev run of an unpackaged checkout would repoint the user's installed handler at that… |
| `electron/desktop-boot-preference.test.ts` | Tests: profile writes preserve other-owned fields and never adopt a broken file |
| `electron/desktop-boot-preference.ts` | Exports `DesktopBootPreference`, `readDesktopBootPreference`, `writeDesktopProfile` |
| `electron/desktop-electron-pin.test.ts` | Regression: the desktop Electron dependency must be an exact, consistent pin. The Windows desktop install failed at "Building desktop app" because Electron changed its install mechanism mid patch-series: electron 40.9.3… |
| `electron/desktop-installation.test.ts` | Every `ps` the marker probes run, answerable by a test that plays macOS. |
| `electron/desktop-installation.ts` | TypeScript source: `desktop-installation` |
| `electron/desktop-log-line.test.ts` | Tests: formatDesktopLogLine; stamps lines with the local wall-clock time, in the shape Python logs use |
| `electron/desktop-log-line.ts` | Desktop log line formatting shared by every desktop log surface: `desktop.log`, the in-app "RECENT LOGS" view, and crash forensics. The stamp is local time in the `YYYY-MM-DD HH:MM:SS,mmm` shape of Python's default `asc… |
| `electron/desktop-plugin-install.test.ts` | Tests: resolvePluginGitUrl; maps owner/repo shorthand to github git url; supports monorepo subdir shorthand; supports hash subdir fragment |
| `electron/desktop-plugin-install.ts` | Probe and install desktop runtime plugins from Git repositories. Pure helpers are exported for unit tests; IPC handlers in main.ts call the async entry points with a resolved git binary. |
| `electron/desktop-plugin-remove.test.ts` | Tests: removeDesktopPlugin; deletes exactly the named standalone folder under the root and leaves its neighbours; refuses anything that is not a single folder name inside the root, deleting nothing; refuses a unified pa… |
| `electron/desktop-plugin-remove.ts` | Uninstall of a STANDALONE desktop plugin: delete one folder directly under the app-level `<HERMES_HOME>/desktop-plugins` root. The renderer names the folder, never a path — containment is by construction (single segment… |
| `electron/desktop-plugins-root.test.ts` | Tests: migrateProfileScopedDesktopPlugins; lifts per-profile desktop plugins into the app root so they survive a profile switch; never overwrites a plugin already installed at the app root; reconcileUnifiedDesktopHalves |
| `electron/desktop-plugins-root.ts` | The standalone desktop-plugin root (`<HERMES_HOME>/desktop-plugins`) and the one-time migrations that make it the ONLY place desktop code loads from. A desktop plugin extends THIS APP — panes, palette commands, themes —… |
| `electron/desktop-profile-mutation.test.ts` | Tests for `desktop-profile-mutation` |
| `electron/desktop-profile-preload.test.ts` | Tests: the native preload exposes routed peer opening and default preference events with unsubscribe |
| `electron/desktop-profile.test.ts` | Tests: failed authoritative writes leave the previous default and listeners untouched; explicit routes are strict and never fall back to a different source window; boot and reconnect retain the window route rather than… |
| `electron/desktop-profile.ts` | Exports `DesktopProfileRoute`, `DESKTOP_PROFILE_NAME_RE`, `requireDesktopProfileRoute`, `resolveDesktopWindowRoute`, `DesktopWindowLaunch`, `resolveDesktopWindowLaunch` … |
| `electron/desktop-redial-route-request.test.ts` | B2-15: an unscopable mutating REST call keeps its pooled backend only while the routing decision sees the request; the stale-ticket redial (ensure + forget) must resolve that same route, or the retry lands on the shared… |
| `electron/desktop-remote-route.test.ts` | Tests: profile remote wins precedence and carries one exact registry id; environment route wins over global but never claims a registry id; environment URL without its token keeps the existing error; global remote uses… |
| `electron/desktop-remote-route.ts` | Exports `DesktopRemoteRoute`, `DesktopRemoteRouteInput`, `v1SshTerminalPoolKey`, `resolveDesktopRemoteRoute`, `registryPrimaryBootRoute` |
| `electron/desktop-shared-metrics.test.ts` | Tests: a packaged apply is reported once through the renderer IPC; a checkout hand-off never is |
| `electron/desktop-shared-metrics.ts` | Main-process shared-metrics wiring, kept out of main.ts: the once-per-launch startup-latency claim, the packaged self-update recorder and the consent-gated renderer-crash recorder the renderer drains once a backend is a… |
| `electron/desktop-uninstall-ipc.test.ts` | Tests: excluded artifact owners block every uninstall IPC before a Python probe or destructive callback; self-managed installs retain summary and uninstall IPC behavior under Electron policy |
| `electron/desktop-uninstall.test.ts` | Tests for electron/desktop-uninstall.ts. Run with: node --test electron/desktop-uninstall.test.ts (Wired into npm test:desktop:platforms in package.json.) These are the pure helpers behind the desktop Chat GUI uninstall… |
| `electron/desktop-uninstall.ts` | desktop-uninstall.ts Pure, electron-free helpers for the desktop Chat GUI uninstaller. These map the three user-facing uninstall modes to the `hermes uninstall` CLI flags, resolve the running app bundle/exe so a detache… |
| `electron/dev-cdp.test.ts` | Tests for electron/dev-cdp.ts. Run with: npx vitest run --project electron electron/dev-cdp.test.ts |
| `electron/dev-cdp.ts` | Dev Chrome DevTools Protocol exposure for the desktop renderer. The renderer is a Chromium page, so `--remote-debugging-port` turns it into something the repo's existing CDP tooling (`scripts/eval.mjs`, `scripts/perf/li… |
| `electron/dock-launch-order.test.ts` | Tests: macOS Dock launch order; registers the deep link before the single-instance lock; keeps non-macOS platforms on the lock at module load, with no Dock race |
| `electron/dock-launch-order.ts` | Order of the two startup steps that decide whether macOS shows a second Dock icon. On macOS, `setAsDefaultProtocolClient` goes through Launch Services. If the single-instance lock has already claimed this process, that… |
| `electron/embed-host.test.ts` | Tests: wraps the player with an origin YouTube can match; serves nothing but a well-formed video id; drops unknown and non-numeric params instead of forwarding them; the live host serves the wrapper locked down, and onl… |
| `electron/embed-host.ts` | YouTube refuses to play (error 153) unless the embedding page has an http(s) origin it can match against the player's `origin` param, and on modern Electron a stamped Referer header is dropped. The packaged renderer is a |
| `electron/embed-referer.ts` | TypeScript source: `embed-referer` |
| `electron/entitlements.mac.inherit.plist` | macOS property list |
| `electron/entitlements.mac.plist` | macOS property list |
| `electron/entry.ts` | A Desktop relaunched by an update (any rung: hand-off script, staged updater, Start-Process) must not keep the system proxy the update's children were given. |
| `electron/event-dedupe.test.ts` | Tests: collapses the same key inside the window (two windows, one event); distinct keys are independent; re-fires once the window elapses; a spoken reply stays claimed long after the tick window, a beep does not |
| `electron/event-dedupe.ts` | Cross-window de-dupe for one-shot side-effects (OS notifications, the turn-end sound, spoken replies). Every desktop window is its own renderer process, so N open windows each independently react to the same backend eve… |
| `electron/external-open.test.ts` | Tests for electron/external-open.ts — the single route every external URL open funnels through. All I/O is injected, so the "open failed → notify" behavior is asserted without loading electron. Run with the electron tes… |
| `electron/external-open.ts` | external-open.ts The single route every external URL open in the desktop app flows through. Electron-free: every side effect (shell.openExternal, spawn, the file opener, the failure channel) is injected, so the "open fa… |
| `electron/external-terminal.test.ts` | Tests: tuiResumeArgs resumes the session in the TUI; tuiResumeArgs pins the profile ahead of the mode flag; posixQuote survives embedded single quotes; windowsQuote doubles embedded quotes |
| `electron/external-terminal.ts` | Launching the Hermes TUI in the user's OWN terminal emulator. This is deliberately NOT the in-app terminal pane: the point of the verb is to hand a session to the terminal the user already lives in, running |
| `electron/f12-shortcut.test.ts` | Tests: arbitrates only native F12 keydown and preserves repeat/modifiers for forwarding |
| `electron/f12-shortcut.ts` | Exports `F12Input`, `F12ShortcutDecision`, `f12ShortcutDecision`, `toF12KeyboardEventPayload` |
| `electron/favicon.test.ts` | Tests: which hosts we will ask at all; a public https host is fair game; reading a page for the marks it declares; declared icons come back absolute against the page |
| `electron/favicon.ts` | Favicon resolution, the thorough way. `<origin>/favicon.ico` answers for maybe half the web. Everyone else declares their marks in the page head (`<link rel="icon">`, apple-touch, SVG mask icons) or in a web app manifes… |
| `electron/feature-flags.test.ts` | feature-flags.ts is the single resolver for which gated surfaces are on in this artifact. These tests pin the flag table: local models ship on Windows, macOS and Linux x64/arm64 on every channel; elsewhere the launch ar… |
| `electron/feature-flags.ts` | Exports `FeatureFlags`, `isCanaryTag`, `FeatureFlagInput`, `resolveFeatureFlags` |
| `electron/fetch-json-oauth-session.test.ts` | Tests: OAuth session response; settles once when a response body fails after headers; preserves JSON and HTTP error contracts when end wins settlement |
| `electron/find-in-page-native-fixture/package.json` | JSON manifest for `find-in-page-native-fixture` |
| `electron/find-in-page-native.test.mjs` | Tests for `find-in-page-native` |
| `electron/find-in-page.test.ts` | Unit tests for the pure find-in-page helpers. The IPC handlers in main.ts are the only consumer — the helpers below must keep the wire shape stable (match counter shape, defaults, no-throw-on-destroyed). |
| `electron/find-in-page.ts` | Pure helpers for the desktop find-in-page bridge (Ctrl/Cmd+F). The renderer drives an Electron `webContents.findInPage` over IPC so it can reuse the native "find-in-page" experience (incremental search, match highlight,… |
| `electron/first-run-setup-gate.test.ts` | Tests: first-run setup gate skips non-bootstrap backends; first-run setup gate prompts once for concurrent waits; continueLocal keeps the setup choice visible until bootstrap owns the overlay; retry reset preserves the… |
| `electron/first-run-setup-gate.ts` | Exports `FirstRunSetupDecision`, `createFirstRunSetupGate` |
| `electron/first-run-setup-main-process.test.ts` | Tests: a first-run bootstrap-needed remote apply connects without ensuring or bootstrapping locally; a primary apply without an active first-run gate tears down before reconnect notification |
| `electron/fixtures/nvidia-recovery.ts` | No windows, gateway, credentials, or real Hermes home. This fixture exercises native Electron locking with the production Linux recovery policy and test driver facts. |
| `electron/fixtures/source-backend.py` | PM publication plus the real backend, using prepared dependencies offline. |
| `electron/fixtures/system-ca.ts` | Synthetic self-signed CAs; no private keys are retained. Tests freeze time between the expired root's 2025 expiry and the other roots' 2035 expiry. |
| `electron/fs-ipc.test.ts` | `hermes:fs:reveal` answers what it did (#115167). `shell.showItemInFolder` selects an existing item and silently no-ops on a missing one, and a remote backend's paths are missing on this computer by construction — a `tr… |
| `electron/fs-ipc.ts` | IPC surface for local filesystem operations the renderer's project/file surfaces use: directory reads, reveal/open in the OS file manager, plugin roots + git installs, rename/write/trash, and the plugin SDK's folder-sco… |
| `electron/fs-probes.ts` | Synchronous filesystem probes main.ts uses on its boot and update paths. |
| `electron/fs-read-dir.test.ts` | Tests: readDirForIpc hides noisy directories and files from the project tree; readDirForIpc filters a hidden basename whether it is a file or directory; readDirForIpc returns directories before files and sorts by name w… |
| `electron/fs-read-dir.ts` | TypeScript source: `fs-read-dir` |
| `electron/gateway-download-transport.test.ts` | Tests: download transport never follows redirects or retries after the save phase begins; the connect timeout is dropped once headers arrive so a slow body streams to completion; a body that stalls mid-stream is destroy… |
| `electron/gateway-download-transport.ts` | Retry only the connection phase, never a save dialog or a partially saved body. |
| `electron/gateway-file-download-transport.test.ts` | Tests: cookie transport preserves the session, waits for the dialog without a deadline, and cancels without writing; cookie connection timeout aborts before headers and never opens a dialog; cookie transport streams byt… |
| `electron/gateway-file-download-transport.ts` | Exports `GatewayDownloadOptions`, `downloadViaTokenToFile`, `GatewayOauthDownloadRequest`, `GatewayOauthRequestOptions`, `GatewayOauthDownloadDeps`, `downloadViaOauthSessionToFile` |
| `electron/gateway-file-download.fs.test.ts` | Real-filesystem witnesses for the failure-atomic save contract (#96597). The unit tests in gateway-file-download.test.ts prove the pump's control flow against fakes. These run the exact production deps (`fsPumpDeps()`)… |
| `electron/gateway-file-download.test.ts` | Tests: downloadTempPath stays beside the destination with a short, random per-call name; pumpStreamToFile waits for the descriptor to close before renaming when the stream supports close(); pumpStreamToFile applies back… |
| `electron/gateway-file-download.ts` | Helpers for saving a gateway-hosted file to the local disk from the Electron main process. Extracted from main.ts so the streaming, data-URL decoding, and filename derivation are unit-testable without spinning up Electr… |
| `electron/gateway-stop-before-update.test.ts` | Tests: non-Windows is a no-op and never invokes the CLI; Windows with missing CLI shim returns false and does not exec; Windows with live CLI invokes ; Windows with failing CLI returns false (best-effort, never throws) |
| `electron/gateway-stop-before-update.ts` | Windows uninstall delegates fleet draining to the CLI before deleting files. |
| `electron/gateway-version.test.ts` | Tests: version follows each supplied gateway response without caching; unavailable gateway version stays unknown instead of using another install; the distance past the release tag wins over the bare release |
| `electron/gateway-version.ts` | The connected process owns its runtime version, not a checkout on disk. `displayVersion` carries the distance past the release tag (`0.21.5+1913`); a backend that predates it only reports the bare release. |
| `electron/gateway-ws-probe.test.ts` | Tests for electron/gateway-ws-probe.ts. Run with: node --test electron/gateway-ws-probe.test.ts (Wired into npm test:desktop:platforms in package.json.) The probe drives a real WebSocket handshake for the "Test remote"… |
| `electron/gateway-ws-probe.ts` | Live WebSocket validation for the remote-gateway "Test remote" button. Background: the desktop boot does two independent things to a remote gateway: 1. The MAIN process hits ``GET /api/status`` over HTTP (token in a hea… |
| `electron/get-windows.d.ts` | Type declarations for the get-windows optionalDependency. get-windows ships no bundled types and is an optionalDependency. `npm ci` can skip it when its native install fails, including Linux and Windows ARM64 |
| `electron/git-binary-candidates.test.ts` | Tests: ugitGitBinaries (#61494); enumerates the UGit app-* glob and returns each bundled git.exe, newest first; sorts app dirs by version, not lexically (app-10.0.0 beats app-9.0.0); returns [] when UGit is not installe… |
| `electron/git-binary-candidates.ts` | The filesystem surface the candidate builders need — injectable for tests. |
| `electron/git-ipc.ts` | IPC surface for git-driven features: worktree management ("Start work"), the composer coding rail's repo status, the Codex-style review pane, and repo-first project discovery. Extracted from main.ts; the git/gh binary |
| `electron/git-repo-scan.test.ts` | Tests: scanGitRepos; does not read the filesystem when discovery is disabled; does not fall back to scanning the home directory when roots are empty (#53328); scans only configured roots and excludes complete subtrees |
| `electron/git-repo-scan.ts` | Repo-first discovery: walk bounded roots for Git repositories using only Node's fs APIs. Electron owns this machine-local capability; the renderer supplies the profile-scoped policy from Hermes config. |
| `electron/git-review-ops.test.ts` | Tests: resolveRenamePath: plain path is unchanged; gitFor accepts an internally resolved git binary path containing spaces; gitFor accepts internally resolved git paths with restricted non-space characters; gitFor accep… |
| `electron/git-review-ops.ts` | Git ops backing the coding rail + Codex-style review pane. Built on `simple-git` (a maintained wrapper around the system git binary — same git the rest of the app shells to, no native build) so we read structured status… |
| `electron/git-root.test.ts` | Tests: gitRootForIpc returns null for invalid and device paths; gitRootForIpc resolves directories files missing descendants and file URLs |
| `electron/git-root.ts` | TypeScript source: `git-root` |
| `electron/git-worktree-ops.test.ts` | Tests: sanitizeBranch: spaces → hyphens, forbidden chars dropped, edges trimmed; parseWorktrees: main checkout + linked worktree; parseWorktrees: detached + locked flags; parseWorktrees: empty input |
| `electron/git-worktree-ops.ts` | Git-driven worktree operations for the desktop "Start work" flow: spin up a fresh worktree the lightest way (`git worktree add -b`), list real worktrees, and remove them. Git is the source of truth; the renderer just dr… |
| `electron/handoff-result-producer.test.ts` | Tests for `handoff-result-producer` |
| `electron/handoff-result.test.ts` | Tests: consumes and returns a fresh failure result; reports each result at most once; discards stale results but still consumes the file; malformed JSON is logged and kept as .corrupt, not reported |
| `electron/handoff-result.ts` | Consume the detached update hand-off's result file (#82328 follow-up). scripts/desktop-update/windows.ps1 runs hidden/detached — the user never sees its console. It writes HERMES_HOME/.hermes-update-result.json on every… |
| `electron/hardening.test.ts` | Tests: clampDataUrlReadMaxMb defaults and bounds the attach size preference; attachment data URL helper reads bytes above the preview default without changing that limit; resolveTimeoutMs falls back to defaults and acce… |
| `electron/hardening.ts` | Relative, not `@hermes/shared`: the electron bundle is built by esbuild with no tsconfig path resolution (see scripts/bundle-electron-main.mjs), so a bare specifier would typecheck and then fail to bundle. |
| `electron/host-backend-singleton-orphan-reap.test.ts` | #81275 regression coverage: the duplicate-serve/orphan bug class (one backend per host across reconnect storms; no PPID-1 orphans after a quit). The causal fixes are on main (dial-claim coalescing #90812, host-backend |
| `electron/host-backend-singleton.test.ts` | Multiplex-only invariants for the Desktop backend pool: one host backend serves every profile, and the local pooled-spawn path is unreachable. |
| `electron/host-backend-singleton.ts` | Multiplex-only, Desktop half: ONE `hermes serve` per HOST serves every profile, so a local profile never gets a backend process of its own. The PRIMARY attaches to the host's running gateway through |
| `electron/hub-iframe-policy.ts` | Capability carve-outs for the embedded Skills Hub iframe ONLY. The Skills Hub picker (Bot Mode) embeds the public docs site (`https://hermes-agent.nousresearch.com/docs/skills?embed=picker`, or the GitHub Pages mirror w… |
| `electron/hud-close.test.ts` | Tests: a renderer that answers the close is never destroyed; a renderer that never answers is destroyed at the grace deadline |
| `electron/hud-close.ts` | Bounded graceful close for the HUD window. `win.close()` is a request, not an action: Electron asks the renderer to run its beforeunload/unload handlers and only destroys the window once it answers. That round-trip is w… |
| `electron/hud-cursor.test.ts` | Unit tests for the HUD's Linux cursor conversion. These cover the two things that decide whether the bar is clickable: landing on the right point, and admitting when the cursor has left. |
| `electron/hud-cursor.ts` | Cursor→page coordinate math for the HUD's Linux click-through fallback. The HUD decides whether to swallow the mouse by hit-testing the document under the cursor, which needs a cursor position in CSS pixels. On macOS an… |
| `electron/hud-drag.test.ts` | Tests: origin is cursor minus the grab offset captured at press; a drag onto another display does not depend on the previous window origin; crossing a mixed-DPI display keeps 1:1 tracking in native DIP; a move before be… |
| `electron/hud-drag.ts` | HUD composer-drag geometry — where to park the window so it stays under the OS cursor, including across monitors. Renderer PointerEvent screen coordinates are CSS pixels. Electron's `screen.getCursorScreenPoint()` and `… |
| `electron/hud-game-overlay.test.ts` | Tests: DPI rounding and the 1px-oversize trick stay within the epsilon; a maximized window stopping at the taskbar does not cover; a fullscreen window on ANOTHER display does not cover this one; fullscreen game under th… |
| `electron/hud-game-overlay.ts` | hud-game-overlay.ts — is the HUD floating over a fullscreen app (a game)? Discord's in-game overlay behavior: while a fullscreen app owns the screen the HUD steps back to a low-opacity, glanceable state, and steps forwa… |
| `electron/hud-geometry.test.ts` | Tests: defaultHudBounds restores the standard size, centered near the bottom of the work area; defaultHudBounds fits the default layout to a small work area; defaultHudBounds keeps the spawn fallback when no display is… |
| `electron/hud-geometry.ts` | Exports `HUD_WIDTH`, `HUD_HEIGHT`, `HUD_BOTTOM_MARGIN`, `HudWorkArea`, `defaultHudBounds`, `HudBoundsWindow` … |
| `electron/hud-hyprland.test.ts` | Unit tests for the Hyprland HUD overlay promote. The socket itself needs a live compositor; what is covered here is the grammar (classic vs Lua), the client lookup, and which dispatchers fire for a tiled vs already-floa… |
| `electron/hud-hyprland.ts` | Hyprland (Omarchy, etc.) tiles a new Electron toplevel by default. `alwaysOnTop` is compositor-owned on native Wayland, and `xdg_toplevel.move` — the native HUD drag path — is ignored on a tiled window. The bar then sit… |
| `electron/hud-ipc.ts` | IPC surface for HUD mode (the chrome-free floating chat band). Extracted from main.ts; the HUD window handle and session-id latch stay injected because main.ts owns the window lifecycle and the close broadcast reads the |
| `electron/hud-modifier-monitor.test.ts` | Tests: native transport gates gestures on ready, bounds framing and isolates replacement children; support policy excludes Wayland even when Xwayland supplies DISPLAY; a missing helper is distinguished from a helper tha… |
| `electron/hud-modifier-monitor.ts` | Exports `HudModifierStatus`, `hudModifierMonitorSupported`, `resolveHudModifierMonitorPath`, `HudModifierMonitor` |
| `electron/hud-modifier-native.test.ts` | hud-modifier-gesture.h is the clean-tap state machine the macOS (.m) and Linux XI2 (-x11.c) helpers both include. Compile its C contract and run it wherever a C toolchain ships with the runner: Linux (the JS CI lane) and |
| `electron/hud-modifier-types.ts` | Exports `HudModifierStatus`, `HudModifierApi` |
| `electron/hud-modifier.test.ts` | Tests: persists opt-in, fences stale native callbacks and re-arms after lock without requesting permission; rejects guest frames and invalid writes, and reports native permission failure without summoning |
| `electron/hud-modifier.ts` | Opt-in device preference: native input never crosses into a renderer. |
| `electron/hud-overlay.test.ts` | Tests: macOS uses the floating window level and all-spaces visibility; Linux and Windows only set the screen-saver always-on-top level |
| `electron/hud-overlay.ts` | HUD overlay adapters. Electron `alwaysOnTop` is the generic ask. Some compositors ignore it (Hyprland tiles the toplevel; COSMIC drops z-order). Each adapter speaks that compositor's dialect; `promoteHudOverlay` is the… |
| `electron/hud-snap-shortcut.test.ts` | Tests: createHudSnapShortcut; registers CommandOrControl+Shift+G while the HUD is up; dispose releases the accelerator; register fails when the chord is already taken |
| `electron/hud-snap-shortcut.ts` | HUD snap-to-pointer — global OS shortcut while the HUD is open. Tap ⌘⇧G (CommandOrControl+Shift+G) from any app to park the HUD bar under the cursor. Main owns registration — same authority split as Quick Entry. Electro… |
| `electron/hud-snap.test.ts` | Tests: anchor under cursor at zoom 1; anchor scales with page zoom; clamp keeps a sliver visible when the anchor would park off-screen; snapHudBounds composes origin + clamp |
| `electron/hud-snap.ts` | HUD snap-to-pointer math — where to park the window so a chosen anchor on the bar (usually the composer center) sits under the OS cursor. Kept pure so the two unit mismatches (screen vs window origin, DIP vs CSS) cannot… |
| `electron/hud-url.test.ts` | Tests: buildHudWindowUrl puts win=hud before the hash route (dev server); buildHudWindowUrl carries the handoff profile in the query before the hash; buildHudWindowUrl encodes the profile and the session id; buildHudWin… |
| `electron/hud-url.ts` | HUD mode's renderer URL. The pure, Electron-free piece lives here so it can be unit-tested (same split as session-windows.ts, and for the same reason: the contract below is invisible until it breaks at runtime). |
| `electron/hud-windowing.test.ts` | Unit tests for the HUD windowing profile. Ozone parsing and the capability matrix live here: one profile, every operation reads the same flags. |
| `electron/hud-windowing.ts` | HUD windowing profile — one object for every operation that used to special-case OS / Ozone / compositor. The Ozone backend (not the login session) is the normalizer: Electron 20+ prefers a native Wayland surface on a W… |
| `electron/hyprland.test.ts` | Unit tests for the Hyprland window provider. The socket itself needs a live compositor, so what is covered here is everything that decides whether the answer is right once the bytes arrive: which instance we talk to, an… |
| `electron/hyprland.ts` | hyprland.ts — window enumeration for Hyprland, via the compositor's own IPC. `read_window_below` normally enumerates through `get-windows`, which on Linux shells out to `xprop` and reads `_NET_CLIENT_LIST_STACKING`. Tha… |
| `electron/install-stamp.ts` | install-stamp.ts — the typed build-time install stamp. scripts/write-build-stamp.mjs writes build/install-stamp.json during `npm run build`. |
| `electron/keep-awake-controller.test.ts` | Tests: createKeepAwakeController: the offer after a sleep mid-turn; offers once, on the wake after a timed sleep interrupted a turn with keep-awake off; does not offer again after a relaunch; stays quiet for a closed li… |
| `electron/keep-awake-controller.ts` | Main's half of keep-awake: the one power-save blocker, its persisted mode, and the one-time offer after a timed sleep interrupted a turn. Kept apart from power-save.ts so the renderer bundle never pulls in Node's fs. |
| `electron/launch-build-identity.test.ts` | Tests: launchBuildIdentity retains version labels and qualifies stamped artifacts; launchBuildIdentity falls back to the install stamp on a source install; launchBuildIdentity moves between two source builds of the same… |
| `electron/launch-build-identity.ts` | Artifact identity for recovery witnesses, adapted from kokhlo's #131067. |
| `electron/launch-profile.test.ts` | Tests: parses both --profile spellings and ignores a missing flag; normalizes a launch profile the same way the CLI does; a launch --profile is persisted before the backend reads active-profile.json; --profile=<name> pe… |
| `electron/launch-profile.ts` | Profile from `--profile <name>` or `--profile=<name>`. Missing, empty, and invalid values are null so a launch without a usable flag leaves the stored desktop profile alone. Names are trimmed and lowercased to match the… |
| `electron/link-metadata.ts` | Link title resolution — curl (tier 1) → hidden BrowserWindow (tier 2). |
| `electron/link-title-curl.test.ts` | Tests: parseCurlTitleResponse; decodes a legacy page from curl content-type metadata; reads the trailer from the retained tail after the body budget is exhausted |
| `electron/link-title-curl.ts` | Exports `CURL_TITLE_WRITE_OUT`, `parseCurlTitleResponse` |
| `electron/link-title-url.test.ts` | #93893: the renderer can send ANY href-shaped string to the hermes:fetchLinkTitle IPC; before these guards, an unparseable string became its own cache key (canonicalTitleCacheKey returned the raw value) |
| `electron/link-title-url.ts` | URL admission for the link-title pipeline. The renderer's title-fetch path can send ANY href-shaped string to the ``hermes:fetchLinkTitle`` IPC; the main process must re-validate before anything reaches curl or the hidd… |
| `electron/link-title-wall.test.ts` | A published Doc answers the cookieless curl tier with its own <title>, so these links must stay fetchable — the wall is proven at fetch time, not from the host. |
| `electron/link-title-wall.ts` | The ladder between the curl tier and the hidden-Chromium tier of link-title resolution: curl (tier 1) → hidden BrowserWindow (tier 2). The title partition is cookieless (`session.fromPartition('hermes:link-titles', |
| `electron/link-title-window.test.ts` | Tests: linkTitleWindowOptions keeps the offscreen, hardened defaults; createLinkTitleWindow mutes audio so historical links never autoplay sound; createLinkTitleWindow hides and zeroes opacity so Windows cannot flash a… |
| `electron/link-title-window.ts` | Hidden BrowserWindow used by tier-2 link-title resolution: when curl can't read a page <title> (bot walls, JS-rendered pages), we briefly load the URL in an offscreen window and read its title. That window loads arbitra… |
| `electron/linux-crash-diagnostics.test.ts` | Regression for #100573: the Linux shell died with SIGTRAP at Chromium's shared fatal-handler address and no launcher kept the FATAL message. The fix is not a guess at the cause; it is making the next crash legible. |
| `electron/linux-crash-diagnostics.ts` | Every Chromium CHECK/LOG(FATAL) in the shell ends at the same instruction — base::ImmediateCrash at the tail of logging::LogMessage::HandleFatal — so a core dump alone says "something fatal happened" and nothing about w… |
| `electron/linux-gpu-fallback.test.ts` | Tests: parseLinuxGpuMarker; accepts a well-formed fallback marker; rejects garbage; decideLinuxGpuLaunch |
| `electron/linux-gpu-fallback.ts` | Linux GPU-child software fallback for #124843. On Mesa/Wayland (Intel iGPU, no NVIDIA driver) the Chromium GPU child can fail initialization (`GPU process launch failed: error_code=1002`) and — instead of crashing — ret… |
| `electron/linux-launcher-ready.test.ts` | Tests: writes one byte to the launcher fd, closes it and consumes the variable; a launch without the variable, or with a garbage value, is a no-op |
| `electron/linux-launcher-ready.ts` | Tells the `hermes desktop` launcher that the main window is on screen. On Linux an app-grid launch defers writing the app's own `.desktop` entry until the window has mapped: unpatched gnome-shell (before GNOME MR !4428)… |
| `electron/linux-nvidia-egl-fallback.test.ts` | Tests: parseNvidiaDriverMajor / parseNvidiaDriverVersion; parses the major and full version from /proc/driver/nvidia/version content; returns null for garbage or empty input; decideNvidiaEglFallback — behavioral probe |
| `electron/linux-nvidia-egl-fallback.ts` | Linux NVIDIA EGL fallback for #40077 / #124255. History: NVIDIA driver 580.x breaks ANGLE's EGL probing on X11/Wayland ("Invalid visual ID requested"), the GPU process dies, and the app goes down with it. Rendering ANGL… |
| `electron/linux-nvidia-egl-recovery.native.test.ts` | Tests: a secondary Electron process leaves state intact, then a normal restart stays native; a clean exit before reveal does not poison the next process |
| `electron/linux-nvidia-egl-recovery.test.ts` | Tests: NVIDIA persisted recovery lifecycle; a successful native launch stays native through an ordinary restart without an override; secondary launches leave the running primary marker unchanged and cannot force the nex… |
| `electron/linux-nvidia-egl-recovery.ts` | Exports `createNvidiaEglRecovery` |
| `electron/linux-sandbox-relaunch.test.ts` | Tests: Linux runtime --no-sandbox relaunch; moves a runtime-only --no-sandbox onto argv exactly once; leaves sandboxed launches, launch-time opt-outs and other platforms alone; relaunches the extracted executable of --a… |
| `electron/linux-sandbox-relaunch.ts` | A runtime `--no-sandbox` is too late on Linux (#131055, #139542, #143569). Chromium forks its zygote into the sandbox (user-namespace or setuid lane) before any application JavaScript runs, so `app.commandLine.appendSwi… |
| `electron/local-backend-lifecycle.test.ts` | Tests: shutdown joins a removed start and prevents its late spawn; shutdown retains a child before asynchronous claim and joins an earlier stop; shutdown is bounded even if startup ignores cancellation; the quit barrier… |
| `electron/local-backend-lifecycle.ts` | Observe every branch, but never leave quit parked on a lost exit/SSH callback. |
| `electron/local-filesystem-path.test.ts` | Tests: recognizes every bare local filesystem path shape; does not claim URLs, relative names, or scheme-ful input; absolutizes protocol-relative URLs as https and leaves everything else alone |
| `electron/local-filesystem-path.ts` | Pure path/URL predicates for the main-process opener. Kept out of external-open.ts so `classifyOpenTarget`-style decisions stay testable without electron, and so protocol-relative `//host/path` can never silently |
| `electron/local-gateway-deadline.test.ts` | Tests: an ensure client that ignores termination is killed and its promise rejects within a second deadline; a stale-owner restart client that times out but obeys SIGTERM is logged and the re-ensure attaches; the defaul… |
| `electron/local-gateway-python-bundled.test.ts` | #138906 (RT-21): the Store/MSIX bundled backend is `kind: 'python'` but its command is the payload's CLI shim (bin/hermes.exe), which rejects the ticket helper's `-P -u -c`. This runs the real resolver and helper proces… |
| `electron/local-gateway-python-launcher-argv.test.ts` | Tests: a .cmd override in a path with spaces asks its launcher for the runtime as one quoted token; a launcher spawned without a shell keeps its bare path |
| `electron/local-gateway-python-native.test.ts` | Tests for `local-gateway-python-native` |
| `electron/local-gateway-python-runtime.test.ts` | Tests: a Python backend is the helper interpreter as-is; a bundled launcher keeps its CLI command but names the payload Python for ticket minting; backends with no interpreter to name stay refused |
| `electron/local-gateway-python.test.ts` | This exercises the real helper process and protocol on this host. The native probe separately exercises Windows SID checks and HTTP/WS admission. |
| `electron/local-gateway-python.ts` | Exports `closeGatewayTicketBridges`, `ticketRuntimeFor`, `createGatewayTicketResolver`, `mintGatewayTicketWithPython` |
| `electron/local-gateway-restart-detach.test.ts` | A real bounded client against a fake `hermes`: `new` knows `--detach`; `old` predates it and rejects it the way argparse does. Each run appends its argv, so the test reads what was executed. |
| `electron/local-gateway-stale-restart-owner.test.ts` | dokterdok N71: two owners (the multiplexer and a standalone profile with multiplex off) on the same stale code are two processes; the second must be restarted too, not attached as-is. |
| `electron/local-gateway-symlinked-home.test.ts` | B2-17: with a symlinked ~/.hermes (dotfiles link, macOS /var -> /private/var) the raw launch HERMES_HOME is not canonical. The sibling profile home is built from the endpoint's own resolved profile_id, so mintLocalGatew… |
| `electron/local-gateway-ticket-identity.test.ts` | A gateway ticket names a profile home by the identity the gateway reserved for it: its `Path.resolve()`, which Desktop must reproduce exactly or the gateway refuses the ticket. |
| `electron/local-gateway-unsafe-path.test.ts` | Tests: an unsafe control path surfaces without forgetting and re-ensuring the same owner |
| `electron/local-gateway.test-helpers.ts` | Temp homes for the local-gateway suites that bind real AF_UNIX control sockets. sun_path is 104 bytes on macOS (108 on Linux). There os.tmpdir() is /var/folders/xx/<28 chars>/T (~49 chars, /private/var/... once realpath… |
| `electron/local-gateway.test.ts` | Tests: the ensure client inherits the caller-scrubbed parent env, not the raw Desktop env; a shell-delegated ensure quotes a spaced Windows install path (#74064); canonical ensure cannot cross a rejected update or profi… |
| `electron/local-gateway.ts` | `hermes gateway ensure` answers with a protocol verdict (ready, or `starting: deadline`) within its own startup deadline: `--timeout` defaults to 60 s (hermes_cli/gateway_runtime.py DEFAULT_ENSURE_TIMEOUT). The client i… |
| `electron/local-read-path.test.ts` | resolveLocalReadPath is the WSL->Windows bridge every file-read boundary must route its raw path through on a Windows host. Spy on it so each test asserts the boundary *applies* the bridge (and with what argument) rathe… |
| `electron/local-read-path.ts` | Path preparation shared by the file-read boundaries that hand a backend- reported target to the hardening resolvers. On a Windows host with a WSL backend the target is a WSL/POSIX path (`/home/...`, `/mnt/c/...`) the |
| `electron/local-runtime-version.test.ts` | Tests: local client version source; parses the exact version line emitted by the local launcher; probes the installation launcher with a bounded command and ignores remote values; fails closed when the local launcher ca… |
| `electron/local-runtime-version.ts` | Exports `VersionProbeRunner`, `parseLocalRuntimeVersion`, `resolveLocalRuntimeVersion`, `resolveDesktopClientVersion` |
| `electron/local-skin.test.ts` | Tests: reads a configured custom skin without a live gateway; reads the active named profile instead of the root home; uses a routed session or hud profile before any gateway can connect; returns built-in names even tho… |
| `electron/local-skin.ts` | Read the local display skin without asking the active gateway. This is used at renderer boot so a Desktop window can still paint its configured local skin when its primary connection is a remote gateway that is offline. |
| `electron/log-rotation.test.ts` | Tests: a log under the cap is left alone, whatever its path; an oversized log cascades to backups instead of growing forever; a boot-loop log past the discard ceiling is reclaimed, not stranded in .1; a log a live proce… |
| `electron/log-rotation.ts` | Any log the shell keeps across launches needs a size bound — desktop.log has been seen at ~326 GB, which exhausts the disk and then breaks update/install (no room for git/venv/npm temp files). |
| `electron/mac-usage-strings.test.ts` | TCC usage strings live in electron-builder.config.cjs's mac.extendInfo — without them a hardened-runtime (signed) build is denied Contacts / Apple Events access silently: macOS requires the usage description BEFORE it w… |
| `electron/machine-profile.test.ts` | Tests: registers the renderer channel and reports native machine facts with the OS locale |
| `electron/machine-profile.ts` | Exports `MachineProfile`, `registerMachineProfile` |
| `electron/main-process-lag-watchdog.test.ts` | Tests: createMainProcessLagWatchdog; does not log while ticks arrive on their expected cadence; records actionable timing when a main-process tick arrives late; cleans up its interval and does not log after stop |
| `electron/main-process-lag-watchdog.ts` | Exports `createMainProcessLagWatchdog` |
| `electron/main-window-lifecycle.test.ts` | Tests: recreates a destroyed primary window without focusing it; waits for app readiness before recreating a primary window; focuses a live primary window for a normal second launch; leaves live-window focus to deep-lin… |
| `electron/main-window-lifecycle.ts` | Exports `ensureMainWindow`, `shouldQuitOnLastChatClosed`, `activateWindow` |
| `electron/main.ts` | TypeScript source: `main` |
| `electron/managed-ssh-update.test.ts` | Tests: ManagedConnectionUpdateGate blocks new dials but admits the exact restoring transaction; durable recovery claim survives memory release and fences ordinary dials, edits, and removal; inactive SSH crash recovery k… |
| `electron/managed-ssh-update.ts` | Desktop-managed SSH update transaction. This module is intentionally Electron-free. main.ts owns the concrete pool maps, while this file owns the security-sensitive ordering and the remote wire protocol: gate dials -> d… |
| `electron/mcp-oauth-callback-ipc.test.ts` | Tests for electron/mcp-oauth-callback-ipc.ts — the client-side one-shot loopback listener MCP OAuth uses against remote backends. Uses a REAL ephemeral http listener (it binds 127.0.0.1:0, no fixed ports) with the elect… |
| `electron/mcp-oauth-callback-ipc.ts` | mcp-oauth-callback-ipc.ts Client-side loopback callback listener for MCP OAuth against a REMOTE backend. The gateway's own `mcp.servers.oauth.start` flow binds its callback listener on the BACKEND machine's 127.0.0.1 —… |
| `electron/media-capture-permission.test.ts` | Tests: isMediaCapturePermission; allows the fullscreen permissions both handlers can receive; allows the capture permissions without metadata (check-handler shape); allows a media request with audio or video mediaTypes |
| `electron/media-capture-permission.ts` | Exports `MediaCapturePermissionString`, `MediaCapturePermissionDetails`, `MediaPermissionRequestDetails`, `isMediaCapturePermission` |
| `electron/media-protocol.test.ts` | Tests: media protocol helpers; recognises only supported audio/video extensions case-insensitively; forwards range/cache negotiation headers but strips renderer credentials; preserves a configured gateway path prefix |
| `electron/media-protocol.ts` | Exports `MEDIA_PROTOCOL`, `MediaRemoteScope`, `MediaRemoteConnection`, `MediaProtocolDependencies`, `mediaProtocolDownloadName`, `isStreamableMediaPath` … |
| `electron/media-range.test.ts` | Tests: media-range: parseByteRange; parses open, closed and suffix ranges; ignores multi-range requests as a whole (RFC 7233 allows answering 200 instead of multipart); returns null without a usable Range and unsatisfia… |
| `electron/media-range.ts` | Range-aware responses for local audio/video served through `hermes-media://stream/…`. The media protocol used to delegate local files to `net.fetch(file://…)` and forward the renderer's `Range` header, expecting a `206… |
| `electron/minimize-to-tray-native-fixture/main.ts` | Targeted native lifecycle probe: compile this fixture with esbuild (external: electron, dbus-native), then run Electron <fixture.cjs> <fresh userData> <icon>. No backend, renderer dev server, CDP listener, or real user… |
| `electron/minimize-to-tray.test.ts` | Tests: tray hide defers past the minimize dispatch (#119252); Windows restore re-activates the window instead of showInactive (#119252); Windows restore of a tray-hidden window by any other path activates it (#127349);… |
| `electron/minimize-to-tray.ts` | Exports `MinimizeToTrayStatus`, `createMinimizeToTray` |
| `electron/native-access-token.test.ts` | Tests: normalised hosts share a rotation, and late bearer rejections reuse its winner; a pending or abandoned login preserves the existing refresh flight and its rotation; explicit token mutations fence stale success an… |
| `electron/native-access-token.ts` | Exports `NativeAccessTokenOptions`, `NativeAccessTokenCoordinatorDeps`, `NativeAuthChangedError`, `createNativeAccessTokenCoordinator` |
| `electron/native-auth-decisions.test.ts` | Regression tests for electron/native-auth-decisions.ts — the pure decision seams behind the RFC 8252 native-app auth flow, each of which was a real runtime bug that the mocked flow tests could not catch. Run via the vit… |
| `electron/native-auth-decisions.ts` | native-auth-decisions.ts Pure decision helpers extracted from main.ts for the RFC 8252 native-app auth flow. These encode six choices that were each the site of a real runtime bug — invisible to the mocked flow tests be… |
| `electron/native-gesture-monitor.ts` | Exports `NativeGestureStatus`, `NativeGestureOptions`, `NativeGestureMonitor` |
| `electron/native-oauth-login.test.ts` | Tests for electron/native-oauth-login.ts — the loopback-listener orchestration of the RFC 8252 native login, with all I/O injected (fake http server, fake openExternal, fake token POST) so no real socket or browser is n… |
| `electron/native-oauth-login.ts` | native-oauth-login.ts Electron-coupled driver for the RFC 8252 native-app login: it runs the loopback HTTP listener that catches the gateway's browser redirect, opens the system browser, redeems the one-time code for to… |
| `electron/native-oauth.test.ts` | Tests for electron/native-oauth.ts — the pure RFC 8252 native-app login helpers (PKCE, capability detection, URL building, loopback callback parsing, token-response normalization, refresh-timing). Run with: node --test… |
| `electron/native-oauth.ts` | native-oauth.ts Pure, electron-free helpers for the desktop's RFC 8252 (OAuth 2.0 for Native Apps) login to a gated Hermes gateway: system-browser + loopback redirect + PKCE, with tokens returned to the app (never brows… |
| `electron/native-token-store.test.ts` | Tests for electron/native-token-store.ts — the encrypted-at-rest persistence seam main.ts uses for RFC 8252 native OAuth tokens. The regression this file exists for (#73271): tokens are persisted as a normalized camelCa… |
| `electron/native-token-store.ts` | native-token-store.ts The encrypted-at-rest persistence seam for RFC 8252 native OAuth tokens: NativeTokenSet → JSON → safeStorage blob → store file, and back again on the next launch. Kept standalone (no `import 'elect… |
| `electron/native/command-screenshot-monitor.m` | Objective-C source file |
| `electron/native/hud-modifier-gesture.cs` | C# source file |
| `electron/native/hud-modifier-gesture.h` | C header |
| `electron/native/hud-modifier-gesture.test.c` | Tests for `hud-modifier-gesture` |
| `electron/native/hud-modifier-monitor-win.cs` | C# source file |
| `electron/native/hud-modifier-monitor-x11.c` | C source file |
| `electron/native/hud-modifier-monitor.m` | Objective-C source file |
| `electron/native/hud-modifier-x11.test.py` | Exercise the actual XI2 helper on a PRIVATE Xvfb server, never the user's display. |
| `electron/no-console-git.test.ts` | Tests: a timed-out git command reaps descendants, including the Windows Python host; app quit kills a timed git command still running, descendants included; windows git spawn uses a CREATE_NO_WINDOW host and does not re… |
| `electron/no-console-git.ts` | Electron is a GUI-subsystem process, so a direct git.exe spawn allocates its own console even when Node's windowsHide is set. windowsHide is SW_HIDE and, from a console-less parent, does not stop that flash (hermes_cli/… |
| `electron/notification-actions.test.ts` | Tests: prefers Electron event details and supports the legacy positional index; ignores missing and out-of-range action indexes |
| `electron/notification-actions.ts` | Exports `resolveNotificationAction` |
| `electron/notification-ipc.test.ts` | Tests: returns native clicks and approval actions to the emitting window, not the primary; delivers plugin callbacks to their source and falls back only for navigation after it closes |
| `electron/notification-ipc.ts` | Exports `registerNativeNotifications` |
| `electron/notification-linux.test.ts` | Tests: bounds failed delivery without dropping older callbacks, and retries only on a later request; releases naturally closed notifications while retaining other click targets; preserves activation, dedupe and source o… |
| `electron/notification-linux.ts` | Exports `createLinuxNotifications` |
| `electron/notification-registry.test.ts` | Tests: retains a dismissed banner until its later click or action is consumed; releases terminal closes immediately when opted in without expiring unrelated notifications early; dismisses an expired notification before… |
| `electron/notification-registry.ts` | Exports `createNotificationRegistry` |
| `electron/notification-types.ts` | Exports `HermesNotification` |
| `electron/oauth-auth-recovery.integration.test.ts` | Real HTTP and encrypted temp-file persistence; no Electron, OS keychain, application state, external gateways or real credentials are touched. |
| `electron/oauth-login-flights.test.ts` | Tests: a burst of background 401s opens one window for the gateway; a failed background login is held until its cooldown expires; the backoff doubles per consecutive failure, stops at the ceiling, and clears on success;… |
| `electron/oauth-login-flights.ts` | One OAuth login window per gateway cookie jar. A gated remote gateway answers every cookie-less request with `401 {reason: "no_cookie"}`, and each refused request used to answer that with its own login window (`retryCoo… |
| `electron/oauth-login-window.test.ts` | Tests: an unattended sign-in never shows its window and gives up after the deadline; an unattended attempt that lands on the gateway chooser stops at once; a revealed attempt stays open on the chooser for the user; a cl… |
| `electron/oauth-login-window.ts` | The embedded gateway sign-in window (cookie-mode OAuth). The window loads the gateway in the connection's cookie partition, follows the IdP round trip back to `/auth/callback`, and settles as soon as the session cookie… |
| `electron/oauth-navigation.test.ts` | Tests: isExpectedOauthNavigationAbort; treats Electron ERR_ABORTED callback navigation as non-fatal; does not suppress genuine gateway load failures |
| `electron/oauth-navigation.ts` | Exports `isExpectedOauthNavigationAbort` |
| `electron/oauth-net-request.test.ts` | Tests for OAuth-session Electron net.request helpers. Run with: node --test electron/oauth-net-request.test.ts |
| `electron/oauth-net-request.ts` | Helpers for Electron net.request calls that ride the OAuth session partition. Electron's ClientRequest forbids app-set restricted headers such as Content-Length. Let Chromium frame the body itself; only set the JSON con… |
| `electron/oauth-partition.test.ts` | #92183 — two basic-auth (cookie-flow) gateways registered in the v2 connections registry must not share one cookie jar. Chromium cookie jars ignore the port, so two gateways on the same VPN host (different ports) |
| `electron/oauth-partition.ts` | oauth-partition.ts Per-connection cookie-jar isolation for cookie-authenticated (OAuth / dashboard basic-auth) remote gateways (#92183). Historically every cookie-mode remote rode ONE Electron session partition (`persis… |
| `electron/oauth-rest-request.test.ts` | Tests: a cookie 401 is replayed only for a gate refusal on an idempotent or vouched operation; background roster auth leaves a gate 401 for the source row without clearing cookies or opening login; background auth inten… |
| `electron/oauth-rest-request.ts` | Exports `OauthRestRequestDeps`, `requestWithOauthFallback`, `MintGatewayWsTicketDeps`, `withoutInteractiveOauthLogin`, `canShowInteractiveOauthLogin`, `retryCookie401WithLogin` … |
| `electron/oauth-session-response.ts` | Response-stream extraction based on Bartok9's #99135 (original issue #72530). |
| `electron/open-missing-file.test.ts` | #122027: a deleted/renamed file handed to the OS comes back as "No application found to open URL" on the open path (LaunchServices kLSApplicationNotFoundErr doubles as the missing-file answer on macOS), and |
| `electron/package-process-reap.test.ts` | Tests: isUnderInstallRoot; matches an image nested under the root regardless of case or separator; does NOT match a sibling package whose name merely shares the prefix; does not match another vendor, an unreadable path,… |
| `electron/package-process-reap.ts` | Clean up detached package tools without touching shared runtimes. Package-owned gpg-agent can outlive its parent and pin an MSIX silo, preventing subsequent activation. A root claim never includes the shared tool store.… |
| `electron/packaged-working-directory.test.ts` | The resident helper (an IME cloud service, a WSL/ssh helper) that the app spawns WITHOUT a cwd of its own, so it inherits the app's. It outlives the app and holds that directory as its cwd for as long as it lives. `deta… |
| `electron/packaged-working-directory.ts` | Exports `WorkingDirectoryFacts`, `packagedWorkingDirectoryTarget`, `releasePackagedWorkingDirectory` |
| `electron/parent-process-identity.test.ts` | Tests: electronProcessStartMarker uses Electron creation time only for its own PID; electronProcessStartMarker rejects unavailable or invalid creation times; parentWatchdogEnv emits an exact identity when the marker is… |
| `electron/parent-process-identity.ts` | Exports `ParentWatchdogEnv`, `electronProcessStartMarker`, `parentWatchdogEnv`, `spawnTag` |
| `electron/payload-backend.test.ts` | Tests: bundled launch paths come from build metadata without filesystem access; ticket minting runs the payload python, never the CLI shim; installIdForRoot matches the Python install id (sha16 of the canonical path); b… |
| `electron/payload-backend.ts` | Electron consumes the launch contract completed by the PM bundle builder. |
| `electron/pet-overlay-ipc.ts` | IPC surface for the pop-out pet overlay (mascot window). Extracted from main.ts; window handles stay injected because main.ts owns their lifecycle. |
| `electron/pet-overlay.test.ts` | Unit tests for the pet-overlay geometry helpers. These cover the logic that protects the popped-out pet: a remembered spot on a since-unplugged monitor must never strand the overlay off-screen (the "pet vanished" bug),… |
| `electron/pet-overlay.ts` | Pure geometry helpers for the popped-out pet overlay — deciding where its window may open and where it must be re-homed when the display topology changes. Side-effect-free so the on-screen validation is unit-testable wi… |
| `electron/plugin-files-guards.ts` | Path rules for the `ctx.files` door (plugin-files.ts): how a plugin-supplied relative path is split, how containment is compared, and which folders can never be granted. Pure helpers plus filesystem identity checks; no… |
| `electron/plugin-files-hardening.test.ts` | `ctx.files` refusals beyond plain containment: sensitive files moved out of their names, kernel pseudo-filesystems, FIFOs, hard links, a folder or file swapped between the check and the open, and the grants record itsel… |
| `electron/plugin-files-ipc.test.ts` | A folder grant is minted only by the native picker main opens itself: the renderer names the plugin and the picker labels, never a path. |
| `electron/plugin-files-ipc.ts` | IPC for the plugin SDK's folder-scoped file door (`ctx.files`). The only way a folder grant is ever minted is `hermes:pluginFiles:request`: main opens the native folder picker itself, attached to the window that asked,… |
| `electron/plugin-files-ops.ts` | The operations behind `ctx.files` (plugin-files.ts owns grants and path resolution). Each op gets a target already resolved inside its folder and re-applies the per-op rules: size caps, sensitive names, no op on the fol… |
| `electron/plugin-files-spellings.test.ts` | `ctx.files` refusals for a second spelling of a path: case on a case-sensitive macOS volume, Unicode case folding, macOS named forks, WSL shares, loopback admin shares, and kernel pseudo-filesystems mounted somewhere a… |
| `electron/plugin-files.test.ts` | The folder-scoped plugin file door (`ctx.files`). Every refusal here is the main process's own: the renderer (and the plugin in it) only names a folder handle and a relative path, and this module decides what that may r… |
| `electron/plugin-files.ts` | The folder-scoped file door behind the plugin SDK's `ctx.files`. A plugin names a folder handle (`'data'` = its own data folder, or the id of a folder the user granted it through the app's picker) plus a RELATIVE path;… |
| `electron/plugin-profile-routes.test.ts` | Tests: buildOpaqueProfileRoutes; groups SSH aliases by their effective route without exposing endpoint data; changes opaque IDs when the effective SSH destination changes; keys IDs to the Desktop installation |
| `electron/plugin-profile-routes.ts` | Exports `ProfileRouteConfig`, `EffectiveSshRoute`, `OpaqueProfileRoute`, `isLocalEnumerationFailure`, `localRouteFallbackProfiles`, `undialedSshRouteSeeds` … |
| `electron/plugin-ws-url.test.ts` | PLG-1: a local gateway's plugin socket rides the native-http grant its REST twin uses. The grant is attached as a header to the one dial main prepared, never placed in the renderer's URL. |
| `electron/plugin-ws-url.ts` | What the renderer's `pluginSocket` asks for: its plugin namespace, the path under it, and the (connectionId, profile) route every other plugin call resolves through. |
| `electron/portal-cookies.test.ts` | Contract: NAS accepts either credential family during the auth migration, so the Desktop must read both, and must tell renewable-only jars (signed in, discovery would 401) apart from jars that can pass /api/agents right… |
| `electron/portal-cookies.ts` | Exports `PortalCookie`, `portalAccessCookies`, `cookiesHavePortalAccessToken`, `cookiesHavePortalSession` |
| `electron/portal-session-live-fixture/main.ts` | Real Chromium cookies, HTTP redirects and renderer requests. All credentials are synthetic and the portal is loopback-only; no existing Electron jar is used. |
| `electron/portal-session-live.test.ts` | Chromium needs a display. macOS and Windows always have one; a headless Linux runner gets a virtual one through xvfb-run when it is installed (the js-tests CI image installs it for this file). Resolved once so the skip… |
| `electron/portal-session.test.ts` | Tests: a superseded portal navigation stays open until the new access cookie lands; a real portal load failure still ends sign-in |
| `electron/portal-session.ts` | Exports `resolvePortalBaseUrl`, `createPortalSession` |
| `electron/power-resume-remote-revalidation.test.ts` | Tests: revalidateSuspectPooledRemoteBackends (#93910); retires and rebuilds a dead-tunnel descriptor while leaving a healthy one alone; retires a dead descriptor on the FIRST failed post-resume probe, not after a failur… |
| `electron/power-save.test.ts` | Tests: createKeepAwake; starts once, is idempotent, and stops; re-arms after the OS dropped the blocker; keep-awake mode |
| `electron/power-save.ts` | Keep-awake — hold a single machine-global power-save blocker. `prevent-app-suspension` stops the system from sleeping (long overnight agent runs keep going) while still letting the display dim. The renderer owns the pre… |
| `electron/pre-update-backup-config.test.ts` | Tests: preUpdateBackupEnabled; readPreUpdateBackupEnabled; fails safe when runtime resolution fails |
| `electron/pre-update-backup-config.ts` | Exports `preUpdateBackupEnabled`, `HermesConfigRuntime`, `readPreUpdateBackupEnabled` |
| `electron/preload-external-open.test.ts` | Tripwire for the dead-wiring class: main broadcasts `hermes:external-open- failed` and the dialog subscribes via `onExternalOpenFailed` — with no preload forwarder in between the dialog never fires and the failure is |
| `electron/preload-flags.test.ts` | Tests: publishes the feature flags answered by main before the renderer starts; forwards full renderer error lines through the exposed bridge |
| `electron/preload-local-skin.test.ts` | Tests: the preload carries the local skin across before the renderer starts |
| `electron/preload-version-scope.test.ts` | Tests: forwards the connection/profile scope to hermes:version |
| `electron/preload.ts` | Which translucency the OS can back. Asked synchronously because the renderer needs it before its first paint, and answered by main because deciding it needs `os.release()` — a sandboxed preload may only require electron… |
| `electron/prepared-submissions.test.ts` | Tests: acknowledged journal mutations survive reopening with exact payload and origin isolation; a corrupt journal is quarantined with its bytes kept, and the origin can send again |
| `electron/prepared-submissions.ts` | Match localStorage's origin isolation; destination keys additionally carry connection/profile/session authority. No renderer-provided filesystem paths. |
| `electron/preview-capture.test.ts` | Tests: normalizeCaptureRect floors origin and ceils size, never zero; mapViewportRectToImage scales CSS pixels onto a DPR bitmap and clamps; capturePreviewContents captures the visible page then crops in bitmap space; c… |
| `electron/preview-capture.ts` | Crop a preview webview via webContents.capturePage. Electron's rect argument is unreliable on guest webviews (empty NativeImage on Windows, DPI-shifted crops). Capture the visible viewport, then crop in bitmap space fro… |
| `electron/preview-file-watch.test.ts` | Unit tests for owner-routed preview/plugin file-watch delivery (#108189). Secondary windows filter by their own watch id, so events must land on the registering WebContents — never the primary alone. |
| `electron/preview-file-watch.ts` | Owner-routed delivery for desktop preview/plugin file watches (#108189). Each watch is owned by the WebContents that registered it. Change events must go back to THAT renderer — secondary windows filter `hermes:preview-… |
| `electron/preview-guest-escape.test.ts` | Tests: previewGuestInputAction; exits fullscreen on Escape only while the host window is fullscreen; closes the preview on Ctrl+Shift+W regardless of fullscreen state; also accepts the Cmd+Shift+W (macOS) form |
| `electron/preview-guest-escape.ts` | The preview pane's escape hatch (#97213). A `<webview>` guest is its own out-of-process webContents: once a guest page takes HTML5 fullscreen it owns the input focus, and nothing in the host renderer — menus, HUD chords… |
| `electron/preview-guest-offscreen.test.ts` | Tests: focused preview guest gestures; navigates the focused guest its host reports on screen; leaves a focused guest its host reported hidden untouched; takes visibility only from the renderer that embeds the guest |
| `electron/preview-guest-offscreen.ts` | Preview guests that are mounted but OFF SCREEN. A hidden session's Browser stays mounted (hidden, inert) so returning to that session shows the same page. Chromium still tracks its guest as the focused webContents after… |
| `electron/preview-guest-preload-entry.ts` | Preload for the preview pane's `<webview>` guests. main.ts installs this file via `will-attach-webview` on the `persist:hermes-preview` partition only (see `installPreviewGuestPreload`), so no other webview inherits it. |
| `electron/preview-guest-preload.test.ts` | Preview-pane guest bridge (#112941): the preload forwards a user's click on a `_blank` anchor to the host and nothing else. |
| `electron/preview-guest-preload.ts` | Logic half of the preview pane's guest preload. The wiring half lives in `preview-guest-preload-entry.ts` (the bundled preload itself); this split keeps the handoff rules unit-testable in a plain Node environment. |
| `electron/preview-guest-throttle.test.ts` | Tests: applyPreviewGuestAttachPrefs; keeps the preview guest animating while the Desktop window is in the background; leaves every other webview alone |
| `electron/preview-guest-throttle.ts` | Partition the preview pane's `<webview>` always carries. |
| `electron/preview-reach.e2e.mts` | E2E: the real preview-reach module against a real remote host. Not a unit test — this spawns actual `ssh -N -L` tunnels to a live box and fetches a dev server that is bound to THAT machine's loopback and is |
| `electron/preview-reach.test.ts` | Tests: loopbackTarget; accepts any port, not a curated list; defaults the port by scheme; rewriteToLocalPort |
| `electron/preview-reach.ts` | Loopback reach for the in-app browser against a REMOTE gateway. The `<webview>` renders on the user's machine. The agent runs on the gateway host. So when the agent says "your dev server is at http://localhost:5173", th… |
| `electron/preview-url-target.test.ts` | Tests: previewHttpUrlTarget; navigates a public https page; keeps a loopback dev server and rewrites the 0.0.0.0 bind address; navigates a plain-http public page and a LAN host |
| `electron/preview-url-target.ts` | HTTP(S) targets for the in-app preview pane. The pane is the desktop's browser: a public page the user asked to open has to navigate. Loopback stays special only for the 0.0.0.0 bind address, which the webview cannot lo… |
| `electron/primary-backend-cancellation.test.ts` | Tests: quit cancels first-run startup without entering the installer |
| `electron/primary-backend-startup.test.ts` | Tests: primary remote descriptor preserves a resolved registry connection id; primary remote descriptor preserves the gateway extra headers for REST calls; primary remote descriptor preserves the effective SSH dialing i… |
| `electron/primary-backend-startup.ts` | Exports `PrimaryBackendStartupOptions`, `PrimaryBackendStartupResult`, `createPrimaryRemoteConnection`, `FirstRunSetupResetError`, `runPrimaryBackendStartup` |
| `electron/primary-connection-rehome.ts` | Exports `PrimaryConnectionRehomeOptions`, `rehomePrimaryConnection` |
| `electron/primary-profile-pin.test.ts` | Tests: a live primary keeps answering for its booted profile after the preference moves; teardown releases the pin so the next start follows the preference; one launch decision feeds routing, argv, and env from the same… |
| `electron/primary-profile-pin.ts` | Which profile the PRIMARY (window) backend answers for. Two signals exist and they legitimately disagree mid-session: - the stored preference (active-profile.json) — the profile Desktop should boot into on the NEXT laun… |
| `electron/product-identity.test.ts` | product-identity.cjs is the single derivation of the desktop product identity; electron/product-identity.ts re-exports it. These tests hold the identity contract: the TS accessor resolves to the .cjs object, and |
| `electron/product-identity.ts` | product-identity.ts — the typed build-time product identity. product-identity.cjs is the single derivation of every name-shaped value a variant owns (product name, appId, channel). Dev bundles and |
| `electron/profile-delete-routing.test.ts` | Tests: profileNameFromDeleteRequest parses a DELETE /api/profiles/<name> path; profileNameFromDeleteRequest lowercases the profile name; profileNameFromDeleteRequest returns null for non-DELETE methods; profileNameFromD… |
| `electron/profile-delete-routing.ts` | Profile-delete routing logic for the `hermes:api` IPC handler. When the renderer issues DELETE /api/profiles/<name>, the handler must tear down every local backend for that profile and route the DELETE itself |
| `electron/profile-id-guard.ts` | Profile ids that cross into backend/TUI spawn argv must be non-empty PROFILE_ID_RE slugs. Anything else (a numeric roster/DB id, an empty string, a display label with spaces) must never reach `--profile <value>`: the CL… |
| `electron/profile-migration.test.ts` | Tests for electron/profile-migration.ts — pure migration-decision helpers for the active-profile.json first-boot seeding. Run with: `vitest run` (wired via the `electronNative` project in `apps/desktop/vitest.config.ts`… |
| `electron/profile-migration.ts` | Pure migration-decision helpers for active-profile.json first-boot seeding. Extracted from main.ts so they're unit-testable without Electron. The helpers here are deliberately side-effect-free except for the orchestrator |
| `electron/profile-rename-routing.test.ts` | Tests: profileRenameFromRequest parses string and object JSON bodies; profileRenameFromRequest rejects malformed and reserved rename requests; prepareProfileRenameLifecycle tears down a pooled backend and routes through… |
| `electron/profile-rename-routing.ts` | Exports `ProfileRenameRequest`, `ProfileRename`, `ProfileRenameLifecycleDeps`, `ProfileRenameLifecycle`, `profileRenameFromRequest`, `prepareProfileRenameLifecycle` |
| `electron/profile-routes.ts` | `/api/profiles/<suffix>` collection routes, by method (hermes_cli/web_routers/profiles.py). Any other method on these paths is the per-profile `/api/profiles/{name}` route of a profile NAMED `active`, `import`, `session… |
| `electron/profile-session-routing.test.ts` | Tests: remote session routing includes the mutation snapshot and session reads, no other child route; legacy remote owner route keeps the mutation identity query for the paired DELETE; all-profiles session routing is li… |
| `electron/profile-session-routing.ts` | Exports `isRemoteProfileScopeError`, `ProfileSessionsResponse`, `isAllProfilesSessionListRequest`, `isRemoteSessionRequestPath`, `tagRegistrySessionResponse`, `mergeProfileSessionWindow` … |
| `electron/quick-entry.test.ts` | Tests: quick-entry submit ack relay; ignores an ack for a stale correlation id; resolves an unacknowledged submit as an unknown, non-retryable timeout and keeps it reconcilable; reconciles a late success through onLateR… |
| `electron/quick-entry.ts` | Quick Entry — the global-hotkey mini composer. A small frameless always-on-top window that a global shortcut summons from anywhere so the user can fire a prompt at Hermes without raising the whole app. The window carrie… |
| `electron/quit-finalization.test.ts` | #116376: on Windows, closing the last window ran the whole JS quit path (window-all-closed → app.quit → before-quit teardown → will-quit) and the process still stayed resident with 0 windows. The fallback must force the… |
| `electron/quit-finalization.ts` | Exports `QuitFinalizationOptions`, `QuitFinalization`, `createQuitFinalization` |
| `electron/quit-guard.test.ts` | Tests: normalizeActiveWork drops junk and keeps the count at least the title count; normalizeActiveWork keeps untitled sessions in the count; mergeActiveWork de-dupes a session two windows both report; quitPromptFor sta… |
| `electron/quit-guard.ts` | Quitting with a turn in flight kills the backend mid-tool-call: the work is lost, and anything the agent had half-written to disk stays half-written. Renderers publish what they're running; the main process asks before… |
| `electron/quit-teardown.test.ts` | Tests: remote-only cleanup does not cancel the original quit; a settled remote descriptor is not backend work that requires a deferred quit; one final quit waits for every required teardown branch; teardown failure stil… |
| `electron/quit-teardown.ts` | Exports `QuitTeardownTask`, `QuitTeardownCoordinator`, `BackendQuitActivity`, `backendQuitNeedsWait`, `BackendTeardownIntent`, `backendTeardownOptions` … |
| `electron/registry-backend-identity.test.ts` | Tests: installIdFromStatus reads a non-empty install_id only; a slow or failing identity probe reads as unknown; the primary install id is cached per backend URL and re-probed when the primary moves; an unresolvable pri… |
| `electron/registry-backend-identity.ts` | Backend identity for the unified session list (RT-42). Session totals are counted once per BACKEND, keyed on the gateway `install_id` that `/api/status` reports (`hermes_cli/install_identity.py`). A sidebar refresh neve… |
| `electron/registry-primary-profile-scope.test.ts` | Tests: primary-remote descriptor reuse keeps profile scope; does not boot ineligible primaries or reuse a different live identity |
| `electron/relaunch-target.test.ts` | Tests: ownAppImage; spawnRelaunch; strips the mount it runs from when APPDIR was lost |
| `electron/relaunch-target.ts` | AppImage is Linux-only; POSIX semantics keep the answer identical on every test host. |
| `electron/release-holder-consent.test.ts` | Tests: #101789: a swap blocked by a program outside Hermes names it and closes it only on an explicit click; review N3: a holder that cannot be closed from here is named for the user, with no Close button; review N1: th… |
| `electron/release-holder-consent.ts` | The Desktop half of the consented "close it and retry" for a Desktop app swap blocked by a program outside Hermes (#101789). The consent is bound to the ONE hand-off run the retry starts (its run id reaches the swap as… |
| `electron/remote-lifecycle-gate-transport.test.ts` | How the relaunch marker gate travels to the remote. `ssh.exec` rides the POSIX ControlMaster mux socket, which hands the client's stdio descriptors over with sendmsg(SCM_RIGHTS) after writing the session request. A requ… |
| `electron/remote-lifecycle-profile-missing.test.ts` | Tests: scrapeReadyPort explains a missing remote profile; scrapeReadyPort keeps the generic spawn failure for other exits |
| `electron/remote-lifecycle-spawn.test.ts` | Tests for `remote-lifecycle-spawn` |
| `electron/remote-lifecycle-v2-marker.test.ts` | Tests for `remote-lifecycle-v2-marker` |
| `electron/remote-lifecycle.test.ts` | Tests: SSH reuse proof rejects a backend whose runtime was replaced; SSH reuse proof remains compatible when runtime state is absent; POSIX relaunch gate refuses live and uncertain install markers without executing Herm… |
| `electron/remote-lifecycle.ts` | remote-lifecycle.ts Pure, electron-free remote Hermes dashboard lifecycle over SSH for Desktop SSH remote mode. Composes an SshConnection (injected) with HTTP probes through the established tunnel (injected fetch) and t… |
| `electron/remote-liveness.test.ts` | Tests: RemoteLivenessTracker; requires consecutive failures before resetting a connection; clears a failure streak after a successful probe; tracks different gateways independently |
| `electron/remote-liveness.ts` | Exports `REMOTE_LIVENESS_TIMEOUT_MS`, `POOLED_REMOTE_DISPATCH_PROBE_TIMEOUT_MS`, `REMOTE_LIVENESS_FAILURE_LIMIT`, `REMOTE_LIVENESS_FAILURE_WINDOW_MS`, `REMOTE_POOLED_LIVENESS_FAILURE_WINDOW_MS`, `RemoteLivenessFailure` … |
| `electron/remote-oauth-ticket.test.ts` | Tests: resolveRemoteOauthTicket; reserves a larger bounded roster dial budget only for OAuth remote sources; mints a fresh ticket on every dial even without a preflight native session; classifies only confirmed auth rej… |
| `electron/remote-oauth-ticket.ts` | Exports `rosterSourceEnumerationTimeoutMs`, `resolveRemoteOauthTicket` |
| `electron/remote-owner-cache.test.ts` | Tests: createRemoteOwnerCache (#58485); returns a fresh entry within the TTL and null past it; never grows past the limit: the oldest entry is FIFO-evicted; re-remembering an existing id refreshes it without growing the… |
| `electron/remote-owner-cache.ts` | Main-process memo: which remote profile owns a session id when the caller gave no profile hint (#85834). #58485: the memo only ever INSERTS — the TTL marks entries stale but never evicts — so a long-lived main process k… |
| `electron/remote-reauth-latch.test.ts` | Regression suite for issue #95701: an expired remote OAuth session must boot into ONE latched recovery overlay, not flicker between the connecting state and the overlay while the renderer re-drives a rejection that can… |
| `electron/remote-session-cookies.test.ts` | Tests: parseSetCookie; takes the first Name=Value pair and keeps the effective path; flags deletions: Max-Age<=0, a past Expires, or an empty value; returns null for unparsable headers |
| `electron/remote-session-cookies.ts` | remote-session-cookies.ts In-memory session-cookie mirror for remote gateways (#61457). The `persist:hermes-remote-oauth` partition family is supposed to keep the dashboard `hermes_session*` cookies on disk, but in the… |
| `electron/remote-ssh-exec.test-helpers.ts` | A local stand-in for `SshConnection.exec` used by the remote-lifecycle suites: runs the command through a POSIX shell and, like the real mux exec, writes `stdinData` to the remote process's stdin. A double that drops it… |
| `electron/remote-update-marker-programs.test.ts` | Tests for `remote-update-marker-programs` |
| `electron/remote-update-marker-programs.ts` | The update-marker judge as programs that run ON an SSH remote. Same contract as `update-marker-judge.ts` (`tests/fixtures/update_marker_corpus.json`), with its constants interpolated so no copy can drift: an identity (p… |
| `electron/remote-ws-headers.test.ts` | Tests: registry gateway WebSocket headers; evicts the least recently accessed exact URL; updates headers without changing insertion recency; token path binds headers to the exact profile scoped URL |
| `electron/remote-ws-headers.ts` | Exports `RegistryGatewayWsConnection`, `RemoteHeaderSource`, `collectRemoteHeaderSources`, `resolveRemoteRequestHeaders`, `formatLoadUrlExtraHeaders`, `oauthLoginLoadUrlOptions` … |
| `electron/renderer-accessibility.test.ts` | Tests: shouldEnableRendererAccessibility is on by default on the typed platforms; shouldEnableRendererAccessibility never enables on platforms without the typed API; shouldEnableRendererAccessibility honors the opt-out… |
| `electron/renderer-accessibility.ts` | renderer-accessibility.ts Chromium only builds the renderer's accessibility tree when it detects an assistive technology — and dictation tools that insert text through the OS accessibility APIs (Wispr Flow and similar)… |
| `electron/renderer-bundle.test.ts` | Tests: parseModuleAssetRefs collects module scripts and modulepreload hrefs; parseModuleAssetRefs ignores non-module tags (plain stylesheet, non-module script); parseModuleAssetRefs drops absolute/CDN URLs — they are no… |
| `electron/renderer-bundle.ts` | Renderer bundle generation check. `index.html` and the hashed chunks under `dist/assets/` are ONE generation: every `lazy()` route resolves to a filename baked into that generation's module graph. A self-update that rep… |
| `electron/renderer-crash-metrics.test.ts` | Tests: rendererCrashReason buckets Electron reasons; RendererCrashRecorder; records nothing until the user opts in; persists only bucketed reasons, ignores clean-exit, and caps the list |
| `electron/renderer-crash-metrics.ts` | Consent-gated renderer-crash counter for shared metrics. A crash can take the renderer (and its backend socket) down before anything is sent, so the main process persists a bucketed reason per render-process-gone and th… |
| `electron/renderer-heap-flags.test.ts` | #77311: the renderer heap ceiling knob (`desktop.renderer_max_old_space_mb`) and `desktop.electron_flags` must reach app.commandLine on packaged launches that never go through the `hermes desktop` launcher. |
| `electron/renderer-heap-flags.ts` | Renderer heap ceiling + `desktop.electron_flags` for packaged launches (#77311). Chromium only forwards `--js-flags` to renderer processes when the BROWSER process has the switch on its own command line before `ready`.… |
| `electron/renderer-load-error-page.test.ts` | Tests: error page names the failure and carries a Reload button; error page reload button targets the real renderer URL when provided; error page escapes HTML in failure details; reloadUrl cannot break out of the inline… |
| `electron/renderer-load-error-page.ts` | Visible renderer-load error page. The white-screen failure modes this exists for: 1. TORN BUNDLE after an update (#95575): `hermes update` replaces the app while its files are locked (antivirus, a still-running instance… |
| `electron/renderer-log.test.ts` | Tests: formatRendererConsoleLine; formats the canonical Electron console-message event at error level; drops a canonical non-error string level; drops malformed event objects |
| `electron/renderer-log.ts` | Renderer console/error capture shared by every renderer-content window. Historically only the primary window (`createWindow()`) attached a `console-message` hook, so a renderer crash in ANY other window — secondary sess… |
| `electron/renderer-manifest.test.ts` | Tests: Vite manifest validates lazy assets without opening their JavaScript; a manifest from another generation falls back to the existing lazy graph check |
| `electron/roster-source-fetch.test.ts` | Tests: roster source starts profile and install-id reads together and preserves both results; roster source preserves a profile-read failure after starting the install-id read |
| `electron/roster-source-fetch.ts` | Exports `fetchRosterSourceData` |
| `electron/roster-source-status.test.ts` | Tests: does not report stale cached profiles as a reachable or signed-in gateway |
| `electron/roster-source-status.ts` | Exports `rosterSourceStatus` |
| `electron/save-text-file.test.ts` | Tests: saveTextFileAs (Electron-side /save write); writes the content where the user chose, defaulting to a bare name in the default dir; asks before overwriting an existing file and can create a directory (Linux needs… |
| `electron/save-text-file.ts` | T11 (#134889): file-writing slash commands (/save) write on the Electron side. The gateway may be remote, so it only returns the rendered content; this module asks the user where the file goes (native save dialog) and w… |
| `electron/secret-storage-policy.test.ts` | Tests for electron/secret-storage-policy.ts — the "is OS-keychain encryption enabled at all?" decision seam. The behavior this file pins: keychain-backed encryption is OPT-IN (default OFF), and once the one-shot legacy… |
| `electron/secret-storage-policy.ts` | secret-storage-policy.ts Single owner of the "do we use the OS keychain at all?" decision for desktop-stored secrets (remote gateway tokens, CF Access headers, native OAuth token sets). Why this exists: Electron safeSto… |
| `electron/select-paths-dialog.test.ts` | Tests: selectPathsDialogProperties; lets a directory picker create a new folder (macOS hides New Folder without createDirectory); keeps file pickers file-only and multi-select by default; drops multi-select only when th… |
| `electron/select-paths-dialog.ts` | Exports `selectPathsDialogProperties` |
| `electron/select-runnable-binary.test.ts` | Tests: missing candidates are never probed, and nothing existing yields null for the caller fallback |
| `electron/select-runnable-binary.ts` | Exports `RunnableBinaryOptions`, `selectRunnableBinary` |
| `electron/semver.d.cts` | TypeScript (CommonJS) |
| `electron/session-windows.test.ts` | Tests: buildSessionWindowUrl puts the secondary flag before the hash route (dev server); buildSessionWindowUrl avoids a double slash when the dev server has a trailing slash; buildSessionWindowUrl carries the owning pro… |
| `electron/session-windows.ts` | Secondary "session windows" — one extra OS window per chat so a user can work with multiple chats side by side. The pure, Electron-free pieces live here so they can be unit-tested with node --test (mirroring how the res… |
| `electron/shell-path.test.ts` | Tests: extractSentinelPath survives profile banner noise around the markers; extractSentinelPath uses the last start marker (echoed command lines cannot poison it); extractSentinelPath returns null when markers are miss… |
| `electron/shell-path.ts` | Login-shell PATH resolution for GUI launches. A desktop app launched from Finder/Dock (macOS launchd) or a desktop environment's launcher (Linux) inherits a minimal PATH such as |
| `electron/singleton-lock.test.ts` | Tests: parseSingletonLockPid reads the owning PID only for this hostname; parseProcStateField survives a comm containing spaces and parentheses; a zombie or missing owner is stale; kill(pid,0) alone would say alive; rem… |
| `electron/singleton-lock.ts` | Parse the PID encoded in Electron's Linux SingletonLock symlink. Chromium's ProcessSingleton on Linux/X11 owns `<userData>/SingletonLock`, a symlink whose target is `<hostname>-<pid>` (#78101). The hostname prefix is th… |
| `electron/source-backend.test.ts` | Tests: Windows console selection uses only the selected interpreter directory |
| `electron/source-backend.ts` | Exports `SourceBackend`, `resolveSourceInstallationBackend`, `createSourcePythonBackend` |
| `electron/source-python.test.ts` | Tests: a checkout with no virtualenv resolves to no interpreter, never a PATH Python; a virtualenv-less checkout yields no source backend, so the ladder moves on; the checkout virtualenv is preferred over the flat venv,… |
| `electron/source-python.ts` | Exports `SourcePythonOptions`, `resolveSourcePython` |
| `electron/spawn-helper-perms.test.ts` | Tests: rewrites an archived node-pty root to the matching unpacked tree exactly once; uses the unpacked helper when resolution reports an app.asar node-pty root; needsExecBit / withExecBits treat any missing exec bit as… |
| `electron/spawn-helper-perms.ts` | node-pty ships its POSIX `spawn-helper` inside the published npm tarball with mode 0644 (no exec bit). node-pty `posix_spawnp`s that helper on macOS/Linux, so a non-executable helper fails every terminal spawn with |
| `electron/spellcheck-dictionary-ipc.test.ts` | Tests: normalizeDictionaryWord; accepts one word of letters, marks, digits, apostrophes and hyphens; refuses anything that is not exactly one bounded word; hermes:spellcheck:dictionary |
| `electron/spellcheck-dictionary-ipc.ts` | Spell-check dictionary IPC: the custom context menu's native spell-check verbs and the plugin SDK's `host.spellcheck` door. Every handler acts on the SENDER's own session (or the named webview guest's), one word per cal… |
| `electron/ssh-binary.test.ts` | #103288: one resolver picks the ssh client for every desktop spawn. Platform, env and filesystem are passed as data; nothing touches process.platform. |
| `electron/ssh-binary.ts` | Which ssh client the desktop spawns (#103288). Windows used to hard-code %SystemRoot%\System32\OpenSSH\ssh.exe for the `ssh -G` probes and the SSH terminal, while SshConnection spawned a bare |
| `electron/ssh-bootstrap-coordinator.test.ts` | Tests: sshConfigFingerprint covers scope and every connection field; same scope and fingerprint share one bootstrap; changed fingerprint waits for old rollback before starting; forceCleanupAll runs registered pending re… |
| `electron/ssh-bootstrap-coordinator.ts` | TypeScript source: `ssh-bootstrap-coordinator` |
| `electron/ssh-config.test.ts` | Tests: parseSshConfigHosts keeps literal aliases and drops wildcard/negated patterns; parseSshConfigHosts de-duplicates; parseSshConfigIncludes extracts include tokens; collectSshConfigHosts follows Include directives (… |
| `electron/ssh-config.ts` | ssh-config.ts Pure, electron-free helpers for reading the user's OpenSSH client config: `Host` aliases for the settings UI's suggestions, `Include` traversal (read-only), and `ssh -G` output parsing. No `import 'electro… |
| `electron/ssh-connection.test.ts` | Tests: redactSecrets scrubs the spawn-time session token env var; redactSecrets scrubs ?token= and ?ticket= URL params; redactSecrets scrubs Authorization and X-Hermes-Session-Token headers; redactSecrets handles null/u… |
| `electron/ssh-connection.ts` | ssh-connection.ts Pure, electron-free OpenSSH ControlMaster connection manager for Desktop SSH remote mode. Uses the system `ssh` client (not a JS SSH library) so it inherits ~/.ssh/config, the agent, jump hosts (ProxyJ… |
| `electron/ssh-control-master-holders.test.ts` | Tests: controlMasterCloseAction exits the master only for the last holder; holders are counted per ControlPath and released in any order; re-acquiring and double-releasing are idempotent; an empty ControlPath (no-mux) i… |
| `electron/ssh-control-master-holders.ts` | Who may run `ssh -O exit` on a shared ControlMaster socket. Every SshConnection built for the same scope/host/identity hashes to the same ControlPath, and ControlMaster=auto makes a later connection attach to |
| `electron/ssh-isolated-keepalive.test.ts` | #106935: Desktop main must hold a long-lived keep-alive WebSocket for every published SSH-isolated backend. Idle-exit (#101626) treats accepted WS as ownership liveness; renderer sockets can drop while sshConnections st… |
| `electron/ssh-isolated-keepalive.ts` | Long-lived keep-alive WebSocket from Electron main for every published SSH-isolated backend (#106935). `web_server_idle_exit` (#101626) treats accepted WebSockets as ownership liveness. Renderer sockets can vanish (`dis… |
| `electron/ssh-teardown.test.ts` | Tests: quit joins teardown whose SSH routing entry was already removed; a stuck SSH teardown and force cleanup cannot hang quit forever |
| `electron/ssh-teardown.ts` | Retain transports removed from routing until their remote kill has settled. |
| `electron/startup-latency-ipc.test.ts` | Tests: the launch latency is claimable once per app launch, whichever window asks |
| `electron/startup-latency-ipc.ts` | Launch -> first renderer gateway attach, claimable once per main process. Renderer reloads, extra windows and backend reconnects all re-run the renderer boot, so the latch must live here (the one object that spans the w… |
| `electron/stream-throttle.test.ts` | Tests: registering a window applies the current throttle state immediately; a turn in flight unthrottles every chat window; settling re-throttles after the trailing delay; a new turn during the trailing window cancels t… |
| `electron/stream-throttle.ts` | Stream-aware background throttling for chat windows. Chat windows must paint the live transcript while blurred, occluded, or minimized — but a static `backgroundThrottling: false` in webPreferences |
| `electron/system-ca.test.ts` | Tests: excludes expired roots and deduplicates real certificates with defaults first; excludes a root at its exact expiry while retaining valid defaults; installs Windows system CAs without dropping existing defaults; i… |
| `electron/system-ca.ts` | TypeScript source: `system-ca` |
| `electron/terminal-ipc.test.ts` | Tests: terminal start preserves the selected SSH target and scope; terminal start does not invent SSH when canonical routing selects local or remote HTTP; terminal start re-reads the SSH target after backend startup; ke… |
| `electron/terminal-ipc.ts` | The embedded terminal's PTY host: shell resolution, env scrubbing, session registry, and the hermes:terminal:* IPC surface. Extracted from main.ts; the factory owns the session map and returns the dispose helpers main.t… |
| `electron/terminal-lc-ctype.test.ts` | terminal-ipc.ts imports the Electron and native PTY modules at module scope; neither loads under plain node, and this test only needs the pure locale helper. |
| `electron/terminal-output-gate.test.ts` | Tests: holds the initial shell prompt until the renderer attaches; flushes buffered output before an early shell exit; attach is idempotent and never replays startup output twice |
| `electron/terminal-output-gate.ts` | Exports `TerminalExitPayload`, `createTerminalOutputGate` |
| `electron/terminal-pty-dispose.test.ts` | terminal-ipc.ts imports the Electron and native PTY modules at module scope; neither loads under plain node, so both are stubbed and the spawned PTY is a fake that captures its onData/onExit listeners. |
| `electron/titlebar-overlay-width.test.ts` | Tests: Windows reserves the overlay fallback width; WSLg custom controls reserve the same fallback width; WSLg disables the undersized native overlay in favor of renderer controls; native Windows and Linux keep the same… |
| `electron/titlebar-overlay-width.ts` | Exports `OVERLAY_FALLBACK_WIDTH`, `nativeOverlayWidth`, `titleBarOverlayOptions`, `scaledOverlayHeight`, `MACOS_TAHOE_DARWIN_MAJOR`, `macTitleBarOverlayHeight` |
| `electron/translucency.test.ts` | The translucency contract both processes read (` |
| `electron/translucency.ts` | Main-process side of window translucency. The mapping itself (modes, clamping, the clear-mode opacity ramp) lives in apps/shared so the renderer and the main process cannot drift; this module adds only what needs a Brow… |
| `electron/tray-host.test.ts` | Tests: a registered host is required, and losing its owner reports loss exactly once; dbus-native 0.15 returns the registered flag as a bare boolean; a missing host and a failed query reject without leaving an open bus… |
| `electron/tray-host.ts` | dbus-native 0.15 defaults plainValues to true, so a property Get returns the bare boolean. Older builds still wrap it as { value }. |
| `electron/ui-preferences-ipc.ts` | Wires the machine's UI preferences store (ui-preferences.ts) into Electron: every app window hears about a change, whoever made it. |
| `electron/ui-preferences.test.ts` | Native Desktop (this module) and the Webapp's Python server must land on ONE file and merge into it without losing each other's keys (#145213). |
| `electron/ui-preferences.ts` | Machine-level UI preferences (#145213): one JSON document beside the ROOT Hermes home, shared by native Desktop (this module, over the typed preload capability) and every browser that opens this machine's Webapp (the Py… |
| `electron/update-api-proxy.test.ts` | Tests: update API uses an HTTPS proxy only when the environment selects one; update API request reaches the configured HTTP CONNECT proxy |
| `electron/update-api-proxy.ts` | Node's https.get ignores proxy env vars; resolve them only for update API requests. |
| `electron/update-gate-cancellation.test.ts` | Tests: quit interrupts an update-gated wait instead of waiting for the next poll |
| `electron/update-gate.test.ts` | Tests for electron/update-gate.ts — the update mutual-exclusion gate that parks local backend spawns while an in-app update is running. The regression this guards (#73822): applyUpdates stops its own backend before comm… |
| `electron/update-gate.ts` | update-gate.ts Pure, dependency-injected gate that parks local backend spawns while an in-app update is running (#73822, #50238). Three independent signals mean "an update owns the local runtime right now": - the on-dis… |
| `electron/update-handoff-ack.test.ts` | Hand-off acknowledgment (R5, A7 rule 6, SPEC 4a.5 / 4b) against REAL processes: the Desktop counts a hand-off as taken only when the marker's line-1 owner is a LIVE incarnation that is not the Desktop and that is correl… |
| `electron/update-handoff-marker.test.ts` | Tests for `update-handoff-marker` |
| `electron/update-handoff-report.test.ts` | Tests: the boot wait reports the result of the run it last parked on, across line-2 heartbeats; a failed run the receipt explains names its stop instead of the bare exit code; a failed run with no receipt keeps the gene… |
| `electron/update-handoff-report.ts` | Report a detached update's result once, where boot passes the update gate. |
| `electron/update-hold-types.ts` | What the blocked boot screen shows while an update hold keeps the local backend stopped (R8 D3). Shared by the main process (update-hold-wiring.ts) and the renderer (src/global.d.ts), so the wire shape has one definitio… |
| `electron/update-hold-wiring.test.ts` | Tests: the boot snapshot carries the update hold to the primary window only; a non-primary window cannot quit from the update-hold screen |
| `electron/update-hold-wiring.ts` | Desktop wiring of an update hold (R8 D3): the marker probe the boot and pool-backend gates share, the blocked boot screen's state, and its three IPC ways out. The judgement itself lives in update-marker-gate.ts; main.ts… |
| `electron/update-marker-async-probe.test.ts` | Review 5411222842: the update gate judges a marker on Electron's main thread every poll while one exists, so its creation-time and process-state probes must never spawn synchronously (`execFileSync` ps / getconf / power… |
| `electron/update-marker-corpus.test.ts` | Shared update-marker corpus consumer (A7 rule 7): `tests/fixtures/update_marker_corpus.json` is authoritative for parsing and judging in every language. Every `judge` case runs through the Desktop's judge with the case'… |
| `electron/update-marker-gate.test.ts` | The update gate's marker probe (R6): a dead/malformed marker is routed through the checkout script's `reclaim` helper — never deleted by Electron — and `held` (a completion still holds the checkout lock) keeps the boot… |
| `electron/update-marker-gate.ts` | The update gate's marker probe (R6, SPEC section 6 "Electron gate"). A marker whose owner and delegate are dead is not necessarily a finished update: an inheriting completion process can still hold the checkout's kernel… |
| `electron/update-marker-judge.ts` | Pure parse + judge of the update marker `HERMES_HOME/.hermes-update-in-progress` (A7 rule 4, contract in `tests/fixtures/update_marker_corpus.json`). The corpus is authoritative: every reader (Python, Rust, bash, PowerS… |
| `electron/update-marker-readonly.test.ts` | A7 rule 3: Electron NEVER deletes or rewrites the update marker. Reading and judging a dead marker — at boot, before a hand-off, before a bridge or staged-updater pre-write — leaves its bytes exactly as they were; recla… |
| `electron/update-marker.test-helpers.ts` | Real-process fixtures for the update-marker suites: sleeping owners, reaped pids, and a claimant child that publishes a marker naming ITSELF (its own pid and kernel creation time), the way a hand-off script does. |
| `electron/update-marker.test.ts` | Tests for electron/update-marker.ts — the update marker (contract C1, v2) that keeps a Desktop reopened mid-update from booting a backend onto the runtime being replaced, and keeps two updaters off one checkout. The liv… |
| `electron/update-marker.ts` | The update marker `HERMES_HOME/.hermes-update-in-progress` (#50238), format v2. One file, shared by every updater (Python `hermes_cli/update_lock.py`, the Rust `UpdateMarkerGuard`, `scripts/desktop-update/{windows.ps1,p… |
| `electron/update-order.test.ts` | Tests: a local handoff waits for remote updates that outlive its exit deadline; an empty selection does nothing and a local-only selection runs once; remote updates still run concurrently with each other |
| `electron/update-order.ts` | A local update hands control to a detached updater that waits for the Desktop window to exit, so every remote update transaction must settle first — otherwise a managed SSH update can outlive the local updater's exit de… |
| `electron/update-prerequisites.test.ts` | Tests: PM update prerequisites use the exact published launcher, not checkout venv files; earlier PM user-bin launchers are accepted only for the reported source tree |
| `electron/update-stop-remedy.test.ts` | Tests: a failed hand-off is explained by the stop its own receipt recorded; a receipt from another run never explains this one; no run identity means no attribution; a record still running has no stop to report |
| `electron/update-stop-remedy.ts` | Name the stop the updater already recorded, instead of a bare "exit 1" dialog. |
| `electron/updater-process.test.ts` | Tests: stagedUpdaterSupportsPrewrittenMarker rejects installers predating the self-adopt fix; stagedUpdaterSupportsPrewrittenMarker accepts installers from the fix onward; stagedUpdaterSupportsPrewrittenMarker treats an… |
| `electron/updater-process.ts` | Exports `resolveVenvDir`, `resolveInstallationLauncher`, `resolveInstallationLauncherAsync`, `userLauncherInstallRoot`, `launcherTargetsInstallation`, `LAUNCHER_ROOT_MISS_TTL_MS` … |
| `electron/updater/app-installer-recovery.test.ts` | Tests: App Installer restores only after teardown begins (${failureAt}); handoff errors retain cleanup failures while still restoring the backend |
| `electron/updater/app-installer-strategy.test.ts` | updater/app-installer-strategy.test.ts — the apply-flow contract: the relaunch registration (marker + detached waiter) completes BEFORE the OS hand-off. Teardown finishes before the descriptor opens. |
| `electron/updater/app-installer.ts` | updater/app-installer.ts — the win32 out-of-store MSIX strategy. The OS App Installer owns the apply. The package was installed from an .appinstaller, which registered the feed URI as the package's update source; |
| `electron/updater/artifact.ts` | Exports `PinnedArtifact`, `verifyPinnedArtifact`, `downloadPinnedArtifact` |
| `electron/updater/channel-artifact-lifetime.test.ts` | Tests: ordinary Windows preparation owns temporary bytes while a resumable download retains its durable file |
| `electron/updater/channel-native.test.ts` | Tests: download verification binds native bytes to the manifest size and digest before signature preparation |
| `electron/updater/channel-native.ts` | Native feeds carry their own hashes; also require the admitted build's hash. |
| `electron/updater/channel-protocol.ts` | The protocol decoder is the sole untrusted-JSON boundary. Unknown inputs and primitive checks belong here; only validated domain objects leave this file. |
| `electron/updater/channel-strategy.ts` | Exports `ChannelRetirementStatus`, `ChannelStrategyDeps`, `ChannelStrategy` |
| `electron/updater/channel-windows-host.ts` | Verify downloaded bytes and native metadata before App Installer can stop the backend. |
| `electron/updater/channel.test.ts` | Tests: channel manifest drops retired bundle keys but rejects unknown names; receiver kind mirrors the identity comparison between retired channel and destination; protected canary accepts bounded Windows revisions with… |
| `electron/updater/channel.ts` | Exports `ChannelTarget`, `ChannelRetirement`, `ChannelResolution`, `ChannelResolverDeps`, `ChannelResolver` |
| `electron/updater/checkout-current-sha.test.ts` | Tests: fills currentSha from the install stamp when the probe omitted it, but never overrides the probe; readStampedCommit returns the stamped commit, or null for absent and malformed stamps |
| `electron/updater/checkout-handoff.test.ts` | Tests: the Windows hand-off wrapper is spawned non-detached so the script shares its hidden console; a failed hand-off spawn keeps the app alive and reports the failure in plain copy; a hand-off whose legacy script neve… |
| `electron/updater/checkout-legacy.test.ts` | Tests: moves a checkout without a source probe to main, but surfaces a broken probe |
| `electron/updater/checkout-ownership.test.ts` | Tests for `checkout-ownership` |
| `electron/updater/checkout-source.test.ts` | Tests: carries each install channel from Python publication checks into the source handoff |
| `electron/updater/checkout-source.ts` | Exports `SourceUpdate`, `SourceUpdateProbe`, `sourceChannelName`, `sourceUpdateEnvironment`, `readSourceUpdate` |
| `electron/updater/checkout.ts` | Checkout update policy and handoff execution. The shell supplies process and UI dependencies. |
| `electron/updater/commit-build.test.ts` | Tests: one-commit artifacts; refuses both checks and apply with no manual-update escape |
| `electron/updater/external.ts` | updater/external.ts — the steward-owned strategy. The stamp declares 'external' when the package owner handles updates without an in-app check or apply action. |
| `electron/updater/feed-config.test.ts` | Tests: reads only the updates feed across equivalent YAML representations; leaves fallback selection available for missing, invalid or non-string config; holds a configured feed base to the update-origin rule and refuse… |
| `electron/updater/feed-config.ts` | The feed base a bundled install downloads its update descriptor from: config.yaml's `updates.desktop_feed_base_url`, else '' (the OS-registered App Installer source / no feed). Config is the one override: a second env s… |
| `electron/updater/index.ts` | updater/index.ts — the desktop update strategy surface. Every install shape updates through a different owner: app-installer out-of-store MSIX on win32 — the OS App Installer owns |
| `electron/updater/mac-client.test.ts` | Tests: macOS client wiring; uses the generated provider by default and forbids implicit installs or downgrades; pins a neutral immutable descriptor instead of interpolating the dynamic name; checks a newer channel head… |
| `electron/updater/mac-client.ts` | Exports `MacClientDeps`, `createChannelMacStrategy`, `createMacStrategy` |
| `electron/updater/mac.test.ts` | Tests: macOS strategy; checks the release, verifies before teardown, and installs once; does not install when the provider reports no newer release; refuses a substituted pinned version or artifact before native signatu… |
| `electron/updater/mac.ts` | Exports `MacStrategyDeps`, `MacStrategy`, `NativeMacUpdater`, `prepareMacInstall` |
| `electron/updater/marker-helper.test-helpers.ts` | A checkout with a REAL fake hand-off script that answers marker-helper ops. |
| `electron/updater/marker-helper.test.ts` | The checkout script's marker helper (A7 rule 3, SPEC section 6): protocol negotiation from the script text, the exact command line, and the one-line verdict — exercised against a REAL fake script process (bash), with th… |
| `electron/updater/marker-helper.ts` | The checkout script's marker helper (A7 rule 3, SPEC section 6): Electron's ONLY way to mutate the update marker. The script holds the `<marker>.lock` kernel lock for the whole read-judge-mutate; Node has no portable ke… |
| `electron/updater/operation.test.ts` | Tests: check and apply share one pending strategy, and a failed initialization can retry; apply ownership precedes async resolution, survives restoration, and retains a successful handoff |
| `electron/updater/operation.ts` | Preserve one native selection across check/apply and one owner through handoff. |
| `electron/updater/packaged-handoff.ts` | Exports `applyPackagedHandoff` |
| `electron/updater/relaunch-isolation.test.ts` | Tests: writes and startup consumption stay in each installation despite a shared Hermes home; cancellation and failed registration remove only their own installation marker |
| `electron/updater/relaunch-waiter-lifecycle.test.ts` | Tests: waiter ownership survives its complete lifecycle (${mode.name}); missing scripts refuse startup before spawning a waiter; every failed start tells the log why it failed; the script log report keeps only this atte… |
| `electron/updater/relaunch-waiter-resource.test.ts` | The sealed payload's repo snapshot has no scripts/, so the relaunch waiter must be shipped by the packaging config at the path main resolves. |
| `electron/updater/relaunch-waiter-spawn.windows-live.test.ts` | Tests for `relaunch-waiter-spawn.windows-live` |
| `electron/updater/relaunch-waiter.ts` | Stage the waiter outside the package and await its old-version snapshot. A failed handshake cancels our child instead of leaving a delayed relaunch. |
| `electron/updater/relaunch-waiter.windows-live.test.ts` | Tests: tags every line of a multi-line script error with its attempt |
| `electron/updater/relaunch.ts` | Electron userData isolates installations that share HERMES_HOME. The marker survives a package swap and records the version that started it. The separate waiter owns automatic relaunch. Cancelling an update stops |
| `electron/updater/state-db-preflight.test.ts` | Tests: the desktop preflight publishes committed WAL rows before its caller can stop the backend; a managed installation runs the snapshot through the installation launcher; an older selected checkout without the snapsh… |
| `electron/updater/state-db-preflight.ts` | Exports `stateDbPreflightTimeoutMs`, `preflightStateDb` |
| `electron/updater/store-client.test.ts` | Tests: the production runner passes modes, full HWND and isolated payload imports; Store runner refuses unusable replies |
| `electron/updater/store-client.ts` | Exports `StoreClientDeps`, `createStoreStrategy` |
| `electron/updater/store.test.ts` | Tests: Microsoft Store update lifecycle; requires automatic relaunch and cancels registration without stopping the backend; downloads before shutdown, owns relaunch before install, and keeps no-update non-destructive; r… |
| `electron/updater/store.ts` | Exports `StoreMode`, `StoreResult`, `StoreStrategyDeps`, `StoreStrategy` |
| `electron/updater/system-proxy-env.test.ts` | Chromium's answer for the system proxy: only github.com goes through it, every other host direct. |
| `electron/updater/system-proxy-env.ts` | The OS proxy for the update's child processes (#123387). git, Python's urllib, npm, uv and electron-builder's downloads all honour HTTPS_PROXY/HTTP_PROXY/NO_PROXY, but none of them reads the macOS or Windows system prox… |
| `electron/updater/update-hosts.ts` | Hosts this install's update reaches beyond the public ones in UPDATE_HOSTS: the checkout's origin (a fork, an internal git mirror) and every package index or npm registry the user configured (#123387 review S2). The sys… |
| `electron/updater/update-metrics.test.ts` | Tests: a hand-off run is reported once as success after the restart, and deleted only once the RPC resolves; a failed run reports only a bucketed stage, never error text |
| `electron/updater/update-metrics.ts` | Shared-metrics report for PACKAGED self-updates (electron-updater, App Installer, Store). Checkout hand-offs run `hermes update`, whose receipt the backend already counts, so they never reach this module. |
| `electron/updater/updater.test.ts` | updater/updater.test.ts — resolution precedence + wire-shape contracts for the strategy layer. Pure DI: no Electron, no payload. |
| `electron/url-filename.ts` | The file name a URL's path ends in, or ``fallback`` when it names none. |
| `electron/user-launcher-install.test.ts` | Tests: a user-bin launcher is ignored when it reports no Hermes source tree |
| `electron/venv-holder-select.test.ts` | Tests: matches the hindsight daemon shim (exe under venv Scripts + hindsight cmdline); Windows path prefix match is ordinal case-insensitive; excludes external venv holders that are not the hindsight daemon; excludes ex… |
| `electron/venv-holder-select.ts` | venv-holder-select.ts Pure Windows venv-holder selection logic (testable without Electron). The pre-update handoff kills Hermes-OWNED venv daemons (the memory plugin's hindsight daemon) so the updater never races a mapp… |
| `electron/vscode-marketplace.test.ts` | Build a minimal zip with stored (uncompressed) entries so the test controls the bytes exactly — exercises the central-directory reader + theme extraction without a deflate dependency. |
| `electron/vscode-marketplace.ts` | VS Code Marketplace color-theme fetcher (main process). Resolves an extension's latest version via the (undocumented but stable) gallery ExtensionQuery API, downloads the `.vsix` (a zip), and extracts the color-theme JS… |
| `electron/wake-indicator-window.ts` | Exports `createWakeIndicatorWindowController` |
| `electron/wake-indicator.test.ts` | Tests: wake indicator window; centers the helper window at the top of the selected display; prefers the internal display and falls back to the primary display; rejects unknown renderer states |
| `electron/wake-indicator.ts` | Exports `WAKE_INDICATOR_WINDOW_WIDTH`, `WAKE_INDICATOR_WINDOW_HEIGHT`, `WAKE_INDICATOR_FADE_MS`, `WAKE_INDICATOR_STATES`, `WakeIndicatorState`, `normalizeWakeIndicatorState` … |
| `electron/watch-storm-breaker.test.ts` | Rate breaker for raw fs.watch handles (#118974): a win32 event storm must close the watcher and fall back to a slow snapshot poll. |
| `electron/watch-storm-breaker.ts` | Rate breaker for raw fs.watch handles (#118974). On Windows, ReadDirectoryChangesW can flood a single fs.watch handle with hundreds of thousands of `rename` events per second (observed: 180k/s on the desktop-plugins dir… |
| `electron/web-text-decoder.test.ts` | Tests: decodeWebText; honours a quoted Big5 charset in the response header; sniffs a Shift-JIS meta charset before decoding the document; sniffs charset from an http-equiv content attribute |
| `electron/web-text-decoder.ts` | Exports `decodeWebText` |
| `electron/window-accelerator.test.ts` | Tests: claims Close Tab on a Windows Ctrl+W keyDown; ignores a Windows Ctrl+W keyUp left over from another app; claims Close Tab on a macOS Cmd+W keyDown; ignores a macOS Cmd+W keyUp |
| `electron/window-accelerator.ts` | Exports `WindowAcceleratorAction`, `FOCUS_GRACE_MS`, `WindowAcceleratorInput`, `windowAcceleratorAction` |
| `electron/window-below.test.ts` | Tests: pickWindowBelow; picks the first overlapping window behind ours in z-order; skips windows behind ours that do not overlap; skips our own other windows (same pid) while walking down |
| `electron/window-below.ts` | window-below.ts — which OS window sits directly underneath a Hermes window. Backs the desktop-gated `read_window_below` tool: the renderer receives `window.read.request` from the gateway, asks main over IPC, and answers |
| `electron/window-chrome-events.test.ts` | Tests: window chrome events |
| `electron/window-chrome-events.ts` | Exports `bindWindowChromeEvents` |
| `electron/window-connection-route.test.ts` | Tests: normalizes an exact registry-scoped connection and profile; keeps legacy/profile-only routes distinct from registry identities; preserves a registry connection when no profile is selected; isolates active routes… |
| `electron/window-connection-route.ts` | Exports `WindowConnectionRoute`, `normalizeWindowConnectionRoute`, `registrySshScopeForWindowRoute`, `appliedPrimaryWindowRoute`, `RegistrySshPoolEntry`, `registrySshPoolScopeByConnectionId` … |
| `electron/window-controls.test.ts` | Tests: performWindowControl; minimizes the sender window; toggles maximize and restore; restores keyboard focus after maximize and restore |
| `electron/window-controls.ts` | Exports `WindowControlAction`, `customWindowControlsEnabled`, `performWindowControl`, `windowControlState`, `registerWindowControlIpc` |
| `electron/window-focus-policy.test.ts` | Invariants for the Windows foreground-steal fix (#83998). `focusWindow()` runs for every ambient window raise (tray restore, notification click, second-instance, dock/taskbar activate). On Windows, `show()` + unconditio… |
| `electron/window-focus-policy.ts` | Foreground-focus policy for the Windows focus-steal bug (#83998). On Windows, `BrowserWindow.show()` and `.focus()` both seize the OS foreground: any native dialog another app is showing (Notepad's save confirmation, a… |
| `electron/window-growth.test.ts` | window-state.json skips a window still at the bounds window sizing gave it, but a user who moves or resizes it afterwards has placed it, and that placement must be saved. |
| `electron/window-growth.ts` | Exports `WindowSizingHost`, `markAppSized`, `isAppSized`, `registerWindowSizing` |
| `electron/window-menu.test.ts` | Tests: macOS registers the native Window menu so AppKit window commands remain available; non-macOS keeps the explicit cross-platform Window menu |
| `electron/window-menu.ts` | TypeScript source: `window-menu` |
| `electron/window-open-policy.test.ts` | @vitest-environment node |
| `electron/window-open-policy.ts` | Window-open policy for every BrowserWindow's webContents. Every external URL the desktop opens on purpose goes through the audited `hermes:openExternal` IPC channel (`openExternalUrl` in main.ts: http/https/ mailto allo… |
| `electron/window-renderer-lifecycle.test.ts` | Tests: pruneReloadTimes drops timestamps outside the rolling window; shouldReloadAfterRendererGone reloads crashed/oom/killed on a live window; shouldReloadAfterRendererGone never reloads expected teardown or unknown re… |
| `electron/window-renderer-lifecycle.ts` | Per-window renderer lifecycle diagnostics + crash recovery (#81290). The desktop app renders one Chromium renderer per window (primary, secondary session windows, full instance windows, and the small helper overlays), b… |
| `electron/window-reveal.test.ts` | Tests: reveals immediately when Electron emits ready-to-show; reveals through the fallback when ready-to-show never arrives; ready-to-show cancels the fallback and settles only once; finalizes an already visible window… |
| `electron/window-reveal.ts` | Exports `WINDOW_REVEAL_FALLBACK_MS`, `createWindowRevealController`, `WindowRevealWindow`, `wireWindowReveal` |
| `electron/window-size-types.ts` | Exports `WindowSizeMode` |
| `electron/window-state.test.ts` | Unit tests for the pure window-state geometry helpers. These cover the logic that protects the user: garbage rejection, off-screen fallback, oversized clamping, and the debounce that collapses mid-drag write storms. |
| `electron/window-state.ts` | Pure geometry helpers for window-state.json — restoring the main window's size, position, and maximized flag across launches. Side-effect-free so the part that actually matters (rejecting garbage + off-screen bounds) is… |
| `electron/windows-backdrop.test.ts` | Tests: Windows backdrop updates; keeps active glass transparent when changing its material; can update only the backing without touching the material; does not write native state for tint-only or opacity-only changes |
| `electron/windows-child-options.test.ts` | #74064: cmd.exe truncates a shell:true command line at the first space in the executable token, so a spaced install path (C:\Users\John Doe\...) must be quoted before it reaches the shell. Direct execution (shell:false)… |
| `electron/windows-child-options.ts` | windows-child-options.ts Shared helper for opting Windows child processes (spawn/execFileSync) into a hidden console. Windows spawns a visible console window per child by default; every desktop-launched helper process (… |
| `electron/windows-hermes-path.test.ts` | Unit tests for the pure Windows `hermes` resolution helpers extracted from main.ts's findOnPath(), handOffWindowsBootstrapRecovery(), and unwrapWindowsVenvHermesCommand(). These pin the two Windows resolution bugs |
| `electron/windows-hermes-path.ts` | windows-hermes-path.ts Pure, dependency-injected pieces of Windows `hermes` resolution pulled out of main.ts's findOnPath(), handOffWindowsBootstrapRecovery(), and unwrapWindowsVenvHermesCommand(). Each of the three fun… |
| `electron/windows-msys-bash-env.test.ts` | Tests: applyWindowsMsysBashEnvDefaults sets both MSYS opt-outs on Windows when unset; applyWindowsMsysBashEnvDefaults preserves an existing MSYS_NO_PATHCONV on Windows; applyWindowsMsysBashEnvDefaults preserves an exist… |
| `electron/windows-msys-bash-env.ts` | Git Bash/MSYS rewrite slash-prefixed native flags (`/FI`) into paths. Set these two opt-outs on Windows unless already present. |
| `electron/windows-remote-inventory.test.ts` | Tests: PATH bin launcher is resolved independently of its absent sibling Python, after the marker gate; held marker stops launcher imports and unrecognized runtime capabilities fail clearly; atomic spawn streams its who… |
| `electron/windows-remote-inventory.ts` | The runtime helper reads through the install's own root and profile predicate; it opens no configs, credentials or sessions and never creates a home or identity. |
| `electron/windows-remote-lifecycle.test.ts` | Tests: Windows spawn holds the update mutex across marker check and helper spawn; Windows spawn publishes the initial ownership record before releasing the mutex; PowerShell transport uses UTF-16LE encoded commands and… |
| `electron/windows-remote-lifecycle.ts` | TypeScript source: `windows-remote-lifecycle` |
| `electron/windows-runtime-command.ts` | The published launcher owns PM activation. A Python guessed beside bin/hermes.exe does not. |
| `electron/windows-sandbox-fallback.test.ts` | Tests: isWindowsSandboxBreakpointExit recognizes signed and unsigned STATUS_BREAKPOINT; alreadyHasNoSandbox honors argv and ELECTRON_DISABLE_SANDBOX; decideWindowsSandboxLaunch stays off outside Windows/Linux and on cle… |
| `electron/windows-sandbox-fallback.ts` | Windows Chromium/Electron sandbox recovery for #38216. On some Windows hosts the GPU/renderer sandboxes die with STATUS_BREAKPOINT (`0x80000003` / exit `-2147483645`). Chromium then FATAL-exits ("GPU process isn't usabl… |
| `electron/windows-ssh-repair.test.ts` | Tests: platform and marker scripts survive outer-shell parsing as one compressed argument without stdin; Windows roster and install id never dispatch POSIX syntax or hide a failed read; Windows inventory rejects malform… |
| `electron/windows-stack-cookie-fallback.test.ts` | Tests: isWindowsStackCookieExit recognizes the issue signed exitCode; isWindowsStackCookieExit recognizes unsigned STATUS_STACK_BUFFER_OVERRUN; isWindowsStackCookieExit rejects STATUS_BREAKPOINT (sandbox owns that code)… |
| `electron/windows-stack-cookie-fallback.ts` | Windows Chromium renderer recovery for #108047. On some local Windows hosts the renderer dies with STATUS_STACK_BUFFER_OVERRUN (`0xC0000409` / signed exit `-1073740791`, FAST_FAIL_STACK_COOKIE_CHECK_FAILURE). After the… |
| `electron/windows-user-env.test.ts` | ── parseRegQueryValue ───────────────────────────────────────────────────── |
| `electron/windows-user-env.ts` | windows-user-env.ts Read a User-scoped environment variable straight from the Windows registry (HKCU\Environment). |
| `electron/workspace-cwd.test.ts` | Tests for electron/workspace-cwd.ts. Run with: node --test electron/workspace-cwd.test.ts |
| `electron/workspace-cwd.ts` | True when `dir` lives inside a packaged app bundle / install tree. |
| `electron/wsl-clipboard-image.test.ts` | Tests: encodePowerShellCommand preserves the clipboard script through UTF-16LE base64; decodeClipboardImageBase64 returns a Buffer for valid PNG base64; decodeClipboardImageBase64 trims surrounding whitespace before dec… |
| `electron/wsl-clipboard-image.ts` | Pull a Windows-host clipboard image from inside WSL2 via PowerShell (WSLg bridges text but not images). Returns PNG bytes or null; exec injectable. |
| `electron/wsl-clipboard-script.ts` | STA is mandatory: System.Windows.Forms.Clipboard throws ThreadStateException off a single-threaded apartment. We emit base64 (not raw bytes) so the PNG survives stdout's text decoding intact, and write with [Console]::O… |
| `electron/wsl-path-bridge-profile.test.ts` | Profile-scoped eligibility for the WSL path bridge (#66447). The single-profile tests in wsl-path-bridge.test.ts cover the *what* (paths pass through unchanged when bridging is disabled) but not the *which profile*. The… |
| `electron/wsl-path-bridge.test.ts` | Tests: parseDefaultDistro reads the first distro from clean utf-8 output; parseDefaultDistro survives UTF-16LE NUL bytes older wsl.exe leaves in (WSL#4607); parseDefaultDistro strips the default-marker and blank lines;… |
| `electron/wsl-path-bridge.ts` | Bridges WSL/POSIX paths into forms the *Windows host* can open, for the case where the desktop UI runs on Windows and the gateway runs inside WSL (remote mode). Only the Windows-side direction lives here: the native fol… |
| `electron/wslg-launch-process.test.ts` | Tests for `wslg-launch-process` |
| `electron/wslg-launch-process.ts` | Spawn the app while leaving this process alive only as its supervisor. |
| `electron/wslg-launch.test.ts` | Tests: WSLg launch arguments; preserves the invocation and restarts only once with native Wayland; respects explicit backends and the existing config-bridged X11 hint; leaves other platforms, missing Wayland displays an… |
| `electron/wslg-launch.ts` | Ozone is selected before application JavaScript. Never appendSwitch here: that leaves the browser on X11 while GPU children receive Wayland. |
| `electron/zoom.test.ts` | Unit tests for the pure zoom helpers: clamping garbage input, the percent <-> zoom-level conversion the settings UI relies on, and the roundtrip stability of the preset percentages. |
| `electron/zoom.ts` | Pure helpers for window zoom. The main process owns webContents.setZoomLevel, so the menu items, the Ctrl/Cmd shortcuts, and the settings UI all funnel through this one clamped scale. Percent is the user-facing unit (10… |
| `eslint.config.mjs` | JavaScript (ES module): `eslint.config` |
| `index.html` | HTML page/template |
| `package.json` | `hermes` — Native desktop shell for Hermes Agent. |
| `packaging/dmg-volume.icns` | macOS icon bundle |
| `packaging/nous-dmg-2b.tiff` | TIFF image asset |
| `playwright.config.ts` | Visual regression testing config. Screenshots are compared against baselines. On `main`, baselines are generated with `--update-snapshots` and cached. On PRs, the cached baselines are restored and screenshots are compar… |
| `pr-assets/profile-launch-menu.png` | PNG image asset |
| `pr-assets/session-source-folders.png` | PNG image asset |
| `preview-demo.html` | HTML page/template |
| `product-identity.cjs` | The desktop product identity — THE single source for every name-shaped value a variant owns. HERMES_DESKTOP_VARIANT=light builds "Hermes Light", the remote-only client; everything else is full "Hermes". |
| `product-identity.d.cts` | TypeScript (CommonJS) |
| `public/apple-touch-icon.png` | PNG image asset |
| `public/ds-assets/filler-bg0.jpg` | JPEG image asset |
| `public/hermes-frames/hermes-frame-0.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-1.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-2.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-3.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-4.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-5.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-6.png` | PNG image asset |
| `public/hermes-frames/hermes-frame-7.png` | PNG image asset |
| `public/hermes-sprite.png` | PNG image asset |
| `public/hermes.png` | PNG image asset |
| `public/nous-girl-dark.png` | PNG image asset |
| `public/nous-girl.png` | PNG image asset |
| `scripts/.gitignore` | Git ignore rules |
| `scripts/after-extract.mjs` | after-extract.mjs — electron-builder afterExtract hook. Stamps the Hermes icon + identity onto the unpacked Windows Electron binary before electron-builder renames it and injects the ASAR integrity resource. WHY afterEx… |
| `scripts/after-extract.test.mjs` | Tests: the exe identity stamp is wired to afterExtract with ASAR integrity kept on; stamps the stock electron.exe on win32 only, before it is renamed to Hermes.exe |
| `scripts/after-pack-digests.test.mjs` | Tests for `after-pack-digests` |
| `scripts/after-pack-toolchain.test.mjs` | This is the Linux afterPack path on a real Linux host, not a fake host flag. macOS adds Developer ID signing; its native release lane owns that proof. |
| `scripts/after-pack.mjs` | after-pack.mjs — electron-builder afterPack hook. Per-platform post-pack work on the unpacked app: payload relocation, nested Chromium + wheel signing on macOS, PE signature sanitizing and batch signing on Windows. The… |
| `scripts/after-pack.test.mjs` | Tests: restores app localizations from the filtered framework without copying locale data; puts the full-resolution .icns back after electron-builder packaged the layered icon; leaves Linux alone and reports a missing f… |
| `scripts/assert-dist-built.mjs` | Build-time guard: refuse to hand a half-built renderer to electron-builder. `npm run pack` / `npm run dist*` are `npm run build && npm run builder`. If the `build` step (tsc -b && vite build) fails but packaging proceeds |
| `scripts/assert-dist-built.test.mjs` | Tests: checkDistBuilt passes when index.html + an assets JS bundle exist; checkDistBuilt fails when the dist directory is absent; checkDistBuilt fails when index.html is missing; checkDistBuilt fails when index.html is… |
| `scripts/assert-root-install.mjs` | Build-time guard: refuse to start a build the installed tree cannot finish. The desktop workspace's dependencies are hoisted to the repo-root `node_modules`, so a root install that only covers *part* of the workspace |
| `scripts/assert-root-install.test.mjs` | Build a throwaway repo shaped like this one: an app workspace whose dependencies are hoisted to the repo root, which is what the guard walks. `manifest` is merged into the app's package.json so tests can declare |
| `scripts/audit-bundle-arch.mjs` | audit-bundle-arch.mjs: prove every native binary inside a packed desktop bundle was built for the target architecture. Why: wrong-arch binaries run FINE on the build runner (Windows-on-ARM and |
| `scripts/audit-bundle-arch.test.mjs` | ─── header builders: the smallest buffers each format needs ─────────────── |
| `scripts/backend-ready-artifact.mjs` | Guard the packaged backend-readiness parser against artifact skew (#60772). The packaged app's `dist/electron-main.mjs` bundle must accept BOTH ready tokens (`HERMES_BACKEND_READY` from a current backend, and the legacy… |
| `scripts/backend-ready-artifact.test.mjs` | Tests: resolves the asar path per platform, including the branded macOS bundle; accepts a packaged bundle whose matcher handles both tokens; rejects the stale dashboard-only matcher — the #60772 artifact skew; fails the… |
| `scripts/batch-sign-binaries.mjs` | batch-sign-binaries.mjs — Authenticode-sign every standalone binary inside the packed Windows app tree (Hermes.exe's sibling DLLs and everything under resources/agent-payload/tools/: node.exe, ffmpeg.exe, chromium, the… |
| `scripts/batch-sign-binaries.test.mjs` | Tests: getBinaries collects .exe and .dll recursively, case-insensitive, sorted; getBinaries skips symlinks and honors the skip predicate (product exe); getBinaries tolerates a missing directory; chunk splits into ~100-… |
| `scripts/before-build.mjs` | Desktop bundles ship precompiled renderer assets. Returning false here tells electron-builder to skip the node_modules collector/install step, which avoids workspace dependency graph explosions and keeps packaging deter… |
| `scripts/before-pack.mjs` | before-pack.mjs — electron-builder beforePack hook. Two responsibilities: 1. Removes any stale unpacked app directory (`appOutDir`) before electron-builder stages the Electron binaries into it. WHY THIS EXISTS ---------… |
| `scripts/before-pack.test.mjs` | Tests: cleanStaleAppOutDir removes a populated unpacked directory; cleanStaleAppOutDir is a no-op when the directory is absent; cleanStaleAppOutDir ignores empty or invalid input; beforePack default export resolves even… |
| `scripts/build-command-screenshot-monitor.mjs` | Exports `buildCommandScreenshotMonitor` |
| `scripts/build-command-screenshot-monitor.test.mjs` | Tests: buildCommandScreenshotMonitor argv; uses the paired sysroot or delegates SDK selection to xcrun; is a no-op off macOS |
| `scripts/build-hud-modifier-monitor.mjs` | Exports `resolveWindowsFrameworkCompiler`, `hudModifierBinaryRelativePath`, `buildHudModifierMonitor` |
| `scripts/build-webapp.mjs` | npm's source-development composition for the browser-hosted renderer. Dependencies are installed into a private workspace, never the checkout: npm ci would prune the native Desktop install (node-pty, Electron), and |
| `scripts/build.mjs` | npm's source-development composition; the compiler consumes prepared inputs. |
| `scripts/build.test.mjs` | Tests: the install stamp is written while the committed assets are still in place |
| `scripts/bundle-electron-main.mjs` | Exports `electronOutputs`, `bundleElectronMain` |
| `scripts/bundle-electron-main.test.mjs` | Tests: the bundled entry relaunches native Wayland sessions with the wayland ozone platform; the bundled entry keeps the WSLg Wayland relaunch; the bundled entry lets desktop.electron_flags choose the ozone platform; th… |
| `scripts/bundle-env.d.mts` | Exports `validateBundleEnvironment`, `applyBundleEnvironment`, `environmentDefaultsBanner` |
| `scripts/bundle-env.mjs` | Defaults must run before bundled modules resolve paths or feature flags. An esbuild define would replace reads, not populate the child process env. Match scripts/releases/bundle_env.py and the channel request decoder. |
| `scripts/bundle-env.test.mjs` | Tests: explicit clears beat inherited homes and prevent Windows registry fallback before spawning; applyBundleEnvironment replays the banner semantics for defaults, runtime overrides and clears; baked defaults precede i… |
| `scripts/check-chunks-parse.mjs` | Parse every emitted renderer chunk as an ES module in ONE node process. assert-dist-built.mjs used to spawn `node --input-type=module --check` once per chunk. With ~1000 emitted chunks the update's desktop build therefo… |
| `scripts/cli-launchers.test.mjs` | Tests: one MSIX extension consumes the launchers declared by the payload; manifest fragments escape every interpolated attribute value |
| `scripts/click-session-helpers.mjs` | click-session-helpers.mjs Shared logic for scripts/click-session.mjs — the interactive CDP helper that clicks a sidebar session by partial title and reads the post-click state. The macOS check-suite flake (#97982): the… |
| `scripts/click-session-helpers.test.mjs` | Tests: buildFindClickExpression scrolls instantly and centered, then clicks; evaluateJsonValue unwraps the nested CDP envelope; evaluateJsonValue returns null on a truncated envelope, not undefined; pollUntil resolves t… |
| `scripts/click-session.mjs` | Click on a session by partial title match. Two flake sources fixed (#97982): a bare scrollIntoView() whose smooth scroll could be dropped under load, and a fixed 3000ms post-click sleep |
| `scripts/commit-bundles.windows.test.mjs` | Tests for `commit-bundles.windows` |
| `scripts/commit-stamp-identity.test.mjs` | Tests: desktop stamp uses the admitted checkout rather than the dispatch SHA |
| `scripts/compiler-cache.d.mts` | Exports `withCompilerCache` |
| `scripts/compiler-cache.mjs` | The React Compiler babel pass is ~85% of a production renderer build (≈13 s over ~770 files), and every source update rebuilt all of it for a one-file change. Its output is a pure function of the module text, its id and… |
| `scripts/compiler-cache.test.mjs` | Tests: a warm build serves the stored output, identical to a fresh compile, without recompiling; a toolchain or NODE_ENV change starts a new generation; a corrupt entry is a miss; closing a build keeps only the entries… |
| `scripts/connector-rehearsal.mjs` | JavaScript (ES module): `connector-rehearsal` |
| `scripts/desktop-update-ui.test.mjs` | Execute the shipped page, including its inline script, rather than matching source strings or testing a second implementation of the progress client. |
| `scripts/dev-no-hmr.mjs` | JavaScript (ES module): `dev-no-hmr` |
| `scripts/diag-code-live.mjs` | Is the tree-split preview path actually active in the running renderer? Checks the served source (what vite compiled) rather than guessing. |
| `scripts/diag-drag-churn.mjs` | Who re-renders the transcript during a sash drag? Standalone probe, not a benchmark: seeds tiles, then drags the sash while recording (a) render attribution and (b) every nanostores atom that notifies |
| `scripts/diag-drag-trace.mjs` | What is the drag actually spending time on? The render counters proved React is no longer the cost (commits 83 -> 12 after the $layoutTree fix) yet drag fps stayed ~3 while p95 halved. That |
| `scripts/diag-jump.mjs` | Wrap the thread scroller's properties and observe pin/scroll/RO events in real time during a submit, then print the timeline. |
| `scripts/diag-key-latency.mjs` | Typing latency, isolated: keystroke -> next paint, with and without an active stream. Distinguishes "input is slow" from "the frame budget is consumed by streaming flushes" — the fix differs completely. |
| `scripts/diag-live-state.mjs` | Quick state probe of the running hgui instance via CDP. |
| `scripts/diag-overlay-ab.mjs` | JavaScript (ES module): `diag-overlay-ab` |
| `scripts/diag-overlay-churn.mjs` | JavaScript (ES module): `diag-overlay-churn` |
| `scripts/diag-overlay-full.mjs` | JavaScript (ES module): `diag-overlay-full` |
| `scripts/diag-overlay-sweep.mjs` | JavaScript (ES module): `diag-overlay-sweep` |
| `scripts/diag-real-loop.mjs` | The real-app perf loop: drive HER hgui instance (real profile, real sessions) through the three interactions that matter — session switch, sidebar drag, composer typing — and report honest single-clock numbers. |
| `scripts/diag-ro-storm.mjs` | How many ResizeObserver callbacks does one sash drag actually fire, and for how many DISTINCT elements? The trace named use-resize-observer.ts at 977ms but not whether that's a few expensive calls or a great many cheap… |
| `scripts/diag-scroll-reset.mjs` | Reproduce + diagnose the "scroll wheel resets position while reading" bug. The complaint (Windows, mouse wheel): scrolling UP through a chat to re-read older content randomly yanks the view to a different position, so y… |
| `scripts/diag-sidebar-dom.mjs` | Dump the sidebar's actual DOM shape so selectors stop being guesses. |
| `scripts/diag-switch-autopsy.mjs` | Session-switch autopsy: click between the two heaviest rows repeatedly, recording per-switch (a) settled ms, (b) React commits, (c) top rendered components — so slow switches name themselves. |
| `scripts/diag-switch-trace.mjs` | What happens during a SLOW session switch? Click a heavy row with tracing on, dump the style/layout/script split plus top callsites. |
| `scripts/dmgbuild-diagnostics.cjs` | JavaScript (CommonJS) |
| `scripts/dmgbuild-diagnostics.test.mjs` | Tests: the resolved dmgbuild uses its paired Python and preserves args, results and live diagnostics; prepared supplier overrides retain the paired-Python diagnostic route; promisified callers retain stdout, stderr and… |
| `scripts/eval.mjs` | Simple eval helper — runs an expression and returns the result.value. node scripts/eval.mjs "document.title" HERMES_DESKTOP_CDP_PORT=9333 node scripts/eval.mjs "document.title" |
| `scripts/gen-msix-manifest.mjs` | Generate the AppxManifest.xml that MsixTarget.writeManifest produces on the win32 CI lane, using the REAL app-builder-lib helpers and the real builder config, so the manifest can be inspected off-Windows — makeappx |
| `scripts/gen-share-codes.ts` | Throwaway generator: deterministic fake star-map graphs → real share codes (runs the actual encoder, so every string round-trips). Run with `npx tsx`. |
| `scripts/i18n-keys.mjs` | Exports `SURFACE`, `flattenKeys`, `renderKeysFile`, `emitDesktopKeys` |
| `scripts/i18n-keys.test.mjs` | Tests: flattenKeys lists every leaf as a sorted dotted path, functions included, arrays as one leaf; the committed locales/_keys.desktop.json matches the English catalog (run |
| `scripts/live-drive.mjs` | Live-drive harness for the REAL hgui instance on :9222. node scripts/live-drive.mjs status — targets, session count, perf-live armed? node scripts/live-drive.mjs fps [seconds] — raw rAF fps over N seconds (default 4) |
| `scripts/local-pack-publish.test.mjs` | Tests: the pack script pins an explicit publish policy |
| `scripts/mac-icon.cjs` | Which macOS icon resource electron-builder packages, decided per build host. `assets/icon.icon` is the Icon Composer package for macOS 26 (the system masks its layers itself, so the border ring follows the real outline). |
| `scripts/mac-icon.test.mjs` | Tests: packages the Icon Composer layers only where actool can compile them; never packages the layered icon from a non-mac host; reads the version out of the actool plist and treats any failure as absent |
| `scripts/mac-sign-cache.mjs` | Reuse Developer ID signatures for loose Mach-O payload files across release builds. codesign embeds the signature (with a secure timestamp) in the file, so signing is not reproducible: the cache stores the signed bytes,… |
| `scripts/mac-sign-cache.test.mjs` | Tests: loose payload binaries are found; nested bundles, the main executable and non-Mach-O are not; an identical input restores the stored signed bytes without signing again; duplicate inputs with the same name are sig… |
| `scripts/mac-sign.mjs` | Exports `createMacSigner` |
| `scripts/mac-sign.test.mjs` | Tests: builder dispatch refreshes real facts after every payload signature and before the outer seal; payload digest refresh rejects corrupt and missing PM facts but skips payload-free builds |
| `scripts/macos-sysroot-native.test.mjs` | Tests for `macos-sysroot-native` |
| `scripts/macos-sysroot.mjs` | Build-time only: resolves the macOS SDK the native helpers compile against. |
| `scripts/macos-sysroot.test.mjs` | Tests: resolves an explicit SDKROOT path or name through xcrun before any developer default; reports a stale SDKROOT and falls back to the toolchain default instead of failing the build; ignores an empty SDKROOT; prefer… |
| `scripts/msix-manifest-roundtrip.test.mjs` | MSIX BUILD_NUMBER round-trip (plan item 3.2): scripts/msix-shared.mjs's appIdentity() derivation must equal the Version= the built manifest ships. The "built manifest" here is the REAL one the win32 lane packs: the repo… |
| `scripts/msix-shared.test.mjs` | msix-shared — native package versions come from the immutable build time. Stable keeps the Store quad; canary uses yy.mmdd.hh.mmss. The git-backed lookup is deterministic here because node:child_process.execFileSync is… |
| `scripts/msix-virtualization.test.mjs` | Hermes shares %LOCALAPPDATA% and HKCU state with the unpackaged CLI/gateway, so every MSIX the repo produces must opt out of write virtualisation and the builder must request the restricted capability that permits it. |
| `scripts/native-quad.test.mjs` | 2026-09-22T00:14:03Z, worked by hand: day-of-year 264 (2026 is not a leap year; Jan 1 is hour 0), so hour-of-year is 264*24 = 6336. The 14th minute holds 14*60+3 = 843 seconds. |
| `scripts/notarize-artifact.mjs` | JavaScript (ES module): `notarize-artifact` |
| `scripts/notarize.mjs` | Exports `runCommand`, `notarize` |
| `scripts/osx-sign-inputs.test.mjs` | Tests: the signing walk stays bounded on a truncated protobuf-like resource |
| `scripts/patch-electron-builder-mac-binary.mjs` | Loaded in the builder child before osx-sign. Keep its walk and classifier, but own each probe through close: isbinaryfile's path API resolves too early. The prebuilder lifecycle also imports this file to validate the su… |
| `scripts/payload-digests.mjs` | Exports `rehashPayloadDigests` |
| `scripts/payload-sign-cache.mjs` | Exports `peContentHash`, `verifySignedPayloads`, `createPayloadSignCache` |
| `scripts/payload-sign-cache.test.mjs` | Tests: input bytes select entries across paths, while policy and executable content stay binding; batch cache publishes only after successful signing and timestamping, and warm hits skip both |
| `scripts/perf/README.md` | Desktop perf harness |
| `scripts/perf/baseline.json` | JSON object with keys `_meta`, `scenarios` |
| `scripts/perf/gateway_attach_bench.py` | Measure the gateway's attach-RPC dispatch, against the real dispatcher. |
| `scripts/perf/image-attach-bench.mjs` | Measures the desktop image-attach pipeline stage by stage on a real image, against the real renderer helpers. No Electron, no LLM — just the transforms an attached image goes through between the paperclip and prompt.sub… |
| `scripts/perf/lib/baseline.mjs` | Baseline + regression gate. This is the capability the old one-off scripts never had: measured numbers are compared against a committed baseline so a PR that regresses streaming/typing/mount cost fails loudly instead of |
| `scripts/perf/lib/cdp.mjs` | The one Chrome DevTools Protocol client for desktop scripts. Before this, every measure-*/profile-* script shipped its own copy-pasted `CDP` class (four subtly different implementations), its own `/json` vs |
| `scripts/perf/lib/launch.mjs` | Connect the harness to a renderer — either an already-running debug instance (`attach`) or a freshly spawned, fully isolated one (`startIsolatedInstance`). The isolated instance is what makes the harness self-contained… |
| `scripts/perf/lib/stats.mjs` | Shared numeric helpers for perf scenarios. Every measure-*/profile-* script used to carry its own copy of these. |
| `scripts/perf/run.mjs` | Desktop perf harness entrypoint. node scripts/perf/run.mjs [scenarios...] [flags] Default (no scenarios): runs the CI suite (stream, keystroke, transcript) |
| `scripts/perf/scenarios/cold-start.mjs` | Cold start — launch → renderer → interactive. Unlike the other scenarios this measures the LAUNCH itself, so it can't run against an already-up instance: the runner spawns a fresh isolated instance per run (requires --s… |
| `scripts/perf/scenarios/first-token.mjs` | Time-to-first-token — Enter → first assistant token painted. The latency an agent app is uniquely judged on, spanning the desktop submit path AND the backend/agent-loop first-token time. Backend tier: fires a REAL promp… |
| `scripts/perf/scenarios/idle-cost.mjs` | What does the app cost while a turn is running but NOTHING is arriving? The user-visible symptom: with a thread spinning, resizing the sidebar or typing in the composer feels slow. That is not streaming cost — the stream |
| `scripts/perf/scenarios/index.mjs` | Scenario registry. Add a scenario module here and it's automatically available to the runner, the default suite (tier 'ci'), and the baseline gate. |
| `scripts/perf/scenarios/keystroke.mjs` | Composer input latency — keystroke → next paint. Subsumes measure-latency, profile-typing, and leak-typing. This is the most-felt latency in a chat app (users type constantly) and nothing measured it against a baseline… |
| `scripts/perf/scenarios/live-window.mjs` | Observe the existing workspace without seeding sessions or changing focus. Run timing separately from --cpuprofile / render counters: attribution costs must not be reported as interaction latency. |
| `scripts/perf/scenarios/multitab.mjs` | Multi-tab working sessions: N session tiles stacked as tabs in the main zone, EVERY tab mounted (keep-alive), all streaming concurrently — the "5 tabs doing PR review" workload. Measures frame pacing + longtasks while |
| `scripts/perf/scenarios/profile-switch.mjs` | Profile-switch latency. Subsumes measure-profile-switch. Backend tier: needs a configured profile in the rail and a live backend. Report-only. node scripts/perf/run.mjs profile-switch --profile <name> |
| `scripts/perf/scenarios/render-churn.mjs` | Render churn during multi-tab streaming: WHAT re-rendered and WHY, and which store published the update. Frame pacing (see `multitab`) tells you the cost; this tells you the cause. |
| `scripts/perf/scenarios/right-pane.mjs` | File-tree + terminal workspace stress. This is the regression scene for the desktop symptom where opening the project tree/terminal made the whole page hitch while chat and PTY output continued. |
| `scripts/perf/scenarios/session-load.mjs` | Visual stability of a session LOAD. Sibling to `submit` (which measures the jump on Enter); this one measures the jump on opening a session — the prepend/settle path, not the append path. |
| `scripts/perf/scenarios/session-switch.mjs` | Session-switch latency. Subsumes profile-session-switch. Backend tier: needs two real stored session ids and a live backend. Report-only. node scripts/perf/run.mjs session-switch --a <sidA> --b <sidB> [--rounds 2] |
| `scripts/perf/scenarios/stream-history.mjs` | Streaming into an ALREADY-LONG transcript. Same measurement as `stream`, but the history is mounted and allowed to settle before the recorders start, so what it captures is the per-delta cost that scales with transcript… |
| `scripts/perf/scenarios/stream.mjs` | Streaming render cost. Subsumes measure-synthetic-stream, profile-synth-stream, profile-long-stream (synthetic) and measure-real-stream / profile-real-stream (via --real). CPU profiling is provided by the runner's --cpu… |
| `scripts/perf/scenarios/submit.mjs` | Submit (Enter) latency + scroll stability. Subsumes measure-submit and measure-jump. Backend tier: fires a REAL prompt, so run it on a throwaway session with a live backend. Report-only (no committed baseline — real |
| `scripts/perf/scenarios/transcript.mjs` | Large-transcript mount cost. New scenario (no prior script measured this): loads N synthetic turns of mixed markdown into $messages and records the mount→paint time plus any longtasks the mount blocks the main thread wi… |
| `scripts/perf/serve.mjs` | Launch a standalone, fully isolated perf instance and leave it running so you can attach the harness (`npm run perf`) or DevTools to it. Ctrl-C tears it down and removes its temp dirs. |
| `scripts/prepare-dmgbuild.mjs` | PM supplies the complete vendor tree, including the diagnostic hook's Python. Source convenience uses the same Python entrypoint as other build helpers. |
| `scripts/prepare-dmgbuild.test.mjs` | Tests: packager selects either same-OS payload architecture but refuses foreign OS; explicit PM supplier is copied with paired Python; missing runtime fails before publication |
| `scripts/prepare-packaging-tools.mjs` | Exports `pinnedPackageRoot`, `packagingTargetArch` |
| `scripts/prepare_dmgbuild.py` | Source-build entrypoint for the independently PM-owned DMG supplier. |
| `scripts/prepared-native-deps.mjs` | Exports `recordNativeInputs`, `nativeInputsComplete`, `readNativeInputs`, `copyNativeInputs`, `copyNativeTree` |
| `scripts/prepared-native-deps.test.mjs` | Tests: beforePack refuses absent native preparation rather than staging from npm; native consumption copies admitted modules and helpers, rejecting changed sources, targets or bytes |
| `scripts/prepared-packaging.mjs` | Exports `preparationRequired`, `fileDigest`, `treeDigest`, `packagingIdentity`, `publishPackagingInputs`, `readPackagingInputs` |
| `scripts/prepared-packaging.test.mjs` | Tests: a failed preparation invalidates an earlier completion claim before loading suppliers; prepared inputs are path-bound and reject changed or missing bytes without repair |
| `scripts/prepared-windows-tools.test.mjs` | Tests: signing validates once per packager, including concurrent file hooks, never process-wide; the per-file Azure signer admits the same prepared selection before constructing its manager; a prepared signing selection… |
| `scripts/probe-command-palette.mjs` | ⌘K open latency, measured in-page (no CDP round-trip in the number). node scripts/probe-command-palette.mjs [--port 9222] [--rounds 8] Reports, per round, the time from the keydown the app actually receives to: |
| `scripts/probe-model-picker.mjs` | Model picker open latency probe: click the composer model pill, time until the dropdown/dialog content paints, repeat. Run with --cpuprofile via the harness runner once promoted; standalone for iteration. |
| `scripts/probe-prepared-native.mjs` | Exports `probePreparedNative` |
| `scripts/probe-prepared-native.test.mjs` | Tests: the native admission child refuses ordinary Node instead of certifying an Electron ABI |
| `scripts/probe-renderer.mjs` | quick probe — read state of the renderer |
| `scripts/probe-thread.mjs` | Probe the cloud shadows thread state — count messages, turn pairs, thread height, composer state |
| `scripts/profile-model-picker.mjs` | CPU-profile one model-picker open. node scripts/profile-model-picker.mjs [--port 9222] |
| `scripts/profile-typing-lag.md` | Profiling renderer typing lag |
| `scripts/reload-renderer.mjs` | Reload the renderer via CDP so it picks up the latest from Vite. |
| `scripts/reload.mjs` | Hard reload the Electron renderer over CDP. Vite-no-HMR mode means edits don't auto-apply — call this after editing source. |
| `scripts/run-electron-builder.mjs` | Source convenience prepares first; --prepared only admits and consumes files. |
| `scripts/run-electron-builder.test.mjs` | Tests: validate-only admits real prepared inputs without launching tools and rejects unsafe arguments; source multiarch prepares isolated native and packaging inputs before each strict invocation; strict builder refuses… |
| `scripts/run-short-session-hang-repro.mjs` | JavaScript (ES module): `run-short-session-hang-repro` |
| `scripts/sanitize-pe-signatures.mjs` | sanitize-pe-signatures.mjs — repair PE certificate tables that point past the end of their own file, before anything tries to sign the tree. Why this exists: python-build-standalone runs `llvm-strip` over every DLL in i… |
| `scripts/sanitize-pe-signatures.test.mjs` | Tests: tree sanitization preserves all bytes except dangling PE ${magic.toString(16)} directories |
| `scripts/set-exe-identity.mjs` | JavaScript (ES module): `set-exe-identity` |
| `scripts/set-exe-identity.test.mjs` | Tests: retries transient rcedit commit failures with bounded backoff; stops retrying after the bounded rcedit retry budget is exhausted; does not retry when the rcedit binary itself cannot be spawned (ENOENT/EACCES) |
| `scripts/side-by-side-launchers.test.mjs` | Tests: the Store bundler rejects nonstable selectors before platform tools or staging; nonstable MSIX CLI aliases each activate their own entrypoint, never the GUI; desktop payload exposes only identity-qualified launch… |
| `scripts/side-by-side.windows.test.mjs` | Native SDK proof, NOT desktop E2E. Run on Windows with desktop dependencies: node apps/desktop/scripts/side-by-side.windows.test.mjs makeappx validates unmodified production manifests in a temporary tree. |
| `scripts/sign-msix.mjs` | electron-builder custom win.sign hook: Azure Trusted Signing for the MSIX package only. Windows install validation checks the package signature (AppxSignature.p7x over AppxBlockMap.xml); inner files are covered by the |
| `scripts/sign-msix.test.mjs` | Tests: shouldSignFile admits only .msix and .msixbundle artifacts; shouldSignFile rejects the Store-submission variant (Partner Center re-signs); shouldSignFile rejects every non-package file the hook is asked to sign;… |
| `scripts/sign-nested-chromium.mjs` | Sign payload Chromium with our Developer ID before osx-sign seals Hermes.app. Google's leftover signatures have no timestamp and no hardened runtime, so Apple's notary rejects them. |
| `scripts/sign-nested-chromium.test.mjs` | Tests: repairFrameworkLinks turns a flattened Foo.framework/Foo into a symlink; signNestedChromium no-ops without an identity; signNestedChromium --deep signs the .app and file-signs loose Mach-O; nested Chromium uses t… |
| `scripts/sign-wheel-zips.mjs` | sign-wheel-zips.mjs — sign Mach-O members inside payload uv-cache wheel zips. uv's cache keeps built wheels as ZIPs beside the extracted archive buckets. electron-osx-sign signs the extracted trees but cannot reach insi… |
| `scripts/sign-wheel-zips.test.mjs` | Tests: signWheelZipMembers; is a no-op without an identity; reports zero for payloads without a uv-cache; signWheelZipMembers machinery |
| `scripts/signing-resources.test.mjs` | Tests for `signing-resources` |
| `scripts/smoke-browser-host-screens.mjs` | The startup screens a working Webapp never shows, titled from the English catalog the renderer renders (the smoke's Chromium runs in English). |
| `scripts/smoke-browser-host-screens.test.mjs` | Runs the page-side expression against a page whose visible text is `innerText`. |
| `scripts/smoke-browser-host-tab.mjs` | The browser smoke checks every viewport in one tab, for the launch link's sake. |
| `scripts/smoke-browser-host-tab.test.mjs` | Tests: browser smoke viewport tab; spends a launch link once and reopens the Webapp it landed on for every later viewport; leaves the previous page before a later viewport starts counting its errors; sizes the tab for e… |
| `scripts/smoke-browser-host.mjs` | JavaScript (ES module): `smoke-browser-host` |
| `scripts/stage-native-deps.mjs` | Exports `removeDirSync`, `classifyNativeBinary`, `stageNodePtyInto`, `stageNodePty`, `activeWindow`, `activeWindowSync` … |
| `scripts/stage-native-deps.test.mjs` | Tests: a missing Linux HUD toolchain leaves no empty package directories; classifyNativeBinary detects ELF as linux; classifyNativeBinary detects Mach-O 64-bit BE as darwin; classifyNativeBinary detects Mach-O 64-bit LE… |
| `scripts/store-package-version.test.mjs` | Tests: Store manifest and envelope agree while executable app semver and sideload sequence remain unchanged; Store calendar ordering survives minute, hour, day and year boundaries and rejects reserved revision; stable c… |
| `scripts/test-desktop.mjs` | JavaScript (ES module): `test-desktop` |
| `scripts/update-relaunch-waiter.ps1` | Wait outside the package until the original app exits and Windows publishes its update. |
| `scripts/utils.mjs` | returns true if the passsed file is being invoked from node, not imported. `node -e` / stdin runs have no argv[1]: nothing is main. |
| `scripts/verify-side-by-side-macos.mjs` | JavaScript (ES module): `verify-side-by-side-macos` |
| `scripts/verify-signed-payloads.ps1` | PowerShell script |
| `scripts/windows-bundle-tools.mjs` | Standalone bundle jobs need the same tools as electron-builder, even when GitHub evicts the build cache before the publishing job starts. |
| `scripts/windows-bundle-tools.test.mjs` | Tests: both bundle modes provision pinned tools rather than search a prefilled cache |
| `scripts/write-build-stamp.mjs` | Write the desktop artifact stamp for source, bundled and Light builds. bundle-electron-main.mjs bakes it into the running code. The packaged sidecar exists only to detect replacement of that artifact by an update. PM's… |
| `scripts/write-build-stamp.test.mjs` | Tests: fromCI reads GITHUB_SHA / GITHUB_REF_NAME; fromLocalGit reads HEAD + branch + dirty status; fromFallback uses the all-zero placeholder commit; resolveStamp prefers CI over local git over fallback |
| `src/AGENTS.md` | apps/desktop/src/ — backend contract, slash palette, Bot Mode |
| `src/api/canonical-ambiguous-owner-reconcile.test.ts` | Tests: a failed owner reconciliation is probed again by the next frame; the frame that triggered a successful reconciliation is delivered to its owner; a prompt declined locally is shown again while the authority still… |
| `src/api/canonical-attach-snapshot.test.ts` | @vitest-environment node |
| `src/api/canonical-bot-relay-deliver.test.ts` | @vitest-environment node |
| `src/api/canonical-clarify-lifecycle.test.ts` | Tests: snapshots expose batch question params without losing already locked answers; a snapshot keeps the owner\ |
| `src/api/canonical-clarify-prompt.test.ts` | @vitest-environment node |
| `src/api/canonical-create-options.test.ts` | @vitest-environment node |
| `src/api/canonical-deadline.test.ts` | Tests: the prerequisite attachment shares the caller deadline and cancellation; a prerequisite attachment resolves the launch profile alias before preparing a mutation; a zero timeout is no deadline on the canonical soc… |
| `src/api/canonical-gateway-socket.test.ts` | Chat and the voice sockets beside it (RT-71, RT-80) share one dial rule: a local gateway's ticket rides only in the gateway subprotocol; a remote route keeps its own query credential. |
| `src/api/canonical-live-pick.test.ts` | Tests: a composer pick is the session-scoped mutate; a busy session answers deferred for the next turn; a fence refusal naming fresh fences is retried once at them, never looped; an older pick refused after a newer pick… |
| `src/api/canonical-model-confirm.test.tsx` | Tests: a guarded canonical picker switch asks; yes applies once with the owner token, no changes nothing; a typed /model on a canonical session answers the same handshake and its resend carries the token once; a confirm… |
| `src/api/canonical-producer-contract.test.ts` | @vitest-environment node |
| `src/api/canonical-profile-route.test.ts` | @vitest-environment node |
| `src/api/canonical-prompt-owner.test.ts` | Tests: retained prompts keep their own profile when imported profiles share a stored session ID; equal stored IDs keep independent revisions, generations, mutation retries and unknown admissions; implicit named-profile… |
| `src/api/canonical-protocol-wire.test.ts` | @vitest-environment node |
| `src/api/canonical-protocol.test.ts` | Tests: sibling routes survive every rebuilt control and compression follow-up; slash compress refreshes its transcript on the owner route and previews stay read-only; corrections preserve intent and fence the observed s… |
| `src/api/canonical-protocol.ts` | Canonical local authority wire adapter. Remote legacy transports keep their existing protocol; unsupported explicit semantics fail before network admission. |
| `src/api/canonical-reasoning-config-set.test.ts` | @vitest-environment node |
| `src/api/canonical-reconnect-replay-owner.test.ts` | @vitest-environment node |
| `src/api/canonical-retained-control-retire.test.ts` | A retained control (reply lost) may be retried only as the session's very next control. Once another verb reached the session, re-issuing the old control must mint a fresh identity: replaying the stale receipt left the… |
| `src/api/canonical-retained-mutation-stale.test.ts` | dokterdok N34: a retained (reply-lost) rename must not be replayed for a LATER equal rename. |
| `src/api/canonical-rewind-lost-reply.test.ts` | A typed /undo or /retry derives its target from a fresh snapshot. After a lost reply the owner has already rewound, so the repeat's snapshot names the turn before: the retained rewind, not a new one at that target, must… |
| `src/api/canonical-rewind-redial-profile.test.ts` | @vitest-environment node |
| `src/api/canonical-session-updated-revision.test.ts` | N91: viewer B learns the CAS revision viewer A's rename committed from the session.updated receipt fanout, and a replayed older receipt never rewinds it. |
| `src/api/canonical-unknown-admission-fence.test.ts` | C20: a delayed generation-1 session.info replay (session.events.since) with `pending: []` must not delete the unknown admission a live generation-2 frame published; a current empty frame still does. |
| `src/api/canonical-watch-window-resume.test.ts` | @vitest-environment node |
| `src/api/client.ts` | Exports `STARTUP_REQUEST_TIMEOUT_MS`, `PROMPT_SUBMIT_REQUEST_TIMEOUT_MS`, `GATEWAY_NOT_CONNECTED_MESSAGE`, `HermesGateway`, `setApiRequestProfile`, `profileScoped` … |
| `src/api/config-route-binding.test.ts` | Tests: config read/write route binding; config record read from A cannot be written to B after primary changes |
| `src/api/config.ts` | Exports `bindConfigReadOrigin`, `peekConfigReadOrigin`, `retainConfigReadOrigin`, `resolveConfigWriteScope`, `getStatus`, `getLogs` … |
| `src/api/cron.ts` | Exports `getCronJobs`, `getCronJob`, `getCronJobRuns`, `getCronDeliveryTargets`, `createCronJob`, `updateCronJob` … |
| `src/api/delegation.ts` | `delegation.backend` values the Settings editors know how to edit (any other plugin backend is a plain string). |
| `src/api/local-models-owner.test.ts` | Tests: pins delayed reads and controls to their captured connection and profile |
| `src/api/local-models.ts` | Exports `LocalModelsScope`, `getLocalModelsStatus`, `getLocalHardware`, `getLocalCatalog`, `installLocalRuntime`, `QuickstartResponse` … |
| `src/api/mcp.ts` | Exports `McpTestResult`, `McpOAuthFlow`, `testMcpServer`, `saveMcpServers`, `mcpOAuthRpc`, `listMcpServers` … |
| `src/api/messaging.ts` | Exports `getMessagingPlatforms`, `MessagingPlatformUpdateResponse`, `updateMessagingPlatform`, `testMessagingPlatform`, `startTelegramOnboarding`, `getTelegramOnboardingStatus` … |
| `src/api/models.ts` | Exports `getGlobalModelInfo`, `getUsageAnalytics`, `getGlobalModelOptions`, `RecommendedDefaultModel`, `getRecommendedDefaultModel`, `setGlobalModel` … |
| `src/api/plugins.test.ts` | desktop.getConnection/getConnectionFor are IPC round-trips into the main process with no timeout of their own (#93454). A wedged main-process round-trip must reject instead of hanging pluginSocket's connect() forever. |
| `src/api/plugins.ts` | Resolve the ACTIVE backend's connection descriptor, (connectionId, profile)-scoped — mirroring how store/profile resolves $connection: a registry agent's descriptor comes from getConnectionFor (its SOURCE connection), e… |
| `src/api/profiles.ts` | Exports `getProfiles`, `createProfile`, `renameProfile`, `deleteProfile`, `getProfileSoul`, `updateProfileSoul` … |
| `src/api/session-http-mutation-identity.test.ts` | Tests: a retained identity on another session survives an acknowledged write |
| `src/api/session-transcript-paging.test.ts` | Tests: session transcript pagination ownership; reads the whole transcript instead of adopting the oldest page from a backend that ignores order; keeps a passive read passive when it falls back to the complete transcrip… |
| `src/api/sessions-mutations.test.ts` | Tests: concurrent equal sidebar edits share the missing-snapshot verdict on older standalone servers; a missing-route response from a write never selects an unfenced retry; uses owner snapshots and preserves the exact d… |
| `src/api/sessions.test.ts` | Tests: deleteSession profile scoping; scopes the DELETE to the owning profile in the URL (object owner); scopes the DELETE to the owning profile in the URL (bare string owner); omits the profile query when no owner is k… |
| `src/api/sessions.ts` | Exports `listSessions`, `SessionSourceFilter`, `listAllProfileSessions`, `SidebarSessionSlice`, `SidebarSessionsResponse`, `SidebarSessionsRequest` … |
| `src/api/skills.ts` | Exports `getSkills`, `getSkillContent`, `setSkillEnabled`, `getStarmapGraph`, `LearningNodeDetail`, `getLearningNode` … |
| `src/api/system.ts` | Exports `AUDIO_SPEAK_MIN_REQUEST_TIMEOUT_MS`, `AUDIO_SPEAK_MAX_REQUEST_TIMEOUT_MS`, `audioSpeakRequestTimeoutMs`, `AUDIO_TRANSCRIBE_MIN_REQUEST_TIMEOUT_MS`, `AUDIO_TRANSCRIBE_MAX_REQUEST_TIMEOUT_MS`, `audioTranscribeReq… |
| `src/api/toolsets.ts` | Exports `getToolsets`, `setToolsetEnabled`, `getToolsetConfig`, `getToolsetModels`, `selectToolsetModel`, `SelectToolsetProviderResponse` … |
| `src/api/webapp-access.test.ts` | Tests: startWebAccess; waits as long as a Webapp build can take |
| `src/api/webapp-access.ts` | Web access: turn on the Webapp the gateway on THIS machine serves, for other devices, behind Nous sign-in. The backend owns every fact here; the pane renders /status and asks for changes. |
| `src/app/agents/index.tsx` | Exports `AgentsView`, `SubagentRow` |
| `src/app/artifacts/artifact-utils.ts` | Exports `ArtifactKind`, `ArtifactFilter`, `ARTIFACT_FILTERS`, `ArtifactRecord`, `ArtifactLoadFailure`, `ArtifactLoadResult` … |
| `src/app/artifacts/index.test.ts` | Tests: collectArtifactsForSession; indexes plain https links from assistant text; strips Markdown code delimiters from discovered link artifacts; stops a URL capture at a closing backtick even when punctuation follows it |
| `src/app/artifacts/index.tsx` | Exports `ArtifactsView` |
| `src/app/artifacts/remote-open.test.tsx` | Tests: keeps discovered file paths and originating session scope intact through remote opening |
| `src/app/capabilities/catalog/catalog-add-button.tsx` | Exports `CatalogAddButton` |
| `src/app/capabilities/catalog/catalog-alert.tsx` | A load failure above the catalog results that keeps what's already shown. |
| `src/app/capabilities/catalog/catalog-arc.ts` | One sweep for every card's hover arc. Each hovered (or focused) card runs the arc rotation on the document timeline with `startTime = 0`, so every card sits at the same angle at the same instant: moving from one card to… |
| `src/app/capabilities/catalog/catalog-bento.ts` | Exports `BENTO_COLUMNS`, `BentoTile`, `packBento` |
| `src/app/capabilities/catalog/catalog-browser.test.tsx` | Tests: defaults to cards, with installed entries marked added; installs from the card + without opening its details; opens the shared detail dialog with source links and the same install target; preserves the parent sea… |
| `src/app/capabilities/catalog/catalog-browser.tsx` | Exports `CatalogBrowser` |
| `src/app/capabilities/catalog/catalog-card.tsx` | Exports `catalogIcon`, `CatalogImage`, `CatalogCardVariant`, `CatalogCard` |
| `src/app/capabilities/catalog/catalog-curation.ts` | Exports `curationOwnsArtwork`, `officialCatalogArtwork`, `curatedFeaturedRank`, `PluginTier`, `PLUGIN_TIER_ORDER`, `pluginTier` |
| `src/app/capabilities/catalog/catalog-data.test.ts` | Tests: public catalog data; preserves every source and distinct install identifier, including same-named skills; keeps catalog identity separate from the source-qualified skill install target; keeps each plugin tier, pi… |
| `src/app/capabilities/catalog/catalog-data.ts` | Exports `CatalogKind`, `CatalogEntry`, `catalogImageUrl`, `catalogLabel`, `parseCatalog`, `fetchCatalog` … |
| `src/app/capabilities/catalog/catalog-detail-dialog.tsx` | Exports `CatalogDetailDialog` |
| `src/app/capabilities/catalog/catalog-detail.tsx` | Exports `CatalogDetail` |
| `src/app/capabilities/catalog/catalog-developer.tsx` | One banner for every catalog. The wing, copy and docs links are shared; the page supplies its own management actions. |
| `src/app/capabilities/catalog/catalog-discovery.css` | Figma Frame 330's geometry, with the existing desktop card and theme surfaces. |
| `src/app/capabilities/catalog/catalog-discovery.test.tsx` | Tests: multi-category discovery; gives every picked category its own shelf, small ones included, with no tier shelves; keeps the default page folding small categories and splitting tiers; featured slider |
| `src/app/capabilities/catalog/catalog-discovery.tsx` | Fewest cards a category needs for its own shelf; smaller ones share "More to explore". |
| `src/app/capabilities/catalog/catalog-download.test.ts` | @vitest-environment node |
| `src/app/capabilities/catalog/catalog-featured-slider.tsx` | How long a slide holds before the hero advances on its own. |
| `src/app/capabilities/catalog/catalog-filter-bar.test.tsx` | Tests: tier chips; collapses to All when the last unselected tier is picked; toggles a tier normally while others stay unselected |
| `src/app/capabilities/catalog/catalog-filter-bar.tsx` | Exports `CatalogFilterBar` |
| `src/app/capabilities/catalog/catalog-filters.tsx` | Exports `FacetRow`, `CatalogFilters` |
| `src/app/capabilities/catalog/catalog-list-row.tsx` | Exports `CatalogListRow` |
| `src/app/capabilities/catalog/catalog-metadata.tsx` | Trust tiers read at a glance (same tones as the installed-plugin pill); the rest stay muted. |
| `src/app/capabilities/catalog/catalog-pointer.ts` | Off for now: without it every card rests at its theme's gradient anchor. |
| `src/app/capabilities/catalog/catalog-query.test.ts` | Tests: plugin tier facet; lists the tiers present in trust order and folds installed-only values in; filters by the normalized tier; keeps skills on their raw registry source |
| `src/app/capabilities/catalog/catalog-query.ts` | Exports `CatalogSort`, `CatalogFacets`, `EMPTY_FACETS`, `facetSource`, `catalogSources`, `catalogCategories` … |
| `src/app/capabilities/catalog/catalog-switch.tsx` | Visible action copy stays attached to the actual controlled switch. Both labels share one grid cell so the control never shifts when it flips. |
| `src/app/capabilities/catalog/catalog.css` | Registered so the gradient can glide instead of jump. Written per card by `trackCatalogPointer`: x/y is the pointer clamped to the card, near is 0–1. |
| `src/app/capabilities/catalog/skill-catalog.tsx` | Exports `SkillCatalog` |
| `src/app/capabilities/catalog/store.ts` | One browsing layout across Skills and Plugins; Installed keeps its own list. |
| `src/app/capabilities/catalog/update-skills-button.tsx` | Exports `UpdateSkillsButton` |
| `src/app/capabilities/catalog/use-catalog-filters.ts` | Exports `useCatalogFilters` |
| `src/app/capabilities/connectors/accounts-section.test.tsx` | Tests: AccountsSection rename; sends the account id and the new name, and shows the new name before the answer; restores the old name and says why when the gateway refuses the name; a slower refusal of an older rename d… |
| `src/app/capabilities/connectors/accounts-section.tsx` | Exports `AccountEdit`, `AccountsSectionProps`, `AccountsSection` |
| `src/app/capabilities/connectors/add-dialog.tsx` | Exports `AddServerDialogProps`, `AddServerDialog` |
| `src/app/capabilities/connectors/add-server-draft.ts` | Exports `AddServerAuth`, `AddServerTransport`, `DraftValue`, `DraftPair`, `AddServerDraft`, `nextRowId` … |
| `src/app/capabilities/connectors/add-server-form.tsx` | Exports `AddServerFormProps`, `AddServerForm` |
| `src/app/capabilities/connectors/catalog-mark.tsx` | Exports `CatalogMark` |
| `src/app/capabilities/connectors/category-picker.tsx` | Exports `CategoryPickerProps`, `CategoryPicker` |
| `src/app/capabilities/connectors/connect-element.test.tsx` | Tests: ConnectElement Try again; stays disabled while its start is in flight, so two clicks cannot mint two sign-ins |
| `src/app/capabilities/connectors/connect-element.tsx` | Exports `ConnectElementProps`, `ConnectElement` |
| `src/app/capabilities/connectors/connector-dialog.tsx` | Exports `ConnectorDialogProps`, `ConnectorDialog` |
| `src/app/capabilities/connectors/connector-kind.ts` | Exports `connectorKindWord`, `showsCatalogMark` |
| `src/app/capabilities/connectors/connector-row-card.tsx` | Exports `ConnectorRowCardProps`, `ConnectorRowCard` |
| `src/app/capabilities/connectors/connectors-directory.tsx` | Exports `ConnectorsDirectoryProps`, `ConnectorsDirectory` |
| `src/app/capabilities/connectors/connectors-tab.tsx` | Exports `ConnectorsTabProps`, `ConnectorsTab`, `useYieldToSignIn` |
| `src/app/capabilities/connectors/data/account-operations.test.ts` | Tests: accountOperationFor; answers only with an operation started in the same profile scope; treats a bare profile and the same profile pinned to the active connection as one scope; retryableAccount |
| `src/app/capabilities/connectors/data/account-operations.ts` | Exports `AccountOperationRequest`, `AccountOperation`, `abandonConnect`, `accountOperationFor`, `retryable`, `retryableAccount` … |
| `src/app/capabilities/connectors/data/alias.ts` | The gateway's account-name format (`ConnectorAlias` in the connector contracts). |
| `src/app/capabilities/connectors/data/connect-address.test.ts` | Tests: reconnect addresses the account the user picked; names a named account by its id, so an unconfirmed rename cannot point the repair at another account; names an unnamed account by its id, the only address it has;… |
| `src/app/capabilities/connectors/data/deep-link.test.ts` | @vitest-environment jsdom |
| `src/app/capabilities/connectors/data/deep-link.ts` | Exports `accountRenameRoute`, `resumeAccountConnect`, `linkedScope`, `claimRouteLink`, `resetRouteLinksForTests` |
| `src/app/capabilities/connectors/data/hosted-actions.ts` | Exports `HostedActions`, `HostedActionOptions`, `useHostedActions` |
| `src/app/capabilities/connectors/data/join.test.ts` | Tests: joinHostedConnectors with several accounts; keeps one row per account, the active one first, then the newest; names the summary by the account alias, falling back to the vendor label; folds a retired account out… |
| `src/app/capabilities/connectors/data/join.ts` | Exports `ConnectorPolicyTagRules`, `ConnectorPolicyRules`, `ConnectorPolicyView`, `EMPTY_POLICY`, `readPolicy`, `memberEnables` … |
| `src/app/capabilities/connectors/data/keys.ts` | Exports `ConnectorRead`, `CONNECTORS_QUERY_ROOT`, `CONNECTOR_LIFETIMES`, `CONNECTOR_GC_TIME`, `connectorsListQueryKey`, `connectorsCatalogQueryKey` … |
| `src/app/capabilities/connectors/data/mutations.ts` | Exports `WriteOutcome`, `ConnectorToolsSaver`, `useConnectorToolsSave`, `ConnectorSwitch`, `useConnectorSwitch`, `AccountDisconnect` … |
| `src/app/capabilities/connectors/data/persist.ts` | Exports `PersistedRead`, `QuerySeed`, `seedOptions`, `startConnectorPersistence`, `storeLocalServers`, `seedLocalServers` … |
| `src/app/capabilities/connectors/data/portal.ts` | Exports `openConnectorsAdmin` |
| `src/app/capabilities/connectors/data/prefetch.test.ts` | Tests: prefetchConnectorTools; reads the tool list only for a card whose hosted account is connected |
| `src/app/capabilities/connectors/data/prefetch.ts` | Exports `hasConnectedTools`, `prefetchConnectorTools`, `usePrefetchConnectedTools` |
| `src/app/capabilities/connectors/data/queries-rules.test.tsx` | Tests: connector rules on the Connectors page; are not asked for while the list is empty (no identity yet); are asked for once the gateway lists apps; are asked for once an identity appears outside the page (an agent co… |
| `src/app/capabilities/connectors/data/queries.ts` | Exports `HostedConnectorsView`, `useHostedConnectors`, `usePluginServers`, `connectorToolsQueryOptions`, `ConnectorToolsView`, `useConnectorTools` |
| `src/app/capabilities/connectors/data/rpc.ts` | Exports `ConnectorRpcError`, `asConnectorError`, `isConnectorReason`, `listConnectors`, `connectorCatalog`, `connectorAccounts` … |
| `src/app/capabilities/connectors/derive-page.ts` | Exports `groupIdOf`, `cardMatchesQuery`, `showsAttentionFirst`, `derivePage` |
| `src/app/capabilities/connectors/derive-tools.ts` | Exports `UNCATEGORISED`, `TINY_CONNECTOR_MAX`, `EMPTY_TOOLS_FILTER`, `isTinyConnector`, `toolDisplayName`, `categoryLabel` … |
| `src/app/capabilities/connectors/derive.ts` | Exports `EMPTY_CONNECTORS_FILTER`, `hostedWay`, `localWay`, `bundledWay`, `bothWaysOn`, `hostedStateWord` … |
| `src/app/capabilities/connectors/dialog-menu.tsx` | Exports `ConnectorDialogMenuProps`, `ConnectorDialogMenu` |
| `src/app/capabilities/connectors/disconnect-confirm.tsx` | A remove scoped to one account, or the app-level disconnect of the account its summary speaks for. |
| `src/app/capabilities/connectors/hint-vocabulary.ts` | Exports `VocabularyTone`, `VocabularyKey`, `VocabularyEntry`, `VocabularyTag`, `VocabularyCopy`, `VocabularyStrings` … |
| `src/app/capabilities/connectors/hosted-dialog.tsx` | Exports `HostedConnectorDialogProps`, `PendingRename`, `renameLinkTarget`, `HostedAccountActions`, `HostedConnectorDialog` |
| `src/app/capabilities/connectors/hosted-notice.test.tsx` | Tests: the Connectors line for a guest; offers a Sign in that starts the sign-in |
| `src/app/capabilities/connectors/hosted-notice.tsx` | Exports `HostedNotice` |
| `src/app/capabilities/connectors/local-dialog.tsx` | Exports `LocalConnectorDialogProps`, `LocalConnectorDialog`, `localCost` |
| `src/app/capabilities/connectors/local-server-control.tsx` | Exports `InstallField`, `LocalInstall` |
| `src/app/capabilities/connectors/local-slots.tsx` | Exports `LocalAdvancedProps`, `LocalAdvanced`, `RemoveServerConfirmProps`, `RemoveServerConfirm` |
| `src/app/capabilities/connectors/plugin-tools-panel.tsx` | Exports `PluginToolsPanelProps`, `PluginToolsPanel` |
| `src/app/capabilities/connectors/tool-row.tsx` | Exports `TOOL_ROW_HEIGHT`, `ToolRowProps`, `ToolRow` |
| `src/app/capabilities/connectors/tools-filter-bar.tsx` | Exports `ToolsFilterBarProps`, `ToolsFilterBar` |
| `src/app/capabilities/connectors/tools-list.tsx` | Exports `ToolsListProps`, `ToolsList` |
| `src/app/capabilities/connectors/tools-panel.tsx` | Exports `HostedToolsPanelProps`, `HostedToolsPanel`, `LocalToolsPanelProps`, `LocalToolsPanel`, `orgDisabledCount` |
| `src/app/capabilities/connectors/tools-status.tsx` | Exports `ToolsWash`, `ToolsStatusAction`, `ToolsStatusPhase`, `isToolsStatusPhase`, `ToolsStatus` |
| `src/app/capabilities/connectors/tools-summary.tsx` | Exports `openToolsList`, `resetOpenedTools`, `useShowAllTools`, `ToolsSummaryProps`, `ToolsSummary` |
| `src/app/capabilities/connectors/types.ts` | Exports `ConnectorResidency`, `LocalServerStatus`, `AccountRow`, `HostedConnectorInput`, `LocalServerInput`, `ConnectorAuthType` … |
| `src/app/capabilities/connectors/use-tools-editor.ts` | Exports `SaveResult`, `SaveOptions`, `UseToolsEditorOptions`, `ToolsEditor`, `useToolsEditor` |
| `src/app/capabilities/connectors/ways-section.tsx` | Exports `WayChoice`, `wayInUse`, `WaysSectionProps`, `WaysSection` |
| `src/app/capabilities/connectors/yield-to-sign-in.test.tsx` | Tests: an open app window and the sign-in; holds the offer back while open, and closes when a sign-in starts |
| `src/app/capabilities/index.test.tsx` | @vitest-environment jsdom |
| `src/app/capabilities/index.tsx` | Skills Hub browsing lives inside the Skills tab. Legacy `?tab=hub` links fall back to 'skills' via useRouteEnumParam. |
| `src/app/capabilities/mcp/install-catalog-entry.ts` | Exports `installBundledEntry` |
| `src/app/capabilities/mcp/mcp-doc.ts` | oxlint-disable-next-line anti-slop/no-shape-in-symbol-names -- `isServerShape` is main's exported name; it is bound to a domain name here instead of renaming the export. |
| `src/app/capabilities/mcp/mcp-editor.tsx` | Exports `McpJsonEditorProps`, `McpJsonEditor`, `McpLogPaneProps`, `McpLogPane`, `McpEditorPane` |
| `src/app/capabilities/mcp/mcp-logs.test.ts` | Tests: filterStdioSections; splits mcp-stderr.log by server for stamped and older banner lines |
| `src/app/capabilities/mcp/mcp-logs.tsx` | Exports `LOG_POLL_MS`, `filterStdioSections`, `McpLogSource`, `useMcpLogLines` |
| `src/app/capabilities/mcp/mcp-status.ts` | Exports `MCP_CATALOG_KEY`, `Probe`, `ServerStatus`, `okProbe`, `ServerCost`, `MCP_USAGE_TTL_MS` … |
| `src/app/capabilities/mcp/use-mcp-draft.ts` | Exports `McpDraft`, `UseMcpDraftOptions`, `useMcpDraft` |
| `src/app/capabilities/mcp/use-mcp-probes.ts` | Exports `McpProbes`, `UseMcpProbesOptions`, `useMcpProbes` |
| `src/app/capabilities/mcp/use-mcp-servers.ts` | Exports `McpServersController`, `UseMcpServersOptions`, `useMcpServers` |
| `src/app/capabilities/plugins/plugin-folder-access.test.tsx` | Tests: PluginFolderAccess; shows each granted folder and revokes it for that plugin; a failed read says so and can be retried, instead of looking like no access |
| `src/app/capabilities/plugins/plugin-folder-access.tsx` | Exports `PluginFolderAccess` |
| `src/app/capabilities/plugins/plugin-packages.test.ts` | Tests: mergePluginPackages; shows a unified package as ONE row with both halves, never two rows; pairs a desktop half with an agent row whose folder differs from its manifest name; a desktop half whose agent half is abs… |
| `src/app/capabilities/plugins/plugin-packages.ts` | One row per PACKAGE on the Plugins page. A package may have a desktop half (loaded into this app, same for every profile), an agent half (installed in the SELECTED profile's backend), or both — a unified package whose f… |
| `src/app/capabilities/plugins/plugin-page-access.test.tsx` | @vitest-environment jsdom |
| `src/app/capabilities/plugins/plugin-page-access.tsx` | Exports `PluginPageAccess` |
| `src/app/capabilities/plugins/plugin-settings-form.test.tsx` | Tests: PluginSettingsForm (#46600, #87934); renders one control per schema type from the table, secrets masked with no value echoed; submits only what changed, coerced to wire types, secrets routed by env name; clears s… |
| `src/app/capabilities/plugins/plugin-settings-form.tsx` | A plugin manifest's `config_schema` rendered as a form. Every non-secret value is edited as TEXT (the draft) and coerced to its wire type on save, so a half-typed number never fights the input; secrets are drafted separ… |
| `src/app/capabilities/plugins/plugin-update.test.ts` | Tests: runPluginUpdate scan override; shows a caution finding, and only ; cancel leaves the plugin alone, and a dangerous verdict never offers the override |
| `src/app/capabilities/plugins/plugin-update.ts` | Exports `scanFindingLines`, `runPluginUpdate` |
| `src/app/capabilities/plugins/plugins-page-header.test.tsx` | @vitest-environment jsdom |
| `src/app/capabilities/plugins/plugins-tab.test.tsx` | Tests: PluginsTab; opens a non-first installed deep-link target from Browse and keeps that selection after consuming the link; renders declared server pills and the unavailable sentence under the description; hides bund… |
| `src/app/capabilities/plugins/plugins-tab.tsx` | Exports `pluginElementId`, `PluginActions`, `PluginsTab` |
| `src/app/capabilities/primitives.tsx` | The chrome the Skills and Tools tabs share: one inspector header, one empty state and one sort control, so switching between them never jumps. Shared inspector header — mirrors Messaging's PlatformDetail so Skills and |
| `src/app/capabilities/scope-selector.tsx` | Exports `CapabilityScope`, `useCapabilityScope`, `CapabilityScopeSelector` |
| `src/app/capabilities/skills/frontmatter.test.ts` | Tests: parseFrontmatter; splits the leading YAML block from the body; keeps a nested block with its key, de-indented one level; returns the whole content as body when there is no frontmatter |
| `src/app/capabilities/skills/frontmatter.ts` | Frontmatter parse for display: the YAML block between the leading `---` fences, flattened to top-level `key: value` rows (nested blocks render as their raw indented text). Display-only — never fed back to the backend. |
| `src/app/capabilities/skills/official-skill-detail.tsx` | Detail pane for a not-yet-installed catalog skill. |
| `src/app/capabilities/skills/skill-detail.tsx` | Exports `SkillDetail` |
| `src/app/capabilities/skills/skill-provenance.test.ts` | #108032: externally mounted skills get an 'external' provenance tier — origin labeling without losing in-place edit rights (commit 8c8fc6c1ec / PR #17512). |
| `src/app/capabilities/skills/skill-provenance.ts` | #108032: an external mount is not a managed hub/bundled source — it is the user's own directory pointed at via skills.external_dirs. Origin only, never mutability: external skills stay editable in place (a refusal would… |
| `src/app/capabilities/skills/skills-data.ts` | Skills live in the RQ cache so switching tabs/pages paints the cached list instantly (no reload flash) and mount only fires a deduped background refetch. A profile swap globally invalidates (see store/profile), so this |
| `src/app/capabilities/skills/skills-tab.tsx` | Exports `SkillsTab` |
| `src/app/capabilities/toolsets/tool-calls.ts` | Per-tool call counts come from a 365-day message scan — heavy, and purely cosmetic (Toolsets usage badges). Cache the result module-wide with a TTL so bouncing between tabs/pages doesn't re-run the scan every time. Keye… |
| `src/app/capabilities/toolsets/toolset-detail.tsx` | Exports `ToolsetDetail` |
| `src/app/capabilities/toolsets/toolsets-data.ts` | Toolsets live in the RQ cache so switching tabs/pages paints the cached list instantly (no reload flash) and mount only fires a deduped background refetch. A profile swap globally invalidates (see store/profile), so this |
| `src/app/capabilities/toolsets/toolsets-tab.tsx` | Exports `ToolsetsTab` |
| `src/app/capabilities/ui/capability-search.tsx` | The one search field every Capabilities tab uses: the boxed SearchField with the tab's name as a scope badge and the tab's own actions (add, view toggle, …) at the end. Callers own the column it sits in and the query. |
| `src/app/capabilities/ui/catalog-surface.tsx` | Exports `CatalogSurfaceItem`, `CatalogSurfaceSection`, `CatalogSurface` |
| `src/app/capabilities/ui/page.css` | The one content column every Capabilities tab sits in: search, filters, sections and directory rows all share these edges. |
| `src/app/chat/browser-popout-handoff.test.tsx` | The consent dialog has its own test file and needs a QueryClientProvider; this test exercises the pop-out content handoff, not the prompt. |
| `src/app/chat/browser-popout-shell.tsx` | Dedicated shell for `?win=browser`: the in-app Browser, full-window, no session sidebar or layout tree. Same webview + address bar the docked tab uses — just in its own OS window. |
| `src/app/chat/built-in-tour.ts` | The app's own tour — what `gui_tour` runs when it starts with no steps. The app owns the stops (stable `data-tour` handles) and their copy, so a look around is one tool call. Before this, the model scanned `targets` and… |
| `src/app/chat/chat-drop-overlay.tsx` | Full-bleed affordance shown while files or a session are dragged over the chat area. Always `pointer-events-none` so the drop lands on the real element underneath and the drop-zone handler claims it — the overlay is pur… |
| `src/app/chat/chat-surface-state.ts` | Exports `useShowChatBar`, `dropOverlayKind` |
| `src/app/chat/chat-swap-overlay.test.tsx` | The overlay used to run its own 80ms setInterval + setState braille ticker — the same mechanism class (per-tick DOM mutation scheduling a style recalc) that GlyphSpinner was rewritten to remove. It now renders GlyphSpin… |
| `src/app/chat/chat-swap-overlay.tsx` | Shown over the conversation while the live gateway swaps to another profile's backend (lazily spawned). Keeps the last profile name through the fade-out so the label doesn't blank. Purely visual — pointer-events-none. |
| `src/app/chat/close-tab.test.ts` | Tests: closeActiveTab; leaves ⌘W to the zone rungs even with previews open; closeWorkspaceTab; shifts the next stacked session into main |
| `src/app/chat/close-tab.ts` | Close the MAIN tab. The workspace pane itself can't leave the tree, so "closing" it means emptying it, and what fills the hole depends on what's stacked beside it: - session tabs stacked with it → the next one shifts IN… |
| `src/app/chat/composer/at-folder-navigation.test.tsx` | Folder navigation in the `@` popover, driven through the REAL hook against a real contentEditable. Tab and Enter used to be the same branch, so picking a folder always committed a chip and closed the menu — there was no… |
| `src/app/chat/composer/attachments.test.tsx` | Tests: AttachmentList; does not crash when attachments array contains undefined entries; renders the thumbnail in the pill but opens the full-resolution image in the lightbox; loads a path-backed full image only when op… |
| `src/app/chat/composer/attachments.tsx` | Exports `AttachmentList` |
| `src/app/chat/composer/busy-submit-state.ts` | Exports `ComposerBusyAction`, `BusySubmitInputs`, `BusySubmitState`, `deriveBusySubmitState` |
| `src/app/chat/composer/chat-bar-parts.tsx` | Radial dock-target glow shown while a popped-out composer is dragged. Intensity tracks how close the composer is to the dock (1 = peak). |
| `src/app/chat/composer/completion-drawer.tsx` | A standalone glassy panel floating just off the composer edge, inset from the left. Skin is the shared composerPanelCard (also used by the attach menu). |
| `src/app/chat/composer/composer-store-writer.test.ts` | Tests: composer store writer — keystrokes reach the assistant-ui store without a write per character; writes an edge flip at once and coalesces the rest of a burst into one trailing write; never lets a pending keystroke… |
| `src/app/chat/composer/composer-store-writer.ts` | Every fact the app derives from the assistant-ui composer text through `useAuiState` (send-button state, the `?` help sigil, steer vs slash, the empty placeholder, hard-newline layout). A keystroke that leaves this sign… |
| `src/app/chat/composer/composer-text-guard.test.tsx` | Regression for #49903: on desktop v0.17.0 the composer threw an uncaught `Error: Composer is not available` at startup and the input went unresponsive. @assistant-ui/core's composer mutators (setText/send/…) throw |
| `src/app/chat/composer/composer-utils-width.test.ts` | Tests: composerInputWidthClass; fills the unstacked 1fr grid track instead of the 8rem inline floor; keeps the stacked editor full-width |
| `src/app/chat/composer/composer-utils.test.ts` | Tests: shouldDisableComposerInput; fails closed when connection atoms disagree about an open gateway; slashArgStage; is true only once the query is past the command name |
| `src/app/chat/composer/composer-utils.ts` | Exports `COMPOSER_STACK_BREAKPOINT_PX`, `COMPOSER_COMPACT_PILL_PX`, `COMPOSER_FOLD_VOICE_PX`, `COMPOSER_MINIMAL_PX`, `COMPOSER_SINGLE_LINE_MAX_PX`, `COMPOSER_FADE_BACKGROUND` … |
| `src/app/chat/composer/context-menu.tsx` | Exports `ContextMenu`, `ContextMenuItem` |
| `src/app/chat/composer/contrib.test.ts` | Tests: runComposerMiddleware; passes the draft through untouched when nothing is registered; chains rewrites in registry order; cancels the send when a handler returns null |
| `src/app/chat/composer/contrib.ts` | Composer contribution surface — every seam of the composer is hook-into-able through the SAME registry schema as every other surface (statusbar, titlebar, panes, layouts): render areas (`render`): composer.top — banner… |
| `src/app/chat/composer/control-classes.ts` | Shared class names for the composer's control row, in a module of their own so both the row (`controls.tsx`) and the menus it renders can wear them without importing each other in a cycle. |
| `src/app/chat/composer/controls-row-layout.test.tsx` | Tests: keeps the minimal controls row on one line, packed from the start, in native Desktop; packs the minimal controls row to the end and lets it wrap in browser-hosted Desktop |
| `src/app/chat/composer/controls.test.tsx` | Tests: HUD mode; keeps the mic inline, fans the toggles on hover, and offers no exit in the docked composer; folds them into one menu and offers the way out in the HUD; reports a live voice state on the collapsed trigger |
| `src/app/chat/composer/controls.tsx` | Re-exported: `context-menu.tsx` and other row neighbours have always reached for these here, and the row is where they read as belonging. |
| `src/app/chat/composer/directive-actions.test.tsx` | Tests: ComposerDirectiveActions; offers an action for a hovered actionable chip; opens a url in the in-app browser rather than navigating the app; sends the pill to the system browser on the platform open-elsewhere modi… |
| `src/app/chat/composer/directive-actions.tsx` | Hover actions for directive chips in a composer. A directive chip (` |
| `src/app/chat/composer/directive-label.test.ts` | A row exactly as tui_gateway's complete.path emits it, run through the real classify() the popover uses. |
| `src/app/chat/composer/directive-scope.test.ts` | Tests: directive scope is a browse mode, not text to maintain; Tab-descend carries the scope down instead of dropping to a bare path; Backspace climbs the path, then drops the whole scope; leaves Backspace alone when th… |
| `src/app/chat/composer/discard-lost-prompt.test.ts` | Tests: Discard uses the queue owner socket and its lost generation, including an unbound runtime; Discard refuses unresolved or unavailable owners instead of falling back to the ambient socket |
| `src/app/chat/composer/discard-lost-prompt.ts` | Exports `discardLostPrompt`, `cancelQueuedPrompt`, `steerQueuedPrompt`, `replaceQueuedPrompt` |
| `src/app/chat/composer/drop-affordance.ts` | Exports `COMPOSER_DROP_FADE_CLASS`, `COMPOSER_DROP_ACTIVE_CLASS` |
| `src/app/chat/composer/empty-composer.test.ts` | Tests: an emptied composer reads as empty; keeps the placeholder <br> so the contenteditable holds its height; reads that editor as empty, not as a newline; reads a truly childless editor as empty |
| `src/app/chat/composer/enter-stale-ime-flag.test.tsx` | Tests: composer Enter — stale IME composition flag recovery (#44135); sends on Enter despite a wedged composing flag when the native event says not composing; still swallows Enter during a genuine composition (isComposi… |
| `src/app/chat/composer/enter-submit-dom-race.test.tsx` | No global setupFiles registers auto-cleanup, so unmount between tests — otherwise a second render() leaks the first editor and getByTestId('editor') matches multiple nodes. |
| `src/app/chat/composer/floating-state.ts` | Exports `FloatingComposerOwner` |
| `src/app/chat/composer/floating-surface.test.tsx` | Tests: shares one visible composer while preserving each editor and draft across hover, focus and docking; hands the floating recipient to a visible tab when its old tab hides or closes |
| `src/app/chat/composer/floating-surface.tsx` | Exports `FloatingComposerSurface` |
| `src/app/chat/composer/floating-target-editable-guard.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/floating-target-floating-layer.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/floating-target-media-controls.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/floating-target-media.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/floating-target-selection-guard.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/floating-target.ts` | Exports `registerFloatingComposer`, `claimFloatingComposer`, `pinFloatingComposerCapture` |
| `src/app/chat/composer/focus-chord.test.ts` | jsdom is not macOS, so the chord is Ctrl+L. isComposerChord reads ctrlKey on other systems and metaKey on macOS. |
| `src/app/chat/composer/focus-chord.ts` | ⌘/Ctrl+L moves focus to the composer from anywhere. This matches the address-bar muscle memory of a browser. The other handlers of the chord keep priority: - A terminal or preview selection sends itself to the composer… |
| `src/app/chat/composer/focus.test.ts` | Tests: focusComposerInput; does not steal the caret from another live composer; still focuses when the caret is not already in a composer; takes the caret from a hidden keep-alive composer on tab switch |
| `src/app/chat/composer/focus.ts` | Composer focus + external-insert bus. Mutations from outside the composer (sidebar attach, drag drop, terminal Cmd+L, preview console, etc.) dispatch through here. Each composer subscribes and routes the work back into… |
| `src/app/chat/composer/help-hint.tsx` | Exports `HelpHint` |
| `src/app/chat/composer/hooks/completion-route.ts` | Where a composer completion RPC (`commands.catalog`, `complete.slash`, `complete.path`) for `sessionId` goes: the session's OWNER, never the window's ambient socket. On a multiplexed local gateway the ambient socket's a… |
| `src/app/chat/composer/hooks/slash-localization.test.tsx` | Tests: desktop slash description localization; uses the active catalog across aliases and help while preserving unknown descriptions and usage syntax; refreshes both cached bare and typed suggestions when the UI locale… |
| `src/app/chat/composer/hooks/use-at-completions-contrib.test.tsx` | `composer.atCompletions` contributions merge into the `@` popover ahead of the gateway's path results (#88060 — Bot Mode agent handles). Covers: rows appear, prefix filtering is delegated to the source, contributed rows… |
| `src/app/chat/composer/hooks/use-at-completions.test.ts` | Tests: PERF: @ path completions are cached and skip the debounce; serves a repeated query with no round trip and no spinner; a cached query paints without waiting out the debounce |
| `src/app/chat/composer/hooks/use-at-completions.ts` | Exports `useAtCompletions` |
| `src/app/chat/composer/hooks/use-auto-speak-replies.cross-window.test.tsx` | Loaded once at collection, outside every test's budget: vi.resetModules() keeps each module's transformed code, so the fresh copy a test imports only re-evaluates it. Without this the first test pays the cold transform… |
| `src/app/chat/composer/hooks/use-auto-speak-replies.owner.test.tsx` | Tests: useAutoSpeakReplies — owner-routed synthesis; synthesizes a Bot reply with the scope owner (connection, profile), not the active scope |
| `src/app/chat/composer/hooks/use-auto-speak-replies.test.tsx` | Tests: useAutoSpeakReplies — Edge TTS fallback chain (#93515); does not re-speak the reply once playback goes idle after an id rewrite mid-fallback; speaks a tool-folded rewrite once when the assistant ordinal drifts; d… |
| `src/app/chat/composer/hooks/use-auto-speak-replies.ts` | Exports `clearOwnedSpeechTurnsForTests`, `useAutoSpeakReplies` |
| `src/app/chat/composer/hooks/use-card-waiting-submit.ts` | In the onboarding chat typed text answers a waiting card through Send; an empty draft still offers Stop. |
| `src/app/chat/composer/hooks/use-completions-owner-route.test.tsx` | Tests: composer completions route to the session owner; serves / catalog and typed lookups from the owning profile, not the ambient socket; does not replay an ambient answer once the session owner resolves; serves @ pat… |
| `src/app/chat/composer/hooks/use-composer-branch.ts` | Exports `useComposerBranch` |
| `src/app/chat/composer/hooks/use-composer-draft.persist-window.test.tsx` | A composer runtime that behaves like assistant-ui's: setText updates the state and notifies subscribers synchronously. |
| `src/app/chat/composer/hooks/use-composer-draft.test.tsx` | Tests: useComposerDraft — attachment scope stays coherent with the committed session on switch (#59305); clears the outgoing session attachments by the layout phase right after switching sessions; swaps the draft TEXT b… |
| `src/app/chat/composer/hooks/use-composer-draft.ts` | Exports `useComposerDraft` |
| `src/app/chat/composer/hooks/use-composer-drop.ts` | Exports `useComposerDrop` |
| `src/app/chat/composer/hooks/use-composer-esc-cancel.test.tsx` | Tests: useComposerEscCancel; cancels the turn on Esc while busy with chat focus; does not cancel on Esc when the turn is not busy; does not cancel on Esc while an overlay surface covers the chat |
| `src/app/chat/composer/hooks/use-composer-esc-cancel.ts` | Exports `useComposerEscCancel` |
| `src/app/chat/composer/hooks/use-composer-metrics.test.tsx` | Tests: useComposerMetrics — published clearance survives an effect replay; keeps main\; uses a single control column below the two-touch-target budget; collapses extra controls earlier when touch targets consume more wi… |
| `src/app/chat/composer/hooks/use-composer-metrics.ts` | Exports `ComposerFit`, `useComposerMetrics` |
| `src/app/chat/composer/hooks/use-composer-placeholder.ts` | Exports `useComposerPlaceholder` |
| `src/app/chat/composer/hooks/use-composer-popout.test.tsx` | Tests: useComposerPopout; removes the pop-out affordance when gestures are disabled |
| `src/app/chat/composer/hooks/use-composer-popout.ts` | Exports `useComposerPopout` |
| `src/app/chat/composer/hooks/use-composer-queue.test.tsx` | Tests: useComposerQueue park integration; admits native Queue through submit and retains an uncertain draft without a local replay; does not clear the next session draft when a queue ACK arrives after navigation; resche… |
| `src/app/chat/composer/hooks/use-composer-queue.ts` | Exports `useComposerQueue` |
| `src/app/chat/composer/hooks/use-composer-screenshot.test.tsx` | Tests: screenshot composer routing; attaches once to the active split composer even without document focus, preserving its draft; rejects a late screenshot after a draft round trip and invalidates the image-write contin… |
| `src/app/chat/composer/hooks/use-composer-screenshot.ts` | Exports `useComposerScreenshot` |
| `src/app/chat/composer/hooks/use-composer-submit.accept-clear.test.tsx` | Only the assistant-ui adapter is substituted; the draft hook, the submit hook and the shared stash are the real ones. |
| `src/app/chat/composer/hooks/use-composer-submit.restore-scoping.test.tsx` | Tests: keeps a late rejected B submit out of A’s draft and next ordinary Send (#66661); restores text and attachments by the loaded draft owner, not an uncommitted navigation render; does not treat arbitrary navigation… |
| `src/app/chat/composer/hooks/use-composer-submit.send-then-close.test.tsx` | The page is real (draft DOM, persistence, submit hook); only the assistant-ui adapter is substituted. A "window close" is the page's own pagehide flush plus a fresh module graph, so nothing the dead page held in memory… |
| `src/app/chat/composer/hooks/use-composer-submit.test.tsx` | Tests: useComposerSubmit external request routing; routes a refused native steer through canonical queue admission; drops an idle hidden request the gateway rejects instead of restoring it into the draft; does not fan o… |
| `src/app/chat/composer/hooks/use-composer-submit.ts` | Exports `useComposerSubmit` |
| `src/app/chat/composer/hooks/use-composer-trigger.test.ts` | Tests: useComposerTrigger — the onboarding chat before setup ends; opens no slash menu, and still opens the @ menu; useComposerTrigger — slash anywhere in the prompt; opens the completion list for a slash typed mid-mess… |
| `src/app/chat/composer/hooks/use-composer-trigger.ts` | Exports `triggerKeyUpHandler`, `rebuildAroundCaret`, `useComposerTrigger` |
| `src/app/chat/composer/hooks/use-composer-undo.test.tsx` | Mount the hook against a real contentEditable, exposing its API. |
| `src/app/chat/composer/hooks/use-composer-undo.ts` | Each mounted composer's undo recorder, keyed by its editor element, for the one edit the app makes from outside the composer tree: a context-menu replacement (`app/context-menu/composer-menu.ts`). |
| `src/app/chat/composer/hooks/use-composer-url-dialog.test.tsx` | Tests: useComposerUrlDialog; drops an @url: directive into the draft when there is no host onAddUrl; prefers the host onAddUrl handler, then clears + closes the dialog; no-ops on an empty / whitespace-only URL |
| `src/app/chat/composer/hooks/use-composer-url-dialog.ts` | Exports `useComposerUrlDialog` |
| `src/app/chat/composer/hooks/use-composer-voice-shortcuts.test.tsx` | Tests: composer voice shortcuts; dictates only on the active visible target and ignores a disabled target; forwards repeated dictation requests without toggling voice conversation |
| `src/app/chat/composer/hooks/use-composer-voice.test.tsx` | Tests: useComposerVoice voice submission; uses live busy state when a retained voice callback submits after barge-in |
| `src/app/chat/composer/hooks/use-composer-voice.ts` | Exports `useComposerVoice` |
| `src/app/chat/composer/hooks/use-emoji-completions.ts` | `:shortcode:` completions for the composers, Slack-style (`:joy` → 😂). Draws from the same bundled emojibase-data the reaction picker uses (served at ./emojibase by the `hermes:emojibase-assets` vite plugin — offline, n… |
| `src/app/chat/composer/hooks/use-live-completion-adapter.ts` | Exports `CompletionEntry`, `CompletionPayload`, `useLiveCompletionAdapter` |
| `src/app/chat/composer/hooks/use-mic-recorder.test.tsx` | The level meter behind continuous voice mode is an AudioContext on the capture stream. #75329: a torn-down context was still closing when the next take opened another, the device errored, and the dead meter silently |
| `src/app/chat/composer/hooks/use-mic-recorder.ts` | Exports `MicRecorderOptions`, `MicRecording`, `MicRecorderErrorCopy`, `micError`, `useMicRecorder` |
| `src/app/chat/composer/hooks/use-micro-actions.ts` | Resolve every registered micro-action provider for this session and publish the result to `$composerActionsBySession`, which the pill strip renders. Core registers nothing, so the strip stays empty until something contr… |
| `src/app/chat/composer/hooks/use-middleware-submit.ts` | Exports `useMiddlewareSubmit` |
| `src/app/chat/composer/hooks/use-popout-drag.test.tsx` | Tests: useComposerPopoutGestures; never peels the composer out when a text-selection drag starts in the rich editor; does not arm a dock peel from the composer surface; still peels out from the dedicated drag region |
| `src/app/chat/composer/hooks/use-popout-drag.ts` | Exports `useComposerPopoutGestures` |
| `src/app/chat/composer/hooks/use-slash-completions.test.tsx` | Tests: useSlashCompletions; serves the bare-slash catalog from cache instead of re-requesting it; scopes a sessionless catalog and typed lookup to the routed profile; leaves only skills for a mid-message slash |
| `src/app/chat/composer/hooks/use-slash-completions.ts` | Exports `SlashCompletions`, `useSlashCompletions` |
| `src/app/chat/composer/hooks/use-status-drawer.test.tsx` | Tests: keeps stored conversations independent from drafts and other conversations |
| `src/app/chat/composer/hooks/use-status-drawer.ts` | Exports `useStatusDrawer` |
| `src/app/chat/composer/hooks/use-status-presence.test.ts` | Tests: useSessionStatusPresence; returns false when session is null or empty; returns true when legacy status items exist; returns true when structured goal exists in session control |
| `src/app/chat/composer/hooks/use-status-presence.ts` | Structural view of the per-session feeds — they hold different item types, and all this hook needs from each is "does this key have rows". |
| `src/app/chat/composer/hooks/use-voice-conversation-boundary.test.tsx` | Tests: speaks a sealed narration while busy and keeps the session open for the final reply |
| `src/app/chat/composer/hooks/use-voice-conversation-meter.test.tsx` | #75329: continuous voice decides "did the user speak?" from the WebAudio level meter alone. When that meter's AudioContext hits a device error the take reads heardSpeech=false, and every later utterance was dropped befo… |
| `src/app/chat/composer/hooks/use-voice-conversation-rearm.test.tsx` | Tests: useVoiceConversation playback rearm; re-arms the microphone after normal streaming playback completes; honors Stop while streaming playback is still preparing; does not start fallback playback after Stop during s… |
| `src/app/chat/composer/hooks/use-voice-conversation-stale-reply.test.tsx` | Regression: after a reply finished playing, the NEXT voice turn must not re-speak that reply while the model is thinking. The normal (silence-detected) submit path has to mark the previous reply spoken BEFORE submitting… |
| `src/app/chat/composer/hooks/use-voice-conversation-warmup.test.tsx` | #105955 review: the warm-up fired when the conversation starts listening is a READINESS BARRIER before transcription — handleTurn() awaits it before handing the clip to `onTranscribeAudio`, so a cold local model load se… |
| `src/app/chat/composer/hooks/use-voice-conversation.test.tsx` | The full-duplex contract: the barge monitor is live across the WHOLE agent turn — generation (thinking) and playback (speaking) — so speaking over the model interrupts it mid-generation instead of the mic being deaf unt… |
| `src/app/chat/composer/hooks/use-voice-conversation.ts` | Exports `ConversationStatus`, `useVoiceConversation` |
| `src/app/chat/composer/hooks/use-voice-live-conversation.owner.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/composer/hooks/use-voice-live-conversation.test.ts` | @vitest-environment jsdom |
| `src/app/chat/composer/hooks/use-voice-live-conversation.ts` | How long an accepted delegation may sit before the gateway shows the turn running. |
| `src/app/chat/composer/hooks/use-voice-recorder-warmup.test.tsx` | #105955 review: the mic-open warm-up must act as a READINESS BARRIER before transcription — `stop()` awaits the warm-up fired at start, so a cold local model load settles inside the lease request's own budget instead of… |
| `src/app/chat/composer/hooks/use-voice-recorder.ts` | Exports `useVoiceRecorder` |
| `src/app/chat/composer/index.tsx` | Exports `ChatBar` |
| `src/app/chat/composer/inline-references.test.ts` | There is ONE inline-reference system: `class="ref"` + `data-ref="<kind>"`. A pasted link, an ` |
| `src/app/chat/composer/inline-refs.ts` | Exports `InlineRefInput`, `SessionDragPayload`, `sessionLabel`, `sessionInlineRef`, `dragHasAttachments`, `droppedFileInlineRef` … |
| `src/app/chat/composer/large-paste.test.ts` | Tests: large paste policy; converts only pastes strictly past the threshold; labels the chip by encoded byte size, not character count |
| `src/app/chat/composer/large-paste.ts` | Large-paste-to-attachment policy. Pasting more than ~3k characters converts the content into a text attachment instead of inserting it inline, keeping the composer clean and preventing a single paste from flooding the i… |
| `src/app/chat/composer/micro-actions.tsx` | Floating pill — the shared treatment for a control that sits over the composer (`composerFloatingPill`), plus this strip's own width cap and disabled state. NEVER `pointer-events-none`, not even when disabled. The pop-o… |
| `src/app/chat/composer/model-pill.test.tsx` | Tests: ModelPill pinned-override badge; shows the pin dot on a draft running a manual pick; stays quiet when the composer reflects the profile default; stays quiet on a live session (footer shows that session, not the p… |
| `src/app/chat/composer/model-pill.tsx` | `shrink` (not `shrink-0`) with a truncating label: the pill is the one control in the row that can give width back continuously, so it absorbs the squeeze between collapse stages instead of pushing Send past the edge. |
| `src/app/chat/composer/new-chat-first-send.test.tsx` | Tests: a new chat first send keeps its creation-time draft, queues on the new chat and leaves session A alone (#139190); a follow-up queued while session.create is in flight moves to the new chat and sends there; claimi… |
| `src/app/chat/composer/paste-to-focus.test.ts` | Minimal DataTransfer stand-in: text/plain + optional image file items. |
| `src/app/chat/composer/paste-to-focus.ts` | Paste-to-focus: the paste twin of type-to-focus. A ⌘V/Ctrl+V landing on non-editable chrome (the transcript, empty chat, the window body) routes the clipboard into the active composer instead of dying on the body — imag… |
| `src/app/chat/composer/paste-url-is-text.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/composer/path-refs.test.ts` | Tab-descending into a folder from the `@` popover leaves a bare ` |
| `src/app/chat/composer/path-refs.ts` | Bare-path recognition for the composer. Walking into a folder from the `@` popover (Tab) re-types the token as a bare ` |
| `src/app/chat/composer/prepared-image-recovery.test.tsx` | Tests: reopened composer offers exact image occurrence only for its original destination; recovery never overwrites a newer draft or offers an ambiguous legacy send |
| `src/app/chat/composer/prepared-image-recovery.tsx` | Exports `PreparedImageRecovery` |
| `src/app/chat/composer/queue-panel.test.tsx` | Tests: QueuePanel expandable previews; offers expansion for long and multiline entries but not short ones; expands an entry to its full text and collapses it back; QueuePanel lost turn |
| `src/app/chat/composer/queue-panel.tsx` | Exports `QueuePanel` |
| `src/app/chat/composer/queue-scope.test.tsx` | Tests: a new chat does not show the queue of the session just left (#139190) |
| `src/app/chat/composer/queue-slot.test.tsx` | Tests: Delete on a server-queued card cancels its admission at the authority; a server-queued card shows the Steer and Edit its owner serves, and never Next (RT-35); a server-queued card from an owner without the queued… |
| `src/app/chat/composer/queue-slot.tsx` | Exports `ComposerQueueSlotInputs`, `useComposerQueueScopeKey`, `renderComposerQueueSlot` |
| `src/app/chat/composer/reasoning-pill.test.tsx` | Tests: ReasoningPill; shows a clamped pick as what the route sends, never as a distinct level (#61634); shows THIS surface; never paints the profile default while a resumed session |
| `src/app/chat/composer/reasoning-pill.tsx` | Exports `ReasoningPill` |
| `src/app/chat/composer/restored-draft-notice.tsx` | Exports `RestoredDraftNotice` |
| `src/app/chat/composer/rich-editor.test.ts` | Tests: renderComposerContents; renders refs and raw text without interpreting user text as HTML; hydrates a committed leading slash command back to its pill; keeps a still-typed leading slash token as editable text |
| `src/app/chat/composer/rich-editor.ts` | Helpers for the contenteditable composer surface: serialize refs to chip HTML, walk the DOM back to plain ` |
| `src/app/chat/composer/scope.tsx` | COMPOSER SCOPE — which live composer a ChatBar instance IS. The main chat's ChatBar runs in the default scope (module-level attachment atom, focus-bus target 'main', the active session's awaiting-input edge). A session… |
| `src/app/chat/composer/send-click-stale-gate.test.tsx` | Tests: composer Send button — pointerdown syncs the live draft (#52950); opens the send gate synchronously on pointerdown when the DOM has text state has not synced; keeps the gate closed when the editor is genuinely em… |
| `src/app/chat/composer/send-closes-completion-list.test.tsx` | @vitest-environment jsdom Sending a message closes the `@`, `/` or `:` completion list that was open over its text, so the next Enter or Tab acts on the new, empty draft instead of picking a row from the stale list. |
| `src/app/chat/composer/slash-refs.test.ts` | Tests: slashCommandMatches; recognizes a leading command and a skill named mid-prose; leaves a path alone — /usr/local/bin is not a command; holds a trailing token as still-typed unless the text is inert |
| `src/app/chat/composer/slash-refs.ts` | Slash-command recognition for text the composer did not watch being typed — a paste, a restored draft, an undo step, a rebuilt line. The typed path chips a command as it's picked or accepted, so the composer agrees with… |
| `src/app/chat/composer/start-voice-button.tsx` | The primary "start voice conversation" button, with the engine picker one click away when the layout shows the voice controls unfolded. In the folded layout the picker lives in the voice menu; unfolded there is no menu,… |
| `src/app/chat/composer/status-stack/coding-row.test.tsx` | Tests: CodingStatusRow; opens the review pane from the branch and the diff counts, never the bar itself; copies the absolute cwd inline — checkmark feedback, no toast |
| `src/app/chat/composer/status-stack/coding-row.tsx` | Exports `CodingStatusRow` |
| `src/app/chat/composer/status-stack/collapsed-indicator.test.tsx` | Tests: ComposerStatusStack collapsed todo indicator; shows a running indicator next to the collapsed todo label; does not show a collapsed todo indicator when no todo is running |
| `src/app/chat/composer/status-stack/default-collapse.test.tsx` | Tests: offers a collapsed read-only checklist from an idle session, without a running spinner; auto-expands only todos and keeps other groups closed as activity arrives; starts structured goals collapsed and preserves m… |
| `src/app/chat/composer/status-stack/drawer.css` | Stylesheet |
| `src/app/chat/composer/status-stack/drawer.tsx` | Exports `StatusDrawerContent`, `StatusDrawerToggle` |
| `src/app/chat/composer/status-stack/goal-indicator.test.tsx` | The stack measures itself into a surface var — jsdom has no ResizeObserver. |
| `src/app/chat/composer/status-stack/hidden-pane-subagent-polls.test.tsx` | Tests: hidden-pane subagent polls; hidden snapshot tile issues no subagent.list; reveal seeds once and polls every 5s; hiding again stops it; hidden transcript tile issues no subagent.tail; reveal seeds once and polls e… |
| `src/app/chat/composer/status-stack/index.tsx` | Exports `ComposerStatusStack` |
| `src/app/chat/composer/status-stack/polling-guard.test.tsx` | The stack measures itself into a surface var — jsdom has no ResizeObserver. |
| `src/app/chat/composer/status-stack/preview-order.test.tsx` | Tests for `preview-order` |
| `src/app/chat/composer/status-stack/preview-row.test.tsx` | Tests: PreviewStatusRow; opens remote non-HTML file artifacts in the in-app preview instead of the local browser bridge; keeps local file artifacts on the browser bridge; keeps remote HTML on the staged browser-open pat… |
| `src/app/chat/composer/status-stack/preview-row.tsx` | Exports `PreviewStatusRow` |
| `src/app/chat/composer/status-stack/session-control-goal.tsx` | Exports `SessionControlGoalSection` |
| `src/app/chat/composer/status-stack/session-control-heartbeat.test.tsx` | Tests: SessionControlHeartbeatSection hidden-pane clock; a mounted card pauses while its pane is hidden and catches up the moment it is shown |
| `src/app/chat/composer/status-stack/session-control-heartbeat.tsx` | Exports `SessionControlHeartbeatSection` |
| `src/app/chat/composer/status-stack/session-control-loop.tsx` | Exports `SessionControlLoopSection` |
| `src/app/chat/composer/status-stack/session-control-utils.ts` | Exports `useSessionValue`, `useCountdownClock`, `ConfirmState`, `formatCountdown`, `formatInterval`, `formatHeartbeatInterval` |
| `src/app/chat/composer/status-stack/session-control.test.tsx` | Tests: ComposerStatusStack session-control UI; calls refreshSessionControl on mount and keeps legacy goal while capability is unknown/unsupported; replaces legacy goal when structured session control is supported withou… |
| `src/app/chat/composer/status-stack/session-control.tsx` | Exports `SessionControlSectionsProps`, `SessionControlSections` |
| `src/app/chat/composer/status-stack/status-row.tsx` | Exports `StatusItemRow` |
| `src/app/chat/composer/status-stack/subagent-controls.test.tsx` | Tests: sends steer and stop to the child parent owner, never the active gateway or child transcript; keeps rejected steer text and does not retarget when the owner is unknown |
| `src/app/chat/composer/status-stack/subagent-controls.tsx` | Exports `SubagentControls` |
| `src/app/chat/composer/status-stack/subagent-hydration.test.tsx` | Tests: hydrates the empty owner composer and exposes an extended owner-routed transcript without leaking on session change; does not resurrect a child completed while the roster snapshot was in flight |
| `src/app/chat/composer/status-stack/subagent-lifecycle.test.tsx` | Tests: keeps each worker draft while inspecting siblings and removes settled selection; measures detail elapsed from worker start rather than first inspection |
| `src/app/chat/composer/status-stack/subagent-section.test.tsx` | Tests: shows live work only from the composer session and keeps it hidden after collapse and progress; collapses a single worker and its selected detail using the caret, preserving the steering draft; retires the live f… |
| `src/app/chat/composer/status-stack/subagent-section.tsx` | Exports `SubagentSection` |
| `src/app/chat/composer/status-stack/subagent-transcript.tsx` | Exports `SubagentTranscript` |
| `src/app/chat/composer/status-stack/use-subagent-snapshot.ts` | Exports `rejectUnownedSubagentRequest`, `useSubagentSnapshot` |
| `src/app/chat/composer/test-utils.ts` | Collapse the selection to the end of the editor's contents. The composer's undo stack, ref rendering, and trigger detection all read the live selection, and jsdom starts with none — without this they see a caret at offs… |
| `src/app/chat/composer/text-utils.test.ts` | Tests: detectTrigger; detects a bare slash trigger with an empty query; detects a slash command query; detects a bare at-mention trigger with an empty query |
| `src/app/chat/composer/text-utils.ts` | Exports `TriggerState`, `DIRECTIVE_SCOPES`, `DirectiveScope`, `blobDedupeKey`, `extractClipboardImageBlobs`, `textBeforeCaret` … |
| `src/app/chat/composer/touch-text-entry.test.tsx` | Tests: composer text entry on a touch host (#145166); one still tap focuses the editor, which offers casing, correction and spelling; desktop keeps the attributes off and leaves taps to the browser |
| `src/app/chat/composer/touch-text-entry.ts` | A tap, not a scroll, drag or long press (which iOS hands to selection). |
| `src/app/chat/composer/trigger-popover-description.test.tsx` | Tests: reveals the complete slash description on hover without intercepting selection |
| `src/app/chat/composer/trigger-popover.test.tsx` | Tests: ComposerTriggerPopover keyboard scrolling; keeps keyboard navigation visible and restores the group header on wrap; uses the nearest drawer edge for upward, visible, and oversized rows; does not scroll for a hove… |
| `src/app/chat/composer/trigger-popover.tsx` | Exports `ComposerTriggerPopover` |
| `src/app/chat/composer/types.ts` | Exports `ContextSuggestion`, `QuickModelOption`, `ChatBarState`, `ChatBarProps`, `VoiceStatus`, `VoiceActivityState` |
| `src/app/chat/composer/undo-cut-drag.test.tsx` | @vitest-environment jsdom The main chat composer shares useComposerUndo with the edit composer and has the same two blind spots: Chromium runs a cut and an intra-editor text drag |
| `src/app/chat/composer/undo-history.test.ts` | Tests: undo/redo shortcut recognition; claims Cmd+Z and Ctrl+Z as undo, but not with Shift or Alt; claims Cmd+Shift+Z everywhere and Ctrl+Y as redo; never treats one keystroke as both undo and redo |
| `src/app/chat/composer/undo-history.ts` | The composer's own undo stack. The rich editor mutates its DOM through `Range` rather than the browser's editing commands — `execCommand('insertText')` is ~O(n²) on large multiline blobs and froze the composer for secon… |
| `src/app/chat/composer/url-dialog.tsx` | Exports `UrlDialog` |
| `src/app/chat/composer/url-refs.test.ts` | Tests: linkifyUrls; rewrites a bare link as a url directive; keeps the link in place mid-sentence and leaves its punctuation behind; keeps balanced parens but drops the one that closed the sentence |
| `src/app/chat/composer/url-refs.ts` | Bare-link recognition for the composer. A link the user pastes or types is the same thing the "+ → Add URL" dialog inserts, so it becomes an ` |
| `src/app/chat/composer/visibility.ts` | Editor visibility is narrower than chat visibility while a shared float is active. Background queues and explicit session actions still belong to the pane. |
| `src/app/chat/composer/voice-activity.test.tsx` | Tests: VoiceActivity accessibility; keeps the dictation timer visible without announcing every tick |
| `src/app/chat/composer/voice-activity.tsx` | Exports `VoiceActivity`, `VoicePlaybackActivity` |
| `src/app/chat/composer/voice-engine-rows.tsx` | Exports `VoiceEngineRows`, `useVoiceEngineName` |
| `src/app/chat/composer/voice-fan.tsx` | Exports `VoiceFanProps`, `VoiceFan` |
| `src/app/chat/composer/voice-menu.tsx` | Exports `VoiceMenuProps`, `VoiceMenu` |
| `src/app/chat/history-window.test.tsx` | Tests: bounded direct history runtime; reads one around page and selects it without replacing the live store; keeps history static during streaming and restores the newest live tail and capabilities; keeps the edit comp… |
| `src/app/chat/history-window.ts` | Exports `HISTORY_WINDOW_LIMIT`, `HistoryWindowResponse`, `fetchHistoryWindow`, `useHistoryWindow` |
| `src/app/chat/hooks/drop-warning.test.ts` | Tests: dropWarning; drops the period of a reason another item follows, and keeps the last one; drops the period before the count of the rest, and keeps each reason whole in the detail; keeps a lone reason as it is, peri… |
| `src/app/chat/hooks/drop-warning.ts` | A drop item the composer could not attach: what was dropped, and why when it is known. |
| `src/app/chat/hooks/use-composer-actions.drop-warnings.test.ts` | A drop item the composer cannot attach is reported in one bounded warning, never dropped silently. |
| `src/app/chat/hooks/use-composer-actions.test.ts` | Tests: partitionDroppedFiles; routes File-bearing OS drops to osDrops and path-only in-app drags to inAppRefs; treats an OS screenshot drop as an upload target (so it gets byte upload + vision); keeps gutter line-range… |
| `src/app/chat/hooks/use-composer-actions.ts` | Exports `isImagePath`, `attachmentPreviewDataUrl`, `resolveImageAttachmentPreview`, `DroppedFile`, `stageDroppedFilePath`, `HERMES_PATHS_MIME` … |
| `src/app/chat/hooks/use-file-drop-zone.ts` | `'session'` is set by callers from the pointer drag session's store — native drags only ever resolve to `'files'` here (sessions left native DnD; see session-drag.ts). |
| `src/app/chat/index.test.tsx` | Tests: ChatView render isolation; does not re-render chat history when an unrelated parent idle tick updates |
| `src/app/chat/index.tsx` | Exports `ChatRuntimeBoundary`, `ChatView` |
| `src/app/chat/intro-visibility.test.ts` | Tests: shouldShowIntro; shows on a fresh draft in the primary window; hides when the Appearance toggle is off; keeps the toggle authoritative over every other clause |
| `src/app/chat/intro-visibility.ts` | Whether the empty-chat intro splash renders. The splash is the full-height empty state of the primary chat: it belongs to a fresh draft in the main window and nothing else. Auxiliary and non-primary windows are scratch… |
| `src/app/chat/new-session-drag.test.ts` | --------------------------------------------------------------------------- The drag MACHINERY (startDragSession) is exercised by the pane-shell's own tests; here we capture the spec the resolver hands it and drive reso… |
| `src/app/chat/new-session-drag.ts` | Sidebar "New session" drag — the NEW-session resolver over the shared pointer drag session (pane-shell drag-session.ts). Same machinery and drop language as a session drag (session-drag.ts): a chat zone's TAB STRIP stac… |
| `src/app/chat/new-session-tab.test.tsx` | Tests: the registered New session ; fronts a blank main instead of creating a session; keeps a still-pending create single-flight: repeated clicks land on that one draft; a failed create does not latch the |
| `src/app/chat/new-session-tab.ts` | Exports `openNewSessionTab` |
| `src/app/chat/pane-mirror.ts` | Mirror a reactive list of "tiles" into layout-tree pane contributions: register a pane per tile, refresh its title in place, and dispose panes whose tile is gone. This is the shared bookkeeping — a keyed registry, a wan… |
| `src/app/chat/perf-probe.tsx` | Exports `PerfProbe` |
| `src/app/chat/pr-tag.tsx` | GitHub's own colour language, mapped onto our tokens: open is the "go" green, merged the purple everyone reads as landed, draft and closed muted since neither is waiting on you. |
| `src/app/chat/preview-error-close.test.tsx` | Tests: a preview whose file is gone; offers Close in the error state, and it closes the tab |
| `src/app/chat/preview-session-focus.test.ts` | Tests: settles session-owned preview reveals in the same group without losing chat ownership |
| `src/app/chat/preview-tab-pin-menu.test.tsx` | Tests: offers Unpin after a pin and Pin after an unpin, toggling the stored flag each time |
| `src/app/chat/preview-tile-live-body.test.tsx` | A native guest has a lifetime beyond React: a remount, or any detach of its element, destroys the Electron guest (unsaved input, page JS state). Count both, on a stand-in for the pane body. |
| `src/app/chat/preview-tile.test.ts` | Tests: browserTabLabel; names the tab after the page; falls back to the host when the page has no title of its own; falls back to the surface when there is no page and no host |
| `src/app/chat/preview-tile.tsx` | PREVIEW TILES — every open preview (a file, a URL, an artifact) rendered as a layout-tree pane, the preview analog of session and route tiles. The rail used to bring its OWN tab strip: a second bar beside the zone's own… |
| `src/app/chat/profile-tag.tsx` | Owning-profile chip: the shared { |
| `src/app/chat/resume-exhausted-overlay.test.tsx` | Stranded resume overlay (#106217 remainder): the full-window "Couldn't load this session" state hides the composer and used to offer only Retry — a wall with no way out. It must offer Start new session |
| `src/app/chat/resume-exhausted-overlay.tsx` | Full-window fallback for a routed session whose resume exhausted every retry (#106217 remainder). The overlay covers the thread AND the composer is hidden underneath it, so a Retry-only action row is a wall with no way |
| `src/app/chat/reuse-draft-tab.test.ts` | Tests: the tab-strip ; fronts the blank draft tab instead of asking for another one; fronts main when main is the blank new chat; still opens a new tab once every draft has been used |
| `src/app/chat/reuse-draft-tab.ts` | Exports `isUntouchedDraftTile`, `frontUntouchedDraftTab` |
| `src/app/chat/right-rail/index.ts` | TypeScript source: `index` |
| `src/app/chat/right-rail/preview-act.test.ts` | Tests: actOnActivePreview (drive_preview tool); tells the agent to open a page when no live pane is behind the tab; re-inventories after a mutating action so the next ref is current; awaits page-owned thenables for inve… |
| `src/app/chat/right-rail/preview-act.ts` | PREVIEW ACT — performs the agent's interactions inside the preview pane's guest page, so `drive_preview` drives whatever web app is open in the in-app browser. The guest page is out-of-process; nothing here can touch it… |
| `src/app/chat/right-rail/preview-active-tab.ts` | THE PREVIEW AN AGENT TOOL ACTS ON — one resolution shared by read_preview (preview-reader.ts), drive_preview (the nav / input / script-runner registries) and the preview tour, so a read and the action after it can never… |
| `src/app/chat/right-rail/preview-annotate-card.test.tsx` | Tests: placeAnnotateCard; sits to the right of the pin instead of past a full-width selection; stays inside the pane when the pin is on the right edge |
| `src/app/chat/right-rail/preview-annotate-card.tsx` | Exports `placeAnnotateCard`, `PreviewAnnotateCard` |
| `src/app/chat/right-rail/preview-annotate-host.test.ts` | Tests: preview annotate host; does not evaluate guest template interpolations while wrapping the overlay source; calls executeJavaScript as a method so Electron can read this.getWebContentsId; pads the element crop befo… |
| `src/app/chat/right-rail/preview-annotate-host.ts` | Drive the guest overlay and crop capture from the preview pane. Overlay I/O only — stack/pack/flush live in lib/preview-annotate. |
| `src/app/chat/right-rail/preview-artifact.test.tsx` | Tests: ArtifactPreview; renders html in a scripts-only sandboxed frame the parent app is unreachable from; opens a browser-hosted HTML blob without corrupting it as a file URL; strips scripts out of svg before it render… |
| `src/app/chat/right-rail/preview-artifact.tsx` | Exports `ArtifactPreview` |
| `src/app/chat/right-rail/preview-browser-bar.test.tsx` | Tests: normalizePreviewAddress; passes through http and https URLs; gives a bare host https and a loopback host http; rejects empty input |
| `src/app/chat/right-rail/preview-browser-bar.tsx` | BROWSER BAR: back / forward / reload / address / pop-out (or pop-in) for a URL preview. The Browser tab had no way to move: no history, and the only address on screen was a read-only label. Every other embedded browser… |
| `src/app/chat/right-rail/preview-browser-frame-hint.tsx` | Exports `PreviewBrowserFrameHint` |
| `src/app/chat/right-rail/preview-browser-frame.ts` | Browser-hosted Desktop has no Electron `<webview>`, so a live web preview mounts a sandboxed iframe instead. The frame is opaque to this renderer (no console, history, page reader, or input channel); the pane only navig… |
| `src/app/chat/right-rail/preview-console-state.test.ts` | Tests: preview console retention; truncates one oversized message and source before retaining them; does not split a UTF-16 surrogate pair at the truncation boundary; evicts oldest large entries and their selections to… |
| `src/app/chat/right-rail/preview-console-state.ts` | Exports `PREVIEW_CONSOLE_MAX_ENTRIES`, `PREVIEW_CONSOLE_MAX_MESSAGE_CHARS`, `PREVIEW_CONSOLE_MAX_SOURCE_CHARS`, `PREVIEW_CONSOLE_MAX_TOTAL_CHARS`, `ConsoleEntry`, `ConsoleEntryInput` … |
| `src/app/chat/right-rail/preview-console-store.ts` | Per-tab preview console stores. The console panel lives in the pane and its toggle lives in the pane's browser bar, but the store has to outlive any one render and be addressable by tab id — a tab can be parked and remo… |
| `src/app/chat/right-rail/preview-console.tsx` | Exports `compactUrl`, `formatLogLine`, `formatConsoleEntries`, `isNearConsoleBottom`, `clampConsoleHeight`, `PreviewConsolePanel` |
| `src/app/chat/right-rail/preview-drive-channels.ts` | The channels the agent acts on a live preview page through, published per tab while the pane's surface is an Electron `<webview>`: the script runner and the trusted-input channel (preview-act.ts drives the page with bot… |
| `src/app/chat/right-rail/preview-drive.ts` | PREVIEW DRIVE — the agent's hand on the mouse and keyboard. Everything here goes out through `sendInputEvent`, so the guest page receives ordinary trusted input: the pointer really moves across it, `:hover` really match… |
| `src/app/chat/right-rail/preview-file-save-scope.test.tsx` | Tests for `preview-file-save-scope` |
| `src/app/chat/right-rail/preview-file.test.tsx` | Behavior tests for the .md file preview renderer: input markdown goes through normalizeFilePreviewMath -> Streamdown (+ KaTeX math plugin) and must come out as real rendered elements, matching what the chat transcript |
| `src/app/chat/right-rail/preview-file.tsx` | Exports `PreviewEmptyState`, `MarkdownPreview`, `PreviewModeSwitcher`, `SourceView`, `PreviewViewMode`, `LocalFilePreview` |
| `src/app/chat/right-rail/preview-guest-offscreen.ts` | A Browser guest that is mounted but OFF SCREEN — an inactive tab, a collapsed side, or a hidden session's kept-alive page — must not act like the page the user is on. Chromium keeps tracking a hidden guest as the focuse… |
| `src/app/chat/right-rail/preview-input.test.ts` | #116281: the act engine measures targets in guest CSS pixels, but the webview's input space is css × zoom. At the shipped 90 % default an unscaled click landed 1/0.9 too far from the origin and missed silently. |
| `src/app/chat/right-rail/preview-input.ts` | PREVIEW INPUT REGISTRY — real input into the preview pane's guest page, the difference between the agent DRIVING the browser and merely poking its DOM. `executeJavaScript` can only ever dispatch synthetic events: `isTru… |
| `src/app/chat/right-rail/preview-mind.ts` | IDLE PULSE — keeps the preview overlay alive while the model reasons. Everything else the overlay draws is narration of an action, so the pane goes dark for the gap between actions — which is most of the time the agent… |
| `src/app/chat/right-rail/preview-nav.test.ts` | Tests: commandFocusedPreview; never routes host keyboard commands to a hidden guest with stale native focus; reports no handler when focus is elsewhere, so ⌘R falls back to the window; answers for focus nested inside th… |
| `src/app/chat/right-rail/preview-nav.ts` | Browser gestures that land on the app's own chrome — ⌘R with the address bar focused, a mouse's back/forward buttons over the pane's frame. The interesting case is handled elsewhere: when the user is INSIDE the guest pa… |
| `src/app/chat/right-rail/preview-nudge.ts` | OVERLAY NUDGE — the one way to say a stage to an overlay that is ALREADY on the page. The act pipeline (preview-act.ts) injects the whole engine because it has to: it needs to resolve a ref, measure a node and read the… |
| `src/app/chat/right-rail/preview-pane.test.tsx` | The consent dialog has its own test file and needs a QueryClientProvider; these tests exercise the pane's console/watch/webview wiring, not the prompt, so isolate it the way the pane's other collaborators are. |
| `src/app/chat/right-rail/preview-pane.tsx` | Side-effect import: watches the turn edge so the overlay keeps a pulse while the model reasons. Lives here because the pane is what makes it reachable. |
| `src/app/chat/right-rail/preview-popout-bridge.test.ts` | Tests: preview pop-out bridge; reports a live surface when a script runner is registered; round-trips an act request to the browser pop-out responder; round-trips a read request over the preload IPC relay |
| `src/app/chat/right-rail/preview-popout-bridge.ts` | Cross-window bridge for the popped-out Browser. Each Electron window is its own renderer, so the webview registries that drive_preview / read_preview use live only in the window that mounts the pane. After pop-out that… |
| `src/app/chat/right-rail/preview-reader.test.ts` | Tests: readActivePreview (read_preview tool); answers null when nothing is open, so the tool reports it cleanly; serializes the Browser tab through its registered page reader; windows long pages with start/count and rep… |
| `src/app/chat/right-rail/preview-reader.ts` | PREVIEW READER — the read_preview tool's window into the preview pane, the preview analog of the terminal's buffer registry (see right-sidebar/ terminal/buffer.ts). A URL/HTML preview renders in a sandboxed <webview> ow… |
| `src/app/chat/right-rail/preview-script-runner.ts` | PREVIEW SCRIPT RUNNER REGISTRY — the one way anything in the app reaches into the preview pane's guest page, the script analog of preview-nav's handle registry. A live browser pane registers its webview's `executeJavaSc… |
| `src/app/chat/right-rail/preview-tour.ts` | PREVIEW TOUR — runs tour actions inside the preview pane's guest page, so a tour can walk through ANY web app open in the in-app browser, not just Hermes itself. The guest page is out-of-process; nothing here can touch… |
| `src/app/chat/right-rail/preview-typing-abort.ts` | PREVIEW TYPING ABORT — the keystroke loop outlives the tool that started it. `drive_preview` blocks on `preview.act` for 45s. When that wait times out, or the turn is interrupted, the backend withdraws the request with… |
| `src/app/chat/right-rail/preview.tsx` | Exports `PreviewTilePane` |
| `src/app/chat/right-rail/real-profile-consent-dialog.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/right-rail/real-profile-consent-dialog.tsx` | Exports `shouldOfferRealProfilePrompt`, `RealProfileConsentDialog` |
| `src/app/chat/route-session-state.test.ts` | Tests: isRouteSessionMismatch; keeps the composer mounted when auto-compression rotates root to tip; still suppresses the previous chat while a genuinely different route loads; does not require a session row when the se… |
| `src/app/chat/route-session-state.ts` | Exports `isRouteSessionMismatch` |
| `src/app/chat/route-tile-reactivity.test.tsx` | #109063: route tiles subscribe to ROUTES_AREA but used to derive routes via an independently-called `contributedRoutes()`, which React Compiler can keep memoized across the delivered subscription update. These tests run… |
| `src/app/chat/route-tile-title.test.tsx` | A route tile opened BEFORE its plugin route registers must pick up the contribution's title once registration lands. `paneMirror` recomputes titles only when one of its atoms changes; without a routes-area signal the ta… |
| `src/app/chat/route-tile.tsx` | ROUTE (PAGE) TILES — a full-page view rendered as a layout-tree pane BESIDE the main thread, the page analog of session tiles. Built-in pages (Capabilities / Messaging / Artifacts) render their view; plugin pages render… |
| `src/app/chat/runtime-backfill.test.tsx` | Tests: runtime older-page expansion |
| `src/app/chat/runtime-repository.test.ts` | Tests: useRuntimeMessageRepository; emits each id once when the transcript repeats one; builds a repository the runtime can link without throwing; anchors a branch group to its fork point, and a windowed cut keeps it |
| `src/app/chat/runtime-repository.ts` | The exact fallback status ExportedMessageRepository.fromBranchableArray uses. Normalization happens HERE, once per message, so the cached record below is already the final ThreadMessage the runtime consumes. |
| `src/app/chat/scroll-to-bottom-button.test.tsx` | Tests: ScrollToBottomButton; isolates pre-runtime panes using their existing composer surface identity; does not light a sibling pane when only one visible session scrolls up; keeps each visible pane |
| `src/app/chat/scroll-to-bottom-button.tsx` | Exports `ScrollToBottomButton` |
| `src/app/chat/session-draft-title.tsx` | Exports `SessionDraftTitleProps`, `SessionDraftTitle` |
| `src/app/chat/session-drag.test.ts` | A session drop resolves its target by rect-testing the chat surfaces in the document. A tab group keeps inactive tabs MOUNTED with their layout box intact, so a background tab's rect is identical to the foreground tab's… |
| `src/app/chat/session-drag.ts` | Sidebar session drag — the session RESOLVER over the shared pointer drag session (pane-shell drag-session.ts). Same machinery as a pane drag (threshold, rAF moves, snapshots, Esc-as-top-layer with synchronous teardown),… |
| `src/app/chat/session-status-dot.tsx` | A pure lookup table: each state maps to its className, aria-label, and title. No priority resolution here — $sessionDotStateById already picked one. Label/title resolve from sidebar.row translations, keyed by name. |
| `src/app/chat/session-tile-actions.test.ts` | Tests: session tile optimistic owner metadata; never lists a bots-workspace tile — hidden relationship chats stay off the Sessions list (#113273); keeps the tile source on its first optimistic sidebar row; useSessionTil… |
| `src/app/chat/session-tile-actions.ts` | Prompt actions for a SESSION TILE — the same verbs the primary chat wires (submit incl. slash, cancel, steer, edit, reload, restore, branch-hide sync), targeted at the tile's session instead of the active one. State wri… |
| `src/app/chat/session-tile-attachments.test.tsx` | Tests: session tile attachment occurrence ownership; preserves a thumbnail that resolves before tile submit staging; rejects stale tile staging after remove and reattach of the same path; preserves a same-path replaceme… |
| `src/app/chat/session-tile-owner.test.ts` | Tests: tileOwnerRoute; prefers the tile own explicit route; falls back to the session row owner when the tile carries no route; falls back to the owner hint when neither tile nor row is tagged |
| `src/app/chat/session-tile-owner.ts` | The owner a session tile routes its own RPCs through — the tile's explicit route first, then the session row's `(connection, profile)` tag, with `knownSessionOwner` folding in the owner hint. A tile opened without an ex… |
| `src/app/chat/session-tile-row.test.ts` | Tests: listTileSessionRow; lists an unlisted ⌘T tab from the user; leaves an already-listed session alone so a real title survives re-sends; matches a listed session across compression by lineage root |
| `src/app/chat/session-tile-slice-title.test.ts` | Tests: tileStoredRow resolves across every sidebar slice; resolves a local recents row; resolves a telegram row listed only in the messaging slice; resolves a cron row listed only in the cron slice |
| `src/app/chat/session-tile.test.ts` | Tests: shouldResumeSessionTile; resumes an unbound tile once the gateway is open; does not resume a session the user is deleting; waits for the gateway, a free slot, and an unbound, unlatched tile |
| `src/app/chat/session-tile.tsx` | SESSION TILES — a stored session rendered as a layout-tree pane BESIDE the main thread (multi-session tiling). A tile IS the real chat surface: the same ChatView/ChatBar/Thread tree the primary session renders, mounted… |
| `src/app/chat/session-view.test.ts` | Tests: primary session view reads its own session slice; shows the active session transcript, not a background session still streaming; ignores a background session that keeps streaming after the user switches away; fal… |
| `src/app/chat/session-view.tsx` | Exports `SessionView`, `reasoningEffortPending`, `PRIMARY_SESSION_VIEW`, `SessionViewProvider`, `useSessionView` |
| `src/app/chat/short-session-hang-repro.tsx` | Exports `bounded` |
| `src/app/chat/sidebar/archive-copy.test.ts` | Tests: archived-session instructions; advertises modifiers that archive rather than open a tab in every locale |
| `src/app/chat/sidebar/chat-sidebar.integration.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/sidebar/chrome-section-add-button.test.tsx` | Tests: SidebarSectionAddButton; keeps a sub-threshold press an ordinary new-session click; starts the new-session drag on pointer-down and creates at the drop placement; stays click-only without either drag handler |
| `src/app/chat/sidebar/chrome.tsx` | Exports `SidebarSectionMeta`, `SidebarSectionAddButton`, `SidebarRowStack`, `SidebarRowNest`, `SidebarDateDivider`, `SidebarRowShell` … |
| `src/app/chat/sidebar/connection-glyph.tsx` | One glyph per connection kind — device, cloud, network, terminal — shared by the statusbar switcher, its menu, the fleet profile rail and the Bots rail so a gateway looks the same wherever it is named. Dependency-free o… |
| `src/app/chat/sidebar/connection-switcher.test.tsx` | Radix menus use pointer capture; jsdom does not implement it. |
| `src/app/chat/sidebar/connection-switcher.tsx` | Exports `ConnectionSwitcher` |
| `src/app/chat/sidebar/cron-jobs-section.test.tsx` | The peek's run list comes off the backend; the liveness flags below are the endpoint's own (`hermes_cli/web_routers/cron.py`: `is_active` is `ended_at IS NULL` + a 300s activity window, `scheduler_owned` is a live |
| `src/app/chat/sidebar/cron-jobs-section.tsx` | Exports `SidebarCronJobsSection` |
| `src/app/chat/sidebar/filter-menu.test.tsx` | Tests: translates the live filter menu while preserving selected values and the current grouping order |
| `src/app/chat/sidebar/filter-menu.tsx` | Exports `SidebarFilterMenu` |
| `src/app/chat/sidebar/fleet-gateway-menu-group.tsx` | Exports `FleetGatewayMenuGroup` |
| `src/app/chat/sidebar/fleet-rail.test.ts` | Tests: buildRestGroups; lists every gateway except the active one, in switcher order, regardless of which is active; carries each gateway default as its own square plus named profiles alphabetically; keeps an unreachabl… |
| `src/app/chat/sidebar/fleet-rail.ts` | Pure grouping for the fleet profile rail: which gateways sit "at rest" beside the active one, and which agents each of them carries. Kept free of React and stores so the ordering/collapse rules are unit-testable. |
| `src/app/chat/sidebar/gateway-group-model.test.ts` | Tests: buildGatewaySessionGroups; keys groups by exact owner, so one profile name on two gateways stays two groups; leaves legacy rows without a connection unassigned instead of guessing a gateway; scopeGatewaySessionGr… |
| `src/app/chat/sidebar/gateway-group-model.ts` | A gateway section's name: its registry label, else `localLabel` for the `local` source a registry does not list (the Webapp's one gateway, the host serving it), else the raw id. |
| `src/app/chat/sidebar/gateway-group-preferences.test.ts` | @vitest-environment jsdom |
| `src/app/chat/sidebar/gateway-group-preferences.ts` | Exports `renameGatewayGroup`, `reorderGatewayGroups`, `toggleGatewayGroup` |
| `src/app/chat/sidebar/gateway-groups-drag.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/sidebar/gateway-groups-webapp.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/sidebar/gateway-groups.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/sidebar/gateway-groups.tsx` | Exports `GatewayProfileGroups` |
| `src/app/chat/sidebar/index.tsx` | Exports `stripFtsMarkers`, `searchResultToSession`, `mergeSearchResults`, `ChatSidebar` |
| `src/app/chat/sidebar/load-more-row.test.tsx` | Tests: SidebarLoadMoreRow; still fires onClick (Tip does not intercept the trigger interaction) |
| `src/app/chat/sidebar/load-more-row.tsx` | Exports `SidebarLoadMoreRow` |
| `src/app/chat/sidebar/local-device-switch.tsx` | Resolve whether This device would install, without starting the installer. Missing bridge fails closed: a click must not reach runBootstrap unseen. |
| `src/app/chat/sidebar/order.test.ts` | Tests: resolveManualSessionOrderIds; clears legacy auto-seeded order until the user manually reorders sessions; keeps a manual order and surfaces newly seen sessions first; clears manual order when none of the saved ids… |
| `src/app/chat/sidebar/order.ts` | Fold ids absent from the persisted order back in, on the side they belong. Callers hand us a recency-sorted `currentIds`, so an id's position relative to the newest id the saved order still knows about says which side i… |
| `src/app/chat/sidebar/profile-dropdown-switcher.test.tsx` | @vitest-environment jsdom |
| `src/app/chat/sidebar/profile-dropdown-switcher.tsx` | Exports `ProfileSwitcher` |
| `src/app/chat/sidebar/profile-launch-menu.test.tsx` | Tests: opens the clicked canonical route without selecting it and saves only that route as default; distinguishes the same profile on another source and reports a rejected default write without success |
| `src/app/chat/sidebar/profile-launch-menu.tsx` | Exports `ProfileLaunchMenuItems`, `ProfileLaunchContextMenu`, `ProfileLaunchMenuSection` |
| `src/app/chat/sidebar/profile-menu-unserved.test.tsx` | The Webapp's gateway lists every installed profile and serves only some of them; its roster marks the rest `reachable: false`, and picking one is refused. The profile menus read that roster and show such a profile as un… |
| `src/app/chat/sidebar/profile-rail-connect.test.tsx` | The rail's discoverability pills are navigation, not identity — assert the multi-gateway entry point deep-links to Settings → Connections instead of relying on someone finding the pane three levels into Settings (the ex… |
| `src/app/chat/sidebar/profile-rail-fleet.test.tsx` | The fleet rail: with several registered gateways, every gateway's agents sit on the one strip — the active gateway's squares exactly as before, the rest as at-rest groups behind a hairline + kind glyph. Clicking an at-r… |
| `src/app/chat/sidebar/profile-rail-status.test.tsx` | #91710: a profile that finishes work while another is selected must carry a durable unread/attention indicator on its rail square (and in the condensed dropdown), with the counts in the accessible name. The summary deri… |
| `src/app/chat/sidebar/profile-remote-override-dialog.test.tsx` | The rail affordance that writes connection.json `profiles.<name>` through the typed Electron bridge (#91349): the renderer must never touch the file itself, the token must ride the safeStorage path (applyConnectionConfi… |
| `src/app/chat/sidebar/profile-remote-override-dialog.tsx` | Exports `ProfileRemoteOverrideDialog` |
| `src/app/chat/sidebar/profile-scope.test.ts` | Build the smallest session row needed by the profile-scope tests. |
| `src/app/chat/sidebar/profile-scope.ts` | Sessions visible in one sidebar profile scope. ALL (`__all__`) returns the caller's list unchanged — including the single-profile case, where Grouping → Profile persists that sentinel while grouped rendering stays off.… |
| `src/app/chat/sidebar/profile-switcher.tsx` | Exports `ProfileRail` |
| `src/app/chat/sidebar/project-dialog.test.tsx` | Tests: ProjectDialog; creates from the folder basename and enters the created project when the name is empty; keeps an explicit project name when a folder is selected; forwards an armed drag placement to createProject o… |
| `src/app/chat/sidebar/project-dialog.tsx` | Exports `ProjectDialog` |
| `src/app/chat/sidebar/project-filter.test.ts` | Tests: resolveLiveProjectFilter; returns the filter unchanged when it is empty; keeps ids the active tree resolves; drops ids that only resolve in another profile (#96246) |
| `src/app/chat/sidebar/project-filter.ts` | Narrow the persisted sidebar project filter to ids the ACTIVE tree resolves. The filter's storage is shared across profiles and outlives project deletes/rebuilds, so ids that resolve nowhere must be inert, not fatal (#9… |
| `src/app/chat/sidebar/projects/base-branch-picker.test.tsx` | Tests: BaseBranchPicker loading; a list from the previous repo does not set the base of the next; WorktreeDialog base branch; cuts the worktree from the base the caller chose |
| `src/app/chat/sidebar/projects/base-branch-picker.tsx` | Exports `BaseBranchPicker` |
| `src/app/chat/sidebar/projects/entered-content.tsx` | Exports `EnteredProjectContent` |
| `src/app/chat/sidebar/projects/index.ts` | Public surface of the project/worktree sidebar, consumed by the sidebar root. |
| `src/app/chat/sidebar/projects/model.test.ts` | Tests: orderProjectsByIds; leaves the deterministic sort alone when nothing has been dragged; applies the saved manual order; keeps freshly-scanned zero-session repos below the hand-ordered list |
| `src/app/chat/sidebar/projects/model.ts` | Page size when revealing more already-loaded rows within a workspace group. |
| `src/app/chat/sidebar/projects/overview-row.test.tsx` | Tests: ProjectOverviewRow; does not render the disclosure toggle when there is nothing to preview; offers ; pages a large hydrated project instead of mounting every session at once |
| `src/app/chat/sidebar/projects/overview-row.tsx` | Exports `projectIcon`, `ProjectBackRow`, `ProjectOverviewRow` |
| `src/app/chat/sidebar/projects/project-appearance.tsx` | Curated codicons for a project glyph (tinted by the chosen color). Shared by the kebab's Appearance popover and the right-click menu's Appearance submenu so both offer the same picker. |
| `src/app/chat/sidebar/projects/project-menu.test.tsx` | Tests: ProjectMenu; opens the appearance popover through the kebab trigger when anchorRef is absent; hides an auto project with an Undo toast that restores it |
| `src/app/chat/sidebar/projects/project-menu.tsx` | Exports `ProjectMenu`, `ProjectContextMenu` |
| `src/app/chat/sidebar/projects/workspace-group.tsx` | Exports `SidebarWorkspaceGroup` |
| `src/app/chat/sidebar/projects/workspace-groups.test.ts` | Tests: baseName; returns the final path segment, ignoring trailing slashes and separators; laneSwitchTarget (#108694); skips the synthetic main fallback on a repo whose trunk is master |
| `src/app/chat/sidebar/projects/workspace-groups.ts` | Session grouping is now computed authoritatively on the backend (`tui_gateway/project_tree.py`, exposed via `projects.tree` / `projects.project_sessions`). The desktop is a thin renderer: this module |
| `src/app/chat/sidebar/projects/workspace-header.test.tsx` | Tests: WorkspaceAddButton; still fires onClick |
| `src/app/chat/sidebar/projects/workspace-header.tsx` | Exports `WorkspaceAddButton`, `WorkspaceShowMoreRow`, `WorkspaceShowMoreButton`, `WorkspaceMenu`, `WorkspaceContextMenu`, `StartWorkButton` … |
| `src/app/chat/sidebar/projects/worktree-dialog.tsx` | Exports `WorktreeDialog` |
| `src/app/chat/sidebar/reorderable-list.tsx` | Sidebar reordering is a strictly vertical list. The dragged item's transform is rendered Y-only in useSortableBindings (no x, no scale); this just stops dnd-kit's auto-scroll from dragging the rail — or the window — sid… |
| `src/app/chat/sidebar/row-geometry.ts` | The sidebar row's measurements, in one place. The session row is canonical and everything else composes these — a row that spells its own geometry floats 1–2px off the sessions above it, which is how the drift starts. |
| `src/app/chat/sidebar/search-result-to-session.test.ts` | Regression (#91068): the backend's /api/sessions/search payload carries the real session title on every hit (web_routers/sessions.py add_lineage_result enriches via get_session_rich_row), but the sidebar's search mapper… |
| `src/app/chat/sidebar/search-results-order.test.ts` | Regression: pasting a session's exact id into the sidebar search buried the id's own row under recency-sorted client matches. Cross-reference workflows open sessions with a pointer line quoting another session's id, and… |
| `src/app/chat/sidebar/section-states.tsx` | Stands in for session rows, so it borrows their chrome instead of copying the grid — a placeholder on a different edge than the rows it resolves into makes the list step sideways on load. |
| `src/app/chat/sidebar/session-actions-menu.test.ts` | The branched-session rename bug: a freshly branched session lives only in the gateway's runtime _sessions map (no state.db row yet), so REST PATCH /api/sessions/{id} 404s with "Session not found". renameSessionPreferrin… |
| `src/app/chat/sidebar/session-actions-menu.test.tsx` | Tests: SessionActionsMenu; opens the dropdown on click; opens the rename dialog focused on its input, not the row trigger; passes profile to renameSession when submitting from RenameSessionDialog |
| `src/app/chat/sidebar/session-actions-menu.tsx` | Exports `renameSessionPreferringRpc`, `SessionActionsMenu`, `SessionContextMenu` |
| `src/app/chat/sidebar/session-index.test.ts` | Tests: buildSessionByAnyId; resolves a pin from every slice the sidebar fetches; resolves a pin stored on the pre-compression lineage root; lets a recents row win a direct id collision |
| `src/app/chat/sidebar/session-index.ts` | Index sessions by every id a pin might be stored under. The sidebar fetches three independent slices — recents, cron, and messaging — and renders the latter two in self-managed sections. Any of them can be pinned, so al… |
| `src/app/chat/sidebar/session-row-actions.test.tsx` | Tests: SidebarSessionRow actions; archives an Inbox card without also resuming it (#85163) |
| `src/app/chat/sidebar/session-row-details.test.ts` | Tests: session row details; formats deterministic metadata without ambiguous call wording; uses singular labels and omits unavailable fields; omits zero counts from metadata so the sidebar stays clean |
| `src/app/chat/sidebar/session-row-details.ts` | Exports `SessionRowDetails`, `SessionRowFormatters`, `sessionRowEstimate`, `SESSION_CARD_ROW_ESTIMATE_PX`, `sessionRowDetails` |
| `src/app/chat/sidebar/session-row-gesture.test.ts` | Tests: resolveSessionRowClick; resumes on a plain click; pins on ⇧-click; opens a new tab on ⌘/⌃-click |
| `src/app/chat/sidebar/session-row-gesture.ts` | Which action a left-click on a sidebar session row triggers, given the modifier keys held. Kept as a pure resolver (separate from the row component) so the precedence — the part that's easy to get subtly wrong — |
| `src/app/chat/sidebar/session-row-rename-drag.test.tsx` | Tests: SidebarSessionRow drag and the rename dialog (portal press); ignores the dialog; still lifts the row from a press on its own body |
| `src/app/chat/sidebar/session-row-slots.tsx` | One row-decoration slot (leading / trailing) for `sessionId`. Mounts every registration and lets each decide — it renders its decoration, or nothing at all for rows it doesn't own. Mounting all of them (rather than firs… |
| `src/app/chat/sidebar/session-row.test.tsx` | Tests: SidebarSessionRow running arc; paints no arc for a settled session; paints the arc while the session is running; SidebarSessionRow |
| `src/app/chat/sidebar/session-row.tsx` | Exports `SidebarSessionRow` |
| `src/app/chat/sidebar/sessions-section-new-session-drag.test.tsx` | Tests: Show all sessions; keeps the five-session page by default and renders every loaded workspace session when enabled; does not cap expanded project previews at two date groups; entered project reaches every session |
| `src/app/chat/sidebar/sessions-section.tsx` | Exports `VIRTUALIZE_THRESHOLD`, `SidebarSessionsSection` |
| `src/app/chat/sidebar/split-submenu.tsx` | Exports `SplitMenuKit`, `DROPDOWN_SPLIT_KIT`, `CONTEXT_SPLIT_KIT`, `SplitSubmenu` |
| `src/app/chat/sidebar/storage-corrupt-notice.test.tsx` | Tests: SidebarStorageCorruptNotice; renders nothing while every store is healthy; names the damaged profile and gives the non-destructive recovery path; keeps atom identity when a refresh reports the same stores |
| `src/app/chat/sidebar/strip-fts-markers.test.ts` | Regression: the backend's session-search FTS layer wraps matched terms in literal '>>>' / '<<<' snippet() delimiters (hermes_state_search.py). The sidebar paints the snippet as plain text, so an unstripped marker renders |
| `src/app/chat/sidebar/unserved-profiles.tsx` | Exports `useUnservedProfiles`, `ProfileRowGlyph`, `UnservedProfileNote` |
| `src/app/chat/sidebar/use-entered-project-sessions.test.ts` | Tests: refetches only when the entered project changes, and keeps an unchanged result; ignores departed drill-ins and clears failure on retry |
| `src/app/chat/sidebar/use-entered-project-sessions.ts` | The mounted drill-in owns its outcome. A global error flag lets a departed project's slow failure overwrite the next project's successful load. |
| `src/app/chat/sidebar/use-fleet-roster.test.tsx` | Tests: re-enumerates a roster that timed out while the local gateway was still booting |
| `src/app/chat/sidebar/use-fleet-roster.ts` | Keep the fleet roster fresh for the profile rail while more than one gateway is registered: pull on mount, when the window regains focus or visibility, immediately when the connection registry changes, and when the gate… |
| `src/app/chat/sidebar/use-profile-prewarm.test.ts` | Tests: useProfilePrewarm (#100548 layout-only pointerenter); does not spawn on pointerenter without a real pointer move (layout shift under a stationary cursor); still prewarms after enter + pointer move + dwell (genuin… |
| `src/app/chat/sidebar/use-profile-prewarm.ts` | Dwell before firing: long enough that sweeping the pointer across the rail or a mixed-profile session list doesn't spawn a backend for every element passed through, short enough to beat the click by hundreds of ms. |
| `src/app/chat/sidebar/use-profile-rail-refresh-on-active.test.ts` | Tests: useProfileRailRefreshOnActive; refreshes once on mount; refreshes again when the window regains focus; refreshes when visibilitychange fires while the document is visible |
| `src/app/chat/sidebar/use-profile-rail-refresh-on-active.ts` | Re-pull the running profile + list on mount, and again whenever the window regains focus/visibility -- a profile created, deleted, or renamed by another surface (Manage Profiles, another window, the CLI) leaves the rail… |
| `src/app/chat/sidebar/use-server-session-search.ts` | Exports `ServerSessionSearch`, `useServerSessionSearch` |
| `src/app/chat/sidebar/virtual-session-list.test.tsx` | The virtualizer is mocked with a STABLE instance (the real hook returns one), so the component's measure() effect fires exactly when its deps change — which is the behavior under test: `card` must invalidate cached |
| `src/app/chat/sidebar/virtual-session-list.tsx` | Exports `VirtualSessionListProps`, `VirtualSessionList` |
| `src/app/chat/surface-vars.test.ts` | Regression: the thread's bottom gap going randomly huge and staying huge. `--thread-last-message-clearance` is `composer + status-stack + 2rem`, and both inputs are published by JS onto the owning `[data-chat-surface]`.… |
| `src/app/chat/surface-vars.ts` | Measured-height CSS vars, scoped to one chat surface. The composer and the out-of-flow status stack both publish their measured height so the thread can reserve bottom clearance for them. Those vars used to be written t… |
| `src/app/chat/thread-loading.test.ts` | Tests: thread loading state; returns session when routed session is still hydrating; returns response while awaiting an assistant reply to the last visible user message; does not show response loading when the last visi… |
| `src/app/chat/thread-loading.ts` | Exports `ThreadLoadingState`, `lastVisibleMessageIsUser`, `threadLoadingState`, `composerStaysMounted`, `routedSessionIsLoading` |
| `src/app/chat/tile-zone-host.ts` | Zone eligibility for SESSION drops — the resolve-side half of the drop contract shared with the zone overlay (hostsSessionDropTarget in pane-shell/tree/store decides PAINT; this decides COMMIT). Living apart from either… |
| `src/app/chat/tour-marker.ts` | `data-tour` handles for the chat surfaces — on the primary one only. A handle has to be UNIQUE in the document. The composer and the model pill are not: side-by-side session tiles mount the same ChatView tree, so a mark… |
| `src/app/chat/transcript-backfill.test.ts` | Tests: transcript tail bookkeeping; marks a full page as possibly truncated with the next offset; marks a short page as complete; treats a legacy response without pagination metadata as complete |
| `src/app/chat/transcript-backfill.tool-fold-graft.test.ts` | A refresh reads only the newest page of a long session, and that page can begin mid tool batch. `toChatMessages` flushes such a batch as a synthetic assistant message whose id is not durable, so the page's first rendere… |
| `src/app/chat/transcript-backfill.ts` | ON-DEMAND OLDER-PAGE BACKFILL for the transcript window. Tail hydration (`getLatestSessionMessages`) loads only the newest page of a session. "Show earlier" first pages the DOM budget, then the in-memory store window —… |
| `src/app/chat/transcript-fold-identity.test.ts` | Tests: keeps a cached fold when the fresh page represents only part of its sources; keeps unstored leading rows before the replacement fold |
| `src/app/chat/transcript-receipt-turns.local-rows.test.ts` | Tests: local notices inside a steered turn; stay inside their own turn when a later turn whose prompt only the page holds follows it; stay in front of a steer prompt the window drew before its row was written |
| `src/app/chat/transcript-receipt-turns.test.ts` | A long chat's newest page begins inside an older tool turn, so the refresh graft pairs rows by stored id. The turn that just ran was drawn live and carries stored ids on some rows at most. The page holds every stored ro… |
| `src/app/chat/transcript-receipt-turns.ts` | A refreshed page that holds a whole turn the window drew live supersedes the window's copy of that turn, decided by the turn's completion receipt. The stored-id merge (transcript-backfill `mergeOverlappingTail`) pairs r… |
| `src/app/chat/transcript-retention.test.ts` | Tests: boundRetainedTranscript; releases the persisted rows older than the window and its slack; keeps a fixed amount of history behind the window, however long the session is; leaves the transcript whole when a release… |
| `src/app/chat/transcript-retention.ts` | BOUND THE RETAINED TRANSCRIPT — release paged-through history from the store. `transcript-window` bounds what REACHES assistant-ui, but the session store underneath it keeps every message it ever materialized: the tail… |
| `src/app/chat/transcript-window-retention.test.ts` | Tests: session transcript-window retention; weakly remembers a windowed source array without breaking warm slice reuse; does not memoize an unwindowed source array that would remain strongly retained; drops an old windo… |
| `src/app/chat/transcript-window.test.ts` | Tests: selectTranscriptWindow; does not window a transcript that fits the budget; windows a HEAVY-but-SHORT transcript that a message-count cap would miss; keeps far MORE messages when they are light than when they are… |
| `src/app/chat/transcript-window.ts` | Bound what reaches assistant-ui at all. Rendering the full transcript of an oversized session rebuilds an unbounded runtime repository on every store update and exhausts the renderer's V8 heap (#55191). The DOM budget i… |
| `src/app/chat/use-chat-bar-state.ts` | Exports `useChatBarState` |
| `src/app/chat/use-transcript-retention.test.tsx` | Tests: useTranscriptRetention — the store releases paged-through history; drops the rows older than the live window, then fetches them back on ; leaves a transcript that fits its window alone; does not release anything… |
| `src/app/chat/use-transcript-retention.ts` | Exports `useTranscriptRetention` |
| `src/app/command-center/delete-confirm.test.tsx` | #99410: the Command Center → Sessions trash button hard-deleted the session (row + messages + request_dump files) instantly, with no confirmation — e6708af1f (#61470) guarded the sidebar/tab/header entry points via |
| `src/app/command-center/index.tsx` | Exports `CommandCenterSection`, `CommandCenterView` |
| `src/app/command-center/maintenance.test.tsx` | The backend spawns each op under one fixed action name ('doctor', 'security-audit', 'backup', 'curator-run'), a re-spawn replaces the record under that name, and /api/actions/<name>/status reports the latest run. The fa… |
| `src/app/command-center/maintenance.tsx` | Exports `MaintenancePanel` |
| `src/app/command-center/open-session.test.tsx` | Tests: Command Center session open carries the row; passes the clicked ROW to onOpenSession, not a bare id |
| `src/app/command-palette/contrib.ts` | Command-palette contribution surface — `palette` data contributions become rows in the ⌘K root list, same schema as every other area. Contributions with an `action` id render that action's live keybind as their hotkey h… |
| `src/app/command-palette/highlight-watcher.test.tsx` | The regression that motivates this file: cmdk calls the root `onValueChange` only in controlled mode (a set `value` prop). The palette is uncontrolled, so a highlight preview wired to that prop never fires. The watcher… |
| `src/app/command-palette/highlight-watcher.tsx` | Reports the cmdk highlight to the palette. cmdk calls the root `onValueChange` only in controlled mode (when the `value` prop is set). This palette is uncontrolled, so that prop never fires. This watcher subscribes to t… |
| `src/app/command-palette/index.tsx` | Exports `CommandPalette` |
| `src/app/command-palette/marketplace-theme-page.tsx` | Cmd-K "Install theme…" page. Browses the VS Code Marketplace for color themes: an empty query shows the most-installed themes, typing runs a live (debounced) search against the Marketplace. Selecting a row downloads + c… |
| `src/app/command-palette/pet-palette-page.tsx` | Cmd-K "Pets…" page — browse the petdex gallery, adopt/switch, toggle off. A thin view over the `pet-gallery` store: it subscribes to the shared atoms and calls the store's actions. The store owns fetching, caching, the… |
| `src/app/command-palette/status-row.tsx` | Centered loading / empty / error row for a Cmd-K page's result list. |
| `src/app/context-menu/app-context-menu.test.tsx` | Tests: resolveDomTarget; resolves an anchor and its href; ignores hash-only placeholder anchors; resolves an image, and the anchor wrapping it |
| `src/app/context-menu/app-context-menu.tsx` | Exports `CONTEXT_MENU_SKIP_ATTR`, `AppContextMenu` |
| `src/app/context-menu/composer-menu.test.tsx` | Tests: composer context-menu contribution area; offers plugin items on the composer and never on any other editable; keeps plugin rows in the browser Webapp, without the edit verbs it cannot run; hands a provider only t… |
| `src/app/context-menu/composer-menu.ts` | The composer's context-menu contribution area, app side. Plugins contribute DATA (`composer.contextMenu` → `ComposerContextMenuProvider`); the app owns everything else: it decides the click landed on a composer, capture… |
| `src/app/context-menu/pane-context-menu.test.tsx` | Tests: the pane fallback serves clicked content without taking explicit or unrelated menus |
| `src/app/context-menu/shell-menu-items.tsx` | Bare right-click on app chrome: the window verbs (the old shell fallback). |
| `src/app/context-menu/store.ts` | Spell-check facts for the open editable menu. They arrive AFTER the menu opens: Chromium reports them on the main-process `context-menu` event, which fires after the DOM gesture that opened the menu. |
| `src/app/context-menu/target.ts` | What a right-click landed on, resolved from the DOM. One resolver so every surface agrees on ownership. Order encodes priority: an editable wins over the link wrapping it (the caret is where the user is working), a link… |
| `src/app/contrib/context.tsx` | The controller publishes its wired surfaces here; every registered pane / chrome slot reads one back through `WiredPane`. |
| `src/app/contrib/controller.tsx` | Exports `ContribController` |
| `src/app/contrib/dev/credits-notice-demo.ts` | Dev-only: drive the credit-notice UX without a backend that can hit real usage bands. Each trigger emits ONE synthetic `notification.show` / `notification.clear` gateway event through the real fan-out |
| `src/app/contrib/hooks/completed-reply-refresh.test.tsx` | Tests: keeps an idle Todo snapshot for review when post-turn history refresh clears the live panel; retries an interrupted reconnect read once on idle, even before that read returns; rejects a read when an existing row… |
| `src/app/contrib/hooks/desktop-onboarding-metrics.test.ts` | Tests: sign-in funnel from the offer; an offer the user signs in from and then cancels is a reach followed by a cancel |
| `src/app/contrib/hooks/desktop-onboarding-metrics.ts` | First-run funnel telemetry (hermes.desktop.onboarding). Observes the onboarding stores' own transitions — the provider picker, first-run onboarding, free-tier sign-in — and maps them onto the closed step set; nothing he… |
| `src/app/contrib/hooks/folded-tool-turn-refresh.test.tsx` | Tests: keeps the settled live reply when the fold lacks one of its tool rounds |
| `src/app/contrib/hooks/live-status-reap.test.ts` | Tests: rehydrateLiveSessionStatuses — reaping vanished runtimes; clears a working session that disappears from the live snapshot; fires the unread ; stays dark for a messaging turn that settles before its messaging row… |
| `src/app/contrib/hooks/live-status-spinner.test.ts` | Tests: rehydrateLiveSessionStatuses — seeding a turn the renderer never saw start; shows the spinner for a turn that started with no stream events; keeps the spinner across polls while the turn is still running; ignores… |
| `src/app/contrib/hooks/notification-focus.test.tsx` | Tests: a native click reveals the existing remote Bot tab without changing its owner or duplicating main |
| `src/app/contrib/hooks/remembered-session.test.ts` | Tests: resolveRememberedSessionId; repairs a remembered delegate child to its parent; clears an orphaned delegate child instead of reopening it; keeps normal sessions |
| `src/app/contrib/hooks/remembered-session.ts` | Returns the session safe to remember/restore: a delegate child (`source === 'subagent'`) is replaced by its parent, everything else keeps its own id. Delegate children are deliberately omitted from the sidebar list (`_L… |
| `src/app/contrib/hooks/restore-late-plugin-route.test.tsx` | Remembered-route restore vs late disk plugins. A remembered plugin page is session-shaped until its route registers; if the session list arrives first (an already-running backend), the restore used to classify it as a s… |
| `src/app/contrib/hooks/use-background-sync.stopped-turn.test.ts` | Tests: a page read right after Stop; draws the stopped turn once when the page lands before the interrupted completion (#144899 N2) |
| `src/app/contrib/hooks/use-background-sync.test.ts` | Tests: resolveActiveTranscriptSession; uses a unique hidden owner hint for hydration and refresh scope; does not promote a different runtime tile into the active transcript owner; does not treat an ownerless active tile… |
| `src/app/contrib/hooks/use-background-sync.test.tsx` | Tests: useBackgroundSync profile-scoped session refresh; coalesces change ticks while the live status request is pending; refreshes the session list after the active gateway profile changes; refreshes the session list w… |
| `src/app/contrib/hooks/use-background-sync.ts` | Exports `profileScopeForTranscriptSession`, `resolveActiveTranscriptSession`, `ActiveTranscriptRefreshDeps`, `stopAwaitsItsReceipt`, `reconcileTileTranscripts`, `hydrateStoredSessionTranscript` … |
| `src/app/contrib/hooks/use-desktop-integrations.test.tsx` | Tests: useDesktopIntegrations; profile-ready gate; does NOT restore before profileReady is true; restores on profileReady when remembered route exists and owns the session |
| `src/app/contrib/hooks/use-desktop-integrations.ts` | Exports `useDesktopIntegrations` |
| `src/app/contrib/hooks/use-desktop-metrics.ts` | Wires Desktop love/hate telemetry (store/desktop-metrics.ts) to the app's existing state: the focused gateway + its collection switch, routes, open overlays, workspace mode, user interaction, long frames and the profile… |
| `src/app/contrib/hooks/use-pet-bridge.test.ts` | Tests: syncPetBusyFromSessions; marks the pet busy while any session is working, foreground or not; clears busy and returns to idle once every session is at rest; stays busy when only one of several sessions finishes |
| `src/app/contrib/hooks/use-pet-bridge.ts` | Mirror "any open session is running the agent" into the pet's `busy` flag. `toolRunning` / `reasoning` are set only inside the per-session message-stream hook (`use-message-stream/gateway-event.ts`), which is mounted fo… |
| `src/app/contrib/hooks/use-quick-entry-bridge.test.ts` | Tests: quickEntrySubmitAck; reports a rejected prompt as failure instead of acknowledging success; names the accepted identity on an accepted ack; useQuickEntryBridge |
| `src/app/contrib/hooks/use-quick-entry-bridge.ts` | Exports `quickEntrySubmitAck`, `useQuickEntryBridge` |
| `src/app/contrib/hooks/use-session-tile-delegate.test.ts` | Tests: useSessionTileDelegate resumeTile; carries the owning profile into a cold tile resume so it cannot fork profiles; resolves and carries a default-profile session explicitly; carries a session row connection owner… |
| `src/app/contrib/hooks/use-session-tile-delegate.ts` | Exports `useSessionTileDelegate` |
| `src/app/contrib/index.ts` | The contribution-driven shell package. `controller` registers panes / layouts / chrome and mounts the app root; `wiring` is the data controller + memoized pane surfaces; `panes` holds the real-data pane bodies + statusb… |
| `src/app/contrib/latest-actions.test.ts` | Tests: latestActions adapters; forwards every present handler — an optional one the adapter forgets never reaches ChatView; dereferences the latest steer handler from a stable actions object; dereferences the latest sid… |
| `src/app/contrib/latest-actions.ts` | Surfaces receive one stable `actions` object whose fields are mutated by the wiring controller each render. If a memoized surface passes `actions.foo` directly, the child keeps the function from the surface's last rende… |
| `src/app/contrib/layout-presets.ts` | --------------------------------------------------------------------------- Layout presets — CHAT (main) always dominates. --------------------------------------------------------------------------- |
| `src/app/contrib/layout-sides.ts` | Side toggles belong to panes, not physical edges. Derive the flip from the tree so dragging sessions or choosing a mirrored preset remaps the buttons. |
| `src/app/contrib/mcp-install-deeplink-dialog.tsx` | Exports `McpInstallDeepLinkDialog` |
| `src/app/contrib/panes.logs.test.tsx` | The pane refetches its tail on an interval; the autoscroll contract (#77794) is that refetched data scrolls to the bottom ONLY while the user is already at the bottom — a deliberate scroll-up must not be yanked back dow… |
| `src/app/contrib/panes.test.tsx` | Registrations are global (module-level registry); each test captures its own disposer and this undoes it, so tests don't bleed into each other. |
| `src/app/contrib/panes.tsx` | Real-data panes + composable bar items for the contrib root: - `PreviewRailPane` — the REAL ChatPreviewRail; files-pane clicks feed it. - `FilesPane` — real file browser; activating a file opens it in preview. - Core st… |
| `src/app/contrib/plugin-preview-consent-dialog.test.tsx` | @vitest-environment jsdom |
| `src/app/contrib/plugin-preview-consent-dialog.tsx` | Exports `PluginPreviewConsentDialog` |
| `src/app/contrib/session-rpc-dispatcher.test.ts` | Fail-closed owner resolution for the window's ONE session-scoped RPC dispatcher. A request that names a session whose owner NO rung can name (tile route → exact hint → connection-tagged / profiled row → REST probe) |
| `src/app/contrib/session-rpc-dispatcher.ts` | The window's ONE session-scoped RPC dispatcher, factored out of the contrib wiring controller so the exact production routing (not a re-implementation) can be driven by integration tests alongside the real session/promp… |
| `src/app/contrib/sessions-pane-tab-title.test.tsx` | The Sessions sidebar pane registers at module import, before `I18nProvider` has fetched `display.language`, so its string `title` is whatever English `translateNow` sampled then. The strip label must come from `tabTitle… |
| `src/app/contrib/surfaces.app-routes.test.tsx` | Tests: ChatRoutesSurface and APP_ROUTES |
| `src/app/contrib/surfaces.late-routes.test.tsx` | A plugin page route registered AFTER the workspace surface mounts must become navigable. Regression for late-loaded desktop plugins (disk plugins load async): the route table was compiled into a memo slot keyed on unrel… |
| `src/app/contrib/surfaces.test.tsx` | Tests: ChatRoutesSurface; passes the live gateway after an open-to-open profile switch |
| `src/app/contrib/surfaces.tsx` | Wiring surfaces — each pane is its own memoized component. Every surface reads the reactive state it renders from at the leaf (its own atom subscriptions) and reaches the controller's callbacks through the stable `actio… |
| `src/app/contrib/types.ts` | Exports `GatewayRequester`, `SidebarActions`, `ChatActions`, `WiringActions`, `WiringApi` |
| `src/app/contrib/wiring-background-queue-drain.test.tsx` | Tests: ContribWiring background queue: independent remote owner |
| `src/app/contrib/wiring-effects.ts` | Exports `useOpenKeybindsListener`, `useCreditsNoticeDemo`, `usePublishRestartPreviewServer`, `useFreshSessionRequest`, `useGatewayScopeRefresh` |
| `src/app/contrib/wiring-routing.test.ts` | Tests: findStoredIdForRuntimeId; reverse-resolves a runtime id to its stored id; returns undefined for an unknown runtime id; resolveRoutingSessionId |
| `src/app/contrib/wiring-routing.ts` | Pure routing helpers for the contrib wiring controller. Kept out of wiring.tsx so they can be unit-tested without importing the whole React/Electron controller module. |
| `src/app/contrib/wiring.tsx` | Real-featureset wiring for the contrib (layout tree) root — the minimal subset of DesktopController's hook chain that makes the REAL surfaces work: gateway boot -> sessions list -> click-to-resume -> live transcript ->… |
| `src/app/contrib/workspace-page-header.test.tsx` | The workspace pane is the one host whose zone paints the page header (#123597). These read the REAL `workspace` contribution registered by the controller, render it through the real tree renderer, and check that a `Work… |
| `src/app/contrib/workspace-page-header.tsx` | Page-owned header controls (#123597). A page route can render in the workspace pane, whose zone paints `WORKSPACE_PAGE_HEADER_AREA` as the page header, or in a route tile, where nothing reads that area. The control asks… |
| `src/app/cron/blueprints.test.ts` | Tests: initialBlueprintValues; seeds each field from its default; falls back to an empty string when a field has no default; returns an empty object for a blueprint with no fields |
| `src/app/cron/blueprints.tsx` | The blueprint catalog is shared with the dashboard, so its deliver slot defaults to "origin" (the chat/home-channel a dashboard or gateway job was created from). Desktop has no origin chat, so seed the deliver slot to t… |
| `src/app/cron/cron-actions.test.ts` | Tests: triggerAndRefreshCronJobs; replaces the local cache with the authoritative list after a trigger; reports refresh failure separately after a successful trigger; still rejects when the trigger itself fails |
| `src/app/cron/cron-actions.ts` | Exports `CronTriggerRefreshResult`, `CronMutationRefreshResult`, `refreshCronJobs`, `mutateAndRefreshCronJobs`, `triggerAndRefreshCronJobs` |
| `src/app/cron/cron-job-model.test.ts` | Tests: cron model choice values; round-trips provider and model colons without ambiguous pairs; jobIsScriptOnly; is true when no_agent is set and a script is present |
| `src/app/cron/cron-job-model.ts` | Exports `jobIsScriptOnly`, `jobDescription`, `CronEditorValidationError`, `CronEditorValidationInput`, `validateCronEditor`, `CronEditorSaveValues` … |
| `src/app/cron/deliver-checkboxes.test.tsx` | Tests: DeliverCheckboxes accessible name; exposes the Field label as the group name |
| `src/app/cron/index.test.tsx` | @vitest-environment jsdom |
| `src/app/cron/index.tsx` | Exports `CronView`, `DeliverCheckboxes` |
| `src/app/cron/job-state.test.ts` | Tests: truncateText; truncates on Unicode code-point boundaries; does not add an ellipsis at the limit; never cuts a grapheme cluster mid-sequence |
| `src/app/cron/job-state.ts` | Status-pip color per cron job state. Single source for the sidebar section and the Cron page so the two never drift. (Animation/size live at the call site.) |
| `src/app/cron/open-cron-run.test.ts` | Tests: isResumableCronRun; keeps a scheduler-owned run live through a long tool call past the activity window; treats a never-closed run the scheduler does not own as a zombie, even if it ticked recently; treats a prope… |
| `src/app/cron/open-cron-run.ts` | Exports `isResumableCronRun`, `isCronRunRow`, `isCronRunSession`, `cronRunWriteGateApplies`, `openCronRun`, `reconcileCronRunVerdicts` … |
| `src/app/cron/plugin-blueprints.test.tsx` | Tests: plugin-registered automation blueprints; lists the plugin blueprint with its plugin label and instantiates it into the scoped profile |
| `src/app/floating-hud.ts` | Shared chrome for the top-center floating HUDs (command palette + session switcher). They pin just under the title bar, centered, and lean on a crisp border + shadow to separate from the app — no dimming/blurring backdr… |
| `src/app/gateway/gateway-event-dedupe.test.ts` | Tests: gateway event dedupe (#120005); admits a frame once even when a second socket to the same backend delivers it again; accepts a re-numbered session after the window, and always passes seq-less events |
| `src/app/gateway/gateway-event-dedupe.ts` | Cross-socket duplicate gate for backend events (#120005 / #120007). The backend joins EVERY socket that sends a session call to that chat's transport fan-out (`tui_gateway/session_transports.py`, intended: shared chats… |
| `src/app/gateway/hooks/canonical-owner-routing.test.tsx` | Tests: keeps canonical alpha events and questions on alpha while beta is foreground |
| `src/app/gateway/hooks/gateway-hmr-survivor.test.ts` | Tests: gateway HMR survivor cache; is single-shot — a second take returns null; persists across re-imports via the globalThis slot; treats open / connecting sockets as adoptable |
| `src/app/gateway/hooks/gateway-hmr-survivor.ts` | Keep the live primary gateway socket alive across Vite HMR so editing UI never drops the agent session. Stash on dispose, re-adopt on remount. globalThis + self-accept so this module's own reload doesn't reset the cache… |
| `src/app/gateway/hooks/primary-reauth-notice.test.ts` | Tests: leaves a signed-out Webapp tab to its sign-in view, with no toast; hands a foreground sign-in to the boot overlay with the error current at the click; offers Gateways settings to a parked background primary, what… |
| `src/app/gateway/hooks/primary-reauth-notice.ts` | Plain "signed out" copy for a reconnect that needs a new sign-in; the raw ticket/HTTP text stays under Details. In the foreground the boot overlay carries the sign-in flow, so the button hands off to it (desktop-14), an… |
| `src/app/gateway/hooks/use-connections-registry.test.tsx` | Tests: window-owned connection registry; waits for primary boot fetches before restoring the launch source; bounds failed reads and recovers on focus without polling a healthy registry |
| `src/app/gateway/hooks/use-connections-registry.ts` | Exports `useConnectionsRegistry` |
| `src/app/gateway/hooks/use-default-profile-preference.ts` | Exports `useDefaultProfilePreference` |
| `src/app/gateway/hooks/use-gateway-boot-initial-connect.test.ts` | Tests: connectInitialGateway (initial-boot dial retry, #49645); retries past transient transport failures and resolves once a connect succeeds; throws the last error after exhausting all attempts; fails fast on reauth e… |
| `src/app/gateway/hooks/use-gateway-boot-profile-pick.test.tsx` | The blocked update-hold screen's renderer leg (R8 D3/M6): a hold the main process publishes on boot progress lands in $desktopBoot even after boot. Shares the fake socket with use-gateway-boot.test.tsx; the desktop brid… |
| `src/app/gateway/hooks/use-gateway-boot-update-hold.test.tsx` | The blocked update-hold screen's renderer leg (R8 D3/M6): a hold the main process publishes on boot progress lands in $desktopBoot even after boot. Shares the fake socket with use-gateway-boot.test.tsx; the desktop brid… |
| `src/app/gateway/hooks/use-gateway-boot-webapp-profile.test.tsx` | A Webapp tab has one socket, and the serving gateway answers it for the profile it was launched as whenever a request names no profile, exactly as its REST does. A tab loaded or reloaded on `?profile=<name>` (or opened… |
| `src/app/gateway/hooks/use-gateway-boot.test.tsx` | Tests: primaryRuntimeConnectionId; uses the registry identity when the primary connection has one; uses the stable local identity for an app-managed backend; returns null for an unknown remote identity so the caller fal… |
| `src/app/gateway/hooks/use-gateway-boot.ts` | Exports `primaryRuntimeConnectionId`, `connectInitialGateway`, `useGatewayBoot` |
| `src/app/gateway/hooks/use-gateway-request.test.ts` | Tests: useGatewayRequest; exposes the live gateway on the first render, before effects run; tracks the gateway when the active socket changes; recovers when the gateway ref is stale but the active gateway is still open |
| `src/app/gateway/hooks/use-gateway-request.ts` | Exports `useGatewayRequest` |
| `src/app/gateway/report-startup-latency.test.ts` | Tests: reportStartupLatency; sends the metric once even when the renderer boots again (reload, reconnect, extra window); skips the metric on an Electron shell without the claim bridge |
| `src/app/gateway/report-startup-latency.ts` | Exports `reportStartupLatency` |
| `src/app/hooks/use-config-record.test.tsx` | Tests: updates the write origin when a refetch replaces the displayed record; does not share one config record across two gateways; a settings cache write after switching gateways does not replace the other gateway reco… |
| `src/app/hooks/use-config-record.ts` | Exports `HERMES_CONFIG_KEY`, `hermesConfigKey`, `useHermesConfigRecord`, `setHermesConfigCache`, `hermesConfigCacheWriter`, `invalidateHermesConfig` |
| `src/app/hooks/use-debounced.ts` | Debounce a fast-changing value (search input, slider, …) so effects/queries keyed on it only fire once the value settles. |
| `src/app/hooks/use-keybinds-browser.test.tsx` | Tests: dispatches the Alt defaults and remaps from text fields, leaving browser keys and AltGr alone; dispatches the macOS ⌃⌘ browser defaults, including ⌃⌘W over an interactive terminal; keeps an Option remap on macOS,… |
| `src/app/hooks/use-keybinds-close-tab.test.tsx` | Tests: close-tab chord over a focused terminal; leaves the default chord to an interactive terminal (word erase); keeps close-tab for a read-only agent terminal; keeps Ctrl/Cmd+Shift+W as the explicit close chord |
| `src/app/hooks/use-keybinds-right-side.test.ts` | Tests: ⌘J (view.toggleRightSidebar); folds a Browser column on the right instead of toggling the terminal |
| `src/app/hooks/use-keybinds-tab-slot.test.ts` | Tests: ⌘N over a tab strip is a tab switch, elsewhere a profile switch; activates the Nth tab of the hovered zone and leaves the profile alone; falls through to the profile switch when no zone is a tab strip; falls thro… |
| `src/app/hooks/use-keybinds.ts` | Exports `KeybindRuntimeDeps`, `useKeybinds` |
| `src/app/hooks/use-on-profile-switch.test.tsx` | Tests: ignores StrictMode effect replay and reacts only to real profile changes |
| `src/app/hooks/use-on-profile-switch.ts` | Run `onSwitch` when the active gateway profile changes — never on first mount. For dropping per-profile view state (probes, cached usage, drafts) when the backend the app talks to swaps underneath a still-mounted view. |
| `src/app/hooks/use-profile-switch-latch.test.ts` | @vitest-environment jsdom |
| `src/app/hooks/use-profile-switch-latch.ts` | Exports `useProfileSwitchLatch` |
| `src/app/hooks/use-refresh-hotkey.ts` | Binds the bare `r` key to a refresh action while the calling view is mounted. Ignored when a modifier is held, the event repeats, or focus is in an editable field (so typing "r" in a search/input never triggers it). |
| `src/app/hooks/use-route-enum-param.ts` | Read/write an enum-shaped URL search param (e.g. ?tab=foo). Used to make tabbed views survive a refresh. Always navigates with replace so tab clicks don't pile up in history. |
| `src/app/hooks/use-route-overlay-active.ts` | True while a full-screen route overlay (settings, agents, command-center, …) is showing. A portaled Radix modal sits above the app shell, so it would cover such a route. Any modal that sends the user to one (e.g. "set u… |
| `src/app/hud/click-through.test.ts` | The HUD's real shape: a React mount wrapping the shell, the bar inside it, and a portalled overlay as a sibling of the mount under <body>. |
| `src/app/hud/click-through.ts` | Whether the OS window should hand the mouse to whatever is behind it. `hit` is what the document reports under the cursor, `active` what holds focus; both are answered against the shell by where they sit in the tree. -… |
| `src/app/hud/composer-drag.test.ts` | Matches LONG_PRESS_MS in composer-drag.ts. |
| `src/app/hud/composer-drag.ts` | Hold anywhere on the HUD composer before the bar becomes draggable. Short enough to feel like grabbing it, long enough that a click still clicks. |
| `src/app/hud/game-overlay.ts` | Whether a fullscreen app (a game) is under the HUD. Main owns the answer — it polls the OS window list while the HUD is open (see startHudGameOverlayFeed / hud-game-overlay.ts) and pushes changes here. The renderer cann… |
| `src/app/hud/glass.test.tsx` | Tests: useHudGlass; leaves the window bare while a turn runs with the composer unfocused; frosts once the caret is in the composer, and lets go when it leaves; stays off while the band is not covering the window, howeve… |
| `src/app/hud/glass.ts` | Match native focus, including window deactivation. |
| `src/app/hud/handoff.test.tsx` | @vitest-environment jsdom |
| `src/app/hud/handoff.ts` | HUD ⇄ app-window handoff. The gateway binds a session's event stream to exactly ONE socket — the last one to submit or resume it (`session["transport"]`). The HUD is a full renderer with its own socket, so entering HUD… |
| `src/app/hud/hud-shell.tsx` | How long the transcript lingers at its glanceable opacity — after a turn lands, or after you let go of the composer — before it goes. This is the ONLY hold: the CSS carries no transition-delay, because two stacked holds… |
| `src/app/hud/hud-shell.viewed-interval.test.tsx` | @vitest-environment jsdom |
| `src/app/hud/layout.test.ts` | Tests: hudTranscriptHeight; uses the resized window space for a non-empty transcript; keeps an empty HUD collapsed |
| `src/app/hud/layout.ts` | Exports `HudTranscriptHeightInput`, `hudTranscriptHeight` |
| `src/app/hud/resize-frame.test.tsx` | @vitest-environment jsdom |
| `src/app/hud/resize-handle.test.ts` | Tests: hudResizeBounds; resizes from every CanvasTTY edge and corner while preserving the opposite edges; clamps at the minimum without moving the opposite edge; hudResizeDirections |
| `src/app/hud/resize-handle.ts` | Clamp to the same mins the window was created with (spawnHudWindow). |
| `src/app/hud/thread-focus.ts` | Exports `useHudThreadFocus` |
| `src/app/hud/transcript-band.test.tsx` | Tests: useHudTranscriptBand; stops polling once the viewport mounts; measures a TurnRow with data-slot=; does not treat clearance or background-resume spacers as message rows |
| `src/app/hud/transcript-band.ts` | Breathing room the sheet keeps above the first row, so the fade has somewhere to land. Folded into the measured height rather than added in CSS, so an empty transcript measures a true zero instead of a 12px strip. |
| `src/app/index.tsx` | The app root is the contribution-driven shell: panes, titlebar/statusbar items, keybinds, palette commands, routes, and themes all register through the contribution registry (src/contrib) — core surfaces use the same ca… |
| `src/app/layout-constants.ts` | Responsive horizontal gutter for primary content bodies (settings right side, skills, artifacts, command center / sessions). Ratio-based so it scales with the window, but clamped so it never collapses on narrow widths o… |
| `src/app/learning/archive-skill-confirm-dialog.tsx` | Exports `ARCHIVE_SKILL_DESCRIPTION`, `notifySkillArchived`, `archiveLearningSkill`, `fireOptimistic`, `ArchiveSkillConfirmDialog` |
| `src/app/master-detail.tsx` | Exports `ToolChip`, `MASTER_DETAIL_WIDE_COLS`, `MasterDetail`, `ListColumn`, `DetailColumn`, `ICON_BUTTON` … |
| `src/app/messaging/allowlist-field.tsx` | Exports `splitAllowlist`, `joinAllowlist`, `AllowlistFieldProps`, `AllowlistField` |
| `src/app/messaging/index.test.tsx` | @vitest-environment jsdom |
| `src/app/messaging/index.tsx` | Exports `MessagingView` |
| `src/app/messaging/platform-icon.tsx` | Exports `PlatformAvatar` |
| `src/app/messaging/telegram-qr-setup.tsx` | Exports `isTerminalTelegramOnboardingError`, `formatExpiry`, `TelegramQrSetupProps`, `TelegramQrSetup` |
| `src/app/model-picker-overlay.test.tsx` | The mock below replaces the computed store with a writable atom. |
| `src/app/model-picker-overlay.tsx` | Exports `ModelPickerOverlay` |
| `src/app/model-visibility-overlay.tsx` | Exports `ModelVisibilityOverlay` |
| `src/app/open-session.test.ts` | Tests: openSessionIntentFromModifiers; defaults to in-place; returns the caller base for an unmodified select; reads ⌘/⌃ as tab and ⇧+mod as window |
| `src/app/open-session.ts` | One door for "open this session" — every surface (sidebar, ⌘K, notifications, session switcher, refs, cron/artifacts) goes through here so a chat that's already a tile (or the main tab) is JUMPED TO instead of yanked in… |
| `src/app/overlays/overlay-breadcrumb-header.tsx` | Exports `OverlayBreadcrumbHeader` |
| `src/app/overlays/overlay-chrome.tsx` | Exports `OverlayIconButton` |
| `src/app/overlays/overlay-split-layout.test.tsx` | Tests: expands independently of navigation and reveals a newly selected child; fills only the current page when a third-level sub-page is open; its parent is named, not filled |
| `src/app/overlays/overlay-split-layout.tsx` | The wide rail and the narrow dropdown swap at exactly the width where OverlaySplitLayout drops to a single column, so the rail never stacks. |
| `src/app/overlays/overlay-view.tsx` | Shared top clearance for overlay content that sits *beside* the floating close button (which is absolute at `0.1875rem + titlebar/2`, -translate-y-1/2, so it costs no layout space): a Panel's header and the split layout… |
| `src/app/overlays/panel.test.tsx` | Tests: PanelRowMenu; opens its actions menu from the kebab without a tooltip |
| `src/app/overlays/panel.tsx` | Overlay "panel" primitive — the centered, capped card + framed chrome lifted straight from the trace / agents overlay so every non-settings overlay (cron, profiles, …) speaks the same visual language: tight type scale,… |
| `src/app/page-search-shell.tsx` | Tabs are data, not nodes: the shell owns their presentation so every page gets the same behavior — a centered TextTab row on wide viewports that collapses into a dropdown when the header can't fit both search and tabs. |
| `src/app/pet-generate/components/draft-grid.tsx` | Exports `DraftGrid` |
| `src/app/pet-generate/components/empty-hint.tsx` | Exports `EmptyHint` |
| `src/app/pet-generate/components/generate-unavailable.tsx` | Exports `GenerateUnavailable` |
| `src/app/pet-generate/components/hatch-preview.tsx` | Exports `HatchPreview` |
| `src/app/pet-generate/components/hatching-view.tsx` | Exports `HatchingView` |
| `src/app/pet-generate/components/provider-picker.tsx` | Image-backend picker for pet generation — the composer's model-pill pattern: a quiet trigger + a dropdown of options. No per-option notes: every backend resolves to the same faithful OpenAI image model, so there's no tr… |
| `src/app/pet-generate/components/reference-chip.tsx` | Exports `ReferenceChip` |
| `src/app/pet-generate/lib/frame-count.ts` | Sprite row → the PetInfo frame-count key it resolves to (directional walks and aliases collapse onto their base state). |
| `src/app/pet-generate/lib/read-reference-image.ts` | Exports `readReferenceImage` |
| `src/app/pet-generate/pet-generate-content.tsx` | Exports `PetGenerateContent` |
| `src/app/pet-generate/pet-generate-overlay.tsx` | "Hatch a Pet" — a dedicated, Pokédex-style overlay for pet generation. Previously generation lived as a cramped nested page inside the Cmd-K command palette (~34rem popover). This is its own full Radix dialog with room… |
| `src/app/pet-overlay/overlay-root.tsx` | Boot the pet-overlay window. Loaded by the same bundle as the main app but via `?win=overlay`, so it shares CSS/atoms while mounting a minimal, transparent surface (no app shell, no gateway, no I18n — the bubble strings… |
| `src/app/pet-overlay/pet-overlay-app.tsx` | Fallbacks mirror pet-sprite's defaults; the gateway normally sends real values. |
| `src/app/profiles/create-profile-dialog.test.tsx` | @vitest-environment jsdom |
| `src/app/profiles/create-profile-dialog.tsx` | Exports `isValidProfileName`, `CreateProfileDialog` |
| `src/app/profiles/delete-profile-dialog.tsx` | Thin wrapper over ConfirmDialog: owns the deleteProfile call, inherits Enter-to-confirm + busy/done/error from the shared dialog. The single choke point for every delete entry point (rail + Profiles view). |
| `src/app/profiles/index.test.tsx` | These tests pin the invariant this whole area exists to hold: the Manage Profiles page and the sidebar rail share ONE set of profile dialogs, so both "New Profile" entry points render the same modal (SOUL.md included),… |
| `src/app/profiles/index.tsx` | Exports `ProfilesView` |
| `src/app/profiles/rename-profile-dialog.test.tsx` | Pins the rename half of the deleted-profile-resurrection class (#88638 fixed the delete half): a retained renderer socket for the OLD profile name must be retired BEFORE the rename PATCH tears down its backend, or the s… |
| `src/app/profiles/rename-profile-dialog.tsx` | Exports `RenameProfileDialog` |
| `src/app/quick-entry/quick-entry-app.test.tsx` | Regression coverage for #77429: native picker options must paint a readable surface. |
| `src/app/quick-entry/quick-entry-app.tsx` | Exports `QuickEntryApp` |
| `src/app/quick-entry/quick-entry-root.tsx` | Boot the Quick Entry window. Loaded by the same bundle as the main app but via `?win=quick`, so it shares CSS/theme tokens while mounting a minimal capture surface (no app shell, no gateway, no router). The index.html b… |
| `src/app/retirement-view.test.tsx` | Tests: discontinued retirement shows the uninstall notice and persists dismissal per revision |
| `src/app/retirement-view.tsx` | The discontinued tier of retirement: a suffixed-identity build (canary / one-off / debug branch) whose channel has closed. There is nothing to download or migrate — the user uninstalls. Rendered inside the updates dialo… |
| `src/app/right-sidebar/file-actions.tsx` | Exports `isRenameShortcut`, `pickRevealLabel`, `FileEntryContextMenu`, `FileActionDialogs`, `InlineRenameInput` |
| `src/app/right-sidebar/files/dnd-manager.ts` | Exports `getFileTreeDndManager` |
| `src/app/right-sidebar/files/ipc.test.ts` | Tests: readProjectDir; returns no-bridge when the desktop bridge is unavailable; filters gitignored entries when readDir returns Windows-style paths; filters gitignored entries when Windows path casing differs across IP… |
| `src/app/right-sidebar/files/ipc.ts` | Exports `ProjectTreeEntry`, `readProjectDir`, `clearProjectDirCache` |
| `src/app/right-sidebar/files/prefs.test.ts` | Tests: files show-ignored preference; defaults to filtering and only opts in the root it was told about; round-trips off again; treats host spellings of one root as the same project |
| `src/app/right-sidebar/files/prefs.ts` | "Show gitignored files" is a per-project preference: a repo that keeps a second checkout, a build output or an env-specific folder out of git is exactly the repo whose owner wants to browse it, while every other project |
| `src/app/right-sidebar/files/remote-picker.test.tsx` | A tiny backend filesystem: the picker reads it through readDesktopDir and grows it through createRemoteDir, the same two calls it makes for real. |
| `src/app/right-sidebar/files/remote-picker.tsx` | Exports `RemoteFolderPicker` |
| `src/app/right-sidebar/files/tree-sizing.test.ts` | Tests: projectTreeViewportSize; uses ResizeObserver contentRect without forcing another layout read; falls back to a rect when ResizeObserver is unavailable |
| `src/app/right-sidebar/files/tree.test.tsx` | jsdom has no layout engine: give the container a real box so projectTreeViewportSize measures a non-zero viewport and the tree mounts (a 0×0 viewport renders the skeleton instead of rows). |
| `src/app/right-sidebar/files/tree.tsx` | Exports `ProjectTree`, `projectTreeViewportSize` |
| `src/app/right-sidebar/files/use-project-tree.test.ts` | Tests: useProjectTree; starts empty when cwd is blank and skips IPC; loads root entries on mount and sorts folders before files; records rootError when readDir returns an error |
| `src/app/right-sidebar/files/use-project-tree.ts` | Exports `TreeNode`, `UseProjectTreeResult`, `resetProjectTreeState`, `useProjectTree` |
| `src/app/right-sidebar/index.test.tsx` | Tests: RightSidebarPane; renders the tree whenever the session has a working dir (repo or not) — no picker; does not read a retained cwd while it belongs to a previous session; shows no tree for a detached chat (no work… |
| `src/app/right-sidebar/index.tsx` | Exports `RightSidebarPane`, `RightSidebarSectionHeader`, `PaneEmptyState`, `EmptyState` |
| `src/app/right-sidebar/review/churn-bar.tsx` | Per-row "digital rain" churn bar: a right-anchored, clipped stream of Matrix-ish glyphs whose width is the file's churn relative to the biggest changed file. Not wired in — drop `<ChurnBar file={file} />` into a review… |
| `src/app/right-sidebar/review/file-tree.test.tsx` | Tests: ReviewFileTree; virtualizes heavy trees: only the visible window is mounted; starts heavy trees collapsed and reveals children on expand, still bounded; keeps rendering small trees in full (animated path untouche… |
| `src/app/right-sidebar/review/file-tree.tsx` | Exports `ReviewFileTree` |
| `src/app/right-sidebar/review/index.test.tsx` | Tests: ReviewPane header gating; enables stage-all / revert-all under the uncommitted scope; disables stage-all / revert-all under the branch scope (read-only); renders the three scope tabs and switches scope on selecti… |
| `src/app/right-sidebar/review/index.tsx` | Exports `ReviewPane` |
| `src/app/right-sidebar/review/scope-row.tsx` | Exports `ReviewScopeRow` |
| `src/app/right-sidebar/review/ship-bar.test.tsx` | Tests: ReviewShipBar; renders the commit bar for the uncommitted scope; renders a read-only note for the branch scope (no working-tree actions); renders nothing for the uncommitted scope when there are no files |
| `src/app/right-sidebar/review/ship-bar.tsx` | Exports `ReviewShipBar` |
| `src/app/right-sidebar/review/tree-data.test.ts` | Tests: buildReviewTree; nests files under their folders and sorts dirs before files; aggregates +/- onto directories; compacts single-child directory chains |
| `src/app/right-sidebar/review/tree-data.ts` | A node in the review changed-files tree. Directories aggregate their descendants' +/- so a collapsed folder still shows its total churn (Codex's folder hierarchy view). |
| `src/app/right-sidebar/store.ts` | Exports `setTerminalTakeover`, `runInTerminal` |
| `src/app/right-sidebar/terminal/active-resize.test.ts` | Tests: observeActiveTerminalResize; fits once on activation and coalesces later resize bursts; cancels activation without fitting when hidden before the first frame; absorbs a real browser-style initial resize delivered… |
| `src/app/right-sidebar/terminal/active-resize.ts` | Exports `observeActiveTerminalResize` |
| `src/app/right-sidebar/terminal/agent-terminal-stream.bound.test.ts` | Tests: agent terminal retention is bounded; a finished process does not pin its backlog for the life of the renderer; keeps the most recent process replayable; never evicts a process whose terminal is mounted |
| `src/app/right-sidebar/terminal/agent-terminal-stream.ts` | Live agent-terminal output, pushed from the backend as `agent.terminal.output` events (see tui_gateway `_wire_agent_terminal_output`). Chunks route straight to the matching read-only xterm, keyed by process id — no poll… |
| `src/app/right-sidebar/terminal/buffer.ts` | Serialized view of the in-app terminal, handed to the agent's `read_terminal` tool. Line indices are absolute into xterm's buffer (0 = oldest scrollback line), so the agent can page with start_line/count against `total_… |
| `src/app/right-sidebar/terminal/chrome.tsx` | Pane-side terminal chrome: the body slot (which the persistent overlay chases) plus the always-on tab rail. Lives in the real pane DOM — NOT the z-4 terminal overlay — so the rail sits above the collapsed sidebars' z-30… |
| `src/app/right-sidebar/terminal/clipboard.test.ts` | Tests: terminalClipboardIntent; never claims a bare Ctrl+C with nothing selected, on either platform; copies on Ctrl+C when text is selected, so a selection is never lost to SIGINT; reserves plain Ctrl+C for the shell o… |
| `src/app/right-sidebar/terminal/clipboard.ts` | Clipboard keybindings for the GUI terminal. xterm renders to a canvas, so its selection is not a DOM selection and the platform's own copy command has nothing to grab. Two mechanisms fix that: |
| `src/app/right-sidebar/terminal/cwd-tracking.ts` | Exports `parseOscCwd`, `trackTerminalCwd` |
| `src/app/right-sidebar/terminal/instance.test.tsx` | Tests: background terminal input guidance (#108233); explains the mirror and opens a separate interactive shell only when requested; does not create shells or change selection on background mount and does not label user… |
| `src/app/right-sidebar/terminal/instance.tsx` | Absolute-stacked so inactive tabs keep layout size (a display:none host goes 0×0 and renders garbled on re-show); visibility toggles which one is seen. |
| `src/app/right-sidebar/terminal/links.test.ts` | Tests: terminal links; opens a ⌘-clicked URL in the in-app browser, not the window.open Electron denies; escapes to the OS browser on ⇧⌘-click; leaves a bare click to the selection, so a misclick never launches a browser |
| `src/app/right-sidebar/terminal/links.ts` | Both of xterm's link paths — the web-links addon (URLs it finds in the buffer) and the core OSC 8 provider (hyperlinks a CLI emits explicitly) — activate through `window.open()`, which the window's setWindowOpenHandler |
| `src/app/right-sidebar/terminal/persistent.test.tsx` | Tests: PersistentTerminal rect tracking; settles after rect changes instead of polling forever; remeasures when layout moves the slot without resizing it; remeasures from an explicit pane-layout state change |
| `src/app/right-sidebar/terminal/persistent.tsx` | One xterm Terminal mounted at the layout root and CSS-overlayed onto whichever `<TerminalSlot />` is active. Moving the host DOM detaches xterm's WebGL renderer (it observes its own attachment) and resets the screen, so… |
| `src/app/right-sidebar/terminal/rail.test.tsx` | Tests: TerminalRail; ⌘-click closes the tab; a plain click selects it |
| `src/app/right-sidebar/terminal/rail.tsx` | Exports `TerminalRail` |
| `src/app/right-sidebar/terminal/reveal-focus.test.ts` | Tests: terminal reveal keyboard focus; takes focus from the keybind on reveal and keeps it when the composer steals it; returns focus to the terminal on every later reveal from the keybind; does not keep refocusing once… |
| `src/app/right-sidebar/terminal/reveal-focus.ts` | Exports `toggleTerminalPane`, `terminalPaletteToggle` |
| `src/app/right-sidebar/terminal/revive-buffer.test.ts` | A default-PowerShell idle prompt: no blank-line separator before it. |
| `src/app/right-sidebar/terminal/revive-history.ts` | Exports `ReviveHistory`, `createReviveHistory` |
| `src/app/right-sidebar/terminal/revive-snapshot.ts` | Revive-buffer text handling for the GUI terminal: the ANSI escape scanner the boot-gap stripper and snapshot cleanup share, and the pure functions that decide which part of a serialized buffer is persisted for relaunch… |
| `src/app/right-sidebar/terminal/selection.test.ts` | Tests: shouldOwnAddSelectionShortcut; only the active tab claims the add-selection shortcut when text is selected (#76116); never claims the shortcut with no selection so clear-screen still reaches the shell |
| `src/app/right-sidebar/terminal/selection.ts` | VS Code's default integrated-terminal palette (terminalColorRegistry.ts) — a fixed table per theme type, not luminance-derived. Light/dark diverge on purpose so each stays legible (e.g. mustard yellow on white). |
| `src/app/right-sidebar/terminal/snapshot-persister.ts` | Leading-edge throttle window for capturing history. The first output after an idle gap persists almost immediately (so `cmd; quit` is on disk before the renderer tears down), then at most once per window while output st… |
| `src/app/right-sidebar/terminal/terminal-context-menu.test.ts` | Tests: terminalMenuHandleFor (production DOM shape); finds the handle registered on the xterm host, not the scope div; returns null outside any terminal scope; commandFocusedTerminal |
| `src/app/right-sidebar/terminal/terminal-context-menu.ts` | Verb registry for the GUI terminals. xterm paints to a canvas: a right-click inside it crosses no link, image, editable, or DOM selection, so the app context menu would see a bare surface and offer the window verbs. Foc… |
| `src/app/right-sidebar/terminal/terminal-drop.test.ts` | Tests: terminal drop in the browser-hosted Desktop; stages each dropped file on the host and types its quoted host path; quotes staged paths for the terminal; keeps in-app paths and staged files in drop order |
| `src/app/right-sidebar/terminal/terminal-drop.ts` | Exports `bindTerminalDrop` |
| `src/app/right-sidebar/terminal/terminal-font.test.ts` | Tests: terminal font resolution; keeps the bundled stack when no preference is configured; quotes a friendly family name and appends the bundled fallback stack; preserves an authored CSS stack before the bundled fallbac… |
| `src/app/right-sidebar/terminal/terminal-font.ts` | Exports `DEFAULT_TERMINAL_FONT_FAMILY`, `TERMINAL_FONT_SUGGESTIONS`, `normalizeTerminalFontFamily`, `resolveTerminalFontFamily`, `setTerminalFontFamilyFromConfig`, `warmTerminalFontFamily` … |
| `src/app/right-sidebar/terminal/terminal-input-bindings.test.ts` | Tests: routes word erase only to a live shell and releases the context-menu handle on cleanup; keeps a plain Alt chord Hermes ran off the PTY and leaves shared Ctrl keys and other cancels to the shell |
| `src/app/right-sidebar/terminal/terminal-input-bindings.ts` | `onData` also carries xterm-generated replies to DSR/CPR/DA queries during shell startup. Treat only real key events (plus explicit paste/drop/inject paths) as user activity, or an untouched refresh re-saves boot rows. |
| `src/app/right-sidebar/terminal/terminal-session-attempt.ts` | Exports `TerminalStatus`, `SessionAttemptController`, `createSessionAttemptController` |
| `src/app/right-sidebar/terminal/terminals.test.ts` | Tests: terminal store persistence; restores user tabs, active tab, and history on module load; persists user tabs and history synchronously, skipping agent mirrors; never attaches a revive buffer to an agent tab |
| `src/app/right-sidebar/terminal/terminals.ts` | xterm WebGL terminals that share one glyph atlas (same font/theme/DPR) keep per-terminal render models over a SHARED texture. Clearing one terminal's atlas (theme switch, tab activation) wipes the shared texture pages,… |
| `src/app/right-sidebar/terminal/use-agent-terminal.test.tsx` | Tests: useAgentTerminal; unmounts safely while initial font preparation is pending; repaints buffered rows through the DOM renderer after a WebGL context loss; retries the mount once a host rendered disconnected joins t… |
| `src/app/right-sidebar/terminal/use-agent-terminal.ts` | Read-only terminal for an agent background process: a write-only xterm (no PTY, no input) fed live by the backend output stream, keyed by process id. Shares the user terminal's look so the two read as one surface. |
| `src/app/right-sidebar/terminal/use-terminal-font.test.tsx` | @vitest-environment jsdom |
| `src/app/right-sidebar/terminal/use-terminal-font.ts` | Exports `useTerminalFontController` |
| `src/app/right-sidebar/terminal/use-terminal-session.test.tsx` | Tests: replays server history once, suppresses parser replies, and detaches on remount; closes a persistent browser tab when its host shell exits; closes a persistent browser tab whose shell exited while it was detached… |
| `src/app/right-sidebar/terminal/use-terminal-session.ts` | Exports `useTerminalSession` |
| `src/app/right-sidebar/terminal/workspace.tsx` | Exports `TerminalWorkspace` |
| `src/app/routes.test.ts` | Tests: primaryRouteSelectedSessionId; prefers the routed session id over a stale/different store selection (#59305); returns null on the new-chat route even with a leftover selection from the previous chat; falls back t… |
| `src/app/routes.titlebar-clusters.test.ts` | Tests: hidesFixedTitlebarClusters; hides clusters on contributed full pages and overlays; keeps clusters on chat and first-party workspace pages |
| `src/app/routes.ts` | Exports `SESSION_ROUTE_PREFIX`, `NEW_CHAT_ROUTE`, `SETTINGS_ROUTE`, `COMMAND_CENTER_ROUTE`, `SESSION_IMPORT_ROUTE`, `CAPABILITIES_ROUTE` … |
| `src/app/routes.workspace-reveal.test.ts` | A full page (Capabilities/Messaging/Artifacts/a contributed route) renders INSIDE the `workspace` pane, so navigating to one has to front that pane — otherwise a main zone parked on a session tile keeps the tile on scre… |
| `src/app/session-import/api.ts` | Exports `ForeignSession`, `ForeignPage`, `ForeignPreview`, `ForeignImportResult`, `foreignRequest` |
| `src/app/session-import/index.test.tsx` | Tests: browses without importing, then retries a failed import on the captured owner before opening; does not navigate when an import finishes after the view has closed |
| `src/app/session-import/index.tsx` | Exports `SessionImportView` |
| `src/app/session-picker-overlay.tsx` | Exports `SessionPickerOverlay` |
| `src/app/session-switcher.tsx` | Compact session-switcher HUD — keyboard-driven from `use-keybinds`, rows clickable via mousedown (Ctrl+click on macOS). No Dialog: Tab stays global. |
| `src/app/session/hooks/branch-owner-routing.integration.test.ts` | End-to-end owner routing for BRANCH (the #97764-adjacent strand). The unit tests in use-session-actions.test.tsx mock `@/store/gateway`, so they prove the branch path ASKS for the right route. They cannot prove the rout… |
| `src/app/session/hooks/browser-profile-folder.test.ts` | Tests: browser default folder follows the profile a new session belongs to; uses the folder Settings saved on the gateway own profile; starts a Bot Mode |
| `src/app/session/hooks/default-new-session.test.tsx` | Tests: generic new session default routing; keeps a legacy profile peer separate from the app default and the active source; keeps an explicit legacy-profile tile request ahead of both defaults; does not mistake the con… |
| `src/app/session/hooks/model-pick-ledger.ts` | Per-session ledger of in-flight model picks, shared by every surface that mounts useModelControls. A pick's own pre-pick snapshot is only the OPTIMISTIC paint of whatever pick came before it, so rollback must target |
| `src/app/session/hooks/new-session-first-message.test.tsx` | Tests: submitTextToNewSession first message; shows the submitted text as the first user message once the route opens the new chat; keeps one first message when the persisted transcript already has it; drops the first me… |
| `src/app/session/hooks/preview-open.test.tsx` | Tests: preview routing; open_preview; opens a tab for a session that has no stored id yet; keeps the tab when the stored session id arrives afterwards |
| `src/app/session/hooks/profile-rail-fresh-chat-owner.test.tsx` | Tests: profile rail: a fresh Omar chat keeps its exact registry owner across turns (#94071); an ordinary profile pick supersedes the legacy default pin on the active registry source; dials homelab::omar when boot publis… |
| `src/app/session/hooks/reconnect-resume-barrier.test.tsx` | Tests: shows the committed reply when the turn finishes between the reconnect page read and the resume; shows the whole reply when its message.complete lands while the cold resume has the view unbound; shows the whole r… |
| `src/app/session/hooks/reload-resume-stream-target.test.tsx` | Tests for `reload-resume-stream-target` |
| `src/app/session/hooks/resume-occurrences.test.tsx` | Tests: settles a retained idle error once across repeated resume and a changed error snapshot |
| `src/app/session/hooks/resume-reattach-arming.test.tsx` | Tests: a resume that fails after painting the history arms the quiet re-attach, and its retry stays quiet |
| `src/app/session/hooks/resume-route-commit.test.tsx` | Tests: binds the resumed session when the route commits onto it mid-resume |
| `src/app/session/hooks/session-context-drift.test.ts` | Tests: routeTargetFromToken; maps a session route to its session id, a non-chat route to null, and the new-chat route to __new__; ignores search and hash — only the pathname selects the chat; treats a colon-free token a… |
| `src/app/session/hooks/session-context-drift.ts` | The chat a route token points at: the stored/routed session id, `'__new__'` for the new-chat route, or null for a route that isn't a chat (settings and the other overlay routes). Used to compare two route tokens by thei… |
| `src/app/session/hooks/switch-back-receipt-race.test.tsx` | Tests: paints the prompt and reply once when the receipt binds them while the switch-back page read is in flight; keeps the receipt binding of a turn that completes while its session is not in the window |
| `src/app/session/hooks/use-background-queue-drain.test.tsx` | Tests: useBackgroundQueueDrain; drains an idle queued prompt for a non-selected background session; submits a queued entry once when two idle windows both drain it; forwards queued displayText so frozen @terminal chips… |
| `src/app/session/hooks/use-background-queue-drain.ts` | Exports `useBackgroundQueueDrain` |
| `src/app/session/hooks/use-background-queue-preservation.test.tsx` | Tests for `use-background-queue-preservation` |
| `src/app/session/hooks/use-busy-input-mode.test.tsx` | Tests: canonical busy policy is session scoped even with a cached global mode; recovers a transient busy policy read without reconnecting; bounds failed reads and cancels retries when their session leaves; uses only the… |
| `src/app/session/hooks/use-busy-input-mode.ts` | Exports `useBusyInputMode` |
| `src/app/session/hooks/use-context-suggestions.ts` | Exports `useContextSuggestions` |
| `src/app/session/hooks/use-cwd-actions.test.tsx` | Tests: useCwdActions session target; re-homes the named tile, not the primary, and leaves the primary readout alone; useCwdActions draft workspace target; ignores stale draft cwd normalization after a newer no-workspace… |
| `src/app/session/hooks/use-cwd-actions.ts` | Exports `useCwdActions` |
| `src/app/session/hooks/use-hermes-config.test.ts` | @vitest-environment jsdom |
| `src/app/session/hooks/use-hermes-config.ts` | Exports `useHermesConfig` |
| `src/app/session/hooks/use-message-stream/agent-init-error.test.tsx` | Tests: useMessageStream agent-init error surfacing (#63078); renders an agent-init failure as a visible in-transcript error and keeps the optimistic first message; merges the terminal error frame into the card the agent… |
| `src/app/session/hooks/use-message-stream/approval-mode-event.test.tsx` | Tests: live session.info approval mode reconciliation; reconciles an active-session event under its source gateway profile; ignores stale session.info from a non-active session on the active gateway; does not cache an e… |
| `src/app/session/hooks/use-message-stream/background-complete-event.test.tsx` | Tests: background.complete event; appends the result to the originating session as a system message; keeps another session untouched when the event targets this one; appends without a task-id header when the backend omi… |
| `src/app/session/hooks/use-message-stream/background-review-interrupt.test.tsx` | Repro for #119543: user sends a new message while the previous turn's `background_review` fork is still in flight. The fork itself emits nothing to the desktop, but the supersede window is where the previous turn's own |
| `src/app/session/hooks/use-message-stream/btw-complete-event.test.tsx` | Tests: btw.complete event; appends the answer to the originating session as a system message; keeps another session untouched when the event targets this one; drops an empty completion instead of appending a blank line |
| `src/app/session/hooks/use-message-stream/clarify-hydration.test.tsx` | A `clarify` server request must leave an answerable inline row even when the `tool.start` that normally mounts it was missed (stream reconnect / hydration race). Without it the sidebar says "needs input" but the |
| `src/app/session/hooks/use-message-stream/collapse-duplicate-final.ts` | Exports `DuplicateFinalCollapse`, `collapseDuplicateFinalAfterToolInterim`, `identicalInterimSiblingIndex`, `collapseDuplicateFinalOntoIdenticalInterim` |
| `src/app/session/hooks/use-message-stream/compaction-event.test.tsx` | Tests: useMessageStream compaction lifecycle; drives the compaction phase from the manual /compress spelling; clears the compaction phase on the structured completion edge; rehydrates the idle active session on the comp… |
| `src/app/session/hooks/use-message-stream/completion-boundaries.test.tsx` | Tests: binds a late submit acknowledgement to its exact optimistic prompt without reviving the turn; binds the sent prompt to the receipt row named by its submission; binds the prompt and the steer of a turn whose recei… |
| `src/app/session/hooks/use-message-stream/completion-projections.test.tsx` | Tests for `completion-projections` |
| `src/app/session/hooks/use-message-stream/composer-model-event.test.tsx` | Tests: session.info does not clobber composer model selection; keeps a sticky manual pick when a global session.info carries the profile default |
| `src/app/session/hooks/use-message-stream/delta-flush.test.tsx` | Tests: useMessageStream delta flush scheduling; flushes streaming text on a bounded timer while the window is unfocused; flushes queued text immediately when a hidden window becomes visible; flushes queued text on focus… |
| `src/app/session/hooks/use-message-stream/duplicate-background-reply.test.tsx` | Tests: refreshes folded background replies without keeping their settled live copies |
| `src/app/session/hooks/use-message-stream/duplicate-completion.test.tsx` | Tests: settles identical tool-interim completion once while retaining every completed call; keeps distinct segments, user boundaries, and failures on their own side of completion |
| `src/app/session/hooks/use-message-stream/duplicate-delivery-120104.test.tsx` | Tests: renders one bubble when the duplicate interim lands after the first completion |
| `src/app/session/hooks/use-message-stream/execution-authority.test.tsx` | Tests: refreshes an idle shared queue and does not let a queued cancellation end a running turn; rejects stale snapshots and terminal frames across generations and owner epochs; accepts a versioned terminal snapshot bef… |
| `src/app/session/hooks/use-message-stream/folded-segment-refresh.test.tsx` | Tests: keeps a settled segment the refreshed fold does not carry yet |
| `src/app/session/hooks/use-message-stream/gateway-event/deferred-pick.test.ts` | Tests: handleDeferredPickEvent; shows a refused next-turn pick by name and repaints the committed model; asks for a guarded next-turn pick instead of dropping it; leaves other session updates to their handlers |
| `src/app/session/hooks/use-message-stream/gateway-event/deferred-pick.ts` | A model pick made during a turn ("applies from your next message") resolves at the next turn boundary. When it does not apply, the owner says so on `session.updated`: - `refused` (with a reason): show the named refusal… |
| `src/app/session/hooks/use-message-stream/gateway-event/desktop-bridge.reaction.test.ts` | Tests: message.reaction bridge session scope; a background session event never mutates the visible transcript or the overlay; an active event from a non-active source is dropped, not painted onto the visible transcript;… |
| `src/app/session/hooks/use-message-stream/gateway-event/desktop-bridge.test.ts` | Tests: tip.show bridge (#117216); a ✕-closed agent tip does not come back on the next tip.show of the same content |
| `src/app/session/hooks/use-message-stream/gateway-event/desktop-bridge.ts` | Exports `handleDesktopBridgeEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/fallback-switch.test.ts` | Tests: desktop fallback switch; shows a model fallback switch in the transcript; does not turn unrelated lifecycle status into a transcript line |
| `src/app/session/hooks/use-message-stream/gateway-event/free-tier.ts` | free_tier.challenge: the account service wants a browser challenge cleared before it mints the free-tier token. The backend polls for the result on its own; this only gets the page loaded (hidden). Any source's challeng… |
| `src/app/session/hooks/use-message-stream/gateway-event/index.ts` | Exports `useGatewayEventHandler` |
| `src/app/session/hooks/use-message-stream/gateway-event/input-requests.approval-timeout.test.ts` | When the server withdraws an unanswered approval on timeout, the Run/Reject bar disappears and the tool row then shows a model-facing "BLOCKED …" result. The transcript must gain a human system line that says what happe… |
| `src/app/session/hooks/use-message-stream/gateway-event/input-requests.settled.test.ts` | A canonical gateway fans one approval out to every attached window; whichever window answers, the authority publishes `approval.settled {prompt_id}`. Every other window's Run/Reject bar must come down then, not stay par… |
| `src/app/session/hooks/use-message-stream/gateway-event/input-requests.test.ts` | Tests: Bot Screen install password card; belongs to the app, not to the chat that happened to be open: it survives a chat switch and its cancel finds it |
| `src/app/session/hooks/use-message-stream/gateway-event/input-requests.ts` | Exports `handleInputRequestEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/lifecycle.approval-cancelled.test.ts` | #106678: interrupt/reap/teardown deny-resolves the backend approval queue silently. The approval.cancelled broadcast is the client's only signal — without it a parked Run/Reject bar keeps offering buttons that answer |
| `src/app/session/hooks/use-message-stream/gateway-event/lifecycle.test.ts` | Tests: handleLifecycleEvent setup.ready; claims the event and triggers one free-tier refresh plus one readiness evaluation from the active source; claims but ignores setup.ready from a non-active source |
| `src/app/session/hooks/use-message-stream/gateway-event/lifecycle.ts` | Exports `handleLifecycleEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/message-stream.test.ts` | Tests: handleMessageStreamEvent session-control integration; refreshes only after message.complete, through the store seam; unread dot for a messaging turn Desktop sent; lights on the stamped completion of a turn Deskto… |
| `src/app/session/hooks/use-message-stream/gateway-event/message-stream.ts` | Exports `handleMessageStreamEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/onboarding.ts` | onboarding.ended: a first-run run ended. Every source's event counts: the run is the install's, and the window showing it may be subscribed to another chat or profile. |
| `src/app/session/hooks/use-message-stream/gateway-event/server-requests.test.ts` | Tests: connection request routing; does not route connection operations through the server-request rail; approval request routing; titles the parked approval toast with the session it belongs to |
| `src/app/session/hooks/use-message-stream/gateway-event/server-requests.ts` | Exports `ServerRequestContext`, `requestNamesActiveSession`, `windowHostsSession`, `windowReadClaimsSession`, `previewSessionRoute`, `SERVER_REQUEST_HANDLERS` … |
| `src/app/session/hooks/use-message-stream/gateway-event/session-control.test.ts` | Tests: handleControlEvent; does not claim non-control events; applies a valid event to the routed session and proves it supported; claims malformed control events without replacing the last good state |
| `src/app/session/hooks/use-message-stream/gateway-event/session-control.ts` | Exports `handleControlEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/session-info.test.ts` | Tests: handleSessionInfoEvent workspace ownership; ignores an unnamed broadcast from a session the pane is not bound to; does not let a fan-out of unnamed broadcasts walk the workspace path; adopts an unnamed session.in… |
| `src/app/session/hooks/use-message-stream/gateway-event/session-info.ts` | Exports `handleSessionInfoEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/settled-during-resume.test.ts` | Tests: a reply settled while a resume is in flight; is newer than that resume, which keeps the live transcript; does not count a settle that landed while the view was unbound from that runtime; does not outrank a resume… |
| `src/app/session/hooks/use-message-stream/gateway-event/status.test.ts` | The gateway `error` event (tui_gateway/prompt_turn.py) carries only a message — no error_surface. The dispatcher must still classify the two refusals it can mean so the card and toast read like a classified turn: |
| `src/app/session/hooks/use-message-stream/gateway-event/status.ts` | Lifecycle text that announces the session left its selected model for a fallback. |
| `src/app/session/hooks/use-message-stream/gateway-event/theme-requests.test.ts` | SAFETY: the set_theme handlers read only activeSessionIdRef, sessionInterrupted and updateSessionState. |
| `src/app/session/hooks/use-message-stream/gateway-event/tools-preview.test.ts` | Tests: reoffers a real later production, never a historical mount or duplicate completion; keeps dismissal when a missed completion arrives through the real reconnect replay path |
| `src/app/session/hooks/use-message-stream/gateway-event/tools-progress.test.ts` | Tests: shows tool.progress on its running row and drops it when the call completes; keeps two chats reusing one call id apart, and a turn end sweeps only its own chat |
| `src/app/session/hooks/use-message-stream/gateway-event/tools-subagent-interrupt.test.ts` | #75505 root cause 2: a Stop interrupts the parent TURN, not the children. A delegation finishing in the background fires `subagent.complete` after the interrupt; the SUBAGENT_EVENT_TYPES guard dropped it and the row spun |
| `src/app/session/hooks/use-message-stream/gateway-event/tools.ts` | Exports `handleToolProgressEvent`, `retireTurnToolProgress`, `handleToolEvent` |
| `src/app/session/hooks/use-message-stream/gateway-event/types.ts` | Exports `GatewayEventDeps`, `GatewayEventContext`, `GatewayEventHandler` |
| `src/app/session/hooks/use-message-stream/heartbeat-complete-reorder.test.tsx` | Tests: #119569 V1: tool-heavy turn keeps the just-delivered reply across complete; #119569 V2: interim-sealed tool turn keeps both segments across complete; #119569 V3: running=false heartbeat before complete must not d… |
| `src/app/session/hooks/use-message-stream/index.ts` | Exports `useMessageStream` |
| `src/app/session/hooks/use-message-stream/interim-history.test.tsx` | Tests: intermediate assistant text survives Desktop lifecycle boundaries |
| `src/app/session/hooks/use-message-stream/interim-redelivery-duplicate.test.tsx` | A turn whose reply was sealed as an interim BEFORE the client had it on screen (the interim materialized its own bubble because a superseded attempt's frames had cleared the live stream) used to paint the reply twice: |
| `src/app/session/hooks/use-message-stream/interim-redelivery.test.tsx` | Redelivered `message.interim` events must not duplicate bubbles (#93926). The gateway delivers stream events over a reconnecting websocket, so any interim event can arrive twice: back-to-back, or long after its segment… |
| `src/app/session/hooks/use-message-stream/interim-sealing.test.tsx` | Tests: useMessageStream interim text sealing; preserves interim text that the final response does not include; hydrates an empty completion when the live transcript still ends with the user message; marks sealed interim… |
| `src/app/session/hooks/use-message-stream/interrupted-reply.test.tsx` | #121594: Stop seals the live bubble at the click and drops every later message.delta, but the agent keeps streaming until it honours the interrupt and persists everything it delivered (state.db and the next turn's conte… |
| `src/app/session/hooks/use-message-stream/interrupted-reply.ts` | Exports `extendInterruptedReply`, `bindStoppedTurnReceipt` |
| `src/app/session/hooks/use-message-stream/interrupted-status-sync.test.tsx` | #81114: a Stop/interrupt seals the assistant bubble, but background work keeps running and its completions still arrive. Those completions must retire the status-stack rows (subagent/delegate) that have no poll to |
| `src/app/session/hooks/use-message-stream/late-tool-events.test.tsx` | Tool events route to the bubble that owns the call id, not to whatever is streaming now. A result that lands AFTER its part was sealed (interim commentary, mid-turn user insert, turn settle) must re-attach to that part |
| `src/app/session/hooks/use-message-stream/moa-progress-event.test.tsx` | Tests: useMessageStream moa.progress / moa.phase surfacing; shows refs k/n lines in the reasoning block as references complete; restarts the progress block on the first ref of a new fan-out; appends the aggregating mark… |
| `src/app/session/hooks/use-message-stream/moa-reference-event.test.tsx` | Tests: useMessageStream moa.reference accumulation (#64658); keeps every reference model labelled block instead of only the latest one; accumulates three or more references in order |
| `src/app/session/hooks/use-message-stream/peer-transcript-notify.test.tsx` | Tests: completed turn notifies peer windows (#65047); broadcasts the stored session when a turn completes; does not broadcast a completed runtime that has no stored session |
| `src/app/session/hooks/use-message-stream/pet-tool-failure-event.test.tsx` | Tests: pet tool-failure reaction; briefly shows failed when the active session has an isolated tool error; does not show failed for a successful tool or a background-session failure |
| `src/app/session/hooks/use-message-stream/provider-wait-event.test.tsx` | Tests: provider wait visibility; surfaces explained waits but ignores generic spinner rewrites; clears the wait when its runtime session is dropped; clears every wait when gateway session state is reset |
| `src/app/session/hooks/use-message-stream/receipt-user-rows.ts` | A stored transcript row id (SQLite rowid: a positive safe integer). |
| `src/app/session/hooks/use-message-stream/replay-gap.test.tsx` | Tests: session.replay_gap recovery; requests an authoritative resume for the affected active route without losing owner scope or its draft; re-resumes the affected mounted tile for a gateway snapshot while retaining its… |
| `src/app/session/hooks/use-message-stream/response-occurrences.test.tsx` | Tests for `response-occurrences` |
| `src/app/session/hooks/use-message-stream/response-parts.ts` | One live bubble may hold several model responses when an equal interim callback is suppressed. The last tool round, not the bubble, bounds the response that an interim/final frame is allowed to replace. |
| `src/app/session/hooks/use-message-stream/reused-final-after-tool.test.tsx` | The housekeeping-tool fallback ends a turn on the answer the model streamed BEFORE its tool call; the backend names that final `response_reused`. The merge bounds "the current response" at the bubble's last tool row, so… |
| `src/app/session/hooks/use-message-stream/segment-identity-replay.test.tsx` | A turn's frames carry their wire identity (tui_gateway/stream_segments.py): message.start the turn id, each delta its segment + offset, each interim the segment it seals. A frame re-sent under a new seq (reconnect repla… |
| `src/app/session/hooks/use-message-stream/segment-identity.ts` | Wire identity of a turn's streamed reply (tui_gateway/stream_segments.py). A prompt turn stamps its message.start with `turn_id`, every message.delta with `turn_id` + `segment` + `offset`, and every message.interim with… |
| `src/app/session/hooks/use-message-stream/session-info-side-effects.test.tsx` | Per-turn REST amplification guards: session.info must not refetch config for background sessions nor invalidate the model-options catalog when the model string is merely PRESENT (the backend stamps it on every event) ra… |
| `src/app/session/hooks/use-message-stream/session-reclaimed.test.tsx` | `session.reclaimed`: the backend tore down a live session we're still holding (idle TTL, LRU cap, WS-orphan reap). Before this event the runtime id stayed cached until something failed against it, which read to the user… |
| `src/app/session/hooks/use-message-stream/stale-pending-settle.test.tsx` | A turn that ends WITHOUT its message.complete (turn crash, reconnect gap, steer race) used to leave its streaming bubble pending:true forever. The next user message then landed after it, stranding a live thinking indica… |
| `src/app/session/hooks/use-message-stream/steer-arrival-order.test.tsx` | Repro for "when I steer it often sends out of order — a user bubble way above" (#73793 / #83151 class). Drives the REAL stream reducer (useMessageStream.handleGatewayEvent) and the REAL steer entry point |
| `src/app/session/hooks/use-message-stream/stream-flush.test.tsx` | Tests: stream delta delivery; delivers a delta while animation frames are parked |
| `src/app/session/hooks/use-message-stream/terminal-error-frame.test.tsx` | Tests: terminal error message.complete frames; marks the bubble failed from the structured error field, not the text heuristic; keeps streamed partial text visible on a partial failure; falls back to the frame text when… |
| `src/app/session/hooks/use-message-stream/test-harness.tsx` | Exports `MessageStreamHarnessOptions`, `GatewayFrame`, `MessageStreamHarness`, `renderMessageStream`, `playFrames` |
| `src/app/session/hooks/use-message-stream/timeline-events.test.tsx` | Tests: live transcript timeline events; records commentary, tool, resumed text, and turn-stop boundaries; preserves cross-channel delta order inside one flush window; uses the gateway event time for an error boundary |
| `src/app/session/hooks/use-message-stream/todo-cleanup.test.tsx` | Tests: useMessageStream turn-end todo cleanup; drops a still-active task list when the turn completes; keeps a finished list on completion so its linger shows the final checkmarks; drops a still-active task list when th… |
| `src/app/session/hooks/use-message-stream/tool-drafting-event.test.tsx` | Tests: drafting-tool label lifecycle; names the tool the model is drafting; leaves another session’s label alone; ignores a tool announced after the user hit stop |
| `src/app/session/hooks/use-message-stream/transformed-final.test.tsx` | Tests: useMessageStream response_transformed settlement; replaces the streamed bubble with transformed final text that shares no prefix; never lets a transformed completion overwrite an already-settled reply |
| `src/app/session/hooks/use-message-stream/usage.test.tsx` | Tests: useMessageStream status-bar usage scoping; merges a live session.usage tick from the focused session; normalizes a canonical top-level session.usage tick for the status bar; paints the status-bar meters from eith… |
| `src/app/session/hooks/use-message-stream/utils.test.ts` | Tests: completionErrorText; flags provider/HTTP/retry failures, ignores normal text; toTodoPayload; routes named todo and anonymous todos-bearing events to the todo stream |
| `src/app/session/hooks/use-message-stream/utils.ts` | Exports `sessionInfoStatePatch`, `hasSessionInfoStatePatch`, `applySessionInfoStatePatch`, `STREAM_DELTA_FLUSH_MS`, `MAX_STREAM_FLUSH_GAP_MS`, `PRE_TURN_LIVE_SETTLE_GRACE_MS` … |
| `src/app/session/hooks/use-model-controls-stale-pick.test.tsx` | Stale model-pick ordering: a superseded selectModel (newer pick, or a chat switch while config.set is in flight) must never roll the pill or a tile back. |
| `src/app/session/hooks/use-model-controls.test.tsx` | Tests: useModelControls; writes optimistic selections only to the owning connection cache; does not clobber the active session footer state with global model info; keeps a live session authoritative when Settings saves… |
| `src/app/session/hooks/use-model-controls.ts` | Exports `useModelControls` |
| `src/app/session/hooks/use-owner-queue-reconcile.ts` | Re-read the owner's queue of chats holding owner work on every edge into an open gateway. |
| `src/app/session/hooks/use-preview-routing.ts` | Exports `usePreviewRouting` |
| `src/app/session/hooks/use-prompt-actions/browser-manage-refusal.ts` | A remote connection refuses /browser connect\|disconnect: both drive the CDP connection inside the gateway process. The Webapp is always remote and has no local gateway to switch to, so it names the machine the command… |
| `src/app/session/hooks/use-prompt-actions/browser-manage.test.tsx` | Tests: usePromptActions /browser connect\|disconnect\|status; /browser status on a remote connection is sent as browser.manage |
| `src/app/session/hooks/use-prompt-actions/index-test-utils.tsx` | Shared fixtures for the usePromptActions suites (index.test.tsx and its split siblings). Each test file keeps its own vi.mock calls. The active id the desktop holds is the *runtime* session id from |
| `src/app/session/hooks/use-prompt-actions/index.background-interrupt.test.tsx` | Tests: usePromptActions background processes: interrupt vs rewind; cancelRun interrupts the turn but leaves running background processes and subagents alone; reloadFromMessage (regenerate) kills processes from the trunc… |
| `src/app/session/hooks/use-prompt-actions/index.deep-cut.test.tsx` | Deep-cut confirms (#133716): regenerate/edit that would archive later user turns. |
| `src/app/session/hooks/use-prompt-actions/index.sleep-wake.test.tsx` | Suites in this file reuse the same stored-id constants. The module-level single-flight resume map (and drift-recovery cache) would otherwise leak a never-settling in-flight promise from one test into the next. |
| `src/app/session/hooks/use-prompt-actions/index.test.tsx` | Tests: durable submit acknowledgement; retires the native private-file journal only after a matching canonical receipt; a journal retirement that fails after admission still reports the delivered prompt and never reuses… |
| `src/app/session/hooks/use-prompt-actions/index.ts` | Exports `uploadComposerAttachment`, `usePromptActions` |
| `src/app/session/hooks/use-prompt-actions/owner-forward.test.tsx` | RT-37 (#140385): a prompt on a chat whose gateway owner is mid-turn. |
| `src/app/session/hooks/use-prompt-actions/prepared-submission-windows.test.tsx` | Tests: two windows sending the same text keep separate identities; only the writer retries its own; without Web Locks, a slash command sent from two tabs keeps each tab its own retry record |
| `src/app/session/hooks/use-prompt-actions/prepared-submissions-spent.test.ts` | Tests: an admitted identity whose journal removal failed stays spent across a reload; two windows retiring different admitted entries keep both tombstones across a reload |
| `src/app/session/hooks/use-prompt-actions/prepared-submissions-tabs.test.ts` | Tests: a tab acting on a stale read of the journal keeps the entry another tab just wrote; an entry an earlier build left in the blob is still offered and adopted, and stays retired once acknowledged; two tabs upgrading… |
| `src/app/session/hooks/use-prompt-actions/prepared-submissions-test-utils.ts` | The browser journal as localStorage holds it: one key per entry. |
| `src/app/session/hooks/use-prompt-actions/prepared-submissions.test.ts` | Tests: image recovery never offers expanded slash intent as an ordinary draft and leaves its exact journal intact; a browser journal read lists the storage keys once, however many stores it reads; native preparation wai… |
| `src/app/session/hooks/use-prompt-actions/prepared-submissions.ts` | Exports `ENTRY_PREFIX`, `PreparedSubmission`, `preparedSubmissionKey`, `listPreparedImageDrafts`, `readPreparedSubmission`, `adoptPreparedSubmission` … |
| `src/app/session/hooks/use-prompt-actions/prompt-actions-harness.tsx` | Shared usePromptActions test harness (index.test.tsx and the topical siblings). |
| `src/app/session/hooks/use-prompt-actions/queue-if-busy.test.ts` | Tests: leaves canonical busy kickoff admission to the submit pipeline instead of the local queue; forwards kickoff identity to queue admission and leaves idle targets alone; keeps caller-provided and generated slash IDs… |
| `src/app/session/hooks/use-prompt-actions/queue-if-busy.ts` | Exports `QueueIfBusyInput`, `queueKickoffIfSessionBusy` |
| `src/app/session/hooks/use-prompt-actions/queued-first-input.test.tsx` | Tests: does not graft explicitly queued input onto the active turn |
| `src/app/session/hooks/use-prompt-actions/resolve-target-session.test.ts` | Tests: resolveTargetSessionId; resumes the routed stored session instead of minting a new one when the runtime binding is gone; reuses the live runtime id when the cache confirms it owns the targeted stored session; rej… |
| `src/app/session/hooks/use-prompt-actions/resolve-target-session.ts` | Resolve the runtime session a submit or slash command must target. Both prompt pipelines need this answer and they must agree: `submit.ts` sends the user's text into it, and `slash.ts` runs backend commands against it.… |
| `src/app/session/hooks/use-prompt-actions/rewind.test.ts` | Tests: appendMidTurnUserMessage; appends the mid-turn message after the live assistant output, sealed in place; appends at the live tail when the stream id is stale or missing; drops an empty pending stream placeholder… |
| `src/app/session/hooks/use-prompt-actions/rewind.ts` | Shared rewind/interrupt core for the prompt verbs — the ONE implementation of the submit primitive + the pure message math behind cancel / reload / restore / edit / branch-visibility. Both the primary chat (`index.ts`)… |
| `src/app/session/hooks/use-prompt-actions/single-flight-resume.test.ts` | Tests: singleFlightSessionResume; two concurrent resume callers for the same stored id produce ONE session.resume RPC; different stored ids still resume independently; does not coalesce the same stored id across backend… |
| `src/app/session/hooks/use-prompt-actions/single-flight-resume.ts` | Single-flight guard for `session.resume`, keyed by backend connection + STORED id. After sleep/wake or a reconnect, many independent surfaces discover the same dead runtime at once — submit recovery, slash/rewind recove… |
| `src/app/session/hooks/use-prompt-actions/slash-desktop-commands.test.tsx` | T11 (#134889): Desktop commands the shared gateway refused as `slash.exec`, or that Desktop never offered, run on the owner's existing verbs instead. |
| `src/app/session/hooks/use-prompt-actions/slash-desktop-commands.ts` | T11 (#134889): /rollback, /agents (/tasks), /config and /history on the session owner's existing verbs. The shared gateway refuses these as `slash.exec` (`gateway/session_commands.py`), and `/config` / `/history` were m… |
| `src/app/session/hooks/use-prompt-actions/slash-reasoning.test.ts` | Tests: says a /reasoning level typed while a reply streams applies from the next message |
| `src/app/session/hooks/use-prompt-actions/slash-session-commands.test.tsx` | /undo, /retry, /steer and /queue run against the session owner's canonical verbs (the Ink TUI's behaviour on the same gateway), never as `slash.exec`, which the shared gateway refuses. |
| `src/app/session/hooks/use-prompt-actions/slash-session-commands.ts` | Exports `SessionCommandEnv`, `retryText`, `userTurnFromEnd`, `truncateRewoundMessages`, `sessionCommandHandlers` |
| `src/app/session/hooks/use-prompt-actions/slash-session-user-turns.test.ts` | After a compression the owner's resume snapshot also carries the turns it summarized away, marked `archived`: history to show, never an /undo or /retry target (the owner refuses a rewind to one). |
| `src/app/session/hooks/use-prompt-actions/slash.ts` | Exports `SESSION_COMPRESS_TIMEOUT_MS`, `useSlashCommand` |
| `src/app/session/hooks/use-prompt-actions/steering-recovery.test.tsx` | Tests for `steering-recovery` |
| `src/app/session/hooks/use-prompt-actions/steering-session.ts` | Exports `captureSteeringSession` |
| `src/app/session/hooks/use-prompt-actions/steering-undelivered-refusal.test.tsx` | Tests: redirectPrompt still surfaces a refusal that may have reached the turn |
| `src/app/session/hooks/use-prompt-actions/submission-destination.test.tsx` | Tests: submission intent destinations; separate mounted composers submit identical text as distinct intents while an explicit retry retains its payload; stages canonical images on the captured owner without a legacy ima… |
| `src/app/session/hooks/use-prompt-actions/submission-destination.ts` | Exports `SubmissionDestination`, `captureSubmissionDestination`, `destinationAfterCreate`, `sameAuthorityPublishedOwner` |
| `src/app/session/hooks/use-prompt-actions/submit-admitted-conflict.test.tsx` | Tests: a retry refused because its id is already admitted settles as delivered; other conflicts still fail; an edited queued entry drains as a new message, not as its admitted original |
| `src/app/session/hooks/use-prompt-actions/submit-unknown-receipt.test.tsx` | Tests: an exact retry answered |
| `src/app/session/hooks/use-prompt-actions/submit-view-binding.test.ts` | Tests: moves the pane and carries the selected conversation into an empty resumed runtime; recognizes the same conversation after compression rotates its stored id; never carries another conversation into the resumed ru… |
| `src/app/session/hooks/use-prompt-actions/submit-voice-stopped.test.tsx` | Tests: a voice_stopped receipt settles the send with no turn, no error and no retained retry; a voice_stopped receipt on the identityless legacy fallback settles the send too |
| `src/app/session/hooks/use-prompt-actions/submit.ts` | Exports `ResumedRuntimeBindingDeps`, `rebindPaneToResumedRuntime`, `useSubmitPrompt` |
| `src/app/session/hooks/use-prompt-actions/upload-composer-attachment.test.ts` | Per-file copy, matching the convention of the other shards in this directory (preview-open.test.tsx, session-tile-actions.test.ts): the id the desktop holds is the *runtime* session id from session.create. |
| `src/app/session/hooks/use-prompt-actions/upload-server-image.ts` | Upload an image attachment over HTTP for a server-owned composer queue. Pin HTTP to the same owner before the native byte read yields. Images are immutable admission payloads, never legacy agent.pending_images. |
| `src/app/session/hooks/use-prompt-actions/utils.test.ts` | Tests: recent interrupt cooldown; is true within the cooldown and false after expiry; shouldInterruptBeforeRewind is true when recently interrupted even if not busy; shouldInterruptBeforeRewind stays false for idle sess… |
| `src/app/session/hooks/use-prompt-actions/utils.ts` | Exports `GatewayRequest`, `delay`, `isSessionIdCandidate`, `blobToDataUrl`, `isProviderSetupError`, `inlineErrorMessage` … |
| `src/app/session/hooks/use-resume-reattach.test.tsx` | Tests: a failed resume that still painted the history; skips a timer that fires after the selection moved or a runtime bound, and stays bounded |
| `src/app/session/hooks/use-resume-reattach.ts` | Exports `useResumeReattach` |
| `src/app/session/hooks/use-route-resume.test.tsx` | The hook only arms the boot-restore one-shot; the listener consuming it lives in the real store (covered by session-states.test.ts). Mock the module so the store's side effects (persistence listeners) stay out of this h… |
| `src/app/session/hooks/use-route-resume.ts` | Exports `useRouteResume` |
| `src/app/session/hooks/use-session-actions.creating-session-hold.test.tsx` | Tests: createBackendSessionForSend creatingSessionRef hold (#66057); keeps creatingSessionRef true until routedSessionId catches up to the created stored id; clears creatingSessionRef when navigate throws; clears creati… |
| `src/app/session/hooks/use-session-actions.test.tsx` | Tests: desktop branch creation idempotency; coalesces duplicate stored-session branch attempts onto one backend child; does not coalesce two same-id parents that live on different connections; opens the branch child eve… |
| `src/app/session/hooks/use-session-actions/ambient-local-owner.test.tsx` | Tests: untagged resume ambient owner; does not remember the foreground source for a session it could not resolve |
| `src/app/session/hooks/use-session-actions/branch-approval-owner.test.tsx` | Branching a chat another profile owns must not let that profile's runtime overwrite the ACTIVE profile's approval chip: forkBranch passes the branch's owner (the parent row's route) to applyRuntimeInfo, which only recon… |
| `src/app/session/hooks/use-session-actions/branch-boundary.test.ts` | Tests: branching from a folded assistant bubble keeps through its last durable row, not its first |
| `src/app/session/hooks/use-session-actions/branch-boundary.ts` | The durable row a message-level branch keeps through: the highest row id the selected bubble shows. An assistant bubble folds several rows (tool-call turns, then its answer), and each text part keeps the row it came fro… |
| `src/app/session/hooks/use-session-actions/branch-create-key.ts` | Exports `branchCreateKey` |
| `src/app/session/hooks/use-session-actions/committed-reply.test.ts` | Tests: a re-attach page that commits the reply before its completion; keeps the live row in the committed bubble’s place instead of beside it; keeps the committed bubble while the live row is still short of it; leaves a… |
| `src/app/session/hooks/use-session-actions/committed-reply.ts` | True when `next` is a pure forward extension of the previous *answer* text. Empty previous answer never accepts a dump as an extension — that is how the mid-turn inflight flat dump used to sandwich structured rows (#764… |
| `src/app/session/hooks/use-session-actions/create-overrides.ts` | Exports `SessionCreateOverrides`, `CreateBackendSessionForSend` |
| `src/app/session/hooks/use-session-actions/created-this-run.ts` | Stored ids created in THIS renderer run. A brand-new session lives only in the gateway's in-memory map until its first turn persists a state.db row — so if a respawning/flapping backend drops it, both resume RPC and the… |
| `src/app/session/hooks/use-session-actions/credential-warning-onboarding.test.ts` | Tests: applyRuntimeInfo credential warning while onboarding is open; drops the warning: onboarding owns the first run |
| `src/app/session/hooks/use-session-actions/display-hydration.ts` | Navigation revokes the view, not a read owned by an unchanged session. |
| `src/app/session/hooks/use-session-actions/index.ts` | Exports `BranchLoadedSessionOptions`, `useSessionActions` |
| `src/app/session/hooks/use-session-actions/live-turn-remainder.test.ts` | Tests: extends one response across arbitrary chunk cuts without changing its tool or text occurrences; settles a matching partial error without discarding richer local parts or distinct failures; pairs only the queue pr… |
| `src/app/session/hooks/use-session-actions/live-turn-remainder.ts` | Whitespace normalization is for comparison only; cuts always address the original text. |
| `src/app/session/hooks/use-session-actions/message-equivalence.ts` | Compile-time exhaustiveness guards. If a new field is added to ChatMessage or a new part type appears in the ChatMessagePart union (e.g. @assistant-ui ships one), these fail tsc until someone explicitly classifies it. |
| `src/app/session/hooks/use-session-actions/pending-turn-identity.ts` | A hydrated bubble can contain several source rows, including the final reply. |
| `src/app/session/hooks/use-session-actions/persisted-live-turn.ts` | Exports `reconcilePersistedLiveTurn` |
| `src/app/session/hooks/use-session-actions/pinned-session-removal.test.tsx` | Regression for #139350: optimistic pin cleanup must not race the fenced removal. |
| `src/app/session/hooks/use-session-actions/provisional-transcript.ts` | Exports `transcriptRestScope`, `provisionalTranscriptPaint` |
| `src/app/session/hooks/use-session-actions/remembered-owner.test.ts` | Tests: rememberedOwnerForResume; keeps the hint of a session with no row (hidden Bot Chat); drops a hint an untagged row contradicts (#97809) |
| `src/app/session/hooks/use-session-actions/remembered-owner.ts` | The persisted owner hint a pathname-driven resume may still trust, repairing a stale one in the map so it cannot re-poison the next resume or a session-scoped RPC dispatch. The cached row is the authority, with the same… |
| `src/app/session/hooks/use-session-actions/remove-archived-session.test.tsx` | Regression: deleting a session from the Archived filter view left a ghost row. Archived rows live in $archivedSessions (their own capped store — they're excluded from $sessions by design), and removeSession only pruned |
| `src/app/session/hooks/use-session-actions/resolve-stored-session.test.ts` | Tests: resolveStoredSession profile ownership; returns a cached row that carries an owning profile; routes a moved resolve into its current slice instead of duplicating it; treats a profile-less cache hit as unresolved… |
| `src/app/session/hooks/use-session-actions/restore-pending-approval.ts` | Re-park a resume snapshot's pending approval; true when one was restored. |
| `src/app/session/hooks/use-session-actions/restore-pending-clarify.test.ts` | Tests: restorePendingClarifyFromSnapshot; hands back the card the request handler already parked for a replayed open clarify request; reports an open request the handler declined (no card parked) without inventing one;… |
| `src/app/session/hooks/use-session-actions/restore-pending-clarify.ts` | Exports `PendingClarifyResumeState`, `restorePendingClarifyFromSnapshot`, `pendingClarifyToolPayload`, `withoutEarlyClarifyProjection` |
| `src/app/session/hooks/use-session-actions/restore-pending-connection.ts` | Exports `PendingConnectionResumeState`, `restorePendingConnectionFromSnapshot`, `connectionRequestToolPayload`, `projectPendingConnection` |
| `src/app/session/hooks/use-session-actions/resume-barrier-reread.ts` | Exports `GraftedTranscriptPage`, `graftTranscriptPage`, `rereadPageAfterResumeBarrier`, `prefetchServesResume` |
| `src/app/session/hooks/use-session-actions/resume-empty-prose-pairing.test.ts` | Tests: reconcileResumeMessages — empty-prose pairing; does not graft a later cached structure onto an earlier tool-only row with empty prose; does not overwrite a settled text-only target when a structured cached row sh… |
| `src/app/session/hooks/use-session-actions/resume-latches.ts` | Exports `ResumeAttemptOptions`, `clearResumeLatches`, `MAX_RESUME_RETRIES`, `resumeRetryDelayMs`, `resumeFailedToastId`, `clearResumeToasts` … |
| `src/app/session/hooks/use-session-actions/resume-owner.ts` | Connection that supplied the current session list, captured before resume's async metadata lookup. A connection switch clears/reloads the session rows before this path runs, so an untagged row belongs to the connection… |
| `src/app/session/hooks/use-session-actions/resume-reconcile.ts` | How a resume snapshot is reconciled with the transcript already on screen. A reconnect re-resumes the open chat. The backend cuts that snapshot when it answers, but the new socket is already attached, so the turn's `mes… |
| `src/app/session/hooks/use-session-actions/resume-structural-parts.test.ts` | Tests: reconcileResumeMessages — structural parts on a mid-turn switch; keeps tool-call parts the authoritative text-only row cannot carry; does not duplicate tool calls the authoritative row already carries; keeps live… |
| `src/app/session/hooks/use-session-actions/resume-verdicts.ts` | A "session genuinely doesn't exist" failure (deleted, or an id from a wiped / rotated backend) — the REST transcript 404s with `Session not found`. Distinct from a transient/wedged backend (ECONNREFUSED, timeout), which… |
| `src/app/session/hooks/use-session-actions/runtime-owner.test.ts` | Tests: applyRuntimeInfo approval mode owner scoping; never lets another backend runtime set the active profile approval chip |
| `src/app/session/hooks/use-session-actions/runtime-owner.ts` | Runtime-info ownership for applyRuntimeInfo: the status-bar approval chip is keyed by the ACTIVE profile's name, so only the active gateway's runtime may reconcile it. This mirrors the session.info event rule, except th… |
| `src/app/session/hooks/use-session-actions/session-create-request.test.ts` | Tests: createGatewaySession; resends once without cwd_explicit (cwd kept) when a pre-#122899 backend rejects the flag; drops service_tier (fast kept) for a pre-Ultrafast backend, one rejected field at a time; never rese… |
| `src/app/session/hooks/use-session-actions/session-create-request.ts` | Exports `createGatewaySession`, `desktopSessionCreateParams` |
| `src/app/session/hooks/use-session-actions/settled-turns.ts` | When this renderer last settled a turn of each runtime session on screen (message.complete), so a resume that was in flight meanwhile can tell its snapshot is older than the reply on screen (resume-reconcile.ts). Bounde… |
| `src/app/session/hooks/use-session-actions/streamed-reply-survives-sync.test.ts` | Tests: preserveLocalPendingTurnMessages — settled reply over an empty tool shell (#123047); keeps the streamed final reply when the stored turn hydrates as a text-less tool shell; carries the shell row identity onto the… |
| `src/app/session/hooks/use-session-actions/transcript-provenance.test.ts` | Tests: transcript provenance; matches only the same connection, profile, stored id, and lineage; strips proof and bumps the authority epoch on invalidation; hides messages from the view without dropping the cache entry |
| `src/app/session/hooks/use-session-actions/transcript-provenance.ts` | Exports `TranscriptProvenanceScope`, `createPersistedDisplayTranscriptProvenance`, `hasPersistedDisplayTranscriptProvenance`, `withoutTranscriptProvenance`, `invalidatePersistedDisplayTranscriptAuthority`, `TranscriptVi… |
| `src/app/session/hooks/use-session-actions/unarchive-session.test.tsx` | Regression (#98813): the sidebar's Archived view reuses the row action menu, so its shared archive verb must RESTORE an already-archived row instead of re-archiving it. unarchiveSession is the restore path the |
| `src/app/session/hooks/use-session-actions/utils-overlay-tool-calls.test.ts` | Tests: overlayConcurrentMessageChanges tool calls; does not duplicate a tool call the live row already carries when merging the prefix; keeps an answered clarify when a later call of another tool reuses its id; keeps th… |
| `src/app/session/hooks/use-session-actions/utils.test.ts` | Tests: applyRuntimeInfo approval mode; reconciles session.info against the gateway profile; applyRuntimeInfo credential warnings; defers the empty-key warning to submit time instead of popping onboarding on switch |
| `src/app/session/hooks/use-session-actions/utils.ts` | Exports `preserveEquivalentTranscript`, `reconcileDurableHistory`, `reconcileResumeMessages`, `preserveLocalPendingTurnMessages`, `appendLiveSessionProjection`, `dedupeInflightUserAgainstTranscript` … |
| `src/app/session/hooks/use-session-actions/webapp-listed-row-resume.test.tsx` | Every socket the store builds besides the tab's own. |
| `src/app/session/hooks/use-session-list-actions.reactivation.test.tsx` | Real gateway registry, stubbed transport: the activation epoch here is the one production bumps, not a test double. |
| `src/app/session/hooks/use-session-list-actions.test.tsx` | Tests: workspace-only sidebar refresh; refreshSessions cold-start load error; flags a thrown first read and clears the flag once a retry lands rows; flags a reported scan failure that leaves the list empty |
| `src/app/session/hooks/use-session-list-actions.ts` | Exports `useSessionListActions` |
| `src/app/session/hooks/use-session-state-cache.test.tsx` | Tests: useSessionStateCache — stored-id rotation provenance; emits the previous, next, and runtime ids and removes the stale reverse mapping; does not publish a foreground-navigation event for a background runtime rotat… |
| `src/app/session/hooks/use-session-state-cache.ts` | Exports `useSessionStateCache` |
| `src/app/session/hooks/use-transcript-peer-sync.test.tsx` | Tests: useTranscriptPeerSync (#65047); re-pulls the transcript when a peer finishes a turn on the viewed session; ignores a peer ping for a session this window is not viewing |
| `src/app/session/hooks/use-transcript-peer-sync.ts` | Exports `useTranscriptPeerSync` |
| `src/app/session/hooks/warm-resume-replay-barrier.test.tsx` | Tests: waits for reconnect replay before activating and reading warm history; still settles a warm resume through session.activate when its replay socket is lost; holds a reconnect re-resume of the selected session behi… |
| `src/app/session/hooks/wrong-session-closeout.test.tsx` | @vitest-environment jsdom |
| `src/app/session/new-session-route.ts` | Exports `defaultNewSessionTarget`, `prepareDefaultNewSession` |
| `src/app/session/session-state-cache.test.ts` | Tests: SessionStateCache; bounds warm settled transcripts by LRU count and cleans ownership atomically; uses transcript bytes as well as count; keeps unsaved drafts and pending messages out of the eviction pool |
| `src/app/session/session-state-cache.ts` | Exports `DEFAULT_WARM_SESSION_TRANSCRIPT_COUNT`, `DEFAULT_WARM_SESSION_TRANSCRIPT_BYTES`, `SessionStateCache` |
| `src/app/session/workspace-session-target.test.ts` | Tests: startWorkspaceSession; keeps a newer sidebar target when an older project lookup resolves; keeps a Home new-session request detached even when another project scope is active; pins the new chat to the profile the… |
| `src/app/session/workspace-session-target.ts` | Exports `startWorkspaceSession` |
| `src/app/settings/about-settings.test.tsx` | Tests: AboutSettings; shows shared version details and refreshes each remote gateway independently; shows the fixed package channel with no selector; lets a source checkout pick its channel and confirms the move to stab… |
| `src/app/settings/about-settings.tsx` | Exports `AboutSettings` |
| `src/app/settings/appearance-contrib.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/appearance-contrib.tsx` | Appearance settings' plugin seam — a render area at the END of the Appearance page, so a plugin adds its own controls (session-colour rules, theme extras) with the app's own primitives instead of injecting nodes into th… |
| `src/app/settings/appearance-settings.extra-slot.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/appearance-settings.tsx` | Exports `AppearanceSettings` |
| `src/app/settings/appearance-subpages.ts` | Exports `APPEARANCE_SUBPAGES`, `AppearanceSubpageId` |
| `src/app/settings/aux-task-rows.tsx` | Built-in auxiliary tasks, in the order `_AUX_TASK_SLOTS` (hermes_cli/web_server_config.py) serves them. Friendly labels and hints come from i18n `m.tasks`; raw task keys (vision, mcp, …) are opaque to most users. Plugin… |
| `src/app/settings/billing/account-row-value.tsx` | Exports `RowValue` |
| `src/app/settings/billing/api.test.ts` | Tests: createBillingApi; passes successful RPC results through as data; normalizes object-shaped refusal envelopes; normalizes current string-shaped refusal envelopes |
| `src/app/settings/billing/api.ts` | Exports `BillingErrorKind`, `BillingRefusal`, `BillingResult`, `BillingChargeResult`, `UpdateAutoReloadInput`, `BillingRequestGateway` … |
| `src/app/settings/billing/auto-reload-row.tsx` | Exports `AutoReloadRow` |
| `src/app/settings/billing/billing-amounts.ts` | Exports `clampAmount`, `parseAmount`, `formatAmountForRequest`, `initialAutoReloadAmount`, `validateAutoReloadInputs`, `validateBillingAmount` … |
| `src/app/settings/billing/current-plan-card.tsx` | Exports `CurrentPlanCard` |
| `src/app/settings/billing/dev-fixtures.ts` | Exports `todayBillingState`, `todaySubscriptionState`, `postTrainBillingState`, `postTrainSubscriptionState`, `loggedOutBillingState`, `loggedOutSubscriptionState` … |
| `src/app/settings/billing/errors.test.ts` | Tests: resolveRefusal; maps every known refusal kind to copy and the expected action; includes monthly cap headroom when the server sends it; includes Stripe retry timing when the server sends it |
| `src/app/settings/billing/errors.ts` | Exports `BillingRefusalPresentation`, `resolveRefusal` |
| `src/app/settings/billing/fixtures.test-util.ts` | Exports `okBilling`, `okSubscription`, `endpointUnavailableBilling`, `endpointUnavailableSubscription`, `windowFixtures` |
| `src/app/settings/billing/index.test.tsx` | Tests: BillingSettings; changes billing shell language without losing the credit amount or issuing a charge; renders the post-train payload with enabled buy controls and card provenance; disables buy controls when no ca… |
| `src/app/settings/billing/index.tsx` | Exports `BILLING_VIEWS`, `BillingSubView`, `BillingSettings` |
| `src/app/settings/billing/inline-feedback.tsx` | Exports `StepUpInlineAction`, `BillingRefusalInline` |
| `src/app/settings/billing/keep-going-on-credits-row.test.tsx` | Tests: KeepGoingOnCreditsRow; without Remote Spending: one click opens the approval, holds the switch, then applies the change; a declined approval puts the switch back and says why, once; with Remote Spending already a… |
| `src/app/settings/billing/keep-going-on-credits-row.tsx` | Exports `KeepGoingOnCreditsRow` |
| `src/app/settings/billing/open-external.ts` | Optional-arg convenience over the canonical opener — the billing rows pass possibly-undefined URLs straight through from their view models. |
| `src/app/settings/billing/plans-view.tsx` | Exports `BillingPlansView` |
| `src/app/settings/billing/simulated-api.test.ts` | Tests: createSimulatedBillingApi; progresses the pending state through the whole loop: schedule sets it, resume clears it; does not mutate the shared fixture object |
| `src/app/settings/billing/simulated-api.ts` | The shape of one `billingDevFixtures` entry — a canned billing + subscription pair. |
| `src/app/settings/billing/tier-art.test.ts` | Tests: resolveTierArt; keys art by lowercase tier name, case-insensitively; returns null for unknown or missing names so the card renders text-only |
| `src/app/settings/billing/tier-art.tsx` | Reproduces the portal's tier-card hero treatment at thumbnail size: each webp sits over a solid Nous-blue well and blends into it. This blue well is the ONLY place Nous blue appears in the billing page — everything else… |
| `src/app/settings/billing/types.ts` | Exports `BillingStateResponse` |
| `src/app/settings/billing/use-billing-state.test.ts` | Tests: deriveBillingView (usage-window plans); replaces the subscription credits row with today / week / month / large-model gauges; shows no month row when the server sends no month gauge (older portal); colours a runn… |
| `src/app/settings/billing/use-billing-state.ts` | Exports `EMPTY_BILLING_VALUE`, `FALLBACK_PORTAL_BILLING_URL`, `FALLBACK_PORTAL_URL`, `BillingSummaryItemView`, `BillingNoticeView`, `BillingRowActionView` … |
| `src/app/settings/billing/use-charge-poller.test.ts` | Tests: pollChargeSettlement; settles after pending polls; returns a failed outcome with the charge failure reason; backs off on rate limits, honors retryAfter, and keeps polling |
| `src/app/settings/billing/use-charge-poller.ts` | Exports `CHARGE_POLL_INTERVAL_MS`, `CHARGE_POLL_CAP_MS`, `ChargeFlowPhase`, `ChargeFlowOutcome`, `ChargePollClock`, `ChargePollOptions` … |
| `src/app/settings/billing/use-step-up.test.tsx` | Tests: useStepUpFlow; subscribes for verification, opens the verification URL, cleans up, and invalidates on completion; one flow dismissing never resumes billing refetches during another flow |
| `src/app/settings/billing/use-step-up.ts` | Exports `StepUpPhase`, `StepUpVerification`, `StepUpMessage`, `useStepUpFlow` |
| `src/app/settings/billing/use-subscription-change.test.tsx` | Tests: useDowngradeFlow; records a preview refusal as the previewFailed phase and re-runs on retry; cancel clears the active change without scheduling; exposes mutating only while the schedule RPC is in flight |
| `src/app/settings/billing/use-subscription-change.ts` | Exports `DowngradeTarget`, `DowngradePhase`, `ActiveDowngrade`, `useDowngradeFlow`, `useResumeFlow` |
| `src/app/settings/browser-real-profile-panel.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/browser-real-profile-panel.tsx` | Exports `readUseRealProfile`, `BrowserRealProfilePanel` |
| `src/app/settings/chat-font-setting.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/chat-font-setting.tsx` | Exports `ChatFontSetting` |
| `src/app/settings/cloud-team-change.ts` | `org` values are the refs NAS echoes (`slug ?? id`) and are compared as opaque strings. If a team gains or changes its slug, a connection saved under the old ref reads as moved once: the reconnect below re-authenticates… |
| `src/app/settings/combobox-input.tsx` | cmdk highlights its first row whenever nothing is selected, which would make Enter swap free text for that row. A value no row carries keeps the list unhighlighted until the user actually arrows or points into it. |
| `src/app/settings/computer-use-panel.tsx` | Exports `ComputerUsePanel` |
| `src/app/settings/config-field-voice-locale.test.tsx` | Tests: renders the translated Echo Transcripts copy without changing its toggle value; preserves distinct Unicode descriptions but suppresses label and schema-key repetitions |
| `src/app/settings/config-field.test.ts` | Tests: parseListFieldDraft; commits comma-separated list values after editing; trims entries and drops empty segments; allows an unfinished trailing comma to remain draft-only until commit |
| `src/app/settings/config-field.tsx` | Exports `parseListFieldDraft`, `ConfigField` |
| `src/app/settings/config-settings.test.tsx` | The vi.mock factory below replaces the computed (read-only) atom with a writable one; narrow the import back so tests can drive it. |
| `src/app/settings/config-settings.tsx` | Exports `ConfigSettings` |
| `src/app/settings/config-subpages.ts` | Exports `CONFIG_SUBPAGES`, `configSubpageForField` |
| `src/app/settings/connections-registry.test.tsx` | Tests: ConnectionsRegistrySection; preserves, replaces and deletes stored headers through plaintext consent without selecting a source; keeps stale browser sign-in out of a storage-only edit for a different URL; refresh… |
| `src/app/settings/connections-registry.tsx` | Exports `normalizeGatewayUrl`, `sshCompositeKey`, `findDuplicateConnection`, `sameBackendPeerLabel`, `ConnectionsRegistrySection` |
| `src/app/settings/constants.ts` | Exports `EMPTY_SELECT_VALUE`, `CONTROL_TEXT`, `PROVIDER_GROUPS`, `ENUM_OPTIONS`, `FREE_INPUT_KEYS`, `FIELD_LABELS` … |
| `src/app/settings/credential-key-ui.tsx` | Exports `KeyRowProps`, `CREDENTIAL_CONTROL_CLASS`, `isKeyVar`, `friendlyFieldLabel`, `credentialPlaceholder`, `KeyField` … |
| `src/app/settings/custom-endpoints-settings.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/custom-endpoints-settings.tsx` | Exports `CustomEndpointsSettings` |
| `src/app/settings/delegation-model-provider-field.test.tsx` | Radix Select calls scrollIntoView / pointer-capture APIs jsdom lacks. |
| `src/app/settings/delegation-model-provider-field.tsx` | Exports `DelegationModelProviderField`, `useOwnerCatalog`, `displayProviders` |
| `src/app/settings/delegation-route-draft.ts` | Exports `DelegationModelProviderValue`, `SavedRoute`, `INHERIT_VALUE`, `MODEL_ONLY_VALUE`, `DIRECT_VALUE`, `CUSTOM_PROVIDER_VALUE` … |
| `src/app/settings/delegation-route-regressions.test.tsx` | Tests: delegation route regressions; requests the exact config owner; keeps an unfinished switch local beyond autosave, then applies one complete route; cancels a provider draft |
| `src/app/settings/delegation-route-row.tsx` | `delegation.provider` renders inside the `delegation.model` row, which applies both at once. |
| `src/app/settings/delegation-settings-integration.test.tsx` | Tests: real settings route and autosave integration; active A/settings B reads and saves B, never autosaves an unfinished route; keeps scopes separate across B to C to B and equal names on two connections; saves a manua… |
| `src/app/settings/delegation/model-route-dialog.tsx` | Exports `ModelRouteDialog` |
| `src/app/settings/delegation/model-routes.tsx` | Exports `ModelRoutesEditor` |
| `src/app/settings/delegation/plugin-actions.ts` | Exports `PluginState`, `useAdvancedDelegationPlugin`, `installAdvancedDelegation`, `enableAdvancedDelegation` |
| `src/app/settings/delegation/profile-routes.tsx` | Exports `ProfileRoutesEditor` |
| `src/app/settings/delegation/routes.test.ts` | Tests: route editing keeps a default while routes exist; names a default on the first route, follows a rename, and moves it off a deleted default; refuses incomplete or clashing drafts; an edit keeps keys the dialog doe… |
| `src/app/settings/delegation/routes.ts` | The fields the route dialog edits; every other key of a stored route round-trips untouched. |
| `src/app/settings/delegation/routing-data.test.ts` | Tests: route saves for one owner; reach the server in order, and an older answer never undoes a newer edit on screen; a failed save does not stop the edits queued behind it |
| `src/app/settings/delegation/routing-data.ts` | Exports `ADVANCED_DELEGATION_PLUGIN`, `PLUGIN_MODES`, `MODES`, `routingQueryKey`, `useDelegationRouting`, `isPluginMode` … |
| `src/app/settings/delegation/routing-section.test.tsx` | A stateful stand-in for the backend's /api/delegation routes (same shapes, same refusal). |
| `src/app/settings/delegation/routing-section.tsx` | Exports `DelegationRoutingSlot`, `DelegationRoutingSection` |
| `src/app/settings/delegation/subagent-model-gate.tsx` | Why the subagent model does not apply in the saved mode, and what a task that picks no route runs on. |
| `src/app/settings/env-credentials.tsx` | Shared filter used by every credential surface (Providers + Keys pages): category gate first, then a free-text match across key name + description. |
| `src/app/settings/env-var-actions-menu.tsx` | Exports `EnvVarActionsMenu`, `EnvVarContextMenu`, `EnvVarActionsTrigger` |
| `src/app/settings/fallback-models-field.test.tsx` | Radix Select calls scrollIntoView / pointer-capture APIs jsdom lacks. |
| `src/app/settings/fallback-models-field.tsx` | An entry is `{provider, model}` plus whatever routing the user hand-wrote (`base_url`, `api_key`, `key_env`, `api_mode`, ...). The editor only edits the two selects; every other key rides along untouched, or an autosave |
| `src/app/settings/field-copy.ts` | Exports `FieldCopyTree`, `schemaKeyToFieldCopyKey`, `fieldCopyForSchemaKey`, `defineFieldCopy` |
| `src/app/settings/file-browser-setting.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/gateway-settings.test.ts` | Tests: normalizeGatewaySettingsState; fills missing and undefined persisted fields with canonical defaults; returns an independent default state for invalid persisted data; savedCloudConnectionUrl |
| `src/app/settings/gateway-settings.test.tsx` | Collect the component graph before the behavioral test deadline starts. |
| `src/app/settings/gateway-settings.tsx` | Exports `GatewaySettingsState`, `normalizeGatewaySettingsState`, `savedCloudConnectionUrl`, `GatewaySettings` |
| `src/app/settings/helpers.test.ts` | Tests: settings helpers; does not shadow the backend schema options for memory.provider; isExternalMemoryProvider; treats only real plugin names as external providers |
| `src/app/settings/helpers.ts` | Canonical implementations live in @/lib/text; re-exported here so the many settings/capabilities call sites keep their import path. |
| `src/app/settings/hud-modifier-settings.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/hud-modifier-settings.tsx` | Exports `HudModifierSettings` |
| `src/app/settings/index.tsx` | Exports `SettingsView` |
| `src/app/settings/keybind-settings.late-actions.test.tsx` | A keybind action contributed AFTER the settings tab mounts must appear in the map. Same class as the late plugin-route bug (#109063): the component subscribed to `useContributions(KEYBINDS_AREA)` but discarded the snaps… |
| `src/app/settings/keybind-settings.tsx` | Exports `KeybindSettings` |
| `src/app/settings/keychain-encryption-setting.tsx` | Exports `KeychainEncryption`, `useKeychainEncryption`, `KeychainEncryptionSetting` |
| `src/app/settings/keys-settings.test.tsx` | Tests: KeysSettings; fetches env vars for the displayed profile (the concrete key, never null) when unscoped; lists tools and excludes settings / channel-managed credentials; lists settings rows and excludes tools / cha… |
| `src/app/settings/keys-settings.tsx` | Sub-views surfaced as sidebar subnav under Tools & Keys (see settings/index.tsx). |
| `src/app/settings/local-model-download-progress.test.tsx` | Tests: LocalModelDownloadActions; running download without explicit can_pause shows NO control (no guessing about old backends); can_pause:false hides the control (server start / default assignment); pause_requested ren… |
| `src/app/settings/local-model-download-progress.tsx` | Exports `ProgressBar`, `gbLabel`, `DownloadStatusCopy`, `DownloadEtaCopy`, `formatSpeed`, `formatEta` … |
| `src/app/settings/local-models-actions.ts` | Exports `LocalModelsCopy`, `LocalModelsActionScope`, `useLocalModelsActionScope`, `isActiveStatus`, `runQuickstart`, `downloadCatalogModel` … |
| `src/app/settings/local-models-browse.tsx` | Exports `LocalModelsBrowseSection` |
| `src/app/settings/local-models-hardware-section.tsx` | Exports `LocalModelsHardwareSectionProps`, `LocalModelsHardwareSection` |
| `src/app/settings/local-models-model-rows.tsx` | Exports `CatalogModelRowProps`, `CatalogModelRow`, `SideloadedModelRowProps`, `SideloadedModelRow` |
| `src/app/settings/local-models-models-section.tsx` | Catalog display order: what runs well leads. Resident (all on GPU) first, then spilled (works, slower), then doesn't-fit; catalog order (recommended first) holds within each band. |
| `src/app/settings/local-models-owner.ts` | The pane remounts per owner and every request inside it must stay pinned to the owner it mounted with; re-deriving from the live stores in a child could retarget an in-flight action at the next connection or profile. |
| `src/app/settings/local-models-quickstart.tsx` | Exports `LocalModelsQuickstartProps`, `LocalModelsQuickstart` |
| `src/app/settings/local-models-runtime-section.tsx` | Exports `LocalModelsRuntimeSectionProps`, `LocalModelsRuntimeSection` |
| `src/app/settings/local-models-settings.test.tsx` | Tests: LocalModelsSettings; keeps a failed explicit update visible with a direct retry and no staged models; starts runtime installation only once while the request is pending; orders the catalog by fit: resident first,… |
| `src/app/settings/local-models-settings.tsx` | Exports `LocalModelsSettings` |
| `src/app/settings/managed-updates-section.tsx` | Exports `ManagedUpdatesSection` |
| `src/app/settings/memory/connect.tsx` | Exports `MemoryConnect` |
| `src/app/settings/memory/field-control.tsx` | Fade the placeholder well below set values so example text never reads as data. |
| `src/app/settings/memory/memory-layers.test.tsx` | Tests: memory layers; names the active provider and its readiness, and marks the built-in layer on by default; says built-in only when no external provider is configured; calls an unsaved draft |
| `src/app/settings/memory/memory-layers.tsx` | Exports `BuiltinToggles`, `memoryProviderRows`, `MemoryLayersSummary`, `MemoryLayersSlot`, `MemoryLayersPanel` |
| `src/app/settings/memory/provider-config-modal.test.tsx` | Tests: ProviderConfigModal; renders every field grouped, including inline ones, with kind-specific controls; saves only edited fields, serializing the toggled bool to |
| `src/app/settings/memory/provider-config-modal.tsx` | Exports `ProviderConfigModal` |
| `src/app/settings/memory/provider-config-panel.test.tsx` | Tests: ProviderConfigPanel; hides fields that are not marked inline; collapses and expands the fields; autosaves a text field on blur as a one-key partial save |
| `src/app/settings/memory/provider-config-panel.tsx` | Inline fields only: the compact panel must never re-write modal-owned keys. |
| `src/app/settings/minimize-to-tray-setting.test.tsx` | Tests: native truth drives both mounted settings rows and survives remount without renderer writes; failed writes roll back visibly, and an older initial read cannot overwrite a peer update |
| `src/app/settings/minimize-to-tray-setting.tsx` | Exports `MinimizeToTraySetting` |
| `src/app/settings/model-select.tsx` | Radix <Select> renders a blank trigger when `value` matches no <SelectItem>. A custom model (e.g. one added via config that isn't in the provider's curated list) would vanish — surface the active value so it stays selec… |
| `src/app/settings/model-settings.test.tsx` | Radix Select calls scrollIntoView on its items when the content opens; jsdom doesn't implement it (nor hasPointerCapture / releasePointerCapture), so stub them to let the dropdown open in tests. |
| `src/app/settings/model-settings.tsx` | Exports `ModelSettingsSkeleton`, `moaSlotComplete`, `moaConfigComplete`, `staleAuxAssignments`, `ModelSettings` |
| `src/app/settings/moved-tabs.test.ts` | Tests: movedSettingsTabRedirect; sends the retired Settings MCP tab to Capabilities, keeping the row selector; leaves live Settings tabs alone |
| `src/app/settings/moved-tabs.ts` | `plugins` used to redirect here too; it is a live Settings view again (Settings ▸ Plugins = each plugin's own settings pages). |
| `src/app/settings/notifications-settings.test.tsx` | Check that the visible sound control silences real cue callers without audio output. |
| `src/app/settings/notifications-settings.tsx` | Exports `NotificationsSettings` |
| `src/app/settings/onboarding-settings.test.tsx` | Tests: Settings > Run onboarding again; replays the whole first-run intro in a new chat; puts the user |
| `src/app/settings/onboarding-settings.tsx` | Advanced → Run onboarding again. |
| `src/app/settings/other-subpages.ts` | Gateway tasks and search rows that only native Desktop can act on; the Webapp's Gateways page is just its serving host (see WebappGatewaySettings). |
| `src/app/settings/pet-settings.tsx` | Exports `PetSettings` |
| `src/app/settings/plugin-install-details.tsx` | Exports `PinState`, `ProfileState`, `PluginInstallDetails` |
| `src/app/settings/plugin-install-modal.browser.test.tsx` | The browser-hosted app: no Electron preload, so no `window.hermesDesktop.probePluginRepo` and no `installDesktopPlugin`. Inspection and install both ride the gateway. |
| `src/app/settings/plugin-install-modal.test.tsx` | The host tab lists installed plugins on mount; only an `install` action counts as installing. |
| `src/app/settings/plugin-install-modal.tsx` | Exports `PluginInstallModal` |
| `src/app/settings/plugin-install-review-guards.test.tsx` | What an install dialog may put down besides the commit it showed: only what the user explicitly chose. An older backend that cannot hold the install to that commit asks first; a catalog pick is held to the pin the backe… |
| `src/app/settings/plugin-install-run.ts` | Exports `ProbeResult`, `InstallModalCopy`, `InstallComponents`, `desktopInstallSupported`, `installComponents`, `skipsDesktopHalf` … |
| `src/app/settings/plugin-install-source-moved.test.tsx` | The source moves between the dialog's inspection and Install. The refusal says so with a structured marker; the dialog must read the source again and show the new commit, never resend the old one. |
| `src/app/settings/plugin-settings-form.test.tsx` | Tests: PluginSettingsForm (#46600, #87934); renders one control per schema type from the table, secrets masked with no value echoed; submits only what changed, coerced to wire types, secrets routed by env name; clears s… |
| `src/app/settings/plugin-settings-form.tsx` | A plugin manifest's `config_schema` rendered as a form. Every non-secret value is edited as TEXT (the draft) and coerced to its wire type on save, so a half-typed number never fights the input; secrets are drafted separ… |
| `src/app/settings/plugin-settings-ownership.test.tsx` | Review regressions for Settings ▸ Plugins (PR #133182): every scenario here reproduced natively against a real backend. Each test drives the REAL route hook under a router, so the URL contract is exercised, not a local… |
| `src/app/settings/plugin-settings.test.tsx` | Tests: Settings ▸ Plugins; lists every plugin with settings and walks into a sub-page, WoW-AddOns style; renders a config_schema page that saves through plugins.manage settings; drops a disabled plugin’s page from the l… |
| `src/app/settings/plugin-settings.tsx` | Exports `OpenPluginSettings`, `PLUGINS_NAV_ICON`, `PAGE_SCOPED_PARAMS`, `usePluginSettingsRoute`, `usePluginSettingsEntries`, `pluginSettingsNavChildren` … |
| `src/app/settings/primitives.tsx` | The settings shell owns page titles; embedded callers retain their headings. |
| `src/app/settings/profile-scope.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/profile-scope.tsx` | Exports `settingsScopeLabel`, `ScopeChip`, `SettingsProfileScope`, `ActiveProfileNote` |
| `src/app/settings/providers-settings.terminal-disconnect.test.tsx` | Tests: connected external provider row; runs the terminal control as disconnect instead of starting sign-in; does not toast success when an API clear reports nothing was removed |
| `src/app/settings/providers-settings.test.tsx` | Tests: ProvidersSettings; reads and saves API keys for the shared Settings target and reloads when it changes; uses the settings target for account reads, removal and sign-in; disconnects a connected provider account an… |
| `src/app/settings/providers-settings.tsx` | Exports `PROVIDER_VIEWS`, `ProviderView`, `ProvidersSettings` |
| `src/app/settings/quick-entry-settings.tsx` | Exports `QuickEntrySettings` |
| `src/app/settings/screenshot-settings.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/screenshot-settings.tsx` | Exports `ScreenshotSettings` |
| `src/app/settings/searchable-select.test.tsx` | Tests: rankSearchOption; ranks a final-segment match above a mid-path match; is case-insensitive; scores a slashless option by plain substring |
| `src/app/settings/searchable-select.tsx` | Exports `rankSearchOption`, `SearchableSelect` |
| `src/app/settings/sessions-settings.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/sessions-settings.tsx` | Exports `SessionsSettings` |
| `src/app/settings/settings-manifest.ts` | Exports `SettingDefinition`, `SETTINGS_MANIFEST`, `ManifestViewKey`, `manifestView`, `settingId`, `notificationKindSettingId` … |
| `src/app/settings/settings-search.test.ts` | Tests: settings search index; builds config results from renderable schema fields with exact deep links; discovers future tool and setting entries entirely from backend metadata; shares the Tools and Settings category b… |
| `src/app/settings/settings-search.ts` | Exports `CredentialSettingsView`, `SettingsSearchTarget`, `SettingsSearchEntry`, `credentialSettingsView`, `buildConfigSearchEntries`, `buildCredentialSearchEntries` … |
| `src/app/settings/shared-metrics-settings.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/shared-metrics-settings.tsx` | Exports `SharedMetricsSettings` |
| `src/app/settings/ssh-host-selection.test.ts` | Tests: selectSshHost; clears host-specific fields when the selected host changes; preserves state when reselecting the same host; enriches only the host that produced the ssh config result |
| `src/app/settings/ssh-host-selection.ts` | TypeScript source: `ssh-host-selection` |
| `src/app/settings/stale-aux-dismissal.test.ts` | Tests: staleAuxFingerprint; binds the acknowledgement to the main provider and the pinned slots; is order-insensitive across slots; includes the slot endpoint, so a repointed base_url re-arms the banner |
| `src/app/settings/stale-aux-dismissal.ts` | Acknowledged stale-aux banner. The warning exists to catch a forgotten pin silently billing a dead provider; a user with a deliberate cross-provider pin (e.g. vision on the only provider that offers it, #66740) would |
| `src/app/settings/subagents-destination.test.ts` | Tests: Subagents settings destination; distinguishes Subagents from Mixture of Agents in navigation; moves every delegation field, including config-present fields, into Model only; keeps old Advanced bookmarks and field… |
| `src/app/settings/subpage-navigation.tsx` | Exports `SettingsSubpageHeader` |
| `src/app/settings/subpages.test.ts` | Tests: settings subpage routing; opens the first ordered child for parents and keeps explicit child destinations; gives the Webapp Gateways page no native-only children or search rows; gives every settings group its own… |
| `src/app/settings/subpages.ts` | Exports `SettingsSubpage`, `settingsSubpageIcon`, `settingsSubpages`, `settingsSubpageForTarget`, `settingsSubpageForLegacyLink`, `resolveSettingsSubpage` |
| `src/app/settings/terminal-backend-panel.test.tsx` | Tests: TerminalBackendPanel; reads and writes the profile currently selected by Capabilities; marks the active backend as pressed; selects a backend when clicked and reports the change |
| `src/app/settings/terminal-backend-panel.tsx` | Exports `TerminalBackendPanel` |
| `src/app/settings/terminal-font-setting.test.tsx` | @vitest-environment jsdom |
| `src/app/settings/terminal-font-setting.tsx` | Exports `TerminalFontSetting` |
| `src/app/settings/test-utils.ts` | An unset secret in `category`. The Keys tab and the settings search both bucket by category and branch on `is_set`, so those are what tests vary. |
| `src/app/settings/toolset-config-panel.test.tsx` | Collect the component graph before the behavioral test deadline starts. |
| `src/app/settings/toolset-config-panel.tsx` | Exports `ToolsetConfigPanel` |
| `src/app/settings/types.ts` | Exports `SettingsView`, `EnvPatch`, `SettingsPageProps`, `ProviderGroup`, `DesktopConfigSection`, `EnvRowProps` |
| `src/app/settings/uninstall-section.test.tsx` | Tests: keeps owned-install removal modes and confirms the selected mode; shows native removal steps, data location, and Apps settings on a managed Windows install |
| `src/app/settings/uninstall-section.tsx` | Exports `UninstallSection` |
| `src/app/settings/update-channel-row.tsx` | Exports `UpdateChannelRow` |
| `src/app/settings/use-deep-link-highlight.ts` | Exports `useDeepLinkHighlight` |
| `src/app/settings/use-plugin-probe.test.ts` | Tests: usePluginProbe; answers unavailable when neither Electron nor the gateway can inspect; keeps the newest inspection when an older gateway answer lands late; drops an answer that lands after cancel |
| `src/app/settings/use-plugin-probe.ts` | Exports `GatewayProbe`, `usePluginProbe` |
| `src/app/settings/use-setting-deep-link.ts` | Land a palette hit (`?setting=<id>`) on a manifest row of this view: once the row's subpage is showing, scroll to it and flash it. Pages with no subpages pass no `show`; pages with subpages pass the same predicate that… |
| `src/app/settings/use-settings-search.ts` | An installed plugin row, deep-linkable as `/capabilities?tab=plugins&plugin=<id>`. |
| `src/app/settings/vault-settings.owner.test.tsx` | Every vault RPC is routed to the OWNER profile's socket; the mock records which profile each call targeted so the tests can prove a draft never crosses owners. |
| `src/app/settings/vault-settings.test.tsx` | Tests: VaultSettings; routes every vault RPC through the active connection, not a bare profile name; opens the Add dialog pre-filled from deep-link query params (never secrets); validates the origin before submitting a… |
| `src/app/settings/vault-settings.tsx` | Exports `vaultOwnerKey`, `VaultSourceName`, `VaultSource`, `VaultKind`, `VaultPrefill`, `VaultSettings` |
| `src/app/settings/voice-field-visible.test.ts` | Tests: voiceFieldVisible; always shows top-level + non-provider keys; shows only the selected TTS provider sub-fields; shows only the selected STT provider sub-fields |
| `src/app/settings/voice-provider-fields.test.ts` | Tests: voiceProviderKeys; covers every built-in TTS provider the Capabilities picker offers; scopes to the exact provider segment (no prefix bleed); voice field option coverage |
| `src/app/settings/voice-provider-fields.tsx` | Exports `voiceProviderKeys`, `VoiceProviderFields` |
| `src/app/settings/web-access-settings.test.tsx` | Tests: WebAccessSettings; offers Start only with a Nous account to sign in with; says why the gateway cannot serve a turned-on web app; never reports a web app the gateway still serves as stopped |
| `src/app/settings/web-access-settings.tsx` | Exports `useWebAccessAvailable`, `WebAccessSettings` |
| `src/app/settings/webapp-gateway-settings.tsx` | Exports `WebappGatewaySettings` |
| `src/app/settings/with-active.test.ts` | A Radix <Select> shows a blank trigger when its `value` matches no <SelectItem>. `withActive` guarantees the controlled value is always representable so a config-only / custom model never renders blank. |
| `src/app/shell/approval-mode-menu.test.tsx` | Tests: approval mode statusbar item; writes the selected mode through the gateway and updates its shared trigger label; syncs once the gateway opens instead of sitting on the pre-sync default |
| `src/app/shell/approval-mode-menu.tsx` | Exports `useApprovalModeStatusbarItem` |
| `src/app/shell/butterbar.css` | One tint drives the whole bar. A tone picks a palette token; a custom `color` sets --bb-tint inline. Every other color is mixed from that tint against the live theme (chrome + foreground), so any hue lands readable in l… |
| `src/app/shell/butterbar.tsx` | Exports `Butterbar` |
| `src/app/shell/context-usage-panel.test.tsx` | Tests: useContextBreakdown; fetches for a session that has not run a turn yet; does not fetch while the gauge is hidden, and fetches once it is shown; skips the estimate mid-turn — the gateway streams measured usage then |
| `src/app/shell/context-usage-panel.tsx` | Exports `ContextUsagePanel`, `ContextMeterDetail` |
| `src/app/shell/gateway-menu-panel.test.tsx` | Tests: GatewayMenuPanel reconnect action; shows reconnect while disconnected and disables it in flight; allows recovery when an open socket stops delivering |
| `src/app/shell/gateway-menu-panel.tsx` | Exports `GatewayMenuPanel` |
| `src/app/shell/group-setter.ts` | The `GroupSetter` shape pages take as an extension-point prop (CapabilitiesView, MessagingView, ChatPreviewRail, …). The live implementation is the registry-backed `registryGroupSetter` in app/contrib/panes.tsx. |
| `src/app/shell/hooks/use-change-workspace.ts` | Exports `useChangeWorkspaceItem` |
| `src/app/shell/hooks/use-context-breakdown.test.ts` | Tests: useContextBreakdown (#94001); caches a live breakdown keyed by session and serves it across busy toggles; drops the cached breakdown when the session changes (no cross-session contamination); evicts the stale cac… |
| `src/app/shell/hooks/use-context-breakdown.ts` | Exports `invalidateContextBreakdown`, `_resetContextBreakdownInvalidationsForTests`, `useContextBreakdown` |
| `src/app/shell/hooks/use-focused-session-row.ts` | The focused session's stored row scalars: its cold/fallback start time and cwd, and the gateway it runs on (a Connections-tagged row names its gateway; an untagged one is the window's primary, which decides whether the… |
| `src/app/shell/hooks/use-overlay-routing.ts` | Exports `useOverlayRouting` |
| `src/app/shell/hooks/use-status-snapshot.test.ts` | Tests: useStatusSnapshot; drops the free-tier verdict on a profile or source switch, not on a gateway flap; pauses status RPCs while visible but unfocused, then catches up on focus; keeps the last authoritative readines… |
| `src/app/shell/hooks/use-status-snapshot.ts` | Statusbar health is ambient chrome, not live data — nothing the user acts on within seconds. 60s + an actively-viewed check keeps traffic low; focus and visibility listeners refresh immediately on return. |
| `src/app/shell/hooks/use-statusbar-items.lifecycle.test.tsx` | Tests: statusbar context usage lifecycle; keeps live usage at turn end until a fresh idle breakdown arrives; does not restore the pre-turn snapshot when the idle refresh fails |
| `src/app/shell/hooks/use-statusbar-items.test.tsx` | Tests: statusbar update channel vocabulary; names a stable release update without presenting its commit distance; names a stable release older than the checkout as a rollback; statusbar workspace menu — |
| `src/app/shell/hooks/use-statusbar-items.tsx` | Exports `useStatusbarItems` |
| `src/app/shell/hooks/use-window-controls-overlay-width.ts` | Measure the EXACT width of the native window-controls overlay (min/max/close) straight from the browser, instead of a hardcoded reservation. When Electron's Window Controls Overlay is active (native Windows AND WSLg), |
| `src/app/shell/local-setup-menu-row.tsx` | "Run locally" at the top of the composer's model menu, for as long as this machine qualifies and nothing is set up. Every menu open re-reads eligibility (a user action, not a poll), so finishing setup retires the row. A… |
| `src/app/shell/model-catalog-menu.search-fold.test.tsx` | Radix calls these on open; jsdom doesn't implement them. |
| `src/app/shell/model-catalog-menu.test.tsx` | Tests: model menu row decorations (MODEL_MENU_ROW_AREA); paints a contributed icon and badge in the row slots, skipping a throwing decorator; the current row effort; does not label the current model with the profile def… |
| `src/app/shell/model-catalog-menu.tsx` | Exports `ModelMenuCloseContext`, `ModelChoice`, `ModelMenuController`, `ModelCatalogMenu` |
| `src/app/shell/model-edit-submenu.test.tsx` | Tests: ModelEditSubmenu reports edits without performing them; param fast: reports the toggle; thinking: toggling off reports the none level; thinking: toggling back on restores the row level, not the hardcoded default |
| `src/app/shell/model-edit-submenu.tsx` | Exports `FastControl`, `resolveFastControl`, `ModelEditSubmenu`, `ModelOptionsContent` |
| `src/app/shell/model-menu-panel.test.tsx` | Radix calls these on open; jsdom doesn't implement them. |
| `src/app/shell/model-menu-panel.tsx` | Exports `ModelMenuPanel` |
| `src/app/shell/model-menu-row-decorations.tsx` | Model menu row decorations — a plugin's per-model mark inside the native model catalog menu (the composer's model pill menu and every other surface that renders `ModelCatalogMenu`). data kind (`data`): modelMenu.row (Mo… |
| `src/app/shell/reasoning-menu-panel.tsx` | The composer's reasoning menu: the same options rows the catalog shows per model row (Thinking / Fast / Effort), opened directly for the ACTIVE model from its own pill. Same controller as the model menu, so an edit here… |
| `src/app/shell/sidebar-label.tsx` | Exports `SidebarPanelLabel` |
| `src/app/shell/statusbar-context-menu.test.tsx` | Tests: statusbar context menu coordination; lets the statusbar Radix menu handle right-clicks instead of the app fallback (#89953) |
| `src/app/shell/statusbar-controls.tsx` | Exports `StatusbarMenuItem`, `StatusbarItem`, `StatusbarSelectModifiers`, `StatusbarItemSide`, `SetStatusbarItemGroup`, `StatusbarControls` |
| `src/app/shell/statusbar-visibility.test.tsx` | Tests: statusbar item visibility; shows an item once the user enables it from the bar context menu; never lets the user hide a locked item (system icon / update pill); leaves items that never opted into the menu alone |
| `src/app/shell/system-resources-statusbar.test.tsx` | The poll fires getLocalHardware() every 5s while the item is shown; the backend spawns nvidia-smi per poll, so a hidden window must stop polling entirely and resume on visibilitychange (#120262). |
| `src/app/shell/system-resources-statusbar.tsx` | Live host-resource readout for the bottom bar: GPU utilization + VRAM + RAM, fed by /api/local-models/hardware. Hidden by default (an item most users don't watch); the poll runs ONLY while the item is shown, so the |
| `src/app/shell/terms-butterbar.tsx` | Exports `TermsButterbar` |
| `src/app/shell/titlebar-controls.test.tsx` | @vitest-environment jsdom |
| `src/app/shell/titlebar-controls.tsx` | Exports `TitlebarTool`, `TitlebarToolSide`, `SetTitlebarToolGroup`, `TitlebarControls` |
| `src/app/shell/titlebar-icon.tsx` | Titlebar-cluster glyph — 13.9px inline (see titlebarIconSizeCss). |
| `src/app/shell/titlebar.test.ts` | Tests: titlebarControlsPosition; offsets controls from visible traffic lights; pins to the edge when macOS fullscreen hides traffic lights; pins to the edge on Windows/Linux where native controls render on the right |
| `src/app/shell/titlebar.ts` | Exports `TITLEBAR_HEIGHT`, `TOUCH_TITLEBAR_HEIGHT`, `TITLEBAR_DRAG_HANDLE_WIDTH`, `MACOS_TRAFFIC_LIGHTS_HEIGHT`, `TITLEBAR_CONTROL_SIZE`, `TITLEBAR_ICON_SIZE` … |
| `src/app/shell/use-model-menu-controller.test.tsx` | Tests: a level picked while a reply streams applies from the next message instead of failing (MP-24) |
| `src/app/shell/use-model-menu-controller.ts` | Exports `ModelSelection`, `ModelMenuHostProps`, `useModelMenuController` |
| `src/app/shell/use-touch-titlebar.ts` | Browser touch chrome needs a 44px band, not Electron's compact 34px band. |
| `src/app/shell/wslg-window-controls.test.tsx` | Tests: WslgWindowControls; routes minimize, maximize and close through the desktop bridge; exposes restore semantics while maximized; stays hidden while the BrowserWindow is fullscreen |
| `src/app/shell/wslg-window-controls.tsx` | Exports `WslgWindowControls` |
| `src/app/starmap/color.ts` | Theme tokens come through `color-mix()`/oklch, so getComputedStyle returns a non-rgb() string. Rasterize through a 1x1 canvas to get real sRGB bytes — naive string parsing of oklab()/color(srgb …) silently yields black. |
| `src/app/starmap/constants.ts` | ── Disk geometry ──────────────────────────────────────────────────────────── |
| `src/app/starmap/context-menu-handle.ts` | Registered context-menu ownership for the Star Map canvas. The app-wide menu listens on window during capture, before React's canvas handler. It asks this handle whether the click hit a node: hits belong to the Star Map… |
| `src/app/starmap/geometry.ts` | Exports `clamp`, `hash`, `nodeRadius`, `recencyInk`, `shapePath`, `fitViewport` … |
| `src/app/starmap/index.tsx` | Star map overlay: a top-down map of what Hermes has learned for a profile, over a radial time axis. Data is fetched on demand into the $starmap* atoms; the map itself lives in ./star-map. The chrome is owned by the map… |
| `src/app/starmap/node-context-menu.test.tsx` | Tests: NodeContextMenu; keeps the destructive row functional through the shared menu |
| `src/app/starmap/node-context-menu.tsx` | Exports `NodeMenuTarget`, `NodeContextMenu` |
| `src/app/starmap/playback-hotkey.test.ts` | Tests: shouldIgnorePlaybackHotkey; toggles on Space when nothing focusable owns the key; ignores Space on a focused Radix menu item (div[role=menuitem] inside role=menu) |
| `src/app/starmap/playback-hotkey.ts` | Decide whether a window-level Space keydown should be ignored by the Star Map playback toggle. Ignored when the key is not Space, when something already handled it (`defaultPrevented`), when the user is typing or the fo… |
| `src/app/starmap/render.ts` | Exports `Scene`, `DrawResult`, `drawScene`, `drawScramble` |
| `src/app/starmap/share-code.test.ts` | Tests: share-code; preserves the visualization; drops memory prose (loadout is viz-only); rebuilds clusters from node categories |
| `src/app/starmap/share-code.ts` | ── Star-map share code ─────────────────────────────────────────────────────── The body schema for a star map, riding the generic loadout codec (@/lib/loadout owns the bitstream, DEFLATE, version+checksum frame, and bas… |
| `src/app/starmap/share-controls.test.tsx` | Tests: ShareControls; opens its dialog when the trigger has a tooltip |
| `src/app/starmap/share-controls.tsx` | Exports `ShareControls` |
| `src/app/starmap/simulation.ts` | Exports `BuiltSim`, `buildSimulation` |
| `src/app/starmap/star-map-context-menu.test.tsx` | Tests: StarMap context menu ownership; keeps the canvas gesture so a node can open its Edit/Delete menu; keeps the shell fallback on empty starfield |
| `src/app/starmap/star-map.tsx` | How long a full play-through sweep takes (ms), reveal 0 → 1. Longer = the build-up breathes; the eased middle no longer rushes past in a blink. |
| `src/app/starmap/text.ts` | Exports `formatDate`, `metaBadges`, `countLabel`, `nodeFooter`, `wrapText`, `ellipsize` |
| `src/app/starmap/time-axis.ts` | Empty lead-in: push the oldest node off 0 so the timeline opens on a beat of emptiness (you watch the first node grow in). Radial position is otherwise a truthful linear map of time, so rings line up with the nodes they… |
| `src/app/starmap/timeline.tsx` | Exports `Timeline` |
| `src/app/starmap/types.ts` | Exports `MemoryCard`, `Shape`, `Viewport`, `Rgb`, `Rect`, `SimNode` … |
| `src/app/types.ts` | Exports `ContextSuggestion`, `ImageAttachResponse`, `ImageDetachResponse`, `FileAttachResponse`, `SlashExecResponse`, `BrowserManageResponse` … |
| `src/app/updates-overlay.channel.test.tsx` | Tests: offers Change only where Settings can switch; a custom branch or older runtime gets the label alone |
| `src/app/updates-overlay.manual.test.tsx` | Tests: shows manual recovery guidance without claiming the help command installs an update; titles a command-less backend refusal honestly and offers nothing to copy; names the backend, not a local install, when a remot… |
| `src/app/updates-overlay.tsx` | Exports `UpdatesOverlay` |
| `src/app/wake-indicator/wake-indicator-app.tsx` | Exports `WakeIndicatorApp` |
| `src/app/wake-indicator/wake-indicator-root.tsx` | Exports `mountWakeIndicator` |
| `src/app/wake-indicator/wake-indicator.css` | Stylesheet |
| `src/app/webhooks/index.test.tsx` | Tests: WebhooksView profile ownership; drops the create draft when the backend profile changes under All profiles; ignores a create completion owned by the previous profile; accepts a create completion after the StrictM… |
| `src/app/webhooks/index.tsx` | Exports `WebhooksView` |
| `src/assets/catalog-wing-retro.svg` | SVG vector image |
| `src/assets/catalog-wing.svg` | SVG vector image |
| `src/assets/tiers/feature-automation.webp` | WebP image asset |
| `src/assets/tiers/feature-connect.webp` | WebP image asset |
| `src/assets/tiers/feature-memory.webp` | WebP image asset |
| `src/assets/tiers/feature-sandbox.webp` | WebP image asset |
| `src/components/Backdrop.tsx` | Exports `Backdrop` |
| `src/components/assistant-ui/ansi-text.tsx` | Exports `AnsiText` |
| `src/components/assistant-ui/artifact-card.tsx` | Exports `ArtifactCard` |
| `src/components/assistant-ui/catalog-advanced-dialog.tsx` | Exports `CatalogAdvancedDialog` |
| `src/components/assistant-ui/catalog-install-tool.test.tsx` | Tests: the catalog install card; draws plugin and skill rows as catalog items with their purpose, and a platform only when restricted; sends defaults from the row, the modal values from Advanced, and nothing on Cancel;… |
| `src/components/assistant-ui/catalog-install-tool.tsx` | Exports `CatalogInstallTool`, `CatalogInstallCard`, `CatalogRow` |
| `src/components/assistant-ui/chat-empty-slot.test.tsx` | The `chat.empty` slot mounts EVERY contributor, not just the first. Ownership of an empty transcript is per session and is not known until each plugin has loaded its own data, so a first-wins slot let whichever plugin h… |
| `src/components/assistant-ui/chat-empty-slot.tsx` | The empty transcript's contributed slot. Mounts every registration and lets each decide — it renders the session's empty state, or nothing at all if the session isn't one it owns. Deliberately a mount rather than a clai… |
| `src/components/assistant-ui/clarify/clarify-one-card-per-question.test.tsx` | A canonical gateway asks a multi-question clarify one card per question when the submitter did not declare `clarify_batch` (gateway/run_turn_runner.py::_clarify_callback_sync). Each card is a new request that re-arms th… |
| `src/components/assistant-ui/clarify/clarify-tool.test.tsx` | The OWNER-socket seam (`requestForOwnedSession` → `requestForSessionProfile` → here). Mocked so the real owner ladder still runs against real fixtures and only the dial is observed; the rest of the gateway store stays a… |
| `src/components/assistant-ui/clarify/core/choice-row.tsx` | Exports `letterFor`, `ChoiceLabel`, `OPTION_ROW_CLASS`, `KeyBadge`, `ChoiceButton` |
| `src/components/assistant-ui/clarify/core/confirm-bar.tsx` | Exports `ClarifyConfirmBar` |
| `src/components/assistant-ui/clarify/core/question-block.tsx` | Exports `QuestionBlock`, `emptyStage` |
| `src/components/assistant-ui/clarify/core/shell.tsx` | field-sizing on top of Textarea's shared chrome; kill min-h-16 for one-liners. |
| `src/components/assistant-ui/clarify/core/use-clarify-keys-handlers.ts` | Exports `isForeignKeystroke`, `arrowMove`, `shortcutIndex` |
| `src/components/assistant-ui/clarify/core/use-clarify-keys.ts` | Exports `useClarifyKeys` |
| `src/components/assistant-ui/clarify/index.tsx` | Exports `ClarifyTool` |
| `src/components/assistant-ui/clarify/parse.ts` | Exports `ClarifyArgs`, `readClarifyArgs`, `ClarifyResponse`, `readClarifyResult` |
| `src/components/assistant-ui/clarify/pending.tsx` | Exports `ClarifyToolPending` |
| `src/components/assistant-ui/clarify/settled.tsx` | Settled batch card: every question with its locked (or absent) answer. |
| `src/components/assistant-ui/clarify/submit-shortcut.ts` | Use the form's enabled submit button so validation and pending state agree. |
| `src/components/assistant-ui/clarify/undelivered-notice.tsx` | Heads a card whose request never reached this window: nothing on it can answer, so say so and point at the way out instead of a silent wait. |
| `src/components/assistant-ui/clarify/use-undelivered.ts` | How long a painted card may wait for its gateway request before asking the backend to re-deliver it. `clarify.request` normally trails `tool.start` by a tick; seconds of silence mean the frame was lost on the way. |
| `src/components/assistant-ui/connector-directory-card.test.tsx` | Tests: ConnectorDirectoryCard; pins Suggested rows first in the given order, then the most used apps, and Continue reports the result; collapses to one receipt line naming what the user connected once the call returns |
| `src/components/assistant-ui/connector-directory-card.tsx` | Exports `ConnectorDirectoryResult`, `ConnectorDirectoryCardProps`, `DirectorySections`, `directorySections`, `ConnectorDirectoryCard` |
| `src/components/assistant-ui/connector-order.ts` | The onboarding apps step's order: the most used apps lead; apps turned off and a hidden few are left out. |
| `src/components/assistant-ui/connector-tool.test.tsx` | Tests: ConnectorOffer named-account notice; says which name Hermes chose once the account connected, and Rename opens that account (by id) on the Connectors tab; ConnectorTool operation card; offers one verb per row and… |
| `src/components/assistant-ui/connector-tool.tsx` | Exports `openConnectionDoneLink`, `reissueConnectionTarget`, `connectionRequestOwnsPart`, `ConnectorTool`, `ConnectorDirectoryReceipt`, `CONNECTOR_CARD_PHASES` … |
| `src/components/assistant-ui/directive-blob-image.test.tsx` | @vitest-environment jsdom |
| `src/components/assistant-ui/directive-chip-links.test.tsx` | Tests: sent-message url chip; escapes to the system browser on the platform open-elsewhere modifier; escapes to the system browser on middle-click |
| `src/components/assistant-ui/directive-text.test.ts` | Tests: formatRefValue; leaves simple paths untouched; wraps paths with whitespace in backticks; falls back to double quotes when value contains backticks |
| `src/components/assistant-ui/directive-text.tsx` | Exports `refAttrs`, `refAttrsHtml`, `directiveIconSvg`, `directiveIconElement`, `SlashChipKind`, `slashIconElement` … |
| `src/components/assistant-ui/embeds/alert.test.tsx` | Tests: extractAlert; detects each GFM alert kind from the leading marker; is case-insensitive on the marker; returns null for a plain blockquote |
| `src/components/assistant-ui/embeds/alert.tsx` | Exports `AlertType`, `extractAlert`, `MarkdownAlert` |
| `src/components/assistant-ui/embeds/embed-consent.tsx` | Privacy placeholder shown before an embed reaches out to a third party. Sized to the embed's footprint (no layout shift). The split control mirrors the commit button: primary "Load" (this embed) with a caret for "Always… |
| `src/components/assistant-ui/embeds/embed-size.ts` | Shared height cap for inline embeds. Ratio embeds cap their width off this in UrlEmbed so height follows the aspect ratio; fenced renderers (mermaid, svg) reuse it directly. Pure CSS — no measuring. |
| `src/components/assistant-ui/embeds/fail.tsx` | Exports `EmbedFail` |
| `src/components/assistant-ui/embeds/frame-embed.tsx` | Exports `FrameEmbedRenderer` |
| `src/components/assistant-ui/embeds/index.ts` | TypeScript source: `index` |
| `src/components/assistant-ui/embeds/listing-embed.tsx` | The conversation's own type scale, so a card reads at the prose's size. |
| `src/components/assistant-ui/embeds/mermaid-embed.test.tsx` | Tests: MermaidRenderer; reuses one render while isolating each mounted SVG in an image resource; repairs a label mermaid returned as HTML, so the image stays loadable |
| `src/components/assistant-ui/embeds/mermaid-embed.tsx` | Exports `MermaidRenderer` |
| `src/components/assistant-ui/embeds/mermaid-render-cache.test.ts` | Tests: createMermaidRenderCache; shares in-flight work and reuses the completed SVG; caches themes separately and serializes cache misses; removes failed work so a later mount can retry |
| `src/components/assistant-ui/embeds/mermaid-render-cache.ts` | Exports `MermaidTheme`, `nextPaint`, `createRetryableLoader`, `createMermaidRenderCache` |
| `src/components/assistant-ui/embeds/providers/detect.test.ts` | Tests: detectEmbed — YouTube; carries a start time from t/start through to the embed; rejects ids that are not 11 chars; detectEmbed — other frame providers |
| `src/components/assistant-ui/embeds/providers/index.ts` | Exports `detectEmbed`, `isEmbeddableUrl` |
| `src/components/assistant-ui/embeds/providers/instagram.ts` | Exports `instagram` |
| `src/components/assistant-ui/embeds/providers/maps.ts` | `@lat,lng` (optionally `,<zoom>z`) as it appears in Google Maps URLs. |
| `src/components/assistant-ui/embeds/providers/pinterest.ts` | Exports `pinterest` |
| `src/components/assistant-ui/embeds/providers/spotify.ts` | Spotify's embed has only two layouts: compact (≤152) and full (352). Any in-between height renders the compact player and pads the rest with grey, so we snap to the compact size for every type — tight, no dead space. |
| `src/components/assistant-ui/embeds/providers/tiktok.ts` | Exports `tiktok` |
| `src/components/assistant-ui/embeds/providers/twitter.ts` | Exports `twitter` |
| `src/components/assistant-ui/embeds/providers/types.ts` | Embed provider model. Detection is pure, synchronous, and dependency-free so it is safe to run during render and trivial to unit-test. Rendering lives in the lazy renderers (see ../registry.tsx) keyed off `renderer`. |
| `src/components/assistant-ui/embeds/providers/vimeo.ts` | Exports `vimeo` |
| `src/components/assistant-ui/embeds/providers/youtube.ts` | Exports `youtube` |
| `src/components/assistant-ui/embeds/registry.tsx` | Root renderer for fenced code blocks: a language → lazy-renderer table. Each renderer is split and loaded only when a block of that language appears. The Mermaid renderer defers its heavier runtime import until after it… |
| `src/components/assistant-ui/embeds/rich-boundary.tsx` | Exports `RichBoundary` |
| `src/components/assistant-ui/embeds/scroll-gate.tsx` | Block wheel until ⌘/Ctrl so map embeds don't hijack transcript scroll. |
| `src/components/assistant-ui/embeds/social-embed.test.tsx` | Tests: SocialEmbedRenderer; ignores height messages from another origin or another window |
| `src/components/assistant-ui/embeds/social-embed.tsx` | X and Instagram render in the provider's own cross-origin iframe, like every other embed. Their widget scripts (widgets.js / embed.js) must never run in this document: it is the privileged app window, and any script her… |
| `src/components/assistant-ui/embeds/spotify-embed.tsx` | Exports `SpotifyEmbedRenderer` |
| `src/components/assistant-ui/embeds/svg-embed.tsx` | Lazy chunk (pulls in DOMPurify). Renders a ```svg fence as an image after hard-sanitising it: the svg profile strips scripts, event handlers, and foreignObject, so untrusted model output can't execute. |
| `src/components/assistant-ui/embeds/types.ts` | Shared prop contract for fenced-block renderers (mermaid, svg). Kept in its own module so renderers and the registry can both import it without a cycle. |
| `src/components/assistant-ui/embeds/url-embed.tsx` | Exports `UrlEmbed` |
| `src/components/assistant-ui/embeds/use-is-dark.ts` | Exports `useIsDark` |
| `src/components/assistant-ui/embeds/youtube-embed.test.tsx` | Tests: YouTubeEmbedRenderer; embeds directly with its own origin on an http renderer, never asking for the host; maps the player URL onto the loopback wrapper with the same video and params |
| `src/components/assistant-ui/embeds/youtube-embed.tsx` | Exports `wrappedYoutubeSrc`, `YouTubeEmbedRenderer` |
| `src/components/assistant-ui/inline-preview-directive.test.ts` | Tests: directiveFrameHeight; returns null (auto-size) when absent or garbage; clamps an explicit height to the sane band; withInlineChrome |
| `src/components/assistant-ui/inline-preview-directive.tsx` | `::preview{file="…"}` — a workspace HTML file rendered LIVE inside the assistant message. A sandboxed iframe with an opaque origin (`sandbox="allow-scripts"`, deliberately no `allow-same-origin`): scripts run and the wi… |
| `src/components/assistant-ui/markdown-table.tsx` | Exports `ResizableMarkdownTable`, `ResizableMarkdownTh` |
| `src/components/assistant-ui/markdown-text.artifacts.test.tsx` | Tests: MarkdownTextContent artifacts; renders a substantial html fence as an artifact card and registers it; keeps a small fence as a plain code block; does not register while the message is still streaming |
| `src/components/assistant-ui/markdown-text.bare-url.test.tsx` | Tests: MarkdownTextContent bare URLs; shows the full URL text for a bare autolink; does not collapse a host-only URL to a bare hostname; keeps the authored label for a labeled markdown link |
| `src/components/assistant-ui/markdown-text.filelinks.test.tsx` | Regression for #82140: a plain filesystem href in assistant markdown (`[report](/home/user/report.md)`) rendered as a bare dead anchor — file:// is blocked in the renderer, and on a remote gateway the path |
| `src/components/assistant-ui/markdown-text.linklabels.test.tsx` | Regression for #121321: authored markdown link labels are the text the model wrote, and formatted labels count. An inline-code label ([`v1.0.1`](url)) used to be dropped by childrenToText (it only handled |
| `src/components/assistant-ui/markdown-text.media-md.test.tsx` | Regression for #84951: a `.md` delivered via MEDIA has no entry in MEDIA_BY_EXT, so it classified as a generic 'file' and rendered as a download-style link. Markdown is renderable content — it must route to the |
| `src/components/assistant-ui/markdown-text.media.test.tsx` | Tests: MarkdownTextContent remote images; passes the gateway bridge data URL through Streamdown to the zoomable image; MarkdownImage media routing; renders a <video> (not a broken <img>) for a video source |
| `src/components/assistant-ui/markdown-text.overflow.test.tsx` | Regression coverage for the "workspace failed to render / Maximum call stack size exceeded" crash loop (#78000, #85295). Two independent recursions in the markdown pipeline can overflow the JS call |
| `src/components/assistant-ui/markdown-text.prose-safety.test.tsx` | Render-level regression for the prose-safety preprocessor fixes that landed on 2026-08-22 (upstream #50871 lone-tilde strikethrough, #53953 unknown html-like tokens swallowing the message tail). The preprocessor unit te… |
| `src/components/assistant-ui/markdown-text.reasoning.test.tsx` | The real surface re-renders preprocessMarkdown → Streamdown on the accumulated text every flush, so a settled message never shows this bug: only frames do. |
| `src/components/assistant-ui/markdown-text.session.test.tsx` | Tests: MarkdownTextContent session refs; renders an agent-written @session ref as a link showing the session title; falls back to a short id when the session is unknown; leaves a ref inside inline code as literal text |
| `src/components/assistant-ui/markdown-text.test.ts` | Tests: preprocessMarkdown; strips inline accidental triple-backtick starts; demotes invalid fenced prose blocks with closers; drops fences around a preview-only URL block |
| `src/components/assistant-ui/markdown-text.tsx` | Exports `MarkdownImage`, `MessageTextContent`, `MarkdownTextContent`, `MarkdownText` |
| `src/components/assistant-ui/mcp-setup-tool.test.tsx` | Tests: the MCP setup card; opens required details from the row action and sends the approved environment; lists every target once settled, in the same three words as the connector card |
| `src/components/assistant-ui/mcp-setup-tool.tsx` | Exports `McpSetupTool`, `McpSetupPending`, `McpSetupOffer` |
| `src/components/assistant-ui/message-render-boundary.test.tsx` | Tests: MessageRenderBoundary; recovers on the next consistent snapshot when resetKey changes; re-throws unrelated errors so real bugs still surface; recovers on the retry timer without a resetKey change |
| `src/components/assistant-ui/message-render-boundary.tsx` | `@assistant-ui/store`'s index-keyed child-scope lookup (`useClientLookup`) throws — rather than returning undefined — when a subscriber reads an index that the message/parts list no longer has. This races during high-fr… |
| `src/components/assistant-ui/reference-kinds.ts` | The composer's reference vocabulary: one place that decides what a ` |
| `src/components/assistant-ui/session-ref-open.test.tsx` | Tests: session refs open the session; opens the session from an agent-written link; opens the session from a chip in the user transcript; url refs open in the browser pane |
| `src/components/assistant-ui/setup-beat/beat-cards.tsx` | A text box for the name. The OS account's full name is offered as a row and is sent only when picked. |
| `src/components/assistant-ui/setup-beat/card-type.ts` | Setup cards read the chat's conversation tokens, so the setup chat's larger scale reaches them too. Relative sizes follow main's setup cards: label and detail one rung under the options, prose above. |
| `src/components/assistant-ui/setup-beat/plugins-card.tsx` | Exports `PluginsCard` |
| `src/components/assistant-ui/setup-beat/receipt.tsx` | Exports `SETUP_BEAT_SHELL_CLASS`, `SetupBeatOutcome`, `setupBeatOutcome`, `useTourLabel`, `SetupBeatReceipt` |
| `src/components/assistant-ui/setup-beat/setup-beat-tool.test.tsx` | Tests: SetupBeatTool; draws the words typed while the card waited as the user; draws nothing for a refusal meant for the model; says a card answer was not accepted, and a row left without a card once the turn ended was… |
| `src/components/assistant-ui/setup-beat/setup-beat-tool.tsx` | Exports `SetupBeatTool` |
| `src/components/assistant-ui/test-utils.tsx` | Fixed clock for message fixtures, so nothing sorts by "now". |
| `src/components/assistant-ui/theme-picker/accent-picker-card.tsx` | Exports `AccentPickerCardProps`, `AccentPickerCard` |
| `src/components/assistant-ui/theme-picker/args.ts` | Exports `SET_THEME_TOOL`, `SetThemeCall`, `setThemeCall` |
| `src/components/assistant-ui/theme-picker/layout-picker-card.tsx` | Exports `LayoutPickerCardProps`, `FIRST_RUN_LAYOUTS`, `LayoutPickerCard` |
| `src/components/assistant-ui/theme-picker/look-preview.ts` | A staged pick; `value` null is the theme's own accent. |
| `src/components/assistant-ui/theme-picker/theme-tool.test.tsx` | Tests: ThemeTool; previews a clicked swatch without answering, then Continue answers with the last one staged; puts the previous accent back when the card settles without a pick; draws the layout card for a call made th… |
| `src/components/assistant-ui/theme-picker/theme-tool.tsx` | Exports `ThemeReceipt`, `ThemeTool` |
| `src/components/assistant-ui/thread-remount.test.tsx` | Tests: thread message mount stability; keeps message DOM nodes mounted when callback props get new identities |
| `src/components/assistant-ui/thread/agent-avatar-cache.test.ts` | The avatar cache is keyed by a handle parsed out of message text — unbounded distinct senders over a long session — and its hits hold base64 avatar data URLs, so it must not grow for the life of the renderer window. Thi… |
| `src/components/assistant-ui/thread/agent-delivery.test.tsx` | Sender-side inter-agent deliveries render as "Messaged X" / "Message from X" notices instead of terminal transcript rows. This pins the detection (the canonical Bot Mode command shape) and the reply extraction. |
| `src/components/assistant-ui/thread/agent-delivery.tsx` | Sender-side inter-agent delivery: `hermes -p <agent> chat … -q "Message from 🤖 <sender>…"` run through the terminal tool IS the messaging pipeline (the Bot Mode / multi-profile convention shipped with #85855). |
| `src/components/assistant-ui/thread/agent-message.test.tsx` | Agent-to-agent deliveries render as a compact attributed timeline notice, not a user bubble. This pins the detection contract: the Bot Mode prefix ("Message from 🤖 <sender>: …"), the handle-carrying form |
| `src/components/assistant-ui/thread/assistant-message.test.tsx` | Bug #2: the Branch-in-new-chat button used to render unconditionally even when its handler was a no-op (session-tile.tsx passed `() => undefined` for branched/tiled chats, where nested branching isn't supported). That |
| `src/components/assistant-ui/thread/assistant-message.tsx` | Exports `AssistantMessage` |
| `src/components/assistant-ui/thread/background-resume.test.tsx` | Tests: keeps background waiting local to its idle thread without echoing child thinking chrome |
| `src/components/assistant-ui/thread/block-direction.test.tsx` | Lists and blockquotes have chrome beside the text (markers, the quote border) whose side is driven by the box's CSS direction, which the unicode-bidi:plaintext rules never touch. These tests pin the split of |
| `src/components/assistant-ui/thread/changed-files-card.tsx` | ~5 rows. A turn that rewrites twenty files should still read as one card in the transcript, not a wall the user has to scroll past to reach the composer. |
| `src/components/assistant-ui/thread/changed-files.ts` | Pure derivation for the assistant message's "N files changed" card: fold a turn's file-edit tool parts into one row per file. No React/DOM. |
| `src/components/assistant-ui/thread/content.test.ts` | Tests: partText; returns plain strings as-is; reads text from untyped and text parts; ignores non-text parts and malformed input |
| `src/components/assistant-ui/thread/content.ts` | Exports `PROCESS_NOTIFICATION_RE`, `partText`, `messageContentText`, `contentHasVisibleText`, `messageAttachmentRefs`, `pickPrimaryPreviewTarget` |
| `src/components/assistant-ui/thread/double-click-reaction.test.tsx` | Double-click an assistant reply to heart it (the iMessage gesture), gated on the same opt-in toggle as the rest of message reactions. |
| `src/components/assistant-ui/thread/duplicate-activity-indicator.test.tsx` | Loading and activity indicators mount only on the thread's last message. The tail-only gate from ba756333 keeps non-tail running bubbles silent, including assistants followed only by a user or system row. The optimistic |
| `src/components/assistant-ui/thread/edit-context.test.tsx` | Thread deliberately keeps cwd/gateway/sessionId OUT of the messageComponents memo deps: those values change on every session switch, and reminting the component types mid-switch remounts the whole outgoing transcript. T… |
| `src/components/assistant-ui/thread/index.test.tsx` | Issue #95595 proposed-fix #3: the `messageComponents` map handed to ThreadMessageList must keep its REFERENCE IDENTITY across a session switch. If it re-minted, React would unmount/remount every visible message — async… |
| `src/components/assistant-ui/thread/index.tsx` | Exports `Thread` |
| `src/components/assistant-ui/thread/inter-agent-collapse.test.tsx` | Two contracts with no coverage before the invalidation-scoping work split AssistantMessage into InterAgentAssistantMessage + AssistantMessageBody: 1. The collapse gate. A reply to an inter-agent delivery renders collaps… |
| `src/components/assistant-ui/thread/list-auto-show-earlier.test.tsx` | Tests: top-edge auto Show earlier; pages older turns in when the reader wheels up at the clamped top, not mid-transcript |
| `src/components/assistant-ui/thread/list-restore-composer-resize.test.tsx` | Tests: list post-settle restore vs composer-only resize; follows pre-settle async layout before the next animation frame can paint; does not rewrite scrollTop when only composer clearance grows; content growth still res… |
| `src/components/assistant-ui/thread/list-row-identity.test.tsx` | Tests: transcript row identity; keeps every stored turn mounted when a slid newest page re-reads it under new renderer ids |
| `src/components/assistant-ui/thread/list-session-scroll.test.tsx` | Tests: list session-scroll restore; marks the chat surface data-session-switching while a switched transcript settles, then clears it; keeps a bottom-pinned reader pinned while a running turn grows the content (#118482)… |
| `src/components/assistant-ui/thread/list.test.ts` | Tests: subscribeToThreadForeground; reanchors on focus when an active turn keeps document visibility pinned visible; leaves a scrolled-up reader in place when the window focuses; drops a queued reanchor when the reader… |
| `src/components/assistant-ui/thread/list.tsx` | Exports `MessageGroup`, `HIDDEN_TRANSCRIPT_RENDER_BUDGET`, `transcriptPaneBudget`, `shouldClampTranscriptBudget`, `shouldAnchorBeforePrepend`, `transcriptBackfillFrameCount` … |
| `src/components/assistant-ui/thread/message-hover-time.tsx` | When the message landed, in seconds: a reply counts from its completion. `createdAt` already carries the row's own timestamp (see `messageCreatedAt`), falling back to now only for a just-sent message. |
| `src/components/assistant-ui/thread/message-parts-connectors.test.tsx` | Runtime id (events, operation store) and stored id (owner hints) differ in the app. |
| `src/components/assistant-ui/thread/message-parts.tsx` | Exports `MESSAGE_PARTS_COMPONENTS` |
| `src/components/assistant-ui/thread/message-reactions.tsx` | Served from the app's own origin (vite.config.ts `hermes:emojibase-assets` plugin bundles emojibase-data): Electron must work offline, and the app should never phone a CDN to draw a picker. |
| `src/components/assistant-ui/thread/preview-embeds.test.tsx` | Link previews moved off the message root into the AssistantPreviewEmbeds leaf, because the selector behind them (`'' while running`, the full `messageContentText(content)` join once settled) flipped on every |
| `src/components/assistant-ui/thread/process-notification.test.tsx` | Tests: renders legacy and current process completions as tool disclosures without interpreting their output |
| `src/components/assistant-ui/thread/reaction-picker-focus-follow.test.tsx` | Tests: assistant reaction picker; stays open while the pointer moves over the message toward it |
| `src/components/assistant-ui/thread/response-copy-scope.test.tsx` | Bug #118864: the footer's text accessor (getMessageText) joined EVERY message in the response group, so the tail reply's Copy/Read-aloud included sealed interim narration and mid-turn commentary. The default Copy/Read |
| `src/components/assistant-ui/thread/response-group.test.tsx` | Tests: keeps background continuations in one response with one action bar and the original message identities; ends the response at a real user prompt or unrelated system event |
| `src/components/assistant-ui/thread/response-group.tsx` | Exports `responseMessageRole`, `ResponseMessageIds`, `ResponseMessages` |
| `src/components/assistant-ui/thread/sealed-tool-parts.test.tsx` | The image card, delegate list and delivery notice decide pending-ness from `result === undefined`; a call sealed without a result must not stay live. |
| `src/components/assistant-ui/thread/session-switching.ts` | `data-session-switching` — the supported hook for styling a chat switch. Core sets it on the chat surface root (`[data-chat-surface]`, one per pane: the primary chat and every tile) while that surface is placing a trans… |
| `src/components/assistant-ui/thread/should-auto-show-earlier.test.ts` | Tests: shouldAutoShowEarlier; pages only for a settled reader at the top edge with older content to show |
| `src/components/assistant-ui/thread/signed-out-transcript.test.tsx` | Tests: transcript while a Webapp tab is signed out; leaves the page while the sign-in view is up and returns after sign-in; keeps the transcript under any other startup failure |
| `src/components/assistant-ui/thread/status-invalidation-scope.test.tsx` | The invalidation-scoping property, as a render-count contract. A streaming turn flips its message status many times a second, and at stream breadth N that is N status flips per flush. The whole point of this |
| `src/components/assistant-ui/thread/status-tail-only.test.tsx` | The thinking indicator (dither block) may only ever render at the TAIL of the thread. A message stuck status:running mid-transcript — however it got there (missed settle event, steer race, upstream state bug) — must ren… |
| `src/components/assistant-ui/thread/status.test.tsx` | Tests: ResponseLoadingIndicator timer; preserves each running session timer while switching between sessions; names a prolonged provider wait in the existing response status row; keeps the ticking timer out of the live… |
| `src/components/assistant-ui/thread/status.tsx` | A status line is scaffolding like any other — "Editing" while the model drafts a call is the same kind of line as "Explored 3 files" once it has run, and reads as one continuous column only if it shares their type and c… |
| `src/components/assistant-ui/thread/sticky-prompt-clip-registration.test.ts` | `use-sticky-prompt-clip.ts` writes this value once per scroll frame onto elements that are whole turns (markdown, code, tool output). If the property stops being registered as a typed, NON-inherited property, every writ… |
| `src/components/assistant-ui/thread/stream-settled-renders.test.tsx` | Streaming into a long transcript must not re-render the settled history (#126486, regression of #69120). A streamed delta replaces only the tail ChatMessage; everything upstream of the thread keeps identity for settled |
| `src/components/assistant-ui/thread/streaming.test.tsx` | Tests: assistant-ui streaming renderer; renders assistant text incrementally before completion; suppresses the action footer on sealed interim messages, keeping it on the final reply; renders assistant provider errors i… |
| `src/components/assistant-ui/thread/system-message.test.tsx` | Timeline timestamps render only when `display.timestamps` is enabled. |
| `src/components/assistant-ui/thread/system-message.tsx` | Exports `BackgroundResult`, `SystemMessage` |
| `src/components/assistant-ui/thread/text-direction.test.tsx` | Appearance → Text direction. Auto is the shipped per-block first-strong behavior and must leave the DOM exactly as it was; RTL/LTR stamp one `dir` on each chat prose surface and both composers, replacing the list/quote |
| `src/components/assistant-ui/thread/thread-message-index.test.ts` | Tests: thread message index; finds a row index and a user ordinal, or reports none; is keyed by array identity, so a new transcript array is re-indexed |
| `src/components/assistant-ui/thread/thread-message-index.ts` | Shared position lookups over `s.thread.messages`, built once per array. Every mounted message row re-runs its `useAuiState` selectors on each thread notify — one per streamed chunk. A selector that scans the transcript… |
| `src/components/assistant-ui/thread/timeline-data.test.ts` | Tests: timelinePreview; collapses whitespace to a single line; truncates with an ellipsis past the limit; timelineBarWidth |
| `src/components/assistant-ui/thread/timeline-data.ts` | Pure timeline helpers — no React/DOM; tested in thread-timeline-data.test.ts. |
| `src/components/assistant-ui/thread/timeline-idle.test.tsx` | The timeline must do NO work it can't currently show. Two gates are proven here by rendering the real component and counting the work it performs: - a background (kept-alive but hidden) tab derives nothing and subscribe… |
| `src/components/assistant-ui/thread/timeline-index.test.ts` | Tests: timeline metadata index; fetches one lightweight page and coalesces concurrent callers; continues only on demand and deduplicates overlapping metadata; isolates identical session IDs by owning connection and prof… |
| `src/components/assistant-ui/thread/timeline-index.ts` | Exports `TimelineIndex`, `timelineIndexKey`, `cachedTimelineIndex`, `fetchTimelineIndex`, `previousPromptRowId` |
| `src/components/assistant-ui/thread/timeline-position.test.tsx` | Tests: timeline position in the real rail component; keeps exact bidirectional positions with logarithmic outer-box reads and no per-frame DOM sweep; refreshes identities after paging and late mounts, measures resize, a… |
| `src/components/assistant-ui/thread/timeline-position.ts` | Exports `createTimelinePositionReader` |
| `src/components/assistant-ui/thread/timeline-rail.test.tsx` | Tests: TimelineRail; bounds mounted buttons for thousands of prompts; keeps the active bar compact without hover and routes selection by stable ID |
| `src/components/assistant-ui/thread/timeline-rail.tsx` | Exports `TimelineRail` |
| `src/components/assistant-ui/thread/timeline-timestamp.test.tsx` | Tests: setDisplayTimestampsFromConfig; accepts boolean and string forms, defaulting off; TimelineTimestamp display.timestamps gate; renders nothing while display.timestamps is off (the default) |
| `src/components/assistant-ui/thread/timeline-timestamp.tsx` | Exports `TimelineTimestamp`, `MessageTimelineTimestamp` |
| `src/components/assistant-ui/thread/timeline.css` | Stylesheet |
| `src/components/assistant-ui/thread/timeline.test.ts` | Several chat surfaces are mounted at once — side by side in a split, and stacked as kept-alive inactive tabs. A timeline scrolls its OWN thread. |
| `src/components/assistant-ui/thread/timeline.tsx` | Exports `ownViewport`, `ThreadTimeline` |
| `src/components/assistant-ui/thread/timestamp.test.ts` | Tests: formatMessageTimestamp; returns an empty string for missing values; uses the today label for timestamps earlier today; uses the yesterday label for timestamps the prior day |
| `src/components/assistant-ui/thread/timestamp.ts` | Exports `formatTimelineTimestamp`, `formatTimelineRange`, `formatMessageTimestamp` |
| `src/components/assistant-ui/thread/transcript-window.test.ts` | Tests: resolveShowEarlierAction; spends the already-materialized DOM page first; expands the store window once the DOM page is exhausted; is a no-op when neither DOM nor store has older content |
| `src/components/assistant-ui/thread/transcript-window.tsx` | Exports `TranscriptWindowValue`, `TranscriptWindowProvider`, `useTranscriptWindow`, `resolveShowEarlierAction`, `TOP_EDGE_PX`, `ShouldAutoShowEarlierInput` … |
| `src/components/assistant-ui/thread/turn-activity.test.ts` | The transcript's activity row has to account for every second the app spends claiming to work. Before this, it ran off a text-length signature and only deferred to the tail part, so it went silent — and stopped counting… |
| `src/components/assistant-ui/thread/turn-activity.ts` | Seconds of silence before an unnamed wait earns a row of its own. Long enough that the pause between one tool call finishing and the next arriving stays silent — a row that appeared for 300ms between every call would st… |
| `src/components/assistant-ui/thread/turn-gap-indicator.test.tsx` | The gap case: the agent is working, the composer's arc border is on and Stop is armed, but the tail bubble has settled — a sealed interim row, or a turn whose last message completed while the agent kept going. The trans… |
| `src/components/assistant-ui/thread/types.ts` | Exports `RestoreMessageTarget` |
| `src/components/assistant-ui/thread/use-message-reactions.ts` | Exports `DOUBLE_CLICK_REACTION`, `isTapbackDoubleClick`, `useMessageReactions`, `useTapbackDoubleClick` |
| `src/components/assistant-ui/thread/use-messages-below-perf.test.ts` | Tests: messages-below scroll cost; does not measure every mounted group to count messages below the fold |
| `src/components/assistant-ui/thread/use-messages-below.test.tsx` | Tests: messages below the viewport; counts the clipped message plus later messages without laying out skipped turns; finds the fold with logarithmic group reads and reuses membership across scroll frames; invalidates ca… |
| `src/components/assistant-ui/thread/use-messages-below.ts` | Exports `createMessagesBelowReader`, `countMessagesBelow`, `useMessagesBelow` |
| `src/components/assistant-ui/thread/use-sticky-prompt-clip.test.tsx` | Tests: clips only visible covered siblings, follows resize, and releases styles and observers on hide |
| `src/components/assistant-ui/thread/use-sticky-prompt-clip.ts` | Exports `useStickyPromptClip` |
| `src/components/assistant-ui/thread/use-timeline-history.test.tsx` | Tests: timeline history index; follows prompts persisted after the complete index was read; does not fetch a freshly minted, still-empty draft (#123622) |
| `src/components/assistant-ui/thread/use-timeline-history.ts` | A bounded metadata page after paint; more titles load only on explicit demand. |
| `src/components/assistant-ui/thread/use-timeline-reveal.test.tsx` | Tests: timeline direct reveal; waits for a single bounded around-page commit and resolves the mounted id; leaves existing content when a direct read fails |
| `src/components/assistant-ui/thread/use-timeline-reveal.ts` | Exports `useTimelineReveal` |
| `src/components/assistant-ui/thread/user-edit-composer-owner-route.test.tsx` | The inline message-edit composer is a second `/` palette: it must reach the edited session's OWNER exactly like the main composer does (#141583). Before it passed its sessionId, its catalog went out on the ambient socke… |
| `src/components/assistant-ui/thread/user-edit-composer.tsx` | Exports `UserEditComposer` |
| `src/components/assistant-ui/thread/user-message-edit-drop-staging.test.tsx` | An OS drop into the message-edit composer that the shell cannot expose as a native path is staged as File bytes (the Webapp bridge uploads it). When that staging is rejected, the reason the server or a proxy gave (an ng… |
| `src/components/assistant-ui/thread/user-message-edit-gesture.test.tsx` | Tests: edit send arrow — macOS click gesture (blur races cancel); keeps touch prose outside the edit button and requires explicit Edit; sends without an uncaught |
| `src/components/assistant-ui/thread/user-message-edit-shared-composer.test.tsx` | @vitest-environment jsdom The inline edit composer opens inside a chat pane whose composer surface is registered with the shared floating-composer recipient tracker |
| `src/components/assistant-ui/thread/user-message-edit-undo-cut-drag.test.tsx` | The edit composer's undo stack misses the two mutation paths Chromium runs without a React-visible beforeinput: cutting selected text and dragging a selection within the editor. Chromium fires the native `cut` / `drop` |
| `src/components/assistant-ui/thread/user-message-edit.test.tsx` | Clicking a user bubble must open the inline edit composer — through the app's incremental external-store runtime (which reimplements capability resolution, incl. `edit: onEdit !== undefined`) and the stock runtime. |
| `src/components/assistant-ui/thread/user-message-pointer.test.tsx` | Tests: user message reactions by pointer; opens the reaction picker on a mouse right-click in a touch-layout browser tab; leaves a touch long-press in a touch-layout browser tab to the platform |
| `src/components/assistant-ui/thread/user-message-text.test.tsx` | Tests: a sent reference renders as the chip the composer showed; chips a backtick-quoted @url: instead of splitting it into code; chips a backtick-quoted @file: path with spaces; labels a large-paste file as pasted cont… |
| `src/components/assistant-ui/thread/user-message-text.tsx` | User messages should render the bare-minimum of markdown: backtick `code` spans and ``` fenced blocks. We deliberately don't pull in the full assistant Markdown pipeline (Streamdown + KaTeX + syntax highlighter) |
| `src/components/assistant-ui/thread/user-message-touch-clamp.test.tsx` | Tests: touch user bubble clamp; clamps a long prompt and lets an explicit toggle hold it open; offers no toggle for a prompt that fits the clamp |
| `src/components/assistant-ui/thread/user-message.tsx` | Exports `hasTextSelection`, `StickyHumanMessageContainer`, `USER_BUBBLE_BASE_CLASS`, `USER_ACTION_ICON_BUTTON_CLASS`, `USER_ACTION_ICON_SIZE`, `StopGlyph` … |
| `src/components/assistant-ui/tool-media-slot.test.tsx` | @vitest-environment jsdom |
| `src/components/assistant-ui/tool-media-slot.tsx` | Exports `ToolMediaSlot` |
| `src/components/assistant-ui/tool/approval-activity.ts` | These calls render as activity, not file diffs or other deliverable cards. |
| `src/components/assistant-ui/tool/approval.test.tsx` | Tests: PendingApprovalStack; retains an empty host without consuming keyboard input; renders run/reject controls for a pending terminal command; renders the description instead of a synthetic plugin-rule placeholder |
| `src/components/assistant-ui/tool/approval.tsx` | Exports `ApprovalPlacementContext`, `PendingApprovalStack`, `ApprovalQueue` |
| `src/components/assistant-ui/tool/delegate-model.test.ts` | Tests: delegateGoals; reads a batch in task order and a single goal alike; delegateRowsFromCall; reads as running before a result and parked once dispatched |
| `src/components/assistant-ui/tool/delegate-model.ts` | A delegation runs somewhere the transcript can't see: the tool call carries the goals it dispatched, the subagent store carries what those children are actually doing, and the tool result carries how they finished. One… |
| `src/components/assistant-ui/tool/delegate.test.tsx` | Tests: delegate card fade; does not put the activity ticker inside a scaffold fade |
| `src/components/assistant-ui/tool/delegate.tsx` | Exports `DelegateTool` |
| `src/components/assistant-ui/tool/fallback-error-summary.test.tsx` | Tests: tool error summary linkification; keeps an explicit URL in the error clickable without rewriting the headline |
| `src/components/assistant-ui/tool/fallback-model.test.ts` | Tests: buildToolView image handling; keeps local image paths for the activity renderer to resolve; keeps fetchable data URLs; keeps remote http(s) image URLs |
| `src/components/assistant-ui/tool/fallback-model/format.ts` | Exports `isRecord`, `browserExecStepLabel`, `compactPreview`, `contextValue`, `MAX_TOOL_RENDER_CHARS`, `clampForDisplay` … |
| `src/components/assistant-ui/tool/fallback-model/index.ts` | Exports `DiffLineStats`, `countDiffLineStats`, `fileEditPath`, `fileEditBasename`, `selectMessageRunning`, `looksRedundant` … |
| `src/components/assistant-ui/tool/fallback-model/targets.ts` | Exports `looksLikeUrl`, `looksLikePath`, `isPreviewableTarget`, `stableHash`, `toolPartDisclosureId`, `toolGroupDisclosureId` … |
| `src/components/assistant-ui/tool/fallback-model/types.ts` | Exports `ToolTone`, `ToolStatus`, `ToolPart`, `SearchResultRow`, `ToolTitleAction`, `CountMetric` … |
| `src/components/assistant-ui/tool/fallback-preview-scope.test.tsx` | Tests: tool row preview recording; records into the session whose transcript the row is in, not the primary; still records into the primary session for the main chat; does not promote reads, failed writes or packaged re… |
| `src/components/assistant-ui/tool/fallback-vision-image.test.tsx` | @vitest-environment jsdom |
| `src/components/assistant-ui/tool/fallback.test.ts` | Tests: splitRunItems; collapses a stretch of activity into one run; keeps a card at the point in the turn where it happened; does not let adjacent cards merge into a run |
| `src/components/assistant-ui/tool/fallback.tsx` | Exports `technicalTrace`, `RunItem`, `splitRunItems`, `ToolGroupSlot`, `ToolFallback` |
| `src/components/assistant-ui/tool/hide-code-diffs.test.tsx` | Tests: keeps edit counts without code in either display mode and restores disclosure when disabled; still discloses failed edits when code diffs are hidden |
| `src/components/assistant-ui/tool/inline-edit-persistence.test.tsx` | Tests for `inline-edit-persistence` |
| `src/components/assistant-ui/tool/run-summary.test.ts` | Tests: summarizeToolRun; names a lone target and counts the rest; orders clauses explore then run regardless of call order; counts commands rather than naming them once they have run |
| `src/components/assistant-ui/tool/run-summary.ts` | Exports `ToolCallLike`, `isToolCallPart`, `toolPresentVerb`, `summarizeToolRun` |
| `src/components/assistant-ui/tool/run-ticker.tsx` | A one-line window over a growing list of rows. Each new row slides the one before it up and out, so activity that would otherwise grow down the page reads as a single line ticking over in place. Rows are clipped to a un… |
| `src/components/assistant-ui/tool/skill-activity.test.ts` | Tests: skill activity identity; keeps each skill identity and failed outcome in mixed collapsed summaries |
| `src/components/assistant-ui/tool/skill-activity.ts` | Exports `skillActivityTitle` |
| `src/components/assistant-ui/tool/tool-feed-chrome.test.tsx` | Tests: tool feed visibility policy; answer-only (both switches off) hides reasoning and non-essential tool chrome; keeps the execution flow while reasoning stays hidden; still shows tool chrome when reasoning blocks are… |
| `src/components/assistant-ui/tool/tool-group.test.tsx` | Timeline timestamps render only when `display.timestamps` is enabled. |
| `src/components/assistant-ui/tooltip-icon-button.tsx` | Exports `TooltipIconButtonProps`, `TooltipIconButton` |
| `src/components/assistant-ui/transcript-directive.test.tsx` | @vitest-environment jsdom |
| `src/components/assistant-ui/transcript-directive.tsx` | Exports `paragraphPlainText`, `TranscriptDirectiveLeaf`, `ResolvedParagraphSegment`, `useResolvedParagraph` |
| `src/components/assistant-ui/typed-answer.tsx` | Words typed in the composer while a card waited, drawn as the user's bubble where the card stood. They live only in the tool result's `said`: a user row between a tool call and its result breaks the transcript. |
| `src/components/assistant-ui/use-connection-owner.ts` | The gateway route that owns a session's connection operation. Null until it resolves and null when it cannot: a card RPC must reach the gateway that holds the operation, never whichever one the window happens to have in… |
| `src/components/billing-banner.tsx` | Exports `BillingBanner` |
| `src/components/boot-failure-cause.test.ts` | Tests: local boot failure classification; classifies the raw main-process failures into plain causes; keeps the raw output out of the headline and behind details; falls back to the first raw line for an unknown failure,… |
| `src/components/boot-failure-cause.ts` | Plain-language cause for a LOCAL backend boot failure. The main process reports what it saw ("exited before it became ready (1)", "Timed out connecting to Hermes backend after 45000ms", an EACCES, a Python traceback tai… |
| `src/components/boot-failure-overlay.test.tsx` | Remote-backend users hit a hard boot failure that isn't OAuth reauth (token auth, wrong URL, unreachable host). The recovery screen must let them fix the remote connection in place — the "Connection settings" action swa… |
| `src/components/boot-failure-overlay.tsx` | Exports `StartupOverlay`, `BootFailureOverlay` |
| `src/components/boot-failure-reauth.test.ts` | Tests: isRemoteConfig; true for remote/cloud with a URL, regardless of auth mode or connection; recognizes SSH as remote recovery without treating it as OAuth reauth; false for local, incomplete SSH, a remote with no UR… |
| `src/components/boot-failure-reauth.ts` | Pure helpers for the boot-failure overlay's remote-reauth branch. Kept out of the .tsx so they can be unit-tested without a React/jsdom render (the jsx-dev-runtime resolution in this repo's vitest setup is flaky for |
| `src/components/brand-mark.tsx` | Exports `BrandMark` |
| `src/components/chat/activity-timer-text.tsx` | Exports `ActivityTimerText` |
| `src/components/chat/activity-timer.test.tsx` | Tests: useElapsedSeconds; keeps elapsed time stable across remounts for the same key; counts from an explicit epoch rather than mount time; re-anchors when the epoch moves |
| `src/components/chat/activity-timer.ts` | Module-level registry so timers survive component unmount/remount (e.g. when a tool row scrolls out and back). Keyed by caller-supplied timerKey; anonymous timers (no key) start fresh each mount. |
| `src/components/chat/code-card.tsx` | Rounded surface for fenced code (and any equivalent: diffs, raw payloads, etc.) sized for the conversation column. Background only — no border, no header, no language label — so a code block reads as a tinted slab of th… |
| `src/components/chat/code-editor-theme.ts` | GitHub "default" palettes, mirroring the read view's Shiki themes (`github-light-default` / `github-dark-default`) so the spot editor matches the preview it replaces. These are token *colors*; CodeMirror tokenizes with |
| `src/components/chat/code-editor.tsx` | Exports `CodeEditorApi`, `CodeEditor` |
| `src/components/chat/compact-markdown.overflow.test.tsx` | Tests: CompactMarkdown overflow containment; soft-wraps fenced code instead of scrolling sideways |
| `src/components/chat/compact-markdown.tsx` | Compact markdown renderer for tool detail bodies. Same Streamdown pipeline as the file preview pane, with tighter typography and external-link routing so tools that emit markdown (tables, headings, links) render properly |
| `src/components/chat/composer-dock.ts` | The composer surface and the status/queue stack paint ONE shared `--composer-fill` var. The state ladder (rest / scrolled) lives in styles.css on `[data-slot='composer-root']`, so the layers can never disagree. |
| `src/components/chat/diff-lines-seen.test.tsx` | Tests: compact FileDiffPanel highlights only once it is on screen; keeps the plain colored rows off screen, then highlights on first intersection |
| `src/components/chat/diff-lines.test.tsx` | Regression coverage for #93479: a failed dynamic import of the lazily-loaded Shiki diff module (packaged asar/asar.unpacked path mismatch, or any other fetch failure) rejects the `React.lazy()` promise. React.Suspense o… |
| `src/components/chat/diff-lines.tsx` | Renders a unified diff for a tool's file edit. Two paths share one parse: - `SyntaxDiff` highlights the change *content* in the file's language via Shiki, then a per-line transformer paints the add/remove tint on top. -… |
| `src/components/chat/disclosure-row.tsx` | Shared header row for any collapsible block (thinking, tool group, single tool). Each parent supplies its own outer wrapper (with the data-slot CSS uses to escape the message padding) and its own expanded body. |
| `src/components/chat/expandable-block.test.tsx` | jsdom has no ResizeObserver and reports scrollHeight === 0, so the block never flips to `overflowing` on its own. Stub RO to fire immediately and force a tall scrollHeight on the observed node so the toggle mounts. |
| `src/components/chat/expandable-block.tsx` | Exports `ExpandableBlock` |
| `src/components/chat/fixed-row-window.ts` | Exports `LineChunk`, `TextLineChunk`, `FixedRowWindow`, `chunkLines`, `chunkTextLines`, `useFixedRowWindow` |
| `src/components/chat/generated-image-open.test.tsx` | The image never loads, so the card collapses to its "Open image" link. An inline source stays its own src, as in the real hook. |
| `src/components/chat/generated-image-result.tsx` | Exports `GeneratedImage` |
| `src/components/chat/image-generation-placeholder.test.tsx` | Tests: DiffusionCanvas scheduling; keeps animating while unfocused but cancels its loop while minimized |
| `src/components/chat/image-generation-placeholder.tsx` | Exports `DiffusionCanvas` |
| `src/components/chat/image-geometry.test.tsx` | Tests: keeps the pending generated-image frame when its result arrives; keys inline data sources by a bounded digest so they are remembered |
| `src/components/chat/intro-copy.jsonl` | JSON-lines dataset/fixture |
| `src/components/chat/intro.test.tsx` | Tests: translates every shipped stock body at the same personality and rotation position; localizes the custom-personality fallback without translating its user-supplied name |
| `src/components/chat/intro.tsx` | Exports `IntroProps`, `Intro` |
| `src/components/chat/json-document-editor.tsx` | Kept a string (not a shared CSS utility): the `size-5` prefix lets tailwind-merge override <Button size="icon">'s larger built-in size. |
| `src/components/chat/log-search.tsx` | Exports `LogSearch`, `useLogSearch`, `LogSearchField` |
| `src/components/chat/log-tail.test.tsx` | Tests: LogTail search; highlights every hit in place and steps one active hit through all of them; returns to the live tail when the search is cleared; LogTail layout |
| `src/components/chat/log-tail.tsx` | Exports `LogTail` |
| `src/components/chat/preview-attachment.test.tsx` | #101683 regression coverage: the delivered-file card must branch on the target's LOCAL filesystem state — an existing directory opens natively with no Download and no broken preview, an existing local file reveals inste… |
| `src/components/chat/preview-attachment.tsx` | What the Electron main process said about this target's LOCAL filesystem state (#101683). `null` keeps the stock card — remote-backend targets keep Download, and a bridge-less dev server can't classify. |
| `src/components/chat/scaffold-row.tsx` | Transcript scaffolding: the quiet lines around the reply that say what the agent did rather than what it said — a thinking header, a settled tool run, the live activity ticker. They all render through here so they canno… |
| `src/components/chat/shiki-block.test.tsx` | Perf regression guard for #95595: switching to a warm session remounts the incoming transcript, and every mounted code block used to re-tokenize from scratch on the main thread. The content-keyed cache must make a remou… |
| `src/components/chat/shiki-block.tsx` | The ONLY static importer of shiki (and through it the multi-MB shiki language/theme/wasm bundle). Every consumer reaches this module through `React.lazy(() => import('./shiki-block'))` — see `LazyShiki` in shiki-highlig… |
| `src/components/chat/shiki-chunk-boundary.tsx` | Chromium/Electron: "TypeError: Failed to fetch dynamically imported module: …". Vite also emits "error loading a dynamically imported module", Safari "a module that couldn't be instantiated" — all three are |
| `src/components/chat/shiki-config.ts` | Shiki theme/color constants shared by the chat code-block renderer (shiki-highlighter.tsx) and the lazy shiki chunk (shiki-block.tsx). Kept in their own dependency-free module so the lazy chunk can import them without |
| `src/components/chat/shiki-highlight-cache.test.ts` | Tests: highlightCacheKey; separates scope, language and code so distinct blocks never collide; HighlightCache; round-trips an entry and refreshes recency on get |
| `src/components/chat/shiki-highlight-cache.ts` | ── Content-addressed syntax-highlight cache (#95595) ──────────────────────── Switching to a warm session remounts the incoming transcript, and every mounted code block used to be re-tokenized from scratch by shiki — N… |
| `src/components/chat/shiki-highlighter.test.ts` | Tests: exceedsHighlightBudget; highlights normal-sized blocks; skips highlighting past the line budget; skips highlighting past the char budget on few lines |
| `src/components/chat/shiki-highlighter.test.tsx` | Regression coverage for #95995: a failed dynamic import of the lazily-loaded Shiki code-block chunk (missing from a packaged app bundle — the reporter's desktop.log shows 229× `Failed to fetch dynamically imported modul… |
| `src/components/chat/shiki-highlighter.tsx` | Theme constants live in shiki-config (dependency-free) so the lazy shiki chunk can import them without pulling this module into the shiki bundle. |
| `src/components/chat/shiki-plain.tsx` | Matches highlighted markup so loading a grammar changes color, not layout. |
| `src/components/chat/skeletons.tsx` | Shared loading skeletons for the file/git trees and diffs — quieter than a spinner and shaped like the content that's about to land. |
| `src/components/chat/stable-text.tsx` | Exports `StableText` |
| `src/components/chat/status-control-row.tsx` | Exports `StatusControlRow` |
| `src/components/chat/status-dismiss-button.tsx` | Exports `StatusDismissButton` |
| `src/components/chat/status-pending-icon.tsx` | Neutral, unfinished state shared by pending tasks and goal criteria. |
| `src/components/chat/status-row.test.tsx` | Tests: keeps dismiss and nested controls independent from row activation |
| `src/components/chat/status-row.tsx` | Exports `StatusRow` |
| `src/components/chat/status-section.tsx` | Exports `StatusSection` |
| `src/components/chat/status-stack.css` | Shared columns: action, state glyph, content, optional trailing actions. |
| `src/components/chat/syntax-diff.tsx` | The Shiki-highlighted compact diff body, split out of diff-lines.tsx so the `react-shiki` static import (and the multi-MB shiki chunk behind it) loads lazily on first use instead of on the cold-start path. diff-lines.ts… |
| `src/components/chat/terminal-output.tsx` | Exports `TerminalOutput` |
| `src/components/chat/transcript-video.test.tsx` | Ported from block/buzz#7336: a rate picked in one video persists and seeds every later player; garbage stored values fall back to 1x. |
| `src/components/chat/transcript-video.tsx` | Playback position per source, remembered across remounts. Transcript rows legitimately unmount while a turn streams (the render-budget slice recycles older rows; the streaming markdown re-parse re-mounts AST leaves), an… |
| `src/components/chat/vibe-hearts.test.ts` | Tests: burstVibeHearts; plays hearts when the preference is on; no-ops when the preference is off; forwards to the popped-out overlay when on |
| `src/components/chat/vibe-hearts.tsx` | TikTok-style floating hearts — a thin skin over { |
| `src/components/chat/widget-shell.ts` | Inline transcript widgets — the few tool results that render as a panel the user reads or acts on (a clarify question, an artifact card) rather than as a scaffold line. They share one shell so they cannot drift apart. T… |
| `src/components/chat/wordmark.tsx` | The oversized display lettering of an empty chat — the Collapse face that writes "HERMES AGENT" across a fresh draft, and a bot's name across its own empty chat. The doubled children are load-bearing, not a typo: `.fit-… |
| `src/components/chat/zoomable-image.test.tsx` | Tests: ZoomableImage lightbox; opens the lightbox when the inline image is activated; renders the lightbox shell transparent, not as a painted box; wheel zooms toward the cursor and prevents the page from scrolling |
| `src/components/chat/zoomable-image.tsx` | Exports `ZoomableImageProps`, `ImageActionCopy`, `ZoomableImage`, `ImageLightbox`, `ImageActionButton` |
| `src/components/confirm-host.test.tsx` | Tests: confirm(); renders nothing until something asks; resolves true when confirmed and false when cancelled; confirms on Enter from wherever focus landed |
| `src/components/confirm-host.tsx` | The one mount point for `confirm()` from @/store/confirm. Mounted once at the shell, the way NotificationStack backs notify(). |
| `src/components/desktop-install-local-card.ts` | Presentation for an install offer or an already-selected local runtime. |
| `src/components/desktop-install-overlay.test.tsx` | @vitest-environment jsdom |
| `src/components/desktop-install-overlay.tsx` | Exports `splitFailureDetails`, `DesktopInstallOverlay` |
| `src/components/error-boundary.test.tsx` | Tests: ErrorBoundary assistant-ui lookup recovery; recovers the production root composition when StrictMode replays its mount lifecycle; stops retrying a persistent lookup error after the recovery budget is exhausted; s… |
| `src/components/error-boundary.tsx` | Exports `ErrorBoundaryFallbackProps`, `ErrorBoundary`, `RootErrorBoundary` |
| `src/components/external-open-failed-dialog.test.tsx` | Tests: ExternalOpenFailedDialog; subscribes, displays, copies and dismisses an external-open failure; shows file-not-found copy for a missing-file failure; renders nothing in a HUD window |
| `src/components/external-open-failed-dialog.tsx` | Exports `ExternalOpenFailedDialog` |
| `src/components/find-bar.test.tsx` | Tests: formatMatchLabel; hides the counter entirely when there is no query; reports an explicit zero when a query matches nothing; formats ordinal over count |
| `src/components/find-bar.tsx` | Exports `FindBar` |
| `src/components/free-tier/notice-owner.test.tsx` | Tests: useFreeTierNoticeOwner; hands the notice to a composer that is still mounted when the owner unmounts |
| `src/components/free-tier/notice-strip.tsx` | Which mounted composer gets to paint the strip. Several can be on screen at once (split zones, a popout mid-dock); the first to mount claims it and the rest report false, so one pending notice never paints N times. The… |
| `src/components/free-tier/sign-in-dialog.test.tsx` | Tests: FreeTierSignInDialog; shows the code small, then the signed-in screen once the poll approves; result screen; shows what moved in the backend lines, and Reconnect opens the app left behind |
| `src/components/free-tier/sign-in-dialog.tsx` | Exports `FreeTierSignInDialog`, `HandoffResult`, `connectorsTarget` |
| `src/components/gateway-connecting-overlay.test.tsx` | Repro for the "remote gateway → stuck on CONNECTING, no way to settings" report. The connecting overlay (full-screen, pointer-events on) used to be shown whenever `gatewayState !== 'open' && !boot.error`. The ONLY escape |
| `src/components/gateway-connecting-overlay.tsx` | Decode mechanics live in the shared <DecodeText> primitive (components/ui/decode-text.tsx). "CONN" stays legible via prefix={4}. |
| `src/components/haptics-provider.registration.test.tsx` | Tests: HapticsProvider registration; registers the live trigger when unmuted and null when muted |
| `src/components/haptics-provider.test.tsx` | web-haptics computes `WebHaptics.isSupported` (typeof navigator.vibrate) once at module load. Desktop Chromium exposes navigator.vibrate as a no-op function, so simulate that BEFORE the library module is imported — |
| `src/components/haptics-provider.tsx` | web-haptics' `debug` option is its desktop audio fallback: on platforms where navigator.vibrate exists (Chromium exposes it as a no-op on desktop) the library plays synthesized click sounds through an |
| `src/components/idle-mount.test.tsx` | Tests: IdleMount; mounts eagerly where requestIdleCallback is unavailable; defers the child to idle, then keeps it mounted |
| `src/components/idle-mount.tsx` | Mounts `children` only once the browser goes idle (or `timeout` ms elapse), then keeps them mounted for good. Lifts non-critical, boot-hidden surfaces (display:none panes: files/preview/review/logs) off the first-paint… |
| `src/components/language-switcher.test.tsx` | Tests: LanguageSwitcher; persists language changes through display.language config; lists a registered language by endonym, renders its pack, and writes its id to display.language; re-lists when a language pack lands af… |
| `src/components/language-switcher.tsx` | Exports `LanguageSwitcherProps`, `LanguageSwitcher` |
| `src/components/model-picker.test.tsx` | The jobs query refetches on mount and would replace a seeded cache entry with whatever the backend answers; answering with the seeded jobs keeps the two equal. |
| `src/components/model-picker.tsx` | Exports `ModelPickerDialog`, `UsageLevelTag`, `PlanLimitLine` |
| `src/components/model-visibility-dialog.test.tsx` | Tests: Edit Models reset; restores the default shortlist when a model is stuck hidden by the known snapshot; keeps the user’s choices when the reset is cancelled; keeps a custom model stored and switched on where the de… |
| `src/components/model-visibility-dialog.tsx` | Exports `ModelVisibilityDialog` |
| `src/components/notifications.test.tsx` | Tests: toast titles |
| `src/components/notifications.tsx` | Exports `NotificationStack`, `NotificationDeck`, `toastTitleClassName`, `InlineNotice` |
| `src/components/onboarding/first-run/assembly.ts` | Exports `openDemoLayout`, `endChatOnboardingSolo`, `keepChatOnboardingLayout`, `assembleChatOnboarding`, `PreviewUndo`, `snapshotChatLayout` … |
| `src/components/onboarding/first-run/intro-copy.css` | The demo layout's narrower reading column (the landed column read a tad too wide). |
| `src/components/onboarding/first-run/intro-copy.tsx` | The boot overlay (the `starting` screen) clears its text before it fades; typing starts under the fade. |
| `src/components/onboarding/first-run/intro.ts` | The intro copy over an empty onboarding chat: it types centred (`playing`), springs up and waits at the top (`landed`) until the backend's first assistant row, which carries the same words, takes its place. |
| `src/components/onboarding/first-run/kickoff.test.ts` | Tests: first-run kickoff; lands on the chat onboarding.start returned and opens the intro over it; reopens a resumed run without the demo layout, at normal size; waits on a slow start with no deadline, and the way out s… |
| `src/components/onboarding/first-run/kickoff.ts` | The opening turn writes the scripted greeting; a chat that already shows it (a resumed run) skips the copy. |
| `src/components/onboarding/first-run/layout.test.ts` | Tests: first-run layout beat; keeps the intro through a preview and grows the window when a layout is committed; keeps the other mode; keeps the Advanced layout the user had when Basic is picked over the demo |
| `src/components/onboarding/flow.test.tsx` | Only the catalog fetch is replaced; the model assignment keeps its real path down to window.hermesDesktop.api so the test observes the wire body. |
| `src/components/onboarding/flow.tsx` | Exports `FlowPanel`, `DeviceCode`, `DocsLink`, `Status` |
| `src/components/onboarding/free-tier-intro.test.ts` | The boot due check has run and no first-run onboarding is open. |
| `src/components/onboarding/free-tier-setup-notice.test.tsx` | Tests: setupFailureCopy; falls back to the backend sentence for a code this build does not know; FreeTierSetupNotice; renders nothing when the backend reported no failure |
| `src/components/onboarding/free-tier-setup-notice.tsx` | Exports `setupFailureCopy`, `FreeTierSetupNotice` |
| `src/components/onboarding/glyph.tsx` | Borrowed from the gateway "connecting" overlay: a mono, letter-spaced label that decodes left-to-right from scrambled glyphs into the real text, with a blinking block cursor. Ties onboarding's success moment to that sam… |
| `src/components/onboarding/index.test.tsx` | Tests: onboarding Picker; features Nous Portal and hides other providers behind a disclosure; shows every provider directly when Nous Portal is absent; offers |
| `src/components/onboarding/index.tsx` | Exports `ApiKeyOption`, `DesktopOnboardingOverlay`, `FEATURED_ID`, `Picker`, `ApiKeyForm` |
| `src/components/onboarding/onboarding-end.test.tsx` | Tests: OnboardingEnd; offers the local model once the settle window passes on a quiet app, once per install; resumes the settle wait after a restart that came before the offer opened; keeps sign-in waiting through a res… |
| `src/components/onboarding/onboarding-end.tsx` | Exports `OnboardingEnd` |
| `src/components/onboarding/providers.tsx` | Titles live in PROVIDER_DISPLAY_NAMES (shared with the model pill); this is only the featured order. Both Anthropic entries sit at the bottom: the API-key path first, then the subscription OAuth path (only works with ex… |
| `src/components/onboarding/skip-gate.test.tsx` | The boot due check has run and no first-run onboarding is open. |
| `src/components/onboarding/skip-setup.test.tsx` | Tests: Skip setup; goes away when the backend ends the run; goes away even when a listener of the ending throws |
| `src/components/onboarding/skip-setup.tsx` | Skip setup, shown in the composer of the onboarding chat only. Once the backend has ended the run, like main's: the intro ends on the previous layout at normal size and the tutorial tips stop. |
| `src/components/overlay-error-boundary.tsx` | Error boundary for the transparent `?win=` overlay windows. Same job as `ErrorBoundary`, none of its weight. That one renders the app's rich fallback, so importing it pulls `Button`, `ErrorState` and the i18n provider —… |
| `src/components/page-loader.tsx` | Exports `PageLoader` |
| `src/components/pane-shell/edit-mode.test.ts` | Layout edit mode force-shows toggle-hidden panes so they can be rearranged. In Simple those panes rest by policy, so edit mode must arrange what Simple shows — otherwise opening the layout editor brings every machinery… |
| `src/components/pane-shell/edit-mode.tsx` | Layout edit mode — the shared toggle for the tree renderer's FancyZones-style rearrangement (see tree/renderer.tsx). The toggle hotkey is a `keybinds` contribution (`layout.editMode`, default ⌘⇧\ — the sibling of ⌘\ = f… |
| `src/components/pane-shell/geometry.ts` | Pane geometry — AABB INTERSECTION → WINDOW-CONTROL AWARENESS. The native window controls (macOS traffic lights top-left / Windows-WSLg overlay top-right) are a rectangle in viewport pixels. Any region whose rect interse… |
| `src/components/pane-shell/index.ts` | Cross-surface event: toggle-reveal a collapsed pane. Dispatched by the keybinds (⌘B / ⌘G / titlebar toggles on narrow viewports) with the pane id in `detail`; the layout tree's narrow overlays (tree/renderer.tsx) listen… |
| `src/components/pane-shell/narrow-overlay-state.ts` | Transient visible overlay pane ids (including aliases and zone mates). Docked/persisted open flags do not describe the narrow overlay. |
| `src/components/pane-shell/pane-lifecycle.test.ts` | Tests: per-zone pane lifecycle; keeps a small recent hidden set and parks older panes; tracks recency independently for each zone state; keeps a hidden terminal alive outside the normal cap |
| `src/components/pane-shell/pane-lifecycle.ts` | Exports `PaneLifecycle`, `DEFAULT_HOT_HIDDEN_PANE_CAP`, `PaneLifecycleState`, `emptyPaneLifecycleState`, `reconcilePaneLifecycle` |
| `src/components/pane-shell/pane-visibility.test.ts` | The live stylesheet, read directly: the painting-contract test below must validate the shipped rule, not a copy of it. Tests run with cwd = apps/desktop (vitest projects root). |
| `src/components/pane-shell/pane-visibility.ts` | Keep-alive visibility — the one policy every document-wide lookup must obey. A tab group keeps each ever-active pane MOUNTED and hides the inactive ones with `visibility: hidden` (see `tree/renderer/tree-group.tsx`), de… |
| `src/components/pane-shell/tree/dock-enforce.test.ts` | Enforced dock invariants: a pane whose dock hint carries `enforce: true` (Bot Mode's Bots pane) re-homes onto its center anchor at EVERY boot's first adoption pass — persisted layouts otherwise pin the stale stacked |
| `src/components/pane-shell/tree/docked-width-churn.probe.test.ts` | Docked-path probe for issue #122761 (NOT part of the shipped suite — a one-shot verification script run from the fix worktree's vitest config). Boots the real tree store like mode-layout-memory.test.ts, writes a sash dr… |
| `src/components/pane-shell/tree/floating-adoption.test.ts` | A `placement: 'floating'` pane must never enter the layout tree. Adoption is what turns a contribution into a track (and therefore into something that steals width from a zone), so this exercises the real `adoptContribu… |
| `src/components/pane-shell/tree/focus-tab-hijack.test.ts` | Focus layout packs `workspace` and `files` into one tab group. A reactive unhide of `files` (cwd arrives on the first reply / new session) must NOT steal the active tab away from the workspace/new-session the user is lo… |
| `src/components/pane-shell/tree/focused-session-tab.test.ts` | ⌘W / ⌘T / ⌘⇧T / the strip "+" used to hardcode the workspace's zone while ⌘1…⌘9 followed the interacted zone — so every tab verb missed a SECOND chat zone the user was working in. They now resolve the same focused zone. |
| `src/components/pane-shell/tree/grid-model.ts` | FancyZones grid model — a faithful port of PowerToys' `FancyZonesEditor/Models/GridLayoutModel.cs` + `FancyZonesEditor/GridData.cs` (microsoft/PowerToys, MIT). Function/field names, algorithms, and invariants follow the… |
| `src/components/pane-shell/tree/grid-to-tree.ts` | Grid -> tree bridge. A FancyZones grid whose zones can be produced by recursive guillotine cuts (every FancyZones template, and almost every practical layout) converts exactly to our runtime `LayoutNode` tree: full-leng… |
| `src/components/pane-shell/tree/hide-only-strip-tabs.test.ts` | Tests: hide-only strip tabs; labels the zone menu rows from the pane string localizer, not the register-time title; hides and shows a chrome tab, keeping the pane in the tree; refuses to hide the zone last visible tab |
| `src/components/pane-shell/tree/hovered-zone-tabs.test.ts` | The tab verbs (⌘1…⌘9, ⌃Tab, ⌘W / ⌘T) target the zone under the POINTER when there is one, so hovering a pane and hitting ⌘2 lands there without clicking in first. Pointer off the panes falls back to the last interacted… |
| `src/components/pane-shell/tree/lone-chat-sibling-zone.test.ts` | Tests: dragging a session tab into its own zone; leaves BOTH chat zones with a strip, and main keeps its own once the tile is gone |
| `src/components/pane-shell/tree/mode-layout-memory.test.ts` | Tests: restores independently customized modes through real pane bindings and reloads |
| `src/components/pane-shell/tree/model.ts` | Layout tree model — the Dockview-style structure that replaces the rails/bands grammar. Two node kinds: - `split`: children laid out along an orientation with fractional weights. - `group`: a stack of panes (tabs) with… |
| `src/components/pane-shell/tree/multi-tab-drag.test.ts` | Tests: movePanes (multi-tab drag); stacks the whole block into the target group at the divider slot, in strip order; an edge drop opens ONE split holding the block as tabs, pressed tab fronted; dragging a whole zone int… |
| `src/components/pane-shell/tree/pane-reload-share.test.ts` | #108679: a hard reload boots with `registered` empty, so the pane-mirror prunes every persisted session-tile pane from the tree — and each removal records its share (0.5 for an evenly-split row) as if it were a user |
| `src/components/pane-shell/tree/pane-reload.test.ts` | Right-click a tab -> Reload remounts THAT pane's content: its epoch (the React key the zone renderer hands the contribution) advances, and no other pane's does. The layout tree itself must never move. |
| `src/components/pane-shell/tree/pane-share-memory.test.ts` | Closing and re-opening a docked tile (the in-app browser) must respect the size the user left it at. Adoption's edge insert used to split the anchor zone [1, 1] every time, so each agent-triggered browser open re-took h… |
| `src/components/pane-shell/tree/pane-toggle-visibility.test.ts` | Tests: a hide-style pane stacked behind a sibling tab; comes forward on the first press instead of swallowing it; a hide-style pane inside a minimized zone; un-minimizes on the first press |
| `src/components/pane-shell/tree/parked-panes.ts` | PARKED PANES — registered contributions that are deliberately OUT of the layout tree. A parked pane keeps its contribution, so a keep-alive body (a live Browser guest) stays mounted — hidden and inert in its keep-alive… |
| `src/components/pane-shell/tree/plugin-pane-close.test.ts` | Tests: closing plugin panes; dismisses one pane without disabling a plugin that contributes multiple panes; keeps disabling a plugin whose only pane is closed |
| `src/components/pane-shell/tree/preset-tree.test.ts` | Tests: stripPresetLivePanes; drops session tiles and keeps the structural rails; drops preview and route tiles, collapsing the zone they emptied; re-points |
| `src/components/pane-shell/tree/preset-tree.ts` | A named layout preset is GEOMETRY (splits, rails, weights, which zones are open) — not a snapshot of the conversations that happened to be on screen when it was saved. `saveCurrentLayoutAs` clones the LIVE tree, which c… |
| `src/components/pane-shell/tree/presets.test.ts` | #94260: a named layout preset is GEOMETRY. Saving cloned the live tree, so a preset carried `session-tile:<storedSessionId>` (from ANY profile — the layout tree and its presets are global) and `preview-tile:*` / |
| `src/components/pane-shell/tree/presets.ts` | Layout presets — the FancyZones treatment. A preset is a CONTRIBUTION (`area: 'layouts'`, `data: LayoutNode`): the app registers its bundled presets as `source: 'core'`, plugins register theirs exactly the same way, and… |
| `src/components/pane-shell/tree/reactive-unhide.test.ts` | Ground-truth repro for "reactive unhides silently re-open a user-collapsed side": `setTreePaneHidden` is the primitive that backs `bindPaneVisibility` (e.g. `bindPaneVisibility('files', $hasWorkspace)`). The original |
| `src/components/pane-shell/tree/remove-pane.test.ts` | Tests: removePane close-neighbor selection; closing a middle active tab keeps you on the tab that slides into its slot; closing the first active tab still advances to the former next tab; closing the last active tab fal… |
| `src/components/pane-shell/tree/renderer/collapse-restore-affordance.test.tsx` | Tests: Sessions/Bots strip — #91223; double-clicking the Sessions tab leaves the strip and both chips; tapping the strip gutter does not collapse the sidebar; an explicit never hides the sessions/Bots strip |
| `src/components/pane-shell/tree/renderer/compact-tab-picker.test.tsx` | Tests: exposes every phone tab and changes the active pane without discarding its draft or siblings; keeps the normal strip on wider layouts; reserves a separate touch row for phone tabs even when the titlebar reports s… |
| `src/components/pane-shell/tree/renderer/compact-tab-picker.tsx` | Exports `CompactTabPicker` |
| `src/components/pane-shell/tree/renderer/drag-session.ts` | THE in-app drag primitive. One pointer-capture session (`startDragSession`) owns the machinery every in-app drag shares — threshold, rAF-coalesced moves, cursor/user-select chrome, ghost chip, Esc-as-top-escape-layer, h… |
| `src/components/pane-shell/tree/renderer/edit-bar.tsx` | Edit-mode palette — the floating, draggable "Layouts" card shown while layout edit mode is on. It hosts the layout picker and the reset/done actions; its header doubles as the drag handle. Position survives edit-mode to… |
| `src/components/pane-shell/tree/renderer/floating-mode-memory.test.tsx` | Loaded once at collection, outside every test's budget: vi.resetModules() keeps each module's transformed code, so the fresh copy a test imports only re-evaluates it. Without this the first test pays the cold transform… |
| `src/components/pane-shell/tree/renderer/floating-panes.test.tsx` | Live-behavior test for FloatingPanes: mounts the REAL component into a real DOM and drives real pointer/resize events. This is the closest thing to "running it" without an Electron main process — it exercises the render… |
| `src/components/pane-shell/tree/renderer/floating-panes.tsx` | Floating panes — the tree's non-tiling placement. `placement: 'floating'` opts a pane OUT of the layout tree: it never becomes a track, never takes width from a zone, and never appears in a tab strip. The tree renders i… |
| `src/components/pane-shell/tree/renderer/floating-rect.test.ts` | Tests: anchoredRect; spawns in the named corner, inset by the margin; never spawns over the reserved top chrome; clampFloatingRect |
| `src/components/pane-shell/tree/renderer/floating-rect.ts` | Floating-pane geometry — pure, so the clamping/anchoring rules are testable without a DOM. A floating pane is NOT a track in the layout tree: it never takes width from a zone. It's a fixed-position card the tree renders… |
| `src/components/pane-shell/tree/renderer/index.tsx` | Layout tree renderer (root). - `split` -> flex row/column; 1px seams between siblings double as resize sashes (the seam IS the boundary — junction-owned, never doubled). See tree-split.tsx. - `group` -> a ZONE: header s… |
| `src/components/pane-shell/tree/renderer/keep-alive-panes.test.tsx` | Tests: keeps a live body continuously connected across replacement IDs, ancestry and missing placement; releases focus held inside a live body when its host is hidden; destroys removed contributions and does not revive… |
| `src/components/pane-shell/tree/renderer/keep-alive-panes.tsx` | Exports `KeepAlivePanes`, `useStablePaneHosts`, `KeepAlivePaneSlot` |
| `src/components/pane-shell/tree/renderer/layout-picker.tsx` | Layout picker — the preset card grid inside the edit palette. Thumbnails are a miniature render of each preset's layout tree; clicking a card applies it, and "Save current arrangement" captures the live tree as a user p… |
| `src/components/pane-shell/tree/renderer/main-placement-floor.test.tsx` | Ground truth for "the main pane always shows, no matter what". Emptying the main strip must never let a sibling absorb the center — the failure Bot Mode shipped, where closing the last bot chat left the roster sidebar s… |
| `src/components/pane-shell/tree/renderer/narrow-overlays.test.tsx` | Ground truth for "the Bots tab is still visible when the sessions sidebar collapses on a narrow window". A collapsible pane DOCKED into the sessions zone (SESSIONS \| BOTS) must leave the grid with the zone, and the nar… |
| `src/components/pane-shell/tree/renderer/narrow-overlays.tsx` | Narrow-viewport edge overlays — the tree's take on the app's hover-reveal collapse. Collapsible panes leave the grid below the sidebar-collapse breakpoint; an edge strip (hover) or PANE_TOGGLE_REVEAL_EVENT (⌘B / ⌘G / ti… |
| `src/components/pane-shell/tree/renderer/pane-body.tsx` | Exports `PaneBody` |
| `src/components/pane-shell/tree/renderer/panel-titlebar-lifecycle.test.tsx` | Tests: titlebar reservation lifecycle; rebinds to replacement nodes and tracks a longer board name under StrictMode; drops narrow panel tabs below the picker and restores them when room returns; refreshes right-caption… |
| `src/components/pane-shell/tree/renderer/panel-titlebar.test.tsx` | The panel tab strip (SESSIONS \| BOTS) reserves the width the fixed titlebar clusters cover by MEASURING them. On a macOS fullscreen transition the left cluster moves to the window edge without changing size, so neither… |
| `src/components/pane-shell/tree/renderer/panel-titlebar.ts` | The window-chrome inputs that move the fixed titlebar clusters without changing their size (macOS fullscreen hides the traffic lights → the left cluster pins to the window edge). |
| `src/components/pane-shell/tree/renderer/strip-visibility.test.ts` | Tests: auto (no stored choice); gives a lone workspace its strip so the tab and + stay on screen; leaves standing side chrome alone in its own zone; has nothing to draw for an empty zone |
| `src/components/pane-shell/tree/renderer/strip-visibility.ts` | Does this zone show its tab strip? One resolver, one precedence order, so every caller gets the same answer and the rule can be read in one place. The decision used to be an inline expression in TreeGroup fed by a flag… |
| `src/components/pane-shell/tree/renderer/tab-close-affordance.test.tsx` | The hover ✕ and middle-click are ONE affordance in two shapes: whichever tabs the pointer gesture can close must advertise it. A tab that closes on middle-click but hides its ✕ is a close verb the user cannot discover,… |
| `src/components/pane-shell/tree/renderer/tab-strip-hide.test.tsx` | Tests: tab strip hide grammar; no pointer gesture hides the strip; the toggle command reaches a zone that has no chrome left to click |
| `src/components/pane-shell/tree/renderer/tab-strip-scroll.test.ts` | Tests: tabStripScrollLeft; scrolls to the end for the last tab so the ; leaves the offset alone when the tab is already fully visible; scrolls left to the tab start when it sits before the window |
| `src/components/pane-shell/tree/renderer/tab-strip-scroll.ts` | Keeping the active tab (and the trailing "+") inside a scrolling tab strip. Once a zone has more tabs than fit, opening a new one appended it past the right edge: the tab you just created — and the "+" that created it —… |
| `src/components/pane-shell/tree/renderer/tool-panel-close.test.tsx` | Tests: right-clicking a tool panel tab; offers Close when logs is STACKED with the terminal; offers Close when logs is ALONE in its zone; offers Close while the zone is MINIMIZED to its rail |
| `src/components/pane-shell/tree/renderer/track-model-absorber.test.ts` | Tests: allFixedAbsorberIndex; picks the last uncapped track; skips a capped last track and picks an earlier uncapped one; refuses to absorb when every fixed track is capped (review/files rail) |
| `src/components/pane-shell/tree/renderer/track-model.ts` | The TRACK MODEL — how a layout node resolves its size along a split axis. A node is a FIXED track when it resolves to a CSS length (sidebars keep their declared size) and a FLEX track when it doesn't (weight-shared left… |
| `src/components/pane-shell/tree/renderer/tree-group.test.tsx` | Tests: TreeGroup; top-edge window drag handle; renders page controls inside their own panel in the normal tab space; keeps a fixed drag handle outside the tablist when tabs share the titlebar |
| `src/components/pane-shell/tree/renderer/tree-group.tsx` | Group node renderer — a ZONE: header strip (tabs when stacked, minimize chevron) + the active pane's content, resolved from the contribution registry (`area: 'panes'`). Empty zones exist only in editor-authored trees (d… |
| `src/components/pane-shell/tree/renderer/tree-node.tsx` | Dispatch a layout node to its renderer — the split/group recursion point. `root` marks the tree's top split (side collapse applies only there). `rootRow` marks the row split that owns the side columns — usually the root… |
| `src/components/pane-shell/tree/renderer/tree-split-cascade-resize.test.tsx` | Tests: TreeSplit cascading expansion; grows Browser through Cron into Chat after Cron reaches its minimum; commits a regular cascade when an unrelated tool rail is already minimized; folding a tool zone at its floor lea… |
| `src/components/pane-shell/tree/renderer/tree-split-sash-preview.test.tsx` | Tests: TreeSplit nested section sash preview; sizes the section wrapper from its pointerdown width and previews the inner zone; previews a nested section reached by a cascade past the seam partner |
| `src/components/pane-shell/tree/renderer/tree-split.test.tsx` | Tests: TreeSplit sash drag cleanup; restores both seam wrapper styles when the released px is a store no-op; runs the full drag teardown when the store commit throws |
| `src/components/pane-shell/tree/renderer/tree-split.tsx` | Split node renderer — a flex row/column whose 1px seams double as resize sashes (the seam IS the boundary — junction-owned, never doubled). Sizing is the TRACK MODEL (track-model.ts): fixed tracks keep their declared si… |
| `src/components/pane-shell/tree/renderer/zone-header-layout.ts` | The desktop tab strip's row (`h-7`). |
| `src/components/pane-shell/tree/resting-presets.test.ts` | Tests: resting presets; keeps the arrangement and closes the resting panes through their stores; a deck saved from the live layout remembers what was closed; a reveal on apply never steals the tab the preset put first |
| `src/components/pane-shell/tree/side-collapse-native.test.ts` | The real tree and side stores in a native Desktop renderer: the Electron preload's bridge is present and no browser-host marker is set. |
| `src/components/pane-shell/tree/side-collapse-persistence.test.ts` | Re-import real stores over the same storage, as a page refresh does. The workspace is available; Files keeps its own toggle, independent of its side. |
| `src/components/pane-shell/tree/store.ts` | Layout tree store: one persisted tree replaces paneStates side/band overrides. The DEFAULT tree is declared by the app root (like config); the persisted tree is the user's customization; reset returns to default. |
| `src/components/pane-shell/tree/tab-key-hint-state.ts` | Exports `useTabKeyHints` |
| `src/components/pane-shell/tree/tab-key-hints.test.tsx` | Tests: reveals only the shortcut target after a hold and clears on release, blur or capture |
| `src/components/pane-shell/tree/tab-key-hints.tsx` | Subscribe in the tiny lead, not the pane/transcript subtree. |
| `src/components/pane-shell/tree/tab-selection.ts` | Multi-tab selection on a zone's tab strip — Chrome's tab-selection grammar: - ⌥-click (Ctrl-click off-Mac) → toggle the tab in/out of the selection; - Shift-click → select the range from the anchor (the last explicitly… |
| `src/components/pane-shell/tree/tab-slot-shown.test.ts` | ⌘1…⌘9 / ⌃Tab must index the same tabs the strip paints. A chrome-hidden pane (Focus layout's `files`) stays in `group.panes` but isn't a chip — indexing the raw array made ⌘2 land on the strip's first session tab. |
| `src/components/pane-shell/tree/tabstrip-migration.test.ts` | A stored `headerHidden: true` is ambiguous — a deliberate "Hide header" and an accidental double-tap wrote the same byte — and it is the state people got stuck in, because hiding removed the only control offering to unh… |
| `src/components/pane-shell/tree/tool-pane-toggle.test.ts` | Tests: binding a tool panel on boot; does not front itself over the tab the persisted tree had active; leaves ⌃; still collapses a tool panel whose store says it is off |
| `src/components/pane-shell/tree/zone-editor-split-preview.test.tsx` | Split preview follows the pointer before a click. Pointermove outruns a frame, and a repeated event in the same snap cell must not write again. Shift flips the line on the next frame while the pointer is still in the ca… |
| `src/components/pane-shell/tree/zone-editor.tsx` | Zone editor — the FancyZones grid editor experience, ported from PowerToys' `GridEditor.xaml.cs` interactions onto the verbatim model port (grid-model.ts): - A full-screen canvas of numbered translucent zones. - A split… |
| `src/components/pane-shell/tree/zones-engine.ts` | FancyZones runtime engine — verbatim port of the drag/highlight internals from PowerToys `FancyZonesLib` (microsoft/PowerToys, MIT): - `Layout.cpp` -> `zonesFromPoint` (sensitivity-radius capture, the "captured but not… |
| `src/components/pane-shell/workspace-scope.test.ts` | Tests: workspace scope; publishes a coherent mode and owner in one batch; publishes the exact new-session route with its Bot owner; workspace owner title |
| `src/components/pane-shell/workspace-scope.ts` | Which workspace surface the window is looking at — sessions, or one exact bot inside Bot Mode. Owner keys are opaque exact strings supplied by callers; this module never parses profile names or infers connections. This… |
| `src/components/particles/particle-field.css` | ── Particle field ───────────────────────────────────────────────────────── Reusable float-up emitter. Three nested layers, each owning ONE transform so they never fight: .particle — full-height track: vertical rise + f… |
| `src/components/particles/particle-field.tsx` | Reusable float-up particle emitter. It owns the motion (rise + organic sway + springy pop) and lifecycle (staggered burst, lifetime, cleanup); callers just hand it a `glyph` (any element using `currentColor`) and `color… |
| `src/components/pet/floating-pet.tsx` | Exports `FloatingPet` |
| `src/components/pet/pet-bubble.tsx` | Speech bubble + status glyph for the pet — the "notification" half of the mascot. It externalizes what the agent is doing (Codex-style) so a glance at the desktop pet replaces switching back to the window. The core stat… |
| `src/components/pet/pet-egg-hatch.tsx` | Egg-hatch visuals for the pet generation flow (Cmd-K → Pets → Generate). `PetEggHatch` is the incubation beat shown while `pet.hatch` runs: a wobbling egg that reads as "something is about to hatch" instead of a bare sp… |
| `src/components/pet/pet-egg-sheet.png` | PNG image asset |
| `src/components/pet/pet-info-poll.ts` | Cadences for the floating-pet `pet.info` refresh timer. Event-capable backends rely on `pet.changed` for live updates but still need a slow backstop: the gateway seeds the pet signature silently at boot and only broadca… |
| `src/components/pet/pet-sprite.test.tsx` | Tests: PetSprite RAF scheduling; sleeps between visible sprite frames instead of chaining RAFs; uses a DPR-sized backing store while preserving the CSS footprint; cancels pending RAF work while the Electron window is pa… |
| `src/components/pet/pet-sprite.tsx` | Exports `DEFAULT_STATE_ROWS`, `roamWalkRow`, `PetSprite` |
| `src/components/pet/pet-star-shower.tsx` | Canvas hatch celebration layered over a freshly revealed pet: a one-shot sunburst of rotating god-rays, a fast radial star burst (confetti physics — velocity + decay + gravity + spin), and a light trickle of rising twin… |
| `src/components/pet/pet-thumb.tsx` | petdex frames are a fixed 192×208 grid; the box matches that aspect. |
| `src/components/pet/pixel-egg-sprite.test.tsx` | Tests: PixelEggSprite scheduling; sleeps during the long bounce rest instead of chaining RAFs; stops scheduling frames after the final hatch frame; cancels a pending animation frame even when the browser assigns ID zero |
| `src/components/pet/pixel-egg-sprite.tsx` | Animated pixel egg — the iamcrog "bouncing hatching egg" 12-frame sheet (32×32 cells, stacked vertically), drawn to a canvas and recolored to a warm white/creme shell. The sheet's shell is mid-gray, so a plain multiply… |
| `src/components/pet/roam-behavior.test.ts` | Tests: dwellMs; clamps the degenerate draws to the floor and ceiling; returns the mean at the exponential median point; stays within [min, max] across the whole rng domain |
| `src/components/pet/roam-behavior.ts` | Pure decision helpers for the floating pet's wander — the "what to do & when" layer, split out from the geometry (`roam-geometry.ts`) and the RAF/DOM loop (`use-pet-roam.ts`) so the *rhythm* of the roam is tunable in on… |
| `src/components/pet/roam-geometry.test.ts` | Tests: overlapsX; is true only when the walkable ranges share real width; resolveLedge; returns the highest surface at or below the feet under the current x |
| `src/components/pet/roam-geometry.ts` | The "where can it stand" layer of the floating pet's wander: it measures the live DOM for walkable surfaces and answers pure questions about them. Split from the decision logic (`roam-behavior.ts`) and the RAF/DOM loop… |
| `src/components/pet/use-pet-roam.test.tsx` | Tests: usePetRoam RAF scheduling; uses a pause timer, not RAF, while dwelling at idle; clears the pause wakeup while the Electron window is paused and restarts it when visible; keeps idle movement scheduled while unfocu… |
| `src/components/pet/use-pet-roam.ts` | Exports `usePetRoam` |
| `src/components/pet/use-pet-zoom-gesture.ts` | Where the gesture happened + how much it scaled — lets callers zoom toward the cursor (keep the pixel under it fixed) instead of growing from a corner. |
| `src/components/prompt-overlays.test.tsx` | Tests: PromptOverlays; shows the full command from the sudo request before accepting a password; answers the live sudo request with an empty value on Cancel and clears the dialog; dismisses a stale sudo dialog when the… |
| `src/components/prompt-overlays.tsx` | Exports `PromptOverlays` |
| `src/components/prompt-overlays.vault-code.test.tsx` | Tests: answers the vault.code server request with the trimmed code, never the ambient gateway; Skip answers an empty code and clears the card |
| `src/components/prompt-overlays.vault-save-login.test.tsx` | Tests: answers the vault.save_login server request with identifier + password as one JSON value; Don |
| `src/components/prompt-overlays.vault-unlock.test.tsx` | Tests: answers the vault.unlock server request with the master password, never the ambient gateway |
| `src/components/provider-status-chip.test.tsx` | Tests: keeps a mixed pool usable and exposes each account rather than a provider-wide empty gauge; only presents a pool-wide wall when every account is limited, preserving unknown and expired states |
| `src/components/provider-status-chip.tsx` | Exports `ProviderStatusChip` |
| `src/components/remote-display-banner.tsx` | GPU acceleration is disabled under remote display (RDP/VNC/etc) to avoid flicker. Surfaces once per launch as a persistent toast through the shared notification stack — was a hand-rolled second top-center card at these… |
| `src/components/remote-setup/fields.tsx` | Exports `RemoteSetupFields` |
| `src/components/remote-setup/first-run.tsx` | Exports `FirstRunRemoteSetup` |
| `src/components/remote-setup/use-remote-connection-test.ts` | Exports `RemoteConnectionTest`, `useRemoteConnectionTest` |
| `src/components/remote-setup/use-remote-oauth.ts` | Exports `RemoteOAuth`, `useRemoteOAuth` |
| `src/components/remote-setup/use-remote-probe.ts` | Exports `useRemoteProbe` |
| `src/components/remote-setup/use-remote-setup.test.tsx` | Tests: remote setup owner; does not publish login completion after the editor unmounts without a probe bridge |
| `src/components/remote-setup/use-remote-setup.ts` | Exports `RemoteSetupHost`, `RemoteCredentials`, `RemoteSetupOptions`, `RemoteSetup`, `useRemoteSetup` |
| `src/components/send-diagnostics-dialog.tsx` | Send Diagnostics — the consent-gated debug-bundle upload dialog. Rendered globally (wiring.tsx, beside ConfirmHost) and driven by the $sendDiagnostics store: any surface (the failed-turn error card today) |
| `src/components/session-picker.tsx` | Exports `SessionPickerDialog` |
| `src/components/shared-metrics/consent-dialog.test.tsx` | Tests: SharedMetricsConsentDialog; never blocks launch: an undecided profile becomes a composer offer, not a modal; details decide nothing when closed and record a chosen answer as both opt-ins |
| `src/components/shared-metrics/consent-dialog.tsx` | Exports `SharedMetricsConsentDialog` |
| `src/components/shared-metrics/consent-strip.test.tsx` | Tests: SharedMetricsConsentStrip; offers two answers, and sharing sets both opt-ins on the focused profile |
| `src/components/shared-metrics/consent-strip.tsx` | Exports `SharedMetricsConsentStrip` |
| `src/components/status-dot.tsx` | Exports `StatusTone`, `StatusDot` |
| `src/components/sync-status-card.test.tsx` | Tests: a rejected bridge leaves the overlay usable |
| `src/components/sync-status-card.tsx` | SyncStatusCard — the desktop warning surface for the latest pm/plugin sync receipt (SPEC-05). The renderer calls `getSyncStatus` here and paints the derived summary: failed venv rebuilds, dependency-bisect disables, nee… |
| `src/components/sync-status.ts` | Derive display state from a pm receipt — the pure logic behind the sync-status surface. Receipts are optional-typed (older/newer receipts may lack sections), so every derive degrades gracefully to 'nothing to show' rath… |
| `src/components/tips/index.tsx` | TIP HOST — one per window, renders nothing until the app has something to say. It owns what the bubble itself must not: keeping the anchor honest, marking it while the arrow is on it, and knowing when a tip has had its… |
| `src/components/tips/local-runtime-update-offer.test.tsx` | Tests: discards a completed read that waited too long for a quiet tick; lets rotation proceed after a failed eligibility read and retries at a later due moment; rechecks backend jobs at the due moment instead of trustin… |
| `src/components/tips/local-runtime-update-offer.ts` | Exports `offerLocalRuntimeUpdateTip` |
| `src/components/tips/tip-bubble.tsx` | THE TIP BUBBLE — a pointer, not an overlay. The app's popover, in its accent variant: same box, same arrow, same placement engine, filled instead of glassed. Nothing here re-implements the surface — a tip that drifted f… |
| `src/components/tips/tips.css` | THE POINTED-AT THING. A tip has no scrim and no spotlight — the arrow is the whole mechanism — so the subject gets marked rather than the rest of the app getting dimmed. The host hangs `data-tip-target` on the subject —… |
| `src/components/tips/tutorial-lifetime.test.tsx` | Tests: retires both tutorial features after 30 days across launches, then keeps a manual re-enable; uses existing tip history on upgrade without treating invalid dates as experience |
| `src/components/tips/use-tip-rotation.test.tsx` | Onboarding's due check answered "not due": first-run surfaces are free to show. |
| `src/components/tips/use-tip-rotation.ts` | The rotation's clock: a few minutes into a launch, then hours apart, offer a tip if the app happens to be quiet. On unless the user turned it off (Settings → Appearance). An agent tip doesn't come through here at all. T… |
| `src/components/ui/__tests__/no-native-title.test.ts` | Static-analysis guard: no <button> or <Button> element in the desktop renderer may use the native HTML `title=` attribute. Native tooltips are unstyled, delayed (~500ms OS default), and visually inconsistent with the th… |
| `src/components/ui/accent-swatch.tsx` | One accent colour as a round swatch; with `onColorChange` it is the custom-colour well. |
| `src/components/ui/action-status.tsx` | idle → saving → done label+icon for action buttons (create / rename / delete…). |
| `src/components/ui/actions-menu.test.tsx` | Tests for `actions-menu` |
| `src/components/ui/actions-menu.tsx` | Exports `MenuKit`, `DROPDOWN_KIT`, `CONTEXT_KIT`, `ActionItemSpec`, `renderActionItem`, `ActionsMenu` … |
| `src/components/ui/alert.tsx` | TypeScript React component: `alert` |
| `src/components/ui/avatar-chip.test.tsx` | Tests: the identity ladder; prefers a brand-supplied monogram over the first letter; lets a caller replace the mark entirely, which is how a resolved favicon gets in; the monogram |
| `src/components/ui/avatar-chip.tsx` | The square identity chip: a brand glyph on a 16% tint of its own color, or a letter monogram when we have no mark for the thing. One treatment, three surfaces — messaging platforms, the MCP servers tab, connector cards… |
| `src/components/ui/badge.tsx` | Small status/metadata tag. App radius (not a full pill); tones map to the shared accent/muted/destructive surfaces so badges read consistently. |
| `src/components/ui/button.tsx` | Text+icon actions underline the label on hover, not the glyph. |
| `src/components/ui/card-stack.test.tsx` | Tests: CardStack completion footprint; retires the footprint while the final card departs, not after it disappears; keeps the next live card measured when a previous departure finishes |
| `src/components/ui/card-stack.tsx` | Exports `CardStackDirection`, `CardStackAction`, `CardStack` |
| `src/components/ui/checkbox.tsx` | TypeScript React component: `checkbox` |
| `src/components/ui/chip.tsx` | Exports `selectableClass`, `Chip` |
| `src/components/ui/codicon.tsx` | Exports `CodiconProps`, `Codicon`, `codiconIcon` |
| `src/components/ui/color-swatches.tsx` | Exports `ColorSwatches` |
| `src/components/ui/command.tsx` | TypeScript React component: `command` |
| `src/components/ui/confirm-dialog-unmount.test.tsx` | Tests: the close timer does not fire after unmount |
| `src/components/ui/confirm-dialog.test.tsx` | Tests: ConfirmDialog secondary action; runs the secondary action and closes without confirming; still opens focused on Confirm, so Enter confirms rather than picking the secondary |
| `src/components/ui/confirm-dialog.tsx` | Exports `ConfirmDialog` |
| `src/components/ui/connector-card.test.tsx` | Tests: a row in the card; says how it stands through the mark, so the verb never has to; holds its verb while it runs; has nothing to press once it is done |
| `src/components/ui/connector-card.tsx` | Presentation leaf: callers own connector semantics and localized copy. The card offers; the transcript explains. One shell, one heading, one row per app. A row carries a mark, a name, at most one cue and at most one ver… |
| `src/components/ui/connector-logo.tsx` | The least a mark needs: something to name it, and somewhere a logo might live. Structural on purpose — a caller's richer connector type satisfies this without the visual layer knowing that type exists. |
| `src/components/ui/context-menu.tsx` | Exports `HERMES_CONTEXT_MENU_TRIGGER_ATTR` |
| `src/components/ui/control.ts` | Single source of truth for non-composer form-control chrome — Input, Textarea, and SelectTrigger all consume this. Mirrors `buttonVariants`: 2.5px radius, 12px text, padding-driven sizing (no fixed heights). The visual |
| `src/components/ui/copy-button.tsx` | Exports `CopyButtonProps`, `CopyButton` |
| `src/components/ui/decode-text.test.tsx` | The decode scramble is decorative. Once a quiet-surface placeholder (empty pane zone, contrib panes) has resolved and held, its interval must be gone: a replaying default kept a 22 Hz setState ticker alive for as long a… |
| `src/components/ui/decode-text.tsx` | DecodeText — the "CONNECTING" scramble-decode effect as a reusable primitive (extracted from gateway-connecting-overlay.tsx; same mechanics): - Even-weight mono ascii charset so cycling glyphs never jump width (matches… |
| `src/components/ui/dialog-dismiss-repro.test.tsx` | Tests: REPRO: dismissing an open Select inside a Dialog; closes only the select, not the dialog, when the press lands on the overlay; still closes the dialog on a genuine overlay click when no dropdown is open |
| `src/components/ui/dialog-portal-context.ts` | Layering system for portalled popovers (Select / Popover / DropdownMenu) that open INSIDE a Dialog. By default every Radix popover portals to `document.body`, i.e. as a sibling |
| `src/components/ui/dialog.test.tsx` | Tests: DialogContent close button; closes the dialog when clicked |
| `src/components/ui/dialog.tsx` | Exports `preventCloseButtonAutoFocus` |
| `src/components/ui/diff-count.tsx` | Snappy spring — fast transitions per the design. |
| `src/components/ui/disclosure-caret.tsx` | Exports `DisclosureCaret` |
| `src/components/ui/drop-affordance.tsx` | Shared drag-and-drop visual language — ONE dashed accent sheet, used by every drop affordance (the composer file/session overlay, the layout zone targets) so "you can drop here" reads identically everywhere. |
| `src/components/ui/dropdown-menu.test.tsx` | Tests: DropdownMenuSearch hover focus; keeps focus in the search field while the mouse moves over rows (#53980); still highlights the hovered row without taking focus; opens a hovered submenu and closes it when another… |
| `src/components/ui/dropdown-menu.tsx` | Exports `dropdownMenuRow`, `dropdownMenuSectionLabel` |
| `src/components/ui/empty-state.tsx` | Canonical centered empty state (title + description). The default for "no results / nothing here yet" page bodies. For richer master-detail lists that want an icon + action, use PanelEmpty (overlays/panel); the file-tre… |
| `src/components/ui/error-state.tsx` | The single canonical error glyph (codicon's filled error mark). Use this everywhere an error is surfaced (boundaries, dialogs, banners) so failures read identically — one icon, one color, no background chip. |
| `src/components/ui/fade-scroll.test.ts` | Tests: scrollEdges; reports no clipped edge when the content fits; reports only the bottom at the top of a clipped list; reports both edges mid-scroll |
| `src/components/ui/fade-scroll.tsx` | How much of a clipped edge the gradient eats. |
| `src/components/ui/fade-text.tsx` | Exports `FadeText` |
| `src/components/ui/fan-menu-tooltip.test.tsx` | Tests: FanMenu hub tooltip; keeps an explicit side override when the fan opens |
| `src/components/ui/fan-menu.test.ts` | Tests: fanOffsets; stacks a column straight up, one step apart; splits a row around the hub in reading order, extra one on the right; keeps arc neighbours one step apart and clear of the hub |
| `src/components/ui/fan-menu.tsx` | Exports `FanDirection`, `FanMenuItem`, `FanMenuProps`, `fanOffsets`, `FanMenu` |
| `src/components/ui/favicon.tsx` | A site's icon, resolved the thorough way. The work happens in the main process (`electron/favicon.ts`): read the page, collect every declared `<link rel="icon">` and web-app-manifest icon, rank them, then fall back to t… |
| `src/components/ui/field.tsx` | Shared form-field primitive for dialog forms: a label stacked above its control, with an optional inline "(optional)" tag. Pair with FieldHint for help text below the control. This is the single field language for every… |
| `src/components/ui/file-type-icon.tsx` | Exports `FileTypeIconProps`, `FileTypeIcon` |
| `src/components/ui/generate-button.tsx` | Exports `GenerateButton` |
| `src/components/ui/glyph-spinner.css` | Compositor-only glyph spinner. The previous implementation ticked a setInterval and replaced `glyph.textContent` every frame. Replacing a text node is a structural DOM mutation, so each tick scheduled a style recalculat… |
| `src/components/ui/glyph-spinner.test.tsx` | GlyphSpinner animates on the compositor: every frame is in the DOM from mount and a transform keyframes animation scrolls between them. It has no timer and performs no per-frame DOM write, because the setInterval + |
| `src/components/ui/glyph-spinner.tsx` | Exports `GlyphSpinnerVars`, `GlyphSpinner` |
| `src/components/ui/guest-shell.test.ts` | @vitest-environment jsdom |
| `src/components/ui/highlight-matches-model.test.tsx` | Tests: folds separators only for model filters and preserves the original marked text |
| `src/components/ui/highlight-matches.test.tsx` | Tests: HighlightMatches; wraps every case-insensitive occurrence in a <mark> without altering the text; renders plain text when the query is empty or does not occur in this label; normalizes the query the same way the p… |
| `src/components/ui/highlight-matches.tsx` | Emphasize every case-insensitive occurrence of `query` inside `text` — the "why is this row in my filtered list" affordance for searchable pickers. Renders semantic `<mark>`s (screen readers announce them as highlighted… |
| `src/components/ui/input.test.tsx` | Tests: Input; forwards value/onChange through the adorned field; disables the field when disabled |
| `src/components/ui/input.tsx` | `prefix`/`suffix` are DOM string attributes on the native element; we shadow them with ReactNode adornments, so they're omitted from the base props. |
| `src/components/ui/kbd.tsx` | TypeScript React component: `kbd` |
| `src/components/ui/keyboard-first.test.ts` | Tests: usePointerQuiet; starts quiet so a list opening under a parked cursor cannot hover-select; wakes on real pointer movement and stays awake; treats a scroll as a hand on the mouse |
| `src/components/ui/keyboard-first.ts` | KEYBOARD-FIRST OVERLAYS — the shared contract for anything you open with a hotkey and drive from a search field: the composer model menu, the ⌘K palette, every cmdk picker. Both halves exist because a mouse that is mere… |
| `src/components/ui/loader.tsx` | Exports `LOADER_TYPES`, `LoaderType`, `Loader` |
| `src/components/ui/log-view.tsx` | Shared raw-log viewer: no bg, hairline border, tight padding, small mono. One style everywhere we surface logs. Pass a max-h-* via className. Selectable by default — logs exist to be read and copied. |
| `src/components/ui/masonry.css` | Stylesheet |
| `src/components/ui/masonry.tsx` | Native grid lanes when available; measured lanes for older Electron releases. Children stay in source order and never move between React parents. |
| `src/components/ui/menu.ts` | The one floating-list look. DropdownMenu, Select, and every Popover + cmdk picker (`<PopoverContent variant="menu">` + `<Command variant="menu">`) paint through these, so a list reads the same wherever it opens. Change… |
| `src/components/ui/pagination.tsx` | TypeScript React component: `pagination` |
| `src/components/ui/pane-tab.test.tsx` | Tests: PaneTab close gestures; middle-click closes — pointer events only, no auxclick; ⌘-click (metaKey + button 0) closes — the Mac middle-click equivalent; ⌘-click preempts the shell drag/activate pointerdown handler |
| `src/components/ui/pane-tab.tsx` | Inset stroke for a vertical tab rail — content-facing edge. |
| `src/components/ui/popover.tsx` | TypeScript React component: `popover` |
| `src/components/ui/preview-document-frame.test.tsx` | Tests: keeps native Desktop srcdoc and its original script permission |
| `src/components/ui/preview-document-frame.tsx` | Exports `PreviewDocumentFrame` |
| `src/components/ui/profile-glyph.test.tsx` | Tests: ProfileGlyph; preserves the first readable grapheme across scripts and emoji; keeps the default profile home mark instead of using an initial |
| `src/components/ui/profile-glyph.tsx` | A profile's mark, in one place: the default profile is the `home` icon (it has no color of its own and an initial would read as just another named profile); every other profile is a soft tint of its color carrying its i… |
| `src/components/ui/progress.tsx` | Exports `ProgressProps`, `Progress` |
| `src/components/ui/reel.tsx` | One row that scrolls sideways, snapping each child to the start edge. Children keep their own width; set it from the caller (`*:w-68`). |
| `src/components/ui/row-button.test.tsx` | Tests: RowButton; renders a real <button> with type=button so it never submits an enclosing form |
| `src/components/ui/row-button.tsx` | A full-row / region click target rendered as a real `<button>`: bakes in `type="button"` + a stable `data-slot`, imposes no styling (callers keep their own layout classes, so nothing changes visually). Use for row/regio… |
| `src/components/ui/sandboxed-frame.test.tsx` | @vitest-environment jsdom |
| `src/components/ui/sandboxed-frame.tsx` | The sandbox posture guest content gets by default: scripts run, the frame has an OPAQUE origin (no reach into the app, its storage, or the bridge). |
| `src/components/ui/sanitized-input.tsx` | Exports `SanitizedInput` |
| `src/components/ui/scroll-area.tsx` | TypeScript React component: `scroll-area` |
| `src/components/ui/search-field.test.tsx` | Tests: SearchField; lays the input out as a flex child so the clear button pins to the row edge; keeps clear wired to the value reset; renders no clear button while empty or loading |
| `src/components/ui/search-field.tsx` | Exports `SearchField` |
| `src/components/ui/segmented-control.tsx` | Exports `SegmentedControlOption`, `SegmentedControl` |
| `src/components/ui/select.tsx` | TypeScript React component: `select` |
| `src/components/ui/separator.tsx` | TypeScript React component: `separator` |
| `src/components/ui/setup-field-list.tsx` | Exports `SetupField`, `SetupFieldList` |
| `src/components/ui/setup-form-dialog.tsx` | Exports `SetupFormDialog` |
| `src/components/ui/sheet.tsx` | TypeScript React component: `sheet` |
| `src/components/ui/sidebar.tsx` | TypeScript React component: `sidebar` |
| `src/components/ui/skeleton.tsx` | TypeScript React component: `skeleton` |
| `src/components/ui/slider.tsx` | The one range control: a hairline track in the app's stroke tint with the native thumb in the primary accent. Settings rows compose it beside a readout or inside a labelled group; nothing hand-rolls `type="range"`. |
| `src/components/ui/split-button.tsx` | Exports `SplitButtonAction`, `SplitButton` |
| `src/components/ui/status-pulse.test.tsx` | Tests: StatusPulse; plays a finite ping and sleeps between pulses; cancels scheduled work while minimized and restarts once visible; stays static when reduced motion is requested |
| `src/components/ui/status-pulse.tsx` | Exports `StatusPulseProps`, `StatusPulse` |
| `src/components/ui/switch.tsx` | TypeScript React component: `switch` |
| `src/components/ui/tab-dropdown.tsx` | Exports `TabMeta`, `tabMetaContent`, `TabDropdownItem`, `TabDropdown`, `ResponsiveTab`, `ResponsiveTabs` |
| `src/components/ui/tabs.tsx` | TypeScript React component: `tabs` |
| `src/components/ui/text-tab.tsx` | TypeScript React component: `text-tab` |
| `src/components/ui/textarea.tsx` | TypeScript React component: `textarea` |
| `src/components/ui/title-menu-trigger.tsx` | Compact "Label ▾" chrome trigger. Domain-agnostic — drop in as the child of `DropdownMenuTrigger asChild` (or any asChild menu trigger). Sessions, projects, filters, etc. own their menus; this only owns the trigger look. |
| `src/components/ui/tool-icon.tsx` | Solid (filled) glyphs for in-thread tool rows. Codicons are an outline icon *font*, so an outline glyph has no separate fillable region — a filled look can't be derived from it (stroke-thickening just bolds the outline)… |
| `src/components/ui/tooltip-pane-layout.test.tsx` | Tests: opens a tip whose nearest tree-group host has no layout; resolves the pane at open time, not at mount |
| `src/components/ui/tooltip-placement.test.tsx` | Tests: tooltip placement; uses the owning pane for a control without changing its trigger; skips a tree-group host without layout and clips against the enclosing pane; allows a control to opt out of its pane boundary |
| `src/components/ui/tooltip-placement.ts` | Exports `TooltipPlacement`, `TOOLTIP_PLACEMENTS` |
| `src/components/ui/tooltip-rail-edge.test.tsx` | Tests for `tooltip-rail-edge` |
| `src/components/ui/tooltip.css` | Stylesheet |
| `src/components/ui/tooltip.test.tsx` | Radix opens tooltips on ANY trigger focus; menus/dialogs restore focus to their trigger on close, which left tips stuck open after a mouse pick (e.g. the composer model pill). The trigger's focus handler must preventDef… |
| `src/components/ui/tooltip.tsx` | Default hover-open delay for `Tip`. Below 150ms a passing cursor still opens the tip; above 250ms an intentional hover feels broken. Call sites that need an instant tip pass `delayDuration={0}`. |
| `src/components/ui/use-zoom-pan.ts` | Exports `FIT_MIN_SCALE`, `useZoomPan` |
| `src/components/ui/zoomable-fit.test.tsx` | jsdom computes no layout: the fit path reads clientWidth/clientHeight off the stage and scrollWidth/scrollHeight off the content wrapper, so plain DOM properties can stand in for real geometry. The fake observer mirrors |
| `src/components/ui/zoomable.test.tsx` | Tests: Zoomable; opens the full-view overlay when the trigger is clicked |
| `src/components/ui/zoomable.tsx` | Exports `Zoomable` |
| `src/components/update-hold-overlay.tsx` | Exports `UpdateHoldOverlay` |
| `src/components/update-status.test.tsx` | VersionHero is the shared About/overlay hero. Its module imports the real updates store graph; mock it shallowly — these tests exercise the hero's own rendering, not the store. |
| `src/components/update-status.tsx` | Exports `UpdateStatusTone`, `UpdateStatusView`, `deriveUpdateStatus`, `VersionHero`, `UpdateStatusCard` |
| `src/components/version-details.test.tsx` | Tests: VersionDetails; opens the commit URL via the system-browser bridge without opening a preview tab; names the source channel, and offers the change action only where the caller passes one |
| `src/components/version-details.tsx` | Human label for an external build's runtime source: the resolution rung plus the location it resolved from, when there is one. |
| `src/contrib/events.ts` | The plugin-facing gateway event tap. The wiring fans every inbound gateway event through here BEFORE its own dispatch; plugins subscribe by type (or `'*'`) via `host.onEvent`. Listeners are isolated — a throwing plugin… |
| `src/contrib/index.ts` | TypeScript source: `index` |
| `src/contrib/kanban-card-badges.test.ts` | The Kanban card-badge contract (#140026): plugins contribute small text badges per card through `KANBAN_CARD_AREAS.badges`; the host validates, orders, caps and paints them. These drive the REAL plugin context and regis… |
| `src/contrib/kanban-card-badges.tsx` | Kanban card badges — small text labels a plugin puts on Kanban card tiles (a tenant, a CI state, an estimate) without touching the board's markup. data kind (`data`): kanban.card.badges (KanbanCardBadgeContribution) The… |
| `src/contrib/kanban-i18n.test.tsx` | Keep the real registration and UI path without opening a board socket. |
| `src/contrib/plugin-files.test.ts` | Tests: ctx.files; always names the calling plugin and asks with the app; tells the user when the app refuses the folder they picked; answers unavailable on a shell without the door instead of throwing |
| `src/contrib/plugin-files.ts` | `ctx.files` — the folder-scoped file door. A plugin reads and writes inside its own data folder (`'data'`) and inside folders the user granted it through the app's picker, by RELATIVE path. Electron's main process owns… |
| `src/contrib/plugin-pet.test.tsx` | The in-window pet's gateway/theme plumbing is unrelated to the bubble; the sprite is a canvas jsdom can't paint, so stand it in with the same a11y label the real one carries. |
| `src/contrib/plugin-preview.test.ts` | Tests: ctx.preview.executeJavaScript; refuses a plugin that did not declare the capability, without asking or running; asks once naming the plugin and origin; Allow runs the script and persists the grant; Don |
| `src/contrib/plugin-preview.ts` | `ctx.preview` — a plugin's door into the preview Browser's guest page. The guest is reached through the same script runner drive_preview and the preview tour use (`activePreviewScriptRunner`), never a scraped `<webview>… |
| `src/contrib/plugin-run-action.test.ts` | Tests: ctx.runAction — plugins run built-in app actions; runs the same handler the keyboard shortcut runs; is unaffected by rebinding or unbinding the shortcut; refuses actions outside the allowlist without running them |
| `src/contrib/plugin.test.ts` | Tests: createPluginContext.onDispose; collects arbitrary cleanups so the host runs them on deactivate; createPluginContext.onEvent; retires the gateway listener with the plugin, even when subscribed after register() |
| `src/contrib/plugin.ts` | The plugin authoring contract. A plugin is a file that default-exports a `HermesPlugin`; it never touches the registry directly — it receives a scoped `PluginContext` whose `register` auto-tags provenance (`source: 'plu… |
| `src/contrib/plugins-store.ts` | PLUGIN INVENTORY — the reactive record of every desktop plugin the app knows about (bundled `src/plugins/*`, the in-repo runtime example, the `<hermes home>/desktop-plugins/*` disk door — incl. agent-written ones), plus… |
| `src/contrib/plugins.ts` | Plugin discovery — both delivery modes: - BUNDLED: every `src/plugins/<name>/plugin.{js,ts,tsx}` default-exporting a `HermesPlugin` registers automatically (vite glob — drop a folder in). `hermes-bots` (Bot Mode) ships… |
| `src/contrib/radio-artist-links.test.ts` | Tests: Radio artist credits; separates only a credited artist and accepts direct artist destinations, never track or search links; resolves exact artist profiles, rejects ambiguity, and falls back after an unavailable p… |
| `src/contrib/radio-plugin.test.ts` | Tests: bundled Radio plugin; inventories off by default and follows the ordinary live enable/disable lifecycle without autoplay; releases the stream on disable and ignores late media events from the old player; survives… |
| `src/contrib/react/boundary.tsx` | Exports `ContribRender`, `ContribBoundary` |
| `src/contrib/react/contribute.tsx` | Mount-scoped contribution — the "reverse portal" companion to `Slot`. `ctx.register` is for PERMANENT contributions (registered at plugin load, alive for the plugin's lifetime). `<Contribute>` is for chrome that belongs… |
| `src/contrib/react/slot.test.tsx` | Tests: Slot contribution render boundary; hot-mounts and replaces hook-using plugin renders without changing the host hook order; lets the contribution boundary contain a render-time plugin failure |
| `src/contrib/react/slot.tsx` | Exports `SlotProps`, `Slot` |
| `src/contrib/react/use-contributions.ts` | Subscribe to the resolved contributions for an area. The subscription is scoped to `area`, so a slot re-renders only when ITS area mutates — a statusbar registration never re-renders a titlebar (or panes) slot. |
| `src/contrib/registry.test.ts` | Registrations are global (module-level registry); each test captures its own disposer and this undoes it, so tests don't bleed into each other. |
| `src/contrib/registry.ts` | Bumped on every registry mutation — the reactive hook for non-React consumers (nanostores `computed`s, memo deps) that read `registry.getArea` imperatively. React trees should keep using `useContributions`. |
| `src/contrib/runtime-loader.test.ts` | Tests: scanDiskPlugins (#66899); scans the Electron-resolved local roots, never the backend hermes_home; no-ops when the resolvers yield no local root; treats a folder without plugin.js as metadata, not a throwing file… |
| `src/contrib/runtime-loader.ts` | Runtime plugin loader — plugins as CODE, not registry edits, loaded after build time. The pipeline every non-bundled plugin takes: source (plain ESM js) -> import allowlist (` |
| `src/contrib/settings-pages.test.ts` | Tests: ctx.registerSettingsPage; lands in the Settings ▸ Plugins area scoped to the registering plugin, and leaves with it; pluginSettingsEntries; lists registered pages by order then title, dropping malformed ones |
| `src/contrib/settings-pages.ts` | Settings ▸ Plugins — one home for every plugin's preferences, WoW-AddOns style: each plugin gets an entry in the Settings rail, optionally with its own sub-pages beneath it. Two feeds produce entries: - Desktop plugins… |
| `src/contrib/types.ts` | Where a contribution came from. `'core'` is the app's own default UI; anything else is a plugin/extension id (e.g. `'plugin:kanban'`). This is the provenance tag that drives precedence and, later, the trust/capability g… |
| `src/debug/README.md` | Dev-only state diagnostics |
| `src/debug/atom-churn.ts` | Dev-only nanostores churn counter — the state-side companion to `render-counter.ts`. Render counts tell you WHAT re-rendered; this tells you WHICH ATOM pushed the update, and whether the push was worth making. |
| `src/debug/dev-only.noop.ts` | Production stand-in for `dev-only.ts`. `vite.config.ts` aliases the dev entry to this module for any build that isn't the dev server, so the diagnostics graph — and bippy with it — never reaches a shipped renderer. |
| `src/debug/dev-only.ts` | Dev-only diagnostics entry. Statically imported from `main.tsx` ABOVE the `react-dom` import — that ordering is load-bearing and non-negotiable. react-dom captures the devtools hook at MODULE INIT, not at `createRoot`. |
| `src/debug/index.ts` | Dev-only state diagnostics: one import, two counters. window.__RENDER_COUNTS__ — what re-rendered, and why (props/state/parent) window.__ATOM_CHURN__ — which store published it, and whether it mattered |
| `src/debug/perf-live.ts` | Live interaction profiler — for driving the app by hand and seeing what the app actually does under YOUR sessions, not a synthetic scenario's. The synthetic scenarios seed toy transcripts (short prose, no tool calls, no |
| `src/debug/render-counter.ts` | Dev-only render counter — answers "what actually re-rendered, and why?". Loaded from `main.tsx` BEFORE `react-dom` (see the import-order note there). That ordering is load-bearing: react-dom decides at module-init wheth… |
| `src/debug/right-pane-events.ts` | Exports `RightPanePerfEvent`, `RightPanePerfSnapshot`, `markRightPanePerf` |
| `src/debug/right-pane-probe.ts` | TypeScript source: `right-pane-probe` |
| `src/debug/watched-atoms.ts` | Dev-only: registers the stores worth attributing during a streaming turn. Deliberately NOT every atom in the app — a churn counter that reports 200 rows is as useless as none. These are the stores on or adjacent to the |
| `src/entry.test.ts` | Tests: catches a failed app import at the renderer entry and shows recovery |
| `src/entry.ts` | Renderer entry. The whole app (every store that reads localStorage when its module evaluates) enters through the dynamic import below, so nothing can read a shared preference before this machine's store hydrated it (#14… |
| `src/fonts/JetBrainsMono-Bold.woff2` | Web font |
| `src/fonts/JetBrainsMono-Italic.woff2` | Web font |
| `src/fonts/JetBrainsMono-Regular.woff2` | Web font |
| `src/global.d.ts` | Exports `DesktopMachineProfile`, `HermesPluginFolderGrant`, `HermesPluginFilesResult`, `DesktopMarketplaceSearchItem`, `DesktopMarketplaceThemeFile`, `DesktopMarketplaceThemeResult` … |
| `src/hermes-capability-scope.test.ts` | Tests: capability helpers are connection-scoped; omits both scopes when none are active (single-source users unaffected); carries the ambient registry connection on the legacy string/ambient path; string scopes override… |
| `src/hermes-cron-scope.test.ts` | Tests: cron helpers are profile-scoped; omits profile when none is active (single-profile users unaffected); forwards the active profile to every cron helper; omits connectionId when the local pool serves the active gat… |
| `src/hermes-parity.test.ts` | Tests: Hermes REST parity helpers (hub / mcp / maintenance); encodes hub search params; tests an MCP server with an encoded name; reads a backend model catalog scoped to a provider row |
| `src/hermes-profile-scope.test.ts` | Tests: backend action helpers are profile-scoped; omits profile when none is active (single-profile users unaffected); forwards the active profile to memory provider config calls; forwards the active profile to every ba… |
| `src/hermes.test.ts` | Tests: Hermes REST helpers; batches the sidebar slices into a single request with per-slice limits + excludes; routes session, profile, and model reads through the active registry source; keeps an explicit This device s… |
| `src/hermes.ts` | The desktop REST/WS client, split by domain under src/api/. This module is the compatibility barrel: every helper keeps its historical `@/hermes` import path while the implementations live in focused files. |
| `src/hooks/use-delayed-true.ts` | Returns true only after `active` has stayed true continuously for `delayMs`. Flips back to false the instant `active` goes false. Use it to gate loading skeletons so a fast operation doesn't flash one — the UI just stay… |
| `src/hooks/use-grab-scroll.ts` | Grab-to-pan for overflow containers — the shared primitive behind "scrub the board/timeline by dragging its background" (kanban lanes, trace waterfalls, wide tables). Sibling of lib/trackpad-gestures.ts: that file class… |
| `src/hooks/use-image-download.ts` | Exports `useImageDownload` |
| `src/hooks/use-media-image.frames.test.tsx` | Regression for #74564 (aperture half): the old preview clamp (--image-preview-height: clamp(16.25rem, …, 26.25rem), max-width 34rem) meant the reserved frame for a landscape image could never span the |
| `src/hooks/use-media-image.test.tsx` | useMediaImage's gateway-proxy retry (#74564): a direct inline https image that fails to load (client blocked from the CDN) is fetched once through the gateway's authenticated /api/media/proxy and swapped in as a data UR… |
| `src/hooks/use-media-image.ts` | Exports `useMediaImage` |
| `src/hooks/use-media-playback-src.expiry.test.tsx` | Tests: a video whose ticket expired before its first play gets a fresh ticket and plays; a fresh source that also fails before loading is a real failure; a paused video gets its fresh ticket without being started; a sou… |
| `src/hooks/use-media-playback-src.owner.test.tsx` | Tests for `use-media-playback-src.owner` |
| `src/hooks/use-media-playback-src.ts` | Exports `useMediaPlaybackSrc` |
| `src/hooks/use-media-query.ts` | Exports `matchesQuery`, `prefersReducedMotion`, `useMediaQuery` |
| `src/hooks/use-mobile.ts` | Narrower than this and the sidebar stops being a docked column: it renders as a floating Sheet over the content instead (components/ui/sidebar.tsx). Anything that sizes a window around a docked sidebar has to clear it. |
| `src/hooks/use-resize-observer.ts` | Observe element resizes. The callback receives the ResizeObserver entries (empty only in non-RO environments) so callers can read the observed size off the entry instead of forcing a fresh layout read. The initial measu… |
| `src/hooks/use-seen-once.ts` | Latches true the first time `ref`'s element intersects the viewport (through every clipping scroll ancestor), and stays true. Expensive work that only matters once seen (syntax highlighting) waits on it, so mounting a l… |
| `src/hooks/use-theme-epoch.ts` | Theme repaints (themes/context.tsx) toggle `.dark` + rewrite inline custom props/data-hermes-* on <html>. Canvas/probe consumers that rasterize the *computed* color-mix()/oklch tokens must re-resolve AFTER the paint — u… |
| `src/hooks/use-viewed-interval.ts` | Run a UI-only clock while this document is actually being viewed. macOS can leave an occluded BrowserWindow `visible`, and active streaming deliberately disables Chromium's background timer throttling. Pairing focus wit… |
| `src/hover-variant.test.ts` | @vitest-environment node |
| `src/i18n/ar.ts` | Exports `arOverrides`, `ar` |
| `src/i18n/ar_artifacts.ts` | Exports `arArtifacts` |
| `src/i18n/ar_assistant.ts` | Exports `arAssistant` |
| `src/i18n/ar_boot.ts` | Exports `arBoot` |
| `src/i18n/ar_capabilities.ts` | Exports `arCapabilities` |
| `src/i18n/ar_chat.ts` | Exports `arChat` |
| `src/i18n/ar_chrome.ts` | Exports `arChrome` |
| `src/i18n/ar_command_center.ts` | Exports `arCommandCenter` |
| `src/i18n/ar_common.ts` | Exports `arCommon` |
| `src/i18n/ar_connectors.ts` | Exports `arConnectors` |
| `src/i18n/ar_delegation_routing.ts` | Exports `arDelegationRouting` |
| `src/i18n/ar_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/ar_diagnostics.ts` | Exports `arDiagnostics` |
| `src/i18n/ar_first_run.ts` | Exports `arFirstRun` |
| `src/i18n/ar_memory_layers.ts` | Exports `arMemoryLayers` |
| `src/i18n/ar_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/ar_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/ar_settings.ts` | Exports `arSettings` |
| `src/i18n/ar_theme_picker.ts` | Exports `arThemePicker` |
| `src/i18n/ar_update_channel.ts` | Exports `arUpdateChannel` |
| `src/i18n/backend-packs.test.ts` | Tests: syncBackendLocalePacks; registers the backend language list and the desktop pack for the requested language; accepts a bare array from i18n.languages and skips the catalog call without a requested language; is si… |
| `src/i18n/backend-packs.ts` | Backend-delivered language packs. A Hermes language-pack plugin (or a user overlay under `$HERMES_HOME/locales/`) ships `<lang>.desktop.yaml`; the gateway serves the flattened strings over `i18n.catalog {lang, surface:… |
| `src/i18n/bots-advanced.test.tsx` | Tests: localizes the advanced editor and hub without translating capability IDs or user data; localizes MCP setup actions while retaining the profile, preset and environment identifiers |
| `src/i18n/bots-cron.test.tsx` | Tests: switches scheduling copy without changing a staged schedule or user instruction; localizes inspector chrome and known states while preserving job data and unknown status |
| `src/i18n/bots-editor.test.tsx` | Tests: keeps a new bot draft when the language changes and localizes advanced controls; localizes Edit Profile and image controls without losing user content |
| `src/i18n/canonical-group-labels.test.ts` | Tests: provides translated canonical group controls and recovery copy in every supported locale |
| `src/i18n/catalog-completeness.test.ts` | Locales that shipped fully translated. They are `defineLocale` overlays like ja/ru, so an English key added later falls back to English instead of failing typecheck; these checks keep the translated copy structurally so… |
| `src/i18n/catalog.ts` | The catalogs compiled into the app. Runtime-registered languages (plugin packs, backend `.desktop.yaml` packs) are NOT here — resolve through `resolveTranslations()` in `./registry`, which layers them over these. |
| `src/i18n/context.test.tsx` | Tests: I18nProvider; defaults to English without a config client; normalizes an initial locale alias and switches translations; loads the initial locale from display.language config |
| `src/i18n/context.tsx` | Exports `I18nConfigClient`, `getConfigDisplayLanguage`, `withConfigDisplayLanguage`, `I18nContextValue`, `I18nProviderProps`, `I18nProvider` … |
| `src/i18n/de.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/de_aux_tasks.ts` | Exports `deAuxTasks` |
| `src/i18n/de_boot.ts` | The boot screen's copy (including the update-hold screen), composed by de.ts. |
| `src/i18n/de_clarify.ts` | Exports `deClarify` |
| `src/i18n/de_connector_accounts.ts` | Exports `deConnectorAccounts` |
| `src/i18n/de_connector_card.ts` | Exports `deConnectorCard` |
| `src/i18n/de_delegation_routing.ts` | Exports `deDelegationRouting` |
| `src/i18n/de_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/de_error_codes.ts` | Exports `deErrorCodes` |
| `src/i18n/de_error_layers.ts` | Exports `deErrorLayers` |
| `src/i18n/de_first_run.ts` | Exports `deFirstRun` |
| `src/i18n/de_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into de.ts. |
| `src/i18n/de_local_models.ts` | Exports `deLocalModels` |
| `src/i18n/de_memory_layers.ts` | Exports `deMemoryLayers` |
| `src/i18n/de_model_menu.ts` | Exports `deModelMenu` |
| `src/i18n/de_model_settings.ts` | Exports `deModelSettings` |
| `src/i18n/de_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into de.ts. |
| `src/i18n/de_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/de_onboarding.ts` | Exports `deOnboarding` |
| `src/i18n/de_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/de_plugin_update.ts` | Copy for updating an installed plugin (Plugins tab): catalog re-pin consent and the security-scan override. |
| `src/i18n/de_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by de.ts. |
| `src/i18n/de_projects.ts` | Die Projekt-Sektion der Sidebar, zusammengesetzt von de.ts. |
| `src/i18n/de_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/de_shared_metrics.ts` | Exports `deSharedMetrics` |
| `src/i18n/de_theme_picker.ts` | Exports `deThemePicker` |
| `src/i18n/de_update_channel.ts` | Exports `deUpdateChannel` |
| `src/i18n/define-locale.ts` | Exports `TranslationOverrides`, `defineLocale` |
| `src/i18n/en.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/en_app_tour.ts` | Exports `enAppTour` |
| `src/i18n/en_aux_tasks.ts` | Exports `enAuxTasks` |
| `src/i18n/en_billing.ts` | Out-of-credits overlay copy (Nous vs. third-party providers), spread into en.ts. |
| `src/i18n/en_boot.ts` | The boot screen's copy (including the update-hold screen), composed by en.ts. |
| `src/i18n/en_catalog.ts` | Exports `enCatalog` |
| `src/i18n/en_catalog_install.ts` | Exports `enCatalogInstall` |
| `src/i18n/en_clarify.ts` | Exports `enClarify` |
| `src/i18n/en_connector_accounts.ts` | Exports `enConnectorAccounts` |
| `src/i18n/en_connector_card.ts` | Exports `enConnectorCard` |
| `src/i18n/en_deep_links.ts` | Exports `enSkillDeepLink`, `enGatewayGroupOpen` |
| `src/i18n/en_delegation_routing.ts` | Exports `enDelegationRouting` |
| `src/i18n/en_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines. |
| `src/i18n/en_error_codes.ts` | Exports `enErrorCodes` |
| `src/i18n/en_error_layers.ts` | Exports `enErrorLayers` |
| `src/i18n/en_external_open.ts` | Exports `enExternalOpenFailed` |
| `src/i18n/en_first_run.ts` | Exports `enFirstRun` |
| `src/i18n/en_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into en.ts. |
| `src/i18n/en_local_models.ts` | Exports `enLocalModels` |
| `src/i18n/en_memory_layers.ts` | Settings > Memory & Context and Command Center > Maintenance (#145175). |
| `src/i18n/en_model_menu.ts` | Exports `enModelMenu` |
| `src/i18n/en_model_settings.ts` | Exports `enModelSettings` |
| `src/i18n/en_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into en.ts. |
| `src/i18n/en_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/en_onboarding.ts` | Exports `enOnboarding` |
| `src/i18n/en_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/en_plugin_update.ts` | Copy for updating an installed plugin (Plugins tab): catalog re-pin consent and the security-scan override. |
| `src/i18n/en_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by en.ts. |
| `src/i18n/en_projects.ts` | The sidebar's projects-section copy, composed by en.ts. |
| `src/i18n/en_session_commands.ts` | Typed /undo /retry /steer /queue lines: the Ink TUI's wording on the same gateway. |
| `src/i18n/en_shared_metrics.ts` | Exports `enSharedMetrics` |
| `src/i18n/en_theme_picker.ts` | Exports `enThemePicker` |
| `src/i18n/en_uninstall_section.ts` | Settings > About > Uninstall, composed by en.ts as `settings.uninstallSection`. |
| `src/i18n/en_update_channel.ts` | Exports `enUpdateChannel` |
| `src/i18n/es.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/es_aux_tasks.ts` | Exports `esAuxTasks` |
| `src/i18n/es_boot.ts` | The boot screen's copy (including the update-hold screen), composed by es.ts. |
| `src/i18n/es_clarify.ts` | Exports `esClarify` |
| `src/i18n/es_connector_accounts.ts` | Exports `esConnectorAccounts` |
| `src/i18n/es_connector_card.ts` | Exports `esConnectorCard` |
| `src/i18n/es_delegation_routing.ts` | Exports `esDelegationRouting` |
| `src/i18n/es_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/es_error_codes.ts` | Exports `esErrorCodes` |
| `src/i18n/es_error_layers.ts` | Exports `esErrorLayers` |
| `src/i18n/es_first_run.ts` | Exports `esFirstRun` |
| `src/i18n/es_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into es.ts. |
| `src/i18n/es_local_models.ts` | Exports `esLocalModels` |
| `src/i18n/es_memory_layers.ts` | Exports `esMemoryLayers` |
| `src/i18n/es_model_menu.ts` | Exports `esModelMenu` |
| `src/i18n/es_model_settings.ts` | Exports `esModelSettings` |
| `src/i18n/es_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into es.ts. |
| `src/i18n/es_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/es_onboarding.ts` | Exports `esOnboarding` |
| `src/i18n/es_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/es_plugin_update.ts` | Copy for updating an installed plugin (Plugins tab): catalog re-pin consent and the security-scan override. |
| `src/i18n/es_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by es.ts. |
| `src/i18n/es_projects.ts` | La sección de proyectos de la barra lateral, compuesta por es.ts. |
| `src/i18n/es_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/es_shared_metrics.ts` | Exports `esSharedMetrics` |
| `src/i18n/es_theme_picker.ts` | Exports `esThemePicker` |
| `src/i18n/es_update_channel.ts` | Exports `esUpdateChannel` |
| `src/i18n/fr.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/fr_aux_tasks.ts` | Exports `frAuxTasks` |
| `src/i18n/fr_boot.ts` | The boot screen's copy (including the update-hold screen), composed by fr.ts. |
| `src/i18n/fr_clarify.ts` | Exports `frClarify` |
| `src/i18n/fr_connector_accounts.ts` | Exports `frConnectorAccounts` |
| `src/i18n/fr_connector_card.ts` | Exports `frConnectorCard` |
| `src/i18n/fr_delegation_routing.ts` | Exports `frDelegationRouting` |
| `src/i18n/fr_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/fr_error_codes.ts` | Exports `frErrorCodes` |
| `src/i18n/fr_error_layers.ts` | Exports `frErrorLayers` |
| `src/i18n/fr_first_run.ts` | Exports `frFirstRun` |
| `src/i18n/fr_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into fr.ts. |
| `src/i18n/fr_local_models.ts` | Exports `frLocalModels` |
| `src/i18n/fr_memory_layers.ts` | Exports `frMemoryLayers` |
| `src/i18n/fr_model_menu.ts` | Exports `frModelMenu` |
| `src/i18n/fr_model_settings.ts` | Exports `frModelSettings` |
| `src/i18n/fr_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into fr.ts. |
| `src/i18n/fr_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/fr_onboarding.ts` | Exports `frOnboarding` |
| `src/i18n/fr_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/fr_plugin_update.ts` | Copy for updating an installed plugin (Plugins tab): catalog re-pin consent and the security-scan override. |
| `src/i18n/fr_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by fr.ts. |
| `src/i18n/fr_projects.ts` | La section projets de la barre latérale, composée par fr.ts. |
| `src/i18n/fr_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/fr_shared_metrics.ts` | Exports `frSharedMetrics` |
| `src/i18n/fr_theme_picker.ts` | Exports `frThemePicker` |
| `src/i18n/fr_update_channel.ts` | Exports `frUpdateChannel` |
| `src/i18n/index.ts` | TypeScript source: `index` |
| `src/i18n/intro-de.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/intro-es.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/intro-fr.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/intro-ja.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/intro-zh-hant.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/intro-zh.ts` | Display-only translations, in the stock JSONL's per-personality rotation order. |
| `src/i18n/ja.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/ja_aux_tasks.ts` | Exports `jaAuxTasks` |
| `src/i18n/ja_boot.ts` | The boot screen's copy, composed by ja.ts. |
| `src/i18n/ja_catalog.ts` | Exports `jaCatalog`, `jaSkillDeepLink` |
| `src/i18n/ja_clarify.ts` | Exports `jaClarify` |
| `src/i18n/ja_connectors.ts` | Exports `jaConnectors` |
| `src/i18n/ja_delegation_routing.ts` | Exports `jaDelegationRouting` |
| `src/i18n/ja_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/ja_error_codes.ts` | Exports `jaErrorCodes` |
| `src/i18n/ja_error_layers.ts` | Exports `jaErrorLayers` |
| `src/i18n/ja_first_run.ts` | Exports `jaFirstRun` |
| `src/i18n/ja_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into ja.ts. |
| `src/i18n/ja_local_models.ts` | Exports `jaLocalModels` |
| `src/i18n/ja_memory_layers.ts` | Exports `jaMemoryLayers` |
| `src/i18n/ja_model_menu.ts` | Exports `jaModelMenu` |
| `src/i18n/ja_model_settings.ts` | Exports `jaModelSettings` |
| `src/i18n/ja_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into ja.ts. |
| `src/i18n/ja_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/ja_onboarding.ts` | Exports `jaOnboarding` |
| `src/i18n/ja_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/ja_plugins.ts` | Exports `jaPluginSettings`, `jaPluginsTab` |
| `src/i18n/ja_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by ja.ts. |
| `src/i18n/ja_projects.ts` | サイドバーのプロジェクトセクションのコピー。ja.ts が参照します。 |
| `src/i18n/ja_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/ja_shared_metrics.ts` | Exports `jaSharedMetrics` |
| `src/i18n/ja_theme_picker.ts` | Exports `jaThemePicker` |
| `src/i18n/ja_update_channel.ts` | Exports `jaUpdateChannel` |
| `src/i18n/languages.test.ts` | Tests: desktop i18n languages; normalizes supported locale aliases; falls back to English for empty or unsupported values; distinguishes exact locale ids from supported config aliases |
| `src/i18n/languages.ts` | Exports `DEFAULT_LOCALE`, `LOCALE_OPTIONS`, `LanguageOption`, `localeMeta`, `isRtlLocale`, `languageOptions` … |
| `src/i18n/localized-tab-title.tsx` | Render-time pane TAB label for panes registered outside React. A contribution's `title` is a plain string sampled once, at `register`. Bundled panes (the Sessions sidebar, Bot Mode's roster) register during module impor… |
| `src/i18n/overlay-completeness.test.ts` | Overlays are partial, so a missing key renders English without failing typecheck or catalog-completeness.test.ts (which reads the merged catalog). This reads each locale's own overlay. overlay-gaps.json maps each Englis… |
| `src/i18n/overlay-gaps.json` | JSON data/configuration |
| `src/i18n/plugin-i18n.test.tsx` | Tests: plugin locale registry; resolves the active locale, falling back to English then the raw key; scopes bundles per plugin — no cross-read; merges repeated registrations and drops everything on dispose |
| `src/i18n/plugin-i18n.ts` | Plugin-scoped i18n — the `ctx.storage` analog for locale bundles. A plugin ships its own strings and registers them under its id; it never edits core `en.ts`. Resolution mirrors the app translator: active locale → the p… |
| `src/i18n/profile-locale.test.tsx` | Tests: reads and persists the owning profile through A → B → A and restart; isolates stale reads and failed saves when the same profile moves between connections |
| `src/i18n/profile-provider.tsx` | Keep gateway/store imports outside the shared i18n context's import graph. |
| `src/i18n/registry.test.ts` | Tests: registerAppLocale; layers a partial pack over English for a new language and falls back per key; wraps a pack string over a function-valued English entry into a positional formatter; keeps dotted leaf keys (keybi… |
| `src/i18n/registry.ts` | App-locale registry — the runtime half of the desktop catalog. `TRANSLATIONS` is what ships in the binary; this registry layers languages that arrive later: a plugin's `host.i18n.registerAppLocale` / `ctx.i18n.registerA… |
| `src/i18n/ru.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/ru_aux_tasks.ts` | Exports `ruAuxTasks` |
| `src/i18n/ru_boot.ts` | The boot screen's copy, composed by ru.ts. |
| `src/i18n/ru_catalog.ts` | Exports `ruCatalog`, `ruSkillDeepLink` |
| `src/i18n/ru_clarify.ts` | Exports `ruClarify` |
| `src/i18n/ru_connectors.ts` | Exports `ruConnectors` |
| `src/i18n/ru_delegation_routing.ts` | Exports `ruDelegationRouting` |
| `src/i18n/ru_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/ru_error_codes.ts` | Exports `ruErrorCodes` |
| `src/i18n/ru_first_run.ts` | Exports `ruFirstRun` |
| `src/i18n/ru_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into ru.ts. |
| `src/i18n/ru_memory_layers.ts` | Exports `ruMemoryLayers` |
| `src/i18n/ru_model_menu.ts` | Exports `ruModelMenu` |
| `src/i18n/ru_model_settings.ts` | Exports `ruModelSettings` |
| `src/i18n/ru_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into ru.ts. |
| `src/i18n/ru_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/ru_onboarding.ts` | Exports `ruOnboarding` |
| `src/i18n/ru_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/ru_plugins.ts` | Exports `ruPluginSettings`, `ruPluginsTab` |
| `src/i18n/ru_plural.ts` | Shared by ru.ts and its sibling overlays. RU_PLURAL: (count, one, few, many) — русские формы сущ. падежа RU_NOUN: (count, one, few, many) — формы род. множественного |
| `src/i18n/ru_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by ru.ts. |
| `src/i18n/ru_projects.ts` | Тексты секции проектов в боковой панели; подключается из ru.ts. |
| `src/i18n/ru_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/ru_shared_metrics.ts` | Exports `ruSharedMetrics` |
| `src/i18n/ru_theme_picker.ts` | Exports `ruThemePicker` |
| `src/i18n/ru_update_channel.ts` | Exports `ruUpdateChannel` |
| `src/i18n/runtime.test.ts` | Tests: desktop i18n runtime translator; translates string paths for the active runtime locale; passes arguments to function translations; keeps translated settings field copy addressable from schema keys |
| `src/i18n/runtime.ts` | Exports `translateFrom`, `setRuntimeI18nLocale`, `subscribeRuntimeI18nLocale`, `getRuntimeI18nLocale`, `runtimeTranslations`, `translateNow` |
| `src/i18n/types.ts` | health: allow FILE_LINES -- the copy contract for the usage-window plan keys every locale adds (allowance gauges, Large/Free tags, the limit card) Desktop i18n type contract. `Translations` is the single source of truth… |
| `src/i18n/types_app_tour.ts` | Exports `AppTourTranslations` |
| `src/i18n/types_aux_tasks.ts` | Copy for one built-in auxiliary-model slot row (Settings → Models → Auxiliary models). |
| `src/i18n/types_billing.ts` | Out-of-credits overlay copy; `Translations` spreads this in. |
| `src/i18n/types_boot.ts` | The boot screen's string surface (including the update-hold screen); `Translations.boot`. |
| `src/i18n/types_catalog.ts` | Exports `CatalogTranslations` |
| `src/i18n/types_catalog_install.ts` | Copy for the desktop catalog-install card (`manage_catalog`) and its Advanced dialog. |
| `src/i18n/types_clarify.ts` | The clarify question card. |
| `src/i18n/types_connectors.ts` | Exports `ConnectorCardTranslations`, `ConnectorDirectoryTranslations`, `ConnectorAccountsTranslations` |
| `src/i18n/types_deep_links.ts` | Opening a skill install link. |
| `src/i18n/types_delegation_routing.ts` | Exports `DelegationRoutingTranslations` |
| `src/i18n/types_desktop_commands.ts` | Transcript lines for the Desktop-side /rollback /agents /config /history /save /export /import /timestamps actions (slash-desktop-commands.ts). Counts arrive as strings, like sessionCommands. |
| `src/i18n/types_external_open.ts` | Exports `ExternalOpenFailedCopy` |
| `src/i18n/types_first_run.ts` | First-run onboarding: the setup_beat cards and their receipts, Skip setup, the local-model offer at the end, and the Settings row that runs it again. |
| `src/i18n/types_gateway_host.ts` | Settings → Gateways copy for a renderer that cannot change its connection: a Desktop whose bridge exposes no gateway settings, and the Webapp, bound to the host that serves it. Plus Settings → Web Access, which turns on… |
| `src/i18n/types_memory_layers.ts` | Settings > Memory & Context and Command Center > Maintenance: the active (saved) memory provider, a selected-but-unsaved one, and the built-in MEMORY.md / USER.md layer; `Translations.settings.memoryLayers`. |
| `src/i18n/types_model_menu.ts` | Exports `ModelMenuTranslations` |
| `src/i18n/types_model_settings.ts` | Settings → Model; `Translations.settings.model`. |
| `src/i18n/types_notices.ts` | Shell notice strings: the remote-display toast, the butterbar, send-outcome toasts and the keep-awake offer; `Translations` spreads this in. |
| `src/i18n/types_notifications.ts` | Notification settings types used by every desktop locale. |
| `src/i18n/types_onboarding.ts` | Exports `OnboardingTranslations` |
| `src/i18n/types_plugin_preview_access.ts` | Copy for the `ctx.preview.executeJavaScript` consent: the app-owned prompt a plugin's first call on a page origin raises, and the per-plugin grant list in Capabilities ▸ Plugins. |
| `src/i18n/types_plugin_update.ts` | Plugins tab copy for the folders a plugin may use (`ctx.files`): the app's picker, the per-plugin grant list and its Revoke action. |
| `src/i18n/types_projects.ts` | The sidebar projects section's copy shape; `Translations.sidebar.projects`. |
| `src/i18n/types_right_sidebar.ts` | The right sidebar's copy (file tree, folder picker, terminals); `Translations.rightSidebar`. |
| `src/i18n/types_shared_metrics.ts` | Exports `SharedMetricsTranslations` |
| `src/i18n/types_theme_picker.ts` | The set_theme picker cards in the chat and their settled receipt. |
| `src/i18n/types_uninstall_section.ts` | Settings > About > Uninstall; `Translations.settings.uninstallSection`. |
| `src/i18n/types_update_channel.ts` | About ▸ Updates: the source checkout's update channel selector. |
| `src/i18n/zh-hant.ts` | Exports `zhHantOverrides`, `zhHant` |
| `src/i18n/zh-hant_artifacts.ts` | Exports `zhHantArtifacts` |
| `src/i18n/zh-hant_assistant.ts` | Exports `zhHantAssistant` |
| `src/i18n/zh-hant_boot.ts` | Exports `zhHantBoot` |
| `src/i18n/zh-hant_capabilities.ts` | Exports `zhHantCapabilities` |
| `src/i18n/zh-hant_chat.ts` | Exports `zhHantChat` |
| `src/i18n/zh-hant_chrome.ts` | Exports `zhHantChrome` |
| `src/i18n/zh-hant_command_center.ts` | Exports `zhHantCommandCenter` |
| `src/i18n/zh-hant_common.ts` | Exports `zhHantCommon` |
| `src/i18n/zh-hant_connectors.ts` | Exports `zhHantConnectors` |
| `src/i18n/zh-hant_delegation_routing.ts` | Exports `zhHantDelegationRouting` |
| `src/i18n/zh-hant_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/zh-hant_diagnostics.ts` | Exports `zhHantDiagnostics` |
| `src/i18n/zh-hant_first_run.ts` | Exports `zhHantFirstRun` |
| `src/i18n/zh-hant_memory_layers.ts` | Exports `zhHantMemoryLayers` |
| `src/i18n/zh-hant_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/zh-hant_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/zh-hant_settings.ts` | Exports `zhHantSettings` |
| `src/i18n/zh-hant_theme_picker.ts` | Exports `zhHantThemePicker` |
| `src/i18n/zh-hant_update_channel.ts` | Exports `zhHantUpdateChannel` |
| `src/i18n/zh.ts` | health: allow FILE_LINES -- locale data: translated copy for the usage-window plan UI (allowance gauges, Large/Free tags, the limit card), one key per string |
| `src/i18n/zh_aux_tasks.ts` | Exports `zhAuxTasks` |
| `src/i18n/zh_catalog.ts` | Exports `zhCatalog`, `zhSkillDeepLink` |
| `src/i18n/zh_clarify.ts` | Exports `zhClarify` |
| `src/i18n/zh_connector_card.ts` | Exports `zhConnectorCard` |
| `src/i18n/zh_delegation_routing.ts` | Exports `zhDelegationRouting` |
| `src/i18n/zh_desktop_commands.ts` | Desktop-side /rollback /agents /config /history /save /export /import /timestamps lines (en_desktop_commands.ts is the source). |
| `src/i18n/zh_error_codes.ts` | Exports `zhErrorCodes` |
| `src/i18n/zh_error_layers.ts` | Exports `zhErrorLayers` |
| `src/i18n/zh_first_run.ts` | Exports `zhFirstRun` |
| `src/i18n/zh_gateway_host.ts` | Settings → Gateways copy where the connection cannot change, spread into zh.ts. |
| `src/i18n/zh_local_models.ts` | Exports `zhLocalModels` |
| `src/i18n/zh_memory_layers.ts` | Exports `zhMemoryLayers` |
| `src/i18n/zh_model_menu.ts` | Exports `zhModelMenu` |
| `src/i18n/zh_model_settings.ts` | Exports `zhModelSettings` |
| `src/i18n/zh_notices.ts` | Shell notices (remote-display toast, butterbar, keep-awake offer), spread into zh.ts. |
| `src/i18n/zh_notifications.ts` | Notification settings copy used when the desktop locale loads. |
| `src/i18n/zh_onboarding.ts` | Exports `zhOnboarding` |
| `src/i18n/zh_plugin_preview_access.ts` | Copy for the preview-script consent prompt and the per-plugin grant list (Capabilities ▸ Plugins). |
| `src/i18n/zh_plugin_update.ts` | Chinese copy for the Plugins tab: updating an installed plugin and the folders it may use. |
| `src/i18n/zh_preview_web.ts` | The in-app browser pane's copy (`preview.web`), composed by zh.ts. |
| `src/i18n/zh_projects.ts` | 侧边栏项目分区的文案，由 zh.ts 组合。 |
| `src/i18n/zh_session_commands.ts` | Typed /undo /retry /steer /queue lines (en_session_commands.ts is the source). |
| `src/i18n/zh_shared_metrics.ts` | Exports `zhSharedMetrics` |
| `src/i18n/zh_theme_picker.ts` | Exports `zhThemePicker` |
| `src/i18n/zh_update_channel.ts` | Exports `zhUpdateChannel` |
| `src/lib/ansi.test.ts` | Tests: parseAnsi; returns a single default segment for plain text; returns nothing for an empty string; parses a basic foreground color sequence and resets |
| `src/lib/ansi.ts` | Minimal ANSI SGR parser for rendering terminal output inside chat tool cards. Only handles the SGR codes that show up in practice (color, bold, reset); cursor motions and other CSI sequences are dropped silently. |
| `src/lib/artifact-detect.test.ts` | Tests: detectArtifact; promotes a full html document; falls back to h1 when the document has no title tag; ignores a small html snippet |
| `src/lib/artifact-detect.ts` | Artifact detection — decides when a fenced block in an assistant message is substantial, self-contained content that deserves an artifact card (opening in the right rail) instead of an inline code block. Pure and cheap:… |
| `src/lib/async-report.test.ts` | Tests: async report hydration; keeps only result bodies beside compact system metadata across current and legacy deliveries; separates batch result blocks without leaking preambles or transcript plumbing |
| `src/lib/attachment-upload-policy.ts` | When a composer attachment must cross as BYTES rather than ride its path. Shared by the submit-time upload pipeline (`uploadComposerAttachment`) and the drop-time routing decision (`partitionDroppedFiles`) so the two ne… |
| `src/lib/audio-context.ts` | One lazily-created AudioContext for the app's synthesized UI cues (wake chime, turn-completion sound, thinking blips). Browsers cap how many contexts a page may open, and these cues are short oscillator bursts that |
| `src/lib/base64.test.ts` | Tests: bytesToBase64; encodes ArrayBuffer and Uint8Array inputs through the same path |
| `src/lib/base64.ts` | Exports `bytesToBase64`, `blobToDataUrl` |
| `src/lib/boot-failure.test.ts` | Tests: shows a rejected loader’s cause and reloads only when the user clicks Reload; uses no inline handler attributes under script-src-attr none; shows the notice in an opaque secondary window; shows a decorative wordm… |
| `src/lib/boot-failure.ts` | Exports `readBootPalette`, `showBootFailure` |
| `src/lib/brand-icon.test.ts` | Tests: resolveBrandIcon; resolves a registrable domain to a brand glyph; ignores case and a leading www.; inherits the parent brand on subdomains |
| `src/lib/brand-icon.ts` | Exports `BrandIcon`, `resolveBrandIcon` |
| `src/lib/browser-bridge-stubs.ts` | Exports `BROWSER_BRIDGE_STUBS` |
| `src/lib/browser-clipboard.ts` | Exports `createBrowserClipboardBridge` |
| `src/lib/browser-connection.ts` | Exports `requireBrowserConnection`, `createBrowserConnectionBridge` |
| `src/lib/browser-desktop-bridge-install.ts` | TypeScript source: `browser-desktop-bridge-install` |
| `src/lib/browser-desktop-bridge-ownership-download.test.ts` | Tests: keeps a captured download on its owning browser profile after a foreground switch; names a fetched cross-origin image after its URL, not the blob URL that carries it; surfaces CORS and HTTP download failures with… |
| `src/lib/browser-desktop-bridge-ownership-media.test.ts` | Tests for `browser-desktop-bridge-ownership-media` |
| `src/lib/browser-desktop-bridge-served-profiles.test.ts` | Tests: profiles the serving gateway does not serve; lists them on the roster as unreachable and routes none of them over the tab socket; reads an empty served list as a gateway that serves only the profile it runs as; k… |
| `src/lib/browser-desktop-bridge-session-owner.test.ts` | Tests: session rows a Webapp tab lists; name the serving gateway as their owner, as the tab sockets and new chats do |
| `src/lib/browser-desktop-bridge-settings.test.ts` | Tests: browser default project folder; keeps a chosen folder across reloads, per hosted gateway and profile, until cleared; rejects a choice this browser cannot keep instead of reporting it saved |
| `src/lib/browser-desktop-bridge-zoom.test.ts` | Tests: browser UI scale; reports app scale independently of display density and applies preset changes before notifying; restores app scale on reload without sharing it across hosted base paths; keeps scaling usable whe… |
| `src/lib/browser-desktop-bridge.test.ts` | Tests: browser-hosted Desktop bridge; does not make network requests to resolve link titles; refuses cloud-team reconnection without a native connection registry; does not replace the Electron preload bridge |
| `src/lib/browser-desktop-bridge.ts` | Install a capability-limited Desktop bridge when the real renderer is served directly by Hermes' authenticated web server. Electron remains authoritative everywhere it exists: no injected dashboard token means this is a… |
| `src/lib/browser-desktop-plugins.test.ts` | The server half (hermes_cli/web_routers/desktop_plugins.py) is pinned in tests/hermes_cli/test_webapp_desktop_plugins.py; this is the server's answer for one plugin. |
| `src/lib/browser-desktop-plugins.ts` | Exports `createBrowserDesktopPluginsBridge` |
| `src/lib/browser-file-urls.test.ts` | The Webapp asks its gateway for a Windows drive-letter or UNC file in the forms the gateway resolves: reads by the native path, streams by the file: URL itself. The gateway half, tests/hermes_cli/test_webapp_file_urls.p… |
| `src/lib/browser-files.ts` | Exports `createBrowserFilesBridge` |
| `src/lib/browser-guest-document.test.ts` | Tests: htmlFromDataUrl; decodes percent-encoded, base64 and charset-labelled HTML like the browser would; returns null for anything that is not a data: HTML document |
| `src/lib/browser-guest-document.ts` | The markup of a `data:text/html` URL, or null for any other src. The Webapp page CSP has no room for guest inline scripts, and a `data:` document inherits it, so the browser host re-serves this markup through the gatewa… |
| `src/lib/browser-image-download.ts` | Match the image attachment byte budget without limiting browser-managed files. |
| `src/lib/browser-launch-session.test.ts` | Tests: uses one private session for REST, RPC and terminal across reload without losing the profile; fails closed with actionable launch instructions in a fresh tab and ignores local grants under OAuth; takes the creden… |
| `src/lib/browser-launch-session.ts` | Exports `WEBAPP_LAUNCH_REQUIRED`, `webappSignInRequired`, `webappSessionKey`, `readWebappSession` |
| `src/lib/browser-profile-prefs.test.ts` | Tests: browser profile folder for a new chat; starts a chat or tile in profile B in B folder, and stays detached when B never chose one; uses the active profile folder when the new-chat pin is empty; keeps Home detached… |
| `src/lib/browser-profile-prefs.ts` | Exports `migrateBrowserProfilePrefs`, `dropBrowserProfilePrefs` |
| `src/lib/browser-profile.test.ts` | Tests: persists the default separately from the active chat and synchronizes only the same server across tabs; records a live profile pick in the URL without dropping the router entry state; opens the requested profile… |
| `src/lib/browser-profile.ts` | Exports `createBrowserProfileBridge` |
| `src/lib/browser-served-profiles.test.ts` | Tests: overlapping served set reads; re-reads for a newer installed list instead of settling it with the older read; re-reads after an invalidation during a read in flight; shares one read among callers that want the sa… |
| `src/lib/browser-served-profiles.ts` | The multiplexer applies a park, unpark or standalone change on its 30 s profile rescan, and none of those changes the installed list, so a known served set is re-read on that cadence. |
| `src/lib/browser-session-workspace-files.test.tsx` | The pane's consent dialog needs a QueryClientProvider; these tests read files, not consent. |
| `src/lib/browser-settings.ts` | Exports `browserPageBasePath`, `browserDefaultProjectDirKey`, `readBrowserDefaultProjectDir`, `migrateBrowserFolderPref`, `dropBrowserFolderPref`, `createBrowserSettings` |
| `src/lib/browser-staged-attachments.test.ts` | Tests: browser staged attachment transport; keeps the picked filename readable while retaining the exact staged source identity; keeps source ownership for multiple occurrences of the same staged path; retains the legac… |
| `src/lib/browser-startup-profile.ts` | Exports `browserStartupProfileKey`, `requireProfileRoute`, `readBrowserStartupProfile`, `migrateBrowserStartupProfile`, `dropBrowserStartupProfile` |
| `src/lib/browser-terminal.test.ts` | Tests: persistent browser terminals; consumes an empty replay frame without suppressing the first live output; reattaches the saved tab after reload to its captured profile, not the newly active one; automatically recon… |
| `src/lib/browser-terminal.ts` | Exports `createBrowserTerminal` |
| `src/lib/browser-transport.ts` | Exports `BrowserBootstrap`, `BrowserReauthRequiredError`, `browserBootstrap`, `endpointUrl`, `websocketUrl`, `navigateToBrowserLogin` … |
| `src/lib/browser-ui-preferences.ts` | Exports `createBrowserUiPreferences` |
| `src/lib/browser-uploads.test.ts` | Tests: browser image paste size; refuses an image larger than the browser can send, before uploading it; stages an image of exactly the limit; browser file stage size |
| `src/lib/browser-uploads.ts` | Exports `BROWSER_UPLOAD_MAX_BYTES`, `IMAGE_EXTENSION_BY_MIME`, `createBrowserUploadsBridge` |
| `src/lib/browser-viewport.test.ts` | Tests: browser visible viewport; fits a keyboard and its pan at UI scale, without changing focus, pinch layout, or closed-keyboard layout; leaves a focus-zoomed iOS keyboard to Safari, whose innerHeight is the visible a… |
| `src/lib/browser-viewport.ts` | Fit the browser app to the visible area when a keyboard leaves layout height unchanged. `interactive-widget=resizes-content` handles supporting browsers; VisualViewport covers the others. Pan/zoom stays with the browser… |
| `src/lib/browser-voice-sockets.test.ts` | The browser-hosted Desktop opens each voice stream with a one-use ticket minted for that stream. A socket ticket opens only the socket it names, so the gateway's ticket (named for `/api/ws`) never opens `/api/audio/spea… |
| `src/lib/browser-window.test.ts` | Tests: a window that says ready after the deadline; gated host pop-out; reports a window the browser blocked within seconds and stops listening for a late one; resolves once the window boots, which drops the hello from… |
| `src/lib/browser-window.ts` | Exports `createBrowserWindowOpener`, `announceWebappWindow`, `sessionWindowTarget` |
| `src/lib/browser-zoom.ts` | Exports `createBrowserZoom` |
| `src/lib/budgeted-loop.test.ts` | Tests: createBudgetedLoop; enforces the fps budget: frames inside the interval reschedule without drawing; keeps drawing while unfocused but pauses while minimized; parks when idleWhen reports nothing to animate and wak… |
| `src/lib/budgeted-loop.ts` | Budgeted renderer loop — the one way to run a decorative rAF animation. Desktop has repeatedly shipped the same bug class: an animation loop that never sleeps (bots face clock #88543, pixel egg #88406, diffusion placeho… |
| `src/lib/chat-empty.ts` | CHAT EMPTY STATE — the blank transcript as a contribution area. Core owns exactly one empty state: the intro splash, which belongs to a fresh draft with no session selected. A session that exists but has nothing in it y… |
| `src/lib/chat-messages.codex-commentary-reprojection.test.ts` | Tests: public Codex commentary after transcript hydration; keeps a tool-call preamble in assistant text, not the Thinking disclosure; removes only exact commentary segments, preserving surrounding and incidental reasoni… |
| `src/lib/chat-messages.codex-json-sidecar.test.ts` | Tests: hydrates the SQLite JSON-text sidecar returned by REST like the decoded RPC sidecar |
| `src/lib/chat-messages.codex-sidecar-hydration.test.ts` | #68321 / GregKM 2026-09-02 v0.21.0 DB-level evidence: an assistant row whose persisted `content` is empty but whose user-visible response text lives only in `reasoning` / `reasoning_content` is dropped by hydration |
| `src/lib/chat-messages.interim-preservation.test.ts` | Tests: stored assistant commentary preservation; keeps separate commentary items in order and joins only chunks of the same item; keeps backend-authorized commentary without exposing analysis; does not duplicate comment… |
| `src/lib/chat-messages.stopped-tool-fold.test.ts` | A turn stopped after a tool round is stored as narration + tool call, the tool result, then the interrupted partial. The partial folds into the tool bubble on read; the stored copy that replaces the live one (any refres… |
| `src/lib/chat-messages.test.ts` | Tests: withUniqueToolCallIdsWithinMessage; renames a duplicate toolCallId within one message (#87857); returns the same reference when there is no duplicate; toChatMessages |
| `src/lib/chat-messages/attachment-turn.ts` | Attachment-rewrite tolerance for pasted attachments (#120978, follow-up to #119326). A pasted clipboard attachment has no rowId on the optimistic local row, and the backend rewrites the durable prompt around it: the cap… |
| `src/lib/chat-messages/competing-contracts.test.ts` | Tests: D1 competing implementation contracts; keeps identified parallel running calls separate even with identical args; honors explicit successful skill results over stale envelope errors; does not report a failed skil… |
| `src/lib/chat-messages/coverage.ts` | Exports `withoutCoveredAssistantPrefix` |
| `src/lib/chat-messages/d1-consumers.test.ts` | Tests: D1 settlement and presentation consumers; seals unknown outcomes without fabricating success and remains idempotent; keeps side-channel diffs in the changed-files consumer after normalization; keeps envelope-only… |
| `src/lib/chat-messages/hydration-model-only.test.ts` | A micro-compaction merge (`display_metadata.model_only`) is skipped, but the ids of the rows after it keep their stored position: filtering first shifted every later message and tool-part id by one. |
| `src/lib/chat-messages/hydration.ts` | Exports `toChatMessages` |
| `src/lib/chat-messages/index.ts` | TypeScript source: `index` |
| `src/lib/chat-messages/parts.capture.test.ts` | Regression for #84361: the bare-word capture branch absorbed trailing sentence punctuation (`open MEDIA:/tmp/a.pdf.` captured `/tmp/a.pdf.`) and accepted degenerate captures (a lone quote, `...`, a bare word with neither |
| `src/lib/chat-messages/parts.test.ts` | Regression for #96657: an unquoted MEDIA: path with interior spaces rendered a card for the text before the first space and left the rest as prose. |
| `src/lib/chat-messages/parts.ts` | Exports `textPart`, `reasoningPart`, `reasoningTextFromDetails`, `renderMediaTags`, `mediaTagValues`, `assistantTextPart` … |
| `src/lib/chat-messages/reasoning-details.test.ts` | Tests: reasoning-details display text; extracts prose from decoded or serialized envelopes without exposing opaque fields; hydrates only extracted reasoning text and preserves canonical-field precedence; hydrates an opa… |
| `src/lib/chat-messages/reconciliation.test.ts` | Tests: reconciles only the represented failed tail, retaining its structured error and omitted segments; drops a local errored turn the refreshed transcript already stored under new ids; keeps an unstored errored turn a… |
| `src/lib/chat-messages/reconciliation.ts` | Exports `spliceOlderPreservedRows`, `preserveLocalAssistantErrors`, `isLocalSystemNotice`, `preserveLocalSystemNotices`, `branchGroupForUser` |
| `src/lib/chat-messages/tool-parts.ts` | Exports `QUESTION_CARD_TOOLS`, `upsertToolPart`, `PendingClarifyProjection`, `SettledClarifyProjection`, `hasUnresolvedToolCall`, `toolCallOwnerMessageId` … |
| `src/lib/chat-messages/tool-result-preservation.test.ts` | Tests: live tool result evidence; preserves every JSON value and display hints through the real runtime adapter and replay; distinguishes a missing completion result from empty results and keeps parallel completions sep… |
| `src/lib/chat-messages/types.ts` | Exports `TimelinePartMetadata`, `ChatMessagePart`, `ChatMessage`, `GatewayEventPayload` |
| `src/lib/chat-runtime.test.ts` | Tests: createClientSessionState; anchors a fresh runtime to its creation time; optimisticAttachmentRef; renders a path-backed image through the same @image: ref as a reloaded turn (#93204) |
| `src/lib/chat-runtime.ts` | Exports `createClientSessionState`, `markReasoningEffortPending`, `sessionTitle`, `NEW_SESSION_TITLE`, `coerceGatewayText`, `coerceThinkingText` … |
| `src/lib/clipboard.test.ts` | Tests: installClipboardShim; routes an Electron write through IPC first; uses the native write only after the Electron IPC write fails; writeClipboardText |
| `src/lib/clipboard.ts` | Primitives and CopyButton enter one policy, never nested fallback retries. |
| `src/lib/cloud-agent-session.ts` | Re-establish a Hermes Cloud agent's gateway session from the shared portal session: drop any lapsed gateway cookies, make sure the portal session is live (interactive login window when it has lapsed), then run the silen… |
| `src/lib/code-skew-error.test.ts` | Tests: isCodeSkewRestartRequired; detects the Models-page IPC 503 from a stale Desktop-owned backend; detects a bare FastAPI detail string; ignores unrelated 503s and load failures |
| `src/lib/code-skew-error.ts` | True when a backend error is the post-update stale-module 503 (#97046). |
| `src/lib/commit-changelog-localization.test.ts` | Tests: changelog display copy; overrides labels without changing grouping, ordering or authored subjects; uses caller fallback copy only when no user-facing commits remain |
| `src/lib/commit-changelog.test.ts` | Tests: parseCommitHeader; extracts type, scope, and subject from a conventional header; flags breaking changes via the ; treats non-conventional commits as untyped with the full header as subject |
| `src/lib/commit-changelog.ts` | Tiny user-facing changelog builder. Takes a list of raw commit summaries, parses the Conventional Commits 1.0 header (`type(scope)!: subject`), filters internal noise (chore/ci/docs/...), and groups the rest into friend… |
| `src/lib/completion-poll.test.ts` | Tests: startCompletionPoll; keeps a slow producer single-flight and resumes cadence after completion; stop suppresses a late publish and leaves no timer behind |
| `src/lib/completion-poll.ts` | Exports `startCompletionPoll` |
| `src/lib/completion-sound.test.ts` | Check completion cue ownership races without opening a real audio device. |
| `src/lib/completion-sound.ts` | Completion sound bank for agent turn-end cues. Fourteen curated presets for A/B in Settings → Appearance, plus variant 0 ("None") to turn the cue off. Default is variant 1. |
| `src/lib/composer-input-sanitize.test.ts` | Tests: stripLeakedBracketedPasteWrappers; strips canonical escape wrappers; keeps embedded literal bracket forms; collapseRepeatedInputArtifacts |
| `src/lib/composer-input-sanitize.ts` | Strip terminal bracketed-paste leaks and repeated artifact tails from composer text before it is shown in the UI or sent to the gateway. Mirrors hermes_cli/input_sanitize.py (CLI/TUI gateway defensive path). |
| `src/lib/connection-display.test.ts` | Tests: connection display helpers; anchors local first and sorts labels case-insensitively with numeric order; does not mutate registry order; matches labels, transport details, localized aliases, and accents |
| `src/lib/connection-display.ts` | Exports `CONNECTION_SEARCH_THRESHOLD`, `sortConnectionsForDisplay`, `connectionMatchesQuery`, `connectionEndpoint`, `connectionTooltip` |
| `src/lib/connection-scoped.test.ts` | Tests: connectionScopeSuffix; is empty for a local connection; includes the profile by default so profile-local lists stay apart; is stable across profile switch when includeProfile is false |
| `src/lib/connection-scoped.ts` | ── Connection-scoped persistence ─────────────────────────────────────────── Multiple Desktop windows share one renderer origin — and therefore one localStorage area — while each window can be connected to a DIFFERENT |
| `src/lib/connector-tools.ts` | Exports `McpTarget`, `mcpTargets`, `ConnectionStatus`, `ConnectorRow`, `connectorIconUrl`, `connectorText` … |
| `src/lib/deeplink-routes.test.ts` | Tests: resolveDeepLinkAction; routes unified plugin install deeplinks; routes catalog= to the catalog lookup, never to a git-path install; does not trust URL catalog metadata on a repository install |
| `src/lib/deeplink-routes.ts` | Exports `DeepLinkPayload`, `DeepLinkAction`, `resolveDeepLinkAction` |
| `src/lib/desktop-fs.test.ts` | Tests: desktop filesystem facade; uses local Electron filesystem methods in local mode; treats browser-hosted local Desktop as backend filesystem mode; routes filesystem reads through authenticated backend REST in remot… |
| `src/lib/desktop-fs.ts` | Exports `DesktopFsRemotePicker`, `setDesktopFsRemotePicker`, `desktopFsCacheKey`, `isDesktopFsRemoteMode`, `desktopFsProfile`, `DesktopFsSessionScope` … |
| `src/lib/desktop-git.test.ts` | Tests: desktop git facade; returns undefined after the renderer global is torn down; uses Electron git locally; routes reads through the backend REST mirror on a remote gateway |
| `src/lib/desktop-git.ts` | Exports `desktopGit` |
| `src/lib/desktop-remote-auth.test.ts` | Tests: deriveRemoteAuthProviderShape; uses fallback copy when the gateway has not reported providers; marks providers as password-style only when every provider supports password login; keeps OAuth copy for redirect pro… |
| `src/lib/desktop-remote-auth.ts` | Exports `RemoteAuthProviderShape`, `deriveRemoteAuthProviderShape` |
| `src/lib/desktop-slash-commands.test.ts` | Tests: desktop slash command curation; treats registry and plugin commands as exec when the catalog says so; hands the /skills write-approval subcommands to the backend, keeping the hub mutations off the wire; groups co… |
| `src/lib/desktop-slash-commands.ts` | Exports `CommandsCatalogSection`, `CommandCatalogMeta`, `CommandsCatalogLike`, `SkillCatalogEntry`, `SkillCatalogMap`, `DesktopSlashCompletion` … |
| `src/lib/desktop-slash-registry.json` | JSON object with keys `/agents`, `/approvals`, `/approve`, `/autoprune`, `/battery`, `/bg` |
| `src/lib/desktop-toolsets.ts` | Curation for the desktop "Skills & Tools → Toolsets" list. `GET /api/tools/toolsets` returns the full CONFIGURABLE_TOOLSETS set with no desktop-specific filter — so it surfaces entries that don't belong in a flat |
| `src/lib/display-path.test.ts` | Tests: displayPath; collapses a macOS home prefix to ~; collapses a Linux home prefix to ~; collapses a Windows user profile to ~ |
| `src/lib/display-path.ts` | One place to format filesystem paths for DISPLAY. Industry standard (shells, VS Code `tildify`, Finder path bar): collapse the user's home directory to `~`, keep forward slashes, leave everything else alone. Copy/reveal… |
| `src/lib/distribution-label.ts` | Pure distribution-label selection for the version-details "Distribution" row, shared by every surface that names an install's provenance. The install stamp carries three independent facts and the label keys on the pair… |
| `src/lib/docs.ts` | docs.ts — canonical docs-site links used by the renderer's recovery and setup surfaces. Single authority so the "reinstall the app" affordance (bundled installs with a damaged payload) and any future doc links point at… |
| `src/lib/download-text.ts` | Save generated text content to a file via a blob download. |
| `src/lib/download.test.ts` | Tests: imageFilename; takes the last path segment of a URL; falls back to ; downloadFilename |
| `src/lib/download.ts` | Exports `imageFilename`, `downloadFilename`, `clickDownloadLink`, `downloadBlob` |
| `src/lib/draft-title.ts` | Matches `agent/title_generator.py`'s MAX_DERIVED_TITLE_CHARS, so a draft doesn't visibly reflow the moment the backend's derived title replaces it. |
| `src/lib/drag-ghost.ts` | A flat, pointer-following drag chip — the shared "what am I holding" affordance for in-app pointer drags. Plain DOM (no React) so it survives a pointer-capture drag without re-renders and tears down synchronously on Esc… |
| `src/lib/embedded-images.test.ts` | Tests: extractEmbeddedImages; returns text untouched when no data URL is present; lifts a bare data:image URL out of prose; lifts a JSON-wrapped image_url envelope out of prose |
| `src/lib/embedded-images.ts` | Exports `DATA_IMAGE_URL_RE`, `EmbeddedImageExtraction`, `dataUrlToBlob`, `extractEmbeddedImages`, `embeddedImageUrls`, `textWithoutEmbeddedImages` … |
| `src/lib/error-surface-copy.test.ts` | Tests: does not blame a slow reply when the provider could not be reached |
| `src/lib/error-surface-copy.ts` | Resolves the error card's title/body for a failed turn from the i18n tables (`assistant.thread.errorCodes` / `errorAuthKinds` / `errorLayers`), so the inline card and the global gateway-error toast read the same words f… |
| `src/lib/error-surface.test.ts` | Tests: parseErrorSurface; accepts a valid descriptor; accepts every documented layer; rejects unknown layers and non-objects |
| `src/lib/error-surface.ts` | Structured turn-error descriptor forwarded by the gateway (see agent/error_surface.py). Names WHICH layer of the stack failed and the classifier's failure code so the error card can say what happened in plain |
| `src/lib/escape-layers.test.ts` | Tests: escape-layers; reports top when nothing is registered; a lower layer yields to a higher open one, and reclaims top when it closes; equal-or-higher priority counts as top (ties act) |
| `src/lib/escape-layers.ts` | Ordered Escape ownership for the app's transient window-level layers. Several surfaces bind their own `window` `keydown` Escape handler (narrow-pane reveal, layout edit mode, the zone editor, full-page overlays). Withou… |
| `src/lib/excluded-paths.ts` | Always hidden across the file tree and review (git) tree, regardless of .gitignore: the VCS internals, heavyweight dep/build/cache dirs, and OS noise. These bloat both trees and are never worth browsing or reviewing — e… |
| `src/lib/execution-authority.frames.json` | JSON object with keys `_generated_by`, `epoch1`, `epoch2` |
| `src/lib/execution-authority.test.ts` | `execution-authority.frames.json` is captured from the real owner (`tests/gateway/fixtures/execution_frames_capture.py`): two successive authority epochs each running one turn on the same session, then an idle `rename`… |
| `src/lib/execution-authority.ts` | Exports `ExecutionStampedEvent`, `acceptExecutionEvent` |
| `src/lib/external-link.test.tsx` | Tests: external link helpers; formats URL fallbacks as host + path; derives readable title fallbacks from URL slugs; keeps identifier casing in separator-less slug tokens but still title-cases words |
| `src/lib/external-link.tsx` | Exports `normalizeExternalUrl`, `shortHostLabel`, `hostPathLabel`, `urlSlugTitleLabel`, `isConnectorAuthorizationLink`, `isTitleFetchable` … |
| `src/lib/file-preview-math.render.test.tsx` | This is the exact pipeline the file preview runs: normalizeFilePreviewMath → Streamdown with the memoized math plugin. Rendering here (jsdom) proves the wiring produces KaTeX output, not raw `$..$` source text. |
| `src/lib/find-in-page-scope.test.ts` | Unit tests for the renderer-side find walker. These tests plant DOM by hand and drive the walker directly so the behavior is auditable without spinning up the React store. The end-to- end behavior (open / setFindQuery /… |
| `src/lib/find-in-page-scope.ts` | Renderer-side find-in-page that scopes matches to the CURRENT VIEW — the active chat surface — instead of the whole document. Background. Electron's `webContents.findInPage` searches the renderer's entire DOM. The deskt… |
| `src/lib/find-in-page.ts` | Pure logic for the find-in-page bar (⌘F). Kept out of the component so the match-counter projection and the in-bar key routing can be unit-tested without jsdom, a BrowserWindow, or the preload bridge. |
| `src/lib/gateway-events.test.ts` | Tests: gateway event routing; rehydrates pending approvals on reconnect ready and resumed session info; does not replay against an active runtime the gateway already reported gone; drops only unscoped subagent events (g… |
| `src/lib/gateway-events.ts` | Exports `UNSCOPED_STREAM_EVENT_TYPES`, `gatewayEventRequiresSessionId`, `GatewayEventSessionRouteInput`, `GatewayEventSessionRoute`, `approvalReplaySessionId`, `resolveGatewayEventSessionId` … |
| `src/lib/gateway-health-pill.test.ts` | Tests: statusBarGatewayHealth; does not paint Gateway ready when the serve socket is up and messaging is down; stays backend-ready when messaging was never configured, and names a down platform while the process is up |
| `src/lib/gateway-health-pill.ts` | Status-bar "backend health" pill. The serve/chat socket and the messaging gateway are different processes; this derivation is the one place that names them so the painted label cannot be read as "Discord is up". |
| `src/lib/gateway-liveness-policy.test.ts` | Tests: decideLivenessForceClose; keeps the socket on the first timeout while a turn is in flight (#95327); defers for every busy session count, not just one; closes once the unanswered streak reaches the limit even whil… |
| `src/lib/gateway-liveness-policy.ts` | Liveness-probe force-close policy for the primary gateway socket (#95327). Why this exists ─────────────── Every window-lifecycle recovery signal (power resume, network online, focus, visibility) nudges `reconnectNow()`… |
| `src/lib/gateway-rpc.test.ts` | Tests: isMissingRpcMethod; trusts the JSON-RPC code over the message when the frame survived; falls back to the message for codeless (IPC-flattened) errors; ignores unrelated failures |
| `src/lib/gateway-rpc.ts` | True when a JSON-RPC call failed because the backend predates the method. The gateway answers -32601 (`tui_gateway/server.py::dispatch`) and the shared client keeps that code on the error; the message match is only for… |
| `src/lib/gateway-ws-url.test.ts` | Tests: desktop connection scope; a registry-scoped flag without a connectionId still takes the legacy mint; a registry-scoped OAuth route without the scoped mint bridge fails instead of dialing the legacy gateway; a reg… |
| `src/lib/gateway-ws-url.ts` | Exports `resolveDesktopGatewayWsUrl` |
| `src/lib/generated-images.test.ts` | Tests: generatedImageFromResult; prefers the host-visible image path; ignores failed image generation results; stripGeneratedImageEchoes |
| `src/lib/generated-images.ts` | Exports `generatedImageFromResult`, `generatedImageDimensionsFromResult`, `generatedImageEchoSources`, `stripGeneratedImageEchoes`, `dedupeGeneratedImageEchoesInParts` |
| `src/lib/guarded-model-switch.test.tsx` | @vitest-environment jsdom |
| `src/lib/guarded-model-switch.ts` | The gateway's model-switch handshake shape — shared by `config.set model` and `profiles.configure` (Bots editor). `confirm_required: true` means the switch was intentionally NOT applied and the gateway is waiting for a… |
| `src/lib/guest-pointer-guard.ts` | Electron <webview> guests (and iframes) hit-test in their own process, so a pointer-capture drag in the embedder goes silent the moment the cursor crosses one — a sash resize froze after a few pixels of travel into the… |
| `src/lib/haptics.ts` | Exports `HapticIntent`, `HapticTrigger`, `registerHapticTrigger`, `triggerHaptic` |
| `src/lib/hermes-open-target.test.ts` | Tests: normalizeHermesOpenString; accepts hash-router paths and strips a leading hash; maps plugin-scoped hermes:// deep links to the same path; maps hermes://open/… deep links by stripping the open host |
| `src/lib/hermes-open-target.ts` | Shared resolver for in-app navigation targets that must stay compatible with `hermes://` deep links and `host.navigate('/path?…')`. Notification activation, deep-link delivery, and plugin `activate` payloads all funnel… |
| `src/lib/host-capabilities.test.ts` | @vitest-environment jsdom |
| `src/lib/host-capabilities.ts` | What the renderer's host can do, by name. The same renderer runs in Electron (native Desktop) and in a browser tab the gateway serves (the Webapp). Call sites ask for the capability they gate, never for the host, so a r… |
| `src/lib/icons.ts` | Exports `iconSize`, `IconSize` |
| `src/lib/identity-trace.ts` | Change-only desktop.log trace for multi-connection identity decisions: which socket a (connection, profile) request rides, the rows each connection returned to the bot relay, and per-route bot titles. Two registry sourc… |
| `src/lib/image-resize.test.ts` | A minimal valid 1x1 red PNG (67 bytes) for testing |
| `src/lib/image-resize.ts` | Downscale a data URL for preview rendering. Large images (Retina screenshots, 6000×4000+) cause Chromium to build very large paint operations when the original is assigned to an <img>. This utility uses createImageBitma… |
| `src/lib/ime.test.ts` | Tests: isImeComposing; detects composition via nativeEvent.isComposing (React events); detects composition via isComposing on the event itself (DOM events); detects the legacy 229 keyCode on nativeEvent |
| `src/lib/ime.ts` | IME-aware Enter handling, shared by every text field whose bare Enter performs an action (submit, rename, commit, adopt, …). CJK/IME users press Enter to *commit a composition* — the candidate text they are still assemb… |
| `src/lib/incremental-external-store-runtime.test.ts` | Tests: syncRepositoryIncrementally; writes only the changed tail instead of the whole transcript; does nothing at all when the transcript is unchanged; appends a new message through the full path |
| `src/lib/incremental-external-store-runtime.ts` | Exports `syncRepositoryIncrementally`, `IncrementalExternalStoreRuntimeCore`, `useIncrementalExternalStoreRuntime` |
| `src/lib/incremental-runtime-adapter-notify.test.ts` | Regression tests for the bot-chat tile crash observed live on 2026-08-23: [error-boundary:contrib:session-tile:20260823_213059_ed6222] Error: Maximum update depth exceeded. The result of getSnapshot should be cached to… |
| `src/lib/inflight-turn-journal.test.ts` | Tests: persistInFlightTurnState; sweeps expired and oldest session entries once before the first write; keeps another session snapshot when one session settles; journals the running turn tail after the throttle window |
| `src/lib/inflight-turn-journal.ts` | Exports `InFlightTurnSnapshot`, `JournalableSessionState`, `InFlightRecoveryResult`, `mergeInFlightMessages`, `resetInFlightTurnJournalStateForTests`, `persistInFlightTurnState` … |
| `src/lib/input-modality.test.ts` | Tests: lastInputModality; defaults to keyboard before any input; tracks the device behind the last interaction; sees events a handler stops from bubbling (capture phase) |
| `src/lib/input-modality.ts` | Which input device drove the most recent interaction. Chromium's `:focus-visible` is not enough to tell a mouse pick from a Tab. Radix menus autofocus their content on open and keyboard-navigate their items, so by the t… |
| `src/lib/json-format.test.ts` | Tests: tryFormatJson; pretty-prints compact JSON; leaves empty input unchanged; reports parse errors |
| `src/lib/json-format.ts` | Exports `FormatJsonResult`, `tryFormatJson` |
| `src/lib/json-rpc-gateway-heartbeat.test.ts` | Tests: JsonRpcGatewayClient heartbeat recovery; invalidates a silently dead advertised socket and ignores its late frames; keeps older backends open when gateway.ready does not advertise heartbeat; keeps an answered soc… |
| `src/lib/json-rpc-gateway-recovery.test.ts` | Tests: hermes-ws-recovery-v1 silent blackhole; keeps a replacement socket open when a superseded connect times out; recovers the persisted final on a replacement socket without duplicating the prompt |
| `src/lib/json-rpc-gateway-url-guard.test.ts` | connect() must reject before WebSocket coerces garbage into `ws://<origin>/[object%20Object]` (#68250 stale-emit boot loop). |
| `src/lib/katex-memo.ts` | Memoizing wrapper around `rehype-katex`. Why: the default ` |
| `src/lib/keybinds/actions.test.ts` | Tests: KEYBIND_ACTIONS; has unique ids (a duplicate would shadow a row in the shortcuts panel); gives every built-in action an English label so it renders in the shortcuts panel; keeps session archive registered and unb… |
| `src/lib/keybinds/actions.ts` | The single source of truth for rebindable desktop hotkeys. Each entry is pure metadata: an id, a category, and the default combo(s). Handlers are wired separately in `use-keybinds.ts` (they need React context |
| `src/lib/keybinds/approval-keys.ts` | Exports `releaseApprovalKey`, `handleApprovalKey` |
| `src/lib/keybinds/browser-defaults.test.ts` | Chords Chrome, Edge and Firefox act on before the page's keydown handler can cancel them (new window/tab/private window, close tab/window, reopen tab, tab cycling, quit), in the canonical form `comboFromEvent` emits per… |
| `src/lib/keybinds/browser-hints.test.tsx` | Tests: renders the resolved browser binding in the first-run tip, tooltips and settings, including remaps |
| `src/lib/keybinds/chords.ts` | True when the event is the ⌘/Ctrl+L chord (no shift). The chord routes input to the composer: a terminal or preview selection goes in as context, and a bare press moves focus. The priority ladder between those consumers… |
| `src/lib/keybinds/combo.test.ts` | Host-native: jsdom never reports a Mac platform, so `IS_MAC` is false here. Mac-only Control/Cmd branches are not faked (tests/AGENTS.md "Don't fake the host OS"). |
| `src/lib/keybinds/combo.ts` | Keybind combo normalization + display. A combo is a canonical lowercase string like "mod+k", "mod+shift+]", "shift+x", or "r". `mod` is Cmd on macOS / Ctrl elsewhere, so a single binding works on |
| `src/lib/keybinds/composer-focus-keys.test.ts` | Tests: isActivateOnEnterTarget; ignores body / null; detects buttons and walks to a wrapping activator; composerFocusBlockedBySurface |
| `src/lib/keybinds/composer-focus-keys.ts` | Soft focus / type-to-focus for the chat composer. On empty chat chrome, Enter focuses the composer; printable keys focus and type. Bound shortcuts still win via the keybind index. Surfaces that own keys (dialogs, menus,… |
| `src/lib/keybinds/contributed-actions.test.ts` | The plugin-command contract: a plugin ships a hotkey through the `keybinds` area and it behaves like a built-in — it dispatches, it resolves a combo for the palette hint, and it survives the plugin being unloaded. These… |
| `src/lib/keybinds/handled-keys.ts` | Keydowns the window keybind dispatcher ran as a Hermes action. It cancels every chord it matches in capture, including one whose passthrough handler then declines, so `defaultPrevented` alone doesn't say an action ran.… |
| `src/lib/keybinds/plugin-actions.ts` | Built-in app actions a plugin may run by id (`ctx.runAction`), through the SAME handler the keyboard shortcut and the command palette dispatch. A plugin that wants "toggle the browser panel" asks for the action, not for |
| `src/lib/keybinds/use-keybind-hint.ts` | The formatted first combo for `actionId`, or null when unbound. Rebindable actions read live from the store; readonly shortcuts (e.g. `composer.steer`) fall back to their fixed combo. Returns null for unknown action ids… |
| `src/lib/keyed-timeouts.ts` | Per-key setTimeout registry for "let this linger, then drop it" UI state. Scheduling a key replaces its pending timer, and an entry removes itself when it fires, so the map never accumulates dead keys. |
| `src/lib/layout-persistence.test.ts` | Tests: retains legacy data in memory when migration writes fail and retries on the next launch; isolates invalid records and keeps auxiliary layouts off primary storage |
| `src/lib/layout-persistence.ts` | Exports `LAYOUT_KEYS`, `createLayoutPersistence` |
| `src/lib/legacy-session-owner-backfill.test.ts` | Tests: maybeBackfillLegacySessionOwners (one-shot per scope); treats the owning gateway\; re-arms the scope after a transient failure so the next enumeration retries; resolveLegacyOwnerBackfillScope (#94724 single-match… |
| `src/lib/legacy-session-owner-backfill.ts` | One-shot durable owner backfill for legacy NULL-profile session rows (#94724 legacy-session migration). The #95407 durable-ownership work made owner resolution fail closed under registry topology, but shipped no migrati… |
| `src/lib/listing-embed.test.ts` | Shaped like what the agent actually emits after a portal sweep. |
| `src/lib/listing-embed.ts` | LISTING EMBEDS — property/rental listings as native transcript cards. The rental portals (Zillow, Redfin, Compass, HAR, homes.com) publish no embeddable surface: the public APIs are deprecated or broker-gated, there is… |
| `src/lib/loadout.ts` | ── Loadout codec ───────────────────────────────────────────────────────────── A generic, WoW-talent-loadout-style binary share codec: pack *bits and indices* (not JSON), DEFLATE the body, frame it with a version + chec… |
| `src/lib/local-gateway-ensure-failure.ts` | Main-process refusals from a local `hermes gateway ensure` (electron/local-gateway.ts) that no automatic redial can fix: every redial of the scope re-spawns the same ensure client against the same install and gets the s… |
| `src/lib/local-preview.local-target.test.ts` | #101683 pipeline invariant: a typed non-previewable normalization result (directory / missing) must NOT fall through to the renderer's blind local classification, which fabricates a text-preview tab for a path that cann… |
| `src/lib/local-preview.test.ts` | Tests: isLoopbackPreviewUrl; remote HTML previews; loads bounded authenticated bytes while retaining the canonical file URL; falls back to source mode when the transport is not canonical HTML |
| `src/lib/local-preview.ts` | Exports `pathToFileUrl`, `isLoopbackPreviewUrl`, `validatedRemoteHtmlDataUrl`, `remoteHtmlPreviewDocument`, `openPreviewTargetInBrowser`, `localPreviewTarget` … |
| `src/lib/log-search.test.ts` | Tests: findLogSearchHits; returns offsets that slice the original line back to the query, case-insensitively; treats the query as a literal, not a pattern; logLineSegments |
| `src/lib/log-search.ts` | Pure matching behind in-log search (LogTail + useLogSearch). Kept free of React so the offsets, segment cuts, and severity column are testable alone. |
| `src/lib/long-poll.ts` | The sign-in and handoff reads are long-polls: the backend holds each request until something changes. An older backend answers at once, so a loop never asks again sooner than this after its previous ask started. |
| `src/lib/lru-cache.test.ts` | Tests: LruCache; never grows past its ceiling; evicts the least recently READ entry, not the least recently written; overwrites in place rather than evicting a live neighbour |
| `src/lib/lru-cache.ts` | A `Map` with a ceiling. The renderer stays open for days, so a module-level cache keyed by anything user-driven (a URL, a connection id, an equation) grows for the life of the window unless something evicts. Only for va… |
| `src/lib/markdown-blocks.test.ts` | The contract: streaming through the cached splitter (one call per growing prefix, exactly how Streamdown calls it per flush) must produce, at every step, the same blocks as a fresh full lex of that prefix. Byte equality… |
| `src/lib/markdown-blocks.ts` | Block splitting for the streaming markdown pipeline, without re-lexing the whole message on every token flush. `parseMarkdownIntoBlocks` is a full `marked` lex of the entire text — measured 3.4–9.6ms per call at 64–192K… |
| `src/lib/markdown-code.test.ts` | Tests: isLikelyProseCodeBlock; detects prose that Streamdown mislabels as an unknown language; keeps real code blocks; keeps an SSH config block fenced (regression: rendered as flat prose) |
| `src/lib/markdown-code.ts` | Exports `sanitizeLanguageTag`, `codiconForLanguage`, `codiconForFilename`, `shikiLanguageForFilename`, `isLikelyStructuredText`, `isLikelyProseFence` … |
| `src/lib/markdown-html-depth.test.ts` | The clamp exists to keep parse5 / hast-util-from-parse5 recursion off the call stack. Its contract is about DEPTH of unclosed elements, so the tests assert that relationship rather than any particular output string. |
| `src/lib/markdown-html-depth.ts` | Bound the nesting depth of raw inline HTML before it reaches `rehype-raw`. Streamdown parses assistant markdown with `allowDangerousHtml` + `rehype-raw`, so any `<tag>` run in the text is handed to parse5. `hast-util-fr… |
| `src/lib/markdown-preprocess.autolink.test.ts` | The bare-URL autolinker wraps prose URLs in `<…>`. It must leave URLs that markdown syntax already owns alone: wrapping the label of `[url](url)` swallowed `](url)` into the href (#49822, #85234). Each case asserts the… |
| `src/lib/markdown-preprocess.citation.test.ts` | Web-citation transport markers (Gemini-style grounding) arrive in model output as private-use-delimited id lists. Desktop must never paint them: the U+E200..U+E202 glyphs render as replacement boxes ("triple bars") and |
| `src/lib/markdown-preprocess.directives.test.ts` | A transcript directive (`::onboarding{...}`) is a card only while the parser hands the paragraph over as ONE text node; the moment an attribute value reads as markdown the paragraph splits into element children and the… |
| `src/lib/markdown-preprocess.fences.test.ts` | Listings whose own text carries fence characters: a ``` mid-line, and the inner fences of a markdown example fenced with a longer or other marker. Each must reach the renderer byte-for-byte, with the prose after it outs… |
| `src/lib/markdown-preprocess.file-preview.test.ts` | Tests: normalizeFilePreviewMath; leaves single-dollar inline math untouched; escapes currency dollar amounts so they are not parsed as math; does not escape dollars inside code fences |
| `src/lib/markdown-preprocess.reasoning.test.ts` | preprocessMarkdown runs on the accumulated text every streaming flush, so the reasoning strip has to behave on a text whose close tag has not arrived yet. |
| `src/lib/markdown-preprocess.ts` | Same tag set as agent/think_scrubber.py THINK_TAG_NAMES, plus desktop-only `scratchpad`/`analysis`. |
| `src/lib/markdown-table-widths.ts` | Column widths for markdown tables in the transcript. A markdown table has no id — it is re-parsed from text on every render, and the same table reappears when the session is reloaded or switched back to. So |
| `src/lib/markdown-whitespace.test.ts` | Tests: Markdown whitespace semantics; preserves significant whitespace through display preprocessing; preserves text outside removed media and preview spans |
| `src/lib/mcp-brands.tsx` | Curated brand glyphs for MCP server names — extracted from the mcp-tab's avatar (its `MCP_BRAND_ICONS`) the moment a second surface (the composer suggestion pills / inline setup card) needed the same identity ladder. Th… |
| `src/lib/mcp-cost.test.ts` | Tests: estimateServerTokens; sums ceil(schema_chars / 4) over tools; returns null when no tool carries schema_chars (older backend); ignores invalid schema_chars values |
| `src/lib/mcp-cost.ts` | MCP fleet cost/usage math — pure functions behind the Capabilities page's per-server cost overlay ("~4.2k tok, 3 uses/30d"). Display-only: nothing here changes what schemas are sent to models. |
| `src/lib/mcp-dashboard-oauth.test.ts` | Tests: Desktop MCP client callback lifecycle |
| `src/lib/mcp-dashboard-oauth.ts` | Exports `McpOAuthCancelled`, `completeMcpDesktopOAuth` |
| `src/lib/mcp-deeplink.test.ts` | Tests: parseMcpInstallDeepLink; accepts a url-shaped config (base64url); accepts a command-shaped config (standard base64 with padding); rejects names outside ^[A-Za-z0-9._-]{1,64}$ |
| `src/lib/mcp-deeplink.ts` | Parser/validator for the `hermes://mcp/install?name=NAME&config=B64` deep link (the "Add to Hermes" button MCP vendors embed, mirroring Cursor's `cursor://anysphere.cursor-deeplink/mcp/install` scheme). `config` is base… |
| `src/lib/mcp-enabled-cases.json` | JSON list (20 entries) |
| `src/lib/mcp-import.test.ts` | Tests: parseMcpImport; mcp.json snippets; parses an mcpServers-wrapped document; parses a bare name→config map and normalizes the Cursor/Claude type field |
| `src/lib/mcp-import.ts` | Paste-anything MCP import: turns whatever a README tells the user to copy — an mcp.json snippet, a bare `npx`/`docker` command, a `claude mcp add` line, a plain server URL, or a Cursor install deeplink — into named mcp.… |
| `src/lib/mcp-probe-cache.test.ts` | Tests: classifyProbe; classifies a successful probe as ok; classifies other failures as error; classifies a failure without an error string as error |
| `src/lib/mcp-probe-cache.ts` | --------------------------------------------------------------------------- Shared MCP probe cache. Extracted from mcp-tab.tsx so the MCP page and the background health checker (store/mcp-health.ts) share ONE cache: a p… |
| `src/lib/mcp-reload.test.ts` | Tests: a saved MCP change reports what the chat got; stays quiet when the chat runs the change; says the change is deferred while the chat is busy, and when it applies; names every server that did not connect beside a p… |
| `src/lib/mcp-reload.ts` | What `reload.mcp` did for the chat that asked. The gateway decides and commits; Desktop only reads its answer, so a successful RPC envelope alone never means the chat got the change. |
| `src/lib/mcp-servers.test.ts` | Tests: getServers; returns empty when the map is absent or not a map; passes object entries through untouched; keeps entries whose fields are junk |
| `src/lib/mcp-servers.ts` | Shape helpers for the `mcp_servers` config map, shared by everything that reads or writes it: the MCP tab editor, the paste-anything importer, and the `hermes://mcp/install` deeplink dialog. These agree on what a server… |
| `src/lib/mcp-tool-filter.test.ts` | Tests: readToolsFilter; returns empty when no tools object; reads include/exclude and ignores non-string entries; isToolEnabled |
| `src/lib/mcp-tool-filter.ts` | Per-tool MCP gating. A server's optional `tools.include` (whitelist) / `tools.exclude` (denylist) decide which discovered tools the agent registers — `include` wins, no filter means all. Mirrors `_register_server_tools`… |
| `src/lib/media-dimensions.test.ts` | Tests: reads a remote-owned image through its gateway, never the local file reader; shares proven path aliases only within an owner and bounds regenerated metadata by LRU; keeps multi-megabyte inline sources to a small,… |
| `src/lib/media-file-download.test.ts` | Tests: captured gateway file download; reports an unavailable desktop bridge; rejects an absent stored path before invoking the bridge; confirms a completed save and stays quiet on cancel |
| `src/lib/media.remote.test.ts` | Tests: filePathFromMediaPath; passes through a plain path; decodes a file:// URL with encoded characters; mediaExternalUrl |
| `src/lib/media.ts` | Exports `MediaKind`, `mediaKind`, `isMarkdownDocumentPath`, `mediaMime`, `mediaName`, `mediaMarkdownHref` … |
| `src/lib/mic-meter-context.ts` | The mic level meters (the recorder's VAD and the barge-in monitor) each open an AudioContext on the capture stream. close() is async, so a context torn down at the end of one turn can still hold the device when the next… |
| `src/lib/middle-click.test.tsx` | Tests: middleClickHandlers; fires without an auxclick — the event Chromium eats when autoscroll starts; cancels mousedown so the autoscroll pan widget never appears; cancels the middle mousedown even with no action — th… |
| `src/lib/middle-click.ts` | `MouseEvent.button` for the middle (wheel) button. |
| `src/lib/model-options.test.ts` | Tests: requestModelOptions; uses the connected gateway even before a session exists; recovers an empty gateway catalog through profile-scoped REST without replacing the session selection; recovers through profile-scoped… |
| `src/lib/model-options.ts` | Exports `catalogProviderMatches`, `findCatalogProvider`, `currentModelCapabilities`, `moaPickRemoved`, `customDefaultSupersedesPick`, `modelOptionsQueryKey` … |
| `src/lib/model-picker-owner.test.ts` | Tests: resolveModelPickerOwner; keeps an active-A focused-B picker on the focused tile owner; uses the ambient owner when the primary session is focused |
| `src/lib/model-picker-owner.ts` | Exports `ModelPickerOwner`, `resolveModelPickerOwner` |
| `src/lib/model-status-label.test.ts` | Tests: model-status-label; strips trailing date-pin snapshots and dots hyphenated Anthropic versions; renders the Anthropic 1M-context route suffix as a tag, never raw brackets; renders local GGUF ids as a clean name wi… |
| `src/lib/model-status-label.ts` | Which model/provider pair a picker should mark "current". SessionView state also drives the composer label, so a complete pair there wins over an older `model.options` response. During initial hydration (or pre-session… |
| `src/lib/mutable-ref.ts` | Imperative ref write — extracted so react-compiler doesn't flag hook-arg refs. |
| `src/lib/oneshot.ts` | Shared client for one-off ("one-shot") LLM requests: a single stateless model call that runs OUTSIDE the conversation. It never appends to session history, so prompt caching stays intact. Use it for small generative cho… |
| `src/lib/path-compare.test.ts` | Tests: isWindowsAbsolutePath; cleanPath; unifies separators and drops trailing slashes; keeps root rather than collapsing to empty |
| `src/lib/path-compare.ts` | Comparing two paths for identity or containment, across host spellings. A cwd reaches us from the backend, a picker, a session row and a project record, and the four don't agree on separator, trailing slash or drive-let… |
| `src/lib/persist-store.ts` | Persist a store: the value it loads with (its default, or a heal of what was stored) as provisional, every later change as the user's. A load value equal to `fallback` (the store's default) is provisional even when it i… |
| `src/lib/persisted.test.ts` | Unique key per test run — persistentAtom instances are singletons per call, so tests mint fresh keys instead of sharing one. |
| `src/lib/persisted.ts` | A nanostore that auto-persists. Reads its seed from localStorage through the storage choke point (so every read/write is observable in one place) and writes back on every change — no per-atom subscribe boilerplate. |
| `src/lib/personalities.ts` | Single source of truth for built-in personality names on the desktop. Mirrors hermes_cli/personality.py BUILTIN_PERSONALITIES — the backend single owner. Keep in sync when a built-in is added there. |
| `src/lib/platform-status.ts` | One reading of a messaging platform's runtime state, shared by the Messaging page and the gateway menu so the same bot never shows two different tones. Anything enabled that isn't connected or failed (connecting, retryi… |
| `src/lib/platform.test.ts` | @vitest-environment jsdom |
| `src/lib/platform.ts` | Platform detection for the renderer. The renderer has no `process.platform`, and several surfaces need to know which OS they're on — keybind glyphs, terminal shortcuts, and glass. One definition so they can't disagree.… |
| `src/lib/plugin-catalog.test.ts` | Tests: lookupPluginCatalogEntry; asks the backend for the entry, not the docs host; refuses a non-catalog name before asking anyone; falls back to the direct feed only when the backend predates the lookup |
| `src/lib/plugin-catalog.ts` | The curated Hermes plugin catalog as the Desktop sees it. `PLUGIN_CATALOG_URL` (`/docs/api/plugins.json`, generated from the repo's `plugin-catalog/` directory at site build) is the catalog the Capabilities → Plugins ca… |
| `src/lib/plugin-source-urls.test.ts` | Tests: resolvePluginSourceLinks; maps owner/repo to github browse and clone urls; includes monorepo subdir in browse url; supports git@ github urls |
| `src/lib/plugin-source-urls.ts` | Exports `PluginSourceLinks`, `resolvePluginSourceLinks` |
| `src/lib/pointer-drag.ts` | Run a pointer drag until pointerup, then unbind both listeners. Capture-phase, on `window`, so the drag keeps tracking when the pointer leaves the element it started on. Forgetting one half of the teardown leaks a live… |
| `src/lib/pool.test.ts` | Tests: mapPool; preserves input order regardless of completion order; never exceeds the concurrency limit |
| `src/lib/pool.ts` | `Promise.all(items.map(fn))` with a concurrency cap: at most `limit` calls run at once, results stay in input order. Keeps a many-repo probe from spawning a `git` process per repo all at once. |
| `src/lib/preview-act/act-in-page.test.ts` | jsdom lays nothing out, so every rect is 0×0 and the engine's visibility check would reject the whole page. Give elements a plausible box, honouring an explicit width/height so a test can lay out a 1px one, and let `dis… |
| `src/lib/preview-act/act-in-page.ts` | PREVIEW ACT ENGINE — the one function that performs an interaction inside a page, so the agent can drive the in-app browser instead of only reading it. `elements` hands back an inventory of what can be interacted with,… |
| `src/lib/preview-act/identity.ts` | IDENTITY — deciding whether the element in front of us is one we already have a handle on, and naming it if it is not. This is what makes a delta possible at all. If handles churned every time a framework re-rendered, e… |
| `src/lib/preview-act/naming.test.ts` | Tests: slug; reads as words a person would recognise; collapses runs of punctuation rather than stacking hyphens; stays short enough to read at a glance, and never ends on a hyphen |
| `src/lib/preview-act/naming.ts` | NAMING — what an element is called, and what it is called by. Everything here turns an element into a short string: the accessible name, the durable handle's stem and slug, the landmark it sits under, the identity selec… |
| `src/lib/preview-act/types.ts` | PREVIEW ACT TYPES — the shapes the engine, the overlay, and the Python tool all agree on. Declarations only. They erase at compile time, which is what lets the engine modules import them while still stringifying into th… |
| `src/lib/preview-act/visibility.ts` | VISIBILITY — is this element actually there, and is it on screen. Two different questions with two different answers. `visible` decides whether an element belongs in the inventory at all: painted, not screen-reader-only… |
| `src/lib/preview-act/watch-in-page.test.ts` | jsdom has no layout engine, so every rect is zero and nothing would be positioned. Give elements a plausible box the way the act-engine tests do. |
| `src/lib/preview-act/watch-in-page.ts` | WATCH OVERLAY — paints the agent's actions onto the live preview page so a person can follow along: the field of things it can reach, a box round the one it is about to touch, and a cursor that goes there. There are exa… |
| `src/lib/preview-annotate/flush.ts` | Exports `AnnotateFlushPorts`, `AnnotateFlushResult`, `flushAnnotateStack` |
| `src/lib/preview-annotate/group.test.ts` | Tests: annotateSplitDepth; splits at the shallowest region where the comments disagree; does not split siblings inside one component; does not split when every comment is on the same element |
| `src/lib/preview-annotate/group.ts` | Structural grouping for a comment batch. Twenty-three comments used to arrive as twenty-three flat blocks, so the agent made twenty-three todos and worked them one at a time. The fix is not a classifier in the renderer… |
| `src/lib/preview-annotate/handoff.test.ts` | Tests: capturePreviewAnnotateDestination; pins the group owned by the active workspace when multiple groups are visible; pins the visible group nearest the Browser pop-out control when rooms are side by side; fails clos… |
| `src/lib/preview-annotate/handoff.ts` | Cross-window handoff for Browser Comment Mode. A popped-out Browser is a separate Electron renderer. The ordinary composer bus is intentionally window-local, so an annotation saved in that renderer cannot reach the chat… |
| `src/lib/preview-annotate/identity.ts` | Exports `ElementSnapshot`, `CompactIdentity`, `compactIdentity`, `formatIdentityLine` |
| `src/lib/preview-annotate/in-page.test.ts` | Tests: annotateInPage overlay; installs a host and tears it down completely; numbers the markers for stacked pins; keeps a pin glued to its element after the element moves |
| `src/lib/preview-annotate/in-page.ts` | Guest-page comment overlay. Injected as source into the preview webview — no imports, no module constants, every value the body needs lives inside `annotateInPage`. Same contract as `watchInPage`. pointer-events on the… |
| `src/lib/preview-annotate/index.ts` | TypeScript source: `index` |
| `src/lib/preview-annotate/pack.test.ts` | Tests: packageAnnotatePin; carries the selector, markup, and computed styles the agent needs to find the source; keeps the target line prose while the DOM detail rides its own labelled lines; packs a numbered crop, comp… |
| `src/lib/preview-annotate/pack.ts` | Exports `ComposerReadyAnnotation`, `packageAnnotatePin`, `packageAnnotateStack`, `annotateFlushPrompt`, `dataUrlToBlob`, `dataUrlToFile` |
| `src/lib/preview-annotate/stack.test.ts` | Tests: annotate pin stack; numbers click and area pins 1..N as they accumulate; keeps numbers stable when a pin is removed; updates a note without sending anything |
| `src/lib/preview-annotate/stack.ts` | Numbered pin stack for comment mode. Saving a pin only appends — it never sends a turn. Numbers are assigned 1..N in add order and stay put if a pin is removed, so Comment 3 in the composer still matches marker 3 on the… |
| `src/lib/preview-annotate/tokens.ts` | Visual tokens for in-app browser comment mode. Drawn onto the GUEST page, which does not load our CSS variables, so these are real colors — the same reason the agent overlay uses a hex. Codex's comment chrome is a desig… |
| `src/lib/preview-external.ts` | Admission for URLs handed up by the preview guest preload (electron/preview-guest-preload.ts, `preview-open-external` channel). A guest page chose this URL, not the user typing it, so the scheme set is |
| `src/lib/preview-markdown-links.test.ts` | @vitest-environment jsdom |
| `src/lib/preview-markdown-links.ts` | Where a click in the desktop markdown preview goes. Electron denies every `target=_blank` / `window.open` (GHSA-9f4c-93c8-jc8g), so a web link has to travel through `ExternalLink` like chat links do. A `#fragment` href… |
| `src/lib/preview-reach.test.ts` | Tests: reachablePreviewUrl; leaves a local gateway alone without touching the bridge; asks main to resolve the URL on a remote gateway; passes the original through when main cannot reach it |
| `src/lib/preview-reach.ts` | Make a URL loadable from THIS machine before the pane tries it. Against a remote gateway the agent's `localhost:5173` names the gateway's loopback, not ours. Main owns the answer — it knows whether an SSH transport is b… |
| `src/lib/preview-targets.test.ts` | Tests: previewName; preview target detection; does not infer preview targets from raw paths or URLs; decodes preview markdown hrefs |
| `src/lib/preview-targets.ts` | Exports `stripPreviewTargets`, `extractPreviewTargets`, `previewMarkdownHref`, `previewTargetFromMarkdownHref`, `previewName`, `previewArtifactKey` … |
| `src/lib/profile-color.ts` | Deterministic per-profile color so a profile is glanceable across the app (the sidebar profile rail). The default/root profile has no color — named profiles get a stable hue derived from the name, so the same profile al… |
| `src/lib/profile-order.ts` | User-defined rail order for named profile squares. Names absent from the order alphabetise at the tail. Pure so both the active strip and the at-rest fleet groups sort identically without pulling stores into fleet-rail. |
| `src/lib/profile-short-label.ts` | Exports `profileShortLabel` |
| `src/lib/project-idea-templates.ts` | Fun starter ideas for the new-project dialog. Pills prefill IDEA.md; the set shown is a random handful from this pool (reshuffled on open / via the dice), so creating a project always feels a little playful. Pure conten… |
| `src/lib/provider-limit.test.ts` | Tests: provider limits; reports an account-wide limit until its reset, then clears without a refetch; tags only the cooled-down models, each until its own reset; leads with the usage window closest to the wall and drops… |
| `src/lib/provider-limit.ts` | Exports `providerLimit`, `accountResetMs`, `modelResetMs`, `USAGE_NOTICE_PERCENT`, `USAGE_WARN_PERCENT`, `UsageWindowView` … |
| `src/lib/provider-setup-errors.test.ts` | Tests: isProviderSetupErrorMessage; matches generic missing-provider copy; matches what agent init actually says on a blank install; matches an explicit provider that has no credentials |
| `src/lib/provider-setup-errors.ts` | Fallback for gateways that send no `code` on the error event. Every alternative here is a sentence the backend actually produces today: `agent_init` raises "No LLM provider configured" on a blank install and `missing_pr… |
| `src/lib/query-client.test.ts` | Tests: invalidateProfileScopedQueries; invalidates profile-scoped caches and leaves account/global caches intact; invalidates unknown/non-string-rooted keys by default (correctness-safe); keepWarmNousRow |
| `src/lib/query-client.ts` | Shared React Query client. Lives in its own module (not main.tsx) so non-React code — e.g. the profile store on a gateway swap — can invalidate cached, profile-scoped settings without importing the app entry point. |
| `src/lib/quick-entry-submission.test.ts` | Tests: captureQuickEntryRequest; freezes the request identity before an await can observe caller mutations; validateQuickEntryAcceptance; rejects an empty object as backend evidence |
| `src/lib/quick-entry-submission.ts` | Exports `QuickEntryAcceptedPromptStatus`, `QuickEntryRequestIdentity`, `CapturedQuickEntryRequest`, `QuickEntryBackendPromptResult`, `QuickEntryBackendResultEvidence`, `QuickEntryAcceptedIdentity` … |
| `src/lib/raf-coalesce.ts` | Coalesce a stream of values (pointermove positions, resize deltas) to one `apply` per animation frame, so a drag can't drive several layouts per frame. `push` records the latest value and schedules a frame; `finish` com… |
| `src/lib/reasoning-blocks.test.ts` | Tests: separateGluedReasoningBlocks; splits heading-onto-heading parts (the ; splits prose-onto-heading parts (vercel/ai#6742 repro); is idempotent on already-separated text |
| `src/lib/reasoning-blocks.ts` | Reasoning-summary models (OpenAI's gpt-5.x family, and anything relaying the Responses API onto the OpenAI chat wire) emit one delta per *completed* summary part, each opening with a bold markdown heading: **Investigati… |
| `src/lib/reasoning-effort.test.ts` | Tests: reasoning-effort; labels every level it claims to support; labels a route clamp from the gateway wire level only, never by inference; treats empty as inherit and only |
| `src/lib/reasoning-effort.ts` | Compact labels for chrome where space is tight (pill, picker rows). Menus and settings use the translated `shell.modelOptions` strings instead. |
| `src/lib/reasoning-slash.test.ts` | `/reasoning hide` typed into the Desktop composer must gate Thinking blocks in the transcript immediately (#111761, #49664): the renderer mirrors the gateway's `config.set key=reasoning` answer instead of waiting for th… |
| `src/lib/reasoning-slash.ts` | `/reasoning` typed into the composer — the Ink TUI's path (ui-tui/src/app/slash/commands/session.ts). The gateway's `config.set key=reasoning` handles both the display words (show/hide/full/clamp) and the |
| `src/lib/reasoning-step.test.ts` | Tests: stepReasoningEffort; steps up and down through off and the normal levels, clamping at both ends; never steps into the expensive tiers (max/ultra stay behind the menu); resolves an unset or stale value through the… |
| `src/lib/reasoning-step.ts` | The level ladder a shortcut steps through: thinking off, then the normal levels in ascending order. `max`/`ultra` are deliberately absent — they are expensive tiers kept behind an explicit menu pick, so stepping must no… |
| `src/lib/remark-soft-breaks.test.ts` | Tests: remarkSoftBreaks; turns single newlines in prose into line breaks; leaves code and math nodes untouched; splits text nested inside emphasis |
| `src/lib/remark-soft-breaks.ts` | Exports `MdastNode`, `remarkSoftBreaks` |
| `src/lib/remote-url.test.ts` | Tests: coerceRemoteUrlScheme; prepends http:// to scheme-less host:port input; leaves explicitly schemed URLs alone; trims and passes through empty input |
| `src/lib/remote-url.ts` | remote-url.ts Renderer-side twin of the scheme coercion in electron/connection-config.ts `normalizeRemoteBaseUrl()`. Users routinely paste scheme-less "host:port" (a Tailscale IP, a LAN hostname) into the remote-gateway… |
| `src/lib/render-weight.test.ts` | Tests: messageStoreWeight; charges large text and tool results by character cost, not only part count; prices a 51KB tool output well above a plain exchange; handles circular tool payloads without recursing forever |
| `src/lib/render-weight.ts` | Render cost of one message's content parts, in budget units. Two layers bound long transcripts and both spend the same currency: the store window (how many messages reach assistant-ui at all) and the DOM page budget (ho… |
| `src/lib/renderer-loop-pause.test.ts` | Tests: installRendererAnimationPauseState; keeps visible animations running across blur and focus, and cleans up its root state |
| `src/lib/renderer-loop-pause.ts` | Exports `RENDERER_ANIMATIONS_PAUSED_ATTRIBUTE`, `createRendererLoopPauseController`, `installRendererAnimationPauseState` |
| `src/lib/reorder.ts` | THE reorder feel — one primitive for every horizontal drag-to-reorder strip (profile rail squares, pane tab chips, and whatever comes next). Reorder surfaces must read identically: - the dragged item GLIDES BETWEEN SNAP… |
| `src/lib/replay-gap-owner.test.ts` | Tests: eventSourceMatchesOwner; matches an exact route only from its own connection, and a bare profile only from the untagged primary |
| `src/lib/replay-gap-owner.ts` | Normalized source tags of a gateway event: the registry connection whose socket delivered it ('' for the untagged local primary) and its profile. |
| `src/lib/runtime-readiness.test.ts` | Tests: interpretRuntimeReadiness; prefers runtime_check when both signals exist; surfaces runtime mismatch details when runtime_check fails; falls back to setup.status when runtime_check has no boolean result |
| `src/lib/runtime-readiness.ts` | Exports `SetupStatusSnapshot`, `RuntimeCheckSnapshot`, `RuntimeReadinessSignals`, `RuntimeReadinessOptions`, `RuntimeReadinessResult`, `RuntimeReadinessDisplay` … |
| `src/lib/sanitize.test.ts` | Tests: gitRef; turns spaces into hyphens and keeps slashes; drops chars git refs forbid and collapses separators; strips a leading separator but stays typeable (keeps a trailing one) |
| `src/lib/sanitize.ts` | Format enforcers for identifier-style inputs, applied live (per keystroke) via <SanitizedInput>. They're intentionally lenient on a trailing separator so a value stays typeable (e.g. "feat/" then keep going); the final… |
| `src/lib/selectable-card.ts` | Exports `SelectableCardState`, `selectableCardClass` |
| `src/lib/selection-copy-colors.test.ts` | Tests: textColorLuma; scores white near the top of the range; scores black near the bottom of the range; composites partial alpha over mid-gray |
| `src/lib/selection-copy-colors.ts` | Chromium's native selection copy (Cmd+C, right-click Copy) serializes the selection as `text/html` with every element's COMPUTED paint inlined as style attributes. Copied from a dark theme, body text lands on the |
| `src/lib/session-branch-tree.test.ts` | Tests: forkParentId; returns undefined for /new and idle/daily reset lineage; returns the branch parent for a genuine /branch fork; falls back to parent_session_id for legacy/optimistic forks without the marker |
| `src/lib/session-branch-tree.ts` | Exports `SidebarSessionEntry`, `FlattenSessionsOptions`, `forkParentId`, `flattenSessionsWithBranches` |
| `src/lib/session-date-groups.test.ts` | Tests: groupEntriesByRecency; limits complete Updated groups without splitting bursts or branch clusters; cuts the head after the most recent handful, then divides by coarse ranges; labels the rest of the current day |
| `src/lib/session-date-groups.ts` | A flat list row is either a divider or a session entry. Interleaving these lets the flat list (and the virtualizer) render separators inline without a second layer of nesting. A divider either names a calendar bucket (r… |
| `src/lib/session-export.ts` | Exports `exportSession` |
| `src/lib/session-ids.test.ts` | Tests: storedSessionIdForNotification; translates a runtime id back to its stored id; returns the id unchanged when no mapping is known; returns the id unchanged for an empty map |
| `src/lib/session-ids.ts` | The gateway tags every event — and therefore every native notification — with the *runtime* session id (the key under which the session lives in the gateway's in-memory `_sessions` map). The chat route, however, is keye… |
| `src/lib/session-link-title.test.ts` | Tests: lookupLocalSessionTitle; reads from the in-memory session list; matches the lineage root so a compressed chat still resolves; ignores a same-id row owned by another profile |
| `src/lib/session-link-title.ts` | Resolves ` |
| `src/lib/session-owner-routed-rpcs.test.tsx` | Every Desktop RPC that carries a session_id must reach the backend that OWNS that session. On a multiplexed local gateway the window's ambient socket is the launch profile's authority, which refuses a secondary profile'… |
| `src/lib/session-owner-stamp.ts` | THE canonical write path for tagging backend-returned session rows with the registry connection that owns them (the read counterpart is `sessionOwnerRouteFromRow` in store/session-request-router). Every other `connectio… |
| `src/lib/session-project-label.ts` | The PROJECT a session belongs to, as a label for the sidebar card. Resolution order: 1. `liveSessionProjectId` — the same resolver the session COLOR reads, so an explicitly-projected row's name and its inherited tint al… |
| `src/lib/session-refs.test.ts` | Tests: parseSessionRefValue; splits profile and session id; treats bare values as session ids; sessionRefFallbackLabel |
| `src/lib/session-refs.ts` | Pure helpers for ` |
| `src/lib/session-row-slots.ts` | Session-row decoration surface — the seams a plugin can decorate a sidebar session row through, with the SAME registry schema as every other surface (statusbar, composer, panes): render areas (`data`): sessionRow.leadin… |
| `src/lib/session-search.test.ts` | Tests: sessionMatchesSearch; matches loaded sessions by full and partial session id; matches projected compression sessions by lineage root id; preserves title, preview, and workspace matching |
| `src/lib/session-search.ts` | Exports `sessionMatchesSearch` |
| `src/lib/session-signatures.test.ts` | Tests: sameCronSignature; is false when the lengths differ; is true when ids and titles match in order; is false when a title changed |
| `src/lib/session-signatures.ts` | Cheap signature compares for poll loops — swap the atom (and re-render) only when the rows/transcript actually changed. |
| `src/lib/session-source.test.ts` | Regression guard for #46761 / PR #47395: Photon (iMessage) must keep its own sidebar section. refreshMessagingSessions() filters rows through isMessagingSource(), so this entry is the sole condition that keeps Photon |
| `src/lib/session-source.ts` | Exports `LOCAL_SESSION_SOURCE_IDS`, `MESSAGING_SESSION_SOURCE_IDS`, `isMessagingSource`, `normalizeSessionSource`, `handoffOriginSource`, `sessionSourceLabel` … |
| `src/lib/session-timer-since.test.ts` | Tests: resolveSessionTimerSince; uses the primary focus stamp while the primary surface is focused; uses the tile focus stamp instead of any other clock (#103123); hides the timer when the tile stamp belongs to a differ… |
| `src/lib/session-timer-since.ts` | Statusbar timer contract (#103123): both surfaces show "focused since". Primary stamps `$sessionStartedAt` on every switch; tiles used to read the row's durable `started_at`, so a day-old tile jumped to 23:03:00. The it… |
| `src/lib/shared-gateway-restart.test.ts` | Tests: sharedGatewayProfiles; lists every bot the shared multiplexer carries, default first, when the profile is served; keeps the plain restart for standalone gateways and older backends |
| `src/lib/shared-gateway-restart.ts` | Profiles a gateway restart would blip when the polled profile is carried by the shared multiplexer, in display order (default first, then as recorded). `null` for a standalone gateway or an older backend that does not r… |
| `src/lib/sibling-ws-url.test.ts` | A sibling stream (voice PCM, Bot Screen RFB) must dial the SAME (connection, profile) backend chat uses. The bare v1 getConnection pair answers for the local primary — the wrong machine when a registry remote rides over… |
| `src/lib/sibling-ws-url.ts` | Sibling WebSocket URLs beside `/api/ws` for a (connection, profile) route. Some gateway streams are not JSON-RPC and cannot share the gateway socket: voice PCM (`/api/audio/speak-stream`) and the Bot Screen's raw RFB (`… |
| `src/lib/signed-out-status.ts` | Whether an `/api/status` answer is the trimmed body the gateway's Webapp gives a caller it does not count as signed in. `/api/status` is public, so the gate never refreshes on it: a signed-in tab whose access token expi… |
| `src/lib/slash-completion-cache.ts` | Root for every cached `/` completion response — the bare-slash catalog and each typed query. Not in PROFILE_INDEPENDENT_QUERY_ROOTS, so a profile or gateway switch drops it with the rest of the profile-scoped cache. |
| `src/lib/speech-text.identifier-corpus.test.ts` | The shared corpus both speech normalizers must agree on (#119207): the identical file is loaded by tests/tools/test_tts_identifier_speech.py, so the desktop (speech-text.ts) and gateway/CLI (tts_text_normalize.py) |
| `src/lib/speech-text.test.ts` | Tests: sanitizeTextForSpeech; does not speak placeholders for fenced code blocks; still keeps normal prose and inline code readable; reads the table header, not its data, between surrounding human text |
| `src/lib/speech-text.ts` | Exports `cutSentences`, `IncrementalSpeechSentenceBuffer`, `sanitizeTextForSpeech` |
| `src/lib/spoken-reply.test.ts` | Tests: isLiveTailReplyId; matches renderer stream and inflight ids only; assistantReplyOrdinal; counts visible assistant bubbles and skips hidden ones |
| `src/lib/spoken-reply.ts` | Spoken-reply identity for Desktop auto-speak / Read Aloud. The live assistant row id (`assistant-stream-*`, `inflight-assistant-*`) is not stable: hydrate rewrites that row under its durable backend id. Keying "already… |
| `src/lib/stable-array.ts` | Keep `prev`'s reference when it's element-equal to `next`, so a nanostores `computed` (notifies on `!==`) skips the emit when its projected list didn't actually change — e.g. status-id sets recomputed on every stream de… |
| `src/lib/statusbar.test.ts` | Tests: statusbar usage readouts; paints the backend cache-hit and throughput fields, and stays blank when they are absent |
| `src/lib/statusbar.tsx` | Exports `formatDuration`, `compactPath`, `contextBar`, `usageContextLabel`, `contextBarLabel`, `cacheHitLabel` … |
| `src/lib/steered-turn-hydration-order.test.ts` | Reload parity for a steered turn: the durable rows a redirect persists (pre-steer assistant narration + tool rows → interrupted-checkpoint row → the user's correction → post-steer continuation with its own tools) must |
| `src/lib/storage.test.ts` | Tests: string array storage; removes the key for an empty array; persists non-empty arrays |
| `src/lib/storage.ts` | ── Persistence choke point ───────────────────────────────────────────────── Every persisted read/write in the app funnels through readKey/writeKey, so a single subscriber (telemetry, cross-window sync, an audit log) ca… |
| `src/lib/stt-lease.test.ts` | Tests: syncSttLease; acquires on the first on and releases on off; skips an initial off — never releases a lease it did not hold; sends every settled-apart acquire — the backend, not a client clock, knows residency |
| `src/lib/stt-lease.ts` | The desktop's voice-input sessions — push-to-talk dictation and the voice conversation loop — are the user telling us STT is about to be needed (or no longer is). The backend turns that into engine lifecycle: acquiring… |
| `src/lib/summarize-command.test.ts` | Tests: summarizeShellCommand; strips a leading cd and trailing tail + status echo; keeps flags on the surviving command; drops a source/activate prefix |
| `src/lib/summarize-command.ts` | Adapted from condensed-milk-pi's command dispatcher: split compounds first, strip pipe tails (`\| head`, `\| tail`, ...), then clean redirects/env prefixes before deciding which segment is meaningful. This is display-on… |
| `src/lib/svg-image-inline-cap.test.ts` | Real mermaid 11.16 output shape for an oversized diagram: width="100%" plus an inline max-width that pins the intrinsic width in pixels. |
| `src/lib/svg-image.test.ts` | Real mermaid 11.16 render output shape (verified against the installed package): width="100%" + inline style="max-width: Npx" + viewBox. |
| `src/lib/svg-image.ts` | Rasterise an SVG string to PNG and copy it to the clipboard. Self-contained SVGs only (inline styles) — mermaid output qualifies. Falls back to copying the SVG markup as text where image clipboard writes aren't permitte… |
| `src/lib/text.ts` | Canonical text micro-helpers. Do not redefine these per-page. |
| `src/lib/thinking-sound.test.ts` | Tests: thinking-sound; plays repeating blips while active and stops instantly; respects the voice.thinking_sound config gate; stays silent while sounds are muted but keeps the loop alive |
| `src/lib/thinking-sound.ts` | Ambient "thinking" sound for the desktop voice conversation. While the agent works (status === 'thinking') no audio flows, which reads as "it died" during long thinking/tool stretches. A calm, quiet, repeating pair of s… |
| `src/lib/time.test.ts` | Tests: formatAgo; reads ; buckets to the coarsest unit, floored; clamps future timestamps to |
| `src/lib/time.ts` | Canonical time/date formatting. Shared `Intl` instances (created once, not per-render) + relative-time helpers. Every surface that shows a timestamp or an age pulls from here so the rendered strings stay consistent app-… |
| `src/lib/tips/anchor.ts` | Where a tip can actually point right now. A tip has no spotlight and no scrim, so a bubble anchored to something the user cannot see is not a dimmed step — it is an arrow into empty space. The anchor is therefore re-res… |
| `src/lib/tips/catalog.ts` | THE TIP CATALOG — what the app tells you about itself when it's quiet. Data only. A tip is an id, somewhere to point, and (optionally) the keybind whose CURRENT combo the bubble prints. The words live in i18n under `tip… |
| `src/lib/tips/local-cta.test.ts` | The local campaign tips' reshow clock. |
| `src/lib/tips/local-cta.ts` | Reshow clock for the local-models campaign tips in the rotation (today: the engine update). A tip ignored (timed out) may return, but on a much longer clock than the rotation's: it is the same message twice, not a tour… |
| `src/lib/tips/rotation.test.ts` | The walk is one lap: a tip that has already been on screen — closed by the timer, not only by the ✕ — is never offered again, and once every tip has had its moment the rotation is spent rather than starting the tour ove… |
| `src/lib/tips/rotation.ts` | Which tip comes next. The catalog is a ring and the rotation walks it in order, resuming from whichever tip was last shown. Order and not shuffle: the catalog reads as a tour of the app — the rail down the left, then th… |
| `src/lib/todos.test.ts` | Tests: todoTree; orders parents before children with depths; degrades dangling and self parents to roots; keeps cycle members instead of dropping them |
| `src/lib/todos.ts` | Exports `TodoStatus`, `TodoItem`, `TodoPatch`, `isTodoToolName`, `parseTodos`, `todoTree` … |
| `src/lib/tool-media-renderers.test.ts` | Tests: findProducingToolCall; picks the earliest call whose result names the path (a later ls or a plugin reading it only mentions it); matches whole paths only: a longer sibling file never claims this one; reads every… |
| `src/lib/tool-media-renderers.ts` | TOOL MEDIA RENDERERS — a plugin draws the media ITS OWN tools produced. When a transcript shows a `MEDIA:` attachment, the host finds the tool call whose result first named the path (earlier in the transcript). If the p… |
| `src/lib/tool-render-class.ts` | Which surface a tool call renders as. Two consumers have to agree on this and they sit on opposite sides of the app: the transcript decides what to draw, and the DOM render budget decides how much of the transcript to m… |
| `src/lib/tool-result-metadata.ts` | Gateway display hints are not the tool's result. Keep them off the raw payload so summaries cannot overwrite evidence, including false/null/"". |
| `src/lib/tool-result-summary.test.ts` | Tests: formatToolResultSummary; unwraps wrapper payloads into structured key-value lines; summarizes object arrays as readable list items; truncates long field values for compact display |
| `src/lib/tool-result-summary.ts` | Heuristic JSON → human summary for tool results. Default view; technical mode still gets the raw JSON section. |
| `src/lib/tool-run-continuity.test.ts` | Tests: tool run segmentation survives rehydration; run identity; keeps the first tool call at the head as the run grows; breaks a run on any non-tool part |
| `src/lib/touch-interaction.test.ts` | Tests: touch input ownership in the browser-hosted Desktop; uses coarse capability only when the event has no input evidence; recognizes touch and pen on a hybrid device; turns the touch layout on for a coarse-pointer t… |
| `src/lib/touch-interaction.ts` | Exports `TOUCH_POINTER_QUERY`, `isBrowserOwnedTouch`, `isTouchInteraction` |
| `src/lib/tour/app-tour.css` | Hermes surface treatment for the APP surface's tour popovers. driver.js ships a fixed light palette, a heavy drop shadow, and 19px/14px type — none of which is how this app draws a floating popover. Repaint it with the… |
| `src/lib/tour/collect-targets.ts` | TOUR TARGET COLLECTOR — discovers what a tour can point at. Fully generic: works on ANY document (the Hermes app's own DOM or an arbitrary page in the preview webview) by scanning for the things that make an element add… |
| `src/lib/tour/engine.test.ts` | A recording fake of the driver.js surface the engine touches. |
| `src/lib/tour/engine.ts` | TOUR ENGINE — the one function that runs a tour action, on BOTH surfaces. The app surface calls it directly (imported driver.js factory + a module holder + `document`). The preview surface injects `runTourEngine.toStrin… |
| `src/lib/tour/index.ts` | TOURS — highlight-and-narrate walkthroughs for any surface. Two consumers, one engine: - The `tour` agent tool, via the gateway (see run-tour.ts). - Your own curated tours, via this module: ```ts import { startTour, sho… |
| `src/lib/tour/run-tour.ts` | RUN TOUR — the tour verbs, on either surface. `runTour` is the generic entry (one normalized action in, a result out) and the named verbs below are the ergonomic API — used by the agent tool through the gateway, and by… |
| `src/lib/tour/spotlight-blur.ts` | SPOTLIGHT BLUR — a blurred scrim that keeps the highlighted element crisp. driver.js paints its scrim as ONE full-viewport <svg> whose fill path has the spotlight punched out. A `backdrop-filter` on that element blurs t… |
| `src/lib/tour/tour-active.ts` | Reactive twin of `isTourActive` for UI that must wait out a tour. Lives apart from run-tour.ts, which is dynamic-imported to keep driver.js off the boot path. |
| `src/lib/trackpad-gestures.ts` | Trackpad / pointer gesture primitives shared across canvas + DOM surfaces. macOS quirk (Chromium/Electron): both pinch-zoom and "smart zoom" arrive as `wheel` events with `ctrlKey` synthetically set — there is no dedica… |
| `src/lib/transcript-directives.test.ts` | Tests: segmentTranscriptDirectives; parses a bare directive with no attributes; parses multiple attributes and accepts single quotes; lowercases attribute keys but preserves values |
| `src/lib/transcript-directives.ts` | TRANSCRIPT DIRECTIVES — the transcript as a contribution area. A plugin registers a named directive; the model addresses it by emitting a paragraph of the form `::name{key="value"}` and that leaf renders as the plugin's… |
| `src/lib/transcript-occurrences.test.ts` | Tests: hydrates repeated tool-round commentary but folds the stop-row echo; recovers only the uncommitted journal suffix until the complete reply becomes durable |
| `src/lib/transparent-windows.ts` | The `?win=` kinds whose Electron window is `transparent: true` and so paints nothing but its own surface over the user's desktop. `secondary` (a session window) and `browser` are ordinary opaque windows and are delibera… |
| `src/lib/tts-lease.test.ts` | Tests: syncTtsLease; acquires on the first on and releases on off; skips an initial off — never releases a lease it did not hold; dedupes a repeat of the last sent state |
| `src/lib/tts-lease.ts` | The desktop's speech-output toggles — "Read replies aloud" and voice conversation mode — are the user telling us TTS is about to be needed (or no longer is). The backend turns that into engine lifecycle: acquiring a lea… |
| `src/lib/turn-done-notification-body.test.ts` | Mirrors the minified 0.20.0 Studio bundle helper quoted in #88488: Xn(n?.content \|\| e.title \|\| "Message complete.", 140) That chain lived in the released dist/client bundle, not this repo's |
| `src/lib/turn-done-notification-body.ts` | Native turn-done notification body (#88488). Prefer the assistant reply. If that text is missing, use a generic completion phrase — never the session title (usually the user's first |
| `src/lib/ui-preferences/boot.test.ts` | Tests: no store module evaluates before the machine store hydrated, so its next write keeps the host’s values |
| `src/lib/ui-preferences/boot.ts` | Runs BEFORE the app's module graph (see src/entry.ts): the localStorage cache must match this machine's shared preferences before any store module reads it, or a plain-atom store keeps a stale value and its next write c… |
| `src/lib/ui-preferences/guidance-sync.test.ts` | Tests: onboarding skipped and tips seen or dismissed in one browser stay so in another (#145600) |
| `src/lib/ui-preferences/keys.ts` | Which persisted keys are machine-level UI preferences (#145213). Only these leave localStorage for the machine's shared store, so native Desktop and every browser that opens this machine's Webapp show the same choices.… |
| `src/lib/ui-preferences/merge.ts` | A store that reads its value once (a plain atom such as the favorite models) keeps what it read when a newer machine value lands later (a first snapshot past the boot bound, another window's change), and its next edit c… |
| `src/lib/ui-preferences/outbox.ts` | Local changes not yet confirmed by the machine's store, kept across reloads: a change made right before the tab reloads or closes must still win over the older store value on the next load, and be written then. One outb… |
| `src/lib/ui-preferences/sync-concurrent.test.ts` | Tests: a favorite another client removed stays removed when a tab that still lists it stars another; an offline star carried over a reload or a takeover joins the favorites native added meanwhile; a frozen tab whose uns… |
| `src/lib/ui-preferences/sync-defaults.test.ts` | Tests: a fresh browser’s translucency default never replaces native’s custom translucency; a fresh browser’s auto-speak migration never replaces native’s choice, across a browser reload too; a migrated auto-speak value… |
| `src/lib/ui-preferences/sync-handoff.test.ts` | Hand-offs between clients and page loads, against the real native writer on a real file (#145536 re-review): an upgraded browser's old defaults, a closed tab's unsent edit, a first snapshot that lands after the app read… |
| `src/lib/ui-preferences/sync-store.test.ts` | Tests: a store a fresh client created never removes another client’s values: it imports them; a corrupt store is kept aside and open windows follow its replacement, re-importing what it lost; same-origin tabs keep each… |
| `src/lib/ui-preferences/sync.test.ts` | A bridge over an in-memory document with the store's semantics: per-key merge, null deletes, `seed` only adds the keys the store lacks. |
| `src/lib/ui-preferences/sync.ts` | Exports `UiPreferencesBridge`, `captureOwnPreferences`, `hydrateFromSnapshot`, `startUiPreferencesSync` |
| `src/lib/update-copy.test.ts` | Tests: resolveUpdateCopy; client target with commits: client title + client body; backend target with commits: names the backend in title and body; no changelog (pip/non-git backend): degrades honestly, still names back… |
| `src/lib/update-copy.ts` | Pure copy-selection for the updates overlay's "available" state. Names the update target (client vs the connected backend in remote mode) and degrades honestly when there's no commit changelog to show (e.g. a pip / non-… |
| `src/lib/update-notes.test.ts` | Tests: update notes; summarizes a release as its highlight headlines, and falls back to the first bullet list; lists the newest merged PRs, pinned to the update when its commit list is complete |
| `src/lib/update-notes.ts` | "What's in this update" for the updates overlay, read from public GitHub. Stable channel: the release's own notes (Highlights headlines, else its first bullet list). Main: the newest merged PR titles. Both are best-effo… |
| `src/lib/usage-percent.test.ts` | Tests: formatPercentUsed; floors, shows <1% for any sliver, and 100% only when exhausted |
| `src/lib/usage-percent.ts` | Whole-percent used for a usage-window allowance. Same rule as the portal (`formatUsedPercentLabel`) and the CLI (`format_percent_used`): floor, any sliver reads `<1%` (never `0%`), and `100%` only once it is actually ex… |
| `src/lib/use-enter-animation.test.tsx` | Tests: useEnterAnimation; plays once on mount; stays out of the way when disabled; does not replay for a key that already animated |
| `src/lib/use-enter-animation.ts` | One-shot enter animation via the Web Animations API. Returns a callback ref. The animation fires exactly once when the element first attaches to the DOM and never replays for an already-mounted node — this is deliberate… |
| `src/lib/use-session-slice.ts` | Exports `useSessionSlice`, `useStoreSelector`, `useStoresSelector` |
| `src/lib/use-stores-selector.test.tsx` | `useStoresSelector` — the multi-store form of `useStoreSelector`. It exists because subscribing to one store while the selector reads another looks correct for exactly as long as the subscribed store happens to churn on… |
| `src/lib/utils.ts` | Exports `cn` |
| `src/lib/version-label.test.ts` | Tests: shortVersion; keeps the distance past the release and drops the commit |
| `src/lib/version-label.ts` | The one short form every surface names a version by: `<release>+<distance>` (`0.21.5+1913`), matching `hermes --version` minus its commit. The commit (`.g<sha>`, `.dirty`) is build metadata the expanded version details… |
| `src/lib/version-status.test.ts` | Tests: resolveVersionStatus; labels a current local client with its distance, keeping the commit for the tooltip; appends the commit diff when the client is behind; shows a count-free update hint when the client count i… |
| `src/lib/version-status.ts` | Pure derivation of how the app names an update target: the label (`v0.4.2`, `backend v0.4.2 (+12)`, `v0.4.2 · update`), its tooltip, and whether an update is waiting. The statusbar and the command palette both name the… |
| `src/lib/voice-barge-in.test.ts` | Tests: monitorSpeechDuringPlayback — voice.barge_in_threshold_multiplier (#117801); a quiet headset cannot interrupt playback at the stock sensitivity; a lower configured multiplier lets the same headset interrupt playb… |
| `src/lib/voice-barge-in.ts` | Full-duplex VAD monitor: watch the mic across the agent turn — while the model is generating (no audio yet) AND while TTS plays — fire the moment the user talks over either phase, and CAPTURE what they say. Detection al… |
| `src/lib/voice-client-direct.test.ts` | Tests: fetchVoiceClientConfig; fetches from /api/audio/voice-config with the ambient scope and caches per scope; a scope switch never reuses another scope; resolves null on an older backend without the endpoint |
| `src/lib/voice-client-direct.ts` | Client-direct voice: call the active profile's STT/TTS providers straight from the desktop, cutting the audio relay hop through the gateway. The gateway stays the single source of truth for WHICH provider and WHICH cred… |
| `src/lib/voice-live.routing.test.ts` | A GPT-Live session is created on the chat OWNER's (connection, profile) — the Bot that owns the chat — never on the window's active scope, mirroring the TTS legs (#117014): two Bots with different voices configured must… |
| `src/lib/voice-live.ts` | GPT-Live voice chat: the full-duplex voice frontend that DELEGATES to Hermes. `voice.voice_chat_mode: gpt-live` swaps the chained mic → STT → turn → TTS loop for one OpenAI voice model (`gpt-live-1`) that listens and sp… |
| `src/lib/voice-microphone-unsupported.test.ts` | A Webapp opened over plain HTTP from another machine has no navigator.mediaDevices; nor has jsdom. |
| `src/lib/voice-playback.routing.test.ts` | The speak-stream WebSocket must dial the ACTIVE (connection, profile) backend — the same one chat and every REST audio call use. Before this contract was pinned it resolved through the bare v1 getConnection path, |
| `src/lib/voice-playback.same-turn.test.ts` | Tests: playSpeechText same-turn start; does not stop an in-flight play when a second start is the same turn; still replaces playback when the next start is a different turn; does not let the idle notification from its o… |
| `src/lib/voice-playback.test.ts` | Teardown contract for voice-playback (#91991): a barge-in (stopVoicePlayback) must drain EVERY live playback — streaming sessions (WebSocket + AudioContext) and data-URL audio elements — and a settled session must never… |
| `src/lib/voice-playback.ts` | Exports `VoicePlaybackOptions`, `stopVoicePlayback`, `resolveSpeakStreamUrl`, `SpeechStreamSession`, `startSpeechStream`, `playSpeechText` … |
| `src/lib/voice-stop-word.test.ts` | Tests: isVoiceStopCommand; matches bare stop commands; matches multi-word stop phrases; matches stop commands addressed to Hermes |
| `src/lib/voice-stop-word.ts` | Spoken stop-word detection for the voice conversation loop. When someone is in a hands-free "Hey Hermes" voice chat, the natural way to end it is to SAY "stop" — not reach for the mouse. Without this, a spoken |
| `src/lib/voice-stream.ts` | Live dictation STT: mic PCM streams to the host's `/api/audio/transcribe-stream` WebSocket WHILE the user speaks; partial text arrives as it is recognized and the transcript lands right at end of recording (server contr… |
| `src/lib/voice-tts-echo.test.ts` | Mirrors tests/tools/test_voice_tts_echo_guard.py::TestIsTtsEcho so the desktop guard and the CLI guard agree on what counts as echo. |
| `src/lib/voice-tts-echo.ts` | TTS self-echo guard for the voice-conversation barge monitor — a port of tools/voice_mode_transcript.is_tts_echo (the CLI's fix for the TTS -> STT -> TTS loop). Over speakers, Hermes' own reply bleeds into the |
| `src/lib/wake-client-capture.test.ts` | Regression test for #119089: macOS Desktop remote-gateway client capture went permanently deaf (platform capture error kills the continuous PCM chain) while the ear still showed "listening" and no error ever surfaced. |
| `src/lib/wake-client-capture.ts` | Client-side mic capture for remote wake word. When the backend arms with `capture: "client"`, PortAudio runs on a headless VM with no mic. The desktop opens getUserMedia here, resamples to 16 kHz mono int16 frames, and… |
| `src/lib/wake-indicator.test.ts` | Tests: wake indicator lifecycle; moves from detection to capture and hides when the wake-started session ends; does not show for a manually started voice conversation |
| `src/lib/wake-indicator.ts` | Exports `WakeIndicatorState`, `WakeIndicatorVoiceStatus`, `activateWakeIndicator`, `syncWakeIndicatorWithVoice`, `clearWakeIndicator` |
| `src/lib/wake-sound.test.ts` | Minimal WebAudio doubles: enough to record that playWakeSound wired oscillators to the destination when it should, and stayed silent when muted. |
| `src/lib/wake-sound.ts` | Wake-word activation chime. A short, bright, rising two-note "ding" that plays the moment "Hey Hermes" is detected, so it's obvious the wake registered before voice capture starts. Deliberately distinct from the |
| `src/lib/with-timeout.test.ts` | Tests: withTimeout; rejects with an onTimeout exception instead of letting it escape the timer callback |
| `src/lib/with-timeout.ts` | Shared budget for any renderer await that rides out a primary backend cold boot (initial getConnection(), the registry restore's descriptor wait). Matches the main-process spawn budget (DEFAULT_BACKEND_READY_TIMEOUT_MS… |
| `src/lib/yolo-session.ts` | Exports `GatewayRequester`, `setSessionYolo`, `setGlobalYolo`, `setYoloEnabled` |
| `src/main.tsx` | Loaded by src/entry.ts once the machine's shared UI preferences hydrated. |
| `src/pairing-scope.test.ts` | Pairing writes must target the profile the user is actually looking at. The approve/revoke endpoints read `profile` off the BODY (a POST body is not touched by query-param scoping), so a request that only carried |
| `src/plugin-socket-scope.test.ts` | pluginSocket must dial the ACTIVE gateway's backend — resolved through the same (connectionId, profile) source of truth ensureGatewayProfile / ensureGatewayAgent maintain for $connection — not the unscoped primary |
| `src/plugins/README.md` | Bundled plugins |
| `src/plugins/hello-runtime/plugin.runtime.js` | Runtime-loaded example — this file is NOT bundled as a module: it ships as raw text (`?raw`) and goes through the real runtime pipeline (specifier rewrite -> SDK/react shim blobs -> blob import -> register). Plain ESM j… |
| `src/plugins/hermes-bots/LICENSE` | Software license text |
| `src/plugins/hermes-bots/avatar-image.test.ts` | Tests: generateAvatarImage (#86161); opts the image.generate RPC out of the socket generic 30 s deadline |
| `src/plugins/hermes-bots/avatar-image.ts` | Image avatars: the device-upload path and the gateway's `image.generate` backend (probe + generation). Kept apart from `avatar.tsx` so the roster's render path doesn't drag the picker's network surface along with it. |
| `src/plugins/hermes-bots/avatar-picker.tsx` | The avatar editor shared by Edit Profile and New Bot: shape grid + color swatches, the Generate and Upload tabs, and the petdex Pet tab. |
| `src/plugins/hermes-bots/avatar.face-clock.test.ts` | The shared face clock: ONE animation loop for every mounted math face. A large roster mounts hundreds of faces, so the clock must not burn frames (or 1Hz whole-document shadow walks) on faces nobody can see. It therefor… |
| `src/plugins/hermes-bots/avatar.test.tsx` | The avatar face: blobatar shape strings, the markup they render to, and the catchlight polarity fix. Shape strings are stored per bot and must round-trip forever — `blobatar[:seed[:kind]]`, where an unlocked seed follow… |
| `src/plugins/hermes-bots/avatar.tsx` | Bot avatars: the shape/color/eyes vocabulary, the deterministic blobatar faces, the shared face clock that animates them, and `BotFace` — the one component every roster row, dialog and tile renders a bot with. Render-on… |
| `src/plugins/hermes-bots/bot-delete.test.ts` | Deleting a bot deletes its Hermes profile, then everything plugin-local that would otherwise leave stale appearance/unread data behind. `host.deleteProfile` is preferred whenever the Desktop build ships it: it routes th… |
| `src/plugins/hermes-bots/bot-open-focus-identity.test.ts` | First-click home bounce (community report, Aug 2026): clicking a bot whose canonical Bot Chat had been COMPRESSED landed on the Bots home instead of the chat, and only a second click got through. Root cause: openRosterB… |
| `src/plugins/hermes-bots/bot-row-opens-canonical-chat.test.ts` | A bot row click lands on the bot's canonical Bot Chat — the session the row previews (`canonical_session`, resolved by name on every roster poll). The regression this pins: a plain click used to front whatever bots-work… |
| `src/plugins/hermes-bots/bot-row.test.tsx` | The bot row's two side effects: pre-warming and opening. Pre-warm is per-row and hover-scoped. Warming the whole roster on paint spun up every profile backend the moment the Bots rail rendered, so the row warms exactly… |
| `src/plugins/hermes-bots/bot-row.tsx` | The two rows the Bots rail lists: one bot, and one group chat. Rows only. Both take their bot or room and their context-menu callbacks as props and own no roster state, so the pane above them decides what to list and th… |
| `src/plugins/hermes-bots/bot-state.focused-owner.test.ts` | The roster highlight and the Routines tile follow the chat the user is LOOKING AT — the focused session's OWNER (profile + connection) — not the gateway socket's home. Tab focus moves without swapping the socket, so key… |
| `src/plugins/hermes-bots/bot-state.ts` | The window-local state Bot Mode's surfaces share: which roster row is selected, which owner's chat is on screen, and the per-bot activity watermarks the unread poll compares against. A leaf by design. The roster, the ro… |
| `src/plugins/hermes-bots/canonical-attachment-download.ts` | Use the existing browser-download -> Electron Save File workflow, not composer staging. Mirrors downloadTextFile and #104199's attachment delivery without a new native IPC. |
| `src/plugins/hermes-bots/canonical-chat-adopt-on-conflict.test.ts` | ADOPT-BEFORE-MINT (#92473 part 2). Between the registry miss and our eager `session.title` write, another writer can take the canonical title (peer dm minting server-side, a second machine, cross-connection sync). UNIQU… |
| `src/plugins/hermes-bots/canonical-chat-creation.test.ts` | Minting a bot's forever-chat. `session.create` is lazy: the stored row does not exist until something writes to it. Creation therefore materializes and TITLES the row eagerly, before it opens or prompts — until the row… |
| `src/plugins/hermes-bots/canonical-chat-expect-history.test.ts` | The roster's history wait must key off rows a transcript read can paint (`live_message_count`), not the denormalized `message_count` total: a chat whose rows are all folded advertises history no reader serves, and waiti… |
| `src/plugins/hermes-bots/canonical-chat-open-failure-toast.test.ts` | notifyBotOpenFailure copy contract (desktop-34): every failed bot open toasts a plain-words title + next step from the plugin bundle, keeps the raw RPC/connection error in `detail` only, never says "gateway", and offers… |
| `src/plugins/hermes-bots/canonical-chat-registry.test.ts` | The canonical-chat REGISTRY contract. A bot's forever-chat has exactly ONE identity: the session titled "Bot Chat" on that bot's profile. The core UNIQUE(title) index makes (profile, "Bot Chat") an exact registry — at m… |
| `src/plugins/hermes-bots/canonical-chat-stale-tiles.test.ts` | RED for hermes-agent#120810: a Bot Chat compression leaves two tabs captioned with the bot name. openStoredBotChat (via openBotCanonicalChat) must run the same owner-scoped stale-"Bot Chat" probe the roster click runs (… |
| `src/plugins/hermes-bots/canonical-chat.ts` | The canonical Bot Chat: one bot, one forever-chat, resolved by exact title. Read the Bot Mode section of the repo root AGENTS.md before touching any of this — the identity contract below is settled and has been regresse… |
| `src/plugins/hermes-bots/canonical-download-test-utils.ts` | Observe a user-facing browser download, not a private cache-writing IPC. |
| `src/plugins/hermes-bots/canonical-group-activity.tsx` | `groups.state` driver fields that say who is answering. |
| `src/plugins/hermes-bots/canonical-group-alias-scope.test.ts` | Tests: a room NAME shaped like a canonical key is not treated as an identity on another connection; a main-format key minted before this change still opens its room; a canonical-shaped name resolved on B is published un… |
| `src/plugins/hermes-bots/canonical-group-attachments.test.tsx` | Tests: downloads only the selected committed attachment from its captured owner |
| `src/plugins/hermes-bots/canonical-group-attachments.tsx` | Exports `CanonicalGroupAttachment`, `CanonicalGroupUploader`, `fetchCanonicalGroupAttachment`, `CanonicalGroupAttachments` |
| `src/plugins/hermes-bots/canonical-group-capabilities.ts` | Exports `GroupExecutionMode`, `groupExecutionMode`, `groupSeatableProfiles`, `groupCreationSource`, `GroupCapabilityState`, `useGroupCapability` … |
| `src/plugins/hermes-bots/canonical-group-capability-gates.test.tsx` | Tests: keeps positive classifications working: legacy renders and creates locally, canonical creates a gateway room; canonical creation offers only members on the current connection before submission; canonical creation… |
| `src/plugins/hermes-bots/canonical-group-download-lifetime.test.tsx` | Tests: initiates the real user-facing download with exact bytes/name, never the composer cache |
| `src/plugins/hermes-bots/canonical-group-header.tsx` | Exports `CanonicalGroupHeader` |
| `src/plugins/hermes-bots/canonical-group-history.test.tsx` | Tests: keeps a committed file downloadable in history after Send clears the composer (F31); binds user/member history downloads to their real event and refuses missing or foreign room identity; renders only room message… |
| `src/plugins/hermes-bots/canonical-group-history.tsx` | Exports `CanonicalGroupEvent`, `CanonicalGroupHistory` |
| `src/plugins/hermes-bots/canonical-group-labels.ts` | Hosted group copy stays plugin-owned; generic controls reuse the core catalog. |
| `src/plugins/hermes-bots/canonical-group-locales.ts` | Exports `CanonicalGroupMessages`, `CANONICAL_GROUP_LOCALES` |
| `src/plugins/hermes-bots/canonical-group-presentation.test.tsx` | Tests: renders the canonical log actors, timestamps and Markdown without transport markers; keeps attachment-only messages and rows without optional display metadata readable; keeps failed, cancelled, deferred and unava… |
| `src/plugins/hermes-bots/canonical-group-registry.tsx` | Exports `forgetCanonicalGroup`, `registerCanonicalGroup`, `CanonicalGroupOrigin`, `canonicalGroupKeyRoute`, `parseCanonicalGroupKey`, `canonicalGroupAliasKey` … |
| `src/plugins/hermes-bots/canonical-group-reopen-by-name.test.tsx` | #140805: after a Desktop restart the in-memory room_id-keyed bindings are empty, so opening a group by NAME (roster row, restored tab) used to reach the gate whose only action minted a fresh room via groups.create. |
| `src/plugins/hermes-bots/canonical-group-row-delete.test.tsx` | #143571: a gateway Group Chat row in the Bots roster offers Delete from its right-click menu. Delete confirms, disbands the room on its own gateway (`groups.disband`), drops it from the list, forgets its bindings and cl… |
| `src/plugins/hermes-bots/canonical-group-row.tsx` | Exports `CanonicalGroupRow` |
| `src/plugins/hermes-bots/canonical-group-send-windows.test.ts` | @vitest-environment node |
| `src/plugins/hermes-bots/canonical-group-send.test.ts` | @vitest-environment node |
| `src/plugins/hermes-bots/canonical-group-send.ts` | Exports `PreparedCanonicalGroupSend`, `readCanonicalGroupSend`, `prepareCanonicalGroupSend`, `retireCanonicalGroupSend` |
| `src/plugins/hermes-bots/canonical-group-upload-race.test.tsx` | Tests: holds Send until the selected attachment is committed, then sends it with the text |
| `src/plugins/hermes-bots/canonical-group-workspace.test.tsx` | Tests: preserves the unsent draft when only the room display name changes; restores a frozen send after remount and retires only its acknowledged exact retry; blocks Send until journal restore and durable preparation co… |
| `src/plugins/hermes-bots/canonical-group-workspace.tsx` | Exports `CanonicalGroupWorkspace` |
| `src/plugins/hermes-bots/canonical-groups.test.ts` | Tests: pins discovery and every subsequent request to its captured authority, including empty filtered pages; creates only same-authority rosters and dispatches exact advertised attempt identities without inference |
| `src/plugins/hermes-bots/canonical-groups.ts` | Exports `CanonicalGroupRoute`, `CanonicalGroupBinding`, `CanonicalRoomMember`, `CanonicalRoom`, `CanonicalPendingAction`, `captureCanonicalGroupRoute` … |
| `src/plugins/hermes-bots/chat-empty.tsx` | What a bot's chat shows before it has said anything. Core's splash is Hermes' own wordmark and belongs to a fresh draft; a bot chat is neither. It gets the same lettering with the bot's name in it, over the same face th… |
| `src/plugins/hermes-bots/cold-bot-switch-pending.test.ts` | Cold bot switch acknowledges the clicked row before the backend answers (hermes-agent#120277). The mark is published only after the fronted-tab check misses, and before prepareBotSource. It is not chat ownership: highli… |
| `src/plugins/hermes-bots/cold-bot-switch-row.test.tsx` | The pending cold-open mark is a spinner on the clicked row, not a new owner. Highlight still follows the chat on screen (hermes-agent#120277). |
| `src/plugins/hermes-bots/create-agent-lazy-profile.test.tsx` | New Bot creates its profile LAZILY. Two contracts hang off that: - MCP OAuth / API-key credentials must be configurable DURING creation rather than forcing create-then-edit, so the setup button materializes the profile… |
| `src/plugins/hermes-bots/create-dialog.single-flight.test.ts` | The create dialog pre-creates the draft profile so the Capabilities tab has a real backend to point at. Every tab that needs one races for it, so the creation is shared through one in-flight slot — otherwise a user tabb… |
| `src/plugins/hermes-bots/create-dialog.tsx` | The two creation dialogs: New Bot, and the group-chat creation flow the roster's group button opens (plus the per-bot group membership dialog it sits beside). New Bot creates its profile LAZILY, so it owns the single-fl… |
| `src/plugins/hermes-bots/cron-create-dialog.test.tsx` | The Create-job dialog: who it says the job belongs to, and where the run's output is delivered. #93572: the dialog's `bot` prop is the pane's create target — an owner OBJECT for roster-scoped bots, a bare profile name o… |
| `src/plugins/hermes-bots/cron-detail.test.tsx` | Bot Mode's cronjob rows were inert: the only interactive controls were the enable switch and the hover-only delete button, so clicking a job to see what it runs, when it runs next, or why it stopped did nothing at all.… |
| `src/plugins/hermes-bots/cron-jobs-view.test.ts` | Which cron jobs the pane shows, and why it can look empty. Jobs are namespaced `[bot:<name>]`. Newer gateways honour the `profile` param and answer with the bot's OWN cron store (echoed back as `scoped`), in which case… |
| `src/plugins/hermes-bots/cron-load.test.ts` | `loadRoutines` — the pane's one read, and the two things it must survive. 1. Profile scope (#37). cron.manage is scoped to the bot's OWN cron store through the core RPC's optional `profile` param: a bot's profile can ru… |
| `src/plugins/hermes-bots/cron-owner.test.tsx` | A cron mutation names the owner that rendered it, never the ambient profile. The Routines pane follows the focused chat, so the live gateway profile can already be on another bot by the time a row's switch is flipped or… |
| `src/plugins/hermes-bots/cron-pane.test.tsx` | #94483: the Scheduled jobs pane read the shared roster with a bare `$lastRoster.get()` while rendering. BotsPane owns the roster fetch, so whenever this pane mounted before the roster hydrated (fresh boot ordering, a re… |
| `src/plugins/hermes-bots/cron-prompt.test.ts` | What a routine actually runs. A job scheduled for the ACTIVE bot profile runs its instruction directly. A job for a different profile keeps the `hermes -p <bot> chat` delegation wrapper so the run lands in that bot's ow… |
| `src/plugins/hermes-bots/cron-rpc-error.test.ts` | #94471: React Query stores whatever the queryFn throws, and React 19 then formats it with `(error.name \|\| '').trim()`. IPC / JSON-RPC rejections are frequently plain objects whose `name` is the numeric error code, so… |
| `src/plugins/hermes-bots/cron-selected-bot.test.ts` | Which bot the Routines pane is scoped to. #89625 (PR #89637 residual): nanostores' `.listen()` never replays the current value the way `.subscribe()` does, so the focused-owner listener in register() only kept `$selecte… |
| `src/plugins/hermes-bots/cron.tsx` | Routines: the Hermes cron jobs scoped to the bot you're chatting with — the list query and its owner resolution, the schedule picker, the create and detail dialogs, and the pane the right tile renders. |
| `src/plugins/hermes-bots/cross-connection-bots.test.ts` | Cross-connection Bot Mode: a roster row can belong to another registered connection's backend, and a group chat can seat members from several machines at once. Everything hangs off one rule — a source-scoped row carries… |
| `src/plugins/hermes-bots/data.bot-meta-migration.test.ts` | The v1 -> v2 bot-metadata migration and the commit protocol that guards it. v1 keyed appearance by bare bot name, which collides the moment two sources expose a same-named profile; v2 keys by `connectionId::profile`. Re… |
| `src/plugins/hermes-bots/data.bot-meta.test.ts` | Bot metadata: the write path (`saveBotMeta`), the disk-load path (`migrateBotMeta`), and the server-reconciliation overlay (`mergeServerMeta`). Every case below is a shipped regression: - a save must report a REAL remot… |
| `src/plugins/hermes-bots/data.cached-roster.test.ts` | `cachedUnionRoster` is the imperative roster read — the |
| `src/plugins/hermes-bots/data.hermes-handle.test.ts` | Tests: the @hermes handle; names the default @default once a real hermes profile holds the handle; keeps each source separate: a remote hermes profile does not rename the local default; never lets a source |
| `src/plugins/hermes-bots/data.identity.test.ts` | The identity layer every Bot Mode surface files a bot under: the |
| `src/plugins/hermes-bots/data.roster.test.tsx` | The multi-source roster merge, driven through the real `useRoster` query. The union agent roster (`host.agents`) enumerates EVERY registered connection — including the gateway that just answered `profiles.list`. The mer… |
| `src/plugins/hermes-bots/data.ts` | Bot Mode's domain layer: the roster query, bot metadata storage, the identity keys everything else is filed under, and needs-attention state. Framework-light — useRoster is the one React binding — and it depends only on… |
| `src/plugins/hermes-bots/dialog-parts.tsx` | The presentation leaves every Bot Mode dialog shares: a labelled control, and the frame the embedded Capabilities surface is rendered into. They sit below the dialogs rather than inside any one of them — the model picke… |
| `src/plugins/hermes-bots/edit-profile-dialog.tsx` | Edit Profile: appearance, title, description, and the advanced profile config disclosure for an existing bot. |
| `src/plugins/hermes-bots/edit-profile-look.ts` | What Edit Profile shows for a bot's look, as opened and as submitted. |
| `src/plugins/hermes-bots/group-activity.test.ts` | Collapsible group Activity view: a runtime-only, bounded feed of truthful turn events (queued / working / replied / passed / timed-out / failed / cancelled / settled / delivered) that the room shows in a quiet disclosur… |
| `src/plugins/hermes-bots/group-activity.ts` | The per-room activity feed: a bounded, runtime-only record of turn events for the room view's collapsible Activity list. Depends on the room store (for the epoch it tags events with and the speaker label it renders) and… |
| `src/plugins/hermes-bots/group-attachments.ts` | Group-chat attachments: turning picked, pasted, or dropped files into the data-URL payloads a room's members are shown. A leaf module — it talks to the DOM and the toast host, nothing else in Bot Mode. |
| `src/plugins/hermes-bots/group-bot-handoff.test.ts` | Clicking a bot while a group room owns the center is a HANDOFF: the room's main-window tab has to be retired before the canonical chat opens, or two surfaces fight for the center. And if the open fails, the room the use… |
| `src/plugins/hermes-bots/group-chat-parts.test.tsx` | Group-composer mentions (#89049): the core composer's @-completion area doesn't mount inside workspace tiles, so the room's composers wrap the SDK input with a member-scoped popover of their own. Everything it inserts h… |
| `src/plugins/hermes-bots/group-chat-parts.tsx` | The leaf components a group-chat room composes: the room picture controls, the mention-aware composer input, and the card a member's pending clarify/approval prompt renders as. None of them reaches back into the room su… |
| `src/plugins/hermes-bots/group-chat-timeline.test.tsx` | Tests: keeps every public member reply readable in room arrival order across interleaved threads |
| `src/plugins/hermes-bots/group-chat-view-members.test.ts` | Both membership doors (room-side "Manage members", per-Bot "Manage groups") must leave the room reading the SAME roster from its two sources — local groups[] metadata and stored member descriptors — and a removed Bot mu… |
| `src/plugins/hermes-bots/group-chat-view-members.tsx` | Membership editing for an EXISTING group room (#91329, #110736): the room-side "Manage members" picker, the per-Bot "Manage groups" toggle, and the one write both doors share. The room reads membership from two places —… |
| `src/plugins/hermes-bots/group-chat-view.inline-code.test.tsx` | Without a room-owned hook the room's `<code>` falls through to Tailwind Typography's fixed near-black ink, which is invisible on every dark theme (#114086). The renderer stub emits a bare `<code>` with NO `.aui-md` |
| `src/plugins/hermes-bots/group-chat-view.render.test.tsx` | Room bodies go through the shell's message renderer (the 1:1 chat's code card + `MEDIA:` transform) when the SDK exports it. The stub records what the room handed it so the test asserts the wiring, not the renderer's ou… |
| `src/plugins/hermes-bots/group-chat-view.test.ts` | The room surface's two lifecycle mutations — opening a room into the MAIN window, and disbanding one — plus the ordering rules that keep the in-pane fallback from painting a duplicate beside the main tab. |
| `src/plugins/hermes-bots/group-chat-view.tsx` | The group-chat room surface: the merged room view, its settings dialog, the MAIN-window tab it opens into, and the two room-lifecycle mutations that surface drives — disband and rename. Disband and rename live here rath… |
| `src/plugins/hermes-bots/group-chat-view.wrap.test.tsx` | #70451: the group room renders bot replies through the raw Streamdown path (no code card), so a wide fenced block used to inherit `[&_pre]:overflow-x-auto` on the room's message-body wrapper — growing a scrollbar under… |
| `src/plugins/hermes-bots/group-chat.test.ts` | The room store: the atom every group surface reads, the durable projection written to plugin storage, and the bounded mirror published to the gateway's profile ui_meta so mobile sees the same rooms. Identity is the load… |
| `src/plugins/hermes-bots/group-chat.ts` | The group-chat room store: the room atoms, the durable record in plugin storage, the bounded cross-client projection that rides the default profile's ui_meta, and the small pure helpers every room surface shares (identi… |
| `src/plugins/hermes-bots/group-compress.test.tsx` | #102291: room member sessions are hidden plumbing nothing else can compress. The room settings dialog owns a per-member "Compress history" that resumes every session the room holds for that member and runs session.compr… |
| `src/plugins/hermes-bots/group-compress.ts` | Manual compression of a room member's hidden plumbing sessions (#102291). Member sessions (`Group: <roomId> · <thread>`, hidden, room_plumbing) grow with every room drive and are reachable from no other surface: they ar… |
| `src/plugins/hermes-bots/group-external-writes.test.ts` | #93813: a member's per-group session is a plain Hermes session, so the CLI (`hermes -p <bot> chat --resume "Group: …"`), cron and the agent's tools write to it too. Those rows must reach the room log — once — or the room |
| `src/plugins/hermes-bots/group-external-writes.ts` | Mirror of what a member said and heard OUTSIDE the room engine. (#93813) A member's hidden per-group session is an ordinary Hermes session, so other writers legitimately append to it: the user resuming it from the CLI (… |
| `src/plugins/hermes-bots/group-hold-status.test.tsx` | Tests: durable group holds; keeps unmatched holds visible instead of reporting all current members held; names a partial hold and disappears after the production resume directive clears it; keeps a persisted source-scop… |
| `src/plugins/hermes-bots/group-hold-status.tsx` | Exports `GroupHoldStatus` |
| `src/plugins/hermes-bots/group-membership.test.ts` | Who is seated in a room, and how a room's membership is written down. Membership lives in two places on purpose: local bots carry it in bot-meta (`groups`, syncable via ui_meta), while remote members can only be describ… |
| `src/plugins/hermes-bots/group-membership.ts` | Who is in a room: the membership keys, the ui_meta group lists each bot carries, and the roster→member descriptor derivation the room engine and the roster UI both read. |
| `src/plugins/hermes-bots/group-mention-text.test.tsx` | #91359 — recognized group |
| `src/plugins/hermes-bots/group-mention-text.tsx` | Semantic |
| `src/plugins/hermes-bots/group-order.test.ts` | Tests: room display order; keeps legacy recency until explicitly ordered, then only replaces room slots within pin bands; moves only visible same-band rooms while retaining hidden slots and ignoring stale targets |
| `src/plugins/hermes-bots/group-order.ts` | Exports `sortGroupRosterRows`, `reorderGroupRows` |
| `src/plugins/hermes-bots/group-panes.test.ts` | group-panes is a leaf over the room store, and the room store reaches the gateway through `host`. Nothing here talks to a gateway, so the mock only has to satisfy the import graph. |
| `src/plugins/hermes-bots/group-panes.ts` | The window-local state a group-chat room needs but never renders: the per-composer drafts, and the registry of MAIN-window tabs a room is open in. A leaf by design. The room surface and the roster pane both read it and… |
| `src/plugins/hermes-bots/group-pin.test.ts` | "Pin to top" for group chats (hermes-agent#89813): the flag the roster sort already honours gets a write site on the room record, and the pin survives a reload through the same durable group-chats persistence the room u… |
| `src/plugins/hermes-bots/group-pin.ts` | Flip a group chat's "Pin to top" flag (hermes-agent#89813). The roster sort already treats `room.pinned` as the outer band for group rows, the same way `bot-meta.pinned` leads bot rows; this is the write site that flag… |
| `src/plugins/hermes-bots/group-presence.ts` | All presence consumers share the exact owner captured by the room driver. |
| `src/plugins/hermes-bots/group-round-members.ts` | Exports `GroupRoundMemberContext`, `heldMemberWatermarkAdvance`, `heldMemberMessageIds`, `runGroupRoundMember`, `runGroupContinuationMembers` |
| `src/plugins/hermes-bots/group-round-prompt.ts` | Exports `GroupChatLineViewer`, `formatGroupChatLine`, `formatGroupDeltaLines`, `formatFreshThreadRoomContext`, `addFreshThreadRoomContext`, `isGroupChatSelf` … |
| `src/plugins/hermes-bots/group-rounds.addressed.test.ts` | #129443 — the redundancy "(pass)" must not swallow an explicit address. The room's participation rules tell a member to reply only with something new and otherwise "(pass)" — so in an |
| `src/plugins/hermes-bots/group-rounds.hermes-handle.test.ts` | A room holding the default bot and a real (pre-reservation) `hermes` profile: the stored member descriptors must keep the roster's claim, or every reader that re-derives handles from them (the turn prompt, mention parsi… |
| `src/plugins/hermes-bots/group-rounds.primary-alias.test.ts` | Tests: keeps primary handoffs callable in both directions across persisted descriptor shapes; keeps qualified remote defaults distinct from the primary alias regardless of roster order |
| `src/plugins/hermes-bots/group-rounds.test.ts` | The round engine: who answers a room message, in what order, with what delta, and how a round ends. Every contract here is about a SERIAL loop that can be superseded mid-flight — a second send, a stop, or a hold all hav… |
| `src/plugins/hermes-bots/group-rounds.ts` | Room-level coordination: who speaks, in what order, for how long — the |
| `src/plugins/hermes-bots/group-rounds.unaddressed.test.ts` | #94478 — the unresolved-handoff detector. A bot's |
| `src/plugins/hermes-bots/group-slash.test.ts` | Tests: rejects command-shaped sends visibly without changing the room or reaching a member, even with attachments; sends path-first text and embedded slash commands to the room members with attachments intact |
| `src/plugins/hermes-bots/group-slash.ts` | Group rooms cannot dispatch slash commands. Keep command-shaped input out of member prompts without rejecting paths such as /etc/hosts. |
| `src/plugins/hermes-bots/group-test-utils.ts` | A scripted gateway for the group-chat room-engine tests. A member turn is a session-scoped RPC SEQUENCE (create/resume → attach → prompt.submit → poll), so nearly every room contract is only observable in what those RPC… |
| `src/plugins/hermes-bots/group-turns.test.ts` | One member's turn: resolve its per-room session, stage attachments, submit, and poll until the gateway says the member is done. The session is the fragile part — it is addressed by a STORED id that outlives every runtime |
| `src/plugins/hermes-bots/group-turns.ts` | One member's turn: its hidden per-group session, the submit/poll loop that runs it, the pending clarify/approval prompts mirrored out of it, and the late-reply harvest for a turn that timed out. Room-level sequencing li… |
| `src/plugins/hermes-bots/hidden-bots.test.ts` | Per-bot Hide/Unhide. Right-click → Hide Bot persists `hidden: true` in bot meta (local ctx.storage AND server ui_meta via saveBotMeta), hidden bots drop out of the roster list, and a header eye toggle — rendered only wh… |
| `src/plugins/hermes-bots/hidden-bots.ts` | Roster-display hiding: the session-only reveal toggle, the two per-row predicates every surface reads, and the selection re-home a hide performs. A leaf by design. Hiding is presentation, so it knows nothing about the r… |
| `src/plugins/hermes-bots/hide-bot-chats.runtime.test.ts` | Tests: Bot Mode hidden-session reconciliation lifecycle; uses persisted REST on load/reconnect and stops with plugin disposal |
| `src/plugins/hermes-bots/hide-bot-chats.test.ts` | Bot Mode sessions are ALWAYS hidden from the global Sessions sidebar. Canonical Bot Chats and group-chat member sessions alike ride the core generic `hidden` session flag. There is no user pref: `session.create` passes… |
| `src/plugins/hermes-bots/hygiene.test.ts` | #93492 root fix: deleting a connection sweeps/annotates the persisted group-chat member rows that referenced it (registry 'removed' push), and a hydrate-time pass annotates rows orphaned before the sweep existed. Rows a… |
| `src/plugins/hermes-bots/hygiene.ts` | Deleted-connection roster hygiene: the pure half of the #93492 sweep. Marking a group-chat member descriptor whose connection is gone does not depend on where the rooms live, so it sits below the room store — the sweep… |
| `src/plugins/hermes-bots/i18n-bind.ts` | Bind the message SHAPE to a plugin translator: string leaves resolve now, function leaves forward their args through t(path, …). |
| `src/plugins/hermes-bots/i18n-messages.ts` | Message SHAPE for Bot Mode's plugin-scoped i18n bundles (see `./i18n.ts`). |
| `src/plugins/hermes-bots/i18n-test-helper.ts` | Resolve a Bot Mode message key against the plugin's own `en` bundle. Tests that render Bot Mode components stub `usePluginI18n` with this instead of registering the bundle for real: registration normally happens in `ctx… |
| `src/plugins/hermes-bots/i18n.ts` | Plugin-scoped i18n for Bot Mode — bundles registered under the plugin id via `ctx.i18n.register`, never touching core `en.ts`. Mirrors the kanban plugin: `usePluginI18n` returns a stringly-typed `t(key, …)`, and `useBot… |
| `src/plugins/hermes-bots/labels.profile-name.test.ts` | Tests: profile-name identity; derives a stable ASCII profile id from a CJK name and keeps the name as the title; folds accented Latin to its base letters and keeps the accented name as the title; keeps one token per NFC… |
| `src/plugins/hermes-bots/labels.ts` | The presentation leaves every Bot Mode surface reads: the name a row shows, the flattened one-line preview beside it, and the slug that identifies a workspace tile. They sit below the surfaces rather than inside any one… |
| `src/plugins/hermes-bots/legacy-sdk-compat.test.ts` | Bot Mode has to keep linking against an OLDER desktop SDK. `ConnectorsTab`, `ToolsetConfigPanel` and `CapabilitiesView` are capability exports: the shell that hosts the plugin may predate any of them. Every use site is… |
| `src/plugins/hermes-bots/mcp-setup.tsx` | Inline per-profile MCP setup: the `mcp.servers.*` RPC wrapper, its feature-detect, and the button a capability row renders. Shared leaf: the advanced profile editor and the create dialog both render the button, so it li… |
| `src/plugins/hermes-bots/model-picker.test.tsx` | #95279: the Bot Mode model picker's catalog read must always SETTLE, and it must not churn the network on every surface remount. The read rides the BOT's own socket — a second, lazily dialed pool backend that can wedge… |
| `src/plugins/hermes-bots/model-picker.tsx` | Provider + model dropdowns backed by the gateway's `model.options` inventory, plus the bounded fetch that keeps a wedged bot socket from spinning the picker forever. Shared by the advanced profile editor and the create… |
| `src/plugins/hermes-bots/new-compact-guard.test.ts` | The /new → /compact guard's identity check. `/new` inside a bot's canonical forever-chat would fork the relationship into a scratch session — the one thing Bots mode promises never happens. The composer middleware rerou… |
| `src/plugins/hermes-bots/pet.test.tsx` | Pet tiles: frame 0 of a petdex spritesheet, cropped server-side by the gateway's `pet.thumb` RPC and cached per slug. Why the tile goes through the gateway rather than fetching the CDN sheet itself: a locally hatched pe… |
| `src/plugins/hermes-bots/pet.tsx` | The Pet tab: browse the petdex gallery and use a companion's first sprite frame as the bot's profile picture. |
| `src/plugins/hermes-bots/plugin-panes.test.tsx` | Bot Mode's pane layout contract, asserted by running the real `register()` against a recording plugin context: - the Bots pane center-stacks into the sessions zone (a SESSIONS \| BOTS tab strip), never splits below it,… |
| `src/plugins/hermes-bots/plugin.mentions.test.ts` | The two composer contributions Bot Mode registers, driven through the real `plugin.register()`: @-mention completions and the mention middleware. Both read the roster IMPERATIVELY (a popover must answer per keystroke, a… |
| `src/plugins/hermes-bots/plugin.tsx` | Hermes Bot Mode — a "one chat per agent" roster for the Hermes desktop. Left pane "Bots": one row per Hermes profile (a bot = an agent profile) with a customizable avatar (shape + color + eyes, image, or pet). Click ope… |
| `src/plugins/hermes-bots/profile-config-capabilities.test.tsx` | The bot editor's Advanced section renders the REAL core Capabilities surfaces — CapabilitiesView (installed skills + hub installs + detail), ToolsetConfigPanel (per-toolset env/keys/model/post-setup) and ConnectorsTab (… |
| `src/plugins/hermes-bots/profile-config.test.ts` | `applyAdvancedConfig` — the advanced editor's save, which persists ONLY the dirty sections and reports per-section outcomes back to the dialog. Two contracts live here: - **Inherit clears the pin.** A dirty model sectio… |
| `src/plugins/hermes-bots/profile-config.tsx` | The advanced profile editor: skills, toolsets, MCP servers, model and SOUL, backed by `profiles.describe` / `profiles.configure`. The optional-SDK feature detects live here because this is the surface that needs them, a… |
| `src/plugins/hermes-bots/profile-ops.test.ts` | Duplicating a bot: clone the profile (config/skills/SOUL/memory via `clone_from`) and copy the LOOK, but never the things that belong to the original — its canonical-chat pointer and its creation stamp. The name search… |
| `src/plugins/hermes-bots/profile-ops.ts` | The profile operations that reach the gateway rather than the screen: two-way avatar sync, duplicate, and delete. They sit below every surface because both the roster and the create dialog drive them — the dialog delete… |
| `src/plugins/hermes-bots/recent-session.test.ts` | "Open recent session" on a bot row (hermes-agent#93054): opens the profile's newest LISTED session as a tab in the bot's workspace — never in place of the canonical Bot Chat — and hands a bot with nothing listable back… |
| `src/plugins/hermes-bots/recent-session.ts` | "Open recent session" (hermes-agent#93054): a bot row's left click always lands on the canonical Bot Chat — that is the bot's stable identity and stays so. Multi-task users also want the freshest ORDINARY conversation (… |
| `src/plugins/hermes-bots/reclaim-refresh-in-place.test.ts` | The `session.reclaimed` listener's re-resume is a BACKGROUND refresh — issue 121874. When the gateway reaps the runtime behind the OPEN bot chat, the plugin re-resolves the canonical chat so the user's next send doesn't… |
| `src/plugins/hermes-bots/relay-budget.ts` | #93911: a delivered turn runs on the target gateway, so the client must outlive the backend's own bound. Without this the call fell to the pool's generic 30s deadline and every long turn (Computer Use, deep research) ca… |
| `src/plugins/hermes-bots/relay-deliver-budget.test.ts` | Tests: bot_relay.deliver budget mirrors; mirrors the backend turn-lock default; mirrors the backend per-attempt turn timeout; shares its settlement margin with the sender-side waiter budget |
| `src/plugins/hermes-bots/relay.test.ts` | The cross-connection bot relay — the Desktop-as-router loops that let a bot on one gateway reach a bot on another (Aug 2026 ruling: connections ARE the peer set). Three incidents are pinned here: - #93091 — the drain wa… |
| `src/plugins/hermes-bots/relay.ts` | The cross-connection bot relay: the Desktop-as-router loops that let a bot on one gateway reach a bot on another. There is one relay per renderer, so its lifecycle lives in the module-scoped `relay` record below rather… |
| `src/plugins/hermes-bots/roster-actions.test.ts` | The unread/toast poll every roster refresh feeds. This poll is the ONLY unread signal a canonical Bot Chat can have: Bot Chats are unconditionally hidden, so they never reach the session list the backend's own watermark… |
| `src/plugins/hermes-bots/roster-actions.ts` | The two roster actions that reach outside a component: the unread/toast poll every roster refresh feeds, and the click path that fronts one exact bot's canonical chat. They sit beside the surfaces rather than inside the… |
| `src/plugins/hermes-bots/roster-pane-content.tsx` | Exports `renderRosterContent` |
| `src/plugins/hermes-bots/roster-pane-derivation.ts` | The two row shapes the roster sorts together — `kind` is the discriminant. |
| `src/plugins/hermes-bots/roster-pane-dialogs.tsx` | Exports `renderRosterDialogs` |
| `src/plugins/hermes-bots/roster-pane-groups.tsx` | Exports `RosterGroupRowView` |
| `src/plugins/hermes-bots/roster-pane-lifecycle.test.tsx` | The roster snapshot publish (`usePublishRosterSnapshot`) is the one place the 5 s roster poll fans out into shared state: `$lastRoster`, workspace owner labels, server-meta merge, avatar pulls, inbound-activity tracking… |
| `src/plugins/hermes-bots/roster-pane-lifecycle.ts` | Last source inventory returned by the desktop-wide agent roster. |
| `src/plugins/hermes-bots/roster-pane-sections.tsx` | Exports `rosterSectionRenderers` |
| `src/plugins/hermes-bots/roster-pane-toolbar.tsx` | Exports `renderRosterToolbar` |
| `src/plugins/hermes-bots/roster-pane.tsx` | Exports `selectedRosterBot`, `sessionOwnsWorkspace`, `botChatOwnsWorkspace`, `releaseStaleOpenBotChat`, `BotsPane` |
| `src/plugins/hermes-bots/roster-sections.tsx` | How the roster groups and labels what it lists: the gateway filter, the per-connection bucketing, and the foldable headings those buckets render. Presentation below the pane. The headings take everything they draw as pr… |
| `src/plugins/hermes-bots/routing.test.ts` | Cross-connection routing: how a roster row resolves its owning connection, how RPCs ride that owner, and how a configured Desktop alias keeps its friendly identity after the backend it points at answers the roster. #891… |
| `src/plugins/hermes-bots/routing.ts` | Cross-connection routing: resolving a roster row's owning connection, the RPC door that rides that owner, and the alias identity that keeps a configured Desktop alias attached to the backend row it activates into. The b… |
| `src/plugins/hermes-bots/row-helpers.test.ts` | The row-level reads a roster row is assembled from: who sent the last message, and whether a bot counts as live right now. Two bug classes are pinned: - #89484 — the bot-to-bot badge rendered the raw captured profile na… |
| `src/plugins/hermes-bots/row-helpers.ts` | The row-level reads a roster row is assembled from: who sent the last message, whether a bot counts as live, and whether its row owns the highlight. Shared by the bot row, roster pane and open path rather than deriving… |
| `src/plugins/hermes-bots/screen-autoraise.test.ts` | Screen auto-raise contract: a live screen-tool call on an opted-in bot raises its Screen tab once; a manual Close holds through the burst; no opt-in, a foreign profile, or a non-screen tool never raises. |
| `src/plugins/hermes-bots/screen-autoraise.ts` | Raise a bot's Screen tab the moment the bot starts driving its desktop, so you watch it work instead of finding out afterwards. Opt-in per bot (`BotMeta.screenAutoOpen`, row context menu): the Desktop rule is "offer, do… |
| `src/plugins/hermes-bots/screen-connection.test.ts` | Two remote hosts can share the same `~/.hermes` path, so a `display.*` event matched on `profile_key` alone would let host B's take-over repaint host A's screen pane. The event must also have arrived on the bot's own co… |
| `src/plugins/hermes-bots/screen-connection.ts` | Bot Screen — connection plumbing for a bot's Bot Desktop (the headless Xfce screen its computer_use drives on the gateway host). Two legs share one authenticated origin: JSON-RPC (`display.*`) rides the bot's pooled gat… |
| `src/plugins/hermes-bots/screen-hero.tsx` | Screen hero — the big preview of a bot's computer at the top of its pane. Shows a live thumbnail (one `display.thumbnail` JPEG every few seconds while the screen runs and the hero is on screen), or an honest placeholder… |
| `src/plugins/hermes-bots/screen-install-retention.test.tsx` | An INACTIVE registry-routed bot's pooled socket is disposed by the SDK as soon as its request count hits zero — so `display.install.log/done` (and the pane's `display.lease` events) would never arrive. The install card… |
| `src/plugins/hermes-bots/screen-install.tsx` | Bot Screen install card — installs the TigerVNC + Xfce packages on the bot's gateway host from inside Hermes Desktop. `display.install` starts the distro package command on the host; sudo, when needed, arrives as the sa… |
| `src/plugins/hermes-bots/screen-isolation.test.tsx` | Tests: applies lease events only from the owning host even when profile paths match; does not match a legacy profile group to a same-named remote bot; discards a late thumbnail from the previous owner and retains a same… |
| `src/plugins/hermes-bots/screen-managed-copy.test.tsx` | A `display.*` method-not-found from a Portal-managed (Hermes Cloud) backend must not be rendered as "Update the bot's Hermes": the user cannot update a managed release, and the managed Cloud tab already reports it is on… |
| `src/plugins/hermes-bots/screen-open.tsx` | Open a bot's Screen as a main-window workspace tab (host.openWorkspace), one tab per bot; a second open refocuses the existing tab. |
| `src/plugins/hermes-bots/screen-pane-clipboard.test.tsx` | Explicit-paste clipboard bridge (#123089): a native `paste` gesture over the live screen must forward the client's text clipboard to noVNC's `clipboardPasteFrom`, but only while this viewer holds the lease — never on a… |
| `src/plugins/hermes-bots/screen-pane-lifecycle.test.tsx` | Tests: sends an intentional close before noVNC can send its statusless close on pane unmount; pins the bot socket for the attach lifetime and lets go on unmount; does not hand back while replacing a stream to reconnect… |
| `src/plugins/hermes-bots/screen-pane-status-events.test.tsx` | The pane paints a cache of backend truth. A start or stop made outside this window (CLI, gateway auto-start, another Desktop) reaches the renderer only as a pushed `display.status` event — a stopped pane with no sibling… |
| `src/plugins/hermes-bots/screen-pane.tsx` | Bot Screen pane — live view of a bot's headless desktop with Take over / Hand back. State authority: the BACKEND owns runtime + lease (`display.status`, pushed as `display.lease` events); this pane paints a cache of it.… |
| `src/plugins/hermes-bots/screen-portal-status-request.test.tsx` | The portal's one-shot `display.status` fetch is a network reply, not an event: a snapshot it returns can predate a newer authoritative write that landed while it was in flight. Like the pane's fetch, it must carry a req… |
| `src/plugins/hermes-bots/screen-portal.tsx` | Screen portal — the compact "this bot's computer" box that sits above a bot's routines and on a gateway/profile group in the Sessions sidebar. One click opens the live Screen pane; the subtitle says whether the screen i… |
| `src/plugins/hermes-bots/screen-state.test.ts` | Lease ordering: `display.lease` events and `display.status` replies race on the wire. A slower status reply describing an OLDER lease must never roll back the newer event — the backend's monotonic `epoch` is the tiebrea… |
| `src/plugins/hermes-bots/screen-state.ts` | Per-bot Bot Screen cache: backend truth (`display.status`) plus the last `display.lease` event, keyed by the bot's roster identity. Renderer-owned cache of backend state — never the authority. |
| `src/plugins/hermes-bots/screen-viewer-identity.test.tsx` | Viewer identity is SERVER-MINTED: `display.observe` returns the id this attach is known by, and lease payloads name the holder by `viewer_hash` (sha256(viewer_id)[:12]) rather than the raw id. "I hold" must be derived f… |
| `src/plugins/hermes-bots/session-sweep.ts` | The always-hidden reconciliation sweep: everything that walks Bot Mode's own sessions on load and on each reconnect and pushes them back to hidden. Durable-visibility plumbing, not a surface. It reads the room store and… |
| `src/plugins/hermes-bots/shared.ts` | The pieces every Bot Mode module needs and no single module can own: the plugin id, the `PluginContext` `register()` captures, and the open generation the bot-open and group-open click paths race on. The mutable ones li… |
| `src/plugins/hermes-bots/skills-hub-picker.test.tsx` | The Skills Hub picker embeds the real hub page in an iframe; the page posts `{type:'hermes-skill-pick'}` back and the plugin installs via skills.manage. The handler used to check only `event.origin`, so ANY window on th… |
| `src/plugins/hermes-bots/skills-hub.tsx` | The real skills hub page embedded as a picker, plus its offline search fallback. A leaf: the advanced profile editor and the create dialog both mount it, and it reaches back into neither. |
| `src/plugins/hermes-bots/soul.test.ts` | The agent-to-agent messaging protocol section every SOUL has to keep. #16: a CUSTOM SOUL silently dropped the handoff protocol, which broke |
| `src/plugins/hermes-bots/soul.ts` | The SOUL a bot is born with, and the agent-to-agent messaging protocol section every SOUL has to keep. Three surfaces need a piece of this and none of them can own it: the create dialog composes a new SOUL, the advanced… |
| `src/plugins/hermes-bots/types.ts` | Bot Mode domain model. Derived from how the gateway's payloads are actually consumed, not from a published schema — so almost everything is optional. A roster row can arrive three ways (a rich `profiles.list` row from t… |
| `src/plugins/hermes-bots/user-sections-ui.test.tsx` | `SectionNameDialog`'s Enter-to-submit handling must go through the shared IME-aware predicate (`isSubmitEnter`), not a hand-rolled `isComposing`-only check — a bare check misses the legacy `keyCode === 229` commit-Enter… |
| `src/plugins/hermes-bots/user-sections-ui.tsx` | The chrome for user sections: the foldable heading (the roster's own `RosterSectionHeader`, with a ⋯ menu and a right-click menu that drive the same actions), the name dialog used for both New section and Rename (the sa… |
| `src/plugins/hermes-bots/user-sections.groups.test.ts` | Group chats file into user-made sections exactly like bots — with the one structural difference the model encodes: a bot's membership is a field on its profile meta (profile sync carries it), while a group's is a field… |
| `src/plugins/hermes-bots/user-sections.test.ts` | User sections — the three invariants that make membership-on-the-bot safe: filing persists through `saveBotMeta` (so it rides profile sync), every row lands in exactly one block with the remainder as Unassigned, and del… |
| `src/plugins/hermes-bots/user-sections.ts` | USER SECTIONS — folders the user makes, not folders the topology makes. The roster already had sections (`roster-sections.tsx`), but only AUTOMATIC ones: one per gateway connection, plus the group-chat bucket. Those ans… |
| `src/plugins/kanban/api.connection-scope.test.ts` | A board lives on ONE gateway; the kanban data layer follows the active connection. See the scope comments in ./api.ts. |
| `src/plugins/kanban/api.default-notify.test.ts` | Tests: default board event notifications; refreshes an open alias-keyed task drawer on a live event; does not resolve or override a caller-selected board; pins the socket to the resolved board and notifies a post-baseli… |
| `src/plugins/kanban/api.events-cursor.test.ts` | Opening /events with no since replayed the board's whole task_events history. The socket must start at the snapshot's tail, and a late snapshot must not reopen a board the user already left. The cursor is per connection. |
| `src/plugins/kanban/api.ts` | Kanban data layer. Everything goes through `ctx.rest` — the plugin's own `/api/plugins/kanban/*` FastAPI router (`plugins/kanban/dashboard/plugin_api.py`), reused as-is via the desktop's namespace-scoped REST door. No n… |
| `src/plugins/kanban/board-switcher-placement.test.tsx` | Where the board switcher mounts (#123597). The full page projects it into the workspace page header; a route tile has no painted page header, so the same switcher sits in the board's own header row. These run the REAL r… |
| `src/plugins/kanban/board-switcher.test.tsx` | Test harness supplies the host's locale registration, as plugin loading does. |
| `src/plugins/kanban/board-switcher.tsx` | Board switcher. On the full page it is projected through `WORKSPACE_PAGE_HEADER_AREA` into the workspace panel's tab-header space; in a split route tile it renders in the board's own header row. Placed by `WorkspacePage… |
| `src/plugins/kanban/board.tsx` | The Kanban board page — mounted at `/kanban` (a ROUTES_AREA contribution) in the workspace pane or a split route tile. The desktop port of the dashboard board: one compact header row (count, board switcher, filter kebab… |
| `src/plugins/kanban/card-badges.test.tsx` | The board paints plugin card badges (#140026): the REAL board page, the REAL plugin context and registry, with only the kanban REST layer mocked. A plugin never touches the card's DOM; it returns text and a palette tone… |
| `src/plugins/kanban/completion-notify.test.ts` | Focused tests for the completion-notify module. Each test starts from a FRESH module instance (vi.resetModules + dynamic import) so the in-memory per-board cursor and rest binding match a fresh renderer process. The |
| `src/plugins/kanban/completion-notify.ts` | Native kanban terminal-event notification (completion, blocker, failure). No maintained exact-fit OSS exists and the SDK has no kanban event door, so this module rides the kanban plugin's EXISTING /events socket (api.ts… |
| `src/plugins/kanban/drawer.test.tsx` | Test harness drives the host's request scope, as a connection switch does. |
| `src/plugins/kanban/drawer.tsx` | Task modal — the desktop port of the dashboard's task detail, Linear-style: a centered two-column dialog (main: diagnostics, description, result, dependencies, comments, activity, runs, log tail; right sidebar: property… |
| `src/plugins/kanban/i18n.ts` | Plugin-scoped i18n for kanban — bundles shipped under the plugin id via ctx.i18n.register (#67303), never touching core en.ts. usePluginI18n('kanban') returns a stringly-typed t(key, …); `useKanban()` binds it to the me… |
| `src/plugins/kanban/kanban.css` | Machine-activity arc — a highlight that travels the card's border while an agent is ACTUALLY working the card (amber-slow when the heartbeat is gone). Queued/attached cards do NOT animate — that's the footer's named-age… |
| `src/plugins/kanban/model-override.test.tsx` | Tests: override label; reads as inherited until something is pinned; a depth-only pin is still an override; the shared catalog menu, driven by an override controller |
| `src/plugins/kanban/model-override.tsx` | Per-task model override — the board's half of the composer's model picker. The MENU is not ours: `ModelCatalogMenu` from the SDK is the same component the chat composer renders, so search, provider grouping, `-fast` fam… |
| `src/plugins/kanban/orchestration.tsx` | Orchestration settings — the dashboard's dispatcher-knobs panel, flat-styled: orchestrator profile, default assignee, auto-decompose, and the profile descriptions the decomposer routes by (save / auto-generate per profi… |
| `src/plugins/kanban/plugin.tsx` | Kanban — the founding plugin use case, now pure SDK-consumer work: a first-class `/kanban` board page + sidebar nav row + a live statusbar count, all reusing the existing `plugins/kanban/dashboard/plugin_api.py` REST ro… |
| `src/plugins/kanban/run-clock.test.tsx` | Test harness supplies the host's locale registration, as plugin loading does. |
| `src/plugins/kanban/transfer.ts` | Board export / import flows — the same shape as the profile ones (`src/store/profile-share.ts`): pick a path with the native dialog, hand the PATH to the backend, toast the outcome. Bytes never cross the renderer. The p… |
| `src/plugins/kanban/types.ts` | The slice of the kanban REST contract the board renders. The backend (`plugins/kanban/dashboard/plugin_api.py`) returns much more per task; we type only what the UI reads so a schema addition never breaks the build. |
| `src/plugins/kanban/ui.tsx` | Shared kanban UI atoms: formatters, the identity avatar, the status menu, section chrome, and the masked scroller. Pure SDK + tokens. |
| `src/plugins/radio/README.md` | Radio |
| `src/plugins/radio/plugin.js` | JavaScript source: `plugin` |
| `src/sdk/areas.ts` | Contribution-area constants the SDK barrel re-exports whole: host-owned areas with no feature module of their own, plus area contracts whose module lives in core but has no other public door. |
| `src/sdk/bridge.test.ts` | The bridge must hit the SAME api-module functions the Capabilities page calls (not a parallel fetch path), forwarding the ProfileScope untouched — that is the whole contract: typing + profile scoping over existing doors. |
| `src/sdk/bridge.ts` | Typed capabilities bridge for desktop plugins (`host.skills`, `host.toolsets`, `host.profiles`, `host.pluginDecisions`). Plugins that configure capabilities used to call `window.hermesDesktop.api` raw and read the persi… |
| `src/sdk/composer.ts` | Exports `composerHost` |
| `src/sdk/host-state.test.ts` | Plugins read app state exclusively through host.state — and before this contract existed, only the PRIMARY workspace tab was reachable ($activeSessionId). Clicking a tile never moved any plugin-visible atom, |
| `src/sdk/i18n.ts` | THE language-pack surface: add a whole UI language (or extend one) at runtime. A registration is a PARTIAL catalog — nested like `en.ts` or flat dotted keys (`{ "common.save": "Zapisz" }`) — merged over the bundled cata… |
| `src/sdk/index.test.ts` | The warm path must route through the guarded prewarm resolver (hover dwell, per-profile throttle), not dial the gateway directly: mocking the store's dialers lets the tests observe the ONLY side effect that matters — wh… |
| `src/sdk/index.ts` | Exports `PluginFocusedSessionOwner`, `DEFAULT_SESSION_HYDRATION_TIMEOUT_MS`, `BOT_CHAT_SESSION_HYDRATION_TIMEOUT_MS`, `HYDRATION_SYNC_BADGE_TIMEOUT_MS`, `PluginOpenSessionOptions`, `PluginNewChatOptions` … |
| `src/sdk/open-session-refresh-in-place.test.ts` | `host.openSession({ refreshInPlace })` — the BACKGROUND re-resume contract (issue 121874). A `session.reclaimed` (or roster-activity) wake re-resolves the open Bot Chat so the user's next send doesn't eat a stale runtim… |
| `src/sdk/plugin-contract.ts` | The plugin authoring contract types; the SDK barrel re-exports them. |
| `src/sdk/plugin-open-session-plan.test.ts` | Tests: planPluginOpenSession; defaults to navigation: dial the worker, do not steal chrome; does not steal chrome even when keepAllProfilesScope is explicitly true; does not re-dial when chrome is already on that profile |
| `src/sdk/plugin-open-session-plan.ts` | How `host.openSession` should treat a named profile. A plugin/Bot Mode open is navigation, not a workspace or chrome API-home switch. `keepAllProfilesScope` defaults true (undefined counts as true). Pass false for an ex… |
| `src/sdk/profile-local.ts` | `host.warmProfile` and `host.dropLeftoverProfilePrefs`: profile verbs that touch only this window's pool and storage, never the profile itself. |
| `src/sdk/profile-request.ts` | Plugin-facing profile routing for `host.requestProfile` and friends. |
| `src/sdk/profile-routing.test.ts` | Tests: connection-aware plugin host APIs; retires a profile gateway before deleting it; pins an ambient SSH profile delete to the active connection and target profile; refreshes the profile inventory before asking Elect… |
| `src/sdk/runtime.ts` | Runtime SDK injection — the other half of the vscode-module model. Bundled plugins resolve ` |
| `src/sdk/sessions.ts` | Exports `sessionsHost` |
| `src/sdk/settings.test.ts` | Tests: host.settings; reads and writes the allowlisted typed preferences through their owning stores; preserves the stores existing persistence schema; subscribes immediately and follows changes from the native settings… |
| `src/sdk/settings.ts` | Exports `DesktopSettingValues`, `DesktopSettingKey`, `desktopSettings` |
| `src/sdk/spellcheck.test.ts` | Tests: host.spellcheck dictionary verbs; routes one word through the app; resolves false instead of throwing without a desktop shell or with a non-string |
| `src/sdk/spellcheck.ts` | `host.spellcheck`: Chromium's custom spell-check dictionary, one word at a time. The word gate and the session call live in main (`electron/spellcheck-dictionary-ipc.ts`); this side only forwards and turns |
| `src/sdk/viewport.ts` | `host.state.viewport`: window geometry + the app's responsive posture. |
| `src/store/active-work.test.ts` | Tests: active work bridge; reports a busy session by title; counts an untitled busy session without inventing a title; drops back to nothing when the turn ends |
| `src/store/active-work.ts` | Mirror of "which chats are mid-turn" to the main process. The renderer is the only side that knows a turn is in flight, and the main process is the only side that can intercept a quit. This module bridges the two: it pu… |
| `src/store/activity.ts` | Exports `RailTaskStatus`, `RailTask`, `DesktopActionTask`, `upsertDesktopActionTask`, `buildRailTasks` |
| `src/store/admitted-submissions.ts` | The input ids (client submission ids) the owner's pending snapshots list per composer queue key, as this page saw them. A send the owner admitted but has not run yet (queued behind a running turn or an unresolved one) h… |
| `src/store/agent-notices.test.ts` | Tests: drops a notice with no text; level maps to toast kind (warn → warning); unknown / missing level falls back to info; sticky notices never auto-dismiss |
| `src/store/agent-notices.ts` | Wire shape of a `notification.show` payload — the driver-agnostic `AgentNotice` spine (`agent/credits_tracker.py`) as forwarded by `tui_gateway/server.py`. Snake_case to match the wire. The `text` carries its own leadin… |
| `src/store/agent-plugins.test.ts` | Tests: installAgentPlugin; waits for a slow successful install instead of reporting the generic 30s timeout; marks a client timeout as an unknown install outcome; never resends without the inspected commit on its own wh… |
| `src/store/agent-plugins.ts` | Feature store for backend (agent) plugins — the native Hermes plugins plus portable Agent Plugins v1 packages the backend discovers on disk. Settings renders this next to the desktop (renderer) plugin inventory so every… |
| `src/store/ambient.ts` | One window owns each cross-window ambient cue (turn-end sound, spoken reply) so N open full windows don't all fire it for the same backend event. The main process is the race-free owner (see electron/event-dedupe.ts). O… |
| `src/store/appearance-apply.test.ts` | Tests: applyAppearance; applies every value and reports the ids the agent reads; applies nothing when one value is unknown, and names what exists |
| `src/store/appearance-apply.ts` | What `set_theme` and its picker cards change: accent, light/dark mode and layout preset, validated as a whole before anything is applied so an unknown layout never leaves a new accent half-applied. Accent persists throu… |
| `src/store/approval-mode.test.ts` | Tests: profile-scoped approval mode cache; labels an unread profile Smart by default and adopts backend truth; scopes reads and writes to the named profile so a non-launch profile is not misrouted; omits the profile par… |
| `src/store/approval-mode.ts` | Exports `ApprovalMode`, `ApprovalModeRequester`, `approvalModeForProfile`, `reconcileApprovalModeForProfile`, `syncApprovalModeForProfile`, `setApprovalModeForProfile` |
| `src/store/artifacts.test.ts` | Tests: artifacts store; registers a new artifact with one version; dedupes identical content by hash (streaming replays are no-ops); appends a version when the same artifact regenerates with new content |
| `src/store/artifacts.ts` | ARTIFACT REGISTRY — substantial generated content (HTML pages, large SVGs, long code) produced in the transcript, promoted out of the message flow into versioned content the right rail can preview. The registry is autho… |
| `src/store/backdrop.ts` | Exports `setBackdrop` |
| `src/store/background-delegation.test.ts` | Tests: tracks only the owning runtime session, independent of foreground busy state and child stream text |
| `src/store/background-delegation.ts` | Exports `BackgroundResume`, `sessionBackgroundResume` |
| `src/store/billing-block.test.ts` | Tests: clearBillingBlock scoped to a session leaves a different session block intact; clearBillingBlock with no arg clears any active block; runBillingRecovery routes Nous to in-app Settings, never an external link; run… |
| `src/store/billing-block.ts` | The active inference billing wall, if any. Set from the gateway `message.complete` / `error` event when a turn fails with `FailoverReason.billing` (see `agent/billing_links.py`). One global slot: a credit wall on the ac… |
| `src/store/boot.ts` | Exports `DesktopBootState`, `applyDesktopBootProgress`, `applyDesktopUpdateHold`, `setDesktopBootStep`, `resumeDesktopBootForRetry`, `completeDesktopBoot` … |
| `src/store/bot-chat-scope.test.ts` | `$botChatSessionIds` is the store a surface must SUBSCRIBE to when it asks `isBotChatSession`. The composer originally subscribed to `$sessionStates` while reading this set. It looked fine because `$sessionStates` churn… |
| `src/store/browser-tab-title.test.ts` | Tests: browserTabTitle; lets a blocking prompt speak over a running turn, behind the unread count; installBrowserTabTitle; follows the focused session and background status in a browser host |
| `src/store/browser-tab-title.ts` | The browser tab title of the browser-hosted Desktop (Webapp). In a browser the tab strip is the one surface that stays visible while the user is in another tab or app, so the title carries the same signals the sidebar d… |
| `src/store/busy-input-mode.ts` | Exports `BusyInputMode`, `normalizeBusyInputMode`, `busyInputOwnerKey` |
| `src/store/butterbar.test.ts` | Tests: butterbar store; is empty until something registers; orders by priority, then registration order, and re-registering replaces in place; a stale unregister does not remove the item that replaced it |
| `src/store/butterbar.ts` | Exports `ButterbarTone`, `ButterbarItem`, `registerButterbar`, `dismissButterbar`, `isButterbarCloseable`, `useButterbar` |
| `src/store/chat-text-scale.test.ts` | Tests: restores the selected chat scale without changing window zoom or global typography; falls back to the default for invalid storage and keeps an explicit 100% selection |
| `src/store/chat-text-scale.ts` | Exports `CHAT_TEXT_SCALE_PRESETS`, `ChatTextScale`, `setChatTextScale` |
| `src/store/clarify.test.ts` | Tests: clarify store; keeps clarify requests from concurrent sessions independent; exposes only the active session via the focus-scoped view; clears only the targeted session, leaving the other pending |
| `src/store/clarify.ts` | Exports `ClarifyQuestion`, `ClarifyRequest`, `RECOMMENDED_LABEL`, `bareChoice`, `MAX_CHOICE_CHARS`, `normalizeChoices` … |
| `src/store/coding-status.test.ts` | Tests: refreshRepoStatus; populates the per-cwd cache and the primary computed for that cwd; falls back to the active session cwd when none is passed; leaves the cache alone (primary reads null) when there is no cwd |
| `src/store/coding-status.ts` | Exports `repoStatusForCwd`, `isGitRepoPath`, `repoWorktreesForCwd`, `RepoChangeKind`, `repoChangeKindForPath`, `registerRepoStatusCwd` … |
| `src/store/command-palette.ts` | Whether the global command palette (Cmd/Ctrl+K) is currently open. |
| `src/store/compaction.test.ts` | Tests: compaction store; tracks session ids that collide with object prototype keys; scopes the view to the session asked for, not whichever is active; clears a session without disturbing the others |
| `src/store/compaction.ts` | Per-session flag while auto-compaction runs mid-turn. Without it the transcript looks like it reset; per-session so a background chat can't clobber the foreground view. |
| `src/store/completion-sound.ts` | Exports `DEFAULT_COMPLETION_SOUND_VARIANT_ID`, `NO_COMPLETION_SOUND_VARIANT_ID`, `resolveCompletionSoundVariantId`, `setCompletionSoundVariantId` |
| `src/store/composer-actions.ts` | Composer micro actions — the floating pill strip at the top of the composer's overlay lane. A badge is a label and a `run`; what it does is entirely the registrar's business. Core ships none — the strip is a seam, fille… |
| `src/store/composer-draft-retry.ts` | The identity of an uncertain send that was restored into a composer draft. Sending that exact draft again is the explicit retry (same `submission_id`, so the owner replays instead of running it twice); editing it, or ty… |
| `src/store/composer-draft-stash.test.ts` | Two windows share localStorage, but each reads its own copy and gets the other's writes milliseconds later. A second module instance is the other window; restoring the storage it loaded with before it writes makes its |
| `src/store/composer-draft-stash.ts` | The shared draft stash every window of the app reads and writes. Each window keeps its own copy of localStorage, and another window's write reaches it some milliseconds later. A window that wrote its whole draft list fr… |
| `src/store/composer-input-history.test.ts` | Tests: deriveUserHistory; returns user messages newest-first with empty/whitespace skipped; browseBackward; returns null when history is empty |
| `src/store/composer-input-history.ts` | Per-session input history browse state. The user-text ring is **derived from the live session messages** on each keypress — it is not mirrored anywhere. This keeps a single source of truth and avoids the entire class of… |
| `src/store/composer-outbox-landed.ts` | A window can close after the backend admitted a send but before the submit ack came back. Its outbox entry then outlives a send that DID land: re-offering it as the draft would show the words twice (in the chat and in t… |
| `src/store/composer-outbox.ts` | Enter clears the composer and hands the words to an async send chain (session resume or create, attachment sync, the prepared journal) before `prompt.submit` is written. Closing or reloading the window inside that gap e… |
| `src/store/composer-popout-preference.test.ts` | Tests: composer pop-out preference; docks the shared composer, preserves its placement, and persists the lock; normalizes stale floating zones when the persisted preference is disabled; locks a fresh install to the dock |
| `src/store/composer-popout.test.ts` | Tests: clampPopoutPosition; keeps the whole box inside its surface, not just its corner; pulls an out-of-bounds intent back into the surface; is pure — the same intent yields a different placement per surface |
| `src/store/composer-popout.ts` | Exports `PopoutPosition`, `ComposerPopoutState`, `POPOUT_WIDTH_REM`, `POPOUT_ESTIMATED_HEIGHT`, `setComposerPoppedOut`, `setComposerPopoutGesturesEnabled` … |
| `src/store/composer-queue-owner.test.ts` | Tests: composer queue ownership for the browser-hosted Desktop; belongs to the gateway when the window dials its canonical socket; stays in the renderer for a backend still on the legacy contract |
| `src/store/composer-queue.test.ts` | Tests: composer queue store; queued-prompt handoff keeps blob previews across composer clear, then revokes when the entry is discarded; drain handoff retains blob previews when the queued entry is removed after submit o… |
| `src/store/composer-queue.ts` | Exports `serverOwnsComposerQueue`, `RemoveQueuedPromptOptions`, `QueuedPromptEntry`, `queuedSubmissionId`, `EnqueueQueuedPromptPayload`, `ResolvedQueuedPromptTransport` … |
| `src/store/composer-status-drawer.test.ts` | Tests: restores the hidden choice without sharing it with another session or owner; follows local profile renames and scopes profile removal to the exact owner |
| `src/store/composer-status-drawer.ts` | Exports `statusDrawerKey`, `setStatusDrawerCollapsed`, `migrateStatusDrawersForProfile`, `dropStatusDrawersForProfile` |
| `src/store/composer-status.test.ts` | Tests: reconcileBackgroundProcesses; maps registry entries to status items; keeps row order stable when a process flips state or the snapshot reorders; appends new processes after existing rows |
| `src/store/composer-status.ts` | Exports `StatusItemState`, `StatusItemType`, `ComposerStatusItem`, `StatusGroup`, `groupStatusItems`, `reconcileBackgroundProcesses` … |
| `src/store/composer.test.ts` | Tests: voice conversation start requests; latches each request until the main composer consumes it once; blob preview URL ownership handoff; direct-submit handoff keeps blob previews across clear, then revokes when the… |
| `src/store/composer.ts` | Exports `revokeAttachmentPreviewUrl`, `revokeAttachmentPreviewUrls`, `revokeDiscardedAttachmentPreviews`, `ClearAttachmentsOptions`, `ComposerAttachment`, `ComposerAttachmentPatch` … |
| `src/store/confirm.ts` | Exports `ConfirmRequest`, `PendingConfirm`, `confirm`, `runConfirm`, `settleConfirm` |
| `src/store/connection-registry-state.ts` | Null only for the legacy profile-only Desktop topology. Once Electron has published a registry, profile names are source-local and are not owners. |
| `src/store/connection-request.test.ts` | Tests: connection-request store; normalizes the wire payload and keeps the server-owned deadline verbatim; binds to the model tool call that opened the operation, on a live request and on resume; rejects a payload with… |
| `src/store/connection-request.ts` | Exports `CatalogEntry`, `ConnectionTarget`, `ConnectionOwner`, `ConnectionRequest`, `ConnectorDisplay`, `CONNECTION_OP_ARG` … |
| `src/store/connections-new-chat-route.test.ts` | Tests: re-homes an explicit draft with the selected source, including the return trip; re-homes a fresh draft when leaving All profiles on the already active source; keeps a draft the user pinned while the silent boot r… |
| `src/store/connections.test.ts` | Tests: connection registry cache; loads only Electron local registry state; restores the last-used source once when that launch mode is enabled; preserves the established Primary-source launch behavior by default |
| `src/store/connections.ts` | Exports `_resetConnectionsForTests`, `setConnectionsRegistry`, `refreshConnectionsRegistry`, `initializeConnectionsRegistry`, `SelectConnectionOptions`, `selectConnection` |
| `src/store/cron.test.ts` | Tests: cron jobs request fencing; rejects an older refresh after a newer refresh commits; rejects a refresh from the previous profile scope; rejects an in-flight poll after a local mutation |
| `src/store/cron.ts` | Cron *jobs* (not run sessions) power the sidebar "Cron jobs" section. Listing the job — schedule, state, live next-run countdown — makes the job the first-class entity; its runs (sessions) resolve under it in the cron d… |
| `src/store/custom-models.test.ts` | Tests: custom models; offers a typed id only while no provider lists it; appends each remembered id under its own provider and keeps the input when nothing applies; merges custom models into a usage-window Nous row too… |
| `src/store/custom-models.ts` | Exports `CustomModel`, `isCustomModel`, `customModelSlug`, `customModelCandidate`, `withCustomModels`, `addCustomModel` … |
| `src/store/data-url-read-max.test.ts` | Tests: clampDataUrlReadMaxMb; defaults invalid input and clamps only the safety range; data-url-read-max store; loads the main-process value into the atom |
| `src/store/data-url-read-max.ts` | Max size for local files Desktop loads as data URLs (composer attach, image previews, etc.). Main owns the real cap + its JSON under userData — this atom only mirrors it for Settings → Chat. See electron/main.ts (`herme… |
| `src/store/dead-session-prune.test.ts` | Tests: __runDeadSessionPrunePass; unpins a pin whose session 404s on every profile; keeps a pin whose session lives on another profile, and caches it as alive; defers on non-404 probe failures instead of dropping, and r… |
| `src/store/dead-session-prune.ts` | Prune renderer-stored session references whose sessions no longer exist on the backend. Pins (`hermes.desktop.pinnedSessions`), composer drafts (`hermes:composer-drafts:v4`, mirrored to v3), queued prompts (`hermes.desk… |
| `src/store/default-profile-startup.test.ts` | Tests: startup default route; does not replace the main-process route after a transient preference read failure; does not override a profile picked while the preference read was pending; does not re-home an already sele… |
| `src/store/default-profile.test.ts` | The native bridge is the persistence boundary; the renderer owns only a mirror. |
| `src/store/default-profile.ts` | Electron owns persistence and cross-window changes. This atom is only a mirror: changing the preference must not re-home an existing conversation. |
| `src/store/desktop-metrics.test.ts` | Tests: consent gate; collection off: nothing is persisted and nothing is sent; an unknown gate (before the switch is read) records nothing either; turning collection off purges the local record and drops anything queued |
| `src/store/desktop-metrics.ts` | Desktop love/hate telemetry: which areas get used, which buttons get pressed, what gets in the way, what gets turned off, and where first run stops. No UI of its own — every fact is a counter wired into an existing inte… |
| `src/store/disable-f12.ts` | Disable F12 DevTools shortcut — a device-local preference. When enabled, F12 is blocked in the main process (before-input-event). Ctrl+Shift+I (or Cmd+Opt+I on Mac) still works regardless. Mirrors the toggle to the main… |
| `src/store/display-timestamps.ts` | `display.timestamps` — one config key for message timestamps everywhere. The same config.yaml key that puts [HH:MM] stamps on classic-CLI labels gates the desktop transcript's per-message / per-tool-run timeline timesta… |
| `src/store/display-toggles.test.ts` | Tests: display toggle mirror; sends the user answer to the gateway when it changes; re-sends a touched setting to a gateway that has never seen it; leaves an untouched setting alone, so a hand-edited config.yaml wins |
| `src/store/display-toggles.ts` | Appearance switches the BACKEND also has to know about. Most of what Settings → Appearance controls is the renderer's own business. A few switches aren't: they decide whether a tool is in the model's schema at all (`rea… |
| `src/store/embed-consent.ts` | Privacy gate for inline embeds. Loading an embed reaches out to a third party (IP, referrer, cookies), so by default we render a placeholder until the user consents — per embed ("Load once") or per service ("Always allo… |
| `src/store/external-links.test.ts` | Tests: always-external-links store; defaults off and persists the pref; follows a change made in another window |
| `src/store/external-links.ts` | Always open links in the system browser — a device-local preference. Off (the default): a clicked web link opens in the in-app browser, and ⌘/Ctrl-click or middle-click escapes to the OS browser. On: every clicked link… |
| `src/store/favorite-models.test.ts` | Tests: favorite models keep their starred order; appends new favorites after existing ones; unfavoriting leaves the remaining order intact; re-starring an unfavorited model puts it at the end, not back in its old slot |
| `src/store/favorite-models.ts` | Exports `favoriteModelKey`, `isModelFavorite`, `setFavoriteModels`, `toggleFavoriteModel` |
| `src/store/file-actions.test.ts` | Tests: shouldOfferRemoteFileDownload; is only for files on a remote backend; shouldOfferLocalReveal; downloadRemoteFile |
| `src/store/file-actions.ts` | Exports `FileActionTarget`, `FileActionDialog`, `requestFileDelete`, `closeFileActionDialog`, `beginInlineRename`, `cancelInlineRename` … |
| `src/store/find-in-page.ts` | Exports `FindInPageState`, `openFindBar`, `closeFindBar`, `setFindQuery`, `findNext`, `findPrevious` … |
| `src/store/fleet-roster.test.ts` | Tests: fleet roster recovery; queues one fresh enumeration when recovery overlaps an older request; keeps on-demand sources cached but lets explicit recovery bypass the cooldown; retries incomplete rosters before the no… |
| `src/store/fleet-roster.ts` | The union agent roster — every profile on every registered gateway — as Electron enumerates it over REST/SSH (`hermes:agents:roster`). Bot Mode and the Capabilities scope selector already read it; the Sessions profile r… |
| `src/store/free-tier-challenge.test.ts` | Tests: runFreeTierChallenge; reports the matching attempt outcome without treating the host as an auth authority; hands a browser challenge to the main process; runs one window per URL while it is in flight, reports it… |
| `src/store/free-tier-challenge.ts` | The free tier's browser challenge, renderer half: a relay. The backend (`hermes_cli/anon_challenge.py`) announces a challenge and polls the account service for the result itself; the Electron main process (`electron/cha… |
| `src/store/free-tier-offer.test.ts` | Tests: sign-in offer after a finished task; waits for the local-model offer to be answered, then claims; waits while an app window is open, so it never covers it; due now: claims once and opens the offer |
| `src/store/free-tier-setup-failure.test.ts` | Tests: freeTierSetupFailure; is nothing when the backend reported no failure, the tier is off, or an identity exists; carries the code, the sentence, and the wait; treats a missing retryable flag as not retryable |
| `src/store/free-tier-sign-in.test.ts` | Tests: free-tier sign-in attempts; a poll from a closed attempt never overwrites the attempt now on screen; free-tier sign-in failure screens; maps the account service verdicts onto ruled screens |
| `src/store/free-tier-sign-in.ts` | Exports `FreeTierSignInFailure`, `FreeTierOfferKind`, `FreeTierSignInState`, `claimFreeTierSignIn`, `releaseFreeTierSignIn`, `freeTierSignInClaim` … |
| `src/store/free-tier.ts` | The model the free-tier route runs on. Used to recognise a session that is still homed on the free tier after a sign-in. |
| `src/store/gateway-activation-epoch-groups.test.tsx` | A real gateway activation can move the activation epoch WITHOUT moving the connectionId / profile / gateway atoms (the primary fast path in ensureGatewayForProfile). Group-capability consumers key their answer on that |
| `src/store/gateway-activation-epoch.ts` | Exports `useGatewayActivationEpoch` |
| `src/store/gateway-activation-prune-lease.test.ts` | Regression suite for #89622: clicking a profile in the rail did nothing. The live-work pruner (pruneSecondaryGateways) disposed the switch target's secondary entry while its socket was still dialing — the target is not… |
| `src/store/gateway-agent-scope.test.ts` | Registry-agent scoping regression (multi-source roster): the active key can name a `conn:<id>::<profile>` scope whose secondaries entry gets evicted by a teardown path (closeSecondaryGateways during a soft gateway switc… |
| `src/store/gateway-background-reconnect.test.ts` | Tests: background remote turn reconnect |
| `src/store/gateway-connection-lifecycle.test.ts` | Connection lifecycle for registry-scoped secondary gateways: 1. Removing a connection must dispose its secondaries — remote/cloud sources have no local process whose death would drop the socket, so |
| `src/store/gateway-connection-scope.test.ts` | Cross-connection event/prune scoping: every registered source exposes a 'default' profile (the roster force-unshifts it), so any consumer keyed by the bare profile name conflates two connected gateways' activity. These |
| `src/store/gateway-dial-failures.ts` | Dial failures the secondary redial ladder (store/gateway.ts reconnectSecondary) treats as permanent for a scoped socket. Electron's getConnectionFor rejects with `No connection with id "…"` when |
| `src/store/gateway-foreground-retention.test.ts` | #93892 regression: the registry disposed the secondary socket an idle Bot Chat tile was bound to — the live-work pruner for a pre-dialed (retained) entry, and the refcount-0 request lease for one the tile's own resume |
| `src/store/gateway-profile-only-owner.integration.test.ts` | Tests: profile-only secondary approval ownership; keeps a profile-only secondary event owner across a focus switch and dispatches the approval.respond fallback on that secondary; rejects unproven profiles and retires on… |
| `src/store/gateway-profile-request.test.ts` | Tests: requestGatewayForProfile; requests through a pooled profile gateway without changing the active gateway; background polls on a down local profile leave redialing to the ladder; a user action still dials (#121865)… |
| `src/store/gateway-reconnect.test.ts` | Tests: gateway reconnect controller; coalesces repeated requests onto one active reconnect; only lets the current registration remove itself; rejects when the gateway boot owner is not mounted |
| `src/store/gateway-reconnect.ts` | Exports `GatewayReconnectSource`, `GatewayReconnectOptions`, `registerGatewayReconnect`, `reconnectGateway`, `reconnectAction` |
| `src/store/gateway-relay-retention.test.ts` | Bot-relay socket retention (#93594): the desktop bot relay RPCs every registered connection on its drain loop through requestGatewayForAgent's per-request lease. With nothing else holding the entry, the refcount hit 0 |
| `src/store/gateway-secondary-open-check.test.ts` | Regression for issue #92265: a transient first-dial WebSocket failure (e.g. ECONNRESET before the socket reaches `open`) must not let Desktop publish the closed gateway as the active route. entry.connection is set |
| `src/store/gateway-shared-remote.test.ts` | The global-remote share (backend routing case 3): every profile is served by the PRIMARY backend over one host, and getConnection() explicitly tags the shared descriptor with `sharedPrimary`. Dialing a second WebSocket… |
| `src/store/gateway-switch.test.ts` | Tests: wipeSessionListsForGatewaySwitch; clears lists and arms loading so sidebar skeletons retrigger; drops the outgoing gateway; leaves the outgoing backend |
| `src/store/gateway-switch.ts` | Exports `GatewaySwitchLifecycle`, `GatewaySwitchToken`, `isCurrentGatewaySwitch`, `registerGatewaySwitchLifecycle`, `beginGatewaySwitch`, `endGatewaySwitch` … |
| `src/store/gateway.test.ts` | Connection lifecycle for registry-scoped secondary gateways: 1. Removing a connection must dispose its secondaries — remote/cloud sources have no local process whose death would drop the socket, so |
| `src/store/gateway.ts` | Exports `SpawnPriority`, `activeGatewayProfileKey`, `configureGatewayRegistry`, `emitLocalGatewayEvent`, `ScopedServerRequest`, `dispatchPrimaryServerRequest` … |
| `src/store/goals.test.ts` | Tests: goal store; stores active goals from /goal output; keeps the current title for continuation and pause messages; lingers done goals before clearing them |
| `src/store/goals.ts` | Exports `GoalStatus`, `SessionGoal`, `setSessionGoal`, `clearSessionGoal`, `applyGoalStatusText`, `refreshSessionGoal` |
| `src/store/haptics.ts` | Exports `setHapticsMuted`, `toggleHapticsMuted` |
| `src/store/hub-actions.blocked.test.ts` | Tests: the current CLI ; the legacy |
| `src/store/hub-actions.test.ts` | A failed hub action (non-zero subprocess exit) must REJECT so callers toast it — the Aug 2026 report shape was a scan-gated/failed `hermes skills install` exiting non-zero with no toast, no list change, and no error |
| `src/store/hub-actions.ts` | The Capabilities Skills-list query key, imported rather than re-spelled so a hub (un)install updates the Skills tab, not just the hub. |
| `src/store/hud.test.ts` | Tests: openHud profile targeting (#82285); carries the session-stamped profile when the target belongs to another profile; falls back to the active gateway profile for an unstamped session; uses the active gateway profi… |
| `src/store/hud.ts` | HUD mode — the chrome-free floating chat. A transparent, frameless, always-on-top window showing nothing but the REAL composer with the reply scrolling above it, so Hermes can be driven while the user works in another a… |
| `src/store/interface-mode.test.ts` | Interface mode is a resolver input, never a preference writer. These tests pin the precedence contract — sessionReveal ?? policy[mode] ?? userPref — and the promise that matters to an existing install: Advanced is a no-… |
| `src/store/interface-mode.ts` | Interface mode: does this window show the machinery, or just the conversation? Two answers. ADVANCED is the app as it has always been — every preference the user set, honoured. SIMPLE is chat-first: the standing |
| `src/store/intro-splash.ts` | Exports `setIntroSplash` |
| `src/store/kanban-connection-scope.test.ts` | A connection switch must leave every profile-scoped query refetched against the NEW gateway — see the $activeConnectionId.listen comment in store/connections.ts for why the switch's own wipe is not enough. |
| `src/store/keep-awake.test.ts` | Tests: keep-awake store; persists the mode and mirrors it to the main process; defaults to while-working on a machine with no preference; migrates the pre-mode toggle: on meant always, off meant off |
| `src/store/keep-awake.ts` | Keep-awake — stop the machine sleeping during long, unattended runs. A device-local preference (each computer keeps its own), 'while-working' by default. This atom backs the Settings → Advanced picker and mirrors change… |
| `src/store/keybinds.test.ts` | Tests: keybinds store persist vs late-registered contributed actions; keeps stored overrides for plugin actions that register after boot; keeps an override written after boot when the plugin unloads and another action i… |
| `src/store/keybinds.ts` | Exports `bindingsFor`, `setBinding`, `clearBinding`, `resetBinding`, `resetAllBindings`, `conflictsFor` … |
| `src/store/layout-connection-scope.test.ts` | Two Desktop windows share one renderer origin (and therefore one localStorage area) while each can be connected to a DIFFERENT gateway. Session/pin lists reconcile against each gateway's own state.db, so any of |
| `src/store/layout-dismissed-projects.test.ts` | Tests: filterVisibleProjects; drops dismissed autos and keeps explicit + home + undismissed; ignores dismiss ids that hit an explicit project; restores a dismissed auto project (Undo round-trip) and is idempotent |
| `src/store/layout-flipped-sides.test.ts` | Loaded once at collection, outside every test's budget: vi.resetModules() keeps each module's transformed code, so the fresh copy a test imports only re-evaluates it. Without this the first test pays the cold transform… |
| `src/store/layout-pinned-order.test.ts` | Tests: setPinnedSessionOrder; applies a full reorder; reorders a subset in place, leaving unresolved pins alone; ignores ids that are not pinned |
| `src/store/layout-sidebar-view.test.ts` | Tests: the sidebar as it ships; remembers expanded project previews across grouping changes and clears them on reset; offers no reset until something actually moves off the defaults; is what reset puts back — every knob… |
| `src/store/layout.ts` | Exports `SIDEBAR_DEFAULT_WIDTH`, `SIDEBAR_MAX_WIDTH`, `FILE_BROWSER_DEFAULT_WIDTH`, `FILE_BROWSER_MIN_WIDTH`, `FILE_BROWSER_MAX_WIDTH`, `SIDEBAR_SESSIONS_PAGE_SIZE` … |
| `src/store/live-sync.ts` | Event-driven "backend data changed" signals — the workspace-events twin for gateway-side state. The change watcher in tui_gateway broadcasts `pet.changed` / `cron.changed` / `sessions.changed` when its on-disk |
| `src/store/local-model-offer.ts` | Install-level: the local-model offer opens at most once per install, and a dismiss is final. |
| `src/store/local-models-flag.ts` | Feature-flag gate for every local-models surface in the GUI. On by default on macOS, Windows, and Linux x64/arm64 (`electron/feature-flags.ts`). Elsewhere the app must be launched with `--local` (`hermes desktop --local… |
| `src/store/local-models-surfaces.test.tsx` | Tests: uses one status polling clock across staggered Settings, picker and menu mounts; keeps paused work alive after Settings unmount and isolates late results by owner; follows an authoritative route change even when… |
| `src/store/local-runtime-jobs.test.ts` | Tests: local runtime jobs store — pause/settle contract; running→error still toasts exactly once; a settle landing after the primary connection moved is bookkept silently, not thrown; publishes a pinned job response int… |
| `src/store/local-runtime-jobs.ts` | Exports `LocalModelsOwner`, `localModelsOwner`, `useLocalModelsOwner`, `localModelsKey`, `isLocalModelsOwnerLive`, `localModelsRequestScope` … |
| `src/store/local-setup-offer.test.ts` | Tests: local-setup offer eligibility; offers the model the catalog recommends; stays quiet on a machine with no recommendation; answers nothing from a read a connection change overtook, never the old machine |
| `src/store/local-setup-offer.ts` | Local-setup eligibility: whether this machine can run a model locally, read once per backend connection from the local-models status + catalog. Two surfaces read it: the "Run locally" row at the top of the model menu (u… |
| `src/store/managed-updates.test.ts` | Tests: runManagedUpdate; routes through the managed drain/update/restore bridge and lands on updated with the receipt; joins a repeat click to the in-flight promise instead of double-dispatching; keeps updated-but-resto… |
| `src/store/managed-updates.ts` | Renderer-side lifecycle of one managed SSH update (#93042 renderer unit, slimmed to what #95942's engine actually exposes today: a single `connections.updateManaged(id)` promise that resolves with a correlated result +… |
| `src/store/mcp-deeplink-install.ts` | Pending `hermes://mcp/install` request awaiting the user's explicit confirmation. Set by the deep-link listener, consumed by `McpInstallDeepLinkDialog`; null means no dialog. Nothing is written to config until the user… |
| `src/store/mcp-health.test.ts` | @vitest-environment jsdom |
| `src/store/mcp-health.ts` | Background MCP health checker. On gateway connect — and every 30 minutes after — probe the ACTIVE profile's enabled HTTP/SSE MCP servers and nudge the user when one is in needs-auth (expired OAuth token) or error: on th… |
| `src/store/memory-status.ts` | Bumped whenever something that changes `GET /api/memory`'s answer lands (config autosave, provider credential save, OAuth completion), so the Memory summary refetches instead of showing the pre-change readiness. |
| `src/store/model-assignment.ts` | Selection-guard warning as a confirm toast. Resolves true on Confirm, false on dismiss. The desktop has no blocking confirm API; this is the same notify-with-action pattern the in-session model picker uses. |
| `src/store/model-presets.test.ts` | Tests: model presets; round-trips a preset and merges patches without dropping prior fields; returns an empty preset for unknown models; keeps Ultrafast distinct and a later legacy Fast edit selects priority |
| `src/store/model-presets.ts` | Exports `ModelPreset`, `modelPresetServiceTier`, `modelPresetKey`, `getModelPreset`, `setModelPreset`, `applyModelPreset` |
| `src/store/model-pricing.ts` | Exports `setShowModelPricing` |
| `src/store/model-visibility.test.ts` | Tests: model visibility; keeps newly configured providers visible when stored choices are stale; does not re-add models the user already judged for a curated provider; shows a model that appeared after the user curated… |
| `src/store/model-visibility.ts` | Exports `DEFAULT_VISIBLE_PER_PROVIDER`, `modelVisibilityKey`, `EMPTY_PROVIDER_SENTINEL`, `emptyProviderSentinelKey`, `isProviderSentinel`, `ModelFamily` … |
| `src/store/nanostores-batch-guard.test.ts` | Regression guard: the desktop's gateway-switch publication runs inside nanostores' batch(). nanostores 1.4.0–1.4.1 annotated batch() with `/* |
| `src/store/native-notifications.test.ts` | Tests: captures durable navigation identity while keeping the runtime id for approval actions; dispatchNativeNotification focus gating; fires a completion notification for the active session when the window is hidden; f… |
| `src/store/native-notifications.ts` | Exports `NativeNotificationKind`, `NATIVE_NOTIFICATION_KINDS`, `NativeNotificationPrefs`, `setNativeNotifyEnabled`, `setNativeNotifyKind`, `NativeNotificationAction` … |
| `src/store/notifications.test.ts` | Tests: gateway_auth_failed error is summarized as sign-in, with an Open Gateways action; provider invalid_api_key error maps to the OpenAI summary and deep-links to Keys; ELEVENLABS_API_KEY not set toasts plain copy wit… |
| `src/store/notifications.ts` | Exports `NotificationKind`, `NotificationAction`, `NotificationPlacement`, `AppNotification`, `NotificationInput`, `isDiskFullErrorMessage` … |
| `src/store/notify-baseline.ts` | Post-connect quiet window for native (OS) notifications. A socket opening replays state that already existed: a session parked on an approval re-emits its request so the UI can render the prompt. Those are not |
| `src/store/onboarding-decide.test.ts` | Loaded once at collection, outside every test's budget: vi.resetModules() keeps each module's transformed code, so the fresh copy a test imports only re-evaluates it. Without this the first test pays the cold transform… |
| `src/store/onboarding-intro.ts` | The first-run intro as this window shows it, in memory only: whether it runs at all is the backend's `onboarding.state`. `starting` holds the boot overlay while the setup chat opens, `intro` is the setup chat in the dem… |
| `src/store/onboarding-owner.test.ts` | Tests: cancels on the original owner after the foreground changes; cancels a late OAuth start on its retired owner, not a newly opened flow; pins local-endpoint validation and persistence to the setup owner; preserves e… |
| `src/store/onboarding-phase.ts` | Where first-run onboarding is: `shown` while it runs, then how it ended. Funnel telemetry reads it. |
| `src/store/onboarding-presence.ts` | Exports `ONBOARDING_DECIDE_OFFER_MS`, `markOnboardingDecided`, `setOnboardingSurfaceActive`, `onboardingSurfaceActive`, `onboardingSurfaceOpen`, `afterOnboardingSurfaceClear` |
| `src/store/onboarding-run.test.ts` | Tests: onboarding run; opens the onboarding chat when due and never shows a clear moment before it; keeps the run on a reconnect in the same launch: it is re-read, never started again; ends once when the backend reports… |
| `src/store/onboarding-run.ts` | First-run onboarding as this window runs it: one chat in the default profile, opened by the backend's `onboarding.start`, ended by the answer to the first-task card or by Skip setup. This module is the one writer of `$o… |
| `src/store/onboarding-scope.ts` | Exports `OnboardingScope`, `captureOnboardingScope`, `requestOnboardingGateway` |
| `src/store/onboarding-session.ts` | Exports `OnboardingSession`, `isOnboardingChat`, `onboardingChatStore` |
| `src/store/onboarding.test.ts` | Tests: refreshOnboarding; keeps onboarding work in its initiating lifetime and profile; refreshes OAuth providers again when onboarding was explicitly requested; shows no sentence of its own over the picker when nothing… |
| `src/store/onboarding.ts` | Exports `OnboardingMode`, `OnboardingSignedIn`, `OnboardingFlow`, `DesktopOnboardingState`, `OnboardingContext`, `DEFAULT_ONBOARDING_REASON` … |
| `src/store/owner-queue-reconcile.test.ts` | Pass-through: records which profile's own backend a read is routed to. |
| `src/store/owner-queue-reconcile.ts` | Exports `sessionsWithOwnerWork`, `reconcileOwnerQueues`, `watchOwnerQueues` |
| `src/store/pane-focus.ts` | Explicit-request pane reveals, keyed to the backend `focus_pane` tool. Each entry drives the pane's own reveal path (some are toggle-bound) so a revealed pane matches a user-driven open. files/review are workspace-gated… |
| `src/store/panes.test.ts` | Tests: panes store; ensurePaneRegistered; is a no-op when the pane already exists; preserves an existing widthOverride when re-registering |
| `src/store/panes.ts` | Exports `PaneStateSnapshot`, `PaneRegisterDefaults`, `ensurePaneRegistered`, `setPaneOpen`, `togglePane`, `setPaneWidthOverride` … |
| `src/store/parked-card-answers.test.ts` | Tests: parked card answers; stops at the first card that takes the text, and forgets a card once it unregisters; reports an answer that failed to send, so the composer can restore the draft; takes typed text for an onbo… |
| `src/store/parked-card-answers.ts` | Answers a card parked on `sessionId` with composer text: null when no card of this kind takes it, else a promise of whether the answer reached the backend. |
| `src/store/pending-submissions-windows.test.ts` | Chromium gives each renderer process its own cached copy of the origin's localStorage and propagates writes asynchronously, last writer wins per key. Two windows: each writes against its own (stale) view, then the copie… |
| `src/store/pending-submissions.test.ts` | Tests: projects resumed runtime pending receipts under durable identity without making them sendable; carries the queued-row controls the owner lists onto the card, and none when it lists none (RT-35); a steer in transf… |
| `src/store/pending-submissions.ts` | One localStorage key per (session, admission). Every Desktop window of the origin shares this storage with last-writer-wins per KEY, so a single journal blob let one window's read-modify-write silently drop an entry ano… |
| `src/store/pet-gallery.test.ts` | Tests: pet gallery pet.info sync; uses pet.info.meta and keeps the cached spritesheet when the revision is current; fetches full pet.info when metadata reports a new spritesheet revision; falls back to full pet.info whe… |
| `src/store/pet-gallery.ts` | Exports `GalleryPet`, `PetGallery`, `PetGalleryStatus`, `GatewayRequest`, `TOGGLE_ON`, `TOGGLE_OFF` … |
| `src/store/pet-generate.ts` | Feature store for the "generate a pet" flow (Cmd-K → Pets → Generate). Three backend steps, mirrored as state here: - `pet.generate` produces N cheap base-look *drafts* keyed by a `token`. - `pet.hatch` turns the chosen… |
| `src/store/pet-overlay.ts` | Controller for the pop-out pet overlay (main-renderer side). Shift-clicking the in-window pet "pops it out" into a transparent, always-on-top OS window (created in electron/main.ts) that can leave the app's bounds and s… |
| `src/store/pet-plugin-messages.ts` | Plugin lines for the pet's speech bubble — the store behind `ctx.pet.say`. A plugin hands the host a short plain-text line; the host owns where and when it shows (the core `PetBubble`, in-window and in the pop-out overl… |
| `src/store/pet.test.ts` | Tests: derivePetState; rests at idle by default and uses waiting when awaiting input; runs when busy or a tool is executing; reviews while reasoning (below tool, above bare busy) |
| `src/store/pet.ts` | Petdex mascot state for the desktop floating pet. The spritesheet payload comes from the gateway `pet.info` RPC (shared with the TUI). The animation *state* is derived here from the same activity signals the chat alread… |
| `src/store/plugin-catalog-install.test.ts` | @vitest-environment jsdom |
| `src/store/plugin-catalog-install.ts` | THE way a curated-catalog pick reaches the Install Plugin dialog. The Plugins tab's embedded picker and the `hermes://plugin/install?catalog=` deep link both land here, so a link opens exactly the reviewed/pinned dialog… |
| `src/store/plugin-install-request.ts` | Which plugin component(s) a legacy deeplink pre-selects after probe. |
| `src/store/plugin-preview-grants.ts` | USER GRANTS FOR `ctx.preview.executeJavaScript` — which plugin may run script in the preview Browser on which page origin. The preview pane can hold pages the user is signed in to, so script there reads session data. A… |
| `src/store/power.ts` | AC ↔ battery mirror of the main process's powerMonitor. Backstop polls are already event-demoted and visibility-gated; battery is the third gate — on battery their cadence stretches (×4) so a laptop running Hermes in th… |
| `src/store/preview-edit.ts` | URLs of preview targets that have unsaved spot-editor changes, keyed by `target.url` so the rail can render a VS Code-style "modified" dot on the tab without threading editor state up through the pane. The editor in |
| `src/store/preview-explicit.ts` | An explicit preview open (tool or user `openPreview`) must survive a later `follow()` from a zone the user was already in. `follow()` copies that zone's tab into `$rightRailActiveTabId`; when the opened pane lives in a… |
| `src/store/preview-open-browser.test.ts` | Tests: openBrowserTab; opens a blank browser when there is no browser tab yet; re-fronts the existing page instead of blanking it; shows the browser it already has rather than stacking duplicates |
| `src/store/preview-ownership.ts` | PREVIEW TAB OWNERSHIP — who a preview tab belongs to. A tab is owned by the stored session that opened it (resolved through every compression rotation), or — before that session's stored id exists — by the runtime that… |
| `src/store/preview-persistence.test.ts` | Tests: persisted preview migration; upgrades a pre-PDF remote tab from binary to pdf; leaves a persisted non-PDF binary tab unchanged; does not overwrite a non-binary PDF preview kind |
| `src/store/preview-status-edge-cases.test.ts` | Tests: retains a close when the same runtime owner is refined from profile-only to an exact route; tolerates malformed persisted scope keys and keeps Windows aliases identical |
| `src/store/preview-status-lifecycle.test.ts` | Tests: moves local dismissals on rename and removes only the deleted owner; keeps a close effective in memory when storage writes fail; honors a durable close after module reload |
| `src/store/preview-status.test.ts` | Tests: recordPreviewArtifact; appends new targets newest-last and is idempotent; caps the list and derives a label; dismiss and clear remove rows |
| `src/store/preview-status.ts` | Session-scoped feed of previewable artifacts (HTML files, localhost dev URLs) a tool produced. Surfaced as compact links in the composer status stack — NOT auto-opened and NOT a bulky inline card. Click opens the rail p… |
| `src/store/preview-tabs-scope.test.ts` | Regression: the right rail's tabs were persisted under ONE global key (`hermes.desktop.previewTabs.v2` holding a bare array), so a preview opened in one agent's chat appeared in every other agent's chat — Tess's model s… |
| `src/store/preview-toggle-browser.test.ts` | Tests: toggleBrowserTab; opens a blank browser when there is no browser tab yet; dismisses the visible browser pane but keeps its tab; re-fronts the existing page instead of blanking it |
| `src/store/preview.test.ts` | Tests: preview store; does not notify status subscribers for restart progress text; opens the pane and fronts the new tab; gives every kind of target its own tab, side by side |
| `src/store/preview.ts` | Exports `PreviewRenderMode`, `PreviewTarget`, `PreviewServerRestart`, `PreviewTab`, `decodePreviewTabs`, `setPreviewScope` … |
| `src/store/profile-agent-activation.test.ts` | Registry-agent activation (ensureGatewayAgent — the SDK ensureAgent door). Two regressions pinned here: 1. Activating an ALREADY-OPEN registry agent must still resync |
| `src/store/profile-cache.test.ts` | Tests: keeps failed incoming profile reads isolated while retaining the outgoing connection cache; lets a fresh active-source list land even when the fleet roster arrives first; treats a null descriptor as a reconnect b… |
| `src/store/profile-dot-state.test.ts` | Tests: profile rail dot state ($profileDotStateByScope); lights the inactive profile; ranks needs-input over working within one profile; ranks working over unread within one profile |
| `src/store/profile-dot-state.ts` | PROFILE DOT STATE — the profile rail's per-profile rollup of the shared session dot state ($sessionDotStateById), so a profile that finished (or blocked, or is still working) while another profile was selected shows an… |
| `src/store/profile-launch-native.test.ts` | The twin of profile-launch-webapp.test.ts: only a browser host starts on its server's profile. Electron's preload installs the bridge before any renderer module evaluates, so native Desktop starts on `default` even if a… |
| `src/store/profile-launch-webapp.test.ts` | A Webapp tab's one socket answers for the profile its gateway runs as, and the gateway refuses a request naming a profile it does not serve (`profile_mismatch`). Boot requests that name the tab's profile (approval mode,… |
| `src/store/profile-rail-prefs.test.tsx` | @vitest-environment jsdom Loaded once at collection, outside every hook's budget: vi.resetModules() keeps each module's transformed code, so the fresh copy a test imports only re-evaluates it. Without this each |
| `src/store/profile-rail-prefs.ts` | The colored profile strip at the sidebar foot. For someone who runs profiles as bots it duplicates the footer's gateway selector, so it can be switched off; while it is off the statusbar grows a profile dropdown beside… |
| `src/store/profile-remote-override.test.ts` | Tests: remoteHostLabel; keeps a non-default port and drops default ones; returns empty for unparseable input; refreshProfileRemoteOverrides |
| `src/store/profile-remote-override.ts` | ── Per-profile remote overrides (connection.json `profiles.<name>`) ──────── The Electron main already routes a profile with a remote entry to its own pooled backend (profileRemoteOverride → resolveProfileBackendRoute c… |
| `src/store/profile-select-source.test.ts` | Picking a profile must stay on the source the user is LOOKING at. $profiles is the active gateway's list, so a pick made while a registry source is live names one of THAT source's profiles. Routing it through the profil… |
| `src/store/profile-select-webapp-served.test.ts` | Every socket the store builds besides the tab's own (the primary each test installs). |
| `src/store/profile-select-webapp.test.ts` | A live profile switch in a Webapp tab is recorded in THAT tab's URL, so a reload lands on the profile the user is in, and a generic New session follows it. It is not the origin's saved default (only "Set as default" |
| `src/store/profile-share.test.ts` | Keep side-effecting transitive imports inert (gateway sockets, REST). |
| `src/store/profile-share.ts` | Profile share: export/import a profile as a portable bundle. The archive is the CLI's own `hermes profile export` tar.gz (config, skills, SOUL.md, cron — credentials always excluded), plus one desktop-only file at the r… |
| `src/store/profile-switch-failure.test.ts` | Profile-door activation failure surfacing (#81094): when a secondary's socket cannot be opened, ensureGatewayForProfile must rethrow (after arming the reconnect schedule) so the caller can surface the failure, |
| `src/store/profile.test.ts` | Keep profile.ts's side-effecting imports inert: the gateway socket layer and the REST query client must not run for real in a unit test. |
| `src/store/profile.ts` | Exports `normalizeProfileKey`, `profileLabel`, `setActiveProfile`, `invalidateProfileListFetches`, `refreshProfiles`, `setProfileOrder` … |
| `src/store/project-scope.ts` | ── Project scope (the "you're inside a project" view, mirroring profile scope)─ The sidebar's grouped view is a project switcher: ALL_PROJECTS shows the project overview (a list you drill into), and a concrete id means… |
| `src/store/project-tree.ts` | The project tree atom lives in this leaf so store/session-states.ts can read it (a focused tile's session is often older than the paginated recents page, so the tree is the only loaded copy of its row, #76535) without |
| `src/store/projects-connection-tag.test.ts` | Tests: project session connection provenance; tags tree-only overview and hydrated rows across Home → local → Home; tags the all-profiles tree without replacing each row profile; leaves This device rows bare on the prim… |
| `src/store/projects.test.ts` | Tests: project scope; enterProject scopes the sidebar to the project id; exitProjectScope returns to the overview; entering the synthetic Home bucket still scopes (no active pin) |
| `src/store/projects.ts` | Exports `enterProject`, `projectRootCwd`, `goToProject`, `resolveNewSessionCwd`, `followEnteredProjectCwd`, `projectIdForCwd` … |
| `src/store/prompts.test.ts` | Tests: approval prompt store; parks a background session prompt out of the active view; clears the active session prompt; correlates clearing to the exact approval request id |
| `src/store/prompts.ts` | Blocking interactive prompts the gateway raises mid-turn. Each is a server→client JSON-RPC request (`tui_gateway/server_requests.py`) the Python side blocks on; `requestId` is that request's id and the card answers thro… |
| `src/store/provider-collapse.ts` | Exports `toggleCollapsedProvider` |
| `src/store/provider-wait.test.ts` | The load-notice string is minted by the backend (agent/chat_completion_helpers._managed_local_load_notice) and parsed here — these tests pin the desktop side of that cross-language contract |
| `src/store/provider-wait.ts` | Exports `sessionProviderWait`, `setSessionProviderWait`, `clearSessionProviderWait`, `clearAllProviderWaits`, `providerWaitText`, `parseModelLoadWait` |
| `src/store/pull-requests.ts` | How a row's PR reads at a glance — and what the sidebar filters on. A session with no branch, no PR, or an unreachable `gh` is `none`. |
| `src/store/quick-entry.test.ts` | Tests: quickComposerReducer; starts visible, empty, DISCONNECTED, and targeting the current chat; submit sends the trimmed draft but waits for acknowledgement to clear and hide; submit-error keeps the draft visible, rec… |
| `src/store/quick-entry.ts` | Quick Entry (renderer side) — the mini composer's own state, and the primary window's bridge back into the real prompt-submit path. The quick window carries NO gateway connection: it hands its text to the main process,… |
| `src/store/reactions-enabled.ts` | Message reactions (iMessage-style tapbacks) — opt-in. Off by default: reactions add affordances to every message row (the ☺ slot, right-click pickers, :shortcode: completions), and the agent gains a tool that reacts to… |
| `src/store/reactions-local.test.ts` | Tests: live reaction overlay scope; a real message.reaction event records into the overlay scoped to its source, and merge prefers it over persisted; a foreign source never sees the overlay: its persisted reaction at th… |
| `src/store/reactions-local.ts` | Reactions the user has set in THIS window, keyed by renderer message id. The UI owns this outright. A tapback is a direct manipulation — it flips the instant you click it, with no round-trip, no gateway, and no dependen… |
| `src/store/reactions.test.ts` | Tests: applyReaction; adds a reaction to an empty message; replaces the same author’s existing reaction (one per author); retracts when the live reaction is re-sent |
| `src/store/reactions.ts` | The six iOS Tapback defaults, in Apple's order. |
| `src/store/read-only-transcript.test.ts` | Tests: read-only stored-transcript resume (#94724 no-owner recovery); opens the stored transcript read-only when the owner fails closed on a 2-connection topology; stays live (and clears the latch) when the owner resolv… |
| `src/store/read-only-transcript.ts` | Read-only stored-transcript resume — the no-owner recovery path (#94724). The fail-closed owner ladder is correct: a session-scoped RPC whose owner nobody can name must NOT ride the ambient socket. But "fail closed" mus… |
| `src/store/real-profile-consent.ts` | One-time consent prompt for real-profile browsing, shown when a Browser pane opens while `browser.use_real_profile` is off. Mirrors the embed consent split: "Don't show again" persists across launches; "Not now" |
| `src/store/reasoning-disclosure.test.ts` | Tests: localShowReasoning; reads the local per-platform key over the global one; falls back to the global key, and ignores other platforms |
| `src/store/reasoning-disclosure.ts` | Exports `setReasoningCollapsedByDefault`, `setShowReasoningFromConfig`, `localShowReasoning` |
| `src/store/reasoning-effort-wire-scope.test.ts` | Tests: reasoning-effort wire scope; drops the wire stamp when the model changes, so a stale arrow is not presented as confirmed; keeps the stamp across a heartbeat that mirrors the runtime model |
| `src/store/recovery-requests.ts` | Recovery intents raised from surfaces that have no React Router context or no knowledge of the active profile — chiefly notification action buttons fired from stores. The shell controller (`app/contrib/wiring.tsx`) owns… |
| `src/store/review.test.ts` | Tests: refreshReview; is a no-op that clears state when the pane is closed; flags not-a-repo (and clears loading) when there is no bridge/cwd; populates the changed-file list from the bridge |
| `src/store/review.ts` | State for the review pane: the working-tree changed-file list, the selected file's diff, and the git mutations (stage / unstage / revert). The active session's cwd is the repo; the pane reads git as the source of truth,… |
| `src/store/right-side-toggle.test.ts` | Tests: positional right-side toggle; folds the rightmost side column (the browser) to a minimized rail; round-trips: a second press restores the zone; leaves the left stack (sessions+files) untouched |
| `src/store/route-tiles.ts` | Route (page) tiles — a full-page view (Capabilities / Messaging / Artifacts, or any plugin route) rendered as a layout-tree pane BESIDE the main thread, the page analog of session tiles. Persisted by path so they re-ope… |
| `src/store/runtime-gone.test.ts` | Tests: markRuntimeGone; unbinds the tile holding the dead runtime so its resume effect refires; asks the primary chat to resume when the dead runtime is the one on screen; does not navigate the primary chat for a tile-o… |
| `src/store/runtime-gone.ts` | Exports `markSessionGone`, `noteRuntimeAlive`, `markRuntimeGone`, `resetRuntimeGoneHealing` |
| `src/store/send-diagnostics.test.ts` | Tests: send-diagnostics store; opens in consent phase without any network I/O; uploads on confirm, attaching error context and the local desktop log; omits extra_files when the desktop IPC is unavailable (browser dashbo… |
| `src/store/send-diagnostics.ts` | "Send Diagnostics" — the error card's consent-gated debug-bundle upload. Flow: an error card (or any surface) calls requestSendDiagnostics() with optional error context → the modal host renders the privacy notice → the |
| `src/store/server-requests.ts` | Live server→client requests (`tui_gateway/server_requests.py`) keyed by request id: clarify / approval / sudo / secret / vault / MCP-setup cards. The per-session prompt stores keep only the id; a card answers through `r… |
| `src/store/session-color.test.ts` | Tests: $sessionColorById; maps each session under a colored project to that color, keyed by live id; recomputes when the projects list changes (color applied later); $sessionColorOverrides |
| `src/store/session-color.ts` | Per-session color OVERRIDES — a user-picked color that wins over the inherited project color (#66565 layer 2). Desktop-local like pins, keyed by the DURABLE lineage id so a color survives auto-compression's session-id r… |
| `src/store/session-control.test.ts` | Tests: session-control store; parses the exact persisted goal, loop, heartbeat, and wait-barrier shapes into fresh data; falls back once on the unsupported transition and suppresses future compatibility retries; retains… |
| `src/store/session-control.ts` | Exports `SessionControlGoalStatus`, `SessionControlLoopMode`, `SessionControlLoopStatus`, `SessionControlHeartbeatStatus`, `SessionControlGoalContract`, `SessionControlGate` … |
| `src/store/session-dot-state.test.ts` | Tests: showsRunningArc; keeps the arc when an authoritative turn goes quiet; yields to the needs-input treatment rather than running both; leaves a session that is not running unmarked |
| `src/store/session-dot-state.ts` | SESSION DOT STATE — one map from session id to the single status a surface should paint, so the sidebar, the pane tabs, and the switcher can never disagree about what a session is doing. It exists for two reasons the in… |
| `src/store/session-event-provenance.ts` | A profile name received over the wire is descriptive, not an ownership claim: primary and arbitrary synthetic events can carry one. The secondary socket closure is the authority for profile-only pool routes, so stamp its |
| `src/store/session-focus.ts` | A chat surface: the primary's workspace or a session tile. Everything else a zone can show — the sessions list, Files, Terminal, a preview tab — is chrome. |
| `src/store/session-gone-latch.ts` | Session ids the gateway has told us are gone. A session-scoped RPC against a runtime the gateway no longer holds fails 4001 "session not found" — terminal for THIS runtime id, not a transient socket loss. Shared by ever… |
| `src/store/session-list-density.test.ts` | Tests: session list density preference; defaults to compact (pre-density behavior) and persists changes; falls back to compact for an unknown stored value |
| `src/store/session-list-density.ts` | Exports `SessionListDensity`, `setSessionListDensity` |
| `src/store/session-no-reply.ts` | Raised only after the backend confirmed the turn is over and no reply reached this window, so Retry cannot run the prompt twice. |
| `src/store/session-owner-holds.ts` | ── Owner hold across the create → foreground gap ─────────────────────────── A routed session.create returns a stored id on the owner's socket, but the surface that will PIN that socket (the selected primary thread, or… |
| `src/store/session-owner-resolution.test.ts` | Tests: session owner topology; fails closed while the modern registry bridge is present but its async cache is not loaded; fails closed on an unknown owner in registry topology while preserving legacy profile routes |
| `src/store/session-owner-resolution.ts` | Fail-closed owner resolution for session-scoped RPCs. A request that carries a `session_id` only means anything on the backend that OWNS that session. When every rung of the owner ladder (tile route → exact owner hint →… |
| `src/store/session-pane-focus.test.ts` | These app-lifetime watchers have no unsubscribe API. Install them once in Vitest's isolated file graph, not once per case (which accumulates listeners). |
| `src/store/session-pin-connection-scope.test.ts` | Tests: desktop pin list is connection-scoped, not profile-scoped; keeps the pin storage key stable across a profile switch; still isolates pin sets between two different remote gateways; lets an unpin survive a profile… |
| `src/store/session-pin-sync.test.ts` | Tests: watchSessionPins; mirrors a new pin as pinned=true with the row profile; mirrors an unpin as pinned=false; defers a pin whose row is not loaded, then flushes once it appears |
| `src/store/session-pin-sync.ts` | Reconcile the sidebar's pins with the backend "keep" flag, both directions. Pins drive the sidebar UI out of `$pinnedSessionIds` (localStorage), but the durable record is `sessions.pinned` in each profile's state.db. Tw… |
| `src/store/session-removal.test.ts` | Tests: isSessionRemovalPending; is true for a tombstoned id and for one whose delete RPC is still in flight; goes false again when a failed delete rolls the row back; ignores blank ids rather than treating them as pendi… |
| `src/store/session-removal.ts` | Client-side cache eviction (Apollo-style optimistic layer): ids the user just deleted/archived. The backend tree is a snapshot that still lists them until its next refresh, so the render-time overlay strips these so the… |
| `src/store/session-request-router.test.ts` | Regression coverage for the #89206 wake-failure class: session-scoped RPCs routed to a backend that does not own the session's profile. Three layers: 1. The registry publishes the ACTIVE route's profile ($activeGatewayR… |
| `src/store/session-request-router.ts` | The ONE authoritative exact owner of a session: the registry connection whose socket minted (or resumed) the runtime, plus the Desktop profile that selects that route. `targetProfile` is the backend profile the route se… |
| `src/store/session-sidebar-focus.test.ts` | Loaded for its primary-follow wiring: a new primary selection re-fronts the workspace, which the last case asserts through the focus derivation. |
| `src/store/session-states-eviction.test.ts` | Tests: publish-time eviction; releases an unreferenced settled transcript while keeping status and its unread dot; does not mark an external messaging completion unread; marks a background profile local completion unrea… |
| `src/store/session-states-foreground-scopes.test.ts` | Tests: foregroundSessionScopes: owner hold across the create → foreground gap; names the owner from the moment a routed create returns, before anything is selected or tiled; retires once the foreground publication cover… |
| `src/store/session-states-interrupted-settle.test.ts` | Tests: settling a deliberately interrupted live turn; never paints a retryable no-reply card for an interrupted turn; still offers the retry card when an uninterrupted turn ends with no reply |
| `src/store/session-states-profile-rename.test.ts` | A profile rename keeps its sessions: every localStorage family keyed by the old profile name must move to the new one, or the restored tabs dial a backend that no longer exists and 404 forever (#111868). Loaded once at… |
| `src/store/session-states-reconnect.test.ts` | Tests: reconcileBusyStatesOnReconnect; clears a stale busy session on primary reconnect; retires the clock and live claim when the backend cannot finish a pending bubble; disarms the stall watchdog with the busy claim |
| `src/store/session-states-runtime-map.test.ts` | Tests: storedSessionIdForRuntimeId; maps a runtime id to the stored id of the tile bound to it; passes a stored id through unchanged (callers may hold either identity); returns null for an unknown id so the caller falls… |
| `src/store/session-states-scopes.test.ts` | Tests: liveSessionScopes; maps a registry-tagged busy session to its composite scope; keeps an explicit local registry session on its composite scope; includes needs-input sessions and drops settled ones |
| `src/store/session-states.test.ts` | Tests: foregroundSessionScopes; keeps the exact registry owner of an idle foreground runtime; fails closed when the foreground runtime has no registered source; keeps every open pane owner, not only the focused runtime |
| `src/store/session-states.ts` | MULTI-SESSION VIEW STATE — the reactive face of the per-runtime session cache (`sessionStateByRuntimeIdRef` in use-session-state-cache). The cache already ingests EVERY session's gateway events; only the view was single… |
| `src/store/session-switcher.test.ts` | Tests: openOrAdvanceSwitcher; does nothing with fewer than two sessions; jumps immediately on a quick Tab tap without opening the HUD; does not open the HUD when Ctrl stays down but Tab was released quickly |
| `src/store/session-switcher.ts` | Mac-style session switcher (^Tab). Quick tap jumps on keydown; the HUD opens only when Tab is held past REVEAL_MS or tapped again while Ctrl is down. |
| `src/store/session-sync.ts` | Cross-window session-list sync. Each desktop window is its own renderer process with its own gateway socket and session store, so a mutation in one (e.g. a new chat started in the compact pop-out) never reaches another |
| `src/store/session-tile-order.ts` | Reorder tiles to match layout-tree encounter order (stored ids in the order their `session-tile:` panes are walked). Restore replays the array through sequential adoption (each center tile APPENDS after the ones before… |
| `src/store/session-tiles-connection-scope.test.ts` | Tests: session tiles across registered backend switches (#120106); keeps each same-named profile on its own connection and restores its tabs on return; migrates legacy remote-owned tabs out of a profile-only bucket |
| `src/store/session-unread-remote.test.ts` | Tests: markSessionUnread; optimistically paints the row, then PATCHes with the owning profile; no-ops for a runtime-only session with no persisted row; rolls back the row and rethrows when the PATCH fails |
| `src/store/session-unread-remote.ts` | Persisted unread flag sync (backend read-state watermark via PATCH /api/sessions/{id} → SessionDB.set_session_read). The sidebar's dot is fed by TWO sources (see session-dot-state.ts): the runtime "turn finished in back… |
| `src/store/session-unread-tile.test.ts` | Cold transforms belong to collection, not the first unread assertion's budget. |
| `src/store/session-unread.test.ts` | Tests: persisted unread (session-unread); reconstructs the green dot from a seen watermark after a cold start; seeds the watermark on first sight instead of painting every row green; keeps a live-edge marker across a tr… |
| `src/store/session-unread.ts` | Exports `noteDesktopAdmission`, `lightDesktopMessagingCompletion`, `noteLiveSessionSource`, `isMessagingCompletion`, `markSessionUnreadFinished`, `ackStoredSessionId` … |
| `src/store/session-watchdog.test.ts` | Tests: session watchdog; marks a silent session stalled without pretending it finished; clears stalled on new activity and rearms the watchdog; clears both running and stalled on an authoritative terminal transition |
| `src/store/session.test.ts` | Tests: composer model persistence scope; keeps manual model selections isolated by remote connection and profile; keeps inferred local-primary connections on the historical bare keys; uses the live registry owner when t… |
| `src/store/session.ts` | Exports `ComposerModelSource`, `_resetLegacyDiscardForTests`, `getRememberedSessionId`, `setRememberedSessionId`, `migrateRememberedNavigationForProfile`, `migrateSessionOwnerHintsForProfile` … |
| `src/store/settings-scope.test.ts` | Keep store/profile's side-effecting imports inert — same seam as store/profile.test.ts. |
| `src/store/settings-scope.ts` | ── Shared settings "Applies to" scope ────────────────────────────────────── One selection shared by every config-backed settings page (Model, Workspace, Safety, Memory & Context, Voice, Tools & Keys) and the Messaging… |
| `src/store/setup-beat.test.ts` | Tests: setup_beat card; takes composer text as the user words and closes, and a stale cancel leaves a newer card; reports a card waiting on the session while a beat is parked, and none once it settles; leaves a message… |
| `src/store/setup-beat.ts` | Open `setup_beat` requests: the onboarding chat's card for one beat, one per session. The setup_beat tool row reads this to draw the beat's card. A pick answers the request with `{answer}`. Composer text answers only th… |
| `src/store/shared-metrics.ts` | Public page describing exactly what shared metrics contain and how consent windows work. |
| `src/store/sidebar-archive.test.ts` | Tests: loadArchivedSessions; keeps same-id archived sessions from different profiles across pages; keeps the last successful result when a refresh fails; does not publish the previous connection rows after a switch mid-… |
| `src/store/sidebar-archive.ts` | The backend's `/api/profiles/sessions` page cap (`le=500`). The Electron merge path (remote profiles, registry gateways) answers every page by re-reading the prefix through offset + limit, so fewer, larger pages keep a |
| `src/store/sidebar-collapse-persistence.test.ts` | Ground-truth repro for "hiding the sidebar doesn't persist on reload": drive the REAL stores, then re-import them (fresh module state reading persisted localStorage) to simulate a ⌃R reload. `bind` mirrors the controlle… |
| `src/store/sidebar-nav.test.ts` | Tests: applySidebarNavPrefs; unions hides, lets the first order win, and keeps the capabilities row; reads contributions in registry order: lowest |
| `src/store/sidebar-nav.ts` | Sidebar-nav preferences — the `sidebarNav.prefs` registry area. A plugin (the sidebar manager) hides nav rows or re-orders them by CONTRIBUTING a preference; core still owns rendering and merges every contribution at |
| `src/store/sidebar-sort.test.ts` | Tests: $sidebarSessionRankIds; ranks the priciest session first; ranks by total tokens, both halves counted; ranks by creation, newest first — the sidebar orders by recency elsewhere |
| `src/store/sidebar-sort.ts` | Same array on every recompute, so the default (unranked) sidebar never churns its subscribers. |
| `src/store/skill-deeplink-install.test.ts` | Tests: skill link installation; shows the exact source and readable destination, and cancellation installs nothing; uses the registered remote name without changing the install destination; keeps a failed action retryab… |
| `src/store/skill-deeplink-install.ts` | The URL supplies only an identifier, never a destination profile or scan override. |
| `src/store/starmap.test.ts` | Tests: loadStarmapGraph; drops the previous profile graph when a reset lands mid-load; keeps the newer in-flight slot when the stranded load settles first; serves the cached graph without refetching |
| `src/store/starmap.ts` | On-demand cache for the star map. The graph scan touches the skills catalog + usage ledger + memory files, so we fetch it only when the panel opens (and on an explicit refresh), never on a turn boundary. |
| `src/store/statusbar-prefs.test.ts` | Tests: statusbar whole-bar visibility; shows the bar on a fresh install and for installs that hid it under the v1 key; still honours a hide made after the update; statusbar hidden items |
| `src/store/statusbar-prefs.ts` | v1 (`hermes.desktop.statusbarHidden`) was seeded with the approval pill hidden, so every existing store carries an `approval-mode` the user never chose. v2 seeds from v1 minus that id: other customizations survive, the |
| `src/store/stream-delta-flush.ts` | Lets a mid-turn boundary (an accepted steer) paint the session's buffered stream deltas before it seals the live bubble, so text the user had already been sent never lands on the far side of the boundary. The stream hoo… |
| `src/store/subagent-snapshot.test.ts` | Tests: hydrates last tool activity without claiming it is active and preserves stream history on refresh |
| `src/store/subagents.test.ts` | Tests: subagent store; upserts subagent progress and keeps terminal status stable; accepts a terminal subagent.complete for an interrupted session, and still drops live progress; keeps completed children retired across… |
| `src/store/subagents.ts` | Exports `SubagentStatus`, `SubagentStreamKind`, `SubagentStreamEntry`, `SubagentProgress`, `SubagentNode`, `SubagentPayload` … |
| `src/store/system-actions-signed-out-status.test.ts` | Tests: confirmSharedGatewayRestart on a signed-out status read; re-reads after a gated request and still asks before restarting the shared multiplexer; reads a full status once |
| `src/store/system-actions.test.ts` | The REST layer is the only seam these flows own; the confirm dialog and notifications stay real. getStatus answers a standalone gateway so confirmSharedGatewayRestart() takes the silent no-dialog path. |
| `src/store/system-actions.ts` | Exports `confirmSharedGatewayRestart`, `runGatewayRestart`, `watchGatewayRestartOutcome` |
| `src/store/tabstrip-prefs.ts` | Exports `TabStripDefault`, `setTabStripDefault`, `effectiveTabStripMode` |
| `src/store/terminal-backend-warning.test.ts` | Tests: a selected non-local backend that is not ready warns once with Use Local / Open settings; local or ready backends and probe failures stay silent |
| `src/store/terminal-backend-warning.ts` | Proactive warning when the selected terminal backend (Docker, SSH, …) fails its probe. Without this the only signal is a "Needs setup" pill inside Skills → Tools → Terminal, so the user learns that shell commands cannot… |
| `src/store/text-direction.ts` | How chat prose and the composers pick their base direction. - `auto`: each block resolves its own direction from its first strong character (the `unicode-bidi: plaintext` rules in styles.css). This is the shipped behavi… |
| `src/store/theme-pick.ts` | Open `theme.pick` requests (the set_theme picker card), one per session. The card in the tool row reads this to draw the picker; a pick applies the value at once and answers the request with what was applied. The backen… |
| `src/store/thread-scroll-restore.test.ts` | Tests: shouldReapplyFrozenThreadScrollOffset; does not re-pin a frozen offset when only composer clearance / viewport box resized; does not rewrite when a settled offset sees a no-op / same-transcript resize; re-pins wh… |
| `src/store/thread-scroll.test.ts` | Tests: publishThreadAtBottom; lets the visible pane flash the jump pill when the thread leaves the bottom; lets a stalled reader un-dim the composer while the jump pill stays; ignores stick-to-bottom misses from a hidde… |
| `src/store/thread-scroll.ts` | "Is the thread parked at the bottom" is owned by use-stick-to-bottom inside ThreadMessageList (the scroll container). That state lives only in that subtree, so ThreadMessageList mirrors it into these atoms for the compo… |
| `src/store/thread-timeline.test.ts` | Tests: thread timeline preference; keeps bars visible by default and remembers both choices across reloads |
| `src/store/thread-timeline.ts` | Exports `setHideThreadTimeline` |
| `src/store/tips.test.ts` | Tests: agent tip retirement; does not show the same agent tip again after the user retires it |
| `src/store/tips.ts` | In-app tips — the app pointing at itself, plus the agent doing the same. Two sources, one bubble, one switch over both of them: - `$tipsEnabled` is the whole feature, ON with a switch to stop it. A feature nobody meets… |
| `src/store/titlebar-app-actions.test.ts` | Tests: titlebarAppActionsClusterCounts; adds extras to the cluster they belong to; releases the space of every tool Simple mode hides, on both sides; $titlebarAppActionsSide |
| `src/store/titlebar-app-actions.ts` | Exports `TitlebarAppActionsSide`, `TITLEBAR_APP_ACTIONS_DEFAULT`, `setTitlebarAppActionsSide`, `TITLEBAR_FIXED_TOOLS`, `TitlebarFixedToolId`, `titlebarAppActionsClusterCounts` |
| `src/store/todos.test.ts` | Tests: setSessionTodos finished-list auto-clear; keeps an in-flight list indefinitely; drops the list shortly after every item completes; clears finished lists for session ids that collide with object prototype keys |
| `src/store/todos.ts` | Live todo list per runtime session, rendered by the composer status stack (the inline transcript panel is gone). Fed from two places: - live `todo` tool events (use-message-stream) - stored-session hydration (desktop-co… |
| `src/store/tool-activity.test.ts` | Tests: tool feed visibility follows display.tool_progress only; silences the feed only for false or ; does not follow show_reasoning |
| `src/store/tool-activity.ts` | Mirrors `display.tool_progress`, independent of `display.show_reasoning`: hiding thinking must not hide the work. Answer-only is both keys off. Parsing matches the gateway's `_load_tool_progress_mode` so the renderer and |
| `src/store/tool-dismiss.ts` | Exports `dismissToolRow`, `clearDismissedToolRows` |
| `src/store/tool-drafting.ts` | The tool whose arguments the model is streaming right now, and when it started. Generating a large payload (a 45 KB write_file) takes seconds during which the tool has not begun and the transcript has nothing to say. |
| `src/store/tool-media-owners.test.ts` | Tests: stale-answer guard; drops an answer orphaned by a plugin-list change and lets the newer request win; an orphaned answer never resurrects the entry it lost, even when it lands first; an orphaned failure neither ma… |
| `src/store/tool-media-owners.ts` | Exports `ToolMediaOwnersEntry`, `MAX_OWNERSHIP_REVALIDATIONS`, `ownersFromPluginRows`, `toolMediaOwnerKey`, `ensureToolMediaOwners`, `revalidateToolMediaOwners` … |
| `src/store/tool-progress.ts` | Latest live progress of a running tool call (`tool.progress`, from MCP `notifications/progress`). |
| `src/store/tool-view.test.ts` | Mount and unmount exactly as a rendered tool row does: subscribe (useStore) then unsubscribe (unmount). Everything else — an un-subscribed call — never attaches a listener, so eviction could only be observed through thi… |
| `src/store/tool-view.ts` | Exports `ToolViewMode`, `setToolViewMode`, `setHideCodeDiffs`, `setToolDisclosureOpen` |
| `src/store/tours.ts` | Guided tours (the `tour` tool) — on, with a switch to stop them. A tour takes the screen: it dims the app, spotlights an element, and pages with Next/Prev. That is worth having and worth being able to refuse, and unlike… |
| `src/store/transcript-lightbox.ts` | The transcript lightbox's open source, hoisted out of `ZoomableImage`. Transcript rows — and the markdown leaves inside them — legitimately remount while a turn streams (the render-budget slice drops older rows; the mar… |
| `src/store/transcript-sync.ts` | Cross-window transcript freshness. Each desktop window owns its own gateway transport for a session, so a turn that completes in window A never streams into window B. This bus pings peers with the stored session id so a… |
| `src/store/transcript-tail-cache.test.ts` | Tests: transcript tail cache; round-trips a session tail keyed by stored id; persists only the bounded tail of a long transcript; falls back to a shorter tail rather than caching an oversized entry |
| `src/store/transcript-tail-cache.ts` | ── Durable transcript-tail cache (#89206 "feels instant" layer) ──────────── The in-memory warm cache (sessionStateByRuntimeIdRef) makes same-window re-opens instant, but dies with the window — so every app launch, back… |
| `src/store/transcript-tail.test.ts` | Tests: recordTranscriptTail no-op suppression; does not notify on an identical re-record (#113842); notifies when the tail actually advances; keeps a no-op re-recorded entry at the MRU end so it survives the next evicti… |
| `src/store/transcript-tail.ts` | REST TAIL-HYDRATION BOOKKEEPING — keyed by STORED session id. `getLatestSessionMessages` loads a small newest-first page instead of a fixed 500-row transcript. When that page comes back full (returned === limit), older… |
| `src/store/translucency-browser.test.ts` | @vitest-environment jsdom |
| `src/store/translucency.linux.test.ts` | @vitest-environment jsdom |
| `src/store/translucency.test.ts` | @vitest-environment jsdom |
| `src/store/translucency.ts` | Window translucency (see-through window). One lever, 0–100. Two modes decide HOW the desktop shows through — see ` |
| `src/store/translucency.win10.test.ts` | @vitest-environment jsdom |
| `src/store/tutorial-lifetime.ts` | Desktop-global, like the two Appearance switches: changing profiles is not learning the app again. Read through storage so another window's completed retirement cannot be replayed over a later manual re-enable. |
| `src/store/updates-backend-check.test.ts` | Tests: mapBackendCheck; surfaces a failed check instead of claiming the backend is up to date; still reports an up-to-date backend when the check ran and found no gap; names a held backend instead of calling it the late… |
| `src/store/updates-channel.test.ts` | Tests: sourceUpdateChannel; offers the selector only where the choice is stable or main and can be saved; sourceUpdateTrack; names what a source checkout follows, including a custom branch and older runtimes |
| `src/store/updates-version-scope.test.ts` | Tests: desktop version follows the request scope; re-fetches when switching from a remote connection back to local; re-fetches when only the profile changes on the same connection; keeps the newest reply when two same-s… |
| `src/store/updates.test.ts` | Tests: gateway version refresh; requests the active gateway and does not publish a previous connection reply; maybeNotifyUpdateAvailable; shows when an update is available and not snoozed |
| `src/store/updates.ts` | Desktop self-update store. Tracks distance from the configured branch, surfaces it as an ambient pill, and orchestrates the apply flow. |
| `src/store/user-bubble-transparency.ts` | Message bubble transparency — how much of your own bubble's fill shows. One 0–100 lever, same direction as Window Translucency: 0 keeps the bubble solid (default), 100 leaves only the outline. Presentation-only, so the… |
| `src/store/vibe-hearts-enabled.test.ts` | Tests: vibe hearts enabled; turns off and persists |
| `src/store/vibe-hearts-enabled.ts` | Floating vibe hearts (affection burst on ily / <3 / good bot / thanks). On by default: that is today's always-on behavior. Settings → Appearance owns the lever so hearts stay presentation-scoped (desktop AGENTS.md: stat… |
| `src/store/video-playback-speed.ts` | Device-level video playback speed. Choosing a speed in any transcript video (via the native controls' rate menu) persists it as the rate every later player starts from, so a viewer who watches at 2x doesn't re-select it… |
| `src/store/voice-live.test.ts` | Tests: setVoiceChatMode; routes the write through the viewed profile, not the bare active socket; re-reads the status after the write instead of joining a pre-write fetch; refreshVoiceLiveStatus |
| `src/store/voice-live.ts` | `voice.voice_chat_mode` as the backend resolves it, plus whether GPT-Live can actually start (an OpenAI key resolves on the gateway host). The composer mounts the chained or the live conversation engine from this; refre… |
| `src/store/voice-playback.ts` | Exports `VoicePlaybackSource`, `VoicePlaybackStatus`, `VoicePlaybackState`, `setVoicePlaybackState` |
| `src/store/voice-prefs.test.ts` | Tests: keeps the desktop toggle local across config refreshes; migrates the legacy preference once, not on every refresh; applyVoiceStopPhraseFromConfig; defaults to |
| `src/store/voice-prefs.ts` | Desktop read-aloud is local; voice.auto_tts belongs to the messaging gateway. |
| `src/store/wake-word-client-capture.test.ts` | Issue #119089: a dead client PCM chain must land the ear in an honest off state with the reason visible — not a "listening" toggle that can never fire. |
| `src/store/wake-word.test.ts` | Tests: applyWakeStatus; syncs availability, listening and phrase from wake.status; tracks unavailability and carries the hint for the tooltip; keeps the dead-mic hint visible while listening (audio_silent) |
| `src/store/wake-word.ts` | "Hey Hermes" wake-word listener state for the composer toggle. The gateway is the single source of truth (the listener lives in the backend and is shared with the TUI under a single-owner mic lease); this atom is the re… |
| `src/store/windows.test.ts` | Tests: isPeerInstanceWindow; recognizes only the full peer marker; isProfilePinnedWindow; is set only by an explicit profile-window launch, not by an inherited peer route |
| `src/store/windows.ts` | Window flag set by the Electron main process when it opens a standalone session window (see electron/main.ts buildSessionWindowUrl). It rides in the query string BEFORE the HashRouter '#', so we read it from location.se… |
| `src/store/workspace-events.ts` | Event-driven "the working tree changed" signal — the smart replacement for polling. The agent only mutates files by running a tool, so the message stream's `tool.complete` (esp. ones carrying an inline_diff) is the prec… |
| `src/store/zoom.test.ts` | Tests: zoom state sync; uses the initial read when no newer change has arrived; does not let a stale initial read overwrite a newer zoom event |
| `src/store/zoom.ts` | Window text size (zoom). The main process owns the zoom level and persists it (see electron/zoom.ts for the scale). The renderer only mirrors the current percent for the settings UI: preset clicks go to the main process… |
| `src/styles.css` | Stylesheet |
| `src/test/deferred.ts` | A promise plus the handle that settles it. For tests that need a call to stay in flight — asserting the pending UI, proving a second call is coalesced or ignored, ordering two resolutions — and then release it on their… |
| `src/test/fake-gateway-socket.ts` | Exports `FakeWebSocket` |
| `src/test/jsdom.ts` | jsdom implements no layout and no animation, so component libraries that call those APIs unconditionally throw on mount. These install inert stand-ins: enough for the component to render, never enough to assert on. A |
| `src/test/oauth-provider.ts` | A logged-out PKCE provider. Onboarding branches on `flow` and `status.logged_in`; the rest is filler the UI only echoes. |
| `src/test/page-storage.ts` | The object that holds `window.localStorage`'s methods, for spying on the page's storage reads and writes. On Node 22 that is jsdom's `Storage.prototype`: a spy defined on the instance is kept as a stored item and never… |
| `src/test/react-root.ts` | A React root in a container attached to the document, for the handful of suites that cannot use Testing Library's `render`. They need the component mounted in the real document — a canvas that must paint, an element mea… |
| `src/test/rest-bridge.ts` | Install a fake `window.hermesDesktop.api`, the preload bridge every REST helper sends through. |
| `src/test/session-info.ts` | A `SessionInfo` with every field at its zero value. `SessionInfo` mirrors a backend row and grows a field whenever the API does. Spelling the whole shape out per test file meant each new field broke a handful of unrelat… |
| `src/test/webapp-session.ts` | Exports `seedWebappSession`, `clearWebappSession` |
| `src/test/webapp-windows.ts` | BroadcastChannel as a browser delivers it within one origin: asynchronously, to every other open channel with the same name, never to the sender, and never after either side closes. |
| `src/test/window-state.ts` | Stand-ins for the two window-visibility signals the renderer reacts to: Electron's `hermesDesktop.onWindowStateChanged` bridge and the DOM's own `document.hidden`. Both are read-only under jsdom, and anything that pauses |
| `src/themes/accent-override.ts` | Dev-only accent override. Live-authoring knob for `retintTheme`: while this holds a hex, the theme context paints the active skin re-seeded from it. `null` means "off" — the theme paints exactly as authored, which is th… |
| `src/themes/accents.ts` | Accent swatches and the ids the agent and the picker use for them. A swatch can paint differently per surface (Mono is black on light, white on dark), so callers resolve an id against the rendered mode at the moment of… |
| `src/themes/backend-sync.test.ts` | Tests: ingestBackendSkin; registers a converted skin without applying when apply=false; applies a new skin name once; seed does not paint, but a later same-name skin.changed applies (missed-activation recovery) |
| `src/themes/backend-sync.ts` | Live skin sync from the Hermes backend. The backend resolves the active skin (built-in or `$HERMES_HOME/skins/*.yaml`) and announces it on `gateway.ready` / `skin.changed`, and answers `config.get skin` with the same pa… |
| `src/themes/boot-palette.test.ts` | Tests: writes the palette as one snapshot and reads it back; drops the previous snapshot when the new one cannot be written; keeps self-contained colour functions |
| `src/themes/boot-palette.ts` | The theme colours the boot-failure notice (src/lib/boot-failure.ts) paints itself with when the app could not load. Written as one snapshot, so a failed write can never pair one theme's background with another's ink, an… |
| `src/themes/chat-font.ts` | Families users ask for by name; the app face is otherwise whatever the theme declares. |
| `src/themes/classic-skin.test.tsx` | What the gateway and the Electron bridge report for a STOCK config (`display.skin: default`): the CLI's classic gold skin, by name `default`. |
| `src/themes/color.ts` | Desktop-only color helpers: the naive light/dark bucketer, the VS Code hex normaliser, and the OKLCH toolkit. The sRGB primitives (parse/mix/measure/ ensureContrast) live in ` |
| `src/themes/context.test.tsx` | The live-authoring loop: Hermes writes/edits one skin file and every surface repaints. An in-place edit keeps the NAME — only the palette moves. |
| `src/themes/context.tsx` | Desktop theme context. Applies the active theme as CSS custom properties on :root so every Tailwind utility that references a color or font-family token picks up the change automatically. Mode (light/dark/system) contro… |
| `src/themes/index.ts` | TypeScript source: `index` |
| `src/themes/install.test.ts` | Tests: buildThemeFromMarketplace; folds a light + dark variant into one family with both slots; orders variants by contribution regardless of light/dark sequence; fills both slots with the sole palette for a single-vari… |
| `src/themes/install.ts` | Install desktop themes from external sources. The heavy lifting (network + .vsix unzip) lives in the Electron main process (`electron/vscode-marketplace.ts`), reached via `window.hermesDesktop.themes`. Main hands back t… |
| `src/themes/persist-accent.test.tsx` | Tests: persistAccent; saves an accent as the profile theme and returns to Nous on null; retints the active theme, keeping its own colours and CSS, exactly as the preview painted it; never overwrites another profile |
| `src/themes/persist-accent.ts` | Save an accent on the live profile's theme: only its accent moves, saved as the `<base>-accent-<hex>` user theme the `$accentOverride` preview painted. `null` (or the base's own accent) returns to the base theme itself.… |
| `src/themes/presets.test.ts` | #40364: none of the UI text/mono fonts carry emoji glyphs, so every font stack must end with a color-emoji fallback or emoji render as tofu on platforms whose default font lacks them (e.g. Linux). |
| `src/themes/presets.ts` | Built-in desktop themes. Names match the CLI skins / dashboard presets. Add new themes here — no code changes needed elsewhere. The palette-bearing skins (nous, catppuccin, everforest, solarized) are forks of their VS C… |
| `src/themes/profile-theme.test.ts` | Skin and mode share one per-profile contract, so assert it once over both. |
| `src/themes/request.test.tsx` | Tests: requestTheme; switches the painted theme from outside React; persists per profile like a manual pick; switches and persists light/dark from outside React |
| `src/themes/request.ts` | Imperative theme switching, for callers with no component to hang a hook on. `useTheme().setTheme` is the React door and covers every in-app surface, but not every switch happens during a render. The backend announces a… |
| `src/themes/retint.test.ts` | Tests: the shipped nous accents; leaves GitHub’s neutrals in place — only the accent family is forked; retintTheme; is an identity at the theme’s own accent |
| `src/themes/retint.ts` | Accent retinting — re-seed a theme's accent family from one color. A palette's accent is not one color, it's a family: the seed plus the soft surfaces mixed from it. In `nous` that's 7 slots per mode — `primary`/`ring`/… |
| `src/themes/skin.test.ts` | Tests: skinToDesktopTheme; returns null without a name or colors; maps the accent onto every brand token and keeps a single palette; seeds the background from status_bar_bg when none is explicit |
| `src/themes/skin.ts` | Hermes skin → DesktopTheme converter. A "skin" is the CLI/TUI theme unit: a YAML file in `$HERMES_HOME/skins/` (or a built-in) resolved by `hermes_cli/skin_engine.py` and pushed to every surface over JSON-RPC (`gateway.… |
| `src/themes/types.ts` | Desktop app theme model. colors — Tailwind color tokens written directly to CSS vars. darkColors — optional hand-tuned dark variant (else `colors` is reused unchanged for dark, and a synth pass generates light). typogra… |
| `src/themes/use-skin-command.ts` | Old names land on a shipped theme so muscle memory works. `gold`/`hermes` only ever meant the classic gold look, so they reach Classic Hermes; `default` stays Nous because it is also the stock config value, which Deskto… |
| `src/themes/user-themes.test.ts` | Tests: user theme registry; installs a theme into the merged registry and persists it; lists built-ins before user themes; removes a theme |
| `src/themes/user-themes.ts` | User-installed desktop themes (currently: converted VS Code themes). This is the extensibility seam. The theme context reads the *merged* registry (built-ins + user themes) for `availableThemes` and for every skin looku… |
| `src/themes/vscode.test.ts` | Tests: vscodeThemeSlug; namespaces, lowercases, and dashes; falls back when the name has no usable characters; parseVscodeTheme (JSONC tolerance) |
| `src/themes/vscode.ts` | VS Code color-theme → DesktopTheme converter. VS Code themes carry ~hundreds of `workbench.colorCustomization` keys, but the desktop theme model only needs a `DesktopThemeColors` struct — `applyTheme` derives every glas… |
| `src/touch-styles.test.ts` | @vitest-environment node |
| `src/types/hermes.ts` | Exports `StoredToolCallLabels`, `ConfigFieldSchema`, `ConfigSchemaResponse`, `AudioTranscriptionResponse`, `AudioSpeakResponse`, `AudioTtsLeaseResponse` … |
| `src/vite-env.d.ts` | @novnc/novnc ships no typings (its export is core/rfb.js); the surface the Bot Screen pane uses. Declared here because `apps/desktop/src/**/*.d.ts` is gitignored except for the allowlisted files, and an ambient `declare… |
| `src/webhooks-rest.test.ts` | Tests: Webhook REST parity helpers; encodes the name when deleting a subscription; routes an explicitly owned delete to that profile, not the ambient scope |
| `tsconfig.e2e.json` | JSON object with keys `extends`, `compilerOptions`, `files`, `include`, `exclude` |
| `tsconfig.electron.json` | JSON object with keys `extends`, `compilerOptions`, `include`, `exclude` |
| `tsconfig.json` | JSON object with keys `compilerOptions`, `include`, `exclude` |
| `update-feed.cjs` | Historical native URLs are a compatibility layout, not a channel registry. |
| `update-feed.d.cts` | TypeScript (CommonJS) |
| `vite.config.ts` | React Compiler preset scoped to modules that can actually contain components/hooks (JSX syntax or a react-ish import). The preset's default code filter matches any PascalCase/use* declaration — effectively every TS modu… |
| `vitest.config.ts` | TypeScript source: `vitest.config` |
| `vitest.hermes-python.ts` | HERMES_PYTHON for the electron contracts that drive real hermes_cli / pm code (mac-sign, source-backend, checkout-source). CI exports the PM test environment's interpreter; a developer's plain `npx vitest` does not, and… |
| `vitest.run-tmp.ts` | One temp root per vitest run, removed at teardown. Tests mkdtemp under os.tmpdir() and not all of them remove what they make: one run of the `electron` project left 54 dirs behind. Workers inherit TMPDIR from this proce… |
| `vitest.setup.ts` | Shared tooltips measure their arrow through Radix's useSize hook. Geometry assertions still belong in a real browser, not this inert observer. Assigned, not `vi.stubGlobal`, so a test's `vi.unstubAllGlobals()` cannot st… |

## `apps/shared/`

| File | What it does |
|---|---|
| `eslint.config.mjs` | JavaScript (ES module): `eslint.config` |
| `package.json` | JSON manifest for `@hermes/shared` |
| `src/ansi.test.ts` | Tests: stripAnsi; strips CSI/OSC/control bytes from plain previews; strips incomplete CSI prefixes and carriage returns; strips multi-byte non-CSI ESC sequences without leaving trailing bytes |
| `src/ansi.ts` | ANSI escape stripping shared by every TS surface (TUI, desktop, web). Covers CSI (complete and truncated tails), OSC (hyperlinks, titles), DCS/SOS/PM/APC strings, multi-byte non-CSI ESC sequences, stray ESC bytes and C0… |
| `src/backend-scope.ts` | Composite backend scope keys for the multi-connection registry — shared between the Electron main process (backend pool keying) and the renderer (secondary socket registry), so both sides derive identical keys. The loca… |
| `src/billing-payment-method.test-d.ts` | Compile-time guard for BillingPaymentMethod. There is nothing to run here — the point is that `tsc` accepts this file. An earlier revision typed the fallback arm's `kind` as `string & {}`, which makes the discriminant n… |
| `src/billing-policy.ts` | Exports `BillingRecovery`, `BillingRefusalPolicy`, `BILLING_REFUSAL_POLICY`, `refusalPolicy` |
| `src/billing-types.ts` | Shared Remote Spending wire contracts. These shapes round-trip between the Python tui_gateway and TypeScript clients such as the TUI and desktop app. Keep rendering state, client logic, and the gateway event union out o… |
| `src/catalog-browse.ts` | Shared with the docs catalog: taxonomy order is independent of popularity. Keep keys in sync with CATALOG_CATEGORIES in hermes_cli/plugin_catalog.py and website/scripts/extract-plugins.py. |
| `src/catalog-curation.json` | JSON object with keys `artwork`, `featured` |
| `src/catalog-featured.test.ts` | Tests: pickFeatured; rotates through curated ranks weekly, in rank order; is the same pick anywhere within one week; falls back to the newest pictured official entry of the last 30 days |
| `src/catalog-featured.ts` | The catalog hero pick, shared by the website and the desktop app so both feature the same entry at the same time. Curated picks come from `catalog-curation.json` → `featured`, stamped into the published catalog as a 1-b… |
| `src/catalog-install.ts` | Install targets shared by the public docs galleries and native catalog. |
| `src/charge-settlement.ts` | Exports `SettlementDeps`, `SettlementOutcome`, `SETTLEMENT_POLL_INTERVAL_MS`, `SETTLEMENT_POLL_CAP_MS`, `SETTLEMENT_MAX_RETRY_AFTER_MS`, `driveChargeSettlement` |
| `src/color.test.ts` | Tests: parseColor; parses hex6, hex3 and rgb() forms; rejects garbage; mix |
| `src/color.ts` | THE sRGB color primitive for every TypeScript surface (desktop themes, the Ink TUI). Parse, mix, measure and fix colors here so tone ladders, contrast floors and one-off UI needs share one set of semantics — and so the… |
| `src/cron-trigger-controller.ts` | Exports `CronTriggerRunResult`, `CronTriggerController`, `createCronTriggerController` |
| `src/data-url-read-max.ts` | Size cap for local files Desktop loads as data URLs (composer attach, image preview, …). Main owns the persisted value; the renderer mirrors it in Settings → Chat and clamps optimistically before sending. Both ends have… |
| `src/external-url.ts` | Which URLs Desktop hands to a browser when asked to open something externally. Electron's `openExternalUrl` (shell.openExternal) and the browser-hosted bridge (window.open) share this one rule, so an agent- or tool-supp… |
| `src/file-url.test.ts` | Tests: fileUrlToNativePath |
| `src/file-url.ts` | Reading a `file:` URL back into the path it names. Desktop meets these URLs in agent output, preview targets and the media pipeline, in the renderer and in Electron main; every surface decodes them with this one rule so… |
| `src/format.test.ts` | Tests: compactNumber; never emits a unit-boundary artifact like |
| `src/format.ts` | THE compact-number formatter — every user-facing count/token figure goes through here. 999 → "999", 1000 → "1k", 1230 → "1.2k", 10000 → "10k", 1_500_000 → "1.5M". `M` is the top rung by design: token and cost figures |
| `src/fuzzy.test.ts` | Tests: fuzzyScore; matches a query as a subsequence (g4o → gpt-4o); returns null when characters are out of order or absent; returns matched positions into the original target |
| `src/fuzzy.ts` | Lightweight fuzzy subsequence scorer for picker filtering. Matches a query as an ordered subsequence of the target (so `g4o` matches `gpt-4o`) and scores by match quality so callers can rank results. Higher |
| `src/gateway-contract.generated.ts` | GENERATED by scripts/gen_gateway_contracts.py from tui_gateway/contracts — DO NOT EDIT. Regenerate: .venv/bin/python scripts/gen_gateway_contracts.py tests/tui_gateway/contracts/test_generated.py fails when this file is… |
| `src/gateway-contract.openrpc.json` | JSON data/configuration |
| `src/gateway-events.ts` | Wire types for the `tui_gateway` JSON-RPC surface shared by the Ink TUI, Desktop and the web dashboard. Every shape here is GENERATED from `tui_gateway/contracts` (Python is the single source): `./gateway-contract.gener… |
| `src/i18n.test.ts` | Tests: formatPositional; substitutes positional placeholders and blanks the ones the call left out; adaptStringOverrides; wraps a pack string over a function-valued base entry into a positional formatter |
| `src/i18n.ts` | Locale scaffolding shared by the desktop and web i18n layers. Generic over the translation catalog type: each app supplies its own `Translations`/`en` and wraps `mergeTranslations` in a one-line `defineLocale`. |
| `src/index.ts` | TypeScript source: `index` |
| `src/json-rpc-channel.test.ts` | Tests: JsonRpcRequestChannel; routes responses to the pending call and keeps JSON-RPC code/data on errors; detach fails every in-flight call and a per-call timeout names the method; advertises server-request support onc… |
| `src/json-rpc-channel.ts` | Exports `GatewayRequestId`, `JsonRpcErrorPayload`, `JsonRpcFrame`, `ServerRequestParams`, `ServerRequest`, `ServerRequestHandler` … |
| `src/json-rpc-gateway-connect.test.ts` | EventTarget-based WebSocket stand-in that never opens, so each failure leg can be driven by hand. |
| `src/json-rpc-gateway-legacy-replay.test.ts` | Desktop in URL, Cloud or SSH mode (no `native_dial`) talks to a standalone `hermes serve` on `/api/ws`. That socket announces a process epoch on gateway.ready. A serve that does not know `replay_epoch` validates `sessio… |
| `src/json-rpc-gateway-replay.test.ts` | Minimal EventTarget-based WebSocket stand-in so the seq-tracking and replay-resume logic can be driven with real dispatch semantics. |
| `src/json-rpc-gateway.ts` | Exports `ConnectionState`, `WebSocketLike`, `GatewayClientOptions`, `APPROVAL_RESPOND_TIMEOUT_MS`, `isGatewayWebSocketUrl`, `GatewayEventHub` … |
| `src/model-search-text.test.ts` | Tests: modelSearchText; keeps ordinary model ids unchanged; model picker search with aliases; surfaces k3 when the user searches kimi |
| `src/model-search-text.ts` | Extra tokens used only for model-picker search ranking. Wire IDs stay unchanged — some providers report short or brand-less ids (Kimi Coding's flagship is literally `k3`) that users still search for by the familiar `kim… |
| `src/plan-usage.ts` | Usage-window plan chrome shared by every model picker (desktop dialog + composer menu, TUI). The gateway sends each model's word per caller (`usage_level` on `/v1/models`); the backend copies it into `ModelOptionProvide… |
| `src/reasoning-effort.test.ts` | Tests: reasoning-effort; is one duplicate-free value set with ; defaults to a real level and recognizes it case-insensitively |
| `src/reasoning-effort.ts` | Hermes' reasoning levels, in ascending order — mirrors the backend's VALID_REASONING_EFFORTS (hermes_constants.py). `none` is not a level: it's thinking disabled. |
| `src/reconnect-backoff.test.ts` | Tests: reconnectBackoffDelayMs; increases the delay ceiling across consecutive failed attempts; caps the delay ceiling instead of growing unbounded; applies full jitter: delay is uniformly within [0, ceiling) |
| `src/reconnect-backoff.ts` | Exponential reconnect backoff shared by every Hermes front-end socket (desktop gateway/plugins, web events feed, web PTY, Ink TUI attach mode). Default is full jitter: a bare exponential backoff still lets every client… |
| `src/session-http-mutations.ts` | Exports `SessionMutationSnapshot`, `SessionMutationIdentity`, `createSessionMutationClient`, `randomUuid` |
| `src/skill-scaffold.test.ts` | Byte-identical to what agent/skill_commands.py emits — a desktop/TUI talking to an older gateway sees exactly these strings. |
| `src/skill-scaffold.ts` | A `/skill` invocation expands into a model-facing message that embeds the whole skill body. That payload is for the agent — the UI shows the invocation the user typed (`/work fix the leak`) and nothing else. The gateway… |
| `src/skin.ts` | Canonical Hermes skin — the theme SDK's cross-surface contract. A skin is authored once as YAML in `$HERMES_HOME/skins/<name>.yaml` (or a built-in), resolved by the Python skin engine (`hermes_cli/skin_engine.py`), and… |
| `src/slash.test.ts` | Tests: parseSlashCommand; splits the name off a single separator and lower-cases it; keeps a multi-line argument byte-for-byte (#41323, #55510); takes the name across a newline boundary like the CLI and gateway (split o… |
| `src/slash.ts` | The slash-command wire contract every TypeScript surface shares: how a typed line splits into `name` + `arg`, and the `command.dispatch` response union (`tui_gateway/methods_tools.py::command.dispatch`). One parser, so… |
| `src/theme-presets.ts` | Raw palette table for every built-in Hermes theme preset — the single source of truth shared by the desktop app (which layers OKLCH synthesis, terminal palettes and typography on top) and the web dashboard (which projec… |
| `src/translucency.ts` | Window translucency — the one place the main process and the renderer agree on what the setting means. One lever, 0–100 (0 = off, the default). Two modes decide HOW the desktop shows through: - 'clear' — the main proces… |
| `src/update-debt.ts` | Owed post-commit work of a dashboard-started `hermes update`, read from the receipt summary the action status route attaches. Shared by the web dashboard toast and the Desktop backend-apply store so both surfaces name |
| `src/usage-tick.ts` | The owner's `session.usage` tick (`SessionUsagePayload`, canonical counters at the top level or the classic sidecar ticker's nested `usage`) or its `session.stats` reply (`SessionStats`). |
| `src/websocket-url.ts` | Exports `GatewayAuthMode`, `GatewayWsConnection`, `ResolveGatewayWsUrlDeps`, `GatewayWsUrlResult`, `GatewayReauthRequiredError`, `isGatewayReauthRequired` … |
| `tsconfig.json` | JSON object with keys `compilerOptions`, `include` |
