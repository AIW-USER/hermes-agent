# File reference: `web`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | web/ + hermes_cli/web_routers/ — the dashboard (`hermes dashboard` → `/chat`) |
| `README.md` | Hermes Agent — Web UI |
| `eslint.config.js` | JavaScript source: `eslint.config` |
| `index.html` | HTML page/template |
| `package.json` | JSON manifest for `web` |
| `public/favicon.ico` | Icon file |
| `public/fonts-terminal/JetBrainsMono-Bold.woff2` | Web font |
| `public/fonts-terminal/JetBrainsMono-Italic.woff2` | Web font |
| `public/fonts-terminal/JetBrainsMono-Regular.woff2` | Web font |
| `public/fonts/Collapse-Bold.woff2` | Web font |
| `public/fonts/Collapse-Regular.woff2` | Web font |
| `public/fonts/Mondwest-Regular.woff2` | Web font |
| `public/fonts/RulesCompressed-Medium.woff2` | Web font |
| `public/fonts/RulesCompressed-Regular.woff2` | Web font |
| `public/fonts/RulesExpanded-Bold.woff2` | Web font |
| `public/fonts/RulesExpanded-Regular.woff2` | Web font |
| `src/App.tsx` | Exports `App` |
| `src/components/AllowlistInput.tsx` | Exports `splitAllowlist`, `joinAllowlist`, `AllowlistInput` |
| `src/components/AuthWidget.test.tsx` | @vitest-environment jsdom |
| `src/components/AuthWidget.tsx` | AuthWidget — sidebar "Logged in as …" affordance for the dashboard OAuth gate (Phase 7 of .hermes/plans/2026-05-21-dashboard-oauth-auth.md). Renders nothing in loopback / --insecure mode. In gated mode, fetches /api/aut… |
| `src/components/AutoField.tsx` | Exports `AutoField` |
| `src/components/AutomationBlueprints.tsx` | Exports `AutomationBlueprints` |
| `src/components/ChatSessionList.test.tsx` | @vitest-environment jsdom |
| `src/components/ChatSessionList.tsx` | ChatSessionList — a ChatGPT-style conversation switcher that sits beside the embedded TUI on the dashboard Chat tab. It lists the most recent sessions for the active management profile and lets the user swap between the… |
| `src/components/ChatSidebar.test.tsx` | @vitest-environment jsdom |
| `src/components/ChatSidebar.tsx` | ChatSidebar — structured-events panel that sits next to the xterm.js terminal in the dashboard Chat tab. Two WebSockets, one per concern: 1. **JSON-RPC sidecar** (`GatewayClient` → /api/ws) — a lightweight session used… |
| `src/components/ChatWorkspacePicker.tsx` | ChatWorkspacePicker — choose which host directory a FRESH dashboard chat starts in. The dashboard is the "drive Hermes from a phone or any browser" surface, yet every new /chat used to spawn in the dashboard process's l… |
| `src/components/ConfirmDialog.tsx` | Exports `ConfirmDialog` |
| `src/components/DeleteConfirmDialog.tsx` | Exports `DeleteConfirmDialog` |
| `src/components/HermesConsoleModal.tsx` | Exports `HermesConsoleModal` |
| `src/components/LanguageSwitcher.tsx` | Language picker — shows the current language's endonym, opens a dropdown of all supported locales when clicked. Persists choice to localStorage via the I18n context. Replaces the older two-state EN↔ZH toggle now that we… |
| `src/components/LoadErrorNotice.tsx` | Exports `LoadErrorNotice` |
| `src/components/Markdown.tsx` | Lightweight markdown renderer for LLM output. Handles: code blocks, inline code, bold, italic, headers, links, lists, horizontal rules. NOT a full CommonMark parser — optimized for typical assistant message patterns. `s… |
| `src/components/MemoryPressureBanner.test.tsx` | @vitest-environment jsdom Tests for the NS-656 memory-pressure banner: trigger selection, severity precedence, dismissal semantics, and escalation re-opening. |
| `src/components/MemoryPressureBanner.tsx` | App-wide warning banner for resource trouble (NS-656): memory pressure and disk exhaustion. Triggers, worst-first: 1. Disk critical — the HERMES_HOME volume is nearly full. Worst because the failure mode is silent data… |
| `src/components/ModelInfoCard.tsx` | Exports `ModelInfoCard` |
| `src/components/ModelPickerDialog.tsx` | Exports `ModelPickerDialog`, `NO_PROVIDERS_MESSAGE` |
| `src/components/ModelReloadConfirm.tsx` | Confirm + full-page reload after a model change. Changing the main model persists to config.yaml, but the RUNNING chat keeps its model until its session is rebuilt. A full reload (fresh PTY session that boots its agent… |
| `src/components/MultiplexStandaloneBanner.tsx` | A multi-profile host whose gateway came up STANDALONE on a boot guard: every other profile's bot is silent until `hermes gateway migrate --multiplex` runs. The backend only sets `multiplex_standalone_reason` when there… |
| `src/components/OAuthLoginModal.test.tsx` | @vitest-environment jsdom OAuthLoginModal expiry behaviour: when the sign-in window lapses locally, the modal must surface the backend poller's actionable message when it has |
| `src/components/OAuthLoginModal.tsx` | Exports `OAuthLoginModal` |
| `src/components/OAuthProvidersCard.tsx` | Exports `OAuthProvidersCard` |
| `src/components/PlatformsCard.tsx` | Exports `PlatformsCard` |
| `src/components/ProfileScopeBanner.tsx` | App-wide amber banner shown while the global switcher targets a profile OTHER than the dashboard's own — every management write (config, keys, skills, MCPs, model) and new Chat sessions land in that profile. |
| `src/components/ProfileSwitcher.tsx` | Exports `ProfileSwitcher` |
| `src/components/ReasoningPicker.tsx` | ReasoningPicker — sets the main model's reasoning effort from the dashboard Chat sidebar, mirroring the desktop app's composer effort radio. The dashboard previously only showed a read-only "Reasoning" capability badge… |
| `src/components/ScheduleBuilder.tsx` | Exports `ScheduleBuilder` |
| `src/components/SharedMetricsConsentBanner.tsx` | Exports `SharedMetricsConsentBanner` |
| `src/components/SidebarFooter.tsx` | Exports `SidebarFooter` |
| `src/components/SidebarStatusStrip.tsx` | Gateway + session summary for the System sidebar block (no separate strip chrome). |
| `src/components/SkillEditorDialog.tsx` | Exports `SkillEditorDialogProps`, `SkillEditorDialog` |
| `src/components/StructuredReasoning.test.tsx` | Tests: StructuredReasoning; renders thinking prose without literal wrapper tags; renders action and result as labeled code blocks |
| `src/components/StructuredReasoning.tsx` | Exports `StructuredReasoning` |
| `src/components/ThemeSwitcher.tsx` | Compact theme picker mounted next to the language switcher in the header. Each dropdown row shows a 3-stop swatch (background / midground / warm glow) so users can preview the palette before committing. User-defined the… |
| `src/components/ToolsetConfigDrawer.tsx` | Exports `ToolsetConfigDrawer` |
| `src/components/auth-widget-visibility.ts` | Exports `shouldHideAuthWidget` |
| `src/contexts/PageHeaderProvider.test.tsx` | @vitest-environment jsdom |
| `src/contexts/PageHeaderProvider.tsx` | Exports `PageHeaderProvider` |
| `src/contexts/ProfileProvider.test.tsx` | @vitest-environment jsdom The management scope and its ?profile= URL param stay in sync. A link that changes the path AND the param together (Profiles > "Manage skills & tools" |
| `src/contexts/ProfileProvider.tsx` | Exports `ProfileProvider` |
| `src/contexts/SystemActions.test.tsx` | @vitest-environment jsdom The update toast names what a committed update still owes for every committed outcome: a partial run (exit 1 after record_user_action) shows the producer's own instruction, and only |
| `src/contexts/SystemActions.tsx` | Exports `SystemActionsProvider` |
| `src/contexts/page-header-context.ts` | Exports `PageHeaderContextValue`, `PageHeaderContext` |
| `src/contexts/profile-context.ts` | Exports `ProfileContextValue`, `ProfileContext` |
| `src/contexts/system-actions-context.ts` | Exports `SystemActionsContext`, `SystemAction`, `SystemActionsState` |
| `src/contexts/usePageHeader.ts` | Fill header slots from `useLayoutEffect` and clear them in its cleanup. A `useEffect` cleanup on the outgoing page runs after the incoming page's layout effects, so it would erase the new page's header. |
| `src/contexts/useProfileScope.ts` | Exports `useProfileScope` |
| `src/contexts/useSystemActions.ts` | Exports `useSystemActions` |
| `src/hooks/useModalBehavior.ts` | Hook that adds standard modal behaviors when `open` is true: - Escape key calls `onClose` - Body scroll is locked - Focus is restored to the previously focused element on close Returns a ref to attach to the modal conta… |
| `src/hooks/useSidebarStatus.ts` | Exports `useSidebarStatus` |
| `src/i18n/af.ts` | Exports `af` |
| `src/i18n/ar.ts` | Exports `ar` |
| `src/i18n/context.tsx` | Exports `LOCALE_META`, `I18nProvider`, `useI18n` |
| `src/i18n/de.ts` | Exports `de` |
| `src/i18n/define-locale.ts` | Partial-locale helper: a translation file supplies only the strings it has translated and every missing key falls back to English, while unknown keys still fail the type-check. |
| `src/i18n/en.ts` | Exports `en` |
| `src/i18n/es.ts` | Exports `es` |
| `src/i18n/fr.ts` | Exports `fr` |
| `src/i18n/ga.ts` | Exports `ga` |
| `src/i18n/hu.ts` | Exports `hu` |
| `src/i18n/index.ts` | TypeScript source: `index` |
| `src/i18n/it.ts` | Exports `it` |
| `src/i18n/ja.ts` | Exports `ja` |
| `src/i18n/ko.ts` | Exports `ko` |
| `src/i18n/pt.ts` | Exports `pt` |
| `src/i18n/ru.ts` | Exports `ru` |
| `src/i18n/tr.ts` | Exports `tr` |
| `src/i18n/types.ts` | Exports `Locale`, `Translations` |
| `src/i18n/uk.ts` | Exports `uk` |
| `src/i18n/zh-hant.ts` | Exports `zhHant` |
| `src/i18n/zh.ts` | Exports `zh` |
| `src/index.css` | Stylesheet |
| `src/lib/api-aux.ts` | Wire types for GET /api/model/auxiliary (built-in + plugin-registered aux slots). |
| `src/lib/api-error.test.ts` | @vitest-environment jsdom |
| `src/lib/api-error.ts` | User-facing error shape for the dashboard REST layer. `fetchJSON` used to throw `new Error("<status>: <raw body>")`, and ~40 toast call sites interpolated the Error object (`Error: ${e}`), so users saw `Error: Error: 40… |
| `src/lib/api-files.ts` | Managed-files API types for the dashboard Files page. Moved out of api.ts so that facade stays under its code-health line cap (the interfaces keep their own cap here, per AGENTS.md § code health ratchet). |
| `src/lib/api-plugins.ts` | One security-scan finding on a plugin's new code (``scan_blocked_result`` in plugins_cmd_install.py). |
| `src/lib/api-whatsapp.ts` | Exports `WhatsAppOnboardingStartRequest`, `WhatsAppOnboardingStartResponse`, `WhatsAppOnboardingStatusResponse`, `WhatsAppOnboardingApplyResponse` |
| `src/lib/api.test.ts` | @vitest-environment jsdom |
| `src/lib/api.ts` | Exports `HERMES_BASE_PATH`, `setManagementProfile`, `getManagementProfile`, `fetchJSON`, `getWsTicket`, `buildWsAuthParam` … |
| `src/lib/automation-blueprints.ts` | Shapes of /api/cron/blueprints catalog entries (cron/blueprint_catalog.py blueprint_catalog_entry). |
| `src/lib/aux-tasks.test.ts` | Tests: auxTaskRows; renders only the built-ins when the backend sends none or only built-ins (older backend); appends plugin-registered tasks after the built-ins with the server label and hint (#40880); falls back to th… |
| `src/lib/aux-tasks.ts` | Exports `AuxTaskMeta`, `BUILTIN_AUX_TASKS`, `auxTaskRows`, `auxTaskLabel` |
| `src/lib/chat-activation.test.ts` | Tests: latchChatActivation; stays inactive while the chat tab has never been active; activates when the chat tab becomes active; stays activated after the chat tab is left (sticky / persistence) |
| `src/lib/chat-activation.ts` | Chat PTY activation latch. The dashboard keeps `ChatPage` mounted persistently (just hidden with CSS) on every route so the embedded chat PTY survives tab switches. The downside is that the PTY-connect effect would othe… |
| `src/lib/chat-channel-id.test.ts` | Tests: generateChannelId; prefixes chat when scoped and chat-fresh when not; never returns the same id twice |
| `src/lib/chat-channel-id.ts` | Channel id ties a chat tab's PTY child (publisher) to its sidebar (subscriber). Generated once per mount so a tab refresh starts a fresh channel — the previous PTY child terminates with the old WS, and its |
| `src/lib/chat-copy-last-button.tsx` | Floating "copy last response" overlay on the chat terminal: sends `/copy` over the PTY (see chat-copy-last.ts) and shows "copied" for the 1.5s reset window. |
| `src/lib/chat-copy-last.ts` | Sends `/copy` over the open PTY WebSocket, waits long enough for Ink's tokenizer to emit a keypress event per character (not coalesce them into a paste), then sends Return as its own event. The 100ms timing is empirical… |
| `src/lib/chat-image-drop.ts` | Browser clipboard/drag-and-drop image wiring for the chat host element. paste / dragover / drop listeners (capture phase) that pull image files out of the transfer data and hand them to the caller's upload+attach pipeli… |
| `src/lib/chat-panel-collapsed.ts` | Collapse state for the desktop chat side panel (model + sessions), persisted in localStorage so the choice survives reloads. Pure helpers so ChatPage stays under its FILE_LINES cap and the persistence stays testable wit… |
| `src/lib/chat-sidebar-banner.test.ts` | Tests: credentialWarning; rewrites the gateway probe into a sentence that names the provider and the fix; passes unknown warnings through untouched and ignores empty input; sidecarErrorMessage |
| `src/lib/chat-sidebar-banner.ts` | Copy for the ChatSidebar banner: the sidecar (JSON-RPC over /api/ws) and the credential probe the gateway sends in `session.info`. Pure helpers so the wording is testable without React. |
| `src/lib/chat-sidebar-session-params.test.ts` | Tests for the sidecar ``session.create`` params built by ChatSidebar. The sidecar must opt its session into close_on_disconnect so the gateway reaps the slash_worker on WS disconnect (the #21370/#21467 leak), and it mus… |
| `src/lib/chat-title.test.ts` | Tests: normalizeSessionTitle; trims non-empty session titles; treats blank and non-string values as no title; titleFromSessionInfoPayload |
| `src/lib/chat-title.ts` | Exports `normalizeSessionTitle`, `titleFromSessionInfoPayload` |
| `src/lib/chat-workspaces.test.ts` | Tests: workspaceOptions; lists project folders first, then repos by recency, deduped on path; abbreviateHomePath; collapses the home prefix only on a path boundary |
| `src/lib/chat-workspaces.ts` | Workspace picker plumbing for the dashboard Chat tab: which host directory a FRESH chat starts in (`/api/pty?cwd=`), persisted per management profile so a phone remembers the repo it drives. |
| `src/lib/chatImagePaste.test.ts` | Tests: firstImageFromClipboard; returns null for null clipboard data; finds an image via items[].getAsFile(); ignores non-file and non-image items |
| `src/lib/chatImagePaste.ts` | Clipboard image MIME → file extension. Mirrors the set the TUI's /image attach path and the gateway's image sniffer accept. |
| `src/lib/chunk-load-recovery.test.ts` | Tests: reloadForChunkLoadError; reloads once per running build: a repeat on the same build is suppressed; ignores plugin bundles, ordinary errors, and tabs without session storage; does not reload for a network failure… |
| `src/lib/chunk-load-recovery.ts` | A tab opened before `hermes update` rebuilt the SPA still references the old hashed chunks; the rebuild deleted them, so the first lazy page it opens 404s and React unmounts the whole app (blank page). A reload picks up… |
| `src/lib/clipboard.test.ts` | Tests: copyTextToClipboard; uses navigator.clipboard when available; falls back to selection copy when Clipboard API fails; uses selection copy directly in insecure browser contexts |
| `src/lib/clipboard.ts` | Exports `copyTextToClipboard` |
| `src/lib/cron-job.test.ts` | Tests: splitCronList; normalizes comma and newline separated cron list fields; buildCronJobPayload; normalizes list fields and base URLs |
| `src/lib/cron-job.ts` | Exports `CronJobFormState`, `splitCronList`, `buildCronJobPayload`, `cronJobHasExecutionContent`, `focusCronField`, `cronJobFormFromJob` … |
| `src/lib/cron-trigger-controller.test.ts` | Tests: createCronTriggerController; announces immediately and coalesces the same job while it is running; releases the job after failure so a retry can start; releases the job when the immediate feedback callback fails |
| `src/lib/dashboard-auth-reload.test.ts` | Tests: attemptDashboardTokenReloadOnce; reloads once and latches the attempt; clears the latch when asked; maybeReloadForLoopbackWsAuthFailure |
| `src/lib/dashboard-auth-reload.ts` | Exports `clearDashboardTokenReloadAttempt`, `attemptDashboardTokenReloadOnce`, `maybeReloadForLoopbackWsAuthFailure` |
| `src/lib/dashboard-flags.ts` | Exports `isDashboardEmbeddedChatEnabled` |
| `src/lib/dashboard-modal-shell.ts` | Shared dashboard dialog shell classes. Page `<Card>` defaults to `bg-background-base/80` (glass). That looks fine on the page canvas, but as a modal panel it lets the Models page bleed through and kills readability — es… |
| `src/lib/env-state.test.ts` | Tests: removeDeletedEnvVarFromState; removes a deleted custom key from dashboard state; keeps a catalog key available while marking it unset |
| `src/lib/env-state.ts` | Reconcile a successful DELETE /api/env response with the Keys page state. |
| `src/lib/events-reconnect.test.ts` | Tests: eventsReconnectDelayMs; doubles from the base delay; clamps at the cap and never exceeds it; is monotonically non-decreasing |
| `src/lib/events-reconnect.ts` | Reconnect policy for the ChatSidebar `/api/events` subscriber socket. Pure helpers, no DOM: the component owns the socket and the timer, this module owns the arithmetic and the "is this close code worth retrying" decisi… |
| `src/lib/eventsFeedClient.ts` | `/api/events` subscriber for the dashboard chat sidebar. A notification-only view of the shared JSON-RPC client: the server never answers requests on this socket (subscribers don't speak), so replay is off and `request(… |
| `src/lib/gatewayClient.test.ts` | @vitest-environment jsdom |
| `src/lib/gatewayClient.ts` | Browser WebSocket client for the tui_gateway JSON-RPC protocol. Speaks the exact same newline-delimited JSON-RPC dialect that the Ink TUI drives over stdio. The server-side transport abstraction (tui_gateway/transport.p… |
| `src/lib/keyboard-inset.test.ts` | Tests: computeKeyboardInset; returns 0 when visualViewport is unavailable; returns 0 when no keyboard is showing (vv fills layout); measures the obscured region below the visual viewport |
| `src/lib/keyboard-inset.ts` | Soft-keyboard inset math for the dashboard chat terminal (NS-434). Problem: when the on-screen keyboard opens on mobile, neither iOS Safari nor Android Chrome (default `interactive-widget=resizes-visual`) shrinks the *l… |
| `src/lib/load-error-copy.test.ts` | Tests: loadErrorCopy; fills the translated template with what failed and the detail line; omits the details line when there is no detail |
| `src/lib/load-error-copy.ts` | Fill the `{what}` / `{detail}` placeholders of the "could not load" card copy. Kept out of the component so the copy shape is testable without rendering. |
| `src/lib/log-classify.test.ts` | Tests: classifyLine; classifies by the structured level token; does NOT flag INFO lines whose payload mentions errors; does NOT let payload text spoof a higher level |
| `src/lib/log-classify.ts` | Log-line level classification for the dashboard Logs page. Prefers the structured level token emitted by hermes_logging ("2026-07-26 13:07:45,228 INFO …"); falls back to word-boundary matching for untimestamped lines (t… |
| `src/lib/mcp-dashboard-oauth.test.ts` | Tests: completeMcpDashboardOAuth; opens the authorization URL in the dashboard browser and polls to approval; surfaces a terminal OAuth error; fails before starting when the browser blocks the popup |
| `src/lib/mcp-dashboard-oauth.ts` | Exports `completeMcpDashboardOAuth` |
| `src/lib/mcp-server-create.test.ts` | Tests: buildMcpServerCreate; builds an HTTP Bearer request without stdio fields; builds OAuth and unauthenticated HTTP requests without a token; parses stdio arguments and environment assignments |
| `src/lib/mcp-server-create.ts` | Exports `McpTransport`, `McpServerDraft`, `emptyMcpServerDraft`, `buildMcpServerCreate` |
| `src/lib/memory-provider-setup.ts` | Exports `setupHasDetails`, `setupHasInstallableSteps` |
| `src/lib/model-picker-current.test.ts` | Tests: assignmentToPickerCurrent; maps a pinned auxiliary task onto that provider/model; treats missing, empty, or auto provider as auto; resolvePickerCurrent |
| `src/lib/model-picker-current.ts` | Resolve what the dashboard model picker should treat as "current". `/api/model/options` always returns the *main* chat model. Auxiliary and MoA pickers reuse that catalog, so they must pass the slot assignment or the he… |
| `src/lib/model-picker-filter.test.ts` | Tests: queryMatchesProviderOnly; returns true when the query finds the provider but no model id (issue #65374); returns false when the query also matches a model id — keeps normal filtering; returns false when the query… |
| `src/lib/model-picker-filter.ts` | True when `trimmedQuery` located the selected provider by name/slug but matches none of its models by id — the case where a single search box filtering both the provider and model columns would otherwise leave the model… |
| `src/lib/nested.ts` | Exports `getNestedValue`, `setNestedValue` |
| `src/lib/plugin-update.test.ts` | Tests: runDashboardPluginUpdate; shows a caution finding and retries with force only after the user agrees; cancel applies nothing, and a dangerous verdict throws without asking |
| `src/lib/plugin-update.ts` | The page copy this flow needs; optional keys fall back to English at the call site. |
| `src/lib/profile-bootstrap.test.ts` | Tests: initialProfileScope; does not replace a launch profile with the sticky active profile; uses the sticky active profile without a URL or launch profile; keeps a named-profile dashboard on its own profile (#96712) |
| `src/lib/profile-bootstrap.ts` | Exports `dashboardInitialProfile`, `dashboardServingProfile`, `initialProfileScope`, `shouldAdoptActiveProfile` |
| `src/lib/pty-attach-token.test.ts` | @vitest-environment jsdom |
| `src/lib/pty-attach-token.ts` | Identity of THIS browser tab's keep-alive PTY, sent as `?attach=`. The dashboard's PTY registry maps one attach token to exactly one PTY, so a token two tabs present makes the second tab take the first one's terminal ov… |
| `src/lib/pty-close-copy.test.ts` | Tests: pty close banners; offers a Reload action for the stale-token and missing-token cases; treats server rejections as banners but not transient drops or the agent exit; stops retrying after the last attempt and poin… |
| `src/lib/pty-close-copy.ts` | User-facing copy for the dashboard chat (PTY) connection lifecycle. Pure: ChatPage owns the socket and state, this module owns the words and the "which button goes with this failure" decision, so both can be tested with… |
| `src/lib/pty-composition.test.ts` | Tests: createPtyCompositionForwarder; forwards committed dead-key text when xterm emits no onData; leaves xterm; forwards a pending composition after unrelated terminal data |
| `src/lib/pty-composition.ts` | Delays an IME/dead-key commit just long enough for xterm to emit onData. xterm is authoritative when it emits onData. Browsers/layouts where it does not emit onData still forward the compositionend text on the next turn… |
| `src/lib/pty-focus.test.ts` | @vitest-environment jsdom |
| `src/lib/pty-focus.ts` | Whether ChatPage may pull keyboard focus back into the xterm textarea. Only when nothing else on the page is holding focus: `document.activeElement` is null / <body> (first activation after mount, or a return from anoth… |
| `src/lib/pty-keyboard-shortcuts.test.ts` | Tests: resolvePtyKeyboardShortcut; copies terminal selection with bare Ctrl+C on non-macOS; preserves Ctrl+C interrupt when nothing is selected; maps Ctrl+Backspace to backward word deletion |
| `src/lib/pty-keyboard-shortcuts.ts` | Exports `PtyKeyboardShortcut`, `resolvePtyKeyboardShortcut`, `sendPtyShortcutSequence` |
| `src/lib/pty-mobile-input.test.ts` | Tests: shouldTreatInputAsMobileReplacement; recognizes explicit browser replacement input; treats multi-character mobile insertText as replacement-like; normalizePtyMobileInput |
| `src/lib/pty-mobile-input.ts` | Exports `MOBILE_REPLACEMENT_WINDOW_MS`, `shouldTreatInputAsMobileReplacement`, `updatePtyInputLine`, `normalizePtyMobileInput` |
| `src/lib/pty-mouse-report.ts` | xterm.js SGR mouse tracking emits raw CSI reports (`\x1b[<...`) that look like ordinary bytes to the backend. The embedded web chat prefers input stability over terminal-style mouse reporting, so ChatPage drops these |
| `src/lib/pty-reconnect.test.ts` | Tests: shouldReconnectPtyOnPageResume; reconnects a missing socket when the active page becomes visible; reconnects closed or closing sockets on visible resume; does not restart the ladder on focus/online after it gave… |
| `src/lib/pty-reconnect.ts` | Exports `PtyConnectionState`, `PTY_RECONNECT_INPUT_MESSAGE`, `PTY_RESUME_RECONNECT_THROTTLE_MS`, `PTY_CONNECTING_TIMEOUT_MS`, `PTY_TICKET_TIMEOUT_MS`, `PTY_RECONNECT_BASE_MS` … |
| `src/lib/pty-resume-loading.test.ts` | Tests: resume hydration gate over the real sanitizer; shouldShowResumeLoadingOverlay; shows while a resume target is connecting or open and still hydrating; hides when there is no resume target |
| `src/lib/pty-resume-loading.ts` | Hard cap so a wedged resume (never gets PTY payload) cannot leave the wait notice up forever. |
| `src/lib/pty-resume-sanitizer.test.ts` | Fixture note — why most cases use CRLF, not LF. `hermes_cli/pty_bridge.py` spawns the agent through `ptyprocess.PtyProcess.spawn()` and never puts the PTY into raw mode, so the line discipline runs with ONLCR: every LF… |
| `src/lib/pty-resume-sanitizer.ts` | PTY resume output sanitizer — strips pathological ANSI sequences that Ink's two-pass virtual scroll emits during session resume. Three properties of the real pipeline drive this design: 1. **The PTY is in cooked mode (O… |
| `src/lib/pty-scroll.test.ts` | Tests: isViewportPinnedToBottom; is pinned when the viewport sits on the bottom row; releases the pin once the user scrolls up into the backlog; stays pinned if viewportY overshoots baseY while rows are trimmed |
| `src/lib/pty-scroll.ts` | Dashboard chat resume-scroll helpers. When a chat session is resumed (`/chat?resume=<id>`) the PTY backend replays the entire scrollback over the WebSocket the instant it opens. xterm.js writes those bytes into its buff… |
| `src/lib/reasoning-effort.test.ts` | Tests: normalizeEffort; treats empty/unset as the Hermes default (medium); passes through every valid effort level; is case- and whitespace-insensitive |
| `src/lib/reasoning-effort.ts` | Exports `EffortOption`, `EFFORT_OPTIONS`, `VALID_EFFORTS`, `normalizeEffort` |
| `src/lib/reasoning-markup.test.ts` | Tests: reasoning markup parsing; unwraps thinking prose; separates prose from action and result segments; does not treat unrelated angle-bracket text as reasoning markup |
| `src/lib/reasoning-markup.ts` | Exports `ReasoningMarkupSegment`, `hasReasoningMarkup`, `shouldRenderStructuredReasoning`, `parseReasoningMarkup` |
| `src/lib/resolve-page-title.test.ts` | Minimal translations stub — only the fields resolvePageTitle touches. |
| `src/lib/resolve-page-title.ts` | Exports `resolvePageTitle` |
| `src/lib/schedule.test.ts` | Tests: parseScheduleString; parses recurring interval strings; parses ISO timestamps into once mode; parses daily cron expressions |
| `src/lib/schedule.ts` | Schedule builder helpers for the cron page. The hermes-agent backend (cron/jobs.py::parse_schedule) accepts a surprisingly broad set of string formats: - Duration (one-shot): "30m", "2h", "1d" - Interval (recurring): "e… |
| `src/lib/session-import.test.ts` | Tests: parseImportSessions; accepts a single exported session; accepts arrays and wrapped session exports; accepts JSONL session exports |
| `src/lib/session-import.ts` | Exports `ImportableSession`, `parseImportSessions`, `importSummary` |
| `src/lib/session-mutations.test.ts` | Tests: prepares import and delete from snapshots and retries unchanged after a lost reply; surfaces revision conflicts and never substitutes missing counters; sends mutations when crypto.randomUUID is unavailable on an… |
| `src/lib/session-mutations.ts` | Exports `createDashboardSessionMutations` |
| `src/lib/session-prune.ts` | Exports `formatSessionPruneResult` |
| `src/lib/session-refresh.test.ts` | Tests: shouldRefreshSessions; returns false on the first poll (no baseline yet); returns false when the current response has no sessions; returns false when the newest session id is unchanged |
| `src/lib/session-refresh.ts` | Decide whether the paginated sessions list should be silently re-fetched after an overview poll. The dashboard's FastAPI server and a terminal CLI are separate processes that share the same SQLite session DB. There is n… |
| `src/lib/shared-gateway.test.ts` | Tests: sharedGatewayProfiles; names every bot on the shared multiplexer, default first; is null for standalone gateways, older backends and a lone default; servedProfileRefusal |
| `src/lib/shared-gateway.ts` | Profiles a gateway restart would blip when the managed profile is carried by the shared multiplexer (default first). `null` for a standalone gateway or an older backend without `gateway_shared_with`; those keep the plai… |
| `src/lib/skill-hub-installed.test.ts` | Tests: installedHubEntry; finds a ClawHub hit; never lets a ClawHub install answer for another source; matches an owner-qualified hit and other sources by their exact id |
| `src/lib/skill-hub-installed.ts` | The installed lock entry a hub search or featured hit names. The backend keys a ClawHub install by its lock id (` |
| `src/lib/terminal-appearance.ts` | Terminal appearance helpers shared by the chat composer's xterm host: theme colors and the layout-width-driven font tiers. Extracted from ChatPage.tsx so the page file can keep shrinking (repo file-size ratchet). |
| `src/lib/terminal-font-refit.test.ts` | Tests: refitWhenTerminalFontLoads; re-measures with the loaded face, then refits and redraws; does nothing after cleanup runs before the font arrives; skips the refit when the faces were already loaded at open() |
| `src/lib/terminal-font-refit.ts` | Dashboard xterm font stack. 'JetBrains Mono' is bundled via |
| `src/lib/terminal-touch-scroll.test.ts` | Tests: installTerminalTouchScroll; converts one-finger vertical drags into xterm scrollback lines; lets the outer page handle touch drags at the terminal boundary; removes listeners on cleanup |
| `src/lib/terminal-touch-scroll.ts` | Exports `installTerminalTouchScroll` |
| `src/lib/utils.ts` | Exports `cn`, `themedFont`, `themedBody`, `themedChrome`, `timeAgo`, `isoTimeAgo` |
| `src/lib/xterm-webgl-gating.test.ts` | @vitest-environment jsdom |
| `src/lib/xterm-webgl-gating.ts` | Gate the dashboard chat's xterm WebGL renderer. The WebGL renderer is the fast path, but a whole class of hosts and content renders wrong or dies on it: - Safari's WebGL texture atlas mangles Unicode box-drawing glyphs… |
| `src/lib/xterm-webgl-release.test.ts` | Tests: loseWebglContexts; loses every WebGL context under the host and leaves 2D canvases alone |
| `src/lib/xterm-webgl-release.ts` | Release the WebGL contexts an xterm WebglAddon left behind. ` |
| `src/main.tsx` | Before the first render, so the first lazy route is covered too. The dev server has no hashed build to go stale. |
| `src/pages/AnalyticsPage.tsx` | Exports `AnalyticsPage` |
| `src/pages/ChannelsPage.tsx` | Exports `ChannelsPage`, `WhatsAppOnboardingPanel` |
| `src/pages/ChannelsPage.whatsapp.test.tsx` | @vitest-environment jsdom |
| `src/pages/ChatPage.a11y.test.tsx` | @vitest-environment jsdom |
| `src/pages/ChatPage.test.tsx` | @vitest-environment jsdom |
| `src/pages/ChatPage.tsx` | ChatPage — embeds `hermes --tui` inside the dashboard. <div host> (dashboard chrome) . └─ <div wrapper> (rounded, dark bg, padded — the "terminal window" . look that gives the page a distinct visual identity) . └─ |
| `src/pages/ConfigPage.tsx` | Exports `ConfigPage` |
| `src/pages/CronPage.tsx` | Exports `CronPage` |
| `src/pages/DocsPage.tsx` | Exports `HERMES_DOCS_URL`, `DocsPage` |
| `src/pages/EnvPage.tsx` | Exports `EnvPage` |
| `src/pages/FilesPage.tsx` | Exports `FilesPage` |
| `src/pages/LogsPage.tsx` | Exports `LogsPage` |
| `src/pages/McpPage.tsx` | Exports `McpPage` |
| `src/pages/ModelsPage.tsx` | Exports `ModelsPage` |
| `src/pages/PairingPage.tsx` | Exports `PairingPage` |
| `src/pages/PluginsPage.test.ts` | Tests: memory provider preparation; offers preparation for a PM member without legacy pip declarations |
| `src/pages/PluginsPage.tsx` | Exports `PluginsPage` |
| `src/pages/ProfileBuilderPage.tsx` | Exports `ProfileBuilderPage` |
| `src/pages/ProfilesPage.tsx` | Exports `ProfilesPage` |
| `src/pages/SessionsPage.test.tsx` | @vitest-environment jsdom |
| `src/pages/SessionsPage.tsx` | Exports `SessionsPage` |
| `src/pages/SessionsPage_sources.tsx` | Exports `SOURCE_CONFIG`, `AUTOMATION_SESSION_SOURCES`, `NO_MATCHING_SESSION_SOURCE`, `SessionFilterCategory`, `SourceSelectionsByCategory`, `isAutomationSource` … |
| `src/pages/SkillsPage.tsx` | Exports `SkillsPage` |
| `src/pages/SystemPage.tsx` | Exports `SystemPage` |
| `src/pages/WebhooksPage.tsx` | Exports `WebhooksPage` |
| `src/plugins/PluginPage.tsx` | Exports `PluginPage` |
| `src/plugins/index.ts` | TypeScript source: `index` |
| `src/plugins/registry.test.ts` | Smoke test for the plugin SDK surface additions. Verifies that `exposePluginSDK()` writes the new dialog/toast primitives to `window.__HERMES_PLUGIN_SDK__`. Each new key is checked individually so a regression in one he… |
| `src/plugins/registry.ts` | Dashboard Plugin SDK + Registry Exposes React, UI components, hooks, and utilities on the window so that plugin bundles can use them without bundling their own copies. Plugins call window.__HERMES_PLUGINS__.register(nam… |
| `src/plugins/sdk.d.ts` | Hermes Dashboard Plugin SDK — typed contract (SPIKE) ==================================================== This is the public type surface for ``window.__HERMES_PLUGIN_SDK__`` and ``window.__HERMES_PLUGINS__``, the globa… |
| `src/plugins/slots.ts` | Plugin slot registry. Plugins can inject components into named locations in the app shell (header-left, sidebar, backdrop, etc.) by calling `window.__HERMES_PLUGINS__.registerSlot(pluginName, slotName, Component)` from… |
| `src/plugins/types.ts` | Types for the dashboard plugin system. |
| `src/plugins/usePlugins.profile.test.tsx` | @vitest-environment jsdom The plugin loader is bound to one profile: its list request, the asset URLs built from that list, and the plugins it reports (PLG-3). A list for an older selection that lands after a |
| `src/plugins/usePlugins.test.ts` | Tests: plugin manifest cache helpers; getCachedManifests returns null when nothing is cached; getCachedManifests returns null for invalid JSON; getCachedManifests returns null for non-array JSON |
| `src/plugins/usePlugins.ts` | usePlugins hook — discovers and loads dashboard plugins. 1. Fetches plugin manifests from GET /api/dashboard/plugins 2. Injects CSS <link> tags for plugins that declare css 3. Loads plugin JS bundles via <script> tags 4… |
| `src/postcss-build.test.ts` | Tests for `postcss-build` |
| `src/themes/context.tsx` | Exports `ThemeProvider`, `useTheme` |
| `src/themes/fonts.ts` | Curated UI-font catalog for the dashboard font override. The font override is an independent layer that sits ON TOP of the active theme: a theme still ships its own `typography.fontSans` default, but a user can pick any… |
| `src/themes/index.ts` | TypeScript source: `index` |
| `src/themes/presets.test.ts` | Every preset the dashboard shares with the desktop must render the shared table's palette, not a private copy — that is the whole point of the table. The second assertion keeps the projection honest: whatever slot the m… |
| `src/themes/presets.ts` | Built-in dashboard themes. Each theme defines its own palette, typography, and layout so switching themes produces visible changes beyond just color — fonts, density, and corner-radius all shift to match the theme's per… |
| `src/themes/types.ts` | Dashboard theme model. Themes customise three orthogonal layers: 1. `palette` — the 3-layer color triplet (background/midground/ foreground). Legacy `warmGlow` / `noiseOpacity` fields remain for theme YAML compat but ar… |
| `tsconfig.app.json` | JSON data/configuration |
| `tsconfig.json` | JSON object with keys `files`, `references` |
| `tsconfig.node.json` | JSON data/configuration |
| `vite.config.ts` | React Compiler preset scoped to modules that can actually contain components/hooks (JSX syntax or a react-ish import). The preset's default code filter matches any PascalCase/use* declaration — effectively every TS modu… |
| `vitest.config.ts` | Same component/hook-scoped compiler preset as vite.config.ts. |
