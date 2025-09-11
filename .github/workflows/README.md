# Migration Tool Validation Workflows

This directory contains GitHub Action workflows that validate the installation of migration tools proposed in each platform-specific prompt file. Each workflow runs on the latest Windows runner to confirm that the proposed tools and installation methods are valid and functional.

## Available Workflows

### 1. Azure DevOps to GitHub Migration Tools Validation
**File:** `validate-ado2gh-tools.yml`  
**Prompt:** `ado2gh.prompt.md`

**Tools Validated:**
- GitHub CLI (gh) with Enterprise Importer extension
- Azure CLI (az) with DevOps extension
- Git CLI (git)
- PowerShell for scripting

**Installation Methods:**
- Uses `winget` for Windows package installation
- Validates extension installations
- Confirms tool accessibility and version information

### 2. Azure DevOps Server to GitHub Migration Tools Validation
**File:** `validate-adoserver2gh-tools.yml`  
**Prompt:** `adoserver2gh.prompt.md`

**Tools Validated:**
- GitHub CLI (gh) with Enterprise Importer extension
- Azure CLI (az) with DevOps extension
- Git CLI (git)
- Azure DevOps Server connection configuration capability
- PowerShell for Windows Server environments

**Key Differences:**
- Tests on-premises server connectivity configuration
- Validates Windows Server environment recommendations
- Confirms Azure DevOps Server-specific connection capabilities

### 3. TFS to GitHub Migration Tools Validation
**File:** `validate-tfs2gh-tools.yml`  
**Prompt:** `tfs2gh.prompt.md`

**Tools Validated:**
- **Git-TFS (git-tfs)** - Essential for TFVC to Git conversion
- GitHub CLI (gh) with Enterprise Importer extension
- Git CLI (git)
- Chocolatey package manager
- Windows environment (highly recommended for TFS)

**Critical Features:**
- Installs and validates Git-TFS for TFVC conversion
- Uses Chocolatey for specialized tool installation
- Includes multiple verification methods for Git-TFS
- Confirms Windows environment compatibility

### 4. GitLab to GitHub Migration Tools Validation
**File:** `validate-gitlab2gh-tools.yml`  
**Prompt:** `gitlab2gh.prompt.md`

**Tools Validated:**
- GitHub CLI (gh) with Enterprise Importer extension
- GitLab CLI (glab)
- Git CLI (git)
- Python with python-gitlab library
- Node.js with gitlab-to-github-migrator
- Migration utility packages

**Installation Features:**
- Downloads GitLab CLI from GitHub releases
- Installs Python libraries for GitLab API interaction
- Sets up Node.js migration utilities
- Validates cross-platform migration tools

### 5. SVN to GitHub Migration Tools Validation
**File:** `validate-svn2gh-tools.yml`  
**Prompt:** `svn2gh.prompt.md`

**Tools Validated:**
- Git with SVN support (git-svn)
- Subversion client (svn) via TortoiseSVN
- GitHub CLI (gh)
- Perl interpreter
- Text processing tools (awk, sed, grep)
- Disk space requirements

**Special Considerations:**
- Validates Git-SVN integration
- Installs TortoiseSVN for command-line SVN tools
- Checks for text processing tool availability
- Monitors disk space for large repository conversions

### 6. Generic to GitHub Migration Tools Validation
**File:** `validate-generic2gh-tools.yml`  
**Prompt:** `generic2gh.prompt.md`

**Tools Validated:**
- Core GitHub tools (GitHub CLI, Git)
- Multi-platform migration tools:
  - Azure DevOps (Azure CLI + extension)
  - TFS (Git-TFS)
  - GitLab (GitLab CLI + Python libraries)
  - SVN (Git-SVN + Subversion client)
- Platform detection and adaptation tools

**Comprehensive Coverage:**
- Installs tools for all supported migration platforms
- Validates platform-specific tool availability
- Provides compatibility summary for different source platforms
- Demonstrates multi-platform migration capability

## Workflow Triggers

Each workflow is triggered by:

1. **Push to main/develop branches** when the corresponding prompt file or workflow file changes
2. **Pull requests to main branch** affecting the prompt or workflow files  
3. **Manual dispatch** for on-demand validation

## Validation Approach

### Installation Validation
- Uses authentic installation methods from prompt files
- Follows exact command sequences as documented
- Validates using Windows PowerShell as specified

### Tool Verification
- Confirms version information accessibility
- Validates extension and library installations
- Tests core functionality where possible
- Provides comprehensive verification summaries

### Error Handling
- Includes alternative verification methods
- Provides informative messages for PATH-related issues
- Notes when session restart may be required
- Offers troubleshooting guidance

## Usage

### Running Individual Workflows
Each workflow can be triggered manually:

1. Go to **Actions** tab in GitHub repository
2. Select the desired validation workflow
3. Click **Run workflow** button
4. Choose the branch and confirm

### Monitoring All Validations
- Push changes to prompt files to trigger related workflows
- Create pull requests to run validation checks
- Review workflow results in the Actions tab

### Interpreting Results
- ✅ **Success**: All tools installed and validated correctly
- ⚠️ **Warning**: Tools installed but may need session restart or PATH updates
- ❌ **Failure**: Installation or validation failed (requires investigation)

## Benefits

### Tool Installation Validation
- Confirms all proposed installation methods work
- Validates tool compatibility on Windows runners
- Ensures command accessibility and functionality

### Documentation Accuracy  
- Verifies that prompt file instructions are accurate
- Tests real-world installation scenarios
- Maintains consistency between documentation and reality

### Migration Readiness
- Demonstrates that migration tools can be successfully installed
- Validates cross-platform migration capabilities
- Provides confidence in migration toolkit completeness

### Continuous Validation
- Automatically tests when prompt files are updated
- Catches breaking changes in installation methods
- Ensures ongoing accuracy of migration guidance

## Maintenance

### Updating Workflows
When prompt files are updated with new tools or installation methods:

1. Update the corresponding workflow file
2. Match exact installation commands from the prompt
3. Add appropriate verification steps
4. Test the workflow manually before committing

### Tool Version Management
- Workflows use latest available versions unless specified
- Update installation methods if tools change
- Monitor for deprecated installation approaches
- Validate compatibility with new tool versions

### Platform Compatibility
- All workflows target `windows-latest` runners
- Maintain Windows PowerShell command compatibility
- Test alternative installation methods when primary methods fail
- Provide platform-specific guidance and troubleshooting

This validation system ensures that every migration tool and installation method proposed in the toolkit is tested and verified, providing confidence in the migration guidance and tooling recommendations.
