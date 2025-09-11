---
mode: 'agent'
description: 'SVN to GitHub Enterprise Migration Assistant'
---

# SVN to GitHub Enterprise Migration

## Prerequisites

### Tools Required
- Git with SVN support (git-svn)
- Subversion client (svn)
- GitHub CLI (gh)
- Perl (for git-svn operations)

### Tool Installation
```powershell
# Windows PowerShell
gh --version
git --version
choco install svn -y
choco install strawberryperl -y

# Verify installations
git svn --version
svn --version
gh --version
perl --version
```

### Tool Verification Checklist
- [ ] Git with SVN support: `git svn --version`
- [ ] Subversion client: `svn --version`
- [ ] GitHub CLI: `gh --version`
- [ ] Perl interpreter: `perl --version`

### Source Setup
🔧 **USER ACTION REQUIRED**
- SVN Repository URL: _______________
- Authentication method: _______________
- Repository structure (trunk/branches/tags): _______________

### Target Setup
🔧 **USER ACTION REQUIRED**
- GitHub Enterprise organization: _______________
- Migration team access confirmed: (Yes/No)

## Migration Process

### Repository Analysis
```powershell
svn info [SVN_URL]
svn list [SVN_URL]
```

### Clone with History
```powershell
git svn clone [SVN_URL] --stdlayout [LOCAL_DIR]
cd [LOCAL_DIR]
```

### Push to GitHub
```powershell
git remote add origin https://github.com/[ORG]/[REPO].git
git push origin --all
git push origin --tags
```

### Validation
- [ ] Repository content migrated
- [ ] Commit history preserved
- [ ] Branches and tags transferred

⚠️ **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
