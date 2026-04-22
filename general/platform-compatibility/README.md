# PLATFORM COMPATIBILITY

> ## Summary

Tandem is designed to work across **Windows, Linux, and macOS** with appropriate platform-specific handling where needed.

## ✅ macOS Comp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Platform Compatibility Analysis

## Summary

Tandem is designed to work across **Windows, Linux, and macOS** with appropriate platform-specific handling where needed.

## ✅ macOS Compatibility Status

### Already Handled Correctly

1. **Clipboard Paste (Images)**:
   - Enhanced handler checks both `clipboardData.items` (standard) and `clipboardData.files` (Linux fallback)
   - macOS WebKit supports `clipboardData.items` natively (like Windows)
   - No macOS-specific changes needed ✅

2. **File Paths**:
   - All path handling uses regex that normalizes both `/` and `\` to `/`
   - Works correctly on macOS (Unix-style paths) ✅
   - Examples:
     ```typescript
     .replace(/\\/g, "/")  // Normalizes Windows \ to /
     .split(/[/\\]/)        // Splits on both / and \
     ```

3. **Process Management**:
   - Windows-specific code (`taskkill`, console hiding) is properly wrapped with `#[cfg(target_os = "windows")]`
   - macOS will use Unix process signals (same as Linux) ✅

4. **Git Commands**:
   - No platform-specific issues
   - `git` command works identically on macOS/Linux/Windows ✅

5. **Environment Variables**:
   - Linux GTK/WebKit fixes are properly wrapped with `#[cfg(target_os = "linux")]`
   - Won't affect macOS ✅
   ```rust
   #[cfg(target_os = "linux")]
   {
       std::env::set_var("GTK_IM_MODULE", "gtk-im-context-simple");
       std::env::set_var("WEBKIT_DISABLE_DMABUF_RENDERER", "1");
   }
   ```

### Known Platform-Specific Code

#### Backend (Rust)

| Location                               | Platform     | Purpose                   | macOS Impact                   |
| -------------------------------------- | ------------ | ------------------------- | ------------------------------ |
| `src-tauri/src/main.rs`                | Linux only   | GTK/WebKit env vars       | None - properly isolated       |
| `src-tauri/src/commands.rs:292`        | Windows only | Hide `git` console window | None - macOS uses Unix path    |
| `src-tauri/src/sidecar_manag

*[truncated — see source for full prompt]*