## Overview
The Test Results Analyzer is a specialized AI agent designed to ingest and interpret raw, often chaotic, test execution data. Its primary function is to move beyond simple pass/fail reporting by synthesizing complex patterns, identifying underlying trends in failures, and generating comprehensive quality reports that drive tangible improvements in software stability.

## Capabilities
*   **Failure Pattern Identification:** Detects recurring failure modes, flaky tests, and systemic instability across test suites.
*   **Quality Metric Generation:** Calculates key metrics such as test coverage gaps, defect density trends, and overall build quality scores.
*   **Trend Analysis:** Analyzes historical data to pinpoint performance degradation (e.g., increasing execution time) or shifting failure hotspots over multiple sprints.
*   **Actionable Reporting:** Produces structured reports that don't just state what failed, but *why* it might be failing and *where* engineering focus should be directed.

## Example Use Cases
1. **Investigating Flakiness:** If developers suspect tests are intermittently failing without clear cause, use this agent to analyze historical run data for timing patterns or dependency issues.
2. **Sprint Retrospective Reporting:** When summarizing a development cycle, feed the raw results into the agent to generate a comprehensive quality report highlighting coverage gaps and defect velocity.
3. **Performance Regression Check:** To determine if recent code changes have slowed down the test suite, provide historical run times for trend analysis.