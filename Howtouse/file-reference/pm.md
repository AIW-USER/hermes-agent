# File reference: `pm`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | pm/ — dependencies and Hermes environments |
| `__init__.py` | pm: the hermes package system. |
| `_marker_eval.py` | Evaluate one PEP 508 marker inside PM's runtime: `_marker_eval.py MARKER ENV_JSON`. |
| `_uv.py` | Pinned tool acquisition for PM's private Python engine; never worker API. |
| `_venv_entry.py` | Run code inside a venv on another interpreter: ``python -S _venv_entry.py SITE ARGS...``. |
| `artifact-mirror.json` | JSON object with keys `origin`, `prefix` |
| `artifact_mirror.py` | Public, content-addressed copies of reviewed binary inputs. |
| `build_env.py` | Build and inspect explicit Python dependency environments through PM. |
| `build_operations.py` | Build/CI operations with caller-owned inputs, independent of live selection. |
| `cli.py` | hermes pm: lock / install / repair / env / doctor / gc / bundle. |
| `client.py` | Synchronous PM mutations in an isolated interpreter, never the app's imports. |
| `defaults.py` | Optional packages the default install carries, and the user's opt-outs. |
| `download_state.py` | Cross-process ownership of resumable partials and their GC boundary. |
| `downloader.py` | Resumable, hash-verified, multi-connection downloads. |
| `environment.py` | PM's private Python engine: tool routing, isolation and command execution. |
| `environments.py` | Dependency-environment layout: where a project's venv generations live, which one is selected, and the interpreter inside any venv. Shared by PM and pre-import launchers. |
| `environments_adopt.py` | Adopt a newly selected dependency generation inside a running process. |
| `extras.py` | Extras: the runtime features of the python venv. |
| `features.py` | The enabled-features file: the exact extras the install carries. |
| `filesystem.py` | Stdlib-only filesystem primitives PM needs before it can replace the caller's interpreter. |
| `index_config.py` | Forward the user's package-index and transport configuration into uv. |
| `install.py` | ensure(): make the installed state match the lockfile for a package, and hand back its composed environment. |
| `install_states.py` | Reclaim per-checkout dependency state whose checkout is gone. |
| `launch.py` | CLI entry after the isolated interpreter has been selected. |
| `libatomic.py` | Install the host libatomic package required by official Linux Node. |
| `lock.json` | JSON object with keys `packages`, `schema` |
| `lock.py` | The lockfile (versions + hashes, machine-written) and the installed-state file (what is actually on this machine). |
| `native_build.py` | Native compiler environment for dependency builds from a source checkout. |
| `network.py` | Bounded retries for PM-owned, idempotent network operations. |
| `operations.py` | Python dependency operations executed by the isolated package manager. |
| `package.py` | Package definitions: what a package IS. No versions, no hashes — those live in lock.json, written by `pm lock`. |
| `packages.py` | Package definitions for the tools hermes manages. Versions and hashes live in pm/lock.json (written by `pm lock`), never here. |
| `paths.py` | Where the store, lockfile, and installed-state file live. |
| `pip_check.py` | Which `uv pip check` incompatibilities the project's lock resolved on purpose. |
| `plugin_declarations.py` | Read plugin build declarations without importing CLI configuration or plugin code. |
| `plugin_eviction.py` | Keep an update alive when an enabled plugin no longer fits the new core. |
| `plugin_inputs.py` | What a venv sync or currency probe should take as its plugin members. |
| `plugins_state.py` | Read every profile's enabled plugins in config order for the shared union. |
| `progress.py` | One output policy for long child processes: verbose in CI, contained elsewhere. |
| `publication.py` | Worker-local plugin selection and code publication. No application dependency imports. |
| `pyproject.toml` | Python project metadata and dependencies |
| `receipt.py` | pm sync receipts: the machine-readable surface for venv operations. |
| `recovery.py` | Restore dependency generations without importing the damaged environment. |
| `registry.py` | Package registry and dependency walk. |
| `runtime.py` | The dependency manager's runtime, independent of the application graph. |
| `runtime_stage.py` | One locked dependency builder for PM workers and packaged runtimes. |
| `security_packages.py` | Optional security executables. Acquisition and publication belong to PM. |
| `shell.py` | pm.shell(): the one place Hermes resolves the shell it runs commands with. |
| `store.py` | Machine-wide byte store: download, verify, extract, publish atomically. |
| `termux_libs.py` | Termux pool pins: the runtime-lib table and lock.json's bionic rows. |
| `termux_runtime_libs.json` | JSON object with keys `_comment`, `licenses`, `libs` |
| `testenv.py` | The isolated environment a checkout's test suite runs under. |
| `update.py` | hermes pm update: resolve the latest versions and re-pin the lockfile. |
| `user_facing.py` | The terminal's PATH: the user's own tools first, Hermes's after them. |
| `uv.lock` | uv dependency lock file |
| `uv_cache_prune.py` | Exact-to-lock pruning for uv caches. |
| `worker.py` | One stdlib JSON-line PM request per isolated process. |
| `worker_operations.py` | Import-light routing and prerequisite policy for the private PM worker. |
| `workspace.py` | Resolve core plus plugin requirements in a writable build snapshot. |
