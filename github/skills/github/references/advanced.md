# Advanced Operations

## Authentication & Config

```bash
gh auth status
gh auth login [--web]
gh auth logout
gh auth refresh --scopes repo,admin:org
gh auth switch
gh auth token

gh config list
gh config get git_protocol
gh config set git_protocol ssh
gh config set editor "code --wait"
gh config clear-cache
```

## Extensions

```bash
gh extension list
gh extension search QUERY
gh extension install OWNER/gh-EXTENSION
gh extension upgrade EXTENSION|--all
gh extension remove EXTENSION
gh extension create NAME
```

## Aliases

```bash
gh alias list
gh alias set co 'pr checkout'
gh alias set --shell igrep 'gh issue list | grep -i'
gh alias delete ALIAS
gh alias import aliases.yml
```

## Secrets & Variables

### Secrets
```bash
gh secret list
gh secret list --org ORG
gh secret set NAME --body "value"
gh secret set NAME --env production
gh secret set NAME --org ORG --visibility all|selected
gh secret delete NAME
```

### Variables
```bash
gh variable list
gh variable get NAME
gh variable set NAME --body "value"
gh variable set NAME --env production
gh variable delete NAME
```

## Labels

```bash
gh label list
gh label create "bug" --color "d73a4a" --description "Something broken"
gh label edit "bug" --name "bug-fix" --color "ff0000"
gh label delete "old-label" --yes
gh label clone OWNER/SOURCE_REPO
```

## Codespaces

```bash
gh codespace list
gh codespace create --repo OWNER/REPO [--branch BRANCH]
gh codespace code --codespace NAME [--web]
gh codespace ssh --codespace NAME
gh codespace jupyter --codespace NAME
gh codespace ports forward 8080:8080 --codespace NAME
gh codespace cp local remote:/path --codespace NAME
gh codespace logs --codespace NAME
gh codespace stop --codespace NAME
gh codespace delete --codespace NAME
gh codespace rebuild --codespace NAME
```

## SSH & GPG Keys

```bash
gh ssh-key list
gh ssh-key add ~/.ssh/id_rsa.pub --title "My Laptop"
gh ssh-key delete KEY_ID --yes

gh gpg-key list
gh gpg-key add < key.asc
gh gpg-key delete KEY_ID --yes
```

## Organizations

```bash
gh org list
gh api orgs/ORG/members --jq '.[].login'
gh api orgs/ORG/teams --jq '.[].name'
```

## Status & Browse

```bash
gh status
gh status --org ORG

gh browse
gh browse path/to/file.js:42
gh browse --branch BRANCH
gh browse --issues|--pulls|--projects|--releases|--settings|--wiki
```

## Rulesets & Attestations

```bash
gh ruleset list
gh ruleset view ID
gh ruleset check BRANCH

gh attestation verify ARTIFACT --owner OWNER
gh attestation download ARTIFACT --owner OWNER
gh attestation trusted-root
```

## Search

```bash
gh search repos "QUERY" --language=ts --stars=">100"
gh search issues "QUERY" --state open
gh search prs "QUERY" --repo OWNER/REPO
gh search code "QUERY" --language typescript
gh search commits "QUERY" --author USERNAME
gh search users "QUERY" --type user|org
```

## Shell Completion

```bash
gh completion -s bash|zsh|fish|powershell
eval "$(gh completion -s zsh)"
```

## Agent Tasks (Preview)

```bash
gh agent-task list
gh agent-task create "Task description"
gh agent-task view NUMBER|SESSION_ID
```
