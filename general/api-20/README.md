# Api

> Genonaut provides a complete REST API built with FastAPI, offering 77 endpoints across all core functionality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Documentation

Genonaut provides a complete REST API built with FastAPI, offering 77 endpoints across all core functionality.

## Running the API Server

Start the API server using the make commands for different database environments:

**Development Database:**
```bash
make api-dev
```

**Demo Database:**
```bash
make api-demo
```

**Test Database:**
```bash
make api-test
```

**Manual Start (Advanced):**
```bash
# Development database
APP_ENV=dev uvicorn genonaut.api.main:app --host 0.0.0.0 --port 8001 --reload

# Demo database
APP_ENV=demo uvicorn genonaut.api.main:app --host 0.0.0.0 --port 8001 --reload

# Test database
APP_ENV=test uvicorn genonaut.api.main:app --host 0.0.0.0 --port 8001 --reload
```

## API Configuration

### Environment Variables

| Environment Variable | Description | Default | Example |
|---------------------|-------------|---------|---------|
| `API_SECRET_KEY` | Secret key for JWT tokens and cryptographic operations | `your-secret-key-change-this-in-production` | `my-super-secret-key-123` |
| `API_HOST` | Host address for the API server | `0.0.0.0` | `127.0.0.1` |
| `API_PORT` | Port for the API server | `8001` | `9000` |
| `API_DEBUG` | Enable debug mode (auto-reload, detailed errors) | `false` | `true` |
| `APP_ENV` | Which database to use by default (`dev`/`demo`/`test`) | `dev` | `test` |
| `DATABASE_URL_DEMO` | Demo database connection URL | Uses `DATABASE_URL` with demo DB name | `postgresql://user:pass@localhost:5432/genonaut_demo` |

## API Documentation & Testing

Once the server is running, you can access:

- **Interactive API Docs (Swagger):** `http://localhost:8001/docs`
- **Alternative API Docs (ReDoc):** `http://localhost:8001/redoc`
- **Health Check:** `http://localhost:8001/api/v1/health`
- **Database Info:** `http://localhost:8001/api/v1/databases`
- **Global Statistics:** `http://localhost:8001/api/v1/stats/global`

## API Endpoints Overview

The API provides **77 endpoints** across 6 main categories:

| Category |

*[truncated — see source for full prompt]*