# Architecture

> This page explains how messages flow through Ratatoskr — from publishing through transport to handler invocation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture

This page explains how messages flow through Ratatoskr — from publishing through transport to handler invocation. Understanding this pipeline helps you make informed decisions about transport choice, durability configuration, and error handling.

## Package Overview

Ratatoskr is split into four packages. The core library provides the abstractions and message routing pipeline. Transport and durability packages plug into the core via well-defined interfaces.

```mermaid
graph LR
    subgraph Core ["Ratatoskr (Core)"]
        IRatatoskr["IRatatoskr"]
        IMessageSender["IMessageSender"]
        IMessageHandler["IMessageHandler&lt;T&gt;"]
        IRouteInterceptor["IMessageRouteInterceptor"]
        MessageRouter["MessageRouter"]
        MessageDispatcher["MessageDispatcher"]
        HandlerInvoker["HandlerInvoker"]
        ChannelRegistry["ChannelRegistry"]
    end

    subgraph EfCore ["Ratatoskr.EfCore"]
        EfCoreSender["EfCoreMessageSender"]
        OutboxProcessor["OutboxProcessor"]
        InboxProcessor["InboxProcessor"]
        InboxAcceptor["InboxAcceptor"]
        InboxInterceptor["InboxRouteInterceptor"]
        OutboxInterceptor["OutboxTriggerInterceptor"]
    end

    subgraph RabbitMq ["Ratatoskr.RabbitMq"]
        RmqSender["RabbitMqMessageSender"]
        RmqConsumer["RabbitMqConsumer"]
        TopologyManager["RabbitMqTopologyManager"]
    end

    IRatatoskr -->|"byte[], MessageProperties"| IMessageSender
    IMessageSender -.->|"implements"| EfCoreSender
    IMessageSender -.->|"implements"| RmqSender
    EfCoreSender -->|"byte[], MessageProperties"| InboxAcceptor
    RmqConsumer -->|"byte[], MessageProperties"| MessageRouter
    MessageRouter -->|"byte[], MessageProperties"| IRouteInterceptor
    IRouteInterceptor -.->|"implements"| InboxInterceptor
    InboxInterceptor -->|"byte[], MessageProperties"| InboxAcceptor
    MessageRouter -->|"byte[], MessageProperties"| MessageDispatcher
    MessageDispatcher -->|"object, Messag

*[truncated — see source for full prompt]*