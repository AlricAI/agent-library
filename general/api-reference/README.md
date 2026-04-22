# Api Reference

> This document provides detailed documentation for the ModPorter AI REST API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Reference

This document provides detailed documentation for the ModPorter AI REST API.

## Base URL

```
http://localhost:8080/api/v1
```

## Authentication

The API uses JWT tokens for authentication. Include the token in the `Authorization` header:

```
Authorization: Bearer <access_token>
```

---

## Authentication Endpoints

### Register User

Create a new user account.

**Endpoint:** `POST /api/v1/auth/register`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "SecurePass123!"
}
```

**Password Requirements:**
- At least 8 characters
- At least one number
- Both uppercase and lowercase letters
- At least one special character (!@#$%^&*()_+-=[]{}|;:,.<>?)

**Response (201):**
```json
{
  "message": "User registered. Please check email for verification link.",
  "user_id": "uuid-string"
}
```

**Errors:**
- `400`: Email already registered
- `422`: Invalid password requirements

---

### Login

Authenticate and receive access tokens.

**Endpoint:** `POST /api/v1/auth/login`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "SecurePass123!"
}
```

**Response (200):**
```json
{
  "access_token": "eyJhbGc...",
  "refresh_token": "eyJhbGc...",
  "token_type": "bearer"
}
```

**Errors:**
- `401`: Invalid email or password
- `403`: Email not verified

---

### Refresh Token

Refresh an expired access token.

**Endpoint:** `POST /api/v1/auth/refresh`

**Request Body:**
```json
{
  "refresh_token": "eyJhbGc..."
}
```

**Response (200):**
```json
{
  "access_token": "eyJhbGc...",
  "token_type": "bearer"
}
```

**Errors:**
- `401`: Invalid or expired refresh token

---

### Verify Email

Verify user's email address.

**Endpoint:** `GET /api/v1/auth/verify-email/{token}`

**Path Parameters:**
- `token`: Verification token from email

**Response (200):**
```json
{
  "message": "Email verified successfully"
}
```

---

### Forgot Password

Request a password reset email.

**Endpoint:** `POST /api/v1/auth/forgot-password

*[truncated — see source for full prompt]*