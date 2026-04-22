# PUBLISHING

> This guide explains how to publish the OpenAI Agent SDK to Maven Central.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Publishing to Maven Central

This guide explains how to publish the OpenAI Agent SDK to Maven Central.

## Prerequisites

Before you can publish, you need to set up the following:

### 1. Maven Central Account

1. Create an account at [Maven Central Portal](https://central.sonatype.com/)
2. Verify your namespace `ai.acolite` (already verified for this project)
3. Generate publishing credentials (User Token) from your account page

### 2. GPG Key for Signing

Maven Central requires all artifacts to be signed with GPG:

```bash
# Generate a GPG key
gpg --gen-key

# List your keys
gpg --list-secret-keys --keyid-format LONG

# Export your private key (use the key ID from previous command)
gpg --armor --export-secret-keys YOUR_KEY_ID
```

### 3. GitHub Secrets

Add the following secrets to your GitHub repository (Settings → Secrets and variables → Actions):

| Secret Name | Description |
|-------------|-------------|
| `OSSRH_USERNAME` | Your Maven Central user token username (from central.sonatype.com account page) |
| `OSSRH_PASSWORD` | Your Maven Central user token password (from central.sonatype.com account page) |
| `GPG_PRIVATE_KEY` | Your GPG private key (entire output from export command) |
| `GPG_PASSPHRASE` | The passphrase for your GPG key |

**To get Maven Central credentials:**
1. Go to https://central.sonatype.com/ and log in
2. Click your profile → Account
3. Click "Generate User Token"
4. Copy the username and password
5. Add them as `OSSRH_USERNAME` and `OSSRH_PASSWORD` in GitHub Secrets

## Publishing Process

### Option 1: Manual Workflow Trigger (Recommended)

**Step 1: Bump the version in pom.xml**

```bash
# Update version from 0.1.0-SNAPSHOT to 0.1.0
mvn versions:set -DnewVersion=0.1.0 -DgenerateBackupPoms=false

# Commit the version bump
git add pom.xml
git commit -m "Bump version to 0.1.0 for release"
git push origin main
```

**Step 2: Trigger the publish workflow**

1. Go to **Actions** → **Publish to Maven Central**
2. Click **Run workflow**

*[truncated — see source for full prompt]*