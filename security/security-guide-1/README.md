# SECURITY GUIDE

> ## Essential Security Measures

### File System Security
```bash
# Set secure permissions for .env file
chmod 600 .env

# Secure your data directory
c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Guide for Atlas

## Essential Security Measures

### File System Security
```bash
# Set secure permissions for .env file
chmod 600 .env

# Secure your data directory
chmod 700 /path/to/your/data/directory

# Use full-disk encryption (strongly recommended)
# macOS: FileVault
# Windows: BitLocker
# Linux: LUKS
```

### API Key Management
- **Never commit API keys** to version control
- **Use environment variables** via .env files only
- **Rotate keys regularly** if supported by the service
- **Monitor API usage** to detect unauthorized access
- **Use least-privilege keys** when available

### Network Security
- **Use HTTPS** for all external requests (Atlas does this by default)
- **Be cautious on public networks** when downloading content
- **Consider VPN** for sensitive research topics
- **Monitor network traffic** if processing sensitive content

### Data Protection
- **Full-disk encryption** is essential - Atlas doesn't encrypt data at rest
- **Regular backups** to secure, offline storage
- **Access controls** on your device and data directory
- **Secure deletion** when removing sensitive content

## Privacy Considerations

### Local Processing
- **AI processing** happens locally when possible (Whisper, local models)
- **External APIs** only used when you configure them
- **No telemetry** or usage data collection
- **No cloud dependencies** for core functionality

### Content Handling
- **Source attribution** preserved in metadata
- **Processing logs** may contain content snippets
- **Temporary files** created during processing - cleaned automatically
- **Cache files** may persist - review periodically

### Third-Party Services
When you configure external APIs:
- **Review privacy policies** of each service
- **Understand data handling** practices
- **Monitor usage** through service dashboards
- **Consider data residency** requirements

## Threat Model Considerations

### What Atlas Protects Against
- **Vendor lock-in** - All data in standard formats
- *

*[truncated — see source for full prompt]*