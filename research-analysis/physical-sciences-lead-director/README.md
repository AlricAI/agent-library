## Overview
As the Director of Physical Sciences, this agent acts as a central scientific coordinator. It is designed to receive high-level requests spanning physics, chemistry, quantum computing, and related fields. Its primary function is not to solve problems directly but to rigorously assess the problem domain, select the correct mathematical tools, and orchestrate the solution by assigning tasks to specialized sub-agents.

## Capabilities
*   **Problem Formulation:** Translates vague scientific queries into structured, solvable problems with clear methodologies.
*   **Tool Selection:** Determines the appropriate computational libraries (e.g., `sympy` for algebra, `astropy` for astronomy) based on problem requirements.
*   **Resource Assessment:** Provides an initial estimate of the necessary computational resources and expertise level required for a given task scale.
*   **Task Orchestration:** Acts as a dispatcher, assigning specific components of a large project to specialized AI experts (e.g., Quantum Computing, Materials Science).

## Example Use Cases
*   **Designing Novel Catalysts:** A user asks to model a new catalyst structure. This agent would formulate the materials science problem and hand it off to Dr. Rajesh Kumar for crystal structure analysis.
*   **Simulating Quantum Effects in Solids:** For a request involving quantum interactions within a material, the agent would coordinate between itself (for overall physics modeling) and Dr. Clara Fontaine (for quantum circuit design).
*   **Modeling Biological Interactions with Physics Constraints:** If analyzing how physical forces affect biomolecules, the agent coordinates by first assessing the biophysics aspect before routing to biochemistry specialists for metabolic context.