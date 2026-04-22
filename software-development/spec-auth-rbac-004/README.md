# Spec Auth Rbac 004

> **Priority**: HIGH | **Timeline**: Week 4-5 | **Team**: 1 Developer (Backend Focus)

---

## Objective

Implement complete authentication and role-bas

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spec: Authentication & Role-Based Access Control (spec-auth-rbac-004)

**Priority**: HIGH | **Timeline**: Week 4-5 | **Team**: 1 Developer (Backend Focus)

---

## Objective

Implement complete authentication and role-based access control (RBAC) using WorkOS for SSO (Gmail and Microsoft), Laravel middleware for route protection, and role-based redirects. Users must be able to sign up/login via WorkOS, be assigned roles (Client, Owner, Admin), and be redirected to appropriate dashboards based on their role.

---

## Requirements

### Functional Requirements

1. **WorkOS Authentication Flow**
   - Login button on HomePage redirects to WorkOS
   - WorkOS handles Gmail and Microsoft SSO
   - Callback endpoint creates/updates user in database
   - Session cookie is set after successful authentication
   - User is redirected to appropriate dashboard based on role

2. **User Roles**
   - **Client**: Can search properties, make bookings, leave reviews
   - **Owner**: Can create/manage properties, view bookings
   - **Admin**: Can moderate properties, manage users, view analytics

3. **Protected Routes**
   - Public routes: HomePage, MapSearch, PropertyDetail, Login
   - Client routes: Client dashboard, bookings, profile
   - Owner routes: Owner dashboard, property management
   - Admin routes: Admin dashboard, user management, moderation

4. **Role-Based Redirects**
   - After login, redirect to appropriate dashboard based on role
   - Prevent unauthorized access to role-specific pages
   - Logout clears session and redirects to HomePage

5. **User Profile Management**
   - View/edit profile information
   - Change password (if applicable)
   - Delete account

### Technical Requirements

- **Framework**: Laravel 12 with Inertia.js
- **Authentication**: WorkOS SSO integration
- **Authorization**: Laravel middleware for role checking
- **Database**: User model with role field (enum: client, owner, admin)
- **Session**: Laravel session management with secure cookies
- **Type

*[truncated — see source for full prompt]*