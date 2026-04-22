# AI COLLABORATION GUIDE

> Here is a detailed guide on what I would need to achieve a 100% success rate on your tasks:

  1. The Ideal Task Definition

  The way you define a ta

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Here is a detailed guide on what I would need to achieve a 100% success rate on your tasks:

  1. The Ideal Task Definition

  The way you define a task is the most critical factor. I don't have intuition or implicit
  understanding, so my performance is directly proportional to the clarity of your instructions.

   * Atomicity: Break down large goals into the smallest possible subtasks. Each task should represent
     a single, logical unit of work.
       * Instead of: "Implement user authentication."
       * Do this:
           1. "Create a new database migration to add a users table with id, email, and password_hash
              columns."
           2. "Create a /register endpoint that takes an email and password, hashes the password, and
              saves a new user to the database."
           3. "Write a unit test for the /register endpoint that verifies a user is created
              successfully."

   * Explicitness and Unambiguity: Leave no room for interpretation.
       * Instead of: "Fix the bug on the dashboard."
       * Do this: "When a user with no projects clicks the 'Dashboard' link, the application crashes.
          It should instead display the 'empty_dashboard' component located at
         `src/components/empty_dashboard.js`."

   * Clear Acceptance Criteria: Define what "done" means in a verifiable way.
       * Instead of: "The API should be fast."
       * Do this: "The GET /api/v1/items endpoint must return a response in under 100ms with a 99%
         success rate under a load of 50 concurrent users."

   * Reference Existing Patterns: If the new code should follow an existing pattern, point me to it
     directly.
       * Do this: "Create a new ProductService that follows the same singleton pattern and method
         structure as the UserService in src/services/user.service.py."

  2. The Ideal Project Environment

  My ability to execute code depends entirely on the environment you provide.

   * Automated Setup: The project sho

*[truncated — see source for full prompt]*