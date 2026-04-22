# Roadmap

> Based on the comprehensive project documentation, here is the detailed execution roadmap for the **Arithmetic Discriminant Barrier (ADB) Framework**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Based on the comprehensive project documentation, here is the detailed execution roadmap for the **Arithmetic Discriminant Barrier (ADB) Framework**. This plan transforms the theoretical conjecture into an actionable research program, structured into four distinct phases.

### **Phase 0: Immediate Launch (First 7 Days)**

**Goal:** Establish infrastructure, public accountability, and baseline validation.

* **Day 1: Foundation**
    * **Repository:** Complete public GitHub setup with `README.md` (overview), `INSTALL.md` (dependencies), and `CITATION.cff`.[^1]
    * **Resources:** Submit applications for AWS Research Credits and Google Cloud Research credits (target: \$5,000 for compute).[^1]
    * **Planning:** Define the exact scope for the "Level 2" computation (near-collision search).
* **Day 2: Baseline Implementation**
    * **Priority 1:** Implement $n$ computation using Odlyzko's zero database (3 hours).
    * **Priority 2:** Build the anomaly detection framework to flag if discriminants approach zero too quickly.[^1]
    * **Protocol:** Commit code to GitHub; if a checkpoint is missed ("Red Day"), post an issue explaining the delay.[^1]
* **Day 3: Validation Tests**
    * **Tests:** Code the "Turn inequality" validation and "Hermite convergence" tests.
    * **Milestone:** Produce the first validated result: $R_n > 1$ for $n < 100$.[^1]
    * **Outreach:** Contact potential collaborators (e.g., Dave Platt) regarding zero databases.[^1]
* **Day 4: Stress Testing**
    * **Precision:** Run precision stress tests (target: maintain 50+ digits of accuracy).
    * **Data:** Create the benchmark dataset for the validation suite.[^1]
* **Day 5: Full Validation \& Pre-Publication**
    * **Execution:** Run the full validation suite (approx. 4 hours runtime).
    * **Drafting:** Finalize the "Methodology" section for the initial preprint.[^1]
    * **Submission:** Prepare and submit the methodology preprint to arXiv ("Assessing Speculative Mathematical Frameworks").
*

*[truncated — see source for full prompt]*