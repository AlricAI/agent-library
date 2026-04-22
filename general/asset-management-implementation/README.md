# ASSET MANAGEMENT IMPLEMENTATION

> This document describes the implementation of the asset management system for the ModPorter-AI addon editor.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Asset Management Implementation

This document describes the implementation of the asset management system for the ModPorter-AI addon editor.

## Overview

The asset management system allows users to upload, manage, and organize assets (textures, sounds, models, etc.) associated with their Minecraft Bedrock addons. The implementation consists of backend CRUD operations, API endpoints, and frontend components.

## Backend Implementation

### CRUD Operations

The following CRUD operations have been implemented in `/backend/src/db/crud.py`:

#### `get_addon_asset(session: AsyncSession, asset_id: PyUUID) -> Optional[models.AddonAsset]`

Retrieves a specific addon asset by its ID.

#### `create_addon_asset(session: AsyncSession, *, addon_id: PyUUID, file, asset_type: str, commit: bool = True) -> models.AddonAsset`

Creates a new addon asset entry in the database and saves the file.

#### `update_addon_asset(session: AsyncSession, *, asset_id: PyUUID, file, commit: bool = True) -> Optional[models.AddonAsset]`

Updates an existing addon asset with a new file.

#### `delete_addon_asset(session: AsyncSession, *, asset_id: PyUUID, commit: bool = True) -> Optional[dict]`

Deletes an addon asset from the database and removes the file from storage.

#### `create_addon_asset_from_local_path(session: AsyncSession, *, addon_id: PyUUID, source_file_path: str, asset_type: str, original_filename: Optional[str] = None, commit: bool = True) -> models.AddonAsset`

Creates an addon asset entry from a local file path.

## API Endpoints

The following API endpoints are available in `/backend/src/main.py`:

### POST `/api/v1/addons/{addon_id}/assets`

Uploads a new asset for a given addon.

### GET `/api/v1/addons/{addon_id}/assets/{asset_id}`

Downloads/serves an addon asset file.

### PUT `/api/v1/addons/{addon_id}/assets/{asset_id}`

Replaces an existing asset file and its metadata.

### DELETE `/api/v1/addons/{addon_id}/assets/{asset_id}`

Deletes an addon asset (file and database reco

*[truncated — see source for full prompt]*