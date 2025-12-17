# Releases & Gists

## Releases

### List & View
```bash
gh release list
gh release view TAG
gh release view TAG --json tagName,name,body,assets
```

### Create
```bash
gh release create TAG --title "Title" --notes "Notes"
gh release create TAG --notes-file CHANGELOG.md
gh release create TAG --generate-notes
gh release create TAG --draft
gh release create TAG --prerelease
gh release create TAG --target BRANCH
gh release create TAG file1.zip file2.tar.gz
```

### Edit
```bash
gh release edit TAG --title "New Title"
gh release edit TAG --notes "Updated notes"
gh release edit TAG --draft=false
gh release edit TAG --prerelease=false
gh release edit TAG --latest
```

### Download & Upload
```bash
gh release download TAG
gh release download TAG --pattern "*.tar.gz"
gh release download TAG --dir ./downloads
gh release upload TAG file.zip
gh release upload TAG file.zip --clobber
```

### Delete
```bash
gh release delete TAG --yes
gh release delete TAG --cleanup-tag
gh release delete-asset TAG ASSET_NAME --yes
```

### Verify Attestation
```bash
gh release verify TAG --owner OWNER
gh release verify-asset ASSET --release TAG
```

## Gists

### List & View
```bash
gh gist list
gh gist list --public|--secret
gh gist view GIST_ID
gh gist view GIST_ID --files
```

### Create & Edit
```bash
gh gist create FILE.txt
gh gist create FILE.txt --public --desc "Description"
gh gist create file1.txt file2.txt
gh gist edit GIST_ID
gh gist rename GIST_ID OLD_NAME NEW_NAME
```

### Clone & Delete
```bash
gh gist clone GIST_ID
gh gist delete GIST_ID
```
