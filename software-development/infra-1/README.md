# INFRA

> Lumineer uses Terraform to manage all GCP infrastructure as code.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Infrastructure Reference

Lumineer uses Terraform to manage all GCP infrastructure as code. This document covers the resource inventory, Terraform variable reference, and operational procedures.

---

## Resource Inventory

| Resource | Name | Type | Purpose |
|----------|------|------|---------|
| Cloud Run service | `lumineer-api` | `google_cloud_run_v2_service` | Gateway (public HTTPS) |
| Cloud Run service | `lumineer-ai` | `google_cloud_run_v2_service` | AI Processing (internal) |
| Artifact Registry | `lumineer-images` | `google_artifact_registry_repository` | Docker image store |
| Service Account | `lumineer-api-sa` | `google_service_account` | Identity for Gateway |
| Service Account | `lumineer-ai-sa` | `google_service_account` | Identity for AI Processing |
| Service Account | `lumineer-gh-actions-sa` | `google_service_account` | CI/CD identity |
| Secret | `lumineer-openai-api-key` | `google_secret_manager_secret` | OpenAI API key |
| Secret | `lumineer-qdrant-url` | `google_secret_manager_secret` | Qdrant Cloud URL |
| Secret | `lumineer-qdrant-api-key` | `google_secret_manager_secret` | Qdrant Cloud API key |
| WIF Pool | `lumineer-github-pool` | `google_iam_workload_identity_pool` | Keyless auth for GitHub Actions |
| Firebase (managed externally) | — | Firebase Hosting | Frontend CDN |

> Cloud SQL is **not managed by Terraform** in the current setup. Use a free PostgreSQL provider (e.g., [Neon](https://neon.tech)) and inject `DATABASE_URL` directly into the Backend service environment.

---

## Terraform Directory

```
infra/
├── provider.tf          # Google provider + required_providers
├── variables.tf         # All input variables with defaults and validation
├── cloud_run.tf         # Cloud Run services (API + AI) + GCP API enablement
├── iam.tf               # Service accounts, IAM bindings, Workload Identity Federation
├── secrets.tf           # Secret Manager resources (slots only — values set manually)
├── firebase.tf          # Firebase 

*[truncated — see source for full prompt]*