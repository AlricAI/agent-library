# API

> All requests go through the **Gateway** at port `3000`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Reference

All requests go through the **Gateway** at port `3000`. The gateway proxies `/api/*` to the Backend service.

Interactive Swagger UI is available at **http://localhost:3001/api/docs** (Backend direct, dev only).

---

## Base URL

| Environment | URL |
|-------------|-----|
| Local development | `http://localhost:3000` |
| Production | `https://<gateway-cloud-run-url>` |

---

## Authentication

Protected endpoints require a JWT access token in the `Authorization` header:

```
Authorization: Bearer <access_token>
```

Access tokens expire in **15 minutes**. Use the refresh endpoint to obtain a new one.

---

## Endpoints

### Auth

#### `POST /api/auth/register`

Register a new user.

**Request body:**

```json
{
  "email": "user@example.com",
  "password": "securepassword",
  "display_name": "Alice"
}
```

**Response `201`:**

```json
{
  "user": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "email": "user@example.com",
    "display_name": "Alice"
  },
  "access_token": "<jwt>",
  "refresh_token": "<jwt>"
}
```

**Errors:** `409` Email already registered

---

#### `POST /api/auth/login`

Log in with email and password.

**Request body:**

```json
{
  "email": "user@example.com",
  "password": "securepassword"
}
```

**Response `200`:** Same shape as register.

**Errors:** `401` Invalid credentials

---

#### `POST /api/auth/refresh`

Exchange a refresh token for a new access token.

**Request body:**

```json
{
  "refresh_token": "<jwt>"
}
```

**Response `200`:**

```json
{
  "access_token": "<jwt>"
}
```

**Errors:** `401` Invalid or expired refresh token

---

#### `GET /api/auth/me` 🔒

Get the currently authenticated user's profile.

**Response `200`:**

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "email": "user@example.com",
  "display_name": "Alice",
  "created_at": "2026-01-15T09:00:00.000Z"
}
```

---

### Courses

#### `POST /api/search`

Search Coursera courses using natural language or keywords. Supports metad

*[truncated — see source for full prompt]*