---
mode: 'agent'
description: 'Team Foundation Server to GitHub Enterprise Migration Assistant'
---

# TFS to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- Chocolatey (package manager for Git-TFS)
- Git-TFS (ESSENTIAL for TFVC conversion)
- GitHub CLI with ADO2GH extension
- Git CLI

### Tool Installation
```powershell
# Windows PowerShell (STRONGLY RECOMMENDED for TFS)

# Install Chocolatey (required for git-tfs)
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Install Git-TFS (ESSENTIAL for TFVC to Git conversion)
choco install gittfs --ignore-dependencies

# Pre-installed on GitHub Actions runners
gh --version
gh extension install github/gh-ado2gh
git --version

# Verify git-tfs installation (CRITICAL)
git tfs --version
git tfs help
```

### Tool Verification Checklist
- [ ] Git-TFS installed and accessible: `git tfs --version`
- [ ] GitHub CLI: `gh --version`
- [ ] ADO2GH extension: `gh extension list | grep ado2gh`
- [ ] Git CLI: `git --version`

### Source Setup
🔧 **USER ACTION REQUIRED**
- TFS Server URL: _______________
- Collection name: _______________
- Team Project(s): _______________
- TFVC vs Git repositories: _______________

### Target Setup
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### TFVC Repository Conversion
```powershell
# List available projects
git tfs list-remote-branches [TFS_SERVER_URL]/[COLLECTION]

# Clone TFVC repository
git tfs clone [TFS_SERVER_URL]/[COLLECTION] $/[PROJECT_PATH] [LOCAL_DIR]
cd [LOCAL_DIR]

# Verify conversion
git log --oneline
```

### Push to GitHub
```powershell
git remote add origin https://github.com/[ORG]/[REPO].git
git push origin --all
git push origin --tags
```

### Validation
- [ ] TFVC history converted to Git
- [ ] Repository content migrated
- [ ] Commit history preserved

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
