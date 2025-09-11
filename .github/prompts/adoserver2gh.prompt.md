---
mode: 'agent'
description: 'Azure DevOps Server to GitHub Enterprise Migration Assistant'
---

# Azure DevOps Server to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- GitHub CLI with ADO2GH extension
- Azure CLI with DevOps extension
- Git CLI
- Git-TFS (ESSENTIAL for TFVC with >90 days history)
- .NET Framework 4.6.2 or higher
- Team Explorer 2012/2013 or Visual Studio (for TFS connectivity)

### Tool Installation
```powershell
# Windows PowerShell
gh --version
gh extension install github/gh-ado2gh
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
az extension add --name azure-devops
git --version

# Install Chocolatey (required for git-tfs)
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# Install git-tfs for TFVC repositories
choco install gittfs --ignore-dependencies

# Verify installations
gh --version
az --version
git --version
git tfs --version
```

### Tool Verification Checklist
- [ ] GitHub CLI: `gh --version`
- [ ] ADO2GH extension: `gh extension list | grep ado2gh`
- [ ] Azure CLI: `az --version`
- [ ] Azure DevOps extension: `az extension list | grep azure-devops`
- [ ] Git CLI: `git --version`
- [ ] Git-TFS: `git tfs --version`

### Source Setup
🔧 **USER ACTION REQUIRED**
- Azure DevOps Server URL: _______________
- Collection name: _______________
- PAT with required permissions: _______________
- Project list: _______________

### Target Setup
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Repository Discovery
```powershell
gh ado2gh inventory --ado-server-url [SERVER_URL] --ado-org [COLLECTION] --output repos.csv
```

### Execute Migration
```powershell
gh ado2gh migrate-repo --ado-server-url [SERVER_URL] --ado-org [COLLECTION] --ado-repo [REPO] --github-org [GH_ORG] --github-repo [REPO]
```

### TFVC Repository Conversion (for >90 days history)
```powershell
# For TFVC repositories with extensive history (>90 days)
# ADO2GH has limitations, use git-tfs for complete conversion

# Prerequisites check
git tfs help  # Verify git-tfs is working

# [Optional] Find TFVC repository paths to clone
git tfs list-remote-branches [TFS_SERVER_URL]/[COLLECTION]

# Clone TFVC repository with full history (this will take time for large repos)
git tfs clone [TFS_SERVER_URL]/[COLLECTION] $/[PROJECT_PATH] [LOCAL_DIR]

# Alternative: Quick clone for latest changeset only (faster)
# git tfs quick-clone [TFS_SERVER_URL]/[COLLECTION] $/[PROJECT_PATH] [LOCAL_DIR]

cd [LOCAL_DIR]

# Verify conversion
git log --oneline  # Shows TFS history converted to Git commits
git tfs --version

# Push to GitHub
git remote add origin https://github.com/[ORG]/[REPO].git
git push origin --all
git push origin --tags
```

**Important Notes:**
- Git-TFS requires .NET 4.6.2+ and Team Explorer/Visual Studio for TFS connectivity
- Full clone can be time-consuming for large repositories with extensive history
- Use `quick-clone` for faster migration if you only need recent changesets
- Git-TFS works outside of TFS workspaces - no workspace setup required

### Validation
- [ ] Repository content migrated
- [ ] Work items transferred
- [ ] Pipelines noted for conversion

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
