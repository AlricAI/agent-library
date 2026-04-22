# AUTH DOCUMENTATION

> ## 🚨 CRITICAL: Authentication Requirements for ZAD Apps 🚨

**IMPORTANT**: WebtoysOS apps MUST implement these THREE critical requirements:
1. **Dual

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# WebtoysOS v3 Authentication System Documentation

## 🚨 CRITICAL: Authentication Requirements for ZAD Apps 🚨

**IMPORTANT**: WebtoysOS apps MUST implement these THREE critical requirements:
1. **Dual Auth**: BOTH localStorage AND postMessage authentication
2. **Uppercase Handles**: Always use UPPERCASE handles for participant IDs
3. **Correct Format**: participant_id must be `HANDLE_PIN` (e.g., `JOHN_1234`)

### Common Failures to Avoid
1. **Race Conditions**: Apps fail when postMessage hasn't arrived yet
2. **Case Mismatch**: lowercase handles cause data isolation (can't find saved data)
3. **Missing participantId**: ZAD API calls fail without proper format

## Complete Authentication Implementation

```javascript
// Global auth state
let currentUser = null;

// STEP 1: Initialize from localStorage (immediate access)
function loadAuthFromStorage() {
    const savedUser = localStorage.getItem('toybox_user');
    if (savedUser) {
        try {
            currentUser = JSON.parse(savedUser);
            
            // CRITICAL: Ensure handle is uppercase and participantId is set
            if (currentUser) {
                if (currentUser.handle) {
                    currentUser.handle = currentUser.handle.toUpperCase();
                }
                if (!currentUser.participantId && currentUser.handle && currentUser.pin) {
                    currentUser.participantId = `${currentUser.handle.toUpperCase()}_${currentUser.pin}`;
                    // Update localStorage with corrected format
                    localStorage.setItem('toybox_user', JSON.stringify(currentUser));
                }
            }
            
            console.log('Loaded auth from storage:', currentUser.handle, 'participantId:', currentUser.participantId);
            return true;
        } catch (e) {
            console.error('Failed to parse saved user:', e);
        }
    }
    return false;
}

// STEP 2: Listen for auth updates from desktop (real-time)
window.addEventLis

*[truncated — see source for full prompt]*