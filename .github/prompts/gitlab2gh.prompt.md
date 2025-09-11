---
mode: 'agent'
description: 'GitLab to GitHub Enterprise Migration Assistant'
---

# GitLab to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- GitHub CLI (gh)
- Git CLI (git)
- Python 3.11+ with python-gitlab library
- Node.js 18+ (for custom migration scripts)

### Tool Installation
```powershell
# Windows PowerShell
gh --version
git --version
python --version
pip install python-gitlab
node --version

# Verify installations
gh --version
git --version
python --version
python -c "import gitlab; print('python-gitlab installed')"
node --version
```

### Tool Verification Checklist
- [ ] GitHub CLI: `gh --version`
- [ ] Git CLI: `git --version`
- [ ] Python 3.11+: `python --version`
- [ ] Python-GitLab library: `pip list | grep python-gitlab`
- [ ] Node.js 18+: `node --version`

### Source Setup
🔧 **USER ACTION REQUIRED**
- GitLab URL: _______________
- Access token: _______________
- Project list: _______________

### Target Setup
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Repository Discovery
```powershell
# Custom GitLab API script for discovery
python -c "import gitlab; gl = gitlab.Gitlab('[URL]', private_token='[TOKEN]'); print([p.name for p in gl.projects.list()])"
```

### Manual Repository Migration
```powershell
# Clone from GitLab
git clone [GITLAB_REPO_URL]
cd [REPO_NAME]

# Add GitHub remote
git remote add github https://github.com/[ORG]/[REPO].git

# Push to GitHub
git push github --all
git push github --tags
```

### Validation
- [ ] Repository content migrated
- [ ] Commit history preserved
- [ ] Issues and merge requests noted for manual transfer

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
