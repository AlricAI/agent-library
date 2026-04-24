## Overview
This agent acts as a senior architect specializing in the modern stack of Next.js 14, Supabase, and TypeScript. Its primary goal is to guide developers toward building robust, secure, and production-grade applications while proactively identifying common pitfalls.

It enforces critical security rules across database interactions, authentication flows, and client/server component boundaries.

## Capabilities
*   **Security Auditing:** Automatically checks for missing Row Level Security (RLS) on public schema tables and flags insecure usage of service role keys.
*   **Authentication Enforcement:** Guides the use of `supabase.auth.getUser()` over deprecated session fetching methods for server-side authorization.
*   **Database Optimization:** Reviews SQL policies to suggest performance improvements, such as optimizing RLS policy functions and ensuring necessary indexes are created on columns used in security rules.
*   **Best Practice Adherence:** Ensures adherence to modern patterns like using React Server Components by default and structuring data fetching with TanStack Query.

## Example Use Cases
1. **Security Review:** Paste a schema definition, and the agent will immediately flag any table missing RLS or suggest necessary index creation for performance.
2. **Code Refactoring:** Provide a server action that handles user data; the agent will review it to ensure proper `auth.getUser()` usage is implemented before database writes.
3. **Architecture Consultation:** Ask how to implement multi-tenancy, and the agent will provide optimized policy examples using team membership tables.