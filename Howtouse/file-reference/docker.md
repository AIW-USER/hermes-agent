# File reference: `docker`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `SOUL.md` | You are Hermes Agent, built by Nous Research. Be direct: match the length of your reply to the weight of the ask — a one-line question gets a one-line answer, and finished work gets a short report of what changed, what'… |
| `build_agent.py` | Supply the image's fixed runtime paths to the shared offline assembler. |
| `cont-init.d/015-supervise-perms` | shellcheck shell=sh Make supervise/ trees for ALL declared s6 services queryable and controllable by the unprivileged hermes user (UID 10000). |
| `cont-init.d/02-reconcile-profiles` | shellcheck shell=sh Container-boot reconciliation of per-profile gateway s6 services. |
| `entrypoint-dispatch.sh` | shellcheck shell=sh Entry-point dispatcher for runtimes that may or may not give the image ownership of PID 1. |
| `entrypoint.sh` | s6-overlay shim. The real logic lives in docker/stage2-hook.sh, invoked by /etc/cont-init.d/01-hermes-setup (installed by the Dockerfile). This file exists so external references to docker/entrypoint.sh still work, |
| `hermes-exec-shim.sh` | shellcheck shell=sh /opt/hermes/bin/hermes — `docker exec` privilege-drop shim. |
| `main-wrapper.sh` | shellcheck shell=sh /opt/hermes/docker/main-wrapper.sh — wraps the container's CMD with the same argument-routing logic the pre-s6 entrypoint.sh used. Runs |
| `s6-rc.d/dashboard/dependencies.d/base` | Data/support file |
| `s6-rc.d/dashboard/finish` | shellcheck shell=sh Dashboard finish script. Companion to ./run. |
| `s6-rc.d/dashboard/run` | shellcheck shell=sh Dashboard service. Always declared so s6 has a supervised slot; if HERMES_DASHBOARD isn't truthy the run script exits cleanly and the |
| `s6-rc.d/dashboard/type` | Data/support file |
| `s6-rc.d/main-hermes/dependencies.d/base` | Data/support file |
| `s6-rc.d/main-hermes/run` | shellcheck shell=sh Main hermes service. |
| `s6-rc.d/main-hermes/type` | Data/support file |
| `s6-rc.d/user/contents.d/dashboard` | Data/support file |
| `s6-rc.d/user/contents.d/main-hermes` | Data/support file |
| `sandbox-desktop-smoke.sh` | Smoke test for the sandbox desktop image: what a terminal backend needs from it. |
| `sandbox-desktop.Dockerfile` | Docker image build recipe |
| `stage2-hook.sh` | s6-overlay stage2 hook — runs as root after the supervision tree is up but before user services start. Handles UID/GID remap, volume chown, config seeding, and skills sync. |
| `tini-shim.sh` | shellcheck shell=sh /usr/bin/tini — compatibility shim for legacy orchestration templates. |
