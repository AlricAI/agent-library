# SECURITY

> ## Reporting Security Vulnerabilities

If you discover a security vulnerability in CodeFRAME, please report it by emailing the maintainers. Do not cre

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Policy

## Reporting Security Vulnerabilities

If you discover a security vulnerability in CodeFRAME, please report it by emailing the maintainers. Do not create public GitHub issues for security vulnerabilities.

## Security Best Practices

### Authentication & Authorization (Issue #132)

CodeFRAME implements comprehensive authentication and authorization to address OWASP A01 - Broken Access Control vulnerability.

#### Authentication
- **Email/Password**: Secure authentication with bcrypt password hashing (salt rounds=12)
- **Session Management**: 7-day sessions with automatic expiry and cleanup
- **Token Validation**: All API requests validate Bearer tokens against sessions table
- **Better Auth**: Frontend authentication using Better Auth v1.4.7

#### Authorization
- **Project Ownership**: All projects have an owner (user_id in projects table)
- **Role-Based Access**: Owner, collaborator, and viewer roles via project_users table
- **Access Checks**: All API endpoints verify `user_has_project_access()` before operations
- **403 vs 404**: Returns 403 Forbidden (not 404) for unauthorized access to prevent information leakage

#### Audit Logging
- **Comprehensive Logging**: All authentication, authorization, and lifecycle events logged
- **Database Persistence**: audit_logs table with indexes for performance
- **Event Types**: AUTH_LOGIN_SUCCESS, AUTH_LOGIN_FAILED, AUTHZ_ACCESS_GRANTED, AUTHZ_ACCESS_DENIED, PROJECT_CREATED, etc.
- **Metadata**: Structured JSON metadata for each event (user_id, ip_address, resource details)

#### Security Configuration

Authentication is **always required**. All API endpoints require valid JWT Bearer tokens.

**See Also**: [docs/authentication.md](docs/authentication.md) for complete authentication guide.

### Command Injection Prevention

CodeFRAME's `AdaptiveTestRunner` executes test commands detected from project configuration files. To prevent command injection vulnerabilities:

#### Safe Command Execution

The `Adapti

*[truncated — see source for full prompt]*