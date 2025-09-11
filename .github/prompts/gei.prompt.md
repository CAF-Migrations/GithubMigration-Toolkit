---
mode: 'agent'
description: 'GitHub Enterprise Importer Migration Assistant'
---

# GitHub Enterprise Importer Migration

## Prerequisites

### Tools Required
- GitHub CLI with GEI extension
- Git CLI

### Tool Installation
```powershell
gh --version
gh extension install github/gh-gei
git --version
```n
### Access Setup
 **USER ACTION REQUIRED**
- Source organization: _______________
- Target organization: _______________
- Admin access confirmed for both: (Yes/No)

## Migration Process

### Repository Discovery
```powershell
gh gei inventory --github-source-org [SOURCE_ORG] --output repos.csv
```n
### Execute Migration
```powershell
gh gei migrate-repo --github-source-org [SOURCE_ORG] --source-repo [REPO] --github-target-org [TARGET_ORG] --target-repo [REPO]
```n
### Validation
- [ ] Repository content migrated
- [ ] Issues and PRs transferred
- [ ] Teams and permissions configured

 **CONFIRMATION REQUIRED** at each step
Reply with "Confirmed - proceed" to continue
