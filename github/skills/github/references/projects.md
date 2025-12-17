# GitHub Projects

## Project Management

### List & View
```bash
gh project list
gh project list --owner ORG_NAME
gh project view NUMBER
gh project view NUMBER --owner ORG_NAME
```

### Create & Edit
```bash
gh project create --title "Project Title"
gh project create --title "Title" --owner ORG_NAME
gh project edit NUMBER --title "New Title"
gh project copy NUMBER --title "Copy of Project"
```

### Status
```bash
gh project close NUMBER
gh project reopen NUMBER
gh project delete NUMBER
gh project mark-template NUMBER
```

### Link to Repo
```bash
gh project link NUMBER --repo OWNER/REPO
gh project unlink NUMBER --repo OWNER/REPO
```

## Project Items

### List & Add
```bash
gh project item-list NUMBER
gh project item-list NUMBER --format json
gh project item-add NUMBER --url ISSUE_OR_PR_URL
gh project item-create NUMBER --title "Draft Issue"
```

### Edit & Archive
```bash
gh project item-edit --project-id ID --id ITEM_ID --field-id FIELD_ID --text "value"
gh project item-edit --project-id ID --id ITEM_ID --field-id FIELD_ID --number 5
gh project item-archive NUMBER --id ITEM_ID
gh project item-archive NUMBER --id ITEM_ID --undo
gh project item-delete NUMBER --id ITEM_ID
```

## Fields

```bash
gh project field-list NUMBER
gh project field-create NUMBER --name "Priority" --data-type "SINGLE_SELECT"
gh project field-delete NUMBER --id FIELD_ID
```
