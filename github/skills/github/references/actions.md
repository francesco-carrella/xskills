# GitHub Actions

## Workflow Runs

### List & View
```bash
gh run list
gh run list --workflow "CI"
gh run list --status failure
gh run list --branch main
gh run view RUN_ID
gh run view RUN_ID --log
gh run view RUN_ID --log-failed
```

### Control
```bash
gh run watch RUN_ID
gh run rerun RUN_ID
gh run rerun RUN_ID --failed
gh run cancel RUN_ID
gh run delete RUN_ID
```

### Artifacts
```bash
gh run download RUN_ID
gh run download RUN_ID --name "artifact-name"
gh run download RUN_ID --dir ./artifacts
```

## Workflows

```bash
gh workflow list
gh workflow list --all
gh workflow view WORKFLOW
gh workflow view WORKFLOW --yaml
gh workflow run WORKFLOW
gh workflow run WORKFLOW --field param1=value1
gh workflow run WORKFLOW --ref BRANCH
gh workflow enable WORKFLOW
gh workflow disable WORKFLOW
```

## Cache

```bash
gh cache list
gh cache delete CACHE_ID
gh cache delete --all
gh cache delete --key CACHE_KEY_PREFIX
```
