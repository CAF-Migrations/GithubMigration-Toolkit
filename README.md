# GitHub Migration Toolkit

## 🚀 AI-Powered Enterprise Migration Framework

Battle-tested migration toolkit for GitHub Enterprise migrations across EMEA and Middle East. Features **mandatory human validation** at each step, supporting Azure DevOps, TFS, GitLab, Bitbucket, and SVN migrations with zero data loss.

### Key Features
- **Human-Validated AI Workflows**: GitHub Copilot intelligence + mandatory checkpoints
- **Platform-Agnostic**: Unified interface for ADO, TFS, GitLab, SVN, Bitbucket
- **Zero-Trust Architecture**: Explicit user confirmation for every operation
- **Enterprise Scale**: Multiple successful Fortune 500 and government migrations
- **Compliance-Ready**: GDPR, SOX audit trails, regional compliance frameworks

## 🎯 Migration Capabilities Matrix

### Supported Migration Paths with Enterprise Features

| Source Platform | Prompt Template | Enterprise Features | Regional Compliance |
|---|---|---|---|
| Azure DevOps Services | `ado2gh.prompt.md` | Git repos, work items, Azure Pipelines → GitHub Actions | GDPR, SOX audit trails |
| **Azure DevOps Server (On-Premises)** | `adoserver2gh.prompt.md` | **Server-specific:** VPN/network, TFVC conversion, AD integration | On-premises data sovereignty |
| Team Foundation Server (TFS) | `tfs2gh.prompt.md` | **TFVC → Git** using git-tfs, work items, build definitions | Legacy compliance preservation |
| GitLab (Cloud/Self-hosted) | `gitlab2gh.prompt.md` | Issues, merge requests, GitLab CI → GitHub Actions | EU data residency support |
| **Bitbucket Server** | `bbs2gh.prompt.md` | **Bitbucket repos**, pull requests, Bamboo CI integration | Enterprise SSO integration |
| Subversion (SVN) | `svn2gh.prompt.md` | SVN → Git conversion, trunk/branches/tags structure | Legacy system modernization |
| **GitHub Enterprise Importer** | `gei.prompt.md` | **Direct GEI operations** for supported platforms | Native enterprise features |
| Generic/Other Platforms | `generic2gh.prompt.md` | Adaptable template for any source control system | Custom compliance frameworks |

## 🔧 Enterprise Utility Framework

| Utility | Prompt Template | Enterprise Purpose | Compliance Features |
|---|---|---|---|
| **Health Check** | `health.prompt.md` | **Pre-migration validation** of tools, access, and environment | Audit trail generation |
| **Post-Migration Validation** | `validate.prompt.md` | **Comprehensive validation** of migrated repositories and access | Compliance verification |
| **Risk Assessment** | `risk.prompt.md` | **Enterprise risk evaluation** and mitigation planning | Risk register automation |
| **Rollback Planning** | `rollback.prompt.md` | **Disaster recovery** procedures and validation | Business continuity compliance |

## 🏢 Architecture Principles

- **Zero-Trust Validation**: Pre-flight checks, human-in-the-loop, automated rollback
- **Compliance Framework**: Data sovereignty, audit trails, role-based access, encryption
- **Event-Driven**: Validation gates → Human checkpoints → Execution → Audit logging

## � Enterprise Framework Structure

```
GithubMigration-Toolkit/
├── README.md                          # Technical architecture documentation
├── .github/
│   ├── copilot-instructions.md        # AI behavior governance framework (5-phase workflow)
│   └── prompts/
│       ├── ado2gh.prompt.md           # Azure DevOps Services → GitHub Enterprise
│       ├── ado2gh-demo.prompt.md      # DEMO: Simulated ADO migration walkthrough
│       ├── adoserver2gh.prompt.md     # Azure DevOps Server (On-Premises) → GitHub Enterprise
│       ├── tfs2gh.prompt.md           # TFS/TFVC → GitHub Enterprise  
│       ├── gitlab2gh.prompt.md        # GitLab → GitHub Enterprise
│       ├── bbs2gh.prompt.md           # Bitbucket Server → GitHub Enterprise
│       ├── svn2gh.prompt.md           # Subversion → GitHub Enterprise
│       ├── gei.prompt.md              # GitHub Enterprise Importer operations
│       ├── generic2gh.prompt.md       # Generic → GitHub Enterprise
│       ├── health.prompt.md           # Pre-migration health checks
│       ├── validate.prompt.md         # Post-migration validation
│       ├── risk.prompt.md             # Enterprise risk assessment
│       └── rollback.prompt.md         # Disaster recovery procedures
├── docs/
│   ├── architecture/                  # Enterprise architecture patterns
│   ├── compliance/                    # Regional compliance frameworks
│   └── case-studies/                  # Customer success stories
└── templates/
    ├── governance/                     # Enterprise governance templates
    └── reporting/                      # Migration reporting frameworks
```



## 🔧 Phase 1: Tool Installation (MANDATORY FIRST STEP)

### Core Tools (Required for All Migrations)
Install these tools **BEFORE** any migration activities:

| Tool | Purpose | Installation Command |
|---|---|---|
| **GitHub CLI** | Core migration operations | `winget install GitHub.cli` |
| **Git CLI** | Repository operations | `winget install Git.Git` |
| **GEI Extension** | GitHub Enterprise Importer | `gh extension install github/gh-gei` |

### Platform-Specific Tools (Install Based on Source)

| Source Platform | Required Tools | Installation Commands |
|---|---|---|
| **Azure DevOps Services** | Azure CLI + DevOps extension | `winget install Microsoft.AzureCLI`<br>`az extension add --name azure-devops` |
| **Azure DevOps Server** | Azure CLI + ADO2GH + git-tfs | `winget install Microsoft.AzureCLI`<br>`gh extension install github/gh-ado2gh`<br>`choco install gittfs` |
| **TFS/TFVC** | git-tfs (Windows only) | `choco install gittfs` |
| **GitLab** | GitLab CLI | `winget install gitlab.gitlab-cli` |
| **Bitbucket Server** | BBS2GH extension | `gh extension install github/gh-bbs2gh` |
| **SVN** | Git-SVN + Subversion | `choco install git.install --params "/GitAndUnixToolsOnPath"`<br>`choco install svn` |

### Tool Installation Workflow

```powershell
# Step 1: Install Core Tools
winget install GitHub.cli
winget install Git.Git
gh auth login

# Step 2: Install Platform-Specific Tools (example: Azure DevOps Server)
winget install Microsoft.AzureCLI
gh extension install github/gh-ado2gh
choco install gittfs

# Step 3: Verify Installation
gh --version
git --version
az --version
gh extension list

# Step 4: Configure Authentication
gh auth login
az login
```

**⚠️ USER CONFIRMATION REQUIRED**
After completing tool installation, confirm: **"Tools installed - proceed"**

## 🚀 Enterprise Migration Workflow

### Streamlined 5-Phase Migration Process

The toolkit implements a proven workflow with **mandatory user confirmation** at each phase:

#### **Phase 1: Tool Installation** → USER CONFIRMS
- Install required CLI tools (GitHub CLI, Azure CLI, platform-specific tools)
- Configure authentication and extensions
- Verify tool versions and dependencies
- **User confirms:** "Tools installed - proceed"

#### **Phase 2: Connectivity Testing** → USER CONFIRMS (On-Premise Only)
- **Azure DevOps Server/TFS**: Ping/curl tests to verify server accessibility
- **Bitbucket Server**: Validate URL accessibility and authentication
- **Use built-in web validation** to test API endpoints
- Verify credentials and permissions work correctly
- **User confirms:** "Connectivity verified - proceed"

#### **Phase 3: Pre-Migration Planning** → USER CONFIRMS
- Discover repositories and analyze scope
- Define batching strategy and priorities
- Review migration plan and risk assessment
- **User confirms:** "Plan approved - proceed"

#### **Phase 4: Execute Migration** → USER CONFIRMS (Each Batch)
- Migrate repositories in defined batches
- Validate each batch before proceeding
- Monitor progress and handle errors
- **User confirms:** "Batch complete - continue" or "Stop"

#### **Phase 5: Post-Migration Validation** → USER CONFIRMS
- Test repository access and cloning
- Verify user permissions and team access
- Confirm CI/CD configurations
- Generate migration report
- **User confirms:** "Migration validated - complete"

### Mandatory Confirmation Pattern

**Every phase requires explicit user confirmation:**
```
⚠️ CONFIRMATION REQUIRED
About to: [specific action]
Reply: "Confirmed - proceed" or "Stop"
```

**Key Principles:**
- **NEVER execute** without user confirmation
- **ALWAYS wait** for approval before next phase
- **Users provide** all credentials, tokens, and validations
- **Stop immediately** if user requests

### Enterprise Success Patterns

**Risk Mitigation Strategies:**
- Zero-downtime migration approaches for critical systems
- Automated rollback capabilities with rapid recovery times
- Real-time migration health monitoring with instant alerting
- Mandatory validation gates at each phase

**Compliance Excellence:**
- GDPR-compliant data handling for European enterprises
- SOX audit trail generation for financial services
- Custom compliance frameworks for government agencies
- Complete audit logs for all operations

**On-Premise Connectivity:**
- Pre-migration endpoint testing (ping, curl, web validation)
- VPN/network connectivity verification
- API accessibility validation
- Authentication and permission testing

## 🌍 Proven Enterprise Success

- **EMEA & Middle East Leadership**: Multiple customers across financial services, government, manufacturing, oil & gas
- **Zero Data Loss**: All production migrations completed successfully
- **High Uptime**: Critical systems maintained during migrations
- **Cost Savings**: Significant reduction in migration time and costs
- **Industry Recognition**: GitHub Partner Excellence Award, Microsoft Partner Award

### Platform-Specific Enterprise Guidance

#### Azure DevOps Server / TFS (On-Premise)
**Phase 1 - Tool Installation:**
- GitHub CLI + ADO2GH extension
- Azure CLI with DevOps extension
- git-tfs for TFVC repository conversion
- Windows environment recommended

**Phase 2 - Connectivity Testing (MANDATORY):**
- Ping ADO Server endpoint: `Test-Connection ado-server.contoso.com`
- Curl API test: `curl https://ado-server.contoso.com/_apis/projects`
- Verify VPN/network connectivity
- Test Azure AD authentication
- Validate collection access permissions
- **User confirms connectivity before proceeding**

#### Bitbucket Server (On-Premise)
**Phase 1 - Tool Installation:**
- GitHub CLI + BBS2GH extension
- Git CLI

**Phase 2 - Connectivity Testing (MANDATORY):**
- Ping Bitbucket Server: `Test-Connection bitbucket.contoso.com`
- Curl API test: `curl https://bitbucket.contoso.com/rest/api/1.0/projects`
- Verify server accessibility
- Test API authentication with PAT
- Validate repository access permissions
- **User confirms connectivity before proceeding**

#### GitLab Self-Hosted (On-Premise)
**Phase 2 - Connectivity Testing:**
- Ping GitLab instance
- Test API endpoint accessibility
- Verify authentication and permissions

#### Cloud Platforms (Azure DevOps Services, GitLab Cloud, etc.)
**Phase 2 - Skip Connectivity Testing:**
- Cloud platforms are publicly accessible
- Proceed directly to Phase 3 after tool installation

## ✅ Migration Success Criteria

- Repositories migrated with complete history
- Users provisioned with correct access and permissions
- Work items converted to GitHub Issues
- CI/CD pipelines operational as GitHub Actions
- Teams and permissions properly mapped
- User acceptance testing completed
- Authentication (SSO/EMU) working correctly

## 🛡️ Troubleshooting & Best Practices

### Common Issues
- **CLI Tool Issues**: Verify PATH, authentication tokens, and tool versions
- **Authentication failures**: Check PAT scopes and expiration
- **Large repository timeouts**: Use batching and optimize network
- **TFVC conversion errors**: Ensure disk space and stable network

### Best Practices
- **Pilot-First**: Validate with non-production projects
- **Audit Trail**: Maintain detailed logs for compliance
- **Zero-Downtime**: Schedule during maintenance windows
- **Disaster Recovery**: Test rollback procedures before migration
- **Stakeholder Communication**: Regular updates throughout lifecycle



## 🤝 Contributing

To extend for additional platforms:
1. Use `generic2gh.prompt.md` as foundation template
2. Add platform-specific tool requirements
3. Customize workflow for compliance features
4. Test with real migration scenarios
5. Update documentation and share patterns

Open-source foundation for enterprise migrations. Commercial usage permitted. Community contributions welcomed.

---

## 📊 Repository Metrics & Community Impact

- **⭐ Growing GitHub Stars** - Expanding community adoption
- **🔄 Active Forks** - Active enterprise customization
- **📈 Multiple Enterprise Deployments** - Proven production reliability
- **🌍 EMEA/Middle East Leadership** - Regional expertise and market presence
- **🏆 Industry Recognition** - Award-winning innovation in enterprise migration

*Built with enterprise excellence for global-scale GitHub migrations.*
