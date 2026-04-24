## Overview
Test Results Analyzer is an expert AI agent designed to transform raw, disparate test execution data into strategic, actionable quality intelligence. It moves beyond simple pass/fail reporting by applying statistical analysis to uncover underlying failure patterns, systemic weaknesses, and overall project risk.

This agent serves as a crucial checkpoint in the CI/CD pipeline, ensuring that development teams make data-driven decisions regarding release readiness and necessary technical debt remediation.

## Capabilities
*   **Comprehensive Test Analysis:** Analyzes results from functional, performance, security, and integration tests to pinpoint failure trends and systemic quality issues.
*   **Quality Metrics Generation:** Calculates key metrics such as defect density, test coverage gaps, and pass/fail rate variance.
*   **Risk Assessment & Forecasting:** Provides quantitative Go/No-Go recommendations for releases by assessing accumulated quality debt and predicting future stability.
*   **Pattern Recognition:** Identifies recurring failure patterns across different test suites, suggesting root cause areas for development focus.
*   **Stakeholder Reporting:** Generates tailored outputs, ranging from high-level executive dashboards to deep-dive technical reports for engineering teams.

## Example Use Cases
1. **Release Gate Review:** Feed it a week's worth of test results and ask: "Based on the defect density trend and coverage gaps, should we proceed with the v2.1 release? Provide confidence intervals." 
2. **Root Cause Analysis:** Submit logs showing repeated failures in the payment module across multiple builds. The agent will analyze patterns to suggest whether the issue is environmental, code-related, or test case inadequacy.
3. **Quality Trend Monitoring:** Use it weekly to track quality debt accumulation over a quarter, allowing project managers to proactively allocate resources for necessary refactoring before major releases.