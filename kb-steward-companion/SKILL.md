---
name: kb-steward-companion
description: Query and update Obsidian vault tasks via obsidian-cli. Use when: (1) Searching tasks by tags (area/integration, type/research, etc.), (2) Updating project status in frontmatter, (3) Creating/deleting project notes, (4) Browsing tag categories. Prefer for structured frontmatter operations over raw sed/grep.
---

# KB Steward Companion

Quick task and project management for Obsidian vault using `obsidian-cli`.

## Prerequisites

Before using this skill, ensure `obsidian-cli` is installed. If not, follow the initialization steps in `references/SETUP.md`.

## Interface

```bash
# Query tasks
scripts/todo.sh [tag]

# Browse tags (dynamic - generated at runtime)
scripts/tags.sh [category]

# Update status
scripts/status.sh <project> <status>

# Priority view
scripts/prio.sh [P0-P3]
```

## Which references to read

- Always read: `references/TAGS.md` (tag taxonomy)
- If user asks about frontmatter: read `references/FRONTMATTER.md`
- If user asks about creating projects: read `references/PROJECT_TEMPLATE.md`
- First-time setup: read `references/SETUP.md`

## Global guardrails

- Never modify frontmatter without explicit user confirmation
- Always show full `obsidian-cli` command before execution
- Use `~` paths in all documentation
- Verify vault configuration before operations

## Tag categories (discovered at runtime)

This skill uses a hierarchical tag system:

- **area/**: Domain (integration, telegram, memory, model-serving, etc.)
- **type/**: Task type (research, implementation, creation, done, etc.)
- **service/**: Specific services (gemini-local, etc.)

Run `scripts/tags.sh` to discover all tags in your vault.

## Common workflows

### Search tasks by tag

```bash
scripts/todo.sh area/integration
scripts/todo.sh type/research
scripts/todo.sh service/gemini-local
```

### Update project status

```bash
scripts/status.sh "Project Name" done
```

Valid statuses: `backlog`, `in_progress`, `done`, `archived`

### View by priority

```bash
scripts/prio.sh P0
scripts/prio.sh P1
```

## Frontmatter operations (via obsidian-cli)

```bash
# Read
obsidian-cli frontmatter "Project Name" --print

# Update
obsidian-cli frontmatter "Project Name" --edit --key "status" --value "done"

# Delete
obsidian-cli frontmatter "Project Name" --delete --key "due"
```

See `references/FRONTMATTER.md` for complete guide.

## Configuration

The skill automatically discovers your Obsidian vault:

- Checks `obsidian-cli print-default` for current vault
- Uses `~/Library/Application Support/obsidian-cli/` or `~/.config/obsidian-cli/` for config
- Default vault name: stored in preferences

No manual configuration needed if `obsidian-cli` is properly set up.
