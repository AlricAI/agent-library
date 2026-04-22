# Authentication

> This document provides comprehensive guidance on CodeFRAME's authentication and authorization system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Authentication & Authorization Guide

This document provides comprehensive guidance on CodeFRAME's authentication and authorization system.

**Last Updated**: 2026-01-06
**Status**: Production Ready (FastAPI Users with JWT)

## Table of Contents

- [Overview](#overview)
- [Authentication](#authentication)
- [Authorization](#authorization)
- [Audit Logging](#audit-logging)
- [Security Considerations](#security-considerations)
- [API Reference](#api-reference)

---

## Overview

CodeFRAME implements a layered security architecture using **FastAPI Users** with JWT tokens:

1. **Authentication Layer**: FastAPI Users with JWT Bearer tokens
2. **Authorization Layer**: Project ownership model with role-based access control
3. **Audit Layer**: Comprehensive logging of security-relevant events

### Key Features

- **Email/Password Authentication**: Secure user registration and login
- **JWT Tokens**: Stateless authentication with configurable lifetime
- **Project Ownership**: Automatic owner assignment on project creation
- **Role-Based Access**: Owner, collaborator, and viewer roles
- **WebSocket Authentication**: Token-based auth via query parameter
- **Audit Logging**: Comprehensive logging of auth/authz events

---

## Authentication

### Architecture

CodeFRAME uses **FastAPI Users** for authentication, a production-ready authentication library that provides:

- JWT token generation and validation
- User registration and management
- Password hashing (bcrypt)
- SQLAlchemy integration

### Backend Auth Module

```
codeframe/auth/
├── __init__.py          # Module exports
├── dependencies.py      # FastAPI dependencies (get_current_user, etc.)
├── manager.py           # UserManager, JWT configuration
├── models.py            # SQLAlchemy User model
├── router.py            # Auth routes (/auth/jwt/login, /auth/register)
└── schemas.py           # Pydantic schemas (UserCreate, UserRead, UserUpdate)
```

### JWT Configuration

Tokens are configured in `codeframe/auth/mana

*[truncated — see source for full prompt]*