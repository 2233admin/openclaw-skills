# KB Steward Companion

**Query and maintenance tools for kb-steward managed vaults**

A companion skill providing task query, tag browsing, and project management utilities for Obsidian vaults managed by `kb-steward`. This skill extends `kb-steward`'s ingestion capabilities with day-to-day maintenance operations.

## Relationship to kb-steward

- **`kb-steward`**: Primary skill for ingesting URLs/snippets into the knowledge base, organizing them into Projects/Areas/Research folders with proper frontmatter and taxonomy.
- **`kb-steward-companion`** (this skill): Utility tools for querying, updating status, and browsing the knowledge base that `kb-steward` creates.

Think of it as: `kb-steward` writes to your KB, `kb-steward-companion` helps you read and maintain it.

## Features

- **Task query**: Search tasks by tags (area/, type/, service/) across Projects
- **Status management**: Update project status via safe frontmatter operations
- **Tag browsing**: Discover all tags in your vault dynamically
- **Priority views**: Filter projects by priority (P0-P3)
- **Frontmatter ops**: Safe YAML manipulation via `obsidian-cli`
- **Note deletion**: Delete notes with automatic backup (.bak)

## Prerequisites

### 1. Install obsidian-cli

```bash
brew install yakitrak/yakitrak/obsidian-cli
```

### 2. Configure your vault

Your vault should follow the `kb-steward` structure:

```
knowledge/
├── 00-Inbox/
├── 10-Projects/     # Tasks managed by companion scripts
├── 20-Areas/        # Durable principles
├── 30-Research/     # Analysis and notes
└── 99-Templates/
```

Configure `obsidian-cli`:

```bash
# Set your vault as default
obsidian-cli set-default <vault-name> <vault-path>

# Example for kb-steward structure:
# obsidian-cli set-default kb-steward ~/workspace-main/knowledge

# Verify
obsidian-cli print-default
```

See `references/SETUP.md` for complete setup guide.

## Usage

This skill provides scripts that work with `kb-steward`'s folder structure:

```bash
# Query tasks in 10-Projects/
scripts/todo.sh area/integration

# Update project status
scripts/status.sh "Project Name" done

# Browse tags across entire vault
scripts/tags.sh area

# View Projects by priority
scripts/prio.sh P0

# Delete a note (with backup)
scripts/delete.sh "Project Name"
```

## Integration with kb-steward

### Tag compatibility

This companion uses the same tag taxonomy that `kb-steward` establishes:

- **area/**: Domain categories that `kb-steward` assigns
- **type/**: Task types (research, implementation, creation)
- **service/**: Specific service integrations

When `kb-steward` ingests a URL and creates a project note, this companion can immediately query it.

### Workflow example

1. **`kb-steward`** ingests a task:
   ```
   /kb-steward add https://example.com --kind project
   → Creates 10-Projects/integrate-example.md with tags
   ```

2. **`kb-steward-companion`** queries and updates:
   ```bash
   scripts/todo.sh area/integration
   → Shows the newly created project

   scripts/status.sh "integrate-example" in_progress
   → Updates status safely via frontmatter
   ```

## File Structure

```
kb-steward-companion/
├── README.md                 # This file
├── SKILL.md                  # Agent documentation
├── scripts/
│   ├── todo.sh               # Query tasks by tag
│   ├── tags.sh               # Browse tag categories
│   ├── status.sh             # Update project status
│   └── prio.sh               # View by priority
└── references/
    ├── SETUP.md              # First-time setup guide
    ├── TAGS.md               # Tag taxonomy (matches kb-steward)
    ├── FRONTMATTER.md        # Frontmatter operations
    └── PROJECT_TEMPLATE.md  # Project creation template
```

## Scope

### This companion DOES:

- Query existing notes created by `kb-steward`
- Update frontmatter fields (status, priority, tags)
- Browse tag taxonomy
- Provide maintenance utilities

### This companion DOES NOT:

- Ingest new URLs/snippets (use `kb-steward add`)
- Create new folders/bootstrap structure (use `kb-steward bootstrap`)
- Manage taxonomy registry (use `kb-steward`'s decision logging)

## Troubleshooting

See `references/SETUP.md` for detailed troubleshooting.

Common issues:

- **"obsidian-cli: command not found"**: Install via Homebrew
- **"Cannot find note in vault"**: Check vault configuration
- **No tags discovered**: Ensure `kb-steward` has created notes with proper frontmatter

## License

Part of the OpenClaw kb-steward ecosystem. Use freely in your workflows.
