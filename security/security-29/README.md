# SECURITY

> ## Overview

qtests v4.0.0 maintains enterprise-grade security posture with comprehensive defense-in-depth security measures to protect against common

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Policy

## Overview

qtests v4.0.0 maintains enterprise-grade security posture with comprehensive defense-in-depth security measures to protect against common attack vectors in testing frameworks.

## 🛡️ Security Features

### Input Validation & Sanitization
- **Command Injection Prevention**: All external command execution uses allow-list validation and argument sanitization
- **Path Traversal Protection**: Dynamic module loading includes path validation to prevent directory traversal attacks
- **Environment Variable Security**: Restricted environment variable access with allow-list enforcement

### Code Injection Prevention
- **Eval() Elimination**: No use of eval() or Function constructor with dynamic strings
- **Template Injection Protection**: Safe template literal usage with input validation
- **Command Separation**: Commands executed with argument arrays rather than concatenated strings

### Dependency Security
- **Vulnerability Management**: Regular dependency audits with automated fix application
- **Version Pinning**: Critical security dependencies pinned to specific versions
- **Supply Chain Security**: Verification of package integrity before installation

### Process Security
- **Safe Spawning**: All child processes use `shell: false` and validated arguments
- **Resource Limits**: CPU, memory, and file handle limits enforced
- **Permission Control**: Minimal privilege execution with explicit permission checks

### Information Disclosure Prevention
- **Sanitized Error Logging**: No sensitive data exposed in error messages or stack traces
- **Debug File Security**: Debug files have restricted permissions and sanitized content
- **Production Data Protection**: No user data or secrets included in logs or output

## 🔒 Supported Security Measures

### Runtime Protection
- **Module Validation**: All dynamic requires validated against allow-lists
- **Environment Isolation**: Test execution environments are isolated and cleaned
- **Resource Cleanup*

*[truncated — see source for full prompt]*