# Safety

> ClawArm controls real robotic hardware.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Safety Guide

ClawArm controls real robotic hardware. This document covers the safety mechanisms and procedures you need to know.

## Safety Hierarchy

1. **Physical E-stop** (highest priority) — hardware button on the arm controller
2. **Software emergency stop** — `arm_stop` tool or `POST /stop` with `emergency_stop`
3. **Software disable** — graceful shutdown via `arm_stop` or `POST /disable`
4. **Safety layer** — pre-move validation of joint limits, workspace bounds, speed
5. **Agent rules** — AGENTS.md instructions for confirmation and slow start

## Physical Safety Checklist

Before every session:

- [ ] Workspace is clear of people within the arm's reach envelope
- [ ] No objects that could be damaged by unexpected motion
- [ ] Physical E-stop button is within reach
- [ ] Someone is present who knows how to use the E-stop
- [ ] First test of new motions uses `speed_percent=30` or lower

## Safety Layer Details

### Joint Limits

Each robot type has per-joint angle limits (in radians):

**NERO (7-DOF)**

| Joint | Min (rad) | Max (rad) | Degrees |
|-------|-----------|-----------|---------|
| J1 | -2.618 | +2.618 | ±150° |
| J2 | -2.094 | +2.094 | ±120° |
| J3 | -2.618 | +2.618 | ±150° |
| J4 | -2.094 | +2.094 | ±120° |
| J5 | -2.618 | +2.618 | ±150° |
| J6 | -2.094 | +2.094 | ±120° |
| J7 | -2.618 | +2.618 | ±150° |

**Piper (6-DOF)**

| Joint | Min (rad) | Max (rad) | Degrees |
|-------|-----------|-----------|---------|
| J1 | -2.618 | +2.618 | ±150° |
| J2 | -2.094 | +2.094 | ±120° |
| J3 | -2.618 | +2.618 | ±150° |
| J4 | -2.094 | +2.094 | ±120° |
| J5 | -2.618 | +2.618 | ±150° |
| J6 | -1.571 | +1.571 | ±90° |

### Workspace Bounds (Default)

| Axis | Min | Max |
|------|-----|-----|
| X | -1.0 m | +1.0 m |
| Y | -1.0 m | +1.0 m |
| Z | -0.1 m | +1.2 m |

Customize by modifying `SafetyConfig` in the bridge server or setting environment variables.

### Speed Cap

Default maximum: **80%**. Override with `CLAWARM_MAX_SPEED` environment variable.

The AI a

*[truncated — see source for full prompt]*