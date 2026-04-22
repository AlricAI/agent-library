# ENHANCEMENT FEATURES

> **ModPorter AI - Advanced Features**

---

## Visual Conversion Editor

### Overview

Side-by-side code editor for reviewing and editing converted cod

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enhancement Features Documentation

**ModPorter AI - Advanced Features**

---

## Visual Conversion Editor

### Overview

Side-by-side code editor for reviewing and editing converted code with live preview.

### Features

**Split-Pane View:**
- Java code (left) - Read-only
- Bedrock code (right) - Editable
- Syntax highlighting for both
- Line number synchronization

**Live Preview:**
- Real-time JSON validation
- Structure tree view
- Error highlighting
- Auto-complete suggestions

**AI Assistance:**
- Fix errors button
- Improve code suggestions
- Alternative implementations
- Confidence scores

**Templates:**
- Pre-built patterns for common conversions
- Customizable fields
- Instant application
- Category browsing

### Usage

**Access:**
1. Complete a conversion
2. Click "Edit in Visual Editor"
3. Review side-by-side comparison
4. Make edits as needed
5. Download updated .mcaddon

**Keyboard Shortcuts:**
- `Ctrl+S` - Save changes
- `Ctrl+Z` - Undo
- `Ctrl+Y` - Redo
- `Ctrl+F` - Find
- `Ctrl+H` - Find and replace
- `F5` - Refresh preview

---

## Batch Conversion

### Overview

Convert multiple mods simultaneously with centralized tracking.

### Limits

| Tier | Max Files | Concurrent | Priority |
|------|-----------|------------|----------|
| **Free** | 5 | 2 | Normal |
| **Pro** | 20 | 10 | High |
| **Studio** | 50 | 20 | Critical |

### Usage

**Start Batch:**
1. Click "Batch Conversion"
2. Upload 2-20 files (drag & drop)
3. Configure options (optional)
4. Click "Start Batch"
5. Monitor progress dashboard

**Progress Tracking:**
- Real-time status for each file
- Overall batch progress bar
- Estimated completion time
- Individual error reporting

**Results:**
- Download individual files
- Download all as ZIP
- View conversion reports
- Re-run failed conversions

### API Example

```python
# Start batch conversion
response = requests.post(
    "https://api.modporter.ai/api/v1/batch/convert",
    headers={"Authorization": f"Bearer {token}"},
    json={
       

*[truncated — see source for full prompt]*