# Setup

> ## 📋 Prerequisites

Before starting the setup process, ensure you have:

- **n8n instance**: Either [self-hosted](https://docs.n8n.io/hosting/) or [n

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Setup Guide: GitHub Issues to Slack Notification Workflow

## 📋 Prerequisites

Before starting the setup process, ensure you have:

- **n8n instance**: Either [self-hosted](https://docs.n8n.io/hosting/) or [n8n.cloud](https://www.n8n.cloud/) account
- **GitHub repository**: Admin access to the repository you want to monitor
- **Slack workspace**: Permission to create apps and webhooks

## 🔧 Installation Steps

### Step 1: Set Up Your n8n Instance

1. If not already running, install and configure your n8n instance:
   - **Self-hosted**: Follow the [official installation guide](https://docs.n8n.io/hosting/installation/)
   - **n8n.cloud**: Sign up at [n8n.cloud](https://www.n8n.cloud/) and create a new workspace

2. Log in to your n8n dashboard

### Step 2: Import the Workflow

1. In the n8n dashboard, navigate to **Workflows** in the left sidebar
2. Click the **Import from File** button in the top-right corner
   ```
   [PLACEHOLDER: Screenshot of n8n import button]
   ```
3. Upload the `github_issues_slack_notification.json` file from this repository
4. Click **Import** to add the workflow to your n8n instance
5. Once imported, you'll see the complete workflow with all nodes ready for configuration
   ```
   [PLACEHOLDER: Screenshot of imported workflow]
   ```

### Step 3: Configure GitHub Webhook

1. In n8n, open the imported workflow by clicking on its name
2. Find and click on the **GitHub Trigger** node to select it
3. In the node settings panel, click **Add Credential** > **GitHub Webhook API**
   ```
   [PLACEHOLDER: Screenshot of GitHub node configuration]
   ```
4. Enter a name for this credential (e.g., "GitHub Issues Webhook")
5. Click **Create** to generate a webhook URL
6. Copy the generated webhook URL to your clipboard

Now, set up the webhook in GitHub:

1. Navigate to your GitHub repository in a new browser tab
2. Go to **Settings** > **Webhooks** (you need admin access)
3. Click **Add webhook**
   ```
   [PLACEHOLDER: Screenshot of GitHub webho

*[truncated — see source for full prompt]*