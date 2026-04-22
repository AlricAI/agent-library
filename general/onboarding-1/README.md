# Onboarding

> > **Last updated:** 2025-02-15 &nbsp;|&nbsp; **Audience:** New contributors & returning team members

Welcome to **Offgrid** — a fictitious online adv

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Offgrid — Monorepo Onboarding Guide

> **Last updated:** 2025-02-15 &nbsp;|&nbsp; **Audience:** New contributors & returning team members

Welcome to **Offgrid** — a fictitious online adventure store that sells biking, winter sports, and water sports equipment. This monorepo contains everything needed to run two full-stack systems locally: a **customer-facing shop** and a **staff-facing admin portal**.

---

## Table of Contents

- [Offgrid — Monorepo Onboarding Guide](#offgrid--monorepo-onboarding-guide)
  - [Table of Contents](#table-of-contents)
  - [📐👷🏻‍♀️ Architecture Overview](#️-architecture-overview)
  - [🗺️ Repository Layout](#️-repository-layout)
  - [🦾 Technology Stack](#-technology-stack)
  - [🏗️ Local Setup](#️-local-setup)
    - [Prerequisites](#prerequisites)
    - [Step 1 — Clone \& verify tooling](#step-1--clone--verify-tooling)
    - [Step 2 — Configure environment files](#step-2--configure-environment-files)
      - [Infrastructure (required first)](#infrastructure-required-first)
      - [Shop app](#shop-app)
      - [Portal app](#portal-app)
      - [Hosts file (required for Docker auth flows)](#hosts-file-required-for-docker-auth-flows)
    - [Step 3 — Start infrastructure](#step-3--start-infrastructure)
    - [Step 4 — Run database migrations](#step-4--run-database-migrations)
    - [Step 5 — Start apps \& APIs](#step-5--start-apps--apis)
    - [Quick-check — service URLs](#quick-check--service-urls)
  - [☑️ Common Tasks](#️-common-tasks)
    - [Manage the local infra stack](#manage-the-local-infra-stack)
    - [Connect to services](#connect-to-services)
  - [✅ VS Code Tasks \& Extensions](#-vs-code-tasks--extensions)
  - [🧩 Domain Event Flow (Portal)](#-domain-event-flow-portal)
  - [🗝️ Authentication \& Keycloak](#️-authentication--keycloak)
  - [🏛️ it Conventions](#️-it-conventions)
  - [⚖️ Decision Making](#️-decision-making)
  - [🐞 Gotchas \& Troubleshooting](#-gotchas--troubleshooting)
  - [👉 Where to Go Next](#-where-to-go-

*[truncated — see source for full prompt]*