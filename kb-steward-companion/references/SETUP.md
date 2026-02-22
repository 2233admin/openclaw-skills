# Initial Setup Guide

First-time configuration for `obsidian-cli` to work with this skill.

## Step 1: Install obsidian-cli

### macOS (Homebrew)

```bash
brew install yakitrak/yakitrak/obsidian-cli
```

### Linux

```bash
# Install via npm
npm install -g obsidian-cli

# Or build from source
git clone https://github.com/yakitrak/obsidian-cli
cd obsidian-cli
cargo install --path .
```

### Verify installation

```bash
obsidian-cli --version
# Should output: obsidian-cli version v0.2.2 or similar
```

## Step 2: Locate your Obsidian vault

Find the path to your Obsidian vault:

1. Open Obsidian app
2. Open the vault you want to use
3. Open Settings → About → Click "Open folder" (or similar)
4. Copy the folder path

Example paths:
- macOS: `~/Documents/Knowledge`
- Linux: `~/Documents/kb-steward`

## Step 3: Configure obsidian-cli

### Set default vault

```bash
obsidian-cli set-default <vault-name> <vault-path>
```

**Example**:
```bash
obsidian-cli set-default kb-steward ~/Documents/kb-steward
```

### Verify configuration

```bash
obsidian-cli print-default
```

Expected output:
```
Default vault name:  kb-steward
Default vault path:  /Users/yourname/Documents/kb-steward
```

## Step 4: Verify vault accessibility

```bash
# Test search (should find any matching content)
obsidian-cli search-content "test"

# Test frontmatter read (if you have any notes)
obsidian-cli frontmatter "Note Name" --print
```

## Step 5: Configure skill scripts (optional)

The scripts in this skill should work out-of-the-box if `obsidian-cli` is configured correctly. However, you can customize these environment variables if needed:

### VAULT_ROOT

The scripts automatically detect your vault path via:
```bash
obsidian-cli print-default
```

Manual override (not recommended):
```bash
export VAULT_ROOT="~/path/to/vault"
```

## Troubleshooting

### "Command not found: obsidian-cli"

- Ensure installation completed successfully
- Check your PATH: `echo $PATH`
- Restart your terminal after installation

### "Cannot find note in vault"

- Verify vault path with `obsidian-cli print-default`
- Ensure the note exists in your vault
- Use partial name match (obsidian-cli uses fuzzy search)

### "Vault not found in Obsidian config"

- Ensure you've opened the vault in Obsidian app at least once
- Check that the vault path is correct
- Try setting default vault again

### Permissions issues (Linux)

If you get permission errors:
```bash
# Make scripts executable
chmod +x scripts/*.sh
```

## Next steps

Once setup is complete:

1. Create your first project using `PROJECT_TEMPLATE.md`
2. Query tasks with `scripts/todo.sh`
3. Browse tags with `scripts/tags.sh`

See `SKILL.md` for complete usage guide.
