# Nuget Publishing

> This document explains how to set up NuGet publishing for the CycoD application, allowing for automatic or manual publishing of the package when new versions are released.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# NuGet Publishing Guide for CycoD

This document explains how to set up NuGet publishing for the CycoD application, allowing for automatic or manual publishing of the package when new versions are released.

## Setting Up a NuGet Feed

### Option 1: Using the Public NuGet.org Feed

1. **Create a NuGet.org Account**:
   - Go to [NuGet.org](https://www.nuget.org/) and sign up for an account if you don't have one.
   - Sign in to your account.

2. **Create an API Key**:
   - Navigate to your account settings.
   - Select "API Keys" from the menu.
   - Click "Create" to generate a new API key.
   - Provide a name for your key (e.g., "CycoD Publishing").
   - Select either "Global" scope or specify the "cycod" package name.
   - Set an expiration date (recommended: 1 year).
   - Click "Create" to generate the key.
   - **Important**: Copy and securely store your API key, as you won't be able to see it again.

### Option 2: Using a Private NuGet Feed

If you prefer to use a private feed, some options include:

1. **GitHub Packages**:
   - Integrates well with GitHub repositories.
   - See [GitHub's documentation on GitHub Packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-nuget-registry).

2. **Azure Artifacts**:
   - Part of Azure DevOps services.
   - Good choice if you're using Azure DevOps for CI/CD.
   - See [Microsoft's documentation on Azure Artifacts](https://docs.microsoft.com/en-us/azure/devops/artifacts/get-started-nuget).

3. **MyGet** or **JFrog Artifactory**:
   - Third-party hosting solutions for package feeds.

## Configuring GitHub Actions for Automatic Publishing

To enable automatic publishing of the NuGet package when a new version tag is pushed:

1. **Add Your NuGet API Key as a GitHub Secret**:
   - Go to your GitHub repository.
   - Navigate to "Settings" > "Secrets and variables" > "Actions".
   - Click "New repository secret".
   - Name: `NUGET_API_KEY`
   - Value: Paste your NuGet API key.
   -

*[truncated — see source for full prompt]*