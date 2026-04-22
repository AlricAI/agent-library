# AMBIENT FILESYSTEM SPEC

> ## Overview

A standalone daemon that watches project directories, logs every filesystem
event with attribution, runs background content analysis, and

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ambient-fs: Standalone Filesystem Awareness Daemon

## Overview

A standalone daemon that watches project directories, logs every filesystem
event with attribution, runs background content analysis, and exposes it all
via a client API. Any app (Kollabor, VS Code plugin, CLI tool, remote agent)
connects to the daemon and gets live filesystem intelligence.

This is not an embedded library. It's a service that runs independently.
Like Watchman, but with event sourcing, content analysis, and multi-machine
sync built in.

```
$ ambient-fsd start
$ ambient-fsd watch ~/dev/my-project
$ ambient-fsd events --since="1h" --source=ai_agent

  10:32  ai_agent  created   src/api/routes.ts      (chat: "Fix auth")
  10:33  user      modified  README.md
  10:41  git       added     48 files                (git pull main)
```


## System Architecture

```
+-----------------------------------------------------------+
|                    ambient-fsd (daemon)                     |
|                                                             |
|  +-------------+  +---------------+  +------------------+  |
|  |  Watcher    |  |  Event Store  |  |  Content         |  |
|  |  (notify)   |->|  (SQLite)     |->|  Analyzer        |  |
|  |             |  |               |  |  (ast-grep+grep) |  |
|  +-------------+  +-------+-------+  +--------+---------+  |
|                            |                   |            |
|                    +-------v-------------------v-------+    |
|                    |     Awareness Aggregator          |    |
|                    +---------------+-------------------+    |
|                                    |                        |
|                    +---------------v-------------------+    |
|                    |     Server (Unix Socket + gRPC)   |    |
|                    +-----------------------------------+    |
+-----------------------------------------------------------+
          |                    |                    |
          v    

*[truncated — see source for full prompt]*