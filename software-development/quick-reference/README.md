# QUICK REFERENCE

> Fast reference for common development tasks and commands.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# A.R.E.S Quick Reference Card

Fast reference for common development tasks and commands.

## 🚀 Quick Start

```bash
# Option 1: Install from crates.io
cargo install ares-server
ares-server init
ares-server

# Option 2: Install with embedded Web UI
cargo install ares-server --features ui
ares-server init
ares-server  # UI available at http://localhost:3000/

# Option 3: Clone and develop
git clone <repo>
cd ares
just setup
just run
```

## 🖥️ CLI Commands

```bash
# Initialize a new project
ares-server init                          # Create ares.toml and config/
ares-server init --provider openai        # Use OpenAI instead of Ollama
ares-server init --provider both          # Configure both providers
ares-server init --host 0.0.0.0 --port 8080  # Custom host/port
ares-server init --force                  # Overwrite existing files
ares-server init --minimal                # Minimal configuration
ares-server init --no-examples            # Skip TOON example files

# View configuration
ares-server config                        # Show config summary
ares-server config --full                 # Show full configuration
ares-server config --validate             # Validate configuration

# Manage agents
ares-server agent list                    # List all agents
ares-server agent show orchestrator       # Show agent details

# Run the server
ares-server                               # Start with default config
ares-server --config custom.toml          # Use custom config file
ares-server --verbose                     # Enable verbose logging
ares-server --no-color                    # Disable colored output

# Help
ares-server --help                        # Show all options
ares-server init --help                   # Show init options
ares-server --version                     # Show version
```

## 📋 Just Commands (Recommended)

Run `just --list` for all available commands. Here are the most common:

```bash
# Build
just build              # Debug build
just build-rele

*[truncated — see source for full prompt]*