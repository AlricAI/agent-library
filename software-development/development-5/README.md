# Development

> This guide is for people working on OpenHands and editing the source code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Development Guide

This guide is for people working on OpenHands and editing the source code.
If you wish to contribute your changes, check out the
[CONTRIBUTING.md](https://github.com/All-Hands-AI/OpenHands/blob/main/CONTRIBUTING.md)
on how to clone and setup the project initially before moving on. Otherwise,
you can clone the OpenHands project directly.

## Start the Server for Development

### 1. Requirements

- Linux, Mac OS, or [WSL on Windows](https://learn.microsoft.com/en-us/windows/wsl/install) [Ubuntu >= 22.04]
- [Docker](https://docs.docker.com/engine/install/) (For those on MacOS, make sure to allow the default Docker socket to be used from advanced settings!)
- [Python](https://www.python.org/downloads/) = 3.12
- [NodeJS](https://nodejs.org/en/download/package-manager) >= 22.x
- [Poetry](https://python-poetry.org/docs/#installing-with-the-official-installer) >= 1.8
- OS-specific dependencies:
  - Ubuntu: build-essential => `sudo apt-get install build-essential python3.12-dev`
  - WSL: netcat => `sudo apt-get install netcat`

Make sure you have all these dependencies installed before moving on to `make build`.

#### Dev container

There is a [dev container](https://containers.dev/) available which provides a
pre-configured environment with all the necessary dependencies installed if you
are using a [supported editor or tool](https://containers.dev/supporting). For
example, if you are using Visual Studio Code (VS Code) with the
[Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
extension installed, you can open the project in a dev container by using the
_Dev Container: Reopen in Container_ command from the Command Palette
(Ctrl+Shift+P).

#### Develop without sudo access

If you want to develop without system admin/sudo access to upgrade/install `Python` and/or `NodeJS`, you can use
`conda` or `mamba` to manage the packages for you:

```bash
# Download and install Mamba (a faster version of conda)
c

*[truncated — see source for full prompt]*