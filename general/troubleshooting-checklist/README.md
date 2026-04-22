# Troubleshooting Checklist

> *Quick reference for common Atlas issues and solutions*

## 🚀 Quick Start Verification

Before troubleshooting, run these quick checks:

```bash
# 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Troubleshooting Checklist

*Quick reference for common Atlas issues and solutions*

## 🚀 Quick Start Verification

Before troubleshooting, run these quick checks:

```bash
# 1. Quick setup verification
python scripts/setup_check.py

# 2. Full environment diagnosis
python scripts/diagnose_environment.py

# 3. Configuration validation
python scripts/validate_config.py
```

## 📋 Common Issues Checklist

### Installation Issues
-   [ ] **Python version is 3.9 or higher**
    -   **Check:** `python3 --version`
    -   **Fix:** Install Python 3.9+ from https://python.org

-   [ ] **All dependencies are installed**
    -   **Check:** Run `python scripts/setup_check.py`
    -   **Fix:** `pip3 install -r requirements.txt`

-   [ ] **Project files are present**
    -   **Check:** `ls run.py helpers/config.py requirements.txt`
    -   **Fix:** Ensure you're in the Atlas project directory

### Configuration Issues
-   [ ] **Configuration file exists**
    -   **Check:** `ls config/.env`
    -   **Fix:** `cp .env.example config/.env`

-   [ ] **Configuration is valid**
    -   **Check:** `python scripts/validate_config.py`
    -   **Fix:** Follow validation error guidance

-   [ ] **API keys are properly formatted**
    -   **Check:** OpenRouter keys start with `sk-or-v1-`
    -   **Fix:** Get correct keys from service providers

### Permission Issues
-   [ ] **Output directory is accessible**
    -   **Check:** `ls -la output/`
    -   **Fix:** `mkdir -p output && chmod 755 output`

-   [ ] **Can write to data directory**
    -   **Check:** `touch output/.test && rm output/.test`
    -   **Fix:** `chmod 755 output` or change DATA_DIRECTORY

### Runtime Issues
-   [ ] **Atlas CLI responds**
    -   **Check:** `python run.py --help`
    -   **Fix:** Check dependencies and configuration

-   [ ] **Network connectivity works**
    -   **Check:** `ping google.com`
    -   **Fix:** Check firewall/proxy settings

-   [ ] **External APIs are accessible**
    -   **Check:** `p

*[truncated — see source for full prompt]*