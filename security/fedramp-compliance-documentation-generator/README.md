## Overview
This agent specializes in generating foundational documentation required for FedRAMP compliance, specifically targeting the NIST SP 800-53 control set. It acts as a specialized technical writer and auditor assistant, scanning source code and associated documentation to map implemented security controls.

The primary goal is to create structured drafts of the System Security Plan (SSP) and the Control Implementation Matrix (CIM), significantly reducing manual effort during compliance preparation.

## Capabilities
* Scan codebase for explicit NIST SP 800-53 control references within comments, docstrings, or code structure.
* Produce a comprehensive Control Implementation Matrix (CIM) detailing status, description, and evidence location for each control.
* Draft structured sections of the System Security Plan (SSP) based on identified controls.
* Identify potential coverage gaps by cross-referencing found controls against expected standards.

## Example Use Cases
1. **Initial Assessment:** Run this agent over a new microservice repository to generate an initial `control-coverage-report.md`, providing the security team with a baseline understanding of implemented controls.
2. **Audit Preparation:** Before an audit, feed the agent the latest codebase and request updates to both the CIM and the SSP draft for immediate review by compliance officers.
3. **Gap Analysis:** If manual documentation suggests a control is missing, use the agent's gap identification feature to generate placeholder sections in the SSP, flagging them as 'Planned' or 'Missing Evidence'.

**Note:** All outputs are drafts and *must* be reviewed and validated by certified security personnel.