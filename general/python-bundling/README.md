# PYTHON BUNDLING

> This document explains how to bundle Python with the Local Operator UI application for macOS to avoid requiring admin privileges during installation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bundling Python with Local Operator UI

This document explains how to bundle Python with the Local Operator UI application for macOS to avoid requiring admin privileges during installation.

## Overview

Instead of installing Python via Homebrew (which requires admin privileges), we bundle a standalone Python directly with the application using [python-build-standalone](https://github.com/indygreg/python-build-standalone). This approach:

- Eliminates the need for admin privileges during installation
- Makes the application more self-contained
- Works offline
- Provides a more reliable user experience
- Supports installation of Python packages via pip

## Setup Instructions

### 1. Download Standalone Python

We provide a script that automatically downloads and sets up the standalone Python for you:

```bash
# Run the setup script to download and configure standalone Python
pnpm setup-python-standalone
```

This script will:

1. Download the appropriate standalone Python build from the python-build-standalone project
2. Extract it to the resources/python directory
3. Make the Python binary executable

### 2. Build the Application

The electron-builder configuration in `package.json` has been updated to include the standalone Python in the build. When you build the application, the Python directory will be included in the app's resources directory.

```bash
pnpm dist:mac
```

## How It Works

1. The standalone Python is included in the app's resources directory
2. During installation, the application uses the bundled Python to create a virtual environment
3. The local-operator package is installed in the virtual environment
4. The application uses the virtual environment to run the local-operator backend

## Implementation Details

We use Gregory Szorc's [python-build-standalone](https://github.com/indygreg/python-build-standalone) project, which provides a version of Python that is designed for easy bundling. This is the same approach used by:

- [Datasette Deskto

*[truncated — see source for full prompt]*