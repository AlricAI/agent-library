# DEPENDENCY GRAPH VISUAL

> **Standalone visual reference for enhancement dependencies**

See [Enhancement Dependencies](../specs/ENHANCEMENT_DEPENDENCIES.md) for detailed analys

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhancement Dependency Graph

**Standalone visual reference for enhancement dependencies**

See [Enhancement Dependencies](../specs/ENHANCEMENT_DEPENDENCIES.md) for detailed analysis.

---

## Complete Dependency Graph

```mermaid
graph TD
    %% Open PRs
    PR119[PR #119: W365 + M365 E2E<br/>✅ Ready to Merge]
    PR121[PR #121: Windows VM<br/>⚠️ Has Security Issues]
    PR123[PR #123: Computer Use<br/>Waiting on PR #121]
    PR112[PR #112: KW CLI<br/>✅ Ready to Merge]

    %% P0-Critical Enhancements
    E124[#124: SIEM Export<br/>P0-Critical<br/>ROI: 120%]
    E125[#125: VM Security<br/>P0-Critical<br/>ROI: 1,165%]

    %% P1-High Enhancements
    E126[#126: Multi-Tenant<br/>P1-High<br/>ROI: 233%]
    E127[#127: Distributed Tracing<br/>P1-High<br/>ROI: 36%]
    E128[#128: Cost Enforcement<br/>P1-High<br/>ROI: 184%]
    E129[#129: Circuit Breakers<br/>P1-High]

    %% P2-Medium Enhancements
    E130[#130: Local Dev<br/>P2-Medium]
    E131[#131: GitHub Actions<br/>P2-Medium]
    E132[#132: Dashboard<br/>P2-Medium]
    E133[#133: Testing Framework<br/>P2-Medium]

    %% Special nodes
    ArchReview[Architecture Review<br/>Required]

    %% Dependencies
    PR119 -->|UNBLOCKS| E124
    PR119 -->|provides data| E127
    PR119 -->|provides data| E132

    E125 -->|FIXES| PR121
    PR121 -->|enables| PR123

    E124 -->|enriches| E127
    E127 -->|provides correlation| E132
    E124 -->|provides data| E132

    E126 -->|REQUIRES| ArchReview

    E129 -->|monitors| PR123
    E129 -->|monitors| E124

    E130 -->|improves testing| PR112
    E133 -->|tests| PR112

    E128 -.->|independent| E127
    E131 -.->|independent| E124

    %% Styling
    style PR119 fill:#90EE90,stroke:#2d7a2d,stroke-width:3px
    style E124 fill:#FF6B6B,stroke:#a52a2a,stroke-width:3px
    style E125 fill:#FF6B6B,stroke:#a52a2a,stroke-width:3px
    style E126 fill:#FFD93D,stroke:#b8860b
    style E127 fill:#FFD93D,stroke:#b8860b
    style E128 fill:#FFD93D,stroke:#b8860b
    style E129 fill:#FFD

*[truncated — see source for full prompt]*