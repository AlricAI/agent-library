# How To Trace Call Paths

> **Quick reference for finding all callers of a method**

---

## 🎯 **Basic Strategy:**

1. Start with the method you changed
2. Find all callers of t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Trace Call Paths in Codebase

**Quick reference for finding all callers of a method**

---

## 🎯 **Basic Strategy:**

1. Start with the method you changed
2. Find all callers of that method
3. For each caller, find their callers
4. Continue up the chain until you reach public APIs or entry points
5. Document the tree
6. Test each major path

---

## 🔍 **Using SearchInFiles to Find Callers:**

### **Pattern 1: Find calls to a specific method**
```
SearchInFiles:
  filePatterns: ["**/*.cs"]
  excludePatterns: ["**/bin/**", "**/obj/**"]
  lineContains: "MethodName\("
  linesBeforeAndAfter: 2
```

**Example:** Finding calls to `WaitForMarkerAsync`:
```
lineContains: "WaitForMarkerAsync\("
```

**Result:** Shows all lines that call this method with context

---

### **Pattern 2: Find where a class is instantiated**
```
lineContains: "new ClassName"
```

**Example:** Finding where `PersistentShellCommandBuilder` is created:
```
lineContains: "new PersistentShellCommandBuilder"
```

---

### **Pattern 3: Find method implementations**
```
lineContains: "public.*async.*Task.*MethodName"
```

**Example:** Finding where `ExecuteCommandAsync` is implemented:
```
lineContains: "public.*async.*Task.*ExecuteCommandAsync"
```

---

## 📋 **Step-by-Step Process:**

### **Step 1: Identify what you changed**
```
Example:
- Modified: PersistentShellProcess.WaitForMarkerAsync()
- Removed: TimeoutException catch block
```

### **Step 2: Find direct callers**
```bash
SearchInFiles for "WaitForMarkerAsync("
```

**Record results:**
- `RunCommandInternalAsync()` calls it (line 236)
- `VerifyShellAsync()` calls it (line 83)

### **Step 3: Find callers of those callers**
```bash
SearchInFiles for "RunCommandInternalAsync("
```

**Record results:**
- `RunCommandAsync()` calls it (line 143)
- `RunCommandWithInputAsync()` calls it (line 384)

### **Step 4: Continue up the tree**
Repeat for each level until you reach:
- Public API methods
- AI function tools ([KernelFunction])
- Entry 

*[truncated — see source for full prompt]*