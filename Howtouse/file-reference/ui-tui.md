# File reference: `ui-tui`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `ui-tui/`

| File | What it does |
|---|---|
| `.gitignore` | Git ignore rules |
| `CANONICAL_GATEWAY.md` | Ink canonical local gateway connection |
| `README.md` | Hermes TUI |
| `eslint.config.mjs` | JavaScript (ES module): `eslint.config` |
| `package.json` | JSON manifest for `hermes-tui` |
| `tsconfig.build.json` | JSON object with keys `extends`, `compilerOptions` |
| `tsconfig.json` | JSON object with keys `compilerOptions`, `include`, `exclude` |
| `vitest.config.ts` | TypeScript source: `vitest.config` |

## `ui-tui/packages/`

| File | What it does |
|---|---|
| `hermes-ink/ambient.d.ts` | Exports `c`, `FiberRoot`, `ConcurrentRoot`, `LegacyRoot`, `DiscreteEventPriority`, `ContinuousEventPriority` … |
| `hermes-ink/index.d.ts` | TypeScript source: `index.d` |
| `hermes-ink/index.js` | JavaScript source: `index` |
| `hermes-ink/package.json` | JSON manifest for `@hermes/ink` |
| `hermes-ink/src/bootstrap/state.ts` | Exports `flushInteractionTime`, `updateLastInteractionTime`, `markScrollActivity`, `getIsInteractive` |
| `hermes-ink/src/entry-exports.ts` | TypeScript source: `entry-exports` |
| `hermes-ink/src/hooks/use-stderr.ts` | Exports `StderrHandle`, `useStderr` |
| `hermes-ink/src/hooks/use-stdout.ts` | Exports `StdoutHandle`, `useStdout` |
| `hermes-ink/src/ink/Ansi.tsx` | Exports `Ansi` |
| `hermes-ink/src/ink/absolute-in-zero-height-box.test.tsx` | Tests: absolute children of a zero-height box; paints an absolute bottom:100% panel when its host box collapses to h=0 |
| `hermes-ink/src/ink/ansi-transition.test.ts` | Tests: transitionAnsiCodes weight family; bold → dim resets the weight family before applying dim; dim → bold resets the weight family before applying bold; carries color changes through a weight swap |
| `hermes-ink/src/ink/ansi-transition.ts` | Bold (SGR 1) and dim (SGR 2) are INDEPENDENT terminal attributes that share one reset code (SGR 22). `diffAnsiCodes` models "same endCode" as "same slot, new start code overwrites" — true for fg (39) / bg (49), false he… |
| `hermes-ink/src/ink/app-held-return-stall.test.ts` | A single-line read ending in CR holds the CR for BURST_END_QUIET_MS. Under host load the event loop can stall past that window while the next paste chunk already waits in the fd: Node runs the timers phase before the po… |
| `hermes-ink/src/ink/app-mouse-watchdog.test.ts` | DECRQM request for mode 1000 (what the watchdog writes). |
| `hermes-ink/src/ink/app-mouse.test.ts` | Tests: handleMouseEvent right-click selection behavior; copies an active selection instead of dispatching right-click paste handlers; clears the highlight after a successful right-click copy; keeps the highlight when ri… |
| `hermes-ink/src/ink/app-rawmode-mouse.test.ts` | Tests: App raw-mode teardown; disables mouse tracking when the last raw-mode consumer detaches |
| `hermes-ink/src/ink/app-stdin-recovery.test.ts` | Regression for issue #31486: when processInput throws inside the handleReadable read loop, any bytes still buffered in stdin are stranded because Node only emits 'readable' on buffer transitions, not for data |
| `hermes-ink/src/ink/bidi.ts` | Bidirectional text reordering for terminal rendering. Terminals on Windows do not implement the Unicode Bidi Algorithm, so RTL text (Hebrew, Arabic, etc.) appears reversed. This module applies the bidi algorithm to reor… |
| `hermes-ink/src/ink/cache-eviction.ts` | Unified cache eviction for the four hot Ink module-level caches: - widthCache (stringWidth.ts) - wrapCache (wrap-text.ts) |
| `hermes-ink/src/ink/clearTerminal.ts` | Cross-platform terminal clearing with scrollback support. Detects modern terminals that support ESC[3J for clearing scrollback. |
| `hermes-ink/src/ink/colorize.test.ts` | Tests: shouldUseRichEightBitDowngradeForLegacyAppleTerminal; uses Rich-compatible 256-color downgrade on legacy Apple Terminal; normalizes Apple Terminal names before matching; does not rewrite when Apple Terminal adver… |
| `hermes-ink/src/ink/colorize.ts` | xterm.js (VS Code, Cursor, code-server, Coder) has supported truecolor since 2017, but code-server/Coder containers often don't set COLORTERM=truecolor. chalk's supports-color doesn't recognize TERM_PROGRAM=vscode (it o… |
| `hermes-ink/src/ink/components/AlternateScreen.tsx` | Exports `AlternateScreen` |
| `hermes-ink/src/ink/components/App.focus.test.tsx` | Tests: App terminal focus events; notifies the renderer on DECSET 1004 focus transitions |
| `hermes-ink/src/ink/components/App.tsx` | Exports `App`, `handleMouseEvent` |
| `hermes-ink/src/ink/components/AppContext.ts` | Exports `Props` |
| `hermes-ink/src/ink/components/Box.tsx` | Exports `Props` |
| `hermes-ink/src/ink/components/Button.tsx` | Exports `Props` |
| `hermes-ink/src/ink/components/ClockContext.tsx` | Exports `Clock`, `createClock`, `ClockContext`, `ClockProvider` |
| `hermes-ink/src/ink/components/CursorAdvanceContext.ts` | Notify Ink that the physical terminal cursor was advanced by an out-of-band stdout.write (e.g. the TextInput fast-echo path). This is a two-part notification — calling it updates both: 1. Ink's cached `displayCursor` (t… |
| `hermes-ink/src/ink/components/CursorDeclarationContext.ts` | Exports `CursorDeclaration`, `CursorDeclarationSetter` |
| `hermes-ink/src/ink/components/ErrorOverview.tsx` | Error's source file is reported as file:///home/user/file.js This function removes the file://[cwd] part |
| `hermes-ink/src/ink/components/Link.tsx` | Exports `Props`, `Link` |
| `hermes-ink/src/ink/components/Newline.tsx` | Exports `Props`, `Newline` |
| `hermes-ink/src/ink/components/NoSelect.tsx` | Exports `NoSelect` |
| `hermes-ink/src/ink/components/RawAnsi.tsx` | Exports `RawAnsi` |
| `hermes-ink/src/ink/components/ScrollBox.tsx` | Exports `ScrollBoxHandle`, `ScrollBoxProps` |
| `hermes-ink/src/ink/components/Spacer.tsx` | A flexible space that expands along the major axis of its containing layout. It's useful as a shortcut for filling all the available spaces between elements. |
| `hermes-ink/src/ink/components/StdinContext.ts` | Exports `Props` |
| `hermes-ink/src/ink/components/TerminalFocusContext.tsx` | Exports `TerminalFocusContextProps`, `TerminalFocusProvider` |
| `hermes-ink/src/ink/components/TerminalSizeContext.tsx` | Exports `TerminalSize`, `TerminalSizeContext` |
| `hermes-ink/src/ink/components/Text.test.ts` | Tests: shouldUseAnsiDim; disables ANSI dim on VTE terminals by default; disables ANSI dim on Apple Terminal by default; keeps ANSI dim enabled elsewhere by default |
| `hermes-ink/src/ink/components/Text.tsx` | Exports `Props`, `shouldUseAnsiDim`, `setDimFallbackColor`, `dimColorFallback`, `Text` |
| `hermes-ink/src/ink/constants.ts` | Shared frame interval for render throttling and animations (~60fps). |
| `hermes-ink/src/ink/cursor.ts` | Exports `Cursor` |
| `hermes-ink/src/ink/devtools.ts` | Optional react-devtools hook; package may be absent. |
| `hermes-ink/src/ink/dom.ts` | Exports `TextName`, `ElementNames`, `NodeNames`, `DOMElement`, `TextNode`, `DOMNode` … |
| `hermes-ink/src/ink/events/click-event.ts` | Mouse click event. Fired on left-button release without drag, only when mouse tracking is enabled (i.e. inside <AlternateScreen>). Bubbles from the deepest hit node up through parentNode. Call stopImmediatePropagation()… |
| `hermes-ink/src/ink/events/cmd-shortcuts.test.ts` | Tests: enhanced keyboard modifier parsing; detects modified Enter sequences for multiline composer shortcuts; preserves Cmd as super for kitty keyboard CSI-u sequences; preserves forwarded VS Code/Cursor Cmd+C copy sequ… |
| `hermes-ink/src/ink/events/dispatcher.ts` | Exports `Dispatcher` |
| `hermes-ink/src/ink/events/emitter.ts` | Similar to node's builtin EventEmitter, but is also aware of our `Event` class, and so `emit` respects `stopImmediatePropagation()`. |
| `hermes-ink/src/ink/events/event-handlers.ts` | Exports `EventHandlerProps`, `HANDLER_FOR_EVENT`, `EVENT_HANDLER_PROPS` |
| `hermes-ink/src/ink/events/event.ts` | Exports `Event` |
| `hermes-ink/src/ink/events/focus-event.ts` | Focus event for component focus changes. Dispatched when focus moves between elements. 'focus' fires on the newly focused element, 'blur' fires on the previously focused one. Both bubble, matching react-dom's use of foc… |
| `hermes-ink/src/ink/events/input-event-control-chord.test.ts` | Regression: #115284 — a stray `l` in the TUI composer after a session resume / tab switch / window restore. The dashboard writes the PTY force-redraw byte (Ctrl+L, 0x0c — `hermes_cli/pty_session.py` |
| `hermes-ink/src/ink/events/input-event.ts` | Exports `Key`, `InputEvent` |
| `hermes-ink/src/ink/events/keyboard-event.ts` | Keyboard event dispatched through the DOM tree via capture/bubble. Follows browser KeyboardEvent semantics: `key` is the literal character for printable keys ('a', '3', ' ', '/') and a multi-char name for special keys (… |
| `hermes-ink/src/ink/events/mouse-event.ts` | Exports `MouseEvent` |
| `hermes-ink/src/ink/events/paste-event.ts` | Exports `PasteEvent` |
| `hermes-ink/src/ink/events/resize-event.ts` | Exports `ResizeEvent` |
| `hermes-ink/src/ink/events/terminal-event.ts` | Exports `TerminalEvent`, `EventTarget` |
| `hermes-ink/src/ink/events/terminal-focus-event.ts` | Exports `TerminalFocusEventType`, `TerminalFocusEvent` |
| `hermes-ink/src/ink/focus.ts` | Exports `FocusManager`, `getRootNode`, `getFocusManager` |
| `hermes-ink/src/ink/frame.ts` | Exports `Frame`, `emptyFrame`, `FlickerReason`, `FrameEvent`, `Patch`, `Diff` … |
| `hermes-ink/src/ink/get-max-width.ts` | Returns the yoga node's content width (computed width minus padding and border). Warning: can return a value WIDER than the parent container. In a column-direction flex parent, width is the cross axis — align-items: str… |
| `hermes-ink/src/ink/global.d.ts` | TypeScript source: `global.d` |
| `hermes-ink/src/ink/hit-test.test.ts` | Tests: hit-test; hits absolutely positioned children that paint outside their parent rect |
| `hermes-ink/src/ink/hit-test.ts` | Exports `hitTest`, `dispatchClick`, `dispatchMouse`, `dispatchHover` |
| `hermes-ink/src/ink/hooks/use-animation-frame.ts` | Hook for synchronized animations that pause when offscreen. Returns a ref to attach to the animated element and the current animation time. All instances share the same clock, so animations stay in sync. The clock only… |
| `hermes-ink/src/ink/hooks/use-app.ts` | `useApp` is a React hook, which exposes a method to manually exit the app (unmount). |
| `hermes-ink/src/ink/hooks/use-cursor-advance.ts` | Returns a function that notifies Ink the physical terminal cursor was advanced out-of-band (e.g. by a direct stdout.write from the TextInput fast-echo bypass). Calling the returned function updates two pieces of Ink sta… |
| `hermes-ink/src/ink/hooks/use-declared-cursor.ts` | Declares where the terminal cursor should be parked after each frame. Terminal emulators render IME preedit text at the physical cursor position, and screen readers / screen magnifiers track the native cursor — so parki… |
| `hermes-ink/src/ink/hooks/use-external-process.ts` | Exports `RunExternalProcess`, `withInkSuspended`, `useExternalProcess` |
| `hermes-ink/src/ink/hooks/use-input.ts` | TypeScript source: `use-input` |
| `hermes-ink/src/ink/hooks/use-interval.ts` | Returns the clock time, updating at the given interval. Subscribes as non-keepAlive — won't keep the clock alive on its own, but updates whenever a keepAlive subscriber (e.g. the spinner) is driving the clock. Use this… |
| `hermes-ink/src/ink/hooks/use-search-highlight.ts` | Set the search highlight query on the Ink instance. Non-empty → all visible occurrences are inverted on the next frame (SGR 7, screen-buffer overlay, same damage machinery as selection). Empty → clears. This is a screen… |
| `hermes-ink/src/ink/hooks/use-selection.ts` | Access to text selection operations on the Ink instance (fullscreen only). Returns no-op functions when fullscreen mode is disabled. |
| `hermes-ink/src/ink/hooks/use-stdin.ts` | `useStdin` is a React hook, which exposes stdin stream. |
| `hermes-ink/src/ink/hooks/use-tab-status.ts` | Exports `TabStatusKind`, `useTabStatus` |
| `hermes-ink/src/ink/hooks/use-terminal-focus.ts` | Hook to check if the terminal has focus. Uses DECSET 1004 focus reporting - the terminal sends escape sequences when it gains or loses focus. These are handled automatically by Ink and filtered from useInput. |
| `hermes-ink/src/ink/hooks/use-terminal-title.ts` | Declaratively set the terminal tab/window title. Pass a single string to set both the tab and window title (OSC 0). Pass `{ tab, window }` to set them independently: the short `tab` string goes to OSC 1 (icon/tab label)… |
| `hermes-ink/src/ink/hooks/use-terminal-viewport.ts` | Exports `useTerminalViewport` |
| `hermes-ink/src/ink/hyperlinkHover.ts` | Highlight every cell whose OSC 8 hyperlink matches `hoveredUrl` by inverting its style. This is the cursor-hover affordance for clickable links: terminal applications can't change the system mouse cursor, so we light up… |
| `hermes-ink/src/ink/ink-backpressure.test.ts` | Regression for issue #31486 (stdout-backpressure strand): when the previous frame's stdout.write has not drained (the terminal parser is overwhelmed — a wide CR+LF burst on a high-context session), the renderer |
| `hermes-ink/src/ink/ink-cursor-advance.test.ts` | Tests: Ink.noteExternalCursorAdvance; seeds displayCursor from frontFrame.cursor when nothing was parked; is a no-op when the delta is zero; skips displayCursor on alt-screen — CSI H resets every frame |
| `hermes-ink/src/ink/ink-focus-redraw.test.ts` | Focus-regain recovery (DECSET 1004 focus-in). Two properties are asserted against the RESULTING SCREEN, not against which bytes were emitted: 1. Healing — a row that is stale on the physical screen but BLANK in the new… |
| `hermes-ink/src/ink/ink-resize.test.ts` | Tests: Ink resize healing; heals same-dimension alt-screen resize events with an erase before repaint; converges to a clean erased frame after a rapid resize burst |
| `hermes-ink/src/ink/ink.tsx` | Exports `Options`, `Ink` |
| `hermes-ink/src/ink/instances.ts` | Store all instances of Ink (instance.js) to ensure that consecutive render() calls use the same instance of Ink and don't create a new one This map has to be stored in a separate file, because render.js creates instance… |
| `hermes-ink/src/ink/layout/engine.ts` | Exports `createLayoutNode` |
| `hermes-ink/src/ink/layout/geometry.ts` | Exports `Point`, `Size`, `Rectangle`, `Edges`, `edges`, `addEdges` … |
| `hermes-ink/src/ink/layout/node.ts` | -- Adapter interface for the layout engine (Yoga) |
| `hermes-ink/src/ink/layout/yoga.ts` | Exports `YogaLayoutNode`, `createYogaLayoutNode` |
| `hermes-ink/src/ink/line-width-cache.ts` | During streaming, text grows but completed lines are immutable. Caching stringWidth per-line avoids re-measuring hundreds of unchanged lines on every token (~50x reduction in stringWidth calls). |
| `hermes-ink/src/ink/log-update.test.ts` | Contract tests for LogUpdate.render() — the diff-to-ANSI path that owns whether the terminal picks up each React commit correctly. These tests pin down a few load-bearing invariants so that any fix for the "scattered le… |
| `hermes-ink/src/ink/log-update.ts` | Exports `LogUpdate` |
| `hermes-ink/src/ink/lru.ts` | Shared eviction for the hot Ink LRU caches (widthCache, wrapCache, sliceCache, lineWidthCache). Hot-path touch-on-read stays inlined per cache — only the bulk eviction is factored here. |
| `hermes-ink/src/ink/measure-element.ts` | TypeScript source: `measure-element` |
| `hermes-ink/src/ink/measure-text.ts` | TypeScript source: `measure-text` |
| `hermes-ink/src/ink/node-cache.ts` | Cached layout bounds for each rendered node (used for blit + clearing). `top` is the yoga-local getComputedTop() — stored so ScrollBox viewport culling can skip yoga reads for clean children whose position hasn't shifte… |
| `hermes-ink/src/ink/optimizer.ts` | Optimize a diff by applying all optimization rules in a single pass. This reduces the number of patches that need to be written to the terminal. Rules applied: - Remove empty stdout patches - Merge consecutive cursorMov… |
| `hermes-ink/src/ink/osc-response-chain.test.ts` | End-to-end (minus the PTY): a terminal's OSC 11 reply arriving on stdin must tokenize as a response, match the pending oscColor(11) query, and parse to a hex background. This is the exact chain App.tsx relies on for |
| `hermes-ink/src/ink/output.ts` | Exports `Operation`, `Clip`, `Output` |
| `hermes-ink/src/ink/parse-keypress-drop-probe.test.ts` | Probe: feed many exotic IME-ish byte patterns straight through the parser and assert NO printable character codepoint silently vanishes. This catches the "chunk falls through every branch -> name:'' with a non-printable |
| `hermes-ink/src/ink/parse-keypress-noregress.test.ts` | Confirm the control-byte split is a NO-OP for clean input (EVKey-style: backspace and recomposed text arrive in separate, non-fused reads). The fix must not change behavior for any text token that has no embedded |
| `hermes-ink/src/ink/parse-keypress.test.ts` | Tests: legacy modified return parsing; legacy function-key parsing; parseMultipleKeypresses bracketed paste recovery; emits empty bracketed pastes when the terminal sends both markers |
| `hermes-ink/src/ink/parse-keypress.ts` | Keyboard input parser - converts terminal input to key events Uses the termio tokenizer for escape sequence boundary detection, then interprets sequences as keypresses. |
| `hermes-ink/src/ink/reconciler.ts` | Exports `dispatcher`, `recordYogaMs`, `getLastYogaMs`, `markCommitStart`, `getLastCommitMs`, `resetProfileCounters` |
| `hermes-ink/src/ink/render-border.test.ts` | Tests: renderBorder viewport parity; intersects nested output clips without changing surviving border cells; renders borders after opaque fills and preserves the fill interior; keeps clipped border parity when an absolu… |
| `hermes-ink/src/ink/render-border.ts` | Exports `BorderTextOptions`, `CUSTOM_BORDER_STYLES`, `BorderStyle` |
| `hermes-ink/src/ink/render-node-to-output.ts` | Exports `resetLayoutShifted`, `didLayoutShift`, `didAbsoluteOverlayMove`, `ScrollHint`, `resetScrollHint`, `ScrollFastPathStats` … |
| `hermes-ink/src/ink/render-to-screen.ts` | Exports `MatchPosition`, `renderToScreen`, `scanPositions`, `applyPositionedHighlight` |
| `hermes-ink/src/ink/renderer.ts` | Exports `RenderOptions`, `Renderer`, `createRenderer` |
| `hermes-ink/src/ink/root.ts` | Exports `RenderOptions`, `Instance`, `Root`, `forceRedraw`, `renderSync`, `createRoot` |
| `hermes-ink/src/ink/screen.ts` | --- Shared Pools (interning for memory efficiency) --- Character string pool shared across all screens. With a shared pool, interned char IDs are valid across screens, |
| `hermes-ink/src/ink/searchHighlight.ts` | Highlight all visible occurrences of `query` in the screen buffer by inverting cell styles (SGR 7). Post-render, same damage-tracking machinery as applySelectionOverlay — the diff picks up highlighted cells as ordinary… |
| `hermes-ink/src/ink/selection.test.ts` | Tests: selection whitespace handling; does not copy whitespace-only selections; trims outer drag padding while preserving selected content; preserves selected indentation when spaces are rendered content |
| `hermes-ink/src/ink/selection.ts` | Text selection state for fullscreen mode. Tracks a linear selection in screen-buffer coordinates (0-indexed col/row). Selection is line-based: cells from (startCol, startRow) through (endCol, endRow) inclusive, wrapping… |
| `hermes-ink/src/ink/squash-text-nodes.ts` | A segment of text with its associated styles. Used for structured rendering without ANSI string transforms. |
| `hermes-ink/src/ink/stringWidth.ts` | Exports `stringWidth`, `widthCacheSize`, `evictWidthCache` |
| `hermes-ink/src/ink/styles.ts` | Exports `RGBColor`, `HexColor`, `Ansi256Color`, `AnsiColor`, `Color`, `TextStyles` … |
| `hermes-ink/src/ink/supports-hyperlinks.ts` | Additional terminals that support OSC 8 hyperlinks but aren't detected by supports-hyperlinks. Checked against both TERM_PROGRAM and LC_TERMINAL (the latter is preserved inside tmux). |
| `hermes-ink/src/ink/tabstops.ts` | Tab expansion, inspired by Ghostty's Tabstops.zig Uses 8-column intervals (POSIX default, hardcoded in terminals like Ghostty) |
| `hermes-ink/src/ink/terminal-background.test.ts` | setTerminalBackgroundHex is first-writer-wins module state — re-import a fresh module instance per test so cases don't contaminate each other. |
| `hermes-ink/src/ink/terminal-focus-state.ts` | Terminal focus state signal — non-React access to DECSET 1004 focus events. 'unknown' is the default for terminals that don't support focus reporting; consumers treat 'unknown' identically to 'focused' (no throttling). |
| `hermes-ink/src/ink/terminal-querier.ts` | Query the terminal and await responses without timeouts. Terminal queries (DECRQM, DA1, OSC 11, etc.) share the stdin stream with keyboard input. Response sequences are syntactically distinguishable from key events, so… |
| `hermes-ink/src/ink/terminal.test.ts` | Tests: terminal resize quirks; uses a deeper alt-screen resize clear for Apple Terminal; keeps the normal resize repaint path for modern terminals; synchronized output detection |
| `hermes-ink/src/ink/terminal.ts` | Exports `Progress`, `isProgressReportingAvailable`, `isSynchronizedOutputSupported`, `setXtversionName`, `isXtermJs`, `needsAltScreenResizeScrollbackClear` … |
| `hermes-ink/src/ink/termio.ts` | ANSI Parser Module A semantic ANSI escape sequence parser inspired by ghostty, tmux, and iTerm2. Key features: - Semantic output: produces structured actions, not string tokens - Streaming: can parse input incrementally… |
| `hermes-ink/src/ink/termio/ansi.ts` | ANSI Control Characters and Escape Sequence Introducers Based on ECMA-48 / ANSI X3.64 standards. |
| `hermes-ink/src/ink/termio/csi.ts` | CSI (Control Sequence Introducer) Types Enums and types for CSI command parameters. |
| `hermes-ink/src/ink/termio/dec.ts` | DEC (Digital Equipment Corporation) Private Mode Sequences DEC private modes use CSI ? N h (set) and CSI ? N l (reset) format. These are terminal-specific extensions to the ANSI standard. |
| `hermes-ink/src/ink/termio/esc.ts` | ESC Sequence Parser Handles simple escape sequences: ESC + one or two characters |
| `hermes-ink/src/ink/termio/host.ts` | Which emulator is hosting this TUI, when the host tells us. `hermes dashboard` spawns the TUI behind a PTY and mirrors it into xterm.js in the browser; the bridge sets HERMES_PTY_HOST=dashboard on the child (hermes_cli/… |
| `hermes-ink/src/ink/termio/osc.test.ts` | Tests: shouldEmitClipboardSequence; suppresses local multiplexer clipboard OSC by default; keeps OSC enabled for remote or plain local terminals; honors explicit env override |
| `hermes-ink/src/ink/termio/osc.ts` | OSC (Operating System Command) Types and Parser |
| `hermes-ink/src/ink/termio/parser.test.ts` | Tests: output parser line endings after ESC |
| `hermes-ink/src/ink/termio/parser.ts` | ANSI Parser - Semantic Action Generator A streaming parser for ANSI escape sequences that produces semantic actions. Uses the tokenizer for escape sequence boundary detection, then interprets each sequence to produce st… |
| `hermes-ink/src/ink/termio/sgr.ts` | SGR (Select Graphic Rendition) Parser Parses SGR parameters and applies them to a TextStyle. Handles both semicolon (;) and colon (:) separated parameters. |
| `hermes-ink/src/ink/termio/tokenize.test.ts` | Tests: tokenizer escape-sequence boundaries; tokenizer state-aware flush; drops a partial control sequence that survives a second flush (truncation); still emits a bare ESC on flush so the Escape key works |
| `hermes-ink/src/ink/termio/tokenize.ts` | Input Tokenizer - Escape sequence boundary detection Splits terminal input into tokens: text chunks and raw escape sequences. Unlike the Parser which interprets sequences semantically, this just identifies boundaries fo… |
| `hermes-ink/src/ink/termio/types.ts` | ANSI Parser - Semantic Types These types represent the semantic meaning of ANSI escape sequences, not their string representation. Inspired by ghostty's action-based design. |
| `hermes-ink/src/ink/useTerminalNotification.ts` | Exports `TerminalWriteContext`, `TerminalWriteProvider`, `TerminalNotification`, `useTerminalNotification` |
| `hermes-ink/src/ink/warn.ts` | Exports `ifNotInteger` |
| `hermes-ink/src/ink/widest-line.ts` | Exports `widestLine` |
| `hermes-ink/src/ink/wrap-text.test.ts` | Tests: wrapText wrap-trim; removes a single soft-wrap boundary space; preserves extra original spacing at soft-wrap boundaries; preserves leading whitespace on unwrapped source lines |
| `hermes-ink/src/ink/wrap-text.ts` | Exports `wrapText`, `wrapCacheSize`, `evictWrapCache` |
| `hermes-ink/src/ink/wrapAnsi.ts` | TypeScript source: `wrapAnsi` |
| `hermes-ink/src/native-ts/yoga-layout/enums.ts` | Exports `Align`, `BoxSizing`, `Dimension`, `Direction`, `Display`, `Edge` … |
| `hermes-ink/src/native-ts/yoga-layout/index.ts` | Exports `Value`, `MeasureFunction`, `Size`, `Config`, `Node`, `getYogaCounters` |
| `hermes-ink/src/native-ts/yoga-layout/round-layout.test.ts` | Tests: incremental layout rounding; keeps rounding work flat when only the clock changes; re-rounds cached raw geometry when the point scale changes; matches a fresh full layout across leaf, root, and scale changes |
| `hermes-ink/src/utils/debug.ts` | Exports `logForDebugging` |
| `hermes-ink/src/utils/earlyInput.ts` | Exports `startCapturingEarlyInput`, `stopCapturingEarlyInput`, `consumeEarlyInput`, `hasEarlyInput`, `seedEarlyInput`, `isCapturingEarlyInput` |
| `hermes-ink/src/utils/env.ts` | Exports `env`, `supportsOsc52Clipboard` |
| `hermes-ink/src/utils/envUtils.ts` | Exports `isEnvTruthy` |
| `hermes-ink/src/utils/execFileNoThrow.test.ts` | These tests shell out to /bin/sh, use chmodSync(0o755), and rely on POSIX sleep/job control. They will not work on Windows. |
| `hermes-ink/src/utils/execFileNoThrow.ts` | Exports `execFileNoThrow` |
| `hermes-ink/src/utils/fullscreen.ts` | Exports `isMouseClicksDisabled` |
| `hermes-ink/src/utils/intl.ts` | Exports `getGraphemeSegmenter`, `firstGrapheme`, `lastGrapheme`, `getWordSegmenter`, `getRelativeTimeFormat`, `getTimeZone` … |
| `hermes-ink/src/utils/log.ts` | Exports `logError` |
| `hermes-ink/src/utils/semver.ts` | Exports `gt`, `gte`, `lt`, `lte`, `satisfies`, `order` |
| `hermes-ink/src/utils/sliceAnsi.ts` | Exports `sliceAnsi`, `sliceCacheSize`, `evictSliceCache` |
| `hermes-ink/text-input.d.ts` | TypeScript source: `text-input.d` |
| `hermes-ink/text-input.js` | JavaScript source: `text-input` |
| `hermes-ink/tsconfig.json` | JSON object with keys `extends` |

## `ui-tui/scripts/`

| File | What it does |
|---|---|
| `bench-history-scroll.tsx` | Deterministic virtual-history benchmark. The file intentionally uses only APIs present before the performance candidate so the exact same script can be copied/run on base and candidate checkouts. |
| `bench-native-history.tsx` | Compare the native primary-buffer transcript with the virtualized ScrollBox path. Run from ui-tui: npx tsx scripts/bench-native-history.tsx --warmups=1 --samples=3 --items=100,1000,10000 |
| `bench-streaming-md.tsx` | Benchmark: streamed-markdown render strategies for the TUI. Replays a newline-terminated, block-heavy synthetic stream at width 80 through a real Ink render (renderSync + rerender per update) and compares: |
| `billing-fixtures.tsx` | Billing/Subscription TUI fixture harness — renders any single overlay STATE live in the terminal so it can be screenshotted (tmux) and UX-reviewed. This is a DEV/REVIEW tool, not shipped behaviour. It bypasses the gatew… |
| `clipboard_image.py` | Extract the Ink host clipboard without loading a session runtime. |
| `gateway_bootstrap.py` | Ink's private pipe bootstrap; the child is a client, never an agent owner. |
| `i18n-export-en.ts` | TypeScript source: `i18n-export-en` |
| `i18n-keys.ts` | TypeScript source: `i18n-keys` |
| `native_canonical_probe.py` | Disposable ordinary-daemon + real Ink PTY probe (no renderer injection). |
| `native_stop_probe.py` | Loopback Stop exercise and observation-only recording of real RPC replies. |
| `profile-tui.mjs` | JavaScript (ES module): `profile-tui` |
| `visual/paths.mjs` | Shared output location for the visual harness. Hardcoded '/tmp/...' paths resolve to a drive-root like C:\tmp on native Windows (and fail when the directory doesn't exist) — os.tmpdir() is the platform-neutral answer. |
| `visual/render.tsx` | Visual self-verification tool: `npm run visual` renders real TUI surfaces across theme x background scenes to <tmpdir>/hermes-tui-visual/tui-visual.html, then shot.mjs screenshots it to tui-visual.png for eyeball + agen… |
| `visual/run.mjs` | Zero-dependency launcher for the visual harness (`npm run visual`). - Sets FORCE_COLOR/COLORTERM itself instead of POSIX `VAR=x cmd` shell assignments (which break under the Windows npm command shell) — no |
| `visual/shot.mjs` | Screenshot the render.tsx output with the workspace's Electron (offscreen). |

## `ui-tui/src/`

| File | What it does |
|---|---|
| `__tests__/activeSessionSwitcher.test.ts` | Tests: session orchestrator helpers; turns model picker values into session-scoped draft model args; highlights the current live session when the picker opens; adds a selectable New row after the live sessions and gates… |
| `__tests__/agentControls.test.ts` | Tests: reports queued acceptance rather than claiming delivery and preserves rejected text; resolves hub labels against the active language at call time, not import time; keeps every roster selection in the visible view… |
| `__tests__/agentRoster.test.ts` | Tests: never rolls event progress back when an older live snapshot arrives; lets the agents shortcut leave the composer without stealing redo; merges one row per actual child and does not notify unchanged snapshots |
| `__tests__/agentsCompact.test.tsx` | Tests: keeps collapsed live chrome to one row without losing count or restore controls; opens the selected live transcript on Enter while details remain independently accessible |
| `__tests__/agentsDock.test.tsx` | Tests: bounds painted chrome by viewport while retaining true live count and activity; deduplicates async batches and hides settled history without dropping live work |
| `__tests__/agentsHydration.test.tsx` | Tests: does not undo an acknowledged pause when opening status resolves late |
| `__tests__/appChromeBlockedTimers.test.tsx` | Tests: status-chrome timers under an occluding overlay; arms the one-second SessionDuration + IdleSince clocks when nothing covers the rule; arms no timer at all when an occluding overlay is already open; arms the FaceT… |
| `__tests__/appChromeStatusRule.test.tsx` | Tests: StatusRule model label; shows a clamped effort as what the route sends, never as a distinct level (#61634); StatusRule session title; marks only estimated context occupancy at every visible width |
| `__tests__/approvalAction.test.ts` | Tests: approvalAction — pure key dispatch for ApprovalPrompt; maps Esc to deny — parity with global Ctrl+C cancellation; maps number keys 1..4 to once/session/always/deny in registration order; ignores out-of-range numb… |
| `__tests__/attachments.test.ts` | Tests: expandTokens (what the agent actually receives); replaces a collapsed paste label with its full content; is a no-op for already-expanded / token-free text (recall round-trip); expands repeated identical labels in… |
| `__tests__/billingStepUp.test.tsx` | Stub useInput so the overlay doesn't enter raw mode under renderSync. |
| `__tests__/blockLayout.test.ts` | Tests: messageGroup; classifies each block kind into its visual band; hasLeadGap; opens a gap only at a boundary between working-area groups |
| `__tests__/brandingCanonicalSnapshot.test.ts` | A canonical gateway's create/resume snapshot carries main's banner inventory (gateway/session_local_inventory.py). The TUI renders main's banner from it unchanged: tools by toolset, skills by category, MCP servers, and… |
| `__tests__/brandingMcpCount.test.ts` | Invariant under test: the TUI banner's MCP headline counts *connected* servers, never configured-but-disabled ones. This mirrors the classic CLI banner (`mcp_connected = sum(1 for s in mcp_status if s["connected"])` in |
| `__tests__/bundleNoAsyncEsmDeadlock.test.ts` | Bundle-shape regression for issue #31227. The dashboard TUI ships as a single esbuild-bundled `dist/entry.js`. When the bundle contains an `async`-init `__esm` wrapper that participates in a circular module graph, esbui… |
| `__tests__/busyQueueAdmission.test.tsx` | Canonical authority rows: `pending` carries the server-issued admission_id, the client's input_id and the public text under `ref` destination fields. |
| `__tests__/canonicalCommandObserve.test.ts` | PLG-7: the shared gateway fires `pre_command` for the commands it runs (slash.exec, command.dispatch). A registry command Ink runs itself is reported through `command.observe` once it ran, as the classic CLI reports its… |
| `__tests__/canonicalDetachClose.test.tsx` | Tests: a resume switch closes the previous view with tui_close; a live switch only detaches; exit closes every held view with tui_shutdown |
| `__tests__/canonicalDetachOrdering.test.tsx` | Tests for `canonicalDetachOrdering` |
| `__tests__/canonicalDisplayPrefs.test.ts` | Tests: the shared gateway persists display preferences through config.set and prints main\; a standalone backend still persists them through config.set |
| `__tests__/canonicalGateway.test.ts` | Tests: retains prepared identity and rejects unsupported TUI launch policy instead of impersonating CLI; carries -s/--checkpoints/--pass-session-id/--accept-hooks (and exported HERMES_ACCEPT_HOOKS=1) onto session.create… |
| `__tests__/canonicalHistory.test.ts` | Tests: hydrates canonical persisted replies through the same transcript path as resumed sessions |
| `__tests__/canonicalI18n.test.ts` | pastels §3: this PR's shared-gateway client text (image staging, launch-contract refusals) is resolved through the catalog at call time, so an installed pack translates it. |
| `__tests__/canonicalImages.test.ts` | Tests: stages private immutable local bytes, uploads remote bytes, and never falls back to a client path; resolves a relative image path in the session folder, never the ui-tui install; extracts clipboard on the client… |
| `__tests__/canonicalMultipartResumeRows.test.ts` | N94: a resumed canonical snapshot whose user row is multipart (text + image parts) still renders that user turn; `content` stays on the row for /undo targeting. |
| `__tests__/canonicalPickerDelete.test.tsx` | The shared gateway has no `session.delete` (-32601): the picker's two-press delete is its revision-fenced `session.mutate operation=delete`, and a refusal stays on screen. |
| `__tests__/canonicalResumeDisplayProjection.test.ts` | TUI parity (PR #106742 rows 12b/31/32): a resumed canonical session renders main's display projection (`display_messages`, the sidecar's `_history_to_messages`), not the raw stored rows. |
| `__tests__/canonicalRetainedControlRetire.test.ts` | A lost-reply control may be retried only as the session's very next control: after another verb, re-issuing it must mint a fresh request_id instead of replaying the stale receipt. |
| `__tests__/canonicalRetryValidate.test.ts` | dokterdok N92 (Ink half): /retry validates the target turn BEFORE rewinding it, as the classic chat and main's retry_last do (agent/context_compressor_retry.py::retryable_user_text): an image turn is refused with nothin… |
| `__tests__/canonicalSessionControls.test.ts` | Tests: canonical model, branch and compression use generation-fenced owner mutations and hydrate results; ambiguous mutations retry the frozen identity while unsupported model scopes never mutate; late model or compress… |
| `__tests__/canonicalSessionPicker.test.tsx` | Tests: canonical sessions render and select owner rows using only the canonical list |
| `__tests__/canonicalSideAgents.test.ts` | The shared (canonical) gateway serves prompt.background / prompt.btw: /bg and /btw take main's path there too instead of refusing with canonical.controls.notAvailable. |
| `__tests__/canonicalSidecarSessionVerbs.test.tsx` | Ink verbs that resolve their session_id in the legacy sidecar's own map. On the shared gateway the sidecar never holds the session, so each answered "session not found" (or an empty roster). Every site here must either… |
| `__tests__/canonicalSlashCommands.test.ts` | pastels §2.5: on the shared (canonical) gateway Ink's /title /undo /retry /usage /tools must use the verbs that gateway serves — never the legacy session.title / session.undo / session.usage / slash.exec RPCs it answers… |
| `__tests__/canonicalStartupImage.test.ts` | Tests: startup image bytes travel with the literal prompt and attachment failure prevents a text-only run |
| `__tests__/canonicalStoredPicker.test.tsx` | Tests: renders and resumes stored history alongside live canonical sessions |
| `__tests__/canonicalSwitcherClose.test.tsx` | #139536: on a canonical gateway the switcher's `^d` close sent no request at all (`session.close` is not in the canonical contract) and then reported "session was already closed". The view closes the row it holds with m… |
| `__tests__/canonicalTuiOps.test.ts` | The shared gateway serves Ink's /save, /reload, /agents pause\|resume and /rollback through the owner verbs in gateway/session_tui_ops.py: each command reaches its verb and renders main's text. |
| `__tests__/canonicalUnsupportedCommand.test.ts` | The shared owner's slash.exec runs only its reviewed reads and refuses every other command with `unsupported_command` (gateway/session_commands.py). Every Ink path that forwards a command there (the generic fallback and… |
| `__tests__/canonicalUsageTotals.test.ts` | Tests: /usage shows main; /usage before any API call says so, as main did; /usage on a usage-window plan adds the allowance bars after the totals; /usage on any other account adds nothing (the billing state carries no p… |
| `__tests__/charts.test.ts` | Tests: chart primitives; sparkline spans the block ramp and respects width; is dimension-stable: short/empty series pad to exactly width; sparkRows partitions each column across rows (top line first) |
| `__tests__/chatBitsCatalog.test.ts` | The chat-bits sibling (branding, thinking, messageLine, todo, queued, entry) is registered in the en facade and resolves through the runtime — including the non-React `messages()` path entry.tsx uses at call time, which… |
| `__tests__/clarifyBatchReconnect.test.tsx` | The owner answers every client request on the next tick; a test sets what session.resume returns. |
| `__tests__/clarifyTranscript.test.ts` | Tests: clarifySettledRows; writes main; reads a blank answer as skipped |
| `__tests__/clipboard.test.ts` | Tests: readClipboardText; reads text from pbpaste on macOS; reads text from PowerShell on Windows; tries powershell.exe first on WSL |
| `__tests__/coldPendingRenderer.test.tsx` | Tests: cold-resumes native queued and ambiguous records by durable identity with a live retry target; cold recovery excludes foreign identities and never replays an ambiguous legacy attempt |
| `__tests__/completionApply.test.ts` | Tests: applyCompletion; replaces from compReplace and drops the leading slash from the row; keeps the leading slash when the row carries one and input does not; replaces an argument token after a space (subcommand compl… |
| `__tests__/composerDestinationRenderer.test.tsx` | Tests: captures hotkey destination before reading the clipboard, while preserving current-owner pastes; discards stale image, drop fallback and collapse completions without changing the new composer |
| `__tests__/composerFreshnessRenderer.test.tsx` | Tests: does not restore stale same-session paste results after editing away and back |
| `__tests__/composerHighlights.test.ts` | Tests: splitComposerHighlights; marks a command invocation and a skill named mid-prose; marks @ references, including quoted values with spaces; marks attachment and paste tokens |
| `__tests__/connectorAccounts.test.ts` | Tests: connector account rows; folds retired accounts and names unnamed ones by their label; refuses a malformed name and a name another live account of the same app holds; reconnect is offered only as a repair |
| `__tests__/contentTables.test.ts` | Tests: content tables read the active catalog lazily; fortunes()/faces()/toolVerbs() observe applyLocale; setup panel keeps the command cells untranslated; dailyFortune draws from the catalog bags |
| `__tests__/createGatewayEventHandler.deferredPick.test.ts` | Tests: a model pick made during a turn that did not apply at the boundary; names the refusal and shows the committed model again; asks before applying a guarded pick, and the answer re-sends with the owner token; a conf… |
| `__tests__/createGatewayEventHandler.notice.test.ts` | Split out of createGatewayEventHandler.test.ts (file-size budget); the mock, ctx builder and beforeEach are duplicated from there unchanged. |
| `__tests__/createGatewayEventHandler.test.ts` | Tests: createGatewayEventHandler; displays generic errors without settling versioned execution; an idle snapshot a frame ahead of the final leaves the tool trail for the final to archive; fences restarted owner lifecycl… |
| `__tests__/createGatewayEventHandler.usage.test.ts` | Tests: canonical session.usage tick; maps the top-level session.stats fields onto the status-bar usage (FINDINGS row 5); passes main; reports cache hit and omits absent figures |
| `__tests__/createGatewayEventHandler.usageLimit.test.ts` | Tests: the usage-limit card on a canonical connection; switches this session with session.mutate (the owner refuses config.set model) and re-sends after it applied; applies nothing to, and never retries, a chat the user… |
| `__tests__/createGatewayEventHandler.wake.test.ts` | T9: a shared-owner session's voice mode is the owner's per-session /voice state, the one voice.record gates on; the sidecar's voice.toggle flips only its process-global flag. |
| `__tests__/createSlashHandler.test.ts` | DASHBOARD_TUI_MODE resolves once at module load from HERMES_TUI_DASHBOARD, so toggling process.env in a test body can't move it. Mock just that one export (everything else stays real) and flip the holder per test. |
| `__tests__/cursorDriftRegression.test.ts` | Pinned regression for the multi-line composer cursor-drift bug. Symptom: in `hermes --tui`, typing into the composer until the input wraps across multiple visual rows would leave several blank cells between the last typ… |
| `__tests__/details.test.ts` | Tests: parseDetailsMode; accepts the canonical modes case-insensitively; rejects junk; isSectionName |
| `__tests__/emoji.test.ts` | Tests: ensureEmojiPresentation; passes through ASCII unchanged; passes through emoji that already defaults to emoji presentation; injects VS16 after text-default emoji codepoints |
| `__tests__/externalLink.test.ts` | Tests: external link helpers; formats URL fallbacks as host + path; derives readable title fallbacks from URL slugs; keeps x.com status fallbacks link-like instead of generic Status labels |
| `__tests__/forceTruecolor.test.ts` | Tests: forceTruecolor; does not force truecolor by default; does not infer truecolor from Apple Terminal on pre-Tahoe macOS; downgrades Apple Terminal when truecolor is only advertised by env |
| `__tests__/gatewayBrowserLinks.test.ts` | Tests: free_tier.challenge; shows the link and opens one tab per ticket; an optional check opens nothing; the gateway event handler routes the event to the presenter |
| `__tests__/gatewayClient.test.ts` | Tests: GatewayClient websocket attach mode; publishes canonical readiness once after discovery and arms the negotiated heartbeat; /logs carries the attach lifecycle like main\; boots the owner |
| `__tests__/gatewayClientHeartbeatLiveness.test.ts` | The TUI channel counts streamed deltas as liveness (#115251): a turn that streams a frame per second for minutes must never trip the 45s deadline, while a socket gone fully silent still fails. This pins the wiring option |
| `__tests__/gatewayClientKillLatch.test.ts` | The race from issue #114987: kill() left the client's transport reference in place, so the transport's late exit reached handleTransportExit → emit('exit') → useMainApp's recovery subscriber → start(), which un-latched |
| `__tests__/gatewayLocalLaunch.test.ts` | Tests: reports failed canonical bootstrap without creating an independent owner or retrying ensure; reports a bootstrap that cannot load Hermes once and stops retrying (#138878) |
| `__tests__/gatewayRecovery.test.ts` | Tests: planGatewayRecovery; recovers the live session and records the attempt; does not recover when there is no session to resume; keeps retrying the recovery target through a startup crash-loop, bounded by the budget |
| `__tests__/gatewayStartTimeout.test.ts` | Tests: shows a terminal bootstrap verdict and its remedy, never |
| `__tests__/goalBar.test.tsx` | Tests: shows a standing goal (active, parked, paused) and hides it once done or cleared |
| `__tests__/gracefulExit.test.ts` | Tests: shouldExitForSignal; ignores only the signals explicitly disabled for embedded dashboard chat |
| `__tests__/i18nRuntime.test.ts` | Tests: TUI i18n catalog; siblings own disjoint top-level namespaces; every leaf is a string or a function; flattenKeys emits sorted dotted leaves |
| `__tests__/imeVietnameseTelex.test.tsx` | End-to-end regression coverage for Vietnamese Telex IME recomposition (OpenKey / Unikey / EVKey). These IMEs commit a finished syllable by emitting a burst of backspaces (and, for OpenKey, a U+202F NARROW NO-BREAK |
| `__tests__/inkIdleSessionInfoStamp.test.ts` | Tests: an idle canonical session.info keeps its payload stamp and passes the lifecycle fence |
| `__tests__/inkOfflinePollRedial.test.ts` | B2-20: Ink keeps `sid` across a socket close (gatewayConnected:false). The 1.5 s refresh poll must stop while offline (each request re-dials through ensureAttachedWebSocket and collapses the reconnect backoff), and ever… |
| `__tests__/inkRemoteReceiptHome.test.tsx` | C22: an explicit HERMES_TUI_GATEWAY_URL owner on another home/machine answers receipts naming ITS profile_id; Ink validates them against the owner identity from the snapshot, not its local HERMES_HOME, and still rejects… |
| `__tests__/inkResumeSnapshotFence.test.tsx` | Tests: a completion that beats the resume reply is replayed after the snapshot, covered frames are dropped |
| `__tests__/inlineSlashSkill.test.ts` | Tests: inlineSlashTrigger; detects a slash typed mid-message; detects a bare slash after whitespace, before any name is typed; fires after a newline, not just a space |
| `__tests__/inputSelectionClipboard.test.ts` | Tests: handleInputSelectionClipboard; copies an active composer selection; cuts an active composer selection; leaves shortcuts available when there is no active selection |
| `__tests__/journeyCommand.test.ts` | Tests: /journey slash command; opens the journey overlay when run; is preserved by the flow-overlay soft reset (deliberate, user-opened) |
| `__tests__/legacyAdmissionRecovery.test.ts` | Tests: never redispatches an ambiguous legacy attempt after native journal reload |
| `__tests__/libTextI18n.test.ts` | The `libText` namespace is resolved at call time, never at module load, so a pack installed after import must be observed by every helper on its next call. |
| `__tests__/loaders.test.ts` | Tests: ShimmerRows leniency (agent-authored calls); accepts a bare row COUNT and derives widths — the generated-code shape; shimmerSegments; always partitions the full width |
| `__tests__/loopBar.test.tsx` | Tests: counts a standing loop down to its next wakeup and hides it once done or cleared; counts down on its own clock between snapshots and stops once the wakeup runs |
| `__tests__/markdown.test.ts` | Tests: INLINE_RE emphasis; matches word-boundary italic/bold; keeps intraword underscores literal; keeps Python dunder identifiers literal |
| `__tests__/mathUnicode.test.ts` | Tests: texToUnicode — symbols; substitutes lowercase Greek; substitutes set theory and logic operators; substitutes relations and arrows |
| `__tests__/memoryMonitor.test.ts` | memory.js performs real heap dumps / fs work — stub it so the monitor's dump path is a no-op in tests. |
| `__tests__/mergeUsageStable.test.ts` | Tests: mergeUsageStable (#41480 status-bar flicker); returns the PRIOR reference when a patch changes nothing; returns the prior reference for an undefined patch; returns a new merged object when a value actually changes |
| `__tests__/messageLine.test.ts` | Tests: shouldShowResponseSeparator; separates assistant response text from visible details; does not add a response separator without details or body text; does not add response separators to non-assistant transcript ro… |
| `__tests__/messages.test.ts` | Tests: toTranscriptMessages; preserves assistant tool-call rows so resume does not drop prior turns; skips hidden display_kind rows entirely; projects model_switch as an event with replaced text |
| `__tests__/moaProgressActivity.test.ts` | Tests: moa.progress / moa.phase activity surface; shows ; swaps the progress line for the aggregator phase on moa.phase; ignores malformed payloads (missing counters / unknown phase) |
| `__tests__/modelPicker.test.ts` | Tests: ModelPicker provider filtering; keeps the selected provider when clearing the provider filter; returns -1 when provider is undefined; returns -1 when provider slug is not in rows |
| `__tests__/modelPickerReasoning.test.ts` | Tests: ModelPicker reasoning step; emits one /model request carrying provider, effort and scope; skips the step only when the catalog says the route has no reasoning control; resolves the labelled effort rows against th… |
| `__tests__/orchestratorPromptSession.test.ts` | Tests: startPromptLiveSession; keeps the created target through a delayed model switch without publishing into the new focus; starts a kept-live session with generated id/title, applies selected model, then dispatches t… |
| `__tests__/osc52.test.ts` | Tests: buildOsc52ClipboardQuery; returns the raw OSC52 query outside multiplexers; wraps the query for tmux passthrough; parseOsc52ClipboardData |
| `__tests__/overlayPrimitives.test.ts` | Tests: clampOverlayWidth; prefers preferred, capped by maxWidth; honors caps BELOW the usability floor instead of overflowing the cell; keeps the floor when the cap allows it |
| `__tests__/parentLog.test.ts` | parentLog gates itself off under VITEST so unit tests can't pollute a real ~/.hermes. To exercise the real persistence path we clear that gate, point HERMES_HOME at a temp dir, and re-import the module fresh (path + ena… |
| `__tests__/paths.test.ts` | Tests: shortCwd; collapses HOME to ~; leaves non-HOME paths alone; truncates long paths from the left with ellipsis |
| `__tests__/pendingMigrationRenderer.test.tsx` | Tests: moves compression queues across cached successors without changing attempted receipts or losing settlement; keeps queue order when inputs queued in the same millisecond on two sessions merge; uses the canonical p… |
| `__tests__/petPane.test.tsx` | Tests: PetPane; overlays the bottom-right corner with a flat, right-aligned sprite; renders nothing when disabled |
| `__tests__/petPolling.test.ts` | Tests: requestPetUpdate; does not enqueue pet.cells while pets are disabled; uses metadata only when the enabled state is already cached; fetches cells only for an enabled uncached state |
| `__tests__/platform.test.ts` | Tests: still uses Ctrl as the action modifier on non-macOS; keeps Ctrl+C as the local non-macOS copy chord; accepts client Cmd+C over SSH even when running on Linux; does not treat local Linux Alt+C as copy |
| `__tests__/precisionWheel.test.ts` | Tests: precisionWheel; passes the first modifier-held wheel event; coalesces same-frame events without throttling line-by-line scroll; keeps queued momentum in precision mode briefly after modifier release |
| `__tests__/processDock.test.tsx` | Tests: keeps running processes, ages finished ones out after the retention window, and carries the exit verdict; paints a Processes block under the agents without letting either block hide the other |
| `__tests__/prompt.test.ts` | Tests: composerPromptText; returns shell prompt for ! commands; prefixes named profiles onto the normal prompt; does not prefix default or custom profiles |
| `__tests__/promptResponseFreshness.test.ts` | Tests: allows only the original prompt in the original execution to publish a response |
| `__tests__/providers.test.ts` | Tests: providerDisplayNames; returns bare names when all are unique; appends slug to every collision so the disambiguation is symmetric; only disambiguates the colliding group |
| `__tests__/queueEditKeepsFields.test.ts` | Tests: editing the text of a local queued item; keeps its attachments, destination and control intent, and starts a new submission |
| `__tests__/queueScopeRenderer.test.tsx` | Tests: pending input destination |
| `__tests__/queueSubmission.test.ts` | Tests: /queue collapsed paste submission; keeps the collapsed argument for display and the full multiline payload for execution; supports the /q alias and rejects an empty queue command; expands paste tokens without con… |
| `__tests__/reasoning.test.ts` | Tests: splitReasoning; extracts <think>…</think> and strips it from text; handles multiple tag shapes; treats unclosed leading <think>… as reasoning (real reasoning-model stream) |
| `__tests__/receiptBusyRenderer.test.tsx` | Tests: reconciles terminal and unknown retries to idle so queued follow-ups can drain without another terminal event; preserves a newer running generation across old receipts and delayed idle snapshots |
| `__tests__/replayGapReattach.test.tsx` | Tests: re-attaches the current session when its subscription overflows on a healthy socket; ignores a replay gap for a session that is not in focus |
| `__tests__/resumeEpochRenderer.test.tsx` | Tests: only the newest attachment request may replace session authority; resumes a successor with a reset epoch while retaining original attempted admission targets; detaches the prior canonical subscription only after… |
| `__tests__/rpc.test.ts` | Tests: asRpcResult; keeps plain object payloads; rejects missing or non-object payloads; rpcErrorMessage |
| `__tests__/scroll.test.ts` | Tests: scrollWithSelectionBy; commits the clamped target directly instead of queueing a scroll delta; uses fresh scroll height when cached height would swallow a down-scroll at a fake bottom; uses fresh height when pend… |
| `__tests__/scrollBoxRendererBounds.test.ts` | Tests: ScrollBox renderer bounds; rejects invalid imperative geometry without poisoning scroll state; fails closed on corrupt ScrollBox child geometry and keeps adjacent rows renderable; clips corrupt dirty-child DECSTB… |
| `__tests__/sessionActivationPrompts.test.tsx` | Tests: activating a live session hydrates its pending approval exactly like resume does |
| `__tests__/slashAttachmentRenderer.test.tsx` | Tests: canonical slash images submit staged bytes and deleting tokens removes payload without RPC detach; slash attachment submission leaves a visible removable image in the cleared composer; stale attachment cleanup us… |
| `__tests__/slashCatalog.test.ts` | Tests: loadSlashCatalog; binds the catalog to the live session, so each session; drops a reply that arrives after the live session has changed |
| `__tests__/slashCatalogSkillsChanged.test.ts` | CFG-8: a skill installed from another terminal reaches Ink's palette through the gateway. |
| `__tests__/slashParity.test.ts` | Tests: slash parity matrix; /q alias resolves to queue, not quit (#31983); /s alias resolves to steer, not sessions or a TUI-local command (#119176); parseSlashCommand argument fidelity |
| `__tests__/slashSessionAuthority.test.tsx` | Tests: branch hydration replaces source authority only after a successful destination attachment |
| `__tests__/spawnHistoryStore.test.ts` | Tests: spawnHistoryStore status normalization; keeps timeout/error statuses from disk snapshots; falls back unknown disk statuses to completed |
| `__tests__/startupLatency.test.ts` | Tests: startup latency metric; reports launch->ready once per process across repeated gateway.ready and handler remounts |
| `__tests__/startupLatencyDashboard.test.ts` | Its own file: the launch latch is module state, so a dashboard TUI must be the first reporter this module ever sees for the test to prove anything. DASHBOARD_TUI_MODE resolves at module load from HERMES_TUI_DASHBOARD, s… |
| `__tests__/stateIsolation.test.ts` | Tests: TUI state isolation; does not notify ui/composer subscribers for high-frequency turn updates |
| `__tests__/statusBarTicker.test.ts` | Tests: FaceTicker verb padding; pads every verb to the same width; keeps trailing ellipsis attached |
| `__tests__/statusRule.test.ts` | Tests: statusRuleWidths; keeps the status rule within the terminal width; truncates the cwd segment before it can wrap in skinny terminals; omits the cwd segment when there is no room for it |
| `__tests__/steerCommand.test.ts` | Tests: /steer; steers the live turn when the gateway accepts; queues the text for the next turn when the gateway rejects the steer |
| `__tests__/streamingMarkdown.test.ts` | Tests: findStableBoundary; returns -1 when no blank line exists yet; returns -1 when only single newlines exist; splits after the last blank line separator |
| `__tests__/subagentTree.test.ts` | Tests: aggregate: tokens, cost, files, hotness; sums tokens and cost across subtree; counts files read + written across subtree; hotness = totalTools / totalDuration |
| `__tests__/submissionCore.test.ts` | A gateway double whose `input.detect_drop` resolution we control, so we can observe UI state DURING the async gap — the exact window the queue-mode race lived in. |
| `__tests__/submissionCoreUndeliveredCorrection.test.ts` | #141511: a busy correction the owner refused before any agent saw it (the turn the TUI believed busy had ended) stayed in the journal as a control naming that dead generation, so every retry was refused again and the wo… |
| `__tests__/submissionDestinationRenderer.test.tsx` | Tests: submits interpolated queued input only to its captured owner and removes it only after the matching receipt; refuses the whole submit when a {!cmd} cannot run instead of sending a placeholder to the model |
| `__tests__/subscriptionCommand.test.ts` | Tests: /subscription slash command; fetches subscription.state and opens the overlay; shows portal-login sys line when not logged in; /upgrade alias resolves to the same command |
| `__tests__/subscriptionOverlay.test.tsx` | Tests: SubscriptionOverlay — overview; free with catalog: plans render inline; the generic portal row disappears; free with catalog: picking a plan opens the portal once, even on double-Enter; subscriber: status line +… |
| `__tests__/syntax.test.ts` | Tests: syntax highlighter; recognizes supported langs and aliases; paints a whole-line comment dim; paints keywords, strings, and numbers in a ts line |
| `__tests__/terminalModes.test.ts` | Tests: terminal mode reset; clears the native frame only on TTY streams; writes reset sequence to TTY streams without fds; skips non-TTY streams |
| `__tests__/terminalParity.test.ts` | Tests: terminalParityHints; warns for Apple Terminal and SSH/tmux sessions; suggests IDE setup only for VS Code-family terminals that still need bindings |
| `__tests__/terminalSetup.test.ts` | Tests: terminalSetup helpers; detects VS Code family terminals from environment; computes VS Code style config dirs cross-platform; strips line comments from keybindings JSON |
| `__tests__/termuxComposerLayout.test.ts` | Tests: Termux composer prompt + width guards; suppresses profile prefixes on narrow Termux panes; keeps profile context on very wide Termux panes; reserves fewer columns for gutter on narrow Termux widths |
| `__tests__/text.test.ts` | Tests: isToolTrailResultLine; detects completion markers; buildToolTrailLine; puts completion duration inline before the result marker |
| `__tests__/textInputBurstInput.test.ts` | Tests: applyPrintableInsert; applies non-bracketed multi-character bursts immediately; replaces the selected range for burst input; rejects control or escape-bearing input |
| `__tests__/textInputCursorSourceOfTruth.test.ts` | Closes Copilot follow-up on PR #26717: the original cursor-drift fix bumped Ink's displayCursor / cursorDeclaration on fast-echo, but if TextInput itself re-renders before the deferred 16ms `setCur` |
| `__tests__/textInputCut.test.ts` | Tests: cutSelection (transactional cut); removes the selection only after the clipboard write succeeds; keeps the text intact when the clipboard write fails (headless/SSH); awaits the write before removing (no fire-and-… |
| `__tests__/textInputFastEcho.test.ts` | Tests: canFastAppendShape; accepts plain ASCII appended at end of single-line input; rejects when cursor is not at end of line; rejects when current is empty (placeholder render path needed) |
| `__tests__/textInputKillLine.test.ts` | Ctrl+U / Ctrl+K are readline motions scoped to the *current logical line*, not the whole buffer. Claude Code documents Ctrl+U as "repeat to clear across lines in multiline input", which only works if a press at a line |
| `__tests__/textInputLineKill.test.ts` | Cmd+Backspace should kill to the line boundary, but the modifier it is distinguished by matters a great deal. `isActionMod` is the wrong test: - on macOS it accepts `key.meta`, and hermes-ink reports Option as |
| `__tests__/textInputLineNav.test.ts` | Tests: lineNav; returns null for single-line input (up); returns null when cursor already on first line of a multiline block; returns null when cursor on last line of a multiline block |
| `__tests__/textInputPassThrough.test.ts` | Tests: shouldPreserveCtrlJNewline; preserves Ctrl+J as newline in Ghostty even when tmux masks TERM/TERM_PROGRAM; keeps bare local POSIX LF-compatible prompts submitting on Ctrl+J; shouldPassThroughToGlobalHandler |
| `__tests__/textInputRedoShift.test.tsx` | Treat the kitty `super` bit as the action modifier regardless of host OS so the Cmd+Shift+Z chord below is exercised on every CI lane. |
| `__tests__/textInputReturnBurst.test.ts` | Tests: valueForReturnSubmit; includes printable input that arrives in the same keypress as return; keeps IME commit text when it arrives in the same burst as return; leaves the draft unchanged when return carries no pri… |
| `__tests__/textInputRightClick.test.ts` | Tests: decideRightClickAction; returns paste when there is no selection; returns paste for a collapsed (empty) range; copies the slice when range covers non-empty text |
| `__tests__/textInputStaleParentEcho.test.tsx` | Regression coverage for the stale own-echo rewind (#111934): while a deferred key-burst flush is in flight, the parent's re-render can hand the TextInput the value it emitted BEFORE the user typed further characters. |
| `__tests__/textInputSubmitClear.test.tsx` | Tests: TextInput submit clearing; accepts the parent clear after a Korean IME commit immediately followed by Enter; clears the composer when text and a CSI-u Enter arrive in one read; keys after a CSI-u Enter in the sam… |
| `__tests__/textInputWordDelete.test.ts` | Tests: Ctrl+Delete → ESC d decode contract; decodes ESC d as meta+; deleteWordForward; deletes the word to the right of the cursor |
| `__tests__/textInputWrap.test.ts` | Helper: compute the "end of text" position that wrap-ansi would render the input to. This is what Ink's <Text wrap="wrap"> uses, so cursorLayout MUST agree. Disagreement is the cursor-drift bug. |
| `__tests__/theme.test.ts` | `theme.js` reads `process.env` at module-load to compute DEFAULT_THEME, and `fromSkin` closes over DEFAULT_THEME. A developer shell with HERMES_TUI_THEME=light (or HERMES_TUI_BACKGROUND set to something |
| `__tests__/themeBoot.test.ts` | Review on #20379 (finding 2): the boot cache seeds the previous session's background into HERMES_TUI_BACKGROUND, which detectLightMode treats as a CURRENT signal. Without provenance, a stale light cache pins a now-dark |
| `__tests__/thinkingLiveCollapse.test.tsx` | Tests: ToolTrail — collapsed mode auto-expands while reasoning is live; collapses (▸) when reasoningActive is false under sections.thinking: collapsed; closes the panel when the reasoning phase ends mid-turn (rerender);… |
| `__tests__/thinkingMoaReferenceVisibility.test.tsx` | Tests: ToolTrail — MoA reference panel visibility (#64701); stays expanded after mount effects settle when reasoningAlwaysVisible is set, even under sections.thinking: hidden |
| `__tests__/topupCommand.test.ts` | Tests: /billing slash command (overlay-driven); not logged in → prompts to log in, no overlay; bare /billing opens the overlay on the overview screen with state; any sub-command arg is ignored — still opens the overview… |
| `__tests__/transformedFinal.test.ts` | A transform_llm_output plugin rewrites the final after the raw reply streamed: the completion carries the rewrite (response_transformed) and the transcript must show only that. |
| `__tests__/turnControllerNotice.test.ts` | turnController.startMessage() treats "flash and yield" notices (the usage-band credits.usage and the one-time credits.grant_spent transition) as "show until next prompt": they flash once, then yield when the next turn s… |
| `__tests__/turnControllerTodos.test.ts` | turnController.recordTodos() parses the raw `todo` tool payload into TodoItem[]. Nested subtasks (apps/desktop's `parent` field) must survive this parse — the TUI todo panel renders hierarchy from it via todoTree(). |
| `__tests__/turnStore.test.ts` | Tests: turnStore live progress helpers; archives completed todos into a transcript trail and clears the live anchor; archives incomplete todos with an incomplete flag so the hint renders; returns nothing when there are… |
| `__tests__/usageCommand.test.ts` | Tests: /usage slash command; resolves the CTA at run time, so a locale pack applied after import is observed; always shows the CTA; ; prints window usage one stripped line at a time |
| `__tests__/usageGauge.test.ts` | Tests: usage gauge coloring; maps used fill like the model picker (green / yellow / red); recognises a gauge row; colors only the bar, leaves the rest of the /usage line alone |
| `__tests__/usagePanel.test.ts` | Tests: planUsageLines; a nearly full allowance reads 99% beside its 9 cells, like the CLI and Desktop; 100% only once the allowance is spent |
| `__tests__/useBatteryPoll.test.ts` | Tests: toBatteryInfo; returns null for a null payload; maps a full reading through faithfully; clamps and rounds the percent into 0-100 |
| `__tests__/useCompletion.test.ts` | Tests: completionRequestForInput; routes real slash commands to slash completion; does not route absolute paths through slash completion; keeps path completion for trailing absolute path tokens |
| `__tests__/useComposerState.test.ts` | Tests: looksLikeDroppedPath; recognizes macOS screenshot temp paths and file URIs; rejects normal multiline or plain text paste; recognizes paths with spaces (not backslash-escaped) |
| `__tests__/useConfigSync.test.ts` | Tests: applyDisplay; fans every display flag out to $uiState and the bell callback; hydrates the destructive slash confirmation policy from approvals; defaults destructive slash confirmation on and preserves it across c… |
| `__tests__/useInputHandlers.test.ts` | Tests: shouldFallThroughForScroll — keep transcript scrolling alive during prompt overlays; falls through for wheel scrolls; falls through for PageUp / PageDown; falls through for Shift+ArrowUp / Shift+ArrowDown |
| `__tests__/useQueue.test.ts` | Tests: removeAtInPlace; removes the item at the given index in place; is a no-op when the index is out of bounds; queue items |
| `__tests__/useSessionLifecycle.test.ts` | Tests: fresh session boundary; signals only when a live session is replaced by a different session; writeActiveSessionFile; writes the actual resumed session id for the shell exit summary |
| `__tests__/useSessionLifecycleGatewayConnected.test.ts` | Tests: a successful bind restores gatewayConnected; /new after a failed recovery resume leaves the composer sending again; activating a live session after a failed recovery resume leaves the composer sending again |
| `__tests__/useSessionLifecycleStoredSid.test.ts` | Mount the real hook and hand its API to the test once the first commit is done. |
| `__tests__/useSubmission.test.ts` | Tests: prepareSubmission; keeps the collapsed paste for display and expands the model payload; does not execute interpolation syntax hidden inside pasted content; visible interpolation combined with a collapsed paste |
| `__tests__/useVirtualHistoryHeights.test.ts` | Tests: ensureVirtualItemHeight; reuses cached heights without invoking the estimator; lazily seeds missing heights from the estimator; falls back to the default estimate when no estimator is provided |
| `__tests__/userMessages.test.ts` | Tests: describeTurnFailure; turns an auth error_surface into a plain title, a Details line and the /model + /retry hint; falls back to the layer copy, and to a generic title, when the code is unknown; honours error_surf… |
| `__tests__/userMessagesUnavailableMethod.test.ts` | Both server routes now answer a missing method with what the backend knows (it does not serve the method); a JSON-RPC client sends no version, so the TUI must not turn that into a claim that the versions differ, nor int… |
| `__tests__/userWidgets.test.ts` | Tests: user widget loading; missing directory is a clean no-op; loads .mjs from disk, registers, dispatches, and reports broken files; a deleted file unregisters its apps on the next scan |
| `__tests__/vaultSaveLoginPrompt.test.tsx` | Tests: VaultSaveLoginPrompt (#109101); shows the identifier step first for the requesting site; declines the whole save when the identifier step is submitted empty; moves to the masked password step after a non-empty id… |
| `__tests__/viewport.test.ts` | Tests: stickyPromptFromViewport; hides the sticky prompt when a newer user message is already visible; shows the latest user message above the viewport when no user message is visible; shows the last prompt once the vie… |
| `__tests__/viewportStore.test.ts` | Tests: viewportStore; normalizes absent scroll handles; includes pending scroll delta in snapshot math and keying; uses fresh scroll height to clear stale non-bottom state |
| `__tests__/virtualHeights.test.ts` | Tests: virtual height estimates; uses stable content keys across resumed message objects; accounts for wrapping and preserved blank-block rhythm; uses compound user prompt width when estimating user message wrapping |
| `__tests__/virtualHistoryClamp.test.ts` | Tests: virtual history clamp bounds; does not clamp sticky live tail content; sets clamp bounds after manual scroll breaks sticky mode; does not clamp while a live tail is growing below virtual history |
| `__tests__/virtualHistoryOffsetCache.test.ts` | Tests: useVirtualHistory offset cache reuse; prunes stable-session external height caches to active history keys; includes viewport height in the external-store snapshot key; remounts enough tail rows after the scroll v… |
| `__tests__/voicePartialStore.test.ts` | Tests: handleVoiceCapture; shows live STT text until the capture settles |
| `__tests__/voiceSubmitModeRenderer.test.tsx` | Tests: voice.submit_mode live composer rendering; renders a draft transcript in the real React composer state without submitting it |
| `__tests__/wakeCommand.test.ts` | Tests: /wake slash command; /wake on calls wake.start with surface tui and reports listening; /wake on clears the session opt-out flag; /wake on prints the reason when the gateway refuses |
| `__tests__/weatherApp.test.ts` | Tests: weather reference app (async contract); uses Open-Meteo for a named location; geolocates by IP when the location is blank; a late resolution cannot resurrect a closed app |
| `__tests__/wheelAccel.test.ts` | Tests: wheelAccel — native path; first click after init returns base; gap beyond window resets mult to base; direction flip defers one event for bounce detection |
| `__tests__/widgetGrid.test.ts` | Tests: layoutWidgetGrid; falls back to a single column on narrow widths; packs spans left-to-right and wraps to the next row; clamps spans to available columns |
| `__tests__/widgetGridComponent.test.tsx` | Tests: WidgetGrid component composition; renders stateful direct children and nested grids inside cells; GridAreas component; renders a rowSpan cell alongside stacked cells at their solved rects |
| `__tests__/widgetSdk.test.ts` | Tests: widget SDK host; launch → dispatch → close lifecycle drives the overlay slot; refused launches return the usage line and leave the slot empty; apps stack each other via the typed programmatic launch |
| `app.tsx` | Exports `App` |
| `app/agentRoster.ts` | Session-local presentation only; never persisted to config. |
| `app/clarifyTranscript.ts` | Exports `ClarifyTranscriptQuestion`, `clarifyQuestionCountLabel`, `clarifySettledRows` |
| `app/connectionOperationStore.ts` | Exports `ConnectionOperationSnapshot`, `ConnectionOverlayState`, `isSettledOperation`, `isDismissedOperation`, `applyConnectionRequest`, `applyConnectionUpdate` … |
| `app/createGatewayEventHandler.ts` | Exports `usageChanged`, `mergeUsageStable`, `reapplyTheme`, `applyConfiguredTuiTheme`, `polarityBackgroundFromForeground`, `syncThemeToTerminalBackground` … |
| `app/createServerRequestHandler.ts` | Exports `ServerRequestHandlerContext`, `createServerRequestHandler` |
| `app/createSlashHandler.ts` | Exports `reportSlashCommand`, `createSlashHandler` |
| `app/delegationStore.ts` | Exports `DelegationState`, `getDelegationState`, `patchDelegationState`, `resetDelegationState`, `toggleOverlaySection`, `getOverlaySectionOpen` … |
| `app/gatewayBrowserLinks.ts` | Links the headless gateway needs the user to open in a browser: it cannot open one or print where the user sees it, so the TUI shows the link (clickable/copyable) and opens it itself. |
| `app/gatewayCanonicalEvents.ts` | Canonical-gateway event handling extracted from createGatewayEventHandler: the owner-epoch lifecycle fence and the generation-bound shared controls (`gateway/session_pending_controls.py`). |
| `app/gatewayContext.tsx` | Exports `GatewayProvider`, `useGateway` |
| `app/gatewayRecovery.ts` | Crash-recovery budget for the gateway exit handler. A gateway that crash-loops on startup must not let the TUI spawn-storm, so respawn+resume attempts are capped to GATEWAY_RECOVERY_LIMIT within a sliding |
| `app/gatewayStartTimeout.ts` | `gateway.start_timeout`: the backend has not attached yet, or its bootstrap gave up for good. |
| `app/goalStatus.ts` | The session's standing /goal, as `session.control.read` / `session.control.update` report it. Session-local presentation only; `/goal` itself stays the control surface. |
| `app/inputSelectionStore.ts` | Exports `InputSelection`, `setInputSelection`, `getInputSelection` |
| `app/interfaces.ts` | Exports `StateSetter`, `StatusBarMode`, `BatteryCategory`, `BatteryInfo`, `BusyInputMode`, `NoticeLevel` … |
| `app/liveSessions.ts` | The live-session roster the status bar's title and count read: on the shared owner its own `session.list` (live scope); the sidecar's `session.active_list` never holds those sessions. |
| `app/loopStatus.ts` | The session's standing /loop, as `session.control.read` / `session.control.update` report it. The gateway publishes on set/pause/resume/stop, when a wakeup fires and when it completes, so the snapshot's `next_due_at` is… |
| `app/overlayStore.ts` | Exports `capturePromptResponseGuard`, `hasFloatingPanel`, `SENSITIVE_PROMPTS`, `hasSensitivePrompt`, `PROMPT_KEYS`, `hasPromptOpen` … |
| `app/pendingBubbles.ts` | Exports `PendingRow`, `markBubbleShown`, `resetBubbleLedger`, `newlyStartedRows`, `isServerQueued` |
| `app/petFlashStore.ts` | Exports `flashPet`, `flashGoodVibes` |
| `app/processRoster.ts` | Background `terminal(background=true)` processes owned by this session, as the gateway's `process.list` reports them. Session-local presentation only. |
| `app/scroll.ts` | Exports `SelectionSnap`, `ScrollWithSelectionOptions`, `scrollWithSelectionBy` |
| `app/serverRequestStore.ts` | Live server→client requests (clarify, approval, sudo, …) keyed by request id. Overlay state keeps only the id; answering resolves the stored request so a re-delivered (`open_requests`) request with the same id reuses the |
| `app/sessionResumeView.test.ts` | Tests: scheduleResumeScrollToBottom; re-snaps while sticky and stops when the user scrolls away; cancels pending resume snaps; keeps the immediate resume snap even before sticky state settles |
| `app/sessionResumeView.ts` | Exports `refreshSessionView`, `scheduleResumeScrollToBottom` |
| `app/setupHandoff.ts` | Exports `RunExternalSetupOptions`, `runExternalSetup` |
| `app/slash/canonicalSessionCommands.ts` | Ink slash commands whose legacy RPCs (`session.title`, `session.undo`, `session.usage`, the `/tools` slash worker) the canonical gateway does not serve, mapped onto what it does serve: `session.mutate` rename / rewind (… |
| `app/slash/canonicalSessionControls.ts` | Exports `CanonicalOperation`, `MutationSnapshot`, `retireCanonicalControls`, `mutateCanonical`, `mutateCanonicalSession`, `openModelConfirmation` … |
| `app/slash/commands/core.ts` | Exports `coreCommands` |
| `app/slash/commands/debug.ts` | Importing the apps barrel registers the reference apps before launch. |
| `app/slash/commands/ops.ts` | Exports `opsCommands` |
| `app/slash/commands/session.ts` | Exports `sessionCommands` |
| `app/slash/commands/setup.ts` | Exports `setupCommands` |
| `app/slash/commands/subscription.ts` | Exports `subscriptionCommands` |
| `app/slash/commands/topup.ts` | Exports `topupCommands` |
| `app/slash/commands/wake.ts` | Exports `wakeCommands` |
| `app/slash/fuzzyScore.test.ts` | Tests: normalizeSlashSearchQuery; trims, strips leading slashes, and lowercases; tokenizeSearchText; returns the full lowercased value plus alphanumeric word tokens |
| `app/slash/fuzzyScore.ts` | Description-aware fuzzy scoring for the slash-command menu. Ported from superagent-ai/grok-cli `src/ui/slash-menu.ts`: candidates are scored in tiers — exact match on id/label/alias (0), prefix (1), substring (2) — and… |
| `app/slash/registry.ts` | Exports `SLASH_COMMANDS`, `findSlashCommand` |
| `app/slash/types.ts` | Exports `SlashRunCtx`, `SlashCommand` |
| `app/slash/usagePanel.ts` | Main's `/usage` session-totals panel (model, input / output / total tokens, API calls, the context line, compressions), from main's `Usage` shape: the sidecar's `session.usage` RPC, or a canonical owner's `session.stats… |
| `app/slashCatalog.ts` | `commands.catalog` bound to `sid` when there is one: project-local skills follow the session's repo, so the catalog is reloaded whenever the live session changes. A reply for a session that is no longer the live one is… |
| `app/spawnHistoryStore.ts` | Exports `SpawnSnapshot`, `SpawnDiffPair`, `getSpawnHistory`, `getSpawnDiff`, `clearSpawnHistory`, `clearDiffPair` … |
| `app/startupLatency.ts` | Module-level so a gateway reconnect/respawn (a fresh gateway.ready, or a remounted handler) never re-reports: the metric is launch -> first ready, once per TUI process. |
| `app/submissionCore.ts` | Exports `isSessionBusyError`, `SubmitPromptDeps`, `markSubmitting`, `markNextSubmitVoice`, `readmitAsPrompt`, `submitPrompt` |
| `app/submissionDestination.ts` | Exports `SubmissionDestination`, `captureDestination`, `isCurrentDestination` |
| `app/turnController.ts` | Exports `SealedInterrupt`, `lateInterruptedReply`, `InterruptDeps`, `turnController` |
| `app/turnStore.ts` | Exports `getTurnState`, `useTurnSelector`, `patchTurnState`, `toggleTodoCollapsed`, `archiveDoneTodos`, `archiveTodosAtTurnEnd` … |
| `app/uiStore.ts` | Exports `getUiState`, `sessionCwd`, `patchUiState`, `resetUiState` |
| `app/useBatteryPoll.ts` | Exports `toBatteryInfo`, `useBatteryPoll` |
| `app/useComposerState.ts` | Exports `looksLikeDroppedPath`, `useComposerState` |
| `app/useConfigSync.ts` | Exports `normalizeStatusBar`, `normalizeStatusBarFields`, `normalizeBusyInputMode`, `normalizeIndicatorStyle`, `normalizeMouseTracking`, `McpRevState` … |
| `app/useInputHandlers.ts` | Exports `shouldAllowIdleHotkeyExit`, `composerHasDraft`, `handleInputSelectionClipboard`, `handleIdleHotkeyExit`, `CtrlCComposerAction`, `resolveCtrlCComposerAction` … |
| `app/useLongRunToolCharms.ts` | Exports `useLongRunToolCharms` |
| `app/useMainApp.ts` | Exports `PromptLiveSessionOptions`, `startPromptLiveSession`, `useMainApp` |
| `app/usePet.ts` | Exports `PetState`, `derivePetState`, `PetRender`, `usePet` |
| `app/useSessionLifecycle.ts` | Exports `writeActiveSessionFile`, `liveSessionInflightMessages`, `hydrateLiveSessionInflight`, `signalFreshSessionBoundary`, `UseSessionLifecycleOptions`, `useSessionLifecycle` |
| `app/useSubmission.ts` | Exports `expandPasteTokens`, `queueItemFromSlash`, `prepareSubmission`, `prepareSlashSubmission`, `shouldInterpolateSubmission`, `BusyControl` … |
| `app/userMessages.ts` | User-facing wording for gateway/transport failures in the TUI. Pure functions so the copy — and the "what happened / what to do" shape — is unit-testable without rendering. The English copy lives in i18n/en/userMessages… |
| `app/voicePartialStore.ts` | Live STT text so far while the user is still speaking (`voice.partial`, stt.streaming). The composer shows it as its placeholder until the capture settles. |
| `app/wakeState.ts` | Session-scoped memory of an explicit `/wake off`. The gateway auto-arms the "Hey Hermes" listener on every `gateway.ready` (see createGatewayEventHandler.ts). When the user explicitly disables the |
| `banner.ts` | Exports `parseRichMarkup`, `LOGO_WIDTH`, `CADUCEUS_WIDTH`, `logo`, `caduceus`, `artWidth` |
| `canonicalGateway.ts` | Exports `SharedControl`, `sharedControlParams`, `CreationContract`, `canonicalRequest`, `canonicalResult`, `pendingSubmissions` … |
| `components/accordion.tsx` | THE expand/collapse primitive — the session panel's tool/skill sections and widget-app accordions are the same component. Click the header to toggle (mouse works even in ambient widgets, which receive no keys); modal ap… |
| `components/activeSessionSwitcher.tsx` | Exports `sessionStatusLabel`, `fixedSessionColumnStyle`, `activeSessionCountLabel`, `sessionsCountLabel`, `SessionRowKind`, `sessionRowKindAt` … |
| `components/agentControls.tsx` | Exports `rosterViewport`, `sendAgentSteer`, `AgentSteerForm`, `AgentLiveTail` |
| `components/agentsOverlay.tsx` | Exports `sortLabel`, `filterLabel`, `AgentsOverlay`, `closeAgentsOverlay`, `openAgentsOverlay` |
| `components/agentsPanel.tsx` | Exports `ProcessBlock`, `EMPTY_PROCESSES`, `buildProcessBlock`, `splitDockBudget`, `processSummary`, `ProcessRowLine` … |
| `components/appChrome.tsx` | Exports `VERB_PAD_LEN`, `padVerb`, `MAX_DURATION_WIDTH`, `busyIndicatorWidth`, `displayStatus`, `statusRuleWidths` … |
| `components/appLayout.tsx` | Importing the apps barrel registers the reference widget apps at startup. |
| `components/appOverlays.tsx` | Exports `PromptZone`, `FloatingOverlays` |
| `components/billingOverlay.tsx` | Exports `BillingOverlay` |
| `components/branding.tsx` | Exports `ArtLines`, `Banner`, `SessionPanel`, `Panel` |
| `components/connectionSetupOverlay.tsx` | Exports `ConnectionSetupOverlay` |
| `components/connectorsOverlay.tsx` | Exports `ConnectorsOverlay` |
| `components/fpsOverlay.tsx` | FPS counter overlay (HERMES_TUI_FPS=1). Zero-cost when disabled. |
| `components/goalBar.tsx` | One `⊙ goal · 3/20 turns · <title>` row above the live-work dock while a /goal is standing. |
| `components/gridStreamsDemo.tsx` | The streams demo tiles six independently-ticking panels through `layoutGridAreas`: one panel owns a promoted 2x2 slot, the rest auto-place densely around it. Promoting a different panel reorders/respans the widget |
| `components/gridTestOverlay.tsx` | Exports `GridTestOverlay` |
| `components/helpHint.tsx` | Exports `HelpHint` |
| `components/journey.tsx` | Exports `Journey` |
| `components/loaders.tsx` | Animated ASCII loaders — THE loading-state primitives (session panel skeleton, widget apps via the SDK). A highlight band sweeps across block runs; rows offset their phase for a diagonal shimmer. One interval per compos… |
| `components/loopBar.tsx` | One `↻ loop · every 45m · 2 runs · next in 44m · <prompt>` row above the live-work dock while a /loop is standing; the countdown ticks down on its own. |
| `components/markdown.tsx` | `\boxed{X}` regions in `texToUnicode` output are marked with the non-printable U+0001 / U+0002 sentinels. Split on them and render the boxed segment with `inverse + bold` so it reads as a highlighter-pen |
| `components/maskedPrompt.tsx` | Exports `MaskedPrompt`, `SudoPrompt`, `SecretPrompt`, `VaultUnlockPrompt`, `VaultSaveLoginPrompt`, `VaultCodePrompt` |
| `components/messageLine.tsx` | Collapse threshold for long system messages (system prompt etc.) |
| `components/modelPicker.tsx` | Exports `reasoningPickerRows`, `pickerOffersReasoning`, `modelPickerCommand`, `providerIndexAfterClearingFilter`, `ModelPicker` |
| `components/overlay.tsx` | Exports `OverlayZone`, `Overlay`, `Dialog` |
| `components/overlayControls.tsx` | Exports `useOverlayKeys`, `OverlayHint`, `windowOffset`, `windowItems` |
| `components/overlayPrimitives.tsx` | Overlay width clamp: prefer `preferred`, honor the caller's `maxWidth` ABSOLUTELY (a grid cell knows its budget — overflowing it clips at the terminal edge), and keep a usability floor only when the cap allows it. |
| `components/overlayScrollbar.tsx` | Mouse-draggable scrollbar bound to a `ScrollBox` ref. Re-renders off the parent `tick` so accordions / async content can resize the thumb without a scroll event. Shared by every full-screen overlay that scrolls a pane. |
| `components/petPicker.tsx` | Exports `PetPicker` |
| `components/petSprite.tsx` | A cell is [tr,tg,tb,ta, br,bg,bb,ba] — the top + bottom pixel of one half-block, as produced by the `pet.cells` gateway RPC. |
| `components/pluginsHub.tsx` | Exports `PluginsHub` |
| `components/prompts.tsx` | Exports `approvalOptions`, `approvalAction`, `ApprovalPrompt`, `ClarifyPrompt`, `ConfirmPrompt` |
| `components/queuedMessages.tsx` | Exports `QUEUE_WINDOW`, `getQueueWindow`, `QueuedMessages` |
| `components/skillsHub.tsx` | Exports `SkillsHub` |
| `components/streamingAssistant.tsx` | Exports `StreamingAssistant`, `LiveTodoPanel` |
| `components/streamingMarkdown.tsx` | StreamingMd — incremental markdown renderer for in-flight assistant text. Rendering <Md text={full}/> per delta re-tokenizes the whole message every time (O(total) × deltas). The prior stable-prefix split fixed the per-… |
| `components/subscriptionOverlay.tsx` | Exports `SubscriptionOverlay` |
| `components/textInput.tsx` | Exports `colorizeHint`, `colorizeEcho`, `hintCursorCell`, `TextInsertResult`, `applyPrintableInsert`, `shouldRouteMultiCharInputAsPaste` … |
| `components/themed.tsx` | Exports `Fg`, `ThemeColor`, `FgProps` |
| `components/thinking.tsx` | Exports `Spinner`, `Thinking`, `ToolTrail` |
| `components/todoPanel.tsx` | Exports `TodoPanel` |
| `components/widgetGrid.tsx` | Exports `WidgetGridRenderContext`, `WidgetGridWidget`, `WidgetGrid`, `GridAreaWidget`, `GridAreas` |
| `config/env.ts` | Exports `TERMUX_TUI_MODE`, `STARTUP_RESUME_ID`, `STARTUP_QUERY`, `STARTUP_IMAGE`, `STARTUP_WORKSPACE_CWD`, `NATIVE_MODE` … |
| `config/limits.ts` | Exports `LARGE_PASTE`, `LIVE_RENDER_MAX_CHARS`, `LIVE_RENDER_MAX_LINES`, `VERBOSE_TRAIL_MAX_CHARS`, `VERBOSE_TRAIL_MAX_LINES`, `LONG_MSG` … |
| `config/timing.ts` | Exports `STREAM_BATCH_MS`, `STREAM_IDLE_BATCH_MS`, `STREAM_SCROLL_BATCH_MS`, `STREAM_TYPING_BATCH_MS`, `TYPING_IDLE_MS`, `REASONING_PULSE_MS` … |
| `content/charms.ts` | Exports `LONG_RUN_CHARMS` |
| `content/faces.ts` | Kaomoji spinner frames, in catalog order, resolved against the active language at call time. |
| `content/fortunes.ts` | Everyday fortunes, in catalog order, resolved against the active language at call time. |
| `content/hotkeys.ts` | Exports `hotkeys` |
| `content/placeholders.ts` | Exports `placeholders`, `placeholder` |
| `content/setup.ts` | Exports `setupRequiredTitle`, `buildSetupRequiredSections` |
| `content/verbs.ts` | Tool name → progress verb, resolved against the active language at call time. |
| `domain/attachments.ts` | Composer tokens are the ONE way deferred content shows up in the input line: a collapsed paste and an attached image both render as `[[ … ]]` sitting in the text the user is editing. They are ordinary characters — arrow… |
| `domain/blockLayout.ts` | Visual group a transcript block belongs to. Blocks in the same group render flush; a single blank line opens at each group boundary. So a run of tool trails (or model paragraphs) reads as one section and the eye only ca… |
| `domain/composerHighlights.ts` | Reference spans in composer text: a `/skill` invoked or named in prose, an ` |
| `domain/connectorAccounts.ts` | The account-name format the gateway enforces (`connector_alias`). |
| `domain/details.ts` | Exports `SECTION_NAMES`, `parseDetailsMode`, `isSectionName`, `resolveDetailsMode`, `resolveSections`, `sectionMode` … |
| `domain/messages.ts` | Exports `introMsg`, `userDisplay`, `toTranscriptMessages`, `fmtDuration` |
| `domain/paths.ts` | Exports `shortCwd`, `fmtCwdBranch`, `shortProject`, `fmtProjectCwdBranch`, `composeTabTitle` |
| `domain/providers.ts` | Exports `providerDisplayNames` |
| `domain/roles.ts` | Exports `ROLE` |
| `domain/slash.ts` | Appended by TUI pickers; converted to the backend's `--session` flag before `config.set`. |
| `domain/usage.ts` | Exports `ZERO` |
| `domain/viewport.ts` | Exports `stickyPromptFromViewport` |
| `entry.tsx` | TypeScript React component: `entry` |
| `gatewayClient.ts` | Exports `WS_HEARTBEAT_INTERVAL_MS`, `WS_HEARTBEAT_DEAD_MS`, `RECONNECT_BASE_MS`, `RECONNECT_MAX_MS`, `OWNER_RECOVERY_LIMIT`, `OWNER_RECOVERY_WINDOW_MS` … |
| `gatewayTypes.ts` | Exports `GatewaySkin`, `CanonicalSharedPrompt`, `CanonicalApprovalPrompt`, `CanonicalClarifyPrompt`, `CanonicalGatewayEventMap`, `AnyGatewayEventMap` … |
| `hooks/useCompletion.ts` | Client-side widget apps live in the TUI's registry, not the gateway — so `/` completions merge their title/metadata here. Registry-driven: a new app surfaces automatically, no hardcoded lists on either side. Matching is… |
| `hooks/useGitBranch.ts` | Exports `useGitBranch` |
| `hooks/useInputHistory.ts` | Exports `useInputHistory` |
| `hooks/useQueue.ts` | Exports `QueueItem`, `queueItem`, `prependQueueItem`, `takeQueueItem`, `removeAtInPlace`, `useQueue` |
| `hooks/useSessionDelete.ts` | The picker's history delete: one request at a time, and a refused delete hands back the viewer attachment its revision read made unless `keepView` says this view already held the session. Settles through `onDeleted` or… |
| `hooks/useVirtualHistory.ts` | Exports `pruneVirtualHeightCache`, `virtualHistorySnapshotKey`, `shouldSetVirtualClamp`, `ensureVirtualItemHeight`, `useVirtualHistory` |
| `i18n/en.ts` | Bundled English catalog for the TUI — the only bundled TUI locale. Every other language arrives as a pack over `i18n.catalog {surface: 'tui'}` and is merged over this object at runtime (see runtime.ts). |
| `i18n/en/app.ts` | app/ layer (excluding slash): notices, turn-controller activity lines, gateway event copy, server-request prompts, session lifecycle, queue, pet. Owned namespaces: `notice`, `turn`, `session`, `queue`, `event`, `request… |
| `i18n/en/billing.ts` | Billing overlay (`/topup`, credit purchases, card step-up). Owned namespace: `billing`. Leaves are strings or `(...args) => string`; packs supply `{0}`, `{1}` positional placeholders, so keep argument order stable and c… |
| `i18n/en/canonical.ts` | Shared-gateway (canonical authority) client text: durable submission/queue receipts, image staging, launch-contract refusals and the slash commands mapped onto `session.mutate`. Owned namespace: `canonical`. Function le… |
| `i18n/en/chatBits.ts` | Chat bits: the banner/session panel (branding.tsx), the reasoning + tool trail tree (thinking.tsx), transcript rows (messageLine.tsx), the todo panel, the queued-messages strip, and the human-facing bootstrap messages |
| `i18n/en/chrome.ts` | App shell: status line, composer, keybind hints, banner, dock, transcript rows. Owned namespaces: `status`, `composer`, `hints`, `help`, `banner`, `transcript`, `dock`. (`content` lives in ./content.ts, chat/transcript… |
| `i18n/en/connection.ts` | Connection setup overlay and the learning-journey (starmap) overlay. Owned namespaces: `connection`, `journey`. Leaves are strings or `(...args) => string`; packs supply `{0}`, `{1}` positional placeholders, so keep |
| `i18n/en/connectors.ts` | The /connectors overlay: the user's hosted connector accounts. Owned namespace: `connectors`. Leaves are strings or `(...args) => string`; packs use positional `{0}`, `{1}` placeholders, so keep argument order stable. |
| `i18n/en/content.ts` | Content tables: tool verbs, fortunes, kaomoji faces, the setup-required panel. Owned namespace: `content`. Lists live as numbered leaves (`fortune01`…) because packs are flat |
| `i18n/en/gatewayMsg.ts` | Lane t2 — app/createGatewayEventHandler.ts: notices/activity lines rendered from gateway events. Owned namespace: `gatewayMsg`. Function leaves take positional args; packs use `{0}`, `{1}` (argument order documented per… |
| `i18n/en/hubs.ts` | Hubs: the agents overlay (spawn tree / replay diff), the live agents dock, per-agent steer/tail controls, the Skills Hub and the Plugins Hub. Owned namespace: `hubs`. |
| `i18n/en/lib.ts` | lib/, domain/, content/, hooks/, sdk/ and root files: clipboard, editor, external links, usage, attachments, widgets. Owned namespaces: `clipboard`, `editor`, `link`, `usage`, `attachment`, `widget`, `common` (`content`… |
| `i18n/en/libText.ts` | Lane t2 — gatewayClient displayed reasons, lib/*, domain/*, hooks/* user-facing text. Owned namespace: `libText`. Function leaves take positional args; packs use `{0}`, `{1}` (argument order documented per leaf). |
| `i18n/en/overlays.ts` | Overlays, pickers and dialogs: prompts, model/pet pickers, hubs, agents panel, billing/subscription, connection setup. Owned namespaces: `overlay`, `prompt`, `picker`, `hub`, `agents`, `billing`, `connection`, `journey`. |
| `i18n/en/pickers.ts` | Picker overlays: the /model provider→model→effort picker, the Ctrl+X live session switcher (orchestrator), and the /pet gallery picker. Owned namespace: `pickers`. |
| `i18n/en/secure.ts` | Credential prompts: the sudo password, secret (env var) and password-manager unlock prompts hosted in MaskedPrompt. Owned namespace: `secure`. Only labels/hints live here — the typed values never touch the catalog. |
| `i18n/en/session.ts` | Lane t2 — app/ session flow: useMainApp, useSessionLifecycle, useInputHandlers, turnController, createServerRequestHandler, setupHandoff. Owned namespace: `session`. Function leaves take positional args; packs use `{0}`… |
| `i18n/en/slash.ts` | Slash-command layer: local command replies, usage hints, RPC error copy. Owned namespaces: `slash`, `rpc`. Slash-command NAMES stay identifiers — only descriptions/replies live here. |
| `i18n/en/slashCmd.ts` | Slash-command replies (app/slash/commands/*). Owned namespace: `slashCmd`. Composed from per-command-file parts under ./slashCmd/ so each part is `slashCmd.<commandFile>.<leaf>`. Command NAMES, aliases and argument synt… |
| `i18n/en/slashCmd/core.ts` | slashCmd.core / slashCmd.debug / slashCmd.setup — replies and usage hints of app/slash/commands/{core,debug,setup}.ts. Command NAMES/aliases/arg syntax stay literal. Grouped one level deeper by command so `slashCmd.core… |
| `i18n/en/slashCmd/ops.ts` | slashCmd.ops / slashCmd.wake — replies and usage hints of app/slash/commands/{ops,wake}.ts. Command NAMES/aliases/arg syntax inside usage strings stay literal. |
| `i18n/en/slashCmd/session.ts` | slashCmd.session / slashCmd.topup / slashCmd.subscription — replies and usage hints of app/slash/commands/{session,topup,subscription}.ts. Command NAMES/aliases/arg syntax stay literal; config VALUES echoed back (auto/l… |
| `i18n/en/subscription.ts` | Subscription overlay (`/subscription`: plans, scheduled changes, remote spending). Owned namespace: `subscription`. Leaves are strings or `(...args) => string`; packs supply `{0}`, `{1}` positional placeholders, so keep… |
| `i18n/en/userMessages.ts` | app/userMessages.ts copy: gateway/transport failure wording, turn-failure titles + next steps, withdrawn-prompt notices, empty states. Owned namespace: `userMessages`. |
| `i18n/index.ts` | TypeScript source: `index` |
| `i18n/keys.ts` | Flatten a catalog into its sorted dotted leaf keys. Shared by the `_keys.tui.json` emitter and its test. |
| `i18n/loader.ts` | Fetch the TUI language from the backend. The locale id comes from `display.language` (already read by useConfigSync's `config.get full`); the strings come from `i18n.catalog {lang, surface: 'tui'}`. A backend that |
| `i18n/merge.ts` | Deep-merge helpers for catalogs. Same semantics as apps/shared/src/i18n.ts `mergeTranslations`, kept local because that module touches `document` (applyDocumentLocale) and the TUI compiles without the DOM lib. |
| `i18n/runtime.ts` | Locale + merged catalog store for the TUI, mirroring apps/desktop/src/i18n/runtime.ts. Resolution for `t(key)`: active catalog (en merged with the RPC-delivered pack for the active language) → bundled en → the bare key.… |
| `i18n/types.ts` | TUI i18n type contract. `Translations` is derived from the bundled English catalog: adding a string to en.ts is the whole schema change. |
| `i18n/useT.ts` | The active merged catalog, re-rendering the caller when the language changes. |
| `lib/agentRows.ts` | Pure merge + layout logic for the docked agents panel. Kept ink-free so it is unit testable on its own; agentsPanel.tsx owns only the presentation. One merged panel row — either a live in-turn subagent or a background |
| `lib/billingDialog.ts` | Exports `BillingDialogCopy`, `billingDialogCopy`, `UsageLimitDialog`, `usageLimitDialog` |
| `lib/charts.ts` | Chart primitives — pure string builders (no React), THE charting layer for widget apps and demos alike. Everything returns plain strings the caller colors with theme tones; everything auto-scales to the series' min/max. |
| `lib/circularBuffer.ts` | Exports `CircularBuffer` |
| `lib/clipboard.ts` | Exports `isUsableClipboardText`, `readClipboardText`, `writeClipboardText` |
| `lib/color.test.ts` | Tests: color() chain; composes the ladder operations |
| `lib/color.ts` | TUI-only color derivations. The sRGB primitives (parse, mix, WCAG measure, `ensureContrast`) live in ` |
| `lib/editor.test.ts` | Tests: resolveEditor; honors $VISUAL above all else; falls back to $EDITOR when $VISUAL is unset; shell-tokenizes editors with arguments |
| `lib/editor.ts` | Editor fallback chain when neither $VISUAL nor $EDITOR is set. Mirrors prompt_toolkit's `Buffer.open_in_editor()` picker so the classic CLI and the TUI launch the same editor on a given box. |
| `lib/emoji.ts` | Exports `ensureEmojiPresentation` |
| `lib/externalCli.ts` | Exports `LaunchResult`, `launchHermesCommand` |
| `lib/externalLink.ts` | Exports `normalizeExternalUrl`, `hostPathLabel`, `urlSlugTitleLabel`, `isTitleFetchable`, `fetchLinkTitle`, `useLinkTitle` … |
| `lib/forceTruecolor.ts` | Targeted 24-bit truecolor override before chalk / supports-color imports. macOS Terminal.app before Tahoe 26 does not support RGB SGR, so do not infer truecolor from TERM_PROGRAM=Apple_Terminal. Users can still opt in e… |
| `lib/fpsStore.ts` | Tiny FPS tracker fed by ink's onFrame callback. Each entry is an Ink frame (React commit + drain-only frames) — the right notion for user-perceived motion. |
| `lib/gracefulExit.ts` | Exports `GracefulSignal`, `shouldExitForSignal`, `setupGracefulExit` |
| `lib/history.ts` | Exports `load`, `append` |
| `lib/imageAttachments.ts` | Exports `ImageAttachment`, `StagedImage`, `stageClipboardImage`, `stageImagePath` |
| `lib/inputMetrics.ts` | Exports `COMPOSER_PROMPT_GAP_WIDTH`, `cursorLayout`, `offsetFromPosition`, `inputVisualHeight`, `composerPromptWidth`, `transcriptGutterWidth` … |
| `lib/liveProgress.test.ts` | Tests: isTodoDone; only treats non-empty all-completed/cancelled lists as done; tool shelf helpers; recognizes contextual thinking shelves as holders |
| `lib/liveProgress.ts` | Exports `countPendingTodos`, `isTodoDone`, `isToolShelfMessage`, `canHoldToolShelf`, `mergeToolShelfInto`, `appendToolShelfMessage` |
| `lib/mathUnicode.ts` | Best-effort LaTeX → Unicode for inline / display math captured by the markdown renderer. The terminal can't typeset LaTeX, but Unicode covers most of what models actually emit: Greek letters, blackboard / fraktur / |
| `lib/memory.test.ts` | Tests: performHeapDump auto opt-in gate (#21767); writes diagnostics only for auto-high without HERMES_AUTO_HEAPDUMP; writes both diagnostics and snapshot for auto-high when HERMES_AUTO_HEAPDUMP=1; treats other values (… |
| `lib/memory.ts` | Exports `MemoryTrigger`, `MemoryDiagnostics`, `HeapDumpResult`, `captureMemoryDiagnostics`, `performHeapDump`, `formatBytes` |
| `lib/memoryMonitor.ts` | Exports `MemoryLevel`, `MemorySnapshot`, `MemoryMonitorOptions`, `startMemoryMonitor` |
| `lib/messages.ts` | Stamp live rows AT APPEND (wall clock, Unix seconds) rather than later: a message's authoring time is when it entered the transcript, not when it happened to be persisted or re-rendered (#82840-class rule). Rehydrated |
| `lib/openExternalUrl.test.ts` | Tests: parseSafeUrl; accepts http and https URLs; rejects file: URLs (would let a hostile model trigger arbitrary local handlers); rejects javascript:, data:, and vbscript: URLs |
| `lib/openExternalUrl.ts` | Opens an external URL in the user's default browser/handler. Wired into the Ink instance via `onHyperlinkClick` in entry.tsx, so any mouse click on a `<Link>` cell (or a row containing a plain-text URL the renderer dete… |
| `lib/osc52.ts` | Exports `OSC52_CLIPBOARD_QUERY`, `buildOsc52ClipboardQuery`, `parseOsc52ClipboardData`, `readOsc52Clipboard`, `writeOsc52Clipboard` |
| `lib/parentLog.ts` | Mirror the Python gateway's panic log (tui_gateway/server.py::_CRASH_LOG) from the Node parent so lifecycle breadcrumbs interleave, by timestamp, with the child's `=== SIGTERM received ===` / `=== gateway exit ===` entr… |
| `lib/pendingInputs.ts` | Exports `pendingDestinationKey`, `pendingInputOwner`, `migratePendingInputs`, `savePendingInput`, `removePendingInput`, `loadPendingInputs` |
| `lib/perfPane.tsx` | Perf instrumentation for the full render pipeline. PerfPane (React.Profiler) → per-pane commit times logFrameEvent (ink.onFrame) → yoga / renderer / diff / optimize / write |
| `lib/petPolling.ts` | Exports `PetMetaResult`, `createPetSingleFlight`, `requestPetUpdate` |
| `lib/platform.ts` | Platform-aware keybinding helpers. On macOS the "action" modifier is Cmd. Modern terminals that support kitty keyboard protocol report Cmd as `key.super`; legacy terminals often surface it as `key.meta`. Some macOS term… |
| `lib/precisionWheel.ts` | Exports `PrecisionWheelState`, `PrecisionWheelStep`, `initPrecisionWheel`, `computePrecisionWheelStep` |
| `lib/processGlyph.ts` | Status→glyph lookup for background-process rows; the docked panel and the /agents overlay render identical glyphs so the two never drift apart. |
| `lib/prompt.ts` | Exports `composerPromptText` |
| `lib/pythonHelpers.ts` | Exports `pythonHelperPath` |
| `lib/reasoning.ts` | Exports `SplitReasoning`, `splitReasoning`, `hasReasoningTag` |
| `lib/resizeCoalescer.test.ts` | Tests: createResizeCoalescer; reflows immediately on the first event (leading edge); collapses a rapid burst into one leading + one trailing reflow; reflows immediately again once the interval has elapsed |
| `lib/resizeCoalescer.ts` | Exports `ResizeCoalescer`, `createResizeCoalescer` |
| `lib/rpc.ts` | Exports `RpcResult`, `asRpcResult`, `rpcErrorMessage` |
| `lib/sessionExport.ts` | Exports `SessionExportPayload`, `defaultSaveName`, `writeSessionExport` |
| `lib/sessionLabel.test.ts` | Tests: sessionLabel; shows a canonical durable id as main; leaves an 8-character label as it is; shows a resumed stored id as a stable 8-character label |
| `lib/sessionLabel.ts` | The canonical owner names a session by its durable id: `local-` + 64 hex for sessions it created, the stored `YYYYMMDD_HHMMSS_xxxxxx` id for history adopted from main. Main's banner always showed an 8-hex runtime label;… |
| `lib/starmapPalette.ts` | Star Map palette — ported from apps/desktop/src/app/starmap/color.ts so the TUI overlay derives the same memory ink (complement of the theme primary) and the same age fade (rgba(ink, alpha) over the background) as the d… |
| `lib/subagentGlyph.ts` | Shared status→glyph lookup for the subagent surfaces. Extracted so the docked agents panel and the full /agents overlay render identical glyphs and colours — a single source of truth prevents visual drift between them. |
| `lib/subagentTree.ts` | Exports `buildSubagentTree`, `aggregate`, `widthByDepth`, `treeTotals`, `flattenTree`, `descendantIds` … |
| `lib/syntax.ts` | Exports `Token`, `isHighlightable`, `highlightLine` |
| `lib/terminalModes.ts` | Exports `TERMINAL_MODE_RESET`, `clearNativeTuiFrame`, `isPaintableHex`, `setTerminalForeground`, `setTerminalBackground`, `resetTerminalModes` |
| `lib/terminalParity.ts` | Exports `MacTerminalHint`, `MacTerminalContext`, `detectMacTerminalContext`, `terminalParityHints` |
| `lib/terminalSetup.ts` | Exports `SupportedTerminal`, `FileOps`, `TerminalSetupResult`, `detectVSCodeLikeTerminal`, `stripJsonComments`, `isRemoteShellSession` … |
| `lib/termux.ts` | Exports `isTermuxEnv`, `isTermuxTuiMode` |
| `lib/text.test.ts` | Tests: stripTrailingPasteNewlines; removes trailing newline runs from pasted text; preserves interior newlines; preserves newline-only pastes |
| `lib/text.ts` | Exports `compactPreview`, `estimateTokensRough`, `edgePreview`, `pasteTokenLabel`, `cleanThinkingText`, `thinkingPreview` … |
| `lib/themeBoot.ts` | Flash-free theme boot — the TUI port of the desktop app's `hermes-boot-background` / `hermes-boot-color-scheme` localStorage keys. Theme resolution is asynchronous by nature (gateway skin arrives after connect; the OSC-… |
| `lib/todo.test.ts` | Tests: todoTree; orders parents before children with depths; degrades dangling and self parents to roots; keeps cycle members instead of dropping them |
| `lib/todo.ts` | Exports `TodoTone`, `todoGlyph`, `todoTone`, `todoTree` |
| `lib/usageGauge.ts` | Split a `/usage` line so `[\|\|\|\| ]` can be colored like the model-picker gauges. |
| `lib/usageLimit.test.ts` | Tests: blockingGauge / planBlocks (the one rule, agent/plan_limits.py twin); a full all-scope gauge blocks every paid model; a full top-tier gauge blocks only top-tier models; free models are never used up (gateway word… |
| `lib/viewportStore.ts` | Exports `ViewportSnapshot`, `ScrollbarSnapshot`, `getViewportSnapshot`, `viewportSnapshotKey`, `getScrollbarSnapshot`, `scrollbarSnapshotKey` … |
| `lib/virtualHeights.ts` | Exports `messageHeightKey`, `wrappedLines`, `estimatedMsgHeight` |
| `lib/wheelAccel.ts` | Wheel-scroll acceleration state machine. One event = 1 row feels sluggish on trackpads (200+ ev/s) and sustained mouse-wheel; one event = 6 rows teleports and ruins precision. |
| `lib/widgetGrid.ts` | Exports `WidgetGridItem`, `WidgetGridCell`, `WidgetGridLayout`, `WidgetGridLayoutOptions`, `widgetGridSpanWidth`, `layoutWidgetGrid` … |
| `localGatewayBootstrap.ts` | Local gateway bootstrap for the Ink TUI: run ui-tui's `gateway_bootstrap.py` on the install's interpreter and parse its grant (or its named terminal failure). Kept out of the transport class; `GatewayClient` takes it as… |
| `protocol/interpolation.ts` | Exports `INTERPOLATION_RE`, `hasInterpolation` |
| `protocol/paste.ts` | Exports `PASTE_SNIPPET_RE` |
| `sdk/apps/dialogTest.tsx` | Exports `DialogTestState`, `dialogTestApp` |
| `sdk/apps/gridTest.tsx` | Exports `gridTestApp` |
| `sdk/apps/gridTestState.ts` | State for the /grid-test reference app. Lives apart from the app definition so the render components can import the type without a cycle. |
| `sdk/apps/index.ts` | Reference apps. Importing this module registers them (defineWidgetApp runs at module load) — appLayout imports it once at startup. User widgets from $HERMES_HOME/tui-widgets ride the same import (async, non-fatal). |
| `sdk/apps/ticker.tsx` | Ticker — the animated ambient reference app: a fake 1-pip chart that random-walks a price and draws a live block sparkline, streams-demo style (the component owns its animation; app state is just the symbol). |
| `sdk/apps/weather.tsx` | Weather — the data-backed reference app. Demonstrates the async contract: `init` returns a loading state and fires the fetch; the resolution lands through `updateWidget`, which no-ops if the app was closed meanwhile. Ev… |
| `sdk/host.tsx` | The widget-app host. Core integrates through exactly four touchpoints: launch (slash commands), dispatch (the input pipeline), the MODAL render slot (viewport-level), and the AMBIENT surfaces (dock rows + side rails, al… |
| `sdk/index.ts` | The TUI widget SDK — the one import surface a widget app needs. An app is a `WidgetApp` (state + reducer + render) registered with `defineWidgetApp` and launched by id (usually from a slash command via `launchWidget`).… |
| `sdk/registry.ts` | Exports `defineWidgetApp`, `getWidgetApp`, `removeWidgetApp`, `listWidgetApps` |
| `sdk/types.ts` | One keypress, as the input pipeline delivers it. |
| `sdk/userWidgets.ts` | User widget apps — Hermes authors its own TUI widgets, mirroring the Python plugin contract: drop `<name>.mjs` into `$HERMES_HOME/tui-widgets/`, default-export `register(sdk)`, and the app surfaces in `/` completions an… |
| `theme.ts` | Exports `ThemeColors`, `ThemeBrand`, `Theme`, `themeToneHex`, `ThemeSeeds`, `buildPalette` … |
| `types.ts` | Exports `ActiveTool`, `TodoItem`, `ActivityItem`, `SubagentProgress`, `SubagentOutputEntry`, `SubagentNode` … |
| `types/hermes-ink.d.ts` | Exports `Key`, `InputEvent`, `InputHandler`, `FrameEvent`, `RenderOptions`, `Instance` … |
