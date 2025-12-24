# Create and Distribute a Plugin Marketplace

Build and host plugin marketplaces to distribute Claude Code extensions across teams and communities.

## Overview

A plugin marketplace is a catalog that lets you distribute plugins to others. Marketplaces provide centralized discovery, version tracking, automatic updates, and support for multiple source types.

Creating and distributing a marketplace involves:

1. **Creating plugins**: Build plugins with commands, agents, hooks, MCP servers, or LSP servers
2. **Creating a marketplace file**: Define `marketplace.json` listing your plugins
3. **Host the marketplace**: Push to GitHub, GitLab, or another git host
4. **Share with users**: Users add your marketplace with `/plugin marketplace add`

## Quick Start

### 1. Create the directory structure

```bash
mkdir -p my-marketplace/.claude-plugin
mkdir -p my-marketplace/plugins/review-plugin/.claude-plugin
mkdir -p my-marketplace/plugins/review-plugin/commands
```

### 2. Create a plugin command

```markdown
# my-marketplace/plugins/review-plugin/commands/review.md

Review the code I've selected or the recent changes for:
- Potential bugs or edge cases
- Security concerns
- Performance issues
- Readability improvements

Be concise and actionable.
```

### 3. Create the plugin manifest

```json
// my-marketplace/plugins/review-plugin/.claude-plugin/plugin.json
{
  "name": "review-plugin",
  "description": "Adds a /review command for quick code reviews",
  "version": "1.0.0"
}
```

### 4. Create the marketplace file

```json
// my-marketplace/.claude-plugin/marketplace.json
{
  "name": "my-plugins",
  "owner": {
    "name": "Your Name"
  },
  "plugins": [
    {
      "name": "review-plugin",
      "source": "./plugins/review-plugin",
      "description": "Adds a /review command for quick code reviews"
    }
  ]
}
```

### 5. Add and install

```shell
/plugin marketplace add ./my-marketplace
/plugin install review-plugin@my-plugins
```

## Marketplace Schema

### Required Fields

| Field | Type | Description |
|:------|:-----|:------------|
| `name` | string | Marketplace identifier (kebab-case). Users see this when installing: `/plugin install tool@marketplace-name` |
| `owner` | object | Maintainer information (`name` required, `email` optional) |
| `plugins` | array | List of available plugins |

### Optional Metadata

| Field | Type | Description |
|:------|:-----|:------------|
| `metadata.description` | string | Brief marketplace description |
| `metadata.version` | string | Marketplace version |
| `metadata.pluginRoot` | string | Base directory for relative plugin paths |

## Plugin Entries

Each plugin entry needs at minimum a `name` and `source`:

```json
{
  "name": "code-formatter",
  "source": "./plugins/formatter",
  "description": "Automatic code formatting on save",
  "version": "2.1.0",
  "author": {
    "name": "DevTools Team"
  }
}
```

### Plugin Sources

**Relative paths** (same repository):
```json
{ "source": "./plugins/my-plugin" }
```

**GitHub repositories**:
```json
{
  "source": {
    "source": "github",
    "repo": "owner/plugin-repo"
  }
}
```

**Git URLs**:
```json
{
  "source": {
    "source": "url",
    "url": "https://gitlab.com/team/plugin.git"
  }
}
```

## Host and Distribute

### GitHub (Recommended)

1. Create a repository for your marketplace
2. Add `.claude-plugin/marketplace.json`
3. Users add with `/plugin marketplace add owner/repo`

### Other Git Services

Any git host works:

```shell
/plugin marketplace add https://gitlab.com/company/plugins.git
```

### Test Locally First

```shell
/plugin marketplace add ./my-local-marketplace
/plugin install test-plugin@my-local-marketplace
```

## Configure for Teams

Add marketplace to `.claude/settings.json` so team members are prompted to install:

```json
{
  "extraKnownMarketplaces": {
    "company-tools": {
      "source": {
        "source": "github",
        "repo": "your-org/claude-plugins"
      }
    }
  },
  "enabledPlugins": {
    "code-formatter@company-tools": true
  }
}
```

## Plugin Components

Plugins can include:

| Component | Description |
|:----------|:------------|
| `commands` | Slash commands (markdown files) |
| `agents` | Specialized AI agents |
| `hooks` | Pre/post tool use automation |
| `mcpServers` | Model Context Protocol servers |
| `lspServers` | Language Server Protocol servers |
| `skills` | Reusable capability definitions |

### Using Plugin Root Variable

Reference files within the plugin's installation directory:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PLUGIN_ROOT}/scripts/validate.sh"
          }
        ]
      }
    ]
  }
}
```

## Validation

Test your marketplace before sharing:

```bash
claude plugin validate .
```

Or from within Claude Code:

```shell
/plugin validate .
```

## File Resolution

When users install a plugin, Claude Code copies the plugin directory to a cache location. This means:

- Plugins can't reference files outside their directory using `../` paths
- Use symlinks (followed during copying) to share files across plugins
- Or restructure so shared directories are inside the plugin source path

## Troubleshooting

### Marketplace Not Loading

- Verify marketplace URL is accessible
- Check `.claude-plugin/marketplace.json` exists
- Validate JSON syntax with `claude plugin validate`
- For private repos, confirm access permissions

### Plugin Installation Failures

- Verify plugin source URLs are accessible
- Check plugin directories contain required files
- For GitHub sources, ensure repos are public or you have access
- Test by cloning/downloading manually

### Files Not Found After Installation

Cause: Plugins are copied to cache; paths outside plugin directory won't work.

Solutions:
- Use symlinks (followed during copying)
- Restructure directories
- Use `${CLAUDE_PLUGIN_ROOT}` for internal references

---

*The tool recedes; the methodology propagates.*
