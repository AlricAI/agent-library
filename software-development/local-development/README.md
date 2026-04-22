# Local Development

> This guide covers setting up your local development environment for Keyteki.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Local Development Setup

This guide covers setting up your local development environment for Keyteki.

## Table of Contents

-   [Running Unit Tests](#running-unit-tests)
-   [Prerequisites](#prerequisites)
-   [Quick Start (Docker)](#quick-start-docker)
    -   [macOS Setup](#macos-setup)
    -   [Accessing the Site](#accessing-the-site)
-   [Hybrid Setup (Docker + Local Node)](#hybrid-setup-docker--local-node)
-   [Non-Docker Setup](#non-docker-setup)
    -   [Required Software](#required-software)
    -   [Setup Steps](#setup-steps)
-   [Useful Commands](#useful-commands)
    -   [Running Tests](#running-tests)
    -   [Linting](#linting)
    -   [In-Game Testing](#in-game-testing)
    -   [Locales](#locales)
-   [Troubleshooting](#troubleshooting)
    -   [Memory Allocation Errors](#memory-allocation-errors)
    -   [package-lock.json Changes Unexpectedly](#package-lockjson-changes-unexpectedly)
    -   [dlopen Errors](#dlopen-errors)
    -   [Git Submodule Issues](#git-submodule-issues)

## Running Unit Tests

For running unit tests, see [Testing Cards](testing-cards.md). It is not necessary to run the full server to run unit tests, and the majority of development can be done by running tests directly.

## Prerequisites

-   Git
-   Node.js v22.22.0
-   Docker (recommended) or PostgreSQL + Redis

## Quick Start (Docker)

Docker is the recommended approach for local development.

### macOS Setup

-   Install [Docker Desktop](https://docs.docker.com/desktop/setup/install/mac-install/)

-   Install a Node version manager ([nvm](https://github.com/nvm-sh/nvm) or [asdf](https://asdf-vm.com/))

-   Install Node v22.22.0:

    ```bash
    # Using nvm
    nvm install 22.22.0
    nvm use 22.22.0

    # Using asdf (add `legacy_version_file = yes` to ~/.asdfrc first)
    asdf install nodejs 22.22.0
    ```

-   Clone and set up the repository:

    ```bash
    git clone https://github.com/keyteki/keyteki.git
    cd keyteki
    git submodule init
    git submodule update

*[truncated — see source for full prompt]*