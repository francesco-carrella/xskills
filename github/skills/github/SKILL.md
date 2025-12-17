---
name: github-cli
description: This skill provides GitHub CLI (gh) operations for repository management, issues, pull requests, releases, actions, and more. Use this skill when the user needs to interact with GitHub repositories, create or manage issues/PRs, work with GitHub Actions, manage releases, or perform any GitHub platform operations.
---

# GitHub CLI Operations

Interact with GitHub using the `gh` CLI. Already authenticated and more efficient than API calls.

## Quick Start

```bash
# Check authentication
gh auth status

# Get help on any command
gh <command> --help
```

## Operation Categories

| Category | Description | Reference |
|----------|-------------|-----------|
| **Repos** | Create, clone, fork, view, edit repositories | [references/repos.md](references/repos.md) |
| **Files & Branches** | File contents, create/update files, branches, commits | [references/files-branches.md](references/files-branches.md) |
| **Issues & PRs** | Create, list, edit, review, merge | [references/issues-prs.md](references/issues-prs.md) |
| **Actions** | Workflows, runs, caching | [references/actions.md](references/actions.md) |
| **Releases & Gists** | Create releases, manage gists | [references/releases-gists.md](references/releases-gists.md) |
| **Projects** | GitHub Projects management | [references/projects.md](references/projects.md) |
| **Advanced** | Codespaces, secrets, labels, orgs | [references/advanced.md](references/advanced.md) |

## Common Workflows

### Create Feature Branch + PR

```bash
git checkout -b feature/my-feature
# make changes
git add . && git commit -m "feat: add feature"
git push -u origin feature/my-feature
gh pr create --title "feat: add feature" --body "Description"
```

### Review and Merge PR

```bash
gh pr checkout 123
gh pr review 123 --approve
gh pr merge 123 --squash --delete-branch
```

### Fix an Issue

```bash
gh issue view 456
gh issue edit 456 --add-assignee "@me"
git checkout -b fix/issue-456
# fix the issue
gh pr create --title "fix: resolve #456" --body "Closes #456"
```

## Quick Reference

### Repository
```bash
gh repo list [OWNER]
gh repo view [OWNER/REPO]
gh repo clone OWNER/REPO
gh repo create NAME --public|--private
gh repo fork OWNER/REPO
```

### Issues
```bash
gh issue list [--state open|closed] [--label LABEL]
gh issue view NUMBER
gh issue create --title "Title" --body "Body"
gh issue close NUMBER
```

### Pull Requests
```bash
gh pr list [--state open|merged|closed]
gh pr view NUMBER
gh pr create --title "Title" --body "Body"
gh pr checkout NUMBER
gh pr review NUMBER --approve|--request-changes
gh pr merge NUMBER --squash|--rebase|--merge
```

### Releases
```bash
gh release list
gh release view TAG
gh release create TAG --title "Title" --notes "Notes"
gh release download TAG
```

### Actions
```bash
gh run list [--workflow NAME]
gh run view RUN_ID [--log]
gh run watch RUN_ID
gh workflow list
gh workflow run WORKFLOW
```

## API Access

For operations not covered by `gh` commands:

```bash
# GET request
gh api repos/OWNER/REPO

# POST request
gh api repos/OWNER/REPO/issues --method POST \
  --field title="Issue" --field body="Body"

# GraphQL
gh api graphql -f query='{ viewer { login } }'

# Parse JSON
gh api repos/OWNER/REPO --jq '.full_name'
```

## Output Formatting

```bash
# JSON output
gh issue list --json number,title,state

# Custom format with jq
gh pr list --json number,title | jq '.[].title'

# Quiet (IDs only)
gh issue list --json number --jq '.[].number'
```

## Tips

1. Use `--help` on any command for options
2. Use `--json` for scriptable output
3. Use `gh api` for any GitHub API endpoint
4. PRs auto-link issues with "Closes #123" in body
5. `@me` refers to authenticated user
