# Reminders

> Agentron supports **one-shot reminders** that you can create from the chat.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Reminders

Agentron supports **one-shot reminders** that you can create from the chat. When the reminder time is reached, the reminder text is posted into the same chat (so you see it when you open that conversation).

## Creating reminders in chat

In the chat, you can say things like:

- **“Remind me in 20 minutes to call John.”**
- **“Remind me at 3pm to submit the report.”**
- **“Set a reminder for tomorrow at 9am: review the draft.”**

The assistant uses the **create_reminder** tool with:

- **message** — The text you want to see when the reminder fires (e.g. “Call John”).
- **at** — An ISO 8601 date/time (e.g. `2026-02-16T15:00:00Z`) when you specify an exact time.
- **inMinutes** — Minutes from now (e.g. 20 for “in 20 minutes”, 60 for “in 1 hour”).

Reminders created from the chat are tied to **that conversation**. When the reminder fires, a message like **“Reminder: Call John”** is added to the same chat so you see it when you open it.

### Scheduling a task for the assistant

You can also **schedule a task for the assistant** so it runs at a specific time in that chat (e.g. at 9am have the assistant summarize my calendar). The assistant uses **create_reminder** with **taskType: assistant_task** and **message** set to the task. When the time comes, that text is added as a **user** message and the assistant runs one full turn; the reply appears in the same conversation. **assistant_task** requires a conversation so the reply has a place to go.

## Listing and cancelling

- **“What reminders do I have?”** / **“Show my reminders”** — The assistant calls **list_reminders** and shows pending (or optionally fired/cancelled) reminders.
- **“Cancel that reminder”** / **“Remove the reminder”** — The assistant uses **cancel_reminder** with the reminder id from **list_reminders**.

## API (for integrations)

| Method | Endpoint | Description |
|--------|----------|-------------|
| **POST** | `/api/reminders` | Create a reminder. Body: `{ "message": "…", "at": "2026-0

*[truncated — see source for full prompt]*