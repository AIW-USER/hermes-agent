# File reference: `hermes_platform`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `AGENTS.md` | hermes_platform/ — machine facts and resource lookup |
| `__init__.py` | Machine facts and resource resolution for every Hermes surface. |
| `declaration.py` | Parse and register application requirements shared by MCP and skill offer-time gates. |
| `host/__init__.py` | Cached facts about the machine running this Python process. |
| `host/darwin_pci.py` | PCI display controllers on macOS, read from the IOKit registry. |
| `host/facts.py` | Cached OS, architecture, CPU, memory and GPU facts for the current machine. |
| `host/gpu_adapters.py` | Windows graphics adapters as DXGI reports them. |
| `host/products.py` | NVIDIA platform recognition derived from host facts. |
| `host/runtime.py` | Cached runtime-environment predicates for WSL, containers, and Termux. |
| `host/summary.py` | One summary of this machine and its OS account, for the desktop first-run onboarding. |
| `resolver/__init__.py` | Resource resolution: where a tool or application is, and what state it is in. |
| `resolver/app.py` | Desktop-application resolver over an `AppDef` (parsed from an MCP manifest's `app:` block). |
| `resolver/availability.py` | Whether a catalog entry can be offered on this host, from its `app` and `requires` blocks. |
| `resolver/base.py` | Resolver protocols and the results of the two non-passive tiers. |
| `resolver/core.py` | Result and context types shared by every resolver, plus passive command location. |
| `resolver/known_dirs.py` | Directories where tools install outside PATH, grouped by the ecosystem that owns them. |
