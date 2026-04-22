# Notion Sync Troubleshooting

> ## Error: `object_not_found: Could not find database with ID`

This error means the Notion API cannot find your database. Here's how to fix it:

### S

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Notion Sync Troubleshooting Guide

## Error: `object_not_found: Could not find database with ID`

This error means the Notion API cannot find your database. Here's how to fix it:

### Step 1: Verify Your Database ID

1. **Open your Notion database** in a web browser
2. **Click the "..." menu** (three dots) in the top-right corner
3. **Click "Copy link"** or look at the URL in your browser
4. **Extract the database ID** from the URL:

   ```
   https://notion.so/workspace/2d393eb1e6d18094b716d2fc817db224?v=...
                                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                                    This is your database ID
   ```

5. **Update your `.env` file**:
   ```bash
   NOTION_DATABASE_ID="2d393eb1-e6d1-8094-b716-d2fc817db224"
   # OR without hyphens:
   NOTION_DATABASE_ID="2d393eb1e6d18094b716d2fc817db224"
   ```

   Both formats work - the code will normalize it automatically.

### Step 2: Share Database with Integration

**This is the most common cause of this error!**

1. **Open your Notion database**
2. **Click the "..." menu** (three dots) in the top-right corner
3. **Click "Add connections"** or "Connections"
4. **Select your Notion integration** from the list
   - If you don't see it, you may need to create one first at https://www.notion.so/my-integrations
5. **Ensure the integration has "Read" permissions** (or "Full access" for syncing)

### Step 3: Verify Integration Permissions

1. Go to https://www.notion.so/my-integrations
2. Click on your integration
3. Check the **"Capabilities"** section:
   - ✅ **Read content** - Required
   - ✅ **Read database** - Required (if available)
   - ✅ **Update content** - Optional (for two-way sync)

### Step 4: Verify API Key

Make sure your `NOTION_API_KEY` in `.env` is correct:

1. Go to https://www.notion.so/my-integrations
2. Click on your integration
3. Copy the **"Internal Integration Token"** (starts with `secret_`)
4. Update your `.env`:
   ```bash
   NOTION_API_KEY="secret_..."
   ```

*[truncated — see source for full prompt]*