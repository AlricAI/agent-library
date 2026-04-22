# WEBSOCKET DEPLOYMENT

> This guide explains how to deploy the WebSocket server (required for Interactive Mode in the music player) on Railway.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# WebSocket Server Deployment Guide for Railway

This guide explains how to deploy the WebSocket server (required for Interactive Mode in the music player) on Railway.

## Problem

The Interactive Mode feature in the music player requires a WebSocket proxy server (`ws-server.js`) that connects the client to OpenAI's Realtime API. However, Railway services can only expose ONE public port per service.

## Solution: Create a Separate Railway Service

The best approach is to create a dedicated Railway service for the WebSocket server.

### Step 1: Create a New Railway Service

1. In your Railway project dashboard, click **"New Service"**
2. Select **"Deploy from GitHub repo"**
3. Choose the same repository but configure it differently

### Step 2: Configure the WebSocket Service

In Railway, configure the new service with these settings:

#### Build Configuration
```
Root Directory: web
Build Command: (leave empty - no build needed)
Start Command: npm run start:ws
```

#### Environment Variables
Set these environment variables for the WebSocket service:
- `NODE_ENV=production`
- `OPENAI_API_KEY=your_openai_api_key_here`
- `WS_PORT=3001` (optional, defaults to 3001)
- `PORT=3001` (Railway will use this for the public port)

### Step 3: Get the WebSocket Service URL

1. Once deployed, Railway will give you a URL like: `ws-service-name-production.railway.app`
2. Note this URL - you'll need it for the web service configuration

### Step 4: Update Web Service Environment Variables

In your main web service (the one running Next.js), add this environment variable:

```
NEXT_PUBLIC_WS_URL=wss://your-ws-service-url.railway.app
```

**Important**: Use `wss://` (secure WebSocket) for production, not `ws://`

### Step 5: Deploy Both Services

1. Deploy the WebSocket service first
2. Then deploy/redeploy the web service with the updated `NEXT_PUBLIC_WS_URL`

## Alternative: Single Service with Concurrently (NOT RECOMMENDED)

While we've set up `concurrently` to run both servers in 

*[truncated — see source for full prompt]*