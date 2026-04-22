# USAGE

> This document describes how to run the onboarding plan and task scripts for the Orbot project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bolt Onboarding Plan - USAGE

This document describes how to run the onboarding plan and task scripts for the Orbot project.

Quick summary
- A Bolt module plan is available: `bolt/modules/onboard/plans/onboard.pp`.
- Run with Bolt: `bolt plan run onboard::onboard yes=true` (or `yes=false`).
- Tasks are in `bolt/tasks/` and can be run individually for troubleshooting.
- Scripts log to `bolt/logs/`.

## Installing the Bolt (Puppet Bolt) CLI (required)

Before running the module plan with Bolt, install the Bolt CLI. Many of the provided helpers assume `bolt` is available and runnable; without it the single-command plan experience won't work — you can still run individual scripts directly, but installing Bolt is recommended.

Primary (recommended): official install guide
- The most reliable way to install Bolt is to follow the official installation documentation for your platform. This ensures you get the supported, up-to-date release and any platform-specific prerequisites.
- Official Bolt installation docs: https://puppet.com/docs/bolt/latest/bolt_installing.html

macOS options
- Preferred: follow the official installer instructions linked above.
- Homebrew may provide Bolt under different taps or names depending on your Homebrew setup. If you prefer Homebrew you can try:

```bash
# Try the simple install first (package name may vary across taps)
brew tap puppetlabs/puppet
brew install --cask puppet-bolt
```

Add `/opt/puppetlabs/bin` to your PATH in .zshrc or .bash_profile as needed:
export PATH="/opt/puppetlabs/bin:$PATH"



Windows options
- Chocolatey (recommended on Windows) or winget are common installers. Example (elevated PowerShell required for Chocolatey installs):

```powershell
# Install via Chocolatey (run in elevated PowerShell)
choco install puppet-bolt -y || choco install bolt -y || Write-Output "If choco can't find bolt, follow the official installer: https://puppet.com/docs/bolt/latest/bolt_installing.html"
# Verify
bolt --version
```

- Alternati

*[truncated — see source for full prompt]*