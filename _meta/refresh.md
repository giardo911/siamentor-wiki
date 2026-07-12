# Wiki Refresh Policy

Updated: 2026-07-12

SiaMentor wiki now has two layers:

- raw/source layer: `daily/`, `design/`, `strategy/`, `project-checklist.md`;
- agent context layer: `_agent_context/`.

The raw layer stores history and evidence. The agent context layer stores current compact truth for future agent turns.

## Update rules

- Add detailed daily/design notes to the raw layer.
- Update `_agent_context/` only when current direction, metrics, backlog, decisions, or source authority changed.
- Do not duplicate long daily notes inside `_agent_context/`.
- Keep `_agent_context/` short enough to read at the start of a task.

## OpenWiki-style goal

The goal is not to adopt a vendor-specific format. The goal is a maintainable Markdown brain:

`raw notes -> curated current state -> agent instructions -> verifiable diffs`

