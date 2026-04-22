# DEPLOYMENT

> ## 🎯 Deployment Options

### Option 1: MCP Server (Recommended for Claude Code)

This integrates directly with Claude Code to provide slash commands 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Context Engineering - Deployment Guide

## 🎯 Deployment Options

### Option 1: MCP Server (Recommended for Claude Code)

This integrates directly with Claude Code to provide slash commands and automatic optimization.

#### Setup Steps

1. **Locate Your Claude Code MCP Configuration**
   ```bash
   # Usually located at:
   # macOS: ~/Library/Application Support/Claude/mcp_settings.json
   # Linux: ~/.config/Claude/mcp_settings.json
   # Windows: %APPDATA%/Claude/mcp_settings.json
   ```

2. **Add OOS Context Engineering Server**
   ```json
   {
     "mcpServers": {
       "oos-context": {
         "command": "python3",
         "args": ["/path/to/your/oos/mcp_server.py"],
         "cwd": "/path/to/your/oos",
         "env": {
           "PYTHONPATH": "/path/to/your/oos/src"
         }
       }
     }
   }
   ```

3. **Install Dependencies**
   ```bash
   cd /path/to/your/oos
   pip install fastapi uvicorn pydantic
   ```

4. **Restart Claude Code**
   - Close Claude Code completely
   - Reopen Claude Code
   - Slash commands should now be available

#### Verification
Test with: `/help-me test the context engineering system`

### Option 2: Standalone Tools (For Terminal Users)

If you prefer to use the tools directly:

1. **Set Up Python Environment**
   ```bash
   cd /path/to/your/oos
   python3 -m venv venv
   source venv/bin/activate  # Linux/Mac
   # or venv\Scripts\activate  # Windows
   pip install -r requirements/base.txt
   ```

2. **Test Core Components**
   ```bash
   # Test clarification workflow
   python3 bin/clarification_cli.py

   # Test code health tools
   ./bin/oos-doctor

   # Test token optimization
   python3 -m src.token_optimization --test
   ```

## 🔧 Configuration

### Environment Variables
```bash
# Optional: Set custom configuration
export OOS_CONTEXT_BUDGET=4000        # Default token budget
export OOS_AUTO_OPTIMIZE=true         # Enable auto-optimization
export OOS_LOG_LEVEL=info             # Logging level
export OOS_CACHE_DIR=/t

*[truncated — see source for full prompt]*