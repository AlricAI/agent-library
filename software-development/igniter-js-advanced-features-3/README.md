# Igniter.js: Advanced Features

> description: | A guide to the advanced features of Igniter.js, including the background jobs system (BullMQ), the caching and pub/sub store (Redis), and the real-time system for live UI updates. alwaysApply: false

## Tags
`typescript` `redis`

## System Prompt
---
description: |
  A guide to the advanced features of Igniter.js, including the background jobs system (BullMQ), the caching and pub/sub store (Redis), and the real-time system for live UI updates.
alwaysApply: false
---

# Igniter.js: Advanced Features

This guide covers the advanced, production-grade features of Igniter.js that enable complex, scalable application development.

## 1. Background Jobs (BullMQ)

The jobs system allows you to offload long-running or resource-intensive tasks to a separate background worker process, preventing API requests from timing out and improving user experience.

### 1.1. Defining a Job
Jobs are defined in a dedicated job router file. Each job has a unique name, a Zod schema for its input, and a handler function.

-   **File Location:** `src/providers/jobs.ts` (or a similar central location)

```typescript
// src/providers/jobs.ts
import { jobs } from '@/igniter';
import { z } from 'zod';

export const emailJobs = jobs.router({
  sendWelcomeEmail: jobs.register({
    // Zod schema for type-safe job inputs
    input: z.object({
      userId: z.string(),
    }),
    // The handler that performs the background work
    handler: async ({ input, context }) => {
      const user = await context.database.user.findUnique({ where: { id: input.userId } });
      if (user) {
        await context.mail.send({
          to: user.email,
          template: 'welcome',
          data: { name: user.name },
        });
      }
    },
  }),
});

export const REGISTERED_JOBS = {
  emails: emailJobs,
};
```

### 1.2. Enqueuing a Job
Jobs are typically enqueued from within a mutation handler. The API call returns immediately to the user while the job is processed in the background.

```typescript
// In a controller
createUser: igniter.mutation({
  // ...
  handler: async ({ request, context, response }) => {
    const newUser = await context.database.user.create({ data: request.body });

    // Schedule the job to run in the background
    await ig

*[truncated — see source for full prompt]*