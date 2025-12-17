# Files & Branches (via API)

These operations use `gh api` to match GitHub MCP server functionality.

## Get File Contents

```bash
# Get file contents (base64 encoded)
gh api repos/OWNER/REPO/contents/PATH --jq '.content' | base64 -d

# Get file from specific branch
gh api repos/OWNER/REPO/contents/PATH?ref=BRANCH --jq '.content' | base64 -d

# Get directory listing
gh api repos/OWNER/REPO/contents/PATH --jq '.[].name'

# Get raw file download URL
gh api repos/OWNER/REPO/contents/PATH --jq '.download_url'
```

## Create or Update File

```bash
# Create new file
CONTENT=$(echo "file content" | base64)
gh api repos/OWNER/REPO/contents/PATH \
  --method PUT \
  --field message="Create file" \
  --field content="$CONTENT" \
  --field branch="BRANCH"

# Update existing file (need current SHA)
SHA=$(gh api repos/OWNER/REPO/contents/PATH --jq '.sha')
CONTENT=$(echo "new content" | base64)
gh api repos/OWNER/REPO/contents/PATH \
  --method PUT \
  --field message="Update file" \
  --field content="$CONTENT" \
  --field sha="$SHA" \
  --field branch="BRANCH"

# Delete file
SHA=$(gh api repos/OWNER/REPO/contents/PATH --jq '.sha')
gh api repos/OWNER/REPO/contents/PATH \
  --method DELETE \
  --field message="Delete file" \
  --field sha="$SHA"
```

## Push Multiple Files

```bash
# For multiple files, use git tree API:

# 1. Get current commit SHA
COMMIT_SHA=$(gh api repos/OWNER/REPO/git/refs/heads/BRANCH --jq '.object.sha')

# 2. Get tree SHA
TREE_SHA=$(gh api repos/OWNER/REPO/git/commits/$COMMIT_SHA --jq '.tree.sha')

# 3. Create new tree with multiple files
NEW_TREE=$(gh api repos/OWNER/REPO/git/trees --method POST \
  --field base_tree="$TREE_SHA" \
  -f 'tree[][path]=file1.txt' \
  -f 'tree[][mode]=100644' \
  -f 'tree[][content]=content1' \
  -f 'tree[][path]=file2.txt' \
  -f 'tree[][mode]=100644' \
  -f 'tree[][content]=content2' \
  --jq '.sha')

# 4. Create commit
NEW_COMMIT=$(gh api repos/OWNER/REPO/git/commits --method POST \
  --field message="Add multiple files" \
  --field tree="$NEW_TREE" \
  --field 'parents[]'="$COMMIT_SHA" \
  --jq '.sha')

# 5. Update branch reference
gh api repos/OWNER/REPO/git/refs/heads/BRANCH --method PATCH \
  --field sha="$NEW_COMMIT"
```

## Branches

### List Branches
```bash
gh api repos/OWNER/REPO/branches --jq '.[].name'
gh api repos/OWNER/REPO/branches/BRANCH
```

### Create Branch
```bash
# Get SHA of source branch
SHA=$(gh api repos/OWNER/REPO/git/refs/heads/main --jq '.object.sha')

# Create new branch
gh api repos/OWNER/REPO/git/refs --method POST \
  --field ref="refs/heads/NEW_BRANCH" \
  --field sha="$SHA"
```

### Delete Branch
```bash
gh api repos/OWNER/REPO/git/refs/heads/BRANCH --method DELETE
```

### Branch Protection
```bash
# Get protection rules
gh api repos/OWNER/REPO/branches/BRANCH/protection

# Set protection (requires admin)
gh api repos/OWNER/REPO/branches/BRANCH/protection --method PUT \
  --field required_status_checks='{"strict":true,"contexts":["ci"]}' \
  --field enforce_admins=true
```

## Commits

### List Commits
```bash
# List commits on default branch
gh api repos/OWNER/REPO/commits --jq '.[] | {sha: .sha[:7], message: .commit.message}'

# List commits on specific branch
gh api repos/OWNER/REPO/commits?sha=BRANCH --jq '.[] | {sha: .sha[:7], message: .commit.message}'

# List commits by author
gh api repos/OWNER/REPO/commits?author=USERNAME

# Get specific commit
gh api repos/OWNER/REPO/commits/SHA

# Get commit diff
gh api repos/OWNER/REPO/commits/SHA --jq '.files[] | {filename, status, changes}'
```

### Compare Commits
```bash
gh api repos/OWNER/REPO/compare/BASE...HEAD --jq '.commits[].commit.message'
gh api repos/OWNER/REPO/compare/BASE...HEAD --jq '.files[].filename'
```
