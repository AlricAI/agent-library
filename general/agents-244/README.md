# AGENTS

> Agent-readable onboarding instructions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dev VPS Client Setup

Agent-readable onboarding instructions. When an agent reads this file, it should walk the developer through each step interactively.

## Instructions for the Agent

You are setting up SSH access and the `vpscli` CLI for a shared development VPS. Walk the developer through this step by step, asking for preferences where noted. Do not skip steps or rush ahead — wait for confirmation before proceeding to the next step.

## Context

- **This repo**: You should already be in the `vpscli` repo checkout. If not, clone it first: `git clone https://github.com/donmasakayan/vpscli.git && cd vpscli`
- **VPS registry**: `machines.yaml` lists all VPS instances (name, host, user)
- **Shared user**: All developers SSH as the same user (defined per-machine) for pair programming via shared tmux sessions
- **Session system**: The VPS runs a tmux session manager. When two people connect to the same named session, they share the exact same terminal — this enables live pair programming.
- **CLI**: `vpscli` is the local client for managing VPS sessions

## Step 1: SSH Key

First, check if I already have SSH key pairs (`~/.ssh/id_ed25519.pub`, `~/.ssh/vps/id_vps_ed25519.pub`, or similar). If I do, ask whether I want to reuse an existing key or generate a dedicated one for this VPS.

If generating a new key:
1. Create the directory: `mkdir -p ~/.ssh/vps && chmod 700 ~/.ssh/vps`
2. Ask me for my **first name** (for the key filename) and **email address** (suggest `firstname@nextfinancial.io` as the format)
3. **IMPORTANT**: Use a unique filename per developer: `~/.ssh/vps/id_<name>_ed25519` (e.g. `id_don_ed25519`). Never overwrite an existing key file without explicit confirmation.
4. Generate with: `ssh-keygen -t ed25519 -C "<my-email>" -f ~/.ssh/vps/id_<name>_ed25519`
   - **Default to using a passphrase** for security. Let me choose the passphrase interactively.
   - After generation, check if an ssh-agent is running (`ssh-add -l 2>/dev/null`). If not, start one (`

*[truncated — see source for full prompt]*