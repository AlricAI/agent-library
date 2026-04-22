# SKILL

> **Version:** 1.0  
**Last Updated:** 2026-03-28  
**Specialization:** High-fidelity 3D, Real-time Rendering, Virtual Production, Photorealistic Visual

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Unreal Engine 5 Expert Skill

**Version:** 1.0  
**Last Updated:** 2026-03-28  
**Specialization:** High-fidelity 3D, Real-time Rendering, Virtual Production, Photorealistic Visualization

---

## Overview

This skill provides comprehensive expertise in Unreal Engine 5 for creating photorealistic 3D experiences, virtual production workflows, and high-end interactive applications. Covers Nanite virtualized geometry, Lumen dynamic global illumination, MetaHuman characters, Blueprints visual scripting, C++ development, and complete asset pipelines.

---

## Core Technologies

### 1. Nanite - Virtualized Geometry

**What it is:** A virtualized micropolygon geometry system that allows importing film-quality source art with millions/billions of polygons directly into UE5.

**Key Capabilities:**
- Import ZBrush sculpts, photogrammetry scans, CAD models without polygon reduction
- Automatic LOD management - no manual LOD creation needed
- No loss of detail at any distance
- Supports massive scene complexity

**Best Practices:**
```
✓ Enable Nanite on static meshes with >2000 triangles
✓ Use Nanite for: terrain, architecture, hero props, background assets
✓ Keep non-Nanite for: foliage (use WPO), translucent materials, sky spheres, skeletal meshes
✓ Memory: Nanite uses 20-40% more VRAM than traditional LODs but eliminates pop-in
```

**Performance Considerations:**
- Primary View Rays: Nanite renders only visible triangles
- Shadow Maps: Nanite can increase shadow rendering cost
- Lumen Reflections: Higher cost with Nanite geometry
- Translucency: Keep non-Nanite for glass/water

**Import Settings:**
- FBX/OBJ/USD formats supported
- Enable "Build Nanite" in Import Settings
- Adjust "Position Precision" for memory optimization
- Use "Reduction Settings" only if memory is constrained

---

### 2. Lumen - Dynamic Global Illumination

**What it is:** A fully dynamic global illumination and reflections system that reacts immediately to scene and light changes.

**Key Capabilit

*[truncated — see source for full prompt]*