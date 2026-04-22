# Queuing

> Genonaut uses Celery with Redis for asynchronous task processing, primarily for image generation jobs via ComfyUI integration.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Queuing: Celery + Redis for Async Tasks

Genonaut uses Celery with Redis for asynchronous task processing, primarily for image generation jobs via ComfyUI integration.

### Prerequisites

1. **Redis Server**: Install and start Redis
   ```bash
   # macOS
   brew install redis
   brew services start redis

   # Ubuntu/Debian
   sudo apt-get install redis-server
   sudo systemctl start redis

   # Docker
   docker run -d -p 6379:6379 redis:latest
   ```

2. **Environment Variables**: Already configured in `.env` (see env/.env for Redis URLs and namespaces)

### Set up
There is a configuration example currently in `env/redis.conf.example`. Use this as a template to create 
`env/redis.conf`, and be sure to set a real password. 

### Running Workers

Start a Celery worker to process async tasks. The worker includes a Beat scheduler (`-B` flag) for handling periodic tasks:

```bash
# Development environment
make celery-dev              # Start Celery worker with Beat scheduler for dev

# Demo/Test environments
make celery-demo             # Start Celery worker with Beat scheduler for demo
make celery-test             # Start Celery worker with Beat scheduler for test
```

**What the worker handles:**
- **Async tasks**: Image generation jobs via ComfyUI integration (queues: `default`, `generation`)
- **Scheduled tasks**: Periodic maintenance tasks configured in `config/base.json`:
  - Tag cardinality stats refresh (daily at midnight UTC)
  - Gen source stats refresh (hourly)

**Typical Workflow:**
```bash
# Terminal 1: Start API server
make api-dev

# Terminal 2: Start Celery worker with Beat scheduler
make celery-dev

# Terminal 3: (Optional) Start Flower monitoring dashboard
make flower-dev              # Access at http://localhost:5555
```

### Flower Monitoring Dashboard

Monitor your Celery workers and tasks in real-time:

```bash
make flower-dev              # Development (http://localhost:5555)
make flower-demo             # Demo
make flower-test             # Te

*[truncated — see source for full prompt]*