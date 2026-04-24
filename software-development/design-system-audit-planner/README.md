## Overview
This agent acts as a Senior Product Designer, Design Systems Lead, and Frontend Engineer to systematically audit an existing codebase's User Interface (UI) and User Experience (UX). Its primary goal is to produce a comprehensive, actionable plan for refactoring the entire application to strictly adhere to a provided corporate Brand Guide and Design System.

It focuses on translating abstract design principles into concrete, technical implementation steps, ensuring compliance with hard constraints like typography, color ratios, grid systems, and interaction patterns.

## Capabilities
*   **Systematic Auditing:** Reviews existing UI/UX against documented brand standards (e.g., LIC Brand Guide).
*   **Constraint Enforcement:** Ensures adherence to non-negotiable rules such as 'no shadows,' '8pt grid everywhere,' and specific color palettes.
*   **Action Plan Generation:** Outputs a structured, phased plan detailing necessary refactoring tasks rather than implementing the code itself.
*   **Technical Documentation:** Formats findings using technical markdown suitable for engineering handoffs.

## Example Use Cases
1.  **Brand Migration:** Given an old application and a new brand guide, it produces a step-by-step plan to replace all visual elements (buttons, forms, layouts) with system-compliant components.
2.  **UX Flow Optimization:** It analyzes complex workflows and suggests improvements based on established interaction rules (e.g., preferring right-side drawers over modals for reviews).
3.  **Design Token Mapping:** It identifies discrepancies between current styling and required design tokens, flagging necessary updates for the component library.