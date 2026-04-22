# Build Optimization Log

> ## Optimization 1: Content-Based OG Image Caching

### Hypothesis
OG images are deterministic: given the same inputs (title, description, tags, date, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Build Optimization Implementation Log

## Optimization 1: Content-Based OG Image Caching

### Hypothesis
OG images are deterministic: given the same inputs (title, description, tags, date, color scheme, dimensions), the output image is always the same. By hashing these inputs and storing generated images in a persistent cache, we can skip regeneration for unchanged content.

### Implementation
**File**: `quartz/plugins/emitters/ogImage.tsx`

1. **Hash computation**: `computeOgHash()` creates a SHA-256 hash from title, description, tags, date, colorScheme, width, height, and a version number (for cache busting on format changes).
2. **Cache directory**: `quartz/.quartz-cache/og-images/` (already gitignored via `.quartz-cache`)
3. **Cache flow**:
   - Before generating, check if `{hash}.webp` exists in cache dir
   - If yes: read cached file and copy to output (fast file copy)
   - If no: generate image via satori+sharp, write to cache AND output
4. **Icon caching**: `getIconBase64()` reads the icon file once and caches in memory, eliminating 2,348 redundant filesystem reads per build.

### Results
| Scenario | OG Image Time | Total Build |
|----------|-------------|-------------|
| Baseline (sequential, no cache) | 315.2s | 5m50s |
| Warm cache | **5.5s** | **45s** |
| **Speedup** | **57x** | **7.7x** |

---

## Optimization 2: Parallel OG Image Generation

### Hypothesis
The original code used an async generator that `yield`ed one image at a time. The consuming `for await` loop awaited each yielded value before requesting the next, making generation purely sequential. Since satori and sharp are both CPU-bound but can overlap their work, processing images in batches with `Promise.all` should yield significant speedup.

### Implementation
**File**: `quartz/plugins/emitters/ogImage.tsx`

1. **Batch processing**: Images are processed in batches of `OG_CONCURRENCY` (20) using `Promise.all`
2. **Yielding results**: After each batch completes, results are yielded to the 

*[truncated — see source for full prompt]*