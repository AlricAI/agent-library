# MULTI ROLE PERMISSIONS

> ## Overview

The permission system supports **multi-role users** where a single user can hold multiple roles (e.g., writer + editor, or publisher + ad

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Role Permissions and Audit Documentation

## Overview

The permission system supports **multi-role users** where a single user can hold multiple roles (e.g., writer + editor, or publisher + admin). Permissions from all assigned roles are combined using a **union** model: a user has a permission if **ANY** of their roles grants it.

## Multi-Role Permission Resolution

### How It Works

**Database Level** (`has_permission()` function in migration `20260313213000_expand_permission_matrix.sql`):

```sql
-- Fetch user's roles (lines 336-341)
caller_roles := coalesce(caller_profile.user_roles, array[]::public.app_role[]);
if cardinality(caller_roles) = 0 then
  caller_roles := array[caller_profile.role];
elsif not (caller_roles @> array[caller_profile.role]::public.app_role[]) then
  caller_roles := array_prepend(caller_profile.role, caller_roles);
end if;

-- Check if admin is in roles (fast path)
if caller_roles @> array['admin'::public.app_role] then
  return true;
end if;

-- Union permission check: ANY role has permission → true
return exists (
  select 1
  from unnest(caller_roles) as role_value
  left join lateral (
    select enabled
    from public.role_permissions rp
    where rp.role = role_value
      and rp.permission_key = p_permission_key
  ) as role_override on true
  where coalesce(
    role_override.enabled,
    p_permission_key = any(public.default_role_permissions(role_value))
  )
);
```

**Frontend Level** (`resolvePermissionsForRoles()` in `src/lib/permissions.ts`):

```typescript
export function resolvePermissionsForRoles(
  roles: AppRole[],
  rolePermissionRows: RolePermissionRow[] = []
) {
  const resolved = new Set<AppPermissionKey>();

  if (roles.includes("admin")) {
    for (const permissionKey of ALL_PERMISSION_KEYS) {
      resolved.add(permissionKey);
    }
  } else {
    // Union: add permissions from ALL roles
    for (const role of roles) {
      const rolePermissionState = getRolePermissionState(role, rolePermissionRows);
    

*[truncated — see source for full prompt]*