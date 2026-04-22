# BUILD

> This document provides instructions for building Local Operator UI distributables for different platforms.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Building Local Operator UI

This document provides instructions for building Local Operator UI distributables for different platforms.

## Prerequisites

Before building the application, ensure you have the following installed:

- **Node.js**: Version 22.13.1 or higher
- **pnpm**: For package management
- **Git**: For version control

## Build Framework

Local Operator UI uses [electron-builder](https://www.electron.build/) for creating distributables. This framework provides:

- Cross-platform building capabilities
- Code signing integration
- Auto-update functionality
- Configurable output formats

## Building the Application

### Quick Start

To build the application for your current platform:

```bash
# Install dependencies
pnpm install

# Build the application
pnpm dist
```

The built distributables will be available in the `dist/` directory.

### Platform-Specific Builds

You can build for specific platforms using the following commands:

```bash
# Build for macOS
pnpm dist:mac

# Build for Windows
pnpm dist:win

# Build for Linux
pnpm dist:linux

# Build for all platforms (requires appropriate environment)
pnpm dist:all
```

## Code Signing

Code signing and notarization are essential for distributing desktop applications. For detailed information about the code signing and notarization process, see the [CODE_SIGNING.md](./docs/CODE_SIGNING.md) document.

### Environment Variables

The following environment variables are used for code signing across all platforms:

- `CSC_CONTENT`: Base64-encoded signing certificate (p12 file)
- `CSC_KEY_PASSWORD`: Password for the signing certificate

For macOS notarization, additional variables are required:

- `APPLE_ID`: Your Apple ID email
- `APPLE_ID_PASSWORD`: App-specific password for your Apple ID
- `APPLE_TEAM_ID`: Your Apple Developer Team ID
- `NOTARIZE`: Set to "true" to enable notarization (optional)

You can set these variables in your CI/CD pipeline or locally in a `.env.build` file before building.

### Loc

*[truncated — see source for full prompt]*