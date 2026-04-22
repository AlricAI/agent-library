# ISSUES

> This document records all issues identified during the pre-launch code review of the LMS Backend NestJS monorepo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Review Findings

This document records all issues identified during the pre-launch code review of the LMS Backend NestJS monorepo.

## Table of Contents

- [Medium Severity Issues](#medium-severity-issues)
- [Low Severity Issues](#low-severity-issues)

---

## Medium Severity Issues

### 1. FileService.createFile Signature Mismatch

**Location**: `apps/file-service/src/file.service.ts:34-37`

**Issue**: Method expects `file: Express.Multer.File` as a required parameter, but the typed-client doesn't pass this parameter.

**Impact**: File upload via typed-client will fail.

---

### 2. TenantId Missing in CreateUserDto

**Location**: `libs/contracts/src/user/dto/create-user.dto.ts`

**Issue**: `CreateUserDto` lacks a `tenantId` field, but `UserContract` requires it. The service creates users without setting `tenantId`.

**Impact**: Data integrity issues; users created without tenant association.

---

### 3. Optional Fields in CourseVideo Marked Required

**Location**: `apps/course-service/src/entities/course-video.entity.ts:26-30`

**Issue**: `unlockCondition` and `validityPeriod` are optional in the contract but marked as required in the entity.

**Contract** (optional):

```typescript
unlockCondition?: string;
validityPeriod?: Date;
```

**Entity** (required):

```typescript
@Column({ name: 'unlock_condition', type: 'text', nullable: true })
unlockCondition!: string;  // Should be unlockCondition?
```

---

### 4. Duplicate Version Column in CourseMaterial

**Location**: `apps/course-service/src/entities/course-material.entity.ts:44`

**Issue**: `version` is defined twice - once as `@Column({ default: 1 })` and again via `@VersionColumn()`.

```typescript
@Column({ default: 1 })
version!: number;  // Duplicate

@VersionColumn()
version!: number;  // Original
```

**Impact**: Potential database conflicts or unexpected behavior.

---

### 5. TypedClientBase Has Unused Constructor Parameter

**Location**: `libs/typed-client/src/typed-client.base.ts:16-21`

**Is

*[truncated — see source for full prompt]*