# File reference: `.github`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `CODEOWNERS` | Paths that need a hermes-agent-core approval before merge. This replaces the ``ci-reviewed`` label gate: GitHub requests the review and enforces it (ruleset: "Require review from Code Owners"), so CI no longer needs to |
| `ISSUE_TEMPLATE/bug_report.yml` | Report a bug — something that's broken, crashes, or behaves incorrectly. |
| `ISSUE_TEMPLATE/config.yml` | YAML configuration/data |
| `ISSUE_TEMPLATE/feature_request.yml` | Suggest a new feature or improvement. |
| `ISSUE_TEMPLATE/setup_help.yml` | Having trouble installing or configuring Hermes? Ask here. |
| `PULL_REQUEST_TEMPLATE.md` | What does this PR do? |
| `actionlint.yaml` | actionlint knows only GitHub-hosted runner labels. An org admin names the larger runners. Each one therefore reads as "unknown runner label" and hides |
| `actions/check-clean-worktree/action.yml` | YAML definition for `Check the checkout is clean` |
| `actions/desktop-build-cache/action.yml` | Transport reusable dependency candidates; preparation always performs owner admission. |
| `actions/detect-changes/action.yml` | YAML definition for `Detect affected areas` |
| `actions/e2e-screen-record/action.yml` | YAML definition for `E2E screen recording` |
| `actions/get-app-token/action.yml` | YAML definition for `Get GitHub App Token` |
| `actions/nix-setup/action.yml` | Install Nix and configure Cachix binary cache |
| `actions/plugin-validate/action.yml` | YAML definition for `Hermes Plugin Validate` |
| `actions/retry/action.yml` | YAML definition for `Retry a flaky command` |
| `actions/setup-pm/README.md` | Locked CI toolchains |
| `actions/setup-pm/action.yml` | Install Python/uv and Node/npm from pm/lock.json; cache tools and dependency downloads. |
| `actions/setup-pm/prune/action.yml` | Register lock-exact pruning before the enclosing cache action saves. |
| `actions/setup-pm/prune/index.mjs` | Composite actions cannot register a post step. Called after actions/cache, this action's post runs first, pruning the cache just before it is saved. |
| `actions/setup-windows-build-deps/action.yml` | Prepare MSVC, SDK, Clang, Rust and static OpenSSL through the shared PowerShell installer. |
| `blob-size-allowlist.txt` | Plain-text file |
| `dependabot.yml` | Dependabot configuration for hermes-agent. Deliberately scoped to github-actions only. |
| `scripts/run-workspace-checks.mjs` | Run every workspace check at the same time and report all failures. The unit of work is a CHECK, and not a workspace. A package that declares `check:*` sub-scripts gives one unit for each sub-script. A package with a |
| `workflows/archive-inputs.yml` | YAML definition for `Archive pinned PM inputs` |
| `workflows/blob-size-check.yml` | YAML definition for `Blob Size Check` |
| `workflows/bootstrap-installer-build.yml` | YAML definition for `Bootstrap installer build` |
| `workflows/bootstrap-installer.yml` | YAML definition for `Bootstrap installer` |
| `workflows/canary-release.yml` | YAML definition for `Canary Release` |
| `workflows/case-collision-check.yml` | YAML definition for `Case Collision Check` |
| `workflows/catalog-tests.yml` | YAML definition for `Catalog tests` |
| `workflows/ci-review-comment.yml` | YAML definition for `CI review comment` |
| `workflows/ci.yaml` | YAML definition for `CI` |
| `workflows/contributor-check.yml` | YAML definition for `Contributor Attribution Check` |
| `workflows/deploy-site.yml` | YAML definition for `Deploy Site` |
| `workflows/desktop-bundle-smoke.yml` | YAML definition for `Desktop bundle smoke` |
| `workflows/desktop-bundled-release.yml` | YAML definition for `Desktop Bundled Release` |
| `workflows/docker-lint.yml` | YAML definition for `Docker / shell lint` |
| `workflows/docker.yml` | YAML definition for `Docker Build, Test, and Publish` |
| `workflows/docs-search-monitor.yml` | YAML definition for `Docs Search Monitor` |
| `workflows/docs-site-checks.yml` | YAML definition for `Docs Site Checks` |
| `workflows/e2e-desktop-core.yml` | YAML definition for `E2E Desktop core` |
| `workflows/e2e-desktop-update.yml` | YAML definition for `E2E Desktop update` |
| `workflows/e2e-desktop.yml` | YAML definition for `E2E Desktop` |
| `workflows/history-check.yml` | YAML definition for `History Check` |
| `workflows/icons-freshness-check.yml` | YAML definition for `Icon Assets Freshness` |
| `workflows/infographic-check.yml` | YAML definition for `Infographic Check` |
| `workflows/install-e2e-macos-run.yml` | Reusable runner for ONE macOS install/update combination. Two driver arms, one runs per dispatch (the other natively skips): |
| `workflows/install-e2e-red.yml` | YAML definition for `Install & Update E2E red tracker` |
| `workflows/install-e2e-run.yml` | YAML definition for `Install & Update E2E (reusable)` |
| `workflows/install-e2e-windows-run.yml` | Reusable runner for ONE Windows install/update combination. One job, two orthogonal axes: tests/install/windows-e2e.ps1 dispatches its |
| `workflows/install-e2e.yml` | YAML definition for `Install & Update E2E` |
| `workflows/js-autofix.yml` | YAML definition for `auto-fix lint issues & formatting` |
| `workflows/js-tests.yml` | .github/workflows/js-tests.yml |
| `workflows/label-rerun.yml` | YAML definition for `Label rerun` |
| `workflows/lazy-deps-guard.yml` | YAML definition for `Lazy-deps import guard` |
| `workflows/lint.yml` | YAML definition for `Lint (ruff + ty)` |
| `workflows/live-providers.yml` | YAML definition for `Live provider canaries` |
| `workflows/lockfile-diff.yml` | YAML definition for `Lockfile diff` |
| `workflows/nix.yml` | YAML definition for `Nix flake check` |
| `workflows/osv-scanner.yml` | YAML definition for `OSV-Scanner` |
| `workflows/plugin-catalog-ci.yml` | YAML definition for `Plugin Catalog CI` |
| `workflows/pm-bundle.yml` | YAML definition for `PM Bundle` |
| `workflows/profile-artifact-check.yml` | YAML definition for `Profile Artifact Boundary` |
| `workflows/prompt-surface-diff.yml` | YAML definition for `Prompt surface diff` |
| `workflows/remote-backends.yml` | YAML definition for `Remote terminal backends` |
| `workflows/rust-tests.yml` | .github/workflows/rust-tests.yml |
| `workflows/sandbox-image.yml` | YAML definition for `Sandbox desktop image` |
| `workflows/skills-index-freshness.yml` | YAML definition for `Skills Index Freshness Check` |
| `workflows/skills-index.yml` | YAML definition for `Build Skills Index` |
| `workflows/stable-release-publication.yml` | YAML definition for `Stable Release Publication` |
| `workflows/stable-release.yml` | YAML definition for `Stable Release` |
| `workflows/supply-chain-audit.yml` | YAML definition for `Supply Chain Audit` |
| `workflows/termux-verify.yml` | YAML definition for `Termux verification` |
| `workflows/tests-os.yml` | YAML definition for `OS-specific tests` |
| `workflows/tests.yml` | YAML definition for `Tests` |
| `workflows/uv-lockfile-check.yml` | YAML definition for `uv.lock check` |
| `workflows/windows-bundle-sdk.yml` | YAML definition for `Windows bundle SDK` |
| `workflows/windows-desktop-attach-e2e.yml` | YAML definition for `Windows Desktop attach E2E` |
| `workflows/windows-install-update-e2e.yml` | YAML definition for `Windows install + update E2E` |
| `workflows/windows-venv-e2e.yml` | YAML definition for `Windows venv-holder live E2E` |
