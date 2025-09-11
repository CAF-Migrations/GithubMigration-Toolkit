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

### Tool Installation
```powershell
# Windows PowerShell
gh --version
gh extension install github/gh-ado2gh
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
az extension add --name azure-devops
git --version

# Verify installations
gh --version
az --version
git --version
```

### Tool Verification Checklist
- [ ] GitHub CLI: `gh --version`
- [ ] ADO2GH extension: `gh extension list | grep ado2gh`
- [ ] Azure CLI: `az --version`
- [ ] Azure DevOps extension: `az extension list | grep azure-devops`
- [ ] Git CLI: `git --version`

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

### TFVC Repository Conversion (if applicable)
```powershell
# Install git-tfs for TFVC repositories
choco install gittfs -y --ignore-dependencies
git tfs --version

# Convert TFVC to Git
git tfs clone [TFS_SERVER_URL]/[COLLECTION] $/[PROJECT_PATH] [LOCAL_DIR]
```

### Validation
- [ ] Repository content migrated
- [ ] Work items transferred
- [ ] Pipelines noted for conversion

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
