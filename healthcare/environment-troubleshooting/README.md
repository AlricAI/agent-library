# Environment Troubleshooting

> This comprehensive guide helps you diagnose and resolve common environment setup issues with Atlas.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Environment Troubleshooting Guide

This comprehensive guide helps you diagnose and resolve common environment setup issues with Atlas. Use this when Atlas doesn't start, configuration fails, or you encounter setup problems.

## 🚨 Quick Diagnosis

If Atlas isn't working, run this diagnostic command first:

```bash
python3 scripts/validate_config.py
```

This will identify most configuration issues with specific fix instructions.

## 📋 Systematic Troubleshooting Checklist

### 1. System Requirements Check

#### Python Version
```bash
python3 --version
```
**Requirement**: Python 3.9 or higher
**Issue**: `ImportError` or syntax errors
**Fix**: Install Python 3.9+ from https://python.org

#### System Dependencies
```bash
# Check if pip is available
pip3 --version

# Check if git is available (for cloning)
git --version
```

### 2. Installation Issues

#### Missing Dependencies
**Symptoms**: `ModuleNotFoundError` when running Atlas
```bash
# Install all required packages
pip3 install -r requirements.txt

# If requirements.txt is missing, install core dependencies
pip3 install requests beautifulsoup4 lxml readability pyyaml python-dotenv schedule
```

#### Permission Issues
**Symptoms**: `Permission denied` errors during installation
```bash
# Option 1: Use user installation (recommended)
pip3 install --user -r requirements.txt

# Option 2: Use virtual environment
python3 -m venv atlas_env
source atlas_env/bin/activate  # On Windows: atlas_env\Scripts\activate
pip3 install -r requirements.txt
```

#### Network/Proxy Issues
**Symptoms**: `Connection timeout` or `SSL errors` during installation
```bash
# For corporate networks, configure pip proxy
pip3 install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org -r requirements.txt
```

### 3. Configuration Problems

#### Missing .env File
**Symptoms**: Atlas runs but can't access external services
```bash
# Create .env file from template
cp .env.example .env

# Or use the a

*[truncated — see source for full prompt]*