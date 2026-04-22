# Console Gui Framework

> This guide documents the Console GUI framework in CycoD, providing developers with information on how to use and extend the interactive console components.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Console GUI Framework Developer Guide

This guide documents the Console GUI framework in CycoD, providing developers with information on how to use and extend the interactive console components.

## Overview

The Console GUI framework provides a set of reusable components for building interactive terminal user interfaces. It's organized into two main categories:

- **Core Components**: Low-level building blocks for console manipulation
- **Controls**: High-level interactive UI components

## Architecture

```
src/common/ConsoleGui/
  Core/                      # Foundation components
    Screen.cs                # Console screen management
    Window.cs                # Window rendering and borders
    Rect.cs                  # Rectangle utilities
    Cursor.cs                # Cursor positioning
  Controls/                  # Interactive controls
    ControlWindow.cs         # Base class for all controls
    ScrollingControl.cs      # Base for scrollable content
    VirtualListBoxControl.cs # Base for efficient list rendering
    ListBoxControl.cs        # Concrete list implementation
    ListBoxPicker.cs         # Interactive list picker ⭐
    SpeedSearchListBoxControl.cs # Type-to-filter search
    EditBoxControl.cs        # Text input control
    EditBoxQuickEdit.cs      # Quick modal text input
    TextViewerControl.cs     # Text viewing with column selection
    HelpViewer.cs            # Interactive help viewer
  InOutPipeServer.cs         # Testing infrastructure
```

## Core Components

### Screen.cs

Manages the console screen dimensions and provides buffer operations.

**Key Methods:**
- `GetBufferWidth()` / `GetBufferHeight()` - Get console buffer dimensions
- `GetWindowHeight()` / `GetWindowWidth()` - Get visible window size
- `Clear()` - Clear the screen
- `Flush()` - Flush output buffer

**Example:**
```csharp
var width = Screen.GetBufferWidth();
var height = Screen.GetBufferHeight();
Console.WriteLine($"Screen: {width}x{height}");
```

### Window.

*[truncated — see source for full prompt]*