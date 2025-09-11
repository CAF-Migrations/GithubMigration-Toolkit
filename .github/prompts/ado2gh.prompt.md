---
mode: 'agent'
description: 'Azure DevOps Services/Server to GitHub Enterprise Migration Assistant'
---

# Azure DevOps to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- GitHub CLI with ADO2GH extension
- Azure CLI with DevOps extension
- Git CLI

### Tool Installation
```powershell
gh --version
gh extension install github/gh-ado2gh
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
az extension add --name azure-devops
git --version
```

### Source Setup
 **USER ACTION REQUIRED**
- Azure DevOps Organization URL: _______________
- PAT with required permissions: _______________
- Project list: _______________

### Target Setup
 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Repository Discovery
```powershell
gh ado2gh inventory --ado-org [ADO_ORG] --output repos.csv
```

### Execute Migration
```powershell
gh ado2gh migrate-repo --ado-org [ADO_ORG] --ado-repo [REPO] --github-org [GH_ORG] --github-repo [REPO]
```

### Validation
- [ ] Repository content migrated
- [ ] Work items transferred
- [ ] Pipelines converted to Actions

 **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
