# GitHub Full Control API - OpenAPI 3.1.0 Specification

## Overview

This repository contains a comprehensive OpenAPI 3.1.0 specification for the GitHub REST API, specifically designed for full control of the `Bath-Analytics/cflow-control-center` repository. The specification is optimized for use with OpenAI GPT Actions, enabling Custom GPTs to perform all supported GitHub operations.

## Specification Details

- **OpenAPI Version:** 3.1.0
- **API Version:** 2.0.0
- **Total Endpoints:** 86
- **Schemas Defined:** 15
- **File:** `github-full-control-api.yaml`

## Coverage

This specification provides complete coverage of the following GitHub REST API categories:

### Repository Management (2 endpoints)
- Get repository information
- Update repository settings (visibility, topics, homepage, default branch, archive status, merge settings)

### Branch Operations (4 endpoints)
- List all branches
- Get branch information
- Create references (branches/tags)
- Delete and update branches

### Branch Protection (2 endpoints)
- Get, create, update, delete branch protection rules
- Configure status checks, review requirements, restrictions
- Manage required signatures and linear history

### Commit Operations (5 endpoints)
- List commits with filtering
- Get commit details
- Get combined commit status
- Create commit status
- Compare commits

### Issue Management (5 endpoints)
- Full CRUD operations for issues
- Issue comments
- Label management
- Repository-wide label operations

### Pull Request Management (6 endpoints)
- Full CRUD operations for pull requests
- Merge pull requests
- List PR files
- PR reviews and review comments
- Repository-wide PR comment management

### GitHub Actions Workflows (5 endpoints)
- List and get workflows
- Enable/disable workflows
- Trigger workflows manually (workflow_dispatch)

### Workflow Runs (8 endpoints)
- List and get workflow runs
- Re-run workflows (all jobs or failed jobs only)
- Cancel workflow runs
- Delete workflow runs
- List jobs for runs
- Download run logs

### Jobs & Artifacts (4 endpoints)
- Get job information
- Download job logs
- List, get, download, and delete artifacts

### Secrets & Variables Management (5 endpoints)
- List, get, create/update, delete repository secrets
- Get public key for secret encryption
- List, get, create, update, delete repository variables

### Security Alerts - Dependabot (2 endpoints)
- List Dependabot alerts with filtering
- Get and update alerts (dismiss, reopen)

### Security Alerts - Code Scanning (2 endpoints)
- List code scanning alerts
- Get and update alerts (dismiss, reopen)

### Security Alerts - Secret Scanning (2 endpoints)
- List secret scanning alerts
- Get and update alerts (resolve, reopen)

### Webhook Management (7 endpoints)
- Full CRUD operations for webhooks
- Test webhooks
- Ping webhooks
- List webhook deliveries
- Get delivery details
- Redeliver webhooks

### Deployment Management (5 endpoints)
- List and create deployments
- Get and delete deployments
- Create and list deployment statuses
- Manage deployment environments

### Collaborators & Team Management (6 endpoints)
- List repository collaborators
- Add, remove, check collaborators
- Get collaborator permissions
- Manage repository invitations
- List repository teams

### Content/File Operations (3 endpoints)
- Get repository content (files/directories)
- Create or update files
- Delete files
- Get README and license

### Release Management (4 endpoints)
- Full CRUD operations for releases
- Get latest release
- Get release by tag

### Tag Operations (1 endpoint)
- List repository tags

### Statistics & Metrics (6 endpoints)
- Contributors statistics
- Commit activity statistics
- Participation statistics
- Traffic views
- Clone traffic
- Community profile metrics

### Global Utilities (2 endpoints)
- Get API rate limit status
- Get user information

## Authentication

The API uses Bearer token authentication with GitHub Personal Access Tokens:

- **Classic Personal Access Token** - Traditional GitHub token with broad scopes
- **Fine-grained Personal Access Token** - Newer token type with granular permissions

Both token types are opaque bearer tokens (not JWTs) and are passed in the Authorization header.

Required scopes for classic tokens:
- `repo`: Full control of repositories
- `admin:repo_hook`: Full control of repository hooks
- `workflow`: Update GitHub Action workflows
- `security_events`: Read and write security events
- `admin:org`: Full control of organizations and teams (for team management)

For fine-grained tokens, grant equivalent repository permissions.

## HTTP Methods

The specification supports all standard HTTP methods:
- **GET (71 operations):** Retrieve resources
- **POST (20 operations):** Create new resources
- **PUT (10 operations):** Replace resources
- **PATCH (12 operations):** Update resources
- **DELETE (14 operations):** Remove resources

## Schemas

The specification includes 15 comprehensive schema definitions:
1. **Error** - Standard error response
2. **Repository** - Repository information
3. **Branch** - Git branch
4. **Commit** - Git commit
5. **Issue** - GitHub issue
6. **PullRequest** - Pull request
7. **Workflow** - GitHub Actions workflow
8. **WorkflowRun** - Workflow run
9. **DependabotAlert** - Dependabot security alert
10. **CodeScanningAlert** - Code scanning alert
11. **SecretScanningAlert** - Secret scanning alert
12. **Webhook** - Repository webhook
13. **Deployment** - Deployment
14. **Collaborator** - Repository collaborator
15. **Release** - Repository release

## Usage with OpenAI GPT Actions

This specification is fully compliant with OpenAI GPT Actions requirements:

1. **Valid OpenAPI 3.1.0 format** ✅
2. **Proper operationIds** ✅ - Each operation has a unique, descriptive ID
3. **Clear descriptions** ✅ - All operations and parameters are well-documented
4. **Standard authentication** ✅ - Bearer token (GitHub PAT)
5. **Proper error handling** ✅ - Standard error schema with documentation URLs
6. **Type-safe schemas** ✅ - All request/response bodies have proper type definitions

### Setting Up in Custom GPT

1. Go to ChatGPT and create a new Custom GPT
2. Navigate to the "Actions" section
3. Click "Import from URL" or paste the specification directly
4. Add your GitHub Personal Access Token in the authentication section
5. Test the integration

### Example GPT Instructions

```
You are a GitHub repository manager assistant for Bath-Analytics/cflow-control-center.

You can:
- Monitor repository activity (commits, issues, PRs, workflows)
- Manage security alerts (Dependabot, code scanning, secret scanning)
- Control GitHub Actions workflows (enable/disable, trigger, cancel)
- Manage deployments and environments
- Handle webhooks and integrations
- Manage collaborators and permissions
- Create and modify repository content
- Manage releases and tags

Always provide clear status updates and confirm actions before making changes.
```

## Validation

The specification has been validated using:
- Python `openapi-spec-validator` ✅
- PyYAML syntax validation ✅
- Manual review against GitHub REST API documentation ✅

## Compliance

This specification is compliant with:
- ✅ OpenAPI Specification 3.1.0
- ✅ JSON Schema 2020-12
- ✅ OpenAI GPT Actions requirements
- ✅ GitHub REST API v3

## Limitations

While this specification is comprehensive, please note:
- Some advanced GitHub Enterprise features may not be included
- Rate limiting applies as per GitHub API limits
- Fine-grained permissions depend on the token's scopes
- Organization-level operations outside the repository context are limited

## Updates and Maintenance

This specification is based on the GitHub REST API documentation as of December 2024. GitHub regularly updates their API, so periodic reviews and updates may be necessary.

## Support

For issues or questions about this specification:
1. Check the GitHub REST API documentation: https://docs.github.com/en/rest
2. Review the OpenAPI 3.1.0 specification: https://spec.openapis.org/oas/v3.1.0.html
3. Consult the OpenAI GPT Actions guide: https://platform.openai.com/docs/actions

## License

This specification is provided for use with the Bath-Analytics/cflow-control-center repository.
