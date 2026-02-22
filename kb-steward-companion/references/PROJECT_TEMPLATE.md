# Project Template

Standard template for creating new project notes in the knowledge base.

## Quick create

```bash
# Using obsidian-cli
obsidian-cli create "Project Name" --content '...content...'

# Or create manually in your vault
# Open Obsidian → Create new note → Paste template
```

See `SETUP.md` for obsidian-cli installation and configuration.

## Field explanations

### Required fields
- **title**: Project name (must match filename)
- **status**: One of `backlog`, `in_progress`, `done`, `archived`
- **prio**: Priority level (`P0`-`P3`)
- **created**: Creation date (YYYY-MM-DD)
- **tags**: At least one `area/*` and one `type/*`

### Optional fields
- **due**: Deadline date
- **blocked_by**: Dependencies
- **related_docs**: Links to related notes

## Tag selection guide

### Choose area/* based on domain
- Integration work → `area/integration`
- OpenClaw core → `area/openclaw`
- Skills development → `area/skills`
- Debugging → `area/debugging`
- Agent persona → `area/agent-persona`
- Memory/Knowledge → `area/memory`

### Choose type/* based on activity
- Research/investigation → `type/research`
- Building something → `type/implementation`
- Creating new agent → `type/creation`
- Automation → `type/automation`

### Add service/* for specific services
- Gemini Local issues → `service/gemini-local`

## Example projects

### Integration project
```yaml
---
title: "接入 ChatPRD.ai"
status: backlog
prio: P1
created: 2026-02-05
tags:
  - area/integration
  - type/implementation
---
```

### Research project
```yaml
---
title: "研究 Epiral Agent OS"
status: in_progress
prio: P2
created: 2026-02-10
tags:
  - area/competitor-analysis
  - area/agent-os
  - type/research
---
```

### Bug fix project
```yaml
---
title: "修复 gemini-local 对 g3flash 的鉴权问题"
status: in_progress
prio: P0
created: 2026-02-10
tags:
  - area/model-serving
  - area/debugging
  - service/gemini-local
  - bug
---
```

## Tasks format

Use standard Markdown checkboxes:

```markdown
## Tasks

### Phase 1
- [ ] Subtask 1.1
- [ ] Subtask 1.2

### Phase 2
- [ ] Subtask 2.1
- [x] Completed task
```

The `scripts/todo.sh` tool will parse these checkboxes.
