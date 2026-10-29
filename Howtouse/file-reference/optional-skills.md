# File reference: `optional-skills`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `optional-skills/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Optional Skills |

## `optional-skills/autonomous-ai-agents/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Optional autonomous AI agent integrations — external coding agent CLIs that can be delegated to for independent coding tasks. |
| `agent-merge-conflict-arbiter/SKILL.md` | Neutral arbiter for merge conflicts between two agents. |
| `antigravity-cli/SKILL.md` | Operate the Antigravity CLI (agy): plugins, auth, sandbox. |
| `antigravity-cli/references/cli-docs.md` | Antigravity CLI docs, condensed |
| `blackbox/SKILL.md` | Delegate coding tasks to the Blackbox AI multi-model CLI. |
| `dynamic-workflow/SKILL.md` | Plan-in-code fan-outs, adversarial verification, waves. |
| `grok/SKILL.md` | Delegate coding to xAI Grok Build CLI (features, PRs). |
| `honcho/SKILL.md` | Configure and troubleshoot Honcho memory for Hermes. |
| `openhands/SKILL.md` | Delegate coding to OpenHands CLI (model-agnostic, LiteLLM). |

## `optional-skills/blockchain/`

| File | What it does |
|---|---|
| `evm/SKILL.md` | Read-only EVM client: wallets, tokens, gas across 8 chains. |
| `evm/scripts/evm_client.py` | evm_client.py — EVM blockchain CLI tool for the Hermes Agent project. Zero external dependencies. Uses stdlib only: urllib, json, argparse, time, os, sys, typing. |
| `hyperliquid/SKILL.md` | Hyperliquid market data, account history, trade review. |
| `hyperliquid/scripts/hyperliquid_client.py` | Hyperliquid CLI Tool for Hermes Agent ------------------------------------- Queries the Hyperliquid info endpoint for market and account data. Uses only Python standard library - no external packages required. |
| `solana/SKILL.md` | Query Solana wallets, tokens, txs, and NFTs in USD. |
| `solana/scripts/solana_client.py` | Solana Blockchain CLI Tool for Hermes Agent -------------------------------------------- Queries the Solana JSON-RPC API and CoinGecko for enriched on-chain data. Uses only Python standard library — no external packages… |

## `optional-skills/communication/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Communication and decision-making frameworks — structured response formats for proposals, trade-off analysis, and stakeholder-ready recommendations. |
| `one-three-one-rule/SKILL.md` | 1-3-1 decision briefs: problem, three options, one pick. |

## `optional-skills/creative/`

| File | What it does |
|---|---|
| `ai-presenter-video/LICENSE` | Software license text |
| `ai-presenter-video/SKILL.md` | Make a verified AI presenter video from script + image. |
| `ai-presenter-video/assets/job.template.json` | JSON object with keys `schema_version`, `job_id`, `state`, `mode`, `input`, `creative` |
| `ai-presenter-video/references/editing.md` | Editing |
| `ai-presenter-video/references/generation.md` | Generation |
| `ai-presenter-video/references/qa-recovery.md` | QA and recovery |
| `ai-presenter-video/scripts/finalize_delivery.sh` | Shell script: `finalize_delivery` |
| `ai-presenter-video/scripts/init_job.py` | Create a non-overwriting presenter-video job from minimal inputs. |
| `ai-presenter-video/scripts/preflight.py` | Validate a presenter-video job and write a machine-readable preflight report. |
| `anatomy/LICENSE.txt` | Plain-text file |
| `anatomy/SKILL.md` | Explain an idea as an interactive isometric machine figure. |
| `anatomy/examples/arcade-cabinet/arcade-cabinet.css` | Stylesheet |
| `anatomy/examples/arcade-cabinet/build.mjs` | JavaScript (ES module): `build` |
| `anatomy/examples/arcade-cabinet/live.js` | JavaScript source: `live` |
| `anatomy/examples/arcade-cabinet/parts.mjs` | Exports `makeParts` |
| `anatomy/examples/arcade-cabinet/screen.mjs` | Exports `SCREEN` |
| `anatomy/examples/desk-computer/build.mjs` | JavaScript (ES module): `build` |
| `anatomy/examples/dial-indicator/build.mjs` | JavaScript (ES module): `build` |
| `anatomy/examples/raptor-engine/build.mjs` | JavaScript (ES module): `build` |
| `anatomy/examples/raptor-engine/live.js` | JavaScript source: `live` |
| `anatomy/examples/raptor-engine/raptor.css` | Stylesheet |
| `anatomy/examples/ripple-tank/build.mjs` | JavaScript (ES module): `build` |
| `anatomy/examples/ripple-tank/live.js` | JavaScript source: `live` |
| `anatomy/examples/ripple-tank/model.mjs` | Exports `WATER`, `GLASS`, `RANGE`, `BEAT`, `SLOPE`, `REACH` … |
| `anatomy/examples/ripple-tank/ripple.css` | Stylesheet |
| `anatomy/examples/spot-plate/art.tsx` | Exports `LiquidArt` |
| `anatomy/examples/spot-plate/drops.ts` | Exports `GlassShape`, `Glint`, `RowShape`, `keyOf`, `rowOf`, `rowsOf` |
| `anatomy/examples/spot-plate/fan.ts` | Exports `BladePose`, `FanPose`, `fanOf` |
| `anatomy/examples/spot-plate/figure.tsx` | Exports `SpotPlateFigure` |
| `anatomy/examples/spot-plate/geometry.ts` | Exports `BASE_ART`, `TRAY_ART`, `DECK_ART`, `BOTTLE_ART`, `LABEL` |
| `anatomy/examples/spot-plate/live.tsx` | Exports `LiquidLive` |
| `anatomy/examples/spot-plate/rig.ts` | Exports `RADII`, `GAPS`, `MERGE`, `MERGE_LEAST`, `MERGE_MOST`, `MERGE_STEP` … |
| `anatomy/examples/spot-plate/spot-plate.css` | Stylesheet |
| `anatomy/examples/test-rig/art.tsx` | Exports `StretchArt` |
| `anatomy/examples/test-rig/figure.tsx` | Exports `TestRigFigure` |
| `anatomy/examples/test-rig/geometry.ts` | Exports `BASE_ART`, `RAIL_ART`, `RIDER`, `PROBE_ART`, `FINGER_ART`, `FRAME_ART` … |
| `anatomy/examples/test-rig/live.tsx` | Exports `StretchLive` |
| `anatomy/examples/test-rig/pose.ts` | Exports `GlassPaths`, `Frame`, `glassOf`, `frameOf` |
| `anatomy/examples/test-rig/rig.ts` | Exports `Pair`, `Tuning`, `Spring`, `Member`, `Pose`, `HALF` … |
| `anatomy/examples/test-rig/stretch.css` | Stylesheet |
| `anatomy/examples/test-rig/view.ts` | Exports `WIDTH`, `HEIGHT`, `AZIMUTH`, `BASE`, `BASE_H`, `FOOT_H` … |
| `anatomy/examples/turning-dial/build.mjs` | Exports `P`, `R`, `T`, `follow`, `tapAt`, `breakAt` … |
| `anatomy/examples/turning-dial/dial.css` | Stylesheet |
| `anatomy/examples/turning-dial/live.js` | JavaScript source: `live` |
| `anatomy/examples/turning-dial/stress.mjs` | Exports `P`, `R`, `T`, `follow`, `poses` |
| `anatomy/kit/audit.mjs` | Exports `body`, `traced`, `lathe`, `solid`, `prism`, `extruded` … |
| `anatomy/kit/canvas-painter.mjs` | Exports `CANVAS2D` |
| `anatomy/kit/gl-shared.mjs` | Exports `GLSL_ISO`, `GLSL_TURN`, `glslPose`, `glCamera`, `glLayer`, `smooth` … |
| `anatomy/kit/gl.mjs` | Exports `GLSL_ISO`, `GLSL_TURN`, `glslPose`, `glCamera`, `glLayer`, `smooth` … |
| `anatomy/kit/iso-kit.mjs` | Exports `AZIMUTH`, `ELEVATION`, `SHADES`, `cameraOf`, `iso`, `towardViewer` … |
| `anatomy/kit/iso-kit.ts` | Exports `Flat`, `Point3`, `Plane`, `Projection`, `Plan`, `SolidPaths` … |
| `anatomy/kit/iso.css` | Stylesheet |
| `anatomy/kit/lathe.mjs` | Exports `dot3`, `add3`, `sub3`, `mul3`, `len3`, `unit3` … |
| `anatomy/kit/react/draw.tsx` | Exports `Solid`, `Line`, `Wire`, `Dots`, `FaceText`, `IsoFigure` … |
| `anatomy/kit/react/live.tsx` | Exports `asksForStillness`, `useStillness`, `useInView`, `Stage`, `useReadout`, `useLoop` … |
| `anatomy/kit/tube.mjs` | Exports `runsOf`, `crossingsOf`, `tubePieces`, `ringsSvg`, `tubeSvg` |
| `anatomy/kit/turn-audit.mjs` | Exports `posed`, `eventsOf`, `orbit`, `orbitReport`, `orbitFailures`, `orbitOrExit` |
| `anatomy/kit/turn-build.mjs` | Exports `roundedPolygon`, `gjk`, `separate`, `turning` |
| `anatomy/kit/turn-fixed.mjs` | JavaScript (ES module): `turn-fixed` |
| `anatomy/kit/turn.mjs` | JavaScript (ES module): `turn` |
| `anatomy/references/3d.md` | 3D: parts that turn in the drawing |
| `anatomy/references/craft.md` | Craft |
| `anatomy/references/kit.md` | Kit API |
| `anatomy/references/motion.md` | Motion and interaction |
| `anatomy/references/react.md` | React and Next.js |
| `anatomy/references/verify.md` | Verify |
| `anatomy/references/walkthrough.md` | Walkthrough: the test rig (Fig 6) |
| `anatomy/references/webgl.md` | WebGL inside the drawing |
| `anatomy/scripts/capture.mjs` | JavaScript (ES module): `capture` |
| `anatomy/scripts/drive.mjs` | JavaScript (ES module): `drive` |
| `anatomy/scripts/inline-kit.mjs` | Exports `kitScript`, `glScript`, `turnScript`, `fixedScript`, `glSharedScript` |
| `anatomy/scripts/line-ends.mjs` | Exports `LINE_ENDS` |
| `anatomy/scripts/lines.mjs` | JavaScript (ES module): `lines` |
| `anatomy/scripts/turn-bench.mjs` | JavaScript (ES module): `turn-bench` |
| `anatomy/scripts/turn-check.mjs` | JavaScript (ES module): `turn-check` |
| `anatomy/scripts/turn-fidelity.mjs` | Exports `identity`, `rounds`, `tubes` |
| `archify/SKILL.md` | Validated interactive HTML diagrams, upstream-maintained. |
| `ascii-art/SKILL.md` | ASCII art: pyfiglet, cowsay, boxes, image-to-ascii. |
| `audiocraft-audio-generation/SKILL.md` | AudioCraft: MusicGen text-to-music, AudioGen text-to-sound. |
| `audiocraft-audio-generation/references/advanced-usage.md` | AudioCraft Advanced Usage Guide |
| `audiocraft-audio-generation/references/troubleshooting.md` | AudioCraft Troubleshooting Guide |
| `auteur/LICENSE` | Software license text |
| `auteur/SKILL.md` | Design and build cinematic, award-level web pages. |
| `auteur/references/ambient-backgrounds.md` | ambient-backgrounds — quiet texture for secondary sections |
| `auteur/references/assets.md` | assets.md — producing visual assets |
| `auteur/references/build.md` | build.md — the standard register |
| `auteur/references/direct.md` | direct.md — the cinematic register |
| `auteur/references/motion.md` | Motion Reference — auteur skill |
| `auteur/references/recon.md` | recon.md — scouting live references and building a moodboard |
| `auteur/references/scroll-cinema.md` | scroll-cinema — Cinematic Scroll Recipes |
| `auteur/references/scroll-flight.md` | scroll-flight — photoreal scroll-scrubbed video ("fly through the world") |
| `auteur/references/system.md` | system.md — the multi-screen register |
| `auteur/references/taste.md` | taste.md — the anti-slop system |
| `auteur/references/verify.md` | verify.md — the acceptance pipeline |
| `auteur/scripts/chromadiff.mjs` | JavaScript (ES module): `chromadiff` |
| `auteur/scripts/moodboard.mjs` | JavaScript (ES module): `moodboard` |
| `auteur/scripts/motionqa.mjs` | JavaScript (ES module): `motionqa` |
| `auteur/scripts/refscout.mjs` | JavaScript (ES module): `refscout` |
| `auteur/scripts/shoot.mjs` | JavaScript (ES module): `shoot` |
| `auteur/scripts/slopscan.mjs` | JavaScript (ES module): `slopscan` |
| `auteur/scripts/source.mjs` | JavaScript (ES module): `source` |
| `auteur/scripts/systemscan.mjs` | JavaScript (ES module): `systemscan` |
| `auteur/templates/CINEMA-QA.md` | CINEMA-QA — <project> |
| `auteur/templates/COMMIT-SHEET.md` | COMMIT-SHEET — <project> |
| `auteur/templates/DESIGN.md` | DESIGN — <project> |
| `auteur/templates/STORYBOARD.md` | STORYBOARD — <project> |
| `auteur/templates/SYSTEM-SHEET.md` | SYSTEM-SHEET — <product> |
| `auteur/templates/scroll-flight-engine.js` | ============================================================================ auteur · scroll-flight-engine.js ---------------------------------------------------------------------------- Portable scroll-scrubbed camera-… |
| `baoyu-article-illustrator/PORT_NOTES.md` | Port Notes — baoyu-article-illustrator |
| `baoyu-article-illustrator/SKILL.md` | Article illustrations: type × style × palette consistency. |
| `baoyu-article-illustrator/prompts/system.md` | Image Specifications |
| `baoyu-article-illustrator/references/palettes/macaron.md` | macaron |
| `baoyu-article-illustrator/references/palettes/mono-ink.md` | mono-ink |
| `baoyu-article-illustrator/references/palettes/neon.md` | neon |
| `baoyu-article-illustrator/references/palettes/warm.md` | warm |
| `baoyu-article-illustrator/references/prompt-construction.md` | Prompt Construction |
| `baoyu-article-illustrator/references/style-presets.md` | Style Presets |
| `baoyu-article-illustrator/references/styles.md` | Style Reference |
| `baoyu-article-illustrator/references/styles/blueprint.md` | blueprint |
| `baoyu-article-illustrator/references/styles/chalkboard.md` | chalkboard |
| `baoyu-article-illustrator/references/styles/editorial.md` | editorial |
| `baoyu-article-illustrator/references/styles/elegant.md` | elegant |
| `baoyu-article-illustrator/references/styles/fantasy-animation.md` | fantasy-animation |
| `baoyu-article-illustrator/references/styles/flat-doodle.md` | flat-doodle |
| `baoyu-article-illustrator/references/styles/flat.md` | flat |
| `baoyu-article-illustrator/references/styles/ink-notes.md` | ink-notes |
| `baoyu-article-illustrator/references/styles/intuition-machine.md` | intuition-machine |
| `baoyu-article-illustrator/references/styles/minimal.md` | minimal |
| `baoyu-article-illustrator/references/styles/nature.md` | nature |
| `baoyu-article-illustrator/references/styles/notion.md` | notion |
| `baoyu-article-illustrator/references/styles/pixel-art.md` | pixel-art |
| `baoyu-article-illustrator/references/styles/playful.md` | playful |
| `baoyu-article-illustrator/references/styles/retro.md` | retro |
| `baoyu-article-illustrator/references/styles/scientific.md` | scientific |
| `baoyu-article-illustrator/references/styles/screen-print.md` | screen-print |
| `baoyu-article-illustrator/references/styles/sketch-notes.md` | sketch-notes |
| `baoyu-article-illustrator/references/styles/sketch.md` | sketch |
| `baoyu-article-illustrator/references/styles/vector-illustration.md` | vector-illustration |
| `baoyu-article-illustrator/references/styles/vintage.md` | vintage |
| `baoyu-article-illustrator/references/styles/warm.md` | warm |
| `baoyu-article-illustrator/references/styles/watercolor.md` | watercolor |
| `baoyu-article-illustrator/references/usage.md` | Usage |
| `baoyu-article-illustrator/references/workflow.md` | Detailed Workflow Procedures |
| `baoyu-comic/PORT_NOTES.md` | Port Notes — baoyu-comic |
| `baoyu-comic/SKILL.md` | Knowledge comics (知识漫画): educational, biography, tutorial. |
| `baoyu-comic/references/analysis-framework.md` | Comic Content Analysis Framework |
| `baoyu-comic/references/art-styles/chalk.md` | chalk |
| `baoyu-comic/references/art-styles/ink-brush.md` | ink-brush |
| `baoyu-comic/references/art-styles/ligne-claire.md` | ligne-claire |
| `baoyu-comic/references/art-styles/manga.md` | manga |
| `baoyu-comic/references/art-styles/minimalist.md` | minimalist |
| `baoyu-comic/references/art-styles/realistic.md` | realistic |
| `baoyu-comic/references/auto-selection.md` | Auto Selection |
| `baoyu-comic/references/base-prompt.md` | Image Specifications |
| `baoyu-comic/references/character-template.md` | Character Definition Template |
| `baoyu-comic/references/layouts/cinematic.md` | cinematic |
| `baoyu-comic/references/layouts/dense.md` | dense |
| `baoyu-comic/references/layouts/four-panel.md` | four-panel |
| `baoyu-comic/references/layouts/mixed.md` | mixed |
| `baoyu-comic/references/layouts/splash.md` | splash |
| `baoyu-comic/references/layouts/standard.md` | standard |
| `baoyu-comic/references/layouts/webtoon.md` | webtoon |
| `baoyu-comic/references/ohmsha-guide.md` | Ohmsha Manga Guide Style |
| `baoyu-comic/references/partial-workflows.md` | Partial Workflows |
| `baoyu-comic/references/presets/concept-story.md` | concept-story |
| `baoyu-comic/references/presets/four-panel.md` | four-panel |
| `baoyu-comic/references/presets/ohmsha.md` | ohmsha |
| `baoyu-comic/references/presets/shoujo.md` | shoujo |
| `baoyu-comic/references/presets/wuxia.md` | wuxia |
| `baoyu-comic/references/storyboard-template.md` | Storyboard Template |
| `baoyu-comic/references/tones/action.md` | action |
| `baoyu-comic/references/tones/dramatic.md` | dramatic |
| `baoyu-comic/references/tones/energetic.md` | energetic |
| `baoyu-comic/references/tones/neutral.md` | neutral |
| `baoyu-comic/references/tones/romantic.md` | romantic |
| `baoyu-comic/references/tones/vintage.md` | vintage |
| `baoyu-comic/references/tones/warm.md` | warm |
| `baoyu-comic/references/workflow.md` | Complete Workflow |
| `brag-slim/SKILL.md` | Launch video from a project or URL, upstream-maintained. |
| `brag/SKILL.md` | Project launch video via Hyperframes, upstream-maintained. |
| `comfyui/SKILL.md` | Generate images, video, and audio via diffusion workflows. |
| `comfyui/references/official-cli.md` | comfy-cli Command Reference |
| `comfyui/references/rest-api.md` | ComfyUI REST + WebSocket API Reference |
| `comfyui/references/template-integrity.md` | ComfyUI Workflow-Template Integrity |
| `comfyui/references/workflow-format.md` | ComfyUI Workflow JSON Format |
| `comfyui/scripts/_common.py` | _common.py — Shared logic for ComfyUI skill scripts. |
| `comfyui/scripts/auto_fix_deps.py` | auto_fix_deps.py — Run check_deps.py, then attempt to install whatever is missing. |
| `comfyui/scripts/check_deps.py` | check_deps.py — Verify a ComfyUI workflow's dependencies (custom nodes, models, embeddings) against a running server. |
| `comfyui/scripts/comfyui_setup.sh` | ComfyUI Setup — Install, launch, and verify using the official comfy-cli. |
| `comfyui/scripts/extract_schema.py` | extract_schema.py — Analyze a ComfyUI API-format workflow and extract controllable parameters. |
| `comfyui/scripts/fetch_logs.py` | fetch_logs.py — Retrieve workflow execution diagnostics from a ComfyUI server. |
| `comfyui/scripts/hardware_check.py` | hardware_check.py — Detect whether this machine can realistically run ComfyUI locally. |
| `comfyui/scripts/health_check.py` | health_check.py — One-stop verification that the ComfyUI environment is ready. |
| `comfyui/scripts/run_batch.py` | run_batch.py — Run a workflow many times, varying parameters per run. |
| `comfyui/scripts/run_workflow.py` | run_workflow.py — Inject parameters into a ComfyUI workflow, submit it, monitor execution, and download outputs. |
| `comfyui/scripts/ws_monitor.py` | ws_monitor.py — Real-time ComfyUI WebSocket monitor. |
| `comfyui/tests/README.md` | ComfyUI Skill Tests |
| `comfyui/tests/conftest.py` | Pytest configuration for the comfyui skill test suite. |
| `comfyui/tests/pytest.ini` | INI configuration |
| `comfyui/tests/test_check_deps.py` | Tests for check_deps.py — focuses on parsing logic that doesn't need a server. |
| `comfyui/tests/test_cloud_integration.py` | Integration tests against the live Comfy Cloud API. |
| `comfyui/tests/test_common.py` | Unit tests for _common.py — pure logic only, no network. |
| `comfyui/tests/test_extract_schema.py` | Tests for extract_schema.py. |
| `comfyui/tests/test_run_workflow.py` | Tests for run_workflow.py — focuses on logic that doesn't require a server. |
| `comfyui/workflows/README.md` | Example Workflows |
| `comfyui/workflows/animatediff_video.json` | JSON object with keys `_comment`, `3`, `4`, `5`, `6`, `7` |
| `comfyui/workflows/flux_dev_txt2img.json` | JSON object with keys `_comment`, `6`, `8`, `9`, `10`, `11` |
| `comfyui/workflows/sd15_txt2img.json` | JSON object with keys `_comment`, `3`, `4`, `5`, `6`, `7` |
| `comfyui/workflows/sdxl_img2img.json` | JSON object with keys `_comment`, `1`, `3`, `4`, `6`, `7` |
| `comfyui/workflows/sdxl_inpaint.json` | JSON object with keys `_comment`, `1`, `2`, `3`, `4`, `6` |
| `comfyui/workflows/sdxl_txt2img.json` | JSON object with keys `_comment`, `3`, `4`, `5`, `6`, `7` |
| `comfyui/workflows/upscale_4x.json` | JSON object with keys `_comment`, `1`, `2`, `3`, `4` |
| `comfyui/workflows/wan_video_t2v.json` | JSON object with keys `_comment`, `6`, `7`, `8`, `37`, `38` |
| `concept-diagrams/SKILL.md` | Generate flat, minimal educational SVG visuals as HTML. |
| `concept-diagrams/examples/apartment-floor-plan-conversion.md` | Apartment Floor Plan: 3 BHK to 4 BHK Conversion |
| `concept-diagrams/examples/automated-password-reset-flow.md` | Automated Password Reset Flow |
| `concept-diagrams/examples/autonomous-llm-research-agent-flow.md` | Autonomous LLM Research Agent Flow |
| `concept-diagrams/examples/banana-journey-tree-to-smoothie.md` | Journey of a Banana: From Tree to Smoothie |
| `concept-diagrams/examples/commercial-aircraft-structure.md` | Commercial Aircraft Structure |
| `concept-diagrams/examples/cpu-ooo-microarchitecture.md` | Out-of-Order CPU Core Microarchitecture |
| `concept-diagrams/examples/electricity-grid-flow.md` | Electricity Grid: Generation to Consumption |
| `concept-diagrams/examples/feature-film-production-pipeline.md` | Feature Film Production Pipeline |
| `concept-diagrams/examples/hospital-emergency-department-flow.md` | Hospital Emergency Department Flow |
| `concept-diagrams/examples/ml-benchmark-grouped-bar-chart.md` | ML Benchmark Grouped Bar Chart with Dual Axis |
| `concept-diagrams/examples/place-order-uml-sequence.md` | Place Order — UML Sequence Diagram |
| `concept-diagrams/examples/smart-city-infrastructure.md` | Smart City Infrastructure |
| `concept-diagrams/examples/smartphone-layer-anatomy.md` | Smartphone Layer Anatomy |
| `concept-diagrams/examples/sn2-reaction-mechanism.md` | SN2 Reaction Mechanism |
| `concept-diagrams/examples/wind-turbine-structure.md` | Modern Onshore Wind Turbine Structure |
| `concept-diagrams/references/dashboard-patterns.md` | Dashboard Patterns |
| `concept-diagrams/references/infrastructure-patterns.md` | Infrastructure Patterns |
| `concept-diagrams/references/physical-shape-cookbook.md` | Physical Shape Cookbook |
| `concept-diagrams/templates/template.html` | HTML page/template |
| `creative-ideation/SKILL.md` | Generate ideas via named methods from creative practice. |
| `creative-ideation/references/anti-slop.md` | Anti-Slop Rules |
| `creative-ideation/references/exercises.md` | Time-Boxed Exercises |
| `creative-ideation/references/full-prompt-library.md` | Constraint Library |
| `creative-ideation/references/heuristics.md` | Routing Heuristics |
| `creative-ideation/references/method-catalog.md` | Method Catalog |
| `creative-ideation/references/methods/affinity-diagrams.md` | Affinity Diagrams |
| `creative-ideation/references/methods/analogy-and-blending.md` | Analogy and Blending |
| `creative-ideation/references/methods/biomimicry.md` | Biomimicry |
| `creative-ideation/references/methods/chance-and-remix.md` | Chance and Remix |
| `creative-ideation/references/methods/compression-progress.md` | Compression Progress |
| `creative-ideation/references/methods/creative-discipline.md` | Creative Discipline |
| `creative-ideation/references/methods/defamiliarization.md` | Defamiliarization |
| `creative-ideation/references/methods/derive-and-mapping.md` | Dérive and Mapping |
| `creative-ideation/references/methods/first-principles.md` | First Principles |
| `creative-ideation/references/methods/jobs-to-be-done.md` | Jobs to Be Done |
| `creative-ideation/references/methods/lateral-provocations.md` | Lateral Provocations |
| `creative-ideation/references/methods/leverage-points.md` | Leverage Points |
| `creative-ideation/references/methods/oblique-strategies.md` | Oblique Strategies |
| `creative-ideation/references/methods/oulipo.md` | OuLiPo |
| `creative-ideation/references/methods/pataphysics.md` | Pataphysics |
| `creative-ideation/references/methods/pattern-languages.md` | Pattern Languages |
| `creative-ideation/references/methods/polya.md` | Pólya's Heuristics |
| `creative-ideation/references/methods/premortem-and-inversion.md` | Premortem and Inversion |
| `creative-ideation/references/methods/scamper.md` | SCAMPER |
| `creative-ideation/references/methods/story-skeletons.md` | Story Skeletons |
| `creative-ideation/references/methods/triz-principles.md` | TRIZ — Theory of Inventive Problem Solving |
| `creative-ideation/references/methods/volume-generation.md` | Volume Generation |
| `draw-your-font/SKILL.md` | Turn a handwriting photo into an installable TTF font. |
| `draw-your-font/references/troubleshooting.md` | Troubleshooting capture & segmentation |
| `dream-loop/LICENSE.txt` | Plain-text file |
| `dream-loop/SKILL.md` | Build stunning 3D scenes via a concept-art fidelity loop. |
| `excalidraw/SKILL.md` | Hand-drawn Excalidraw JSON diagrams (arch, flow, seq). |
| `excalidraw/references/colors.md` | Excalidraw Color Palette |
| `excalidraw/references/dark-mode.md` | Excalidraw Dark Mode Diagrams |
| `excalidraw/references/examples.md` | Excalidraw Diagram Examples |
| `excalidraw/scripts/upload.py` | Upload an .excalidraw file to excalidraw.com and print a shareable URL. |
| `heartmula/SKILL.md` | HeartMuLa: Suno-like song generation from lyrics + tags. |
| `hyperframes/SKILL.md` | Render MP4/WebM videos from HTML compositions. |
| `hyperframes/references/cli.md` | HyperFrames CLI |
| `hyperframes/references/composition.md` | Composition Authoring |
| `hyperframes/references/features.md` | HyperFrames Feature Reference |
| `hyperframes/references/gsap.md` | GSAP for HyperFrames |
| `hyperframes/references/troubleshooting.md` | Troubleshooting |
| `hyperframes/references/website-to-video.md` | Website to Video |
| `hyperframes/scripts/setup.sh` | HyperFrames setup for Hermes. |
| `impeccable/SKILL.md` | Frontend design guidance, upstream-maintained (impeccable). |
| `ip-as-logo/LICENSE` | Software license text |
| `ip-as-logo/SKILL.md` | Design minimal cute IP mascot marks readable at 32px. |
| `kanban-video-orchestrator/SKILL.md` | Plan and run multi-agent video production pipelines. |
| `kanban-video-orchestrator/assets/brief.md.tmpl` | Text template |
| `kanban-video-orchestrator/assets/setup.sh.tmpl` | Text template |
| `kanban-video-orchestrator/assets/soul.md.tmpl` | Text template |
| `kanban-video-orchestrator/references/examples.md` | Worked Examples |
| `kanban-video-orchestrator/references/intake.md` | Intake — Discovery Question Banks |
| `kanban-video-orchestrator/references/kanban-setup.md` | Kanban Setup — Project Bootstrap & Profile Configuration |
| `kanban-video-orchestrator/references/monitoring.md` | Monitoring — Watch the Pipeline + Intervene |
| `kanban-video-orchestrator/references/role-archetypes.md` | Role Archetypes |
| `kanban-video-orchestrator/references/tool-matrix.md` | Tool Matrix — Skills + Toolsets per Role |
| `kanban-video-orchestrator/scripts/bootstrap_pipeline.py` | Bootstrap a video production kanban from a structured plan JSON. |
| `kanban-video-orchestrator/scripts/monitor.py` | Monitor a running video-production kanban. Polls `hermes kanban list` and `events` for a tenant and surfaces issues (stuck tasks, missing heartbeats, repeated retries, dependency deadlocks). |
| `meme-generation/EXAMPLES.md` | Meme Generation Examples |
| `meme-generation/SKILL.md` | Create meme PNGs from templates with Pillow text overlay. |
| `meme-generation/scripts/.gitignore` | Git ignore rules |
| `meme-generation/scripts/generate_meme.py` | Generate a meme image by overlaying text on a template. |
| `meme-generation/scripts/templates.json` | JSON object with keys `this-is-fine`, `drake`, `distracted-boyfriend`, `two-buttons`, `expanding-brain`, `change-my-mind` |
| `mono-color/LICENSE.txt` | Plain-text file |
| `mono-color/SKILL.md` | Generate one- or two-ink editorial print poster images. |
| `mono-color/design-system/carriers.json` | JSON object with keys `schema_version`, `carriers` |
| `mono-color/design-system/colors.json` | JSON object with keys `schema_version`, `substrates`, `defaults`, `inks`, `palettes` |
| `mono-color/design-system/compositions.json` | JSON object with keys `schema_version`, `compositions` |
| `mono-color/design-system/imperfections.json` | JSON object with keys `schema_version`, `selection`, `effects`, `guardrails` |
| `mono-color/design-system/rhythm.json` | JSON object with keys `schema_version`, `default_profile`, `focal_events`, `release_devices`, `optional_unresolved_edges`, `profiles` |
| `mono-color/design-system/typography.json` | JSON object with keys `schema_version`, `selection_rule`, `roles`, `secondary_voice_rules` |
| `mono-color/references/composition.md` | Composition: Decision Flow, Layout Families, Grammar, Rhythm |
| `mono-color/references/quality-gate.md` | Quality Gate: Originality Firewall, Hard Avoids, Inspection |
| `mono-color/references/visual-language.md` | Visual Language: Color, Image Treatment, Typography, Tone |
| `pixel-art/ATTRIBUTION.md` | Attribution |
| `pixel-art/SKILL.md` | Pixel art w/ era palettes (NES, Game Boy, PICO-8). |
| `pixel-art/references/palettes.md` | Named Palettes |
| `pixel-art/scripts/__init__.py` | Package marker / package-level exports |
| `pixel-art/scripts/palettes.py` | Named RGB palettes for pixel_art() and pixel_art_video(). |
| `pixel-art/scripts/pixel_art.py` | Pixel art converter — Floyd-Steinberg dithering with preset or named palette. |
| `pixel-art/scripts/pixel_art_video.py` | Pixel art video — overlay procedural animations onto a source image. |
| `pretext/SKILL.md` | Build creative browser demos with DOM-free text layout. |
| `pretext/references/patterns.md` | Pretext Patterns |
| `pretext/templates/donut-orbit.html` | HTML page/template |
| `pretext/templates/hello-orb-flow.html` | HTML page/template |
| `simple-english/SKILL.md` | Rewrite text to ASD-STE100 Simplified Technical English. |
| `simple-english/references/checklist.md` | Verification checklist |
| `simple-english/references/use-cases.md` | Use cases beyond documentation |
| `sketch/SKILL.md` | Throwaway HTML mockups: 2-3 design variants to compare. |
| `social-media-content-calendar/SKILL.md` | Plan multi-platform social campaigns: briefs to posting. |
| `system-atlas/LICENSE.txt` | Plain-text file |
| `system-atlas/SKILL.md` | Build explorable isometric architecture atlases as HTML. |
| `system-atlas/assets/build.mjs` | Builds <outDir>/SYSTEM.md and <outDir>/atlas.html from data.mjs (same folder). Usage: bun <atlasDir>/build.mjs — outDir = parent of atlasDir by default, or META.outDir |
| `system-atlas/assets/data.example.mjs` | Single source of truth for one atlas. Copy to <atlas home>/data.mjs and edit. Build: bun <atlas home>/build.mjs → writes ../SYSTEM.md and ../atlas.html The atlas home is docs/{system}/atlas/ in repos that commit design… |
| `system-atlas/assets/template.html` | HTML page/template |
| `system-atlas/references/design-language.md` | Atlas design language |
| `system-atlas/references/process-and-lessons.md` | Process and lessons |
| `tldraw-offline/SKILL.md` | Drive and script tldraw offline canvases with an agent. |
| `tldraw-offline/scripts/counter.js` | Interactive Counter — a tldraw offline document script. HOW TO RUN IT ON YOUR MACHINE: 1. Open tldraw offline, create or open a document. |
| `tldraw-offline/scripts/main.js` | tldraw offline — document script (script/main.js) A document script's default export receives a ctx object and runs whenever the document loads (and reruns when you save the script). Contract, verified against |
| `tldraw-offline/scripts/validate_shapes.mjs` | JavaScript (ES module): `validate_shapes` |
| `unreal-mcp/SKILL.md` | Automate Unreal Engine editor scenes, actors, and renders. |
| `unreal-mcp/references/advanced-workflows.md` | Advanced workflows (live-verified on UE 5.8) |
| `unreal-mcp/references/pitfalls.md` | Unreal MCP — Pitfalls & Lessons |
| `unreal-mcp/references/recipes.md` | Unreal MCP — Worked Recipes |
| `unreal-mcp/references/scene-craft.md` | Unreal MCP — Scene-Craft Cheat Sheet |
| `unreal-mcp/references/tool-surface.md` | Unreal MCP — Tool Surface Reference |

## `optional-skills/data-science/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for data science workflows — interactive exploration, Jupyter notebooks, data analysis, and visualization. |
| `jupyter-notebook/SKILL.md` | Iterative Python via live Jupyter kernel (hamelnb). |

## `optional-skills/devops/`

| File | What it does |
|---|---|
| `actual-setup/SKILL.md` | Set up Actual Computer (actual.inc) inference in Hermes. |
| `actual-setup/references/opencode.md` | actual.inc as an OpenCode provider |
| `docker-management/SKILL.md` | Manage Docker containers, images, volumes, and Compose. |
| `hermes-s6-container-supervision/SKILL.md` | Modify or debug s6 services in the Hermes Docker image. |
| `inference-sh-cli/SKILL.md` | Run 150+ AI apps (image, video, LLM) via inference.sh CLI. |
| `inference-sh-cli/references/app-discovery.md` | Discovering Apps |
| `inference-sh-cli/references/authentication.md` | Authentication & Setup |
| `inference-sh-cli/references/cli-reference.md` | CLI Reference |
| `inference-sh-cli/references/running-apps.md` | Running Apps |
| `pinggy-tunnel/SKILL.md` | Zero-install localhost tunnels over SSH via Pinggy. |
| `setup-wizard-generator/SKILL.md` | Generate a bash wizard guiding a human through manual setup. |
| `setup-wizard-generator/templates/template.sh` | A wizard walks a human through a manual procedure, step by step. Generated by the setup-wizard-generator skill. |
| `watchers/SKILL.md` | Poll RSS, JSON APIs, and GitHub with watermark dedup. |
| `watchers/scripts/_watermark.py` | Shared watermark helper used by the three watcher scripts. |
| `watchers/scripts/watch_github.py` | Watch GitHub activity — issues, pulls, releases, or commits — with dedup. |
| `watchers/scripts/watch_http_json.py` | Watch any JSON endpoint that returns a list of objects; dedup by ID field. |
| `watchers/scripts/watch_rss.py` | Watch an RSS 2.0 or Atom feed; print new items to stdout, silent on empty. |

## `optional-skills/dogfood/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Dogfood — Advanced QA & Testing Skills |
| `adversarial-ux-test/SKILL.md` | Roleplay a hostile user to find and triage UX pain points. |

## `optional-skills/email/`

| File | What it does |
|---|---|
| `agentmail/SKILL.md` | Use when an agent needs AgentMail CLI email inboxes. |
| `agentmail/references/core.md` | AgentMail Core |
| `agentmail/references/mcp.md` | AgentMail MCP |
| `agentmail/references/signup.md` | AgentMail Self-Signup |
| `agentmail/references/webhooks.md` | AgentMail Webhooks |
| `agentmail/references/websockets.md` | AgentMail WebSockets |

## `optional-skills/finance/`

| File | What it does |
|---|---|
| `3-statement-model/SKILL.md` | Build integrated IS/BS/CF financial workbooks in Excel. |
| `3-statement-model/references/formatting.md` | Formatting Standards Reference |
| `3-statement-model/references/formulas.md` | Formula Reference |
| `3-statement-model/references/sec-filings.md` | SEC Filings Data Extraction Reference |
| `comps-analysis/SKILL.md` | Build comparable-company valuation workbooks in Excel. |
| `dcf-model/SKILL.md` | Build discounted cash flow valuation workbooks in Excel. |
| `dcf-model/TROUBLESHOOTING.md` | DCF Model Troubleshooting Guide |
| `dcf-model/requirements.txt` | Plain-text file |
| `dcf-model/scripts/validate_dcf.py` | DCF Model Validation Script Validates Excel DCF models for formula errors and common DCF mistakes |
| `excel-author/SKILL.md` | Build auditable financial workbooks headless via openpyxl. |
| `excel-author/scripts/recalc.py` | Recalculate an .xlsx file's formulas using LibreOffice headless. |
| `lbo-model/SKILL.md` | Build leveraged buyout workbooks with IRR/MOIC in Excel. |
| `merger-model/SKILL.md` | Build M&A accretion/dilution workbooks in Excel. |
| `polymarket/SKILL.md` | Query Polymarket: markets, prices, orderbooks, history. |
| `polymarket/references/api-endpoints.md` | Polymarket API Endpoints Reference |
| `polymarket/scripts/polymarket.py` | Polymarket CLI helper — query prediction market data. |
| `pptx-author/SKILL.md` | Build PowerPoint decks headless with python-pptx. |
| `stocks/SKILL.md` | Stock quotes, history, search, compare, crypto via Yahoo. |
| `stocks/scripts/stocks_client.py` | stocks_client.py - Stock market data CLI tool for the Hermes Agent project. Zero external dependencies - Python stdlib only. |

## `optional-skills/gaming/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for setting up, configuring, and managing game servers, modpacks, and gaming-related infrastructure. |
| `minecraft-modpack-server/SKILL.md` | Host modded Minecraft servers (CurseForge, Modrinth). |
| `pokemon-player/SKILL.md` | Play Pokemon via headless emulator + RAM reads. |

## `optional-skills/health/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Health, wellness, and biometric integration skills — BCI wearables, neurofeedback, sleep tracking, and cognitive state monitoring. |
| `fitness-nutrition/SKILL.md` | Workout planning, macros, and body metrics via wger/USDA. |
| `fitness-nutrition/references/FORMULAS.md` | Formulas Reference |
| `fitness-nutrition/scripts/body_calc.py` | body_calc.py — All-in-one fitness calculator. |
| `fitness-nutrition/scripts/nutrition_search.py` | nutrition_search.py — Search USDA FoodData Central for nutrition info. |
| `neuroskill-bci/SKILL.md` | Use live BCI cognitive and mood state from NeuroSkill. |
| `neuroskill-bci/references/api.md` | NeuroSkill WebSocket & HTTP API Reference |
| `neuroskill-bci/references/metrics.md` | NeuroSkill Metric Definitions & Interpretation Guide |
| `neuroskill-bci/references/protocols.md` | NeuroSkill Guided Protocols |

## `optional-skills/mcp/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Markdown document |
| `fastmcp/SKILL.md` | Build, test, and deploy Python MCP servers. |
| `fastmcp/references/fastmcp-cli.md` | FastMCP CLI Reference |
| `fastmcp/scripts/scaffold_fastmcp.py` | Copy a FastMCP starter template into a working file. |
| `fastmcp/templates/api_wrapper.py` | Defines `_headers`, `_request`, `health_check`, `get_resource`, `search_resources` |
| `fastmcp/templates/database_server.py` | Defines `_connect`, `_reject_mutation`, `_validate_table_name`, `list_tables`, `describe_table`, `query` |
| `fastmcp/templates/file_processor.py` | Defines `_read_text`, `summarize_text_file`, `search_text_file`, `read_file_resource` |
| `mcp-oauth-remote-gateway/SKILL.md` | Manual OAuth for remote MCP servers on headless gateways. |
| `mcp-oauth-remote-gateway/references/stripe-mcp-oauth-revocation.md` | Stripe MCP (`mcp.stripe.com`) — recurring OAuth session revocation, fix with a restricted key |
| `mcp-oauth-remote-gateway/scripts/diagnose-oauth-mcp.py` | Diagnose an OAuth-gated remote MCP server's connection state. |
| `mcporter/SKILL.md` | List, auth, and call MCP servers/tools from the terminal. |

## `optional-skills/mlops/`

| File | What it does |
|---|---|
| `accelerate/SKILL.md` | Run PyTorch training across GPUs with minimal changes. |
| `accelerate/references/custom-plugins.md` | Custom Plugins for Accelerate |
| `accelerate/references/megatron-integration.md` | Megatron Integration with Accelerate |
| `accelerate/references/performance.md` | Accelerate Performance Tuning |
| `chroma/SKILL.md` | Embedding database for RAG and semantic search. |
| `chroma/references/integration.md` | Chroma Integration Guide |
| `clip/SKILL.md` | Zero-shot image classification and image-text search. |
| `clip/references/applications.md` | CLIP Applications Guide |
| `evaluation/DESCRIPTION.md` | Model evaluation benchmarks, experiment tracking, data curation, tokenizers, and interpretability tools. |
| `evaluation/evaluating-llms-harness/SKILL.md` | lm-eval-harness: benchmark LLMs (MMLU, GSM8K, etc.). |
| `evaluation/evaluating-llms-harness/references/api-evaluation.md` | API Evaluation |
| `evaluation/evaluating-llms-harness/references/benchmark-guide.md` | Benchmark Guide |
| `evaluation/evaluating-llms-harness/references/custom-tasks.md` | Custom Tasks |
| `evaluation/evaluating-llms-harness/references/distributed-eval.md` | Distributed Evaluation |
| `evaluation/weights-and-biases/SKILL.md` | W&B: log ML experiments, sweeps, model registry, dashboards. |
| `evaluation/weights-and-biases/references/artifacts.md` | Artifacts & Model Registry Guide |
| `evaluation/weights-and-biases/references/integrations.md` | Framework Integrations Guide |
| `evaluation/weights-and-biases/references/sweeps.md` | Comprehensive Hyperparameter Sweeps Guide |
| `faiss/SKILL.md` | Fast vector similarity search at billion scale. |
| `faiss/references/index_types.md` | FAISS Index Types Guide |
| `flash-attention/SKILL.md` | Speed up long-sequence transformer training and inference. |
| `flash-attention/references/benchmarks.md` | Performance Benchmarks |
| `flash-attention/references/transformers-integration.md` | HuggingFace Transformers Integration |
| `guidance/SKILL.md` | Constrain LLM output with grammars; guarantee valid JSON. |
| `guidance/references/backends.md` | Backend Configuration Guide |
| `guidance/references/constraints.md` | Comprehensive Constraint Patterns |
| `guidance/references/examples.md` | Production-Ready Examples |
| `huggingface-tokenizers/SKILL.md` | Fast BPE/WordPiece tokenization and custom vocab training. |
| `huggingface-tokenizers/references/algorithms.md` | Tokenization Algorithms Deep Dive |
| `huggingface-tokenizers/references/integration.md` | Transformers Integration |
| `huggingface-tokenizers/references/pipeline.md` | Tokenization Pipeline Components |
| `huggingface-tokenizers/references/training.md` | Training Custom Tokenizers |
| `inference/DESCRIPTION.md` | Model serving, quantization (GGUF/GPTQ), structured output, inference optimization, and model surgery tools for deploying and running LLMs. |
| `inference/llama-cpp/SKILL.md` | llama.cpp local GGUF inference + HF Hub model discovery. |
| `inference/llama-cpp/references/advanced-usage.md` | GGUF Advanced Usage Guide |
| `inference/llama-cpp/references/hub-discovery.md` | Hugging Face URL Workflows for llama.cpp |
| `inference/llama-cpp/references/optimization.md` | Performance Optimization Guide |
| `inference/llama-cpp/references/quantization.md` | GGUF Quantization Guide |
| `inference/llama-cpp/references/server.md` | Server Deployment Guide |
| `inference/llama-cpp/references/troubleshooting.md` | GGUF Troubleshooting Guide |
| `inference/outlines/SKILL.md` | Outlines: structured JSON/regex/Pydantic LLM generation. |
| `inference/outlines/references/backends.md` | Backend Configuration Guide |
| `inference/outlines/references/examples.md` | Production-Ready Examples |
| `inference/outlines/references/json_generation.md` | Comprehensive JSON Generation Guide |
| `inference/serving-llms-vllm/SKILL.md` | vLLM: high-throughput LLM serving, OpenAI API, quantization. |
| `inference/serving-llms-vllm/references/optimization.md` | Performance Optimization |
| `inference/serving-llms-vllm/references/quantization.md` | Quantization Guide |
| `inference/serving-llms-vllm/references/server-deployment.md` | Server Deployment Patterns |
| `inference/serving-llms-vllm/references/troubleshooting.md` | Troubleshooting Guide |
| `instructor/SKILL.md` | Structured LLM outputs validated with Pydantic. |
| `instructor/references/examples.md` | Real-World Examples |
| `instructor/references/providers.md` | Provider Configuration |
| `instructor/references/validation.md` | Advanced Validation Patterns |
| `lambda-labs/SKILL.md` | On-demand GPU cloud instances for ML training. |
| `lambda-labs/references/advanced-usage.md` | Lambda Labs Advanced Usage Guide |
| `lambda-labs/references/troubleshooting.md` | Lambda Labs Troubleshooting Guide |
| `llava/SKILL.md` | Vision-language chat: VQA, captioning, image dialogue. |
| `llava/references/training.md` | LLaVA Training Guide |
| `modal/SKILL.md` | Serverless GPU cloud for ML jobs and model APIs. |
| `modal/references/advanced-usage.md` | Modal Advanced Usage Guide |
| `modal/references/troubleshooting.md` | Modal Troubleshooting Guide |
| `models/DESCRIPTION.md` | Specific model architectures and tools — image segmentation (Segment Anything / SAM) and audio generation (AudioCraft / MusicGen). Additional model skills (CLIP, Stable Diffusion, Whisper, LLaVA) are available as option… |
| `models/huggingface-hub/SKILL.md` | HuggingFace hf CLI: search/download/upload models, datasets. |
| `models/segment-anything-model/SKILL.md` | SAM: zero-shot image segmentation via points, boxes, masks. |
| `models/segment-anything-model/references/advanced-usage.md` | Segment Anything Advanced Usage Guide |
| `models/segment-anything-model/references/troubleshooting.md` | Segment Anything Troubleshooting Guide |
| `nemo-curator/SKILL.md` | Curate LLM training data: dedupe, filter, PII redaction. |
| `nemo-curator/references/deduplication.md` | Deduplication Guide |
| `nemo-curator/references/filtering.md` | Quality Filtering Guide |
| `obliteratus/SKILL.md` | OBLITERATUS: abliterate LLM refusals (diff-in-means). |
| `obliteratus/references/analysis-modules.md` | OBLITERATUS Analysis Modules — Reference |
| `obliteratus/references/methods-guide.md` | OBLITERATUS Methods — Detailed Guide |
| `obliteratus/templates/abliteration-config.yaml` | OBLITERATUS Abliteration Config Usage: obliteratus run this-file.yaml |
| `obliteratus/templates/analysis-study.yaml` | OBLITERATUS Analysis Study Config Usage: obliteratus run this-file.yaml --preset jailbreak |
| `obliteratus/templates/batch-abliteration.yaml` | OBLITERATUS Batch Abliteration Config Abliterate multiple models with the same method for comparison. |
| `peft/SKILL.md` | Fine-tune large LLMs with LoRA on limited GPU memory. |
| `peft/references/advanced-usage.md` | PEFT Advanced Usage Guide |
| `peft/references/troubleshooting.md` | PEFT Troubleshooting Guide |
| `pinecone/SKILL.md` | Managed vector DB for production RAG and search. |
| `pinecone/references/deployment.md` | Pinecone Deployment Guide |
| `pytorch-fsdp/SKILL.md` | Fully sharded data-parallel training for large models. |
| `pytorch-fsdp/references/common-patterns.md` | PyTorch FSDP — Common Patterns (full reference) |
| `pytorch-fsdp/references/index.md` | Pytorch-Fsdp Documentation Index |
| `pytorch-fsdp/references/other.md` | Pytorch-Fsdp - Other |
| `pytorch-lightning/SKILL.md` | Clean training loops with built-in distributed support. |
| `pytorch-lightning/references/callbacks.md` | PyTorch Lightning Callbacks |
| `pytorch-lightning/references/distributed.md` | PyTorch Lightning Distributed Training |
| `pytorch-lightning/references/hyperparameter-tuning.md` | Hyperparameter Tuning with PyTorch Lightning |
| `qdrant/SKILL.md` | Vector search engine for production RAG systems. |
| `qdrant/references/advanced-usage.md` | Qdrant Advanced Usage Guide |
| `qdrant/references/troubleshooting.md` | Qdrant Troubleshooting Guide |
| `research/DESCRIPTION.md` | ML research frameworks for building and optimizing AI systems with declarative programming. |
| `research/dspy/SKILL.md` | DSPy: declarative LM programs, auto-optimize prompts, RAG. |
| `research/dspy/references/examples.md` | DSPy Real-World Examples |
| `research/dspy/references/modules.md` | DSPy Modules |
| `research/dspy/references/optimizers.md` | DSPy Optimizers (Teleprompters) |
| `saelens/SKILL.md` | Train sparse autoencoders to interpret model features. |
| `saelens/references/README.md` | SAELens Reference Documentation |
| `saelens/references/api.md` | SAELens API Reference |
| `saelens/references/tutorials.md` | SAELens Tutorials |
| `simpo/SKILL.md` | Reference-free preference alignment, simpler than DPO. |
| `simpo/references/datasets.md` | Datasets |
| `simpo/references/hyperparameters.md` | Hyperparameters |
| `simpo/references/loss-functions.md` | Loss Functions |
| `slime/SKILL.md` | RL post-training for LLMs with Megatron and SGLang. |
| `slime/references/api-reference.md` | slime API Reference |
| `slime/references/troubleshooting.md` | slime Troubleshooting Guide |
| `stable-diffusion/SKILL.md` | Text-to-image generation, inpainting, and img2img. |
| `stable-diffusion/references/advanced-usage.md` | Stable Diffusion Advanced Usage Guide |
| `stable-diffusion/references/troubleshooting.md` | Stable Diffusion Troubleshooting Guide |
| `tensorrt-llm/SKILL.md` | High-throughput LLM inference on NVIDIA GPUs. |
| `tensorrt-llm/references/multi-gpu.md` | Multi-GPU Deployment Guide |
| `tensorrt-llm/references/optimization.md` | TensorRT-LLM Optimization Guide |
| `tensorrt-llm/references/serving.md` | Production Serving Guide |
| `torchtitan/SKILL.md` | Pretrain LLMs at scale with PyTorch 4D parallelism. |
| `torchtitan/references/checkpoint.md` | Checkpointing in TorchTitan |
| `torchtitan/references/custom-models.md` | Adding Custom Models to TorchTitan |
| `torchtitan/references/float8.md` | Float8 Training in TorchTitan |
| `torchtitan/references/fsdp.md` | FSDP2 in TorchTitan |
| `training/axolotl/SKILL.md` | Axolotl: YAML LLM fine-tuning (LoRA, DPO, GRPO). |
| `training/axolotl/references/api.md` | Axolotl - Api |
| `training/axolotl/references/dataset-formats.md` | Axolotl - Dataset-Formats |
| `training/axolotl/references/index.md` | Axolotl Documentation Index |
| `training/axolotl/references/other.md` | Axolotl - Other |
| `training/trl-fine-tuning/SKILL.md` | TRL: SFT, DPO, GRPO, RLOO reward modeling for LLM RLHF. |
| `training/trl-fine-tuning/references/dpo-variants.md` | DPO Variants |
| `training/trl-fine-tuning/references/grpo-training.md` | GRPO (Group Relative Policy Optimization) — Deep Guide |
| `training/trl-fine-tuning/references/online-rl.md` | Online RL Methods |
| `training/trl-fine-tuning/references/reward-modeling.md` | Reward Modeling |
| `training/trl-fine-tuning/references/sft-training.md` | SFT Training Guide |
| `training/trl-fine-tuning/templates/basic_grpo_training.py` | Basic GRPO Training Template ============================= |
| `training/unsloth/SKILL.md` | Unsloth: 2-5x faster LoRA/QLoRA fine-tuning, less VRAM. |
| `training/unsloth/references/index.md` | Unsloth Documentation Index |
| `training/unsloth/references/llms-full.md` | Unsloth Docs |
| `training/unsloth/references/llms-txt.md` | Unsloth - Llms-Txt |
| `training/unsloth/references/llms.md` | Unsloth Documentation |
| `whisper/SKILL.md` | Transcribe and translate speech in 99 languages. |
| `whisper/references/languages.md` | Whisper Language Support Guide |

## `optional-skills/payments/`

| File | What it does |
|---|---|
| `mpp-agent/SKILL.md` | Pay HTTP 402 APIs via Machine Payments Protocol (MPP). |
| `stripe-link-cli/SKILL.md` | Agent payments via Stripe Link — cards, SPT, approvals. |
| `stripe-projects/SKILL.md` | Provision SaaS services + sync creds via Stripe Projects. |

## `optional-skills/productivity/`

| File | What it does |
|---|---|
| `canvas/SKILL.md` | Fetch Canvas LMS courses and assignments via API token. |
| `canvas/scripts/canvas_api.py` | Canvas LMS API CLI for Hermes Agent. |
| `decision-questionnaire/SKILL.md` | Turn an unanswerable decision into a questionnaire doc. |
| `here-now/SKILL.md` | Publish sites to {slug}.here.now and store files in Drives. |
| `here-now/scripts/drive.sh` | Shell script: `drive` |
| `here-now/scripts/publish.sh` | Shell script: `publish` |
| `live-dashboard/SKILL.md` | Build self-updating dashboards from live sources. |
| `memento-flashcards/SKILL.md` | Spaced-repetition flashcards: create, review, quiz, export. |
| `memento-flashcards/scripts/memento_cards.py` | Memento card storage, spaced-repetition engine, and CSV I/O. |
| `memento-flashcards/scripts/youtube_quiz.py` | Fetch YouTube transcripts for Memento quiz generation. |
| `property-listings/SKILL.md` | Present property and rental listings as desktop cards. |
| `shop/SKILL.md` | Shop catalog search, checkout, order tracking, returns. |
| `shop/references/catalog-mcp.md` | Direct Global Catalog MCP |
| `shop/references/direct-api.md` | Direct Auth, Checkout, And Orders API |
| `shop/references/legal.md` | Legal |
| `shop/references/safety.md` | Safety, Security, And Legal |
| `shopify/SKILL.md` | Query Shopify Admin/Storefront GraphQL APIs via curl. |
| `siyuan/SKILL.md` | Query and edit a SiYuan knowledge base via its API. |
| `telephony/SKILL.md` | Provision Twilio numbers, SMS/MMS, and AI outbound calls. |
| `telephony/scripts/telephony.py` | Telephony helper for the Hermes optional telephony skill. |

## `optional-skills/research/`

| File | What it does |
|---|---|
| `bioinformatics/SKILL.md` | Gateway to 400+ genomics and computational biology skills. |
| `blogwatcher/SKILL.md` | Monitor blogs and RSS/Atom feeds via blogwatcher-cli tool. |
| `darwinian-evolver/SKILL.md` | Evolve prompts/regex/SQL/code with Imbue's evolution loop. |
| `darwinian-evolver/scripts/parrot_openrouter.py` | parrot_openrouter: same as the upstream `parrot` example but the LLM call goes through OpenRouter (OpenAI SDK) instead of Anthropic native. Lets us run an end-to-end evolution with whatever model the user already has pa… |
| `darwinian-evolver/scripts/show_snapshot.py` | show_snapshot.py — Dump the population from a darwinian-evolver snapshot pickle. |
| `darwinian-evolver/templates/custom_problem_template.py` | Template: a custom darwinian-evolver problem. |
| `domain-intel/SKILL.md` | Passive recon of subdomains, SSL certs, WHOIS, and DNS. |
| `domain-intel/scripts/domain_intel.py` | Domain Intelligence — Passive OSINT via Python stdlib. |
| `drug-discovery/SKILL.md` | Drug discovery: ChEMBL search, drug-likeness, interactions. |
| `drug-discovery/references/ADMET_REFERENCE.md` | ADMET Reference Guide |
| `drug-discovery/scripts/chembl_target.py` | chembl_target.py — Search ChEMBL for a target and retrieve top active compounds. Usage: python3 chembl_target.py "EGFR" --min-pchembl 7 --limit 20 No external dependencies. |
| `drug-discovery/scripts/ro5_screen.py` | ro5_screen.py — Batch Lipinski Ro5 + Veber screening via PubChem API. Usage: python3 ro5_screen.py aspirin ibuprofen paracetamol No external dependencies beyond stdlib. |
| `duckduckgo-search/SKILL.md` | Free keyless web, news, and image search via ddgs. |
| `duckduckgo-search/scripts/duckduckgo.sh` | DuckDuckGo Search Helper Script Wrapper around ddgs CLI with sensible defaults Usage: ./duckduckgo.sh <query> [max_results] |
| `gitnexus-explorer/SKILL.md` | Serve an interactive codebase knowledge graph web UI. |
| `gitnexus-explorer/scripts/proxy.mjs` | GitNexus reverse proxy — serves production web UI + proxies /api/* to backend. Zero dependencies, Node.js built-ins only. Usage: node proxy.mjs <dist-dir> [port] dist-dir: path to gitnexus-web/dist (production build) po… |
| `osint-investigation/SKILL.md` | Follow the money via public records and sanctions data. |
| `osint-investigation/references/sources/courtlistener.md` | CourtListener — Free Law Project |
| `osint-investigation/references/sources/gdelt.md` | GDELT — Global News Monitoring |
| `osint-investigation/references/sources/icij-offshore.md` | ICIJ Offshore Leaks Database |
| `osint-investigation/references/sources/nyc-acris.md` | NYC ACRIS — NYC Real Property Records |
| `osint-investigation/references/sources/ofac-sdn.md` | OFAC SDN — Specially Designated Nationals List |
| `osint-investigation/references/sources/opencorporates.md` | OpenCorporates — Global Corporate Registry |
| `osint-investigation/references/sources/sec-edgar.md` | SEC EDGAR — Corporate Filings |
| `osint-investigation/references/sources/senate-ld.md` | Senate LD — Lobbying Disclosure (LD-1 / LD-2) |
| `osint-investigation/references/sources/usaspending.md` | USAspending — Federal Government Contracts and Grants |
| `osint-investigation/references/sources/wayback.md` | Wayback Machine — Internet Archive CDX |
| `osint-investigation/references/sources/wikipedia.md` | Wikipedia + Wikidata |
| `osint-investigation/scripts/_http.py` | Tiny stdlib HTTP helper used by fetch_*.py scripts. |
| `osint-investigation/scripts/_normalize.py` | Shared entity-name normalization helpers (stdlib-only). |
| `osint-investigation/scripts/build_findings.py` | Build a structured findings.json with evidence chains (stdlib-only). |
| `osint-investigation/scripts/entity_resolution.py` | Cross-source entity resolution (stdlib-only). |
| `osint-investigation/scripts/fetch_courtlistener.py` | Search court records via CourtListener (Free Law Project). |
| `osint-investigation/scripts/fetch_gdelt.py` | Search the GDELT 2.0 DOC API for news mentions. |
| `osint-investigation/scripts/fetch_icij_offshore.py` | Search ICIJ Offshore Leaks via the bulk CSV database. |
| `osint-investigation/scripts/fetch_nyc_acris.py` | Search NYC property records via ACRIS (Automated City Register Information System). |
| `osint-investigation/scripts/fetch_ofac_sdn.py` | Fetch OFAC SDN list (CSV format) and normalize. |
| `osint-investigation/scripts/fetch_opencorporates.py` | Search OpenCorporates company registry data. |
| `osint-investigation/scripts/fetch_sec_edgar.py` | Fetch SEC EDGAR filings index for a given CIK or company name. |
| `osint-investigation/scripts/fetch_senate_ld.py` | Fetch Senate Lobbying Disclosure (LD-1 / LD-2) filings. |
| `osint-investigation/scripts/fetch_usaspending.py` | Fetch federal contracts/awards from USAspending.gov API v2. |
| `osint-investigation/scripts/fetch_wayback.py` | Search the Internet Archive Wayback Machine via the CDX server. |
| `osint-investigation/scripts/fetch_wikipedia.py` | Search Wikipedia + Wikidata for an entity (person, company, place, concept). |
| `osint-investigation/scripts/timing_analysis.py` | Permutation test for donation/contract timing correlation (stdlib-only). |
| `osint-investigation/templates/source-template.md` | <Source Name> |
| `parallel-cli/SKILL.md` | Agent-native web search, deep research, and enrichment. |
| `pinecone-research/SKILL.md` | Agent RAG and long-term memory with Pinecone. |
| `pinecone-research/scripts/memory_manager.py` | Pinecone memory manager — namespace-based session memory for agents. |
| `pinecone-research/scripts/rag_pipeline.py` | Pinecone RAG pipeline — index documents and query with retrieval-augmented generation. |
| `qmd/SKILL.md` | Hybrid local search over notes, docs, and transcripts. |
| `research-paper-writing/SKILL.md` | Write ML papers for NeurIPS/ICML/ICLR: design→submit. |
| `research-paper-writing/references/autoreason-methodology.md` | Autoreason: Iterative Refinement Methodology |
| `research-paper-writing/references/checklists.md` | Conference Paper Checklists |
| `research-paper-writing/references/citation-workflow.md` | Citation Management & Hallucination Prevention |
| `research-paper-writing/references/experiment-patterns.md` | Experiment Design Patterns |
| `research-paper-writing/references/human-evaluation.md` | Human Evaluation Guide for ML/AI Research |
| `research-paper-writing/references/paper-types.md` | Paper Types Beyond Empirical ML |
| `research-paper-writing/references/phase5-paper-drafting.md` | Phase 5: Paper Drafting (full procedure) |
| `research-paper-writing/references/reviewer-guidelines.md` | Reviewer Guidelines & Evaluation Criteria |
| `research-paper-writing/references/sources.md` | Source Bibliography |
| `research-paper-writing/references/writing-guide.md` | ML Paper Writing Philosophy & Best Practices |
| `research-paper-writing/templates/README.md` | LaTeX Templates for ML/AI Conferences |
| `research-paper-writing/templates/aaai2026/README.md` | AAAI 2026 统一LaTeX模板使用说明 / AAAI 2026 Unified LaTeX Template Guide |
| `research-paper-writing/templates/aaai2026/aaai2026-unified-supp.tex` | LaTeX source/template |
| `research-paper-writing/templates/aaai2026/aaai2026-unified-template.tex` | LaTeX source/template |
| `research-paper-writing/templates/aaai2026/aaai2026.bib` | BibTeX bibliography (LaTeX template) |
| `research-paper-writing/templates/aaai2026/aaai2026.bst` | BibTeX style file (LaTeX template) |
| `research-paper-writing/templates/aaai2026/aaai2026.sty` | LaTeX style file |
| `research-paper-writing/templates/acl/README.md` | *ACL Paper Styles |
| `research-paper-writing/templates/acl/acl.sty` | LaTeX style file |
| `research-paper-writing/templates/acl/acl_latex.tex` | LaTeX source/template |
| `research-paper-writing/templates/acl/acl_lualatex.tex` | LaTeX source/template |
| `research-paper-writing/templates/acl/acl_natbib.bst` | BibTeX style file (LaTeX template) |
| `research-paper-writing/templates/acl/anthology.bib.txt` | Plain-text file |
| `research-paper-writing/templates/acl/custom.bib` | BibTeX bibliography (LaTeX template) |
| `research-paper-writing/templates/acl/formatting.md` | Instructions for *ACL Proceedings |
| `research-paper-writing/templates/colm2025/README.md` | Template |
| `research-paper-writing/templates/colm2025/colm2025_conference.bib` | BibTeX bibliography (LaTeX template) |
| `research-paper-writing/templates/colm2025/colm2025_conference.bst` | BibTeX style file (LaTeX template) |
| `research-paper-writing/templates/colm2025/colm2025_conference.pdf` | PDF document |
| `research-paper-writing/templates/colm2025/colm2025_conference.sty` | LaTeX style file |
| `research-paper-writing/templates/colm2025/colm2025_conference.tex` | LaTeX source/template |
| `research-paper-writing/templates/colm2025/fancyhdr.sty` | LaTeX style file |
| `research-paper-writing/templates/colm2025/math_commands.tex` | LaTeX source/template |
| `research-paper-writing/templates/colm2025/natbib.sty` | LaTeX style file |
| `research-paper-writing/templates/iclr2026/fancyhdr.sty` | LaTeX style file |
| `research-paper-writing/templates/iclr2026/iclr2026_conference.bib` | BibTeX bibliography (LaTeX template) |
| `research-paper-writing/templates/iclr2026/iclr2026_conference.bst` | BibTeX style file (LaTeX template) |
| `research-paper-writing/templates/iclr2026/iclr2026_conference.pdf` | PDF document |
| `research-paper-writing/templates/iclr2026/iclr2026_conference.sty` | LaTeX style file |
| `research-paper-writing/templates/iclr2026/iclr2026_conference.tex` | LaTeX source/template |
| `research-paper-writing/templates/iclr2026/math_commands.tex` | LaTeX source/template |
| `research-paper-writing/templates/iclr2026/natbib.sty` | LaTeX style file |
| `research-paper-writing/templates/icml2026/algorithm.sty` | LaTeX style file |
| `research-paper-writing/templates/icml2026/algorithmic.sty` | LaTeX style file |
| `research-paper-writing/templates/icml2026/example_paper.bib` | BibTeX bibliography (LaTeX template) |
| `research-paper-writing/templates/icml2026/example_paper.pdf` | PDF document |
| `research-paper-writing/templates/icml2026/example_paper.tex` | LaTeX source/template |
| `research-paper-writing/templates/icml2026/fancyhdr.sty` | LaTeX style file |
| `research-paper-writing/templates/icml2026/icml2026.bst` | BibTeX style file (LaTeX template) |
| `research-paper-writing/templates/icml2026/icml2026.sty` | LaTeX style file |
| `research-paper-writing/templates/icml2026/icml_numpapers.pdf` | PDF document |
| `research-paper-writing/templates/neurips2025/Makefile` | Make build recipes |
| `research-paper-writing/templates/neurips2025/extra_pkgs.tex` | LaTeX source/template |
| `research-paper-writing/templates/neurips2025/main.tex` | LaTeX source/template |
| `research-paper-writing/templates/neurips2025/neurips.sty` | LaTeX style file |
| `rss-feeds/SKILL.md` | Read RSS, Atom, JSON feeds; discover feeds behind a page. |
| `rss-feeds/scripts/feed.py` | Read RSS / Atom / JSON Feed sources and discover feeds behind a page URL. |
| `scrapling/SKILL.md` | Scrape sites with stealth browsing and Cloudflare bypass. |
| `searxng-search/SKILL.md` | Free keyless meta-search aggregating 70+ engines. |
| `searxng-search/scripts/searxng.sh` | Usage: ./searxng.sh <query> [max_results] [engines] Example: ./searxng.sh "python async" 10 "google,bing" |

## `optional-skills/security/`

| File | What it does |
|---|---|
| `1password/SKILL.md` | Set up op CLI, sign in, and read or inject secrets. |
| `1password/references/cli-examples.md` | op CLI examples |
| `1password/references/get-started.md` | 1Password CLI get-started (summary) |
| `DESCRIPTION.md` | Security |
| `godmode/SKILL.md` | Jailbreak LLMs: Parseltongue, GODMODE, ULTRAPLINIAN. |
| `godmode/references/jailbreak-templates.md` | GODMODE CLASSIC — Jailbreak System Prompt Templates |
| `godmode/references/refusal-detection.md` | Refusal Detection & Response Scoring |
| `godmode/scripts/auto_jailbreak.py` | Auto-Jailbreak Pipeline |
| `godmode/scripts/godmode_race.py` | ULTRAPLINIAN Multi-Model Racing Engine Ported from G0DM0D3 (elder-plinius/G0DM0D3). |
| `godmode/scripts/load_godmode.py` | Loader for G0DM0D3 scripts. Handles the exec-scoping issues. |
| `godmode/scripts/parseltongue.py` | Parseltongue v4 — Input Obfuscation Engine Ported from G0DM0D3 (elder-plinius/G0DM0D3) JavaScript to Python. |
| `godmode/templates/prefill-subtle.json` | JSON list (2 entries) |
| `godmode/templates/prefill.json` | JSON list (4 entries) |
| `oss-forensics/SKILL.md` | GitHub supply-chain forensics: recovery, IOCs, reporting. |
| `oss-forensics/references/evidence-types.md` | Evidence Types Reference |
| `oss-forensics/references/github-archive-guide.md` | GitHub Archive Query Guide (BigQuery) |
| `oss-forensics/references/investigation-templates.md` | Investigation Templates |
| `oss-forensics/references/recovery-techniques.md` | Deleted Content Recovery Techniques |
| `oss-forensics/scripts/evidence-store.py` | OSS Forensics Evidence Store Manager Manages a JSON-based evidence store for forensic investigations. |
| `oss-forensics/templates/forensic-report.md` | Forensic Investigation Report |
| `oss-forensics/templates/malicious-package-report.md` | Malicious Package Investigation Report |
| `sherlock/SKILL.md` | Find accounts for a username across 400+ platforms. |
| `unbroker/README.md` | unbroker |
| `unbroker/SKILL.md` | Remove your info from data-broker sites, by name or phone. |
| `unbroker/assets/unbroker.png` | PNG image asset |
| `unbroker/references/brokers/addresses.json` | JSON manifest for `Addresses.com` |
| `unbroker/references/brokers/advancedbackgroundchecks.json` | JSON manifest for `AdvancedBackgroundChecks` |
| `unbroker/references/brokers/beenverified.json` | JSON manifest for `BeenVerified` |
| `unbroker/references/brokers/clustal.json` | JSON manifest for `Clustal` |
| `unbroker/references/brokers/clustrmaps.json` | JSON manifest for `ClustrMaps` |
| `unbroker/references/brokers/cyberbackgroundchecks.json` | JSON manifest for `CyberBackgroundChecks` |
| `unbroker/references/brokers/familytreenow.json` | JSON manifest for `FamilyTreeNow` |
| `unbroker/references/brokers/fastpeoplesearch.json` | JSON manifest for `FastPeopleSearch` |
| `unbroker/references/brokers/intelius.json` | JSON manifest for `Intelius` |
| `unbroker/references/brokers/mylife.json` | JSON manifest for `MyLife` |
| `unbroker/references/brokers/nuwber.json` | JSON manifest for `Nuwber` |
| `unbroker/references/brokers/peekyou.json` | JSON manifest for `PeekYou` |
| `unbroker/references/brokers/peoplefinders.json` | JSON manifest for `PeopleFinders` |
| `unbroker/references/brokers/radaris.json` | JSON manifest for `Radaris` |
| `unbroker/references/brokers/rehold.json` | JSON manifest for `Rehold` |
| `unbroker/references/brokers/searchpeoplefree.json` | JSON manifest for `SearchPeopleFree` |
| `unbroker/references/brokers/socialcatfish.json` | JSON manifest for `Social Catfish` |
| `unbroker/references/brokers/spokeo.json` | JSON manifest for `Spokeo` |
| `unbroker/references/brokers/thatsthem.json` | JSON manifest for `That's Them` |
| `unbroker/references/brokers/truepeoplesearch.json` | JSON manifest for `TruePeopleSearch` |
| `unbroker/references/brokers/usphonebook.json` | JSON manifest for `USPhoneBook` |
| `unbroker/references/brokers/whitepages.json` | JSON manifest for `Whitepages` |
| `unbroker/references/legal/ccpa.md` | CCPA / CPRA (California) |
| `unbroker/references/legal/drop.md` | California DROP portal (highest-leverage lever) |
| `unbroker/references/legal/gdpr.md` | GDPR / UK-GDPR (roadmap - Phase 3) |
| `unbroker/references/methods.md` | Opt-out method playbooks |
| `unbroker/references/site-playbooks.md` | Per-site playbooks (pre-recorded game plans) |
| `unbroker/references/state-machine.md` | Case state machine |
| `unbroker/scripts/autopilot.py` | Autonomous action queue: what should the agent do RIGHT NOW for this subject? |
| `unbroker/scripts/badbool.py` | Pull and parse the Big-Ass Data Broker Opt-Out List (BADBOOL) into broker records. |
| `unbroker/scripts/brokers.py` | Load and query the broker database (references/brokers/*.json). |
| `unbroker/scripts/cdp.py` | Launch (or detect) the operator's local Chrome/Chromium over the DevTools Protocol (CDP). |
| `unbroker/scripts/config.py` | Install-wide configuration with easiest-first defaults. |
| `unbroker/scripts/crypto.py` | At-rest encryption for sensitive files via the `age` binary (optional). |
| `unbroker/scripts/dossier.py` | Subject dossier management + consent gate + least-disclosure field selection. |
| `unbroker/scripts/email_modes.py` | Email modes A/B/C helpers + anti-phishing verification-link extraction. |
| `unbroker/scripts/emailer.py` | Programmatic email (Mode B) via stdlib smtplib/imaplib - no human in the loop. |
| `unbroker/scripts/ledger.py` | Case ledger: opt-out state machine + append-only audit log. |
| `unbroker/scripts/legal.py` | Render opt-out / legal request text from templates/ with safe substitution. |
| `unbroker/scripts/paths.py` | Filesystem paths for the unbroker skill (stdlib only). |
| `unbroker/scripts/pdd.py` | unbroker - deterministic CLI helper. |
| `unbroker/scripts/registry.py` | Ingest the California Data Broker Registry into broker records (coverage breadth). |
| `unbroker/scripts/report.py` | Status dashboards, Markdown reports, human-task digest, and Google Sheets row export. |
| `unbroker/scripts/scan.py` | Stdlib fetch helper for simple url_pattern brokers (osint-style). |
| `unbroker/scripts/storage.py` | Storage helpers (stdlib only): atomic JSON, append-only JSONL, strict perms. |
| `unbroker/scripts/tiers.py` | Automation-tier selection and per-subject action planning. |
| `unbroker/scripts/vectors.py` | Enumerate the search queries to run per broker, across ALL of a subject's identifiers. |
| `unbroker/templates/consent/authorization.md` | Authorization to act on my behalf (data removal) |
| `unbroker/templates/emails/ccpa-authorized-agent.txt` | Plain-text file |
| `unbroker/templates/emails/ccpa-deletion.txt` | Plain-text file |
| `unbroker/templates/emails/ccpa-indirect-deletion.txt` | Plain-text file |
| `unbroker/templates/emails/gdpr-erasure.txt` | Plain-text file |
| `unbroker/templates/emails/generic-optout.txt` | Plain-text file |
| `web-pentest/SKILL.md` | Authorized web pentest: recon, proof-based exploits, report. |
| `web-pentest/references/bypass-techniques.md` | Bypass Techniques |
| `web-pentest/references/exploitation-techniques.md` | Exploitation Techniques |
| `web-pentest/references/scope-enforcement.md` | Scope Enforcement |
| `web-pentest/references/vuln-taxonomy.md` | Vulnerability Taxonomy |
| `web-pentest/scripts/recon-scan.sh` | Rate-limited recon scan wrapper for the web-pentest skill. Wraps nmap + whatweb + curl headers; enforces scope.txt. |
| `web-pentest/templates/authorization.md` | Engagement Authorization |
| `web-pentest/templates/exploitation-queue.json` | JSON object with keys `schema`, `vuln_class`, `generated_at`, `engagement_id`, `candidates` |
| `web-pentest/templates/pentest-report.md` | Penetration Test Report |

## `optional-skills/smart-home/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for controlling smart home devices — lights, switches, sensors, and home automation systems. |
| `openhue/SKILL.md` | Control Philips Hue lights, scenes, rooms via OpenHue CLI. |

## `optional-skills/social-media/`

| File | What it does |
|---|---|
| `reddit-reading/SKILL.md` | Read Reddit: subreddits, search, threads, users. No browser. |
| `reddit-reading/scripts/reddit.py` | Read Reddit without a browser: listings, search, threads with comments, user pages. |

## `optional-skills/software-development/`

| File | What it does |
|---|---|
| `ast-grep/LICENSE` | Software license text |
| `ast-grep/SKILL.md` | AST-aware structural code search and rewrite via ast-grep. |
| `ast-grep/install.ps1` | PowerShell script |
| `ast-grep/install.sh` | install.sh - install the ast-grep binary on POSIX systems (macOS, Linux, WSL, Git Bash). |
| `ast-grep/references/cli.md` | CLI reference — `sg` / `ast-grep` |
| `ast-grep/references/install.md` | Install ast-grep |
| `ast-grep/references/patterns.md` | Pattern syntax — meta-variables and how patterns parse |
| `ast-grep/references/pitfalls.md` | Pitfalls — what breaks patterns and how to fix them |
| `ast-grep/references/recipes.md` | Recipes — copy-paste patterns by language |
| `ast-grep/references/sgconfig.md` | sgconfig.yml — project configuration |
| `ast-grep/references/yaml-rules.md` | YAML rule reference — atomic, relational, composite, transform, fix |
| `ast-grep/scripts/ast_grep_helper.py` | ast-grep-helper: a thin LLM-friendly wrapper around `sg` (ast-grep). |
| `ast-grep/tests/smoke.ps1` | Smoke test for the ast-grep skill on Windows (PowerShell 5.1+). |
| `ast-grep/tests/smoke.sh` | Smoke test for the ast-grep skill on POSIX (macOS / Linux / WSL / Git Bash). |
| `code-wiki/SKILL.md` | Generate wiki docs + Mermaid diagrams for any codebase. |
| `code-wiki/templates/README.md` | {{PROJECT_NAME}} |
| `code-wiki/templates/architecture.md` | Architecture |
| `code-wiki/templates/getting-started.md` | Getting Started |
| `code-wiki/templates/module.md` | Module: `{{MODULE_NAME}}` |
| `grill-me/SKILL.md` | Adversarial plan interview before implementation. |
| `pr-lens/LICENSE.txt` | Plain-text file |
| `pr-lens/SKILL.md` | Draw code changes as animated architecture/data-flow SVGs. |
| `pr-lens/references/config.md` | Correcting the map: `.github/pr-lens.yml` |
| `pr-lens/references/example.graph.json` | Broadcast delivery moves from one Postmark request per recipient to batched requests of 500, with suppression filtering pulled in front of the send and the payload builder extracted into a shared library. |
| `pr-lens/references/graph-document.md` | Authoring a graph document |
| `rest-graphql-debug/SKILL.md` | Debug REST/GraphQL APIs: status codes, auth, schemas, repro. |
| `subagent-driven-development/SKILL.md` | Execute plans via delegate_task subagents (2-stage review). |
| `subagent-driven-development/references/context-budget-discipline.md` | Context Budget Discipline |
| `subagent-driven-development/references/gates-taxonomy.md` | Gates Taxonomy |

## `optional-skills/web-development/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Web Development |
| `cloudflare-temporary-deploy/SKILL.md` | Deploy a Worker live, no account, via wrangler --temporary. |
| `cloudflare-temporary-deploy/scripts/parse_deploy_output.py` | Parse `wrangler deploy --temporary` output into structured JSON. |
| `har-derived-api-client/SKILL.md` | Record a site's XHR into a HAR, derive an HTTP client. |
| `har-derived-api-client/scripts/har_capture.py` | Record a HAR file while driving a website with Playwright. |
| `har-derived-api-client/scripts/har_capture_cdp.py` | Capture a HAR from a browser you connect to over CDP (not one you launch). |
| `har-derived-api-client/scripts/har_to_client.py` | Distill a HAR file into an API summary an agent can turn into a client. |
| `page-agent/SKILL.md` | Embed an in-page natural-language GUI copilot in web apps. |
| `publish-site/SKILL.md` | Versioned site deploys to GitHub/Cloudflare/Netlify Pages. |
| `scrollcraft/LICENSE.txt` | Plain-text file |
| `scrollcraft/SKILL.md` | Premium scroll-driven landing pages; scroll = timeline. |
| `scrollcraft/engine/scrollcraft.css` | ============================================================================ scrollcraft.css: the taste floor ---------------------------------------------------------------------------- Two layers, and the split matter… |
| `scrollcraft/engine/scrollcraft.js` | ============================================================================ scrollcraft: a scroll-driven interaction runtime ---------------------------------------------------------------------------- Vanilla JS. Zero… |
| `scrollcraft/references/assets.md` | Assets |
| `scrollcraft/references/device-diag.html` | HTML page/template |
| `scrollcraft/references/devices.md` | The device kit |
| `scrollcraft/references/feel.md` | The emotion axis |
| `scrollcraft/references/taste.md` | The taste floor |
| `scrollcraft/references/template.html` | HTML page/template |
| `scrollcraft/references/uniqueness.md` | The structure axis |
| `scrollcraft/references/verify.md` | Verify |
| `scrollcraft/references/worldflight.md` | Worldflight: the continuous-world page mode |
| `scrollcraft/references/worlds.md` | Worlds |
| `scrollcraft/scripts/doctor.mjs` | JavaScript (ES module): `doctor` |
| `scrollcraft/scripts/encode.sh` | scrollcraft: encode a clip for scrubbing, not for playback. |
| `scrollcraft/scripts/kie.mjs` | JavaScript (ES module): `kie` |
| `scrollcraft/scripts/serve.mjs` | JavaScript (ES module): `serve` |
| `scrollcraft/scripts/shoot.mjs` | JavaScript (ES module): `shoot` |
| `scrollcraft/scripts/workspace.mjs` | Exports `resolveWorkspace`, `paths`, `ensure` |
| `scrollcraft/scripts/worldflight-assert.mjs` | JavaScript (ES module): `worldflight-assert` |
| `scrollcraft/templates/FINGERPRINTS.md` | Fingerprints |

## `optional-skills/yuanbao/`

| File | What it does |
|---|---|
| `SKILL.md` | Yuanbao (元宝) groups: @mention users, query info/members. |
