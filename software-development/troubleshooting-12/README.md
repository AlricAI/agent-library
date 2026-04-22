# TROUBLESHOOTING

> This comprehensive guide addresses common issues, troubleshooting steps, and solutions for qtests users.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting Guide

This comprehensive guide addresses common issues, troubleshooting steps, and solutions for qtests users.

## 🔧 Installation & Setup Issues

### Module Resolution Problems

**Issue**: Cannot resolve qtests imports
```typescript
// Error: Cannot find module 'qtests/lib/envUtils.js'
import { httpTest } from 'qtests/lib/envUtils.js';
```

**Solutions**:
1. **Check Build Status**: Ensure you're using the built version
```bash
npm run build  # If using qtests from source
```

2. **Use Dist Path**: Import from compiled distribution
```typescript
// Correct import from dist
import { httpTest } from 'qtests/dist/lib/envUtils.js';

// Or use main exports
import { httpTest } from 'qtests';
```

3. **Verify package.json Exports**
```json
{
  "exports": {
    ".": "./dist/index.js",
    "./lib/envUtils": "./dist/lib/envUtils.js"
  }
}
```

### TypeScript Configuration Issues

**Issue**: TypeScript errors with qtests imports
```
TS2307: Cannot find module 'qtests' or its corresponding type declarations.
```

**Solutions**:
1. **Update tsconfig.json**
```json
{
  "compilerOptions": {
    "moduleResolution": "node",
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "types": ["node", "jest"]
  },
  "include": ["node_modules/qtests/dist/**/*.d.ts"]
}
```

2. **Install Type Definitions**
```bash
npm install --save-dev @types/node @types/jest
```

3. **Use Type Assertion** (temporary fix)
```typescript
import qtests from 'qtests';
const { stubMethod } = qtests as any;
```

## 🧪 Test Execution Issues

### Stub Not Working

**Issue**: Methods not being stubbed correctly
```typescript
import './node_modules/qtests/setup.js';
import { myService } from './myService';

const restore = stubMethod(myService, 'getData', () => 'stubbed');
console.log(myService.getData()); // Still calls original method
```

**Solutions**:
1. **Import Order Check**
```typescript
// ✅ Correct - setup first
import './node_modules/qtests/setup.js';
import { myServi

*[truncated — see source for full prompt]*