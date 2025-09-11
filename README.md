# GitHub Migration Toolkit

Minimal GitHub Copilot prompts for migrating source control platforms to GitHub Enterprise with human validation workflows.

## Supported Migration Paths

| Source Platform | Prompt Template | Key Features |
|---|---|---|
| Azure DevOps Services/Server | `ado2gh.prompt.md` | Git repos, work items, Azure Pipelines → GitHub Actions |
| Team Foundation Server (TFS) | `tfs2gh.prompt.md` | **TFVC → Git** using git-tfs, work items, build definitions |
| GitLab (Cloud/Self-hosted) | `gitlab2gh.prompt.md` | Issues, merge requests, GitLab CI → GitHub Actions |
| Subversion (SVN) | `svn2gh.prompt.md` | SVN → Git conversion, trunk/branches/tags structure |
| Generic/Other Platforms | `generic2gh.prompt.md` | Adaptable template for any source control system |

## File Structure

```
GithubMigration-Toolkit/
├── README.md                          # This documentation
├── .github/
│   ├── copilot-instructions.md        # Copilot behavior instructions
│   └── prompts/
│       ├── ado2gh.prompt.md           # Azure DevOps → GitHub Enterprise
│       ├── tfs2gh.prompt.md           # TFS/TFVC → GitHub Enterprise  
│       ├── gitlab2gh.prompt.md        # GitLab → GitHub Enterprise
│       ├── svn2gh.prompt.md           # Subversion → GitHub Enterprise
│       └── generic2gh.prompt.md       # Generic → GitHub Enterprise
```

## Essential CLI Tools

### Core Tools (Required for All Migrations)
- **GitHub CLI** (`gh`) + Enterprise Importer extension
- **Git CLI** (`git`) 

### Platform-Specific Tools

| Source Platform | Key Tool | Purpose |
|---|---|---|
| **Azure DevOps** | `az devops` | Repository and work item access |
| **TFS/TFVC** | **`git-tfs`** | **TFVC → Git conversion** |
| **GitLab** | `glab` | GitLab API operations |
| **SVN** | `git-svn` | SVN → Git conversion |

### Quick Install Commands

```powershell
# Windows (PowerShell) - Core Tools
winget install GitHub.cli
winget install Git.Git
gh extension install github/gh-migration

# Platform-Specific Tools
winget install Microsoft.AzureCLI; az extension add --name azure-devops  # Azure DevOps
choco install gittfs  # TFS/TFVC (git-tfs)
```

```bash
# Linux/macOS - Core Tools
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
sudo apt update && sudo apt install gh git
gh extension install github/gh-migration

# Platform-Specific Tools
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash; az extension add --name azure-devops  # Azure DevOps
sudo apt install git-svn subversion  # SVN
```

## Usage

1. Choose the appropriate prompt template from `.github/prompts/`
2. Use with GitHub Copilot for guided migration
3. Follow human validation checkpoints  
4. Confirm each phase before proceeding

### TFVC/TFS Special Notes
- **git-tfs** is essential for TFVC repository conversion
- Windows environment strongly recommended for TFS migrations
- Requires Visual Studio Team Explorer or TFS connectivity

## Human-Validated Workflow

Each migration follows this pattern:

1. **URLs & Access** → USER CONFIRMATION
2. **PATs & Authentication** → USER CONFIRMATION  
3. **Tool Verification** → USER CONFIRMATION
4. **Repository Discovery** → USER CONFIRMATION
5. **Migration Execution** → USER CONFIRMATION
6. **Validation & Go-Live** → USER CONFIRMATION

## Key Tools by Platform

- **Azure DevOps**: GitHub Enterprise Importer + Azure CLI
- **TFS/TFVC**: **git-tfs** (essential for TFVC conversion) + Team Explorer
- **GitLab**: GitLab CLI + migration utilities  
- **SVN**: git-svn + Subversion client

## Success Criteria

✅ **Repositories migrated** with complete history  
✅ **Users provisioned** and access configured  
✅ **Work items converted** to GitHub Issues  
✅ **CI/CD pipelines** operational as GitHub Actions  
✅ **Teams and permissions** properly mapped

✅ **User Migration**
- All users can access GitHub Enterprise
- Team permissions match source platform access
- Authentication (SSO/EMU) working correctly

✅ **Validation & Training**
- User acceptance testing completed
- Team training provided and documented  
- Source platform properly transitioned

## Support and Troubleshooting

### Common Issues

#### CLI Tool Issues
- **GitHub CLI not found**: Ensure GitHub CLI is in system PATH and restart terminal
- **Git-TFS fails on Linux**: Use Windows or Windows Subsystem for Linux (WSL)
- **Azure CLI authentication**: Run `az login` before migration operations
- **GitLab CLI authentication**: Configure with `glab auth login` before starting
- **SVN tools missing**: Install complete Subversion client, not just libraries

#### Migration Issues  
- **Authentication failures**: Verify PAT scopes and expiration dates
- **Large repository timeouts**: Use batching and optimize network settings
- **Permission mapping errors**: Review team structure and validate GitHub Enterprise setup
- **CI/CD conversion complexity**: Consider manual recreation for complex pipelines
- **TFVC conversion errors**: Ensure sufficient disk space and stable network connection

### Best Practices
- Always start with a pilot repository/project
- Maintain audit trail of all migration steps
- Test with non-production data first  
- Have rollback procedures documented and tested
- Schedule migrations during low-activity periods

### Getting Help
- Review platform-specific prompt templates for detailed guidance
- Use GitHub Enterprise support for platform-specific issues
- Consult Microsoft documentation for Azure DevOps/TFS specifics
- Engage with GitHub Professional Services for complex enterprise migrations

## Contributing

To extend this toolkit for additional platforms:
1. Use `generic2gh.prompt.md` as a template
2. Add platform-specific tool requirements and commands  
3. Customize the workflow phases for platform features
4. Test the prompt with real migration scenarios
5. Update this README with the new platform support

## License

This toolkit is provided as-is for GitHub migration projects. Customize and adapt as needed for your specific requirements.
