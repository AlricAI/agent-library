# Mobile

> ## Overview

The web app (`dist/`) is wrapped as a native app by Capacitor 8. Capacitor serves the built files from a local WebView — there is no serv

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Mobile / Capacitor Spec

## Overview

The web app (`dist/`) is wrapped as a native app by Capacitor 8. Capacitor serves the built files from a local WebView — there is no server and no internet connection for assets.

Bundle ID: `com.sprintread.app`
Platforms: Android (primary), iOS

## Critical Vite Config

`vite.config.ts` must have `base: './'`. Without it, Vite emits absolute asset paths (`/assets/index.js`) that fail in the WebView because there is no root `/`.

```ts
export default defineConfig({
  base: './',
  build: { assetsInlineLimit: 0 },  // don't inline assets — keep them as files
  plugins: [react()],
})
```

## PDF.js Worker

The PDF.js worker **must not load from a CDN**. The WebView has no network access. The worker file is bundled locally:

- Source: `node_modules/pdfjs-dist/build/pdf.worker.min.mjs`
- Committed copy: `public/pdf.worker.min.mjs`
- Vite copies `public/` verbatim to `dist/`; Capacitor copies `dist/` to native assets

If you upgrade `pdfjs-dist`, copy the new worker file to `public/pdf.worker.min.mjs`.

Worker URL is set in `src/utils/pdfParser.ts`:
```ts
pdfjsLib.GlobalWorkerOptions.workerSrc = new URL('../../public/pdf.worker.min.mjs', import.meta.url).href
```

## Build → Deploy Flow

Every code change requires a full rebuild before testing on device:

```bash
npm run build           # 1. TypeScript + Vite → dist/
npx cap sync android    # 2. Copy dist/ to android/app/src/main/assets/public/
# Open Android Studio → Run
```

The built assets in `android/app/src/main/assets/public/` are **committed to git**. This lets the Android project build without requiring an npm build step (useful for CI and reviewers who don't have Node installed).

When pushing, always include the updated assets directory so the Android project stays in sync.

## Viewport / Safe Areas

`index.html` meta viewport:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
```

`vie

*[truncated — see source for full prompt]*