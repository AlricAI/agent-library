# CONTENT RELAY DOCUMENTATION BRIEF

> ## Section 1 — What This App Does
### Purpose (plain English)
Content Relay is a stage-based content operations app that moves work from intake to liv

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Documentation Brief: Content Relay Web App
## Section 1 — What This App Does
### Purpose (plain English)
Content Relay is a stage-based content operations app that moves work from intake to live publication with clear ownership, required-field gates, and visible handoffs so teams can execute without guessing what to do next.

### The two tracks
| Track | What it manages | End state |
|---|---|---|
| Blogs | Long-form editorial and publishing workflow | Blog is published |
| Social Posts | Social creative + review + posting + proof-of-publication | Post is published with at least one live link |

### How they differ operationally
| Area | Blogs | Social Posts |
|---|---|---|
| Workflow shape | Writing flow plus publishing flow | Single end-to-end social status flow |
| Midpoint handoff | Writing completion hands off to publishing | Creative review hands off back to execution owner |
| Final gate | Publishing completion rules | Live link gate before `Published` |
| Terminal behavior | Published content exits active workflow | `Published` is terminal; no active owner |

## Section 2 — Key Concepts & Roles
### Roles
| Role | Practical responsibility |
|---|---|
| Creator/Worker (Assigned owner) | Executes drafting, revisions, publishing actions, and link submission |
| Reviewer | Reviews quality, requests changes, or approves forward movement |
| Admin | Configures users/permissions and can perform operational overrides/tools |

### Core concepts
| Term | Definition |
|---|---|
| Stage | A named workflow status that controls what happens next |
| Gate | A required condition that must be true before stage transition |
| Handoff | Ownership change between execution and review functions |
| Terminal stage | Final stage where no further workflow action is expected |

### Ownership rule of thumb
- Work stage = execution owner acts.
- Review stage = reviewer acts.
- Terminal stage = done, no active owner.

## Section 3 — Social Post Pipeline
### Stage-by-stage map
| Status 

*[truncated — see source for full prompt]*