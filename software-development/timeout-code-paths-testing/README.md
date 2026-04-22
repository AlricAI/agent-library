# Timeout Code Paths Testing

> **Purpose:** Ensure all code paths that check for timeout work correctly after our fix

---

## 📋 **All Timeout Check Locations:**

### **1. ShellExe

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Timeout Detection - Testing All Code Paths

**Purpose:** Ensure all code paths that check for timeout work correctly after our fix

---

## 📋 **All Timeout Check Locations:**

### **1. ShellExecutionResults.ToAiString()** 
**File:** `src/common/ProcessExecution/ShellExecutionResults.cs:171`

**Check:** `if (TimedOut)`

**Special Message:**
```
<timed out; still running; use GetShellOrProcessOutput>
```

**How to Test:**
```csharp
RunShellCommand("sleep 10", expectedTimeout: 2000)
// Should return JSON with status="stillRunning" and the above message
```

---

### **2. ShellExecutionResults.FromProcessResult()**
**File:** `src/common/ProcessExecution/ShellExecutionResults.cs:202-206`

**Check:** `result.IsTimeout`

**Special Messages:**
```csharp
Success = result.ExitCode == 0 && !result.IsTimeout  // False when timeout
FriendlyErrorMessage = result.IsTimeout ? "Command timed out" : ...
```

**How to Test:**
```csharp
// Execute any shell command with timeout
// Check that Success=false and FriendlyErrorMessage="Command timed out"
```

---

### **3. GitHubSearchHelperFunctions.SearchGitHub()**
**File:** `src/cycod/FunctionCallingTools/GitHubSearchHelperFunctions.cs:77`

**Check:** `if (result.CompletionState == ProcessCompletionState.TimedOut)`

**Special Message:**
```
<cycodgr command timed out after 120 seconds>
```

**How to Test:**
```csharp
SearchGitHub("--contains 'some really slow search that takes forever'")
// Hard to test without actual slow search - might need mock
```

---

### **4. ShellCommandToolHelperFunctions (Legacy)**
**File:** `src/cycod/FunctionCallingTools/ShellCommandToolHelperFunctions.cs:32, 64, 96`

**Check:** `if (result.IsTimeout)`

**Special Message:**
```
<timed out and killed process - environment state has been reset>
```

**NOTE:** These are for singleton shells (BashShellSession.Instance, etc.) which DO get killed on timeout

**How to Test:**
```csharp
// These functions aren't AI tools anymore (no [KernelFunction])
// But they'r

*[truncated — see source for full prompt]*