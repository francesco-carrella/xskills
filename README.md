# xskills

Token-efficient Claude Skills to replace heavy MCP servers. **Save 90%+ context** by using Skills instead of MCP.

## Available Skills

| Plugin | Replaces | Token Savings |
|--------|----------|---------------|
| `github` | @modelcontextprotocol/server-github | ~18k tokens |
| `archon` | Archon MCP server | ~12k tokens |

## Installation

### Add Marketplace
```
/plugin marketplace add francesco-carrella/xskills
```

### Install Individual Skills

**GitHub only:**
```
/plugin install github@xskills
```

**Archon only:**
```
/plugin install archon@xskills
```

**Both:**
```
/plugin install github@xskills
/plugin install archon@xskills
```

## Skills

### 🐙 github

Complete GitHub operations via `gh` CLI.

**Requirements:** `gh` CLI installed and authenticated (`gh auth login`)

**Covers:**
- Repositories: list, search, create, fork, clone
- Issues: list, search, create, edit, comment, close
- Pull Requests: create, review, merge, checkout, diff
- Code: search, view files, create/update files
- Branches: list, create, delete
- Actions: list runs, view logs, trigger workflows
- Releases & Gists

### 📋 archon

Interact with [Archon](https://github.com/coleam00/Archon) knowledge management system via REST API.

**Requirements:** Archon server running (default: `http://100.91.166.2:8181`)

**Covers:**
- RAG: search knowledge base, code examples, read pages
- Projects: CRUD operations, features
- Tasks: create, update status, assign
- Documents: project documentation management
- Versions: history and rollback

## Why Skills over MCP?

| Aspect | MCP | Skills |
|--------|-----|--------|
| **Idle tokens** | Thousands always loaded | ~100 until needed |
| **Active tokens** | Same thousands | ~3-5k when used |
| **Flexibility** | Fixed tool definitions | Claude generates code |

## Manual Installation

If you prefer not to use the plugin system:

```bash
git clone https://github.com/francesco-carrella/xskills
cp -r xskills/github/skills/github ~/.claude/skills/
cp -r xskills/archon/skills/archon ~/.claude/skills/
```

## Customization

### Archon URL
Edit the skill at `~/.claude/skills/archon/SKILL.md` and update:
```
**Base URL**: `http://YOUR_HOST:8181`
```

## License

MIT
