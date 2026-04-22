# MODULE BROWSER AUTOMATION

> ## Overview

**File Location**: `/src/azure_haymaker/testing/browser_automation.py`

**Responsibility**: Execute automated E2E test scenarios on provi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Browser Automation & E2E Testing

## Overview

**File Location**: `/src/azure_haymaker/testing/browser_automation.py`

**Responsibility**: Execute automated E2E test scenarios on provisioned Cloud PCs via Selenium, validating Magentic-UI agent capabilities and M365 integrations.

**Status**: E2E testing component (Phase 4)

---

## 1. Purpose & Scope

### What It Does

The BrowserAutomationTester orchestrates browser-based E2E testing:

- **RDP Connection**: Establish remote desktop session to Cloud PC
- **Browser Control**: Launch and control Chrome/Edge via Selenium
- **Navigation**: Automated navigation to M365 applications
- **Interactions**: Click, type, form submission, etc.
- **Verification**: Assert expected behavior and state
- **Screenshot Capture**: Capture key states for reporting
- **Performance Metrics**: Measure page load times, action latencies
- **Report Generation**: JSON and HTML test reports

### What It Does NOT Do

- Unit testing of agent code (separate concern)
- Performance profiling beyond basic metrics
- Security/penetration testing
- Cross-browser compatibility testing (single browser focus)
- Load testing

---

## 2. Class Design

### BrowserAutomationTester

**Principle**: Modular test scenarios, reusable steps, comprehensive logging.

#### Constructor

```python
def __init__(
    self,
    cloud_pc_info: CloudPCInfo,
    browser_type: str = "chrome",  # "chrome" or "edge"
):
    """Initialize browser automation tester.

    Args:
        cloud_pc_info: CloudPCInfo with RDP connection details
        browser_type: Browser to use ("chrome" or "edge")

    Raises:
        ValueError: If cloud_pc_info invalid
    """
```

#### Instance Variables

```python
self.cloud_pc_info: CloudPCInfo
self.browser_type: str
self.rdp_session: Any | None  # RDP session object
self.driver: Any | None  # Selenium WebDriver
self.logger: logging.Logger
self.test_results: list[TestResult] = []
self.screenshots: list[ScreenshotRecord] = [

*[truncated — see source for full prompt]*