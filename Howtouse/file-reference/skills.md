# File reference: `skills`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

## `skills/`

| File | What it does |
|---|---|
| `AGENTS.md` | skills/ + optional-skills/ — bundled skills, authoring standards, curator |

## `skills/apple/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Apple / macOS skills — tools that interact with the Mac desktop (Finder, native apps) or system features (accessibility, screenshots). |
| `apple-notes/SKILL.md` | Manage Apple Notes via memo CLI: create, search, edit. |
| `apple-reminders/SKILL.md` | Apple Reminders via remindctl: add, list, complete. |
| `findmy/SKILL.md` | Track Apple devices/AirTags via FindMy.app on macOS. |
| `imessage/SKILL.md` | Send and receive iMessages/SMS via the imsg CLI on macOS. |

## `skills/autonomous-ai-agents/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for spawning and orchestrating autonomous AI coding agents and multi-agent workflows — running independent agent processes, delegating tasks, and coordinating parallel workstreams. |
| `claude-code/SKILL.md` | Delegate coding to Claude Code CLI (features, PRs). |
| `codex/SKILL.md` | Delegate coding to OpenAI Codex CLI (features, PRs). |
| `computer-use/SKILL.md` | Drive the desktop background-first; escalate on signal. |
| `hermes-agent/SKILL.md` | Use, configure, theme, extend, and orchestrate Hermes Agent. |
| `hermes-agent/references/background-systems.md` | Durable & Background Systems |
| `hermes-agent/references/cli-reference.md` | Hermes CLI Reference |
| `hermes-agent/references/configuration.md` | Configuration, Toolsets & Voice |
| `hermes-agent/references/contributor-guide.md` | Contributor Quick Reference |
| `hermes-agent/references/delegate-task-concurrency-diagnosis.md` | delegate_task: diagnosing "my batch was capped" |
| `hermes-agent/references/desktop-plugins.md` | Desktop App Plugins — UI Panes, Commands, Widgets |
| `hermes-agent/references/native-mcp.md` | Native MCP Client |
| `hermes-agent/references/petdex.md` | Petdex — Animated Pet Mascots |
| `hermes-agent/references/portal-auth-for-third-party-apps.md` | Nous Portal — authenticating third-party apps against the subscription |
| `hermes-agent/references/project-context-files.md` | Project Context Files |
| `hermes-agent/references/providers-and-models.md` | Providers & Model Aliases |
| `hermes-agent/references/security-privacy.md` | Security & Privacy Toggles |
| `hermes-agent/references/slash-commands.md` | Slash Commands (In-Session) |
| `hermes-agent/references/themes.md` | Themes / Skins — Author a Hermes Color Theme |
| `hermes-agent/references/troubleshooting.md` | Troubleshooting |
| `hermes-agent/references/tui-widgets.md` | TUI Widgets — Live Panels for the Ink TUI Dock |
| `hermes-agent/references/webhooks.md` | Webhook Subscriptions |
| `hermes-agent/references/windows-quirks.md` | Windows-Specific Quirks |
| `hermes-agent/templates/clock.mjs` | Reference user widget: a live clock docked above the status bar. Copy to ~/.hermes/tui-widgets/clock.mjs, then `/widgets-reload` and `/clock`. |
| `hermes-agent/templates/plugin.js` | Hermes desktop plugin template. Save as: <hermes home>/desktop-plugins/<id>/plugin.js (folder name == id) where <hermes home> is ~/.hermes by default, or ~/.hermes/profiles/<name> when running a named profile (`hermes -… |
| `hermes-agent/templates/skin.yaml` | Hermes skin template — themes the CLI, TUI, and desktop GUI from one file. Copy to <hermes-home>/skins/<name>.yaml, edit the palette, then set |
| `opencode/SKILL.md` | Delegate coding to OpenCode CLI (features, PR review). |

## `skills/creative/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Creative content generation — ASCII art, hand-drawn style diagrams, and visual design tools. |
| `architecture-diagram/SKILL.md` | Dark-themed SVG architecture/cloud/infra diagrams as HTML. |
| `architecture-diagram/templates/template.html` | HTML page/template |
| `ascii-video/README.md` | ☤ ASCII Video |
| `ascii-video/SKILL.md` | ASCII video: convert video/audio to colored ASCII MP4/GIF. |
| `ascii-video/references/architecture.md` | Architecture Reference |
| `ascii-video/references/composition.md` | Composition & Brightness Reference |
| `ascii-video/references/effects.md` | Effect Catalog |
| `ascii-video/references/inputs.md` | Input Sources |
| `ascii-video/references/optimization.md` | Optimization Reference |
| `ascii-video/references/scenes.md` | Scene System & Creative Composition |
| `ascii-video/references/shaders.md` | Shader Pipeline & Composable Effects |
| `ascii-video/references/troubleshooting.md` | Troubleshooting Reference |
| `baoyu-infographic/PORT_NOTES.md` | Port Notes — baoyu-infographic |
| `baoyu-infographic/SKILL.md` | Infographics: 21 layouts x 21 styles (信息图, 可视化). |
| `baoyu-infographic/references/analysis-framework.md` | Infographic Content Analysis Framework |
| `baoyu-infographic/references/base-prompt.md` | Image Specifications |
| `baoyu-infographic/references/layouts/bento-grid.md` | bento-grid |
| `baoyu-infographic/references/layouts/binary-comparison.md` | binary-comparison |
| `baoyu-infographic/references/layouts/bridge.md` | bridge |
| `baoyu-infographic/references/layouts/circular-flow.md` | circular-flow |
| `baoyu-infographic/references/layouts/comic-strip.md` | comic-strip |
| `baoyu-infographic/references/layouts/comparison-matrix.md` | comparison-matrix |
| `baoyu-infographic/references/layouts/dashboard.md` | dashboard |
| `baoyu-infographic/references/layouts/dense-modules.md` | dense-modules |
| `baoyu-infographic/references/layouts/funnel.md` | funnel |
| `baoyu-infographic/references/layouts/hierarchical-layers.md` | hierarchical-layers |
| `baoyu-infographic/references/layouts/hub-spoke.md` | hub-spoke |
| `baoyu-infographic/references/layouts/iceberg.md` | iceberg |
| `baoyu-infographic/references/layouts/isometric-map.md` | isometric-map |
| `baoyu-infographic/references/layouts/jigsaw.md` | jigsaw |
| `baoyu-infographic/references/layouts/linear-progression.md` | linear-progression |
| `baoyu-infographic/references/layouts/periodic-table.md` | periodic-table |
| `baoyu-infographic/references/layouts/story-mountain.md` | story-mountain |
| `baoyu-infographic/references/layouts/structural-breakdown.md` | structural-breakdown |
| `baoyu-infographic/references/layouts/tree-branching.md` | tree-branching |
| `baoyu-infographic/references/layouts/venn-diagram.md` | venn-diagram |
| `baoyu-infographic/references/layouts/winding-roadmap.md` | winding-roadmap |
| `baoyu-infographic/references/structured-content-template.md` | Structured Content Template |
| `baoyu-infographic/references/styles/aged-academia.md` | aged-academia |
| `baoyu-infographic/references/styles/bold-graphic.md` | bold-graphic |
| `baoyu-infographic/references/styles/chalkboard.md` | chalkboard |
| `baoyu-infographic/references/styles/claymation.md` | claymation |
| `baoyu-infographic/references/styles/corporate-memphis.md` | corporate-memphis |
| `baoyu-infographic/references/styles/craft-handmade.md` | craft-handmade (DEFAULT) |
| `baoyu-infographic/references/styles/cyberpunk-neon.md` | cyberpunk-neon |
| `baoyu-infographic/references/styles/hand-drawn-edu.md` | hand-drawn-edu |
| `baoyu-infographic/references/styles/ikea-manual.md` | ikea-manual |
| `baoyu-infographic/references/styles/kawaii.md` | kawaii |
| `baoyu-infographic/references/styles/knolling.md` | knolling |
| `baoyu-infographic/references/styles/lego-brick.md` | lego-brick |
| `baoyu-infographic/references/styles/morandi-journal.md` | morandi-journal |
| `baoyu-infographic/references/styles/origami.md` | origami |
| `baoyu-infographic/references/styles/pixel-art.md` | pixel-art |
| `baoyu-infographic/references/styles/pop-laboratory.md` | pop-laboratory |
| `baoyu-infographic/references/styles/retro-pop-grid.md` | retro-pop-grid |
| `baoyu-infographic/references/styles/storybook-watercolor.md` | storybook-watercolor |
| `baoyu-infographic/references/styles/subway-map.md` | subway-map |
| `baoyu-infographic/references/styles/technical-schematic.md` | technical-schematic |
| `baoyu-infographic/references/styles/ui-wireframe.md` | ui-wireframe |
| `claude-design/SKILL.md` | Design one-off HTML artifacts (landing, deck, prototype). |
| `design-md/SKILL.md` | Author/validate/export Google's DESIGN.md token spec files. |
| `design-md/templates/starter.md` | One-sentence description of the visual identity. |
| `humanizer/LICENSE` | Software license text |
| `humanizer/SKILL.md` | Humanize text: strip AI-isms and add real voice. |
| `manim-video/README.md` | Manim Video Skill |
| `manim-video/SKILL.md` | Manim CE animations: 3Blue1Brown math/algo videos. |
| `manim-video/references/animation-design-thinking.md` | Animation Design Thinking |
| `manim-video/references/animations.md` | Animations Reference |
| `manim-video/references/camera-and-3d.md` | Camera and 3D Reference |
| `manim-video/references/decorations.md` | Decorations and Visual Polish |
| `manim-video/references/equations.md` | Equations and LaTeX Reference |
| `manim-video/references/graphs-and-data.md` | Graphs, Plots, and Data Visualization |
| `manim-video/references/mobjects.md` | Mobjects Reference |
| `manim-video/references/paper-explainer.md` | Paper Explainer Workflow |
| `manim-video/references/production-quality.md` | Production Quality Checklist |
| `manim-video/references/rendering.md` | Rendering Reference |
| `manim-video/references/scene-planning.md` | Scene Planning Reference |
| `manim-video/references/troubleshooting.md` | Troubleshooting |
| `manim-video/references/updaters-and-trackers.md` | Updaters and Value Trackers |
| `manim-video/references/visual-design.md` | Visual Design Principles |
| `manim-video/scripts/setup.sh` | Shell script: `setup` |
| `p5js/README.md` | p5.js Skill |
| `p5js/SKILL.md` | p5.js sketches: gen art, shaders, interactive, 3D. |
| `p5js/references/animation.md` | Animation |
| `p5js/references/color-systems.md` | Color Systems |
| `p5js/references/core-api.md` | Core API Reference |
| `p5js/references/export-pipeline.md` | Export Pipeline |
| `p5js/references/interaction.md` | Interaction |
| `p5js/references/shapes-and-geometry.md` | Shapes and Geometry |
| `p5js/references/troubleshooting.md` | Troubleshooting |
| `p5js/references/typography.md` | Typography |
| `p5js/references/visual-effects.md` | Visual Effects |
| `p5js/references/webgl-and-3d.md` | WebGL and 3D |
| `p5js/scripts/export-frames.js` | JavaScript source: `export-frames` |
| `p5js/scripts/render.sh` | p5.js Skill — Headless Render Pipeline Renders a p5.js sketch to MP4 video via Puppeteer + ffmpeg |
| `p5js/scripts/serve.sh` | p5.js Skill — Local Development Server Serves the current directory over HTTP for loading local assets (fonts, images) |
| `p5js/scripts/setup.sh` | p5.js Skill — Dependency Verification Run: bash skills/creative/p5js/scripts/setup.sh |
| `p5js/templates/viewer.html` | HTML page/template |
| `popular-web-designs/SKILL.md` | 54 real design systems (Stripe, Linear, Vercel) as HTML/CSS. |
| `popular-web-designs/templates/airbnb.md` | Design System: Airbnb |
| `popular-web-designs/templates/airtable.md` | Design System: Airtable |
| `popular-web-designs/templates/apple.md` | Design System: Apple |
| `popular-web-designs/templates/bmw.md` | Design System: BMW |
| `popular-web-designs/templates/cal.md` | Design System: Cal.com |
| `popular-web-designs/templates/claude.md` | Design System: Claude (Anthropic) |
| `popular-web-designs/templates/clay.md` | Design System: Clay |
| `popular-web-designs/templates/clickhouse.md` | Design System: ClickHouse |
| `popular-web-designs/templates/cohere.md` | Design System: Cohere |
| `popular-web-designs/templates/coinbase.md` | Design System: Coinbase |
| `popular-web-designs/templates/composio.md` | Design System: Composio |
| `popular-web-designs/templates/cursor.md` | Design System: Cursor |
| `popular-web-designs/templates/elevenlabs.md` | Design System: ElevenLabs |
| `popular-web-designs/templates/expo.md` | Design System: Expo |
| `popular-web-designs/templates/figma.md` | Design System: Figma |
| `popular-web-designs/templates/framer.md` | Design System: Framer |
| `popular-web-designs/templates/hashicorp.md` | Design System: HashiCorp |
| `popular-web-designs/templates/ibm.md` | Design System: IBM |
| `popular-web-designs/templates/intercom.md` | Design System: Intercom |
| `popular-web-designs/templates/kraken.md` | Design System: Kraken |
| `popular-web-designs/templates/linear.app.md` | Design System: Linear |
| `popular-web-designs/templates/lovable.md` | Design System: Lovable |
| `popular-web-designs/templates/minimax.md` | Design System: MiniMax |
| `popular-web-designs/templates/mintlify.md` | Design System: Mintlify |
| `popular-web-designs/templates/miro.md` | Design System: Miro |
| `popular-web-designs/templates/mistral.ai.md` | Design System: Mistral AI |
| `popular-web-designs/templates/mongodb.md` | Design System: MongoDB |
| `popular-web-designs/templates/notion.md` | Design System: Notion |
| `popular-web-designs/templates/nvidia.md` | Design System: NVIDIA |
| `popular-web-designs/templates/ollama.md` | Design System: Ollama |
| `popular-web-designs/templates/opencode.ai.md` | Design System: OpenCode |
| `popular-web-designs/templates/pinterest.md` | Design System: Pinterest |
| `popular-web-designs/templates/posthog.md` | Design System: PostHog |
| `popular-web-designs/templates/raycast.md` | Design System: Raycast |
| `popular-web-designs/templates/replicate.md` | Design System: Replicate |
| `popular-web-designs/templates/resend.md` | Design System: Resend |
| `popular-web-designs/templates/revolut.md` | Design System: Revolut |
| `popular-web-designs/templates/runwayml.md` | Design System: Runway |
| `popular-web-designs/templates/sanity.md` | Design System: Sanity |
| `popular-web-designs/templates/sentry.md` | Design System: Sentry |
| `popular-web-designs/templates/spacex.md` | Design System: SpaceX |
| `popular-web-designs/templates/spotify.md` | Design System: Spotify |
| `popular-web-designs/templates/stripe.md` | Design System: Stripe |
| `popular-web-designs/templates/supabase.md` | Design System: Supabase |
| `popular-web-designs/templates/superhuman.md` | Design System: Superhuman |
| `popular-web-designs/templates/together.ai.md` | Design System: Together AI |
| `popular-web-designs/templates/uber.md` | Design System: Uber |
| `popular-web-designs/templates/vercel.md` | Design System: Vercel |
| `popular-web-designs/templates/voltagent.md` | Design System: VoltAgent |
| `popular-web-designs/templates/warp.md` | Design System: Warp |
| `popular-web-designs/templates/webflow.md` | Design System: Webflow |
| `popular-web-designs/templates/wise.md` | Design System: Wise |
| `popular-web-designs/templates/x.ai.md` | Design System: xAI |
| `popular-web-designs/templates/zapier.md` | Design System: Zapier |
| `songwriting-and-ai-music/SKILL.md` | Songwriting craft and Suno AI music prompts. |

## `skills/devops/`

| File | What it does |
|---|---|
| `sdlc-review/SKILL.md` | Review Kanban handoffs and route verified outcomes. |

## `skills/email/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for sending, receiving, searching, and managing email from the terminal. |
| `email-inbox-triage/SKILL.md` | Triage an inbox: prioritize threads, draft replies safely. |
| `himalaya/SKILL.md` | Himalaya CLI: IMAP/SMTP email from terminal. |
| `himalaya/references/configuration.md` | Himalaya Configuration Reference |
| `himalaya/references/message-composition.md` | Message Composition with MML (MIME Meta Language) |

## `skills/index-cache/`

| File | What it does |
|---|---|
| `anthropics_skills_skills_.json` | JSON list (16 entries) |
| `lobehub_index.json` | JSON data/configuration |
| `openai_skills_skills_.json` | JSON list (0 entries) |

## `skills/media/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for working with media content — YouTube transcripts, GIF search, music generation, and audio visualization. |
| `gif-search/SKILL.md` | Search/download GIFs from Tenor via curl + jq. |
| `songsee/SKILL.md` | Audio spectrograms/features (mel, chroma, MFCC) via CLI. |
| `youtube-content/SKILL.md` | YouTube transcripts to summaries, threads, blogs. |
| `youtube-content/references/output-formats.md` | Output Format Examples |
| `youtube-content/scripts/fetch_transcript.py` | Fetch a YouTube video transcript and output it as structured JSON. |

## `skills/note-taking/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Note taking skills, to save information, assist with research, and collab on multi-session planning and information sharing. |
| `obsidian/SKILL.md` | Read, search, create, and edit notes in the Obsidian vault. |

## `skills/productivity/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for document creation, presentations, spreadsheets, and other productivity workflows. |
| `airtable/SKILL.md` | Airtable REST API via curl. Records CRUD, filters, upserts. |
| `box/SKILL.md` | Box manages cloud files, sharing, search, and metadata. |
| `box/references/bulk-operations.md` | Bulk operations |
| `box/references/cli-guide.md` | Box CLI guide |
| `box/references/content-workflows.md` | Content workflows |
| `box/references/hubs.md` | Box Hubs |
| `box/references/oauth-setup.md` | OAuth setup |
| `box/references/rest-api.md` | REST API fallback |
| `box/references/sdk-development.md` | SDK development |
| `box/references/search-and-ai.md` | Search, metadata, and Box AI |
| `box/references/troubleshooting.md` | Troubleshooting |
| `box/references/webhooks-and-events.md` | Webhooks and events |
| `document-to-action-items/SKILL.md` | Extract cited obligations, deadlines, tasks from documents. |
| `docx/LICENSE` | Software license text |
| `docx/SKILL.md` | Create, read, edit, template, and review Word .docx files. |
| `docx/references/revisions-and-comments.md` | Revisions and Comments — XML details |
| `docx/scripts/docx_comments.py` | List, add, and delete comments in a .docx. |
| `docx/scripts/docx_common.py` | Shared helpers: paragraph iteration and run-preserving text replacement. |
| `docx/scripts/docx_create.py` | Create a .docx document from a JSON spec. |
| `docx/scripts/docx_edit.py` | Edit an existing .docx in place (or to a new file). |
| `docx/scripts/docx_read.py` | Read a .docx: text, structure outline, styles, images, revision detection. |
| `docx/scripts/docx_revisions.py` | Inspect and resolve tracked changes (w:ins / w:del) in a .docx. |
| `docx/scripts/docx_template.py` | Fill {{placeholder}} tokens in a .docx from a JSON mapping. |
| `docx/scripts/docx_validate.py` | Health-check a .docx package and report issues as JSON. |
| `docx/tests/test_docx_skill.py` | Pytest suite proving create / read / edit / template round-trips. |
| `google-workspace/SKILL.md` | Gmail, Calendar, Drive, Docs, Sheets via gws CLI or Python. |
| `google-workspace/references/daily-brief.md` | Daily Brief (Gmail + Calendar) |
| `google-workspace/references/gmail-search-syntax.md` | Gmail Search Syntax |
| `google-workspace/scripts/_hermes_home.py` | Resolve HERMES_HOME for standalone skill scripts. |
| `google-workspace/scripts/google_api.py` | Google Workspace API CLI for Hermes Agent. |
| `google-workspace/scripts/gws_bridge.py` | Bridge between Hermes OAuth token and gws CLI. |
| `google-workspace/scripts/setup.py` | Google Workspace OAuth2 setup for Hermes Agent. |
| `maps/SKILL.md` | Geocode, POIs, routes, timezones via OpenStreetMap/OSRM. |
| `maps/scripts/maps_client.py` | maps_client.py - CLI tool for maps, geocoding, routing, POI search, and more. Uses only Python stdlib. Data from OpenStreetMap/Nominatim, Overpass API, OSRM, and TimeAPI.io. |
| `meeting-action-items/SKILL.md` | Turn meeting notes into cited decisions, owners, tickets. |
| `notion/SKILL.md` | Notion API + ntn CLI: pages, databases, markdown, Workers. |
| `notion/references/block-types.md` | Notion Block Types |
| `pdf/LICENSE` | Software license text |
| `pdf/SKILL.md` | PDF files: create, read, merge, fill, OCR, edit text. |
| `pdf/references/forms.md` | Building Fillable Forms: spec format and workflow |
| `pdf/references/nano-pdf-editing.md` | Natural-language PDF text editing with nano-pdf (merged from the nano-pdf skill) |
| `pdf/references/ocr-extraction.md` | OCR & Document Text Extraction (merged from the ocr-and-documents skill) |
| `pdf/scripts/_raster.py` | Shared page rasterizer with a fallback chain: pypdfium2 -> pdftoppm. |
| `pdf/scripts/extract_marker.py` | Extract text from documents using marker-pdf. High-quality OCR + layout analysis. |
| `pdf/scripts/extract_pymupdf.py` | Extract text from documents using pymupdf. Lightweight (~25MB), no models. |
| `pdf/scripts/pdf_create.py` | Create a PDF from a JSON spec using reportlab platypus. |
| `pdf/scripts/pdf_fill_form.py` | Fill AcroForm fields from a UTF-8 JSON file; optionally flatten. |
| `pdf/scripts/pdf_form_layout.py` | Validate a form-spec layout BEFORE building the PDF, with optional visual overlay rendering for review with a vision model. |
| `pdf/scripts/pdf_make_form.py` | Create a fillable AcroForm PDF from a JSON spec (reportlab canvas.acroForm). |
| `pdf/scripts/pdf_merge.py` | Merge multiple PDFs into one, optionally adding a bookmark per source file. |
| `pdf/scripts/pdf_meta.py` | Document metadata and file attachments for PDFs (pypdf). |
| `pdf/scripts/pdf_page_image.py` | Export PDF pages as PNG images at a chosen DPI. |
| `pdf/scripts/pdf_read.py` | Read a PDF: per-page text, tables, metadata, or form fields. JSON to stdout. |
| `pdf/scripts/pdf_secure.py` | Encrypt or decrypt a PDF with passwords (AES-256 via pypdf). |
| `pdf/scripts/pdf_split.py` | Extract page ranges from a PDF, optionally rotating and/or compressing pages. |
| `pdf/scripts/pdf_stamp.py` | Stamp text or an image at coordinates onto selected PDF pages. |
| `pdf/scripts/pdf_watermark.py` | Stamp/watermark every page of a PDF with page 1 of another PDF. |
| `pdf/tests/test_pdf_skill.py` | End-to-end tests for the pdf skill helper scripts. No network required. |
| `powerpoint/LICENSE` | Software license text |
| `powerpoint/SKILL.md` | Create, read, edit .pptx decks with python-pptx. |
| `powerpoint/scripts/pptx_create.py` | Create a .pptx presentation from a JSON deck spec. |
| `powerpoint/scripts/pptx_edit.py` | Edit a .pptx in place (or save to --output). |
| `powerpoint/scripts/pptx_from_template.py` | Build a deck from a .pptx template (brand deck) and fill placeholders. |
| `powerpoint/scripts/pptx_read.py` | Read a .pptx file: JSON outline, notes, or export embedded images. |
| `powerpoint/scripts/pptx_render.py` | Render every slide of a .pptx to per-slide PNG images. |
| `powerpoint/tests/test_powerpoint_skill.py` | End-to-end tests for the powerpoint skill helper scripts. |
| `product-price-monitor/SKILL.md` | Watch product, flight, or listing prices; alert on target. |
| `teams-meeting-pipeline/SKILL.md` | Teams meeting summaries, job replay, Graph subscriptions. |
| `weekly-review-planning/SKILL.md` | Weekly reset: commitments, stalled work, next-week plan. |
| `xlsx/LICENSE` | Software license text |
| `xlsx/SKILL.md` | Create, read, edit Excel .xlsx workbooks and CSVs. |
| `xlsx/references/restructuring.md` | Reference-aware restructuring (xlsx_restructure.py) |
| `xlsx/scripts/csv_to_xlsx.py` | Convert a CSV file to a styled .xlsx workbook with type inference. |
| `xlsx/scripts/xlsx_create.py` | Create an .xlsx workbook from a JSON spec. |
| `xlsx/scripts/xlsx_edit.py` | Edit an existing .xlsx workbook in place (or to --out). |
| `xlsx/scripts/xlsx_read.py` | Read an .xlsx workbook: inventory, JSON/CSV dumps, formula listing. |
| `xlsx/scripts/xlsx_recalc.py` | Recalculate a workbook's formulas headlessly with LibreOffice. |
| `xlsx/scripts/xlsx_restructure.py` | Reference-aware row/column insert and delete for .xlsx workbooks. |
| `xlsx/scripts/xlsx_to_csv.py` | Export one sheet of an .xlsx workbook to CSV. |
| `xlsx/tests/test_xlsx_skill.py` | End-to-end tests for the xlsx skill helper scripts. |

## `skills/research/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for academic research, paper discovery, literature review, domain reconnaissance, market data, content monitoring, and scientific knowledge retrieval. |
| `arxiv/SKILL.md` | Search arXiv papers by keyword, author, category, or ID. |
| `arxiv/scripts/search_arxiv.py` | Search arXiv and display results in a clean format. |
| `competitor-news-monitor/SKILL.md` | Watch named companies for material news; cited digests. |
| `grounded-citations/SKILL.md` | Ground answers and documents in cited, verifiable sources. |
| `grounded-citations/references/citation-formats.md` | Citation formats per output target |
| `grounded-citations/references/grounding-rationale.md` | Why numbered ledger ids (grounding research basis) |
| `grounded-citations/scripts/_hermes_home.py` | Resolve HERMES_HOME for standalone skill scripts. |
| `grounded-citations/scripts/sources.py` | Citation ledger for grounded answers and documents. |
| `llm-wiki/SKILL.md` | Karpathy's LLM Wiki: build/query interlinked markdown KB. |

## `skills/social-media/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for interacting with social platforms and social-media workflows — posting, reading, monitoring, and account operations. |
| `xurl/SKILL.md` | X/Twitter via xurl CLI: raw post search, posting, DM, media. |

## `skills/software-development/`

| File | What it does |
|---|---|
| `codebase-inspection/SKILL.md` | Inspect codebases w/ pygount: LOC, languages, ratios. |
| `dogfood/SKILL.md` | Exploratory QA of web apps: find bugs, evidence, reports. |
| `dogfood/references/issue-taxonomy.md` | Issue Taxonomy |
| `dogfood/templates/dogfood-report-template.md` | Dogfood QA Report |
| `github/SKILL.md` | GitHub via gh CLI: PRs, issues, reviews, repos, auth. |
| `github/references/auth.md` | GitHub Authentication Setup |
| `github/references/ci-troubleshooting.md` | CI Troubleshooting Quick Reference |
| `github/references/code-review.md` | GitHub Code Review |
| `github/references/conventional-commits.md` | Conventional Commits Quick Reference |
| `github/references/github-api-cheatsheet.md` | GitHub REST API Cheatsheet |
| `github/references/issue-to-pr.md` | GitHub Issue to Pull Request |
| `github/references/issues.md` | GitHub Issues Management |
| `github/references/pr-workflow.md` | GitHub Pull Request Workflow |
| `github/references/repo-management.md` | GitHub Repository Management |
| `github/references/review-output-template.md` | Review Output Template |
| `github/scripts/gh-env.sh` | GitHub environment detection helper for Hermes Agent skills. |
| `github/scripts/git-credential-token.py` | Print the first unambiguous GitHub token in a git credential-store file. |
| `github/templates/bug-report.md` | Bug Description |
| `github/templates/feature-request.md` | Feature Description |
| `github/templates/pr-body-bugfix.md` | Bug Description |
| `github/templates/pr-body-feature.md` | Summary |
| `hermes-agent-skill-authoring/SKILL.md` | Author in-repo SKILL.md files: frontmatter and structure. |
| `inspecting-hermes-desktop-dom/SKILL.md` | Read the live Hermes desktop DOM/CSS over CDP. |
| `node-inspect-debugger/SKILL.md` | Debug Node.js via --inspect + Chrome DevTools Protocol CLI. |
| `python-debugpy/SKILL.md` | Debug Python: pdb REPL + debugpy remote (DAP). |
| `requesting-code-review/SKILL.md` | Pre-commit review: security scan, quality gates, auto-fix. |
| `simplify-code/SKILL.md` | Parallel 4-agent cleanup of recent code changes. |
| `spike/SKILL.md` | Throwaway experiments to validate an idea before build. |
| `systematic-debugging/SKILL.md` | 4-phase root cause debugging: understand bugs before fixing. |
| `test-driven-development/SKILL.md` | TDD: enforce RED-GREEN-REFACTOR, tests before code. |

## `skills/web/`

| File | What it does |
|---|---|
| `DESCRIPTION.md` | Skills for reaching web content when direct access fails — blocked, paywalled, rate-limited, or bot-walled pages. |
| `blocked-page-recovery/SKILL.md` | Use when a fetch fails: 403/429, paywall, WAF, bot wall. |
| `blocked-page-recovery/scripts/recover_page.py` | Recover a blocked / paywalled / WAF'd page from third-party copies. |
