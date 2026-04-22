# GITOPS DEPLOYMENT

> Fully automated GitOps deployment fer AzureHayMaker with secret injection, integration testin', and deployment verification.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GitOps Deployment

Fully automated GitOps deployment fer AzureHayMaker with secret injection, integration testin', and deployment verification.

## Quick Start

Push to any tracked branch - GitOps handles the rest automatically:

```bash
git push origin develop    # Deploys to dev environment
git push origin main        # Deploys to staging environment
```

The workflow automatically:
- Builds and deploys infrastructure
- Injects secrets with RBAC handling
- Runs integration tests
- Verifies deployment health
- Rolls back on any failure

## How It Works

### Automated Secret Injection

During GitHub Actions workflow deployment, the Secret Injection Handler automatically:

1. Waits for RBAC propagation (after managed identity role assignment)
2. Connects to Key Vault using managed identity
3. Retrieves Anthropic API key
4. Injects secret into orchestrator's environment variables
5. Restarts orchestrator with updated configuration

**No manual steps required.** The GitHub Actions workflow handles all secret injection before marking deployment as complete.

```python
# Example: Secret injection happens in GitHub Actions workflow
# .github/scripts/inject_secrets.py

handler = SecretInjectionHandler(
    subscription_id=subscription_id,
    resource_group=resource_group
)
handler.wait_for_rbac_propagation(keyvault_name, principal_id)
handler.inject_secrets_to_container_app(container_app_name, keyvault_name, secrets)
```

### Integration Test Framework

After deployment completes, integration tests automatically verify all CLI commands against the deployed API:

```bash
# Tests run automatically in GitHub Actions
# Tests ALL CLI commands:
- haymaker deploy
- haymaker resources list
- haymaker resources show <id>
- haymaker status
- haymaker cleanup
```

Tests verify:
- API endpoints respond correctly
- CLI authentication works
- Resource operations succeed
- Error messages are clear

**If any test fails, deployment is marked as failed.**

### Deployment Verification

Af

*[truncated — see source for full prompt]*