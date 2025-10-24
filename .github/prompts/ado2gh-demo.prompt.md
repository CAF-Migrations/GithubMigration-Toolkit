---
mode: 'agent'
description: 'DEMO: Azure DevOps to GitHub Enterprise Migration (Simulated)'
---

# ADO to GitHub Migration - DEMO MODE

**This is a dry-run demonstration workflow. All actions are simulated with mock data—no actual repositories will be migrated.**

## Phase 1: Tool Installation

### Installing Required Tools
I'll simulate installing:
- GitHub CLI with ADO2GH extension
- Azure CLI with DevOps extension
- Git CLI

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Install tools"** to begin installation

---

## Phase 2: Connectivity Testing (On-Premise Only)

### Testing Azure DevOps Server Connectivity
For on-premise ADO Server migrations, I'll test:
- Ping ADO Server endpoint
- Verify API accessibility
- Test authentication
- Check permissions

**Demo Values:**
- ADO Server: `https://ado-server.contoso.com`
- Connection Status: Testing...

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Test connectivity"** to verify endpoint access

---

## Phase 3: Pre-Migration Setup

### Source Configuration (Azure DevOps)
**Demo Values:**
- Organization: `contoso-ado`
- PAT Token: `demo_***************`
- Projects: `ProjectAlpha`, `ProjectBeta`, `ProjectGamma`

### Target Configuration (GitHub Enterprise)
**Demo Values:**
- GitHub Org: `contoso-enterprise`
- Migration Team: `migration-admins`

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Configuration confirmed"** to proceed

---

## Phase 4: Repository Discovery

### Scanning Azure DevOps Organization
I'll discover repositories from the demo organization.

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Discover repositories"** to scan

---

## Phase 5: Migration Planning

### Migration Batches
I'll organize repositories into batches for migration.

**Demo Batch Strategy:**
- Batch 1: 3 small repos (< 100 MB)
- Batch 2: 2 medium repos (100-500 MB)
- Batch 3: 1 large repo (> 500 MB)

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Approve plan"** to continue

---

## Phase 6: Execute Migration

### Batch 1 Migration
Migrating:
1. `web-frontend` (45 MB, 234 commits)
2. `api-gateway` (78 MB, 567 commits)
3. `shared-utils` (23 MB, 123 commits)

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Migrate batch 1"** to start migration

---

### Batch 2 Migration
Migrating:
1. `microservice-auth` (230 MB, 890 commits)
2. `data-processor` (345 MB, 1234 commits)

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Migrate batch 2"** to continue

---

### Batch 3 Migration
Migrating:
1. `monolith-legacy` (789 MB, 3456 commits)

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Migrate batch 3"** to complete migration

---

## Phase 7: Post-Migration Validation

### Validation Checks
I'll verify:
- Repository access and cloning
- Commit history integrity
- Branch protection rules
- Team permissions
- Work items (as GitHub Issues)
- Wiki pages

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Validate migration"** to run validation tests

---

## Phase 8: Migration Complete

### Final Report
I'll generate a summary report with:
- Total repositories migrated
- Success/failure status
- Validation results
- Next steps for CI/CD conversion

**⚠️ USER CONFIRMATION REQUIRED**
Reply: **"Generate report"** to complete demo

---

## Demo Instructions

**To run this demo, simply respond with the confirmation phrases at each phase:**
1. "Install tools"
2. "Test connectivity" (for on-premise)
3. "Configuration confirmed"
4. "Discover repositories"
5. "Approve plan"
6. "Migrate batch 1"
7. "Migrate batch 2"
8. "Migrate batch 3"
9. "Validate migration"
10. "Generate report"

**Or use:** "Start demo" to begin from Phase 1

**Stop anytime with:** "Stop demo"
