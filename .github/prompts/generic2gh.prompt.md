---
mode: 'agent'
description: 'Universal GitHub Enterprise Migration Assistant'
---

# Universal GitHub Enterprise Migration

## Prerequisites

### Core Tools Required
- GitHub CLI (gh)
- Git CLI (git)
- Python 3.11+ (for GitLab and other migration scripts)
- Node.js 18+ (for various migration tools)

### Platform-Specific Tools (Install as needed)
- Azure CLI with DevOps extension (for Azure DevOps)
- Git-TFS (for TFS Server TFVC conversions)
- Subversion client (for SVN repositories)
- Strawberry Perl (for git-svn operations)
- Python-GitLab library (for GitLab migrations)

### Tool Installation
```powershell
# Windows PowerShell - Core Tools
gh --version
git --version
python --version
node --version

# Azure DevOps migrations
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
az extension add --name azure-devops

# TFS migrations
choco install gittfs

# SVN migrations
choco install strawberryperl -y
choco install svn -y

# GitLab migrations
pip install python-gitlab
```

### Source Platform Identification
🔧 **USER ACTION REQUIRED**
Identify your source platform:
- [ ] Azure DevOps Services/Server
- [ ] Team Foundation Server (TFS)
- [ ] GitLab
- [ ] Subversion (SVN)
- [ ] Bitbucket Server
- [ ] GitHub.com (using GEI)

### Target Setup
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Platform-Specific Migration Commands

**Azure DevOps:**
```powershell
gh extension install github/gh-ado2gh
gh ado2gh inventory --ado-org [ORG] --output repos.csv
gh ado2gh migrate-repo --ado-org [ORG] --ado-repo [REPO] --github-org [GH_ORG] --github-repo [REPO]
```

**TFS Server:**
```powershell
git tfs clone [TFS_URL]/[COLLECTION] $/[PROJECT] [LOCAL_DIR]
```

**GitLab:**
```powershell
# Manual clone and push
git clone [GITLAB_URL]
git remote add github [GITHUB_URL]
git push github --all
```

**SVN:**
```powershell
git svn clone [SVN_URL] --stdlayout [LOCAL_DIR]
```

**Bitbucket Server:**
```powershell
gh extension install github/gh-bbs2gh
gh bbs2gh migrate-repo --bbs-server-url [URL] --archive-path [PATH] --target-repo [OWNER/REPO]
```

**GitHub Enterprise Importer:**
```powershell
gh extension install github/gh-gei
gh gei migrate-repo --github-source-org [SOURCE] --source-repo [REPO] --github-target-org [TARGET] --target-repo [REPO]
```

### Validation
- [ ] Repository content migrated
- [ ] Commit history preserved
- [ ] Platform-specific features transferred

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
