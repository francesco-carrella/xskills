# Issues & Pull Requests

## Issues

### List & Search
```bash
gh issue list
gh issue list --state open|closed
gh issue list --label "bug" --assignee "@me"
gh search issues "QUERY" --repo OWNER/REPO
```

### View
```bash
gh issue view NUMBER
gh issue view NUMBER --json title,body,state,labels
gh issue view NUMBER --comments
```

### Create & Edit
```bash
gh issue create --title "Title" --body "Description"
gh issue create --title "Title" --label "bug" --assignee "@me"
gh issue edit NUMBER --title "New Title"
gh issue edit NUMBER --add-label "priority"
gh issue comment NUMBER --body "Comment"
```

### Status & Close
```bash
gh issue status
gh issue close NUMBER
gh issue close NUMBER --reason "not planned"
gh issue reopen NUMBER
gh issue delete NUMBER --yes
```

### Develop (Linked Branches)
```bash
gh issue develop NUMBER
gh issue develop NUMBER --name "feature-branch" --checkout
gh issue develop NUMBER --list
```

### Lock & Pin
```bash
gh issue lock NUMBER --reason "resolved"
gh issue unlock NUMBER
gh issue pin NUMBER
gh issue unpin NUMBER
gh issue transfer NUMBER DEST_REPO
```

## Pull Requests

### List & Search
```bash
gh pr list
gh pr list --state open|merged|closed
gh pr list --author "@me" --base main
gh search prs "QUERY" --repo OWNER/REPO
```

### View
```bash
gh pr view NUMBER
gh pr view NUMBER --json title,body,state,reviews
gh pr diff NUMBER
gh pr checks NUMBER
gh pr status
```

### Create
```bash
gh pr create
gh pr create --title "Title" --body "Description"
gh pr create --draft
gh pr create --reviewer user1,user2
gh pr create --body-file pr.md
```

### Edit & Comment
```bash
gh pr edit NUMBER --title "New Title"
gh pr edit NUMBER --add-label "review"
gh pr edit NUMBER --add-reviewer USERNAME
gh pr comment NUMBER --body "Comment"
```

### Review
```bash
gh pr review NUMBER --approve
gh pr review NUMBER --request-changes --body "Fix X"
gh pr review NUMBER --comment --body "Looks good"
```

### Merge & Close
```bash
gh pr checkout NUMBER
gh pr ready NUMBER
gh pr merge NUMBER
gh pr merge NUMBER --squash --delete-branch
gh pr merge NUMBER --rebase
gh pr close NUMBER
```

### Update & Revert
```bash
gh pr update-branch NUMBER
gh pr lock NUMBER --reason "resolved"
gh pr unlock NUMBER
gh pr revert NUMBER
```
