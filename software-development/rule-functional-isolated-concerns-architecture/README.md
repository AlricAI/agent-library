# Rule: Functional Isolated Concerns Architecture

> description: Functional patterns for scripts, CLIs, and standalone Node programs globs: - "scripts/**/*"

## Tags
`typescript` `react` `prisma`

## System Prompt
---
description: Functional patterns for scripts, CLIs, and standalone Node programs
globs:
  - "scripts/**/*"
  - "tooling/**/*"
  - "packages/**/cli/**/*"
  - "**/*.script.ts"
scopes:
  - node
  - backend
  - tooling
alwaysApply: false
---

# Rule: Functional Isolated Concerns Architecture

**Use this pattern for:** Scripts, CLIs, background workers, utility packages
**NOT for:** Express.js applications (see `monorepo-node-express-architecture.rules.mdc` instead)

---

## 🔗 When to Use This Rule

**✅ Use Functional Isolated Concerns when:**
- Building standalone scripts or CLIs
- Creating background workers or batch processors
- Developing utility packages in `/packages/`
- Working on non-HTTP Node.js programs

**❌ Use Express Architecture instead when:**
- Building HTTP APIs or web servers
- Need routes, controllers, and middleware
- Working in `/apps/server/` directory
- See: `monorepo-node-express-architecture.rules.mdc`

---

#### 1. **Core Principles**
* **ALWAYS** use functional programming patterns (NO CLASSES)
* **ALWAYS** organize code into isolated concern files
* **COMBINE** both transformations in a single refactoring pass
* **NEVER** create class wrappers or compatibility layers

#### 2. **Refactoring Triggers & Process**
**WHEN** encountering code that violates either principle:
1. **ANALYZE** the entire module/class structure first
2. **TRANSFORM** to functional patterns WHILE splitting into concern files
3. **NEVER** do two-pass refactoring (class→functional→isolated)
4. **DELETE** all class-based code without creating wrappers

#### 3. **Critical Anti-patterns FORBIDDEN**
```typescript
// ❌ NEVER create backward compatible class wrappers:
class UserService {
  constructor() {
    this.create = createUser;  // NO!
    this.find = findUser;      // NO!
  }
}

// ❌ NEVER create "function bag" objects mimicking classes:
export const userService = {
  create: createUser,  // This is just a class in disguise
  find: findUser
};

// ✅ INSTEAD: Direct fu

*[truncated — see source for full prompt]*