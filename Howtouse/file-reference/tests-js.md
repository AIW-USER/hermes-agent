# File reference: `tests-js`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `allow-scripts-sync.test.ts` | Invariants tying ``allowScripts`` to the lockfile it gates. npm's ``allowScripts`` allowlist is keyed by exact ``name |
| `assistant-ui-tap-compat.test.ts` | Invariant: the |
| `bootstrap-installer-stage-timer.test.ts` | Regression for the bootstrap installer's stage timers (issue report: "it says 744 hours or minutes — I don't know how to adjust the counter"). ``formatElapsed`` rendered a running stage as ``m:ss`` with unbounded minute… |
| `bundle-inputs.test.mjs` | Tests: package transitions are ordered, identity-preserving, and report through the existing family; explicit bundled routes refuse absent package inputs instead of reporting a skipped pass; a download whose connection… |
| `bundle-smoke-metadata.test.mjs` | Tests: fresh-install provenance admits tagless commit stamps without relaxing update acceptance; identity uses the production bundled variant and exact input tokens, not inherited build flags; channel smoke binds the co… |
| `desktop-builder.test.mjs` | Tests: desktop development composition reuses prepared icon pixels instead of provisioning them again; desktop development composition restages native inputs only when their receipt is stale; desktop compiler consumes e… |
| `desktop-mac-entitlements.test.ts` | Regression for #37718: macOS microphone entitlement must be inherited. Hermes Desktop signs with ``hardenedRuntime: true`` and points electron-builder at two entitlement files (see ``apps/desktop/package.json``): - ``en… |
| `desktop-mac-usage-descriptions.test.ts` | Regression for #54551: macOS Info.plist privacy usage descriptions declared by the Desktop electron-builder config (`apps/desktop/electron-builder.config.cjs -> mac.extendInfo`) must pin every `NS*UsageDescription` key… |
| `e2e-matrix-route.test.ts` | Tests: a leg name, or the job name GitHub shows for it, runs exactly that leg; an OS preset runs that OS whole and no other; a route that selects nothing fails instead of running an empty green matrix; the pr route runs… |
| `electron-runtime.test.mjs` | Tests: read-only validation refuses missing or stale binaries without executing either entry point; propagates installer failure and rejects success without a complete runtime; refuses a foreign installed version before… |
| `eslint.config.mjs` | JavaScript (ES module): `eslint.config` |
| `freshness-metadata.test.mjs` | The freshness contract for OS file-manager metadata (#122632, #122803): writing .DS_Store / AppleDouble sidecars / .localized / Thumbs.db / Desktop.ini into any hashed tree must never flip a recorded product from curren… |
| `frontend-common-publish.test.mjs` | Windows antivirus holds a freshly written tree (the HUD helper exe in native-deps, web_dist after a long build) and publication's renames fail EPERM until the scan ends (#126914). Fault only the renames a test names; |
| `frontend-common.test.mjs` | rmTree retries ENOTEMPTY from Finder/Spotlight dropping files into a directory mid-removal (#122803). Node's rmSync is the only seam that can reproduce that race deterministically, so replace it and keep the rest of |
| `generate-icons.test.mjs` | Tests: the real wrapper builds and checks native icon artifacts in an independent output; failed icon processes cannot report a successful build |
| `install-e2e-red-tracker.test.mjs` | Tests: one tracker: a red run opens it, the next red run rewrites it, a green run closes it |
| `install-known-failures.test.ts` | Tests: known install failures; recognizes the released launcher self-lock, not generic access denied; matches manual-only app updates only for the three proven July script cases; CLI writes a receipt and exits zero only… |
| `install-process-close.test.ts` | Tests: waits for native close, not exit, and retains a close observed before hand-off; fails if the launched process never closes |
| `macos-bundled-helpers.test.mjs` | Tests: codesign stderr identifies the team but never blesses an unsigned/ad-hoc signature; installed stamp independently binds payload, mechanism, commit and tag; feed server rejects literal and encoded traversal |
| `macos-publish-config.test.mjs` | Tests: bakes only a canonical https feed base into the updater config |
| `node-deps.test.mjs` | Tests: read-only dependency preparation reuses complete receipts but refuses missing inputs; reuse refuses a gutted package directory and repairs it with npm ci; native toolchain admission rejects a changed compiler wit… |
| `node-engine-alignment.test.ts` | semver ships no declarations in this lock; type the two library calls used here. |
| `notarize.test.mjs` | Tests: accepted submissions retry only ticket propagation, without resubmitting or rebuilding; HTTP timeouts resume the same submission with notarytool wait and a shrinking budget; wait recovery requires a known submiss… |
| `package-json-lazy-deps.test.ts` | Invariants for what is eager vs lazy in the root ``package.json``. The root ``package.json`` is installed by ``hermes update`` on every user, including users who never opted into a given browser backend. Anything listed… |
| `package.json` | JSON manifest for `@hermes/root-tests` |
| `product-builders.test.mjs` | Tests: product outputs exclude the source tree except supported generated destinations; publication replaces only builder-owned directories and rechecks ownership after compilation; existing npm build directories can be… |
| `react-dom-pair-compat.test.ts` | Invariant: every workspace that renders React ships one react/react-dom pair. React validates at import time that ``react`` and ``react-dom`` come from the same installed copy. When they don't, it throws "Minified React… |
| `renderer-syntax-node.test.mjs` | Tests: renderer syntax checks use the running Node without PATH and preserve explicit NODE |
| `scripts/desktop-chat-smoke.ts` | Exports `ChatPhase`, `DesktopChatSmokeOptions`, `ChatIdentity`, `TranscriptMessage`, `DesktopChatReceipt`, `readChatIdentity` … |
| `scripts/desktop-smoke-launch-failure.test.ts` | Tests: an app that dies before Playwright attaches leaves a failed receipt carrying its exit code and stderr |
| `scripts/desktop-smoke-process.ts` | Exports `NativeProcess`, `BackendProcess`, `OriginEvidence`, `readInstallationCommit`, `readBundledBundleEnv`, `readNativeProcesses` … |
| `scripts/desktop-smoke.test.ts` | Tests: a later CI step\; one server owns inference and a fresh, per-server prompt witness; provider reconfiguration preserves feed, plugins, history and explicit fixture options; OLD history, partial/wrong replies, acti… |
| `scripts/desktop-transcript.test.ts` | @vitest-environment jsdom |
| `scripts/launch-from-spec.test.ts` | Tests: the update window pins its isolated route before Electron requests the singleton lock; the update window carries Hermes connection state without cloning Chromium state |
| `scripts/mock-provider-config.ts` | Exports `MOCK_MODEL_ID`, `validateMockUrl`, `writeMockProviderConfig`, `writeEnvFile` |
| `scripts/mock-server.ts` | Minimal OpenAI-compatible mock inference server for E2E tests and the dev:mock dev flow. Implements just enough of the /v1/* surface for `hermes serve` to resolve a provider, list models, and stream a canned chat comple… |
| `setup-pm-cache.test.mjs` | Tests: pull requests restore the caches main saves and never write their own; only dependency-carrying callers touch the uv cache; finds a release and a commit leg for every native target, and the payload producer; each… |
| `setup-pm-post.test.mjs` | Tests: prunes the saved uv cache to the lock at teardown, never during registration |
| `source-update-observer.test.mjs` | Lets a test play the relaunched app: it unlinks the result file after the observer listed it and before the observer reads it. |
| `tsconfig.json` | JSON object with keys `compilerOptions`, `include`, `exclude` |
| `update-ui.test.mjs` | Tests: checks the live Desktop bridge against the staged target before opening About; test-only source probe pins staged main without changing other Python invocations; preloaded Electron-style execFile transports expli… |
| `vitest.config.ts` | TypeScript source: `vitest.config` |
| `webapp-keep-previous.test.mjs` | A rebuild copies the previous generation's chunks for tabs that still load them; a copy can fail for reasons that are no fault of the entry (a full disk). Fault only the copies a test names, by the complete native path… |
| `window-open-policy.test.ts` | Security regression for GHSA-9f4c-93c8-jc8g (CVE-2026-70608): a sandboxed iframe without `allow-popups` can reach `setWindowOpenHandler` with no user gesture, so the handler must always deny and must never open a URL. T… |
| `windows-bundled-helpers.test.mjs` | Tests: Windows packaged-update helper contracts run in the ordinary JS lane |
