# File reference: `acp_adapter`

One line per file. Descriptions are taken from each file's own docstring, header
comment, frontmatter or first heading; where a file has none, the description is
derived from its name and type. Back to the [file-reference index](README.md).

| File | What it does |
|---|---|
| `__init__.py` | ACP (Agent Communication Protocol) adapter for hermes-agent. |
| `__main__.py` | Allow running the ACP adapter as ``python -m acp_adapter``. |
| `auth.py` | ACP auth helpers — detect and advertise Hermes authentication methods. |
| `catalog.py` | ACP historical catalog without storage initialization or an execution owner. |
| `commands.py` | Headless slash commands for ACP sessions (``/help``, ``/model``, ``/compress`` ...). |
| `content.py` | ACP prompt content blocks -> Hermes/OpenAI user-content payloads (text, images, resources). |
| `edit_approval.py` | Pre-execution ACP edit approval helpers. |
| `elicitation.py` | A canonical ``clarify`` prompt in an ACP editor, answered through ``clarify.respond``. |
| `entry.py` | CLI entry point for the hermes-agent ACP adapter. |
| `events.py` | Callback factories for bridging AIAgent events to ACP notifications. |
| `gateway_commands.py` | Editor slash commands on the gateway path; each one is an existing gateway verb. |
| `gateway_media.py` | Editor prompt content -> ``prompt.submit`` text and staged image attachments (ACP gateway bridge). |
| `gateway_reply.py` | How a gateway turn's reply reaches the editor: ``messageId`` grouping, exactly-once final text, tool and permission bubbles closed as the in-process agent closed them. Mixed into ``GatewayACPAgent``, whose state (``_con… |
| `gateway_server.py` | ACP projection of the profile gateway; never constructs an execution owner. |
| `gateway_session_meta.py` | Editor session metadata on the gateway path, projected from the gateway's existing reads. |
| `model_catalog.py` | ACP model picker: deduplicated ``provider:model`` rows from the Hermes inventory + named endpoints. |
| `modes.py` | ACP's edit modes, one table for the in-process server and the gateway path. |
| `permissions.py` | ACP permission bridging for Hermes dangerous-command approvals. |
| `provenance.py` | Derive ACP session-provenance metadata from the existing compression chain. |
| `server.py` | ACP agent server — exposes Hermes Agent via the Agent Client Protocol. |
| `session.py` | ACP session manager — maps ACP sessions to Hermes AIAgent instances. |
| `tools.py` | ACP tool-call helpers for mapping hermes tools to ACP ToolKind and building content. |
