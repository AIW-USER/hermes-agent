# File reference: `nix`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `checks.nix` | nix/checks.nix — Build-time verification tests |
| `configMergeScript.nix` | nix/configMergeScript.nix — Deep-merge Nix settings into existing config.yaml |
| `desktop.nix` | nix/desktop.nix — Hermes Desktop (Electron) app build + wrapper |
| `devShell.nix` | nix/devShell.nix — Dev shell that delegates setup to each package |
| `hermes-agent.nix` | nix/hermes-agent.nix — Overridable Hermes Agent package |
| `homeManagerModules.nix` | nix/homeManagerModules.nix — the Home Manager module for hermes-agent |
| `icons.nix` | Run the shared generator offline; generated assets are not tracked in git. |
| `lib.nix` | nix/lib.nix — Shared helpers for nix stuff |
| `moduleCommon.nix` | nix/moduleCommon.nix — the code that the NixOS and Home Manager modules share |
| `nixosModules.nix` | nix/nixosModules.nix — the NixOS module for hermes-agent |
| `node-gyp-11-4-0-package-lock.json` | JSON data/configuration |
| `node-gyp-11-4-0.nix` | Nix expression |
| `npm-pinned.nix` | Nix expression |
| `overlays.nix` | nix/overlays.nix — Expose pkgs.hermes-agent for external NixOS configs |
| `packages.nix` | nix/packages.nix — Hermes Agent package built with uv2nix |
| `pm-packages.nix` | Nix expression |
| `pm-runtime.nix` | PM's dependency graph must remain independent of the application closure. |
| `python.nix` | nix/python.nix — uv2nix virtual environment builder |
| `pythonLock.nix` | Nix uses the Python family pinned by PM, not a second version constant. |
| `sandbox.nix` | Nix expression |
| `tests/agent-references.py` | Check the shipped Nix agent, not a reconstruction of its assembly recipe. |
| `tests/desktop-backend.py` | Launch the packaged desktop with a competing mutable install. |
| `tui.nix` | Self-contained Hermes TUI, compiled by the same recipe as npm. |
| `web.nix` | Dashboard compilation consumes prepared icons; no npm lifecycle preparation. |
| `webapp.nix` | The Webapp: the Desktop renderer built for a browser. The npm hook has already installed the locked workspace, so it compiles there, with no private workspace and no Electron. |
