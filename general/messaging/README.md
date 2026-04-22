# Messaging

> ## Introduction

The mooR RPC/IPC messaging layer is a critical component of the mooR system, providing the
communication infrastructure that connects

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# mooR Messaging Layer Overview

## Introduction

The mooR RPC/IPC messaging layer is a critical component of the mooR system, providing the
communication infrastructure that connects different parts of the application architecture. It
enables the flow of messages between daemon, hosts, workers, and clients, forming the backbone of
the distributed system that powers mooR's virtual social spaces.

The messaging layer uses ZeroMQ (zmq/0mq) for inter-process communication, allowing for efficient
and flexible message passing between the various components of the system. 0mq supports multiple
messaging patterns, including request-reply and publish-subscribe.

When running purely on a single host, the IPC (Inter-Process Communication) transport can be used
for fast local communication. IPC endpoints (e.g., `ipc:///tmp/moor_rpc.sock`) use Unix domain
sockets that rely on filesystem permissions for security and do not use encryption.

When running in a distributed environment, TCP transport is used to communicate over the network.
TCP endpoints (e.g., `tcp://0.0.0.0:7899`) automatically enable CURVE encryption to protect all
communication. In this manner, the daemon can run on one machine while the hosts and workers can run
on different machines, allowing for a scalable, flexible, and resilient architecture.

## Purpose

The messaging layer serves several key purposes:

1. **Process Isolation**: Separates the daemon (core server) from host processes that handle client
   connections
2. **Distributed Operation**: Allows hosts and workers to run on different machines from the daemon
3. **Protocol Management**: Handles the serialization and deserialization of messages between
   components
4. **Authentication**: Provides secure token-based authentication between system components
5. **Event Broadcasting**: Enables publishing events to multiple subscribers (hosts, clients,
   workers)

## Architecture Components

The mooR messaging layer follows a multi-process architecture wit

*[truncated — see source for full prompt]*