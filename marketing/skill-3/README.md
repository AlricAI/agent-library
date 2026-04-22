# SKILL

> **Version:** 1.0  
**Focus:** Unity 6 / 2022.3 LTS for Agent Visualization, Dashboards, and Interactive 3D Applications

---

## Table of Contents

1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Unity 3D Development Expert - SKILL.md

**Version:** 1.0  
**Focus:** Unity 6 / 2022.3 LTS for Agent Visualization, Dashboards, and Interactive 3D Applications

---

## Table of Contents

1. [Unity Engine Overview](#unity-engine-overview)
2. [C# Scripting Fundamentals](#c-scripting-fundamentals)
3. [Core Systems](#core-systems)
4. [Physics System](#physics-system)
5. [Animation System](#animation-system)
6. [UI System (UI Toolkit & uGUI)](#ui-system)
7. [Asset Pipeline](#asset-pipeline)
8. [Optimization](#optimization)
9. [Deployment](#deployment)
10. [Agent-Specific Patterns](#agent-specific-patterns)

---

## Unity Engine Overview

### Version Matrix

| Version | Status | Use Case |
|---------|--------|----------|
| Unity 6 | Current (2024+) | New projects, latest features |
| 2022.3 LTS | Stable | Production, long-term support |
| 2021.3 LTS | Legacy | Existing projects |

### Key Unity 6 Features

- **VFX Graph improvements**: Better GPU particle systems
- **ECS (Entity Component System)**: High-performance data-oriented design
- **DOTS Runtime**: Faster runtime with Burst compiler
- **APV (Adaptive Probe Volumes)**: Better lighting for dynamic scenes
- **DLSS/FSR Support**: Upscaling for performance
- **WebGPU backend**: Modern web export
- **SpeedTree 9**: Improved vegetation

### Unity Architecture

```
GameObject (container)
├── Transform (position, rotation, scale)
├── Component A (MonoBehaviour)
├── Component B (MonoBehaviour)
└── Component C (Renderer, Collider, etc.)
```

### Execution Order

```
Awake() → OnEnable() → Start() → FixedUpdate() → Update() → LateUpdate() → OnDisable() → OnDestroy()
```

---

## C# Scripting Fundamentals

### Script Lifecycle

```csharp
public class LifecycleDemo : MonoBehaviour
{
    // Called when script is loaded (even if disabled)
    void Awake()
    {
        Debug.Log("Awake: One-time initialization");
    }
    
    // Called when object becomes active
    void OnEnable()
    {
        Debug.Log("OnEnable: Subscrib

*[truncated — see source for full prompt]*