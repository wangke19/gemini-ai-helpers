# Workspaces Plugin

**Isolated git worktree workspaces for multi-repo development.**

Work on features spanning multiple repositories without branch conflicts. Each task gets its own directory with synchronized worktrees—delete everything at once when done.

```bash
/workspaces:create New field in azure machine template
# Creates workspace with worktrees for machine-api-operator, machine-api-provider-azure,
# api, client-go. All on fresh branch off origin/main.

/workspaces:delete new-field-in-azure-machine-template
# Clean up when done
```

**Customizable:** Define aliases, auto-include rules (e.g., azure work → include related repos), and naming conventions for your team.

## Commands

| Command | Description |
|---------|-------------|
| `/workspaces:create` | Create workspace with git worktrees for specified repos |
| `/workspaces:delete` | Remove workspace (checks for uncommitted/unpushed work) |

---

## Setup

First run prompts for two paths:
- **Git repos root**: Where your repos are cloned (e.g., `~/git`)
- **Workspaces root**: Where workspaces are created (e.g., `~/workspaces`)

Config stored in `~/.gemini/extensions/config/workspaces/config.env`.

To reconfigure:
```bash
rm ~/.gemini/extensions/config/workspaces/config.env
# Next command will prompt for new paths
```

## How It Works

**Git worktrees** let you check out multiple branches of the same repo simultaneously. This plugin:

1. Creates a dedicated directory for your task
2. Adds worktrees for each repository (all on the same feature branch)
3. Copies template files (customize in `${GEMINI_WORKSPACES_ROOT}/.template/`)
4. Creates a `GEMINI.md` with workspace context

**Workspace structure:**
```
${GEMINI_WORKSPACES_ROOT}/
├── .template/              # Template copied to new workspaces
└── TEAM-1234/              # Your workspace
    ├── GEMINI.md           # Context for Gemini
    ├── frontend/           # Git worktree (branch: TEAM-1234)
    └── backend/            # Git worktree (branch: TEAM-1234)
```

**Benefits:**
- Isolated environments per task (no branch switching in main repos)
- Atomic workspace deletion (clean up everything at once)
- Shared branches across repos (consistent naming)
- Template customization (add scripts, configs, etc.)

## Customization

**Custom aliases and auto-detect rules:**

A template file `~/.gemini/extensions/config/workspaces/custom-prompt.md.template` is created on first setup.

To customize for your team:
```bash
cd ~/.gemini/extensions/config/workspaces
cp custom-prompt.md.template custom-prompt.md
# Edit custom-prompt.md to add your team's aliases and auto-detect rules
```

Example customizations:
- Repository name aliases (e.g., `FE` → `frontend`)
- Auto-detect rules (e.g., when `frontend` is selected, also add `shared-components`)

**Template customization:**

Add files to all new workspaces:
```bash
cd ${GEMINI_WORKSPACES_ROOT}/.template
# Add your .gitignore, scripts, etc.
```

## Requirements

- `git` v2.5+ (worktree support)
- `bash` v4.0+
- `gh` CLI (optional, for PR checkout)
- Linux or macOS
