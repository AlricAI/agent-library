# Compilation Guide

> This comprehensive guide covers building Docu from source code, packaging for distribution, and deployment options.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Compilation and Packaging Guide

This comprehensive guide covers building Docu from source code, packaging for distribution, and deployment options.

## Table of Contents

1. [Development Environment Setup](#development-environment-setup)
2. [Building from Source](#building-from-source)
3. [Testing](#testing)
4. [Packaging for Distribution](#packaging-for-distribution)
5. [VS Code Extension Installation](#vs-code-extension-installation)
6. [Troubleshooting Build Issues](#troubleshooting-build-issues)
7. [Continuous Integration](#continuous-integration)

## Development Environment Setup

### Prerequisites

#### Required Software
- **Node.js 20.x or higher** - [Download Node.js](https://nodejs.org/)
- **npm 10.x or higher** - Included with Node.js
- **Git** - [Download Git](https://git-scm.com/)
- **VS Code 1.97.0+** - [Download VS Code](https://code.visualstudio.com/)

#### Recommended Tools
- **VS Code Extensions**:
  - TypeScript and JavaScript Language Features (built-in)
  - ESLint
  - Prettier
  - Jest Test Explorer
- **Command Line Tools**:
  - `vsce` - VS Code Extension Manager
  - `typescript` - TypeScript compiler

### Environment Verification

Check your environment setup:

```bash
# Check Node.js version
node --version
# Should output: v20.x.x or higher

# Check npm version
npm --version
# Should output: 10.x.x or higher

# Check Git version
git --version
# Should output: git version 2.x.x or higher

# Check VS Code version
code --version
# Should output: 1.97.0 or higher
```

### Install Global Dependencies

```bash
# Install VS Code Extension Manager
npm install -g @vscode/vsce

# Install TypeScript compiler (optional, project includes local version)
npm install -g typescript

# Verify installations
vsce --version
tsc --version
```

## Building from Source

### Step 1: Clone Repository

```bash
# Clone the repository
git clone https://github.com/rodhayl/specItGithubCopilot.git

# Navigate to project directory
cd specItGithubCopilot
# Check repository s

*[truncated — see source for full prompt]*