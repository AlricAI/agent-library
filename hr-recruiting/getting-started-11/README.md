# Getting Started

> This guide walks you through building a working Ratatoskr application from scratch.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started

This guide walks you through building a working Ratatoskr application from scratch. By the end, you will have a message producer and consumer running with RabbitMQ and the transactional outbox.

## Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download) or later
- [Docker](https://docs.docker.com/get-docker/) (for RabbitMQ and PostgreSQL)

## 1. Start Infrastructure

Create a `docker-compose.yml` with RabbitMQ and PostgreSQL:

```yaml
services:
  rabbitmq:
    image: rabbitmq:4-management
    ports:
      - "5672:5672"
      - "15672:15672"
  postgres:
    image: postgres:17
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: ratatoskr
      POSTGRES_PASSWORD: ratatoskr
      POSTGRES_DB: orders
```

Start the services:

```bash
docker compose up -d
```

## 2. Create the Project

```bash
dotnet new web -n OrderService
cd OrderService
dotnet add package Ratatoskr
dotnet add package Ratatoskr.EfCore
dotnet add package Ratatoskr.RabbitMq
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package DistributedLock.FileSystem
```

## 3. Define a Message

Create a `Messages/OrderPlaced.cs` file. The `[RatatoskrMessage]` attribute sets the CloudEvents `type` used for routing:

```csharp
using Ratatoskr;

[RatatoskrMessage("order.placed")]
public record OrderPlaced(Guid OrderId, string CustomerEmail, decimal Total);
```

## 4. Create a Handler

Create a `Handlers/OrderPlacedHandler.cs` file. Handlers implement `IMessageHandler<T>`:

```csharp
using Ratatoskr.Core;

public class OrderPlacedHandler(ILogger<OrderPlacedHandler> logger)
    : IMessageHandler<OrderPlaced>
{
    public Task HandleAsync(
        OrderPlaced message,
        MessageProperties properties,
        CancellationToken cancellationToken)
    {
        logger.LogInformation("Processing order {OrderId} for {Email}",
            message.OrderId, message.CustomerEmail);
        return Task.CompletedTask;
    }
}
```

## 5. Set Up the DbContext



*[truncated — see source for full prompt]*