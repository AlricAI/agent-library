# Api

> This document describes the YouAndINotAI REST API endpoints and their usage.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Documentation

This document describes the YouAndINotAI REST API endpoints and their usage.

## Base URL

Production: `https://api.youandinotai.com/api/v1`

## Authentication

Most endpoints require authentication via JWT Bearer tokens.

```http
Authorization: Bearer <your-jwt-token>
```

## API Endpoints

### Health

#### GET /health

Check the health status of the API.

**Response:**

```json
{
  "status": "ok",
  "db_connected": true,
  "square_connected": true,
  "square_signature_configured": true,
  "wallet_rails_proven": false,
  "wallet_rails_status": "unproven",
  "payment_proof_labels": [],
  "user_count": 2
}
```

### Authentication

#### POST /auth/register

Register a new user.

**Request:**

```json
{
  "email": "user@example.com",
  "password": "securepassword",
  "display_name": "User Name"
}
```

**Response:**

```json
{
  "user_id": "uuid",
  "email": "user@example.com",
  "display_name": "User Name",
  "token": "jwt-token"
}
```

#### POST /auth/login

Authenticate a user and obtain a JWT token.

**Request:**

```json
{
  "email": "user@example.com",
  "password": "securepassword"
}
```

**Response:**

```json
{
  "user_id": "uuid",
  "email": "user@example.com",
  "display_name": "User Name",
  "token": "jwt-token"
}
```

#### POST /auth/refresh

Refresh an expired JWT token.

**Headers:**

```http
Authorization: Bearer <expired-jwt-token>
```

**Response:**

```json
{
  "token": "new-jwt-token"
}
```

### Users

#### GET /users/me

Get the current user's profile.

**Headers:**

```http
Authorization: Bearer <jwt-token>
```

**Response:**

```json
{
  "id": "uuid",
  "email": "user@example.com",
  "display_name": "User Name",
  "bio": "User biography",
  "created_at": "2026-01-01T00:00:00Z"
}
```

#### PUT /users/me

Update the current user's profile.

**Headers:**

```http
Authorization: Bearer <jwt-token>
```

**Request:**

```json
{
  "display_name": "New Name",
  "bio": "Updated biography"
}
```

**Response:**

```json
{
  "id": "uuid",

*[truncated — see source for full prompt]*