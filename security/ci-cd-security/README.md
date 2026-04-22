# Ci Cd Security

> This document outlines important security considerations and best practices for the CI/CD pipeline and NuGet package publishing process.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CI/CD Security Considerations for CycoD

This document outlines important security considerations and best practices for the CI/CD pipeline and NuGet package publishing process.

## Secure Secret Management

### NuGet API Keys

The NuGet API key used for publishing packages is a sensitive credential:

1. **Rotation Schedule**: 
   - Rotate your NuGet API key every 90-180 days
   - Update the `NUGET_API_KEY` GitHub secret after rotation

2. **Scope Limitation**:
   - Create scoped API keys on NuGet.org that only have access to the CycoD package
   - Use expiration dates when generating API keys

3. **Monitoring**:
   - Regularly check your published packages on NuGet.org
   - Enable email notifications for package publications

### GitHub Secrets

1. **Access Control**:
   - Limit repository access to trusted contributors
   - Use branch protection rules for the main branch
   - Consider requiring code reviews before merging

2. **Secret Auditing**:
   - Periodically review who has access to repository secrets
   - GitHub's secret scanning will alert you if secrets are accidentally committed

## Workflow Security

### Permission Boundaries

Our workflows use the principle of least privilege:

1. **CI Workflow**: 
   - Only needs read access to repository contents
   - Does not have access to any secrets

2. **Release Workflow**:
   - Limited to read access for repository contents
   - Write access for GitHub Packages (if used)
   - Access to production environment and its secrets

### Environment Protection

The production environment adds an additional layer of security:

1. **Requiring Approvals**:
   - Configure environment protection rules in GitHub:
     - Go to repository Settings > Environments > production
     - Add required reviewers who must approve deployments

2. **Waiting Period**:
   - Consider adding a waiting period before deployments
   - This provides time to cancel if a malicious deployment is detected

## Package Security

### Package Verificat

*[truncated — see source for full prompt]*