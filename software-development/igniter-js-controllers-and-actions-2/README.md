# Igniter.js: Controllers and Actions

> description: | A focused guide on creating Igniter.js controllers and actions (queries and mutations). This rule details the properties, validation layers (Zod and Ensure), and the response object for building API endpoints. alwaysApply: false

## Tags
`typescript`

## System Prompt
---
description: |
  A focused guide on creating Igniter.js controllers and actions (queries and mutations). This rule details the properties, validation layers (Zod and Ensure), and the response object for building API endpoints.
alwaysApply: false
---

# Igniter.js: Controllers and Actions

This guide provides a detailed reference for creating controllers and actions, which are the fundamental building blocks of an Igniter.js API.

## 1. Controllers (`igniter.controller`)

A controller is a logical grouping of related API actions under a common base path.

### 1.1. Definition
```typescript
export const postsController = igniter.controller({
  name: 'Posts', // A descriptive name for documentation and debugging
  path: '/posts', // The base URL path for all actions in this controller
  actions: {
    // ... actions are defined here
  },
});
```

### 1.2. Controller Properties
| Property    | Type   | Required | Description                                                                 |
| :---------- | :----- | :------- | :-------------------------------------------------------------------------- |
| `name`      | string | Yes      | A descriptive name for the controller, used in documentation.               |
| `path`      | string | Yes      | The base URL segment for all actions within this controller (e.g., `/posts`). |
| `actions`   | object | Yes      | An object containing all the API endpoints (actions) for this controller.   |

## 2. Actions (`igniter.query` & `igniter.mutation`)

Actions are the individual API endpoints within a controller.

### 2.1. Query Actions (`igniter.query`)
Used for fetching data, corresponding to `GET` requests.

```typescript
list: igniter.query({
  path: '/', // Final path: /posts/
  query: z.object({ // Zod schema for URL query parameter validation
    limit: z.string().optional(),
  }),
  handler: ({ request, response, context }) => {
    // ... business logic
  },
})
```

### 2.2. Mutation Actions (`igniter.mutation`)
Used 

*[truncated — see source for full prompt]*