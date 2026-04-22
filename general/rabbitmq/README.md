# Rabbitmq

> The RabbitMQ transport provides production-grade message delivery via AMQP.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RabbitMQ Transport

The RabbitMQ transport provides production-grade message delivery via AMQP. It handles exchange and queue topology provisioning, consumer lifecycle management, CloudEvents AMQP encoding, retry with dead-letter queues, and health checks.

## Setup

Install the package and configure the transport:

```bash
dotnet add package Ratatoskr.RabbitMq
```

[!code-csharp[](../examples/Docs/Program.cs#ConfigureRabbitMq)]

The `ConnectionString` accepts a standard AMQP URI (`amqp://user:pass@host:port/vhost`).

## Exchange Types

Ratatoskr supports three AMQP exchange types:

| Exchange Type | Routing Behavior | Use Case |
|---------------|-----------------|----------|
| **Topic** (default) | Pattern matching on routing key (`order.*`, `#`) | Events with flexible subscriptions |
| **Direct** | Exact routing key match | Commands targeted at specific consumers |
| **Fanout** | Broadcast to all bound queues (routing key ignored) | Notifications to all subscribers |

Configure per channel:

```csharp
// Topic exchange (default) — pattern-based routing
bus.AddEventPublishChannel("orders.events", c => c
    .WithRabbitMq(r => r.WithTopicExchange())
    .Produces<OrderPlaced>());

// Direct exchange — exact routing key match
bus.AddCommandConsumeChannel("orders.commands", c => c
    .WithRabbitMq(r => r
        .WithDirectExchange()
        .WithQueueName("orders.commands.queue"))
    .Consumes<ProcessPayment>(m => m.WithHandler<ProcessPaymentHandler>()));

// Fanout exchange — broadcast to all queues
bus.AddEventPublishChannel("notifications", c => c
    .WithRabbitMq(r => r.WithFanoutExchange())
    .Produces<SystemAlert>());
```

## Queue Types

| Queue Type | Description |
|------------|-------------|
| **Quorum** (default) | Replicated across cluster nodes. Recommended for production. |
| **Classic** | Single-node queue. Lower latency, no replication. |

```csharp
.WithRabbitMq(r => r
    .WithQueueName("orders.handler")
    .WithQueueType(QueueType.Classic))

*[truncated — see source for full prompt]*