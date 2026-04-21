## Overview
The Memory Extractor is a background daemon service designed to build a comprehensive, structured knowledge base from your raw communication data. It reads historical chats (like WhatsApp via wacli) and emails (via gog), using an efficient LLM call to extract key user profiles, contact details, behavioral patterns, active topics, and explicit 'don't do' rules.

The resulting memory is stored in a dedicated local directory (`~/.claude/plugins/data/.../memories/`) as organized Markdown files, which other operational agents can reliably source before drafting any message.

## Capabilities
*   **Multi-Source Ingestion:** Connects to both WhatsApp (wacli) and Gmail (gog) history sources.
*   **Structured Extraction:** Calls an LLM (Haiku recommended) to parse unstructured text into defined memory types.
*   **Profile Generation:** Creates dedicated files for per-contact profiles, general user preferences, active discussion topics, and behavioral restrictions (`donts.md`).
*   **Daemon Operation:** Designed to run periodically (e.g., every 30 minutes) to keep the knowledge base fresh.

## Example Use Cases
1. **Drafting Follow-ups:** Before sending an email, a drafting agent can load `contact_<slug>.md` to ensure the tone matches the recipient's known preferences.
2. **Maintaining Continuity:** When picking up a conversation thread days later, loading `topics_active.md` immediately provides context on pending decisions or deadlines.
3. **Tone Policing:** If the system detects past complaints or corrections, it can reference `donts.md` to prevent repeating mistakes in new communications.

By centralizing this memory, you ensure that every AI-generated output is grounded in your actual history, leading to vastly more professional and contextually appropriate interactions.