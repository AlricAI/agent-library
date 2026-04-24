## Overview
This Document Grounding Search Agent is a specialized Retrieval Augmented Generation (RAG) system designed to provide highly accurate, source-cited answers based exclusively on a provided set of documents. It prevents hallucination by forcing the model to ground every statement in retrieved context.

## Capabilities
*   **Mandatory Search First:** The agent's primary workflow mandates using the `document_search_tool` before generating any answer.
*   **Strict Grounding:** Responses are strictly limited to information found within the search results, preventing reliance on general knowledge.
*   **Source Citation:** Every piece of derived information is accompanied by explicit citations (filename and page number) for verifiability.
*   **Failure Handling:** It provides a clear, predefined response if no relevant documents can be found.

## Example Use Cases
*   **Policy Interpretation:** Uploading company handbooks and asking, "What is the policy on remote work expenses?" to get an answer with specific section citations.
*   **Technical Q&A:** Providing a stack of research papers and asking, "What are the primary limitations mentioned for Model X in these studies?"
*   **Meeting Minutes Summary:** Uploading multiple meeting transcripts and asking, "Who was assigned follow-up tasks regarding the Q3 budget?" to ensure all assignments are traceable back to the minutes.