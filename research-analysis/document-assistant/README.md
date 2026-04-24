## Overview
The Document Assistant is a specialized AI agent designed to answer complex questions by thoroughly searching and synthesizing information from a set of provided documents. It operates as a Retrieval-Augmented Generation (RAG) system, ensuring that every piece of generated content is directly traceable back to its source material.

Its key feature is real-time streaming; users can observe the agent's entire workflow—from searching the corpus to synthesizing the final answer—providing transparency and building trust in the results.

## Capabilities
*   **Document Search:** Utilizes a dedicated tool to index and search across multiple uploaded files.
*   **Contextual Retrieval:** Retrieves only the most relevant document excerpts pertaining to the user's query.
*   **Guided Synthesis:** Employs strict prompting guidelines to synthesize answers that are accurate, well-formatted markdown, and strictly confined to the provided context.
*   **Source Citation:** Automatically cites every piece of information using a precise format (e.g., `(Source: filename, Page X)`).
*   **Streaming Output:** Streams its internal thoughts, search steps, and final answer in real time for maximum user engagement.

## Example Use Cases
*   **Policy Interpretation:** Uploading an employee handbook and asking, "What is the policy on remote work reimbursement?" The agent will cite the exact section and page number.
*   **Research Synthesis:** Providing multiple academic papers and asking, "What are the three main contributing factors to climate change according to these sources?" The agent compiles a list with citations from each paper.
*   **Meeting Minutes Q&A:** Uploading transcripts of several meetings and asking, "Who was assigned the follow-up task regarding budget review?"