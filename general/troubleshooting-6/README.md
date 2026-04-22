# Troubleshooting

> This guide provides solutions for common issues you might encounter when using CycoD.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting

This guide provides solutions for common issues you might encounter when using CycoD.

## API Connection Issues

### Issue: Unable to connect to OpenAI API

**Symptoms:**
- Error messages about failed API calls
- "Connection refused" or timeout errors

**Possible Solutions:**
1. **Check API Key**: Ensure your OpenAI API key is correctly set in the environment variable `OPENAI_API_KEY`.
   ```bash
   # Check if the key is set (Linux/macOS)
   echo $OPENAI_API_KEY
   
   # Set the key if needed
   export OPENAI_API_KEY=your_api_key_here
   ```

2. **Check Internet Connection**: Verify you have a stable internet connection.

3. **Check API Status**: Visit [OpenAI Status Page](https://status.openai.com/) to see if there are any ongoing service disruptions.

4. **Check Firewall Settings**: Ensure your firewall allows outgoing connections to the OpenAI API.

## Function Calling Issues

### Issue: Shell Commands Not Working

**Symptoms:**
- Shell commands return errors or don't execute
- Permission errors when running commands

**Possible Solutions:**
1. **Check Permissions**: Ensure CycoD has the necessary permissions to execute commands.

2. **Path Issues**: For commands that rely on specific tools, ensure they are installed and in your PATH.
   ```bash
   # Check if a command is available (e.g., git)
   which git
   ```

3. **Shell Availability**: Ensure the requested shell is available on your system:
   - For `RunBashCommand`: Bash must be installed
   - For `RunCmdCommand`: Windows Command Prompt (only works on Windows)
   - For `RunPowershellCommand`: PowerShell must be installed

### Issue: File Operations Failed

**Symptoms:**
- Error messages when trying to create or modify files
- "Access denied" or "File not found" errors

**Possible Solutions:**
1. **Check File Permissions**: Ensure you have read/write permissions for the directories you're working with.

2. **Check File Paths**: Ensure you're using correct absolute or relative paths.

3. **

*[truncated — see source for full prompt]*