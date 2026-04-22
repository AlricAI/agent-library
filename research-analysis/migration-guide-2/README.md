# Migration Guide

> Vectro 2.0 introduces a new versioned storage format (`vectro_npz` v2) that adds
precision-mode tracking, group-size metadata, and provenance records 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Migration Guide: v1 → v2

Vectro 2.0 introduces a new versioned storage format (`vectro_npz` v2) that adds
precision-mode tracking, group-size metadata, and provenance records to every
artifact. All new artifacts written by `save_compressed` are v2.

**v1 artifacts are still readable** via `load_compressed` — they are handled
transparently. However, you should upgrade them to v2 to benefit from
migration tracking and to keep your tooling consistent.

---

## What Changed in v2

| Field | v1 | v2 |
|-------|----|----|
| `storage_format_version` | absent (treated as `1`) | `2` |
| `storage_format` | absent | `"vectro_npz"` |
| `artifact_type` | absent | `"single"` or `"batch"` |
| `precision_mode` | absent | `"int8"` / `"int4"` etc. |
| `group_size` | absent | integer (`0` = no grouping) |
| `metadata_json` | absent | JSON provenance blob |

The `quantized` and `scales` arrays are **byte-for-byte identical** in v2 —
no data is recomputed during upgrade.

---

## Detecting the Format Version

```python
from python.migration import inspect_artifact

info = inspect_artifact("embeddings.npz")
print(info["format_version"])   # 1 or 2
print(info["needs_upgrade"])    # True if version < 2
print(info["precision_mode"])   # "int8" (default for v1 files)
```

---

## Upgrading an Artifact

```python
from python.migration import upgrade_artifact

upgrade_artifact("old.npz", "old_v2.npz")
```

Or use the CLI:

```bash
python -m python.migration upgrade old.npz old_v2.npz
```

The upgrade tool writes a `migration` record inside `metadata_json`:

```json
{
  "migration": {
    "migrated_from_version": 1,
    "migrated_to_version": 2,
    "migrated_at_utc": "2025-01-15T12:00:00+00:00",
    "src_fields": ["quantized", "scales", "dims", "n"]
  }
}
```

### Dry-run mode

Preview what would happen without writing any files:

```bash
python -m python.migration upgrade old.npz new.npz --dry-run
```

---

## Validating an Artifact

```bash
python -m python.migration validate embeddings.n

*[truncated — see source for full prompt]*