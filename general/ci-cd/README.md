# Ci Cd

> This document provides an overview of the CI/CD workflows configured for the CycoD project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CI/CD Workflows for CycoD

This document provides an overview of the CI/CD workflows configured for the CycoD project.

## Available Workflows

### 1. CI Workflow

**File**: `.github/workflows/ci.yml`

**Triggers**:
- Pull requests to the `main` branch
- Direct pushes to the `main` branch
- Scheduled nightly builds (midnight UTC)
- Manual triggering via GitHub UI

**Purpose**:
- Validate that the codebase can be built successfully
- Run tests to ensure code quality
- Provide early feedback on pull requests
- Verify cross-platform builds (Windows, Linux, macOS)

**Steps**:
1. Check out code
2. Set up .NET 8.0
3. Restore dependencies
4. Build in Release configuration
5. Publish for multiple platforms (Windows, Linux, macOS)
6. Run tests and generate test reports
7. Upload test results as artifacts
8. Publish test results to GitHub UI
9. Upload build artifacts for inspection (including platform-specific builds)

### 2. Release Workflow

**File**: `.github/workflows/release.yml`

**Triggers**:
- Tags matching the pattern `X.Y.Z-YYYYMMDD` (e.g., `1.0.0-20250330`)
- Manual triggering via GitHub UI (with version parameter)

**Purpose**:
- Build and test the application
- Create platform-specific builds (Windows, Linux, macOS)
- Create and package a release version
- Generate a NuGet package with cross-platform support
- Optionally publish to NuGet.org

**Steps**:
1. Check out code
2. Set up .NET 8.0
3. Determine version from tag or input
4. Update version in project file
5. Build in Release configuration
6. Publish specific builds for Windows, Linux, and macOS
7. Run tests and generate test reports
8. Upload and publish test results
9. Create NuGet package (including all platform runtimes)
10. Generate package checksums
11. Upload NuGet package as an artifact
12. Publish to NuGet.org (if API key is configured)

## Cross-Platform Support

CycoD is built with cross-platform compatibility in mind and includes runtime components for:
- Windows (win-x64)
- Linux (linux-x64)
-

*[truncated — see source for full prompt]*