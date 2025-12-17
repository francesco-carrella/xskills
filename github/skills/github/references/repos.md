# Repository Operations

## List & Search

```bash
gh repo list
gh repo list OWNER --limit 50
gh search repos "QUERY" --language=typescript --stars=">100"
```

## View & Clone

```bash
gh repo view OWNER/REPO
gh repo view OWNER/REPO --json name,description,url,stargazerCount
gh repo clone OWNER/REPO
```

## Create & Fork

```bash
gh repo create REPO_NAME --public --description "Description"
gh repo create REPO_NAME --private --clone
gh repo fork OWNER/REPO --clone
```

## Edit Settings

```bash
gh repo edit --description "New description"
gh repo edit --visibility public
gh repo edit --enable-issues=false
gh repo edit --default-branch main
```

## Archive & Delete

```bash
gh repo archive OWNER/REPO --yes
gh repo unarchive OWNER/REPO
gh repo delete OWNER/REPO --yes
```

## Rename & Sync

```bash
gh repo rename NEW_NAME
gh repo sync                    # Sync fork with upstream
gh repo sync --force
gh repo set-default OWNER/REPO
```

## Deploy Keys

```bash
gh repo deploy-key list
gh repo deploy-key add KEY_FILE --title "Key Title"
gh repo deploy-key add KEY_FILE --title "Key" --allow-write
gh repo deploy-key delete KEY_ID
```

## Autolinks

```bash
gh repo autolink list
gh repo autolink create PREFIX URL_TEMPLATE
gh repo autolink view AUTOLINK_ID
gh repo autolink delete AUTOLINK_ID
```

## Templates

```bash
gh repo gitignore list
gh repo gitignore view Node
gh repo license list
gh repo license view mit
```
