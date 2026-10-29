# File reference: `plugins`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `plugins/`

| File | What it does |
|---|---|
| `AGENTS.md` | plugins/ — plugin kinds, compat contract, in-tree policy |
| `__init__.py` | Hermes plugins package |
| `plugin_loader.py` | Shared directory-plugin loader for ``plugins/<kind>/<name>/`` discovery packages (cron_providers, context_engine, memory): import ``__init__.py`` by path with siblings pre-registered so relative imports work, then extra… |
| `plugin_storage.py` | Per-plugin persistent storage: ``<hermes home>/plugin-data/<name>/``. |
| `plugin_utils.py` | Thread-safe lazy singletons for plugin authors (stdlib-only). |

## `plugins/browser/`

| File | What it does |
|---|---|
| `_common.py` | Shared base for the bundled cloud-browser plugins. Every vendor speaks the same REST shape (POST to create a session, one request to release it); :class:`CloudBrowserProvider` owns that lifecycle, subclasses supply attr… |
| `browser_use/__init__.py` | Browser Use cloud browser plugin — bundled, auto-loaded. |
| `browser_use/plugin.yaml` | Browser Use (https://browser-use.com) cloud browser backend. Supports both direct BROWSER_USE_API_KEY and the managed Nous tool gateway. Also powers the 'Nous Subscription' UX flow that bills usage to a Nous subscriptio… |
| `browser_use/provider.py` | Browser Use cloud browser provider — the only backend with dual auth: direct ``BROWSER_USE_API_KEY`` (https://browser-use.com) or the managed Nous tool gateway (bills to a Nous subscription). Direct first, managed secon… |
| `browserbase/__init__.py` | Browserbase cloud browser plugin — bundled, auto-loaded. |
| `browserbase/plugin.yaml` | Browserbase (https://browserbase.com) cloud browser backend. Requires BROWSERBASE_API_KEY + BROWSERBASE_PROJECT_ID. Supports stealth, proxies, and keep-alive sessions; auto-falls-back when paid features are unavailable. |
| `browserbase/provider.py` | Browserbase cloud browser provider: direct ``BROWSERBASE_API_KEY`` + ``BROWSERBASE_PROJECT_ID`` only (the Nous subscription routes through Browser Use). Config ``browser.cloud_provider: "browserbase"``; knobs ``BROWSERB… |
| `firecrawl/__init__.py` | Firecrawl cloud browser plugin — bundled, auto-loaded (distinct from plugins/web/firecrawl/). |
| `firecrawl/plugin.yaml` | Firecrawl (https://firecrawl.dev) cloud browser backend. Requires FIRECRAWL_API_KEY. Distinct from the firecrawl WEB search/extract plugin — the two share an API key but operate on different endpoints. |
| `firecrawl/provider.py` | Firecrawl cloud browser (``/v2/browser`` only; the web plugin under ``plugins/web/firecrawl/`` shares ``FIRECRAWL_API_KEY``). Config ``browser.cloud_provider: "firecrawl"`` (explicit only — not in the legacy auto-detect… |

## `plugins/computer_use/`

| File | What it does |
|---|---|
| `__init__.py` | Computer-use provider discovery: bundled ``plugins/computer_use/<name>/`` (the built-in ``cua`` driver lives here too) then user ``$HERMES_HOME/plugins/<name>/`` (bundled wins on collision). Exactly one provider is acti… |
| `cua/__init__.py` | Built-in ``cua`` computer-use provider: cua-driver over MCP (:mod:`tools.computer_use.cua_backend`). |
| `cua/plugin.yaml` | YAML definition for `cua` |

## `plugins/config_backends/`

| File | What it does |
|---|---|
| `__init__.py` | Config backends (``HERMES_CONFIG_BACKEND``). Selected by ``hermes_cli.config_backend`` directly from the environment, never discovered through the general plugin loader: that loader reads config.yaml, and the backend is… |
| `remote/__init__.py` | Remote config backend: ``HERMES_CONFIG_BACKEND=remote`` serves each profile's config from the config plane (config-config) instead of ``config.yaml``. See ``backend.py``. |
| `remote/backend.py` | The remote config backend (config-config design §4, contract.md §11, §15). |
| `remote/client.py` | HTTP client for the agent routes of the config plane (contract.md §7.1, §7.2). |
| `remote/credentials.py` | The plane credential (design §4.4 step 2, D26, D31, D32). |
| `remote/destination.py` | Where Remote Config may send a credential (the plane bearer, the IdP client secret). |
| `remote/diff.py` | Remote write computation (contract.md §6.4, §15.2). |
| `remote/paths.py` | Dotted-path grammar of the config plane wire contract (contract.md §3). |
| `remote/plugin.yaml` | YAML definition for `remote` |
| `remote/values.py` | Client-side value rules of the config plane wire contract. |
| `remote/vendor/SOURCE.json` | JSON object with keys `repo`, `commit`, `fixtureDigest`, `contractDigest` |
| `remote/vendor/conformance/config-fixtures.sha256` | SHA-256 checksum |
| `remote/vendor/conformance/config-paths.json` | JSON object with keys `fixtureVersion`, `valid`, `invalid`, `covers` |
| `remote/vendor/conformance/config-resolution/chain-order-with-group.json` | `chain-order-with-group` — Proves rule-0, rule-2: With a mapped group the group level sits between tenant and principal. |
| `remote/vendor/conformance/config-resolution/chain-order-without-group.json` | `chain-order-without-group` — Proves rule-0, rule-2: With no mapped group the chain is global, tenant, principal, agent, profile; each lower level overrides the one above it. |
| `remote/vendor/conformance/config-resolution/default-unlocked-every-level-may-write.json` | `default-unlocked-every-level-may-write` — Proves rule-1: With no locks anywhere every level may set, unset, lock and unlock any path. |
| `remote/vendor/conformance/config-resolution/defaults-merge-under-effective.json` | `defaults-merge-under-effective` — Proves rule-5: The agent's DEFAULT_CONFIG step deep-merges the effective document over defaults: mappings merge, lists replace, null over a default scalar stays null. |
| `remote/vendor/conformance/config-resolution/dotted-key-segment.json` | `dotted-key-segment` — Proves path-grammar, rule-3: A key that contains dots is one escaped segment (service\.name) in locks, provenance and writes; the unescaped form names a different path. |
| `remote/vendor/conformance/config-resolution/empty-mapping-is-a-leaf.json` | `empty-mapping-is-a-leaf` — Proves r8, rule-5: An empty mapping is a leaf for provenance; merged over a non-empty mapping it changes nothing, over a scalar it replaces it. |
| `remote/vendor/conformance/config-resolution/global-lock-binds-every-level.json` | `global-lock-binds-every-level` — Proves rule-3, r7: A Global lock binds every stored level; siblings of the locked leaf stay writable; a scalar at its parent is refused. |
| `remote/vendor/conformance/config-resolution/group-absent-level-skipped.json` | `group-absent-level-skipped` — Proves rule-0: When the owner has no mapped group the group level is skipped: no group values or locks apply. |
| `remote/vendor/conformance/config-resolution/group-present-lock-binds-principal.json` | `group-present-lock-binds-principal` — Proves rule-0, rule-3: When the owner has a mapped group, the group level's values apply and its locks bind principal, agent and profile. |
| `remote/vendor/conformance/config-resolution/list-replaces-whole-list.json` | `list-replaces-whole-list` — Proves rule-5: A lower list replaces the whole upper list (no element merge), including lists of mappings and DEFAULT_CONFIG lists. |
| `remote/vendor/conformance/config-resolution/lock-coverage-is-segment-wise.json` | `lock-coverage-is-segment-wise` — Proves rule-3, path-grammar: A lock on terminal covers terminal.backend but not terminal_extra: coverage compares segments, never string prefixes. |
| `remote/vendor/conformance/config-resolution/lock-does-not-restrict-its-own-level.json` | `lock-does-not-restrict-its-own-level` — Proves rule-3: A lock binds only the levels below the level that stores it; the locking level may still set, unset, unlock and add locks under it. |
| `remote/vendor/conformance/config-resolution/lock-freezes-inherited-value-with-no-value-at-locking-level.json` | `lock-freezes-inherited-value-with-no-value-at-locking-level` — Proves rule-3: A tenant lock on a leaf it does not set freezes the global value; lower values under it are ignored and lower writes refused; the tenant its… |
| `remote/vendor/conformance/config-resolution/lock-on-absent-value-freezes-absence.json` | `lock-on-absent-value-freezes-absence` — Proves rule-3: A lock on a path no level at or above it sets freezes it to absent: lower values under it are stripped and a mapping emptied by stripping is removed. |
| `remote/vendor/conformance/config-resolution/lock-under-upper-locked-prefix-rejected.json` | `lock-under-upper-locked-prefix-rejected` — Proves rule-4: A level cannot add a lock equal to or under an upper lock; it may add a lock on a path no upper level has locked. |
| `remote/vendor/conformance/config-resolution/lower-level-adds-lock-on-unlocked-path.json` | `lower-level-adds-lock-on-unlocked-path` — Proves rule-4, rule-3: A principal lock on a path no upper level locked binds agent and profile, but not the levels above the principal. |
| `remote/vendor/conformance/config-resolution/lower-overrides-upper-and-sets-unset-keys.json` | `lower-overrides-upper-and-sets-unset-keys` — Proves rule-2: On unlocked keys a lower level overrides an upper value and may set keys no upper level sets. |
| `remote/vendor/conformance/config-resolution/mappings-merge-key-by-key-across-levels.json` | `mappings-merge-key-by-key-across-levels` — Proves rule-5, rule-2: Nested mappings merge key by key across every level; each leaf takes the value and provenance of the lowest level that sets it. |
| `remote/vendor/conformance/config-resolution/multi-group-emptied-mapping-pruned.json` | `multi-group-emptied-mapping-pruned` — Proves d5-provenance: A mapping emptied because a higher group's lock governs its only key is dropped, not left as an empty leaf; every group provenance leaf names a group. |
| `remote/vendor/conformance/config-resolution/multi-group-higher-ancestor-lock-covers-lower-child-lock.json` | `multi-group-higher-ancestor-lock-covers-lower-child-lock` — Proves d5-lock, r9: A higher group locks a with a scalar over a lower group's lock on a.b; the higher locking group governs the whole section, so a is the hig… |
| `remote/vendor/conformance/config-resolution/multi-group-higher-child-lock-strips-lower-ancestor-scalar.json` | `multi-group-higher-child-lock-strips-lower-ancestor-scalar` — Proves d5-lock, r7, r9: A higher group locks a.b with no value while a lower group locks a with a scalar; the scalar would clobber a.b, so it is stripped an… |
| `remote/vendor/conformance/config-resolution/multi-group-highest-locking-group-value.json` | `multi-group-highest-locking-group-value` — Proves d5-lock: When several groups lock a key the value is the highest-priority LOCKING group's value; a higher non-locking group does not supply it. |
| `remote/vendor/conformance/config-resolution/multi-group-lock-in-lower-group-wins.json` | `multi-group-lock-in-lower-group-wins` — Proves d5-lock: A lower-priority group that locks a key locks it for the principal and supplies the value, over a higher-priority group that sets it unlocked. |
| `remote/vendor/conformance/config-resolution/multi-group-lock-only-freezes-inherited.json` | `multi-group-lock-only-freezes-inherited` — Proves d5-lock: The highest-priority locking group has no value at the locked path, so the inherited tenant value is frozen and a lower group's value is discarded. |
| `remote/vendor/conformance/config-resolution/multi-group-lock-strips-higher-ancestor-scalar.json` | `multi-group-lock-strips-higher-ancestor-scalar` — Proves d5-lock, r7: A higher group's scalar at a strict ancestor of a lower group's lock is stripped; the locked sub-path keeps the locking group's value. |
| `remote/vendor/conformance/config-resolution/multi-group-nested-locks.json` | `multi-group-nested-locks` — Proves d5-lock, r9: A higher group's lock inside a lower group's locked section supplies that sub-path; the rest of the section comes from the lower locking group; the covered lock is droppe… |
| `remote/vendor/conformance/config-resolution/multi-group-no-groups.json` | `multi-group-no-groups` — Proves d5-no-groups: A principal in no group has no group level; groupProvenance is empty and no lock names a group. |
| `remote/vendor/conformance/config-resolution/multi-group-priority-tie-break-by-id.json` | `multi-group-priority-tie-break-by-id` — Proves d5-tie-break: Two groups share a priority (a transient state during a NAS reorder); the group with the byte-wise smaller id is applied last and wins. |
| `remote/vendor/conformance/config-resolution/multi-group-same-key-priority-wins.json` | `multi-group-same-key-priority-wins` — Proves d5-priority: Two groups set the same key; the higher priority wins per leaf, mappings still merge key by key, and file order is not application order. |
| `remote/vendor/conformance/config-resolution/multi-group-three-groups-per-path-governor.json` | `multi-group-three-groups-per-path-governor` — Proves d5-lock, d5-priority: Three groups; each locked path takes the value (or inherited absence) of the highest-priority group whose lock covers it, unlocked paths take t… |
| `remote/vendor/conformance/config-resolution/non-mapping-replaces-mapping-and-back.json` | `non-mapping-replaces-mapping-and-back` — Proves rule-5, r8: A lower scalar or list replaces an upper mapping, and a lower mapping replaces an upper scalar; provenance of replaced leaves is dropped. |
| `remote/vendor/conformance/config-resolution/null-over-empty-mapping-supplies-nothing.json` | `null-over-empty-mapping-supplies-nothing` — Proves rule-5, r8: null over an empty upper mapping is ignored like null over any mapping, so the empty mapping keeps the provenance of the level that supplied it. |
| `remote/vendor/conformance/config-resolution/null-over-mapping-ignored.json` | `null-over-mapping-ignored` — Proves rule-5: null at a lower level over an upper mapping is ignored: the upper mapping and its provenance stay. |
| `remote/vendor/conformance/config-resolution/null-over-scalar-and-list-sets-no-value.json` | `null-over-scalar-and-list-sets-no-value` — Proves rule-5: null at a lower level over an upper scalar or list sets no value (null); over DEFAULT_CONFIG it stays null. |
| `remote/vendor/conformance/config-resolution/profile-level-below-agent.json` | `profile-level-below-agent` — Proves rule-0, rule-3: The profile level overrides the agent level on unlocked keys; an agent-level lock binds the profile level. |
| `remote/vendor/conformance/config-resolution/r7-ancestor-non-mapping-stripped-and-rejected.json` | `r7-ancestor-non-mapping-stripped-and-rejected` — Proves r7: A lower scalar, null or list at a strict ancestor of a locked path would replace the locked subtree: it is stripped on read and refused on write; a mapping at… |
| `remote/vendor/conformance/config-resolution/r7-inner-value-at-ancestor-stripped-and-rejected.json` | `r7-inner-value-at-ancestor-stripped-and-rejected` — Proves r7: An inner non-mapping value of a set at a strict ancestor of a lock is refused; on read it is stripped and a mapping emptied by stripping is removed. |
| `remote/vendor/conformance/config-resolution/r9-redundant-lower-lock-dropped.json` | `r9-redundant-lower-lock-dropped` — Proves r9: A lower lock already covered by an upper lock is omitted from the effective lock list, so lock errors name the upper level. |
| `remote/vendor/conformance/config-resolution/secret-literal-rejected.json` | `secret-literal-rejected` — Proves secret: A literal string or number under a secret-shaped key is refused at every level, including inside mappings and lists; ${env:X} is not a placeholder. |
| `remote/vendor/conformance/config-resolution/secret-placeholder-accepted.json` | `secret-placeholder-accepted` — Proves secret: A ${VAR} placeholder, an empty string, null, and non-secret keys (R14 exemptions, token_count, *_URL env keys) are accepted. |
| `remote/vendor/conformance/config-resolution/section-lock-covers-later-sub-keys.json` | `section-lock-covers-later-sub-keys` — Proves rule-3: A lock on a section covers every sub-key under it, including keys no level had set when the lock was added. |
| `remote/vendor/conformance/config-resolution/set-value-touching-locked-sub-path.json` | `set-value-touching-locked-sub-path` — Proves rule-3, r7: A set of a mapping is checked at every path inside the value: a key under an upper lock is refused, keys beside it are accepted. |
| `remote/vendor/conformance/config-resolution/tenant-section-lock-freezes-inherited.json` | `tenant-section-lock-freezes-inherited` — Proves rule-3, rule-4: A tenant lock on a section freezes the resolved value from levels at or above it and refuses lower writes under it. |
| `remote/vendor/conformance/config-resolution/unset-restores-upper-value.json` | `unset-restores-upper-value` — Proves rule-6: After the profile level unsets model.default it stops overriding and the tenant value applies again; unset of an absent key is accepted. |
| `remote/vendor/conformance/config-resolution/unset-under-lock-rejected-ancestor-unset-accepted.json` | `unset-under-lock-rejected-ancestor-unset-accepted` — Proves rule-6, rule-3: Unset of a locked path by a lower level is refused; unset of an ancestor of the lock only removes the lower level's own subtree and is accepte… |
| `remote/vendor/conformance/config-resolution/upper-lock-cannot-be-removed-or-narrowed.json` | `upper-lock-cannot-be-removed-or-narrowed` — Proves rule-4: A lower level cannot unlock an upper lock, nor lock or unlock a path under it; the level that stores the lock may unlock it. |
| `remote/vendor/conformance/config-resolution/write-accept-reject-per-level.json` | `write-accept-reject-per-level` — Proves rule-3, rule-0: Each level holds one lock; a write by level k to a path locked at level j is refused exactly when j is above k. |
| `remote/vendor/conformance/config-secret-keys.json` | JSON object with keys `fixtureVersion`, `source`, `secretKeys`, `secretKeySuffixes`, `nonSecretKeySuffixes`, `envConfigKeys` |

## `plugins/context_engine/`

| File | What it does |
|---|---|
| `__init__.py` | Context engine plugin discovery: bundled ``plugins/context_engine/<name>/`` then user ``$HERMES_HOME/plugins/<name>/`` (bundled wins on collision) → ``ContextEngine``. Separate from the general plugin system: ``context.… |

## `plugins/cron_providers/`

| File | What it does |
|---|---|
| `__init__.py` | Cron scheduler provider discovery: bundled ``plugins/cron_providers/<name>/`` then user ``$HERMES_HOME/plugins/<name>/`` (bundled wins on collision). The built-in InProcessCronScheduler is core, not discovered here, so… |
| `chronos/__init__.py` | Chronos — NAS-mediated managed cron provider (scale-to-zero). |
| `chronos/_nas_client.py` | Thin HTTP client for the agent -> NAS ``agent-cron`` endpoints (Chronos): arm one-shot / cancel / list, authenticated with the existing Nous Portal token. Wire contract: ``website/docs/developer-guide/chronos-managed-cr… |
| `chronos/plugin.yaml` | YAML definition for `chronos` |
| `chronos/verify.py` | Inbound cron-fire token verification for Chronos. |

## `plugins/dashboard_auth/`

| File | What it does |
|---|---|
| `_shared.py` | Helpers shared by the bundled dashboard-auth providers. |
| `basic/__init__.py` | BasicAuthProvider — username/password dashboard auth (no OAuth IDP). |
| `basic/plugin.yaml` | Dashboard auth provider — username/password (no OAuth IDP). A self-hosted 'just put a password on my dashboard' provider. Activates when dashboard.basic_auth.username plus a password (or password_hash) are configured vi… |
| `drain/__init__.py` | DrainSecretProvider — shared-bearer-secret auth for the drain-control endpoint. |
| `drain/plugin.yaml` | Dashboard auth provider — non-interactive shared-bearer-secret for the gateway drain-control endpoint. The first consumer of the generic token-auth capability (supports_token/verify_token). nous-account-service provisio… |
| `nous/__init__.py` | NousDashboardAuthProvider — Nous Portal OAuth (authorization-code + PKCE). |
| `nous/plugin.yaml` | Dashboard auth provider — OAuth 2.0 (authorization-code + PKCE) against Nous Portal. Auto-activates when a client_id is configured via either dashboard.oauth.client_id in config.yaml (canonical surface) or HERMES_DASHBO… |
| `self_hosted/__init__.py` | SelfHostedOIDCProvider — generic self-hosted OpenID Connect dashboard auth. |
| `self_hosted/plugin.yaml` | Dashboard auth provider — generic self-hosted OpenID Connect (authorization-code + PKCE, public client). Works against any conformant OIDC identity provider (Authentik, Keycloak, Zitadel, Authelia, Auth0, Okta, Google,… |
| `session_token/__init__.py` | SessionTokenProvider — the deployment session token as a first-class credential. |
| `session_token/plugin.yaml` | Dashboard auth provider — the deployment session token (HERMES_DASHBOARD_SESSION_TOKEN, including the file:<path> form the Nix modules render) as a first-class gated-mode credential. verify_session constant-time-compare… |

## `plugins/delegation/`

| File | What it does |
|---|---|
| `default/__init__.py` | Default delegation strategy (``delegation.backend: default``). |
| `default/plugin.yaml` | Default delegation strategy: every delegate_task subagent follows the delegation section of config.yaml (delegation.provider / model / base_url ...), else inherits the parent's model and credentials. |

## `plugins/disk-cleanup/`

| File | What it does |
|---|---|
| `README.md` | disk-cleanup |
| `__init__.py` | disk-cleanup plugin — auto-cleanup of ephemeral Hermes session files. |
| `disk_cleanup.py` | disk_cleanup — ephemeral file cleanup library behind the disk-cleanup plugin. |
| `plugin.yaml` | Auto-track and clean up ephemeral files (test scripts, temp outputs, cron logs) created during Hermes sessions. Runs via plugin hooks — no agent action required. |

## `plugins/google_meet/`

| File | What it does |
|---|---|
| `README.md` | google_meet plugin |
| `SKILL.md` | Join a Google Meet call, transcribe live captions, optionally speak in realtime, and do the followup work afterwards. Use when the user asks the agent to sit in on a meeting, take notes, summarize, respond in-call, or a… |
| `__init__.py` | google_meet plugin — let the agent join a Meet call, transcribe it, follow up. |
| `_jsonfile.py` | Tiny JSON file helpers shared by the bot, process manager, node registry and node server. |
| `audio_bridge.py` | Virtual audio bridge for feeding generated speech into Chrome's mic. |
| `cli.py` | CLI commands for the google_meet plugin (``hermes meet <subcommand>``). |
| `meet_bot.py` | Headless Google Meet bot — Playwright + live-caption scraping. |
| `node/__init__.py` | Remote 'node host': run the Meet bot on a different machine than the gateway. |
| `node/cli.py` | `hermes meet node ...` subcommand tree, wired under the ``hermes meet`` parser. |
| `node/client.py` | Gateway-side RPC client for a remote meet node: one short-lived sync WebSocket per call, so non-async tool handlers need no persistent connection. ``websockets`` is imported lazily. |
| `node/protocol.py` | Wire protocol for gateway ↔ node RPC (JSON envelopes). |
| `node/registry.py` | Local JSON registry of approved remote meet nodes. |
| `node/server.py` | Remote node server — hosts the Meet bot on another machine (``hermes meet node run``). |
| `plugin.yaml` | Join a Google Meet call, transcribe live captions, speak in realtime, and follow up afterwards. v1 transcribe-only is the default; v2 realtime duplex audio via OpenAI Realtime + BlackHole/PulseAudio ships with mode='rea… |
| `process_manager.py` | Subprocess lifecycle manager for the google_meet bot. |
| `realtime/__init__.py` | Realtime speech: thin OpenAI Realtime client + file-queue speaker for the Meet bot. |
| `realtime/openai_client.py` | OpenAI Realtime API WebSocket client + file-queue speaker. |
| `tools.py` | Agent-facing tools for the google_meet plugin. |

## `plugins/hermes-achievements/`

| File | What it does |
|---|---|
| `LICENSE` | Software license text |
| `README.md` | Hermes Achievements |
| `dashboard/dist/index.js` | JavaScript source: `index` |
| `dashboard/dist/style.css` | hermes-achievements dashboard styles Originally authored by |
| `dashboard/manifest.json` | `hermes-achievements` — Steam-style achievements for vibe coding and agentic Hermes workflows. |
| `dashboard/plugin_api.py` | Hermes Achievements dashboard plugin backend, mounted at /api/plugins/hermes-achievements/. |
| `docs/assets/achievements-dashboard-hd.png` | PNG image asset |
| `docs/assets/achievements-tier-showcase-hd.png` | PNG image asset |
| `tests/test_achievement_engine.py` | Tests: `AchievementEngineTests`, `CompactionScanTests` |

## `plugins/image_gen/`

| File | What it does |
|---|---|
| `_common.py` | Shared helpers for the bundled ``image_gen`` provider plugins. Providers are loaded by path (``hermes_plugins.image_gen__<name>``) and resolve this via the repo root on ``sys.path``; not a plugin itself (the scanner onl… |
| `deepinfra/__init__.py` | DeepInfra image generation (FLUX, Qwen-Image-Edit, …) via the OpenAI-compatible ``/v1/openai/images/generations`` endpoint. The catalog is fully dynamic (``image-gen``-tagged models from :func:`hermes_cli.models._fetch_… |
| `deepinfra/plugin.yaml` | DeepInfra image generation backend (FLUX, Qwen-Image, …) via OpenAI-compatible /v1/images/generations. Catalog discovered live from api.deepinfra.com. |
| `fal/__init__.py` | FAL.ai registration adapter. Catalog, payload, submission, managed-gateway selection and Clarity Upscaler chaining live in :mod:`tools.image_generation_tool`; this plugin imports it at call time so tests keep patching `… |
| `fal/plugin.yaml` | FAL.ai image generation backend (flux-2-klein, flux-2-pro, nano-banana-2, nano-banana-pro, gpt-image-1.5, recraft-v3, etc.). |
| `krea/__init__.py` | Krea image generation backend: ``Krea 3`` (generates and edits) and ``Krea 2`` Medium / Large / Medium Turbo. |
| `krea/plugin.yaml` | Krea image generation backend: Krea 3 (generates and edits) and Krea 2 Medium, Large and Medium Turbo. Direct KREA_API_KEY or managed Nous Subscription gateway. |
| `meta-ai/__init__.py` | Meta Model API (``muse-image``): OpenAI-compatible (https://api.meta.ai/v1), so the OpenAI SDK is pointed at Meta's base URL with ``META_MODEL_API_KEY``. Output is base64 WebP → image cache. Selection: ``model`` kwarg →… |
| `meta-ai/plugin.yaml` | Meta Model API image generation backend (muse-image). OpenAI-compatible /v1/images/generations. Saves images to $HERMES_HOME/cache/generated/images/. |
| `openai-codex/__init__.py` | OpenAI image generation — ChatGPT/Codex OAuth variant. |
| `openai-codex/plugin.yaml` | OpenAI image generation backed by ChatGPT/Codex OAuth (gpt-image-2 via the native Codex images/generations and images/edits endpoints). Saves generated images to $HERMES_HOME/cache/generated/images/. |
| `openai/__init__.py` | OpenAI GPT Image 2 and 2.5 Flare/Sunburst quality tiers; base64 output → image cache. Selection: ``OPENAI_IMAGE_MODEL`` → ``image_gen.openai.model`` → ``image_gen.model`` → :data:`DEFAULT_MODEL`; an id outside the catal… |
| `openai/plugin.yaml` | OpenAI image generation backend (GPT Image 2 and GPT Image 2.5 Flare/Sunburst). Saves generated images to $HERMES_HOME/cache/generated/images/. |
| `openrouter/__init__.py` | OpenRouter-compatible image generation backend (OpenRouter + Nous Portal). |
| `openrouter/plugin.yaml` | OpenRouter + Nous Portal image generation. Chat-completions image output (reference-grounded) plus OpenRouter's Dedicated Image API (/images/generations) for gpt-image-2, Krea 2, Qwen Image 3 Pro, MAI-Image-2.5 and Grok… |
| `xai/__init__.py` | xAI ``grok-imagine-image`` backend: text-to-image (``/v1/images/generations``) and editing (``/v1/images/edits``), base64 output saved to cache. Selection: ``model`` kwarg → ``XAI_IMAGE_MODEL`` → ``image_gen.xai.model``… |
| `xai/plugin.yaml` | xAI image generation backend (grok-imagine-image). Text-to-image. |

## `plugins/kanban/`

| File | What it does |
|---|---|
| `dashboard/dist/index.js` | Hermes Kanban — Dashboard Plugin Board view for the multi-agent collaboration board backed by ~/.hermes/kanban.db. Calls the plugin's backend at /api/plugins/kanban/ and tails task_events over a WebSocket for live updat… |
| `dashboard/dist/style.css` | Hermes Kanban — dashboard plugin styles. All colors reference theme CSS vars so the board reskins with the active dashboard theme. No hardcoded palette. |
| `dashboard/manifest.json` | `kanban` — Multi-agent collaboration board — drag-drop cards across columns, read comment threads, see which profile is running what |
| `dashboard/plugin_api.py` | Kanban dashboard plugin — backend API routes, mounted at /api/plugins/kanban/. |
| `systemd/hermes-kanban-dispatcher.service` | systemd unit file |

## `plugins/memory/`

| File | What it does |
|---|---|
| `__init__.py` | Memory provider plugin discovery: bundled ``plugins/memory/<name>/``, user ``$HERMES_HOME/plugins/<name>/``, project ``./.hermes/plugins/<name>/`` (opt-in via HERMES_ENABLE_PROJECT_PLUGINS), then ``hermes_agent.memory_p… |
| `byterover/README.md` | ByteRover Memory Provider |
| `byterover/__init__.py` | ByteRover memory plugin — MemoryProvider interface. |
| `byterover/plugin.yaml` | ByteRover — persistent knowledge tree with tiered retrieval via the brv CLI. |
| `config_schema.py` | Declarative config schema for memory provider plugins: each declares its fields in a ``config_schema.py`` beside ``__init__.py``; one generic renderer and one ``GET/PUT /api/memory/providers/{name}/config`` pair drive t… |
| `query_rewrite.py` | Rewrite the latest user message into a clean memory-retrieval query. |
| `retaindb/README.md` | RetainDB Memory Provider |
| `retaindb/__init__.py` | RetainDB memory plugin — MemoryProvider interface. |
| `retaindb/plugin.yaml` | RetainDB — cloud memory API with hybrid search and 7 memory types. |

## `plugins/model-providers/`

| File | What it does |
|---|---|
| `README.md` | Model Provider Plugins |
| `actual/__init__.py` | Actual Computer provider profile. |
| `actual/plugin.yaml` | Actual Computer inference |
| `ai-gateway/__init__.py` | Vercel AI Gateway provider profile: attribution headers + reasoning passthrough. |
| `ai-gateway/plugin.yaml` | Vercel AI Gateway |
| `alibaba-coding-plan/__init__.py` | Alibaba Cloud Coding Plan provider profiles (intl + CN): a dedicated endpoint and key tier separate from ``alibaba``. Names match models.dev catalog keys. |
| `alibaba-coding-plan/plugin.yaml` | Alibaba Cloud Coding Plan |
| `alibaba/__init__.py` | Alibaba Cloud DashScope provider profiles (intl + CN, plus the Model Studio Token Plan flat-token tier with its own key/endpoints — one module per vendor). |
| `alibaba/plugin.yaml` | Alibaba DashScope (international) |
| `anthropic/__init__.py` | Native Anthropic provider profile. |
| `anthropic/plugin.yaml` | Anthropic (Claude) |
| `arcee/__init__.py` | Arcee AI provider profile. |
| `arcee/plugin.yaml` | Arcee AI |
| `azure-foundry/__init__.py` | Microsoft Foundry provider profile: OpenAI-compatible, per-resource base URL supplied by the user at setup. |
| `azure-foundry/plugin.yaml` | Microsoft Foundry |
| `bedrock/__init__.py` | AWS Bedrock provider profile. |
| `bedrock/plugin.yaml` | AWS Bedrock |
| `commandcode/__init__.py` | CommandCode provider profiles: ``commandcode`` (chat_completions) and ``commandcode-anthropic`` (anthropic_messages, Bearer auth — see ``agent/anthropic_adapter.py``). Same key and base URL for both. |
| `commandcode/plugin.yaml` | CommandCode — unified multi-model API (OpenAI chat completions + Anthropic Messages) |
| `custom/__init__.py` | Custom / Ollama (local) provider profile: any endpoint registered as provider="custom" (Ollama, vLLM, llama.cpp, GLM-5.2 on ARK, …). |
| `custom/plugin.yaml` | Custom / Ollama / local OpenAI-compatible endpoint |
| `deepinfra/__init__.py` | DeepInfra provider profile (chat surface; image-gen/TTS/STT are wired via their own plugin subsystems). |
| `deepinfra/plugin.yaml` | DeepInfra — 100+ open models, pay-per-use |
| `deepseek/__init__.py` | DeepSeek provider profile. |
| `deepseek/plugin.yaml` | DeepSeek |
| `fireworks/__init__.py` | Fireworks AI provider profile. Models are addressed by full catalog ID (``accounts/fireworks/models/<slug>``), tracking fw-ai/fireconnect ``setup-cli``. |
| `fireworks/plugin.yaml` | Fireworks AI — fast inference for open and proprietary models |
| `gemini/__init__.py` | Google Gemini (AI Studio) provider profile. |
| `gemini/plugin.yaml` | Google Gemini (API key + Cloud Code OAuth) |
| `gmi/__init__.py` | GMI Cloud provider profile. |
| `gmi/plugin.yaml` | GMI Cloud |
| `huggingface/__init__.py` | Hugging Face provider profile. |
| `huggingface/plugin.yaml` | HuggingFace Inference Providers |
| `kilocode/__init__.py` | Kilo Code provider profile. |
| `kilocode/plugin.yaml` | Kilo Code |
| `kimi-coding/__init__.py` | Kimi / Moonshot provider profiles (chat_completions path; sk-kimi-* keys are redirected to api.kimi.com/coding by core). |
| `kimi-coding/plugin.yaml` | Moonshot Kimi Coding (global + China) |
| `lmstudio/__init__.py` | LM Studio provider profile (local desktop app with an OpenAI-compatible server). |
| `lmstudio/plugin.yaml` | LM Studio |
| `meta-ai/__init__.py` | Meta Model API (Muse Spark) provider profile — https://api.meta.ai/v1. |
| `meta-ai/plugin.yaml` | Meta Model API — Muse Spark family (Meta Superintelligence Labs) |
| `minimax/__init__.py` | MiniMax provider profiles (international, China, OAuth). |
| `minimax/plugin.yaml` | MiniMax M-series (global + China + OAuth) |
| `nebius-token-factory/__init__.py` | Nebius Token Factory provider profile. |
| `nebius-token-factory/plugin.yaml` | Nebius Token Factory OpenAI-compatible inference |
| `nous/__init__.py` | Nous Portal provider profile. |
| `nous/plugin.yaml` | Nous Research Portal |
| `novita/__init__.py` | NovitaAI provider profile. |
| `novita/plugin.yaml` | NovitaAI AI-native cloud for builders and agents |
| `nvidia/__init__.py` | NVIDIA NIM provider profile. |
| `nvidia/plugin.yaml` | NVIDIA NIM |
| `ollama-cloud/__init__.py` | Ollama Cloud provider profile. |
| `ollama-cloud/plugin.yaml` | Ollama Cloud |
| `openai-codex/__init__.py` | OpenAI Codex (Responses API) provider profile. |
| `openai-codex/plugin.yaml` | OpenAI Codex (Responses API) |
| `opencode-zen/__init__.py` | OpenCode provider profiles (Zen + Go). |
| `opencode-zen/plugin.yaml` | OpenCode (Zen + Go) |
| `openrouter/__init__.py` | OpenRouter provider profile. |
| `openrouter/plugin.yaml` | OpenRouter aggregator |
| `qwen-oauth/__init__.py` | Qwen Portal provider profile. |
| `qwen-oauth/plugin.yaml` | Qwen Portal (OAuth) |
| `router/__init__.py` | Ramp Router (router.com) provider profile: Responses-only LLM gateway (verified live). |
| `router/plugin.yaml` | Ramp Router (router.com) — OpenAI Responses-compatible LLM gateway |
| `solstice/__init__.py` | Solstice provider profile: a user's own per-user-quota Gemini subscription, signed in with OAuth. |
| `solstice/auth.py` | Solstice sign-in: browser PKCE with a loopback redirect, token exchange and refresh brokered by the Nous portal (NAS), which holds the confidential client secret. Hermes keeps its own PKCE verifier and the user's tokens… |
| `solstice/plugin.yaml` | Solstice (per-user-quota OAuth, pre-release) |
| `solstice/transport.py` | Solstice inference transport: the native Gemini wire on the per-user-quota methods, with the user's OAuth access token as a Bearer instead of an API key. |
| `stepfun/__init__.py` | StepFun provider profile. |
| `stepfun/plugin.yaml` | StepFun Step Plan |
| `tencent-tokenhub/__init__.py` | Tencent TokenHub provider profile (OpenAI-compatible, tokenhub.tencentmaas.com). |
| `tencent-tokenhub/plugin.yaml` | Tencent TokenHub |
| `upstage/__init__.py` | Upstage Solar provider profile: top-level ``reasoning_effort`` (low\|medium\|high). |
| `upstage/plugin.yaml` | Upstage (Solar API) |
| `vertex/__init__.py` | Google Vertex AI provider profile: Gemini via Google Cloud's OpenAI-compatible endpoint. |
| `vertex/plugin.yaml` | Google Vertex AI (Gemini via OpenAI-compatible endpoint, OAuth2) |
| `xai/__init__.py` | xAI (Grok) provider profile. |
| `xai/plugin.yaml` | xAI Grok (Responses API) |
| `xiaomi/__init__.py` | Xiaomi MiMo provider profile. |
| `xiaomi/plugin.yaml` | Xiaomi MiMo |
| `zai/__init__.py` | ZAI / GLM provider profile. |
| `zai/plugin.yaml` | Z.AI / GLM |

## `plugins/platforms/`

| File | What it does |
|---|---|
| `a2a/DESIGN.md` | A2A Platform Plugin — Design |
| `a2a/README.md` | A2A — Agent-to-Agent protocol for Hermes |
| `a2a/__init__.py` | A2A (Agent-to-Agent) plugin: registers the inbound ``a2a`` platform adapter and the five outbound client tools of the ``a2a`` toolset through the public PluginContext. |
| `a2a/adapter.py` | A2A inbound adapter: stdlib http.server (daemon thread) serving the Agent Card, /metrics and JSON-RPC (message/send, message/stream SSE, tasks/*, push-config CRUD). Inbound tasks are framed (security.wrap_inbound) and r… |
| `a2a/plugin.yaml` | YAML definition for `a2a-platform` |
| `a2a/protocol.py` | A2A protocol helpers — Agent Card, JSON-RPC framing, task store, conversation persistence. Wire shape is A2A v1.0: SCREAMING_SNAKE_CASE states/roles; Parts and StreamResponse events are discriminated by member presence… |
| `a2a/security.py` | A2A security primitives (adapter + client tools). A2A is a *network* surface: bind safety (no token => 127.0.0.1 only); peer identity from credentials, never the body (A2A_PEER_TOKENS token->name, shared A2A_BEARER_TOKE… |
| `a2a/tools.py` | A2A client tools (``a2a`` toolset): a2a_discover/call/list/history/orchestrate talk to *other* agents. Peers come from config.yaml ``a2a_agents: {name: {url, auth: {type: bearer, token}, timeout, capabilities}}``. Stdli… |
| `bluebubbles/__init__.py` | Package marker / package-level exports |
| `bluebubbles/adapter.py` | BlueBubbles iMessage platform adapter: local BlueBubbles macOS server for outbound REST sends and inbound webhooks (text, media attachments, typing indicators, read receipts). |
| `bluebubbles/gateway_env.py` | BlueBubbles (iMessage) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `bluebubbles/plugin.yaml` | YAML definition for `bluebubbles-platform` |
| `buzz/__init__.py` | Package marker / package-level exports |
| `buzz/adapter.py` | Buzz platform adapter (Block's Nostr-based human+agent community relay). |
| `buzz/buzz_cursors.py` | Durable per-channel receive cursors for the Buzz adapter (#90464): a restart resumes from the saved cursor instead of reseeding from history and marking downtime arrivals as seen. |
| `buzz/nostr_auth.py` | Dependency-free Nostr signing (secp256k1 / BIP-340) for Buzz WebSocket authentication. |
| `buzz/plugin.yaml` | YAML definition for `buzz-platform` |
| `buzz/send_targets.py` | send_message declarations for the Buzz ``PlatformEntry`` (kept out of the adapter module). |
| `dingtalk/__init__.py` | Package marker / package-level exports |
| `dingtalk/adapter.py` | DingTalk platform adapter (Stream Mode via dingtalk-stream >=0.20; replies via session webhook markdown or AI Cards). Requires ``pip install "dingtalk-stream>=0.20" httpx``. config.yaml ``platforms.dingtalk``: ``enabled… |
| `dingtalk/gateway_env.py` | DingTalk env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `dingtalk/inbound.py` | Pure parsers for inbound DingTalk ``ChatbotMessage`` payloads (no I/O, no adapter state). |
| `dingtalk/plugin.yaml` | YAML definition for `dingtalk-platform` |
| `discord/__init__.py` | Package marker / package-level exports |
| `discord/adapter.py` | Defines `_voice_mixer_module`, `_image_ext_from_content_type`, `_format_discord_markdown_link`, `_Snowflake`, `_default_voice_ack_phrases`, `_t_discord` … |
| `discord/adapter_authorization.py` | Fresh membership checks for owner-held durable native inputs. |
| `discord/adapter_component_auth.py` | Shared user-or-role authorization for Discord component (button) clicks. |
| `discord/adapter_config_readers.py` | config.yaml readers for the Discord adapter: DM role-auth guild opt-in and button-view timeout. |
| `discord/adapter_exec_approval_view.py` | The Discord exec-approval card's button view. |
| `discord/adapter_hint.py` | Discord system-prompt platform hint (``PlatformEntry.platform_hint``), kept out of the adapter facade. |
| `discord/adapter_media.py` | Discord native media uploads and delivery fallbacks. |
| `discord/adapter_slash_auth.py` | Slash-command authorization verdict for the Discord adapter: the on_message gates, side-effect free. |
| `discord/adapter_thread_titles.py` | Keep Hermes's own auto-thread title rename out of the pinned session-context prompt. |
| `discord/adapter_voice_info.py` | Who is in the bot's Discord voice channel and who is speaking, for status and prompt context. |
| `discord/dashboard_card.py` | Discord's Channels-page card (Desktop + web dashboard): the PlatformEntry ``dashboard_*`` / ``docs_url`` fields register() spreads in. Kept apart from adapter.py, which is over its size cap. |
| `discord/ffmpeg_utils.py` | ffmpeg discovery for Discord voice: ``tools.transcription_audio`` owns the shared lookup (PATH + Homebrew/local prefixes); this layers an explicit ``FFMPEG_PATH`` override and a Windows winget fallback (installs that ne… |
| `discord/gateway_env.py` | Discord env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `discord/onboarding.py` | Discord onboarding: check a bot token against Discord and walk the user through setup. |
| `discord/plugin.yaml` | YAML definition for `discord-platform` |
| `discord/recovery.py` | Durable state for Discord reconnect message recovery. |
| `discord/send_targets.py` | send_message declarations for the Discord ``PlatformEntry`` (kept out of the adapter module). |
| `discord/voice_mixer.py` | Defines `_require_numpy`, `MixerChild`, `VoiceMixer`, `decode_to_pcm`, `synth_ambient_pcm` |
| `email/__init__.py` | Package marker / package-level exports |
| `email/adapter.py` | Email platform adapter for the Hermes gateway: users talk to Hermes by sending email; IMAP (polled) receives, SMTP sends. Configured via EMAIL_* env vars or ``platforms.email`` in config.yaml (see website docs). |
| `email/gateway_env.py` | Email env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `email/plugin.yaml` | YAML definition for `email-platform` |
| `feishu/__init__.py` | Package marker / package-level exports |
| `feishu/adapter.py` | Feishu/Lark platform adapter. |
| `feishu/adapter_hint.py` | Feishu system-prompt platform hint (``PlatformEntry.platform_hint``), kept out of the adapter facade. |
| `feishu/dashboard_card.py` | Feishu / Lark's Channels-page card (Desktop + web dashboard): the PlatformEntry ``dashboard_*`` / ``docs_url`` fields register() spreads in. Kept apart from adapter.py, which is over its size cap. |
| `feishu/feishu_admission_diagnostics.py` | Operator-facing diagnostics for Feishu inbound admission. |
| `feishu/feishu_comment.py` | Feishu/Lark drive document comment handling (``drive.notice.comment_add_v1`` → Drive v1/v2 comment APIs). Flow: parse event -> access check -> OK reaction -> parallel fetch (doc meta + comment) -> timeline (whole-doc co… |
| `feishu/feishu_comment_rules.py` | Feishu document comment access-control rules: exact doc > wildcard "*" > top-level > code defaults, each field (enabled/policy/allow_from) falling back independently. Config ~/.hermes/feishu_comment_rules.json (mtime-ca… |
| `feishu/feishu_meeting_invite.py` | Feishu/Lark meeting-invitation events: ``vc.bot.meeting_invited_v1`` -> synthetic gateway ``MessageEvent`` so the reply reaches the inviter through the normal gateway pipeline (no agent is instantiated here). |
| `feishu/gateway_env.py` | Feishu/Lark env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `feishu/plugin.yaml` | YAML definition for `feishu-platform` |
| `feishu/send_targets.py` | send_message declarations for the Feishu ``PlatformEntry`` (kept out of the adapter module). |
| `google_chat/__init__.py` | Package marker / package-level exports |
| `google_chat/adapter.py` | Google Chat platform adapter. |
| `google_chat/cards.py` | Google Chat outbound text formatting and Cards v2 rendering. |
| `google_chat/oauth.py` | User OAuth helper for the Google Chat gateway adapter. |
| `google_chat/plugin.yaml` | YAML definition for `google_chat-platform` |
| `google_chat/setup_files.py` | ``/setup-files`` in-chat OAuth setup flow for native attachment delivery. |
| `irc/__init__.py` | Package marker / package-level exports |
| `irc/adapter.py` | IRC Platform Adapter for Hermes Agent — stdlib asyncio only, zero external dependencies. |
| `irc/plugin.yaml` | YAML definition for `irc-platform` |
| `line/__init__.py` | Package marker / package-level exports |
| `line/adapter.py` | LINE Messaging API adapter: aiohttp webhook (signature-verified) → BasePlatformAdapter. |
| `line/plugin.yaml` | YAML definition for `line-platform` |
| `matrix/__init__.py` | Package marker / package-level exports |
| `matrix/adapter.py` | Matrix gateway adapter (any homeserver, via mautrix; optional E2EE with ``mautrix[encryption]``). |
| `matrix/adapter_crypto.py` | Matrix E2EE crypto state-store shim handed to mautrix's OlmMachine. |
| `matrix/adapter_hint.py` | Matrix system-prompt platform hint (``PlatformEntry.platform_hint``), kept out of the adapter facade. |
| `matrix/dashboard_card.py` | Matrix's Channels-page card (Desktop + web dashboard): the PlatformEntry ``dashboard_*`` / ``docs_url`` fields register() spreads in. Kept apart from adapter.py, which is over its size cap. |
| `matrix/gateway_env.py` | Matrix env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `matrix/plugin.yaml` | YAML definition for `matrix-platform` |
| `matrix/send_targets.py` | send_message declarations for the Matrix ``PlatformEntry`` (kept out of the adapter module). |
| `matrix/voice_mention.py` | Park unmentioned MSC3245 voice messages until the sender's bare @mention claims them. |
| `mattermost/__init__.py` | Package marker / package-level exports |
| `mattermost/adapter.py` | Mattermost gateway adapter — REST API v4 + WebSocket via aiohttp (no Mattermost SDK). |
| `mattermost/gateway_env.py` | Mattermost env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `mattermost/plugin.yaml` | YAML definition for `mattermost-platform` |
| `ntfy/__init__.py` | Package marker / package-level exports |
| `ntfy/adapter.py` | ntfy platform adapter: HTTP-streaming subscription (``/json``, ``poll=false``) in, POST out. |
| `ntfy/plugin.yaml` | YAML definition for `ntfy-platform` |
| `photon/README.md` | Photon iMessage platform plugin |
| `photon/__init__.py` | Photon Spectrum (iMessage) platform plugin entry point. |
| `photon/adapter.py` | Photon Spectrum (iMessage) platform adapter. |
| `photon/auth.py` | Photon Dashboard API client + device-code login flow (pure Python, no spectrum-ts). |
| `photon/cli.py` | ``hermes photon ...`` CLI subcommands (registered via ``ctx.register_cli_command()``): setup (device login + project + user + sidecar), status, install-sidecar (npm install in the sidecar dir), telemetry [on\|off]. Devi… |
| `photon/plugin.yaml` | YAML definition for `photon-platform` |
| `photon/sidecar/.gitignore` | Git ignore rules |
| `photon/sidecar/README.md` | Photon sidecar |
| `photon/sidecar/index.mjs` | Hermes Agent — Photon Spectrum sidecar Spawned by `plugins/platforms/photon/adapter.py` to bridge BOTH directions of messaging to Photon's Spectrum platform via the `spectrum-ts` SDK (the |
| `photon/sidecar/package-lock.json` | JSON manifest for `@hermes-agent/photon-sidecar` |
| `photon/sidecar/package.json` | `@hermes-agent/photon-sidecar` — Spectrum-ts bridge for the Hermes Agent Photon platform plugin. |
| `photon/sidecar/patch-spectrum-mixed-attachments.mjs` | Exports `patchSpectrumTs` |
| `photon/sidecar/send-format.mjs` | Outbound /send builder selection for the Photon sidecar. spectrumMarkdown() enables data detection (enableDataDetection) in the underlying iMessage API, which can 500 on messages containing raw URLs. |
| `photon/sidecar/stream-staleness.mjs` | Pure decision helpers for the zombie-stream (half-open gRPC) watchdog. spectrum-ts only reconnects when its inbound async iterator throws or ends. A half-open ("zombie") socket makes the iterator hang forever — no error, |
| `photon/sidecar_paths.py` | Resolve where the Photon sidecar runs from and where its Node deps live. |
| `qqbot/__init__.py` | Package marker / package-level exports |
| `qqbot/adapter.py` | QQ Bot platform adapter (Official QQ Bot API v2): WebSocket gateway for inbound events, REST (``api.sgroup.qq.com``) for outbound messages and media uploads. |
| `qqbot/chunked_upload.py` | QQ Bot chunked upload flow (files 10 MB..~100 MB; inline uploads cap at ~10 MB): 1. POST .../upload_prepare → upload_id, block_size, pre-signed COS part URLs; 2. per part: PUT bytes to COS, then POST .../upload_part_fin… |
| `qqbot/constants.py` | QQBot package-level constants shared across adapter, onboard, and other modules. |
| `qqbot/crypto.py` | AES-256-GCM utilities for QQBot scan-to-configure credential decryption. |
| `qqbot/gateway_env.py` | QQ (Official Bot API v2) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `qqbot/keyboards.py` | QQ Bot inline keyboards + approval / update-prompt helpers. A button click dispatches an ``INTERACTION_CREATE`` event carrying the button's ``data``; the bot must ACK promptly via ``PUT /interactions/{id}`` or the user… |
| `qqbot/onboard.py` | QQBot scan-to-configure (QR code onboard). Mirrors the Feishu pattern: synchronous HTTP + one entry-point ``qr_register()`` (create task → display QR → poll → decrypt) against ``q.qq.com`` bind-task endpoints. |
| `qqbot/plugin.yaml` | YAML definition for `qqbot-platform` |
| `qqbot/register.py` | QQ Bot platform plugin: interactive setup and registry entry. |
| `qqbot/send.py` | Out-of-process QQ Bot sender (cron / CLI). Text tries guild, then C2C, then group. Media uploads through C2C then group; guild channels have no native media path. |
| `qqbot/utils.py` | QQBot shared utilities — User-Agent, HTTP helpers, config coercion. |
| `raft/__init__.py` | Package marker / package-level exports |
| `raft/adapter.py` | Raft channel platform adapter. |
| `raft/plugin.yaml` | YAML definition for `raft-platform` |
| `signal/__init__.py` | Absolute import (not ``from .adapter``): the plugin loader executes this package under a synthetic ``hermes_plugins.platforms__signal`` name, and the adapter's own absolute sibling imports would then load a second ``plu… |
| `signal/adapter.py` | Signal messenger platform adapter for a signal-cli daemon in HTTP mode (``signal-cli daemon --http 127.0.0.1:8080``): inbound via SSE, outbound via JSON-RPC 2.0. Requires SIGNAL_HTTP_URL and SIGNAL_ACCOUNT. |
| `signal/gateway_env.py` | Signal env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `signal/plugin.yaml` | YAML definition for `signal-platform` |
| `signal/register.py` | Signal plugin registration: configured/validate checks and ``register``. |
| `signal/setup.py` | Interactive ``hermes gateway setup`` wizard for Signal. Helpers resolve late through the ``hermes_cli.gateway`` facade so the plugin stays importable outside the CLI and the seams tests patch there keep intercepting. |
| `signal/signal_format.py` | Shared Signal formatting helpers: Markdown → Signal native formatting lives here so both the live adapter and the standalone send paths emit the same bodyRanges. |
| `signal/signal_rate_limit.py` | Signal attachment rate-limit scheduler: process-wide token-bucket simulator mirroring the per-account attachment rate limit signal-cli/Signal-Server enforce. Producers (``SignalAdapter.send_multiple_images`` and the ``s… |
| `signal/standalone.py` | Out-of-process Signal send (cron / ``hermes send`` / send_message without a live gateway): raw signal-cli JSON-RPC with Signal formatting, attachment batching and the process-wide rate-limit scheduler shared with the ga… |
| `simplex/__init__.py` | Package marker / package-level exports |
| `simplex/adapter.py` | SimpleX Chat adapter: persistent WebSocket to a simplex-chat daemon (``simplex-chat -p 5225``, or ``docker run -p 5225:5225 simplexchat/simplex-chat-cli -p 5225``); JSON commands out, events in. |
| `simplex/plugin.yaml` | YAML definition for `simplex-platform` |
| `slack/__init__.py` | Package marker / package-level exports |
| `slack/adapter.py` | Slack platform adapter: slack-bolt Socket Mode (messages, slash commands, threads). |
| `slack/adapter_hint.py` | Slack system-prompt platform hint (``PlatformEntry.platform_hint``), kept out of the adapter facade. |
| `slack/adapter_slash_lane.py` | Per-session handoff order for Slack slash commands. |
| `slack/adapter_slash_payload.py` | Slack slash-command payload decoding: the gateway text and the thread anchor of a slash. |
| `slack/block_kit.py` | Render agent markdown into Slack Block Kit blocks. |
| `slack/dashboard_card.py` | Slack's Channels-page card (Desktop + web dashboard): the PlatformEntry ``dashboard_*`` / ``docs_url`` fields register() spreads in. Kept apart from adapter.py, which is over its size cap. |
| `slack/gateway_env.py` | Slack env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `slack/plugin.yaml` | YAML definition for `slack-platform` |
| `slack/send_targets.py` | send_message declarations for the Slack ``PlatformEntry`` (kept out of the adapter module). |
| `sms/__init__.py` | Package marker / package-level exports |
| `sms/adapter.py` | SMS (Twilio) platform adapter. |
| `sms/gateway_env.py` | SMS (Twilio) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `sms/plugin.yaml` | YAML definition for `sms-platform` |
| `teams/__init__.py` | Package marker / package-level exports |
| `teams/adapter.py` | Microsoft Teams adapter: microsoft-teams-apps SDK for auth/activity processing, an aiohttp webhook server for inbound, ``App.send()`` for proactive sends. |
| `teams/plugin.yaml` | YAML definition for `teams-platform` |
| `teams/summary_writer.py` | Pipeline-facing Teams outbound delivery (meeting-summary writer). |
| `telegram/__init__.py` | Package marker / package-level exports |
| `telegram/adapter.py` | Telegram platform adapter (python-telegram-bot): inbound messages/media/commands, outbound replies. |
| `telegram/adapter_hint.py` | Telegram system-prompt platform hint (``PlatformEntry.platform_hint``), kept out of the adapter facade. |
| `telegram/dashboard_card.py` | Telegram's Channels-page card (Desktop + web dashboard): the PlatformEntry ``dashboard_*`` / ``docs_url`` fields register() spreads in. Kept apart from adapter.py, which is over its size cap. |
| `telegram/gateway_env.py` | Telegram env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `telegram/inline_picker.py` | Telegram inline command picker — searchable access to EVERY command/skill. |
| `telegram/plugin.yaml` | YAML definition for `telegram-platform` |
| `telegram/telegram_context.py` | Telegram group addressing helpers, kept out of the adapter facade. |
| `telegram/telegram_entities.py` | Telegram ``text_link`` expansion, kept out of the adapter facade. |
| `telegram/telegram_held_inbound.py` | Telegram held-inbound queue: events PTB already acked that cannot dispatch yet are held, redispatched on reconnect, and handed to the adapter that replaces this one (#132829). |
| `telegram/telegram_ids.py` | Helpers for Telegram Bot API chat identifiers: a ``chat_id`` is a numeric ID (int) or an ``@username`` string for public channels/groups; a bare ``int(chat_id)`` crashes on the username form. |
| `telegram/telegram_network.py` | Telegram network helpers: a hostname-preserving fallback transport (Host + SNI stay api.telegram.org while TCP retries known IPv4 literals) plus DoH-based IP discovery. |
| `telegram/telegram_topic_routing.py` | Route a client-created Telegram DM topic's thread-less opener into that topic (#136567). |
| `telegram/telegram_topic_transfer.py` | Opt-in root-DM -> fresh topic transfer for Telegram ``/topic`` mode (``dm_topic_auto_transfer``). |
| `telegram/update_admission.py` | Telegram admission before every PTB handler group, including native plugins. |
| `wecom/__init__.py` | Package marker / package-level exports |
| `wecom/adapter.py` | WeCom (Enterprise WeChat) AI Bot adapter over the ``openws`` WebSocket gateway. Streaming lives in ``streaming.py``, media in ``media.py``, per-chat send queue in ``send_queue.py``. Config (``platforms.wecom.extra``): `… |
| `wecom/callback_adapter.py` | WeCom callback-mode adapter (self-built apps): decrypt POSTed XML, queue for the agent, ack at once; reply later via proactive ``message/send``. Multiple apps are scoped by ``corp_id:user_id``. |
| `wecom/gateway_env.py` | WeCom (bot + callback sibling) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `wecom/media.py` | WeCom media mixin: inbound attachment caching; outbound chunked ``aibot_upload_media_*`` upload then native send (image/video/voice/file). |
| `wecom/plugin.yaml` | YAML definition for `wecom-platform` |
| `wecom/send_queue.py` | Per-chat FIFO send queues (OpenClaw chat-queue.ts) + token bucket for WeCom's 30 msgs/min/chat limit (846607). Two lanes per chat: normal, and a control lane (approval prompts, finalize frames) backed by a reserved toke… |
| `wecom/streaming.py` | WeCom native streaming mixin (``msgtype: stream`` via aibot_respond_msg): per-turn state, per-req_id ack tracking (official replyStreamNonBlocking semantics), keep-alive heartbeat, finalize clock fallback. |
| `wecom/wecom_crypto.py` | WeCom callback-mode AES-CBC crypto, wire-compatible with Tencent's official ``WXBizMsgCrypt`` SDK. |
| `weixin/__init__.py` | Package marker / package-level exports |
| `weixin/adapter.py` | Weixin (WeChat personal account) adapter over Tencent's iLink Bot API. Long-poll ``getupdates`` drives inbound delivery; every outbound reply must echo the peer's latest ``context_token``; media moves through an AES-128… |
| `weixin/gateway_env.py` | Weixin (personal WeChat via iLink Bot API) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `weixin/plugin.yaml` | YAML definition for `weixin-platform` |
| `whatsapp/__init__.py` | Package marker / package-level exports |
| `whatsapp/adapter.py` | WhatsApp platform adapter (Baileys bridge): a Node.js bridge process runs the WhatsApp Web client; messages are polled over a local HTTP API and responses are posted back through it. |
| `whatsapp/bridge_ownership.py` | Non-destructive bridge allocation for multiplexed secondary profiles. |
| `whatsapp/gateway_env.py` | WhatsApp (Baileys bridge) env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `whatsapp/plugin.yaml` | YAML definition for `whatsapp-platform` |
| `whatsapp_cloud/__init__.py` | Package marker / package-level exports |
| `whatsapp_cloud/adapter.py` | WhatsApp Cloud API adapter — official Meta WhatsApp Business Platform (Graph API + aiohttp webhook). Complements the Baileys bridge plugin; both share gating / mention / formatting behavior via ``WhatsAppBehaviorMixin``. |
| `whatsapp_cloud/gateway_env.py` | WhatsApp Cloud API env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `whatsapp_cloud/plugin.yaml` | YAML definition for `whatsapp_cloud-platform` |
| `whatsapp_cloud/setup_wizard.py` | Interactive setup wizard for the WhatsApp Cloud API adapter: the 6 Meta credentials + recipient allowlist, an auto-generated verify token, and exact follow-up instructions for what can't happen inside the wizard process… |
| `yuanbao/__init__.py` | Absolute import (not ``from .adapter``): the plugin loader executes this package as ``hermes_plugins.platforms__yuanbao``; importing the adapter by its canonical module name keeps ONE ``YuanbaoAdapter`` class object, so… |
| `yuanbao/adapter.py` | Yuanbao platform adapter: WebSocket gateway client (AUTH_BIND, ping/pong heartbeat, reconnect), inbound middleware pipeline (T05 push → MessageEvent) and outbound sender (T06 text/media). |
| `yuanbao/gateway_env.py` | Yuanbao env -> gateway config bridge (``PlatformEntry.env_overrides``). |
| `yuanbao/plugin.yaml` | YAML definition for `yuanbao-platform` |
| `yuanbao/register.py` | Yuanbao plugin registration: setup row, configured check, standalone sender, ``register``. |
| `yuanbao/yuanbao_media.py` | yuanbao_media.py — 元宝平台媒体处理：COS 上传、URL 下载（SSRF 防护）、TIM 媒体消息体。 移植自 TypeScript 版 media.ts（yuanbao-openclaw-plugin），用 httpx 替代 cos-nodejs-sdk-v5。 |
| `yuanbao/yuanbao_proto.py` | yuanbao_proto.py - Yuanbao WebSocket 协议编解码（手写 protobuf wire-format，不依赖 google.protobuf） |
| `yuanbao/yuanbao_sticker.py` | Yuanbao sticker (TIMFaceElem) support. Ported from yuanbao-openclaw-plugin/src/sticker/. |

## `plugins/security-guidance/`

| File | What it does |
|---|---|
| `LICENSE` | Software license text |
| `NOTICE` | Data/support file |
| `README.md` | security-guidance |
| `__init__.py` | security-guidance plugin — fast pattern-matched security warnings on file writes. |
| `patterns.py` | Regex-based security pattern definitions for the security-guidance plugin. |
| `plugin.yaml` | Append security warnings to file-write tool results when the new content contains known-dangerous patterns (pickle.load, yaml.load, eval(, os.system, dangerouslySetInnerHTML, verify=False, ECB, XXE, GitHub Actions injec… |

## `plugins/teams_pipeline/`

| File | What it does |
|---|---|
| `__init__.py` | Teams meeting pipeline plugin. |
| `cli.py` | CLI commands for the Teams meeting pipeline plugin. |
| `meetings.py` | Graph-backed Teams meeting helpers for the plugin runtime. |
| `models.py` | Normalized models for the Teams meeting pipeline plugin. |
| `pipeline.py` | Pipeline orchestration for Microsoft Teams meeting summaries. |
| `plugin.yaml` | Microsoft Teams meeting pipeline plugin with durable runtime state and operator CLI flows for Graph-backed transcript-first meeting summaries. |
| `runtime.py` | Gateway runtime wiring for the Teams meeting pipeline plugin. |
| `store.py` | Durable local state for the Teams pipeline plugin. |
| `subscriptions.py` | Microsoft Graph subscription helpers for the Teams pipeline plugin. |

## `plugins/video_gen/`

| File | What it does |
|---|---|
| `deepinfra/__init__.py` | DeepInfra video generation backend. |
| `deepinfra/plugin.yaml` | DeepInfra video generation (text-to-video & image-to-video) via the OpenAI-compatible /v1/openai/videos endpoint. Catalog discovered live from api.deepinfra.com. |
| `fal/__init__.py` | FAL.ai video generation backend. |
| `fal/plugin.yaml` | FAL.ai video generation backend. Multi-model — Veo 3.1, Kling, Pixverse — covering text-to-video and image-to-video via fal_client's queue API. |
| `openrouter/__init__.py` | OpenRouter video generation backend. |
| `openrouter/plugin.yaml` | OpenRouter video generation backend. Every generative model on the /api/v1/videos API (Veo, Sora, Kling, Seedance, Wan, Hailuo, Grok Imagine, FLUX Video, …) — text-to-video, image-to-video and reference-to-video; catalo… |
| `xai/__init__.py` | xAI Grok-Imagine video generation backend. |
| `xai/plugin.yaml` | xAI Grok Imagine video generation backend. Supports text-to-video, image-to-video, reference-to-video, video editing, video extension, and stored public URLs via the xAI async videos API. |

## `plugins/web/`

| File | What it does |
|---|---|
| `__init__.py` | Bundled web search providers: plugins/web/<name>/{plugin.yaml, __init__.py, provider.py} (image_gen plugin layout). They auto-load via kind: backend and register via ctx.register_web_search_provider() into agent.web_sea… |
| `_common.py` | Shared plumbing for the bundled web-search provider plugins. |
| `brave_free/__init__.py` | Brave Search (free tier) plugin — bundled, auto-loaded. |
| `brave_free/plugin.yaml` | Brave Search (free tier) — web search via Brave's Data-for-Search API. Requires BRAVE_SEARCH_API_KEY (free signup at https://brave.com/search/api/, 2k queries/month). |
| `brave_free/provider.py` | Brave Search (free-tier Data-for-Search API) — search only, 2,000 queries/month. |
| `ddgs/__init__.py` | DuckDuckGo search plugin (``ddgs`` package, optional dep) — bundled, auto-loaded. |
| `ddgs/_search_worker.py` | DDGS search child-process entrypoint, run as ``python plugins/web/ddgs/_search_worker.py``. |
| `ddgs/plugin.yaml` | DuckDuckGo web search via the ddgs Python package — no API key required. Install with `pip install ddgs`. |
| `ddgs/provider.py` | DuckDuckGo search via the optional ``ddgs`` package (search only, no key). ``is_available()`` reflects package importability; the plugin registers either way so ``hermes tools`` can offer to install it. Isolation: ``ddg… |
| `exa/__init__.py` | Exa web search + extract plugin — bundled, auto-loaded (sync SDK; dispatcher wraps async callers). |
| `exa/plugin.yaml` | Exa web search and content extraction. Requires EXA_API_KEY — sign up at https://exa.ai. |
| `exa/provider.py` | Exa web search + content extraction via the ``exa-py`` SDK (lazy-installed). |
| `firecrawl/__init__.py` | Firecrawl web search + extract plugin — bundled, auto-loaded. |
| `firecrawl/plugin.yaml` | Firecrawl web search + content extraction. Supports keyless cloud, direct API, and Nous-hosted tool-gateway routing for subscribers. |
| `firecrawl/provider.py` | Firecrawl web search + extract provider (direct SDK, keyless cloud, or Nous tool-gateway). |
| `keenable/__init__.py` | Keenable web search + extract plugin — bundled, auto-loaded; keyless-ring member. |
| `keenable/plugin.yaml` | Keenable web search + page fetch (independent web index for AI apps). Works keyless on Keenable's free tier as part of the default rotation; set KEENABLE_API_KEY for higher limits — https://keenable.ai. |
| `keenable/provider.py` | Keenable (https://keenable.ai) web search + fetch — keyless-ring member. |
| `keyless_mcp.py` | Keyless web search/extract via public free-tier endpoints (Exa, Parallel, Firecrawl, Keenable). Resolved strictly LAST — after every keyed backend, the managed gateway, ddgs and custom plugin providers — so it never pre… |
| `openai_native/__init__.py` | OpenAI native web search plugin — bundled, auto-loaded. |
| `openai_native/plugin.yaml` | OpenAI native web search — declares the Responses API server-side ``web_search`` built-in instead of running a client-side search. Requires the Codex Responses transport plus openai-codex OAuth (``hermes auth add openai… |
| `openai_native/provider.py` | OpenAI native web search — declares the Responses API server-side ``web_search`` built-in. |
| `parallel/__init__.py` | Parallel.ai web search + extract plugin — bundled, auto-loaded; async-native ``extract``. |
| `parallel/plugin.yaml` | Parallel.ai web search + content extraction. Search returns objective-tuned results; extract uses the async SDK for parallel page fetches. Requires PARALLEL_API_KEY — sign up at https://parallel.ai. |
| `parallel/provider.py` | Parallel.ai web search (sync ``Parallel`` SDK) + async extract (``AsyncParallel``). |
| `perplexity/__init__.py` | Perplexity web search + snippets plugin — bundled, auto-loaded. |
| `perplexity/plugin.yaml` | Perplexity Search API web search and query-relevant page snippets. Requires PERPLEXITY_API_KEY — get one at https://www.perplexity.ai/account/api. |
| `perplexity/provider.py` | Perplexity web search + page snippets — plugin form. |
| `searxng/__init__.py` | SearXNG search-only plugin — bundled, auto-loaded (``SEARXNG_URL``). |
| `searxng/plugin.yaml` | SearXNG web search — free, self-hosted, privacy-respecting metasearch engine. Requires SEARXNG_URL pointing at your instance. |
| `searxng/provider.py` | SearXNG search via a user-hosted instance (``/search?format=json``). |
| `tavily/__init__.py` | Tavily web search + extract plugin — bundled, auto-loaded. |
| `tavily/plugin.yaml` | Tavily web search + extract. Opt-in keyless via hermes tools; set TAVILY_API_KEY for higher limits — https://app.tavily.com/home. |
| `tavily/provider.py` | Tavily web search + content extraction (``/search``, ``/extract``; sync httpx). |
| `xai/__init__.py` | xAI web search plugin — bundled, auto-loaded. |
| `xai/plugin.yaml` | xAI Web Search — search the web via Grok's agentic web_search tool (Responses API). Requires xAI Grok OAuth (via `hermes auth`) or XAI_API_KEY (https://x.ai). |
| `xai/provider.py` | xAI Web Search — search-only provider backed by Grok's server-side ``web_search`` tool on the Responses API (https://docs.x.ai/developers/tools/web-search); Grok is asked for structured JSON so rows match every other He… |
