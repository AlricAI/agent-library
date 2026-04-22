# AMBIENT FS KOLLABOR INTEGRATION

> ## Overview

This spec covers how Kollabor connects to the ambient-fsd daemon.
For the daemon itself, see AMBIENT_FILESYSTEM_SPEC.md.

Kollabor become

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ambient-fs: Kollabor Integration Spec

## Overview

This spec covers how Kollabor connects to the ambient-fsd daemon.
For the daemon itself, see AMBIENT_FILESYSTEM_SPEC.md.

Kollabor becomes a CLIENT of ambient-fsd. It does not embed the
filesystem watching, event storage, or content analysis directly.
Instead, it connects via Unix socket and receives events + awareness
data from the daemon.


## Integration Architecture

```
ambient-fsd (separate process)
  |
  |  Unix socket (/tmp/ambient-fs.sock)
  |
  v
tauri-plugin-ambient-fs (Rust, in Kollabor's Tauri backend)
  |
  |  Tauri IPC events
  |
  v
useAmbientFs.ts (Vue composable)
  |
  |  reactive state
  |
  v
UniversalSidebar / FileTreeNode (UI)
```


## Tauri Plugin: tauri-plugin-ambient-fs

Lives at: ambient-fs/integrations/tauri-plugin-ambient-fs/

### Responsibilities

1. Auto-launch ambient-fsd if not running
2. Connect to daemon via Unix socket
3. Register Kollabor's projects with the daemon
4. Bridge daemon events to Tauri window events
5. Bridge Kollabor's tool_runner attribution to daemon
6. Expose IPC commands for frontend queries

### Rust API

```rust
// src-tauri/Cargo.toml
[dependencies]
tauri-plugin-ambient-fs = { path = "../ambient-fs/integrations/tauri-plugin-ambient-fs" }

// src-tauri/src/main.rs
fn main() {
    tauri::Builder::default()
        .plugin(tauri_plugin_ambient_fs::init())
        .run(tauri::generate_context!())
}
```

### IPC Commands (registered by plugin)

```
Frontend -> Backend:

  ambient_fs_watch_project(path)
    Register a project directory with the daemon.
    Returns project_id.

  ambient_fs_unwatch_project(project_id)
    Stop watching a project.

  ambient_fs_get_awareness(project_id, file_path)
    Get FileAwareness for a single file.

  ambient_fs_get_project_awareness(project_id)
    Get FileAwareness for all files in project.
    Returns Map<file_path, FileAwareness>.

  ambient_fs_get_events(project_id, filters)
    Query event log. Filters: since, source, fi

*[truncated — see source for full prompt]*