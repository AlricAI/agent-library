# RPC API SPEC

> ## Overview

This document provides a technical reference for the mooR RPC API. The API enables communication
between the daemon ( core server) and va

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# mooR RPC API Specification

## Overview

This document provides a technical reference for the mooR RPC API. The API enables communication
between the daemon ( core server) and various client types: hosts (TCP/WebSocket connection
handlers), workers (external service handlers), and end-user clients.

All messages are serialized using [FlatBuffers](https://flatbuffers.dev/) as defined in
`crates/common/schema/moor_rpc.fbs`. For architectural context, see `doc/messaging.md`.

### Key Concepts

- **Daemon**: The core server process managing the database, VM, and task scheduling
- **Host**: A process handling client connections (e.g., telnet-host, web-host)
- **Worker**: A background process performing specialized tasks (e.g., HTTP requests)
- **Client**: An end-user connection managed by a host
- **Connection Object**: A negative object ID representing a client connection
- **Player Object**: A positive object ID representing an authenticated user

### Transport

The API uses [ZeroMQ](https://zeromq.org/) with two patterns:

1. **[Request-Reply](https://zeromq.org/socket-api/#request-reply-pattern) (REQ/REP)**: For direct
   host/worker → daemon communication
2. **[Publish-Subscribe](https://zeromq.org/socket-api/#publish-subscribe-pattern) (PUB/SUB)**: For
   daemon → host/client/worker broadcasts

### Transport Security

ZeroMQ communication security depends on the endpoint type:

#### TCP Endpoints (Encrypted)

When using TCP endpoints (e.g., `tcp://0.0.0.0:7899`), all communication is secured using
**CurveZMQ** encryption:

- **CURVE Protocol**: Uses Curve25519 elliptic curve cryptography for encryption and authentication
- **ZAP Authentication**: The daemon validates connecting hosts/workers via ZeroMQ Authentication
  Protocol (ZAP)
- **Key Exchange**: Each host/worker has a unique CURVE keypair; public keys are registered during
  enrollment
- **Encryption**: All messages are encrypted end-to-end with ephemeral session keys
- **Enrollment Flow**:
  1. Host/work

*[truncated — see source for full prompt]*