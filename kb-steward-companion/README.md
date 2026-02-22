# KB Steward Companion

**Query and update Obsidian vault tasks via obsidian-cli**

A skill for managing tasks and projects in an Obsidian vault using structured frontmatter and tag-based filtering. Ideal for agents that need to track work, update project status, or query tasks by category.

## Features

- **Tag-based task search**: Query tasks by hierarchical tags (area/, type/, service/)
- **Frontmatter operations**: Safe YAML manipulation via `obsidian-cli`
- **Priority views**: Filter projects by priority (P0-P3)
- **Status management**: Update project status (backlog → in_progress → done → archived)
- **Dynamic tag discovery**: Automatically discovers all tags in your vault

## Prerequisites

### 1. Install obsidian-cli

```bash
brew install yakitrak/yakitrak/obsidian-cli
```

### 2. Configure your vault

```bash
# Set your vault as default
obsidian-cli set-default <vault-name> <vault-path>

# Example:
# obsidian-cli set-default kb-steward ~/Documents/kb-steward

# Verify
obsidian-cli print-default
```

### 3. Verify installation

```bash
# Should show your vault info
obsidian-cli print-default

# Should search content
obsidian-cli search-content "test"
```

## Installation

1. Copy this skill to your OpenClaw skills directory
2. The skill is self-contained and ready to use

## Usage

See `SKILL.md` for complete usage guide. Quick examples:

```bash
# Search tasks
scripts/todo.sh area/integration

# Update status
scripts/status.sh "My Project" done

# Browse tags
scripts/tags.sh area

# View by priority
scripts/prio.sh P0
```

## Tag System

This skill uses a hierarchical tag system:

- **area/**: Domain categories (integration, telegram, memory, etc.)
- **type/**: Task types (research, implementation, creation, etc.)
- **service/**: Specific services (gemini-local, etc.)

See `references/TAGS.md` for complete taxonomy.

## Project Format

Projects use YAML frontmatter:

```yaml
---
title: "Project Name"
status: backlog
prio: P2
created: 2026-02-21
tags:
  - area/integration
  - type/implementation
---

# Goal

[Describe objective]

## Tasks

- [ ] Task 1
- [ ] Task 2
```

See `references/PROJECT_TEMPLATE.md` for complete template.

## Troubleshooting

### "obsidian-cli: command not found"

Install via Homebrew:
```bash
brew install yakitrak/yakitrak/obsidian-cli
```

### "Cannot find note in vault"

Check your vault configuration:
```bash
obsidian-cli print-default
```

### Tags not discovered

Ensure your project files use the `tags:` field in YAML frontmatter.

## File Structure

```
kb-steward-companion/
├── README.md                 # This file (human documentation)
├── SKILL.md                  # Agent documentation (router)
├── scripts/
│   ├── todo.sh               # Query tasks by tag
│   ├── tags.sh               # Browse tag categories
│   ├── status.sh             # Update project status
│   └── prio.sh               # View by priority
└── references/
    ├── SETUP.md              # First-time setup guide
    ├── TAGS.md               # Complete tag taxonomy
    ├── FRONTMATTER.md        # Frontmatter operations
    └── PROJECT_TEMPLATE.md  # Project creation template
```

## License

Part of the OpenClaw ecosystem. Use freely in your workflows.
