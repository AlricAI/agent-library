# Api

> ## Overview

The Octopus Trading Platform provides a comprehensive RESTful API built with FastAPI, offering real-time market data, portfolio managemen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔗 API Documentation - Octopus Trading Platform™

## Overview

The Octopus Trading Platform provides a comprehensive RESTful API built with FastAPI, offering real-time market data, portfolio management, risk analysis, and advanced trading capabilities.

## Base URL

- **Development**: `http://localhost:8000`
- **Production**: `https://your-domain.com`

## Authentication

All API endpoints require authentication via JWT tokens.

### Getting Started

1. **Register/Login** to get access token:
```bash
curl -X POST "http://localhost:8000/api/auth/login" \
  -H "Content-Type: application/json" \
  -d '{"email": "demo@octopus.trading", "password": "demo123"}'
```

2. **Use the token** in subsequent requests:
```bash
curl -H "Authorization: Bearer YOUR_TOKEN" \
  "http://localhost:8000/api/portfolios/"
```

## Core Endpoints

### 🔐 Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/refresh` - Refresh token
- `GET /api/auth/me` - Get current user profile

### 📊 Market Data
- `GET /api/market/quote/{symbol}` - Real-time quote
- `GET /api/market/historical/{symbol}` - Historical data
- `GET /api/market/search` - Symbol search
- `GET /api/market/trending` - Trending stocks

### 💼 Portfolio Management
- `GET /api/portfolios/` - List user portfolios
- `POST /api/portfolios/` - Create new portfolio
- `GET /api/portfolios/{id}` - Get portfolio details
- `PUT /api/portfolios/{id}` - Update portfolio
- `DELETE /api/portfolios/{id}` - Delete portfolio

### 📈 Positions
- `GET /api/portfolios/{id}/positions` - List positions
- `POST /api/portfolios/{id}/positions` - Add position
- `PUT /api/positions/{id}` - Update position
- `DELETE /api/positions/{id}` - Close position

### 🎯 Orders
- `POST /api/orders/` - Place order
- `GET /api/orders/` - List orders
- `GET /api/orders/{id}` - Get order details
- `PUT /api/orders/{id}/cancel` - Cancel order

### ⚠️ Risk Management
- `GET /api/risk/portfolio/{id}` - Portfolio

*[truncated — see source for full prompt]*