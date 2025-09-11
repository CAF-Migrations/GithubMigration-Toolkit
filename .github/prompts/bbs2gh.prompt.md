---
mode: 'agent'
description: 'Bitbucket Server to GitHub Enterprise Migration Assistant'
---

# Bitbucket Server to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- GitHub CLI with BBS2GH extension
- Git CLI

### Tool Installation
```powershell
gh --version
gh extension install github/gh-bbs2gh
git --version
```

### Source Setup
🔧 **USER ACTION REQUIRED**
- Bitbucket Server URL: _______________
- Admin/Project access confirmed: (Yes/No)
- Archive token/credentials available: (Yes/No)

### Target Setup  
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Repository Discovery
```powershell
gh bbs2gh inventory --bbs-server-url [URL] --output repos.csv
```

### Execute Migration
```powershell
gh bbs2gh migrate-repo --bbs-server-url [URL] --archive-path [PATH] --target-repo [OWNER/REPO]
```

### Validation
- [ ] Repository content migrated
- [ ] Commit history preserved  
- [ ] Access permissions verified

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
